---
title: "PROBLEM with VirtualBox Guest Additions"
date: 2013-10-27
forum: Virtualisation
---

### Post by daviderix on 2013-10-27
Dear all,
I'm a total Noob in using Linux so please be kind with me.
Since I needed to use a Linux machine, I installed VirtualBox on my Windows 7 with the last release of Xubuntu (13.10).
I understand that, in order to share folders, I have to install these GuestAdditions: so I did it. 
I mounted the .iso image, installed the required kernels (linux-headers, linux-headers-generic, build-essential, dkms) 
with the command 
[COLOR=#636363][FONT=Courier New]sudo apt-get install dkms build-essential linux-headers-generic 
[/FONT][/COLOR]and ran VBox with
[COLOR=#636363][FONT=Courier New]sudo sh /media/VBOXADDITIONS_3.2.10_66523/VBoxLinuxAdditions.run
[/FONT][/COLOR][COLOR=#636363][FONT=Courier New]
[/FONT][/COLOR]Now, although this, the installation process gives me this error (see attachment) which is driving me mad. 
I really need your help. Thank you really much indeed in advance. 
Cheers, 
Dr[COLOR=#636363][FONT=Courier New]
[/FONT][/COLOR]

---

### Post by Toz on 2013-10-27
Hello and welcome to the forums.

What version of Virtualbox did you install? 3.2? The current is 4.3. You might have more luck installing the guest additions with this version of Virtualbox.

*Moving thread to the **Virtualization** subform.*

---

### Post by ian-weisser on 2013-10-27
> **daviderix said:**
> Since I needed to use a Linux machine, I installed VirtualBox on my Windows 7 with the last release of Xubuntu (13.10).

Er, which is the is the Host, and which is the Guest?
If you installed VB for a Windows 7 host, then that's where you also need to install guest additions.

---

