# utl-remove-the-variable-name-sufix-for-149-variables
Remove the '_14' suffix from 149 variables. 
    Remove the '_14' suffix from 149 variables

    SAs Forum
    https://co
    https://tinyurl.com/y9vdykslmmunities.sas.com/t5/New-SAS-User/How-to-delete-the-suffix-of-variable-names/m-p/510353

    github macros
    https://tinyurl.com/y9nfugth
    https://github.com/rogerjdeangelis/utl-macros-used-in-many-of-rogerjdeangelis-repositories


    HAVE
    ====

    Middle Observation(1 ) of Last dataset = WORK.HAVE - Total Obs 1

     -- NUMERIC --

    VAR      TYPE   VALUE

    S_1_14    N8    1234
    S_2_14    N8    1234
    S_3_14    N8    1234

    S_147_14  N8    1234
    S_148_14  N8    1234
    S_149_14  N8    1234


    WANT
    ====

    Middle Observation(1 ) of Last dataset = WORK.WANT - Total Obs 1

     -- NUMERIC --

    VAR      TYPE   VALUE

    S_1    N8    1234
    S_2    N8    1234
    S_3    N8    1234

    S_147  N8    1234
    S_148  N8    1234
    S_149  N8    1234

    PROCESS
    =======

    %array(rns,values=1-149);

    data want;
      set have(rename=(%do_over(rns,phrase=%str(s_?_14 = s_?))));
    run;quit;

    MAKE DATA
    =========

    %array(rns,values=1-149);

    data have;
     array vars[149] %do_over(rns,phrase=s_?_14) (149*1234);
    run;quit;


