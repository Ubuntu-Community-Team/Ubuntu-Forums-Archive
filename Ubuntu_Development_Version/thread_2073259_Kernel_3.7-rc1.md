---
title: "Kernel 3.7-rc1"
date: 2012-10-19
forum: Ubuntu Development Version
---

### Post by paul_in_london on 2012-10-19
Just checked the mainline daily again:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)

The all.debs are still missing.

---

### Post by dino99 on 2012-10-19
Seems compil is borked:

Use of uninitialized value $builddep in string ne at /usr/share/kernel-wedge/commands/gen-control line 42, <KVERS> line 6.
Use of uninitialized value $builddep in split at /usr/share/kernel-wedge/commands/gen-control line 43, <KVERS> line 6.
Use of uninitialized value $builddep in string ne at /usr/share/kernel-wedge/commands/gen-control line 42, <KVERS> line 8.
Use of uninitialized value $builddep in split at /usr/share/kernel-wedge/commands/gen-control line 43, <KVERS> line 8.
Use of uninitialized value $builddep in string ne at /usr/share/kernel-wedge/commands/gen-control line 42, <KVERS> line 9.
Use of uninitialized value $builddep in split at /usr/share/kernel-wedge/commands/gen-control line 43, <KVERS> line 9.

---

### Post by VinDSL on 2012-10-20
> **paul_in_london said:**
> Just checked the mainline daily again:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)

The all.debs are still missing.
Just checked the mainline kernel PPA...

Kernel 3.7-rc2 is available now.

The all.debs are still missing.  :D

---

### Post by paul_in_london on 2012-10-20
> **VinDSL said:**
> Just checked the mainline kernel PPA...

Kernel 3.7-rc2 is available now.

The all.debs are still missing.  :D

Thanks Vin.

Damn. Thought they might have been there with rc2.

---

### Post by sammiev on 2012-10-20
Looks like the all debs are there now.

---

### Post by paul_in_london on 2012-10-20
> **sammiev said:**
> Looks like the all debs are there now.

I don't see them?! :confused:

---

### Post by dino99 on 2012-10-20
I've sent a message to the maintainer about that missing all.deb package.

---

### Post by zika on 2012-10-21
> **paul_in_london said:**
> Thanks Vin.

Damn. Thought they might have been there with rc2.So, we will have to wait for rc3... ;)

---

### Post by dino99 on 2012-10-21
> **zika said:**
> So, we will have to wait for rc3... ;)

or rc2 been rebuilt  (not found a 3.7 ppa)

---

### Post by Vrroom on 2012-10-21
[http://xkcd.com/456/](http://xkcd.com/456/) :)

---

### Post by thotz on 2012-10-21
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc2-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc2-quantal/) is there :)

---

### Post by zika on 2012-10-21
> **thotz said:**
> [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc2-quantal/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.7-rc2-quantal/") is there :)Look up, it is without  _all.deb, still, ... ;)

---

### Post by donniezazen on 2012-10-21
> **Vrroom said:**
> [http://xkcd.com/456/](http://xkcd.com/456/) :)

Happened to me last weekend. High system temperature drives me crazy.

BTW Where is linux-headers-all? I suppose I need linux-headers-generic, linux-headers-all and linux-image.

---

### Post by zika on 2012-10-21
> **donniezazen said:**
> Happened to me last weekend. High system temperature drives me crazy.

BTW Where is linux-headers-all? I suppose I need linux-headers-generic, linux-headers-all and linux-image.And linux-image-extra...

---

### Post by fooman on 2012-10-21
i see 3.6.3 has been added today....with the all.deb!!  :)

---

### Post by PaulW2U on 2012-10-21
> **fooman said:**
> i see 3.6.3 has been added today....with the all.deb!!  :)

Thanks. Downloaded and installed.

---

### Post by paul_in_london on 2012-10-21
> **paulw2u said:**
> thanks. Downloaded and installed.

+1

---

### Post by sparker256 on 2012-10-21
> **fooman said:**
> i see 3.6.3 has been added today....with the all.deb!!  :)
Thanks downloaded and installed.
```

bill@billsim-64-1304:~$ uname -r
3.6.3-030603-generic

```
Bill

---

### Post by VinDSL on 2012-10-22
Liquorix, here...  :)


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-21-oct-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-21-oct-2012-1.png")[/INDENT]


```
vindsl@Zuul:~$ uname -r
3.6.0-3.dmz.1-liquorix-686

```

---

### Post by JMB74 on 2012-10-22
3.7 RC2 will all.debs

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc2-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc2-raring/)

---

### Post by fyfe54 on 2012-10-22
This needs its own thread.
It's here, and complete with the all debs.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc2-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc2-raring/)

Downloading...

Update:  Fast install, and system seems altogether snappier.

---

### Post by Vrroom on 2012-10-22
> **JMB74 said:**
> 3.7 RC2 will all.debs

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc2-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc2-raring/)

Raring build can be safely installed in Quantal?

---

### Post by zika on 2012-10-22
> **fyfe54 said:**
> This needs its own thread.
It's here, and complete with the all debs.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc2-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc2-raring/)

Downloading...

Update:  Fast install, and system seems altogether snappier.Thank You...
@dino99: Thank You! ([http://ubuntuforums.org/showpost.php?p=12308054&postcount=7](http://ubuntuforums.org/showpost.php?p=12308054&postcount=7) )

---

### Post by zika on 2012-10-22
@JMB74 Thank You...
@dino99: [http://ubuntuforums.org/showthread.php?p=12310590#post12310590](http://ubuntuforums.org/showthread.php?p=12310590#post12310590)
> **Vrroom said:**
> Raring build can be safely installed in Quantal?There is not even a &#8222;R&#8220; from Raring available yet... ;)
In my opinion: Yes of course...
I've never made any attention to that part of the name of a kernel...

[]("http://ubuntuforums.org/showthread.php?p=12310590#post12310590")

---

### Post by sparker256 on 2012-10-22
> **thotz said:**
> [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc2-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc2-quantal/) is there :)
Tried that build and get a PANIC error. My 3.6.3 is working fine using nvidia-current-updates 304.51.

PANIC: early exception of rip 10:ffffffff810440a6 error 0 cr 0

Anyone have it working?

Bill

---

### Post by JMB74 on 2012-10-22
Seems to boot and run OK on this laptop with Intel Sandybridge graphics.

---

### Post by Harry33 on 2012-10-22
> **sparker256 said:**
> Tried that build and get a PANIC error. My 3.6.3 is working fine but am **not** using Nvidia current yet.

PANIC: early exception of rip 10:ffffffff810440a6 error 0 cr 0

Anyone have it working?

Bill

At least nvidia-current_310.14 (beta) from xorg-edgers (quantal series) works fine with kernel 3.6.3.

---

### Post by dino99 on 2012-10-22
Its working here on i386 + 8500gt + nvidia 310.14 from edgers

oem@oem-desktop:~$ uname -r
3.7.0-030700rc2-generic

at first boot, it failed due to required vmlinux image not found, so i've tried recovery mode, and voila :P

---

### Post by cecilpierce on 2012-10-22
I would like to try it, what order do I install the 4 .deb files ?
When I tried it I got a couple errors about vbox and something else, cant remember, dah!

---

### Post by sparker256 on 2012-10-22
As this was updated today I tried it and all is well again using nvidia current 310.14.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc1-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc1-raring/)

```

bill@billsim-64-1304:~$ uname -r
3.7.0-030700rc1-generic

```

The order I used 

linux-headers-3.7.0-030700rc1_3.7.0-030700rc1.201210220602_all.deb
linux-headers-3.7.0-030700rc1-generic_3.7.0-030700rc1.201210220602_amd64.deb
linux-image-3.7.0-030700rc1-generic_3.7.0-030700rc1.201210220602_amd64.deb
linux-image-extra-3.7.0-030700rc1-generic_3.7.0-030700rc1.201210220602_amd64.deb

Bill

---

### Post by dino99 on 2012-10-22
> **cecilpierce said:**
> I would like to try it, what order do I install the 4 .deb files ?
When I tried it I got a couple errors about vbox and something else, cant remember, dah!

what i do with new kernel :
- download the required debs (2 headers + 2 images) into an empty folder
- then from that folder:  sudo dpkg -i *

thats all  :P

---

### Post by fooman on 2012-10-22
lost the nvidia drivers when i first booted up (GTX480),  no top panel or unity....had to right-click on desktop to open terminal.  from there i opened firefox and got the command to install the x-edgers PPA:
```
sudo add-apt-repository ppa:xorg-edgers/ppa 
```ran that,  then opened synaptic from the terminal (sudo synaptic),  updated the repos,  let it install all updates plus the edgers *nvidia-current* (vers. 310.14).  rebooted and all is well:

```
jackel@jackel-GA-990FXA-UD5:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"

jackel@jackel-GA-990FXA-UD5:~$ uname -r
3.7.0-030700rc2-generic
```...working great!!  :)

btw,  i install the kernels same as dino99's reply above.

---

### Post by cariboo on 2012-10-22
Merged similar threads.

---

### Post by PaulW2U on 2012-10-22
> **sparker256 said:**
> Tried that build and get a PANIC error. My 3.6.3 is working fine using nvidia-current-updates 304.51.

PANIC: early exception of rip 10:ffffffff810440a6 error 0 cr 0

Anyone have it working?

Bill

Not here using Intel graphics.

PC completely froze on start-up. Even the reset button failed to properly reboot the PC. Had to pull out the mains plug. Tried several times but have now reverted to 3.6.3.

Best not to play with things I don't understand. :)

---

### Post by cpatrick08 on 2012-10-22
3.7r2 can be found with all.deb [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc2-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc2-raring/)

---

### Post by VinDSL on 2012-10-22
> **sparker256 said:**
> Anyone have [Linux 3.7.0-rc2] working?

Bill
A little history...
[LIST]
[*]Installed Linux 3.7.0-rc1, last week, sans the all.deb file.
[*]Compiled Linux 3.7.0-rc1, yesterday, from source(s).
[*]Installed Linux 3.7.0-rc2, today, complete with all.deb file.
[/LIST]
They've ALL displayed the same behavior on this machine -- they boot, but no 3D display.

