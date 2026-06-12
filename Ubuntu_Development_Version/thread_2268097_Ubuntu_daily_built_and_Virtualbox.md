---
title: "Ubuntu daily built and Virtualbox"
date: 2015-03-06
forum: Ubuntu Development Version
---

### Post by jdeca57 on 2015-03-06
Hi all,
I encounter some strange behavior when I start Ubuntu 15.04 coming from the file vivid-desktop-amd64.iso: after installation it fails to login and hangs on the login screen. Host-F1 (Host is right ctrl) brings me to tty1 and there a login is possible. Immediately after the welcome message folown:
[  52.476484] systemd-logind[576]: failed to start user service: Unknown unit: [email]user@1000.servic[/email]e

I suppose that this message comes from the Graphic login because in the text console it seems to work and sudo apt-get update and upgrade give me the last updates.Shutdown works. But no joy, I can't get farther than the login screen for the GUI. And there is something wrong with the home directory of the user: it is rather empty, no Documents folder and so.
Last, /var/log/Xorg.0.log ends with
[   12.631] (EE) FBDEV(0): FBIOBLANK: Invalid argument
so I guess It's also an X problem. I gave 128 MB Graphic memory, no 3D

Are there known issues with Vivid-next and Virtualbox? On the same computer, Ubuntu Mate 15.04 works perfectly under VB.
Thanks in advance.

---

### Post by ajgreeny on 2015-03-06
Is the iso file you used today's or from an earlier date, and is this the standard Ubuntu using unity desktop or some other version?

I have Xubuntu 15.04 64bit running fully updated in VB and it is sweet as a nut, with no problems at all at the moment.

I installed it in the middle of December 2014, and so far it has been almost faultless, and certainly has had fewer problems in my experience than the pre-released version of trusty.

Can you login to cli and then run startx, or does that still not allow you to login to the GUI?

---

### Post by slickymaster on 2015-03-06
See this: [https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1359439](https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1359439)

---

### Post by rrnbtter on 2015-03-06
Greetings,
(In my experience) Virtual Box is a problem child for development versions.  It is usually corrected by Final Release or shortly afterward. I lost VBox with my install of kernel 4.0 (Unity Desktop). 
This section used to be termed by its users as "testing".
Testing doesn't work well without "updating" and installing new things.
Updating and installing new things creates "breakage". 
Many times there are "workarounds" often it is a "report" and "wait" situation. 
This is complicated by all of the different "buntu's" available. 

But you have been around since 2007 so you probably already know all of this. 
Just thought I would reinterate.:)

---

### Post by jdeca57 on 2015-03-06
> **ajgreeny said:**
> Is the iso file you used today's or from an earlier date, and is this the standard Ubuntu using unity desktop or some other version?

I have Xubuntu 15.04 64bit running fully updated in VB and it is sweet as a nut, with no problems at all at the moment.

I installed it in the middle of December 2014, and so far it has been almost faultless, and certainly has had fewer problems in my experience than the pre-released version of trusty.

Can you login to cli and then run startx, or does that still not allow you to login to the GUI?

The iso I used is yesterday's (march 5) and I tried the one of march 4 also (with zsync the download isn't a big issue). Since I found out that apt-get update/upgrade works this morning I didn't go for another download. The command is:

```
zsync http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/vivid-desktop-amd64.iso.zsync
```

And yes, other Ubuntu like mate beta1 works flawless. And now your last question: the GUI is frozen at the log screen, Host-F7 switches and Host-F1 goes back. startx gives this puzzling answer:

The program 'startx' is currently not installed. You can install it by typing: sudo apt-get install xinit

That leaves me competely at loss... why should I install xinit?

---

### Post by jdeca57 on 2015-03-06
> **rrnbtter said:**
> Greetings,
(In my experience) Virtual Box is a problem child for development versions.  It is usually corrected by Final Release or shortly afterward. I lost VBox with my install of kernel 4.0 (Unity Desktop). 
This section used to be termed by its users as "testing".
Testing doesn't work well without "updating" and installing new things.
Updating and installing new things creates "breakage". 
Many times there are "workarounds" often it is a "report" and "wait" situation. 
This is complicated by all of the different "buntu's" available. 

But you have been around since 2007 so you probably already know all of this. 
Just thought I would reinterate.:)

O yes, but since the beta of mate and xubuntu work reasonably well I assumed the main version was also almost getting there. I'm not expecting stable, only to get to the desktop and look around. We're already to the point where there is a feature freeze and a debian import freeze, and march 12 there is a user interface freeze. Perhaps I'll try it again at that point.

---

### Post by rrnbtter on 2015-03-06
Greetings,
Well! What do you know? a new Vbox update in this mornings updates!

   Job for virtualbox.service failed. See "systemctl status virtualbox.service" and "journalctl -xe" for details.
 invoke-rc.d: initscript virtualbox, action "restart" failed.
 Setting up virtualbox-qt (4.3.24-dfsg-1) ...
 Setting up virtualbox-dkms (4.3.24-dfsg-1) ...
 Loading new virtualbox-4.3.24 DKMS files...
 Building only for 4.0.0-040000rc2-generic
 Building initial module for 4.0.0-040000rc2-generic

VBox working fine now with 4.0 RC2 kernel. Also systemd and x-mir.
If you don't get it make sure you are using a fully updated server. 
This is really good response from Vbox. Thanks

---

