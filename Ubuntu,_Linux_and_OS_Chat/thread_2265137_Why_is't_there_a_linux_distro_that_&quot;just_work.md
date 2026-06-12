---
title: "Why is't there a linux distro that &quot;just works&quot; on  Macs"
date: 2015-02-12
forum: Ubuntu, Linux and OS Chat
---

### Post by c@ssie on 2015-02-12
I've been looking for years for a linux distro that "just works" on a Mac.  By that I mean fully functional 

* with hardware graphics acceleration, 
* with sleep mode, 
* with 802.11n WIFI, 
* with bluetooth
* with  S.M.A.R.T disk diagnostics
* with  the ability to read the temperature sensores and properly adjust fan speed.

* without requiring "boot camp" BIOS emulators, 
* without needing to create hybrid MBRs.
* without needing to go through a bunch install steps, just to get it working.
* without needing a GRUB CD
* without needing an extra USB drive (other than the install disk)


Why doesn't such a thing exist? Or if it does where is it?

---

### Post by Matthew_Harrop on 2015-02-12
What have you tried?

---

### Post by c@ssie on 2015-02-12
Ubuntu , LinuxMint,  Debian , OpenSUSE , Fedora , Mageia , CentOS , Arch , elementary , Puppy , Deepin , Bodhi , Ultimate Edition, Sabayon , Mandriva , Lunar , SUSE , ZevenOS , PinguyOS

---

### Post by QIII on 2015-02-12
You could ask the developers of any of them to make sure their distributions work on Macs.

But there would need to be some motivation for them to do that.

Is there a compelling reason why they should expend the resources?

---

### Post by c@ssie on 2015-02-12
> **QIII said:**
> You could ask the developers of any of them to make sure their distributions work on Macs.

But there would need to be some motivation for them to do that.

Is there a compelling reason why they should expend the resources?

Because there are millions of Macs out there.

---

### Post by QIII on 2015-02-12
That is, of course, true.

But is that a motivation?  There are many more machines that are not Macs, and many users of Apple hardware do find ways to install.  We have a sub forum here just for them.

Could someone do it?  Certainly.

Apple hardware is a closed ecosystem.  It probably is not attractive.

---

### Post by ian-weisser on 2015-02-12
Linux developers don't exclude Macs. Apple makes systems that are not fully Linux-compatible.

Why would Apple want to make their hardware Linux-compatible?  They *compete* with Linux. They sell OS.
You paid them for a system when it wasn't Linux-compatible.
And you will likely pay another in a few years when it's still not Linux-compatible.
As far as Apple is concerned, vendor lock-in a valuable *feature*. Why would they eliminate it?

---

### Post by gfelsner on 2015-02-12
> **ian-weisser said:**
> Linux developers don't exclude Macs. Apple makes systems that are not fully Linux-compatible.

Why would Apple want to make their hardware Linux-compatible?  They *compete* with Linux. They sell OS.
You paid them for a system when it wasn't Linux-compatible.
And you will likely pay another in a few years when it's still not Linux-compatible.
As far as Apple is concerned, vendor lock-in a valuable *feature*. Why would they eliminate it?

I was reading in a Linux book a great quote. When the internet was first opened to the public, you were the king! Starting a website was quite simple and could carve out your mark. Now we live in the world where we are mere dwellers in the great kingdoms of Google, Windows, Apple et al...

Every piece of software we write, piece of hardware we support, platform we open, is a step in the right direction. The Holy Grail of convergence is coming. Imagine the possibilities that will be open when a single and open OS can be supported by our phones, PC's, TV's, tablets and whatever the future throws at us. And that it will be open source. That is the goal, and with the last half of Earth's population coming online in the next 10 - 20 years venders will have to enable their platforms to keep costs down. I might be a little to optimistic, but at some point the vender locks will be gone. Good luck for you in your search. ;)

---

### Post by buzzingrobot on 2015-02-13
I'm not a developer, but I am a former Mac owner with experience trying to put Linux on them.  I'll try to address some of the points raised by the OP.

Macs use components from the same vendors that supply components to makers of Intel PC's intended to run Windows, but Macs are not built on the same architecture that's been used for years by PC's intended to run Windows.

 Macs do not use a BIOS. It doesn't exist on a Mac. Windows assumes the presence of a BIOS.  Hence, Apple created the 'boot camp' approach to emulate a BIOS for Windows.

While Macs use more-or-less standard PC components, their performance is very often leveraged/controlled/optimized via proprietary code.  Component manufacturers may also make slight, but important, changes to components sold exclusively to Apple. (E.g., Macs use a different, proprietary, approach to handling hybrid video than Windows PC's.)

Macs often vary in big and little ways from model to model.  These differences are often not apparent to the casual user, but they do mean that, for example, an Ubuntu version that installs successfully on a Macbook 8,2 model may not install at all on a Macbook 8,1 from a few months earlier. It can also mean that something like reverse-engineered fan control code that works on a developer's Mac won't work on your Mac.)

Macs use a different bootup method than PC's designed for Windows.

An extra drive is not needed.

---

### Post by Bucky Ball on 2015-02-13
I'm amazed that Linux runs on Macs at all, considering the 'closed shop' approach they take, and impressed that people in the Linux community have actually been bothered to work out ways of getting it to run on Macs. Despite the fact that OSX is based on Unix (open a terminal in OSx and you will find that it understands many of the commands commonly used in Linux), they closed any door to open-source long ago. ;)

---

### Post by buzzingrobot on 2015-02-13
> **Bucky Ball said:**
> I'm amazed that Linux runs on Macs at all...

Yeah.  The last time I tried it was with 13.04 on a 2011 Macbook Pro. Automatic switching between the onboard Intel video and the Radeon card, normally invisibly transparent in OS X, was impossible since it was controlled by proprietary hardware.  The approach was to emit a specific string of bytes via grub *before* the kernel booted to turn off one of the cards. 

That worked, and the other hardware in the machine worked fine, as well.  Then a kernel update came along and Bang!, all up in smoke.

---

