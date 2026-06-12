---
title: "Not able to install Virtual Box on latest Kali"
date: 2017-05-01
forum: Ubuntu/Debian BASED
---

### Post by LastDino on 2017-05-01
Hi!

I've tried installing Virtual box by following procedure on Kali pages and other tutorials, but I've had no success with latest edition of Kali

I've Kali 16.2 (upgraded to latest) and experiencing following error messages 

> apt-get install -y linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-4.3.0-kali1-amd64
E: Couldn't find any package by glob 'linux-headers-4.3.0-kali1-amd64'
E: Couldn't find any package by regex 'linux-headers-4.3.0-kali1-amd64'


This is me trying to install headers since I was getting errors for missing headers. Even after installing VM by following 
> apt-get install build-essential dkms
and then
> apt-get install virtualbox

I was getting similar errors in completed installations. 

When I tried to run VM I got error saying that the VM will not run unless this problem is solved.

I've tried lot of things available on net, even tried to do 
> apt-get install build-essential
Which polled in packages sizing 1,060 MB or something...

Still no luck

After trying to run virtual machine I get error saying 
>  modprobe vboxdrv


is missing or something

Sorry if post sounds confusing, but I'm guessing this is something to do with the kernel updates, not sure though

I also tried running
> apt-get install linux-headers-amd64
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-amd64 is already the newest version (4.9+79+kali2).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Can anyone help here?:confused:

---

### Post by LastDino on 2017-05-02
No luck here *Sign*

---

### Post by Bucky Ball on 2017-05-02
Tried [here]("https://forums.kali.org/")?

---

### Post by LastDino on 2017-05-02
Yes, in fact, I posted this same thread there before here <.<

No response.

---

### Post by LastDino on 2017-05-07
bumping bumping :(

---

