---
title: "How to install Borderlands"
date: 2010-08-07
forum: Wine
---

### Post by MugenFox on 2010-08-07
I am having problems running Borderlands 1.0 on my Karmic x86 installation. Can someone please tell me a step by step n00b guide on how to get it running in Wine or PlayOnLinux. Thanks a bunch.

---

### Post by asdfoo on 2010-08-07
goto winehq.org - get latest version from download section for ubuntu

look up borderlands on the winehq appdb for any specific instructions - if none, use the wine FAQ to find out how to run the installer

---

### Post by MugenFox on 2010-08-07
There's no how to which is why I'm asking for help here. I can successfully install the retail version from the DVD v1.0 but it won't run. I can successfully activate it from the offline activation becuase I get the securom once, cancel it, then activate it using the offline activator but it wont run

---

### Post by asdfoo on 2010-08-07
> **MugenFox said:**
> There's no how to which is why I'm asking for help here. I can successfully install the retail version from the DVD v1.0 but it won't run. I can successfully activate it from the offline activation becuase I get the securom once, cancel it, then activate it using the offline activator but it wont run

newer securom is not likely to work in Wine properly, they do dirty tricks.  you may need to use a nocd/nodvd for non-steam borderlands.

---

### Post by MugenFox on 2010-08-07
I have a no dvd and still no hope. I guess I might just do VirtualBox.

---

### Post by thenellt on 2010-08-07
I assume you have winetricks (if not, "sudo apt-get winetricks") then run 
sudo winetricks d3dx9 vcrun2005 vcrun2008
That should be everything you need to run it. Make sure you have wine version 1.2 or 1.3 and go into preferences and tell it to emulate a virtual desktop. This is all taken directly from [[COLOR="Blue"]appdb[/COLOR]]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=18268")
Good luck, thats a fun game.

---

### Post by MugenFox on 2010-08-07
I'm currently installing that. Will love you if it works.

---

### Post by thenellt on 2010-08-07
Hehe, Appdb is your friend.

---

### Post by MugenFox on 2010-08-07
No luck. It installs sucessfully and I hear sound but I get nothing. I can hear all the intros and everything. I'll try lowering the resolution in windowed mode.

---

### Post by thenellt on 2010-08-07
What graphics card do you have and what drivers are you using?

---

