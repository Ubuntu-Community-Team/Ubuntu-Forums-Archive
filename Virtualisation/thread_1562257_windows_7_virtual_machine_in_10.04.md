---
title: "windows 7 virtual machine in 10.04"
date: 2010-08-27
forum: Virtualisation
---

### Post by wahoobob on 2010-08-27
Is there a relatively safe and easy way to place a windows 7 virtual machine in 10.04 booted from a windows 7 partition on a T42p thinkpad laptop?  (2 gb ram) There are 1 or two programs that I need from windows 7 and would like to avoid rebooting when I switch to them.  It would be useful to have the work update the files when I do boot into 7.  Is there a tutorial that a newbie could follow for this?  Any help would be appreciated.:)

---

### Post by spydeyrch on 2010-08-27
So if I understand you correctly, you currently have a thinkpad where you have win7 installed. You want to take that and convert it to a VM (virtual machine) that you could then run in VirtualBox so that you wouldn't have to reboot every time you would like to access your win7 programs?

Am I even close? If that is what you would like to do, yes there is a way to do so. But first verify if that is in fact what you are wanting to do, please. Thank you.

-Spydey:KS

EDIT: What are the programs that you need to run in win7? Have you thought about finding an alternative program that does the same thing but linux native? Or how about using Wine? Just some after thoughts.

Also, what system are you planning on running your VMs on? I am assumming that it is going to be your thinkpad laptop, am I right? What are it's specs?

---

### Post by nigamp on 2010-08-27
you want to run win7 inside 10.04......
hpe u ve installed ubuntu .. if not then u can simply install ubuntu "inside windows" which ll let u boot 4m the windows partition......
boot into ubuntu  n install virtualbox  by typing this command at the teminal
sudo apt-get install virtualbox

run virtualbox 
then install win7 on the VM .. n ya u can easily switch between both the OS so dat u acn wnjoy ur progs in win7



PS: u can use VMware instead of virtualbox..but VMware is nt free.

---

### Post by spydeyrch on 2010-08-27
After reading nigamp's post, I think that I may have misunderstood your original post. You have win7 installed on your think pad and you want to install ubuntu on your win7 partition. Then from with in ubuntu, you want to run a win 7 vm.

Nigamp's post gives you some basic instructions on how to do it.

You would be installing ubuntu into win7 via Wubi.

Once finished, you would then be installing VB (Virtual Box) inside ubuntu and then Win7 inside virtual box.

Pretty simple to do.

Just note that you original Win7 would see Ubuntu (Wubi) as just a normal program.

-Spydey :KS

---

### Post by wahoobob on 2010-08-27
> **spydeyrch said:**
> So if I understand you correctly, you currently have a thinkpad where you have win7 installed. You want to take that and convert it to a VM (virtual machine) that you could then run in VirtualBox so that you wouldn't have to reboot every time you would like to access your win7 programs?

Am I even close? If that is what you would like to do, yes there is a way to do so. But first verify if that is in fact what you are wanting to do, please. Thank you.

-Spydey:KS

EDIT: What are the programs that you need to run in win7? Have you thought about finding an alternative program that does the same thing but linux native? Or how about using Wine? Just some after thoughts.

Also, what system are you planning on running your VMs on? I am assumming that it is going to be your thinkpad laptop, am I right? What are it's specs?

