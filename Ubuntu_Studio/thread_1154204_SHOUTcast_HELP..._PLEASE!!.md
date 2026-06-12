---
title: "SHOUTcast HELP... PLEASE?!!?"
date: 2009-05-09
forum: Ubuntu Studio
---

### Post by higashi on 2009-05-09
I've followed so many tutorials trying to broadcast an internet radiostatio with absolutely no success. I have no idea what im doing and i'm getting extremely frustrated with it.

Can someone PLEASE provide me with a tutorial that a complete newb such as myself can follow without having any problems??

I would like a control thing that would allow me to talk when i want, play my music, and accept calls from skype.

Please help  :(

---

### Post by pastalavista on 2009-05-09
Still at it, eh? Well I've done some checking for you and I know now why my son stopped messing with it. [This page]("http://www.boutell.com/newfaq/creating/broadcastlive.html") explains that you need to have a seperate server. Live365 is the only free way they mention. Hope you figure it all out...good-luck

---

### Post by higashi on 2009-05-09
mkay, i akshully got a shoutcast server up tho.. now i just need to find something to allow me to broadcast.

Whenever i try to run  Internet DJ Console, i get a message saying it couldn't connect to JACK... So i then went Applications > Sound & Video > JACK control  and i clicked Start to start the JACK server. When i do this, i get an error message saying
> 16:16:03.544 Patchbay deactivated.
16:16:03.547 Statistics reset.
16:16:03.907 ALSA connection graph change.
16:16:04.102 ALSA connection change.
16:16:05.396 Startup script...
16:16:05.398 artsshell -q terminate
sh: artsshell: not found
16:16:05.800 Startup script terminated with exit status=32512.
16:16:05.806 JACK is starting...
16:16:05.807 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2
16:16:05.813 JACK was started with PID=30323.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1211795776, from thread -1211795776] (1: Operation not permitted)
cannot create engine
16:16:06.247 JACK was stopped successfully.
16:16:06.248 Post-shutdown script...
16:16:06.249 killall jackd
jackd: no process killed
16:16:06.672 Post-shutdown script terminated with exit status=256.
16:16:07.935 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

How can i fix the JACK server?

---

### Post by higashi on 2009-05-09
Nevermind, fixed that. Now i'm having a different problem with idjc...

When i tried opening it, a pop up asked which profile to use, i clicked default and then OK, and then the pop up closed and nothing else opened.
I tried running it in a terminal, got no errors. This is what it said:

> me@my-desktop:~$ idjc
Compromise language match found en_GB
Internet DJ Console Version 0.7.7
Copyright 2005-2008 Stephen Fairchild
Released under the GNU General Public License V3.0

Language translation: en_GB
/usr/lib/python2.5/site-packages/idjcgui.py:1565: DeprecationWarning: os.popen2 is deprecated.  Use the subprocess module.
  self.mixer_ctrl, self.mixer_rply = os.popen2([ libexecdir + "idjcmixer" ], 4096)
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/idjcgui.py", line 2360, in <module>
    run_instance = MainWindow()
  File "/usr/lib/python2.5/site-packages/idjcgui.py", line 1731, in __init__
    self.mic_select = nice_mic_togglebutton()
  File "/usr/lib/python2.5/site-packages/idjcgui.py", line 225, in __init__
    gtk.ToggleButton.__init__(self, label, use_underline)
RuntimeError: more argument specifiers than keyword list entries (remaining format:'):GtkToggleButton.__init__')
me@my-desktop:~$ Mixer module has closed


Why did it close? how can i keep it open and actually use it?

---

### Post by StephenF on 2009-05-09
> **higashi said:**
> Why did it close? how can i keep it open and actually use it?
You can't since this particular IDJC package doesn't work with the latest Ubuntu.

---

### Post by higashi on 2009-05-10
> **StephenF said:**
> You can't since this particular IDJC package doesn't work with the latest Ubuntu.

...................DAMN!
-sigh-  so much for internet radio. -.-

---

### Post by bobince on 2009-05-10
The version of idjc included with Ubuntu has always been useless for streaming to SHOUTcast servers anyway, because it's compiled without MP3 support. You'll need to compile your own idjc, which isn't hard: see Stephen's post and the further comments in [this thread](http://ubuntuforums.org/showthread.php?t=820058).

Piping Skype into JACK to do on-air interviews is a little bit more work. See the comments in [this thread](http://ubuntuforums.org/showthread.php?t=577914).

---

### Post by higashi on 2009-05-12
Thanks, bobince, i'll check those threads out when i get a chance.

Can anyone recommend anything better than idjc?

---

