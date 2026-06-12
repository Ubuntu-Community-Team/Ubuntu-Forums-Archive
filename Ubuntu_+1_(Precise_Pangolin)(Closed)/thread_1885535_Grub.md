---
title: "Grub"
date: 2011-11-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by raja.genupula on 2011-11-23
Well , Actually its not a Problem . Just small doubt.

I have a system with 11.10 and 12.04 .
Today morning i have installed Debian 6 first time .

I have installed Boot loader too.

Well now What I wanna ask is 

1...In my grub menu , now its only Ubuntu 12.04 and Debian . Its not showing My Ubuntu 11.10

2...I think there is no problem with version of GRUB.

Dont worry i have used sudo dpkg-reconfigure grub-pc and and installed grub to sda of ubuntu

so no issues , but just wanna know the reason why Debian not included Ubuntu 11.10 . 

Thanks in advance .

---

### Post by ranch hand on 2011-11-23
While this is a good question it is difficult to answer with the information given.

When you did your new install there should have been a question asked when grub was being installed (pretty close to the end of the install process) about the other OS's on your box.  Something like "Grub has found these other OS', if this is correct continue....", did you see this?  Was it correct there?

Assuming you let it install grub on the MBR and then booted to your new install, did you then run, as root;
```

update-grub

```
?  This should have picked up your missed OS.
u

---

### Post by jerrrys on 2011-11-23
Hi Raja:

Ranch Hand is right.  When installing other distro's, you got to sure about grub.

Do you multi-boot so you can play with other distro's?  Becomes kind of a pain, doesn't it? I know ranch hand doesn't necessarily agree with this.  But you may want to check out something like VirtualBox.  It makes playing a bit less painless

---

### Post by effenberg0x0 on 2011-11-23
> **jerrrys said:**
> Hi Raja:

Ranch Hand is right.  When installing other distro's, you got to sure about grub.

Do you multi-boot so you can play with other distro's?  Becomes kind of a pain, doesn't it? I know ranch hand doesn't necessarily agree with this.  But you may want to check out something like VirtualBox.  It makes playing a bit less painless

Just a note to reinforce that. Although a VM may be sort of slow on a slow PC (and perform incredibly fast in a fast enough PC), you can create clones of it and test/break them many times a day without a concern. 

I work with PP as my default install. It runs vmware-player (for 2D / Console tests) and Virtualbox (for 3D Acceleration - Unity Tests). Each has 4 Ubuntu machines: Ubuntu-OO32, Ubuntu-OO64, Ubuntu-PP32, Ubuntu-PP64. All these machines are default ISO installs, not even upgraded.

When I want to test something, all I do is choose one of them, depending on what I'll test, clone it, run, test, delete the clone. It makes life easier.

---

### Post by raja.genupula on 2011-11-23
> **ranch hand said:**
> While this is a good question it is difficult to answer with the information given.

When you did your new install there should have been a question asked when grub was being installed (pretty close to the end of the install process) about the other OS's on your box.  Something like "Grub has found these other OS', if this is correct continue....", did you see this?  Was it correct there?

Assuming you let it install grub on the MBR and then booted to your new install, did you then run, as root;
```

update-grub

```
?  This should have picked up your missed OS.
u

Hi man , sorry for late . 

Yeah its asked me and i said yes .i have provided the information in my first post too . 

Debian grub have My ubuntu 12.04 loader but its not having 11.10 Ubuntu loader .

---

### Post by raja.genupula on 2011-11-23
> **jerrrys said:**
> Hi Raja:

Ranch Hand is right.  When installing other distro's, you got to sure about grub.

Do you multi-boot so you can play with other distro's?  Becomes kind of a pain, doesn't it? I know ranch hand doesn't necessarily agree with this.  But you may want to check out something like VirtualBox.  It makes playing a bit less painless

Hi man , its good to see you again .

No problem with multi boot man , i can handle that .I did all to get grub to Ubuntu again . Now no worries . But only that doubt killing me.

---

### Post by raja.genupula on 2011-11-23
> **effenberg0x0 said:**
> Just a note to reinforce that. Although a VM may be sort of slow on a slow PC (and perform incredibly fast in a fast enough PC), you can create clones of it and test/break them many times a day without a concern. 

I work with PP as my default install. It runs vmware-player (for 2D / Console tests) and Virtualbox (for 3D Acceleration - Unity Tests). Each has 4 Ubuntu machines: Ubuntu-OO32, Ubuntu-OO64, Ubuntu-PP32, Ubuntu-PP64. All these machines are default ISO installs, not even upgraded.

When I want to test something, all I do is choose one of them, depending on what I'll test, clone it, run, test, delete the clone. It makes life easier.

Hi man , 
its really a good idea but not suitable to me, I mean its looking some what tedious and time eater but i am struggling with time . 

But this is really good idea man. :)

---

### Post by kansasnoob on 2011-11-23
> **raja.genupula said:**
> Well , Actually its not a Problem . Just small doubt.

I have a system with 11.10 and 12.04 .
Today morning i have installed Debian 6 first time .

I have installed Boot loader too.

Well now What I wanna ask is 

1...In my grub menu , now its only Ubuntu 12.04 and Debian . Its not showing My Ubuntu 11.10

2...I think there is no problem with version of GRUB.

Dont worry i have used sudo dpkg-reconfigure grub-pc and and installed grub to sda of ubuntu

so no issues , but just wanna know the reason why Debian not included Ubuntu 11.10 . 

Thanks in advance .

I see you have a link to the Boot Info Script in your signature. Would you be kind enough to post a fresh BIS output so we can have a look?

It may be helpful :)

---