As Ed would say to Johnny Carson, "you are correct sir".  I have a T42p that was running W7 as the main parition and put 10.04 on a scond partition.  Now I need to occasionally use the Family Tree program (yes, I know about GRAMPS - too much to port over and get fixed with pictures, etc.) and a program for my work to report activity to the Bosses (they don't know about Linux and I can't/won't invest my time to convert the company).  This is enought to keep 7 on the machine, and 7 is the best windows to date.  I would like to use the existing installed 7 partition while in 10.04.  Have not yet put any VM software on the machine.  The T42p has 2gb of memory, Celeron 1.7, 160gb hard drive, good machine for its age and runs all compiz, windows7 eye candy, etc.  Windows has 100 gb of HD using about 40 - and Linux has 60 using about 15.  Any other specs?  This re-booting is not a deal breaker, just a thing that would save some time.
Thanks for any help in advance.......

---

### Post by spydeyrch on 2010-08-27
> **wahoobob said:**
> As Ed would say to Johnny Carson, "you are correct sir".  I have a T42p that was running W7 as the main parition and put 10.04 on a scond partition.  Now I need to occasionally use the Family Tree program (yes, I know about GRAMPS - too much to port over and get fixed with pictures, etc.) and a program for my work to report activity to the Bosses (they don't know about Linux and I can't/won't invest my time to convert the company).  This is enought to keep 7 on the machine, and 7 is the best windows to date.  I would like to use the existing installed 7 partition while in 10.04.  Have not yet put any VM software on the machine.  The T42p has 2gb of memory, Celeron 1.7, 160gb hard drive, good machine for its age and runs all compiz, windows7 eye candy, etc.  Windows has 100 gb of HD using about 40 - and Linux has 60 using about 15.  Any other specs?  This re-booting is not a deal breaker, just a thing that would save some time.
Thanks for any help in advance.......


Ok, well, to tell you the truth, running a VM on those specs will be a little difficult. Not that it is impossible but because of your CPU, you don't have hardware support for virtual machines, which honestly makes a HUGE improvement.  But VB (virtual Box) has some pretty cool coding built into it where it can emulate the hardware support. But please be aware that you will take a significant performance hit due to lack of hardware support. How much, I can't really say with percentages or numbers, but you will notice it, that is for sure.

As far as converting your current win7 to a VM, it is possible but again, because of your hardware, you might need to invest in a large portion of patience (hehehehe). It will take your machine a while to convert your current win7 to a VM.

I don't mean to sound negative or trying to tell you not to do it, but I just want to make sure that you are aware of the performance penalties you will feel/see.

Do you still want to give it a try? :D

-Spydey :KS

EDIT: Did you do a full install of ubuntu in your dual boot setup or did you install ubuntu via wubi?

---

### Post by wahoobob on 2010-08-27
> **spydeyrch said:**
> Ok, well, to tell you the truth, running a VM on those specs will be a little difficult. Not that it is impossible but because of your CPU, you don't have hardware support for virtual machines, which honestly makes a HUGE improvement.  But VB (virtual Box) has some pretty cool coding built into it where it can emulate the hardware support. But please be aware that you will take a significant performance hit due to lack of hardware support. How much, I can't really say with percentages or numbers, but you will notice it, that is for sure.

As far as converting your current win7 to a VM, it is possible but again, because of your hardware, you might need to invest in a large portion of patience (hehehehe). It will take your machine a while to convert your current win7 to a VM.

I don't mean to sound negative or trying to tell you not to do it, but I just want to make sure that you are aware of the performance penalties you will feel/see.

Do you still want to give it a try? :D

-Spydey :KS

EDIT: Did you do a full install of ubuntu in your dual boot setup or did you install ubuntu via wubi?

Full Ubuntu in partition.  I have a feeling that 7 is too heavy an environment to run inside 10.04... It might work better the other way around and put Linux inside 7 since it runs on less overhead...  I could download the virtual box for Windows and install 10.04 inside that?  Maybe use a Damn small linux or puppy, etc?

---

### Post by spydeyrch on 2010-08-27
> **wahoobob said:**
> Full Ubuntu in partition.  I have a feeling that 7 is too heavy an environment to run inside 10.04... It might work better the other way around and put Linux inside 7 since it runs on less overhead...  I could download the virtual box for Windows and install 10.04 inside that?  Maybe use a Damn small linux or puppy, etc?

You could do that if you wanted to. You could install VB for Windows and then install Ubuntu as a VM in VB. But you will run into the same issue really. the problem being that your system doesn't have any virtual machine hardware support.

Now which will run better, Windows as the host and ubuntu the guest or ubuntu the host and windows the guest, I don't really know. I would assume that the performance of one over the other, due to your hardware, would be very minimal.

How would you like to proceed?

-Spydey :KS

---

### Post by wahoobob on 2010-08-27
> **spydeyrch said:**
> You could do that if you wanted to. You could install VB for Windows and then install Ubuntu as a VM in VB. But you will run into the same issue really. the problem being that your system doesn't have any virtual machine hardware support.

Now which will run better, Windows as the host and ubuntu the guest or ubuntu the host and windows the guest, I don't really know. I would assume that the performance of one over the other, due to your hardware, would be very minimal.

How would you like to proceed?

-Spydey :KS


I guess I'll just re-boot (literally) for now and maybe take a look at crunch bang in virtual box in windows... I'll go grab an iso and make a ghost of the drive, then try to install inside windows...  I'll just putter for the weekend and restore if unsuccessful.  If it works, I'll do a tutorial and post.

---

### Post by spydeyrch on 2010-08-27
> **wahoobob said:**
> I guess I'll just re-boot (literally) for now and maybe take a look at crunch bang in virtual box in windows... I'll go grab an iso and make a ghost of the drive, then try to install inside windows...  I'll just putter for the weekend and restore if unsuccessful.  If it works, I'll do a tutorial and post.

Ok, sounds good. Have fun with it and if you ever do want to do the whole ubuntu host windows guest thing, I am more than willing to help you through it. :D If needs be, just PM me.

-Spydey :KS

---

### Post by Cwhoward1 on 2010-08-27
> **wahoobob said:**
> Is there a relatively safe and easy way to place a windows 7 virtual machine in 10.04 booted from a windows 7 partition on a T42p thinkpad laptop?  (2 gb ram) There are 1 or two programs that I need from windows 7 and would like to avoid rebooting when I switch to them.  It would be useful to have the work update the files when I do boot into 7.  Is there a tutorial that a newbie could follow for this?  Any help would be appreciated.:)

Glad to read someone is using the same enviroment I am testing.
What desktop do you suggest for ubuntu?
I just installed KDE 4.4.2 - not knowing what to install.
Thanks.

---

### Post by wahoobob on 2010-09-01
using GNOME - no real reason, except I'm more used to it.

---

### Post by DjSesso on 2010-09-01
I have actually just did this install and it works perfectly. I am using 10.04 with win 7 installed inside of virtual box. It works flawlessly. :)

