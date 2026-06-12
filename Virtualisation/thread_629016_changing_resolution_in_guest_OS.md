---
title: "changing resolution in guest OS"
date: 2007-12-01
forum: Virtualisation
---

### Post by Inxsible on 2007-12-01
i m using virtual box and have installed DSL, Puppy, Xubuntu and Zenwalk.

My Xubuntu and Puppy run only as 640x480 whereas DSL and Zenwalk has resolutions from 640x480 to 1024x768.

I tried changing the resolution in Xubuntu in the xorg.conf, but then how do i restart X ?

Ctrl + Alt + Backspace restarts my host OS (ubuntu), and if i save the state, under virtual box...it doesn't work and starts up in 640x480 again. 

1) How do I fix this so that i can have 1440x900 (max my monitor supports) as resolution for my guest OSes?

2) My nvidia card is also not recognized and it says its using the vesa drivers. On going to the restricted driver manager, it says that "Your hardware does not need any restricted drivers". How do I make it use my gpu?

Thanks

---

### Post by Delvien on 2007-12-02
> **Inxsible said:**
> 

1) How do I fix this so that i can have 1440x900 (max my monitor supports) as resolution for my guest OSes?

2) My nvidia card is also not recognized and it says its using the vesa drivers. On going to the restricted driver manager, it says that "Your hardware does not need any restricted drivers". How do I make it use my gpu?

Thanks

1) Install guest additions and just resize the window itself, should change the size of the desktop for you.

2) You wont have direct access to your GPU ( not much 3d support in virtualization)  but im also not sure which one you have to chose, so cant answer this question, sorry.

---

### Post by Inxsible on 2007-12-04
how do I install guest additions? Sorry I am really new to virtualization.

So there is no way I can see if Compiz Fusion etc runs on a distro, without actually installing the OS or using the live CD maybe?

---

### Post by gakudva on 2007-12-05
You will have a VBoxAdditions.iso file in your host system.  You must mount it as a CD ROM in the guest system.  Now, if you will see this .iso as a CD in yoru guest system.

For more complete info read the pdf manual which is at virtual box site: [http://www.virtualbox.org/download/1.5.2/UserManual.pdf](http://www.virtualbox.org/download/1.5.2/UserManual.pdf)  

rgds, Ganesh

---

### Post by Inxsible on 2007-12-10
> **gakudva said:**
> You will have a VBoxAdditions.iso file in your host system.  You must mount it as a CD ROM in the guest system.  Now, if you will see this .iso as a CD in yoru guest system.

For more complete info read the pdf manual which is at virtual box site: [http://www.virtualbox.org/download/1.5.2/UserManual.pdf](http://www.virtualbox.org/download/1.5.2/UserManual.pdf)  

rgds, GaneshI wasn't able to find the VBoxAdditions.iso file on my host system. Could you tell me where exactly it is?

---

### Post by lil_B on 2007-12-11
When I installed Virtualbox on my machine (Gutsy 64) it didn't include the ISO. When I selected "Install Guest Additions" from the "Devices" menu on the Guest OS window it automatically downloaded it for me. I think I had to click it a few times before it kicked in.

---

### Post by gakudva on 2007-12-13
> **Inxsible said:**
> I wasn't able to find the VBoxAdditions.iso file on my host system. Could you tell me where exactly it is?

[http://virtualbox.org/download/1.5.2/VBoxGuestAdditions_1.5.2.iso](http://virtualbox.org/download/1.5.2/VBoxGuestAdditions_1.5.2.iso)

---

### Post by Inxsible on 2007-12-18
It seems that the virtualbox gues additions work only for Windows Guests (as per the manual)

:(

---

