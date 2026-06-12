---
title: "Accessing Files between Ubuntu 8.04 and VirtualBox?"
date: 2009-03-16
forum: Virtualisation
---

### Post by gerryo on 2009-03-16
I have Virtual box  version 1.56 OSE up and running with Win XP Pro as the guest on an AMD 64 processor.  I can go online and check email. I have a few win xp rprograms that are vital to my daily work that I would like to load on to my guest XP. One program is Clipmate. How do I get clip mate from my thumb Drive (USB) into my guest XP? I have tried to drag Clipmate from the usb to my open XP and the program will not 'stick' it just disappears as if I had not attempted to drag and release. Do I have to have another function of  Ubuntu installed or activated before this step can be carried out?

Cheers....Gerry

---

### Post by null.byte on 2009-03-16
VirtualBox OSE doesn't support USB's. Get the closed source one.

---

### Post by gerryo on 2009-03-16
> **null.byte said:**
> VirtualBox OSE doesn't support USB's. Get the closed source one.
Thank-you for your quick reply. I have also moved the Clipmate.exe program to my Ubuntu Desktop and still can't drag and stick the .exe to the guest XP desktop. I would think that would be possible as the USB is not involved?

Cheers...Gerry

PS I had a bit of frustration to actually get any  version of VirtualBox running so I am reluctant to try and reinstall another version without exploring all avenues.

---

### Post by null.byte on 2009-03-17
You may create Shared Folders. Create a folder on your Linux desktop. After that, share it in VirtualBox:

Machine - Settings - Shared folders - Add new shared folder.

After that, start the VM and the shared folder with be found in My Network Places. Be aware that you first must have installed VirtualBox Guest Tools.

---

### Post by HermanAB on 2009-03-17
I normally install ssh-server on Linux and FileZilla on Windows.  That is the easiest way by far to exchange data between machines and it is secure too.

Cheers,

Herman

---

### Post by loomsen on 2009-03-19
O.o

Easiest way? Are you sure?

[quote=null.byte]...[/quote]

Dead on. Simply share the mounpoint of your USB, that way you wont have to find the file holding the automagic config to make it work :)

In Win, rum a cmd line and mount the share as a networkdrive.

c:\> net use s: \\vboxsvr\<your-shared-folder-name>

Nothing easier than that imho...

---

### Post by null.byte on 2009-03-20
I didn't think about that. Good idea :)

---

### Post by meka4996 on 2009-05-07
try this
[http://ubuntuforums.org/showthread.php?p=7236471#post7236471](http://ubuntuforums.org/showthread.php?p=7236471#post7236471)

---

