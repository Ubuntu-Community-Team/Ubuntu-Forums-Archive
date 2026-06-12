---
title: "FreeNas / ZFS / ubuntu server question"
date: 2013-10-07
forum: Server Platforms
---

### Post by Borg_1Twenty3 on 2013-10-07
I am running a few cloud servers that are running ubuntu server 13.x 

At home I'm running a 15 TB FreeNas 9.x server with ZFS in a Raid Z1 configuration (5 drives + 1 auto hot spare)
My question is if i wanted to switch from FreeNas to Ubuntu can i do this without losing any data?
I know about "exporting" my ZFS pool. (limited knowledge about it)

If i install an SSD in my server, install unbuntu 13 server on it, can i then "re-import" my ZFS pools?

My initial google searches didn't yield much information.

any help is appreciated.
Thanks!

---

### Post by mastablasta on 2013-10-08
if freenas works why do you need to switch to Ubutnu? moreover why to Ubuntu 13.04 (i presume) which support runs out in January next year. why not install 12.04 supported until April 2017?

: [https://wiki.ubuntu.com/ZFS](https://wiki.ubuntu.com/ZFS)

---

### Post by Borg_1Twenty3 on 2013-10-08
> **mastablasta said:**
> if freenas works why do you need to switch to Ubutnu? moreover why to Ubuntu 13.04 (i presume) which support runs out in January next year. why not install 12.04 supported until April 2017?

: [https://wiki.ubuntu.com/ZFS](https://wiki.ubuntu.com/ZFS)

Thank you for the reply.
well the reason is I only have 1 server. FreeNas is working great as a file storage system. However I wanted to run more stuff on it than just a file server.
There is a couple of plugin's that run. but it seems to me there is much more out there for linux/ubuntu than for freenas/bsd
at least easily installed through a package. 
So i thought about switching, but i have allot of data and don't want to risk losing it.

If you don't mind. could you help me understand the support model? I get what LTS means. but why would they stop supporting a newer version?
I assume there will be something after 13.04 in which case wouldn't everyone just upgrade to that? I'm not sure I understand the model very well.

---

### Post by DuckHook on 2013-10-08
> **Borg_1Twenty3 said:**
> ...help me understand the support model? ...why would they stop supporting a newer version?The Ubuntu support model is actually quite simple:

Every even-numbered year (2012, 2014, 2016...) the April release (hence the .04) is a Long Term Support (LTS), meaning that Ubuntu will commit to supporting it for five years. All other releases will only be supported for 18 months.

Canonical has limited resources like any other company. And since very few people pay for Ubuntu, Canonical cannot commit to supporting every release for an extended period. On the other hand, Linux evolves so quickly that Canonical must release more often than just once every two years. Therefore, the best compromise is to release twice a year, but provide LTS only every fourth release.

Experimenters and the eager-beaver crowd tend to install new versions as soon as they are available. It is true that these releases tend to have the latest and greatest on them. On the other hand, stodgy, boring types tend to stick to the LTSes because they are more stable and the better choice for mission-critical boxes (like servers) that don't need the latest bells and whistles anyway.

Summary:

LTS: Pros=stability, 5-year support, lots of help on forums, large installed base. Cons=missing functionality, increasing obsolescense, yesterday's stuff.

Non-LTS: Pros=latest & greatest, newest drivers, most current apps, bug fixes. Cons=support is short-term, committed to upgrade treadmill, less stability.

---

### Post by DuckHook on 2013-10-08
> **Borg_1Twenty3 said:**
> ...it seems to me there is much more out there for linux/ubuntu than for freenas/bsd
at least easily installed through a package.Actually, there's more out there for FreeBSD than most people think. It's a heavily supported OS with a significant geek/hacker culture of its own, which is a good thing when it comes to supporting/maintaining/evolving the OS. And the packaging system is not hard once you get the hang of it. If you want a BSD distro that is easy on beginners, check out PC-BSD which is just FreeBSD with a friendly DE and an easy-to-use package manager.

However, there is also no question that Linux has usurped the hacker throne that at one time looked like belonging to BSD. There are many more hackers working on Linux than BSD, so the sheer numbers alone push Linux along at a faster clip than any of the Unixes. And because there are also more average desktop users in Linux-space, this creates a demand for more user-friendly apps, utilities and services. You are correct in concluding the greater ease of use, ease of getting help, etc.> ...i have allot of data and don't want to risk losing it.That's what backups are for. ;)

Seriously, don't count on any tool that allows you to simply migrate from one OS to a completely different OS. Linux and BSD may superficially look similar, but that is only because they share many of the same open-source surface treatments. Underneath, they are completely different operating systems. I've never heard of any simple migration tool. If others have, perhaps they can jump in here.

---

### Post by Borg_1Twenty3 on 2013-10-08
> **DuckHook said:**
> The Ubuntu support model is actually quite simple:

Every even-numbered year (2012, 2014, 2016...) the April release (hence the .04) is a Long Term Support (LTS), meaning that Ubuntu will commit to supporting it for five years. All other releases will only be supported for 18 months.

Canonical has limited resources like any other company. And since very few people pay for Ubuntu, Canonical cannot commit to supporting every release for an extended period. On the other hand, Linux evolves so quickly that Canonical must release more often than just once every two years. Therefore, the best compromise is to release twice a year, but provide LTS only every fourth release.

Experimenters and the eager-beaver crowd tend to install new versions as soon as they are available. It is true that these releases tend to have the latest and greatest on them. On the other hand, stodgy, boring types tend to stick to the LTSes because they are more stable and the better choice for mission-critical boxes (like servers) that don't need the latest bells and whistles anyway.

Summary:

LTS: Pros=stability, 5-year support, lots of help on forums, large installed base. Cons=missing functionality, increasing obsolescense, yesterday's stuff.

Non-LTS: Pros=latest & greatest, newest drivers, most current apps, bug fixes. Cons=support is short-term, committed to upgrade treadmill, less stability.

And that's about what i expected. but the previous person asked why i would use 13.04, as if to say it was a bad idea because support would be ending. support isn't really an issue. I would just upgrade to whatever version comes out next. but i wanted to make sure i understood what exactly was being talked about. thanks for the explanation.

---

### Post by DuckHook on 2013-10-08
Final note:

Upgrading is not a painless exercise. While many here have reported easy upgrades, my experience has been a mixed bag. It's when upgrading *doesn't* go hunky-dory that you wonder why you didn't just stick with a LTS release. I believe that is what *mastablasta* was referring to. Similar thinking behind his asking why you wanted to switch from FreeBSD... the "if it ain't broken, don't fix it" philosophy.

---

### Post by Borg_1Twenty3 on 2013-10-08
> **DuckHook said:**
> Actually, there's more out there for FreeBSD than most people think. It's a heavily supported OS with a significant geek/hacker culture of its own, which is a good thing when it comes to supporting/maintaining/evolving the OS. And the packaging system is not hard once you get the hang of it. If you want a BSD distro that is easy on beginners, check out PC-BSD which is just FreeBSD with a friendly DE and an easy-to-use package manager.

However, there is also no question that Linux has usurped the hacker throne that at one time looked like belonging to BSD. There are many more hackers working on Linux than BSD, so the sheer numbers alone push Linux along at a faster clip than any of the Unixes. And because there are also more average desktop users in Linux-space, this creates a demand for more user-friendly apps, utilities and services. You are correct in concluding the greater ease of use, ease of getting help, etc.That's what backups are for. ;)

Seriously, don't count on any tool that allows you to simply migrate from one OS to a completely different OS. Linux and BSD may superficially look similar, but that is only because they share many of the same open-source surface treatments. Underneath, they are completely different operating systems. I've never heard of any simple migration tool. If others have, perhaps they can jump in here.

for FreeNas there is about 6 or 7 semi-official plugins. ultimately i'm looking for just easy mgmt. I don't care to spend a million hours figure out why something isn't working. I've followed some thread of guys trying to get something working and it can be a headache.  

To be clear i'm not looking for a migration tool. I'm asking if i install ubuntu on a fresh SSD drive, and install the ZFS package, can i then "import" my pools from freenas and have all my data be available?
I don't want to have to re-do everything just to switch OS. If i'm looking at this situation correctly. my NAS drives are basically just "external" storage. which should be able to be plugged in to about any OS that supports the partition types.. in this case i'm using ZFS and since Ubuntu will support ZFS. i'm hoping to export the pool and then re-import.
but i don't have any room for trial and error. I was hoping to get the advise of someone who's done it before.  
appreciate the reply's to my question though.

---

### Post by DuckHook on 2013-10-08
> **Borg_1Twenty3 said:**
> I was hoping to get the advise of someone who's done it before.Then this precludes any further advice from me. The only RAID I run is software LVM-based.

Just a few thoughts though, from other threads and from lurking around these forums in general:

Unless you have a real HW RAID controller, don't count on Linux being able to instantly recognize and/or work with your RAID controller. Many RAID controllers are actually FAKERAID, offloading so much of their RAID functions to software that they become highly driver-dependent. That's where a lot of people trip up trying to easily migrate from, say, Windows to Linux. They assume that their RAID will work as seamlessly in Linux as it did in Windows, then discover that no Linux driver exists for their controller, thus rendering considerations of filesystem compatibility, etc academic.

To get the help you are looking for:

1. Post in the "Server Platforms" subforum where the real gurus hang out. This present forum is called "Absolute Beginners" for good reason.

2. Include exhaustive details of your system HW when you do post there, esp make/model/firmware of your RAID controller. Otherwise, you will be wasting time.

3. Tell them exactly what your plan of attack is. You will attract more responses if you've shown yourself to have already done some research and at least taken a stab at a solution.

---

### Post by CharlesA on 2013-10-08
Moved to Server Platforms. ;)

