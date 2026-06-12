---
title: "Help for newbie with some basic questions about Ubuntu"
date: 2018-12-31
forum: Ubuntu, Linux and OS Chat
---

### Post by kibiras on 2018-12-31
Hello. I think I should start in that case I'm 10+yrs Windows (now Windows 10) user. And you know, it's terrible :). I mean I'm not a developer, but that updates, gliches and all other stuff.... just enough for me. In future I'm thinkin to buy mac, but for now I want to try Ubuntu. And many friends just scary me "uuuhhh, ubuntu is not for basic users", "uuuuhhh on ubuntu you can't install programs and other staff", "uuhhh ubuntu is hard OS". So what is the true? What I need is youtube, facebook, torrents, video player and google drive. How about that? And is it true there is no programs for Ubuntu?

Ubuntu just look safe for me and stabile. Thats why I want to try it.

Please, help me with that :).

P.S. and what is Ubuntu **LTS**? I mean LTS have long term support? But then what is the point to install non LTS version? :)

---

### Post by CatKiller on 2018-12-31
There are plenty of programs available of the types you listed. 

> **kibiras said:**
> P.S. and what is Ubuntu **LTS**? I mean LTS have long term support? But then what is the point to install non LTS version? :)

The LTS versions get security updates, bug fixes, and browser updates, but everything else stays at the same version. You'd use the interim versions if you really need the latest versions of things, or if you want to help with testing. New users should stay with LTS versions.

---

### Post by kibiras on 2018-12-31
> **CatKiller said:**
> There are plenty of programs available of the types you listed. 



The LTS versions get security updates, bug fixes, and browser updates, but everything else stays at the same version. You'd use the interim versions if you really need the latest versions of things, or if you want to help with testing. New users should stay with LTS versions.

So I just need to start using Ubuntu with no questions? :)
And how about installing? Becouse I have one SSD and one HDD :)

---

### Post by CatKiller on 2018-12-31
> **kibiras said:**
> So I just need to start using Ubuntu with no questions? :)

Yep ;) 

Use the live environment for a while to get a feel for it and make sure that everything works. You *might* hate it: no need to rush in. 

> And how about installing? Becouse I have one SSD and one HDD :)

When you've decided that you'd like to install, it's easy enough. You can install alongside Windows as a dual-boot if you like. Install generally takes somewhere between 10 and 30 minutes, depending on your hardware and the options you choose.

---

### Post by kibiras on 2018-12-31
> **CatKiller said:**
> When you've decided that you'd like to install, it's easy enough. You can install alongside Windows as a dual-boot if you like. Install generally takes somewhere between 10 and 30 minutes, depending on your hardware and the options you choose.

Well I want to have a clean install. And I need to install it from USB FLASH DRIVE, but when I search youtube how to do it, it looks not so easy :O.

I think it should be the same like other OS? Create a bootable flash drive with rufus, then restart PC and select boot from flash drive and thats all? I'll get options in which SSD or HDD to install, format and etc? :).

Sorry for noob questions.

---

### Post by CatKiller on 2018-12-31
I'm not familiar with Windows tools, but yes, that's the gist. Make a bootable drive from the image that you download, and boot into it.

You'll be in the same sort of environment that you'll have after you've installed, so you can do whatever to see that it all works. The installer just asks some questions, and can download updates in parallel with the installation.

---

### Post by kibiras on 2018-12-31
> **CatKiller said:**
> I'm not familiar with Windows tools, but yes, that's the gist. Make a bootable drive from the image that you download, and boot into it.

You'll be in the same sort of environment that you'll have after you've installed, so you can do whatever to see that it all works. The installer just asks some questions, and can download updates in parallel with the installation.

Well okay.... When I will be at home after some days I'll try. I hope everything will be fine :D. Thank you for your help :).

---

### Post by CatKiller on 2018-12-31
No problem. I hope you enjoy it :)

