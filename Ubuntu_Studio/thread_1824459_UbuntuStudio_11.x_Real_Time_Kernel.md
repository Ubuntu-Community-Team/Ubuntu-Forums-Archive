---
title: "UbuntuStudio 11.x Real Time Kernel"
date: 2011-08-13
forum: Ubuntu Studio
---

### Post by JuanPabloCuervo on 2011-08-13
Hi,

just want to know if the RT Kernel supports [ifenslave]("http://linux.die.net/man/8/ifenslave") bonding "NIC Teaming"?
[http://linux.die.net/man/8/ifenslave](http://linux.die.net/man/8/ifenslave)

Thanks.

---

### Post by jejeman on 2011-08-13
Ubuntu studio 11.x does not have RT kernel. It uses generic kernel.

---

### Post by JuanPabloCuervo on 2011-08-13
> **jejeman said:**
> Ubuntu studio 11.x does not have RT kernel. It uses generic kernel.

Why in the Installation asks if i want to install the RealTime Kernel ?
and makes all kinds of warnings?

---

### Post by jejeman on 2011-08-14
Personally I've installed Ubuntu Studio 11.04, and it never ask me about RT kernel.
Maybe you refer when it asks some thing like: "Do you want to enable realtime priority?" Thats jack configuration, not RT kernel.

---

### Post by JuanPabloCuervo on 2011-08-14
> **jejeman said:**
> Personally I've installed Ubuntu Studio 11.04, and it never ask me about RT kernel.
Maybe you refer when it asks some thing like: "Do you want to enable realtime priority?" Thats jack configuration, not RT kernel.
You are right,
juanpc@ubuntu:~$ uname -a
Linux ubuntu 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686 i686 i386 GNU/Linux

time for apt-get install... or use another distro with Low Latency/Soft RT Kernel.

[https://launchpad.net/~abogani/+archive/ppa]("https://launchpad.net/%7Eabogani/+archive/ppa")

# add-apt-repository ppa:abogani/ppa
# apt-get update


[http://longspine.com/how-to/real-time-kernel-on-ubuntu-10-10-maverick-meerkat/](http://longspine.com/how-to/real-time-kernel-on-ubuntu-10-10-maverick-meerkat/)
[http://www.hispasonic.com/foros/kernel-30-real-time-sigue-siendo-necesario-parche-rt/374780](http://www.hispasonic.com/foros/kernel-30-real-time-sigue-siendo-necesario-parche-rt/374780)
[http://openstudio.no-ip.info/2011/01/install-low-latency-kernel-on-ubuntu-studio-10-10-maverick/](http://openstudio.no-ip.info/2011/01/install-low-latency-kernel-on-ubuntu-studio-10-10-maverick/)
[http://osdir.com/ml/ubuntu-studio-devel/2011-04/msg00115.html](http://osdir.com/ml/ubuntu-studio-devel/2011-04/msg00115.html)
[http://sevencapitalsins.wordpress.com/2007/08/10/low-latency-kernel-wtf/](http://sevencapitalsins.wordpress.com/2007/08/10/low-latency-kernel-wtf/)
[http://lowlatency.linuxaudio.org/](http://lowlatency.linuxaudio.org/)
[http://kernel.ubuntu.com/git?p=abogani/ubuntu-natty-lowlatency.git;a=commitdiff;h=38931b3ae14c0fd6b29589b79e18623fb8513ca4](http://kernel.ubuntu.com/git?p=abogani/ubuntu-natty-lowlatency.git;a=commitdiff;h=38931b3ae14c0fd6b29589b79e18623fb8513ca4)

---

### Post by JuanPabloCuervo on 2011-08-16
juanpc@juanpc-pc:~$ uname -a
Linux juanpc-pc 2.6.38-8-lowlatency-pae #42+all1~lucid1-Ubuntu SMP PREEMPT Fri Apr 29 03:15:36 UTC 2011 i686 GNU/Linux

64Studio Kernel vs. KXStudio with Abogani -lowlatency Kernel
:popcorn:

---

### Post by JuanPabloCuervo on 2011-08-16
Abogani -lowlatency didnt worked on UbuntuStudio 11 32-Bits
but found Linux-RT Hard a "fully   preemptive hard-realtime Kernel")
[http://pengutronix.de/software/linux-rt/debian_en.html](http://pengutronix.de/software/linux-rt/debian_en.html)

Let the Kernel War Begin...:popcorn:[URL="http://wiki.linuxmusicians.com/doku.php?id=system_configuration#how_do_i_build_a_realtime_audio_workstation_on_linux"]
http://wiki.linuxmusicians.com/doku.php?id=system_configuration#how_do_i_build_a_realtime_audio_workstation_on_linux[/URL]

AV Studio 5 [http://www.bandshed.net/](http://www.bandshed.net/)
vs.
UbuntuStudio 11
vs.
64Studio v3 beta
vs
KXStudio
vs.
Musix 3 Beta GNU/Linux [http://distrowatch.com/table.php?distribution=musix](http://distrowatch.com/table.php?distribution=musix)
vs.
Fedora CCRMA

---

### Post by Stanley2011 on 2011-10-12
stanley@stanley-System-Product-Name:~$  sudo apt-get install linux-rt linux-headers-rt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-rt
E: Unable to locate package linux-headers-rt

Now what to do?

---

### Post by sgx on 2011-10-13
Looks like you were offline, or the files were not there
for apt-get to find. If you have downloaded debian package files
to install locally,
use the full path and filename like this

sudo dpkg -i /home/stanlee/guitarix2_0.19.0-0lucid_i386.deb

You will be prompted if more files are needed.
Try adding the KX repositories, so you can utilize synaptic
to help build your system:

kernels:   [https://launchpad.net/~kxstudio-team/+archive/kernel](https://launchpad.net/~kxstudio-team/+archive/kernel)

list of KX PPAs   [https://launchpad.net/~kxstudio-team](https://launchpad.net/~kxstudio-team)

How to add a PPA repository for use with synaptic:

[https://launchpad.net/+help/soyuz/ppa-sources-list.html](https://launchpad.net/+help/soyuz/ppa-sources-list.html)

Cheers

---

### Post by Stanley2011 on 2011-10-13
I am sorry but I do not understand. How to download a PPA Sorry

---

### Post by sgx on 2011-10-13
Hi, the PPA is a small repository of software. Your system package manager, synaptic, looks in repositories for software updates. When you
are online, and press the reload button in synaptic, it checks the
repositories for updates, and refreshes the list with the information.

The list of repositories is a textfile

/etc/apt/sources.list

Yours will have entries for main, multiverse, universe, and maybe more.

To add official repositories, and PPAs, follow these guides:

[https://launchpad.net/+help/soyuz/ppa-sources-list.html](https://launchpad.net/+help/soyuz/ppa-sources-list.html)

There are security provisions involved, to insure that faked
software does not get listed or installed. Here is another guide
describing screenshots for each step.

[http://www.ubuntugeek.com/synaptic-package-manager-beginners-guide-for-ubuntu-users.html](http://www.ubuntugeek.com/synaptic-package-manager-beginners-guide-for-ubuntu-users.html)

Be patient, the system is excellent, once the (seemingly endless)
learning curve is climbed. (Actually, the freedom to constantly
learn and increase ones skills, is the great linux treasure :)  ) 

Corporate software giants tend to limit user access to knowledge, as they can sell it, per their business plans. And there are millions
of users content to only master the Enter-key and the spacebar, 
like me on a Saturday night;)
Cheers

---

### Post by Stanley2011 on 2011-10-14
sgx, I am so sorry for your time but I just not get it. How long is the learning curve?
I not understand the command line? I like the download button and set up wizard that works for me. I was hope to be recording by now. thanks for your time but for now I gave up until I can get some more money up to buy something that will work.

---