Thus...
[LIST]
[*]Unity has no dash or panel; nothing but Conky, on the desktop.
[*]GS comes up in fallback mode, e.g. no Gnome 3 goodness.
[*]LXDE/Openbox loads and works fine. It always does.
[/LIST]
Of interest, I just noticed that an ABI file is being added to /boot.  Haven't read about that anywhere.

I've also noticed that one the modules isn't building correctly in the Linux 3.7.0-rc's.

Anyway, no panic here, with Linux 3.7.0-rc2, just no 3D... ;)

---

### Post by sparker256 on 2012-10-22
There was a new update to the 3.7.0rc1 today and with it all working fine including 3d. Need a way to find out how to post a screen shot with out using a link but here it is taking the shuttle for a ride at KERI. X-Plane 10 seems quite happy and my plugin is also working fine.

[https://www.dropbox.com/s/5yj0b5xta8j8ds1/bill-desktop-22-oct-2012.png](https://www.dropbox.com/s/5yj0b5xta8j8ds1/bill-desktop-22-oct-2012.png)

Bill

---

### Post by fooman on 2012-10-22
> **VinDSL said:**
> 

Anyway, no panic here, with Linux 3.7.0-rc2, just no 3D... ;)

pretty much what happened to me.  i was using the nvidia experimental drivers when i installed the rc2 this morning....rebooted to no 3d,  no dash, unity or top panel.  

i just went ahead and added the x-edgers ppa,  updated and installed all updates along with the nvidia-current (310.14) from the newly added ppa,  rebooted and all is working again!

---

### Post by ventrical on 2012-10-22
Worked seamlessly here on Intel Graphics chipset.

```

ventrical@ventrical-PY028AA-ABA-A1106N:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
ventrical@ventrical-PY028AA-ABA-A1106N:~$ uname -r
3.7.0-030700rc2-generic
ventrical@ventrical-PY028AA-ABA-A1106N:~$ 


```

```

00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)

```

---

### Post by funicorn on 2012-10-22
3.7.0-rc2-RR surprisingly works normally in QQ, with nvidia 310.14-0ubuntu1~x, thanks to last upgrade from xorg-edgers . But I will not say it's fine. In fact I can feel something not that right. I see one more error in kern.log, and the old one "ACPI _OSC support notification failed, disabling PCIe ASPM" which largely shorten battery life is still there, a big disappointment.

Sometimes Linux is ridiculous. It tries very hard to develop new features but care not much about sucking at the basics. Making a system in which notebooks run without ASPM ? That's a crime.

---

### Post by dino99 on 2012-10-22
yes acpi is not a recent issue on the kernels since .... 2.4 if i remember

---

### Post by ventrical on 2012-10-22
Here is what I get installing on nvidia graphics.

Error! Bad return status for module build on kernel: 3.7.0-030700rc2-generic (i686)
Consult /var/lib/dkms/nvidia-current/304.43/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.7.0-030700rc2-generic /b

---

### Post by ventrical on 2012-10-23
All that solved.

thanks to @fooman
@dino99

---

### Post by Harry33 on 2012-10-23
> **ventrical said:**
> All that solved.

thanks to @fooman
@dino99

Did you solve that by installing the beta version 310.14 from edgers?

---

### Post by ventrical on 2012-10-23
> **Harry33 said:**
> Did you solve that by installing the beta version 310.14 from edgers?


Yes .. I think so .. I just did:

```

sudo add-apt-repository ppa:xorg-edgers/ppa

```

Then updated, rebooted .. and it is working great on my nVidia Geforce 218/210

---

### Post by ventrical on 2012-10-23
> **Harry33 said:**
> Did you solve that by installing the beta version 310.14 from edgers?


Yes.

```

01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce G210] (rev a2)

```

---

### Post by ventrical on 2012-10-23
...and this just put me all the way in.

[CODE]
Installing new version of config file /etc/issue ...
Installing new version of config file /etc/issue.net ...
Installing new version of config file /etc/lsb-release ...

Configuration file `/etc/os-release'
 ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** os-release (Y/I/N/O/D/Z) [default=N] ? y
Installing new version of config file /etc/os-release ...
Processing triggers for plymouth-theme-ubuntu-text ...
[CODE]

dale@dale-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Raring Ringtail (development branch)
Release:    13.04
Codename:    raring
dale@dale-desktop:~$

---

### Post by JMB74 on 2012-10-23
Well, after a switching to the RR based packaging for the daily upstream master builds, these now also ahve a complete set of debs (including all headers).

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2012-10-23-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2012-10-23-raring/)

---

### Post by funicorn on 2012-10-23
I'm a little confused here. So linux-kernel-image-3.7.0-999 should be considered as a higher version compared to  3.7rc2 or vice versa ?

> **JMB74 said:**
> Well, after a switching to the RR based packaging for the daily upstream master builds, these now also ahve a complete set of debs (including all headers).

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2012-10-23-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2012-10-23-raring/)

---

### Post by JMB74 on 2012-10-23
> **funicorn said:**
> I'm a little confused here. So linux-kernel-image-3.7.0-999 should be considered as a higher version compared to  3.7rc2 or vice versa ?

Any RC is a snapshot of Linus' development tree at the time he released the RC.

The [http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/) builds are _daily _builds of the master branch of his tree.

So between RCs, they represent the latest upstream revisions as of the date of the snapshot date and time.

So not really a higher or lower version. 

Just an alternative way of following the development in finer detail with more frequent updates.

Regards version numbers, the RC  and 3.7.0-999 numbering are version distinct, meaning that you can have both installed on a system at the same time.

---

### Post by funicorn on 2012-10-23
Thanks for explanation. I know it may has no definitive answer but doesn't hurt to ask : which one of those two generally runs better in stability ?

---

### Post by JMB74 on 2012-10-23
Hard to say really on that.

Assuming that Linus does not roll out a new RC until he thinks it's not hugely unstable, then you would have to say the RCs I suppose?

However, even RCs are not to be considered that inherently stable, so it's not that uncommon for some regressions to be found just after one is released. In which case if you were running just the RCs then you would have to wait for the next RC to get any fix that might have been merged since. Whereas with the daily builds, you could get that fix much sooner.

So swings and roundabouts......

To be honest when testing linux kernels with test ubuntu mainline builds I tend to take the belt and braces approach.

In that I install the RCs and use those mostly on the system and consider them to be pseudo-stable. But at the same time I do daily updates of the daily build so that should anything problem crop up, or an interesting fix/feature go in, then I can test that ASAP.

---

### Post by sparker256 on 2012-10-23
Also getting a kernel PANIC with this version as soon as I select it from my grub menu.

PANIC: early exception 08 rip 246:10 error 810440a6 cr2 0

My 3.7.0-030700rc1-generic with Nvidia 310.14 is working find.

How to I report this?

Bill

---

### Post by dino99 on 2012-10-23
> **sparker256 said:**
> Also getting a kernel PANIC with this version as soon as I select it from my grub menu.

PANIC: early exception 08 rip 246:10 error 810440a6 cr2 0

My 3.7.0-030700rc1-generic with Nvidia 310.14 is working find.

How to I report this?

Bill

i dont know if it help to report that as its only a rc2 version, meanly blocks of code are rewritten/modified/erased/added/tweaked/.... and the kernel team have bots to test in realtime their modifs, so.
I've got myself this kind of error at very beginning before grub been loaded, when the ramdisk is created (seen it in verbose mode). Then i've tested my ram, and sometimes got errors, explaining the kernel issue, in fact not really the kernel but sysvinit i suppose. Wait & see to know if RR will bring systemd to drop sysvinit.

---

### Post by funicorn on 2012-10-23
Look into the latest nvidia-current changelog and you may find the answer:
> 
nvidia-graphics-drivers (310.14-0ubuntu1~xedgers~quantal3) quantal; urgency=medium

  * New upstream beta release
  * debian/*:
    - Remove XvMC references
    - Add dkms patch for linux 3.7rc1


A kernel interface of certain kernel version for certain version of nvidia driver has to be built to launch the installed nvidia kernel module to work. And this job is done by dkms via the postinst script in nvidia-current package. If the build fails, nvidia module cannot be loaded into kernel or works abnormally hence causes a kernel panic.

The fact kernel 3.7 works normally with nvidia 310.14 is owed to the dkms patch made by xedgers team to nvidia-current 310.14.

> **dino99 said:**
> i dont know if it help to report that as its only a rc2 version, meanly blocks of code are rewritten/modified/erased/added/tweaked/.... and the kernel team have bots to test in realtime their modifs, so.
I've got myself this kind of error at very beginning before grub been loaded, when the ramdisk is created (seen it in verbose mode). Then i've tested my ram, and sometimes got errors, explaining the kernel issue, in fact not really the kernel but sysvinit i suppose. Wait & see to know if RR will bring systemd to drop sysvinit.

---

### Post by ventrical on 2012-10-23
Lots of apparmor errors with latest update.

```

 * Starting AppArmor profiles                                                   Warning from /etc/apparmor.d/lightdm-guest-session (/etc/apparmor.d/lightdm-guest-session line 13): profile /usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper network rules not enforced
