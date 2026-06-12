---
title: "What is Virtualbox exactly?"
date: 2008-05-20
forum: The Cafe
---

### Post by ujhony03 on 2008-05-20
Is just like vmware? 
Whats the difference between the two? Are there any perfomance differences between either method?

Also, are you able to install virtualbox with the regular apt-get method?


Sorry if these are stupid questions, i just switched over to linux like a week ago.

---

### Post by spoown on 2008-05-20
I just installed it a few days ago ! And yes, it's like VMWare but there is an open source edition, and not with VMWare ! So, let's choose VirtualBox !

For performance and difference, I have no idea.

And yes, you can install it with a regular apt-get method, you can look at this page for more information on how to install it :

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)


It's really easy to install it and use it !!

---

### Post by mips on 2008-05-20
> **ujhony03 said:**
> Is just like vmware?
Yes

> **ujhony03 said:**
> Whats the difference between the two? Are there any perfomance differences between either method?

Not sure.

> **ujhony03 said:**
> Also, are you able to install virtualbox with the regular apt-get method?

Yes, should be able to from what I recall.


> **ujhony03 said:**
> Sorry if these are stupid questions, i just switched over to linux like a week ago.

No such thing as a stupid question.

For the average joe like me I prefer VirtualBox

---

### Post by stmiller on 2008-05-20
Virtualbox is based on qemu. It is now owned by Sun, and a .deb to install is available on the virtualbox webpage.

Vmware server is free, but the vmware 'workstation' costs money.


Performance on both are quite quick. Speed is pretty much identical and actual to your real hardware.

---

### Post by LaRoza on 2008-05-20
> **ujhony03 said:**
> 
Sorry if these are stupid questions, i just switched over to linux like a week ago.

VirtualBox is what I use. It has worked fine for me. Having no experience in the others, I can't judge it.

VirtualBox is also available for Windows, which is where I used it mostly actually, so you can use it there also.

---

### Post by jespdj on 2008-05-20
VirtualBox has some limitations compared to VMWare.

For example, if you have a dual-core or multi-core processor, then VirtualBox virtual machines will only use one core; VirtualBox doesn't support multi-core processors for the virtual machines. VMWare does.

