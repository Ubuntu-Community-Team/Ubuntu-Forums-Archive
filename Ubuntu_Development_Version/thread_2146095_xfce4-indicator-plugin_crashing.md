---
title: "xfce4-indicator-plugin crashing"
date: 2013-05-17
forum: Ubuntu Development Version
---

### Post by slickymaster on 2013-05-17
After today's updates I'm facing continuously crashes with xfce4-indicator-plugin. A pop-up message shows indicating that Plugin "Indicator Plugin" unexpectedly left the panel, and restarted more than once in the last 60 seconds.
 
2013-05-17 updates made:
```
slickymaster@VirtualBox:~$ cat /var/log/dpkg.log | grep "^2013-05-17.*\ installed\ "
2013-05-17 09:11:34 status installed lsb-base:all 4.1+Debian9ubuntu4
2013-05-17 09:11:45 status installed man-db:i386 2.6.3-6
2013-05-17 09:11:46 status installed libdrm2:i386 2.4.45-1
2013-05-17 09:11:46 status installed libdrm-intel1:i386 2.4.45-1
2013-05-17 09:11:46 status installed libdrm-nouveau2:i386 2.4.45-1
2013-05-17 09:11:46 status installed libdrm-radeon1:i386 2.4.45-1
2013-05-17 09:11:46 status installed libsensors4:i386 1:3.3.3-1ubuntu1
2013-05-17 09:11:47 status installed lsb-release:all 4.1+Debian9ubuntu4
2013-05-17 09:11:47 status installed iputils-tracepath:i386 3:20121221-1ubuntu1
2013-05-17 09:11:48 status installed openssh-client:i386 1:6.2p2-1
2013-05-17 09:11:48 status installed iputils-arping:i386 3:20121221-1ubuntu1
2013-05-17 09:11:48 status installed libgssdp-1.0-3:i386 0.14.2-1
2013-05-17 09:11:48 status installed libgtk2-perl:i386 2:1.247-2
2013-05-17 09:11:48 status installed libgupnp-1.0-4:i386 0.20.2-2
2013-05-17 09:11:48 status installed os-prober:i386 1.59ubuntu1
2013-05-17 09:11:48 status installed python-pkg-resources:all 0.6.37-1ubuntu1
2013-05-17 09:11:49 status installed python3-pkg-resources:all 0.6.37-1ubuntu1
2013-05-17 09:11:49 status installed libc-bin:i386 2.17-0ubuntu5
2013-05-17 09:22:27 status installed man-db:i386 2.6.3-6
2013-05-17 09:22:29 status installed libgnutls-openssl27:i386 2.12.23-1ubuntu1
2013-05-17 09:22:29 status installed iputils-ping:i386 3:20121221-1ubuntu1
2013-05-17 09:22:29 status installed libc-bin:i386 2.17-0ubuntu5
2013-05-17 12:54:12 status installed man-db:i386 2.6.3-6
2013-05-17 12:54:14 status installed desktop-file-utils:i386 0.21-1ubuntu1
2013-05-17 12:54:15 status installed mime-support:all 3.54ubuntu1
2013-05-17 12:54:15 status installed bamfdaemon:i386 0.4.0daily13.05.02-0ubuntu1
2013-05-17 12:54:15 status installed gnome-menus:i386 3.6.2-0ubuntu1
2013-05-17 12:54:16 status installed gconf2:i386 3.2.6-0ubuntu1
2013-05-17 12:54:20 status installed hicolor-icon-theme:all 0.12-1ubuntu2
2013-05-17 12:54:21 status installed libglib2.0-0:i386 2.37.0-0ubuntu1
2013-05-17 12:54:23 status installed fakeroot:i386 1.19-2
2013-05-17 12:54:23 status installed file-roller:i386 3.8.2-0ubuntu1
```

```
slickymaster@VirtualBox:~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy
3.10.0-031000rc1-generic
slickymaster@IMT-VirtualBox:~$ ^C
```
I've reported the [bug]("https://bugs.launchpad.net/ubuntu/+source/xfce4-indicator-plugin/+bug/1181134").

Anyone dealing with the same issue.

---

### Post by slickymaster on 2013-05-17
Furthermore, doing same test cases at UbuntuQA, with daily saucy-desktop-i386.iso (2013-05-16) and facing the exact same crashes.

---

### Post by Elfy on 2013-05-17
I had one crash in it a short while ago, nothing since though.

---

### Post by slickymaster on 2013-05-17
> **Elfy said:**
> I had one crash in it a short while ago, nothing since though.

The crashes happen in two distinct Saucy installations, on one I'm running 3.10.0-031000rc1-generic kernel and it happened after running the updates I mentioned in my first post, through TTY1. After updating and when log in my Xubuntu session, immediately xfce4-indicator-plugin crashed.

