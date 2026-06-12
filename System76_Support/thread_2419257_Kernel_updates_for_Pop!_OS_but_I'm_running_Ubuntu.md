---
title: "Kernel updates for Pop!_OS but I'm running Ubuntu"
date: 2019-05-18
forum: System76 Support
---

### Post by shochatd on 2019-05-18
I have two System76 machines, a Ratel Pro and a Galago Pro. Both are running Ubuntu 19.04. So why am I getting notifications for kernel updates that are identified as being for Pop!_OS? I keep trying to say no, but of course the notifications keep coming back. What would happen if I accepted these?

---

### Post by Frogs Hair on 2019-05-18
What repositories are listed when running the following ? ```
sudo apt update
```

---

### Post by shochatd on 2019-05-19
> **Frogs Hair said:**
> What repositories are listed when running the following ? ```
sudo apt update
```
```

Hit:2 http://dl.google.com/linux/chrome/deb stable Release                                                         
Hit:4 http://us.archive.ubuntu.com/ubuntu disco InRelease                                                          
Get:5 http://security.ubuntu.com/ubuntu disco-security InRelease [97.5 kB]
Hit:6 http://ppa.launchpad.net/system76-dev/stable/ubuntu disco InRelease      
Get:7 http://us.archive.ubuntu.com/ubuntu disco-updates InRelease [97.5 kB]    
Get:8 http://us.archive.ubuntu.com/ubuntu disco-backports InRelease [88.8 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu disco-updates/main amd64 DEP-11 Metadata [82.1 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu disco-updates/main DEP-11 48x48 Icons [13.5 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu disco-updates/main DEP-11 64x64 Icons [22.4 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu disco-updates/universe amd64 DEP-11 Metadata [11.1 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu disco-updates/universe DEP-11 48x48 Icons [8,722 B]
Get:14 http://us.archive.ubuntu.com/ubuntu disco-updates/universe DEP-11 64x64 Icons [11.8 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu disco-backports/universe amd64 DEP-11 Metadata [7,232 B]
Get:16 http://security.ubuntu.com/ubuntu disco-security/main amd64 DEP-11 Metadata [17.8 kB]
Get:17 http://security.ubuntu.com/ubuntu disco-security/universe amd64 DEP-11 Metadata [1,744 B]
Get:18 http://security.ubuntu.com/ubuntu disco-security/universe DEP-11 48x48 Icons [6,157 B]

```

---

### Post by Frogs Hair on 2019-05-19
Were there any updates offered after running the command  or was the system up to date ?

---

### Post by shochatd on 2019-05-19
> **Frogs Hair said:**
> Were there any updates offered after running the command  or was the system up to date ?
Yes.
```

linux-generic/disco 5.0.0.15.16pop0 amd64 [upgradable from: 5.0.0.15.16]
linux-headers-generic/disco 5.0.0.15.16pop0 amd64 [upgradable from: 5.0.0.15.16]
linux-image-generic/disco 5.0.0.15.16pop0 amd64 [upgradable from: 5.0.0.15.16]
```
Those are the same ones that I was referring to in my original post.

---

### Post by PhilGil on 2019-05-19
> **shochatd said:**
> ```

Hit:6 http://ppa.launchpad.net/system76-dev/stable/ubuntu disco InRelease      

```

You have the System 76 ppa enabled. Your system is trying to update the kernel because it's newer than the one in Ubuntu 18.04. You either need to disable the repo or use apt-pinning to set it to a lower priority than the Ubuntu repos.

It probably wouldn't break your system if you upgraded to the System 76 kernel, but your system is likely to be more stable if you use the kernel that ships with your distro.

---

### Post by Frogs Hair on 2019-05-19
You should be able to disable the source from software and updates/other software. Pop doesn't use Grub, so the previous post is good advice.

>  systemd-boot bootloader and the automatic configuration tool we’ve created for it called kernelstub replace the outdated GRUB bootloader used on Ubuntu. The systemd-boot bootloader is faster and smaller in size, increasing your computer’s startup speed.

[https://pop.system76.com/docs/difference-between-pop-ubuntu/](https://pop.system76.com/docs/difference-between-pop-ubuntu/)

---

### Post by shochatd on 2019-05-19
> **PhilGil said:**
> You have the System 76 ppa enabled. Your system is trying to update the kernel because it's newer than the one in Ubuntu 18.04. You either need to disable the repo or use apt-pinning to set it to a lower priority than the Ubuntu repos.

It probably wouldn't break your system if you upgraded to the System 76 kernel, but your system is likely to be more stable if you use the kernel that ships with your distro.

I do have a System76 machine (two of them). So I do want things from them that are relevant in that sense, such as the System76 Driver. But these kernel updates say that they are somehow specific not to System76 hardware, but to Pop!_OS, which is something else, and is something I am *not* running. I do realize that Pop!_OS is from System76.

---

### Post by PhilGil on 2019-05-19
> **shochatd said:**
> I do have a System76 machine (two of them). So I do want things from them that are relevant in that sense, such as the System76 Driver. But these kernel updates say that they are somehow specific not to System76 hardware, but to Pop!_OS, which is something else, and is something I am *not* running. I do realize that Pop!_OS is from System76.

The Pop!_OS kernel is in the ppa, so you're going to be asked to install it. It's not ideal, but the disabling the PPA won't uninstall the packages you've already installed. It will, however prevent them from being updated, so it's a good idea to occasionally re-enable the repo and check that the packages you have installed are up to date.

Alternately, you can try [pinning]("https://help.ubuntu.com/community/PinningHowto")

---

### Post by shochatd on 2019-05-20
> **PhilGil said:**
> The Pop!_OS kernel is in the ppa, so you're going to be asked to install it. It's not ideal, but the disabling the PPA won't uninstall the packages you've already installed. It will, however prevent them from being updated, so it's a good idea to occasionally re-enable the repo and check that the packages you have installed are up to date.

Alternately, you can try [pinning]("https://help.ubuntu.com/community/PinningHowto")
Thank you for these suggestions. I'll need to study that pinning Howto, but I'm also going to ask the folks at System76 about this.

---

### Post by shochatd on 2019-05-20
I called System76 technical support and they told me that a recent security update from the regular Ubuntu kernel had dropped some changes that are needed for some of their machines (newer than mine) so they put out this update to restore those patches. In other words, it should have no effect on my machine. None of this has anything to do with Pop!_OS specifically, so I'm wondering why they labeled it that way, but no matter.

---

### Post by Frogs Hair on 2019-05-20
Good to know ! Perhaps more people are selecting Pop which is the default option when they order their computers.

---

### Post by shochatd on 2019-05-20
> **Frogs Hair said:**
> Good to know ! Perhaps more people are selecting Pop which is the default option when they order their computers.
Yes it is. My Galago Pro (laptop) came with it and I installed Ubuntu over it. I guess I want to be in the larger community.

---

