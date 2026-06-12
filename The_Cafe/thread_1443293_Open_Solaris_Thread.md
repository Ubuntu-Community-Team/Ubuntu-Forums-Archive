---
title: "Open Solaris Thread"
date: 2010-03-30
forum: The Cafe
---

### Post by swoll1980 on 2010-03-30
I started using Open Solaris like a week ago. I'm triple booting it with 10.04 and 7. It's alot different, than I expected it to be.  I want some UNIX experience, so I guess this is a way to get it. If you have any tips that will make it easy to do every day task share them here. The easiest way I find to learn an OS is just to use it for everything. You run into problems try to figure them out . A command here, a command there. This file needs to be configured like this, and pretty soon you actually have an idea of what you're doing. Getting my nvidia drivers to work was the first thing I learned how to do. I tried freeBSD in the past but never stuck with it long enough to actually learn much about it.

---

### Post by NightwishFan on 2010-03-30
I plan on trying it. I like the Nimbus gtk theme.

---

### Post by swoll1980 on 2010-03-30
> **NightwishFan said:**
> I plan on trying it. I like the Nimbus gtk theme.

Yeah it's nice there is supposed to be a way to get it to work with Ubuntu, but I never had any luck with it. One thing that drives me nuts about it is boot time. It's a freakin' slug. I'm talking like 5 minutes, and I have a pretty good rig. There's many cool features I guess once you know what the hell you're doing though.

---

