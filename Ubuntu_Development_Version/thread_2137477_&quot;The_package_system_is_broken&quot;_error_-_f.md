---
title: "&quot;The package system is broken&quot; error - fgrlx related"
date: 2013-04-20
forum: Ubuntu Development Version
---

### Post by beetee2 on 2013-04-20
Hello all.

I have 13.04 installed and I get a red icon in the taskbar telling me to update. However, when I try to update (updates are System Settings, Video driver for the AMD graphics accelerators, and Ubuntu Base) I get an error saying "The package system is broken. Check if you are using third party repositories. If so disable them, since they are a common source of problems. Furthermore run the following command in a Terminal: apt-get install -f"

This problem started after I manually installed drivers for my 7970 using this method:

[http://www.noobslab.com/2013/04/install-ati-amd-catalyst-drivers-in.html](http://www.noobslab.com/2013/04/install-ati-amd-catalyst-drivers-in.html)

After I run:

apt-get install -f 

I receive:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  fglrx
The following NEW packages will be installed:
  fglrx
0 upgraded, 1 newly installed, 0 to remove and 20 not upgraded.
2 not fully installed or removed.
Need to get 0 B/87.2 MB of archives.
After this operation, 267 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 189370 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a12.100~beta7-0ubuntu1~xedgers~raring1_amd64.deb) ...
One or more files have been altered since installation.
Uninstall will not be completed. See /etc/ati/fglrx-uninstall.log for details.
dpkg: error processing /var/cache/apt/archives/fglrx_2%3a12.100~beta7-0ubuntu1~xedgers~raring1_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
No apport report written because MaxReports is reached already 
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx_2%3a12.100~beta7-0ubuntu1~xedgers~raring1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Here is the output from fglrxinfo:

display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7900 Series  
OpenGL version string: 4.2.12173 Compatibility Profile Context 12.10.17

And the output from dpkg -l | grep -i linux-headers-3.8.0.1*:

ii  linux-headers-3.8.0-16                    3.8.0-16.26                                   all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-16-generic            3.8.0-16.26                                   amd64        Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-3.8.0-19                    3.8.0-19.29                                   all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-19-generic            3.8.0-19.29                                   amd64        Linux kernel headers for version 3.8.0 on 64 bit x86 SMP


Any tips on how I could resolve this issue would be greatly appreciated! Thanks in advance :)

---

### Post by jfernyhough on 2013-04-20
I don't think this is anything specifically to do with the drivers. It's more likely due to that random third-party tool (which is completely unnecessary); I'm not really surprised it borked your installation, especially if you're combining that with the X-Edgers PPA. Without knowing what order you installed what, or whether you have installed the PPA version over the self-built version, it's impossible to know exactly what's gone wrong.

There is a line in what you posted which might indicate where an issue lies: "Uninstall will not be completed. See /etc/ati/fglrx-uninstall.log for details."

You might want to open that file and see what the error is.



Otherwise, if you like typing random stuff off the internet, try this:

Stage 1 - remove the fglrx driver

$ sudo apt-get purge fglrx [COLOR=red]ati-amd-v2.4-NoobsLab64.deb[/COLOR]
$ sudo rm /etc/X11/xorg.conf
$ sudo apt-get clean

Step 2 - reinstall the fglrx driver from the repo

$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get install -f
$ sudo apt-get install fglrx
$ sudo amdconfig --initial

Reboot.

---

### Post by beetee2 on 2013-04-20
> **jfernyhough said:**
> Otherwise, if you like typing random stuff off the internet, try this:

I lol'd. You're right, I'm a Linux n00b still, so my only option it feels like sometimes is to read fragmented, generalized suggestions and roll with them. Unfortunately that gets me in more trouble than it should most of the time. :)

Thanks for your suggestions, I hadn't even noticed the log that was generated. I'll look around further and see if that gives any tips, otherwise I'll hit up some of your "random stuff on the internet". ;)

---

### Post by beetee2 on 2013-04-20
By the way, here's that log:

*** AMD Catalyst(TM) Proprietary Driver Uninstall Log 2013-04-20 20:42:56 ***
md5sum integrity check failed for /usr/lib/libfglrx_dm.a.
md5sum integrity check failed for /etc/ati/signature.
One or more files have been altered since installation.
Uninstall will not be completed.

To force uninstall, removing all installed files without verification,
run /usr/share/ati/amd-uninstall.sh --force.

Forcing uninstall is not recommended and may cause system corruption.

---

### Post by beetee2 on 2013-04-20
Fixed the issue quickly thanks to your help, and pointing out the error log that was generated. :)

Here are the steps I did in case anyone else follows my stupidity:

sudo /usr/share/ati/amd-uninstall.sh --force
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f
fglrxinfo (to verify my graphics card was still detected)
sudo amdconfig --initial

Reboot

sudo amdcccle (reconfigured dual monitors, etc)

Reboot

Update through software updater worked flawlessly.

Thanks again!

---

