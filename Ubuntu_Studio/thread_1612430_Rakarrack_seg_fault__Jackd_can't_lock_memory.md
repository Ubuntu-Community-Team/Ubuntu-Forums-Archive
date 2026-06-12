---
title: "Rakarrack seg fault / Jackd can't lock memory"
date: 2010-11-03
forum: Ubuntu Studio
---

### Post by decomp on 2010-11-03
So, I haven't changed anything, or updated - I have installed a couple games. 

And now rakarrack won't start.

when started in terminal it gives:
```
fake@fake-laptop$ rakarrack

rakarrack 0.5.8_Equinox - Copyright (c) Josep Andreu - Ryan Billing - Douglas McClendon - Arnout Engelen
Try 'rakarrack --help' for command-line options.
Cannot lock down memory area (Cannot allocate memory)
Segmentation fault

```

So I looked at jack, and jack says this: 
```
21:51:27.191 Startup script...
21:51:27.192 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
21:51:27.595 Startup script terminated with exit status=32512.
21:51:27.595 JACK is starting...
21:51:27.596 /usr/bin/jackd -dalsa -r192000 -p512 -n3 -D -Chw:1 -Phw:0
21:51:27.600 JACK was started with PID=1979.
Cannot create thread 1 Operation not permitted
Cannot create thread 1 Operation not permitted
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
Cannot lock down memory area (Cannot allocate memory)
audio_reservation_init
Acquire audio card Audio1
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:1|512|3|192000|0|0|nomon|swmeter|-|32bit
Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xf4780000 irq 45
configuring for 192000Hz, period = 512 frames (2.7 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 3 periods for playback
Cannot use real-time scheduling (RR/10)(1: Operation not permitted)
AcquireSelfRealTime error
21:51:29.664 Server configuration saved to "/home/case/.jackdrc".
21:51:29.667 Statistics reset.
21:51:29.682 Client activated.
21:51:29.699 JACK connection change.
21:51:29.703 JACK connection graph change.
Cannot lock down memory area (Cannot allocate memory)

```

Now, jack has ALWAYS told me "Cannot lock down memory area (Cannot allocate memory)" but it hasn't been a problem. But all this stuff about
"Cannot use real-time scheduling (RR/10)(1: Operation not permitted)" is news to me. 

So I tried removing everything & reinstalling:
```
sudo apt-get remove --purge jackd jackd2 jackd2-firewire rakarrack 
```
and deleting jacks config file in /home/.jackdrc

But my setting still persist upon reinstall! Where is it keeping them!? :confused:

So, two questions:

1. whats going on with not being able to create 'threads' and rakarrack throwing a segfault?

2. How do I delete my jack config?

Thanks for reading!

Edit: I am part of group @audio and my /etc/security/limits.conf looks like this:

@audio - rtprio          99
@audio - nice -10
@audio - memlock unlimited

Also, other jack applications (ardour, hydrogen, fmit) are working normally.

---

### Post by sgx on 2010-11-03
jackd2-fireware 

typo in your uninstall command!

Rakarrack, qjackctl, and a jackd commandlines do not always
cooperate. Set qjackctl prefs to not automatically start
jackd. Craft a root jackd command that starts rakarrack, based
on the soundcard contents of the  >  from

Input devices >
Output devices >

If that works, you can try as a normal user, in case
there is a permissions conflict somewhere

I think rakarrack has a bug, where you should be able to
turn off its automatic startup of jackd from its prefs,
but it starts it anyway, and causes issues sometimes,
especially when its command is different from the one in

/home/user/.jackdrc

the text file created when using Save from qjackctl.

I wasted too much life on stupid config issues left by devs
who don't or can't cooperate, and record during root sessions.
Problems rarely occur. Happiness at 9.9 out of 10 :)

Cheers

---

### Post by cchhrriiss121212 on 2010-11-03
>  I am part of group @audio and my /etc/security/limits.conf looks like this
For 10.04 and above, the file has changed, from here[https://help.ubuntu.com/community/UbuntuStudioPreparation]("https://help.ubuntu.com/community/UbuntuStudioPreparation"):

> Since Ubuntu 10.04 the permissions to enable real time access for "audio" group users are set in the file /etc/security/limits.d/audio.conf. In versions prior to 10.04 these settings were done in /etc/security/limits.conf

---

### Post by Pablo_F on 2010-11-03
Hi, 

qjackctl configurations are saved in ~/.config/rncbc.org/QjackCtl.conf

On the other hand, you can check if your user has rtprio and memlock priviliges with:

ulimit -r -l

What login manager are you using?

Cheers! Pablo

---

### Post by decomp on 2010-11-04
sgx: good eye on the typo! but actually just a typo in the post, I got it right in the terminal :) So I ran both qjacktcl and rakarrack as root, and everything worked fine. I'm hoping for a more long term solution than that, but THANKS! at least I can keep playing.

cchhrriiss121212: ok, commented out the settings from /etc/security/limits.conf and moved them to /etc/security/limits.d/audio.conf. Logged out, logged back in, (also tried restart) and I get the same error from jack and rakarrack.

Pablo_F: thanks! deleted qjackctl settings, no change. ulimit reports:
```
$ ulimit -r -l
real-time priority              (-r) 0
max locked memory       (kbytes, -l) 64

```
Both before and after updating limits.d/audio.conf as suggested by cchhrriiss121212. That can't be right can it? My login manager is lxdm - I'm running lubuntu 10.10.

Edit: so did some googling and came across more threads involving this issue and your help pablo! 

