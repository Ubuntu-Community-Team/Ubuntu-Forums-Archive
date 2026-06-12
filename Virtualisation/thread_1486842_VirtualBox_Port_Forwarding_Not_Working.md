---
title: "VirtualBox Port Forwarding Not Working"
date: 2010-05-18
forum: Virtualisation
---

### Post by finer recliner on 2010-05-18
I have an Ubuntu 10.04 Host running VirtualBox and a Guest Ubuntu Server 10.04 set up.

My host machine is behind a linksys router. I would like to use the VM as a web server (to the outside world). I have NAT networking between the host and guest machines, and used port forwarding ([guide here]("http://www.virtualbox.org/manual/ch06.html#natforward")) to foward port 8888 on the host to port 80 on the guest.

I also have my linksys router forwarding port 8888 to my host's IP address.

Now when I go to [http://127.0.0.1:8888](http://127.0.0.1:8888) in a browser on the host, I get the expected web page served from the guest.

But if I try to navigate to [http://w.x.y.z:8888](http://w.x.y.z:8888) (where w.x.y.z is my router's IP to the outside world), I get a page timeout.

Anyone know what the problem is? :confused:

---

### Post by finer recliner on 2010-05-20
*facepalm*

turns out port forwarding works better when you don't make silly typos.

---

### Post by uidb4056 on 2010-05-20
I think your problem is to have NAT in your guest, try change it to Bridged and I think it will run.

---

### Post by finer recliner on 2010-05-20
> **uidb4056 said:**
> I think your problem is to have NAT in your guest, try change it to Bridged and I think it will run.

Thank you for the suggestion, but I already solved this problem (see the second post in this thread)

---

### Post by jdpipe on 2011-03-08
Reading this post, I note that it looks as though the VirtualBox documentation (see [http://www.virtualbox.org/manual/ch06.html#natforward](http://www.virtualbox.org/manual/ch06.html#natforward)) has been updated and does not correspond to the 3.1.6 version of VirtualBox that is available on Ubuntu.

Can anyone give me some clear instructions for how this is to be achieved on 10.04's version of VirtualBox? Hugely appreciated.

**Note** related post: [http://ubuntuforums.org/showthread.php?t=1435211](http://ubuntuforums.org/showthread.php?t=1435211)

---

