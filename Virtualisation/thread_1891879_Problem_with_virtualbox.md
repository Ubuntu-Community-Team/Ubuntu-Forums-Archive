---
title: "Problem with virtualbox"
date: 2011-12-06
forum: Virtualisation
---

### Post by chenr1 on 2011-12-06
Hey guys. im trying to virtualize a operating system under virtual box but my problem is whenever i click start in virtualbox i get this error [B]VT-x/AMD-V hardware acceleration is not available on your system. Certain guests (e.g. OS/2 and QNX) require this feature and will fail to boot without it. 
[/B]
I can click continue but after the os loads i get this error

**A critical error has occurred while running the virtual machine and the machine execution has been stopped.****For help, please see the Community section on [[COLOR=#0000ff]_http://www.virtualbox.org_[/COLOR]]("http://www.virtualbox.org/") or your support contract. Please provide the contents of the log file VBox.log and the image file VBox.png, which you can find in the /home/caleb/VirtualBox VMs/OSX/Logs directory, as well as a description of what you were doing when this error happened. Note that you can also access the above files by selecting Show Log from the Machine menu of the main VirtualBox window.**
**Press OK if you want to power off the machine or press Ignore if you want to leave it as is for debugging. Please note that debugging requires special knowledge and tools, so it is recommended to press OK now.**
 could use any help you guys could give. 

Im also on an optiplex 745
thanks

---

### Post by CharlesA on 2011-12-06
You can't virtualize OSX unless you are virtualzing OSX server.

---

### Post by chenr1 on 2011-12-06
But i just read that you can. [http://lifehacker.com/5583650/run-mac-os-x-in-virtualbox-on-windows.]("http://lifehacker.com/5583650/run-mac-os-x-in-virtualbox-on-windows")

---

### Post by CharlesA on 2011-12-06
If you are running it on non Apple hardware, it's a breach of Apple's ToU.

In any case Installing pure OSX in VirtualBox isn't supported by Oracle or these forums.

---

### Post by chenr1 on 2011-12-06
1. First how do you suppose im emulating osx. (which you happen to be right about)
2. Your not going to help me with this problem? Please just don't lock it before i get any help.

---

### Post by CharlesA on 2011-12-06
> **chenr1 said:**
> 1. First how do you suppose im emulating osx. (which you happen to be right about)
2. Your not going to help me with this problem? Please just don't lock it before i get any help.

1. Magic.

2. Your Processor doesn't support hardware virtualization, so you will not be able to run 64-bit guests on a 32-bit OS.

---

### Post by chenr1 on 2011-12-06
How do i run in 32 bit? im a bit familiar with hackintoshes but not virtulazation.

---

### Post by CharlesA on 2011-12-06
No idea.

You won't get any support here though.

---

