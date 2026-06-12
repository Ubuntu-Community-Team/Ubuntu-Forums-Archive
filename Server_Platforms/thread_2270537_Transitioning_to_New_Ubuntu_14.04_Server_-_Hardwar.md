---
title: "Transitioning to New Ubuntu 14.04 Server - Hardware Help Needed"
date: 2015-03-23
forum: Server Platforms
---

### Post by Marc-NJ on 2015-03-23
I previously was running an Ubuntu 12.04 server with a single 2 TB hard drive in a somewhat-older small form-factor (SFF) PC for a while now. Unfortunately, the HD started experiencing corruption recently, and so instead of just replacing it, I've decided it makes sense to come up with a better solution (when I first built this machine, it wasn't being used for anything that important, but now that time's gone by I'm using it for some semi-critical things).  You can read more about this (and also some questions I had that haven't been answered yet as of this posting here: [http://askubuntu.com/questions/598896/crashed-ubuntu-12-04-server-need-help-recovering-transitioning-to-new-serve](http://askubuntu.com/questions/598896/crashed-ubuntu-12-04-server-need-help-recovering-transitioning-to-new-serve)).

At this point, I'm wavering between a few options:

1) I was going to try and use an older top-of-the-line HP desktop as the new Ubuntu 14.04 server with 2 x 4 TB drives in a RAID1 array.  I was able to "mod" the BIOS of this machine so that the fakeRAID controller (Intel RST) could recognize the 4 TB drives, but now am having issues figuring out how to install Ubuntu Server 14.04 to the machine using fakeRAID (vs. mdadm).

2) Possibly just setting up Win8.1 (or even WinServer) on the HP desktop mentioned above and then setting up Ubuntu Server 14.04 in a virtual machine (maybe VirtualBox?).  My concern is that I'm using Ubuntu Server for a lot of things, including to store lots of data (it will ultimately be between 1 - 3 TB probably), and am wondering if doing things in this manner is going to cause stability issues, other issues, or I'll take a performance hit when accessing the virtualized Ubuntu Server.

3) Using an older Optiplex 360 to install Ubuntu Server 14.04 with the 2 x 4 TB drives and mdadm / software RAID.  I actually just tried this, but there were a few issues that I might have to work out (including a few weird errors now that it's set up and whether or not I did the partitioning correctly for GPT, etc.).  Also, the max memory for this machine is 4 GB which is somewhat low I think (would prefer 8 GB - especially so that I can then run a virtualized Win7 install on top of the Ubuntu Server at times).

4) Buying a somewhat newer machine (circal 2011-2012) - either server or business desktop - and then using that to set up the Ubuntu Server 14.04.  I've been looking on Craigslist and eBay, but would prefer to not spend a fortune (or even anything if any of the above works), although if I do I want to make sure I get the right machine for me (something that supports the 2 x 4 TB drives, possibly with some sort of fakeRAID or hardware RAID, with 8 GB of RAM or more, newer processor, etc.).


As far as concrete technical questions:


*This first one is probably the most important, since if I can figure this out I'll probably move forward with it:*
1) I have been completely unsuccessful in finding any sort of guide or tutorial on how to set up Ubuntu Server (14.04 or even 12.04 since I imagine it's not that much different) on a fakeRAID system using RAID 1 with 4 TB drives (since larger than 2 TB drives requires a different approach I believe) and not dual booting or anything else.  Ubuntu's help documentation is for much older versions of their OS, and on top of that when I tried it initally, I ran into these questions and I had no idea how to proceed:
- One or more drives containing MDADM containers (Intel/DDF RAID) have been found.  Do you wish to acivate these RAID devices?
- One or more drives containing Serial ATA RAID configurations have been found. Do you wish to activate these RAID devices?
I also know that there are issues with getting the GRUB boot loader to work (I think, although I never got that far).

Can anyone point me to a guide or tutorial that might be appropriate given the above information?

2) Can anyone advise if running Ubuntu Server 14.04 in a virtualized (possibly VirtualBox, although am open to other suggestions) environment on top of Win8.1 or WinServer would cause issues (performance hits, other issues, etc.) - or would this work given what I'm trying to accomplish?

3) Can anyone advise whether I should be looking for a used business workstation to host my Ubuntu Server 14.04 vs. a low-end used business server if I decide to go out and purchase something?  And specifically what the advantages and disadvantages might be?


