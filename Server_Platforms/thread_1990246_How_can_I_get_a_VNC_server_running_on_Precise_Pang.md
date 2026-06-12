---
title: "How can I get a VNC server running on Precise Pangolin Server 12.04?"
date: 2012-05-29
forum: Server Platforms
---

### Post by zigmoo on 2012-05-29
Hello All,

How can I get a proper VNC server running on Ubuntu Server (Precise Pangolin 12.04)?
I just upgraded my linode Ubuntu Server 10.04/kernel 2.6 to 12.04/kernel 3.x

I followed the directions to install this server for Precise Pangolin here: [http://j.mp/JK9smq](http://j.mp/JK9smq)
I get the following errors in my vnc4server log when I start the VNC server.
I've already downgraded my libxfont1 to 1:1.4.4-1

Am I trying to use the wrong VNC server? 

Thanks in advance for any help,

moo
@zigmoo

=====================================
moo@kargath:~$ cat  /home/moo/.vnc/kargath:1.log

Xvnc Free Edition 4.1.1 - built Feb  5 2012 20:06:55
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
Underlying X server release 40300000, The XFree86 Project, Inc


Tue May 29 02:30:26 2012
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      created VNC server for screen 0
error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Speedo/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/misc/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/75dpi/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/100dpi/, removing from list!
Could not init font path element /usr/share/fonts/X11/misc/, removing from list!
Could not init font path element /usr/share/fonts/X11/Type1/, removing from list!
Could not init font path element /usr/share/fonts/X11/75dpi/, removing from list!
Could not init font path element /usr/share/fonts/X11/100dpi/, removing from list!

Fatal server error:
could not open default font 'fixed'
xsetroot:  unable to open display 'kargath:1'
vncconfig: unable to open display "kargath:1"

** (gnome-session:3893): WARNING **: Cannot open display: 

================================
Current Installed Version of libxfont1
------------------------------------
moo@kargath:~$ apt-cache policy libxfont1
libxfont1:
  Installed: 1:1.4.4-1
  Candidate: 1:1.4.4-1
  Version table:
 *** 1:1.4.4-1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main i386 Packages
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main i386 Packages
        100 /var/lib/dpkg/status

---

### Post by zigmoo on 2012-06-01
Should I be trying to use a different VNC server?

---

### Post by Jose Catre-Vandis on 2012-06-01
Presumably you have X installed and a desktop working?

If so try:

```
sudo apt-get install vino
```
```
vino-preferences
``` tick preferences as required
Add the following to autostart applications
```
usr/lib/vino/vino-server
```
reboot

---

### Post by tbrminsanity on 2012-06-01
Good day,

I'm having an issue with my VNC connection.  Every VNC client I use to connect to my Ubuntu box (12.04) only gives me a snapshot of my desktop.  Any transactions I perform won't show.  I effectively have to kill my VNC connection and re-connect to see the change.

Example:
* I select the Firefox icon on my launcher
* Re-connect session
* I can now see Firefox, I select the bookmark for the Ubuntu forums
* Re-connect session
* I can now see the Ubuntu forums in Firefox, I select the username box and enter in my user name (but I can't see it on the screen), and then do the same for my password and press login.
* Re-connect session
* I now see myself logged into the Ubuntu forms
... Continue this madness till I've finished working on my Ubuntu box :-x

---

### Post by zigmoo on 2012-06-01
This is a linode cloud server, so I can't see the GUI until I'm able to login to it with VNC.

sudo apt-get install vino says that I already have the newest version, and I installed ubuntu-desktop.

When I run vino-preferences, I get:
(vino-preferences:4327): Gtk-WARNING **: cannot open display: 

Thanks very much for your help!

moo

> **Jose Catre-Vandis said:**
> Presumably you have X installed and a desktop working?

If so try:

```
sudo apt-get install vino
```
```
vino-preferences
``` tick preferences as required
Add the following to autostart applications
```
usr/lib/vino/vino-server
```
reboot

---

### Post by arrrghhh on 2012-06-01
> **zigmoo said:**
> This is a linode cloud server, so I can't see the GUI until I'm able to login to it with VNC.

sudo apt-get install vino says that I already have the newest version, and I installed ubuntu-desktop.


Why are you guys putting VNC on Ubuntu Server?

Just install Ubuntu Desktop and be done - it ships with a RDP-like version of VNC (the previously mentioned 'Vino').

The Server edition doesn't come with a DE, GUI, or any of that stuff - so putting VNC on it doesn't make a whole lot of sense!

Edit - just saw your post.  You installed the ubuntu-desktop package ON TOP of Ubuntu Server...

Again, why not just install Ubuntu Desktop?  You've effectively done just that!

---

### Post by Jose Catre-Vandis on 2012-06-01
> **zigmoo said:**
> This is a linode cloud server, so I can't see the GUI until I'm able to login to it with VNC.

sudo apt-get install vino says that I already have the newest version, and I installed ubuntu-desktop.

When I run vino-preferences, I get:
(vino-preferences:4327): Gtk-WARNING **: cannot open display: 

Thanks very much for your help!

moo

You'll need to be on the server to do this, with GUI running. :(

Can you ssh into your cloud server?
```
ssh -Y [email]name@ipaddy.com[/email]
```
You can then run vino-preferences on your linux machine?

---

### Post by CharlesA on 2012-06-01
> **arrrghhh said:**
> Why are you guys putting VNC on Ubuntu Server?

Just install Ubuntu Desktop and be done - it ships with a RDP-like version of VNC (the previously mentioned 'Vino').

The Server edition doesn't come with a DE, GUI, or any of that stuff - so putting VNC on it doesn't make a whole lot of sense!

Edit - just saw your post.  You installed the ubuntu-desktop package ON TOP of Ubuntu Server...

Again, why not just install Ubuntu Desktop?  You've effectively done just that!
This whole thing.

If it's a VPS, just manage it via SSH.

---

### Post by tbrminsanity on 2012-06-02
I am using vino to host my vnc connection.  It just isn't refreshing the screen for me.  Should I be connecting to my Ubuntu box via a RDC connection instead?

---

### Post by CharlesA on 2012-06-02
> **tbrminsanity said:**
> I am using vino to host my vnc connection.  It just isn't refreshing the screen for me.  Should I be connecting to my Ubuntu box via a RDC connection instead?
Turn off desktop effects and see what happens.

---

### Post by tbrminsanity on 2012-06-11
> **CharlesA said:**
> Turn off desktop effects and see what happens.

It kinda works.  The connection is very slow and my GUI ended up crashing.

---

### Post by arrrghhh on 2012-06-11
> **tbrminsanity said:**
> It kinda works.  The connection is very slow and my GUI ended up crashing.

As was previously stated, it's a VPS.  Why would you want to add more overhead and security holes - just manage it via SSH!

---

### Post by CharlesA on 2012-06-11
> **arrrghhh said:**
> As was previously stated, it's a VPS.  Why would you want to had more overhead and security holes - just manage it via SSH!
Yep. It is easier to forward X over SSH if you need to access something with a GUI too.

---

### Post by HermanAB on 2012-06-12
OK, since no-one gave the poor sod any examples, here is one:
$ ssh -X -C -c arcfour128 user@serveripaddress "gedit /etc/fstab"

So, you neither need VNC, nor a desktop environment on the server.  SSH has its own X server built right in, so you can run GUI programs remotely, transparently on your local desktop.

For more info, read the Snailbook:
[http://www.snailbook.com](http://www.snailbook.com)

If VNC is the answer, then you asked the wrong question.

---

### Post by cebrooks on 2012-06-28
Jose,
 
Can you tell me where exactly this file is please?
 
Add the following to autostart applications

Code:
/usr/lib/vino/vino-server

---

