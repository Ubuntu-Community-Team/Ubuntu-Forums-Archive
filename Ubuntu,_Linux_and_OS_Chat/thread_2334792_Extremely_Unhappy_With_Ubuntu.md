---
title: "Extremely Unhappy With Ubuntu"
date: 2016-08-22
forum: Ubuntu, Linux and OS Chat
---

### Post by jhansensd on 2016-08-22
Hello, I have just installed Ubuntu again to do web development and everything has been working great for some time. The computer froze on the weekend in Chrome and I had to hold down the power button. Upon restarting it wouldn't boot as there were hard disk errors. I managed to get in and run an fdisk to fix the errors. However, when I rebooted the system wouldn't start because systemd had many failures, and the login service failed.

I searched all over the internet and couldn't find any basic help on how to repair broken services on start. I also was unable to find utilities to help the situation. Surprisingly, I even read I should be able to reinstall Ubuntu and maintain all my local files and folders, but the Ubuntu install couldn't even find the existing Ubuntu installation and said "unknown linux distribution."

I even managed to install without reformatting the drive. But then when I started ubuntu the package manager wouldn't work and dpkg kept failing with depcon: error in linux package manager due to dependencies and linux generic or something like that. I tried everything that was supposed to fix it but I couldn't install any packages like vim. It always failed.

This was getting so frustrating I ended up reformatting the entire drive and now everything works fine.

How come a modern operating system like Ubuntu Desktop has so many problems that are unrecoverable and it seems unacceptable that there isn't more support than what is out there. To have Ubuntu become unrecoverable like this seems to be totally unacceptable. Isn't there a utility or repair tool (not for grub), but for other issues. In fact, grub is also a problem, I installed ubuntu on my external drive but now I am unable to boot without my external drive (even though grub is on main windows partition). I have tried grub repair and it doesn't work. Nothing works without plugging in my external hd. I feel like I am back in the 80's.

My machine is a 3 year old Dell Lenovo laptop with 16gigs of ram and a lot of hard drive space. Please let me know what is happening here, thanks!

---

### Post by leunam12 on 2016-08-22
Have you check your hard drive? Maybe it's failing.

---

### Post by javan-cardillo on 2016-08-22
my guess is you are running 16, for what ever reason 16 has done that with me also but only when i run chrome, i have givin up on 16 and am on 15.10 right now, im really really close to giving up on ubuntu all together, seems like 12 was the last good one they made.

---

### Post by QIII on 2016-08-22
Every new release of Ubuntu is "the worst release ever".

It seems that with one post it is unlikely you looked everywhere.  You missed here.

While it is certainly unfortunate that you have encountered problems, you can't assume your experience is the norm.  If you have a support request, please start a thread on the subjects. Individually.

---

### Post by yancek on 2016-08-22
fdisk doesn't fix filesystem errors it simply manages partitions and displays information on drives/partitions.  If you had hard disk or filesystem errors you would run fsck (file system check).  Not knowing exactly what you did, it's hard to guess what happened as there are many possibilities.  

Having a Live DVD or flash drive of the system you installed is a pretty good way to do repairs.  The SystemRescueCD has a large number of tools/programs to repair problems so you could try downloading that.

If Ubuntu had so many problems that were 'unrecoverable', I doubt there would be tens of millions of users worldwide.

If you want more support, you need to either pay for it the way you do with a Mac or windows or be patient and wait for 'volunteers' such as as this forum to respond.  

> I installed ubuntu on my external drive but now I am unable to boot  without my external drive (even though grub is on main windows  partition). I have tried grub repair and it doesn't work.


That's a common 'user' error.  You  accepted the default which is to install boot code to the MBR of the initial drive, that would be the first drive in the computer and NOT the external drive.  There is an option as to where to install "Device for bootloader installation" and you can select the MBR of any drive as well as any partition if you use the manual "Something Else" option.

---

### Post by poorguy on 2016-08-22
> **jhansensd said:**
> 
My machine is a 3 year old Dell Lenovo laptop with 16gigs of ram and a lot of hard drive space.

Which is it a Dell Laptop or a Lenovo Laptop? Never heard of a Dell Lenovo Laptop, however I could be wrong.

---

### Post by ian-weisser on 2016-08-22
> **jhansensd said:**
> How come a modern operating system like Ubuntu Desktop has so many problems that are unrecoverable and it seems unacceptable that there isn't more support than what is out there. To have Ubuntu become unrecoverable like this seems to be totally unacceptable. Isn't there a utility or repair tool (not for grub), but for other issues. In fact, grub is also a problem, I installed ubuntu on my external drive but now I am unable to boot without my external drive (even though grub is on main windows partition). I have tried grub repair and it doesn't work. Nothing works without plugging in my external hd. I feel like I am back in the 80's.

We do understand your frustration. We have all been frustrated like that.

We agree with you that an unrecoverable system is unacceptable, and welcome your help to get there.If you feel that you can reproduce those errors in a test environment,  please share the details on a bug report so a developer can fix them. Better yet, if you have the skills to diagnose and fix the problem yourself, please share it upstream.

We agree with you that improving the existing utility and repair tools is a great goal. Do feel free to pitch in.

We agree with you that documenation is fragmented and hard to find. The Ubuntu Documentation Team welcomes your contributions.

You are not a customer. Ubuntu is a community...not a company. Ubuntu improves when you participate.

---

### Post by buzzingrobot on 2016-08-23
> **jhansensd said:**
>  I managed to get in and run an fdisk to fix the errors. 

fdisk is not a repair tool. It is a partitioning tool.  If you used it to change something, you may very well have altered the partitioning scheme in a way that accounts for the errors you saw after rebooting.  Altering or deleting partitions could easily account for boot failure and/or systemd services and the login process failing.  Or, for that matter, failure of the kernel to boot in the first place

> the Ubuntu install couldn't even find the existing Ubuntu installation and said "unknown linux distribution." 

Again, very likely because of the damage done with fdisk. 


> How come a modern operating system like Ubuntu Desktop has so many problems that are unrecoverable...


Some kinds of damage are unrecoverable on any operating system.  

Your best bet for support with future Ubuntu problems is to post questions here when the problem first arises.  Avoid random Googling for help unless you are confident you have the experience and expertise to tell bad advice from good advice.

---

### Post by fromwin2lin on 2016-08-24
Maybe you were just unlucky, I am running 16.04.1 on my old Dell Inspiron n5050 and it works just fine. Maybe your hard drive is failing?

---

### Post by ventrical on 2016-08-24
> **jhansensd said:**
> 

My machine is a 3 year old Dell Lenovo laptop with 16gigs of ram and a lot of hard drive space. Please let me know what is happening here, thanks!

I think your unhappiness is misplaced. Assuming the above was a typo .. could you please give us the details of your PC.

Enter:

```

inxi -FXz

```

You have to install inxi first.

```

sudo apt-get install inxi

```

 then copy and paste the output here.

Regards..

---

### Post by wildmanne39 on 2016-08-25
For future reference this is a safe way to reboot  a frozen system without damaging the hard drive.
[http://blog.kember.net/articles/reisub-the-gentle-linux-restart/](http://blog.kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by Bucky Ball on 2016-08-25
> **javan-cardillo said:**
> i have givin up on 16 and am on 15.10 right now ...

Not a solution to your problem unfortunately as 15.10 is no longer supported and that means no updates since July, including security updates. This will become a security vulnerability if the machine is online.

---