Sorry for such a long post - and thanks to all who took the time to read and can help out or offer some advice.  All help is welcome!

---

### Post by nerdtron on 2015-03-24
I hope I can shed some light on you concerns.


> 1) I was going to try and use an older top-of-the-line HP desktop as the  new Ubuntu 14.04 server with 2 x 4 TB drives in a RAID1 array.  I was  able to "mod" the BIOS of this machine so that the fakeRAID controller  (Intel RST) could recognize the 4 TB drives, but now am having issues  figuring out how to install Ubuntu Server 14.04 to the machine using  fakeRAID (vs. mdadm).

We used Intel FakeRaid before (RAID5), it worked until I needed to replace a hard drive which it happily said it can't rebuild. At least the server is still running so just migrated everything and re-initiliazed software raid. Never gonna use it again. Software RAID in Linux is quite good but I don't like the hassle of it. I recommend using a Hardware RAID controller.

> 2) Possibly just setting up Win8.1 (or even WinServer) on the HP desktop  mentioned above and then setting up Ubuntu Server 14.04 in a virtual  machine (maybe VirtualBox?).  My concern is that I'm using Ubuntu Server  for a lot of things, including to store lots of data (it will  ultimately be between 1 - 3 TB probably), and am wondering if doing  things in this manner is going to cause stability issues, other issues,  or I'll take a performance hit when accessing the virtualized Ubuntu  Server.
Definitely slower read/writes on virtualbox. Why do you want to do this? Is there a reason not to use a dedicated Server and install Ubuntu on it?

> 3) Using an older Optiplex 360 to install Ubuntu Server 14.04 with the 2  x 4 TB drives and mdadm / software RAID.  I actually just tried this,  but there were a few issues that I might have to work out (including a  few weird errors now that it's set up and whether or not I did the  partitioning correctly for GPT, etc.).  Also, the max memory for this  machine is 4 GB which is somewhat low I think (would prefer 8 GB -  especially so that I can then run a virtualized Win7 install on top of  the Ubuntu Server at times).
Old machine, time to retire.

> 4) Buying a somewhat newer machine (circal 2011-2012) - either server or  business desktop - and then using that to set up the Ubuntu Server  14.04.  I've been looking on Craigslist and eBay, but would prefer to  not spend a fortune (or even anything if any of the above works),  although if I do I want to make sure I get the right machine for me  (something that supports the 2 x 4 TB drives, possibly with some sort of  fakeRAID or hardware RAID, with 8 GB of RAM or more, newer processor,  etc.).
Buying used servers are cost effective (if you're on a budget). Just make sure your hard drives are NEW.

> 1) I have been completely unsuccessful in finding any sort of guide or  tutorial on how to set up Ubuntu Server (14.04 or even 12.04 since I  imagine it's not that much different) on a fakeRAID system using RAID 1  with 4 TB drives (since larger than 2 TB drives requires a different  approach I believe) and not dual booting or anything else.  Ubuntu's  help documentation is for much older versions of their OS, and on top of  that when I tried it initally, I ran into these questions and I had no  idea how to proceed:
- One or more drives containing MDADM containers (Intel/DDF RAID) have been found.  Do you wish to acivate these RAID devices?
- One or more drives containing Serial ATA RAID configurations have been found. Do you wish to activate these RAID devices?
I also know that there are issues with getting the GRUB boot loader to work (I think, although I never got that far).
As I said, I don't recommend Fake Raid because Software Raid in Ubuntu is better. But a Hardware RAID Controller is my best option here. 
For tutorials on Software RAID, it's not hard to find, maybe you search the wrong keyword. Here's a sample youtube link RAID1: [https://www.youtube.com/watch?v=z84oBqOxsD0](https://www.youtube.com/watch?v=z84oBqOxsD0)

> 2) Can anyone advise if running Ubuntu Server 14.04 in a virtualized  (possibly VirtualBox, although am open to other suggestions) environment  on top of Win8.1 or WinServer would cause issues (performance hits,  other issues, etc.) - or would this work given what I'm trying to  accomplish?
Yes you can run Ubuntu Server on Virtual Box in Windows 8, but why do you want this? Slower read/writes on Virtualbox. What do you need windows 8 for? You can also virtualize windows on Ubuntu if you need window 8 for some simple windows programs.

> 
3) Can anyone advise whether I should be looking for a used business  workstation to host my Ubuntu Server 14.04 vs. a low-end used business  server if I decide to go out and purchase something?  And specifically  what the advantages and disadvantages might be?
I'd go for a business server. You can find servers with dual power supply, hot-swappable drives and hardware RAID controller. If your server is mission critical, it's important to have these.

