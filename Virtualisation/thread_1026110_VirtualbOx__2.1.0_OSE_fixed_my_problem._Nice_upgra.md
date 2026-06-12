---
title: "VirtualbOx  2.1.0 OSE fixed my problem. Nice upgrade!"
date: 2008-12-30
forum: Virtualisation
---

### Post by akelsall on 2008-12-30
I was having all kinds of problems being able to connect to the Internet from my virtual WinXP guest (running in Vbox). I tried every imaginable config you might come across (using TAPs and br0 interfaces) and never could get it working. 

Well, today I installed the new Virtualbox OSE edition (v2.1.0) and with this version, when you select "Attach to:Host Interface", at the bottom of the screen I noticed they now provide the available interfaces I can use (which were eth1 and br0 in my case). I selected eth1 and BAM! I can now surf the Net from the WinXP guest. woo hoo!!! I went back and modified my /etc/network/interfaces file and commented out the br0 info, and I can STILL surf from my WinXP guest (after stopping and restarting networking). 

I don't know what they did, but they sure have done something right in a big way this time. If you're having problems, I highly recommend upgrading.

Andy

Ubuntu Intrepid (8.10) and VirtualBox v2.1.0
Linux host / WinXP guest (inside vbox)

---

