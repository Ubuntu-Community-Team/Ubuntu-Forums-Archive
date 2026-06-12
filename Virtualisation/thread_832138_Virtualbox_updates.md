---
title: "Virtualbox updates"
date: 2008-06-17
forum: Virtualisation
---

### Post by bstone17 on 2008-06-17
Recently, normal updates changed the kernel level to 2.6.24-19.  The Virtualbox driver will not load whenever the kernel level changes until the matching updates are released for Virtualbox.  When the 2.6.24-18 update was released, it took about a week for the Virtualbox update to catch up.

I've had no luck trying to compile my own driver, so waiting for a working driver leaves my virtual machines dead. Are there instructions somewhere for updating the driver when the kernel changes?

---

### Post by NetworkGuy on 2008-06-17
Easiest instructions:   Don't update your kernel until the virtualbox driver is updated. :)

You could also just keep booting -18 until the driver update is released.

I also learned this the hard way.

---

### Post by cszikszoy on 2008-06-17
If you look at the error message that VirtualBox gives when it complains about the kernel driver, it tells you exactly what to do.

Open up a terminal and type:

```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by NetworkGuy on 2008-06-17
> **cszikszoy said:**
> If you look at the error message that VirtualBox gives when it complains about the kernel driver, it tells you exactly what to do.

Open up a terminal and type:

```
sudo /etc/init.d/vboxdrv setup
```

I don't think that works on the OSE version.

---

### Post by cszikszoy on 2008-06-17
I'm using the non-OSE version.  I haven't used the non OSE version.  Strange that it would only work for the non-ose version though.

Might be worth it to just use the non-OSE version to get around this problem.  There seems to be lots of kernel upgrades being pushed out.  Last week there were 2 I think.

---

### Post by kcnnc on 2008-06-18
For non-OSE version, the following works.
The kernel module recompile without any problem:
```
root@ubuntu-server:~# /etc/init.d/vboxdrv setup
* Stopping VirtualBox kernel module       *  done.
* Recompiling VirtualBox kernel module    *  done.
* Starting VirtualBox kernel module       *  done.
```

If you are running a fresh Ubuntu server, you may need to install these first:
```
apt-get install make gcc linux-headers-2.6.24-19-server
```

If you are running other kernel, do ***uname -a*** replace the kernel header with the right version.

After that run
```
/etc/init.d/vboxdrv setup
```

The module will recompile correctly and everything back to normal.

Cheers!

---

### Post by cszikszoy on 2008-06-18
So this will work on the non-ose version too?

---

### Post by MillDaKill on 2008-06-18
That does not seem to work.  I have the OSE version.

matt@mattDesktop:/mnt/Storage/ISOs$ /etc/init.d/vboxdrv setup
 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}

---

### Post by buntunub on 2008-06-18
> **kcnnc said:**
> The kernel module recompile without any problem:
```
root@ubuntu-server:~# /etc/init.d/vboxdrv setup
* Stopping VirtualBox kernel module       *  done.
* Recompiling VirtualBox kernel module    *  done.
* Starting VirtualBox kernel module       *  done.
```

If you are running a fresh Ubuntu server, you may need to install these first:
```
apt-get install make gcc linux-headers-2.6.24-19-server
```

If you are running other kernel, do ***uname -a*** replace the kernel header with the right version.

After that run
```
/etc/init.d/vboxdrv setup
```

The module will recompile correctly and everything back to normal.

Cheers!

This is absolutely wrong for OSE (or any) edition of Virtualbox that I am aware of without having the Kmod.

---

### Post by kcnnc on 2008-06-19
The steps are only for the NON OSE version.

---

### Post by jerome1232 on 2008-06-19
Yeah I just comment out the newest kernel in my menu.lst until the updates for virtual box come out.

---

### Post by seetho on 2008-06-19
> **jerome1232 said:**
> Yeah I just comment out the newest kernel in my menu.lst until the updates for virtual box come out.

You only have to change the "default" number to point to the correct entry you want to boot by default.

---

### Post by cashattamu on 2008-06-19
Yep, I have the same problem. This seems to happen almost every time Ubuntu sends out a kernel update. In my opinion (as well as others in my office) it reflects very poorly on Ubuntu.

---

### Post by cashattamu on 2008-06-19
posted bug report - 

[https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/241344](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/241344)

---

### Post by benhur99ph on 2008-06-19
I use the non-OSE version and whenever this happens to me (happened twice already), I just double-click on the virtualbox deb file and hit reinstall. After that, it works. No problems with my existing VM.

---

### Post by Tux Aubrey on 2008-06-19
> it reflects very poorly on Ubuntu.

IMO it reflects even more poorly on Sun.  They should be maintaining up-to-date packages for all major distros and hosting their own repos if they want to maintain control - not simply providing their own downloadables.  VB 1.6 has been a royal pain on Hardy.

---

### Post by seetho on 2008-06-22
> **Tux Aubrey said:**
> IMO it reflects even more poorly on Sun.  They should be maintaining up-to-date packages for all major distros and hosting their own repos if they want to maintain control - not simply providing their own downloadables.  VB 1.6 has been a royal pain on Hardy.

Don't you just hate it when companies like Sun pretend to support open source software when they just make use of community contributed code for their commercial purpose and just leave scraps in the form of a crippled version of the software for you and I.

---

### Post by jerome1232 on 2008-06-30
yeah, the OSE version is definitely crippled, Downloaded the non-OSE version today, got the USB support and seamless mode working and I'm simply amazed at this piece of software. My wife is actually starting to prefer Ubuntu to Windows (because of all the cool stuff I can do for free), if only web-designers thought of something other than IE/Windows..., well virtualbox solves that for us and with seamless mode it *almost* feels like I'm not booting up windows, if it only behaved with Compiz perfectly </wish>

ps, why the heck is all this good stuff disabled in the OSE version

---

