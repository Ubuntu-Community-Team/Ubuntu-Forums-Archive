---
title: "Why is it so flaky??"
date: 2010-06-22
forum: Testimonials &amp; Experiences
---

### Post by tosh124 on 2010-06-22
Hi all,
I thought I would give Ubuntu a try on an old machine as it was just too slow on windows. It ran ok for a few days before requiring a disk scan  at every boot! Not good!
It does dual boot with windows but that shouldn't really cause a problem.

Anyway I perserved and put it onto a dual core laptop dual booted with Vista, same again, constant disk scans. I put this down to it still being buggy, but as it was faster left it on.
6-8 weeks in, 4 crashes (put into debug mode to fix it) and now a permanent crash needing a full checkdisk and yet you just cannot access it.

I have to say, windows is slow & also flaky, but at least it is reliable and lasts longer than 2 months!
In the meantime I will go back to windows as I simply cannot be bothered with constant crashes (on both machines!). It is a shame as it shows promise, but until the bugs are sorted it just isn't worth the time. 
Rant over! ](*,)

Have fun and keep developing, otherwise MS really will take over the world!

---

### Post by dabl on 2010-06-22
It's odd that my Kubuntu 10.04 has been running stably since I installed it in late March, as Alpha 3.  I wonder why it doesn't scan the disks and crash all the time?   :confused:

---

### Post by Mark Phelps on 2010-06-22
Sorry to hear about your problems, but in general, Ubuntu is not "flakey", but since Canonical doesn't have the deep pockets that MS has, they can only test the releases on a limited set of configurations.

You could be one of the unlucky ones that has a hardware combination that Ubuntu just doesn't handle well.  There are boot options, and kernel parameters, that can often be added that work around the hardware problems ... but you have to post your problems and work with folks individually to get them fixed.

Regarding instability, there is nothing inherent in dual-boot systems ("true" dual-boot in which each OS has its own dedicated partitions; not Wubi, in which the Ubuntu "partition" is actually inside the MS Windows OS partition) that renders them unstable -- unless you make the mistake of automounting your MS Windows OS partition inside Ubuntu.  One unclean shutdown and you won't be able to boot MS Windows anymore.

You didn't mention it, but in future, you should try the LiveCD mode first.  Any showstopper hardware/driver issues will show up in that scenario -- without changing anything on your machines.

---

### Post by tosh124 on 2010-06-22
> **Mark Phelps said:**
> Sorry to hear about your problems, but in general, Ubuntu is not "flakey", but since Canonical doesn't have the deep pockets that MS has, they can only test the releases on a limited set of configurations.

You could be one of the unlucky ones that has a hardware combination that Ubuntu just doesn't handle well.  There are boot options, and kernel parameters, that can often be added that work around the hardware problems ... but you have to post your problems and work with folks individually to get them fixed.

Regarding instability, there is nothing inherent in dual-boot systems ("true" dual-boot in which each OS has its own dedicated partitions; not Wubi, in which the Ubuntu "partition" is actually inside the MS Windows OS partition) that renders them unstable -- unless you make the mistake of automounting your MS Windows OS partition inside Ubuntu.  One unclean shutdown and you won't be able to boot MS Windows anymore.

You didn't mention it, but in future, you should try the LiveCD mode first.  Any showstopper hardware/driver issues will show up in that scenario -- without changing anything on your machines.

Not your fault mate, just one of those things. I did try the live CD first on both machines, without any issues other graphics card, drivers loaded and fine.

The systems are dual boot with a shared data parition so all is not lost. As regards the fixes, TBH I don't have the time or patience at the moment. I will try another flavour of linux tho as overall I am impressed with it and want to move away from windows to something that isn't as resource hungry and (hopefully) more stable. 
Any recommendations?
It is a shame about the lack of deep pockets, but having watched Linux develop over the years I still feel that it can become a viable alternative to MS. For the average user it is generally OK, just that I'm not an average user :) 
thanks for the replies everyone.
Oh and thanks for spelling correction, I thought it didn't look right  ;)

---

