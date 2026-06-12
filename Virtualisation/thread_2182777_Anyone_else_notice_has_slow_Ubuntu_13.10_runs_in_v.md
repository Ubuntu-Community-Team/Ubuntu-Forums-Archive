---
title: "Anyone else notice has slow Ubuntu 13.10 runs in virtualbox?"
date: 2013-10-22
forum: Virtualisation
---

### Post by linuxguru43 on 2013-10-22
Is there some setting I am using wrong in Virtualbox when installing Ubuntu 13.10? This is taking forever. It is as slow as molasses... I used to be able to keep the default settings just the way they are in virtualbox after installing it, and then using any Ubuntu installation cd image file. It would bootup live, and installation would take about 20 minutes tops. What happened?? Why does Ubuntu 13.10 need the guest additions to run at normal speed??? Is there a download just for virtualbox installations of Ubuntu 13.10? What am I doing wrong here because it shouldn't take this long to install anything in virtualbox.

---

### Post by pqwoerituytrueiwoq on 2013-10-22
13.10 is released this place is for 14.04 LTS now
it is probably cause of compiz needing GPU acceleration

---

### Post by linuxguru43 on 2013-10-22
Sorry, well then they need to disable compiz by default for Virtualbox users. Isn't it more counter-intuitive to assume everyone wants special effects like compiz? They need to change it back to non-compiz effects for virtual installations. I don't have time to use Ubuntu if it takes 50 minutes to install it in virtualbox because virtualbox can't handle the over-used compiz window dressing effects. Who has time for that? (sorry about posting in the wrong forum but 13.10 sure feels buggy and I thought it was for trying to figure out problems like this)

AT LEAST give the users an option when booting if they want window dressing effects like compiz or not. I don't need window dressing for a virtualbox install. I just need it to install and run.

---

### Post by howefield on 2013-10-22
Thread moved to the "*Virtualisation*" forum.

---

### Post by howefield on 2013-10-22
> **linuxguru43 said:**
> I don't have time to use Ubuntu if it takes 50 minutes to install it in virtualbox because virtualbox can't handle the over-used compiz window dressing effects. Who has time for that?.

You prompted me to install a 13.10 virtualbox which took 16 minutes and 32 second to install from booting the iso to rebooting to the hard disk, including downloading updates and third party codecs. This machine is about 4 years old so is far from being that good.

Is your hardware up to it ?

---

### Post by TheFu on 2013-10-23
> **howefield said:**
> You prompted me to install a 13.10 virtualbox which took 16 minutes and 32 second to install from booting the iso to rebooting to the hard disk, including downloading updates and third party codecs. This machine is about 4 years old so is far from being that good.

Is your hardware up to it ?

Ubuntu being slow AFTER the first reboot inside a VM has been an issue since they started with all the Unity stuff as default - GPU accel. After a slow install last year, I wrote up a how-to to make Ubuntu not be slow under VirtualBox here: [http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox)

I've also had an install take almost 2 hours because it was on a network, but not connected to the internet. Every remote request had to timeout ... taught me to disconnect the cable during installs - much easier and less than 20min.

Anyway, I hope it helps someone.  It isn't just for vbox users - KVM, VMware, Xen users can learn from the overall ideas and a few of the settings too.

---

### Post by linuxguru43 on 2013-10-23
Okay, tell me how to make it run faster please? I used to be able to install Ubuntu in less than 10 minutes in Virtuabox before you required everybody to have window dressing effects enabled by default... How do I disable these dumb window dressing effects that slow down the process of installation, and these special fx I do not need before booting this Ubuntu 13.10 iso? IMHO - If users want that glitz and glamor they should install it separately. I'm really seriously considering using pure debian instead if you are blaming my hardware, because I didn't have this problem before with Ubuntu OS & virtualbox... This is very unhelpful.

---

### Post by TheFu on 2013-10-24
Did you read and follow the settings in that link I provided above?

---

