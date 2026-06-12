---
title: "Is WUBI useful?"
date: 2011-10-26
forum: The Cafe
---

### Post by Linux_junkie on 2011-10-26
Having read these forums for a while I've discovered that an awful lot of (new) users are using Ubuntu as a Windows application and getting a lot of problems operating Ubuntu that way.  I can see why WUBI was developed in the first place to allow Windows users discover the great things within Ubuntu but surely isn't a better option to use the live CD's to test Ubuntu and if works from a live CD then it will work once installed properly on the hard disk.

Likewise, isn't it better to encourage new users to duel boot rather than install within Windows?

What do you think?

---

### Post by philinux on 2011-10-26
> **Linux_junkie said:**
> Having read these forums for a while I've discovered that an awful lot of (new) users are using Ubuntu as a Windows application and getting a lot of problems operating Ubuntu that way.  I can see why WUBI was developed in the first place to allow Windows users discover the great things within Ubuntu but surely isn't a better option to use the live CD's to test Ubuntu and if works from a live CD then it will work once installed properly on the hard disk.

Likewise, isn't it better to encourage new users to duel boot rather than install within Windows?

What do you think?

Check out the wubi megathread post #1 in General Help forum.

---

### Post by haqking on 2011-10-26
> **Linux_junkie said:**
> Having read these forums for a while I've discovered that an awful lot of (new) users are using Ubuntu as a Windows application and getting a lot of problems operating Ubuntu that way.  I can see why WUBI was developed in the first place to allow Windows users discover the great things within Ubuntu but surely isn't a better option to use the live CD's to test Ubuntu and if works from a live CD then it will work once installed properly on the hard disk.

Likewise, isn't it better to encourage new users to duel boot rather than install within Windows?

What do you think?

WUBI is dual boot

Ubuntu is not running as an application under Windows, it is just stored in a file not a partition

---

### Post by Linux_junkie on 2011-10-26
> **haqking said:**
> WUBI is dual boot

Ubuntu is not running as an application under Windows, it is just stored in a file not a partition

Yeah sorry, as I've never installed Ubuntu the WUBI way I just assumed it was treated as a Windows app from reading comments about it on these forums.

But I still think that WUBI is a waste of time when you can duel boot from the normal installation process.

---

### Post by haqking on 2011-10-26
> **Linux_junkie said:**
> Yeah sorry, as I've never installed Ubuntu the WUBI way I just assumed it was treated as a Windows app from reading comments about it on these forums.

But I still think that WUBI is a waste of time when you can duel boot from the normal installation process.

And if you dont have a partition available ? It also prevents Windows users from losing data due to paritioning and formatting.

WUBI exists for people who want to use it under windows to experience Ubuntu.  A live CD/USB/DVD is good, but for someone in windows who has no experience of Linux might be overwhelmed by the things like making these persistent and if they dont they get frustrated as changes cant be made.  A VM works but doesnt test Ubuntu on the real hardware. IMO

As for people having problems with it, that is the nature of people ;-)

---

### Post by ajgreeny on 2011-10-26
A live CD or USB is very slow in comparison with a wubi installation within windows, so to get a good view of the speed of Ubuntu vs windows wubi is a much better test-bed.

It is not, however, really meant as a long term dual-boot option, more a means of testing the OS fully before going down the partitioning route, which often scares people, as they do not even know what partitions are all about.

---

### Post by fatality_uk on 2011-10-26
Yes, next question.

---

### Post by mamamia88 on 2011-10-26
live cd is too slow live usb flash drive would be much better.   wubi is a good choice if you can't commit to partitioning your harddrive or restoring mbr if you decide to delete ubuntu.   Trust me it's kind of a pain in the ***.  But I have it installed because i've used it long enough that i'm not gonna delete it but for new users who can't commit it's great

---

### Post by sanderd17 on 2011-10-26
Wubi is useful for a long testing period (a few months). During that time, you have a quite complete user experience, you have the time to try things, and it's easy to uninstall if you don't like it.

This may not be used as a stable system because you mostly trust on a windows installation that sometimes isn't maintained anymore after installing Ubuntu.

---

### Post by munchlaxy on 2011-10-26
> **sanderd17 said:**
> Wubi is useful for a long testing period (a few months). During that time, you have a quite complete user experience, you have the time to try things, and it's easy to uninstall if you don't like it.

This may not be used as a stable system because you mostly trust on a windows installation that sometimes isn't maintained anymore after installing Ubuntu.


So if this is the case, WUBI's usefulness is limited to a few months because of these stability issues? Or can a person pretty safely use it for a much longer period of time?

I dual-boot, but have heard of people using WUBI for quite some time without thinking of switching. Is there any reason why a person would rather do this (assuming they only are using the partitions that came with the computer... if that makes sense).

---

### Post by kaldor on 2011-10-26
> **munchlaxy said:**
> So if this is the case, WUBI's usefulness is limited to a few months because of these stability issues? Or can a person pretty safely use it for a much longer period of time?

I dual-boot, but have heard of people using WUBI for quite some time without thinking of switching. Is there any reason why a person would rather do this (assuming they only are using the partitions that came with the computer... if that makes sense).

I used to use it on an older PC a few years ago. It was riddled with loads of weird issues that disappeared after a real install. I also remember getting a black screen on boot (on the Ubuntu side) after a Windows XP update which rendered it useless. Same sort of little quirks happened with a couple of other people I've talked to as well.

It also runs slow.

---

### Post by Paqman on 2011-10-26
Anything that lowers the bar of people's first experience with Linux is good.Most people have never partitioned a hard drive, which I think is something some Linux users forget because it's second nature to us. Wubi completely dodges the need to learn a new technical trick in order to get Linux installed, and is therefore supremely awesome. 

