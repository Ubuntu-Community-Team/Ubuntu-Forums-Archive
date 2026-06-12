---
title: "Anyone managed to install Ubuntu One in Kubuntu?"
date: 2011-08-18
forum: Ubuntu One (CLOSED)
---

### Post by PeteAsdf on 2011-08-18
Hi, did anyone manage to install Ubuntu 1 in Kubuntu? I tried a few ways but still can't make it run. I managed to install it on Win XP and an Android phone, really weird that there's no explicit support for Kubuntu yet...

---

### Post by Dragonbite on 2011-08-18
Wasn't somebody working on a KDE app for Ubuntu One?

I know when I am using KDE for a distro that kDropbox doesn't have a package for, I just install the Server version instead.

It does synchronize, and place the icon in the system tray, but it does not give you those nice indicators on the folder of their status.  Otherwise it works exactly like it does in the Gnome variant (for Ubuntu and Fedora).

---

### Post by Dragonbite on 2011-08-22
Any luck recently?

I found a couple of pages from 2010 that referred to an ubuntuone-kde package and PPA.  Their steps for installing are
```
sudo add-apt-repository ppa:apachelogger/ubuntuone-kde
sudo apt-get update
sudo apt-get install ubuntuone-kde
```I know these are a little old and looks like they were before the UbuntuOne Music Store.  I don't know if it will sync with Contacts (to KMail?) Bookmarks (Firefox) or Notes (???). It doesn't look like it works fully yet either but all those notes are old.

It would be great, though, to be able to use it and be able to share files between Ubuntu and Kubuntu.

REFERENCES:
------------------------------------------------
[How to Install And Setup Ubuntu One In Kubuntu]("http://maketecheasier.com/how-to-install-and-setup-ubuntu-one-in-kubuntu/2010/03/15")
[How to install Ubuntu one alpha1 in Kubuntu 10.10]("http://www.ubuntugeek.com/how-to-install-ubuntu-one-alpha1-in-kubuntu-10-10.html")

---

### Post by PeteAsdf on 2011-08-24
Hi, thanks for the reply. I tried to follow up the advice on those links (plus several others) without any luck. At one point it did install the Ubuntuone client, however I couldn't launch it (it appeared in the system tray briefly when I clicked on the icon but then nothing happened (there was no process for the program running either.
I guess I'll just wait till they release an official KDE version... or use the DropBox instead...

Thanks anyhow

---

### Post by Docaltmed on 2011-08-26
I have it working on Kubuntu, more or less successfully (see my other thread; I don't think the problem is KDE-related).

On one machine, I had originally been using Natty/Unity, and just added KDE, and U1 just kept working.

The other machine is a clean Kubuntu install. I added U1 with directions I found on a Google search, not the commands listed in your previous post. I wish I could remember where...

EDIT: I think this was it -- [http://ubuntuforums.org/showpost.php?p=9548953&postcount=2](http://ubuntuforums.org/showpost.php?p=9548953&postcount=2)

---

### Post by PeteAsdf on 2011-10-17
Wohoo, updated to the new 11.10 and it's working seamlessly there!

---

### Post by Dragonbite on 2011-10-17
> **PeteAsdf said:**
> Wohoo, updated to the new 11.10 and it's working seamlessly there!

By "seamlessly", does that mean out-of-the-box, or after following the instructions on one of the linked directions here?

---

