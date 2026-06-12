---
title: "Can't Start Up My Virtual Machine"
date: 2007-11-03
forum: Virtualisation
---

### Post by IronOxide on 2007-11-03
I come here with my problem because I can't make heads or tails of the VMWare support system, and I have always been helped very promptly and well here.

I am a casual user of VMWare to virtualize Windows to run some apps that I can't get a good replacement for in Ubuntu. I'm not sure what caused it, I haven't used it since either the upgrade to Gutsy Gibbon or when VMWare server released version 1.0.4, but when I try to start up my virtual machine from suspend, it gives me the (somewhat cryptic) error message:

Unable to change virtual machine power state: The process exited with an error:
End of error message.

I have tried updating my copy of VMWare, but Synaptic does not appear to recognize that there is a version of the program out past version 1.0.3.

Any help would be greatly appreciated!

---

### Post by koenn on 2007-11-03
after a kernel upgrade you have to get the new header files that correspond to the kernel version
```
sudo apt-get install linux-headers-$(uname -r)
```
and possible run the vmware install script again. 
Look around, I've seen a few other threads with the same problem here.

---

### Post by IronOxide on 2007-11-04
Well, I installed new headers and everything, and it didn't work, so I tried uninstalling and reinstalling the program, now it's telling me that:

"Package vmware-player is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source"

Does this mean their servers are just down for now or something more potentially sinister?

---

### Post by markharding557 on 2007-11-04
vmware isn't working for me either but virtualbox is so you try that and it is in the repository
there is also a more up to date version on the virtualbox website

---

### Post by IronOxide on 2007-11-04
I grabbed virtualbox, but for the life of me can't figure out how to get a .vmx file to work on it.

---

### Post by markharding557 on 2007-11-05
vmx will not work virtualbox makes its own called vdi

---

