---
title: "Zenoss VMware ubuntu 7.10"
date: 2008-03-31
forum: Server Platforms
---

### Post by mikeduffy13 on 2008-03-31
so i installed Zenoss VMware appliance and everything worked fine to make a long story short.  I was using the server on a test network 10.17.x.x using dhcp for the server and Zenoss.  I moved the server over to the correct network and statically addressed it.  10.17.x.x.  The server is fine, i can ssh in remotely, but now Zenoss won't recognize the static addressing.  It keeps looking for 10.17.1.1... I have searched all the Zenoss documentation I can find and haven't found an answer, any ideas?

---

### Post by BillGod on 2008-03-31
I have been running zenoss for a while now.  I had nothing but problems with the pre-configured zenoss vm.  I would recommend just installing ubuntu server then download the .tar file and build it yourself.  their documentation for it is actually pretty good.

[http://www.zenoss.com/community/docs/install-guides/install-on-ubuntu-7.04/](http://www.zenoss.com/community/docs/install-guides/install-on-ubuntu-7.04/)

make sure you run "apt-get install build-essential" before you start to install g++ compiler.

---

### Post by mikeduffy13 on 2008-04-01
scrapped VMware install and compiled source code.  worked flawlessly.  thanks Bill!

---