### Post by mkvnmtr on 2010-06-22
I believe the default is a disk scan after 30 boots. When my systems do scans out of that cycle it is because I have a problem that is not software related such as a hard drive problem. Or maybe a power failure.Might be a good idea to read the logs.

---

### Post by koenn on 2010-06-22
> **tosh124 said:**
>  I will go back to windows ... until the bugs are sorted it just isn't worth the time. 

ok, bye.

---

### Post by mojota on 2010-06-22
Welcome to the forums, 

I know what you mean by wanting something lighter than Windows to run on a laptop, we have a Vista laptop in the family and it feels clanky right from the word boot. lol

Luckily I have a couple of Macs where one being dual booted with Xfce, I opted for Xfce a long time ago because I like the panel and how customisable it is.

---

### Post by steveneddy on 2010-06-22
First of all I believe this belongs in Testimonials IMHO.

I, as most of us around here, have run Ubuntu very successfully from the very first release over five years ago.

Your issue could have something to do with not enough memory or other hardware compatibility issues.

Try it on supported hardware and you will be surprised what Ubuntu can do - especially when comparing it to a Windows operating system.

Sorry about your troubles. Better luck next time.

---

### Post by Timmer1240 on 2010-06-22
Funny mine runs like a bullet stable as hell after 5 months running 24-7 I never shut it down runs great!

---

### Post by Timmer1240 on 2010-06-22
sounds like a hardware problem being vista is flacky too!

---

### Post by K.Mandla on 2010-06-22
Let's let this one live out its life in Testimonials and Experiences.

---

### Post by WinterRain on 2010-06-22
> **steveneddy said:**
> 

I, as most of us around here, have run Ubuntu very successfully from the very first release over five years ago.


Me too. Ubuntu is much more stable than windows ever was.

---

### Post by Timmer1240 on 2010-06-22
I just love how people join the forum just to rant about how ubuntu is no good and ya da ya da ya da!Go back I banish you back to Windowsville where viruses are a plenty and blue screen of death is the desktop wallpaper!:lolflag:

---

### Post by tosh124 on 2010-06-23
> **Timmer1240 said:**
> I just love how people join the forum just to rant about how ubuntu is no good and ya da ya da ya da!Go back I banish you back to Windowsville where viruses are a plenty and blue screen of death is the desktop wallpaper!:lolflag:
Viruses? Nah only ever had one in 12 yrs
Blue screen of death? Hmm don't recall the last time :)

Come now, I'm sure you can do better than that ;)

---

### Post by tosh124 on 2010-06-23
> **Timmer1240 said:**
> sounds like a hardware problem being vista is flacky too!

Vista isn't flakey, just sooo slow.
I put originally dual boot Vista & Win7, but W7 didnt like being dual booted :confused:

But thats windows for ya.

---

### Post by kimda on 2010-06-24
Have you looked into your logs what might be the problem? Also you can test your disks with the diskutility System > Administration > Diskutility. It will test on startup the smart data of your disk(s). In the option smartdata you can do an disk test.

---

### Post by tosh124 on 2010-06-24
> **kimda said:**
> Have you looked into your logs what might be the problem? Also you can test your disks with the diskutility System > Administration > Diskutility. It will test on startup the smart data of your disk(s). In the option smartdata you can do an disk test.
Sadly I cannot get into the system to do anything. It does a disk check then tells me I there is an error it cannot fix and I must do it manually :)

---

### Post by kimda on 2010-06-24
Can you execute commands as root? Usually when this happens it will start a root terminal. Then you can issue the fsck command to check the disk manually. ex. fsck.ext4 /dev/sda1  or fsck.ext3 /dev/sda1 (use first command to check ext4 file system and second if it is a ext3 file system). Also you need to change /dev/sda1 into the partition which isn't getting checked.

---

### Post by WinterRain on 2010-06-24
> **tosh124 said:**
> Viruses? Nah only ever had one in 12 yrs
Blue screen of death? Hmm don't recall the last time :)

Come now, I'm sure you can do better than that ;)

