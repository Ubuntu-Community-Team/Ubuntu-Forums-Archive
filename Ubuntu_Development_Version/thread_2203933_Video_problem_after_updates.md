---
title: "Video problem after updates"
date: 2014-02-05
forum: Ubuntu Development Version
---

### Post by s-cradock on 2014-02-05
After a bunch of updates on Feb 4th my Trusty install failed to boot to desktop. I did notice some mir packages updating, some plymouth packages, lightdm (I think), and a whole lot more.

Starting in Recovery mode | resume gave me a partial desktop with the wrong display parameters - 1024x768 (4:3) instead of 1600x900, but no Unity sidebar, so no access to programs.

Recovery mode + networking | root allowed me to update/upgrade, with a number of upgrades held back today. After that I could boot to the desktop, but still at the incorrect display parameters. Synaptic completed the upgrades, so I'm now up to date , but still getting an incorrect display.

Any ideas? Other versions (Saucy) give correct display parameters, but all three Trusty kernels (3.13.0-5,6,7) are "stuck" at 1024x768.

Any help appreciated...

---

### Post by PotatoHead007 on 2014-02-06
hey :)
Did you update your graphics driver? It may be that, as the graphics card(also called video card) has very much to do with the resolution. Maybe try checking for Additional drivers in System settings?

---

### Post by cariboo on 2014-02-06
I had the same problem this morning after yesterday's updates, I just pressed Alt-F2, logged in, and ran:

```
 sudo apt-get update && sudo apt-get -y dist-upgrade
```

Then rebooted, I've been on the system for the last 10 hours with no problems so far.

---

### Post by ventrical on 2014-02-06
I had a compiz crash on SandyBridge but all is working well on  those systems which I have recently upgraded. This has been the smoothest development cycle yet.

---

### Post by P-I H on 2014-02-06
Had also problem with the desktop. The terminal started with Ctrl+Alt+T and I changed from the Nvidia driver to Noveau, but that didn't help. Changed back to the Nvidia driver and waited for updates. Updateds during the day fixed the desktop.

---

### Post by Mateusz Stachowski on 2014-02-06
If the problems started on 4th or 5th February than it's most likely caused by buggy version of protobuf.

