---
title: "I got Ubuntu 12 i386 installed on a SG30 if update will not boot."
date: 2020-03-05
forum: Server Platforms
---

### Post by Raymond Day on 2020-03-05
If I do the update of:

do-release-upgrade

Then it will not boot.

On boot now it stays at a screen that says.

[This at this link on my google photos.]("https://photos.app.goo.gl/a4PYTeyeRHEETefz7")

What that link shows is this text:

**udevd[73]: kernel-provided name 'dm-0' and NAME= 'mapper/sg30-root' disagree, please use SYMLINK+= or change the kernel to provide the proper name**

It says the same on the next line only 'dm-1" and 'mapper/sg30-swap_1"

I looked and there is a link at /dev/dm-o that points to mapper/sg30-root

Should I rename the /dev/dm-0 to sg30-root or something to fix this?

I think that is why it don't boot after I upgrade. But not sure.
It still boots but stays at this message for a wile.

How to I fix this?

---

### Post by CelticWarrior on 2020-03-05
You cannot do a "do-release-upgrade" in any "Ubuntu 12".

Ubuntu 12.04 was a LTS release supported until 2017. 12.10, not LTS, expired mid-2013.

You need to install from scratch a supported release.

---

### Post by Raymond Day on 2020-03-05
Wow thank you good to know.

It still will say:

**97 package updates are available, of which 36 are security updates**

But will not install them hold back. I guess need to do the some other update were it did do it then it don't boot. I think it was something like "do-release-upgrade" This is the 3rd time installing and I don't want to mess up the boot.

---

### Post by Raymond Day on 2020-03-07
I installed them and it it did not boot and I booted a live CD that installed it from and said to fix system. It went though about to installing it again. Then I said fix grub and then had to pick the boot and I typed that in were a line had boot on it.

It fixed it.

Then did another update from 12 to 14 and it booted but the could not see the VGA I edit grub were it said 640 x 480 and took off the # before that line rebooted and can get command prompt on the VGA again.

Now it's saying:

[B]New release '18.04.4 LTS' available.
Run 'do-release-upgrade' to upgrade to it.[/B]

It's running now. I thought 16 was the last 32 bit one or i386. I know the new one coming out next month with have a 32 bit version. If this update works maybe when the next one comes out next month it will say New release again.

-Raymond Day

---

### Post by Raymond Day on 2020-03-07
Wow it did updated and booted. It worked. Still 32-bit but it says this:

Welcome to Ubuntu 18.04.4 LTS (GNU/Linux 4.15.0-88-generic i686)

But I thought it was a i386.

phpsysinfo says this about it.

	Intel(R) Celeron(TM) CPU 1200MHz

How can I test if it's 64 or 32 bit?

-Raymond Day

---

### Post by TheFu on 2020-03-07
uname -a

Ubuntu and most Linux distros don't support intel CPUs prior to the i686 line. In fact, some low-cost i686 clone CPUs from VIA and other vendors don't have the complete i686 instruction set and do not work.  That output is talking instruction-set support, not any specific CPU model.

For example, amd64 doesn't mean that only amd64 CPUs are supported. It is about the instruction-set that amd64 supports, which includes most x86 Intel 64-bit CPUs.  The uname **x86_64** is show on both an Intel Core i5 and an AMD Ryzen 5 here they are clearly different CPUs from different vendors.

