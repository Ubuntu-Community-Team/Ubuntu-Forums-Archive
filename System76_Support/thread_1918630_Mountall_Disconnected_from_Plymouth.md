---
title: "Mountall: Disconnected from Plymouth"
date: 2012-02-01
forum: System76 Support
---

### Post by ahowe42 on 2012-02-01
I just received my new Gazelle laptop with Ubunu 11.04, and let the update manager update everything.  I did nothing to any display drivers.  I spent the day copying my data to it, and setting it up (setup fingerprint scanner, installation of texlive-full, virtualbox, synaptic pm, etc) with various reboots throughout.  Suddenly, when I rebooted once, it came the bootup screen stuck on mountall: Disconnected from Plymouth and just sat there.  I turned it off, then on again after a minute, and it went into loading the GUI just fine.  Now, it is getting stuck in the same place, and I can't get past it.  I can get into the console, but can't get into the GUI at all.

Unlike another user with a similar mountall error, it doesn't flash then continue - it is completely stuck.  How can I get past this?

Thanks in advance!

Andrew

---

### Post by isantop on 2012-02-01
When did your order ship out? I'll need to know this information in order to come to an accurate resolution.

---

### Post by ahowe42 on 2012-02-01
Order Number: 21306, shipped 24 Jan.

Andrew

---

### Post by ahowe42 on 2012-02-01
Slight update - if I enter a terminal, then run sudo lightdm, the GUI starts and everything seem ok.  I ran dpkg-reconfigure lightdm, to maybe fix anything that might have been corrupted or setup wrong.

Is there anything else I should do?  I don't want to have to start it like this everytime...

Andrew

---

### Post by chriscross93 on 2012-02-01
I have had the same problem with my GazP6 since I installed 11.10 in November.

---

### Post by isantop on 2012-02-01
For everyone having this problem:

please run these commands from a terminal:

```
cat /etc/X11/default-display-manager
echo "break"
sudo ls -al /var/lib/lightdm
echo "break"
cat /etc/passwd | grep lightdm
```

Then post the results here. This is all information I can use to help diagnose the problem and come up with a solution.

---

### Post by chriscross93 on 2012-02-01
Screenshot attached.

---

### Post by ahowe42 on 2012-02-02
First of all, running sudo lightdm &disown basically did nothing but print a number to the console.  I entered wihtout using &disown.  Here's my output from the commands after that:


[sudo] password for ahowe42: 
(process:6226): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(process:6226): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(process:6226): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
QGtkStyle was unable to detect the current GTK+ theme.

Sorry, try again.
[sudo] password for ahowe42: 
(process:6267): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(process:6267): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(process:6267): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
QGtkStyle was unable to detect the current GTK+ theme.

total 44
drwxr-x---  9 lightdm lightdm 4096 2012-02-02 08:53 .
drwxr-xr-x 68 root    root    4096 2012-02-01 15:29 ..
drwx------  4 lightdm lightdm 4096 2012-02-01 08:57 .cache
drwx------  4 lightdm lightdm 4096 2012-02-01 08:57 .config
drwx------  3 lightdm lightdm 4096 2012-02-01 08:57 .dbus
-rw-------  1 lightdm lightdm   16 2012-02-01 08:57 .esd_auth
drwx------  2 lightdm lightdm 4096 2012-02-02 08:53 .gconf
drwx------  2 lightdm lightdm 4096 2012-02-01 08:57 .gvfs
drwxrwxr-x  3 lightdm lightdm 4096 2012-02-01 08:57 .local
drwx------  2 lightdm lightdm 4096 2012-02-02 08:53 .pulse
-rw-------  1 lightdm lightdm  256 2012-02-01 08:57 .pulse-cookie
-rw-------  1 lightdm lightdm    0 2012-02-02 08:53 .Xauthority

---

