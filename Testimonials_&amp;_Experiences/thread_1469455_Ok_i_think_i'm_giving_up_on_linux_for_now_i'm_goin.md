---
title: "Ok i think i'm giving up on linux for now i'm going back to windows 7"
date: 2010-05-02
forum: Testimonials &amp; Experiences
---

### Post by aviramof on 2010-05-02
There are just too many problem with this os for my taste all i did today was to try this simple guide:
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)
 
And it crashed my ubuntu again and caused me a lot of problems.
 
After booting i got nothing no grub 2 no nothing so i said let's reinstall grub 2 i entered the live dvd i 
use which by the way takes a long time to load and i used the commands i always use to install grub 2
(by the way even after format and clean install of final version i was force to use this command):
 
 
```

sudo mount /dev/sdb2 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo chroot /mnt

```
 
```

sudo grub-install /dev/sda

```
 
```

sudo grub-install /dev/sdb

```
 
```

exit

```
 
```

sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt

```
 
It didn't worked so i said let's remove grub 2 the way i usally do with windows 7/server 2008 cd using command prompt 
and bootrec.exe /fixboot bootre.exe /fixmbr. So i did it and then tried to reinstall grub 2 and again it didn't worked and so 
i used the windows 7/server 2008 cd removed grub 2 again and that it. The problem is that now i need to reinstall daz's loader
in windows 7 and in server 2008 because the bootrec.exe commands also remove the loader from bote OS'S.
 
And as for linux ubutnu 10.04 i grew tierd of it she's too bugy all you need to do is to 
add the wrong ppa or download the wrong package or do even the smallest wrong thing and it crash.
 
Further more except compiz i didn't see any thing uniq there the reposetories are nice but also a source of trobule.
There is no auto arrange,there are only few sorting option in nautilus and other files managers,there are problems 
with ati drivers,there are problems with plymouth not working with kmps or what ever it's called.
 
There are numberous unsolved and old bugs in launchpad that were never checked.
There are still RTL problems even in official ubuntu let along xunbunt,lubuntu and kubuntu. 
 
there are problems of installing higer kernels because fglrx don't support them and the script i found don't install 0ubuntu3 
version of fglrx only 0ubuntu1 version that is not so good version.
 
Even compiz is now not updated completly to work with lucid not all the pacages are already build.
 
as for networking the network manager or pppoeconf don't work so well i had to set my modem to be router to bypase ubuntu problems. 
When in windows i never had any problems with that so basicly as i see it after months of using it ubuntu is an incredibley buggy system 
and i can't continue using it anymore.
 
When i first started using this OS i thought microsoft have problems but now i know a lot better.
 
So goodbye and i'm hopping that one day you would be able to fix all this problem and make ubuntu a much 
more stable and worthy OS then she is now and as she can be.

---

### Post by chriswyatt on 2010-05-02
Why not give an older version of Ubuntu a go?

Karmic's been out for 6 months, and when I had it I found it extremely stable.

I'm having no problems with the official version of Lucid so far.  Well, except for a VirtualBox issue but I don't know if it's to do with Karmic, Windows or VirtualBox.

---

### Post by CharlesA on 2010-05-02
Use what works for you.

---

### Post by JDShu on 2010-05-02
Sure.

---

### Post by aviramof on 2010-05-02
When i tested Karmic's i was still using pppoeconf to connect and it didn't worked in 9.04 and 9.10 at all. 
 
And i don't see that 10.04 is better even final ubiquity can't install grub 2 properly on my computer, let along the problem i had with ubuntu itself.

---

### Post by AlexEagar on 2010-05-02
Encountering bugs is definitely discouraging. If you still want to get Linux working, [here is a list of the top ten Linux distributions]("http://distrowatch.com/dwres.php?resource=major"). They're all great distributions. I'm sure you can find one that meets your needs without too much trouble by trying them out based on your impression of them after reading their descriptions. I wish the best of luck with whichever operating system(s) and distribution you decide to use.

---

### Post by Ad@m on 2010-05-02
> **AlexEagar said:**
> Encountering bugs is definitely discouraging. If you still want to get Linux working, [here is a list of the top ten Linux distributions]("http://distrowatch.com/dwres.php?resource=major"). They're all great distributions.

Emphasis on top 10* "popular" *distributions.

 Fedora is a testing platform for RedHat to try the latest innovations and to help further develop their commercial product.

Is it great, well that is debatable but being often referred to as a bleeding edge distribution it is also a potentially unstable and unreliable distribution.

I have on a few occasions and recently with F12 performed an update which killed the system.

