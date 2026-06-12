---
title: "VirtualBox modprov error"
date: 2023-05-29
forum: Virtualisation
---

### Post by Tom_ZeCat on 2023-05-29
I've installed VirtualBox 6.1.38 with the intent of installing Windows 7 and Win 2K under it, exactly how I did on my old Dell PC.  However, when I was trying to install Win 7, VirtualBox would not let me.  It gave me the following error message: 

```

The VirtualBox Linux kernel driver is either not loaded or not set up correctly.  Please reinstall virtualbox-dkms package and load the kernel module by executing: 

‘modprobe vboxdrv’

as root.  

If your system has EFI Secure Boot enabled you may also need to sign the kernel modules (vboxdrv, vboxnetfit, vboxnetadp, vboxpci) before you can load them.  Please see your Linux system's documentation for more information.  

where: suplibOsInit what: 3 VERR_VM_DRIVE_NOT_INSTALLED (-1908)- The support driver is not installed.  On linux, open returned ENOENT.  


```

????  Before installing Kubuntu 22.04 LTS on this PC, I made sure to go into the BIOS and disable the EFI Secure Boot thing.  

I've googled around, trying to find the solution, and I did find a page that suggested doing this on the command line: 

```

sudo pacman -Syu linux-headers

```

However, I think that might be a practical joke.  When I look up "pacman" in Muon Package Manager, it's simply a game based on the 1980s classic arcade game.  That couldn't possibly be relevant.  

As near as I can tell from my googling, I'm missing some kind of Oracle driver.  Is that correct?  One difference between this PC and the old one is I used Open Java in this one while I installed Oracle Java on the old one.  Maybe this Oracle driver got installed somehow on the old PC when I installed Oracle Java?  

Or maybe the VirtualBox install from Kubuntu's Discover Software Center was incomplete for some reason, though that is exactly how I installed it on the old PC.  Should I uninstall and re-install via some kind of PPA?  

But I'm not even sure that's right.  If anyone here understands what's going on and could shed some light on how I might fix this, I would be extremely grateful.  Thank you so much.

---

### Post by SeijiSensei on 2023-05-29
> The VirtualBox Linux kernel driver is either not loaded or not set up correctly.  Please reinstall virtualbox-dkms package and load the kernel module by executing: 

&#8216;modprobe vboxdrv&#8217;

as root.  

VirtualBox requires a proprietary kernel driver. Run "sudo apt install virtualbox-dkms" as instructed followed by "sudo modprobe vboxdrv".

When I used VB in the past, I always used the PPA and never the repository version.

You might consider migrating to the built-in support for virtual machines via KVM. Works fine with much less overhead.
[https://www.tecmint.com/install-kvm-on-ubuntu/](https://www.tecmint.com/install-kvm-on-ubuntu/)

Ubuntu doesn't directly use pacman, a different packaging scheme.

---

### Post by Tom_ZeCat on 2023-05-29
> **SeijiSensei said:**
> VirtualBox requires a proprietary kernel driver. Run "sudo apt install virtualbox-dkms" as instructed followed by "sudo modprobe vboxdrv".

When I used VB in the past, I always used the PPA and never the repository version.

You might consider migrating to the built-in support for virtual machines via KVM. Works fine with much less overhead.
[https://www.tecmint.com/install-kvm-on-ubuntu/](https://www.tecmint.com/install-kvm-on-ubuntu/)

Ubuntu doesn't directly use pacman, a different packaging scheme.

Thank you.  I very much appreciate your efforts to help me.  I have good news and bad news.  The bad news is that I tried your suggestion, but it failed.  The good news is I found another solution that worked.  

When I ran "sudo apt install virtualbox-dkms", I got the message that it's already installed.  Then, when I ran "sudo modprobe vboxdrv", I got this error message: 

```
modprobe: ERROR: could not insert 'vboxdrv': Key was rejected by service
```

So I googled that error message and got more info.  I found the posts by someone having the same problem.  They talked about how this Dell "secure boot" feature of the EUFI was protecting the system by not allowing another OS to install.  The thing is, I disabled secure boot when I first installed Kubuntu on this thing, or I thought I did.  The solutions proposed involved running a bunch of commands to make an exception for modprobe that secure boot will know to ignore.  However, I simply went into the BIOS and disabled secure boot.  I think when I disabled it before, it re-enabled itself protecting Ubuntu as the system OS instead of Windows.  But I don't do a bunch of risky computing on nefarious web sites, so I think I'm fine with that.  I disabled secure boot, and now Windows 7 installs fine under VirtualBox.  

I've saved your info on that KVM program in my CherryTree database of my Kubuntu install notes.  I'll keep that in mind if I ever decide to use something other than VirtualBox.  It's good to know that there's another option.  

I appreciate all your help.  Even though your suggestion was not the final solution, it lead me to the right info.  I've updated my situation in case this info ends up helping someone else.  I'm marking this thread solved.

---

