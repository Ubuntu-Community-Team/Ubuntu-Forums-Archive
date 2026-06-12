---
title: "&quot;Give root password for maintenance&quot; after upgrading from 14.04 LTS to 16.04 LTS"
date: 2016-09-09
forum: Server Platforms
---

### Post by ehamdja on 2016-09-09
Hi,

I am newbie to ubuntu so bear with me. I just upgraded my server from 14.04 LTS to 16.04 LTS through do-release-upgrade. After it says completed i reboot the system and now it gives me "give root password for maintenance" I used to access it from webmin or shellinabox but now i can't. Any help what to do to fix this? Thank you in advance.

---

### Post by ehamdja on 2016-09-15
Anybody that might be able to help? Any guide or link?

---

### Post by steeldriver on 2016-09-15
Do you have physical access, or is this a remote server?

IIRC "give root password for maintenance" indicates that you set a root password (enabling root login) - otherwise it would have dropped directly to a root shell, I think

---

### Post by ehamdja on 2016-09-15
It's a remote server. Right now I can only access it physically (after the upgrade) no more remote access (I use webmin and shellinabox to access). I can login to root using the root password but it seemed nothing was loaded because of the prompt "give root password for maintenance". Any idea?

---

### Post by steeldriver on 2016-09-15
So it's some kind of hosted server? by "physically" I guess you are referring to some kind of remotely accessible control panel provided by the host?

Do you get a root shell if you type the root password at that point? The filesystem may initially be mounted read-only.

---

### Post by ehamdja on 2016-09-15
Sorry for the confusion, i was running headless server but i had access to it by login directly from the server machine and also remotely before. Now after the upgrade i can't login remotely anymore. Yes i can get to root shell by inputting the root password. But can no longer access it remotely from web browser using webmin nor shellinabox.

---

### Post by steeldriver on 2016-09-15
Well that suggests that it's not restarting all the necessary services (sshd and so on) - for example, what does

```

systemctl status ssh

```

say?

---

### Post by ehamdja on 2016-09-15
ssh.service - openBSD Secure Shell server
  Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: enabled)
  Active: inactive (dead)

Feb 11 08:29:31 erickh-odroidXU4 systemd[1]: Stopped OpenBSD Secure Shell server

---

### Post by SeijiSensei on 2016-09-15
Often when you get the "maintenance" error you need to run fsck against the filesystem. If you can get to a root prompt, you can force a filesystem check at reboot like this:
```
sudo mount -o remount,rw /
sudo touch /forcefsck
sudo reboot

```
Notice there is no space in "remount,rw".  

This is the only way to check the main filesystem since you cannot run fsck against a mounted filesystem.  The other option is to boot from a CD/DVD then run "sudo fsck /dev/sda1" assuming that's where the Linux installation resides.  If you're not sure which partition holds Linux, then run "sudo blkid" first.  That will provide a complete inventory of all partitions on all drives in the system.

---

### Post by ehamdja on 2016-09-16
I tried the first option that you recommended and reboot but after that still the same asking the "give root password for maintenance".
I can't do second option since im running my home server using OdroidXU4 (similar to raspberry pi) where i don't have cd/dvd drive. Any more suggestion? Thank you.

---

### Post by ehamdja on 2016-09-16
Okay i think i might solve my own problem. Apparently i have fstab configured for external drives in 14.04 LTS and forgot to plug the external drives through USB. Once i plugged it, everything run smoothly no more "give root password for maintenance. My question is, when in 14.04 whenever i forgot to plug the external USB drive, it will ask me if i want to skip disk check by pressing ctrl c instead of giving me root password for maintenance. Why in 16.04 did not give the same prompt but instead asking me root password for maintenance?

---