### Post by NightwishFan on 2010-03-30
[https://launchpad.net/~merlwiz79/+archive/nimbus](https://launchpad.net/~merlwiz79/+archive/nimbus)

Or you can probably just package it yourself in .tar.gz from /usr/share/themes.

Does Solaris run on AMD64?

---

### Post by swoll1980 on 2010-03-30
> **NightwishFan said:**
> [https://launchpad.net/~merlwiz79/+archive/nimbus]("https://launchpad.net/%7Emerlwiz79/+archive/nimbus")

Or you can probably just package it yourself in .tar.gz from /usr/share/themes.

Does Solaris run on AMD64?

Yeah that's what I'm running. Phenom II 3.1

---

### Post by NightwishFan on 2010-03-30
Excellent, I shall have to give it a go, I believe it will run in Virtualbox (as I have no spare CDs, so I will have to go with 32-bit, since I lack vt-x).

---

### Post by swoll1980 on 2010-03-30
> **NightwishFan said:**
> Excellent, I shall have to give it a go, I believe it will run in Virtualbox (as I have no spare CDs, so I will have to go with 32-bit, since I lack vt-x).

There's an audio problem you can run into with Virtualbox I believe there is a fix for it. I just said screw it and installed it on my portable hard drive. Since I knew all my machines hardware was compatible. Figured that would be easier than trying to fix it in a vm.

---

### Post by NightwishFan on 2010-03-30
I see, thanks. I have no problem with that. I will not judge problems just because it is in a VM. I hope you get some other opinions here as well not just me. :D

---

### Post by swoll1980 on 2010-03-30
> **NightwishFan said:**
> I see, thanks. I have no problem with that. I will not judge problems just because it is in a VM. I hope you get some other opinions here as well not just me. :D

I just went to log into it and found out it was trashed. I tried using gparted earlier to expand the partition it was in, and I got an error. At the time it looked like nothing was done to it, but as I went to log in it said my partition didn't exist.  Looks like I have to reinstall it. This time I will expand the partition first.  /Duh #-o

---

### Post by kaldor on 2010-03-30
> **swoll1980 said:**
> I started using Open Solaris like a week ago. I'm triple booting it with 10.04 and 7. It's alot different, than I expected it to be.  I want some UNIX experience, so I guess this is a way to get it. If you have any tips that will make it easy to do every day task share them here. The easiest way I find to learn an OS is just to use it for everything. You run into problems try to figure them out . A command here, a command there. This file needs to be configured like this, and pretty soon you actually have an idea of what you're doing. Getting my nvidia drivers to work was the first thing I learned how to do. I tried freeBSD in the past but never stuck with it long enough to actually learn much about it.

Give me a link on how to dual boot Ubuntu/OpenSolaris without messing things up!

I love what I see when I use OpenSolaris; I'd love to learn how to use true UNIX OS's, commercial ones at that.

---

### Post by Dayofswords on 2010-03-30
i'm not sure about this....

but isnt linux an open source(well...gpl) version of unix, same commands, same location of stuff

---

### Post by swoll1980 on 2010-03-30
> **kaldor said:**
> Give me a link on how to dual boot Ubuntu/OpenSolaris without messing things up!

I love what I see when I use OpenSolaris; I'd love to learn how to use true UNIX OS's, commercial ones at that.

All you will have to do is log back into Ubutu and reinstall/fix the grub [this is the link]("http://www.google.com/url?sa=t&source=web&ct=res&cd=2&ved=0CBcQFjAB&url=http%3A%2F%2Fpraveen.kumar.in%2F2010%2F02%2F20%2Fchainloading-opensolaris-from-grub-2%2F&ei=Z8CyS4SyC4Gdlgf_x7y-BA&usg=AFQjCNH5ET1Tq6G86DldGQ_SnQwtm9VqCA") I used to learn how.

---

### Post by swoll1980 on 2010-03-30
> **Dayofswords said:**
> i'm not sure about this....

but isnt linux an open source(well...gpl) version of unix, same commands, same location of stuff

That's what I thought, but in my Linux class I have a teacher who is a UNIX guy, and during the class we run into things that don't work the same as what he's used to. ZFS is one major difference I've noticed myself the chattr command doesn't work in Solaris so I will have to learn a way around that.

---

### Post by kaldor on 2010-03-30
Linux is NOT UNIX in any way; it's a clone. 

Linux has re-created many UNIX features, but it is not identical. It isn't a free/GPL version of UNIX.

Solaris is based on UNIX System V.


Edit: The only thing stopping me from trying out Solaris as my main OS for awhile to try it out is just Skype; I use Skype a *lot* for many things. Is there any way to get Skype running on OpenSolaris? I don't mean a distro of Solaris. I want to try "true" Solaris out, if you know what I mean.

Any clients for Skype?

---

### Post by kaldor on 2010-03-31
Oh, another topic for discussion; what do you OpenSolaris/Solaris users think about Oracle? Will Solaris die/fall behind like it currently is, or will it keep up? Maybe even surpass Linux?

---

### Post by swoll1980 on 2010-03-31
> **kaldor said:**
> Oh, another topic for discussion; what do you OpenSolaris/Solaris users think about Oracle? Will Solaris die/fall behind like it currently is, or will it keep up? Maybe even surpass Linux?

I don't think it will ever surpass Linux, but who knows. It has some nice features that Linux doesn't have. What it doesn't have is the momentum. As far as Oracle goes they have more money, and man power then Sun ever did, so I we will have to see what they do with it. I think Solaris will only get better this is a solution for customers that want UNIX, and it gives Oracle an edge to be able to cater to both Linux, and UNIX customers.

---

### Post by Dayofswords on 2010-03-31
> **kaldor said:**
> Linux is NOT UNIX in any way; it's a clone. 

Linux has re-created many UNIX features, but it is not identical. It isn't a free/GPL version of UNIX.

well... what i meant was that
not being a version unix, just like it
i guess it came out wrong

---

### Post by Dobbie03 on 2010-03-31
I like Open Solaris and I would like to use it more but I have two issues:
1.  It's boot time
2. For the life of me I cant seem to work out how to mount my external hard disk.

---

### Post by swoll1980 on 2010-03-31
> **MattDobson said:**
> I like Open Solaris and I would like to use it more but I have two issues:
1.  It's boot time
2. For the life of me I cant seem to work out how to mount my external hard disk.

It lacks ntfs support at this time. It can only mount fat partitions on the Windows side.

---

### Post by Regenweald on 2010-03-31
> **swoll1980 said:**
> It lacks ntfs support at this time. It can only mount fat partitions on the Windows side.

I believe they have the ntfs-3g libraries in thir repos. You should double check that. I'm waiting for whenever they release the 2010 version to grab a copy.

---

### Post by swoll1980 on 2010-03-31
> **Regenweald said:**
> I believe they have the ntfs-3g libraries in thir repos. You should double check that. I'm waiting for whenever they release the 2010 version to grab a copy.

  Well then he would just need to install the libs then I'm sure. This is good news.

---

### Post by Regenweald on 2010-03-31
I'll join you on your Opensolaris quest once I get an external and sort out my drives. I'm juggling about 2 gigs of free space now across 3 hd's. You should look into crossbow and zones/containers. Really impressive tech.

---

### Post by swoll1980 on 2010-03-31
> **Regenweald said:**
> I'll join you on your Opensolaris quest once I get an external and sort out my drives. I'm juggling about 2 gigs of free space now across 3 hd's. You should look into crossbow and zones/containers. Really impressive tech.

Yeah that stuff sounds pretty interesting.

---

### Post by Dobbie03 on 2010-03-31
> **swoll1980 said:**
> It lacks ntfs support at this time. It can only mount fat partitions on the Windows side.

Ah that sucks.  They need to remedy that....pronto.

---

### Post by kaldor on 2010-03-31
*bump*

Skype? :(

---

### Post by Laxman_prodigy on 2010-03-31
Sorry mate.

[B]Sounds like Opensolaris is/will be no longer free.
[/B]
[http://www.katonda.com/news/solaries-no-more-free-open-solaris-may-die/936/2010](http://www.katonda.com/news/solaries-no-more-free-open-solaris-may-die/936/2010)[URL="http://http//www.katonda.com/news/solaries-no-more-free-open-solaris-may-die/936/2010"]
[/URL]

---

### Post by ve4cib on 2010-03-31
> **Laxman_prodigy said:**
> Sorry mate.

[B]Sounds like Opensolaris is/will be no longer free.
[/B]
[http://www.katonda.com/news/solaries-no-more-free-open-solaris-may-die/936/2010](http://www.katonda.com/news/solaries-no-more-free-open-solaris-may-die/936/2010)[URL="http://http//www.katonda.com/news/solaries-no-more-free-open-solaris-may-die/936/2010"]
[/URL]

Solaris 10 (the Enterprise version of Solaris) won't be free anymore, but OpenSolaris will still be free.  At least until Oracle decides to pull the plug on it, at which point it will be unavailable (so you still won't need to pay for it).  Oracle has stated that they will continue to support OpenSolaris though, which is good news.

[http://itmanagement.earthweb.com/osrc/article.php/3867771/OpenSolaris-Alive-](http://itmanagement.earthweb.com/osrc/article.php/3867771/OpenSolaris-Alive-)

---

### Post by samalex on 2010-03-31
I just downloaded Open Solaris last weekend but couldn't get it to install in VirtualBox.  Just sat at the first screen with the copyright text with no options to move forward.

I didn't spend much time playing with it though, and just deleted the ISO this morning.  I may toy with it later, I was just curious because I hadn't used Solaris since college in the late 90's.

Sam

---

### Post by swoll1980 on 2010-03-31
> **MattDobson said:**
> Ah that sucks.  They need to remedy that....pronto.
I was mistaken you can install from repos.

---

### Post by Dobbie03 on 2010-04-01
> **swoll1980 said:**
> I was mistaken you can install from repos.

What is it that I need to install to be able to mount my external?

---

### Post by NightwishFan on 2010-04-01
Ntfs-3g.

---

### Post by m4tic on 2010-04-01
Solaris wants me to format my home drive, it doesnt recognise extended partitions, 2 bad it doesnt even boot on my lenovo 3000 N200

---

### Post by swoll1980 on 2010-04-02
I haven't been able to get mine running again. I don't know what I did.

---

### Post by NightwishFan on 2010-04-02
Can you run Solaris from a liveusb?

---

### Post by tilapia on 2010-04-04
> I don't think it will ever surpass Linux, but who knows. It has some nice features that Linux doesn't have. What it doesn't have is the momentum. As far as Oracle goes they have more money, and man power then Sun ever did, so I we will have to see what they do with it. I think Solaris will only get better this is a solution for customers that want UNIX, and it gives Oracle an edge to be able to cater to both Linux, and UNIX customers.

ZFS is amazing, and it's a shame that Linux doesn't have it (outside of Fuse). The TimeSlider application which they've integrated into Gnome is absolutely brilliant. While I haven't used them myself, Dtrace and Zones are also meant to be really good. I used OpenSolaris for quite a while on my workstation and then my laptop and found it really stable and quite quick. 

There are two reasons why I stopped using it though. Firstly, it doesn't have many decent video codecs, so if you want to use it on a laptop for anything other than dev/work then it's limited. Secondly, the OpenSolaris community is small and, dare I say it, not really as friendly as that of Linux. If you get a problem you'll be on your own if you don't pay for support, unlike with Linux, in which case support is only a helpful forum user away.

---

### Post by swoll1980 on 2010-04-05
> **tilapia said:**
> ZFS is amazing, and it's a shame that Linux doesn't have it (outside of Fuse). The TimeSlider application which they've integrated into Gnome is absolutely brilliant. While I haven't used them myself, Dtrace and Zones are also meant to be really good. I used OpenSolaris for quite a while on my workstation and then my laptop and found it really stable and quite quick. 

There are two reasons why I stopped using it though. Firstly, it doesn't have many decent video codecs, so if you want to use it on a laptop for anything other than dev/work then it's limited. Secondly, the OpenSolaris community is small and, dare I say it, not really as friendly as that of Linux. If you get a problem you'll be on your own if you don't pay for support, unlike with Linux, in which case support is only a helpful forum user away.

They have a community media repo now that has all the video codecs you would need for normal day to day things. The support is limited to gstreamer, though this doesn't bother me. It's what I've always used anyways

---

### Post by swoll1980 on 2010-04-05
> **NightwishFan said:**
> Can you run Solaris from a liveusb?

I'm running it on an external USB hard drive. Not sure if there would be any difference.

---

### Post by neu5eeCh on 2010-04-06
> **swoll1980 said:**
> They have a community media repo now that has all the video codecs you would need for normal day to day things. The support is limited to gstreamer, though this doesn't bother me. It's what I've always used anyways

Can you provide a link for that? I've been googling, found a "community repo" but none of the packages seem related to video codecs. (Thought I'd get all my ducks in a row before I dabble in OSOL.)

---