---

### Post by Marc-NJ on 2015-03-25
Wow, thanks for the awesome reply - greatly appreciated.  I've been wavering back and forth now for a while between a business desktop that I convert into an Ubuntu server with software RAID and a true server with hardware RAID, but found the Lenovo ThinkServer TS440's priced very inexpensively online (~$500, possibly even less), and think I'm going to take the plunge with them and true hardware RAID (plus other benefits that I get with a true server).  What do you think of the ThinkServer TS440's - any thoughts?

Also, what would you recommend I use for virtualizing Win7/8/8.1 on top of Ubuntu Server?  I was previously using VirtualBox running on the Ubuntu Server to run Win VM's, but maybe there are better solutions?  And I'm guessing I should go at least 8 GB of RAM, and maybe even 16?

Thanks!

P.S. If you have any knowledge of how I can "recover" the data in my current crashed server's lost+found directory so that I can get it all sorted before moving it over to this new machine (so I ensure I don't have any data loss presumably), that'd be great also!  Sorry to ask so much, and feel free to ignore this last part of my question since it's pretty much off-topic.  Thanks again.

---

### Post by MAFoElffen on 2015-03-25
I've been running Win Server 2012 and Win 8.1 virtuals in KVM on two of my Ubuntu 14.04.2 Servers. Have had them up to do my MOAC cert classes. One of them is 8GB and the other of mine is 48GB. 8 GB should be fine, depending on how many you have actively consuming resources at the same time. I try not to over-allocate them... then reallocate RAM in each as needed. I played with using dynamic memory allocation, but static RAM allocation was more efficient for me. I connect to all of them through Virt-Manager, from one of my remote consoles.

---

### Post by nerdtron on 2015-03-25
> What do you think of the ThinkServer TS440's - any thoughts?
No experience on that part. So no thoughts

> Also, what would you recommend I use for virtualizing Win7/8/8.1 on top  of Ubuntu Server?  I was previously using VirtualBox running on the  Ubuntu Server to run Win VM's, but maybe there are better solutions?   And I'm guessing I should go at least 8 GB of RAM, and maybe even 16?
Best way we do it is KVM. Your server has no GUI so it's difficult to manage the virtual. Then you have your own desktop machine, from this, you install the virt-manager which is a GUI front-end to control your VMs on the server. An I think 16 GB should be the minimum here.
More here: [http://www.howtogeek.com/117635/how-to-install-kvm-and-create-virtual-machines-on-ubuntu/](http://www.howtogeek.com/117635/how-to-install-kvm-and-create-virtual-machines-on-ubuntu/) and here: [http://www.havetheknowhow.com/Configure-the-server/Configure-KVM.html](http://www.havetheknowhow.com/Configure-the-server/Configure-KVM.html)

> P.S. If you have any knowledge of how I can "recover" the data in my  current crashed server's lost+found directory so that I can get it all  sorted before moving it over to this new machine (so I ensure I don't  have any data loss presumably), that'd be great also!
That's what backups are for. Files/folders on the lost+found directory are more likely corrupt so you can't just restore them. I haven't used any recovery programs since we have good backup.
Backups saves lives and saves business :cool:

---

### Post by MAFoElffen on 2015-03-25
+1 on lost+found. 

Most of those files in that directory are file fragments that were put there during a fsck... Sometimes some will happen and will be something more:
[http://karuppuswamy.com/wordpress/2010/06/09/how-to-recover-files-from-lostfound-after-fsck-in-linux-how-i-did-it-in-ubuntu/comment-page-1/](http://karuppuswamy.com/wordpress/2010/06/09/how-to-recover-files-from-lostfound-after-fsck-in-linux-how-i-did-it-in-ubuntu/comment-page-1/)

... but that is rare.

A good recovery plan with backups. Otherwise, those file fragments... even it good files or filenames, or directory names... I look at those with a disk editor, so is usually beyond a normal user's paygrade.. I refrain from recommending working on those without "knowing" who I'm talking with.

My firend just bought a T440 and he likes that model... But he has his for home use and it fits his needs. From what I hear... all others seems to be okay... except for the T340. That one works fine for RHEL and Centos, but has had issues with Debian branches.

---