Warning from /etc/apparmor.d/lightdm-guest-session (/etc/apparmor.d/lightdm-guest-session line 13): profile chromium_browser network rules not enforced
Warning from /etc/apparmor.d/lightdm-remote-session-freerdp (/etc/apparmor.d/lightdm-remote-session-freerdp line 14): profile /usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper network rules not enforced
Warning from /etc/apparmor.d/lightdm-remote-session-freerdp (/etc/apparmor.d/lightdm-remote-session-freerdp line 14): profile chromium_browser network rules not enforced
Warning from /etc/apparmor.d/lightdm-remote-session-uccsconfigure (/etc/apparmor.d/lightdm-remote-session-uccsconfigure line 14): profile /usr/lib/i386-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper network rules not enforced
Warning from /etc/apparmor.d/lightdm-remote-session-uccsconfigure (/etc/apparmor.d/lightdm-remote-session-uccsconfigure line 14): profile chromium_browser network rules not enforced
Warning from /etc/apparmor.d/sbin.dhclient (/etc/apparmor.d/sbin.dhclient line 74): profile /sbin/dhclient network rules not enforced
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Warning from /etc/apparmor.d/usr.lib.telepathy (/etc/apparmor.d/usr.lib.telepathy line 133): profile /usr/lib/telepathy/mission-control-5 network rules not enforced
Warning from /etc/apparmor.d/usr.lib.telepathy (/etc/apparmor.d/usr.lib.telepathy line 133): profile /usr/lib/telepathy/telepathy-* network rules not enforced
Warning from /etc/apparmor.d/usr.lib.telepathy (/etc/apparmor.d/usr.lib.telepathy line 133): profile sanitized_helper network rules not enforced
Warning from /etc/apparmor.d/usr.sbin.cupsd (/etc/apparmor.d/usr.sbin.cupsd line 175): profile /usr/lib/cups/backend/cups-pdf network rules not enforced
Warning from /etc/apparmor.d/usr.sbin.cupsd (/etc/apparmor.d/usr.sbin.cupsd line 175): profile /usr/sbin/cupsd network rules not enforced
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
Warning from /etc/apparmor.d/usr.sbin.tcpdump (/etc/apparmor.d/usr.sbin.tcpdump line 64): profile /usr/sbin/tcpdump network rules not enforced
Warning from /etc/apparmor.d/usr.bin.evince (/etc/apparmor.d/usr.bin.evince line 160): profile /usr/bin/evince network rules not enforced
Warning from /etc/apparmor.d/usr.bin.evince (/etc/apparmor.d/usr.bin.evince line 160): profile sanitized_helper network rules not enforced
Warning from /etc/apparmor.d/usr.bin.evince (/etc/apparmor.d/usr.bin.evince line 160): profile /usr/bin/evince-previewer network rules not enforced
Warning from /etc/apparmor.d/usr.bin.evince (/etc/apparmor.d/usr.bin.evince line 160): profile sanitized_helper network rules not enforced
Warning from /etc/apparmor.d/usr.bin.evince (/etc/apparmor.d/usr.bin.evince line 160): profile /usr/bin/evince-thumbnailer network rules not enforced
Warning from /etc/apparmor.d/usr.bin.evince (/etc/apparmor.d/usr.bin.evince line 160): profile sanitized_helper network rules not enforced
                                                                         [ OK ]
 * Reloading AppArmor profiles                                                  Warning from /etc/apparmor.d/lightdm-remote-session-freerdp (/etc/apparmor.d/lightdm-remote-session-freerdp line 14): profile /usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper network rules not enforced
Warning from /etc/apparmor.d/lightdm-remote-session-freerdp (/etc/apparmor.d/lightdm-remote-session-freerdp line 14): profile chromium_browser network rules not enforced
Warning from /etc/apparmor.d/lightdm-guest-session (/etc/apparmor.d/lightdm-guest-session line 13): profile /usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper network rules not enforced
Warning from /etc/apparmor.d/lightdm-guest-session (/etc/apparmor.d/lightdm-guest-session line 13): profile chromium_browser network rules not enforced
Warning from /etc/apparmor.d/sbin.dhclient (/etc/apparmor.d/sbin.dhclient line 74): profile /sbin/dhclient network rules not enforced
Warning from /etc/apparmor.d/lightdm-remote-session-uccsconfigure (/etc/apparmor.d/lightdm-remote-session-uccsconfigure line 14): profile /usr/lib/i386-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper network rules not enforced
Warning from /etc/apparmor.d/lightdm-remote-session-uccsconfigure (/etc/apparmor.d/lightdm-remote-session-uccsconfigure line 14): profile chromium_browser network rules not enforced
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Warning from /etc/apparmor.d/usr.lib.telepathy (/etc/apparmor.d/usr.lib.telepathy line 133): profile /usr/


```

---

### Post by funicorn on 2012-10-24
I have switched back to 3.6.3. In my case Both 3.7.0-999 and 3.7.rc2 have serious I/O problem. It takes very long time for gcc to work out a small building job. And it takes very long time for dpkg to commit any change like installing or removing any package. The same thing also happens to dkms, depmod, etc. Although there is barely read/write event, the system behaves like it just recovers from very heavy I/O load and  system memory is used up. In a word, the system easily gets  'tired'.

---

### Post by VinDSL on 2012-10-24
> **funicorn said:**
> I have switched back to 3.6.3 [...]
Same here...

I spent the better part of a day, trying every possible combination(s) of drivers, and so forth, and so on.

nVidia 310.x & Linux 3.7.x refuse to play well together, on THIS machine. 

On the other hand, nVidia 304.x & Linux 3.6.x are working great!

I'm tired of messing with it!  At some point, you gotta admit defeat and move on, you know?

I'll monitor the threads.  When things pan out for others, I give it another whirl.  ;)

---

### Post by ventrical on 2012-10-24
As stated earlier  they are both working great here , the RC2  on the 310.x nvidia driver.

---

### Post by VinDSL on 2012-10-24
> **ventrical said:**
> A stated earlier  they are both working great here , the RC2  on the 310.x nvidia driver.
Edited [that post]("http://ubuntuforums.org/showpost.php?p=12315692&postcount=58") for clarification...  ;)

---

### Post by VinDSL on 2012-10-24
Eureka!  I *knew* I read this somewhere.  Ran across it, again...

SOURCE:  [http://www.phoronix.com/scan.php?page=news_item&px=MTE4MTM](http://www.phoronix.com/scan.php?page=news_item&px=MTE4MTM)

> [SIZE="+1"]NVIDIA Announces New Legacy Linux Support

Posted by Michael Larabel on September 10, 2012[/SIZE]

NVIDIA has announced today the graphics cards that are no longer supported by their mainline Linux graphics driver going forward but will be moved to a new 304.xx Linux legacy driver branch. 

The information that NVIDIA officially posted today is basically the same as what I wrote two weeks back in NVIDIA To Discontinue Linux Support For Some GPUs. **[COLOR="Red"]With the NVIDIA 304.xx proprietary driver series that they're currently on, they will be ending support for GeForce 6 "NV4x" and GeForce 7 "G7x" graphics processors. [/COLOR]**

The full list of all the individual NVIDIA graphics cards losing support (including their PCI IDs) with the 304.xx series is mentioned on [[COLOR="Blue"]this NVIDIA.com page[/COLOR]]("http://www.nvidia.com/object/IO_32667.html"). 

Going forward the 304.xx Linux legacy driver will mainly just be updated for new Linux kernel and X.Org Server compatibility along with any critical bug-fixes needed by major NVIDIA customers. 

NVIDIA is also still maintaining the NVIDIA 173.14.xx Linux driver series for the GeForce 5/FX graphics cards. There is also the now-discontinued NVIDIA 96.43.xx and 71.86.xx drivers for even older NVIDIA hardware, but no further releases in those series are planned.

nVidia 304.xx is the end-of-the-road for my Geforce 7600GT card, according to the nVidia link (quoted above).

Also, here:  [http://nvidia.custhelp.com/app/answers/detail/a_id/3142](http://nvidia.custhelp.com/app/answers/detail/a_id/3142)

Oh, well, maybe they'll add DKMS support for my ancient iron in Linux 3.7.0  LoL!  :D

Anyone else's video card / mobo video support chipset on this Legacy list?!?!?

---

### Post by ventrical on 2012-10-25
> **VinDSL said:**
> Edited [that post]("http://ubuntuforums.org/showpost.php?p=12315692&postcount=58") for clarification...  ;)

Thanks VinDSL.:) I don't mean to be so pernickity. :) lol

---

### Post by zika on 2012-10-25
3.7 definitely has issues with, let's say smoothness. Unusable for audio... At this moment...

---

### Post by wnelson on 2012-10-26
For audio problems, do you have the following in $HOME

.asoundrc

If not create the following script to create the .asoundrc

```

#!/bin/bash
# asoundrc v0.1.0 20090101 markc@renta.net GPLv3
# asoundrc v0.2.0 20090320 quatro_por_quatro@yahoo.es GPLv3
#
# A simple script to create a particular default audio device regardless
# of what cards are loaded or in what order. It could be used anytime or
# placed in a ~/.bashrc script for a persistent setup every login.
#
# Usage: asoundrc [DEFAULT_CARD] > ~/.asoundrc

# use the first parameter as the card name, or else
# look for the sound card, discarding those that are only microphones
# when there are multiple cards, use the first one
if default_card="${1:-$(cat "$(for f in $(ls -1 /proc/asound/card[0-9]*/{midi,codec}* 2>/dev/null); do echo "${f%/*}"; done \
| sed -e '\|^[\[:blank:]\]$|d' -e 'q')/id" 2>/dev/null)}"; then
   echo "Using sound card: ${default_card}" >&2 
   cat /proc/asound/card[0-9]*/id | \
   gawk --assign default_card="${default_card}" \
'{print "pcm."$1" { type hw; card "$1"; }\nctl."$1" { type hw; card "$1"; }"}
END {print "pcm.!default pcm."default_card"\nctl.!default ctl."default_card}'
else
   echo "Warning: No sound cards found." >&2

```

---

### Post by zika on 2012-10-26
> **wnelson said:**
> For audio problems, do you have the following in $HOME

.asoundrc

If not create the following script to create the .asoundrc

```

#!/bin/bash
# asoundrc v0.1.0 20090101 markc@renta.net GPLv3
# asoundrc v0.2.0 20090320 quatro_por_quatro@yahoo.es GPLv3
#
# A simple script to create a particular default audio device regardless
# of what cards are loaded or in what order. It could be used anytime or
# placed in a ~/.bashrc script for a persistent setup every login.
#
# Usage: asoundrc [DEFAULT_CARD] > ~/.asoundrc

# use the first parameter as the card name, or else
# look for the sound card, discarding those that are only microphones
# when there are multiple cards, use the first one
if default_card="${1:-$(cat "$(for f in $(ls -1 /proc/asound/card[0-9]*/{midi,codec}* 2>/dev/null); do echo "${f%/*}"; done \
| sed -e '\|^[\[:blank:]\]$|d' -e 'q')/id" 2>/dev/null)}"; then
   echo "Using sound card: ${default_card}" >&2 
   cat /proc/asound/card[0-9]*/id | \
   gawk --assign default_card="${default_card}" \
'{print "pcm."$1" { type hw; card "$1"; }\nctl."$1" { type hw; card "$1"; }"}
END {print "pcm.!default pcm."default_card"\nctl.!default ctl."default_card}'
else
   echo "Warning: No sound cards found." >&2