after reading this thread [http://www.linuxmusicians.com/viewtopic.php?f=27&p=14713](http://www.linuxmusicians.com/viewtopic.php?f=27&p=14713)
I checked my /etc/pam.d/lxdm (which was already present) and it looks like this:
```

#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
auth    sufficient      pam_succeed_if.so user ingroup nopasswdlogin
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
session required        pam_limits.so
@include common-session
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
session optional        pam_gnome_keyring.so auto_start
@include common-password

```

Hmm. What do you reckon? 

And if the answer is 'bug lxde devs,' then I'm happy to file a bug report, but I'm still kind of confused as to what the bug in lxdm thats causing this actually is. something with permissions?

---

### Post by cchhrriiss121212 on 2010-11-04
I would double check that you are in the audio group based on that ulimit output. I just noticed in your earlier post you have:
 > I am part of group @audio
The group is just "audio" and not "@audio" which could be the source of your problems.

---

### Post by decomp on 2010-11-04
> **cchhrriiss121212 said:**
> I would double check that you are in the audio group based on that ulimit output. I just noticed in your earlier post you have:
 
The group is just "audio" and not "@audio" which could be the source of your problems.

good thinking, typos are the worst! but I think I've got it.

```
$ sudo adduser case audio
[sudo] password for case: 
The user `case' is already a member of `audio'
```

---

### Post by cchhrriiss121212 on 2010-11-04
OK but in the first post your username is fake, are you setting up multiple accounts?

---

### Post by Pablo_F on 2010-11-04
This is most probably a problem with the login manager. See [http://www.linuxmusicians.com/viewtopic.php?f=27&t=2979](http://www.linuxmusicians.com/viewtopic.php?f=27&t=2979)

It seems that José has solved it by installing slim even if slim gave this same problem in the recent past. Go figure. 

Cheers! Pablo.

---

### Post by transmogrifox on 2010-11-05
> **Pablo_F said:**
> This is most probably a problem with the login manager. See [http://www.linuxmusicians.com/viewtopic.php?f=27&t=2979](http://www.linuxmusicians.com/viewtopic.php?f=27&t=2979)

It seems that José has solved it by installing slim even if slim gave this same problem in the recent past. Go figure. 

Cheers! Pablo.

I prefer to avoid the login manager completely.  In your home folder .xinitrc put the components you want to start with startx from the terminal at login. I think openbox by itself without other things that come with LXDE is more than enough for my needs.  I use openbox and xfce4-panel, and that is an acceptable combination for me...actually more feature-rich than LXDE, but seems xfce4-panel is not as bad on resources as xfce4-desktop.  

If you must, then also try gdm or kdm.  Just my 2C.

---

### Post by decomp on 2010-11-06
replaced lxdm with slim. it didnt create a file for slim in /etc/pam.d/slim. so I copied my lxdm one and renamed it. when I start qjack ctl i get:

```
16:54:42.142 /usr/bin/jackd -dalsa -r192000 -p512 -n3 -D -Chw:0 -Phw:0
16:54:42.144 JACK was started with PID=1956.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|512|3|192000|0|0|nomon|swmeter|-|32bit
Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xf4780000 irq 46
configuring for 192000Hz, period = 512 frames (2.7 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 3 periods for playback
16:54:44.339 Server configuration saved to "/home/case/.jackdrc".
16:54:44.340 Statistics reset.
16:54:44.356 Client activated.
16:54:44.370 JACK connection change.
16:54:44.376 JACK connection graph change.
```

So that all looks good. try to start rakarrack: segmentation fault
qjackctl and rakkarack both work fine as sudo.

:shrug:

Maybe I'll try your suggestion transmogrifox

Edit:

Disabled slim with sudo /etc/init.d/slim stop and started lubuntu using startx. also tried rebooting & using startx. same result as with slim. in qjackctl everything looks fine, but I'm still getting a segfault in rakarrack unless it's all sudo. guess it's time to file a bug report?

---

### Post by AutoStatic on 2010-11-06
The segfault probably comes from an old rakarrack config file. Rename *~/.fltk/rakarrack.sf.net* and try again.

---

### Post by AutoStatic on 2010-11-06
> **transmogrifox said:**
> I prefer to avoid the login manager completely.  In your home folder .xinitrc put the components you want to start with startx from the terminal at login. I think openbox by itself without other things that come with LXDE is more than enough for my needs.  I use openbox and xfce4-panel, and that is an acceptable combination for me...actually more feature-rich than LXDE, but seems xfce4-panel is not as bad on resources as xfce4-desktop.Never thought about that actually, disabling the login manager alltogether. Saves another service from being started up. Thanks for the tip!

---

### Post by decomp on 2010-11-06
> **AutoStatic said:**
> The segfault probably comes from an old rakarrack config file. Rename *~/.fltk/rakarrack.sf.net* and try again.

yea I tried deleting the config file in that folder and then ended up just deleting the whole folder. still segfaulting. It's probably a dumb user error, but I can't think of what it is.

---

### Post by alexan on 2010-11-23
same problem there.
Its the bug report already made? where's the link (usually there's temporary fix in there)?

---

### Post by decomp on 2010-11-26
I haven't filed a bug report b/c I'm still not sure what's causing it. But I posted in the rakarrack help forums [here]("http://sourceforge.net/projects/rakarrack/forums/forum/778862/topic/3931285") and a fix was suggested. I am lazy so I haven't tried that and I've just been running everything as root as suggested by sgx :)

---