It's just a shame it'a not as stable as it should be, but given the complexity of what it's trying to achieve and the fact that it's (with the greatest of respect to the dude behind it) basically a giant hack, that's perhaps not unexpected.

---

### Post by beew on 2011-10-26
If you can get a hold on an old hard drive or an external hard drive the best way to "test" Ubuntu would be to do a full installation into the external drive. It is a "real" install in every way. Unlike live usb with persistence, you can do system updates and it is fast,--you get the real speed of Ubuntu except booting may take longer than an internal install. I have several Linux on an external hdd which I use  mainly to test new releases before I install them in my main computer. But I also have partitions for some stable releases and use the external hd as a portable installation, I plug  it into almost any computer and boot and instantly I have a Ubuntu or Fedora session.

WUBI is NOT dual boot, if your windows dies so does WUBI, that is not dual boot. Also installing WUBI puts "something" in Windows so it changes Windows, it is not testing Linux without changing Windows as advertised.

---

### Post by haqking on 2011-10-26
> **beew said:**
> 
**WUBI is NOT dual boot, if your windows dies so does WUBI, that is not dual boot.** Also installing WUBI puts "something" in Windows so it changes Windows, it is not testing Linux without changing Windows as advertised.


WUBI is dual boot because you can boot into more than one OS hence dual and boot, i do not disagree that losing windows loses your WUBI install but it is still dual boot, just not the same as a regular dual boot in a seperate partition

---

### Post by FuturePilot on 2011-10-26
From my experience going through the support forums there seems to be a lot of issues with Grub getting messed up and .dlls gone missing preventing Windows from booting.

---

### Post by beew on 2011-10-26
> **haqking said:**
> WUBI is dual boot because you can boot into more than one OS hence dual and boot, i do not disagree that losing windows loses your WUBI install but it is still dual boot, just not the same as a regular dual boot in a seperate partition

I think we are just arguing semantics, to me a dual boot means you can boot into both systems on equal footing, WUBI allows you to run a diminished version of Ubuntu, it lives in a WIndows folder, you can remove it from WIndows using Add/Remove but you can't get rid of Windows. It is limited in terms of size, speed and the file system it can use. 

So it maybe "dual booting", but not with full feature Ubuntu. It is also buggy, unstable and have strange problems that don't appear in normal install from the numerous WUBI thread, it actually gives Ubuntu a bad name IMO.

---

### Post by haqking on 2011-10-26
> **beew said:**
> I think we are just arguing semantics, to me a dual boot means you can boot into both systems on equal footing, WUBI allows you to run a diminished version of Ubuntu, it lives in a WIndows folder, you can remove it from WIndows using Add/Remove but you can't get rid of Windows. It is limited in terms of size, speed and the file system it can use. 

So it maybe "dual booting", but not with full feature Ubuntu. It is also buggy, unstable and have strange problems that don't appear in normal install from the numerous WUBI thread, it actually gives Ubuntu a bad name IMO.

I agree 100%, so semantics it was, i argued the semantics as you capitalised the "NOT dual boot" to make the point ;-)

Peace

---

### Post by RaganN on 2011-10-26
I used Wubi for six months on 11.04, and I am using now and have had no problems running Ubuntu once it was installed.  There are several reasons someone would want to use Wubi to dual boot.

Someone might not know or be comfortable with partitioning.

Someone might want an Ubuntu install that can be easily removed, for instance if they were just trying it out.

There might be a situation in which changing the partitions could negatively affect the computer (which is my case).

Mainly, it's a matter of partitioning, and Wubi allows for Ubuntu to be installed without affecting that.  I haven't had issues with Ubuntu on it, or noticed a difference between the Wubi version and the one on my other computer which is installed properly.  Other people's mileage might vary.  The main advantage of Wubi is that if something goes wrong, it's easy to get rid of...just uninstall from Windows.

---

### Post by SharkMonster on 2011-10-26
I feel it's decent for new users since it lets them use a distro with better performance than a LiveCD without any of the dangers of partitioning. So yes it is useful, IMO.

---

### Post by Frogs Hair on 2011-10-26
I started with Wubi 9.10 and know 3 people that have been using it to test the latest Ubuntu versions since 10.04 . Not one of them has reported any problems , but they all use Windows as there main operating and maintain it well . 

The only thing I suggest to them is to defrag after removal an wipe the Windows partition free space before installing the next release .

---

### Post by sffvba[e0rt on 2011-10-26
Thanks to WUBI our LoCo got 30 curious students to try out Ubuntu on there machines.


404

---

### Post by critin on 2011-10-26
I really appreciate Wubi because I installed my first ubuntu 7? with it and couldn't have without it.  I knew nothing about partitions and just thinking of the word scared me.  I used it until after upgrading through Wubi to 9.04?.  I didn't have any problems and didn't know I was using a 'temporary' program--it worked.

But---I learned nothing about ubuntu/linux.  Wubi never gave me any problems so I didn't have to fix anything.  I let it do all my thinking and went happily along working on my documents until the computer finally quit. 

After a while I read up on it and decided to try installing a side-by-side with windows.  I was surprised that I could, and that began a journey that I'm still on of learning.  If I was still using Wubi I wouldn't learn anything--that's the bad side of using it. (for me)  I'm so glad the comp quit and I was free to try ubuntu for real.  Now I have a comp completely dedicated to linux distros only, and it's the one I use though I have a windows right here behind it.

There's a time for Wubi's usefulness, and a time to grow out of it.

---

