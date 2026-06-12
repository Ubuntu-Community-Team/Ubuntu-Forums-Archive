---
title: "Anyone Recommend Virtualization Software?"
date: 2009-02-16
forum: Virtualisation
---

### Post by beastrace91 on 2009-02-16
So I had been using Virtual Box up until recently when it basically stopped working on me... Since no one has any idea what might be wrong with it I am wondering if anyone here would mind point me in the direction of another semi-user friendly piece of Virtualization Software. I tried the latest VMWare but I was unsuccessful in getting it to work and all the tuts of various other ones look rather daunting so I wanted some user input before I just jump into one of them.

Thanks,
~Jeff

---

### Post by Lizzo on 2009-02-16
Which VMWare did you try? I use VMware Server 2.0 on Intrepid and have minimal issues. I can run an XP appliance 100% of the time and have little noticable tax on my system. Once it's up and going you can do all of your tasks from a web interface. You do however, have to install from source.

---

### Post by beastrace91 on 2009-02-16
I believe I installed 1.0.8, link to 2.0? Also what is the command I would want to run to purge all the 1.0.8 files?

Thanks,
~Jeff

---

### Post by nlz on 2009-02-16
virtualbox is ultra stable with me.. Running it on 3 machines with 12 boxes in total.

---

### Post by beastrace91 on 2009-02-16
> **nlz said:**
> virtualbox is ultra stable with me.. Running it on 3 machines with 12 boxes in total.

I already said I had VB working and it was nice [quote=Jeff]up until recently when it basically stopped working on me[/quote] if you want to help me get it to work again here are the threads I have started in different places asking for help that have been dead ends:

[http://ubuntuforums.org/showthread.php?t=1062393](http://ubuntuforums.org/showthread.php?t=1062393)
[http://ubuntuforums.org/showthread.php?t=1070851](http://ubuntuforums.org/showthread.php?t=1070851)
[http://forums.virtualbox.org/viewtopic.php?t=14198](http://forums.virtualbox.org/viewtopic.php?t=14198)

But thank you for wasting space posting something that was meaningless to the topic at hand.

~Jeff

---

### Post by Lizzo on 2009-02-16
If you decide to take the 2.0 route...

[http://www.vmware.com/go/getserver](http://www.vmware.com/go/getserver)

You have to sign up for a free serial number but then there's download link for linux. For purging 1.0.8 see if you have a /usr/bin/vmware-unistall.pl file. Sudo run that and it should take it all out.

---

### Post by the_unforgiven on 2009-02-16
> **Lizzo said:**
> If you decide to take the 2.0 route...

[http://www.vmware.com/go/getserver](http://www.vmware.com/go/getserver)

You have to sign up for a free serial number but then there's download link for linux. For purging 1.0.8 see if you have a /usr/bin/vmware-unistall.pl file. Sudo run that and it should take it all out.
If you can avoid 2.0, please do.
It's pathetic in terms of usability and resource usage.

---

### Post by nlz on 2009-02-17
> **beastrace91 said:**
> 
But thank you for wasting space posting something that was meaningless to the topic at hand.

~Jeff

I think virtualization is not your biggest problem. But heh, you could try rebuilding the virtualbox kernel:
```
sudo /etc/init.d/vboxdrv setup
```

Did you try to create a new machine? If that works, then there is probably something wrong with the *.vdi file, if not, it's something with virtualbox itself.

---

### Post by binbash on 2009-02-17
Virtualbox is not stable for me for 2-3 builds.I prefer Vmware workstation over virtualbox because of this.

---

### Post by beastrace91 on 2009-02-17
I've tried rebuilding the VB kernel, I've tried 4 different Nvidia drivers, I've tried different version of VB... none of it works, they all yield black screens on load.

~Jeff

---

### Post by beastrace91 on 2009-02-17
Downloading VMWare server 2 now going to give it a try. Does it support USB devices on the VMs?

~Jeff

---

### Post by ubersolid on 2009-02-17
VMWare Workstation is good, on a Vista host. Haven't tried it on an linux / ubuntu one yet. What I can tell you is that VirtualBox is far better and faster than VMWare Server 2. On my box, VirtualBox can run windows server 2003 + xp pro simultaniously, VMWare Server cannot. It's not even close.
And my box is an AMD Athlon XP 2600+ with 1.75 Gb of RAM.
VMWare is not exactly userfriendly either, the 1.X releases were much better.

---

### Post by beastrace91 on 2009-02-17
Can we please stop throwing salt into my wound by telling me how much you all love Virtual Box? Virtual Box is great and I was plenty happy with it up until it flat out STOPPED WORKING. I'm not sure how many times I have to say this... I've tried everything short of reformatting (which I am not about to do I finally have everything else I need fully working on Ubuntu) to try to make it work with no luck. If you have an idea that might help please go post it in one of my above indicated threads...

Will post back about whether I was able to get VMWare working within the next day or so.

~Jeff

---

