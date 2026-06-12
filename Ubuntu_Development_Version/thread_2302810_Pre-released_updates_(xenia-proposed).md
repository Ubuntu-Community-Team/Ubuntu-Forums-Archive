---
title: "Pre-released updates (xenia-proposed)"
date: 2015-11-13
forum: Ubuntu Development Version
---

### Post by sammiev on 2015-11-13
I have been taking all the proposed updates since the start of Xenia at least once a day.

As of today or 1 hours ago there is no issues with the proposed updates.

Thanks

---

### Post by ventrical on 2015-11-13
+1!

Same here Sammiev.

Thanks

Regards..

---

### Post by sammiev on 2015-11-15
The only issue found was when the power button is set to shut off and pressed, it goes into suspend.

---

### Post by tista on 2015-11-15
@sammiev,

This is because Ubuntu contributors only added gschema keys for Unity-settings-daemon instead of patching gsd-power-manager.c. For example, 'button-power', 'button-sleep' ...etc.
But today original gnome-settings-daemon only accepts 'power-button-action' key and this key has the 3 strings could be accepted for, 'suspend', 'hibernate' and 'none' for standard desktops/laptops.

The default value of 'power-button-action' is 'suspend' so, you would see such behavior when pressing power button...
I don't know how long we should provide the "meaningless" gschema keys for u-s-d, and I think those keys would mislead the power button actions for most users who runs Ubuntu GNOME. To be honest, I want the contributors to stop providing such keys in Xenial... :(

Please read the comments of upstream developer Bastien Nocera in details:
> In commit 50564cde49ca2e17fb7e59f36a35d61c2cbef1af, we removed support
for configuring the various "sleep state" buttons. However, the power
button might need different behaviour based on the machine, which we
cannot always detect.

In later commits, we'll hard-code the actions for tablets and virtual
machines. Note that "power off" is not an option as this would make
the default action too destructive. It is recommended that you use a
custom shortcut for this instead.

[https://bugzilla.gnome.org/show_bug.cgi?id=755953](https://bugzilla.gnome.org/show_bug.cgi?id=755953)

I completely agreed with his comments.

Best Regards.
Tista

---

### Post by sammiev on 2015-11-15
Hi Tista,

Thanks for the update. :)

---

### Post by ventrical on 2015-11-18
Got this little hicup on xubuntu proposed.

```

Registering documents with scrollkeeper...
Errors were encountered while processing:
 /var/cache/apt/archives/libjpeg-progs_1%3a9a-2ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ventrical@ventrical-OptiPlex-755:~$ 

```

---

### Post by deadflowr on 2015-11-18
@Ventrical
Your probably running into this bug
[https://bugs.launchpad.net/ubuntu/+source/libjpeg8-empty/+bug/1516072](https://bugs.launchpad.net/ubuntu/+source/libjpeg8-empty/+bug/1516072)

---

### Post by ventrical on 2015-11-19
> **deadflowr said:**
> @Ventrical
Your probably running into this bug
[https://bugs.launchpad.net/ubuntu/+source/libjpeg8-empty/+bug/1516072](https://bugs.launchpad.net/ubuntu/+source/libjpeg8-empty/+bug/1516072)

Thanks ! :)

---

### Post by QDR06VV9 on 2015-11-19
> **deadflowr said:**
> @Ventrical
Your probably running into this bug
[https://bugs.launchpad.net/ubuntu/+source/libjpeg8-empty/+bug/1516072](https://bugs.launchpad.net/ubuntu/+source/libjpeg8-empty/+bug/1516072)
Yep Thanks!:o

---

### Post by ventrical on 2015-11-19
Todays updates (ubuntu-gnome)(proposed-on) breaks the login session after it suspends. Will try reboot.

Regards..

---

### Post by QDR06VV9 on 2015-11-19
With two DE's here Unity and Mate, Unity gives a log-in loop then reboot from there I just choose Mate and all is good.
Regards..

---

### Post by ventrical on 2015-11-19
I have two separate installs. One xubuntu and one ubuntu-gnome. Gnome re-booted ok. xubuntu now busted.

regards..

---

### Post by sammiev on 2015-11-19
> **ventrical said:**
> Todays updates (ubuntu-gnome)(proposed-on) breaks the login session after it suspends. Will try reboot.

Regards..

Been updating twice a day with ubuntugnome with proposed on and no issues at all.

Been updating my 1st post every update about an hour after taking the latest proposed. :D

---

### Post by QDR06VV9 on 2015-11-19
I must of had a hicth in my giddy-up(LOL) After some time using the Mate Session I then Logged Out and back in to Unity and All is good, and even after a reboot Unity booted fine.

---

### Post by ventrical on 2015-11-19
> **sammiev said:**
> Been updating twice a day with ubuntugnome with proposed on and no issues at all.

Been updating my 1st post every update about an hour after taking the latest proposed. :D

After hard boot ubuntu-gnome came up with no issues.  It was just while it was updating/upgrade that the glitch happened. I could not log -on . It would not accept password  in logon screen. Works now though.

regards..

---

### Post by v3.xx on 2015-11-20
I opened proposed on Mate for the first time.

```
The following NEW packages will be installed:
distro-info-data libisl15 liblouis9 libqpdf17

The following packages will be upgraded:
cpp-5 cups-browsed cups-filters cups-filters-core-drivers dbus dbus-x11 gcc-5 
gcc-5-base grep libasan2 libatomic1 libcc1-0 libcilkrts5 libcupsfilters1
libdbus-1-3 libfontembed1 libgcc-5-dev libgcc1 libgfortran3 libgmp10 libgomp1
libgutenprint2 libitm1 libkeyutils1 liblouis-data liblsan0 libmpx0 
libopenexr22 libquadmath0 libselinux1 libsemanage-common libsemanage1 libsqlite3-0 
libstdc++6 libtsan0 libubsan0 libxmmsclient6 lsb-base lsb-release
printer-driver-gutenprint python-requests python3-louis python3-pycurl python3-
requests qpdf tcl tk
```

---

### Post by sammiev on 2015-11-24
Todays updates (ubuntu-gnome)(proposed-on) 

package apport 2.19.2-0ubuntu7 failed to install/upgrade: subprocess installed post-installation script returned error exit status 2

I see it is now marked as New &#8594; Confirmed as the bug affects multiple users.

---

### Post by sammiev on 2015-11-24
After 2 reboots the bug was still there and there was no more updates to take.

So after reporting the bug and another reboot, there is no sign of the bug. :)

---

### Post by zika on 2015-11-25
Already fixed but also easy fix with```
sudoedit  /var/lib/dpkg/info/apport.postinst
```in situ (simple if-fi typo).

---

### Post by sammiev on 2015-11-25
> **zika said:**
> Already fixed but also easy fix with```
sudoedit  /var/lib/dpkg/info/apport.postinst
```in situ (simple if-fi typo).

+1

Thanks

---