### Post by linuxguru43 on 2013-10-24
Yes, thank you for your kind suggestions. They didn't help with the non-functionality or the sluggishness. How do I disable compiz before the system loads at bootup? I don't want any effects during bootup in virtualbox or vmware. I just want the OS and that is it. There should obviously be some setting I can use at bootup to disable all of these window dressings and special effects I don't need in virtualbox or VMware. I can't use Ubuntu 13.10 Unity when it runs this slowly in Virtualbox. No way. Try it yourself if you don't believe me. It is soooooooooooooo slow. Even after I installed the guest additions for virtualbox and Ubuntu 13.10 it still runs pretty lousy. I'm sitting here for like 15 minute pauses and glitches. I was going to do some development and testing for a new product, but I can't recommend Ubuntu 13.10 in visualization when it runs this crappy. Should I just use the latest Fedora F19 which doesn't have any of these issues? Please advise.

Howie - please don't blame my hardware. This is virtualbox on a semi new desktop computer. I don't have any of these problems with Ubuntu 12.04.02 ISO or Fedora 19. I either need a solution or a confirmation that this problem exists or not.

---

### Post by TheFu on 2013-10-25
Uh ... did you disable 3d-Accel in the video section of the guide? Compiz can't run with that disabled.

To me this is NOT an Ubuntu issue. It is a VirtualBox issue. vbox needs to recognize the OS and tweak their settings appropriately. They've done this numerous times since the beginning.  VMware-player/workstation has been doing tweaks based on the OS since the beginning. I remember the days when VMware-Workstation wouldn't even allow us to try an OS they didn't _know_ in their DB.

As a dev, I'd rather you didn't run anything other than LTS releases. Building for "newest" releases is anti-business. Forcing a business to run unstable releases with a focus on things other-than-stability is unhelpful, IMHO.  Software is seldom backwards compatible, but old software CAN run fine on newer platforms.  I have code compiled on very old Linux releases that runs fine on 12.04 ... 6 yrs later. That is my advice.

While you aren't the only person with this issue, others get passed it by tweaking their vbox VM settings.  Sure, it would be nice if Canonical recognized that Ubuntu was running inside a virtual environment and altered the settings dynamically. Perhaps a feature request for that?  OTOH, virtualization of a desktop OS is probably NOT what Canonical wants. It means they run as a 2nd class OS.

F19 has lots of issues too ... like the installer, which sucks in many ways. Whatever. We all have opinions and nothing is perfect.

BTW, Ubuntu 12.04.3 is the release most people should be on.  Run **apt-get dist-upgrade** to get it.

I cannot test on virtualbox anymore. We switched to KVM on Ubuntu for all our virtualization needs and removed the last virtualbox install last May. Sorry.  I was fairly confident that link would provide settings to make things fast. I know it has for all prior Ubuntu releases and the constant visitors to that page this month (it is the 2nd most popular link on my blog) got me thinking it still works and that the vbox defaults still suck.

Sorry it didn't help you. Were any parts of the article confusing?

---

### Post by linuxguru43 on 2013-10-25
2nd class OS? I wanted to deploy this OS for development, how is that 2nd class? Are we now stuck with cloud or server images only? I haven't tried the work-around yet to get this latest release of Ubuntu to squeeze into my virtualbox or vmware yet. FYI - It -never- had a problem with virtualbox before though, and I find that disturbing. How are we supposed to test each new frequent 9 month release of Ubuntu OS if it won't run virtually? I don't have a extra computer tower laying around to completely dedicate to this inflexible mess. So to test the latest version of Ubuntu OS we can't expect visualization support in the latest releases anymore? Again, I don't need all these FX during my live installation of Ubuntu. Why would you bother having FX during the live sessions anyhow? That seems illogical, and really impractical esp. if you are just trying to install it on your system. I don't have an extra computer to dedicate to testing the latest version of Ubuntu each rollout. I have VMware and virtualbox, and that is all I am going to use. If Ubuntu OS will not run properly virtualized then just give up, delete the support group, and call it a day. I'm going to be stuck using cloud/server installations of the latest versions of Ubuntu each release. You don't think that is a problem? I think you could make it much more easier by letting users decide for themselves if they want all this FX bloat at the bootup phase. BTW my old Ubuntu 12.04.02 ISO is the only one that still boots successfully (without fail or hesitation).  Ubuntu 12.02.03 has the same problem booting in virtualbox as U13.10. This is crazy. I haven't had to use this many hacks to get a OS to install virtualized since I tried to run OS X mountain lion in Vmware. Ridiculous. Thank you for at least admitting one thing and that this, the latest releases of ubuntu are NOT really supposed to be used on production systems for businesses, that is news to me.

