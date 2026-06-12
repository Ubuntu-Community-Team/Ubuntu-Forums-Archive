---
title: "issuing seeing Ubuntu desktop"
date: 2020-07-20
forum: Virtualisation
---

### Post by alexvanr on 2020-07-20
Awhile ago I installed Ubuntu onto Virtual Box and had no issue running the desktop 16.04.6 (doing tutorials with the earlier one) but then I delete the OS and tried to reinstall a new VM on Virtual Box but I cannot get anything but a black screen. I have made several attempts to 1. delete the VM 2. delete the Virtual Box 3. left the vm running for HOURS but nothing happens. 4. Read forums about adjusting processor specs/display specs but It still will not load anything. All I see is a black screen with a blinking _. Can someone please help? I am lost as to what to do next.

---

### Post by ajgreeny on 2020-07-20
We need much more information about the version of VBox you're  using and the VMs you are having trouble with, without which there is not much e can do.
Also we need to know what host OS you have.

---

### Post by alexvanr on 2020-07-20
I was using Virtual Box 6.1 but just upgraded it to the 6.1.12 yesterday to see if this would make a difference which it did not.

Virtual Box- 6.1.12
Ubuntu - 16.04.6 LTS (Xenial Xerus)

[https://static.wixstatic.com/media/bbe2b0_4fd028b6896b4e4f81f522765bf3d497~mv2.png](https://static.wixstatic.com/media/bbe2b0_4fd028b6896b4e4f81f522765bf3d497~mv2.png)

---

### Post by ajgreeny on 2020-07-20
Still need more info to be able to help.
Please can I check with you that your host system is Ubuntu 16.04 and you are having trouble running a VM of Ubuntu 20.04?  Updating your host will be necessary in 9 months time so it may be worth considering updating that to a more recent version; I suggest 20.04 but whether Ubuntu or some other flavour with a lighter DE is difficult to say until I see the hardware details of your host (see below).

I see you have set only 16MB video memory in the VM, which I suggest you increase to the full 128MB available as the gnome desktop of Ubuntu 20.04 needs higher memroy than just 16MB to work well, but I can not see from the image how much RAM is set for it, nor what your host hardware is in detail.
On the host please run command ```
inxi -Fzx
```and copy/paste the output back here. Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

And finally, please in future do not add large images in the text as you did here  but add as an attachment using the Attachment icon, a paperclip, in the "Reply to Thread" window then pointing to the image on your hard drive; this is preferred on this forum to using third party image hosting sites as you did.

---

### Post by lammert-nijhof on 2020-08-05
I had the same problem trying to start the VM in full screen. I got a screen by pushing one or two times CTRL + F. It seems to be a bug in Virtualbox, to avoid having to press CTRL + F all the time, I use the version 6.1.4 of the Guest Additions.

---

