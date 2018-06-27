# utl_proc_gmap_classic_graphics_grid_containing_four_states
Proc gmap classic graphics grid layout containing four states.  Keywords: sas sql join merge big data analytics macros oracle teradata mysql sas communities stackoverflow statistics artificial inteligence AI Python R Java Javascript WPS Matlab SPSS Scala Perl C C# Excel MS Access JSON graphics maps NLP natural language processing machine learning igraph DOSUBL DOW loop stackoverflow SAS community.

    Proc gmap classic graphics grid layout containing four states

    You may need classic SAS to run this, no enhancements?

    for graphic output
    https://tinyurl.com/y8pz3qap
    https://github.com/rogerjdeangelis/utl_proc_gmap_classic_graphics_grid_containing_four_states/blob/master/utl_proc_gmap_classic_graphics_grid_containing_four_states


    github
    https://github.com/rogerjdeangelis/utl_proc_gmap_classic_graphics_grid_containing_four_states


    see SAS Forum
    https://tinyurl.com/yb8q6us6
    https://communities.sas.com/t5/ODS-and-Base-Reporting/ODS-PDF-Output-ODS-LAYOUT-GRIDDED-Advance-bygroup-with-PROC-GMAP/m-p/473505

    INPUT
    =====

      1. C:\Program Files\SAS\SASFoundation\9.4\maps  (part of classic SAS)
         maps.counties  ( the maps libredf is usually automatically assigned)

      2. SASHELP.TEMPLT (part of classic SAS)

           Contents of Catalog SASHELP.TEMPLT

           Name       Description
         -----------------------------------------------------
           H2         1 BOX LEFT, 1 BOX RIGHT
           H2S        1 BOX LEFT, 1 BOX RIGHT (WITH SPACE)
           H3         3 BOXES ACROSS (HORIZONTALLY)
           H3S        3 BOXES ACROSS (WITH SPACE)
           H4         4 BOXES ACROSS (HORIZONTALLY)
           H4S        4 BOXES ACROSS (WITH SPACE)
           L1R2       1 BOX LEFT, 2 BOXES RIGHT
           L1R2S      1 BOX LEFT, 2 BOXES RIGHT (WITH SPACE)
           L2R1       2 BOXES LEFT, 1 BOX RIGHT
           L2R1S      2 BOXES LEFT, 1 BOX RIGHT (WITH SPACE)
           L2R2       2 BOXES LEFT, 2 BOXES RIGHT

           L2R2S      2 BOXES LEFT, 2 BOXES RIGHT (WITH SPACE)  ** we will use this one

           U1D2       1 BOX UP, 2 BOXES DOWN
           U1D2S      1 BOX UP, 2 BOXES DOWN (WITH SPACE)
           U2D1       2 BOXES UP, 1 BOX DOWN
           U2D1S      2 BOXES UP, 1 BOX DOWN (WITH SPACE)
           V2         1 BOX UP, 1 BOX DOWN
           V2S        1 BOX UP, 1 BOX DOWN (WITH SPACE)
           V3         3 BOXES STACKED VERTICALLY
           V3S        3 BOXES STACKED VERTICALLY (WITH SPACE)
           WHOLE      ENTIRE SCREEN TEMPLATE


    PROCESS
    =======

    title;
    footnote;

    %utlfkil(d:\pdf\utl_proc_gmap_classic_graphics_grid_containing_four_states.pdf);

    filename outfile "d:/pdf/utl_proc_gmap_classic_graphics_grid_containing_four_states.pdf";
    goptions
        reset   = global
        rotate  = portrait
        gsfmode = replace
        device  = pdf
        gsfname = outfile
        vsize   = 10in
        hsize   = 8in
        htext   = 2
        nodisplay;

    run;quit;

    %macro map_state(state,abv=);

       /* for trsting without macro  %let abv=NJ; %let state=34; */

       proc gproject data=maps.counties(where=(state=&state)) out=&abv;
         id state county;
       run;quit;

       pattern1 v=me c=black r=15;
       proc gmap data=&abv map=&abv gout=work.gseg;;
           id state county;
           choro county / nolegend coutline=grayaa name="&abv";
       run; quit;

    %mend map_state;

    %map_state(state=50,abv=VT);
    %map_state(state=33,abv=NH);
    %map_state(state=10,abv=DE);
    %map_state(state=34,abv=NJ);

    goptions display;
    proc greplay igout=gseg  gout=excat
                 tc=sashelp.templt nofs
       template=l2r2s;

         treplay 1:VT
                 2:NH
                 3:DE
                 4:NJ
    ;
    quit;run;


    OUTPUT
    ======

      +--------------------------------------------------------------------------------+
      |                                                                                |
      |        *****************************       *************** *                   |
      |        *                           *       *               *                   |
      |        *                          *      *             *                       |
      |        *                         *       *          *                          |
      |        *                          *      *      *                              |
      |         *                        **      *        *                            |
      |          *                      *        *         *                           |
      |         *                   *  *          *        *                           |
      |       * *                  *              *          *                         |
      |       *      VERMONT                       * DELAWARE   *                      |
      |      *                     *               *               *                   |
      |      *                    *                *                *                  |
      |       *                  *                 *               *                   |
      |       *                 *                  *               *                   |
      |      *               **                    *                   *               |
      |      *               *                      *                    *             |
      |          *          *                       *                      *           |
      |          *         *                        *                         *        |
      |          *         *                        *                           *      |
      |         *         **                         *                          *      |
      |         *         *                          *                           *     |
      |         *         *                          *                           *     |
      |         *       * *                           *                           *    |
      |         *       **                            *                          *     |
      |         ***********                           *************************** *    |
      |                                                                                |
      +--------------------------------------------------------------------------------+
      |                                                                                |
      |                        ***                       * *                           |
      |                        ** *                     *      *                       |
      |                      ***  *                                *                   |
      |                      **   *                    *           *                   |
      |                    **     *                                   *                |
      |                    **     *                  *            *                    |
      |                     **    *                  *           *                     |
      |                *  *       *                  *           *                     |
      |               *           *                   *             *                  |
      |              *            *                   *              *                 |
      |              C            *                  *  NEW JERSEY   *                 |
      |             * NEW HANSHIRE*                  *   *           *                 |
      |             *             *                        *                           |
      |             *             *                      *             *               |
      |           *               *                       *            *               |
      |          **               *                   *                 *              |
      |        **                 *                *                 *                 |
      |       C                   C                *                 *                 |
      |      *                    *              *                *                    |
      |      **                   * *           *                *                     |
      |      *                      *           *               *                      |
      |       C                       *         *                                      |
      |      *                        **          *           *                        |
      |     **                      *              *          *                        |
      |     **********************                  * *        *                       |
      |                                                   *    *                       |
      |                                                        *                       |
      +--------------------------------------------------------------------------------+



    *                _              _       _
     _ __ ___   __ _| | _____    __| | __ _| |_ __ _
    | '_ ` _ \ / _` | |/ / _ \  / _` |/ _` | __/ _` |
    | | | | | | (_| |   <  __/ | (_| | (_| | || (_| |
    |_| |_| |_|\__,_|_|\_\___|  \__,_|\__,_|\__\__,_|

    ;

      * all data and templates oart of classic SAS
      * see input section

    *          _       _   _
     ___  ___ | |_   _| |_(_) ___  _ __
    / __|/ _ \| | | | | __| |/ _ \| '_ \
    \__ \ (_) | | |_| | |_| | (_) | | | |
    |___/\___/|_|\__,_|\__|_|\___/|_| |_|

    ;

    see process


