---
title: "Xen kernel what parameters do I need to compile"
date: 2009-11-09
forum: Server Platforms
---

### Post by tapas_mishra on 2009-11-09
I compiled a xen kernel on my Ubuntu 9.04 ,
I am not clear with modules that I need to enable or disable to be able to use the Xen Kernel,everything went when when I did the following steps,except an error at the last of the compilation

[http://www.howtoforge.com/installing-xen-3.3-with-kernel-2.6.27-on-ubuntu-8.10-x86_64](http://www.howtoforge.com/installing-xen-3.3-with-kernel-2.6.27-on-ubuntu-8.10-x86_64)

The machine I am using is having Ubuntu 9.04 and the steps above are described for Ubuntu 8.10 but then more or less with minor modifications the steps should be same ,
The following commands executed successfully 
** Step1 **

apt-get upgrade

** Step2** 
apt-get install linux-image-server linux-server

** Step 3**
apt-get install ubuntu-xen-server build-essential libncurses5-dev gawk mercurial

** Step 4**
mkdir -p ~/build/linux-2.6.27-xen
  cd /usr/src/
hg clone [http://xenbits.xensource.com/ext/linux-2.6.27-xen.hg](http://xenbits.xensource.com/ext/linux-2.6.27-xen.hg)

** Step 5 **

cd linux-2.6.27-xen.hg
make O=~/build/linux-2.6.27-xen/ menuconfig

** Step 6** 
in the 
In the kernel configuration menu, after selecting the options which were described on the link 

[http://www.howtoforge.com/installing-xen-3.3-with-kernel-2.6.27-on-ubuntu-8.10-x86_64](http://www.howtoforge.com/installing-xen-3.3-with-kernel-2.6.27-on-ubuntu-8.10-x86_64)

** Step 7** 
when I started compiling the kernel 
make O=~/build/linux-2.6.27-xen/

here I got the error at the last step 

arch/x86/kernel/built-in.o: In function `timer_interrupt':
/usr/src/linux-2.6.27-xen.hg/arch/x86/kernel/time_32-xen.c:469: undefined reference to `__udivdi3'
make: *** [.tmp_vmlinux1] Error 1


So if some one can help me with what went wrong or tell me where more should I look for the solution.
I had a look on Gentoo xen documentation here
[http://www.gentoo.org/doc/en/xen-guide.xml](http://www.gentoo.org/doc/en/xen-guide.xml)

Some one please tell some right guide or document that help me with Xen on Ubuntu I want to run Dom0 on it.

---

### Post by tapas_mishra on 2009-11-09
Hi while googling The error that I got I came across 
[http://mulps.wordpress.com/2009/05/29/compiling-xen-kernel-2-6-29-2/](http://mulps.wordpress.com/2009/05/29/compiling-xen-kernel-2-6-29-2/)
some one suggested me it is a known issue  please suggest some thing.

---

### Post by tapas_mishra on 2009-11-12
I have finally got some luck in trying over Xen there are supported Operating System and some Operating Systems do not support 
I had been googling since I was getting a lot of errors as I had tried to install Xen or say compile a Dom0 kernel on it from jeremy repository on the unsupported OS,
and since from my post it is absolutely clear that I am a novice as far as Xen is concerned 
I came across a good book about XEN 
A hands on guide to the art of virtualization Jeanna Mathews
[http://www.amazon.ca/Running-Xen-Hands-Guide-Virtualization/dp/0132349663/ref=sr_1_3/189-9122115-5316947?ie=UTF8&s=books&qid=1258034980&sr=1-3](http://www.amazon.ca/Running-Xen-Hands-Guide-Virtualization/dp/0132349663/ref=sr_1_3/189-9122115-5316947?ie=UTF8&s=books&qid=1258034980&sr=1-3)

I am posting the above link so that if some one like me is searching for a lot of basic questions among documentations etc does not get confused by the blogs on internet everything available for free does not leads to the right solution.But still it has a lot of support on the community and a good place to ask questionbs is [http://gmane.org]("http://gmane.org/") the mailing list about xen users it is here 
[http://lists.xensource.com/xen-users](http://lists.xensource.com/xen-users)

A relevant thing to search on internet will be 
CONFIG_XEN_PCI
CONFIG_NETXEN_NIC
Initially they appear to be jargons but if you keep googling and reading you will answers.

---

