---
title: "JACK setup"
date: 2010-03-18
forum: Ubuntu Studio
---

### Post by bikodog on 2010-03-18
I have been using ubuntu exclusively for years now, and by no means consider myself a noob; however i am consistently perplexed by the setup of JACK. I have tried on numerous occasions with no success. There are lots of threads, howtos, etc out there, but none seem to fit together for me as a solution.

So, this time I am calling on the community to help me walk through the setup. I dont care if it takes weeks or months to get through this, but I really want to solve my problem for good. Hopefully as we start walking through this from scratch, many others who have had the same problems will learn from the process.

My ultimate objective is to use rosegarden, hydrogen, audacity, etc to sync up my various midi instruments and digital recorders. At this point I am not interested in soft-synths etc (those will follow once everything else is working).

I have installed ubuntu-studio a few times; but I get the same results. That's as well because I'm not a fan of one-size-fits-all solutions. My challenge is to install each component individually because i do not want to forego the learning experience.

The first item that needs to be solved is getting qjackctl to start without super user privileges.

When starting qjackctl in terminal i get the following:

```
ej-studio@ej-studio:~$ qjackctl
Connection failure: Connection refused
Suspending PulseAudio
Connection failure: Connection refused
```

Followed by this error msg:

```
Could not connect to JACK server as client.
- Overall operation failed.
- Unable to connect to server.
Please check the messages window for more info.
```

So after canceling that msg, here's the jack output:

```
12:40:20.788 Patchbay deactivated.
12:40:20.791 Statistics reset.
12:40:20.880 ALSA connection graph change.
12:41:55.186 Startup script...
12:41:55.187 artsshell -q terminate
sh: artsshell: not found
12:41:55.589 Startup script terminated with exit status=32512.
12:41:55.589 JACK is starting...
12:41:55.590 /usr/bin/gksu /usr/bin/jackd -R -dalsa -r44100 -p64 -n3 -D -Chw:0 -Phw:0 -m
12:41:55.595 JACK was started with PID=5085.
/usr/bin/gksu: invalid option -- 'R'
GKsu version 2.0.2
Usage: /usr/bin/gksu [-u <user>] [options] <command>
  --debug, -d
    Print information on the screen that might be
    useful for diagnosing and/or solving problems.
  --user <user>, -u <user>
    Call <command> as the specified user.
  --disable-grab, -g
    Disable the "locking" of the keyboard, mouse,
    and focus done by the program when asking for
    password.
  --prompt, -P
    Ask the user if they want to have their keyboard
    and mouse grabbed before doing so.
  --preserve-env, -k
    Preserve the current environments, does not set $HOME
    nor $PATH, for example.
  --login, -l
    Make this a login shell. Beware this may cause
    problems with the Xauthority magic. Run xhost
    to allow the target user to open windows on your
    display!
  --description <description|file>, -D <description|file>
    Provide a descriptive name for the command to
    be used in the default message, making it nicer.
    You can also provide the absolute path for a
    .desktop file. The Name key for will be used in
    this case.
  --message <message>, -m <message>
    Replace the standard message shown to ask for
    password for the argument passed to the option.
    Only use this if --description does not suffice.
  --print-pass, -p
    Ask gksu to print the password to stdout, just
    like ssh-askpass. Useful to use in scripts with
    programs that accept receiving the password on
    stdin.
  --sudo-mode, -S
    Make GKSu use sudo instead of su, as if it had been
    run as "gksudo".
  --su-mode, -w
    Make GKSu use su, instead of using libgksu's
    default.
12:41:55.658 JACK was stopped successfully.
12:41:55.659 Post-shutdown script...
12:41:55.659 killall jackd
12:41:55.792 ALSA connection change.
jackd: no process killed
12:41:56.066 Post-shutdown script terminated with exit status=256.
12:41:57.798 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```


That didn't work, so I close JACK and restart using super user:

```
ej-studio@ej-studio:~$ gksu qjackctl
Suspending PulseAudio
Connection failure: Connection refused
```

...and here's the JACK window output:

