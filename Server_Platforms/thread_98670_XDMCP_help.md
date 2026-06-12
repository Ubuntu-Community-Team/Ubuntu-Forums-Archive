---
title: "XDMCP help"
date: 2005-12-03
forum: Server Platforms
---

### Post by UbuntUser4389 on 2005-12-03
I am trying to set up my computer as a terminal server. I have installed the LTSP software. I have run the "ltspadmin" program and installed all of the packages and configured everything! The only thing that isn't working is XDMCP, it says it's not even installed. How can that be?? I searched in synaptic for "xdmcp" and the xdmcp package (version 6 i believe) is installed. Why can't the LTSP software find XDMCP??

When I bring up the screen to view the services, everything is installed and running except XDMCP. I can't figure out why!

Thanks a TON for all of your help.

---

### Post by cactus on 2005-12-03
in gnome.. the easiest way to turn it on...
$ sudo gdmsetup

then...
go to "Security" tab
put a check mark in "enable xdmcp"
click newly ungreyed "XDMCP tab"
configure..
click close

enjoy.

---

### Post by UbuntUser4389 on 2005-12-03
I did what you said Cactus, and still no luck. The LTSP software is still saying that I don't have the XDMCP service installed. Now what??

---

### Post by cactus on 2005-12-04
hmm. i remember when i did that (ltsp install on centos), it never showed it..even though it was working just fine. I know it was working, because I had 50 users using it! lol

I suggest you try connecting to it from a remote gdm... if it works..gravy.

---

### Post by chrismyers on 2007-02-18
Found a fix:

Host machine:

1. Go to System » Administration » Login Window.

    Select tab Remote » Style: Same as Local

    Close the window

2. Open a terminal & type: sudo gedit /etc/X11/gdm/gdm.conf

    Now search for RemoteGreeter=/usr/lib/gdm/gdmlogin

    & uncomment this line.

3. Search for the [xdmcp] section & scroll a few lines down until you find Enable=False

    Change it to Enable=True

4. Save & reboot. Your host is sorted.

Client Machine

Enable the XDMCP option in the Terminal Server Client:

sudo apt-get install xnest

I hope this helps.

---

### Post by hortimech on 2007-02-19
how did you install LTSP? did you download it from the LTSP website? if so you have probably got the wrong version.
I tried LTSP and got exactly to the same point as you, I cured the problem by starting again and downloaded LTSP by apt-get, what you end up with is the LTSP from EDUBUNTU.

hortimech

---

