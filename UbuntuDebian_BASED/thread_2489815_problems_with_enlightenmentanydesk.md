---
title: "problems with enlightenment/anydesk"
date: 2023-08-10
forum: Ubuntu/Debian BASED
---

### Post by rosika on 2023-08-10
Hi altogether, :smile:

I´m running Linux Lite 6.2 as my daily driver but I also make frequent use of running **Debian as a virtual machine** (KVM/qemu/virt-manager).
Recently I installed the **enlightenment** DE on my Debian VM, which uses the xfce DE per default. I already had installed i3 tiling WM, which I use most of the time.

After that I tested enlightenment in the VM and it works very well and meets all my demands. Actually I like it a lot.
I tested the vast majority of installed applications/programmes and they work as expected... except of one:
I ran into problems with **anydesk**. :-(

As soon as I started anydesk the whole of the VM froze immediately. I couldn´t use the mouse any longer, nor would any keyboard input have any effect.

Of course  I couldn´t open a terminal. Fortunately virt-manager provides the possibility of opening a number of virtual terminals by clicking on dedicated keyboard shortcuts. So I logged into virtual terminal 2 and here I could kill the anydesk process.

Curiously enough I was logged out of Debian as a result of that. After logging in again everything worked as expected.

I repeated the procedure a few times more, always resulting in the same outcome.

When using either xfce or i3 tiling WM anydesk works without fail. 

So what´s preventing **anydesk** from working with **enlightenment**? Why would starting the programme make the VM freeze?

Thanks a lot in advance.

Many greetings from Rosika ):P

---

### Post by jeremy31 on 2023-08-10
Moved to Ubuntu/Debian based

---

### Post by similar2 on 2023-08-19
Hi rosika,
Posting on the Enlightenment users mailing list is probably your best best if you have specific technical issues.

[https://sourceforge.net/p/enlightenment/mailman/enlightenment-users/](https://sourceforge.net/p/enlightenment/mailman/enlightenment-users/)

---