We're here to answer any specific questions you might have after you've played around with it for a bit.

---

### Post by kibiras on 2018-12-31
> **CatKiller said:**
> No problem. I hope you enjoy it :)

We're here to answer any specific questions you might have after you've played around with it for a bit.

Well it's nice to find friendly community :).

---

### Post by CatKiller on 2018-12-31
> **kibiras said:**
> Becouse I have one SSD and one HDD :)

With regard to this bit in particular, if you're just having Ubuntu on the computer, installing to the SSD and having the HDD as your /home will work well. /home is for user settings and data.

---

### Post by kibiras on 2018-12-31
> **CatKiller said:**
> With regard to this bit in particular, if you're just having Ubuntu on the computer, installing to the SSD and having the HDD as your /home will work well. /home is for user settings and data.

Sorry, my english a little bit bad :). You mean I can install Ubuntu in SSD use both of them, SSD and HDD. Like SSD for programs and HDD for files, right? I mean everything is fine? :)

---

### Post by The Cog on 2018-12-31
> **CatKiller said:**
> With regard to this bit in particular, if you're just having Ubuntu on the computer, installing to the SSD and having the HDD as your /home will work well. /home is for user settings and data.

That's exactly what I do. 
Except that I install purely to the SSD, and then when I'm happy the OS is working properly I then reconfigure to use the HDD as /home. This simplifies the install itself. And I keep my real /home data between installs, much the same way as people use C: for the OS and D: for data on windows (or at least they used to - I'm not sure if windows still allows that these days).

When you boot the installer USB, choose to **try** the live environment rather than just install straight away. This will let you see what it looks like, whether it has any hardware compatibility issues. 

Your first problem is figuring out which drive is which so you can tell the insatller whcih one to install to. While trying out, open a terminal and use the command **lsblk** which will print out the drive IDs and sizes.

---

### Post by CatKiller on 2018-12-31
> **kibiras said:**
> Sorry, my english a little bit bad :). You mean I can install Ubuntu in SSD use both of them, SSD and HDD. Like SSD for programs and HDD for files, right? I mean everything is fine? :)

That's right.

/home is just the name of where user-specific files are kept. One of the questions that the installer will ask you is whether you want to use a different partition for different parts of the filesystem. 

As The Cog says, you can use the sizes to easily identify which drive is which.

---

