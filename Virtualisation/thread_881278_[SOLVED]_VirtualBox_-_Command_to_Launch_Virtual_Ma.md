---
title: "[SOLVED] VirtualBox - Command to Launch Virtual Machine?"
date: 2008-08-05
forum: Virtualisation
---

### Post by SlalomMan on 2008-08-05
I'm using VirtualBox to emulate Windows XP so I can transfer files to my Zune. I would like to be able to have an icon in my dock that will launch my XP machine when I click it instead of going to the VirtualBox main screen first. Any ideas?

---

### Post by estyles on 2008-08-05
```
vboxmanage startvm WinXP
```

Replace WinXP above with the name of your virtual machine.  Note this is for Virtual Box OSE.  I don't know if it's different for another version.

---

### Post by SlalomMan on 2008-08-05
Ack! I have the closed source version for the USB support that I need; I'm not sure if the OSE edition has usb support yet.

---

### Post by kevin11951 on 2008-08-06
> **SlalomMan said:**
> Ack! I have the closed source version for the USB support that I need; I'm not sure if the OSE edition has usb support yet.

No USB in OSE

---

### Post by estyles on 2008-08-06
I might be wrong, not having used the closed version, but I think you replace 'vboxmanage' with 'VBoxManage'.  And if you type VBoxManage by itself at a prompt, you should get a list of commands.  At least, both vboxmanage and VBoxManage work for me, on OSE, so I'm guessing that at least one of them should work on the closed version.

---

### Post by tuxxy on 2008-08-06
You can add a virtualbox icon to your main menu by navigating to system > prefs > main menu > add , then just enter the command to run virtual.

---

### Post by SlalomMan on 2008-08-06
Thanks guys, "VBoxManage startvm "Windows XP"" worked perfectly. Thanks for all the help!

---

### Post by AlexanderDGreat on 2010-10-23
How do you protect your VirtualBox GUI?

In my understanding, if you type:

VirtualBox

Any user can tinker with the setting

---

### Post by AlexanderDGreat on 2010-10-24
I've found a Quick & Dirty Step:

> Backup first your VirtualBox command, it's found in /usr/bin/

sudo cp /usr/bin/VirtualBox /home/username

Then remove it entirely:

sudo rm /usr/bin/VirtualBox

There!

PS I hope someday they will make a feature to password protect the VirtualBox GUI! It makes sense.

---

