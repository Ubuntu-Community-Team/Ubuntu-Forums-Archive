---
title: "Ubuntu 18.04.1LTS runs slowly on virtualbox-v5.2.18!!!"
date: 2018-09-29
forum: Virtualisation
---

### Post by michaelcc2 on 2018-09-29
Hi guys,

I installed Ubuntu v18.04 in the virtualbox-v5.2.18. 
I find the Ubuntu 18.04.1 LTS runs slowly after maximizing the window of files folder, terminal window or the browser, etc each time.
It's very easily reproduced. It's very annoyed.  Is this a bug?

---

### Post by TheFu on 2018-09-29
Why do you think it is a bug?

---

### Post by michaelcc2 on 2018-09-29
Actually I'm not very sure, but I quite doubt it's a bug.
Each time when I click the maximizing button of the window of files folder/files management/terminal..., the system begins to run very slowly.  
I have seen such case on about six computers, the host system includes WIN7 and WIN10, and the virtualbox's version is V5.2.18.

---

### Post by TheFu on 2018-09-29
Sorry I wasn't clear.

You say it is slow, but don't compare it against anything else.

You haven't provided any hardware specs for CPU, RAM, storage, storage type, networking, ...   I expect virtualbox to perform terrible on a Pentium4 with 1GB of RAM.  BTW, people do still use systems like that.

Some people try to run Ubuntu off a slow USB2 flash drive and expect great performance.  That isn't likely.

You haven't provided any VM settings.  I can make any OS run like crap if I setup the VM poorly, even on the newest Core i7 systems, poor configuration can lead to terrible performance.

Did the same hardware and config run Ubuntu 12.04 perfect? 14.04?  16.04?  Or is this the very first release ever attempted?  

Was it a fresh install or upgrade?

Are you using the defaults for everything? Have you tried lighter desktops than gnome3?  DEs that prefer direct access to a GPU tend to perform poorly inside a VM.  Very few people use Gnome3 inside a VM.

Did you follow any Virtualbox tuning guides?

So, will you share some info, please?

---

### Post by michaelcc2 on 2018-09-29
Right now I thought of the virtualbox's 3D accelerator. It was enabled since I created the virtual machine (VM).
Now, after I disable it, the issue above disappears...  really unbelievable....  I'm sure the virtualbox's extended package has already been installed in the VM.

The VM configuration I have tested is shown below.
1. CPU cores: 2~4 cores.
2. RAM memory: 4GB~5GB.
3. ROM memory: 32GB~380GB
4. Display cache: 128MB

So, do you have some other ideas about this issue? Maybe it's a virtualbox's bug.. hahaha..

---

### Post by coffeecat on 2018-09-29
Support, not chat.

*Thread moved to **Virtualisation**.*

---

### Post by TheFu on 2018-09-29
And the other answers?

---

### Post by michaelcc2 on 2018-09-29
OK&#65292;thanks for your reminder.

---

### Post by michaelcc2 on 2018-09-29
> **TheFu said:**
> And the other answers?

I don't know why...

---

### Post by rhorne on 2018-10-12
Lots of things can slow down a VM.  Running a VM off of a spindle drive versus a SSD is a big one.  Even slow SSDs are 5x faster than a HDD.

Running Ubuntu in a Windows host from a spinning hard drive gave me abysmal performance. I thought it was Ubuntu just running slow at first.  It wasn't until I ran VMs from a Linux host off of a SSD drive that I figured out that VMs can run like a scalded banshee.  They just have to be set up right.

Oh, and the new Hyper-V installs of Ubuntu in Windows have terrible performance over RDP.  Virtualbox is faster.

---

### Post by TheFu on 2018-10-12
If you use sparse files for storage, then an SSD is very helpful.  If you fully preallocate the storage, it isn't very important at all. 90+% of native performance is very possible, for non-GUI applications.

Windows as a VM host has some issues, but performance can be tuned to get reasonable, feels-like-native performance for non-GUI programs.

Saw a trick for hyper-v VMs.  Don't use auto-login and disabled both 2D and 3D accel.

For virtualbox, there are multiple guides for tuning the virtual machines for performance. "vbox performance improvements" will find them. The general rules apply to all hypervisors. VMs work fine with office programs and server stuff without too much difficulty.  Good performance for heavy GUI programs is harder. [https://askubuntu.com/questions/190330/how-do-i-improve-the-performance-of-my-virtualbox-guest](https://askubuntu.com/questions/190330/how-do-i-improve-the-performance-of-my-virtualbox-guest) has details.

---

