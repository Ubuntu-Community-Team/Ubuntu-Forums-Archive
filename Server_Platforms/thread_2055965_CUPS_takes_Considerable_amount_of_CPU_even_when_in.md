---
title: "CUPS takes Considerable amount of CPU even when in rest"
date: 2012-09-10
forum: Server Platforms
---

### Post by ninadpchaudhari on 2012-09-10
Just yesterday i installed the CUPSD and to my surprise, the cupsd takes up 100% CPU while startup :eek: 
i notice the CPU meter in LXDE task-bar showing constant 100% !!
from the top command i found it was cupsd that takes up so much CPU power !!
is there any way i can stop this ? 
As sometimes,  this takes up 100% even if the printer is off ...
casuses damn high temperature in CPU and causes the Server to shut down !
temperature monotor by lm-sensor packages sensors command

---

### Post by SeijiSensei on 2012-09-10
Something is definitely wrong with your configuration.  I have a relatively old server running cupsd.  The machine has been up over 136 days, and "ps ax | grep cups" reports a total of just 3 seconds of CPU time.

Maybe there's a connection problem of some kind between the server and the printer?  I could imagine some mismatch that leads to the server polling the printer continously and not getting the replies it is looking for.  That's just a guess, though.  Have you checked any of the support resources at [cups.org](http://www.cups.org/)?

---

### Post by ninadpchaudhari on 2012-09-10
Thanks SeijiSensei :KS for the suggestion , 
The
ps ax | grep cups command returned this : 
```

   533 ?        Rs    68:14 /usr/sbin/cupsd -F
 5270 pts/1    S+     0:00 grep --color=auto cups

```

I am not aware of how to study the output of the above mentioned command :rolleyes:

currently TOP gives 50% usage !!!!!!!
though, 
I just went thru the regular installation & config. of the cupsd.conf file ... 
Nothing special :eek: got the packages from the official Manufacturer : Brother MFC 295CN


Do you think i must try reinstalling the CUPSD ?

---

### Post by SeijiSensei on 2012-09-10
I'm running CentOS on my server; it doesn't use the "-F" option.  As a test, edit the contents of /etc/init/cups.conf and remove the "-F" from the end of the exec command about midway down that file.  Then use "sudo service cups restart" and see if that helps any.

What do you see in /var/log/cups, particularly /var/log/cups/error_log?

---

### Post by ninadpchaudhari on 2012-09-10
Damn  !! 

The cups/error_log says : 

```

E [10/Sep/2012:23:59:58 +0530] cupsdAuthorize: Empty Basic password!
E [10/Sep/2012:23:59:58 +0530] cupsdAuthorize: Empty Basic password!
E [10/Sep/2012:23:59:58 +0530] cupsdAuthorize: Empty Basic password!
E [10/Sep/2012:23:59:59 +0530] cupsdAuthorize: Empty Basic password!
E [10/Sep/2012:23:59:59 +0530] cupsdAuthorize: Empty Basic password!
E [10/Sep/2012:23:59:59 +0530] cupsdAuthorize: Empty Basic password!
E [10/Sep/2012:23:59:59 +0530] cupsdAuthorize: Empty Basic password!
E [11/Sep/2012:00:00:00 +0530] cupsdAuthorize: Empty Basic password!
E [11/Sep/2012:00:00:00 +0530] cupsdAuthorize: Empty Basic password!
E [11/Sep/2012:00:00:00 +0530] cupsdAuthorize: Empty Basic password!
E [11/Sep/2012:00:00:00 +0530] cupsdAuthorize: Empty Basic password!
E [11/Sep/2012:00:00:01 +0530] cupsdAuthorize: Empty Basic password!
E [11/Sep/2012:00:00:01 +0530] cupsdAuthorize: Empty Basic password!
E [11/Sep/2012:00:00:02 +0530] cupsdAuthorize: Empty Basic password!
E [11/Sep/2012:00:00:02 +0530] cupsdAuthorize: Empty Basic password!
E [11/Sep/2012:00:00:02 +0530] cupsdAuthorize: Empty Basic password!
E [11/Sep/2012:00:00:03 +0530] cupsdAuthorize: Empty Basic password!

```

Filed with Empty Basic password :D :D

What i tried now is 

**Allow all** in **<Location /admin/conf>** xD
now i get the output of ps ax as
```

  515 ?        Ss     0:00 /usr/sbin/cupsd -F
 1945 pts/0    S+     0:00 grep --color=auto cups

```
 + no Cups thing in the top list ;)

I think the problem is solved, but will add the SOLVED tag after a few days to see if this works fine !

Thanks a lot :KS SeijiSensei :KS  :) :) :) again !!!!

Btw,
 i did not find how to remove that -F ... Will that matter if runs in Foreground ? 
also, 
can you please explain what the digits mean in the ps ax command ? 
Manual i found :  ps - report a snapshot of the current processes.

---

### Post by SeijiSensei on 2012-09-10
No, leave it alone.  You've obviously found the real culprit.

If you just run "ps" without piping it through grep, you'll see column headers at the top of the list.  If you run "ps aux" you'll see these headers:

```

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND

```

The first column is the user running the process. Many of them will belong to root, but you'll also see processes belonging to ordinary users.  Then comes the "process ID," a number between 1 and 65535 assigned to the process by the operating system.  In a complete ps list you'll see a bunch of processes with low numbers, typically followed by a bunch with much larger numbers.  Those low-numbered processes were started at boot and are running continuously.  The higher numbers cycle around as programs are opened and closed.

The next two columns show the percent of CPU cycles the process is using at the moment, and the percent of memory it is using.  These are followed by a column for the "virtual" size of the program in memory and another figure representing the amount of memory used for just that instance of a program.  A good example would be the processes running /sbin/getty, which is a program that listens for input at the keyboard in text mode.  When Ubuntu starts up, getty spawns half-a-dozen terminals.  You can see them if you boot into safe mode and hit Alt-F1, Alt-F2, and the like.  On my machine the virtual size of these terminals is 4612 kBytes, but the RSS value for each is just 176.  That's because most of the code the individual terminals use is shared across all the instances, and just a small bit needs to be allocated to manage each one.  If you run server software like Apache, it will spawn multiple "listeners" to handle inbound web requests that have a unique memory image and collectively share a bunch of code as well.

The tty column indicates which terminal was used to start a program.  For most programs there is no terminal since they are started at boot by the system, not by a user.  The next column reports the process's status.  There are a bunch of status codes; read the manual using "man ps" to see a list.  

Finally there is a column that says when the process was started, followed by the amount of CPU time that process has consumed in minutes and seconds.  The last column gives the complete command used to start the process.  Sometimes that will be truncated because of the default output width, but you can add the "w" option to expand the width of the output.

---

