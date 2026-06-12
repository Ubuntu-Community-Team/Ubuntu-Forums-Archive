---
title: "Ubuntu Desktop on Vmware ESXi"
date: 2011-10-05
forum: Virtualisation
---

### Post by Tappers1979 on 2011-10-05
I have a VMWare ESXi 3.5 server running various OS's, most of which are fine and work well.

I have installed Ubuntu Desktop 10.10 and 11.04 and want to use them quite regularly for administration of other servers and various things.

My problem is the screen refresh is very slow and the mouse is really jerky / choppy when you move it.

I for some reason found it impossible to install the VMWare tools to resolve it (installing the VMWare tools on Windows resolved these problems), am I missing sometihng obviously or is there a guide that provides simple installation of the tools.....

All of the guides I have found on the internet haven't worked in one way or another....

Many thanks

---

### Post by lcman on 2011-10-05
> **Tappers1979 said:**
> I have a VMWare ESXi 3.5 server running various OS's, most of which are fine and work well.

I have installed Ubuntu Desktop 10.10 and 11.04 and want to use them quite regularly for administration of other servers and various things.

My problem is the screen refresh is very slow and the mouse is really jerky / choppy when you move it.

I for some reason found it impossible to install the VMWare tools to resolve it (installing the VMWare tools on Windows resolved these problems), am I missing sometihng obviously or is there a guide that provides simple installation of the tools.....

All of the guides I have found on the internet haven't worked in one way or another....

Many thanks

If I remember correctly, you need to mount the vmware tools media and run the .sh script.

---

### Post by Tappers1979 on 2011-10-06
Thanks for the reply Icman.

Where can I find the .sh script?

I have extracted the tools from the tar.gz and run the vmware-install.pl and got a load of problems with C libraries but when I finally got past that somehow it made no difference.

Am I looking in the wrong place?

Many thanks

---

### Post by dcstar on 2011-10-07
> **Tappers1979 said:**
> 
I have extracted the tools from the tar.gz and run the **vmware-install.pl** and got a load of problems with C libraries but when I finally got past that somehow it made no difference.


Install the **build-essential** package and try again.

You are using sudo, aren't you?

---

### Post by Tappers1979 on 2011-10-07
thanks dcstar.

I found it in synaptic package manager and when I selected it, it said mark for re-installation so have tried that, was that the correct thing to do?

I am using sudo when running the vmware-install.pl, I used the command:

sudo ./vmware-install.pl

Hope that is correct?

Just re-running the install with above command!

---

### Post by Tappers1979 on 2011-10-07
Just re-run and cam up against the same problem I have come again before that I cannot get past is the messages:

What is the location of the directory of C header files that match your running kernet? [/usr/src/linux/include]

If I press enter I get

The path "/usr/src/linux/include" is not an existing directory.

Have found Kernel version by running : uname -r

I got : 2.6.35-30-generic

In /usr/src I have a folder called linux-headers-2.6.35-30 and linux-headers-2.6.35-30-generic.

If I point the message above to these files I get:

The path "/usr/src/linux-headers-2.6.35-30" is an existing directory, but it does not contain a "linux" subdirectory as expected.

Is there a way to get what it is expecting as I really want to use the Ubuntu desktop through this but with the mouse all over the palce it is not useable!

Thanks for any assistance!

---

### Post by dcstar on 2011-10-07
Manually download the latest VMware Tools for Linux from the VMware website or set up your client to do it via Synaptic, the one you are currently trying to use may not be compatible with the later Ubuntu versions:

[http://www.vmware.com/pdf/osp_install_guide.pdf](http://www.vmware.com/pdf/osp_install_guide.pdf)

---