```I have sound but it is not of the quality I want and I'm used to with other kernels. Simply put there are latency problems...
Thank You...
I do not have ~/.asoundrc and did not need it for years and (I think) still do not need it...
(Alsa, Jack, Pulseaudio...)

---

### Post by ventrical on 2012-10-26
Yes.. I am getting 'sand through the wheat fields' at the end of hi-biased notes in intervals. All the controls are working. Seems  like it is trying to emulate a low band-pass filter and so there is a hiss and it sounds kind of stumpy.

*edit*

3.5.0-18 kernel is not as stumpy but I am still getting a small amout of hiss... must be  my Box.

Using RythmBox.

---

### Post by ventrical on 2012-10-26
Audacious/Output/Effects/Extra Stereo did the trick on 3.7.x.x RC2

---

### Post by zika on 2012-10-28
[http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D)
Sandy?

---

### Post by ventrical on 2012-10-28
Yes .. on that kernel. (currently)

---

### Post by fyfe54 on 2012-10-28
> **zika said:**
> [http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D)
Sandy?

Just sorts the list of kernels so the newest is on top.

---

### Post by zika on 2012-10-29
> **fyfe54 said:**
> Just sorts the list of kernels so the newest is on top.
I know that...  I meant no new kernel for some time... Preparing for Sandy... ;) ?
Sorry, a bad joke...
Good luck to all in the path of Sandy... Fingers crossed...

---

### Post by Chdslv on 2012-10-29
I didn't have any problems with sound. Clementine is working here. All apps working well.

---

### Post by Chdslv on 2012-10-29
If you happen to have lost sound or crappy sound, do the following;
sudo apt-get remove [COLOR=Red]**--purge**[/COLOR] alsa-base
sudo apt-get remove [COLOR=Red]**--purge**[/COLOR] pulseaudio
sudo apt-get install alsa-base
sudo apt-get install pulseaudio
sudo alsa force-reload

Now, reboot.

I found this somewhere, I can't remember. :)

---

### Post by ventrical on 2012-10-29
> **zika said:**
> I know that...  I meant no new kernel for some time... Preparing for Sandy... ;) ?
Sorry, a bad joke...
Good luck to all in the path of Sandy... Fingers crossed...


 I live  near Detroit MI. Yesterday there was an outer band (from Sandy) that edged north to upper Lake Huron, across Detroit area, right to the center of that storm!! Today , cold, gusty, raining with gales in forecast tommorrow.

Thanks for your concerns.

regards,
ventrical

edit- my apologies for OT msg.

---

### Post by zika on 2012-10-29
> **Chdslv said:**
> If you happen to have lost sound or crappy sound, do the following;
sudo apt-get remove [COLOR=Red]**--purge**[/COLOR] alsa-base
sudo apt-get remove [COLOR=Red]**--purge**[/COLOR] pulseaudio
sudo apt-get install alsa-base
sudo apt-get install pulseaudio
sudo alsa force-reload

Now, reboot.

I found this somewhere, I can't remember. :)First and foremost: here is no need to reboot. No Windows here... Pulseaudio, as it is trie for almost all services in Ubuntu and in Linux generally, can be restarted always &#8222;nice way&#8220;...
All this You've copy&paste-ed is a &#8222;big hammer&#8220; approach. Windows legacy...
Sound works on this (tweaked and battered machine (two and a half round of testing without reinstalk)) like a clockwork on all but that kernel... So, no need to fix what **is not** broken when I can fix what **is** broken...
I'm confused why nobody suggested to reinstall...
My observation about that kernel and quality of latency in sound is confirmed (in more than ten cases) already...

---

### Post by Chdslv on 2012-10-29
> **zika said:**
> First and foremost: here is no need to reboot. No Windows here... Pulseaudio, as it is trie for almost all services in Ubuntu and in Linux generally, can be restarted always &#8222;nice way&#8220;...
All this You've copy&paste-ed is a &#8222;big hammer&#8220; approach. Windows legacy...
Sound works on this (tweaked and battered machine (two and a half round of testing without reinstalk)) like a clockwork on all but that kernel... So, no need to fix what **is not** broken when I can fix what **is** broken...
I'm confused why nobody suggested to reinstall...
My observation about that kernel and quality of latency in sound is confirmed (in more than ten cases) already...

Whatever.:)
If it helps, you might have to log out, log in, maybe it'd fix itself, but when you are playing with not-yet-released distro and a new kernel, maybe it's better to reboot. Does it take that much time?

When one keeps of updating/upgrading everyday, one might get into to trouble on the way, as it is still a not-yet-released distro, but it is nice to have a bleeding edge distro. :)

By the way, I cannot remember, when I last booted into my Windows partition. I had been designing in Sketchup in Ubuntu with Wine, and haven't touched Autocad for a long time. :)

---

### Post by zika on 2012-10-29
> **Chdslv said:**
> maybe it's better to rebootNo, it is not... No point in that... Not even logging out, because services and daemons can be restarted. That is the beauty of U*X... But that is Your choice. It does not have any connection with trouble with latency in sound that I mentioned days ago...
It does take time to reboot and that depends on what was running on that machine. There is no point in testing a distro in the way that machine is doing nothing serious... It is easy to bring it down, getting it back to a state it was before getting down could last some (considerable) time...

---

### Post by Chdslv on 2012-10-29
> **zika said:**
> No, it is not... No point in that... Not even logging out, because services and daemons can be restarted. That is the beauty of U*X...

I agree, but how many of us know about that...Sometimes the simpler way is the better way, because not everyone is a geek.

Good day!:)

---

### Post by dino99 on 2012-10-29
> **Chdslv said:**
> I agree, but how many of us know about that...Sometimes the simpler way is the better way, because not everyone is a geek.

Good day!:)

here its the U+1 forum :P
Spreading basic knowledge is not the right place

---

### Post by zika on 2012-10-29
> **Chdslv said:**
> I agree, but how many of us know about that...Sometimes the simpler way is the better way, because not everyone is a geek.

Good day!:)
Many happy returns from a very old and irreparable geek...
It might be simpler to unplug/plug it or even better to reset a fuse for Your street...
All the best!

---

### Post by Milos_SD on 2012-10-30
> **VinDSL said:**
> Eureka!  I *knew* I read this somewhere.  Ran across it, again...

SOURCE:  [http://www.phoronix.com/scan.php?page=news_item&px=MTE4MTM](http://www.phoronix.com/scan.php?page=news_item&px=MTE4MTM)



nVidia 304.xx is the end-of-the-road for my Geforce 7600GT card, according to the nVidia link (quoted above).

Also, here:  [http://nvidia.custhelp.com/app/answers/detail/a_id/3142](http://nvidia.custhelp.com/app/answers/detail/a_id/3142)

Oh, well, maybe they'll add DKMS support for my ancient iron in Linux 3.7.0  LoL!  :D

Anyone else's video card / mobo video support chipset on this Legacy list?!?!?

There is a way to install 304.xx (60 is the newest one), on 3.7-rcX kernels. 
Check this out: [http://www.nvnews.net/vbulletin/showthread.php?t=194465](http://www.nvnews.net/vbulletin/showthread.php?t=194465)

I have Nvidia 7600GT and 3.7-rc3 kernel. :)

```
uname -a
Linux c2d-desktop 3.7.0-rc3-core2duo #1 SMP PREEMPT Mon Oct 29 01:16:33 CET 2012 x86_64 x86_64 x86_64 GNU/Linux

```

```
lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation G73 [GeForce 7600 GT] (rev a1)

```

```
lsmod | grep nvidia
nvidia              11205656  44 

```

And yes, when you patch the nvidia driver and install it, there is DKMS support, so no need for reinstalling it when you install a new 3.7-rcX kernel. :)

---

### Post by zika on 2012-10-30
I think I've isolated culprit responsible for  &#8222;latency of sound problems&#8220; I've mentioned. Once I'm sure that that is true I'll write what it was...
Hint: It seems that it was not kernel but serendipity of two upgrades...

Update: No, it was 3.7... New rc and 999 are looking (it seems) better...

---

### Post by VinDSL on 2012-10-31
Hrm...

Wonder if I should give Kernel 3.7-rc3 a whirl?!?!?

Linkage:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc3-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc3-raring/)

---

### Post by xebian on 2012-10-31
> **VinDSL said:**
> Hrm...

Wonder if I should give Kernel 3.7-rc3 a whirl?!?!?

Linkage:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc3-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc3-raring/)

I think you should.  I just compiled 3.7.0-rc3 under 13.04, and it's working great.  This is the first time I could get a working session on this box without passing 'nomodeset', and under nouveau as well.  I haven't compiled 304.60 but I know it won't because Nvidia never support dev kernels.
The only problem I have before in rc1 was flash crawling/freezing, but looks like it's fixed on rc3.

```
Linux rubu6 3.7.0-rc3-ik1 #2 SMP Wed Oct 31 14:59:30 CDT 2012 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by PaulW2U on 2012-10-31
> **VinDSL said:**
> Hrm...

Wonder if I should give Kernel 3.7-rc3 a whirl?!?!?


Installed fine here, the only version of 3.7 so far that has done.

```
paul@G620:~$ uname -a
Linux G620 3.7.0-030700rc3-generic #201210310756 SMP Wed Oct 31 11:57:18 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by sparker256 on 2012-10-31
Working fine here.
```

bill@billsim-64-1304:~$ uname -a
Linux billsim-64-1304 3.7.0-030700rc3-generic #201210310756 SMP Wed Oct 31 11:57:18 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
bill@billsim-64-1304:~$ cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86_64 Kernel Module  310.14  Tue Oct  9 11:52:41 PDT 2012
GCC version:  gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-5ubuntu3) 
bill@billsim-64-1304:~$ 

