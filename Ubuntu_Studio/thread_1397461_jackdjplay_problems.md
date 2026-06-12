---
title: "jack/djplay problems"
date: 2010-02-03
forum: Ubuntu Studio
---

### Post by 3177 on 2010-02-03
Everytime ive opened up dj-play, it dissapears 2 seconds later. I then open jack config, check the message window and it gives me this:
 p, li { white-space: pre-wrap; }  [COLOR=#999999]10:08:49.215 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]10:08:49.370 Statistics reset.[/COLOR]
 [COLOR=#999999]10:08:49.428 Startup script...[/COLOR]
 [COLOR=#990099]10:08:49.429 artsshell -q terminate[/COLOR]
 [COLOR=#66CC99]10:08:49.437 ALSA connection graph change.[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]10:08:49.847 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]10:08:49.849 JACK is starting...[/COLOR]
 [COLOR=#990099]10:08:49.849 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p4096 -n3 -P[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
 Please check your /etc/security/limits.conf for the following lines
 and correct/add them:
   @audio          -       rtprio          100
   @audio          -       nice            -10
 After applying these changes, please re-login in order for them to take effect.
 You don't appear to have a sane system configuration. It is very likely that you
 encounter xruns. Please apply all the above mentioned changes and start jack again!
 [COLOR=#999999]10:08:49.913 JACK was started with PID=6286.[/COLOR]
 [COLOR=#999999]10:08:49.993 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#999999]10:08:49.994 Post-shutdown script...[/COLOR]
 [COLOR=#990099]10:08:49.995 killall jackd[/COLOR]
 [COLOR=#CCCC99]10:08:50.053 ALSA connection change.[/COLOR]
 jackd: no process found
 [COLOR=#999999]10:08:50.407 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]10:08:52.100 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]



[COLOR=#FF0000][/COLOR]
/etc/security/limits.conf says to edit it using dpkg-reconfigure -p high jackd, so I did.
I tried enabling and disabling realtime but neither works. 
Any suggestions?

---

### Post by cchhrriiss121212 on 2010-02-04
You can edit limits.conf using gedit:
```
sudo gedit /etc/security/limits.conf
```
I'm not sure whether you added the recommended audio group settings or not? If you did, what message does jack display when you open qjackcontrol and press start? It should be different than what you have displayed.
I would leave realtime unchecked unless you are using a realtime kernel.

---

### Post by AutoStatic on 2010-02-05
Hello 3177, you're running Lucid right? Maybe you could ask your question here: [http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

---

### Post by 3177 on 2010-02-05
> **cchhrriiss121212 said:**
> You can edit limits.conf using gedit:
```
sudo gedit /etc/security/limits.conf
```I'm not sure whether you added the recommended audio group settings or not? If you did, what message does jack display when you open qjackcontrol and press start? It should be different than what you have displayed.
I would leave realtime unchecked unless you are using a realtime kernel.


after pressing start on jack control there a pop up that reads: Could not connect to jack server as client.-overall operation failed-unable to connect to server. Check messages window for more info 
Messages window reads:

 p, li { white-space: pre-wrap; }  [COLOR=#999999]09:33:35.354 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]09:33:35.417 Statistics reset.[/COLOR]
 [COLOR=#999999]09:33:35.501 Startup script...[/COLOR]
 [COLOR=#990099]09:33:35.502 artsshell -q terminate[/COLOR]
 [COLOR=#66CC99]09:33:35.527 ALSA connection graph change.[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]09:33:36.144 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]09:33:36.145 JACK is starting...[/COLOR]
 [COLOR=#990099]09:33:36.146 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p4096 -n3 -P[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
 Please check your /etc/security/limits.conf for the following lines
 and correct/add them:
   @audio          -       rtprio          100
   @audio          -       nice            -10
 After applying these changes, please re-login in order for them to take effect.
 You don't appear to have a sane system configuration. It is very likely that you
 encounter xruns. Please apply all the above mentioned changes and start jack again!
 [COLOR=#999999]09:33:36.206 JACK was started with PID=2148.[/COLOR]
 [COLOR=#999999]09:33:36.274 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#999999]09:33:36.275 Post-shutdown script...[/COLOR]
 [COLOR=#990099]09:33:36.275 killall jackd[/COLOR]
 [COLOR=#CCCC99]09:33:36.361 ALSA connection change.[/COLOR]
 jackd: no process found
 [COLOR=#999999]09:33:36.703 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]09:33:38.375 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 [COLOR=#999999]09:33:42.923 Startup script...[/COLOR]
 [COLOR=#990099]09:33:42.925 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]09:33:43.327 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]09:33:43.328 JACK is starting...[/COLOR]
 [COLOR=#990099]09:33:43.328 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p4096 -n3 -P[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
 [COLOR=#999999]09:33:43.351 JACK was started with PID=2160.[/COLOR]
 Please check your /etc/security/limits.conf for the following lines
 and correct/add them:
   @audio          -       rtprio          100
   @audio          -       nice            -10
 After applying these changes, please re-login in order for them to take effect.
 You don't appear to have a sane system configuration. It is very likely that you
 encounter xruns. Please apply all the above mentioned changes and start jack again!
 [COLOR=#999999]09:33:43.373 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#999999]09:33:43.375 Post-shutdown script...[/COLOR]
 [COLOR=#990099]09:33:43.375 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]09:33:43.790 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]09:33:45.493 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]


I have disabled realtime via dpkg , but i did that was when i posted this thread.
when i use 
sudo gedit /etc/security/limits.conf  the file looked completely different than when i opened it with gedit by going through folders.
Im gonna post both .
Im also gonna post this problem following the link Autostatic posted.

---

### Post by 3177 on 2010-02-05
Okay the reason it looked different was because the last time i looked at the file was before i disabled realtime (Im pretty sure anyway). at any rate heres what my limits.cinf reads:  

# /etc/security/limits.conf
#
#Each line describes a limit for a user in the form:
#
#<domain>        <type>  <item>  <value>
#
#Where:
#<domain> can be:
#        - an user name
#        - a group name, with @group syntax
#        - the wildcard *, for default entry
#        - the wildcard %, can be also used with %group syntax,
#                 for maxlogin limit
#        - NOTE: group and wildcard limits are not applied to root.
#          To apply a limit to the root user, <domain> must be
#          the literal username root.
#
#<type> can have the two values:
#        - "soft" for enforcing the soft limits
#        - "hard" for enforcing hard limits
#
#<item> can be one of the following:
#        - core - limits the core file size (KB)
#        - data - max data size (KB)
#        - fsize - maximum filesize (KB)
#        - memlock - max locked-in-memory address space (KB)
#        - nofile - max number of open files
#        - rss - max resident set size (KB)
#        - stack - max stack size (KB)
#        - cpu - max CPU time (MIN)
#        - nproc - max number of processes
#        - as - address space limit (KB)
#        - maxlogins - max number of logins for this user
#        - maxsyslogins - max number of logins on the system
#        - priority - the priority to run user process with
#        - locks - max number of file locks the user can hold
#        - sigpending - max number of pending signals
#        - msgqueue - max memory used by POSIX message queues (bytes)
#        - nice - max nice priority allowed to raise to values: [-20, 19]
#        - rtprio - max realtime priority
#        - chroot - change root to directory (Debian-specific)
#
#<domain>      <type>  <item>         <value>
#

#*               soft    core            0
#root            hard    core            100000
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4

# End of file

i realize @audio isnt there
It WAS before i dissabled realtime via dkpg

---

### Post by cchhrriiss121212 on 2010-02-05
The way to enable/disable realtime in jack is by running qjackctl and using the setup options. It is listed first under parameters.
You shouldn't need to use any dpkg commands for any of this.
All you need to do is use the command I posted earlier and type in the 2 values shown in the jack message window, then save the file, and restart jack.

---

### Post by 3177 on 2010-02-05
> **cchhrriiss121212 said:**
> The way to enable/disable realtime in jack is by running qjackctl and using the setup options. It is listed first under parameters.
You shouldn't need to use any dpkg commands for any of this.
All you need to do is use the command I posted earlier and type in the 2 values shown in the jack message window, then save the file, and restart jack.


well.....

# /etc/security/limits.conf
#
#Each line describes a limit for a user in the form:
#
#<domain>        <type>  <item>  <value>
#
#Where:
#<domain> can be:
#        - an user name
#        - a group name, with @group syntax
#        - the wildcard *, for default entry
#        - the wildcard %, can be also used with %group syntax,
#                 for maxlogin limit
#        - NOTE: group and wildcard limits are not applied to root.
#          To apply a limit to the root user, <domain> must be
#          the literal username root.
#
#<type> can have the two values:
#        - "soft" for enforcing the soft limits
#        - "hard" for enforcing hard limits
#
#<item> can be one of the following:
#        - core - limits the core file size (KB)
#        - data - max data size (KB)
#        - fsize - maximum filesize (KB)
#        - memlock - max locked-in-memory address space (KB)
#        - nofile - max number of open files
#        - rss - max resident set size (KB)
#        - stack - max stack size (KB)
#        - cpu - max CPU time (MIN)
#        - nproc - max number of processes
#        - as - address space limit (KB)
#        - maxlogins - max number of logins for this user
#        - maxsyslogins - max number of logins on the system
#        - priority - the priority to run user process with
#        - locks - max number of file locks the user can hold
#        - sigpending - max number of pending signals
#        - msgqueue - max memory used by POSIX message queues (bytes)
#        - nice - max nice priority allowed to raise to values: [-20, 19]
#        - rtprio - max realtime priority
#        - chroot - change root to directory (Debian-specific)
#
#<domain>      <type>  <item>         <value>
#

#*               soft    core            0
#root            hard    core            100000
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4
#@audio          -       rtprio          100
#@audio          -       nice            -10

# End of file

still says what ive already posted when i restart. RT is off.
should it be on? i get the same when it is.

---

### Post by cchhrriiss121212 on 2010-02-05
# is used when you want the text to be ignored. Just remove the # from those 2 lines. The others shown are just examples.
You can also add:
@audio - memlock unlimited
which will allow audio applications to use as much memory as they need.

---

### Post by 3177 on 2010-02-05
thanks a lot

---

### Post by shanefiddle on 2012-01-06
Yes, thanks from my studio as well!  solved my problem perfectly.

---

