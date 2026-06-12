---
title: "Cannot get the bash script correct?"
date: 2017-01-04
forum: Server Platforms
---

### Post by agarwaldvk on 2017-01-04
Hi Everyone


This bash script is supposed to send out backup job email notification to me (sudo privilieged user on the home server) at the completion of job - it does that but I want to add one more line of text to the content of the email text but haven't been able to get it going. Any help here would be great.

```

#!/bin/bash
todaysdatetime=$(date)
backup2l -b > /home/agarwaldvk/serverbackupjoboutput.txt
mail -s "Server Backup Job Status Report - Run : $todaysdatetime" deepakagarwalathome@gmail.com < /home/agarwaldvk/serverbackupjoboutput.txt

```


The notification email content currently looks something like this :-

```

backup2l v1.5 by Gundolf Kiefer

Wed Jan  4 10:10:01 AEDT 2017

Running pre-backup procedure...
  pre-backup: nothing to do

Removing old backups...
  removing <all.1>
  removing <all.11>
  removing <all.12>
  removing <all.13>
  removing <all.14>
  removing <all.15>
  removing <all.16>
  moving <all.2> to <all.1>
  moving <all.21> to <all.11>
  moving <all.22> to <all.12>
  moving <all.23> to <all.13>
  moving <all.24> to <all.14>
  moving <all.25> to <all.15>
  moving <all.26> to <all.16>
  moving <all.3> to <all.2>
  moving <all.31> to <all.21>
  moving <all.32> to <all.22>
  moving <all.33> to <all.23>
  moving <all.34> to <all.24>
  moving <all.35> to <all.25>
  moving <all.36> to <all.26>

Preparing full backup <all.3>...
  58 / 58 file(s), 14 / 14 dir(s), 86.9MB / 86.9MB (uncompressed)
  skipping: 0 file(s), 0 dir(s), 0 B (uncompressed)

Creating archive using 'DRIVER_TAR_GZ'...
Checking TOC of archive file (< real file, > archive entry)...
Creating check file for <all.3>...

Running post-backup procedure...
  post-backup: nothing to do

Wed Jan  4 10:10:05 AEDT 2017


Summary
=======

Backup       Date       Time  |  Size   | Skipped  Files+D |  New  Obs. | Err.
------------------------------------------------------------------------------
all.1        2017-01-03 16:50 |   86.3M |       0       72 |   72     0 |    0
all.11       2017-01-03 16:52 |      1K |       0       72 |    0     0 |    0
all.12       2017-01-03 16:54 |      1K |       0       72 |    0     0 |    0
all.13       2017-01-03 16:56 |      1K |       0       72 |    0     0 |    0
all.14       2017-01-03 16:58 |      1K |       0       72 |    0     0 |    0
all.15       2017-01-03 19:00 |      1K |       0       72 |    0     0 |    0
all.16       2017-01-03 19:10 |      1K |       0       72 |    0     0 |    0
all.2        2017-01-03 19:20 |   86.3M |       0       72 |   72     0 |    0
all.21       2017-01-03 19:30 |      1K |       0       72 |    0     0 |    0
all.22       2017-01-03 19:40 |      1K |       0       72 |    0     0 |    0
all.23       2017-01-03 19:50 |      1K |       0       72 |    0     0 |    0
all.24       2017-01-03 20:05 |      1K |       0       72 |    0     0 |    0
all.25       2017-01-04 07:36 |      1K |       0       72 |    0     0 |    0
all.26       2017-01-04 09:45 |      1K |       0       72 |    0     0 |    0
all.3        2017-01-04 10:10 |   86.3M |       0       72 |   72     0 |    0

Filesystem      Size  Used Avail Use% Mounted on
/dev/sdd1       1.8T  327M  1.7T   1% /sharedfiles/backupdata

```


What I would like to do is add another line (shown in bigger colour coded text to differentiate it from the original text) to the above content as the first line and leave a blank line after it so the email content would look something like this :-