```
12:46:02.280 Patchbay deactivated.
12:46:02.283 Statistics reset.
12:46:02.294 ALSA connection graph change.
12:46:02.491 ALSA connection change.
12:46:16.368 Startup script...
12:46:16.369 artsshell -q terminate
sh: artsshell: not found
12:46:16.771 Startup script terminated with exit status=32512.
12:46:16.771 JACK is starting...
12:46:16.772 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2
12:46:16.776 JACK was started with PID=5133.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
Enhanced3DNow! detected
SSE2 detected
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
12:46:18.792 Server configuration saved to "/root/.jackdrc".
12:46:18.793 Statistics reset.
12:46:18.820 Client activated.
12:46:18.821 JACK connection change.
12:46:18.830 JACK connection graph change.
Enhanced3DNow! detected
SSE2 detected
```

So the first thing i need is this...how do I set qjackctl so that it will launch without granting super user privileges?

---

### Post by AutoStatic on 2010-03-18
> **bikodog said:**
> 
```
ej-studio@ej-studio:~$ qjackctl
Connection failure: Connection refused
Suspending PulseAudio
Connection failure: Connection refused
```Hello bikodog, which version of Ubuntu is this about? If it's Jaunty or Karmic then PulseAudio should suspend without problems. Did you modify something in the configuration of PulseAudio?

> **bikodog said:**
> 12:41:55.590 /usr/bin/gksu /usr/bin/jackd -R -dalsa -r44100 -p64 -n3 -D -Chw:0 -Phw:0 -m
12:41:55.595 JACK was started with PID=5085.
/usr/bin/gksu: invalid option -- 'R'You shouldn't run jackd as root so its best to remove the /usr/bin/gksu part. That's where part of your problems comes from.
And what does **ls -al ~/.jackdrc** and **ls -al ~/.config/rncbc.org/** in a terminal output?

---

### Post by bikodog on 2010-03-18
hello AutoStatic

Thanks for the quick reply.

> which version of Ubuntu is this about? If it's Jaunty or Karmic then PulseAudio should suspend without problems. Did you modify something in the configuration of PulseAudio?

Jaunty 9.04 - but I have installed various ubuntu's over the past few years from hardy through karmic; each time my /home partition is unchanged. I am suspecting some settings are jumbled up over the repeated attempts to get this going. Jaunty is my preferred version.

output

```
ej-studio@ej-studio:~$ ls -al ~/.jackdrc
ls: cannot access /home/ej-studio/.jackdrc: No such file or directory

```

```
ej-studio@ej-studio:~$ ls -al ~/.config/rncbc.org/
total 16
drwxr-xr-x  2 ej-studio ej-studio 4096 2009-09-25 22:52 .
drwxr-xr-x 32 ej-studio ej-studio 4096 2010-02-20 17:56 ..
-rw-r--r--  1 ej-studio ej-studio 3779 2010-03-18 16:16 QjackCtl.conf
-rw-r--r--  1 ej-studio ej-studio 4027 2009-09-25 23:33 Qtractor.conf

```

---

### Post by AutoStatic on 2010-03-19
Output looks good. Maybe it helps to rename your */home/ej-studio/.pulse/* directory to something like */home/ej-studio/.pulse.orig/*
What does **pasuspender -- qjackctl.bin** in a terminal do?

---

### Post by bikodog on 2010-03-19
hey autostatic.

output is the same after renaming .pulse.orig and usint pasuspender -- qjacktl.bin

Where can I find the script that launces qjackctl?

---

### Post by AutoStatic on 2010-03-20
That's weird. Could you try creating the file */home/ej-studio/.pulse/client.conf* with a single line:
```
autospawn = no
```

And then open a terminal, enter **pulseaudio -k** followed by **qjackctl.bin**. This should work. The full path to the QjackCtl wrapper script is */usr/bin/qjackctl*.

---

### Post by raboofje on 2010-03-20
> **AutoStatic said:**
> You shouldn't run jackd as root so its best to remove the /usr/bin/gksu part.

This is indeed part of the problem - have you found out where this comes from yet?

The 'Server' setting in ~/.config/rncbc.org/QjackCtl.conf perhaps?

---

