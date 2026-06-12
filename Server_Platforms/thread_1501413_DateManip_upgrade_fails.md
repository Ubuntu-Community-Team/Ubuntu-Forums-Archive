---
title: "Date::Manip upgrade fails"
date: 2010-06-04
forum: Server Platforms
---

### Post by pdc124 on 2010-06-04
upgrading Date::Manip fails here . 
ive tried upgrading File::Spec::Unix but that seems to be up to date. 


Use of uninitialized value in join or string at /usr/local/lib/perl/5.8.8/File/Spec/Unix.pm line 86.
Use of uninitialized value in pattern match (m//) at /usr/local/lib/perl/5.8.8/File/Spec/Unix.pm line 267.
Use of uninitialized value in join or string at /usr/local/lib/perl/5.8.8/File/Spec/Unix.pm line 86.
Use of uninitialized value in pattern match (m//) at /usr/local/lib/perl/5.8.8/File/Spec/Unix.pm line 267.
Use of uninitialized value in join or string at /usr/local/lib/perl/5.8.8/File/Spec/Unix.pm line 86.
Use of uninitialized value in pattern match (m//) at /usr/local/lib/perl/5.8.8/File/Spec/Unix.pm line 267.
Use of uninitialized value in join or string at /usr/local/lib/perl/5.8.8/File/Spec/Unix.pm line 86.
Use of uninitialized value in pattern match (m//) at /usr/local/lib/perl/5.8.8/File/Spec/Unix.pm line 267.
Use of uninitialized value in join or string at /usr/local/lib/perl/5.8.8/File/Spec/Unix.pm line 86.
Use of uninitialized value in pattern match (m//) at /usr/local/lib/perl/5.8.8/File/Spec/Unix.pm line 267.
Use of uninitialized value in join or string at /usr/local/lib/perl/5.8.8/File/Spec/Unix.pm line 86.
Use of uninitialized value in pattern match (m//) at /usr/local/lib/perl/5.8.8/File/Spec/Unix.pm line 267.

  CPAN.pm: Going to build S/SB/SBECK/Date-Manip-6.11.tar.gz

Warning: No success on command[/usr/bin/perl Build.PL ]
  SBECK/Date-Manip-6.11.tar.gz
  /usr/bin/perl Build.PL  -- NOT OK
Running Build test
  Make had some problems, won't test
Running Build install
  Make had some problems, won't install
Failed during this command:
 SBECK/Date-Manip-6.11.tar.gz                 : writemakefile NO '/usr/bin/perl Build.PL ' returned status -1

                                                                                                                       cpan[26]> upgrade File::Spec:Unix
All modules are up to date for File::Spec:Unix

                                                                                                                       cpan[27]> upgrade Date::Manip    

Package namespace         installed    latest  in CPAN file
Date::Manip                    5.58      6.11  SBECK/Date-Manip-6.11.tar.gz
Running install for module 'Date::Manip'
Running Build for S/SB/SBECK/Date-Manip-6.11.tar.gz
  Has already been unwrapped into directory /home/server/.cpan/build/Date-Manip-6.11-3z2SiK
  '/usr/bin/perl Build.PL ' returned status -1, won't make
Running Build test
  Make had some problems, won't test
Running Build install
  Make had some problems, won't install


how do i fix this ?

---

### Post by paulharwood on 2010-06-16
Having a similar issue when installing from cpan.

I have pasted as much of the code as the buffer had here

```


Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in regexp compilation at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 200.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 258.
Use of uninitialized value in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 182.
Use of uninitialized value in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 183.
Use of uninitialized value in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 184.
Use of uninitialized value in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 185.
Use of uninitialized value in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 186.
Use of uninitialized value in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 187.
Use of uninitialized value in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 188.
WARNING: [printf] Object must contain a valid delta
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 258.
WARNING: [printf] Object must contain a valid delta
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 258.
WARNING: [printf] Object must contain a valid delta
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 258.
WARNING: [printf] Object must contain a valid delta
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 258.
WARNING: [printf] Object must contain a valid delta
t/delta.printf.t .......................... 1/? Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
t/delta.printf.t .......................... Failed 20/36 subtests 
t/delta.set.t ............................. ok    
t/delta.type.t ............................ ok    
t/dm5.convtz.t ............................ skipped: Date::Manip 5.xx required
t/dm5.date.t .............................. skipped: Date::Manip 5.xx required
t/dm5.date_date_0.t ....................... skipped: Date::Manip 5.xx required
t/dm5.date_date_1.t ....................... skipped: Date::Manip 5.xx required
t/dm5.date_date_2a.t ...................... skipped: Date::Manip 5.xx required
t/dm5.date_date_2b.t ...................... skipped: Date::Manip 5.xx required
t/dm5.date_delta_0.t ...................... skipped: Date::Manip 5.xx required
t/dm5.date_delta_1.t ...................... skipped: Date::Manip 5.xx required
t/dm5.date_delta_2a.t ..................... skipped: Date::Manip 5.xx required
t/dm5.date_delta_2b.t ..................... skipped: Date::Manip 5.xx required
t/dm5.date_delta_french.t ................. skipped: Date::Manip 5.xx required
t/dm5.date_delta_russian.t ................ skipped: Date::Manip 5.xx required
t/dm5.date_delta_sign.t ................... skipped: Date::Manip 5.xx required
t/dm5.date_french.t ....................... skipped: Date::Manip 5.xx required
t/dm5.date_german.t ....................... skipped: Date::Manip 5.xx required
t/dm5.date_misc_a.t ....................... skipped: Date::Manip 5.xx required
t/dm5.date_misc_b.t ....................... skipped: Date::Manip 5.xx required
t/dm5.date_romanian.t ..................... skipped: Date::Manip 5.xx required
t/dm5.date_russian.t ...................... skipped: Date::Manip 5.xx required
t/dm5.date_today_0.t ...................... skipped: Date::Manip 5.xx required
t/dm5.date_today_1.t ...................... skipped: Date::Manip 5.xx required
t/dm5.delta_a.t ........................... skipped: Date::Manip 5.xx required
t/dm5.delta_b.t ........................... skipped: Date::Manip 5.xx required
t/dm5.delta_delta_0.t ..................... skipped: Date::Manip 5.xx required
t/dm5.delta_delta_1.t ..................... skipped: Date::Manip 5.xx required
t/dm5.delta_delta_2a.t .................... skipped: Date::Manip 5.xx required
t/dm5.delta_delta_2b.t .................... skipped: Date::Manip 5.xx required
t/dm5.delta_format.t ...................... skipped: Date::Manip 5.xx required
t/dm5.delta_romanian.t .................... skipped: Date::Manip 5.xx required
t/dm5.events.t ............................ skipped: Date::Manip 5.xx required
t/dm5.getnext.t ........................... skipped: Date::Manip 5.xx required
t/dm5.getprev.t ........................... skipped: Date::Manip 5.xx required
t/dm5.normalize_business.t ................ skipped: Date::Manip 5.xx required
t/dm5.nthday.t ............................ skipped: Date::Manip 5.xx required
t/dm5.recur_0.t ........................... skipped: Date::Manip 5.xx required
t/dm5.recur_1.t ........................... skipped: Date::Manip 5.xx required
t/dm5.settime.t ........................... skipped: Date::Manip 5.xx required
t/dm5.unixdate.t .......................... skipped: Date::Manip 5.xx required
t/orig.convtz.t ........................... ok   
t/orig.datecalc.date_date.t ............... Not an ARRAY reference at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Date.pm line 1352.
t/orig.datecalc.date_date.t ............... Dubious, test returned 255 (wstat 65280, 0xff00)
No subtests run 
t/orig.datecalc.date_delta.0.t ............ Not an ARRAY reference at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Date.pm line 1352.
t/orig.datecalc.date_delta.0.t ............ Dubious, test returned 255 (wstat 65280, 0xff00)
No subtests run 
t/orig.datecalc.date_delta.1.t ............ Not an ARRAY reference at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Date.pm line 1352.
t/orig.datecalc.date_delta.1.t ............ Dubious, test returned 255 (wstat 65280, 0xff00)
No subtests run 
t/orig.delta_format.t ..................... Use of uninitialized value in regexp compilation at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 195.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
t/orig.delta_format.t ..................... Failed 6/8 subtests 
t/orig.eventslist.t ....................... Use of uninitialized value $of in regexp compilation at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Date.pm line 1347.
Use of uninitialized value $on in regexp compilation at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Date.pm line 1338.
Use of uninitialized value $day_name in regexp compilation at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Date.pm line 1339.
Use of uninitialized value $day_abb in regexp compilation at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Date.pm line 1339.
Use of uninitialized value $abb in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Date.pm line 1297.
Use of uninitialized value $nam in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Date.pm line 1297.
Not an ARRAY reference at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Date.pm line 1377.
t/orig.eventslist.t ....................... Dubious, test returned 255 (wstat 65280, 0xff00)
No subtests run 
t/orig.getnext.t .......................... Not an ARRAY reference at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Date.pm line 1352.
t/orig.getnext.t .......................... Dubious, test returned 255 (wstat 65280, 0xff00)
No subtests run 
t/orig.getprev.t .......................... Not an ARRAY reference at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Date.pm line 1352.
t/orig.getprev.t .......................... Dubious, test returned 255 (wstat 65280, 0xff00)
No subtests run 
t/orig.nthdayofyear.t ..................... ok   
t/orig.parsedatedelta.t ................... Use of uninitialized value in regexp compilation at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 195.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in regexp compilation at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 200.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 258.
Use of uninitialized value in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 182.
Use of uninitialized value in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 183.
Use of uninitialized value in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 184.
Use of uninitialized value in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 185.
Use of uninitialized value in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 186.
Use of uninitialized value in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 187.
Use of uninitialized value in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 188.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 258.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 258.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 258.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 258.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 258.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 258.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 258.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 258.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 258.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 258.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 258.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 258.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 258.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 258.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 258.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 258.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 258.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
Use of uninitialized value in numeric eq (==) at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Delta.pm line 222.
t/orig.parsedatedelta.t ................... Failed 22/31 subtests 
t/orig.parsedatestring.t .................. Not an ARRAY reference at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Date.pm line 1352.
t/orig.parsedatestring.t .................. Dubious, test returned 255 (wstat 65280, 0xff00)
No subtests run 
t/orig.parserecur.t ....................... Use of uninitialized value $on in regexp compilation at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1345.
Use of uninitialized value $of in regexp compilation at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1345.
Use of uninitialized value $each in regexp compilation at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1337.
Use of uninitialized value $month in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1367.
Use of uninitialized value $week in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1368.
Use of uninitialized value $day in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1369.
Use of uninitialized value $last in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1371.
Use of uninitialized value $nth in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1372.
Use of uninitialized value $nth_wom in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1373.
Use of uninitialized value $nth_dom in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1374.
Use of uninitialized value $day_name in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1377.
Use of uninitialized value $day_abb in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1377.
Use of uninitialized value $mon_name in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1378.
Use of uninitialized value $mon_abb in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1378.
(?<nth>)* matches null string many times in regex; marked by <-- HERE in m/^(?:(?:^|\s+)(?<nth>)?(?:^|\s+)(?:(?<day_name>)|(?<day_abb>))(?:^|\s+)(?:(?<mon_name>)|(?<mon_abb>))(?:(?:^|\s+)(?:(?<y>\d\d\d\d)|(?<y>\d\d)))?|(?:^|\s+)(?<last>)(?:^|\s+)(?:(?<day_name>)|(?<day_abb>))(?:^|\s+)(?:(?<mon_name>)|(?<mon_abb>))(?:(?:^|\s+)(?:(?<y>\d\d\d\d)|(?<y>\d\d)))?|(?:^|\s+)(?<nth>)?(?:^|\s+)(?:(?<day_name>)|(?<day_abb>))(?:^|\s+)(?<month>)(?:(?:^|\s+)(?:(?<y>\d\d\d\d)|(?<y>\d\d)))?|(?:^|\s+)(?<last>)(?:^|\s+)(?:(?<day_name>)|(?<day_abb>))(?:^|\s+)(?<month>)(?:(?:^|\s+)(?:(?<y>\d\d\d\d)|(?<y>\d\d)))?|(?:^|\s+)(?<nth>)?(?:^|\s+)(?<day>)(?:^|\s+)(?<month>)(?:(?:^|\s+)(?:(?<y>\d\d\d\d)|(?<y>\d\d)))?|(?:^|\s+)(?<last>)(?:^|\s+)(?<day>)(?:^|\s+)(?<month>)(?:(?:^|\s+)(?:(?<y>\d\d\d\d)|(?<y>\d\d)))?|(?:^|\s+)(?<nth>)* <-- HERE (?:^|\s+)(?<day>)(?:(?:^|\s+)(?:(?<y>\d\d\d\d)|(?<y>\d\d)))?|(?:^|\s+)(?<n>\d+)(?:^|\s+)(?<day>)(?:(?:^|\s+)(?:(?<y>\d\d\d\d)|(?<y>\d\d)))?)\s*$/ at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1410.
Not an ARRAY reference at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Date.pm line 1352.
t/orig.parserecur.t ....................... Dubious, test returned 255 (wstat 65280, 0xff00)
No subtests run 
t/orig.settime.t .......................... Not an ARRAY reference at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Date.pm line 1352.
t/orig.settime.t .......................... Dubious, test returned 255 (wstat 65280, 0xff00)
No subtests run 
t/orig.unixdate.t ......................... Not an ARRAY reference at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Date.pm line 1352.
t/orig.unixdate.t ......................... Dubious, test returned 255 (wstat 65280, 0xff00)
No subtests run 
t/pod.t ................................... ok       
t/pod_coverage.t .......................... ok       
t/recur.dates.0.t ......................... Use of uninitialized value $on in regexp compilation at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1345.
Use of uninitialized value $of in regexp compilation at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1345.
Use of uninitialized value $each in regexp compilation at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1337.
Use of uninitialized value $month in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1367.
Use of uninitialized value $week in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1368.
Use of uninitialized value $day in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1369.
Use of uninitialized value $last in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1371.
Use of uninitialized value $nth in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1372.
Use of uninitialized value $nth_wom in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1373.
Use of uninitialized value $nth_dom in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1374.
Use of uninitialized value $day_name in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1377.
Use of uninitialized value $day_abb in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1377.
Use of uninitialized value $mon_name in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1378.
Use of uninitialized value $mon_abb in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1378.
(?<nth>)* matches null string many times in regex; marked by <-- HERE in m/^(?:(?:^|\s+)(?<nth>)?(?:^|\s+)(?:(?<day_name>)|(?<day_abb>))(?:^|\s+)(?:(?<mon_name>)|(?<mon_abb>))(?:(?:^|\s+)(?:(?<y>\d\d\d\d)|(?<y>\d\d)))?|(?:^|\s+)(?<last>)(?:^|\s+)(?:(?<day_name>)|(?<day_abb>))(?:^|\s+)(?:(?<mon_name>)|(?<mon_abb>))(?:(?:^|\s+)(?:(?<y>\d\d\d\d)|(?<y>\d\d)))?|(?:^|\s+)(?<nth>)?(?:^|\s+)(?:(?<day_name>)|(?<day_abb>))(?:^|\s+)(?<month>)(?:(?:^|\s+)(?:(?<y>\d\d\d\d)|(?<y>\d\d)))?|(?:^|\s+)(?<last>)(?:^|\s+)(?:(?<day_name>)|(?<day_abb>))(?:^|\s+)(?<month>)(?:(?:^|\s+)(?:(?<y>\d\d\d\d)|(?<y>\d\d)))?|(?:^|\s+)(?<nth>)?(?:^|\s+)(?<day>)(?:^|\s+)(?<month>)(?:(?:^|\s+)(?:(?<y>\d\d\d\d)|(?<y>\d\d)))?|(?:^|\s+)(?<last>)(?:^|\s+)(?<day>)(?:^|\s+)(?<month>)(?:(?:^|\s+)(?:(?<y>\d\d\d\d)|(?<y>\d\d)))?|(?:^|\s+)(?<nth>)* <-- HERE (?:^|\s+)(?<day>)(?:(?:^|\s+)(?:(?<y>\d\d\d\d)|(?<y>\d\d)))?|(?:^|\s+)(?<n>\d+)(?:^|\s+)(?<day>)(?:(?:^|\s+)(?:(?<y>\d\d\d\d)|(?<y>\d\d)))?)\s*$/ at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1410.
t/recur.dates.0.t ......................... 1/? Use of uninitialized value $of in regexp compilation at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Date.pm line 1347.
Use of uninitialized value $on in regexp compilation at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Date.pm line 1338.
Use of uninitialized value $day_name in regexp compilation at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Date.pm line 1339.
Use of uninitialized value $day_abb in regexp compilation at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Date.pm line 1339.
Use of uninitialized value $abb in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Date.pm line 1297.
Use of uninitialized value $nam in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Date.pm line 1297.
Not an ARRAY reference at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Date.pm line 1377.
t/recur.dates.0.t ......................... Dubious, test returned 9 (wstat 2304, 0x900)
Failed 26/113 subtests 
t/recur.dates.1.t ......................... Not an ARRAY reference at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Date.pm line 1352.
t/recur.dates.1.t ......................... Dubious, test returned 255 (wstat 65280, 0xff00)
No subtests run 
t/recur.dates.2.t ......................... Use of uninitialized value $on in regexp compilation at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1345.
Use of uninitialized value $of in regexp compilation at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1345.
Use of uninitialized value $each in regexp compilation at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1337.
Use of uninitialized value $month in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1367.
Use of uninitialized value $week in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1368.
Use of uninitialized value $day in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1369.
Use of uninitialized value $last in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1371.
Use of uninitialized value $nth in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1372.
Use of uninitialized value $nth_wom in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1373.
Use of uninitialized value $nth_dom in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1374.
Use of uninitialized value $day_name in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1377.
Use of uninitialized value $day_abb in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1377.
Use of uninitialized value $mon_name in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1378.
Use of uninitialized value $mon_abb in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1378.
(?<nth>)* matches null string many times in regex; marked by <-- HERE in m/^(?:(?:^|\s+)(?<nth>)?(?:^|\s+)(?:(?<day_name>)|(?<day_abb>))(?:^|\s+)(?:(?<mon_name>)|(?<mon_abb>))(?:(?:^|\s+)(?:(?<y>\d\d\d\d)|(?<y>\d\d)))?|(?:^|\s+)(?<last>)(?:^|\s+)(?:(?<day_name>)|(?<day_abb>))(?:^|\s+)(?:(?<mon_name>)|(?<mon_abb>))(?:(?:^|\s+)(?:(?<y>\d\d\d\d)|(?<y>\d\d)))?|(?:^|\s+)(?<nth>)?(?:^|\s+)(?:(?<day_name>)|(?<day_abb>))(?:^|\s+)(?<month>)(?:(?:^|\s+)(?:(?<y>\d\d\d\d)|(?<y>\d\d)))?|(?:^|\s+)(?<last>)(?:^|\s+)(?:(?<day_name>)|(?<day_abb>))(?:^|\s+)(?<month>)(?:(?:^|\s+)(?:(?<y>\d\d\d\d)|(?<y>\d\d)))?|(?:^|\s+)(?<nth>)?(?:^|\s+)(?<day>)(?:^|\s+)(?<month>)(?:(?:^|\s+)(?:(?<y>\d\d\d\d)|(?<y>\d\d)))?|(?:^|\s+)(?<last>)(?:^|\s+)(?<day>)(?:^|\s+)(?<month>)(?:(?:^|\s+)(?:(?<y>\d\d\d\d)|(?<y>\d\d)))?|(?:^|\s+)(?<nth>)* <-- HERE (?:^|\s+)(?<day>)(?:(?:^|\s+)(?:(?<y>\d\d\d\d)|(?<y>\d\d)))?|(?:^|\s+)(?<n>\d+)(?:^|\s+)(?<day>)(?:(?:^|\s+)(?:(?<y>\d\d\d\d)|(?<y>\d\d)))?)\s*$/ at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1410.
t/recur.dates.2.t ......................... ok   
t/recur.frequency.t ....................... Use of uninitialized value $on in regexp compilation at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1345.
Use of uninitialized value $of in regexp compilation at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1345.
Use of uninitialized value $each in regexp compilation at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1337.
Use of uninitialized value $month in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1367.
Use of uninitialized value $week in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1368.
Use of uninitialized value $day in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1369.
Use of uninitialized value $last in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1371.
Use of uninitialized value $nth in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1372.
Use of uninitialized value $nth_wom in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1373.
Use of uninitialized value $nth_dom in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1374.
Use of uninitialized value $day_name in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1377.
Use of uninitialized value $day_abb in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1377.
Use of uninitialized value $mon_name in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1378.
Use of uninitialized value $mon_abb in concatenation (.) or string at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1378.
(?<nth>)* matches null string many times in regex; marked by <-- HERE in m/^(?:(?:^|\s+)(?<nth>)?(?:^|\s+)(?:(?<day_name>)|(?<day_abb>))(?:^|\s+)(?:(?<mon_name>)|(?<mon_abb>))(?:(?:^|\s+)(?:(?<y>\d\d\d\d)|(?<y>\d\d)))?|(?:^|\s+)(?<last>)(?:^|\s+)(?:(?<day_name>)|(?<day_abb>))(?:^|\s+)(?:(?<mon_name>)|(?<mon_abb>))(?:(?:^|\s+)(?:(?<y>\d\d\d\d)|(?<y>\d\d)))?|(?:^|\s+)(?<nth>)?(?:^|\s+)(?:(?<day_name>)|(?<day_abb>))(?:^|\s+)(?<month>)(?:(?:^|\s+)(?:(?<y>\d\d\d\d)|(?<y>\d\d)))?|(?:^|\s+)(?<last>)(?:^|\s+)(?:(?<day_name>)|(?<day_abb>))(?:^|\s+)(?<month>)(?:(?:^|\s+)(?:(?<y>\d\d\d\d)|(?<y>\d\d)))?|(?:^|\s+)(?<nth>)?(?:^|\s+)(?<day>)(?:^|\s+)(?<month>)(?:(?:^|\s+)(?:(?<y>\d\d\d\d)|(?<y>\d\d)))?|(?:^|\s+)(?<last>)(?:^|\s+)(?<day>)(?:^|\s+)(?<month>)(?:(?:^|\s+)(?:(?<y>\d\d\d\d)|(?<y>\d\d)))?|(?:^|\s+)(?<nth>)* <-- HERE (?:^|\s+)(?<day>)(?:(?:^|\s+)(?:(?<y>\d\d\d\d)|(?<y>\d\d)))?|(?:^|\s+)(?<n>\d+)(?:^|\s+)(?<day>)(?:(?:^|\s+)(?:(?<y>\d\d\d\d)|(?<y>\d\d)))?)\s*$/ at /home/paulh/.cpan/build/Date-Manip-6.11-9S1lry/blib/lib/Date/Manip/Recur.pm line 1410.
t/recur.frequency.t ....................... ok    
t/tz.all_periods.t ........................ ok   
t/tz.convert.t ............................ ok    
t/tz.convert_from_gmt.t ................... ok   
t/tz.convert_to_gmt.t ..................... ok   
t/tz.date_period.t ........................ ok   
t/tz.define_abbrev.t ...................... ok   
t/tz.define_alias.t ....................... ok   
t/tz.define_offset.t ...................... ok    
t/tz.periods.t ............................ ok    
t/tz.zone.t ............................... ok    
t/tzdata._ruleinfo.t ...................... ok    
t/tzdata._zoneinfo.t ...................... ok    

Test Summary Report
-------------------
t/date.calc.date_date_approx.t          (Wstat: 65280 Tests: 0 Failed: 0)
  Non-zero exit status: 255
  Parse errors: No plan found in TAP output
t/date.calc.date_date_bapprox.t         (Wstat: 65280 Tests: 0 Failed: 0)
  Non-zero exit status: 255
  Parse errors: No plan found in TAP output
t/date.calc.date_date_business.t        (Wstat: 65280 Tests: 0 Failed: 0)
  Non-zero exit status: 255
  Parse errors: No plan found in TAP output
t/date.calc.date_delta.romanian.t       (Wstat: 512 Tests: 0 Failed: 0)
  Non-zero exit status: 2
  Parse errors: No plan found in TAP output
t/date.calc.date_delta.t                (Wstat: 0 Tests: 50 Failed: 47)
  Failed tests:  2-21, 23-33, 35-50
t/date.calc.date_delta_business.0.t     (Wstat: 65280 Tests: 0 Failed: 0)
  Non-zero exit status: 255
  Parse errors: No plan found in TAP output
t/date.calc.date_delta_business.1.t     (Wstat: 65280 Tests: 0 Failed: 0)
  Non-zero exit status: 255
  Parse errors: No plan found in TAP output
t/date.calc.date_delta_business.2.t     (Wstat: 65280 Tests: 0 Failed: 0)
  Non-zero exit status: 255
  Parse errors: No plan found in TAP output
t/date.calc.date_delta_business.french.t (Wstat: 512 Tests: 0 Failed: 0)
  Non-zero exit status: 2
  Parse errors: No plan found in TAP output
t/date.holiday.t                        (Wstat: 2304 Tests: 0 Failed: 0)
  Non-zero exit status: 9
  Parse errors: No plan found in TAP output
t/date.is_business_day.t                (Wstat: 2304 Tests: 1 Failed: 0)
  Non-zero exit status: 9
  Parse errors: No plan found in TAP output
t/date.list_events.0.t                  (Wstat: 65280 Tests: 0 Failed: 0)
  Non-zero exit status: 255
  Parse errors: No plan found in TAP output
t/date.list_events.1.t                  (Wstat: 65280 Tests: 0 Failed: 0)
  Non-zero exit status: 255
  Parse errors: No plan found in TAP output
t/date.list_holidays.t                  (Wstat: 2304 Tests: 0 Failed: 0)
  Non-zero exit status: 9
  Parse errors: No plan found in TAP output
t/date.nearest_business_day.t           (Wstat: 65280 Tests: 0 Failed: 0)
  Non-zero exit status: 255
  Parse errors: No plan found in TAP output
t/date.next_business_day.t              (Wstat: 65280 Tests: 0 Failed: 0)
  Non-zero exit status: 255
  Parse errors: No plan found in TAP output
t/date.parse.common.t                   (Wstat: 65280 Tests: 1 Failed: 0)
  Non-zero exit status: 255
  Parse errors: No plan found in TAP output
t/date.parse.delta.t                    (Wstat: 65280 Tests: 0 Failed: 0)
  Non-zero exit status: 255
  Parse errors: No plan found in TAP output
t/date.parse.french.t                   (Wstat: 512 Tests: 0 Failed: 0)
  Non-zero exit status: 2
  Parse errors: No plan found in TAP output
t/date.parse.misc.0.t                   (Wstat: 65280 Tests: 0 Failed: 0)
  Non-zero exit status: 255
  Parse errors: No plan found in TAP output
t/date.parse.misc.1.t                   (Wstat: 65280 Tests: 0 Failed: 0)
  Non-zero exit status: 255
  Parse errors: No plan found in TAP output
t/date.parse_date.common.t              (Wstat: 65280 Tests: 3 Failed: 0)
  Non-zero exit status: 255
  Parse errors: No plan found in TAP output
t/date.parse_date.misc.0.t              (Wstat: 65280 Tests: 0 Failed: 0)
  Non-zero exit status: 255
  Parse errors: No plan found in TAP output
t/date.parse_date.misc.1.t              (Wstat: 65280 Tests: 0 Failed: 0)
  Non-zero exit status: 255
  Parse errors: No plan found in TAP output
t/date.parse_format.t                   (Wstat: 0 Tests: 2 Failed: 1)
  Failed test:  2
t/date.parse_time.t                     (Wstat: 65280 Tests: 0 Failed: 0)
  Non-zero exit status: 255
  Parse errors: No plan found in TAP output
t/date.prev_business_day.t              (Wstat: 65280 Tests: 0 Failed: 0)
  Non-zero exit status: 255
  Parse errors: No plan found in TAP output
t/date.printf.0.t                       (Wstat: 65280 Tests: 0 Failed: 0)
  Non-zero exit status: 255
  Parse errors: No plan found in TAP output
t/date.printf.1.t                       (Wstat: 65280 Tests: 0 Failed: 0)
  Non-zero exit status: 255
  Parse errors: No plan found in TAP output
t/delta.calc.delta_delta_approx.t       (Wstat: 0 Tests: 8 Failed: 8)
  Failed tests:  1-8
t/delta.calc.delta_delta_business.0.t   (Wstat: 0 Tests: 1 Failed: 1)
  Failed test:  1
t/delta.calc.delta_delta_business.1.t   (Wstat: 0 Tests: 1 Failed: 1)
  Failed test:  1
t/delta.calc.delta_delta_exact.t        (Wstat: 0 Tests: 7 Failed: 7)
  Failed tests:  1-7
t/delta.parse.t                         (Wstat: 0 Tests: 26 Failed: 24)
  Failed tests:  1, 3-25
t/delta.printf.t                        (Wstat: 0 Tests: 36 Failed: 20)
  Failed tests:  7, 9-22, 27-30, 36
t/orig.datecalc.date_date.t             (Wstat: 65280 Tests: 0 Failed: 0)
  Non-zero exit status: 255
  Parse errors: No plan found in TAP output
t/orig.datecalc.date_delta.0.t          (Wstat: 65280 Tests: 0 Failed: 0)
  Non-zero exit status: 255
  Parse errors: No plan found in TAP output
t/orig.datecalc.date_delta.1.t          (Wstat: 65280 Tests: 0 Failed: 0)
  Non-zero exit status: 255
  Parse errors: No plan found in TAP output
t/orig.delta_format.t                   (Wstat: 0 Tests: 8 Failed: 6)
  Failed tests:  2-4, 6-8
t/orig.eventslist.t                     (Wstat: 65280 Tests: 0 Failed: 0)
  Non-zero exit status: 255
  Parse errors: No plan found in TAP output
t/orig.getnext.t                        (Wstat: 65280 Tests: 0 Failed: 0)
  Non-zero exit status: 255
  Parse errors: No plan found in TAP output
t/orig.getprev.t                        (Wstat: 65280 Tests: 0 Failed: 0)
  Non-zero exit status: 255
  Parse errors: No plan found in TAP output
t/orig.parsedatedelta.t                 (Wstat: 0 Tests: 31 Failed: 22)
  Failed tests:  1, 3-9, 11-12, 17, 20-21, 23-31
t/orig.parsedatestring.t                (Wstat: 65280 Tests: 0 Failed: 0)
  Non-zero exit status: 255
  Parse errors: No plan found in TAP output
t/orig.parserecur.t                     (Wstat: 65280 Tests: 0 Failed: 0)
  Non-zero exit status: 255
  Parse errors: No plan found in TAP output
t/orig.settime.t                        (Wstat: 65280 Tests: 0 Failed: 0)
  Non-zero exit status: 255
  Parse errors: No plan found in TAP output
t/orig.unixdate.t                       (Wstat: 65280 Tests: 0 Failed: 0)
  Non-zero exit status: 255
  Parse errors: No plan found in TAP output
t/recur.dates.0.t                       (Wstat: 2304 Tests: 113 Failed: 26)
  Failed tests:  74-99
  Non-zero exit status: 9
  Parse errors: No plan found in TAP output
t/recur.dates.1.t                       (Wstat: 65280 Tests: 0 Failed: 0)
  Non-zero exit status: 255
  Parse errors: No plan found in TAP output
Files=152, Tests=3113, 47 wallclock secs ( 1.62 usr  0.46 sys + 43.00 cusr  3.19 csys = 48.27 CPU)
Result: FAIL
Failed 49/152 test programs. 163/3113 subtests failed.
  SBECK/Date-Manip-6.11.tar.gz
  ./Build test -- NOT OK
//hint// to see the cpan-testers results for installing this module, try:
  reports SBECK/Date-Manip-6.11.tar.gz
Warning (usually harmless): 'YAML' not installed, will not store persistent state
Running Build install
  make test had returned bad status, won't install without force
Could not read '/home/paulh/.cpan/build/YAML-Syck-1.10-hrPLaa/META.yml'. Falling back to other methods to determine prerequisites
Failed during this command:
 AVAR/YAML-Syck-1.10.tar.gz                   : writemakefile NO '/usr/bin/perl Makefile.PL INSTALLDIRS=site' returned status 512
 SBECK/Date-Manip-6.11.tar.gz                 : make_test NO



```

---

### Post by paulharwood on 2010-06-16
Ignore me, 

apt-get install build-essential

:oops:

---

### Post by pdc124 on 2010-06-16
ive discovered that you can install it through synaptic 

libdate-manip-perl does the job. 

Im not sure of the relationship between this and cpan to install modules, though

---

