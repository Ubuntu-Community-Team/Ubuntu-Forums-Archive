---
title: "Ubuntuzilla is having a problem"
date: 2009-04-07
forum: Ubuntuzilla
---

### Post by Baasha on 2009-04-07
Hi, I installed Ubuntuzilla a couple of days ago. I wasn't expecting anything to happen for a while since I already have the latest versions of TB and FF.  But now, each time I boot up I get a window at the bottom of the screen that says:

Ubuntuzilla: Firefox Update Available
A Firefox Update is Available. The version
you are running is /bin/sh: firefox: not
found. The new release available is 3.0.8.
Please refer to these detailed update
instructions.

Since I already have vs. 3.0.8 I thought, ok it's probably just because this is the first time Ubuntuzilla has tried to do its thing. So I clicked on the link for the update instructions but all I get is a blank screen.  How do I go about setting Ubuntuzilla straight?  I also noticed that the check for updates in each program is greyed out, in case that has any bearing on this problem.

---

### Post by nanotube on 2009-04-08
Hi,

can you run the checkforupdates manually, from a terminal, and see what it says?

ubuntuzilla.py -p firefox -a checkforupdategui

from the message it appears that it cannot find the firefox executable...

---

### Post by Baasha on 2009-04-08
Hi,
It says much the same as the message in the window:

bob@ubuntu:~$ ubuntuzilla.py -p firefox -a checkforupdategui
Retrieving the version of the latest release of Firefox from the Mozilla website...
Latest release version of Firefox : 3.0.8
Currently installed version of Firefox : /bin/sh: firefox: not found

I checked, and the message is right; there is no Firefox in my bin directory.  But I am running Firefox as I write, so it is there somewhere.  Before installing Ubuntuzilla I was running Firefox as the normal program installed by the repositories.  So how do I correct this problem?

---

### Post by nanotube on 2009-04-08
what does command "whereis firefox" say?

---

### Post by Baasha on 2009-04-08
> **nanotube said:**
> what does command "whereis firefox" say?

bob@ubuntu:~$ whereis firefox
firefox: /usr/bin/firefox.ubuntu /etc/firefox /usr/lib/firefox /usr/share/firefox

That is a neat command that I didn't know about.  Now that we know where it is, do I need to alter the Ubuntuzilla program to match?  If so, exactly what do I do to accomplish that?

---

### Post by nanotube on 2009-04-11
Hi,
It looks like there's no /usr/bin/firefox, where it should be.
so... it seems that the ubuntuzilla installation process did not complete successfully (because if it had, there would be a "/usr/bin/firefox").

when you ran ubuntuzilla to install firefox, did it say "firefox installation completed successfully" or a message to that effect?

you are probably running the firefox.ubuntu, which is the repositories version.

could you try exiting firefox completely, then run ubuntuzilla to install firefox again? (and make sure to save the entire output of ubuntuzilla, just in case something goes wrong you can post it here for me to look at?)

---

