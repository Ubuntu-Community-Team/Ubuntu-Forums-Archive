---
title: "MythTV reset commercial flagging"
date: 2011-11-04
forum: Server Platforms
---

### Post by wesg on 2011-11-04
My MythTV installation has been humming along nicely, but recently I updated my system clock and I think that messed with my commercial flagging. My clock was late so tv shows were clipped 10 minutes at the start, and it seems like that time was stored somewhere, so now that the clock is correct, the commercials have been flagged at incorrect times, without respect to the proper flags, like transitions, logos, etc.

Is there a way I can reset the way commercials are flagged so it learns again? I'm using XBMC on Windows for my frontend, but adjusting the backend isn't a problem.

---

### Post by ian dobson on 2011-11-05
Hi,

If you have mythweb installed you can select the recording and run commercial flagging again. Otherwise you should be able to run mythcommflag from the command line on the backend.

```

/usr/bin/mythcommflag --help
2011-11-05 11:08:09.078 Valid Options are:
-c OR --chanid <chanid>      Flag recording with given channel ID
-s OR --starttime <time>     Flag recording with given recording start time
-f OR --file <filename>      Flag recording with specific filename
--video <filename>           Rebuild the seektable for a video (non-recording) file
--sleep                      Give up some CPU time after processing each frame
--nopercentage               Don't print percentage done
--rebuild                    Do not flag commercials, just rebuild seektable
--clearskiplist              Clear the commercial skip list
--gencutlist                 Copy the commercial skip list to the cutlist
--clearcutlist               Clear the cutlist
--setcutlist CUTLIST         Set a new cutlist.  CUTLIST is of the form:
                             #-#[,#-#]...  (ie, 1-100,1520-3012,4091-5094
--getcutlist                 Display the current cutlist
--getskiplist                Display the current Commercial Skip list
-v or --verbose debug-level  Use '-v help' for level info
--queue                      Insert flagging job into the JobQueue rather than
                             running flagging in the foreground
                             WARNING: This option does NOT work with --rebuild
--quiet                      Don't display commercial flagging progress
--very-quiet                 Only display output
--all                        Re-run commercial flagging for all recorded
                             programs using current detection method.
--allstart YYYYMMDDHHMMSS    when using --all, only flag programs starting
                             after the 'allstart' date (default = Jan 1, 1970).
--allend YYYYMMDDHHMMSS      when using --all, only flag programs ending
                             before the 'allend' date (default is now).
--force                      Force flagging of a video even if mythcommflag
                             thinks it is already in use by another instance.
--method <method>            Commercial flagging method[s] to employ
                             off, blank, scene, blankscene, logo, all
                             d2, d2_logo, d2_blank, d2_scene, d2_all
--outputfile <filename>      file to write comm flagging output to - for stdout
--outputmethod <method>      format of output written to outputfile: essentials,full
--hogcpu                     Do not nice the flagging process.
                             WARNING: This will consume all free CPU time.
--skipdb                     Avoid DB usage
-h OR --help                 This text

Note: both --chanid and --starttime must be used together
      if either is used.

If no command line arguments are specified, all
unflagged videos will be flagged.
```

something like:-
/usr/bin/mythcommflag -f 93018_20100812053900.mpg

Regards
Ian Dobson

---

### Post by wesg on 2011-11-05
Ian,
thanks for the information. I tried that once too with MythWeb, but it seems like the timing of flagging is off. Some reason the commercials are 3-5 minutes late from what they should be. 

Maybe I'll look for some MythTV cache data somewhere...

---

