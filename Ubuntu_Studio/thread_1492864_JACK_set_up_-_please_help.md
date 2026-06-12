---
title: "JACK set up - please help"
date: 2010-05-25
forum: Ubuntu Studio
---

### Post by ferucci on 2010-05-25
hi!
for hours im trying to set up JACK.Since i have a integrated audio card  that is came with my laptop i would like to set up JACK only in playback  mode so that i can run some programs like Ardor and same...
i've been trying few options and i always get same message,I would be  very grateful if you would help me to solve this problem!
here is the message
 p, li { white-space: pre-wrap; }  [COLOR=#999999]13:15:37.726  Patchbay deactivated.[/COLOR]
 [COLOR=#999999]13:15:37.774 Statistics reset.[/COLOR]
 [COLOR=#66cc99]13:15:37.792 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]13:15:38.041 ALSA connection change.[/COLOR]
 [COLOR=#999999]13:16:30.887 Startup script...[/COLOR]
 [COLOR=#990099]13:16:30.888 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]13:16:31.289 Startup script terminated with exit  status=32512.[/COLOR]
 [COLOR=#999999]13:16:31.289 JACK is starting...[/COLOR]
 [COLOR=#990099]13:16:31.290 /usr/bin/jackd -P1 -p128 -t5000  -dalsa -dhw:0,1 -r44100 -p128 -n2 -P[/COLOR]
 [COLOR=#999999]13:16:31.293 JACK was started with PID=2228.[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben  Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK is running in realtime mode, but you are not allowed to use  realtime scheduling.
 Please check your /etc/security/limits.conf for the following lines
 and correct/add them:
   @audio          -       rtprio          100
   @audio          -       nice            -10
 After applying these changes, please re-login in order for them to take  effect.
 You don't appear to have a sane system configuration. It is very likely  that you
 encounter xruns. Please apply all the above mentioned changes and start  jack again!
 [COLOR=#999999]13:16:31.310 JACK was stopped with exit  status=255.[/COLOR]
 [COLOR=#999999]13:16:31.311 Post-shutdown script...[/COLOR]
 [COLOR=#990099]13:16:31.312 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]13:16:31.719 Post-shutdown script terminated with  exit status=256.[/COLOR]
 [COLOR=#ff0000]13:16:32.404 Could not connect to JACK server as  client. - Overall operation failed. - Unable to connect to server.  Please check the messages window for more info.[/COLOR]

---

### Post by psidrum on 2010-05-28
try changing your setting to Softmode instead of Realtime

---

### Post by sgx on 2010-05-29
At a fresh start, 
try from this command

jackd -d alsa -r 44100

then start ardour, and then Jack Control (qjackctl if started by command)

Cheers

---

### Post by zettberlin on 2010-05-30
Whell, the errormessage tells you that:

#> **ferucci said:**
> hi!
...
 JACK is running in realtime mode, but you are not allowed to use  realtime scheduling.
 Please check your /etc/security/limits.conf for the following lines
 and correct/add them:
   @audio          -       rtprio          100
   @audio          -       nice            -10
 After applying these changes, please re-login in order for them to take  effect.
 

the message is not perfectly correct though, do NOT put the nice-line into limits.conf, it is useless. But you NEED to set special memory access for jack so the 2 lines should be:
   @audio          -       rtprio          100
   @audio          -       memlock          unlimited


These 2 lines need to be at the end of limits.conf and before the line that says End of file. You need to run a texteditor as root to do that and you need to be in group audio
Unfortunately, the Ubuntu-Devs have chosen, to break this standard, that worked perfectly well now for years. They use another file to set up this.

Still the method to put these 2 lines into /etc/security/limits.conf should work.
With your cheapo-soundchip you should set periods/buffer at 3 instead of 2 and it should work OK with 512 frames/period.

Realtime should always be checked, soft-mode is useless, dont touch priority in qjackctl.

Good luck ;-)

---