### Post by yancek on 2018-12-31
I would suggest you read the official Uubntu documentation at the link below on dual booting with windows 10.  Even if you are going to overwrite windows, there is useful information at the site, particularly on UEFI which you likely have.

   [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by ajgreeny on 2018-12-31
If you do want to keep Windows for the times and programs that Ubuntu just will not run, make sure you have created the restore DVDs as I believe is suggested when you first boot Windows.
Without them you will have major problems should you inadvertently overwrite the Windows OS when installing Ubuntu.

---

### Post by Geoffrey_Arndt on 2019-01-01
It is always a good idea for new users to go to youtube and watch a few tutorials and reviews of Linux distros and ubuntu.   There are perhaps 50 or 60 good video channels about different aspect of Linux.   The quality and understandability does vary (from great to bad).   Look for good channels by video authors such as "Joe Collins" or "Distro Tube" or  "Average Linux User".

Don't try to do too much too quickly - - take your time learning and reading and watching the channels of experienced users.   Good Luck!

---

### Post by david503 on 2019-01-02
Since you have two drives: Do you still want to be able to boot into win10?  If so, well, coincidentally I just posted today about having two drives and working out how to use the two (Win10 and Ubuntu) without them knowing about each other during installation.  

Summary:

What I did was install ubuntu on one and kept windows on the other.  In fact I went out of my way to make sure they didn't know about each other to the point that I unplugged the windows drive during install to make sure!  I'm not saying it's the right way to go for you; you can still install ubuntu on the same drive as windows, but in a different partition, but I just figured if I've got two drives I may as well keep them separate.  

Again- that was just the way I chose to go, so here's the conclusion (the "SOLVED") that I posted just a few hours ago:

[https://ubuntuforums.org/showthread.php?t=2408351&page=4&p=13827740#post13827740](https://ubuntuforums.org/showthread.php?t=2408351&page=4&p=13827740#post13827740)

I was talking to guru's (such as Catkiller) so it looks complicated but I was in a special/unusal situation, it's not as hard as it looks. 

Also- you should know that while you're in ubuntu you can still easily access (both read and write), your windows drive's files (NTFS), but the other way around, windows accessing the linux drive, is really tricky, so FYI.  


d

---

### Post by kibiras on 2019-01-05
Thank you for everyone opinion, today I will install Ubuntu, but in evening, so I will write how it is going on :). I'll try to search youtube how to install clean ubuntu and how to make HDD /home. I don't know how to do that, but I hope youtube will help me :D.

/home as I get it will work from my HDD but Ubuntu will boots from SSD, right?

---

### Post by kibiras on 2019-01-05
Finally I'm on Ubuntu! Can I ask here some offers? Which VIDEO player to use? Which .torrent software to use? And should I use Firefor? Ir back to (my default) chrome? And how to set HDD to /home? And should I use antivirus?
[ATTACH=CONFIG]282103[/ATTACH]

---

### Post by Impavidus on 2019-01-05
For using the HDD as /home partition, see [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving). I suggest you format it as ext4. Use the tool gparted on your live disk.

Video player: Various options. I use vlc.
Torrent software: Various options. I just use the one installed by default. I rarely use it though.
Browser: Firefox is the default, but you can download chrome if you really prefer.
Antivirus: Commonly used on mail servers, not on laptops/desktops. The best way to keep malware out (most of which is not a virus) is common sense, not security in a box.

---

### Post by kibiras on 2019-01-05
> **Impavidus said:**
> For using the HDD as /home partition, see [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving). I suggest you format it as ext4. Use the tool gparted on your live disk.

Video player: Various options. I use vlc.
Torrent software: Various options. I just use the one installed by default. I rarely use it though.
Browser: Firefox is the default, but you can download chrome if you really prefer.
Antivirus: Commonly used on mail servers, not on laptops/desktops. The best way to keep malware out (most of which is not a virus) is common sense, not security in a box.

Thanks, I'll check the link.

 About other answers, I'm asking offers with some comments. I know that I can use anything what I want, but I'm asking offers :). And I think I can't find .torrent software installed by default. What name of it?

After checking disk usage I clicked on my HDD and now I have this:

[ATTACH=CONFIG]282104[/ATTACH]

Is that okay to use it like that? Or should I create /home for some reason?

And how can I add other keyboard layout? :)

---

### Post by oldrocker99 on 2019-01-05
Transmission is the usual default torrent program installed already. VLC is great, and so is smplayer, which sometimes runs video files that VLC, unaccountably. won't. Here's how to install Chrome.

```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add - 
sudo sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
sudo apt update
sudo apt install google-chrome-stable

```

```
sudo add-apt-repository ppa:videolan/master-daily
sudo apt update
sudo apt install vlc
```

In 10 years, I have had **ZERO** instances of malware. Ubuntu (and all other distros) are as secure as an OS can be. Install updates every day:
```
sudo apt update
sudo apt upgrade
```

There is a Linux virus protector, ClamAV, but it is mostly for servers which handle Windows files. Windows games from GOG or Steam are virus-free.

If you're a gamer, look at [https://www.gog.com](https://www.gog.com), and so this:
```
sudo apt install steam
```

That is the ONLY way to install Steam.

---

### Post by kibiras on 2019-01-06
> **oldrocker99 said:**
> Transmission is the usual default torrent program installed already. VLC is great, and so is smplayer, which sometimes runs video files that VLC, unaccountably. won't. Here's how to install Chrome.