If you need help with it let me know. ;)

---

### Post by wahoobob on 2010-09-02
> **DjSesso said:**
> I have actually just did this install and it works perfectly. I am using 10.04 with win 7 installed inside of virtual box. It works flawlessly. :)

If you need help with it let me know. ;)

Did you have windows 7 as a dual boot then use that install inside 10.04 or a new install of 7 inside 10.04?  Tell me what your computer specs are....

---

### Post by spydeyrch on 2010-10-06
> **DjSesso said:**
> I have actually just did this install and it works perfectly. I am using 10.04 with win 7 installed inside of virtual box. It works flawlessly. :)

If you need help with it let me know. ;)


Yes, it will work, but what are your specs? Depending on your specs, it make not run at its best and in some situations, it may not run at the desirable performance level.

For example, I have a triple boot system: Win7 Pro x64, Ubuntu 10.04 x64, & Mint 9 x64.  In each of them, I have VB and a VM of the other two. Thus, if I am running Win7, I have a VM of Ubuntu 10.04 & Mint 9, if I need them. And if I am running Ubuntu 10.04, I have a VM of Win7 & Mint 9 available too. Get the jist?  ;)

But my specs are:

AMD Phenom 9950 Quad Core 2.6 GHz, oc'd 3.2GHz
4GB DDR2 8500 1066 RAM
1 TB, 3 x 500 TB (all SATA)


I can dedicate 1-3 cores to any given VM and up to just under half of my RAM to any given VM. The CPU has hardware support for VMs. Thus I can run multiple VMs at any given time as well as not take any performance penalty.

Being able to install a VM and run it is completely doable. But what kind of performance is attained? That is the real question. :confused::confused:

So even though it may be doable, will it really be usable/worth it? That all depends on hardware support.  :)

Just my $0.02.  I will step down from my soap-box now. hehehehe :P

-Spydey :KS

---

### Post by UltraZone on 2011-04-21
Wow dude seriously?  You are a thread killer.  You post all the awesome stuff you can do, but you do not share any detailed instructions?  Sheesh... way to make a thread worthless.

---