Want better? How about the fact that millions of people DO get viruses and blue screens of death. I love it when 1 out of a million windows users come in here and say "I never have viruses or problems". If your experience with windows was typical, 1000's of pc techs would be out of work. (like me)

---

### Post by tosh124 on 2010-06-24
> **WinterRain said:**
> Want better? How about the fact that millions of people DO get viruses and blue screens of death. I love it when 1 out of a million windows users come in here and say "I never have viruses or problems". If your experience with windows was typical, 1000's of pc techs would be out of work. (like me)

I agree millions of people do, but there are more than 1 in a million users who dont experience it. Likewise I love it when Linux boffins claim that their system is so fantastic they NEVER have problems ;)

When I was doing my IT degree there was such a guy, and  yet he was forever tinkering & rebuilding the box :)

Blue screen of death isnt a really problem since Vista, but viruses just take a little care to avoid
 
It could be that I am pc tech therefore my networks & I dont have those kinda problems :)
Admittedly I am a windows techie and this is my first proper forray into linux simply because windows is sooo slow and everything connected with it is megabucks.

---

### Post by tosh124 on 2010-06-24
> **kimda said:**
> Can you execute commands as root? Usually when this happens it will start a root terminal. Then you can issue the fsck command to check the disk manually. ex. fsck.ext4 /dev/sda1  or fsck.ext3 /dev/sda1 (use first command to check ext4 file system and second if it is a ext3 file system). Also you need to change /dev/sda1 into the partition which isn't getting checked.

I can get into the root terminal, but TBH havent got as far as working thru the proper commands to move it on. I wont be able to do that until the weekend as I am pretty busy at the mo. 
I think I set the file system to ext2, so I will test it at the weekend. Thanks for the syntax, much appreciated.

---

### Post by tosh124 on 2010-06-24
Actually all, are there any lighter, more robust flavours of linux. I'm considering trying Mint and see how that works on my hardware.
What are your thoughts anyone?

---

### Post by Linuxforall on 2010-06-24
WOW! Ubuntu is so flaky that it runs here for years before it gets updated with a newer version, thats the LTS. OTOH, Windows needs a format and install every six months or less.

---

### Post by tosh124 on 2010-06-24
> **Linuxforall said:**
> WOW! Ubuntu is so flaky that it runs here for years before it gets updated with a newer version, thats the LTS. OTOH, Windows needs a format and install every six months or less.

:lolflag:   I've been waiting for that old chestnut & I do mean OLD chestnut.

---

### Post by kimda on 2010-06-24
> **tosh124 said:**
> I can get into the root terminal, but TBH havent got as far as working thru the proper commands to move it on. I wont be able to do that until the weekend as I am pretty busy at the mo. 
I think I set the file system to ext2, so I will test it at the weekend. Thanks for the syntax, much appreciated.
ext2 has no journaling. I hope you are mistaken that you set the file system to ext2, because in case of filesystem errors it won't be able to get information out of the journals like ext3 and ext4 can.

---

### Post by tosh124 on 2010-06-24
That could be an issue then as I am fairly sure that is the one I picked. What is the difference between them?
TBH if it doesn't work then I will do a re-install. It isnt really a problem as it is a dual boot machine. How do you edit the boot (grub?) loader? I'm a little wary that it will cause a problem with the current boot loader pointing to a partition that doesnt work...
thanks again

---

### Post by kimda on 2010-06-24
There's a big difference between them. 
Here's some info on ext3 and ext4.

[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)
[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

On my systems I made a seperate partition for /boot, / and /home. And all partitions are ext4. And I made only /boot ext3 because there were some issues with that. Ext4 has better performance and other features. You will probably notice a difference in filesystem speed when using ext4 if you are used to ext2.

---

### Post by kimda on 2010-06-24
I would go for a new install. Because you would first have to check all your disks and then convert them to ext3 and/or ext4.

---

### Post by kimda on 2010-06-24
Maybe you can get data of the current disks by starting with an live cd and mounting the partitions and copying this to an external disk or another machine.

---

### Post by Elfy on 2010-06-24
This is not the place for support.

If the OP needs support then I suggest they start a second thread - as the first was this one.

Thread closed.

---

