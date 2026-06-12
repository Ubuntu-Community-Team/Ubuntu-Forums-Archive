---
title: "vmware  server 1.0.6 install"
date: 2008-07-22
forum: Server Platforms
---

### Post by looney_greg on 2008-07-22
I need some help geting vmware server running on ubuntu server version 8.04 Here is what I have done so far:

sudo aptitude install build-essential linux-kernel-devel linux-headers-generic xinetd

wget -c [http://download3.vmware.com/software/vmserver/VMware-server-1.0.6-91891.tar.gz](http://download3.vmware.com/software/vmserver/VMware-server-1.0.6-91891.tar.gz)

tar xf VMware-server-1.0.6-*.tar.gz

cd vmware-server-distrib

sudo ./vmware-install.pl

sudo ln -sf /usr/lib/gcc/i486-linux-gnu/4.2.3/libgcc_s.so /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1

sudo ln -sf /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0

this worked perfect on ubuntu desktop but i am getting a c compiler error on server. any help would be much appreciated

---

### Post by gtdaqua on 2008-07-23
wats the exact server version?

do you have the latest linux-headers-`uname -r` and build-essential installed for your running kernel?

---

### Post by tinny on 2008-07-23
Have you seen this?

[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

These instructions worked for my install on Hardy

---

### Post by windependence on 2008-07-23
tinny, gtd is on track here, he doesn't have the correct kernel headers installed, hence it won't compile.

-Tim

---

### Post by tinny on 2008-07-23
> **windependence said:**
> tinny, gtd is on track here, he doesn't have the correct kernel headers installed, hence it won't compile.

-Tim

Yes true.

I just noticed that you now dont have to run the "vmware-any-any-update" (that used to be detailed in the tutorial).

Looks like version 1.0.5 needed this but 1.0.6 doesn't...?

---

### Post by windependence on 2008-07-23
That's correct, but some people have had problems with 1.06 with Windoze guests.

-Tim

---

### Post by looney_greg on 2008-07-23
Thanks everyone I will try the post from tinny today. It looks similar to what I have already done with one exception. I am getting into Linux more and more on a daily basis so you will have to excuse any stupid questions. What is the difference between the command I used, "linux-headers-generic" and this command in the post that tinny suggested "linux-headers-`uname -r`". I have all of the other dependicies installed just like the tutorial.

---

### Post by windependence on 2008-07-23
'uname -r' is a variable in Liniux that holds the kernel version. If you do a

sudo uname -r

at the command line you will see what I mean. So because of this, the command will automatically pull the correct version of the kernel source and install it for you. That is why you have the error. No need to start another tutorial, just install the new kernel source and compile.

-Tim

---

### Post by looney_greg on 2008-07-23
Cool Thanks Windependance. I formatted the hard drive and started from scratch so I knew the steps I took could be easily reproduced. Here is what I did:

sudo aptitude install build-essential linux-kernel-devel linux-headers-`uname -r` xinetd

wget -c [http://download3.vmware.com/software/vmserver/VMware-server-1.0.6-91891.tar.gz](http://download3.vmware.com/software/vmserver/VMware-server-1.0.6-91891.tar.gz)

tar xf VMware-server-1.0.6-*.tar.gz

cd vmware-server-distrib

sudo ./vmware-install.pl

sudo ln -sf /usr/lib/gcc/i486-linux-gnu/4.2.3/libgcc_s.so /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1

sudo ln -sf /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0



I used the symbolic link approach. I liked that better than the tutorial example. I now have a good working poor mans ESX server. Thanks for everyones responses and Help. 

Greg

---