Simple tasks can also be hindered by the latest innovations, when F12 was released installing the nvidia proprietary driver required additional steps.

Disabling the nouveau driver, changing the SE Linux policy.....

Quite a few people were caught out by this and ended up with a blank screen and the additional misery of recovering their system.

Hence when using such a distribution, you have to pay that little bit of extra attention to the documentation.

---

### Post by aviramof on 2010-05-02
You need to understand that i used 10.04 since it alpah state and now in the final version i don't see that things have changed dramaticly as i hopped even grub 2 
don't install itself automaticly and i need to install it automatcily and the install process 
thakes like 40 minutes 25 only on the dpkg at the end and another five just on the restart button so it's not very impressing as far as i see it.
 
and you can't install higher kernels because fglrx don't support it.
 
and networking even bacme worse at the begining when i used pppoeconf it did not auto load pppd and connect automaticly i needed to use sudo pon dsl-provider for this
and network manager didn't worked in the end they bote worked but i guess there is some tcp ip limit or other security protocol because it killed all my P2P sotwares so i had to 
set my modem as router and bypase linux completly.
 
And my web camera and motorola phone is not recognize.
 
and what about plymouth and ati/nvidia drivers? how can you call it final version when it doesn't work properly yet?
 
Basicly a lot a lot of problems that were not solved in the "final" version.

---

### Post by Paulplex on 2010-05-02
> **aviramof said:**
> There are just too many problem with this os for my taste Afternoon,

Different, sure: but although I'm still very amateur with Linux, having applied myself over the past few months since 9.10, I'm quite confident with tweaking things and managing software through the desktop and shell.

Each to their own of course, but although I'll admit there are a few bugs I've found with Ubuntu 10.04, the same is true of Windows XP, Vista or even Windows 7 when they were first released.

I'm more than happy with Linux now myself and although I keep Windows XP to hand through a VirtualBox guest operating system, I don't see myself going back to Windows anytime soon.

Aviramof, although 10.04 is working generally as I need it to, try Ubuntu 9.10 since that was certainly quite stable for me: go back to Windows if you have to but although I respect the charity work of Bill Gates, I don't personally want to give Microsoft any more of my money when there's better out there for free :P

---

### Post by aviramof on 2010-05-02
Who said i ever paid bill a signle buck?
 
My big problem with ubuntu 10.04 lucid is that every slightly advance thing i try like the guide in the top of thread or just adding ppa's and etc can crash the system like nothing.
 
For instance teleplay ppa erase everything for me from nautilus-send-to at the top panel and webupt8 or what ever it's called vlc ppa made my mkv movies not to work properly.
 
And samba for a long time never worked for me propelry and i had countless permissions problems and grub 2 and ubiquity and plymouth and fglrx and what not with almost every package that is not something like gimp i had problems and i grew tierd of that fact i think i formated and reinstlled ubuntu like 20 to 30 times in the last few months i never needed to that with microsoft os's ever.
 
In microsoft os's there are so many options in ubuntu i can't even download files to 
the desktop or create shortcuts to sites without the files to pile up one on top of the other.
 
I had to talk to a firefox extenssions developer to add support to ubuntu to it savelink addon because ubuntu don't have url files support.
 
And countless other things that i mentioned before and i don't have time to go over them now but you can find by doing search on my nickname here and in launchpad and bugzilla and etc.

---

### Post by Tamlynmac on 2010-05-02
> aviramof

Thanks for sharing and since this isn't a debating section of the forum, I will not comment on your opinions.

But rather wish you the best with which ever OS meets your needs and expectations. I think it's been said many times in this forum "Use what works for you".

Good Luck

---

### Post by uRock on 2010-05-02
Lucid hasn't crashed on me since Alpha testing. I am no pro nor genius with Ubuntu, but it works for me. You should install an older version. Hardy may be dated, but it is rock solid and you will be able to upgrade it when it gets to the end of its support cycle. 

No auto arrange? I think you need to try going into properties from within an open nautilus session. You can select how you want everything organized with just a few clicks.

Explore computer. Almost every program has a properties menu that can be customized to change the looks and actions of the program.

If your machine isn't compatible with Linux, then by all means use what it was built for.

I wish people wouldn't bash ubuntu on their way out of the door. The ubuntu devs can't design the OS to work on every model of every brand out there.

---

### Post by Elfy on 2010-05-02
Everyone is welcome to their choice - I really can't see any need for this to go on any longer as all the points the OP has made were also made in their threads in the Lucid development forum.

Good luck with whatever OS you use.

---

