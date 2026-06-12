---
title: "Run fsck on root filesystem"
date: 2020-10-26
forum: Virtualisation
---

### Post by pitchshift on 2020-10-26
I am running Ubuntu Server 18.04.5 as a VM using VMWare 6.2. At login I get the following message - "/dev/sda2 should be checked for errors". This is my root filesystem. I'm not great with Linux so the solutions I have tried I found via Google search. Here's what I've tried so far..


[LIST]
[*]Run 'sudo touch /forcefsck', nothing happened on reboot
[*]Run fsck from the recovery menu, get the following error - "/lib/recovery-mode/recovery-menu: line 80: /etc/default/rcs: no such file or directory fsck from util-linux 2.31.1"
[*]Booted into ubuntu-18.04.5-live-server-amd64.iso, but no option to enter terminal and 'CTRL ALT T' does not respond using VMWare Remote Console
[/LIST]

Google results isn't giving me anymore options so any advice offered would be greatly appreciated.

---

### Post by slickymaster on 2020-10-26
Thread moved to **Virtualisation** for a better fit

---

### Post by TheFu on 2020-10-26
> **pitchshift said:**
>  
[LIST]
[*]Run 'sudo touch /forcefsck', nothing happened on reboot
[*]Run fsck from the recovery menu, get the following error - "/lib/recovery-mode/recovery-menu: line 80: /etc/default/rcs: no such file or directory fsck from util-linux 2.31.1"
[*]Booted into ubuntu-18.04.5-live-server-amd64.iso, but no option to enter terminal and 'CTRL ALT T' does not respond using VMWare Remote Console
[/LIST]

Google results isn't giving me anymore options so any advice offered would be greatly appreciated.

Well, crap.  
Is the storage encrypted or using LVM or ZFS or btrfs?  Those shouldn't break using the "Recovery" menu method, but if that is the situation, ouch.

The **sudo touch /forcefsck** method stopped working when systemd was introduced.

Which means the only possible answer is to boot from alternate media, manually determine the correct device file, and run the fsck against that device file.  Any Desktop Ubuntu flavor for the same release number (18.04 is close enough) can be used, just go into the "Try Ubuntu" option.  Then you have a GUI and multiple terminals to get the **lsblk** output, handle any LUKS commands or LVM commands to get the storage seen, and can run **fsck** in another terminal.

So, the first step is to say which file systems, encryption, ZFS, LVM, etc ... are used so we don't go down the 50,000 options.

I think there is a grub command option to force an FSCK, but since systemd took over, I've not used it and before then, I just used the touch /forcefsck method.  [https://www.linuxuprising.com/2019/05/how-to-force-fsck-filesystem.html](https://www.linuxuprising.com/2019/05/how-to-force-fsck-filesystem.html) option 2. Not that the fstab has to be correctly setup too. Lots of people have fsck checking disabled in their fstabs for some reason.  Use **sudoedit /etc/default/grub** to modify the grub boot command as the link says.  All the examples in this link assume you are not using encryption or LVM. If you are, all the device names are different.

---

### Post by ajgreeny on 2020-10-26
I don't know vmware but when I used VBox I just inserted an iso of a lubuntu live system into the virtual CD drive of that VM, quickly pressed F12 when booting the VM to select boot device, chose to boot the iso and used that live Lubuntu system to run fsck on the VM.

It worked just as it would if I was doing the same on a bare metal install.
Does vmware have such a facility?

---

### Post by TheFu on 2020-10-26
I took the exact error message and googled it:
[https://askubuntu.com/questions/1149957/unable-to-login-to-account-in-ubuntu-18-04-vmware-workstation-15-after-update](https://askubuntu.com/questions/1149957/unable-to-login-to-account-in-ubuntu-18-04-vmware-workstation-15-after-update)
That points to something related to using Wayland for gdm. Some people have X11 enabled, but gdm was still using Wayland. A few different fix options are offered.

---

### Post by pitchshift on 2020-10-27
No encryption is enabled, I will try mount a desktop Ubuntu ISO and see if I can get to terminal that way.

---

### Post by pitchshift on 2020-10-27
I booted into Ubuntu desktop ISO and was able to run fsck on the root partition successfully and is now showing as clean.

I still get the error message on boot. I ran fsck again and it's still showing as clean. How do I manually remove this message?

---

### Post by pitchshift on 2020-10-27
Found a fix [https://www.linuxuprising.com/2019/05/how-to-force-fsck-filesystem.html](https://www.linuxuprising.com/2019/05/how-to-force-fsck-filesystem.html)

I probably could have done this rather than booting into Ubuntu desktop. Learnt something new I guess. Thanks for the support.

---

