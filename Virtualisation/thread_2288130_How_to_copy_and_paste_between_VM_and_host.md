---
title: "How to copy and paste between VM and host"
date: 2015-07-24
forum: Virtualisation
---

### Post by satimis on 2015-07-24
Hi all,

host	ubuntu 14.04 desktop
VM	ubuntu 14.04 server

I have gpm installed on the server.  I can highlight the text with mouse point but I couldn't copy the highlight text nor paste it on host.

please help.  Thanks

Regards
satimis

---

### Post by slickymaster on 2015-07-24
*Moved to the ***Virtualisation*** sub-forum*

What virtualisation solution are you using?

---

### Post by satimis on 2015-07-24
> **slickymaster said:**
> *Moved to the ***Virtualisation*** sub-forum*

What virtualisation solution are you using?

Oracle VirtualBox

satimis

---

### Post by slickymaster on 2015-07-24
Do you have the VirtualBox Guest Additions package installed? You need it to be able to share the clipboard between the host and the guest.

---

### Post by v3.xx on 2015-07-24
also set bidirectional
[ATTACH=CONFIG]263355[/ATTACH]

---

### Post by ajgreeny on 2015-07-24
The guest-additions also allows you to use a shared folder if you wish, which I do, using my home folder from the host OS.  You must add your user to the vboxsf group in your guest OS, and I recommend you use automount for whichever folder you decide to share; it means the share is available straight away at boot of the guest in /media/sf_*foldername*.

I copy a few of the config folders in my home as well, eg ~/.mozilla, ~/.config/libreoffice, but do not share them in the usual sense in case there are any version conflicts.

---

### Post by satimis on 2015-07-24
Hi all,

Thanks for your advice.

I have VirtualboxGuestAddition installed and rebooted VM.  Also set bidirectional on Settings

On VM console highlighting the text
-> Ctrl+C
it pasted the text immediately on console

On Host editor
-> Ctrl+V
nothing happened.

I'll do file-sharing latter

Regards
satimis

---

### Post by ajgreeny on 2015-07-24
> **satimis said:**
> Hi all,

Thanks for your advice.

I have VirtualboxGuestAddition installed and rebooted VM.  Also set bidirectional on Settings

[COLOR="#FF0000"]On VM console highlighting the text
-> Ctrl+C[/COLOR]
it pasted the text immediately on console

On Host editor
-> Ctrl+V
nothing happened.

I'll do file-sharing latter

Regards
satimis
If you are talking about copy/paste in a terminal application or tty command line console, you will have to use Shift+Ctrl+C to copy and Shift+Ctrl+V to paste, which is why I think your paste operation did not work; simply because the copy did not do anything in the first place.

Try copying from something like a GUI text editor (gedit) in the guest and then pasting in another text editor in the host.

---

### Post by satimis on 2015-07-24
> **ajgreeny said:**
> If you are talking about copy/paste in a terminal application or tty command line console, you will have to use Shift+Ctrl+C to copy and Shift+Ctrl+V to paste, which is why I think your paste operation did not work; simply because the copy did not do anything in the first place.

Try copying from something like a GUI text editor (gedit) in the guest and then pasting in another text editor in the host.
How can I hit "capital C/V"?

If I stop gpm 
$ sudo /etc/init.d/gpm stop

I can't highlight text on VM console with mouse pointer.  This is server version NOT desktop

satimis

---

### Post by v3.xx on 2015-07-24
Use lower case c/v

---

### Post by JKyleOKC on 2015-07-25
> **satimis said:**
> Hi all,

host	ubuntu 14.04 desktop
VM	ubuntu 14.04 server

I have gpm installed on the server.  I can highlight the text with mouse point but I couldn't copy the highlight text nor paste it on host.You have to remember that in Linux there are not just one, but two "clipboard buffers" that have nothing to do with each other, when the X Windows server is involved. I've never managed to get vbox's host-guest copy-paste interface working, but achieve the same end by setting up a permanent shared folder in each guest to use as a staging area.

That is, in the guest I can copy or paste between any guest folder and the shared folder on the host. I can then return to the host and copy or paste from the shared folder to any other place (if permissions allow -- I often have to use "sudo" to bypass permissions problems).

An interesting byproduct of the dual-clipboard situation is that I can highlight something in one host window, then use the middle-click mouse action to paste it elsewhere, with no need to involve the ctrl-c/ctrl-v actions. Comes in quite handy at times when a web page has blocked ctrl-c copying but still allows highlighting...

---

### Post by satimis on 2015-07-25
> **JKyleOKC said:**
> You have to remember that in Linux there are not just one, but two "clipboard buffers" that have nothing to do with each other, when the X Windows server is involved. I've never managed to get vbox's host-guest copy-paste interface working, but achieve the same end by setting up a permanent shared folder in each guest to use as a staging area.

That is, in the guest I can copy or paste between any guest folder and the shared folder on the host. I can then return to the host and copy or paste from the shared folder to any other place (if permissions allow -- I often have to use "sudo" to bypass permissions problems).

An interesting byproduct of the dual-clipboard situation is that I can highlight something in one host window, then use the middle-click mouse action to paste it elsewhere, with no need to involve the ctrl-c/ctrl-v actions. Comes in quite handy at times when a web page has blocked ctrl-c copying but still allows highlighting...

Hi,

Thanks for your advice.

I think the problem comes from Ubuntu 14.04 server VM.  I have no problem in copy-n-paste between host and Ubuntu 14.04 desktop VMs and amongst Ubuntu 14.04 desktop VMs.  Xorg is running on Ubuntu 14.04 server VM.

satimis

---

### Post by TheFu on 2015-07-29
Or just use normal X/Windows select/paste between the terminal used to ssh into the guest OS from the hostOS. Forget about using the "GUI" connection at all.  Forget about the virtualization and just treat the OS connections as if they were different physical machines. That goes for ssh and for NFS - just treat the machine like it was a real machine with normal networking.  All the normal network protocols *just work* and the security implications are extremely well understood.  Users tend to forget about security implications with built-in VM tools.

The first thing I do after installing the OS is to setup ssh, push my keys over and then stop using the "console" and only use ssh connections going forward - I do this mainly to solve the select/paste thing.  Select/paste between xterms works exactly as expected.

---

### Post by Doug S on 2015-07-30
> **TheFu said:**
> Or just use normal X/Windows select/paste between the terminal used to ssh into the guest OS from the hostOS. Forget about using the "GUI" connection at all.  Forget about the virtualization and just treat the OS connections as if they were different physical machines.

The first thing I do after installing the OS is to setup ssh, push my keys over and then stop using the "console" and only use ssh connections going forward - I do this mainly to solve the select/paste thing.  Select/paste between xterms works exactly as expected.+1. I pretty much only use ssh to communicate with my VM servers.

---