I've only used mdadm and my MegaRAID card, so  I don't really have much to add, but at least it's in the right area now.

---

### Post by tgalati4 on 2013-10-08
Understand that there are several versions of ZFS.  Your freenas install supports one version of ZFS.  Ubuntu's ZFS support may be a different version--and that version may change depending on what version of Ubuntu you end up choosing.  So, in theory, if the ZFS versions are the same, then Ubuntu will recognize the zpools without any effort on your part.  In practice, you may not have access to your data and you may end up screwing up the zpools beyond recognition.

If you use Ubuntu, you might as well just stick with ext4 and use a soft RAID which will be better supported than ZFS.  If you need ZFS's features, then stick with freenas and add modules to add functionality.  You can almost get a complete BSD system by adding plug-ins.  It's not as easy to maintain or update as an Ubuntu system, but then you want uptime, so you won't be updating that often.

---

### Post by Borg_1Twenty3 on 2013-10-09
Thanks for all the responses. I guess I'll have to think about doing this. probably i'll end up sticking with freenas and then throw together a cheap lowend pc for ubuntu. but I was trying to be green and all by not having to run 2 machines 24/7
but i'll use it as an excuse to buy some new toys :)

---

### Post by tgalati4 on 2013-10-10
Set the Ubuntu machine to wake-on-lan and put launchers on every device that needs to access it--phones, tablets, laptops, desktops, etc.  I have several machines set up this way.  They stay asleep until I need something from them.  Do some searching on freenas extensibility--you can load most open-source services on freenas, you just have to find the port and load it.

---

### Post by CharlesA on 2013-10-10
> **tgalati4 said:**
> Set the Ubuntu machine to wake-on-lan and put launchers on every device that needs to access it--phones, tablets, laptops, desktops, etc.  I have several machines set up this way.  They stay asleep until I need something from them.  Do some searching on freenas extensibility--you can load most open-source services on freenas, you just have to find the port and load it.

Just giving WoL a +1. I use it to wake up my backup server so it isn't running all the time.

---

### Post by lavender.t on 2014-08-07
Hi [[COLOR=#000000]Borg_1Twenty3[/COLOR]]("http://ubuntuforums.org/member.php?u=1868556"), did you try ZFS/Ubuntu could use the FreeNas pool ?

---