### Post by ranch hand on 2011-11-23
In your first post you said;
"Dont worry i have used sudo dpkg-reconfigure grub-pc and and installed grub to sda of ubuntu"

This is not what I asked.

The dpkg command will do pretty much the same thing but it is not the reliable way to correct what grub is picking up.  That is done by one script   /etc/grub.d/30_os-prober   at the command, as root;
```

update-grub

```
Did you run that command?

If not I would go to your Debian install and try it.  When you have run i, run this, again as root;
```

grub-mkconfig

```
This will print out your /boot/grub/grub.cfg file in your terminal so you can see if all of your installs are listed with out having to use Debians grub to boot with to check that way.

With out this information there is no answer to your question as to why both Ubuntu installs were not picked up.

The other thing that I asked was if you saw the question on the Debian installer about what OS's were detected.  If so what did it say?  You had to OK this to proceed with the install.

This is also critical to your question.

If, when you go to Debian and run the correct commands, and the grub.cfg file has all three installs now listed, then we know grub is working correctly.  The grub.cfg file is where your screen menu comes from, if you did not know that.

Then we need to know why it did not work when you installed it.  There are two possibilities.
1>the box listing your other installs was correct and the "update-grub" command was not successful when run from the installer

2>the box listing your other installs was not correct and os-prober was not communicating with the installer correctly

If, on the other hand, you go to debian and run the correct commands, both installs are not listed in the grub.cfg file, then we need to consider what is wrong with your grub-pc or grub-common or grub-bin install.

Please answer the questions asked.  They really do matter.

---

### Post by raja.genupula on 2011-11-24
> The dpkg command will do pretty much the same thing but it is not the  reliable way to correct what grub is picking up.  That is done by one  script   /etc/grub.d/30_os-prober   at the command, as root;
[FONT=monospace]update-grub[/FONT]

Did you run that command?

No after installing Debian i haven't run anything .

> The other thing that I asked was if you saw the question on the Debian  installer about what OS's were detected.  If so what did it say?  You  had to OK this to proceed with the install.

This is also critical to your question.

Yes its detected Ubuntu 12.04 only and shown 

> the box listing your other installs was correct and the "update-grub" command was not successful when run from the installer

I have n't interrupted installation process , If grub not properly runs means then  why 12.04 detected ,? 

```
the box listing your other installs was not correct and os-prober was not communicating with the installer correctly


```

If proper communication is not there means , what kind of communication compatibility needed ? 

Because 11.10 founded both Debian and 12.04 .
12.04 also founded 11.10 and Debian
But why Debian founded only 12.04 why not 11.10.


Sorry for late reply , my timings are different .

---

### Post by jerrylamos on 2011-11-24
I haven't tried vm image testing lately.  I do have USB hard drives to test with, a couple 2.5" laptop drives I had laying around in a USB case, $20 for one case $10 for the other.  Not much cost for fast response.  Even the 40 GB one has space for 3 installs, the 100 GB plenty.  

USB hard drives my impression speed and user response "same" as installed hard drive while allowing install and grub testing without screwing up the main hard drive.  Hopefully.

My biggest caution is my fast tower with a sata and an ide hard drive.
All ubuntu's up through Natty Narwhal call the boot hard drive /dev/sda and the other hard drive /dev/sdb.  The USB hard drive is /dev/sdc.

Oneiric and Pangolin call the boot hard drive /dev/sdb and the other hard drive /dev/sda.  Just reversed!  Yes there's a launchpad bug.  No, development's not interested.

Plus on this netbook, the USB hard drive that was /dev/sdc is /dev/sdb.  On my latest notebook the USB hard drive is /dev/sdc.  Go figure.

Why does all this matter?  Install says which /dev/sdx it is going to install grub to, better pay attention....

Jerry

---

### Post by raja.genupula on 2011-11-24
Hi man its good to see you again.
Yeah i have verified while installation going on ..

---

### Post by ranch hand on 2011-11-24
> **raja.genupula said:**
> No after installing Debian i haven't run anything .



Yes its detected Ubuntu 12.04 only and shown 


I have n't interrupted installation process , If grub not properly runs means then  why 12.04 detected ,? 

```
the box listing your other installs was not correct and os-prober was not communicating with the installer correctly


```If proper communication is not there means , what kind of communication compatibility needed ? 

Because 11.10 founded both Debian and 12.04 .
12.04 also founded 11.10 and Debian
But why Debian founded only 12.04 why not 11.10.


Sorry for late reply , my timings are different .
Time zones happen and we are a bit apart.  This is no problem.

The problem, which seems to happen with all distros when installing is actually, I think, caused by the install script for the package grub-pc in some way.  Some times it just misses an install.  This is, by the way, run by dpkg  configuring grub-pc.

The command update-grub on the other hand is not configuring a package.  It is a native command configuring a boot loading system, primarily working with grub-pc and grub-common

You really ought to pop over to your Debian install and see, in the manner I described earlier, if grub is working correctly.  I suspect it will work fine.

All that is needed is to run update-grub (as root - in Debian I just use the root terminal) and then check the grub.cfg file by running "grub-mkconfig" and look at it.

This will not change which OS is in charge of you MBR or anything else.  This will just effect the files in the Debian install, if that has been bothering you.

It is a good idea to check this.  It is possible that os-prober is not working properly.

I am embarrassed that I am not sure which version of grub-pc Squeeze is running as  I do have an install of it that I was on last night.   It is however an older version than your other installs are running.  Should be about what Ubuntu 10.04 is running.  This was, at least in Ubuntu, somewhat buggy.  My wife uses 10.04 but does not have that version on there as I installed a newer one there.

I do not have, all that said, any trouble booting any of the 6 installs of a mixed Debian and Ubuntu drive using the grub that is standard in Squeeze to do the job.

---