```
Bill

---

### Post by VinDSL on 2012-10-31
Well, I'll be dipped!  :D

Since my last post (above), and with your encouragement, I went ahead and gave Linux 3.7-rc3 a whirl.

Nothing, nada!  No nVidia legacy support. And, a slew of errors & warnings, just like my previous attempts.

Next, following up on Milos_SD's post, I started patching my edgers 304.51 drivers.  I started with "conftest.sh".

Only one error, this time, but it was fatal.  Still no nVidia legacy support.

Finally, I tried the "nv-mmap.c" patch.  Bingo!!!

Third install worked a treat...



[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-31-oct-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-31-oct-2012-1.png")[/INDENT]



SOURCE:  [http://www.nvnews.net/vbulletin/showthread.php?t=194465](http://www.nvnews.net/vbulletin/showthread.php?t=194465)
> I hope NVIDIA will publish a driver that supports 3.7 kernel in new 304.xx legacy branch [...]

In the meantime, I guess ppl running ancient iron will have to roll your own...  ;)

---

### Post by Harry33 on 2012-11-01
This is odd.
In the kernell-ppa/mainline, there is now two new 3.6 kernels:
3.6.4. and 3.6.5 for raring.

But neither of those have the linux-headers-*-all.deb package.

Did they build it in a different way.
Usually linux-headers-*-generic-*.deb depends on linux-headers-*-all.deb.

Also the new 3.7.0 rc3 can be found from there. (and with the -all.deb package).

---

### Post by dino99 on 2012-11-01
have seen that too, so yesterday i've requested again the missing all.deb; wait & see.

---

### Post by funicorn on 2012-11-01
I tried 3.7.rc2 a week ago and it does not work fine. Anybody tried both 3.7.rc2 and rc3 and find any improvement ?

---

### Post by VinDSL on 2012-11-01
> **funicorn said:**
> I tried 3.7.rc2 a week ago and it does not work fine. Anybody tried both 3.7.rc2 and rc3 and find any improvement ?
I couldn't get 3.7-rc1 & 3.7-rc2 to work, so I can't do an A-B-C comparison, but I've been pushing 3.7-rc3 hard, for over 10 hours, without a single hiccup.

Oddly, Flash et al. seems to be much smoother and more stable than 3.6.x. Usually, my browser runs out of mem, several times a day, especially when I have lots of tabs open.  But, I haven't had one occurence yet, with 3.7-rc3.

---

### Post by paul_in_london on 2012-11-01
> **VinDSL said:**
> Well, I'll be dipped!  :D

Since my last post (above), and with your encouragement, I went ahead and gave Linux 3.7-rc3 a whirl.

Nothing, nada!  No nVidia legacy support. And, a slew of errors & warnings, just like my previous attempts.

Next, following up on Milos_SD's post, I started patching my edgers 304.51 drivers.  I started with "conftest.sh".

Only one error, this time, but it was fatal.  Still no nVidia legacy support.

Finally, I tried the "nv-mmap.c" patch.  Bingo!!!

Third install worked a treat...



[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-31-oct-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-31-oct-2012-1.png")[/INDENT]



SOURCE:  [http://www.nvnews.net/vbulletin/showthread.php?t=194465](http://www.nvnews.net/vbulletin/showthread.php?t=194465)


In the meantime, I guess ppl running ancient iron will have to roll your own...  ;)

I'm in the same boat. My graphics card isn't supported by the latest **[COLOR="Red"]nvidia-current[/COLOR]**. The kernel module built ok with 3.7-rcN I think, but wasn't loadable.

I've switched to **[COLOR="Red"]nvidia-current-updates[/COLOR]** which doesn't build at the moment with 3.7-rcN (without patching).

Will either hold out for a new version of **[COLOR="Red"]nvidia-current-updates[/COLOR]** or look into patching it.

---

### Post by VinDSL on 2012-11-01
> **paul_in_london said:**
> I'm in the same boat. My graphics card isn't supported by the latest **[COLOR="Red"]nvidia-current[/COLOR]**. The kernel module built ok with 3.7-rcN I think, but wasn't loadable.

I've switched to **[COLOR="Red"]nvidia-current-updates[/COLOR]** which doesn't build at the moment with 3.7-rcN (without patching).

Will either hold out for a new version of **[COLOR="Red"]nvidia-current-updates[/COLOR]** or look into patching it.
A few thoughts...

Evidently, my GeForce 7600GT has been deemed a legacy device, and won't be supported beyond nVidia 304.x.

Put another way, nVidia >= 310.x will never work in this rig, unless I upgrade my hardware.

The greater issue is, the VM_RESERVED flags have disappeared in kernel 3.7.x and need to be replaced (kernel patch) or ignored (nVidia patch).

I took the easy route and simply patched two (2) files in my nVidia 304.51 folder.  My assumption is, as long as I don't do a fresh install of nvidia-current, e.g. not patched, I will be able to upgrade the kernel, at will.

The VM_RESERVED flags are not coming back, AFAIK.  They are remapping a lot of things in kernel 3.7.x to make it compatible with upstream developments -- kmod being one of them.

Anyway, that's the *feeling* I get, from reading around in the gits.

I can live with nVidia legacy drivers, but my kernel fetish is a different matter.  LoL!  :D

Patching the nVidia install seems to be the easiest way of accomplishing this...

Here are the patches I applied:


```

--- conftest.sh.dist	2012-10-11 19:18:22.704848496 -0400
+++ conftest.sh	2012-10-12 20:35:55.707213868 -0400
@@ -20,6 +20,7 @@
 ISYSTEM=`$CC -print-file-name=include 2> /dev/null`
 SOURCES=$4
 HEADERS=$SOURCES/include
+HEADERSA=$SOURCES/include/uapi
 OUTPUT=$5
 XEN_PRESENT=1
 
@@ -118,7 +119,7 @@
         fi
     fi
 
-    CFLAGS="$CFLAGS $OUTPUT_CFLAGS -I$HEADERS $AUTOCONF_CFLAGS"
+    CFLAGS="$CFLAGS $OUTPUT_CFLAGS -I$HEADERS -I$HEADERSA $AUTOCONF_CFLAGS"
 
     test_xen
 
@@ -146,10 +147,10 @@
         fi
     fi
 
-    CFLAGS="$BASE_CFLAGS $MACH_CFLAGS $OUTPUT_CFLAGS -I$HEADERS $AUTOCONF_CFLAGS"
+    CFLAGS="$BASE_CFLAGS $MACH_CFLAGS $OUTPUT_CFLAGS -I$HEADERS -I$HEADERSA $AUTOCONF_CFLAGS"
 
     if [ "$ARCH" = "i386" -o "$ARCH" = "x86_64" ]; then
-        CFLAGS="$CFLAGS -I$SOURCES/arch/x86/include -I$OUTPUT/arch/x86/include/generated"
+        CFLAGS="$CFLAGS -I$SOURCES/arch/x86/include -I$SOURCES/arch/x86/include/uapi -I$OUTPUT/arch/x86/include/generated -I$OUTPUT/arch/x86/include/generated/uapi"
     elif [ "$ARCH" = "arm" ]; then
         CFLAGS="$CFLAGS -I$SOURCES/arch/arm/include -I$OUTPUT/arch/arm/include/generated"
     fi

```



```

--- nv-mmap.c.dist 2012-08-08 22:52:53.000000000 -0400
+++ nv-mmap.c 2012-08-14 23:52:41.257235863 -0400
@@ -450,7 +450,7 @@
NV_PRINT_AT(NV_DBG_MEMINFO, at);
nv_vm_list_page_count(&at->page_table[i], pages);

- vma->vm_flags |= (VM_IO | VM_LOCKED | VM_RESERVED);
+ vma->vm_flags |= (VM_IO | VM_LOCKED | (VM_DONTEXPAND | VM_DONTDUMP));

```


The first patch is a drop-in.  
[LIST]
[*]Make a text file. Example: uapi-patch.txt
[*]Drop it into your nVidia folder. Example: ~/usr/src/nvidia-current-304.51
[*]Run the patch from inside your nVidia folder with superuser privs.  Example: ```
sudo patch -p0 <uapi-patch.txt
```
[/LIST]


The second patch is a bad copy n' paste, or whatever -- couldn't get it to work -- so I manually patched it...
[LIST]
[*]Edit nv-mmap.c with root auth
[*]Find: ```
vma->vm_flags |= (VM_IO | VM_LOCKED | VM_RESERVED);
```
[*]Replace with: ```
vma->vm_flags |= (VM_IO | VM_LOCKED | (VM_DONTEXPAND | VM_DONTDUMP));
```
[*]Save
[/LIST]


Having said that, I *might* try to install nVidia 304.60... :cool:

---

### Post by VinDSL on 2012-11-02
****> **Harry33 said:**
> This is odd.
In the kernell-ppa/mainline, there is now two new 3.6 kernels:
3.6.4. and 3.6.5 for raring.

But neither of those have the linux-headers-*-all.deb package.

> **dino99 said:**
> have seen that too, so yesterday i've requested again the missing all.deb; wait & see.

They must have listened to you, Dino.  :D

```
vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 12.9.30 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Xserver Xorg Core Branch:" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor:    Dell UltraSharp 1907FP (analog input)" && echo  && xdpyinfo | grep -E '(resolution|dimensions)' && echo

~ VinDSL Unity Debug Script 12.9.30 (vindsl.com) ~
Current Date/Time: Thu Nov  1 23:18:17 MST 2012
Distro Release: Ubuntu Raring Ringtail (development branch)
Kernel Release: **[COLOR="Red"]Linux 3.6.5-030605-generic[/COLOR]**
Unity Release: unity 6.10.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 **[COLOR="Red"]NVIDIA 304.60[/COLOR]**

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 132
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

Xserver Xorg Core Branch:
  Installed: 2:1.13.0+git20120920.70e57668-0ubuntu0ricotz

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[02]--+-07.0  U.S. Robotics USR5660A (USR265660A, USR5660A-BP) 56K PCI Faxmodem
           |            \-0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor:    Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (339x271 millimeters)
  resolution:    96x96 dots per inch

vindsl@Zuul:~$ 

