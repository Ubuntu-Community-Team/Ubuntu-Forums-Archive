---
title: "VirtualBox 4.0.8. Ubuntu host. Fedora 15 guest problems"
date: 2011-06-07
forum: Virtualisation
---

### Post by coffeecat on 2011-06-07
I've had a somewhat frustrating few days with VirtualBox 4.0.8 r71778 running in Natty (Unity). That's the proprietary version of VB installed from the virtualbox.org repository, not the virtualbox-ose version.

This is not a request for technical help, unless anyone has any suggestions for what I might have missed, but rather a plea for comments. 

I've had repeated and unpredictable guest OS freezes with (mostly) Fedora 15, Ubuntu Oneiric Alpha 1 and less so with Lucid, all installed to their own virtual machines. The 'mostly' Fedora is mainly because I've been trying to get the thing installed more often than trying the others. The Fedora installer regularly freezes part way into the writing packages to drive stage - this from both the live CD ISO and the DVD ISO - although I did get one installation up and running together with guest-additions installed until repeated freezes broke it. A virtual Vista seems unaffected by this problem although I must admit I haven't used it much yet.

At first I thought I had a bad RAM stick because swapping them around seemed to make a difference, but further experimentation showed that this was not so. I've now installed VirtualBox from the same deb to another machine also running Natty, run the Fedora installer to a virtual guest and guess what? It froze more solidly than the North Pole when it reached the partitioning stage. I do **not** believe that four RAM sticks in one machine and two in another are all faulty, particularly when only virtual machines running in VB are playing up.

I've looked (briefly) on the Virtual Box forum but I didn't see any complaints about this (latest) version of VB. I'm wondering if there is an issue with this version running in Natty as a host, and with a Linux guest. I would be interested in others' experiences. What version of VB are you using, what as a host, what guests?

Thanks.

---

### Post by jerrrys on 2011-06-08
i recently tried an upgrade to 4.x and had problems with xserver.  played with it for half a day and went back to 3.x  host ubuntu 10o4; guest X and Lubuntu.  i think my problem could of been resolved, but i am more interested in using it and not fixing it.

---

### Post by coffeecat on 2011-06-08
Unfortunately, going back to VB version 3 is not an option for me. I was wanting to use it to test Oneiric and try out gnome shell in Fedora, for both of which I need 3d accleration in the guest, which isn't possible in VB <4.

Every time I try to install Fedora now, it seizes up whereas Oneiric has been behaving itself last few times I booted it up. I'm beginning to wonder if there is a serious incompatibility with Fedora 15 as a guest and the few freezes I had with Oneiric is because it is still alpha.

I'm giving up on Fedora and will see how Oneiric shapes up as a guest over the next little while. I would still be interested in others' experiences.

---

### Post by coffeecat on 2011-06-09
Well - I didn't completely give up after all and I have some sort of an answer, though not exactly a fix. On the principle of one picture being worth a thousand words, have a look at my screenshot, which must rank as one of the silliest screenshots I'm ever likely to post to this forum. Yes, folks, that's a virtual Fedora 15 running as guest in a virtual Vista as host, which itself is a guest in the real host, Ubuntu Natty. :redface:

What puzzled me about all this was this link which clearly describes Fedora 15 running OK in VirtualBox 4.0.8:

[http://www.sysprobs.com/install-fedora-15-virtualbox-steps-install-virtualbox-guest-additions-fedora-15](http://www.sysprobs.com/install-fedora-15-virtualbox-steps-install-virtualbox-guest-additions-fedora-15)

Until I took a closer look and saw the unmistakable features of Windows in the screenshots. Which is why I installed VirtualBox to my virtual Vista and installed Fedora 15 to a guest VM in that. The Fedora installer behaved impeccably, albeit in a leisurely sort of way, and I can boot into a (just) usable Fedora desktop - very sluggish and in fallback mode because of no 3d acceleration - but usable nonetheless.

Long story short, these are my experiences.

**Vista** has been stable as a guest machine, surviving the lengthy Fedora install process. Vista stable - that must be noteworthy!

**Oneiric** has been fine for a day or so now. The couple of freezes I did get were probably a function of how unstable it is at this early alpha stage of the development cycle, and nothing to do with the issues affecting Fedora.

**Lucid**. As far as I remember, just one freeze. I'm prepared to write that off as just one of those things.

**Fedora**. Ah, Fedora! I must have run the DVD ISO installer more than a dozen times, once on another machine. It froze most times during the copy packages to hard drive stage, and a couple of times at the partitioning stage. I tried the live CD ISO more than half-a-dozen times and most times it froze similarly. The one time it did complete the install must have been a fluke, but Fedora triumphed in the end by freezing itself a couple of times and making itself unbootable.

Just to exclude the possibility of this being a Natty-as-host problem, I installed Lucid to another partition on this machine, installed the Lucid version of VirtualBox 4.0.8 and ran the Fedora DVD installer to a VM in Lucid. The Fedora installer froze in the usual place. Of course.

Moral: Fedora 15 in a virtual machine in Vista is doable. In Ubuntu as host it is not worth trying.

Whether this is a problem in Fedora itself or with Fedora in the Linux version of VirtualBox, or even just the Ubuntu version of VB, I have no idea. I could install Fedora natively to its own partition, install VirtualBox and then Fedora inside a guest VM running in Fedora. I could, but I've had enough of Fedora. I have been cured of Fedora. I don't think I want to see the Fedora installer every again. And I certainly don't want to see that stripey blue wallpaper again. :wink:

---

### Post by Jake.Debord on 2011-06-10
I've seen where they suggest a vbox inside a vbox having LOTS of problems... I've been to so many forums and pages and documentation I have no idea where exactly I witnessed the statements. I'm sure you have a good reason for doing so, but it may just be rough experience until more support is available :(

---

### Post by collisionystm on 2011-06-10
> **coffeecat said:**
> I've had a somewhat frustrating few days with VirtualBox 4.0.8 r71778 running in Natty (Unity). That's the proprietary version of VB installed from the virtualbox.org repository, not the virtualbox-ose version.

This is not a request for technical help, unless anyone has any suggestions for what I might have missed, but rather a plea for comments. 

I've had repeated and unpredictable guest OS freezes with (mostly) Fedora 15, Ubuntu Oneiric Alpha 1 and less so with Lucid, all installed to their own virtual machines. The 'mostly' Fedora is mainly because I've been trying to get the thing installed more often than trying the others. The Fedora installer regularly freezes part way into the writing packages to drive stage - this from both the live CD ISO and the DVD ISO - although I did get one installation up and running together with guest-additions installed until repeated freezes broke it. A virtual Vista seems unaffected by this problem although I must admit I haven't used it much yet.

At first I thought I had a bad RAM stick because swapping them around seemed to make a difference, but further experimentation showed that this was not so. I've now installed VirtualBox from the same deb to another machine also running Natty, run the Fedora installer to a virtual guest and guess what? It froze more solidly than the North Pole when it reached the partitioning stage. I do **not** believe that four RAM sticks in one machine and two in another are all faulty, particularly when only virtual machines running in VB are playing up.

I've looked (briefly) on the Virtual Box forum but I didn't see any complaints about this (latest) version of VB. I'm wondering if there is an issue with this version running in Natty as a host, and with a Linux guest. I would be interested in others' experiences. What version of VB are you using, what as a host, what guests?

Thanks.

I have Ubuntu Natty as a host. Most of the time I use Vmware Player. It lets you keep Aero in Windows 7 and drag and drop files from one desktop to the other. Much better.

However, I did run Windows 7 in  the latest Vbox with no issues. I havent tried any Linux OS because I run them all in vmware player.

---

### Post by coffeecat on 2011-06-10
> **Jake.Debord said:**
> I've seen where they suggest a vbox inside a vbox having LOTS of problems... I've been to so many forums and pages and documentation I have no idea where exactly I witnessed the statements. I'm sure you have a good reason for doing so, but it may just be rough experience until more support is available :(

Yes, there was a "good reason". It's all described in my previous posts. :)

I think you must have missed the central point I was making. Fedora 15 won't install as a guest in VBox 4.0.8 with Ubuntu as host. It froze consistently. I merely used my virtual Vista as a convenient Windows installation to try to install Fedora as a VBox guest in a Windows host. It worked just fine, albeit slowly, thus suggesting that a virtual VBox Fedora in an Ubuntu host is a no-go.

I have done some eccentric things in my time, but routinely using a virtual machine inside a virtual machine  goes beyond a line I do not wish to cross! :-s 

 :wink:

---

### Post by Jake.Debord on 2011-06-10
Haha, it would be like watching a T.V. inside a T.V. or wiping before you poop, wouldn't make much sense! I remember someone said they got it to working *better* was adding more ram to the vm for the install etc...

---

### Post by collisionystm on 2011-06-10
A guest within a guest? I will give it a go. Natty host, natty guest and fedora 15 guest. Same as you. I will see what happens

---

### Post by coffeecat on 2011-06-10
> **collisionystm said:**
> I have Ubuntu Natty as a host. Most of the time I use Vmware Player. It lets you keep Aero in Windows 7 and drag and drop files from one desktop to the other. Much better.

However, I did run Windows 7 in  the latest Vbox with no issues. I havent tried any Linux OS because I run them all in vmware player.

Thanks for that. That's really helpful.

I did try VMWare Player as well - first time I had done so. If you look very closely, you might be able to make out the VMware Player icon in the launcher in my screenshot. :) Even though the VMWare Player said it had enabled 3d and even though I installed VMWare Tools to a test virtual Lucid install, I couldn't enable compiz and turned my attention back to VirtualBox at that point.

