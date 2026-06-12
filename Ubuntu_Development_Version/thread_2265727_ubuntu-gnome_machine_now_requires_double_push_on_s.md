---
title: "ubuntu-gnome machine now requires double push on start button"
date: 2015-02-17
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-02-17
I'll have to investigate further - but ubuntuGnome update killed my PC. (It appears).

I could not shut down from the panel and so used terminal (Ctrl+Alt+F1) sudo reboot and I got the  <starting session 128> and my machine shut off and will not restart. There is no smoke or anything .. green light is still on but wull just not boot. I pulled the power cord out..etc.. reset .. but looks like the update bricked my mobo.

 Ok .. I had to double throw the power on button and it started.

```

ventrical@ventrical-System-Product-Name:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Vivid Vervet (development branch)
Release:    15.04
Codename:    vivid
ventrical@ventrical-System-Product-Name:~$ uname -a
Linux ventrical-System-Product-Name 3.18.0-13-generic #14-Ubuntu SMP Fri Feb 6 09:55:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
ventrical@ventrical-System-Product-Name:~$ 


```

---

### Post by ventrical on 2015-02-17
Looks like it may be this bug.

[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1422776](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1422776)

---

### Post by kansasnoob on 2015-02-17
Me too. I feared a hardware brick but after clearing the CMOS all seems well so far, of course that meant having to go back thru BIOS and reset all of my preferred tweaks.

---

### Post by ventrical on 2015-02-17
wow. Thanks for affirming that.  I was ready to do a tear down.  Now they have a Windows 8 Metro thingy at the shutdown process.  It really spooked me.

All I do now is pull the  power cord out  for 10 seconds and it will reboot.

---

### Post by mc4man on 2015-02-17
The bug you reported is duped to one from 16 days ago, hopefully is really the same. Maybe one of these things that gets fixed before any bug does..

---

### Post by ventrical on 2015-02-17
> **mc4man said:**
> The bug you reported is duped to one from 16 days ago, hopefully is really the same. Maybe one of these things that gets fixed before any bug does..

I hope so too. I just let apport take the lead on this one. If I get time I'll take a video and put it up.

edit:

Here is clunky video of the problem..


[https://www.youtube.com/watch?v=ixMS_rCaaKE&feature=youtu.be](https://www.youtube.com/watch?v=ixMS_rCaaKE&feature=youtu.be)

---

### Post by grahammechanical on 2015-02-17
Did you notice this

systemd-logind [1286]: failed to start user service: unknown unity user .... something that is too blurred to see. Does this happen with upstart?

Regards.

---

### Post by sammiev on 2015-02-17
I'm not getting any of that. Boot and shutdown are normal on Ubuntu-Gnome 15.o4 with a fresh install from last Friday and updated to a few hours a go.

No systemd errors at all.

> sam@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Vivid Vervet (development branch)
Release:	15.04
Codename:	vivid
sam@ubuntu:~$ uname -a
Linux ubuntu 3.18.0-13-generic #14-Ubuntu SMP Fri Feb 6 09:55:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
sam@ubuntu:~$ 

---

### Post by ventrical on 2015-02-18
> **grahammechanical said:**
> Did you notice this

systemd-logind [1286]: failed to start user service: unknown unity user .... something that is too blurred to see. Does this happen with upstart?

Regards.

Yes . I am booting into default, not systemd. I had seen that error. Hmmm...   This install has been nurtured from the beginning so it is not fresh install.  I will try a few things and get back.  I do not have unity8 or other desktop alongside it. It is bare metal ubuntuGnome methinks... I'll have to check that and make sure too. Maybe my bad?

edit:

 Mouse is gone. Now it locks up the whole KVM array until I unplug it. All the other installs I have currently running are working just fine .. so it is not PC hardware failing. Behaves like malware.

edit:

 Also tried other kernels.. same things now. I was working with 3.18.0-11 but now all the kernels will not work from recovedry/root. I run /top/ and it just locks up after I exit.

---

### Post by ventrical on 2015-02-23
I discovered this purely by accident.  I was using my USB docking station device for SATA hdds and discovered that the hdd I was using for my 15.04 ubuntuGnome install (from beggining) had some of the remaining Windows 8 UEFI partitons that I had previously used on that same drive.  Ubiquity and other installs I have on that hdd would not show up using gparted or <disks> utilities but they all came up while using my USB SATA docker.

  I think this is why I am having problems with the bootup/shutdown of ubuntuGnome 15.04 daily upgrades.

 So the real bug is that when installing ubuntuGnome via ubiquity it did not wipe all the other partitons (as it said it was going to do) It only hid them until now.

@kanasanoob&oldfred

You may find the above interesting , or not.

---

### Post by ventrical on 2015-02-23
I proceeded to remove all of the existing Windows partitions including BIOS/BOOT and then swapped the hdd to the original machine. I first went to terminal and:

```


sudo update-grub

```

and I got several ufs errors (could not capture in that state) so perhaps it is in grub log. I update/upgraded and ran update-grub once again and the errors appeared to have gone. I have not hard booted yet, but I am about too.

  I just wanted to comment that I am totally surprised that these partitions were hidden from Ubiquity, gparted and ubuntu disks utility and that I had to use a USB SATA docking station to discover that this crud was still on the hdd.


Regards..

---

### Post by ventrical on 2015-02-23
Shutdown/KVM lock error is gone. There is still the GDM bug  which I had already filed a bug for which is a dupe.

To start gnome-shell in stable I have to use Ctrl+Alt+F1 and then:

```

sudo service gdm restart

```

and gnome3 will start stable and log on.

Regards..

---

### Post by ventrical on 2015-02-26
This gnome install will run without glitch when I choose systemd from grub.

Just keeping updated here.

Using 4.x.x-x kernel.

---

### Post by sammiev on 2015-02-26
> **ventrical said:**
> This gnome install will run without glitch when I choose systemd from grub.

Just keeping updated here.

Using 4.x.x-x kernel.

I had to run systemd because of all this, even posted on this back about 3 weeks a go.

Thanks for the work around on upstart.

---