```

---

### Post by serdotlinecho on 2012-11-02
Ubuntu 13.04 will likely be shipping with the linux 3.8 kernel.

[http://www.phoronix.com/scan.php?page=news_item&px=MTIxODg](http://www.phoronix.com/scan.php?page=news_item&px=MTIxODg)

---

### Post by VinDSL on 2012-11-05
Kernel 3.7-rc4 is available.

Cheated death again...  LoL! :D


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-4-nov-2012-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-4-nov-2012-2.png")[/INDENT]

---

### Post by ventrical on 2012-11-05
Geesh ! :)  Another one of those awesome 3D screens..!:)

---

### Post by dino99 on 2012-11-05
what are they doing ?

[HTML]drm/nouveau: headless mode by default if pci class != vga display[/HTML]

so if your display is not a vga one, be ready for a "no device found" or a blackscreen  :(

very strange setting  :confused: or is it switching to nouveau driver in that case ?

---

### Post by Milos_SD on 2012-11-05
3.7-rc4 running great for the past 11 hours. There are no memory leaks that I had with -rc3, and no a lot of iowait that I had with -rc2. :)

---

### Post by zika on 2012-11-05
> **Milos_SD said:**
> 3.7-rc4 running great for the past 11 hours. There are no memory leaks that I had with -rc3, and no **a lot of iowait that I had with -rc2**. :)These where the culprits that messed with my audio pleasure that I' wrote about. The same conclusion...
It was fixed couple of days ago in daily... (999)...

---

### Post by Milos_SD on 2012-11-06
I spoke too early. After 24h uptime, memory usage is almost doubled. Insted of normal 2.5GB usage, I have 4.52GB. :(

---

### Post by ventrical on 2012-11-06
605MiBs out of 1.5 GiBs here on this dual core.. this unit has been up on 3.7xxRC4 for a solid 17 hours so far. Rebooted only thrice.


dale@dale-desktop:~$ uname -a
Linux dale-desktop 3.7.0-030700rc4-generic #201211041435 SMP Sun Nov 4 19:43:27 UTC 2012 i686 i686 i686 GNU/Linux
dale@dale-desktop:~$ 

Running 35 firefox tabs, system monitor, gnome-terminal, Pcmanfile manager.

---

### Post by zika on 2012-11-06
> **Milos_SD said:**
> I spoke to early. After 24h uptime, memory usage is almost doubled. Insted of normal 2.5GB usage, I have 4.52GB. :(Can You decode what is the memory  &#8222;used&#8220; for... I can not confirm such sort of growth... To be more precise: I can account every kind of growth to a service or application I've used... In other words I can not suspect any (major) memory leakage...
I will try to use other kernel for the same amount of time and to see if I would notice any considerable differences...

---

### Post by Milos_SD on 2012-11-06
```
 free -m
             total       used       free     shared    buffers     cached
Mem:          7989       7563        426          0        146       2772
-/+ buffers/cache:       4643       3345
Swap:         1953        688       1264

```

See that -/+ buffers/cache used? That should not be so much. And I can't account everything to applications and services. Not even half of that is used by apps and services. Even when I logout/login there is almost 4GB of usage.
I know what buffers and cache are, but it doesn't behave like it should. If I start playing some game, I'm starting to get a lot of swapping and slowdowns because of it.

P.S. I have very unique kernel configuration. :) I have PREEMPT+1000Hz+HugeTLB+RCU ...

---

### Post by dino99 on 2012-11-06
rc4

o```
em@oem-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3905       3770        135          0          4        950
-/+ buffers/cache:       2815       1090
Swap:        10548         19      10529

```

---

### Post by zika on 2012-11-06
> **Milos_SD said:**
> ```
 free -m
             total       used       free     shared    buffers     cached
Mem:          7989       7563        426          0        146       2772
-/+ buffers/cache:       4643       3345
Swap:         1953        688       1264

```See that -/+ buffers/cache used? That should not be so much. And I can't account everything to applications and services. Not even half of that is used by apps and services. Even when I logout/login there is almost 4GB of usage.
I know what buffers and cache are, but it doesn't behave like it should. If I start playing some game, I'm starting to get a lot of swapping and slowdowns because of it.

P.S. I have very unique kernel configuration. :) I have PREEMPT+1000Hz+HugeTLB+RCU ...I'll keep my eye(s) on that... Will report if I see anything to report...
(I have a sledgehammer tool for cleaning memory... ```
sudo sync ; sudo sysctl -w vm.drop_caches=3 ; sudo sysctl -w vm.drop_caches=1
```but I'm afraid that will not affect parameter You're watching...)

Update: @MilosSD: It seems that You have a valid point... Confirmed...

---

### Post by funicorn on 2012-11-06
I have tried over 4 different version of 3.7rc[1-4], none of which works normally. The system runs but without stability. At first it looks good, but after a while you may feel some different compared to 3.5 or 3.6. And also there are more fails in /var/log/kern.log. In my case the kernel specially has a thing on my ata hard drive, which results in low I/O performance. My opinion is kernel 3.7rc is far from being usable. I'm running Ubuntu 12.10 not 13.04, but I don't think it's relevant.

---

### Post by zika on 2012-11-07
Today's 996 looks promising... (drm-next) ...

---

### Post by Milos_SD on 2012-11-07
Can everyone that have this bug with memory leaks, go here and confirm it:
[https://bugzilla.kernel.org/show_bug.cgi?id=50181](https://bugzilla.kernel.org/show_bug.cgi?id=50181)

Also, describe it better then me, please. My English s**ks. :)

Thanks. :)

---

### Post by paul_in_london on 2012-11-07
Some good news for those of us who can only use the legacy nvida driver now (i.e. latest nvidia-current does not support our graphics cards).

```
paul@raring-64:~$ apt-cache policy**[COLOR="Red"] nvidia-current-updates[/COLOR]**
nvidia-current-updates:
  Installed: **[COLOR="Red"]304.64-0ubuntu1[/COLOR]**
  Candidate: 304.64-0ubuntu1
  Version table:
 *** 304.64-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ raring-proposed/restricted amd64 Packages
        100 /var/lib/dpkg/status
     304.51-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ raring/restricted amd64 Packages
paul@raring-64:~$ 
```

With this version, the nvidia kernel module builds ok with kernel 3.7-rcN. :)

---

### Post by Milos_SD on 2012-11-07
Strange, my uptime is more then a day now, and still, I have good 2.26GB memory used with firefox, evolution, pidgin, deluge (with more then 180 torrents), and ktorrent running. Don't know what I did. Maybe it was nvidia driver issue all along. Before, for nv-mmap.c patch, I just remove VM_RESERVED, but now I'm replaced it with (VM_DONTEXPAND | VM_DONTDUMP). And I did changed drivers 3 times in that time. I was benchmarking new 304.64 vs 310.14 beta. And I'm sticking to 310.14, much better performance in Oil Rush and Fallout 3. :D I hope I will not jinx it. :D

---

### Post by VinDSL on 2012-11-07
> **paul_in_london said:**
> Some good news for those of us who can only use the legacy nvida driver now (i.e. latest nvidia-current does not support our graphics cards).[...]

With this version, the nvidia kernel module builds ok with kernel 3.7-rcN. :)
Good news, indeed!  I'll try it, after I hit the "Submit" button on this post.

As an aside, I spent a whole day (last week) trying different combinations of various nVidia drivers & Linux kernels.  

I was successful in perfecting a hack, but it was so contrived, I never posted 'complete' details here. Explaining it would have been a nightmare!

Proof-Of-Concept (as I type)...
```
vindsl@Zuul:~$ nvidia-smi -q | grep "Product Name" | sed -e 's/.*: /nVidia /'
**[COLOR="Red"]nVidia GeForce 7600 GT[/COLOR]**

vindsl@Zuul:~$ uname -r
**[COLOR="Red"]3.7.0-030700rc4-generic[/COLOR]**

vindsl@Zuul:~$ apt-cache policy nvidia-current
nvidia-current:
  **[COLOR="Red"]Installed: 304.51-0ubuntu1~xedgers~quantal1[/COLOR]**
  Candidate: 310.14-0ubuntu1~xedgers~quantal3
  Version table:
     310.14-0ubuntu1~xedgers~quantal3 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ quantal/main i386 Packages
     304.60-0ubuntu1~precise~xup2 0
        500 http://ppa.launchpad.net/noobslab/nvidia-quantal/ubuntu/ quantal/main i386 Packages
     304.51.really.304.43-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/restricted i386 Packages
        500 http://archive.ubuntu.com/ubuntu/ raring/restricted i386 Packages
 *** 304.51-0ubuntu1~xedgers~quantal1 0
        100 /var/lib/dpkg/status

```

_**Bottom line**_:  The only driver I could find that worked on both kernel 3.6.X AND kernel 3.7-rcX was the edgers 304.51 drivers -- which 'they' deleted from their "pool", some time ago.  Luckily, I happened to have it saved locally (been around the track a few times).  ;)

Moreover, I had to patch two (2) files to install/update/remove kernel  3.7-rcX -- but, use the original files to install/update/remove kernel 3.6.X.

If it works, as promised, this will make life much easier, all the way around!  :D

Hrm... Which way to proceed?!?!?!?

I think I'll:
[LIST]
[*]Boot into kernel 3.6.6
[*]Wash, rinse, and restyle "nvidia-current/nvidia-settings"
[*]Re-install kernel 3.7-rc4
[/LIST]
Er... they do have a new "nvidia-settings", too, yes?


BBL...

---

### Post by VinDSL on 2012-11-07
> **Milos_SD said:**
> Strange, my uptime is more then a day now, and still, I have good 2.26GB memory used with firefox, evolution, pidgin, deluge (with more then 180 torrents), and ktorrent running. Don't know what I did. Maybe it was nvidia driver issue all along. Before, for nv-mmap.c patch, I just remove VM_RESERVED, but now I'm replaced it with (VM_DONTEXPAND | VM_DONTDUMP). And I did changed drivers 3 times in that time. I was benchmarking new 304.64 vs 310.14 beta. And I'm sticking to 310.14, much better performance in Oil Rush and Fallout 3. :D I hope I will not jinx it. :D
Which nVidia card are you running?

Legacy device, or currently supported?

310.14 beta won't do shucks, on this GeForce 7600 GT...

---

### Post by paul_in_london on 2012-11-07
> **VinDSL said:**
> Good news, indeed!  I'll try it, after I hit the "Submit" button on this post.

As an aside, I spent a whole day (last week) trying different combinations of various nVidia drivers & Linux kernels.  

I was successful in perfecting a hack, but it was so contrived, I never posted 'complete' details here. Explaining it would have been a nightmare!

Proof-Of-Concept (as I type)...
```
vindsl@Zuul:~$ nvidia-smi -q | grep "Product Name" | sed -e 's/.*: /nVidia /'
**[COLOR="Red"]nVidia GeForce 7600 GT[/COLOR]**

