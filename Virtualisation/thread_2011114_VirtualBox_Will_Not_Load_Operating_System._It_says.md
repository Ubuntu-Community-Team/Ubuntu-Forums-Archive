---
title: "VirtualBox Will Not Load Operating System. It says to use appropriate kernel"
date: 2012-06-26
forum: Virtualisation
---

### Post by robtygart on 2012-06-26
[Solved] [http://ubuntuforums.org/showpost.php?p=12056903&postcount=4]("http://ubuntuforums.org/showpost.php?p=12056903&postcount=4")

The program loads but the OS does not. I get this message when trying to load an Operating system, I have tried two.

```
This kernel requires the following features not present on the CPU: pae
Unable to boot – please use a kernel appropriate for your CPU.
```

I haven't updated to 12.04 yet. Is the kernel of my running system the problem? 

My "Muon software center" Keeps crashing so I downloaded it using the package manager. 

What I installed 
x86 virtualization solution
And it added the rest.

---

### Post by dummy910 on 2012-06-26
I ran into this exact problem on a laptop just yesterday and here's what I did to get Virtual to run error free,  and here's where I found a solution that worked.  

**[http://forums.debian.net/viewtopic.php?f=10&t=80468 ]("http://forums.debian.net/viewtopic.php?f=10&t=80468")**

```
sudo apt-get install linux-headers-`uname -r`
``````
sudo apt-get --reinstall install virtualbox virtualbox-dkms
``````
sudo modprobe vboxdrv
```

---

### Post by robtygart on 2012-06-26
No. I am still getting the same message. I have used this one before. I might take a look at anoter program, I haven't ever looked. Do you have any reccomendations?

---

### Post by robtygart on 2012-06-26
[Solved]

    Power off Virtual Machine
    Click Machine -> Settings -> System -> Processor
    Check Enable PAE/NX
    Click OK
    Start Virtual Machine

[COLOR="Red"][/COLOR]**Thank you dummy910**

---

