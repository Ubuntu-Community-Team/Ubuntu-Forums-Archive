---
title: "Where can I download 64-bit VMware Server for Ubuntu amd64?"
date: 2008-03-29
forum: Virtualisation
---

### Post by OzzyFrank on 2008-03-29
OK, I know I can install VMware on my 64-bit Gutsy via Synaptic, but I would like to see if I can find a download of it, as even if I retrieve it from my packages archive, it will be in 4 separate packages, one being for my specific kernel. At the VMware site, each installer comes as one package, and on 32-bit Ubuntu I successfully used Alien to convert the .rpm into a .deb, but that being for i386 means it won't install on my 64-bit system. I know one can force install 32-bit apps on 64-bit systems, but I really doubt this is one of those programs you'd want to do that with!

I've looked around for even just a 64-bit .rpm to convert, but haven't had any luck. Anyone know where I can get one? Or preferably a .deb (and as current as possible)? I'd even consider compiling from the .tar.gz version, but suspect it's for i386 too (correct me if I am wrong though!).

I'd prefer to have a single package that will install on any kernel, so I can just grab that and take it to a couple of friends' places to install. Any suggestions would be welcome! Thanks

---

### Post by fjgaude on 2008-03-30
As far as I know there are no 64-bit VMware servers. You can see what's at their site, vmware.com. I simply download the server and install it on my 64-bit machine. All works well, even installing 64-bit VMs with it.

---

### Post by OzzyFrank on 2008-03-31
Well, I'm running the 64-bit version of Ubuntu, which will complain if you try installing 32-bit software. As I mentioned, you can force install them, but prefer to go the 64-bit route. I ended up just installing through Synaptic, which I assume means I have a 64-bit version of the server in Ubuntu now. Correct me if I am wrong on that peoples. And yes, there is no 64-bit version of the Server available for download from VMware, which is almost pathetic in this day and age.

---

### Post by fjgaude on 2008-03-31
I can't believe that Ubuntu takes a 32-bit version from VMware and makes it into 64. I think that the Console ends up being whatever the host OS is in terms of bits. Then the guest gets to be whatever it is, 32 or 64, that's why a gcc compiler is used in the install.

I've run 32 and 64-bit guests on my version I get from vmware.com.

---

### Post by zyco321 on 2008-03-31
> **OzzyFrank said:**
> And yes, there is no 64-bit version of the Server available for download from VMware, which is almost pathetic in this day and age.

you can try the vmware-server 2.0 beta, it´s available as a 32bit and 64bit version [http://www.vmware.com/beta/server/overview.html](http://www.vmware.com/beta/server/overview.html)

---

