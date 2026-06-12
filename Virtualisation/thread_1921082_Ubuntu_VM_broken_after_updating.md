---
title: "Ubuntu VM broken after updating"
date: 2012-02-06
forum: Virtualisation
---

### Post by BradleyAtkins on 2012-02-06
Hi All

At work on my Win7 laptop I have Oracle VirtualBox installed and am running Ubuntu 11.10 as a virtual machine on it.

I normally accept the Ubuntu updates as a matter of course, but something in them is causing my display to break and I have to revert to a snapshot.

I am running two displays off the laptop and normally work with the lid down and the displays on. One displaying the Ubuntu VM full screen and the other the Win7 machine full screen.

If I update the VM I find I lose full screen on the VM. Even worse, when I click in the VM the mouse pointer jumps back to the Win7 machine. If I repeatedly click in the VM I can get the mouse to stay there but the mouse will not traverse the whole desktop...

Can anyone suggest a way of investigating / fixing this?

Thanks in advance

Brad

---

### Post by CharlesA on 2012-02-06
There was probably a kernel update. You will need to reinstall the guest additions.

---

### Post by japzone on 2012-02-06
I second the Reinstall of Guest Additions. Guest Additions works Low Level so there is always a chance that a Low Level update(Like to the Kernel) will break it. Just try reinstalling it after the Update to Ubuntu and see if that fixes your problem.

---

### Post by BradleyAtkins on 2012-02-07
Well the Guest additions didn't fix it but they did improve things to the point where I could click on the firefox icon in unity and look up my old threads on the display issues I have had in the past.

I installed the additional video drivers again - jockey-gtk and that restored the desktop.

Thanks for the help guys

---

### Post by japzone on 2012-02-07
If it's fixed  you should mark the Thread solved. Go to "Thread Tools" and click "Mark as Solved".

---

