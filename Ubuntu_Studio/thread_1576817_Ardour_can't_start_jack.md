---
title: "Ardour can't start jack"
date: 2010-09-17
forum: Ubuntu Studio
---

### Post by jeffdunn on 2010-09-17
I just installed ardour (jack came with it). When I try to start ardour for the first time I get a message saying
") You requested audio parameters that are not supported..
2) JACK is running as another user.
"
If I try to start jack I get this message
" p, li { white-space: pre-wrap; }Could not connect to JACK server as client. - Overall operation failed.
 - Unable to connect to server.
 Please check the messages window for more info."


This is what I get in the message window.
19:08:23.218 Patchbay deactivated.
19:08:23.220 Statistics reset.
19:08:23.409 ALSA connection graph change.
19:08:23.605 ALSA connection change.
19:08:24.468 Startup script...
19:08:24.469 artsshell -q terminate
sh: artsshell: not found
19:08:24.872 Startup script terminated with exit status=32512.
19:08:24.873 JACK is starting...
19:08:24.873 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
19:08:24.884 JACK was started with PID=9984.
Your system has an audio group, but you are not a member of it.
Please add yourself to the audio group by executing (as root):
  usermod -a -G audio (null)
After applying these changes, please re-login in order for them to take effect.
You don't appear to have a sane system configuration. It is very likely that you
encounter xruns. Please apply all the above mentioned changes and start jack again!
19:08:24.903 JACK was stopped with exit status=255.
19:08:24.904 Post-shutdown script...
19:08:24.905 killall jackd
jackd: no process found
19:08:25.316 Post-shutdown script terminated with exit status=256.
19:08:27.015 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.


When I try to run 'sudo usermod -a -G (null)', I get this message:


jeff@jeff-desktop:~$ sudo usermod -a -G (null)
bash: syntax error near unexpected token `('



I'm stuck, please help.

---

### Post by Pablo_F on 2010-09-18
Hi, 

If you are in lucid, did you give your user the privileges for rtprio and memlock when jackd was installed?

If you did not, do it now with:

sudo dpkg-reconfigure -p high jackd

To add your user to the audio group you need:

sudo usermod -a -G jeff

And reboot

Cheers! Pablo

---

### Post by jeffdunn on 2010-09-18
I tried your advice Pablo, (I am in Lucid)
sudo dpkg-reconfigure -p high jackd
sudo usermod -a -G jeff

, however, I am still getting exactly the same messages (after rebooting).

I just looked at System>Administration>Users and Groups. I see that there is an audio group and I am a member of it.

I'm very confused. Any other thoughts?
Cheers,
Jeff

---

### Post by Pablo_F on 2010-09-18
Oh sorry, I must have given you the wrong command. 

Check what groups jeff user is in with:

groups


EDIT:

Oh, the right usermod command should have been:

sudo usermod -a -G audio jeff

you also can do (I normally use this):

sudo adduser jeff audio

And reboot.

Sorry!

Cheers! Pablo

---

### Post by AutoStatic on 2010-09-18
> 2) JACK is running as another user.
That's probably the cause of the error, you're running either JACK or Ardour as another user.

---

### Post by Pablo_F on 2010-09-18
I think that he just have to add himself to the audio group and he is done. I gave him the wrong command, sorry. Jack is already running for him I hope.

Cheers Auto! ):P

---

