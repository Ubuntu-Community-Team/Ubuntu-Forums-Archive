---
title: "how-to-connect-to-internet-from-ubuntu-which-is-installed-in-a-virtual-machine-u"
date: 2013-02-02
forum: Virtualisation
---

### Post by barcealona on 2013-02-02
I have installed Ubuntu 9.04 on a virtual machin using VMWare workstation. I have WIndows 7 as my host OS.

 
  I want to connect to internet from Ubuntu. Can anyone please gives steps for connecting to internet through guuest OS?

---

### Post by sanderj on 2013-02-02
> **barcealona said:**
> I have installed Ubuntu 9.04 on a virtual machin using VMWare workstation. I have WIndows 7 as my host OS.

 
  I want to connect to internet from Ubuntu. Can anyone please gives steps for connecting to internet through guuest OS?

Ubuntu 9.04 is not supported anymore. See [http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions)

So get a recent & supported Ubuntu: 12.04 or 12.10, and run that.

HTH

---

### Post by barcealona on 2013-02-02
> **sanderj said:**
> Ubuntu 9.04 is not supported anymore. See [http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions)

So get a recent & supported Ubuntu: 12.04 or 12.10, and run that.

HTH
yes ,i have ubuntu 12.04 not 9.04 ,please answer me about my question

---

### Post by DougB1958 on 2013-02-02
Also be sure you set up the virtual machine with a network interface that can talk to the outside world. (Under VirtualBox, which I run Ubuntu 12.04 as a guest under, that would be a network interface that uses NAT and gets configured via DHCP--I don't know about VMWare, but I expect it's similar in concept if not in detail, and has documentation you can consult for the details.) Good luck.

---

### Post by sanderj on 2013-02-03
Is Internet working on the host machine?

Can you tell how you set up the Ubuntu virtual machine? Did you all leave to default?

---

### Post by barcealona on 2013-02-03
> **sanderj said:**
> Is Internet working on the host machine?

Can you tell how you set up the Ubuntu virtual machine? Did you all leave to default?
yes, There is internet in home machine .
i leave all setting to default except i do one thing form setting vm->Network Adapter ->Nat

---

### Post by sanderj on 2013-02-03
> **barcealona said:**
> yes, There is internet in home machine .
i leave all setting to default except i do one thing form setting vm->Network Adapter ->Nat

and why do you do that? 

What happens when you leave that to default too?

---

### Post by barcealona on 2013-02-03
> **sanderj said:**
> and why do you do that? 

What happens when you leave that to default too?
I read that in some subjects but not work .
can tell me what should i do

---

### Post by sanderj on 2013-02-03
Create a new VM, leave everything on default
Start the VM, and point to the fres Ubuntu ISO. Install it.
Then everything should work

HTH

---