```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add - 
sudo sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
sudo apt update
sudo apt install google-chrome-stable

```

```
sudo add-apt-repository ppa:videolan/master-daily
sudo apt update
sudo apt install vlc
```

In 10 years, I have had **ZERO** instances of malware. Ubuntu (and all other distros) are as secure as an OS can be. Install updates every day:
```
sudo apt update
sudo apt upgrade
```

There is a Linux virus protector, ClamAV, but it is mostly for servers which handle Windows files. Windows games from GOG or Steam are virus-free.

If you're a gamer, look at [https://www.gog.com](https://www.gog.com), and so this:
```
sudo apt install steam
```

That is the ONLY way to install Steam.

Well I installed steam on Ubuntu Software app. How to use that codes I don't know for really :). As I said I'm new :). And if you say code is only one way to install steam, but I installed it with Ubuntu Software, so is there any different between Ubuntu Software and code installations?

And is that okay to use ssd as home and hdd as volume?

---

### Post by Impavidus on 2019-01-06
Ubuntu Software is a graphical front-end for apt, so it's actually the same way to install things. The command line just gives finer control and better error messages.

As it stands now, that 1TB partition is not permanently attached to your filesystem. Attaching a partition as a directory to your filesystem is called mounting. You can click it to temporarily mount that partition and use it to store files, but it's probably more convenient to make it permanent. I believe that will be faster too. If you want to make it a /home partition, you can configure your system to mount it at /home at boot time.

Have you completely removed Windows from your computer? Then you shouldn't keep the 1TB partition as an NTFS partition. Linux can read and write NTFS, but cannot fix it if broken. If you want to use it as /home, it's mandatory you use some sort of Linux filesystem, best ext4. If you still have Windows, you can use an NTFS partition as a shared data partition, accessible from both operating systems.

You can use the 1TB as /home, leaving only the OS and installed software on the SSD. That's about 10GB, so depending on the size of your SSD, that may be a waste of space. I can't find the size of your SSD in this thread. What you should do depends on the details of your system and on your needs. Linux gives you the freedom to make choices about your system, but it takes some technical knowledge to make those choices.

---

### Post by kibiras on 2019-01-06
> **Impavidus said:**
> Ubuntu Software is a graphical front-end for apt, so it's actually the same way to install things. The command line just gives finer control and better error messages.

As it stands now, that 1TB partition is not permanently attached to your filesystem. Attaching a partition as a directory to your filesystem is called mounting. You can click it to temporarily mount that partition and use it to store files, but it's probably more convenient to make it permanent. I believe that will be faster too. If you want to make it a /home partition, you can configure your system to mount it at /home at boot time.

Have you completely removed Windows from your computer? Then you shouldn't keep the 1TB partition as an NTFS partition. Linux can read and write NTFS, but cannot fix it if broken. If you want to use it as /home, it's mandatory you use some sort of Linux filesystem, best ext4. If you still have Windows, you can use an NTFS partition as a shared data partition, accessible from both operating systems.

You can use the 1TB as /home, leaving only the OS and installed software on the SSD. That's about 10GB, so depending on the size of your SSD, that may be a waste of space. I can't find the size of your SSD in this thread. What you should do depends on the details of your system and on your needs. Linux gives you the freedom to make choices about your system, but it takes some technical knowledge to make those choices.

my SSD is 120GB space. I have NO WINDOWS! :D.

So if I understand, best way is to make 1TB HDD as /home? Or somehow make it like partition to use for files and SSD use for software?

I want to be clear so what's why I'm asking so much. And I'm really grateful for your all help.

---

### Post by CatKiller on 2019-01-06
The easiest way is to have the SSD as / and the HDD as /home. Your programs get the benefit of the speed, and your bulk storage gets the benefit of the space.

In all circumstances you don't want your Home folder to be on NTFS. That filesystem doesn't understand permissions.

---