On the other, I was starting to run [COLOR=#000000]UbuntuQA's[/COLOR] Xubuntu Post-installation testsuite, with 2013/05-16 daily iso, after installing it, and as soon as I log in the Xubuntu session, xfce4-indicator-plugin crashed. The daily iso is running 3.9.0-2-generic kernel.

---

### Post by Elfy on 2013-05-17
This install has the generic kernel. 

I've had nothing since the one I reported earlier, I'll try and check with an up to date iso rather than an up to date install shortly.

Edit - should have waited a bit longer ...

---

### Post by matt_symes on 2013-05-17
I'll be installing todays zsync'ed iso in a couple of hours so i'll also check for this.

---

### Post by slickymaster on 2013-05-17
> **Elfy said:**
> This install has the generic kernel. 

I've had nothing since the one I reported earlier, I'll try and check with an up to date iso rather than an up to date install shortly.

Edit - should have waited a bit longer ...

I'm assuming you're still facing the problem. Anyway the [bug]("https://bugs.launchpad.net/ubuntu/+source/xfce4-indicator-plugin/+bug/1181134") status changed to 'Confirmed' because it now affects multiple users.

---

### Post by Elfy on 2013-05-17
Not seeing it in the daily here, but I've me too'd it for the installed one.

I thought I'd posted that ^^ forum restore autosaved reminded me I hadn't :)

---

### Post by ventrical on 2013-05-17
I just downloaded the full .iso and did a hard install and it works just beautifully. The Ubiquity session was just awesome. I did an "install alongside".

---

### Post by ventrical on 2013-05-17
Oy ... I just :

sudo apt-get update


and here is what I got..

---

### Post by slickymaster on 2013-05-17
> **ventrical said:**
> Oy ... I just :

sudo apt-get update


and here is what I got..

Yeaps :) That's the one.

There are several issues with the daily iso.
Running UbuntuQA's Xubuntu Raring Parole 0.5.0 testcase, I found out that out-of-the-box, Parole can't play several media files, not even opening an installation prompt to install the missing codecs. As I'm posting I'm installing in that other box xubuntu-restricted-extras to see if it works.
Another issue is when trying to Restart, a Log out password prompt appears but the text box is disabled making it impossible to access it. The obvious solution was to resort to terminal and ```
sudo reboot
```

Perhaps you could try to reproduce those issues?

---

### Post by Elfy on 2013-05-17
The reboot issue is probably this one

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1178373](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1178373)

---

### Post by slickymaster on 2013-05-17
> **Elfy said:**
> The reboot issue is probably this one

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1178373](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1178373)

Yes, that's the one. Marked it as also affecting me and subscribed it. In the meanwhile I'll have to edit my testsuite at UbuntuQA as I didn't mentioned this problem before.

