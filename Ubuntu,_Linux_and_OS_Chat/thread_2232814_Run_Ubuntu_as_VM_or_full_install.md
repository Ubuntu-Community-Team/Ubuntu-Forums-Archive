---
title: "Run Ubuntu as VM or full install?"
date: 2014-07-04
forum: Ubuntu, Linux and OS Chat
---

### Post by carlito3 on 2014-07-04
Hi guys i was wondering whether it is better to run Ubuntu on a virtual machine or install ubuntu on the hard drive?
What are the differences (pros and cons)?
thanks

---

### Post by Bucky Ball on 2014-07-04
*Post moved to own thread.*

---

### Post by smirnich on 2014-07-04
The difference is performance. I can only speak from my experience with a pretty cheap laptop (2,1 Ghz AMD A6-4455M with 6 GB RAM) , but on this hardware Ubuntu runs very good on a full install, but in a vm it is veeery slooow. But if you have good hardware, then it shouldn't be a problem.

But you could try it in a VM first, and if you're not satisfied with the performance go for full installation. I'm dualbooting with Windows 8 and have no problems with that :)

---

### Post by carlito3 on 2014-07-04
yes i'm trying to triple boot ubuntu mac os x , windows 7.
I had windows 7 via bootcamp already installed but experienced big issues in terms of partitioning the hard drive, so was just thinking of VM as last resort..

---

### Post by sudodus on 2014-07-04
> **smirnich said:**
> The difference is performance. I can only speak  from my experience with a pretty cheap laptop (2,1 Ghz AMD A6-4455M  with 6 GB RAM) , but on this hardware Ubuntu runs very good on a full  install, but in a vm it is veeery slooow. But if you have good hardware,  then it shouldn't be a problem.

But you could try it in a VM first, and if you're not satisfied with the  performance go for full installation. I'm dualbooting with Windows 8  and have no problems with that :smile:

+1

I might add: If you want to keep Windows as the main OS you can run a lighter flavour of Ubuntu: Xubuntu or Lubuntu, which can manage reasonably well, even if the virtual machine will be slow with standard Ubuntu.

Another alternative is to let Ubuntu be the main OS and host for a virtual machine and run Windows as guest. But if you have an OEM licence for Windows, it is locked to the computer hardware, and does not work in the virtual machine.

I'm also dual booting with Windows 8. Even though I use Windows very seldom nowadays, I still need it for certain tasks.

---

### Post by at_first_light on 2014-07-20
As other's have said you'll get better performance from a real install, but you can always go the vm route and if it's too weak perform a full install later. If you plan to use a virtual machine I would suggest disabling swap, if possible storing the vm on a seperate drive from the host operating system, and using an Ubuntu derivative that uses a lighter desktop environment like Lubuntu which uses LXDE. I personally use dynamically expanding virtual hard drives, but allocated virtual drives are supposed to aid performance.

---

### Post by kurt18947 on 2014-07-20
> **sudodus said:**
> +1

...............................
Another alternative is to let Ubuntu be the main OS and host for a virtual machine and run Windows as guest. But if you have an OEM licence for Windows, it is locked to the computer hardware, and does not work in the virtual machine.

I'm also dual booting with Windows 8. Even though I use Windows very seldom nowadays, I still need it for certain tasks.

I had thought that OEM Windows 8 (or any version) could not be installed in a VM.  However, I found this on Microsoft's site:[INDENT]**Q.** Can I install OEM software on a virtual machine (VMware)?
[/INDENT]
 [INDENT]**A.**  You can install OEM software in a virtual environment as long as you  have a separate license for each instance of the software. It is fine to  use the OEM version as long as it is properly licensed. To be clear, a  separate version of the software must be installed for both the  “standard” and “virtual” installations.
[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT] [http://www.microsoft.com/OEM/en/Pages/support-faq.aspx](http://www.microsoft.com/OEM/en/Pages/support-faq.aspx)[/INDENT]

That just sounds like you can't run more than one session of the same software, e.g. Using the same license for host and guest. Am I misreading it?

---

### Post by QIII on 2014-07-20
You can't have it *installed *on more than one machine without a separate license for each machine, be that physical or virtual.

You need two licenses to install Windows on a virtual machine and on a physical machine.

You can't just use a single license and turn one off before turning the other on.

"Instance" != "Session"

---

### Post by kurt18947 on 2014-07-20
So one cannot have two instances of the same software installed even if only one is in use at a given time.  Is it kosher to uninstall the 'real' instance and install a virtual instance?  There would be only 1 Windows O.S. installed in that case, a virtual one.  Not trying to be a pain, just trying to understand.

---

### Post by QIII on 2014-07-20
No. By Microsoft's EULA, you cannot have two instances if you only have one license.  A license is required for each machine.

The problem with an OEM disk is that when it is registered/validated with a product key, it is locked to the original hardware it is installed on.  If you were to remove that instance and attempt to install using the same product key on a different machine, you would not be able to validate -- even if the virtual machine was created on the same computer as the original installation.

Most VM solutions create a hardware abstraction layer that is different from the physical hardware.  The difference would be detected and the validation process would fail.

---

### Post by at_first_light on 2014-07-20
OEM key activation makes the key specific to that computer. It cannot be transfered to a new machine like retail keys.

---

### Post by kurt18947 on 2014-07-20
> **QIII said:**
> No. By Microsoft's EULA, you cannot have two instances if you only have one license.  A license is required for each machine.

The problem with an OEM disk is that when it is registered/validated with a product key, it is locked to the original hardware it is installed on.  If you were to remove that instance and attempt to install using the same product key on a different machine, you would not be able to validate -- even if the virtual machine was created on the same computer as the original installation.

Most VM solutions create a hardware abstraction layer that is different from the physical hardware.  The difference would be detected and the validation process would fail.

Okay, that makes sense ........... I guess.  Even though the same processor(s), RAM, Hard drive, network adapter etc. are used, the HAL makes it look different.

---

### Post by QIII on 2014-07-20
Not exactly.  

The VM software presents its own "hardware" via a hardware abstraction layer.  The CPU is different (say you have an eight core CPU and assign only two cores to the machine, then it is a dual core processor as far as any OS is concerned.), the network adapter is different, the graphics adapter is different, etc.

The virtualization software handles communication between the OS on the virtual machine and the physical hardware.  But from the point of view of the OS, it's a completely different machine with different hardware.

It's called a *Virtual *Machine for a reason.  :)

---

### Post by monkeybrain20122 on 2014-07-20
Of course it is better to install in  hard drive. is that a trick question? :)

---

### Post by LastDino on 2014-07-20
Get it on HD as many have suggested. You may consider having cheap ssd or external HD for that if you don't want to mess with the current config.

Installing on VM is not a bad idea but it will need considerable resources and if you don't have them, you wont get best offered performance out of Ubuntu. Even if you install the lighter versions of Ubuntu, being on VM is totally different than being installed on HD. And the difference is noticeable.

---

