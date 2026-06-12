---
title: "Running Ubuntu 12.10 as a virtual machine"
date: 2012-10-29
forum: Virtualisation
---

### Post by ade234uk on 2012-10-29
I am currently using Kubuntu 12.10. I have installed Ubuntu 12.10 as a Virtual Machine. Ubuntu 12.10 installs fine, but performance is very sluggish.

I have gone in to compiz settings manager and turned off some of the effects.

I have installed Virtualbox Guest Additions

Any other ideas how I can improve performance?

I like using Kubuntu 12.10 as my main OS, but I would still like the ability to keep Ubuntu around.

---

### Post by 2F4U on 2012-10-29
How much processors and RAM did you assign to the VM? I have Ubuntu 12.10 running in a VM with 2 GB RAM, but it still feels a bit sluggish compared to 12.04. This seems to be a feature of the release and there are several reports on the web that 12.10 is slow compared to 12.04.

---

### Post by ade234uk on 2012-10-29
I am giving it 1.5GB of ram, 128mb of Graphics memory. I have Intel i5 processor so I could look at giving it more processor.

It's a shame because I remember when Ubuntu used to absolutely fly before Unity came along. 

I do hope that Ubuntu 13.04 main aim is to improve overall performance, because that will be one of the main reasons people will pull plug on Ubuntu. U

---

### Post by kennjason on 2012-10-29
How much RAM total does your machine have? When you're running your VM (or your base OS, really), what is the average usage of system resources?

---

### Post by c911darkwolf on 2012-10-30
This is prob a GPU issue.  that 128mb is Virtual Graphics.  Not Real Graphics memory.  I would bet money that your problem is running the 3d Unity profile.  


Did you goto settings on the virtual machine and Enable 3D Support under Display?

Attempts to turn off the Unity 3D desktop I think thats your issue.

I would suggest using [http://lubuntu.net/](http://lubuntu.net/) if all else fails.

---

### Post by danelwillis on 2012-10-30
its would probalbly work fast if you install ubuntu desktop envirmoent as well then theres no need for VM an you are using the potential of the computer

---

### Post by c911darkwolf on 2012-10-30
lubuntu would be better, it's a minimal resource setup.

---

### Post by MartinpRobson on 2012-10-30
There is a known issue with VirtualBox and 12.10 see [https://forums.virtualbox.org/viewtopic.php?f=1&t=52327.](https://forums.virtualbox.org/viewtopic.php?f=1&t=52327.)
Hopefully will be sorted soon. In the meantime I'd stick with 12.04.

---

### Post by markbl on 2012-10-30
Yes, known issue for Ubuntu 12.10 guests in current VB 4.2.4. See also [https://forums.virtualbox.org/viewtopic.php?f=3&t=51727](https://forums.virtualbox.org/viewtopic.php?f=3&t=51727).

---

