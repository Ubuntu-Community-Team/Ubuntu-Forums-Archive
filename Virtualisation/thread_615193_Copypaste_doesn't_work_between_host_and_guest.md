---
title: "Copy/paste doesn't work between host and guest"
date: 2007-11-16
forum: Virtualisation
---

### Post by brodym on 2007-11-16
Hi,

I'm using VMWare. Here's my setup:

Host: Ubuntu 7.10
Guest: Vista (VMWare Tools are installed)

In VMWare Server Console, Edit/Preferences shows "Enable copy and paste to and from virtual machine" is checked.

Still, I cannot get copy and paste to work between the guest and host.
What am I doing wrong?

Thanks for your help!

---

### Post by brodym on 2007-11-19
No replies?

---

### Post by Lem on 2007-11-19
Which vmware are you using? VMPlayer 2 has drop'n'drop functionality between host and VM which I believe is unique amongst the free products.

---

### Post by brodym on 2007-11-19
Thanks for your reply. I'm running VMware Server 1.0.4 build-56528.

---

### Post by tighem on 2007-11-19
VMWare Server does this with the guest tools installed and the option selected in the client interface (it runs in the toolbar under XP).

---

### Post by SgtDude on 2007-11-19
tighem's right, for the copy/paste to/from host/guest machine, the vmware tools have to be instaled on the guest machine.  Depending on the OS running on the guest machine this can be really easy or extremely difficult but the first step is to right click on the machine in the list (on the left) and click "Install VMware tools".  (don't quote me on that, I'm running off of memory)

This will mount a disk image in place of whatever you have mounted to the guest CDROM.  On this CD is the .exe file for windows and a .rpm and a .tar.gz for linux (again, running off my spotty memory).  That should get you started.  Post back here if you get stuck.

---

### Post by brodym on 2007-11-20
Thank you for your suggestions.

As I mentioned in my original post, VMware Tools are running
on the guest (Vista). The VMware Tools icon is showing in the toolbar,
though I don't see any option to enable copy/paste in VMware Tools.

Copy/paste is enabled in VMware server settings.

---

### Post by as1 on 2007-12-31
Hey,
Has anyone been able to resolve this question? I am also experiencing the same problem with VM Server software - cannot copy and paste despite ticking the relevant box and installing (and runnning in the taskbar of windows xp guest operating system) vm tools.

Does anyone know why?

Thanks
Andrew.

---

### Post by fjgaude on 2007-12-31
I'm sure I don't why it works for me and not you. I run VMware 1.0.4 and WinXP and do copy/paste perfectly. I couldn't do that in VBox. Thus I only use VMware Server now, the free kind.

I run NAT and also have SAMBA shares setup on Ubuntu host. Other than that, that's it.

---

### Post by as1 on 2008-01-01
Hey,
I'm not sure about the SAMBA stuff (not sure what it is...) but I am also using NAT for the network connection and the internet on my virtual OS works perfectly. 

When you copy and paste, do you literaly just highlight something on your host machine and right click COPY and then PASTE on the desktop (for example) of your virtual machine? Or do you put the files somewhere else like your working directory for the virtual OS?

I'm finding this really confusing! I don't get why it does not work.... I just want to be able to run itunes in windows because some of the music I purchased using istore does not work with linux ipod/music software....

Andrew.

---

### Post by as1 on 2008-01-01
HI,
Just a quick update:

I realised that I could in fact copy and paste - it's just that I cannot copy/paste programs/folders etc.. - only (for example) lines of text from a text editor in the host machine to a text editor in the guest machine. Is this the case with you guys?

I got around the fact that I couldn't copy and paste programs etc. (i.e. word documents created in windows guest machine to my ubuntu host machine) by creating a SAMBA share as per this tutorial:

[http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/](http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/)

Though if anyone figures out how to copy and paste files that would be greatly appreciated.

Many Thanks
Andrew.

---

### Post by fjgaude on 2008-01-01
> **as1 said:**
> Hey,
I'm not sure about the SAMBA stuff (not sure what it is...) but I am also using NAT for the network connection and the internet on my virtual OS works perfectly. 

When you copy and paste, do you literaly just highlight something on your host machine and right click COPY and then PASTE on the desktop (for example) of your virtual machine? Or do you put the files somewhere else like your working directory for the virtual OS?

I'm finding this really confusing! I don't get why it does not work.... I just want to be able to run itunes in windows because some of the music I purchased using istore does not work with linux ipod/music software....

Andrew.

You can read this how-to and that might help:

[http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/](http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/)

I copy/paste from one program to another across the host/guest. I don't remember if I have done it desktop to desktop.

Happy New Year!

---

### Post by Tex-Twil on 2008-01-03
Hi,
I also have VMware server installed and the copy/paste (of text only) is not working. I installed vmware tools on the guest correctly and enabled the option in the host's Edit->Preferences->Input option dialog.

Thanks,

---

### Post by fjgaude on 2008-01-03
> **Tex-Twil said:**
> Hi,
I also have VMware server installed and the copy/paste (of text only) is not working. I installed vmware tools on the guest correctly and enabled the option in the host's Edit->Preferences->Input option dialog.

Thanks,

Try rebooting the machine after setting the copy/paste feature. I have no othe suggestion for simply copying lines of text from host to guest and back. Of course you have to use SAMBA to copy, move whole files and the like because the Windows stuff is in NTFS format, but text bites and pieces are not and can be handled by the clip board of both Windows and Linux.

---

### Post by Tex-Twil on 2008-01-03
> **fjgaude said:**
> Try rebooting the machine after setting the copy/paste feature. I have no othe suggestion for simply copying lines of text from host to guest and back. Of course you have to use SAMBA to copy, move whole files and the like because the Windows stuff is in NTFS format, but text bites and pieces are not and can be handled by the clip board of both Windows and Linux.

I did it but it stil doesnt work. Im not interested in copying **files** ( I use ssh for this purpose) I only want the  text copy/apste feature.

btw, both host and guest are Debian.

---

### Post by fjgaude on 2008-01-03
Likely Debian is the issue... I use Ubuntu Gutsy 64-bit on three machines.

---

### Post by gm.matias on 2010-02-12
I am using VMPlayer and in the configuration I enabled the Share Files options but it did not work for me. I read some more articles and found a good solution that works for me. I put in here: [http://www.gmmatias.com/sharing-a-disk-drive-of-an-ubuntu-host-to-a-guest-windows-on-vmplayer-using-samba-2010-02-12](http://www.gmmatias.com/sharing-a-disk-drive-of-an-ubuntu-host-to-a-guest-windows-on-vmplayer-using-samba-2010-02-12)

Hope it helps.

---

