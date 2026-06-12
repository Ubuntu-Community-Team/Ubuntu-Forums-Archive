---
title: "Multiple roots"
date: 2009-05-12
forum: Server Platforms
---

### Post by Zeratul021 on 2009-05-12
Hi I would like to test something but unfortunatelly I dont know the right keywords to search for it.
The thing is, I wonder if it is possible to setup kind of virtualization in ubuntu that would allow multiple "roots" to administrate their parts of server that would be chrooted to their local /, (eg all stored in /usr/local/accounts).
Kind of all will be roots but only up to their /. So they wouldnt have acces to other things.
I see problem in how they would acces standar apt-get or other /bin scripts.

Anyone can post any advice or something to search for, or even if it is possible?

Thanks a lot, regards

---

### Post by lykwydchykyn on 2009-05-12
Well, you could create virtual machines if your hardware is up to it.  This also sounds a lot like *user mode linux*, which is a kind of pseudo-virtualization technology that was big before everyone got into vmware/virtualbox/kvm.

[https://help.ubuntu.com/community/UserModeLinux](https://help.ubuntu.com/community/UserModeLinux)

---

### Post by a9k3d on 2009-05-12
This also sound a lot like using OpenVZ. You'd need to switch to an -openvz kernel, install vzctl and get up to speed. It's pretty easy in hardy and jaunty now the ubuntu has openvz kernels.

I use openvz a lot now. It's basically a super chroot jail that also jails the networking. If you want to runs windows in a virtual machine then openvz isn't for you.

---

### Post by Zeratul021 on 2009-05-12
Thanks for replies.
Basically I run each service in separate VM in VirtualBox because I am not short on HW.
But more like for educational purposes, OpenVZ seems what I was looking for, an user-system virtualization, not whole machine.
Regards

---

