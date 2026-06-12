---
title: "avoid halt command by ssh"
date: 2009-03-26
forum: Server Platforms
---

### Post by islanddancer on 2009-03-26
Hi, there
I have got two questions about a ubuntu server, the /etc/issue shows it is a dapper.

1 
how to determine if the dapper on the server is a server version or a desktop version?

2 how to avoid careless halt via ssh.
sometimes I forgot I was working on a server and did a halt. and it shuts the server down which is nightmare...

Thank you for any pointers.

Zhang

---

### Post by castrojo on 2009-03-26
For 1 - there might be a more formal way to do it but I usually just do a uname -a and see if a server kernel is running

2 - The package "molly-guard" is a great way to prevent accidents.

---

### Post by islanddancer on 2009-03-26
> **whiprush said:**
> For 1 - there might be a more formal way to do it but I usually just do a uname -a and see if a server kernel is running

2 - The package "molly-guard" is a great way to prevent accidents.


Thank you very much for your response!

so is this 
Linux  2.6.15-27-amd64-xeon #1 SMP PREEMPT Fri Dec 8 18:09:00 UTC 2006 x86_64 GNU/Linux

a server kernel?

Thank you once again!

---

### Post by windependence on 2009-03-26
```
cat /etc/issue
```

-Tim

---

### Post by Bachstelze on 2009-03-26
There is no fundamental difference between a "Server" and a "Desktop" version. Even the meaning of those terms is very vague, so there is no way to clearly distinguish them.

---

### Post by windependence on 2009-03-26
> **HymnToLife said:**
> There is no fundamental difference between a "Server" and a "Desktop" version. Even the meaning of those terms is very vague, so there is no way to clearly distinguish them.

Sorry but you are blatantly wrong.

> **Optimised Kernel **

  The Linux kernel is world-renowned for its superb efficiency and its capacity to be configured to match particular requirements. Ubuntu Server Edition includes a specially configured kernel to match the requirements of all common workloads typically found on a server so that you get the most out of your hardware while maintaining optimal power consumption. Whether you will be running on Intel, AMD or Sun Sparc processors in 32 or 64 bit modes, our engineers have worked closely with the hardware manufacturers in order to ensure optimisation for the specific architectures, right up to the most recent ones at the time of release. 
  Here is a list of the server-specific kernel optimisations that we include: 
 
[LIST]
[*]  	The Server Edition uses the Deadline I/O scheduler instead of the CFQ scheduler used by the Desktop Edition. 	
[*]  	Pre-emption is turned off in the Server Edition. 	
[*]  	The timer interrupt is 100 Hz in the Server Edition and 250 Hz in the Desktop Edition. 	
[*]  	The Server Edition is optimised for i686 processors while the Desktop Edition is optimised for both  the i586 and i686. 	
[*]  	Virtualization is better supported in the Server Edition through the enabling of IPC namespaces. 	
[*]  	Multiple routing tables for the IPv6 protocol are also supported in the Server Edition. 	
[*]  For 32-bit systems the Server Edition is configured to use PAE which allows addressing up to 64GB of memory while the Desktop Edition is configured for 4GB. 
[*]  	When running a 64-bit version of Ubuntu on 64-bit processors you are not limited by memory addressing space. 	
[/LIST]
 **Optimised for Virtualization**

  Ubuntu Server Edition is optimised to run in a virtual environment through work done on multiple aspects of the Linux Kernel, including IO drivers and usage of hardware features. This work is done, for KVM, our selected open source technology, as well as in co-operation with leading virtualization vendors to ensure performance and availability when used not only as a guest operating system, but also as a virtualization host.
[More on virtualization >> ]("http://www.ubuntu.com/products/whatisubuntu/serveredition/technologies/virtualization") 
  Additionally, for companies that would like to take advantage of our optimisation work to distribute their software as a virtual appliance, the Canonical ISV team can explain how to use Ubuntu JeOS, a Server flavour built to run virtual appliances in VMware or KVM environments. JeOS can also be used by users to deploy their custom application on virtualization farms.
[URL="http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos"]More on Ubuntu Server Edition JeOS >>
[/URL] 
 **New in 8.10**

  [DKMS]("http://linux.dell.com/dkms") (by Dell) is included in Ubuntu 8.10, allowing kernel drivers to be automatically rebuilt when new kernels are released. This makes it possible for kernel package updates to be made available immediately without waiting for rebuilds of driver packages, and without third-party driver packages becoming out of date when installing these kernel updates. 
   
  
       



[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel)

-Tim

---

### Post by islanddancer on 2009-03-26
> **windependence said:**
> Sorry but you are blatantly wrong.



[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel)

-Tim

I catted /etc/issue

Ubuntu 6.06.2 LTS \n \l

so is it a server edition?

---