```


[COLOR="#800000"][SIZE=3]The server would be shut down at the completion of the backup job[/SIZE][/COLOR]                     #Added line

backup2l v1.5 by Gundolf Kiefer

Wed Jan  4 10:10:01 AEDT 2017

Running pre-backup procedure...
  pre-backup: nothing to do

Removing old backups...
  removing <all.1>
  removing <all.11>
  removing <all.12>
  removing <all.13>
  removing <all.14>
  removing <all.15>
  removing <all.16>
  moving <all.2> to <all.1>
  moving <all.21> to <all.11>
  moving <all.22> to <all.12>
  moving <all.23> to <all.13>
  moving <all.24> to <all.14>
  moving <all.25> to <all.15>
  moving <all.26> to <all.16>
  moving <all.3> to <all.2>
  moving <all.31> to <all.21>
  moving <all.32> to <all.22>
  moving <all.33> to <all.23>
  moving <all.34> to <all.24>
  moving <all.35> to <all.25>
  moving <all.36> to <all.26>

Preparing full backup <all.3>...
  58 / 58 file(s), 14 / 14 dir(s), 86.9MB / 86.9MB (uncompressed)
  skipping: 0 file(s), 0 dir(s), 0 B (uncompressed)

Creating archive using 'DRIVER_TAR_GZ'...
Checking TOC of archive file (< real file, > archive entry)...
Creating check file for <all.3>...

Running post-backup procedure...
  post-backup: nothing to do

Wed Jan  4 10:10:05 AEDT 2017


Summary
=======

Backup       Date       Time  |  Size   | Skipped  Files+D |  New  Obs. | Err.
------------------------------------------------------------------------------
all.1        2017-01-03 16:50 |   86.3M |       0       72 |   72     0 |    0
all.11       2017-01-03 16:52 |      1K |       0       72 |    0     0 |    0
all.12       2017-01-03 16:54 |      1K |       0       72 |    0     0 |    0
all.13       2017-01-03 16:56 |      1K |       0       72 |    0     0 |    0
all.14       2017-01-03 16:58 |      1K |       0       72 |    0     0 |    0
all.15       2017-01-03 19:00 |      1K |       0       72 |    0     0 |    0
all.16       2017-01-03 19:10 |      1K |       0       72 |    0     0 |    0
all.2        2017-01-03 19:20 |   86.3M |       0       72 |   72     0 |    0
all.21       2017-01-03 19:30 |      1K |       0       72 |    0     0 |    0
all.22       2017-01-03 19:40 |      1K |       0       72 |    0     0 |    0
all.23       2017-01-03 19:50 |      1K |       0       72 |    0     0 |    0
all.24       2017-01-03 20:05 |      1K |       0       72 |    0     0 |    0
all.25       2017-01-04 07:36 |      1K |       0       72 |    0     0 |    0
all.26       2017-01-04 09:45 |      1K |       0       72 |    0     0 |    0
all.3        2017-01-04 10:10 |   86.3M |       0       72 |   72     0 |    0

Filesystem      Size  Used Avail Use% Mounted on
/dev/sdd1       1.8T  327M  1.7T   1% /sharedfiles/backupdata

```

I think I can achieve this by doing the following :-
1. store the contents of the file (/home/agarwaldvk/serverbackupjoboutput.txt) in a variable - say 'outputlog'
2. store the text content for the new line in another variable - say 'testnewline'
3. store the combined contents of these 2 variables 'outputlog' and 'testnewline' with a new line between them in a new variable, say 'finalvalue' - but I am not able to do it - that should be relatively easy to do, shouldn't it?
4. modify the last line in my bash script to read the content from this new variable like so :-

```

mail -s "Server Backup Job Status Report - Run : $todaysdatetime" deepakagarwalathome@gmail.com < finalvalue

```

Can anyone please suggest how to do that?


Edit :-
I was able to store the contents of the output log file in to a variable like so :-

```

outputlog=$(</home/agarwaldvk/testoutput.txt)

```

but couldn't combine the 2 variables in to one (1) with a newline character in between them.


Best regards


Deepak

---

### Post by TheFu on 2017-01-04
Why not just create the file with the shutdown notice, then append the other stuff to the same file?

<<, >>, or tee -a

Did appending not work?

---

### Post by agarwaldvk on 2017-01-04
Hi TheFu


I don't quite understand what you mean. Is this what you mean

