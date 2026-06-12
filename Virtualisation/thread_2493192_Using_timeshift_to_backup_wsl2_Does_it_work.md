---
title: "Using timeshift to backup wsl2 Does it work ?"
date: 2023-12-06
forum: Virtualisation
---

### Post by cedbarth on 2023-12-06
Hi,
I am a noob in restore software, but I am quite interested in it as I have quite frequent BSOD because of a 3rd party driver on windows that enables me to lower the fan speed of my clevo laptop, no other solution found  to lower that laptop constant noise.
 
I'd like to do on a regular basis snapshots of wsl2, ideally live snapshots with linux tool, that would free me from diving into powershell scripting :P

I haven't found any tool stating explicitly the ability to do live snapsphots.
Anyway, I've just started to do a first snapshot of wsl2 and I am wondering if other people do that and if it works .
Thanks for your suggestions !

---

### Post by MAFoElffen on 2023-12-06
It "might"... If you config it to write the snapshots to a Windows Network share, sort of like this:
```

mkdir -P /export/share
sudo mount -t drvfs '\\server\share' /export/share
## or
sudo apt install --yes cifs-utils
sudo mount -t cifs -o user=<user_name>},pass=<password>,vers=1.0 //server/share /export/share

```
I cannot guaranty that will work, but logically it looks like it might.

If timeline doesn't work, it will be for these reasons:

WSL & WSL2 is not full blown Linux. It is the "Windows Subsystem for Linux" which emulates and appears to be a Linux-like system. It does not have a full suite of Linux basic utilities present. It does not connect directly to block devices.

You want a picture of what isn't there? Run the UbuntuForums 'system-info' script inside it, and when it goes through it's check of minimum Linux base utilities used in the script, it will dump out a long list of those basic Linux utilities that are not really present... That will be a quick realization of what it isn't.

I know that some things just will not work with WSL. You can access it from Windows via //wsl$/<distroname> as a psuedo network share... The Windows Doc's say, if you try any other way, then you risk file corruption, as Windows fakes the Linux attributes using external metadata for the files and they need to stay in sync between the two...

Otherwise, I do know these work... This is not the answer you are looking for...

I use these for reference:
[https://medium.com/codex/setting-up-regular-automatic-backup-of-your-windows-subsystem-for-linux-wsl2-data-using-task-b36d2b2519dd](https://medium.com/codex/setting-up-regular-automatic-backup-of-your-windows-subsystem-for-linux-wsl2-data-using-task-b36d2b2519dd)
[https://www.xda-developers.com/how-back-up-restore-wsl/](https://www.xda-developers.com/how-back-up-restore-wsl/)

The next consideration of why it is usually backed up externally, is that it's not like a VM or physical machine, in that you can't boot it externally (like from a LiveUSB Installer or other LiveEnv), to copy the whole system while not mounted, nor restore to an unmounted filesystem while it is running WSLx... You won't be able to recover from a catastrophic failure from inside of WSLx. You 'might' be able to re-install the distro into WSlx, then resync it from the snapshots.

---

### Post by Tadaen_Sylvermane on 2023-12-06
No Bueno. Timeshift needs a physical drive. And it needs a drive compatible with Nix permissions as it creates rsync based snapshots. No permissions your timeshift sync will be useless assuming it let's you do it in the first place.

---

### Post by cedbarth on 2023-12-06
Hi, thanks for your answer
Actually the filesystem within the vhdx file is ext4, it has file permissions. Timesync did a snapshot, I just don't know if it works.
I'll have a try on another wsl distribution that I don't work with and that I don't fear losing

---

### Post by cedbarth on 2023-12-06
post to delete

---

### Post by cedbarth on 2023-12-06
> **MAFoElffen said:**
> It "might"... If you config it to write the snapshots to a Windows Network share, sort of like this:
```

mkdir -P /export/share
sudo mount -t drvfs '\\server\share' /export/share
## or
sudo apt install --yes cifs-utils
sudo mount -t cifs -o user=<user_name>},pass=<password>,vers=1.0 //server/share /export/share

```
I cannot guaranty that will work, but logically it looks like it might.

If timeline doesn't work, it will be for these reasons:

WSL & WSL2 is not full blown Linux. It is the "Windows Subsystem for Linux" which emulates and appears to be a Linux-like system. It does not have a full suite of Linux basic utilities present. It does not connect directly to block devices.

You want a picture of what isn't there? Run the UbuntuForums 'system-info' script inside it, and when it goes through it's check of minimum Linux base utilities used in the script, it will dump out a long list of those basic Linux utilities that are not really present... That will be a quick realization of what it isn't.

I know that some things just will not work with WSL. You can access it from Windows via //wsl$/<distroname> as a psuedo network share... The Windows Doc's say, if you try any other way, then you risk file corruption, as Windows fakes the Linux attributes using external metadata for the files and they need to stay in sync between the two...

Otherwise, I do know these work... This is not the answer you are looking for...

I use these for reference:
[https://medium.com/codex/setting-up-regular-automatic-backup-of-your-windows-subsystem-for-linux-wsl2-data-using-task-b36d2b2519dd](https://medium.com/codex/setting-up-regular-automatic-backup-of-your-windows-subsystem-for-linux-wsl2-data-using-task-b36d2b2519dd)
[https://www.xda-developers.com/how-back-up-restore-wsl/](https://www.xda-developers.com/how-back-up-restore-wsl/)

The next consideration of why it is usually backed up externally, is that it's not like a VM or physical machine, in that you can't boot it externally (like from a LiveUSB Installer or other LiveEnv), to copy the whole system while not mounted, nor restore to an unmounted filesystem while it is running WSLx... You won't be able to recover from a catastrophic failure from inside of WSLx. You 'might' be able to re-install the distro into WSlx, then resync it from the snapshots.

Hi, thanks for your detailed answer
I don't really understand why it would be useful or necessary to use a windows network share .
I haven't told yet that the snapshots are stored on the second disk of my laptop on which there's an ext4 partition.
I'll probably do the usual way that you pointed out, but I am bit pissed  with usb devices connection within wsl. Unless the usb devices get  bound with usbipd, it is quite often busy and tedious to find the  process to kill to enable attach it to wsl using usbipd as I intend to  use borg to backup the ext4 second drive containing user home folder tp  an external usb drive.
It would have been easier for me to keep all the usb backup drives attached constantly to linux.
Your idea of just reinstalling the same distribution, running it and  then using timeshift to restore seems perfect to me as it could enable  to "recover" from a serious crash.
I'll have to make a few tests on another wsl distribution that I don't care losing and that I'll use just for that.

---

### Post by MAFoElffen on 2023-12-06
Like you found out, WSL doesn't do well writing to any physical block devices... But it will mount to a Windows Network share... Which you can setup on the same Windows Host. == It doesn't have to be hosted on another computer.

Even if Timeshift didn't work, you can always rsync to a network share. To anything you can connect to, from inside of WSL. Network shares, whether Windows or Linux are easy ways to use shared data between machines, VM's, Containers, etc, etc.

Personally, On a Windows machine, I would would rather turn on Hyper-V and run a full blown Ubuntu VM. Lest confining. More possibilities. The real deal.

I have done a lot with WSL1 and WSL2, and found both disappointing and limited in what you can actually do, compared to the real thing.

---