vindsl@Zuul:~$ uname -r
**[COLOR="Red"]3.7.0-030700rc4-generic[/COLOR]**

vindsl@Zuul:~$ apt-cache policy nvidia-current
nvidia-current:
  **[COLOR="Red"]Installed: 304.51-0ubuntu1~xedgers~quantal1[/COLOR]**
  Candidate: 310.14-0ubuntu1~xedgers~quantal3
  Version table:
     310.14-0ubuntu1~xedgers~quantal3 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ quantal/main i386 Packages
     304.60-0ubuntu1~precise~xup2 0
        500 http://ppa.launchpad.net/noobslab/nvidia-quantal/ubuntu/ quantal/main i386 Packages
     304.51.really.304.43-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/restricted i386 Packages
        500 http://archive.ubuntu.com/ubuntu/ raring/restricted i386 Packages
 *** 304.51-0ubuntu1~xedgers~quantal1 0
        100 /var/lib/dpkg/status

```

_**Bottom line**_:  The only driver I could find that worked on both kernel 3.6.X AND kernel 3.7-rcX was the edgers 304.51 drivers -- which 'they' deleted from their "pool", some time ago.  Luckily, I happened to have it saved locally (been around the track a few times).  ;)

Moreover, I had to patch two (2) files to install/update/remove kernel  3.7-rcX -- but, use the original files to install/update/remove kernel 3.6.X.

If it works, as promised, this will make life much easier, all the way around!  :D

Hrm... Which way to proceed?!?!?!?

I think I'll:
[LIST]
[*]Boot into kernel 3.6.6
[*]Wash, rinse, and restyle "nvidia-current/nvidia-settings"
[*]Re-install kernel 3.7-rc4
[/LIST]
Er... they do have a new "nvidia-settings", too, yes?


BBL...

Hi Vin,

I did think about trying to patch the previous version based on your posts in this thread, but there seemed to be some conflicting views on the nv forums so I held out. This is the update that did the trick for me.

Extract from /var/log/aptitude:

```
paul@raring-64:~$ grep -i nvidia /var/log/aptitude
[UPGRADE] nvidia-current-updates:amd64 304.51-0ubuntu1 -> 304.64-0ubuntu1
paul@raring-64:~$ 
```

Now I'm using:

```
paul@raring-64:~$ uname -a
Linux raring-64 3.7.0-030700rc4-generic #201211041435 SMP Sun Nov 4 19:35:50 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
paul@raring-64:~$
```

Cheers,

Paul

EDIT: Originally when all this trouble started I pinned nvidia-current to 304.51.really.304.43-0ubuntu2, but I ended up removing nvidia-current and installing nvidia-current-updates instead.

---

### Post by Milos_SD on 2012-11-07
> **VinDSL said:**
> Which nVidia card are you running?

Legacy device, or currently supported?

310.14 beta won't do shucks, on this GeForce 7600 GT...

It was 7600GT until few days ago. But had so much trouble with it on 1080p monitor, so I have bought a new nVidia GT640 2GB. Running 310.14 beta drivers.

---

### Post by VinDSL on 2012-11-07
> **Milos_SD said:**
> It was 7600GT until few days ago. But had so much trouble with it on 1080p monitor, so I have bought a new nVidia GT640 2GB. Running 310.14 beta drivers.
Oh, okay.  Wish I could use a modern GPU.

Unfortunately, I'm stuck with AGP on this mobo...

---

### Post by VinDSL on 2012-11-07
Alrighty, then...

Exceedingly scary, nasty, and ugly looking splash, on restart, but the 304.64 module built fine, on kernel 3.7-rc4!


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-7-nov-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-7-nov-2012-1.png")[/INDENT]

---

### Post by cecilpierce on 2012-11-07
I see the 3.7.0 linux-headers-generic and linux-image-generic are in synaptic...:)
Waiting fro the rest...:(

---

### Post by VinDSL on 2012-11-07
> **paul_in_london said:**
> This is the update that did the trick for me.

Extract from /var/log/aptitude:

```
paul@raring-64:~$ grep -i nvidia /var/log/aptitude
[UPGRADE] nvidia-current-updates:amd64 304.51-0ubuntu1 -> 304.64-0ubuntu1
paul@raring-64:~$ 
```
Hi Paul,

That's what I'm running, too...

```
vindsl@Zuul:~$ apt-cache policy nvidia-current-updates
nvidia-current-updates:
  Installed: 304.64-0ubuntu1
  Candidate: 304.64-0ubuntu1
  Version table:
 *** 304.64-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ raring/restricted i386 Packages
        100 /var/lib/dpkg/status
     304.51-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/restricted i386 Packages
vindsl@Zuul:~$ 
```


I tried to install the proprietary nVidia drivers, but the installer didn't like 3.7-rc4 -- with, or without DKMS.

So, I'm back to "nvidia-current-updates"...  ;)

---

### Post by Milos_SD on 2012-11-08
After 2 days uptime, it happend again. Maybe it's use of some specific software that makes kernel leak memory. :(

---

### Post by zika on 2012-11-09
For the first time in years 999 (daily) is a clear no-boot-er on my machine... It even makes monitor cry...

Update: [http://ubuntuforums.org/showpost.php?p=12345448&postcount=13](http://ubuntuforums.org/showpost.php?p=12345448&postcount=13) it seems that this kind of 3.7 (still) works...

---

### Post by Harry33 on 2012-11-09
> **VinDSL said:**
> Hi Paul,

That's what I'm running, too...

```
vindsl@Zuul:~$ apt-cache policy nvidia-current-updates
nvidia-current-updates:
  Installed: 304.64-0ubuntu1
  Candidate: 304.64-0ubuntu1
  Version table:
 *** 304.64-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ raring/restricted i386 Packages
        100 /var/lib/dpkg/status
     304.51-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/restricted i386 Packages
