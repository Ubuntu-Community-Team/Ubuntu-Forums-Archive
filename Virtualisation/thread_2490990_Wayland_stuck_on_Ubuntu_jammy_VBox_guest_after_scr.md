---
title: "Wayland stuck on Ubuntu jammy VBox guest after screen unlock on Windows host"
date: 2023-09-22
forum: Virtualisation
---

### Post by phormion on 2023-09-22
Hi,

I have an Ubuntu 22.04 VM running on VirtualBox 7.0.10, the host OS being Windows 10. Ubuntu was installed from scratch (not updated from a previous version), the default GNOME flavor, and it seems to be using Wayland. Now, the Windows screen locks after a certain timeout and I've noticed that most times, when unlocking the (Windows) screen, the Ubuntu UI seems hung: the keys don't seem to be working and neither is the mouse. I can, however, go to a tty console (Ctrl-Alt-F3, I was confused that C-A-F1 did not work anymore and first thought the OS was stuck) and from there reboot. Is this a known problem? Is there a way to restart wayland from the console, rather than restarting the machine?

---

### Post by TheFu on 2023-09-22
You need to prevent Windows from harming the virtual machines running under it.  There are multiple solutions, but best would be NOT to allow sleep/standby/hibernation modes in Windows.

Also, have you installed the vbox guest additions?

---

### Post by MAFoElffen on 2023-09-24
What I do to end a frozen desktop from a vtty is
```

de_pid=$(pidof gdm3)
sudo kill $de_pid

```
It will kill the Desktop Environment and return to the graphical login screen (the DM, aka Desktop Manager).

+1 on the question about vbox guest additions.

---

### Post by phormion on 2023-09-25
I have the guest additions installed, yes. I had an old VM running on the same Windows just fine, with the exception of copy/paste not working after a resume (which still happens). Any suggestion on how to check what possibly went wrong on the Wayland side?

---

### Post by TheFu on 2023-09-25
Every time there is a new vbox or a new kernel, the current guest additions for the specific vbox version need to be reinstalled. A single install 3 months ago isn't likely to work today.

---

### Post by phormion on 2023-09-25
I'm pretty sure I have the latest installed, I checked in Machine > Session Information  > Runtime Information. It says: 

> 
Guest Additions: 7.0.10 r158379


---

### Post by phormion on 2023-09-25
> **MAFoElffen said:**
> What I do to end a frozen desktop from a vtty is
```

de_pid=$(pidof gdm3)
sudo kill $de_pid

```


Sorry, I missed your reply earlier today. That's a good suggestion, thanks. I guess this would be a more low level equivalent of

```
systemctl restart gdm
```

right?

---

### Post by MAFoElffen on 2023-09-26
Yes. 

As for having to rebuild vbox'es modules after a kernel update... That is how it used to be. Up until a few years ago, if you just had the default packages installed...

At around 2014, VirtualBox added package 'virtualbox-dkms' as an optional package that "was supposed" to do that for the user when the kernel updates. But it was an optional, user installed package. 

Since around VirtualBox 5.2, that functionality was added to the main package by default. In Ubuntu 22.04 that optional package was removed from the Ubuntu Repo's even though, it was not needed for a few years by then.

Though, sometimes that process still fails, and the modules have to be rebuilt. The world is not perfect.

You never answered if you had 3D Acceleration turned on for the guest(?)

Other than that... Then it's a Windows and VirtualBox for Windows issue. The default video for Ubuntu running within VBox has o reported problem at this time. I see no one else having this issue since about 2021 with Windows 10. Then it had something to do with speakers in displays.

Did you check your VM Guest LOG file at similar to C:\Users\UserName\VirtualBox VMs\VmName\Logs\VBoxSVC.log? Or similar... It's been awhile since I have used VBox. I switched to just using KVM and Hyper-V...

---

### Post by phormion on 2023-10-03
Hm, sorry if I missed the question about 3d acceleration. It seems to be off in Machine > Settings > Display.
Yes, the way the modules are rebuilt is tricky; dkms does not fix compilation problems, I guess.

VirtualBox 7 has been a real gem of a release: offered to resize my VMDK disk, then managed to corrupt it irreversibly; this screen freezing is small stuff :). Anyway, the workaround with restarting gdm works (though you lose your workspace). Any idea on what log I can check to see what is malfunctioning on the Wayland end? Is there a Wayland log?

Later: about the suggestion to check the VBox log, I'll check it next time this happens. I did first ask about this on the virtualbox forums and uploaded my log, but it didn't look the people there found any useful info inside.

---

