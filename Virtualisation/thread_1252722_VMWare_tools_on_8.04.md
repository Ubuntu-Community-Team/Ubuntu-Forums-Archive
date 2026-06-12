---
title: "VMWare tools on 8.04"
date: 2009-08-29
forum: Virtualisation
---

### Post by cseguino on 2009-08-29
Hello,

I installed Ubuntu 8.04 in VMWare (I downloaded the iso today). It's working fine but now I'm trying to install the VMWare tools and it's not OK anymore.

I saw detailled procedures all around the Web ([http://www.howtogeek.com/howto/ubuntu/install-vmware-tools-on-ubuntu-edgy-eft/](http://www.howtogeek.com/howto/ubuntu/install-vmware-tools-on-ubuntu-edgy-eft/)) for exemple.

So I run all suggested commands successfully.

So I start the installation and I'm blocked here :

[FONT=Courier New]What is the location of the directory of C header files that match your running 
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.24-24/include/

The path "/usr/src/linux-headers-2.6.24-24/include" is a kernel header file 
directory, but it does not contain the file "linux/version.h" as expected.  This
can happen if the kernel has never been built, or if you have invoked the "make 
mrproper" command in your kernel directory.  In any case, you may want to 
rebuild your kernel.

What is the location of the directory of C header files that match your running 
kernel? 
[/FONT]

Does anyone can help me ?

Cheers,

Christophe Seguinot

---

### Post by cariboo on 2009-08-31
A bump for the move from Ubuntu One

---

### Post by Jive Turkey on 2009-09-09
hint: search using synaptic for kernel headers, or take 15sec and use google to find this command:

```
$ sudo apt-get install linux-headers-$(uname -r)
```

"sudo apt-get install <blah>" is how you install things from the repositories and "$(uname -r)" is a variable that returns a string(text) equal to the current version of the running kernel.

If your output looks like this you have a bigger problem:> user@host:~$ sudo apt-get install linux-headers-$(uname -r)
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.28-15-generic [COLOR="Red"]is already the newest version.[/COLOR]
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

