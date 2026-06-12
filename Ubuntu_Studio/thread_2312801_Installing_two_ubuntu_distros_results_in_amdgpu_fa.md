---
title: "Installing two ubuntu distros results in amdgpu fatal error"
date: 2016-02-07
forum: Ubuntu Studio
---

### Post by Dedalus1983 on 2016-02-07
I am not sure someone already answered this, but I cannot find a similar situation.

I have a Dell Inspiron notebook, 1TB hard disk. I did 4 partition there, meant to be: 

sda1 -> ubuntu-gnome 15.10 
sda2 -> ubuntu-studio 15.10 
sda3 -> shared ext4 partition 
sda4 -> shared swap partition

I started with ubuntu-gnome, everything worked very well, it boots without the grub menu (obviously), no problem at all with hardware.

After a couple of weeks, I install (today) ubuntu-studio.

It shows the grub menu (I suppose it uses grub from sda2), and boots well into its distribution, while if I try to boot into ubuntu-gnome (sda1) again, I have a fatal error and boots into recovery mode.

The error says "memory type 2 has not been initialized", something about amdgpu.

So, I use boot-repair distro (live usb key) to restore grub in sda1, now I think is using grub from sda1 but the problem remais.

Can you help me please? What did I do wrong?

(if you need extra information tell me, I can't figure out how to solve it)

Thanks in advance

---

### Post by oldfred on 2016-02-07
Post link to Summary report from Boot-Repair.

Do you have dual video? What video card/chip is it?

Grub may not be initializing correct video mode. 

But I do not know AMD and its required settings.
AMD has obsoleted some old cards/chips and you have to install legacy drivers.

Google search on your error finds posts back to 2010, and rebuilding kernel. I would think by now it should be fixed.

---

### Post by Dedalus1983 on 2016-02-07
Hello oldfred, thanks for replying.

No it's not an old problem, seems to be solved just with kernel 4.5, have a look here:

[https://bbs.archlinux.org/viewtopic.php?id=190236&p=2]("https://bbs.archlinux.org/viewtopic.php?id=190236&p=2")

I am using a 4.2.0-28 as per official ppa, hardware is Amd Radeon.

But I am realizing that this error is not related to the problem I am facing, that is, it was there before when I was using ubuntu-gnome; I just had a look at messages and it is there in the ubuntu-studio dmesg too.
So, it is an error but now it does not concern me.

Wait a minute, I will reboot and send you the Boot-Repair summary.

Thanks

---

### Post by oldfred on 2016-02-07
I have not followed details on AMD, as I have nVidia.
But what I have seen is different generations of cards/chips and different drivers, some better than others. And some older obsoleted so only older driver will work.

This was in release notes:
 With 15.10 Release notes
AMD's fglrx driver does not work with the current kernel


 dual AMD
[http://ubuntuforums.org/showthread.php?t=2288314&p=13329042#post13329042](http://ubuntuforums.org/showthread.php?t=2288314&p=13329042#post13329042)
With the upcoming Linux 4.2 kernel will be the premiere of the new "AMDGPU" 
kernel driver to succeed the "Radeon" DRM kernel driver
[http://tech.slashdot.org/story/15/07/25/2014228/amd-starts-rolling-out-new-linux-driver-model-but-many-issues-remain](http://tech.slashdot.org/story/15/07/25/2014228/amd-starts-rolling-out-new-linux-driver-model-but-many-issues-remain)

---

### Post by Dedalus1983 on 2016-02-07
Solved!

As I figured out, the amd gpu fatal error that it was showed as last before emergency login, but has nothing to do with the error.

It was just that... the installation of ubuntu-studio changed the uuid of sda2 (
where was ubuntu-studio installed). When I booted to ubuntu-gnome in sda1, the fstab still had the old uuid for sda2 and this was enough reason to go emergency mode.

Now everthings's ok. Hope it will be useful to other people.

Thanks you!

---

### Post by oldfred on 2016-02-07
You can change to [Solved].

I have several installs on HDD. And when I over install a very old install with a new one and tick format it does change UUID. Then grub complains if in older grub menu. But I have changed most of my grub menus to boot partitions, using simplified boot stanza and the link to newest kernel in / of install.

Good to know error not related to what it seems, but a bit surprised that a bad UUID, caused that error.

---