### Post by Impavidus on 2019-01-06
> **CatKiller said:**
> The easiest way is to have the SSD as / and the HDD as /home. Your programs get the benefit of the speed, and your bulk storage gets the benefit of the space.

In all circumstances you don't want your Home folder to be on NTFS. That filesystem doesn't understand permissions.

Yes, that's the easy way. My only concern is that that will waste about 80% of the SSD. It's big enough to put a lot more on it than just the OS and software. Personally, I could put all my documents on that SSD, use the HDD for backups only and still have room to spare. I would consider having both a root partition and a /home partition on the SSD and a data and/or backup partition on the HDD (in addition to an external backup disk). But you can also use the SSD to install 4 Linux systems alongside each other, if you like experimenting with different Linuxes.

---

### Post by kibiras on 2019-01-06
> **CatKiller said:**
> The easiest way is to have the SSD as / and the HDD as /home. Your programs get the benefit of the speed, and your bulk storage gets the benefit of the space.

In all circumstances you don't want your Home folder to be on NTFS. That filesystem doesn't understand permissions.

Can you help me how to do that correctly? :)

---

### Post by CatKiller on 2019-01-06
> **Impavidus said:**
> Yes, that's the easy way. My only concern is that that will waste about 80% of the SSD. It's big enough to put a lot more on it than just the OS and software. Personally, I could put all my documents on that SSD, use the HDD for backups only and still have room to spare. I would consider having both a root partition and a /home partition on the SSD and a data and/or backup partition on the HDD (in addition to an external backup disk). But you can also use the SSD to install 4 Linux systems alongside each other, if you like experimenting with different Linuxes.

The OP's already got the drives, so putting them to use in the simplest manner seems like the way to go for me. Room to grow is good.

When I had that configuration in my old computer - small SSD and large spinning rust - I set it up like this, and then moved that handful of Steam games with irritating loading times over to the SSD. Symlinking back makes it transparent to Steam, or one can use Steam itself to move parts of the library. 

You don't want either partition to get more than about 70% full in any case.

This setup has the minimum of pain and most flexibility. It's easy enough to resize later should the OP find they want more partitions once they've got their feet wet.

---

### Post by CatKiller on 2019-01-06
> **kibiras said:**
> Can you help me how to do that correctly? :)

From what I've seen at far, what you've done before but choosing ext4 rather than NTFS for all the partitions. 

This thread has got a bit tangled, though, and it's difficult to follow on a phone. I'll try to check back later from my computer in case you've got stuck somewhere.

---

### Post by kibiras on 2019-01-06
> **CatKiller said:**
> From what I've seen at far, what you've done before but choosing ext4 rather than NTFS for all the partitions. 

This thread has got a bit tangled, though, and it's difficult to follow on a phone. I'll try to check back later from my computer in case you've got stuck somewhere.

Well for now stay at this problem on how to activate HDD normally :D. If it will help I attach 2 screens here, one of SSD and one of HDD. How to format it correctly and how to make HDD to use normally for files like you told it before?

[ATTACH=CONFIG]282110[/ATTACH][ATTACH=CONFIG]282111[/ATTACH]

---

### Post by CatKiller on 2019-01-06
> **kibiras said:**
> Well for now stay at this problem on how to activate HDD normally :D. If it will help I attach 2 screens here, one of SSD and one of HDD. How to format it correctly and how to make HDD to use normally for files like you told it before?

[ATTACH=CONFIG]282110[/ATTACH][ATTACH=CONFIG]282111[/ATTACH]

If you've not done much, the simplest way is to just reinstall. During the install process, format that hard drive as ext4 and say that you want it mounted as /home.

If you don't want to reinstall, use the live USB to copy anything you want to keep from that partition somewhere else, then format it as ext4. Since you've been using a directory in your / partition as your Home folder, you'll want to copy those files across to your now-fresh partition. Use Crl-H to show the hidden files so that you capture everything. Then edit the /etc/fstab file on your / partition to tell it to mount the hard drive partition as /home, then reboot into your install.

