---
title: "VMware"
date: 2012-08-31
forum: Virtualisation
---

### Post by Akhj on 2012-08-31
Dear All,

Greetings of the Day.

I am new to Linux. And very 1st time i am using Ubuntu. Here are the specification :-
I have a Desktop running Windows XP SP3. I have installed VMware 6.5.3 & installed Ubuntu 12.04 (LTS 32 bit). Now i am trying to install VMware-tools. But unable to do so. Please help me step by step. Below is the pasted what i have done :-

lg@lg-virtual-machine:~$ sudo -i
[sudo] password for lg: 
root@lg-virtual-machine:~# /usr/bin/vmware-config-tools.pl

Stopping VMware Tools services in the virtual machine:
   Guest operating system daemon:                                      done
   Virtual Printing daemon:                                            done
None of the pre-built vmmemctl modules for VMware Tools is suitable for your 
running kernel.  Do you want this program to try to build the vmmemctl module 
for your system (you need to have a C compiler installed on your system)? 
[yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

The path "/usr/src/linux/include" is not an existing directory.


Please help me.
Thanks & Regards

---

### Post by TJet1.8 on 2012-08-31
To compile the modules, you need 3 components:
- The gcc compiler.
- The linux headers for your kernel.
- The build files.

It looks like you have the compiler...but not the other 2 components.

To be sure, just install all 3 components:

sudo apt-get install gcc linux-headers-$(uname -r) build-essential

Then re-run the vmware tools install.

Good luck.

;)

---

### Post by Akhj on 2012-09-01
TJet, 1st of all Thanks for a quick reply :) . But i am new to Linux/Ubuntu and knows nothing. Although i followed steps as you had told (as per my best knowledge) :-

lg@lg-virtual-machine:~$ uname -r
3.2.0-29-generic-pae
lg@lg-virtual-machine:~$ sudo apt-get install gcc linux-headers-$3.2.0-29-generic-pae build-essential
[sudo] password for lg: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-.2.0-29-generic-pae
E: Couldn't find any package by regex 'linux-headers-.2.0-29-generic-pae'


Please let me know step-by-step (if possible for you or anybody) 
I know its boring / tiring job to explain but eventually i will learn.
Thanks & Regards

---

### Post by Old_Grey_Wolf on 2012-09-01
Try the command without the $ in front of the kernel number.
```
sudo apt-get install gcc linux-headers-3.2.0-29-generic-pae build-essential
```

---

### Post by dcstar on 2012-09-01
> **Akhj said:**
> Dear All,

Greetings of the Day.

I am new to Linux. And very 1st time i am using Ubuntu. Here are the specification :-
I have a Desktop running Windows XP SP3. I have installed **VMware 6.5.3** & installed Ubuntu 12.04 (LTS 32 bit).
..........

VMware Workstation 6.5.3 is ancient and does not support 12.04 VMs.

Get a current version.

---

### Post by Akhj on 2012-09-02
@ Old_Gray_Wolf : Thanks, i tried the given command but result is same as earlier :
```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 
```
@ dcstar : Thanks for revert. I will search if i could find a latest version.

---

