---
title: "Xen on Jaunty"
date: 2009-07-16
forum: Virtualisation
---

### Post by xOrphenochx on 2009-07-16
Sorry for cross posting, was late at night.

--------------------------------------------------------------------------------

Welp, time to resort to posting. Compiled 2.6.30 kernel find. Compiled xen 3.4 fine after much troubleshooting. Doesn't work, I get python errors about missing modules. I follow a guide and install some deb kernels and the xen off of the official jaunty repositories, computer reboots after I've edited grub per the documentation. What in the world am I missing?!

Links used:
[http://www.infohit.net/blog/post/run...nd-jaunty.html](http://www.infohit.net/blog/post/run...nd-jaunty.html)

Google:
[http://www.google.com/search?q=ImportError:+No+module+named+xen.xend.server&hl=en&start=10&sa=N&cts=1247713054030&cts=1247713087799](http://www.google.com/search?q=ImportError:+No+module+named+xen.xend.server&hl=en&start=10&sa=N&cts=1247713054030&cts=1247713087799)

[http://www.google.com/search?q=from%20xen.xend.server%20import%20SrvDaemon&ie=utf-8&oe=utf-8](http://www.google.com/search?q=from%20xen.xend.server%20import%20SrvDaemon&ie=utf-8&oe=utf-8)

[http://www.google.com/search?hl=en&q=xen.lowlevel.xc.error+1+%27internal+error%27+%27could+not+obtain+handle+on+privileged+command+interface&cts=1247710701518&aq=0&oq=xen.lowlevel.xc.Error%3A+(1%2C+%27Internal+error%27&aqi=g1](http://www.google.com/search?hl=en&q=xen.lowlevel.xc.error+1+%27internal+error%27+%27could+not+obtain+handle+on+privileged+command+interface&cts=1247710701518&aq=0&oq=xen.lowlevel.xc.Error%3A+(1%2C+%27Internal+error%27&aqi=g1)

---

### Post by champi0n on 2009-07-17
Been trying to get Xen working on ubuntu for 2 days now.

Apparently they've switched to support the KVM visualization which is very insecure by the nature of how it works. So this doesn't work for anyone wanting to use any type of production environment. 

I have xenserver (enterprise) installed in about 10 minutes on 2 other machines, where I'm able to add VM's and configure storage and all that jazz.

But I want to install Xen (opensource) on my raided ubuntu setup but it's a HUGE Pain! I want to have ubuntu as the dom0 - so i can still keep the desktop to do various things, but many hours of BS and it's not working.

I'm actually going to give up on ubuntu and switch to CentOS for ease of installation. Unless by some miracle i get it working on ubuntu in the next 4 hours.

---

### Post by bodhi.zazen on 2009-07-17
champi0n : xen , dom0 , is supported on Ubuntu 8.04. Ubuntu 8.10 supports domU.

I am not sure about 9.10, the Ubuntu wiki says you can run dom0 with a Debian kernel, but I am skeptical and have not tried.

I have learned the hard way, if you want to run virtualization you should stay with a supported host. This holds true for openvz, Xen, and VMWare.

VirtualBox seems to have the boradest host support followed by VMWare, although you will often need to find and apply unsupported patches for VMWare.

KVM also has fairly broad support if you have the hardware.

Xen is very spotty.

Do you have any documentation to back up your claim that KVM is not ready for a "production server" , I have never heard this and am wondering if you would not mind pointing me to a technical reference.

---

### Post by xOrphenochx on 2009-07-18
Oh wow, I got replies. Yeah, I'm playing with KVM right now, but I wanted to get my hands into everything I can and just as champi0n has stated, its a major PITA. I think most of my problems lie in getting xen to run with the kernel, no matter what I do, after grub loads it reboots my pc, or hangs. I even made the one kernel Jeremy put out for Xen, no luck. For now I have the Lenny kernel and this config, which it made after installing the kernel, this one causes a reboot after grub loads, no Ubuntu splash, just instant reboot.

title           Xen 3.3 / Ubuntu 9.04, kernel 2.6.26-2-xen-amd64
uuid            0da846ae-248f-4fbe-8bca-837dfccab5df
kernel          /boot/xen-3.3.gz noreboot acpi=off
module          /boot/vmlinuz-2.6.26-2-xen-amd64 root=UUID=0da846ae-248f-4fbe-8bca-837dfccab5df ro console=tty0
module          /boot/initrd.img-2.6.26-2-xen-amd64
quiet

---

### Post by champi0n on 2009-07-22
Well you are aware with KVM that if one VM gets "rooted", it can expose the entire system. (including all the other VMs)

But either way, it's not going to install on ubuntu 9.10 without heavy modification and custom building. 8.04 might be a bit "easier" by actually being able to apt-get install the xen stuff

I figured it easiest (and it was) to download centos 5.3 and install it. Clicked the "virtualization" checkbox during install and XEN kernel was chosen and virtual management tools were installed. (also didn't have to download an alternate cd to install raid which saved a cd)

System booted up and right away I could create a new VM.

I do like Ubuntu as a desktop os. but unfortunately for ease of use in virtualization I had to go centos.

---

### Post by bodhi.zazen on 2009-07-22
Nothing wrong with Centos, it is a nice OS.

No need to bash OS, Ubuntu or otherwise, it does not sound as if you tried 8.04 =)

At any rate you make some fairly broad claims against KVM, which version of KVM are you referring to and would you be so kind as to provide a technical reference, bug report, or security alert to back that up ? I would be interested in reading it.

Although Xen is popular in RHEL, I think outside of RHEL, interest in Xen is waning, not to say that Xen does not have nice features mind you, I just see Xen becoming less popular.

---

### Post by juancarlospaco on 2009-07-23
> **champi0n said:**
> 
I have xenserver (enterprise) installed in about 10 minutes on 2 other machines, where I'm able to add VM's and configure storage and all that jazz.

But I want to install Xen (opensource) 

I'm actually going to give up on ubuntu and switch to CentOS for ease of installation.

Citrix XenServer its Open Source Now, 
you can download the sources at Citrix.com, 
so its the same condition than Xen.

CentOS is a clone of Red Hat, 
and Red Hat preferred Virtualization is KVM.

You don't get pwned if all your VMs get rooted using KVM.
You don't get pwned if your Host get rooted using SELinux.

---