And thanks for letting me know that you could get Aero in Windows 7. Rather conversely, I had no problem with activating compiz in a virtual Ubuntu in VitualBox, but simply couldn't get Aero enabled in Vista. Vista kept telling me that my Windows Experience score was only 1. Considering it's Vista, that sounds about right! :rolleyes:

When I've recovered from my Fedora/VirtualBox exertions, I'll have another look at VMWare. I liked the look of what I saw but I have far less experience than with VirtualBox. My inability to get compiz in a virtual Lucid may be simply an error on my part.

Apart from which I'm concerned for the future of VirtualBox. Now that it's in the hands of Oracle, who knows how long they will support it?

---

### Post by coffeecat on 2011-06-10
> **collisionystm said:**
> A guest within a guest? I will give it a go. Natty host, natty guest and fedora 15 guest. Same as you. I will see what happens

Well, good luck with that, is all I can say. :) After all my efforts (documented in my previous posts) I will never, ever, ever, ever try to install Fedora as a guest OS in Ubuntu ever, ever, ever again. ](*,) :(

Of course, now you're going to come back and tell me it installed and ran like a charm! :p

**EDIT**: no "Natty host, natty guest and fedora 15 guest. Same as you." is not quite right.

Natty host, Fedora 15 guest - there lie anguish and pain.

Natty host, Vista guest hosting Fedora 15 as guest - works. Glacially. :)

---

### Post by Jake.Debord on 2011-06-10
Please move at a glacial pace you KNOW how that thrills me.

Devil wears Prada reference... Sorry, had to.

---

### Post by collisionystm on 2011-06-10
> **coffeecat said:**
> Thanks for that. That's really helpful.

I did try VMWare Player as well - first time I had done so. If you look very closely, you might be able to make out the VMware Player icon in the launcher in my screenshot. :) Even though the VMWare Player said it had enabled 3d and even though I installed VMWare Tools to a test virtual Lucid install, I couldn't enable compiz and turned my attention back to VirtualBox at that point.

And thanks for letting me know that you could get Aero in Windows 7. Rather conversely, I had no problem with activating compiz in a virtual Ubuntu in VitualBox, but simply couldn't get Aero enabled in Vista. Vista kept telling me that my Windows Experience score was only 1. Considering it's Vista, that sounds about right! :rolleyes:

When I've recovered from my Fedora/VirtualBox exertions, I'll have another look at VMWare. I liked the look of what I saw but I have far less experience than with VirtualBox. My inability to get compiz in a virtual Lucid may be simply an error on my part.

Apart from which I'm concerned for the future of VirtualBox. Now that it's in the hands of Oracle, who knows how long they will support it?

yeah I cant really say I am a fan of oracle. I really wish I could get my hands on vmware workstation. Have you checked it out? It has FULL 3D support.... it has a screenshot of playing half life 2 in a windows session!!

---

### Post by collisionystm on 2011-06-10
> **coffeecat said:**
> Thanks for that. That's really helpful.

I did try VMWare Player as well - first time I had done so. If you look very closely, you might be able to make out the VMware Player icon in the launcher in my screenshot. :) Even though the VMWare Player said it had enabled 3d and even though I installed VMWare Tools to a test virtual Lucid install, I couldn't enable compiz and turned my attention back to VirtualBox at that point.

And thanks for letting me know that you could get Aero in Windows 7. Rather conversely, I had no problem with activating compiz in a virtual Ubuntu in VitualBox, but simply couldn't get Aero enabled in Vista. Vista kept telling me that my Windows Experience score was only 1. Considering it's Vista, that sounds about right! :rolleyes:

