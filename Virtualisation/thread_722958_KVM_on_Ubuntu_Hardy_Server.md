---
title: "KVM on Ubuntu Hardy Server"
date: 2008-03-13
forum: Virtualisation
---

### Post by e30power on 2008-03-13
I know Hardy isnt out yet, but this is theoretical.
I have an AM2 CPU that supports the AMD-V flag. I plan on upgrading my 6.06 server to 8.04 with a fresh install in a few months, and would also love to run KVM in order to move my Windows 2003 server from an actual computer to a guest system.
I will have 2 NIC's in the server, and obviously wont have a GUI on Hardy Server.
My questions are:
Can I set it so my Hardy box will answer only on eth0 (192.xxx.x.2) and Win03 only on eth1 (192.xxx.x.1)?
Is it possible to have a Hardy Server running on TTY1, install KVM, make an image and somehow have Win 03 boot in TTY2 or something?
If KVM wont do it, will Xen let me? What is the speed difference?

Sorry to ask so many newbie questions, but this seems like the perfect time to be able to reduce power and heat in my closet :)

---

### Post by ansicplusplus on 2008-03-15
Hy,
using one IP for your hardy server and one for Win03 is possible. It could be tricky to tie them to the exact NICs. You will have to set the ip routes on your server manually otherwise both IPs will answer on both interfaces. You should reconsider if you really need the physical separation.
When you launch your vm with Win03 it should be possible to redirect stdio to tty2, but I never did that before. I recommend using the -vnc option. That way you can access the GUI of your win03 using any decent vncviewer.
Yours, ansicplusplus

---