---

### Post by TheFu on 2013-10-25
Where do I start?

Did you try the fixes for virtualbox in the article?  Am I misunderstanding? Please clarify.  The comment above seems to say you haven't.

BTW, I installed Ubuntu 13.10 desktop into a KVM VM on a 12.04.3 server this morning and I timed it.
Install started at : 08:43:54 
Install ended at   : 08:58:07  

Seems fast to me.

---

### Post by linuxguru43 on 2013-10-27
Thanks, if I was running KVM VM, I totally believe you that everything would be just perfectly fine, with Ubuntu 13.10 and KVM. I'm not running KVM. I'm running virtualbox and VMwaresphere. I tried to be as specific as I could, and hey I even put it in the title of my OP. I'm sorry, I'm really not trying to seem like a d*ck but I really do need answers here about is wrong with U13.10 and virtualbox. I don't really care about how awesome KVM works with Ubuntu 13.10, and maybe someday I will use that instead if I can't get Ubuntu 13.10 to work with virtualbox or vmware. Why doesn't anyone here care about these issues I have found? Why are you trying to get me to use some other virtualization software instead? This isn't the way we normally troubleshoot problems on linux. I'm curious, what happened to trying to improve linux issues like these? Why can't I turn the FX off at bootup on Ubuntu 13.10? I didn't have this problem with Ubuntu 12.03.02. Now we do. Does someone know of a better OS that might be more helpful to my needs? I'm beginning to think Ubuntu is just for netbooks or whatever. 
  
PS How are we going to solve problems like this when you are using some completely different virtualization software? wow

---

### Post by TheFu on 2013-10-27
> **linuxguru43 said:**
> Thanks, if I was running KVM VM, I totally believe you that everything would be just perfectly fine, with Ubuntu 13.10 and KVM. I'm not running KVM. I'm running virtualbox and VMwaresphere. I tried to be as specific as I could, and hey I even put it in the title of my OP. I'm sorry, I'm really not trying to seem like a d*ck but I really do need answers here about is wrong with U13.10 and virtualbox. I don't really care about how awesome KVM works with Ubuntu 13.10, and maybe someday I will use that instead if I can't get Ubuntu 13.10 to work with virtualbox or vmware. Why doesn't anyone here care about these issues I have found? Why are you trying to get me to use some other virtualization software instead? This isn't the way we normally troubleshoot problems on linux. I'm curious, what happened to trying to improve linux issues like these? Why can't I turn the FX off at bootup on Ubuntu 13.10? I didn't have this problem with Ubuntu 12.03.02. Now we do. Does someone know of a better OS that might be more helpful to my needs? I'm beginning to think Ubuntu is just for netbooks or whatever. 
  
PS How are we going to solve problems like this when you are using some completely different virtualization software? wow

Sorry for trying to help. We do care and have offered vbox specific ideas, which appear to have been ignored. 
Sorry I couldn't help. No response is better than mine, I guess.

---

### Post by linuxguru43 on 2013-10-27
They haven't been ignored. I'm using virtualbox. That is what everyone ignored. I guess this OS is just for netbooks and competing with Apple products. I'm going back to slackware. Bye. Close thread.

---

### Post by novo2809 on 2013-12-10
from [http://namhuy.net/951/how-to-fix-slow-performance-ubuntu-13-04-running-in-virtualbox.html](http://namhuy.net/951/how-to-fix-slow-performance-ubuntu-13-04-running-in-virtualbox.html)
it will help your virtualbox run faster
To enable 3D supported, fist you will need to update linux-headers
 ```
uname -r
 sudo apt-get install linux-headers-$(uname -r)
 sudo apt-get autoremove
 sudo apt-get install build-essential


```

Now insert vitualbox guest iso from devices and to install manually
 ```
cd /media
 ls
 cd username
 ls
 cd VBOX*
 ls
 sudo ./VBoxLinuxAdditions.run

```


Insert vboxvideo to /etc/modules
 ```
sudo nano /etc/modules
```


Add “vboxvideo” at the end of the file
 ```
loop
 lp
 vboxvideo

```


Reboot the machine
 ```
sudo reboot
```

---