### Post by cariboo on 2009-03-26
No you aren't using a server kernel, you kernel is compiles for xeon support. I'm not really sure if you would gain anything by going with a server kernel for your version. After Dapper, it looks like xeon support is compiled into the kernel so you may want to update to a newer version.

Jim

---

### Post by islanddancer on 2009-03-26
> **cariboo907 said:**
> No you aren't using a server kernel, you kernel is compiles for xeon support. I'm not really sure if you would gain anything by going with a server kernel for your version. After Dapper, it looks like xeon support is compiled into the kernel so you may want to update to a newer version.

Jim
Hello,
you mean a newer version in the dapper repository or upgrade dapper to higher version?
Thanks!

---

### Post by Xiong Chiamiov on 2009-03-27
> **islanddancer said:**
> how to avoid careless halt via ssh.
sometimes I forgot I was working on a server and did a halt. and it shuts the server down which is nightmare...

```

shudown -c

```
cancels shutdown.

---

### Post by windependence on 2009-03-27
> **cariboo907 said:**
> No you aren't using a server kernel, you kernel is compiles for xeon support. I'm not really sure if you would gain anything by going with a server kernel for your version. After Dapper, it looks like xeon support is compiled into the kernel so you may want to update to a newer version.

Jim

Thanks for answering this one Jim, I missed it.

-Tim

---

### Post by volkswagner on 2009-03-27
> **islanddancer said:**
> Thank you very much for your response!

so is this 
Linux  2.6.15-27-amd64-xeon #1 SMP PREEMPT Fri Dec 8 18:09:00 UTC 2006 x86_64 GNU/Linux

a server kernel?

Thank you once again!

You have 64bit Desktop edition. 

Your kernal has not been updated since December 2006.

---

### Post by islanddancer on 2009-03-27
> **volkswagner said:**
> You have 64bit Desktop edition. 

Your kernal has not been updated since December 2006.

I thought at least it is a workstation...

---

### Post by Bachstelze on 2009-03-27
> **windependence said:**
> Sorry but you are blatantly wrong.

So by your reasoning, just installing the server kernel on a desktop system magically turns it into an Ubuntu Server Edition&#8482;? Fair enough, but I disagree. Actually, I think Ubuntu Server Edition, just like Kubuntu, Xubuntu, etc. is just a marketing term and is totally nonsensical in practice. I only know Ubuntu.

Oh, and by the way, your suggestion of looking at /etc/issue was blatantly wrong too. Last I checked, it doesn't print the kernel version.

---

### Post by islanddancer on 2009-03-27
> **HymnToLife said:**
> So by your reasoning, just installing the server kernel on a desktop system magically turns it into an Ubuntu Server Edition™? Fair enough, but I disagree. Actually, I think Ubuntu Server Edition, just like Kubuntu, Xubuntu, etc. is just a marketing term and is totally nonsensical in practice. I only know Ubuntu.

Oh, and by the way, your suggestion of looking at /etc/issue was blatantly wrong too. Last I checked, it doesn't print the kernel version.

I don't get kernel info in /etc/issue either.

---

### Post by Bachstelze on 2009-03-27
> **islanddancer said:**
> I don't get kernel info in /etc/issue either.

The command to get your kernel version is [font="monospace"]uname -r[/font]. As you saw, you're not running the server kernel. To install it, do

```
sudo apt-get install linux-image-server
```

---

### Post by windependence on 2009-03-28
> **HymnToLife said:**
> So by your reasoning, just installing the server kernel on a desktop system magically turns it into an Ubuntu Server Edition™? Fair enough, but I disagree. Actually, I think Ubuntu Server Edition, just like Kubuntu, Xubuntu, etc. is just a marketing term and is totally nonsensical in practice. I only know Ubuntu.

It's not MY reasoning. It's Canonical's, which I think as a member of the forum staff, you should have been aware of. If you bothered to read the entire server section of the Ubuuntu web site, you would see that the server edition is far from just another kernel plopped on top of a desktop distro. This is not in ANY way my thought, it is pure information from the website of the creators of this Linux distribution.

> **HymnToLife said:**
> Oh, and by the way, your suggestion of looking at /etc/issue was blatantly wrong too. Last I checked, it doesn't print the kernel version.

Not quite. The uname command was the first response to his question, and /etc/issue gives additional information as to the installed version. I wouldn't call that blatant, but rather an attempt to discredit me for pointing out YOUR blatant error. Of course, this isn't helping anyone here at all. If you are trying to bully me because you are forum staff, I'm not biting. Posting your opinion that the server edition is no different from the desktop edition as if it was fact (more credible because you are a staff member) misleads people who are new to this distro, or who may not be aware of what the server version entails. I'm not so sure Canonical would agree with your assessment. At best, if your opinion is correct, it is also misleading as there are definite advantages to running the server version over the desktop version if you are running a production server, otherwise why would they even go to the trouble to offer it?

-Tim

---

