---
title: "Problems with Vbox and Hardy."
date: 2008-04-25
forum: Virtualisation
---

### Post by jrharvey on 2008-04-25
I have just installed virtualbox on Hardy and it works fine except for the autocapture function. I cannot capture my mouse to the virtual machine. With no mouse, i can pretty much not do anything at all. Has anyone else ran into this problem and if so, how do i fix it?

---

### Post by Rob2008 on 2008-04-25
I'm getting the same problem- looks good, but can't use it :(

---

### Post by snappy46 on 2008-04-25
Hi,

In order to use the auto capture mode you have to have the add-on loaded on the guest machine.  It is an easy process to install that can be done using VB top menu when your guest machine is loaded.

Hope this help

Snappy

---

### Post by jrharvey on 2008-04-25
> **snappy46 said:**
> Hi,

In order to use the auto capture mode you have to have the add-on loaded on the guest machine.  It is an easy process to install that can be done using VB top menu when your guest machine is loaded.

Hope this help

Snappy

Ok but the problem is that i cannot install the addons without a mouse. So how can I install the addons? Also I have not keyboard for some reason.

---

### Post by jrharvey on 2008-04-25
I have also tried this with a GUEST version of vista and GUEST ubuntu 7.10 I still have the same problem in hardy. Works fine in gutsy.

---

### Post by snappy46 on 2008-04-25
It appear that your problem is a little more complicated that what I first understood.  You should be able to release your mouse by using the hot key (default is the right CTRL key) then you should be able to access the menu on top.

---

### Post by jrharvey on 2008-04-26
Problem solved, I reinstalled VBOX from the website and installed guest additions. Im not sure why but the repository doesnt work.

---

### Post by hise0001 on 2008-04-26
I just installed hardy yesterday and installed the virtualbox OSE from repository.  I experienced the same thing with my mouse.  I would click on my windows guest; but, the mouse was still controlling hardy.  The mouse is now working in the windows guest; but, I don't know why it started working... I think it was restarting virtualbox.

I've been reading the properties of the virtualbox package and it does not appear that VBoxGuestAdditions.iso is included.  Anybody know where that iso can be obtained?

I went to the virtualbox.org site; but, they didn't have a hardy package available.

---

### Post by jrharvey on 2008-04-26
> **hise0001 said:**
> I just installed hardy yesterday and installed the virtualbox OSE from repository.  I experienced the same thing with my mouse.  I would click on my windows guest; but, the mouse was still controlling hardy.  The mouse is now working in the windows guest; but, I don't know why it started working... I think it was restarting virtualbox.

I've been reading the properties of the virtualbox package and it does not appear that VBoxGuestAdditions.iso is included.  Anybody know where that iso can be obtained?

I went to the virtualbox.org site; but, they didn't have a hardy package available.

I think part of the problem is that the latest package is built for gutsy. I simply installed the gutsy package from the website. I could not use my mouse but it would capture my keyboard. I had to navigate and install guest additions with my keyboard which was a pain to figure out. the .deb from the website should hae guest additions on it already.

---

