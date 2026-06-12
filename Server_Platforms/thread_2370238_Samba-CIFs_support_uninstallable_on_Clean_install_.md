---
title: "Samba-CIFs support uninstallable on Clean install of 17.04 server"
date: 2017-09-01
forum: Server Platforms
---

### Post by gbambo on 2017-09-01
A server that can't share files with the most widely deployed desktop OS in the world?

...

But how on Earth do I migrate from Windows to Linux without Samba-CIF's support? (I not saying it is not possible, I'm saying it a ridiculous constraint.)

The very first command I entered after installation of Ubuntu 17.04 was to install Samba. Numerous errors resulted, mainly focused on iSCSI being unstartable. 

     job for iscsid.service failed because of unavailable resources or another system error
     see systemctl status iscsid.service and journalctl -xe
     failed to start iSCSI initiator daemon
     errors were encountered while processing open-iscsi
     package cifs-utils is not ready for configuration
     iSCSI daemon with pid=20272 started!
     failed to start iSCSI initiator daemon


Are my components somehow problematic?

i7-950 Bloomfield quad hyperthreading 3.05ghz
2tb Sata3 x 2 Enterprise-grade
     HGST HUS724020ALA640
48gb DDR3-1600 running @ 1066 in 3 ch mode
Mobo = MSI A7522IMT v8.14b8  110912 <- BIOS vers
     model = MSI X58 Pro (released 2009)
MBR support only
1gbps Intel Pro/1000 GT

This machine just won't accept an Ubuntu install. Each fresh install from a newly downloaded installer from a different mirror has a different problem. That makes no sense to me. No trouble with Debian though. 

Yet how could bad hardware result in subsequent bad installs which each suffered a fatal flaw in a different subsystem? How could bad hardware manifest as incompatible in several different ways with Ubuntu, but none under Debian?

---

### Post by darkod on 2017-09-01
Have you tried with 16.04 LTS? You should always use LTS releases for servers anyway, even for home servers. 17.04 support ends in 4 months, while 16.04 will have support until April 2021 (5 years).

Try that version, and if it doesn't work you will surely find help here to start solving the problems one by one... I assure you samba shares do work with both windows and linux, have it on my desk right in front of me... :)

---

### Post by gbambo on 2017-09-01
Of course Samba shares work. That is my frustration. Obviously something is very wrong. It just seems so much more wrong that common sense would suggest is possible. I have experience 5 inexplicable errors, each of which individually made my installation entirely unusable. I wonder if there is not some common thread.

---

### Post by TheFu on 2017-09-02
+1 for using an LTS server.
+1 for not running a GUI on a server install.

Linux allows us to request things that are usually a bad idea, but the OS assumes we are smart enough to understand those complexities.  Why? Sometimes something dumb is really smart, under certain situations, which is part of the amazing flexibility of Unix-like systems.  That doesn't make it a good idea.

I looked at your other post. Couldn't figure out why you were doing it the hard way.  That goes against common sense.

Have you looked at the boot dependency tree?  Any issues in there?

But, I wouldn't waste my time on 17.04 (or 17.10).  Stay on an LTS.

---

### Post by gbambo on 2017-09-02
I have switched to LTS.

As for doing things the hard way, you were not clear where exactly I did that. Most likely I was not aware it was the hard way.

I agree the flexibility to make terrible mistakes is inseparable from its great power. That is why I am persevering and not just walking away. But some things seem unforgivable, like the failure of the installer to complete the 5th time it is run and the inability to select the keyboard mapping of my choice.

---

### Post by cariboo on 2017-09-02
Ubuntu has pretty extensive documentation available at:

[https://help.ubuntu.com/](https://help.ubuntu.com/)
[https://help.ubuntu.com/community/CommunityHelpWiki](https://help.ubuntu.com/community/CommunityHelpWiki)
[https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/)

---

### Post by TheFu on 2017-09-02
Adding a GUI to a server. Hard way.
Using the minimal install. Hard way.
Redoing installations expecting the outcome to be different.  "Insanity."

As for the keyboard selection, it is easy to pick one that doesn't work the way you think it does.  Plus there are 2 keyboard settings - the console and the GUI. These are not necessarily tied together.

If you aren't clicking Next-Next-Next-Next, then you are doing it the hard way, especially if this is a first attempt with Ubuntu-anything.  At this stage, I can't tell what is an issue and what is a misunderstanding from someone new to Ubuntu.  There are differences between Debian and Ubuntu.  They don't quite work the same way in all things.

Are you trying to use iSCSI?  You mention errors, but not intent.

---

### Post by darkod on 2017-09-03
I'm little confused. What we can see in your first post are iscsi messages, not strictly samba messages. What has iscsi got to do with it, and how are you trying to set up the server?

But first of all, does 16.04 show the same behaviour?

I would try only samba first (don't add iscsi to the new install). Once you get samba working, then you know it works. If you then want to start with iscsi, go ahead.

---

