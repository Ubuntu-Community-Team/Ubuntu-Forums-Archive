---
title: "Networking Final Year Project Based on Virtualization"
date: 2007-11-02
forum: Virtualisation
---

### Post by Mechanized_Infantry on 2007-11-02
Hey guys! Nice to be on the forums

Well anyway, I have my final year project which I am starting to write up and I was just wondering if you guys could possibly point out any critisms' with the aspect of the work

The premise of the project will be

-One PC runnig Ubuntu
-Ubuntu running VMWare Player & Win4Lin (Or any other virtualization software which is better, do you have any reccomendations?)
-The virual machine running XP and running a few programs and benchmarking the XP virtual machine to test performance
-Benchmarking Ubuntu to see how it runs with the different virtual machines
-Analysising results and drawing up a plan for a hypothetic situation where a network admin has a certain amount of machines running Ubuntu and he/she needs to run a windows virtual machine, and then providing the best out come

Do you think I can make the project better in any places? Which places do you think are good? 

Also, which of the virtualization tools do you think are better? I was advised on VMWare Player and Win4Lin, do you think that these are the best?

Thanks for all advise, I really appreciate this:guitar:

-Emeka

---

### Post by Delvien on 2007-11-04
> -One PC runnig Ubuntu
**: D**
> -Ubuntu running VMWare Player & Win4Lin (Or any other virtualization software which is better, do you have any reccomendations?)

**I would not use VMware player as my virtualization tool, Use VirtualBox OSE (open source edition) or just VirtualBox (labeled PUEL (Public User End License) (I think))**

> -The virual machine running XP and running a few programs and benchmarking the XP virtual machine to test performance
**VirtualBox... fastest emulation I have come across.**

> -Benchmarking Ubuntu to see how it runs with the different virtual machines
**ubuntu is fast, I dont think there are benchmarking tools though.**

> -Analysising results and drawing up a plan for a hypothetic situation where a network admin has a certain amount of machines running Ubuntu and he/she needs to run a windows virtual machine, and then providing the best out come.

**How about a school teacher that deals with Adobe Photoshop and needs the speed of a regular workstation, but the school uses Ubuntu for its Host OS, because of the overall cost/security. So a Virtual machine is needed to run Adobe Photoshop (which is what i use my virtual machine for)**

> Do you think I can make the project better in any places? Which places do you think are good? 

**Hard to say, I dont know what class you are taking.**

> Also, which of the virtualization tools do you think are better? I was advised on VMWare Player and Win4Lin, do you think that these are the best?

**win4Lin = slow, Vmware player=limited. Again, I would use VirtualBox over anything else right now, that or VMware workstation.**

> Thanks for all advise, I really appreciate this:guitar:
**Anytime :P**

---

### Post by Mechanized_Infantry on 2007-11-05
Thank you very much for the reply! I will hopefully keep this thread updated with results etc

> I would use VirtualBox over anything else right now, that or VMware workstation.

That could be a possible thing that I test. In a series of tests:

**_Which O/S operates better with a VM_**

-Two different Linux o/s (Ubuntu vs Fedora/SUse) with Virtualbox & VMWare running XP to see which O/S virtualises better. Or would the difference be so minimal that it would not be useful testing?

**_Find which VM is faster/more reliant_**

-Virtual Box vs VMware Workstation (One one o/s [The quickest one out of the test after analysis]) 

Then

**_Which is more worthwhile, a stand alone program virtualiser (WINE) or an o/s VM_** (Hopefully it wont be as straight forward as WINE winning)

-Wine vs Virtual Box/VMware Player (Depending which one runs fastest. I want to test Wine for multiple windows/applications to see whether it holds up against one whole VM o/s)

Thanks for the input on the Photoshop part too, as that was an idea that I was looking for!

*edit

Who knows about the licensing on VMWare Player and XP. For example:

**_VMWare Problem_**
-One workstation > Then installing VMWare W/S on Ubuntu, and then installing it on a new HD running SuSe for example. Would it still work with the same license key?

**_XP Problem_**
-With the two virtual Machines running, installing it on VMWare & Virtual Box on Ubuntu.
-Then on VMWare & Virtual Box on Suse/Fedora. Will the same license key be OK? 

Thanks indeed:KS

---

### Post by Delvien on 2007-11-05
Since Wine runs applications not OS/s im afraid its two different genre's so to speak.

It would be a bad comparison because over all, the VM's would win. Wine is for running applications IN linux, not running Windows IN linux to run applications.

I hope to see more about your project : )

---

### Post by Delvien on 2007-11-05
> **Mechanized_Infantry said:**
> 
**_XP Problem_**
-With the two virtual Machines running, installing it on VMWare & Virtual Box on Ubuntu.
-Then on VMWare & Virtual Box on Suse/Fedora. Will the same license key be OK? 

Thanks indeed:KS

Ummm, cannot legally be done, because you must have 1 license per 1 install.

Not saying it its not possible, just illegal.

---