Also, some other processor features such as 64-bit extensions and [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension") are not supported by VirtualBox. Because of this, you can't install a 64-bit OS in a VirtualBox VM and you can't install 32-bit Ubuntu Server (which uses PAE) in a VirtualBox VM.

Note that VirtualBox comes in two editions: the Open Source Edition (OSE) and the closed-source edition. The OSE edition, which is in the Ubuntu repository, does not support USB in virtual machines.

---

### Post by ujhony03 on 2008-05-20
> **jespdj said:**
> VirtualBox has some limitations compared to VMWare.

For example, if you have a dual-core or multi-core processor, then VirtualBox virtual machines will only use one core; VirtualBox doesn't support multi-core processors for the virtual machines. VMWare does.

Also, some other processor features such as 64-bit extensions and [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension") are not supported by VirtualBox. Because of this, you can't install a 64-bit OS in a VirtualBox VM and you can't install 32-bit Ubuntu Server (which uses PAE) in a VirtualBox VM.

Note that VirtualBox comes in two editions: the Open Source Edition (OSE) and the closed-source edition. The OSE edition, which is in the Ubuntu repository, does not support USB in virtual machines.

Ah.. i am running dual-core 64bit. VMWare it is then.

Thanks for the feedback from everyone!

---

### Post by bufsabre666 on 2008-05-20
all i know is virtualbox is so easy and simple to use and i couldnt figure out how in hell to make vmware work

virtualbox: win
vmware: FAIL

---

### Post by ujhony03 on 2008-05-20
> **bufsabre666 said:**
> all i know is virtualbox is so easy and simple to use and i couldnt figure out how in hell to make vmware work

virtualbox: win
vmware: FAIL

i got it to work as soon as i installed ubuntu. i'll look around to see if i can find the walkthrough i found. It was simple enough that even I (never had used linux before) could follow.
I was able to get XP installed no problem on it.

---

### Post by 3L33T on 2009-09-24
> **jespdj said:**
> 
Note that VirtualBox comes in two editions: the Open Source Edition (OSE) and the closed-source edition. The OSE edition, which is in the Ubuntu repository, does not support USB in virtual machines.

There is a way to enable USB in VirtualBox. [HERE's the link on how to do it.]("http://eyereex.eryell.com/?p=132")

---

### Post by Firestem4 on 2009-09-24
> **ujhony03 said:**
> Ah.. i am running dual-core 64bit. VMWare it is then.

Thanks for the feedback from everyone!

If you really need the performance from utilizing both cores then you shouldn't be looking to run a VM. And don't underestimate the power of a single-CPU. If anything, the CPU (32/64bit single or 32xquad) will not be your bottleneck lol. Most people don't use a CPU to their full potential. Running 100% utilization of a single core is where you finally "notice" the performance of your computer lol.

Also, 1 Core does not equal 32bit. Its still 64bit.

---

### Post by hellmet on 2009-09-24
The latest versions of Virtualbox also support PAE so you can run Ubuntu server

---

### Post by zupal1461 on 2009-09-25
right now, i am using VirtualBox to  test Ubuntu linux. For the reason that I don't want to mess up my unit. 

The host is a Windows xp sp2, while the guest is ubuntu linux. although, for now, i am still having trouble getting all the necessary packages installed/working since i am one of the many who has no internet connection :p

---

### Post by frogging on 2010-03-01
OK so this is going to sound real stupid but I'm going to ask it anyway.  So I guess I have to buy another copy of windows to use this product.  I have a windows laptop and a Linux desk top.  I can't print cause my Lexmark printer X4550 is not Linux compadable.  One of the form posts said 

Copied and pasted from [http://forums.linux-foundation.org/read.php?29,2980,page=2](http://forums.linux-foundation.org/read.php?29,2980,page=2)

**** Start copy paste

Re: LEXMARK X4550 looking for driver
Posted by: david (IP Logged)
Date: October 05, 2009 02:06PM

hello. i use Lexmark X4650 on ubuntu9.04 throght Window Vista. how? 

My native operating system computer is Ubuntu9.04. I have installed VirtualBox. Using VBox I have installed a virtual windows machine... when I want to print then I active VirtualBox, and throght Windows printing all the documents I need. 

Once printed documents, I close VirtualBox and continue using Linux. 

Easy? Easy is the only way!

End copy paste****

This is the only work around I have found
So my question is once I get this set up will I have to get a new copy of win XP to run on the virtualbox.

Im new to this Linux thing.  Don't want to buy a new printer, or another Microsoft Program.

---

### Post by Johnsie on 2010-03-01
it's a PC emulator in a program ;-)

---

### Post by Kantis on 2010-03-01
> **3L33T said:**
> There is a way to enable USB in VirtualBox. [HERE's the link on how to do it.]("http://eyereex.eryell.com/?p=132")

Thank you so much for this!:D

---

### Post by blueshiftoverwatch on 2010-03-01
> **jespdj said:**
> if you have a dual-core or multi-core processor, then VirtualBox virtual machines will only use one core; VirtualBox doesn't support multi-core processors for the virtual machines. VMWare does.
This post was made back in 2008. But I have Virtualbox installed currently and under the settings for each individual virtual machine you can choose the max number of CPU's (which, I assume equates to cores) each virtual machine can use. So, I'm guessing that this is no longer the case.

---

### Post by 3L33T on 2010-12-09
> **ujhony03 said:**
> Is just like vmware? 
Whats the difference between the two? Are there any perfomance differences between either method?

Also, are you able to install virtualbox with the regular apt-get method?


Sorry if these are stupid questions, i just switched over to linux like a week ago.

[CLICK HERE for the best answers...]("http://www.google.com")

---

