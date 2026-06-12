---
title: "Windows XP freezes sometimes in VMware Player 3.0"
date: 2009-11-05
forum: Virtualisation
---

### Post by littlevick on 2009-11-05
Hi Everyone,

Here is my Hardware Configuration
Dell D630 Laptop
2GB RAM 800MHz
Core 2 1.8G
Assign 1GB to Windows XP
VMPlayer 3.0
Xubuntu 9.10

I am currently making a linux system as a root parent to run the guest system - Windows XP Professionl on top of it. However, the whole system including host and guest will freeze together whatever I press the anykey from the keyboard, but after 1 minute the problem will go away. It will happen again in sometime. There have no time slot that the system will freeze.  I don't have any idea why it happens. Can anyone help me to figure out the problem?

Let me know if you need any information from me.

---

### Post by littlevick on 2009-11-12
> **littlevick said:**
> Hi Everyone,

Here is my Hardware Configuration
Dell D630 Laptop
2GB RAM 800MHz
Core 2 1.8G
Assign 1GB to Windows XP
VMPlayer 3.0
Xubuntu 9.10

I am currently making a linux system as a root parent to run the guest system - Windows XP Professionl on top of it. However, the whole system including host and guest will freeze together whatever I press the anykey from the keyboard, but after 1 minute the problem will go away. It will happen again in sometime. There have no time slot that the system will freeze.  I don't have any idea why it happens. Can anyone help me to figure out the problem?

Let me know if you need any information from me.


OK, I found that the vmware player 3.0 will check the ROM every time so that the laptop will hang.....

Anyone has any idea how can I modify the checking time of the ROM in vmx file?

---

### Post by alexgrex on 2010-11-14
Hello, I am having a similar problem with Ubuntu 10.04 and VMware Player 3.1
I try to make a virtual machine with windows xp, but the system freezes for 5 to 10 min, then continues operation for about 1 minute and again freezes making the installation take too long...

System info:
motherboard: ASUS P7H55-M LX 
processor: Core i5-750 4x 2.66GHz
memory: 4096 MB DDR3 1333MHz

VM
Win XP Pro
1024 MB assigned virtual memory
1 processor

tried with binary translation on and off. 

Any suggestion is appreciated

---

### Post by AlexanderDGreat on 2011-08-16
Yes, I agree VMware Player 3.0 hangs on Windows XP, I don't know why, but sometimes, if the Guest Windows XP, comes out of a screensaver , then it STOPS Freezes the Ubuntu Host, and itself.

I wonder why this happens.

---

### Post by AlexanderDGreat on 2011-08-16
OK first of all, try these:

On swapppiness - read the comments

[http://www.phocean.net/2006/12/06/slow-performance-in-vmware-using-ubuntu.html]("http://www.phocean.net/2006/12/06/slow-performance-in-vmware-using-ubuntu.html")

Then there's a user who investigated:

[http://communities.vmware.com/thread/146002]("http://communities.vmware.com/thread/146002")

Finally, a similar blog:

[http://magicbox.iblogger.org/vmware/how-to-tweak-vmware-workstation-in-linux-host/]("http://magicbox.iblogger.org/vmware/how-to-tweak-vmware-workstation-in-linux-host/")


And a very cool lots of info and links on the explanation of each one.

[http://www.techenclave.com/open-source-and-linux/post-you-vmware-workstation-optimization-parameters-196153.html]("http://www.techenclave.com/open-source-and-linux/post-you-vmware-workstation-optimization-parameters-196153.html")

Try them and post your comments! :)

---

