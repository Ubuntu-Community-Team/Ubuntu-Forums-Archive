---
title: "Guest additions for VBox don't work on Lucid Lynx"
date: 2010-01-16
forum: Virtualisation
---

### Post by patman0623 on 2010-01-16
I am running the most up-to-date version of VirtualBox. My host OS is 9.10 Karmic; the guest OS is 10.4 Lucid Alpha 2, installed on the same virtual hard disk as a Win XP disk.

When I go to install guest additions directly from the iso image (acting as a CD), and restart, nothing happens, I still have a separate mouse. It believe it's saying it's compiling the guest additions from scratch.

Am I doing something wrong? I tried to install guest additions from the repository, without luck it appears.

---

### Post by Perryg on 2010-01-16
I find a temporary work around is to create /etc/X11/xorg.conf and add the following will get the mouse integrations working in 10.04
```
Section "InputDevice"
        Identifier  "VBoxMouse"
        Driver      "vboxmouse"
        Option      "CorePointer"
EndSection
```
Screen resolution was not effected. If you are having other problems besides the mouse please explain.

---

### Post by patman0623 on 2010-02-17
After installing kernel version 2.6.32.13, this workaround no longer is effective. I tried to uninstall then reinstall virtualbox-guest-additions, but it is not working.

---

### Post by Perryg on 2010-02-17
Strange I run my 10.04 seamless 24/7 and it is fully up-to-date as of today running on VBox 3.1.4 PUEL.  It has the mouse entry in the xorg.conf and works just fine.  Did you have dkms installed so when the kernel updated it recompiled your VBox kernel and did you make sure that the headers matches the kernel?  The VBox DEVs are tell me that by the next maintenance release of VBox you will not need the mouse statement in the xorg.conf file.

---

### Post by patman0623 on 2010-02-17
I have dkms installed. As for the headers installed, I don't even understand, let alone can I say yes or no.

---

### Post by Perryg on 2010-02-17
You didn't by chance do a partial update to 10.04 a few days ago did you?  I never do and wait until I see the updates are in sync.  If so you may need to do a dist-upgrade.

---

### Post by mkvnmtr on 2010-02-17
When you say you installed did you just click on the top of the window to install or did you run the installation from the installation file?
Normally I find the file in the guest additions and right click on it and it offers me the option to execute. If it does not I open the file and cut and paste it into th terminal and run it there. I believe it is the file that says install.sh.

---

### Post by patman0623 on 2010-02-18
I actually installed it via both methods, after installing 10.4, kernel 32.10. And it worked great. I upgraded to VBox 3.14, and it still worked. Then I upgraded to kernel 32.13 (32.11 didn't even seem to want to boot, so I disabled it), and now it doesn't work. 

This time I reinstalled via the virtual CD instead of the Ubuntu repository, and it worked, thanks all.

---