On the Parole front, installing xubuntu-restricted-extras did'nt manage to fix. The only workaround that fixed it was to run ```
parole --xv false
```More information about this can be found on the already reported bug: [Bug #1155151]("https://bugs.launchpad.net/ubuntu/+source/parole/+bug/1155151")

---

### Post by ventrical on 2013-05-17
> **slickymaster said:**
> Yeaps :) That's the one.

There are several issues with the daily iso.
Running UbuntuQA's Xubuntu Raring Parole 0.5.0 testcase, I found out that out-of-the-box, Parole can't play several media files, not even opening an installation prompt to install the missing codecs. As I'm posting I'm installing in that other box xubuntu-restricted-extras to see if it works.
Another issue is when trying to Restart, a Log out password prompt appears but the text box is disabled making it impossible to access it. The obvious solution was to resort to terminal and ```
sudo reboot
```

Perhaps you could try to reproduce those issues?

yeap.... same thing .. but I just entered the password <silent> and <click>OK and it rebooted.

---

### Post by slickymaster on 2013-05-17
> **ventrical said:**
> yeap.... same thing .. but I just entered the password <silent> and <click>OK and it rebooted.

In my case it was impossible to enter the password since the text box was disabled, but as Elfy mentioned that's an already reported bug.

Continuing with UbuntuQA's testcases, I'm expecting that probably some other issues will came up since we're still on an early stage.

---

### Post by ventrical on 2013-05-17
> **slickymaster said:**
> Yeaps :) That's the one.

There are several issues with the daily iso.
Running UbuntuQA's Xubuntu Raring Parole 0.5.0 testcase, I found out that out-of-the-box, Parole can't play several media files, not even opening an installation prompt to install the missing codecs. As I'm posting I'm installing in that other box xubuntu-restricted-extras to see if it works.
Another issue is when trying to Restart, a Log out password prompt appears but the text box is disabled making it impossible to access it. The obvious solution was to resort to terminal and ```
sudo reboot
```

Perhaps you could try to reproduce those issues?


Parole works just great here, mp4,MOV etc... I just clicked <install> when the plugin jockey came up.

---

### Post by ventrical on 2013-05-17
I keep getting this apport notification and it will not report when I click send.

whoops .. wrong screenshot

edit

---

### Post by pqwoerituytrueiwoq on 2013-05-17
crashes every time i try to work with a crash report here

---

### Post by ventrical on 2013-05-17
This one here. cannot report.

---

### Post by ventrical on 2013-05-17
You tube works by default in FireFox. It says you need to install plugins but just wait and the video will play, just like in Ubuntu.

---

### Post by slickymaster on 2013-05-17
> **ventrical said:**
> This one here. cannot report.

Concerning this one, see this bug reported by me in 2013-04-12: [Bug #1168558]("https://bugs.launchpad.net/ubuntu/+source/tumbler/+bug/1168558")

---

### Post by slickymaster on 2013-05-17
> **ventrical said:**
> You tube works by default in FireFox. It says you need to install plugins but just wait and the video will play, just like in Ubuntu.

Over here it didn't even said anything needed to be installed, just went on and played the video. :P

---

### Post by ventrical on 2013-05-17
> **slickymaster said:**
> Concerning this one, see this bug reported by me in 2013-04-12: [Bug #1168558]("https://bugs.launchpad.net/ubuntu/+source/tumbler/+bug/1168558")


Ok.. I 'affects me tooed' it :)

---

### Post by slickymaster on 2013-05-17
And yet, another one. Running UbuntuQA testcase Desktop (Xubuntu), item [B]New user
[/B]> 
Go to Applications -> Settings Manager -> Users and Groups and add a new user
Logout, and try to login as the new user
You should be able to login
Logout, then log back in as the initial user
Remove the new user

After removing the new user and login in with the initial user gnome-system-tools 3.0.0-2ubuntu2 package crashed: **users-admin crashed with SIGSEGV in gst_user_profiles_get_for_user()**

Do you feel like trying to reproduce it?

---

### Post by ventrical on 2013-05-17
All I had to do was make a new user - no log in or log out and :

---

### Post by ventrical on 2013-05-17
I think apport is hyper or somthing.

---

### Post by slickymaster on 2013-05-17
> **ventrical said:**
> I think apport is hyper or somthing.

Didn't manage to send the report. Apport went nuts on me.

---

### Post by ventrical on 2013-05-17
> **slickymaster said:**
> Didn't manage to send the report. Apport went nuts on me.

I think a lot of those reports are f/ps, but, then again, in some cases they are real bugs.

---

### Post by slickymaster on 2013-05-17
> **ventrical said:**
> I think a lot of those reports are f/ps, but, then again, in some cases they are real bugs.

Yeah. The real pain in the neck is to distinguish them. :confused:

---

### Post by ventrical on 2013-05-22
> **slickymaster said:**
> And yet, another one. Running UbuntuQA testcase Desktop (Xubuntu), item [B]New user
[/B]

After removing the new user and login in with the initial user gnome-system-tools 3.0.0-2ubuntu2 package crashed: **users-admin crashed with SIGSEGV in gst_user_profiles_get_for_user()**

Do you feel like trying to reproduce it?

These bugs appear fixed as of recent update today. App indicator bug fixed too .. but I have this bug with the top right hand corner where my user name is ...I have to click it about three time before the pulldown dialogue menu comes up.

---

### Post by slickymaster on 2013-05-22
> **ventrical said:**
> These bugs appear fixed as of recent update today. App indicator bug fixed too .. but I have this bug with the top right hand corner where my user name is ...I have to click it about three time before the pulldown dialogue menu comes up.

That's good to hear and it's a sign of a good rhythm of work by the developers.
Unfortunately I had to travel due to a work project and I'll just be home by next week. Until then I'm forced to put my testings on hold, but I'm looking forward to next week to see how much has been improved.

---

### Post by slickymaster on 2013-05-29
> **ventrical said:**
> These bugs appear fixed as of recent update today. App indicator bug fixed too .. but I have this bug with the top right hand corner where my user name is ...I have to click it about three time before the pulldown dialogue menu comes up.

Apparently not. With 27-05-2013's daily iso, I'm still facing the [bug with xfce4-indicator-plugin]("https://bugs.launchpad.net/ubuntu/+source/xfce4-indicator-plugin/+bug/1181134"), but now also when I tried to install applications with Ubuntu Software Center.

---

### Post by slickymaster on 2013-05-29
There's still some other two persisting bugs, with 27-05-2013 daily iso:
[Bug #336272 - Missing suspend button]("https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/336272")
[Bug #1178373 - Restart spawns a password box]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1178373")

---

### Post by slickymaster on 2013-05-29
> **slickymaster said:**
> And yet, another one. Running UbuntuQA testcase Desktop (Xubuntu), item [B]New user
[/B]

After removing the new user and login in with the initial user gnome-system-tools 3.0.0-2ubuntu2 package crashed: **users-admin crashed with SIGSEGV in gst_user_profiles_get_for_user()**

Do you feel like trying to reproduce it?

This one is also persisting. Already filled a bug in Launchpad: [Bug #1185396]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/1185396")

---