[https://lists.ubuntu.com/archives/ubuntu-desktop/2014-February/004425.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2014-February/004425.html)

> [COLOR=#000000]Hey Adam,[/COLOR]
Sorry about those issues. There was a protobuf update uploaded 
yesterday, which included an unfortunate abi change, that got fixed today:
[https://launchpad.net/ubuntu/+source/protobuf/2.5.0-8ubuntu1](https://launchpad.net/ubuntu/+source/protobuf/2.5.0-8ubuntu1)

The buggy version had a missing symbol that was leading to compiz/unity 
not loading, which is probably the issue you describe. The issue is 
fixed in the archive so updating should give you back a working desktop 
environment.

Cheers, [COLOR=#000000]Sebastien Bacher[/COLOR]

---

### Post by xc3RnbFO8P on 2014-02-06
I had this problem, but it was solved with partial upgrade 

[[img]http://farm8.staticflickr.com/7438/12341788973_846ea24002_c.jpg[/img]](http://www.flickr.com/photos/96052779@N07/12341788973/)
[Screenshot from 2014-02-05 11:26:36](http://www.flickr.com/photos/96052779@N07/12341788973/) by [ringi_is](http://www.flickr.com/people/96052779@N07/), on Flickr

---

### Post by zika on 2014-02-06
Alt-PrtScr (i.e. only shot of active window) would be easier to read and less to DL...

---

### Post by xc3RnbFO8P on 2014-02-06
That is the problem, no active window,  I cant re-size window and I cant copy...

---

### Post by zika on 2014-02-06
> **Ringi said:**
> That is the problem, no active window,  I cant re-size window and I cant copy...Can You scroll through that report-window?

---

### Post by xc3RnbFO8P on 2014-02-06
Not anymore, this was 2 day ago and got solved with Partial upgrade 

> Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libcmis-0.3-3 liblcms1:i386 libpoppler43 libwebp4 linux-headers-3.13.0-3
  linux-headers-3.13.0-3-generic linux-image-3.13.0-3-generic linux-image-extra-3.13.0-3-generic
  python3.4 python3.4-minimal wine-gecko1.4 wine-gecko1.4:i386 wine1.4-amd64 wine1.4-i386:i386
Use 'apt-get autoremove' to remove them.
The following packages have been kept back:
  krb5-multidev libgssapi-krb5-2 libgssapi-krb5-2:i386 libgssrpc4 libk5crypto3 libk5crypto3:i386
  libkdb5-7 libkrb5-3 libkrb5-3:i386 libkrb5-dev libkrb5support0 libkrb5support0:i386
  libubuntu-application-api-mirserver1 libubuntu-location-service0 linux-headers-generic
  linux-image-generic plasma-active-data
The following packages will be upgraded:
  compiz compiz-core compiz-gnome compiz-plugins compiz-plugins-default compiz-plugins-extra
  compiz-plugins-main compiz-plugins-main-default compizconfig-backend-gconf
  compizconfig-settings-manager indicator-datetime iso-codes krb5-locales libcompizconfig0
  libdecoration0 libdecoration0-dev libdvdnav4 libmuonprivate2 libphonon-dev libphonon4
  libphononexperimental4 libubuntu-platform-hardware-api1 libupstart1 linux-libc-dev muon
  muon-discover muon-notifier muon-updater phonon python-compizconfig python-subunit unity8
  unity8-autopilot unity8-fake-env unity8-private upstart
36 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.

---

### Post by s-cradock on 2014-02-06
Well, thanks for the suggestions....

I have re-done the apt-get update && apt-get upgrade without solving the problem. I didn't see the protobuf package upgrading, but it may have done.

It looks more like a video driver problem - but Settings only offers me 4:3 options in Display - I need some 16:9 options (specifically 1600x900).

Until now the intel drivers have been rock solid - has anything changed?

I'm going to report a bug against xserver-xorg-video-intel....which was changed on Feb 5th, and is likely the cause of the problem.

---

### Post by ajgreeny on 2014-02-07
I'm using xubuntu trusty 64bit in a virtualbox installation on an Intel powered and intel HD4000 graphics machine and after faultless running for weeks I have the same problem of booting to a low res cli, though it does after about a minute go to a desktop, but still in low res.

I have vb guest additions installed, and the system has been running full screen 1440x900 with no problems for all the time until now.  In the last lot of updates there was a new kernel plus headers, and new xserver-xorg-video-intel, but I thought the host video driver was the one used in a VM, so that may not be of any consequence.

Any thoughts?

---

### Post by mcse2000ca on 2014-02-07
Same happened here witha Nvidia gt640 when I purged out the nvidia drivers it went in but still alot of issues, tried removing xorg and reinstalling it and then reinstalling a fresh nvidia driver and still low res.

---

### Post by plucky on 2014-02-07
> **ajgreeny said:**
> I'm using xubuntu trusty 64bit in a virtualbox installation on an Intel powered and intel HD4000 graphics machine and after faultless running for weeks I have the same problem of booting to a low res cli, though it does after about a minute go to a desktop, but still in low res.

I have vb guest additions installed, and the system has been running full screen 1440x900 with no problems for all the time until now.  In the last lot of updates there was a new kernel plus headers, and new xserver-xorg-video-intel, but I thought the host video driver was the one used in a VM, so that may not be of any consequence.

Any thoughts?

I had this problem where the display was a small screen. 640 X 330

It was not using the 

This worked for me.

Open synaptic package manager and search for **virtualbox** and then select to install **virtualbox-dkms** and**virtualbox-guest-dkms** and apply.It will install some other packages.After it is finished,you have to reboot and your display should now be correct.

I think it might work if you just install **virtualbox-guest-dkms**

Good Luck

---

### Post by ajgreeny on 2014-02-07
> I think it might work if you just install **virtualbox-guest-dkms**It worked!!

Thank you so much for that.  I had presumed that all might work properly again after further updates, but this has now solved my problem.  I did not install the **virtualbox-dkms** package as that  required a lot of dependencies including the open-source virtualbox itself (vb on a vm  seemed unnecessary) and was only needed for the host, not the guest.

Thanks again.

By the way, it only needed logout and login again to get the correct full screen resolution; reboot was not needed.

---

### Post by s-cradock on 2014-02-07
My problem is due to an error in a mir update - see LP bug #1277343.

Eagerly awaiting a solution...

Meanwhile un-installing ubuntu-desktop-xmir and xserver-xorg-xmir restored my display and allowed a normal boot process.

---

### Post by ajgreeny on 2014-02-07
I had to repeat all those the dkms packages installation this evening when another kernel turned up, 3.13.0-8 in place of 3.13.0-7.

It looks as if I have to install the dkms packages and the vb guest additions each time a new ker4nel appears, so I shall look at writing a script to do it in one go.

---