```

#!/bin/bash
shutdownnotice=$'The server would be shutdown at the completion of the backup job!\n'
todaysdatetime=$(date)
echo  $shutdownnotice > /home/agarwaldvk/serverbackupjoboutput.txt
backup2l -b >> /home/agarwaldvk/serverbackupjoboutput.txt
mail -s "Server Backup Job Status Report - Run : $todaysdatetime" myemailaddress@gmail.com < /home/agarwaldvk/serverbackupjoboutput.txt

```

I haven't tried this yet but do you think this might work? I will try it out on my return - need to go out now!


Best regards


Deepak

---

### Post by TheFu on 2017-01-05
```
cat /etc/hosts > /tmp/file  # creates a file with the contents of the input.
cat /etc/hosts >> /tmp/file # appends whatever is in the input to the existing file.  Or creates the file new as needed.

```
Test it. See what happens. BTW, this is normally covered in day 3 of a basic Unix course.

---

### Post by agarwaldvk on 2017-01-05
Hi


Have now been able to get it to work - this is what I have done :-


```

#!/bin/bash
shutdownnotice=$'The server would be shutdown at the completion of the backup job!\n'
echo "$shutdownnotice" > /home/agarwaldvk/serverbackupjoboutput.txt
todaysdatetime=$(date)
backup2l -b >> /home/agarwaldvk/serverbackupjoboutput.txt
mail -s "Server Backup Job Status Report - Run : $todaysdatetime" myemailaddress@gmail.com < /home/agarwaldvk/serverbackupjoboutput.txt

```

The output email notification looks something like so (The  first line has been highlighted for emphasis only) :-

```

[SIZE=3][COLOR="#800000"]The server would be shutdown at the completion of the backup job![/COLOR][/SIZE]

backup2l v1.5 by Gundolf Kiefer

Thu Jan  5 18:50:01 AEDT 2017

Running pre-backup procedure...
  pre-backup: nothing to do

Removing old backups...

Preparing differential level-1 backup <all.33> based on <all.32>...
  0 / 58 file(s), 0 / 14 dir(s), 0 B / 86.9MB (uncompressed)
  skipping: 0 file(s), 0 dir(s), 0 B (uncompressed)

Creating archive using 'DRIVER_TAR_GZ'...
Checking TOC of archive file (< real file, > archive entry)...
Creating check file for <all.33>...

Running post-backup procedure...
  post-backup: nothing to do

Thu Jan  5 18:50:01 AEDT 2017


Summary
=======

Backup       Date       Time  |  Size   | Skipped  Files+D |  New  Obs. | Err.
------------------------------------------------------------------------------
all.1        2017-01-03 19:20 |   86.3M |       0       72 |   72     0 |    0
all.11       2017-01-03 19:30 |      1K |       0       72 |    0     0 |    0
all.12       2017-01-03 19:40 |      1K |       0       72 |    0     0 |    0
all.13       2017-01-03 19:50 |      1K |       0       72 |    0     0 |    0
all.14       2017-01-03 20:05 |      1K |       0       72 |    0     0 |    0
all.15       2017-01-04 07:36 |      1K |       0       72 |    0     0 |    0
all.16       2017-01-04 09:45 |      1K |       0       72 |    0     0 |    0
all.2        2017-01-04 10:10 |   86.3M |       0       72 |   72     0 |    0
all.21       2017-01-05 07:36 |      1K |       0       72 |    0     0 |    0
all.22       2017-01-05 18:10 |      1K |       0       72 |    0     0 |    0
all.23       2017-01-05 18:15 |      1K |       0       72 |    0     0 |    0
all.24       2017-01-05 18:20 |      1K |       0       72 |    0     0 |    0
all.25       2017-01-05 18:25 |      1K |       0       72 |    0     0 |    0
all.26       2017-01-05 18:30 |      1K |       0       72 |    0     0 |    0
all.3        2017-01-05 18:35 |   86.3M |       0       72 |   72     0 |    0
all.31       2017-01-05 18:40 |      1K |       0       72 |    0     0 |    0
all.32       2017-01-05 18:45 |      1K |       0       72 |    0     0 |    0
all.33       2017-01-05 18:50 |      1K |       0       72 |    0     0 |    0

Filesystem      Size  Used Avail Use% Mounted on
/dev/sdd1       1.8T  327M  1.7T   1% /sharedfiles/backupdata

```

So thanks again everyone who helped me get there!


Best regards


Deepak

---

