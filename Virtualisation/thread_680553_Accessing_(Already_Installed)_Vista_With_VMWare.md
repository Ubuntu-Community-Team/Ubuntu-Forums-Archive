---
title: "Accessing (Already Installed) Vista With VMWare"
date: 2008-01-28
forum: Virtualisation
---

### Post by MikeonTV on 2008-01-28
Hey all. I duel boot Ubuntu (FF) and Vista Home Basic (32) and have gotten used to Ubuntu as the primary OS. My GF however is confused and frustrated when having to us Linux and thus reboots back in to Windows.

Since we are both often using this machine back and forth I'm trying to find a way to keep Vista open in something like VMWare and thus be able to easily work in Linux - In theory having Vista run in a window in Ubuntu.

I know this has been done many times before ( [http://www.flickr.com/photo_zoom.gne?id=483787173&size=o](http://www.flickr.com/photo_zoom.gne?id=483787173&size=o) ) but my issue is finding a tut that allows me to open an already installed vista partition in Linux. I can't fathom installing vista again. Any advice for this amateur but loyal Linux user?

---

### Post by spupy on 2008-01-28
You got two options:
1. Use [VMWare Converter]("http://www.vmware.com/products/converter/"). It's a program that you run on windows and it converts the installed OS to a VMWare image, that you can load in Virtual Machine that you are running in Ubuntu. _This is what i recommend_.
2. User [this guide]("http://oopsilon.com/Running-a-Windows-Partition-in-VMware"). It is for Windows XP, but i think it could be easily adapted for Vista. The guide shows you how to create a virtual machine file, that, when run in the VMWare software, runs the Windows installation off your harddisk. I was using this myself, and i was pretty satisfied. **HOWEVER**: when you switch and run the same windows installation directly and in the virtual machine, windows finds out that the hardware has changed, and asks you to activate this windows copy. Unfortunately, windows has limited activations, after that it becomes unusable. Also, other problems might arise from the hardware  differences, but this haven't happend to me.

After all, the first method is more secure and more easy. But then you will actually have two different Vistas - one on your harddisc and the other one in the virtual machine. Then you might need some extra software to sync user preferences, favorites and whatnot between the two, so your girlfriend be happy! ;)

If you have any questions., don't hesitate to ask!

---

### Post by MikeonTV on 2008-01-28
If I run the first option would everything new that we do in vista only be added the new vista image or does it retroactive with both images?

Would downloading a 1 gb video file mean that two gb are now used? Thanks for the swift reply

---

### Post by spupy on 2008-01-28
In the first option, after the conversion, you got two vista installs - on disk and in the virtual machine - and they are no more connected in any way! That is the problem with this variant. And, if your vista is, lets say 6GB, you will need another 6+ GB for the VMWare image.
For the second option you should be OK if you find some way to stop windows asking for activation. But this is not very legal.

Option 1:
+ easy to do, no software problems later
- very uncomfortable (having two vistas); huge disk space usage.

Option 2:
- not so easy to set up, may have problems with software, may include illegal practices.
+ immensely more comfortable (no need to install stuff twice, etc.)!

---

### Post by MikeonTV on 2008-01-28
So If I can overcome the legal moralities (done) the only other problem with option number 2 is that it might trigger some activation defense system. But I am for sure this OS on this machine has only activated once. When I purchased it. 

Thanks

---

### Post by spupy on 2008-01-29
Well, my windows was also activated once when i purchased it. See, when you use the installed windows in the VM, it finds that the hardware has changed, and since you could have just copied windows and transplanted it on another computer (in our case the VM), it has to be activated to avoid using one license for multiple machines. So you can activate only about 20 (?) times, after which your serial key is invalidated.
But you know, i now remembered, there were some stories ago i think, and vista might not need activation. I will check this out when i have more time.

---

### Post by MikeonTV on 2008-01-29
Thanks for the reply. This machine came installed with vista and I forget if I used a Key. Also I am living overseas now and don't have any documentation with me so it might be wise to wait until I get home before I go this route. I would love to know your findings (when you have time of course) Thanks again.

---

### Post by spupy on 2008-01-30
You should have a key with your computer. Anyway, i searched a little, and [here]("http://lifehacker.com/software/vista/extend-vistas-activation-period-indefinitely-248217.php")  for example, but it seems the methods don't provide infinite ..uhm.. un-activation (lol). And one of the results in google is this thread...
See if you can find anything else about the actiovation - keywords in google like:
vista activation vmware running


EDIT: Oh, thanks, but there is no need to thank me after each reply! ;)

---

### Post by jack frost on 2008-07-22
:)I know this is an old thread but I have 2 machines with vista  32 bit and was going to go back to ubuntu 8.04 on one machine and just wipe the drive and install the vista 32 bit vm image inside ubuntu..step1 on this thread.  I already activated etc.. my question is that I have games like halo2, gears of war pc.. etc.. will those games be playable in the vm on ubuntu?
 
I know I can dual boot..but just wanted to know if the vm can play the games before I wipe my drive.. thanks.

---

### Post by MikeonTV on 2008-07-22
I abandoned this idea and now dual boot. I have been slowly weeding out windows on said machine. I don't game and figured that it wont be too long until I completely close the door on Vista. 

Now to answer your question, while playing games in Ubuntu using VMW is possible I do think that it would be a huge strain on resources. I would jump back and forth to play games. But thats why you have two machines right?

---