An alternative, since you've got it installed already, although it's more fiddly to use and doesn't have some conveniences, is to use the hard drive as just a big bunch of dumb storage. So you could create directories on that partition and symlink them to the places you want to use them. You'll still probably want it to be ext4 rather than NTFS, though. You'd use /etc/fstab to mount it somewhere like /mnt/bigdumbstorage and then symlink /mnt/bigdumbstorage/Music to /home/kibiras/Music, and /mnt/bigdumbstorage/Downloads to /home/kibiras/Downloads, say.

---

### Post by oldrocker99 on 2019-01-06
> **kibiras said:**
> Well I installed steam on Ubuntu Software app. How to use that codes I don't know for really :). As I said I'm new :). And if you say code is only one way to install steam, but I installed it with Ubuntu Software, so is there any different between Ubuntu Software and code installations?

And is that okay to use ssd as home and hdd as volume? Well, first of all, /home can **never** be too big. The SSD should be /, and the HDD should be /home, unless your SSD is enormous.

The Ubuntu Software app uses the same repositories as the terminal method, so you have installed it correctly.

And there is no such thing as a stupid question. It can be stupid **not** to ask that question. We denizens of the Ubuntu Forums LIKE to help, if we can.

---

### Post by kibiras on 2019-01-06
Okay, I found the way to format my partition to Ext4 with Disks. Now how to make it /home exactly?

---

### Post by oldrocker99 on 2019-01-07
When reinstalling (which I think is the thing you should do), select "Something Else," then select the SSD and format it, and mount it as /. Then, as long as you don't have data on the HDD, do not format it, and mount it as /home. Then your (backed up, of course) /home will be preserved if you should reinstall, or try another distro. Every Linux distro uses the /home folder exactly the same.

You can also mount a disk as /home by booting into a live USB session, and using gparted to try to mount the partition as /home. It's a bit more complicated that way, though.

---

### Post by kibiras on 2019-01-07
> **oldrocker99 said:**
> When reinstalling (which I think is the thing you should do), select "Something Else," then select the SSD and format it, and mount it as /. Then, as long as you don't have data on the HDD, do not format it, and mount it as /home. Then your (backed up, of course) /home will be preserved if you should reinstall, or try another distro. Every Linux distro uses the /home folder exactly the same.

You can also mount a disk as /home by booting into a live USB session, and using gparted to try to mount the partition as /home. It's a bit more complicated that way, though.

Oh. I don't want to reinstall my OS. Is that okay if I use HDD just like using right now without /home then? Because I don't get any point why I should make HDD like /home. All downloads and files I still can keep in HDD. Even steam games working from HDD without /home.

---

### Post by kibiras on 2019-01-08
At least I can't reinstall, because I can't find any information how to enter BIOS and F12 isn't working when I clicking when PC starts

finally i found a way. I removed a battery from motherboard.

Well now I set SSD to / and HDD to /home and when installing this is what i get:

[ATTACH=CONFIG]282129[/ATTACH]

why it's so hard to install.....

---

### Post by CatKiller on 2019-01-08
> **kibiras said:**
> At least I can't reinstall, because I can't find any information how to enter BIOS and F12 isn't working when I clicking when PC starts

Del or F2 are common for entering the BIOS; F12 or F8 are common for displaying the boot menu. You can generally search for *<computer/motherboard name> boot menu key* to find out what it is. Presumably you knew what it was when you installed last time, though.

> **kibiras said:**
> Oh. I don't want to reinstall my OS. Is that okay if I use HDD just like using right now without /home then? Because I don't get any point why I should make HDD like /home. All downloads and files I still can keep in HDD. Even steam games working from HDD without /home.

It's your computer; use it however makes most sense to you. This is the bigdumbstorage option I posted earlier.