vindsl@Zuul:~$ 
```
I tried to install the proprietary nVidia drivers, but the installer didn't like 3.7-rc4 -- with, or without DKMS.

So, I'm back to "nvidia-current-updates"...  ;)

You could also try X Updates PPA (Ubuntu X Team).
There is this nvidia-current_304.64.
It is for quantal, but RR is exactly the same now.
That one accepts all these:
xorg-video-abi-11 | xorg-video-abi-12 | xorg-video-abi-13

Here:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+packages?field.name_filter=&field.status_filter=published&field.series_filter=quantal](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+packages?field.name_filter=&field.status_filter=published&field.series_filter=quantal)

---

### Post by VinDSL on 2012-11-09
> **Harry33 said:**
> You could also try X Updates PPA (Ubuntu X Team).[...]
Thanks, Harry!

I'm on the trot, right now.

Will do, when I return to the abode...  ;)

---

### Post by VinDSL on 2012-11-09
BTW, I noticed that "acpid" is being held-back in Synaptic, because I don't have KMOD installed -- KMOD was causing problems for me, when it first hit the repos.

Is KMOD working for everyone (else) now?!?!?

---

### Post by Harry33 on 2012-11-09
> **VinDSL said:**
> BTW, I noticed that "acpid" is being held-back in Synaptic, because I don't have KMOD installed -- KMOD was causing problems for me, when it first hit the repos.

Is KMOD working for everyone (else) now?!?!?

Working here fine.
I think it was fixed a while ago.

---

### Post by Harry33 on 2012-11-09
> **VinDSL said:**
> Thanks, Harry!

I'm on the trot, right now.

Will do, when I return to the abode...  ;)

I also tried that one (304.64 - X updates PPA).
Couldn't build kernel module for 3.7.0 rc4 from the kernel PPA.
The xorg edgers version (310.14 beta) works fine.

---

### Post by serdotlinecho on 2012-11-09
> Working here fine.
I think it was fixed a while ago.

Everything is OK now?

```
serdotlinecho@raring:~$ dpkg -l | egrep "module-init-tools|kmod"
ii  kmod                                      9-2ubuntu3                                  i386         tools for managing Linux kernel modules
ii  libkmod2:i386                             9-2ubuntu3                                  i386         libkmod shared library
ii  module-init-tools                         9-2ubuntu3                                  all          transitional dummy package (module-init-tools to kmod)
```

---

### Post by paul_in_london on 2012-11-11
rc5 is here and working:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc5-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc5-raring/)

```
paul@raring-64:~$ uname -a
Linux raring-64 3.7.0-030700rc5-generic #201211110835 SMP Sun Nov 11 13:35:49 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
paul@raring-64:~$
```

---

### Post by VinDSL on 2012-11-11
> **paul_in_london said:**
> rc5 is here and working:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc5-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc5-raring/)

```
paul@raring-64:~$ uname -a
Linux raring-64 3.7.0-030700rc5-generic #201211110835 SMP Sun Nov 11 13:35:49 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
paul@raring-64:~$
```
Interesting!

This is the first attempt at installing a kernel, since I re-instated KMOD.

```
vindsl@Zuul:~/Downloads/Kernel 3.7$ sudo dpkg -i *.deb
[sudo] password for vindsl: 
Selecting previously unselected package linux-headers-3.7.0-030700rc5.
(Reading database ... 412232 files and directories currently installed.)
Unpacking linux-headers-3.7.0-030700rc5 (from linux-headers-3.7.0-030700rc5_3.7.0-030700rc5.201211110835_all.deb) ...
Selecting previously unselected package linux-headers-3.7.0-030700rc5-generic.
Unpacking linux-headers-3.7.0-030700rc5-generic (from linux-headers-3.7.0-030700rc5-generic_3.7.0-030700rc5.201211110835_i386.deb) ...
Selecting previously unselected package linux-image-3.7.0-030700rc5-generic.
Unpacking linux-image-3.7.0-030700rc5-generic (from linux-image-3.7.0-030700rc5-generic_3.7.0-030700rc5.201211110835_i386.deb) ...
Done.
Selecting previously unselected package linux-image-extra-3.7.0-030700rc5-generic.
Unpacking linux-image-extra-3.7.0-030700rc5-generic (from linux-image-extra-3.7.0-030700rc5-generic_3.7.0-030700rc5.201211110835_i386.deb) ...
Setting up linux-headers-3.7.0-030700rc5 (3.7.0-030700rc5.201211110835) ...
Setting up linux-headers-3.7.0-030700rc5-generic (3.7.0-030700rc5.201211110835) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.7.0-030700rc5-generic /boot/vmlinuz-3.7.0-030700rc5-generic
[B][COLOR="Red"]ERROR (dkms apport): binary package for nvidia: 304.64 not found
Error! Bad return status for module build on kernel: 3.7.0-030700rc5-generic (i686)
Consult /var/lib/dkms/nvidia/304.64/build/make.log for more information.[/COLOR][/B]
Setting up linux-image-3.7.0-030700rc5-generic (3.7.0-030700rc5.201211110835) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.7.0-030700rc5-generic /boot/vmlinuz-3.7.0-030700rc5-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.7.0-030700rc5-generic /boot/vmlinuz-3.7.0-030700rc5-generic
[B][COLOR="Red"]ERROR (dkms apport): binary package for nvidia: 304.64 not found
Error! Bad return status for module build on kernel: 3.7.0-030700rc5-generic (i686)
Consult /var/lib/dkms/nvidia/304.64/build/make.log for more information.[/COLOR][/B]
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.7.0-030700rc5-generic /boot/vmlinuz-3.7.0-030700rc5-generic
update-initramfs: Generating /boot/initrd.img-3.7.0-030700rc5-generic
[B][COLOR="Red"]modprobe: ../tools/modprobe.c:550: print_action: Assertion `kmod_module_get_initstate(m) == KMOD_MODULE_BUILTIN' failed.
Aborted
WARNING: could not open /tmp/mkinitramfs_z1I53a/lib/modules/3.7.0-030700rc5-generic/modules.builtin: No such file or directory[/COLOR][/B]
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.7.0-030700rc5-generic /boot/vmlinuz-3.7.0-030700rc5-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.7.0-030700rc5-generic /boot/vmlinuz-3.7.0-030700rc5-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.7.0-030700rc5-generic /boot/vmlinuz-3.7.0-030700rc5-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.7.0-030700rc5-generic...
P: Writing config for /boot/vmlinuz-3.7.0-030700rc4-generic...
P: Writing config for /boot/vmlinuz-3.6.6-030606-generic...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.7.0-030700rc5-generic /boot/vmlinuz-3.7.0-030700rc5-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.7.0-030700rc5-generic
Found initrd image: /boot/initrd.img-3.7.0-030700rc5-generic
Found linux image: /boot/vmlinuz-3.7.0-030700rc4-generic
Found initrd image: /boot/initrd.img-3.7.0-030700rc4-generic
Found linux image: /boot/vmlinuz-3.6.6-030606-generic
Found initrd image: /boot/initrd.img-3.6.6-030606-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 10.10 (10.10) on /dev/sda1
done
Setting up linux-image-extra-3.7.0-030700rc5-generic (3.7.0-030700rc5.201211110835) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.7.0-030700rc5-generic /boot/vmlinuz-3.7.0-030700rc5-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.7.0-030700rc5-generic /boot/vmlinuz-3.7.0-030700rc5-generic
[B][COLOR="Red"]ERROR (dkms apport): binary package for nvidia: 304.64 not found
Error! Bad return status for module build on kernel: 3.7.0-030700rc5-generic (i686)
Consult /var/lib/dkms/nvidia/304.64/build/make.log for more information.[/COLOR][/B]
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.7.0-030700rc5-generic /boot/vmlinuz-3.7.0-030700rc5-generic
update-initramfs: Generating /boot/initrd.img-3.7.0-030700rc5-generic
[B][COLOR="Red"]modprobe: ../tools/modprobe.c:550: print_action: Assertion `kmod_module_get_initstate(m) == KMOD_MODULE_BUILTIN' failed.
Aborted
WARNING: could not open /tmp/mkinitramfs_WObYQQ/lib/modules/3.7.0-030700rc5-generic/modules.builtin: No such file or directory[/COLOR][/B]
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.7.0-030700rc5-generic /boot/vmlinuz-3.7.0-030700rc5-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.7.0-030700rc5-generic /boot/vmlinuz-3.7.0-030700rc5-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.7.0-030700rc5-generic /boot/vmlinuz-3.7.0-030700rc5-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.7.0-030700rc5-generic...
P: Writing config for /boot/vmlinuz-3.7.0-030700rc4-generic...
P: Writing config for /boot/vmlinuz-3.6.6-030606-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.7.0-030700rc5-generic /boot/vmlinuz-3.7.0-030700rc5-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.7.0-030700rc5-generic
Found initrd image: /boot/initrd.img-3.7.0-030700rc5-generic
Found linux image: /boot/vmlinuz-3.7.0-030700rc4-generic
Found initrd image: /boot/initrd.img-3.7.0-030700rc4-generic
Found linux image: /boot/vmlinuz-3.6.6-030606-generic
Found initrd image: /boot/initrd.img-3.6.6-030606-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 10.10 (10.10) on /dev/sda1
done
vindsl@Zuul:~/Downloads/Kernel 3.7$ 

```

Oh, well.  Gives me something to do this afternoon...

Thanks, Paul!  :D

---

### Post by VinDSL on 2012-11-11
Hrm...

It's inexplicable, but it worked, despite all the errors  :confused:


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-11-nov-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-11-nov-2012-1.png")[/INDENT]


Never had that happen before!

I booted into Gnome-Shell, expecting it to go into fallback mode, but...

```
vindsl@Zuul:~$ apt-cache policy nvidia-current-updates
nvidia-current-updates:
  **[COLOR="Red"]Installed: 304.64-0ubuntu1[/COLOR]**
  Candidate: 304.64-0ubuntu1
  Version table:
 *** 304.64-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ raring/restricted i386 Packages
        100 /var/lib/dpkg/status
     304.51-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/restricted i386 Packages

vindsl@Zuul:~$ apt-cache policy nvidia-settings
nvidia-settings:
 **[COLOR="Red"] Installed: 304.64-0ubuntu1~quantal~xup1[/COLOR]**
  Candidate: 310.14-0ubuntu1~xedgers~quantal2
  Version table:
     310.14-0ubuntu1~xedgers~quantal2 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ quantal/main i386 Packages
 *** 304.64-0ubuntu1~quantal~xup1 0
        100 /var/lib/dpkg/status
     304.60-0ubuntu1~precise~xup2 0
        500 http://ppa.launchpad.net/noobslab/nvidia-quantal/ubuntu/ quantal/main i386 Packages
     304.51-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main i386 Packages
        500 http://archive.ubuntu.com/ubuntu/ raring/main i386 Packages

```

---

### Post by Milos_SD on 2012-11-13
@zika: Do you have any idea what is the problem with this past -rc2 kernel and memory usage increase for active buffers?

---

### Post by zika on 2012-11-13
> **Milos_SD said:**
> @zika: Do you have any idea what is the problem with this past -rc2 kernel and memory usage increase for active buffers?Sadly no. I've done complete clean-up, backup and reinstall (QQ>RR) yesterday. Now I have:
```
:~$ uname -a
Linux zika 3.7.0-0-generic #5-Ubuntu SMP Thu Nov 8 20:58:16 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3954       3584        370          0        165       1747
-/+ buffers/cache:       1671       2282
Swap:         4093          0       4093
``````
:~$ uname -a
Linux zika 3.6.0-6.dmz.1-liquorix-amd64 #1 ZEN SMP PREEMPT Thu Nov 8 19:51:13 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3953       1202       2750          0         35        496
-/+ buffers/cache:        670       3282
Swap:         4093          0       4093
```(Liquorix is just brought up, I'll post change after couple of hours...)

Later:```
:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3953       1507       2445          0         39        540
-/+ buffers/cache:        926       3026
Swap:         4093          0       4093
```It stabilized:```
:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3953       1674       2278          0         62        630
-/+ buffers/cache:        980       2972
Swap:         4093          0       4093

```(It seems to grow irrespectively of which kernel is used... But, there is a significant difference...)(It, also, might have to do with FF that was the only important application open during this time. There is a complaint that FF is leaking memory, as far as I recall...)

---

### Post by paul_in_london on 2012-11-17
3.7-rc6 is available now:

```
http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc6-raring/
```

---

### Post by VinDSL on 2012-11-17
> **paul_in_london said:**
> 3.7-rc6 is available now:

```
http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc6-raring/
```
Works!

```

vindsl@Zuul:~$ uname -sr
Linux 3.7.0-030700rc6-generic

```

But, I'd be willing to swear, "network-manager" is getting flakier with each new rc :confused:

For instance, when I click on the NM indicator (in the top panel) there is a box for enabling networking, and not much else.  Mind you, "networking" is enabled, but it runs like grunt.

If I check "Enable networking" it sends me a notification that I just disconnected.  Then, when I check "Enable networking" a second time. NM connects, and works fine for the rest of the session.

Possibly, this is unrelated to the kernel, but I didn't notice it until the 3.7-rcs appeared... and I *think* it's getting worse.  I could ignore it before.  But, now, if I don't check the "Enable networking" box a couple of times, speeds are horrendous, my browser is slow and/or unresponsive, with 404s and so forth. Sometimes, I can't even log into machines on my LAN, in the next room, unless I go though this seemingly silly procedure. :(

Maybe, I'll switch to Wicd for a while, and see if that helps...

---

### Post by Milos_SD on 2012-11-22
Memory leak that we expirianced is fixed in latest git. :D

["fix incorrect NR_FREE_PAGES accounting (appears like memory leak)"]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commit;h=ef6c5be658f6a70c1256fbd18e18ee0dc24c3386")

---

### Post by jerrylamos on 2012-11-22
3.7.0-3 2Acer Aspire1 netbook here, 1.6 gHz dual processors, 1 gb memory

Not long afer booted up with Firefox 5 tabs:

```
             total       used       free     shared    buffers     cached
Mem:           992        847        144          0         27        422
-/+ buffers/cache:        397        594
Swap:         1996         17       1979

```
Memory pretty full not much swap used.

After a while, not doing much, 
```

             total       used       free     shared    buffers     cached
Mem:           992        892         99          0         10        479
-/+ buffers/cache:        402        589
Swap:         1996        216       1779

```
swap usage going up as the clock tics.

Yeh, it could use more memory - one of the ways they got the price down to $250 was by simplifying the case - to add memory, remove keyboard, unplug and remove mother board, then have access to the memory and hard drive....not frustrated enough to try that yet.

---

