---
title: "Lubuntu, Own Cloud"
date: 2014-09-28
forum: Virtualisation
---

### Post by support3 on 2014-09-28
The plan is to install OwnCloud in a virtual machine, as I have a few old hard drives with  old information, I just want to stick everything on a 1TB Hard drive.

I installed Lubuntu in a virtual machine (Virtual Box), and then installed a LAMP server on top of that.

So my question is, can I run OwnCloud in a virtual machine, and secondly since I am using the community version are there are any limits on the amount I can store?

Also because I wanted a static IP address from my network I set Lubuntu to use a Bridged Adaptor. It works perfectly, I can ping the virtual machine, 
however the only problem is I cannot now connect to the internet on the virtual machine.

---

### Post by CharlesA on 2014-09-28
In a bridged connection, the VM shows up on the network as another machine.

If you are unable to connect to the internet but can access things locally, check to see if you can ping something like 8.8.8.8.

---

### Post by support3 on 2014-09-28
> **CharlesA said:**
> In a bridged connection, the VM shows up on the network as another machine.

If you are unable to connect to the internet but can access things locally, check to see if you can ping something like 8.8.8.8.

Ok thanks, I will try this tomorrow.

---

### Post by nerdtron on 2014-09-29
> So my question is, can I run OwnCloud in a virtual machine, and secondly  since I am using the community version are there are any limits on the  amount I can store?
This is a question for the OwnCloud community and not Ubuntu, but last time I installed OwnCloud, there are no such limit. I'm not sure on the latest version though.

If you can ping 8.8.8.8 and not ping google.com, there must be DNS issue on your VM. Check your network config and add appropriate DNS entries.

---

### Post by mastablasta on 2014-10-02
why do you need lubuntu for that? just download virtual image: [https://bitnami.com/stack/owncloud](https://bitnami.com/stack/owncloud)

set up the virtual machine (with bridged internet), boot it, select password and such and connect to the cloud from a browser in host.

you can install jmysql if you plan more users or large database. with a good host PC you should be up and running within less than 10 min.

---