Having your /home on a separate drive has a number of benefits: it's tidy, so you won't have the icon sitting on your desktop or elsewhere in the file browser. Your applications and their settings can load in parallel, which is less of an issue these days but was significant when drives were slow. The biggie, though, is that if you break everything through experimentation all your data and settings will be preserved and automatically applied when you reinstall the OS.

---

### Post by kibiras on 2019-01-08
> **CatKiller said:**
> Del or F2 are common for entering the BIOS; F12 or F8 are common for displaying the boot menu. You can generally search for *<computer/motherboard name> boot menu key* to find out what it is. Presumably you knew what it was when you installed last time, though.



It's your computer; use it however makes most sense to you. This is the bigdumbstorage option I posted earlier.

Having your /home on a separate drive has a number of benefits: it's tidy, so you won't have the icon sitting on your desktop or elsewhere in the file browser. Your applications and their settings can load in parallel, which is less of an issue these days but was significant when drives were slow. The biggie, though, is that if you break everything through experimentation all your data and settings will be preserved and automatically applied when you reinstall the OS.

I get it, thank you. BTW my motherboard key f11 still not worked. So I just removed battery.

I trying to install with / on ssd and /home on hdd but get errors.

[ATTACH=CONFIG]282130[/ATTACH]

Should I create one EFI too? And with how much space?

---

### Post by CatKiller on 2019-01-08
> **kibiras said:**
> I get it, thank you. BTW my motherboard key f11 still not worked. So I just removed battery.

I trying to install with / on ssd and /home on hdd but get errors.

Should I create one EFI too? And with how much space?

The thing that comes to mind is that by pulling the battery you've reset all your BIOS settings. That will mean that you could be booting in Legacy Mode when you should be booting in UEFI mode, or vice versa. I find the EFI stuff very confusing, generally, though.

Best to start a new focused thread about the reinstall so that someone who knows about that stuff will see it.

---

### Post by kibiras on 2019-01-08
Finally I found this:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

So I think for now all my problems gone.

There is what I did with normal-clear installation:

When need to select how I want to install I choose "something else". I set my all HDD to ext4 /home. I set my SSD 1GB (enough ~100-250MB) for efi. I set my SSD 8GB (amount of RAM) for swap. I set my all other space of SSD to ext4 /.

Thank you for everyone of you help for me. It means a lot for me as for new user! See you in next topics :D

---

### Post by Paulgirardin on 2019-01-26
> **kibiras said:**
> Oh. I don't want to reinstall my OS. Is that okay if I use HDD just like using right now without /home then? Because I don't get any point why I should make HDD like /home. All downloads and files I still can keep in HDD. Even steam games working from HDD without /home.
 I'd like to offer my opinion.
Considering your noob status and the hardware on your system,I think the suggestions for your installation have been over complicated.

I would have suggested you install Ubuntu entirely on the SSD ( / and /home - the default install option) and use the HDD for data.

You can always move the /home to the HDD at a later time or during installing a newer version of Ubuntu if you feel it will be beneficial.

Using the 'Disks' application set the HDD to mount at boot ( > settings > edit mount options )

Create downloads , pictures ,documents etc folders on the HDD if desired and change the download location setting in various apps to download the these new folders (optional)

I have used Ubuntu since 2006 .I used to create a separate /home partition ,but I stopped doing this because it was of no advantage to me.

Catkiller post #38:
"The biggie, though, is that if you break everything through experimentation all your data and settings will be preserved and automatically applied when you reinstall the OS."

I suggest you install Timeshift restore tool and set it to save snapshots of the OS onto the HDD This is an alternative resolution for the problem described above.Without reinstalling. Or to reproduce your previous set up in a new install.
 [http://www.linuxandubuntu.com/home/timeshift-a-system-restore-utility-tool-review](http://www.linuxandubuntu.com/home/timeshift-a-system-restore-utility-tool-review)

qbittorrent is an excellent torrent client.
[https://qbittorrent.org](https://qbittorrent.org)

---