If this [https://www.cpubenchmark.net/cpu.php?cpu=Intel+Celeron+1200MHz&id=717](https://www.cpubenchmark.net/cpu.php?cpu=Intel+Celeron+1200MHz&id=717) is the CPU, all I can say is OUCH!   An $80 used chromebook would be 10x faster.   

I assume SG30 isn't a guitar?

---

### Post by Raymond Day on 2020-03-08
It shows this:

root@sg30:/usr/share# uname -a
Linux sg30 4.15.0-88-generic #88-Ubuntu SMP Tue Feb 11 20:12:47 UTC 2020 **i686 i686 i686** GNU/Linux
root@sg30:/usr/share#

So the 3 i686 I guess it is 64 bit.

When I tried to install a i686 and said something it can't install it. So that is why I thought it was a 32 bit CPU.

---

### Post by Raymond Day on 2020-03-08
[URL="https://askubuntu.com/questions/41332/how-do-i-check-if-i-have-a-32-bit-or-a-64-bit-os"]I looked it up and this one says this:
[/URL]
root@sg30:/usr/share# file /lib/systemd/systemd
/lib/systemd/systemd: ELF **32-bit** LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib, for GNU/Linux 3.2.0, BuildID[sha1]=28d57709bf1ed9a357c16359b8dcb8c615a1aec6, stripped
root@sg30:/usr/share#

So is that right 32-bit?

---

### Post by Raymond Day on 2020-03-08
This should show it.

root@sg30:/usr/share# getconf LONG_BIT
32
root@sg30:/usr/share#

I thought they did not have a 32-bit for "Ubuntu 18.04.4 LTS"? But I know that will have Ubuntu 20.04 LTS for both 64-bit and 32-bit's too right?

---

### Post by guiverc on 2020-03-08
Ubuntu 18.04 LTS Desktop was available for amd64 only, with 17.10 being the last x86 desktop release of Ubuntu.  Flavors however do have i386/x86 desktop releases, and you could add the `ubuntu-desktop` to a minimal/server install of 18.04 i386 install even though x86 ISOs were not produced.

Xubuntu 18.10 & Lubuntu 18.10 still had x86/i386 releases, and both continued producing x86 into the 19.04 cycle (I know as I was testing them both) but both stopped producing x86 in Dec-2018 (Xubuntu first, Lubuntu a couple of weeks later). 18.10 installs could release-upgrade to 19.04 if pushed, and if done packages were still produced for x86 to the end of 19.04's supported life.

Infrastructure stopped building x86/i386 a couple of days prior to 19.10's release date, and it won't be turned on for 20.04 so x86/i386 is dead into the future.  Any older i386 systems upgraded to 19.10 shouldn't be used online because not all packages are built, even if some are still receiving upgrades  (*I release-upgraded one 19.04 x86 system to 19.10 & watched upgrades as they ceased, comparing with my amd64 boxes*).

For x86/i386, Ubuntu 18.04 LTS will still have support until 2023-April, and x86/i386 flavors until 2021-April.

  There will be no i386 builds of Ubuntu 20.04, though some i386 packages will be available so you can run i386 as a second (multiarch)architecture, but **not** a full i386 system.

---

### Post by TheFu on 2020-03-08
sg30 is just the hostname.  It could be "steve" or "bobs-big-computer" nothing special about that name at all.

When I google'd the CPU, an Intel "ARK" result was returned which clearly says it is a 32-bit CPU.

One of mine:
```
$ uname -a
Linux **hadar** 4.15.0-88-generic #88~16.04.1-Ubuntu SMP Wed Feb 12 04:19:15 UTC 2020 **x86_64** x86_64 x86_64 GNU/Linux
```
hadar is just the hostname. Running 16.04.
Another, 
```
$ uname  -a
Linux **lubuntu** 4.15.0-88-generic #88~16.04.1-Ubuntu SMP Wed Feb 12 04:18:19 UTC 2020 **i686** athlon i686 GNU/Linux

```
lubuntu is just the hostname. This is a virtual machine that has been my primary desktop since around 2008, upgraded over time.
Running 16.04.

I'm waiting for 18.04 to clearly document, or fix, the networking subsystem.  May need to leave Ubuntu due to some other Canonical decisions that do not align with our needs.  I have a year to decide.

---

### Post by Raymond Day on 2020-03-08
[Good info. But it does say Ubuntu 20.04 LTS will have 32-bit here.]("https://ubuntu.com/blog/statement-on-32-bit-i386-packages-for-ubuntu-19-10-and-20-04-lts")

It's all so neat to know they don't have a ISO for 32-bit 18.04.4. So can only upgrade to it looks like.

So that must be right?

---

### Post by Raymond Day on 2020-03-11
When I installed this at 1st I could not get it to boot and found out if I picked **LVM for format it then booted**. I worked on this for like 3 weeks and wow was I happy that it booted. Then the 1st next one upgrade it did not boot. I rebooted the ISO and picked fix broken system. After a wile looks like was installing it again but it went to fix things and I picked fix grub and that worked. From all the other upgrades it booted. Got this on a 500GB SSD.

Is there some settings that should do if running a server on a SSD?

Thank you.

-Raymond Day

---

### Post by guiverc on 2020-03-11
No only some packages are being built, on the link your provided you'll note 

> [COLOR=#111111][FONT=Ubuntu]build selected 32-bit i386 packages for Ubuntu 19.10 and 20.04 LTS[/FONT][/COLOR]

I've said before, Lubuntu and Xubuntu both started building for 19.04, thus the builds of packages continued through the life of that release.

I mentioned this before, but I actually release-upgraded a 19.04 x86 box to 19.10 before builds for 19.10 were shut off. Whilst it'll continue to run, it's not a system you would want to rely on as many packages are now outdated (no longer being built, thus no upgrades).  To keep it up to date would involve a lot of manual work, and would be risky in my books. I don't use my x86/19.10 system so don't care, I hoped it would be helpful in testing Lubuntu changes, so kept it updated (but as packages fell behind due to no longer being built for x86/i386 the boxes testing value disappeared). If you upgrade to 20.04 with x86 - this will be where you will be.

If you need x86/i386 after Ubuntu 18.04 LTS's EOL, I'd suggest Debian 10 (I have an old thinkpad r50p which is i586 class so it won't boot 18.04, but it'll run debian 10/buster okay; debian & ubuntu never used the kernel i486/i585/i686 tags for ISOs, all being called i386)

---