When I've recovered from my Fedora/VirtualBox exertions, I'll have another look at VMWare. I liked the look of what I saw but I have far less experience than with VirtualBox. My inability to get compiz in a virtual Lucid may be simply an error on my part.

Apart from which I'm concerned for the future of VirtualBox. Now that it's in the hands of Oracle, who knows how long they will support it?


Ill bet if you added more memory.... 2 cpu's, and upped your Video card memory in the vista guess it would get a high enough score. Oh and make sure you install guest editions with 3d support, but it has to be ran in safe mode!

---

### Post by collisionystm on 2011-06-10
wow it let me run unity in a virtualbox session... didnt see that one coming

---

### Post by coffeecat on 2011-06-10
> **collisionystm said:**
> Ill bet if you added more memory.... 2 cpu's, and upped your Video card memory in the vista guess it would get a high enough score. Oh and make sure you install guest editions with 3d support, but it has to be ran in safe mode!

Been there; done that! :) 3GB system memory allocated to the Vista guest machine, 4 CPU cores of my quad-core allocated and video card memory to the max allowed - 128MB iirc. And installed guest-additions in safe mode. But Vista still gives an experience score of only 1. Perhaps it's a Vista-only problem that doesn't occur with W7.

---

### Post by collisionystm on 2011-06-10
Well Natty host, natty guest with unity support, and a fedora guest inside of that natty.... Bust. My CPU isnt powerful enough to handle it lol. I kept htop running and it was maxing out. To many calculations! Now if only I still had my alienware.... 2 quad core xeons and 16gb of ram. I had Lucid on it... natty would be awesome.

---

### Post by collisionystm on 2011-06-10
hahahhaha I installed Vmware player and I think I can get this to work.

VIrutalbox running natty, natty running vmware player... I just need a 32bit fedora because virtualbox isnt passing on info to vmware saying it can do VT on my cpu

---

### Post by fjgaude on 2011-06-10
Fedora 15, VMplayer, Natty host... how do you install the Tools within the VM?

I had to install lots of things, like gcc, etc., but still I couldn't get the Tools to compile, because of missing programs within the install of Fedora.

Help!

---

### Post by collisionystm on 2011-06-10
> **fjgaude said:**
> Fedora 15, VMplayer, Natty host... how do you install the Tools within the VM?

I had to install lots of things, like gcc, etc., but still I couldn't get the Tools to compile, because of missing programs within the install of Fedora.

Help!

did you run the fedora software update first?

---

### Post by fjgaude on 2011-06-10
> **collisionystm said:**
> did you run the fedora software update first?

Can't remember... likely not because I haven't used Fedora for about seven years... will try it, as you suggest.

Thank you!

---

### Post by coffeecat on 2011-06-10
> **fjgaude said:**
> 

I had to install lots of things, like gcc, etc., but still I couldn't get the Tools to compile, because of missing programs within the install of Fedora.

Off the top of my head, I'd suggest kernel headers and dkms.

If that doesn't work, and as entertaining as this thread is becoming, I suggest you start your own thread. The thread title may not attract people experienced in VMWare who would be able to help.

Unless collisionystm has the answer. :)

**EDIT**: beat me to it!

---

### Post by fjgaude on 2011-06-10
> **coffeecat said:**
> Off the top of my head, I'd suggest kernel headers and dkms.

If that doesn't work, and as entertaining as this thread is becoming, I suggest you start your own thread. The thread title may not attract people experienced in VMWare who would be able to help.

Unless collisionystm has the answer. :)

**EDIT**: beat me to it!

This is a Fedora guest issue. Okay, ran the update, and now it's as you say: header location?

Can't find it.

---

### Post by collisionystm on 2011-06-10
yum install kernel-devel

that will install the headers

---

### Post by collisionystm on 2011-06-10
> **coffeecat said:**
> off the top of my head, i'd suggest kernel headers and dkms.

If that doesn't work, and as entertaining as this thread is becoming, i suggest you start your own thread. The thread title may not attract people experienced in vmware who would be able to help.

Unless collisionystm has the answer. :)

**edit**: Beat me to it!


:d

---

### Post by collisionystm on 2011-06-10
after install headers, run the vmware config again

su root

cd /usr/bin/

./vmware-config-tools.pl

or it may be 

sh vmware-config-tools.pl

---

### Post by fjgaude on 2011-06-10
All done, working like a charm!

Thanks guys for the help.

---

