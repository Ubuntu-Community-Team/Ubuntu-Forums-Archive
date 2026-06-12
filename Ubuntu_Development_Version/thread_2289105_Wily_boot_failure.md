---
title: "Wily boot failure"
date: 2015-08-01
forum: Ubuntu Development Version
---

### Post by crcarson on 2015-08-01
Rebuilt 15.10 from daily build download 7/30.  Got the system up and running (after seeing and ignoring the udt-timezone error).  Seem to boot and run OK.  Customize with the additional applications and setup static IP address for this home server.  Found the system would no longer complete the boot, hung before login screen.  Appears the custom interface file (same file as I have working on 15.04 and another 15.10 system) is causing the hang.  The my interface file is set to modify the ethernet device eth0 but this version of 15.10 is booting with the ethernet named eno1.  Had this naming problem before on earlier 15.10 build and found changing the interface file to look for eno1 worked.  Some later update to this earlier 15.10 system changed the name back to eth0 so had to again modify the interface file.  With that in mind modified the interface file to look for eno1 and was able to boot.

Why the change in the name of the ethernet?  I know the file /etc/udev/rules.d/70-persistant-net.rules is missing from this new 15.10 build but remember when this problem occurred on a prior build it was there and did specify the name eth0 although it didn't work.

---

### Post by crcarson on 2015-08-02
Anyone know the package the file /lib/udev/write_net_rules is in?  This exists on my 15.04 system but not on 15.10 and is supposed build the file 70-persistant-net.rules that assigns the network device names.

---

### Post by dino99 on 2015-08-02
[https://launchpad.net/ubuntu/+source/systemd/222-1ubuntu4](https://launchpad.net/ubuntu/+source/systemd/222-1ubuntu4)

Systemd-223-1 :
 * Drop debian/extra/base-installer.d/05udev: We use net.ifnames by default
    now, thus we don't need to copy 70-persistent-*.rules any more.

---

### Post by crcarson on 2015-08-03
OK, the ethernet device name is eno1 and should not change again (for now).  Do find it troubling that I can make my 15.10 system unbootable by specifying eth0 in the static definition of my ethernet.

---

### Post by VinDSL on 2015-08-03
> **crcarson said:**
> Found the system would no longer complete the boot, hung before login screen.

I had a similar problem, after doing an incremental update, last week - "*hung before login screen*".  I might also add, there was no network connection possible in recovery mode either - which mirrors what you said above.

After several hours of trying to put Humpty Dumpty back together again, I finally gave up and chrooted my install using a daily build.

Guess what?!?!?!  No change !!  LoL :p

The fact that it wasn't booting before the login screen got me thinking... Hrm... I've always run GDM not LightDM.  It couldn't be that easy, right?  Wrong!

I switched to LightDM, and BOOM!!!  It booted normally, and life was good, again.

This probably doesn't have anything to do with your situation, but I thought I should mention it, in case another GDM user has the same problem that I did.  

The "Wily boot failure" title is rather all-encompassing, so I thought I would add my two-cents...  :)

---

### Post by syntaxerror74 on 2015-08-10
> **crcarson said:**
> Anyone know the package the file /lib/udev/write_net_rules is in?
Well, it's almost too simple for words: it IS in the udev package! :D 
[http://pkgs.org/ubuntu-12.04/ubuntu-main-i386/udev_175-0ubuntu9_i386.deb.html](http://pkgs.org/ubuntu-12.04/ubuntu-main-i386/udev_175-0ubuntu9_i386.deb.html)

---

