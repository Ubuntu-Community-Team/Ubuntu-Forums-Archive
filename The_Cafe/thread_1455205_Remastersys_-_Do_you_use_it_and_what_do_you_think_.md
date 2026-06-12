---
title: "Remastersys - Do you use it and what do you think of it?"
date: 2010-04-15
forum: The Cafe
---

### Post by Fragadelic on 2010-04-15
Just polling the community here to see how many folks actually use remastersys.

I'm the man behind remastersys in case you didn't know.

I'd like to find out how many folks are actually using it and what they think of it.

I spend a lot of time testing and updating it for each new Ubuntu version that comes out and would like to know if I'm wasting my time or you all actually find remastersys useful.

Don't be shy.  I really want to know what folks think of it.  Partially to see if there is something I need to fix about it or if it is even worth it to continue working on it.

Regards,
Tony aka Fragadelic

[http://www.geekconnection.org/remastersys](http://www.geekconnection.org/remastersys)

---

### Post by aysiu on 2010-04-15
I haven't used it in a while, but when I did I liked it a lot.

Basically, Jaunty had a weird sound glitch and some buggy wireless issues with the HP Mini 1000 series, so I tweaked Ubuntu and wanted an easy way to distribute the tweaked version to other HP Mini users, and Remastersys offered a great way for me to do that.

Since those issues got fixed in Karmic, I haven't used Remastersys for quite a while. It was good nine months ago. I'm hoping it can have only gotten better in the meantime.

Thanks for all your hard work.

---

### Post by Fragadelic on 2010-04-15
It's always a work in progress due to keeping up with the latest Ubuntu but I try to make it better as time goes.  Some things folks want just isn't possible in the grand scheme of things especially if it is very specific to their needs and causes a conflict with other desktops or other settings.  It's definitely a balancing act.

Thanks for the feedback and my apologies for posting it originally in the wrong area.

I'd like to hear everything, especially the bad points.  If lots of folks are using it and the majority would like something changed then I can do it but I don't want to be putting in so much time for just a small handfull of people.  I want to be realistic about the time I spend working on it as I have other interests and projects on the go as well.

---

### Post by Lightstar on 2010-04-15
I choose Option 5
No, but I would like to try it.

----------------

I often carry an ubuntu cd and/or usb drive, for backup, emergencies, etc etc  (I'm often called by friends and family to fix their pc)  I'd like to customize it with the programs I use.

I might also use it to clone my ubuntu install in case things go wrong when I play around a bit too much.

---

### Post by Fragadelic on 2010-04-16
The lucid supporting release of remastersys 2.0.16 - is almost here.

I have some final testing and then I'll prepare the package and put it on the repository.

I've changed the boot from regular isolinux text based to the vesamenu.c32 which is more like what the old grub iso boot menu looked like.  It allows you to navigate the boot options with the arrow keys and enter on your boot choice.  Changing the background png file is very simple as well.

---

### Post by Fragadelic on 2010-04-16
If you respond with anything other than option 1 of the poll, please let me know why.

You can either post it here or PM me privately if that is more to your liking.

I'm at a point right now where I really want/need feedback from the community whether it be positive or negative is irrelevant.

---

### Post by Phrea on 2010-04-16
> **lightstar said:**
> i choose option 5
no, but i would like to try it.

+1

EDIT: I have heard and read about it, it seems interesting and I am planning on using it. :)

---

### Post by Twitch6000 on 2010-04-16
I use to like it,but seeing as it is one of the main causes of all these "new" distros... I hate it...

---

### Post by chris200x9 on 2010-04-16
I have not used it but would if I ever needed something like it.

---

### Post by helliewm on 2010-04-16
I like to do a fresh install for each new Ubuntu release. I always set up a separate home partitions. So I do fresh install on my desktop, set it up the programmes I like. Then I use Remastersys to make a custom DVD. I then use the DVD as fresh install for my 2 laptops. I keep that DVD incase anything screws up so I can get my computers up and running qucikly.

You are doing a great job, I could not live without it.

Many thanks,

Helen

---

### Post by Fragadelic on 2010-04-16
Helen,

Sounds like you use it in the same manner I do - lol.

There are 6 of us in my house and almost as many pc's and laptop's(most are recycled things others have long discarded).

I usually get my main box setup with everything we use in the house and then remaster it for the others.  I maintain a server in the house for all of our more critical documents and such so reimaging any single pc or laptop doesn't mean any data loss.

Once all of them are setup with their usernames and settings I then make a backup for each of them and store it on the server.

Regards,
Tony

---

### Post by Homer on 2010-04-16
Hi,

I found your project recently.  We are using some Ubuntu PC at work and I'm looking for a deployment strategy for the next LTS release.

I think remastersys can be a great help for me if it can allow me to create custom Ubuntu install dvd.

I'm waiting your lucid compatible version for trying for real.  I found the actual version is not working (installer crash) with lucid release.

---

### Post by Fragadelic on 2010-04-16
> **Homer said:**
> Hi,

I found your project recently.  We are using some Ubuntu PC at work and I'm looking for a deployment strategy for the next LTS release.

I think remastersys can be a great help for me if it can allow me to create custom Ubuntu install dvd.

I'm waiting your lucid compatible version for trying for real.  I found the actual version is not working (installer crash) with lucid release.

The installer in Lucid now requires a file to be present on the livecd that shows the filesystem size.  I have the code to produce that information already working on my test version of remastersys that I should be releasing in a few days.  This version will still work on Karmic but add support for Lucid as well.

---

### Post by earthpigg on 2010-04-16
I use it, as you know :D

---

### Post by Firestem4 on 2010-04-16
Well I never knew about it till now :) I'll definitely give a go the next time I have the chance.

---

### Post by lisati on 2010-04-16
I've used it once or twice before, and like it. I've recommended it on a couple of occasions on the forums for people wanting to do backups or make custom install CDs

---

### Post by DubyBreaks on 2010-04-17
I am Fairly new to ubuntu and remastersys was one of the first (and best) applications I ran across when looking for ways to backup and create a Disk Image.  I use it very frequently and feel that this software is pretty awesome........kudos to you.  The only issue i have had with it is a weird (what I would call glitchy) double/tripple flash of the xsplash screen when booting after installing (Karmic) from a remastersys image.  Am I doing something wrong?  It hasn't ever effected pc performance or booting speed and is certainly not a deal breaker, as the program works very well, it just looks weird when booting.  Great job on this software and please continue to support it!

---

### Post by Endomancer on 2010-04-17
I tried it in February with Karmic. But I did make some errors with it, like burn it to disc at full speed. When I tried the custom disc I made all fonts had been replaced with boxes, but again I had just switched to ubuntu from windows and had no clue as to what I was doing.

But I am planning on trying again after Lucid is officially released and supported to make a customised live USB for portability (hopefully an updatable one)

---

### Post by ydristi on 2010-04-17
i really liked it ....but now it refuses to work .i made 2 or 3 iso's of karmic using it .
then all of sudden it won't make iso's .it makes all other files but only iso is missing 
i am really sad since i play with ubuntu a lot :(:(

---

### Post by helliewm on 2010-04-17
Lol I am shortly going to build a PC to use a server! Seems like we both use IT in a  similar way.

> Sounds like you use it in the same manner I do - lol.

Keep up your excellent work. I would be lost without Remastersys.

Helen

---

### Post by Fragadelic on 2010-04-17
> **ydristi said:**
> i really liked it ....but now it refuses to work .i made 2 or 3 iso's of karmic using it .
then all of sudden it won't make iso's .it makes all other files but only iso is missing 
i am really sad since i play with ubuntu a lot :(:(

It sounds like the filesystem.squashfs is too large.  The forked package in debian and ubuntu that is responsible for creating iso file has a limit of 4GB for a single file and if the compressed filesystem is more than 4GB it will not create the iso file.  You can try and move some non-essential media files from your home folder onto a portable drive and then try the backup again.

Colin Watson(the main casper person) sent me some code to try that would allow more than 1 squashfs file which would get around this issue but I have not had the time to try it out yet.

---

### Post by kjdixo on 2010-04-17
Fragadelic.
Your Remastersys backup system is an essential part of my Linux life.
I have used it on Linux Mint 6 XFCE and Xubuntu 8.10.
My current OS is Xubuntu 9.04.
Recently I installed Ubuntu Netbook 10.04 Beta (Easy Peasy Linux) on two computers for different people (who live many miles away) and I would have preferred to have left them with Remastersys 'restore' discs.
Then when I get the 'it doesn't work phone call' (usually as a result of certain little people thinking the computer is a toy and breaking the software) I simply get them to boot to the Remastersys disc all set up with my original configurations.
It is a temporary fix until I can go there and reinstall.
A Remastersys Disc definitely provides that extra 'peace of mind'.
In fact I was waiting for two major and important (for me) pieces of software before installing Lucid Lynx 10.04 (Ubuntu Netbook) on my 3 desktop PCs . . .

1. Remastersys. A few months ago you wrote you would not release a new Remastersys until the 10.04 final stable release of Linux Ubuntu, because of all the work involved and you didn't want to keep changing it whenever the Lucid Developers made changes. Of course, very sensible.

2. I am also waiting for the ATI Catalyst driver (10.4) because I run 3 screens as one large desktop. It seems there is a pre-release of that available now.

Things are looking promising.

I definitely want Remastersys to continue in Lucid 10.04 please. 
Having not made a Remastersys disc for several months I can't remember any problems, only that it was a bit time consuming tracking down and removing all the large files (some hidden) on the Customized Linux before creating the ISO. Linux has trash hidden here and there (and .debs in the APT archive) , so it takes a bit of research and effort to clear it all.
Thanks and keep up the good work, it is appreciated.
Kevin Dixon

---

### Post by kevin11951 on 2010-04-17
While I love the idea, I find myself doing the manual steps instead of using remastersys.  The reason is that I am planning on making distributable dvds for me and my no-so-tech-savvy friends to use, but with remastersys it leaves remastersys installed on the distro dvd, and thats not a great idea...

---

### Post by Fragadelic on 2010-04-17
> **kevin11951 said:**
> While I love the idea, I find myself doing the manual steps instead of using remastersys.  The reason is that I am planning on making distributable dvds for me and my no-so-tech-savvy friends to use, but with remastersys it leaves remastersys installed on the distro dvd, and thats not a great idea...

Why is it not a good idea?  Remastersys is a backup tool.  Thats like saying it wouldn't be a good idea to leave a burning app after install.

I think you might not fully understand what remastersys is and can do.

The primary function is to make a backup of your system.  The dist mode is something I have left in there for folks that want to use it since it is similar but I have to shake my head every time I hear someone like you say leaving it on the system is not a good idea.  It just clearly tells me they aren't fully aware of what it does or is capable of.

---

### Post by praveesh on 2010-04-17
I created a distro with it in jaunty . I liked it . But I think it is difficult to customise themes , colour schemes in kde and  application softwares .

---

### Post by praveesh on 2010-04-17
> **Fragadelic said:**
> The lucid supporting release of remastersys 2.0.16 - is almost here.

I have some final testing and then I'll prepare the package and put it on the repository.

I've changed the boot from regular isolinux text based to the vesamenu.c32 which is more like what the old grub iso boot menu looked like.  It allows you to navigate the boot options with the arrow keys and enter on your boot choice.  Changing the background png file is very simple as well.

I would prefer the Ubuntu's default boot menu.

---

### Post by praveesh on 2010-04-17
By the way, thanks for your hard work . Keep it up.

---

### Post by kevin11951 on 2010-04-17
> **Fragadelic said:**
> Why is it not a good idea?  Remastersys is a backup tool.  Thats like saying it wouldn't be a good idea to leave a burning app after install.

I think you might not fully understand what remastersys is and can do.

The primary function is to make a backup of your system.  The dist mode is something I have left in there for folks that want to use it since it is similar but I have to shake my head every time I hear someone like you say leaving it on the system is not a good idea.  It just clearly tells me they aren't fully aware of what it does or is capable of.

Alright, I think we got off on the wrong foot...

Hi, My name is Kevin.  I have been using Remastersys on and off for a few years, and absolutely love your project!

With that said, I am not comfortable about giving a dvd with the same software on it used to create it, because it may look unprofessional.  I am not saying you should change it, because as a backup tool its great.

---

### Post by Fragadelic on 2010-04-18
I've just released the remastersys version that includes support for Lucid.

Here is the announcement from my forum.

[http://geekconnection.org/remastersys/forums/index.php?topic=732.msg4236#msg4236](http://geekconnection.org/remastersys/forums/index.php?topic=732.msg4236#msg4236)

---

### Post by Fragadelic on 2010-04-18
> **praveesh said:**
> I would prefer the Ubuntu's default boot menu.

Then just copy the contents of the isolinux/ folder from the original ubuntu live cd to /etc/remastersys/customisolinux/ and run remastersys.  The original ubuntu menu will be there.

---

### Post by BslBryan on 2010-04-18
I have used it as a backup tool, but also to create a new distribution of Linux.  There was a time when I wanted to make a widely released Debian or Ubuntu based distro, but there was really nothing that hadn't been done that I was thinking about.  The only thing that really changed was look, and that wasn't enough for me to continue the project.  I suppose it would be a lot of fun to actually keep going, but I don't really know what direction it's heading.  If I figure it out, I'm sure you'll hear about it, and your Remastersys will be an essential tool in its creation.

---

### Post by earthpigg on 2010-04-18
> **praveesh said:**
> I created a distro with it in jaunty . I liked it . But I think it is difficult to customise themes , colour schemes in kde and  application softwares .

dig around and find out where the default theme data is stored ***outside*** of /home or /root, then replace the system files with the ones from your /home.

[example]("http://sites.google.com/site/masonux/home/notes-to-myself"), for lxde:

> Make panels look pretty. Then:
cp ~/.config/lxpanel/LXDE/panels/panel /usr/share/lxpanel/profile/LXDE/panels/. 

that will make the current user's lxpanel setup the default from then on.

you will have to dig around yourself to find where that stuff is hidden for whatever software you want to re-theme.

another, also slightly ghetto method, is to simply replace the files that contain the default theme with your own. rename the old ones to "themename-default.theme" or whatever, and drop your own in it's place as.

---

### Post by brucewagner on 2010-04-19
@ earthpigg    Or, you could just do a "backup" type of ISO using remastersys.  It will then retain everything... including your appearance settings, user account(s), and even all your data in /Home...

---

### Post by brucewagner on 2010-04-19
Tony,

The remastersys software is arguably one of THE most important applications available for Ubuntu.  The power it provides is not easily available any other way. 

It is essential for what we do.  And if more users were aware of it, it would likely be critical for their backup plans. 

If there was one improvement I'd love to see, here's what it would be:

The ability for remastersys to,  upon discovering a squashfs exceeding the 4GB limit, to either:

-- automatically create multiple squashfs files, spanning multiple DVDs if necessary 

And / Or

-- automatically separate the largest files onto separate DVDs 

And / Or

-- somehow remove software that's too large and automatically reinstall it from repositories after re- install of the OS 

In other words, be able to intelligently handle systems of any size.... spanning them over multiple DVDs as needed. 

That would be way cool!

If I had a second feature wish list item, it would be:

The ability for remastersys to automatically MAKE the current user's appearance settings, the system default settings,  prior to creating the ISO.  (....or prompt the user to Ask if te user would like this done.)

Hey!   You asked!

Thanks, Tony.   Your hard work is changing the world in HUGE ways.   More than you know.

---

### Post by Fragadelic on 2010-04-19
The 4GB limit is due to the cd/dvd writing tools in Ubuntu and the live boot scripts(casper) can't handle more than 1 squashfs file at the moment.  As I said earlier, Colin Watson sent me some code to test that would allow multiple squashfs files but that wouldn't make it be able to span acroos media.  AUFS, the filesystem that allows it to work like a regular filesystem and the actual squashfs filesystem need to have access to all of the squashfs files that are mounted.  Remember, the entire thing isn't loaded into ram.  It accesses the files you need as you need them.  It would be like saying you could have your system on 2 or more drives that you hot swap in and out - basically you can see that this would not be possible.

What I have been looking into is to try and make a bootable usb with larger files but then the fat16/fat32 file limits would apply so it wouldn't help either.  What would be required would be to have an ext2 filesystem for the usb so that the squashfs file size can be larger.

There really is no way to get around the 4GB limit until the backend cd/dvd writing tools are fixed to be able to go up to a dual layer size.  Then again you would still be limited to the size of a dual layer dvd.

None of what you mentioned is new to me.  I've been thinking about it for a long time but you just can't get a live system to span on the same media no matter what way you look at it.  It is just not possible.

---

### Post by dartdog on 2010-04-20
Well I hope this is what I'm looking for I'm a newb to Ubuntu and am repurposing an older xp Gateway laptop so I bought a new 160gb drive and got Lucid 10.04 beta 4 up after some trials a tribulations apparently due in part to bios disk size grub geometry issues ( I don't know but it required me to reformat and nuke the drive to get the install/grub to take..

Each time I got a certain point along.. the machine bricked.. and then I was up for hours of junk reformatting.. I finally have realized (by only updating portions after install) that something in the open or x org gl drivers is doing it, I'm down to 22 suspect packages,, but I need to create a re-install disk that will flat work,, so I'm not up for (too many) hours... this looks like it may do the trick... Advice??

I want to get it down to which of the 22 packages is bricking my start-up.. so it will still be painful... So I'm using ext4 and I have an external usb ntfs terrabyte drive,, but the machine has a built in dvd so I guess I'll use it...:P

Is this the right tool????

---

### Post by Fragadelic on 2010-04-20
Once you have things like you want them, then you can make a backup to use elsewhere.

FWIW - I seem to have had issues with ext4 having weird lockups and hangs and when I switched to ext3 - the old tried and true linux filesystem, all the issues went away.

---

### Post by Bachstelze on 2010-04-20
Other: I never used it just because I never felt the need to. If sometime I need something like that, I'll definitely at least give it a try.

---

### Post by deeptiman.panda on 2010-04-22
> **Fragadelic said:**
> If you respond with anything other than option 1 of the poll, please let me know why.
 
You can either post it here or PM me privately if that is more to your liking.
 
I'm at a point right now where I really want/need feedback from the community whether it be positive or negative is irrelevant.
 
Hi All

I have been using Ubuntu since 8.10. From time to time, I have used **[COLOR=#ff0000]Remastersys[/COLOR]** to preserve my customizations and reinstall it when something goes wrong. It is a very good program which helps me preserve my system settings in case of unforseen crashes or bad upgrades. 

Recently I have upgraded to 10.04. Now, I am trying to save all the updates and my customizations using **[COLOR=#ff0000]Remastersys[/COLOR]**. Everything goes fine and I am able to create a custom CD. But when I try to run this live CD, it is asking for a log in.

I have no idea what that login could be. I tried some standard logins like - custom/custom or my own user name and password from the installed Ubuntu, but nothing seems to be working. 

Now, I am worried, that if something goes wrong, then I have to redo the installation + upgrades and my customization.

Any help is much appreciated. Also, please let me know, if anyone else is also experiencing this issue.

Thanks
Deeptiman

---

### Post by Fragadelic on 2010-04-22
Boot with the debug boot option and see why it is failing to create the live user.

---

### Post by Lord Stig on 2010-04-22
> **Fragadelic said:**
> Just polling the community here to see how many folks actually use remastersys.

I'm the man behind remastersys in case you didn't know.

I'd like to find out how many folks are actually using it and what they think of it.

I spend a lot of time testing and updating it for each new Ubuntu version that comes out and would like to know if I'm wasting my time or you all actually find remastersys useful.

Don't be shy.  I really want to know what folks think of it.  Partially to see if there is something I need to fix about it or if it is even worth it to continue working on it.

Regards,
Tony aka Fragadelic

[http://www.geekconnection.org/remastersys](http://www.geekconnection.org/remastersys)

It's an excellent tool - very easy to use for someone (like me) with limited knowledge of Linux and I used it to when replacing a laptop hard drive. I was a bit skeptical that it would work (nothing personal, just seemed too good to be true) but it worked brilliantly.

I keep the CD to get a tailored system installed should I need to again.

Just wanted to say my thanks to you since I have the opportunity.

---

### Post by roachk71 on 2010-04-22
I'm now the owner of an Acer Aspire One and can't afford to buy an external DVD drive, so that leaves me with using a combination of Remastersys and UNR's USB Startup Disk Creator.

So far, it's worked flawlessly for me. :guitar:

---

### Post by deeptiman.panda on 2010-04-22
> **Fragadelic said:**
> Boot with the debug boot option and see why it is failing to create the live user.

Hi

Can you please be more specific. What do I need to do?

This will help me figure out and if possible fix the problem.

Deeptiman

---

### Post by Fragadelic on 2010-04-22
From the livecd boot menu - arrow down to debug and boot with that.  It turns off splash and shows all messages generated during boot which will show you all the casper steps.  Casper is failing to create the user or something like that and you will see it on the screen.

---

### Post by Fragadelic on 2010-04-22
One thing that you have to remember is that the temporary working folder for remastersys must be a proper linux filesystem that contains file ownership properties.  Windows filesystem mounted in linux do not have ownership properties.  They only have the ownership of the user that mounted the device.  They also need to have the OGW(Owner, Group, World) permissions like a linux filesystem but the mounting can override this to whatever the mount command has in it.  There really is no way to get this to work properly so the working folder ABSOLUTELY MUST be on a linux filesystem like ext2, ext3, reiserfs, etc.  It definitely cannot be on fat16, fat32, or ntfs filesystems.

I have been trying to figure out a way of testing this and may have figured it out.  After more testing I will include the test in remastersys so that it stops and errors out rather than continuing on for nothing.

---

### Post by deeptiman.panda on 2010-04-22
> **Fragadelic said:**
> One thing that you have to remember is that the temporary working folder for remastersys must be a proper linux filesystem that contains file ownership properties.  Windows filesystem mounted in linux do not have ownership properties.  They only have the ownership of the user that mounted the device.  They also need to have the OGW(Owner, Group, World) permissions like a linux filesystem but the mounting can override this to whatever the mount command has in it.  There really is no way to get this to work properly so the working folder ABSOLUTELY MUST be on a linux filesystem like ext2, ext3, reiserfs, etc.  It definitely cannot be on fat16, fat32, or ntfs filesystems.

I have been trying to figure out a way of testing this and may have figured it out.  After more testing I will include the test in remastersys so that it stops and errors out rather than continuing on for nothing.

thanks for your quick turn around. The stuff about ownership should be fine in my case, as I am using the same partition as the original Ubuntu installation drive, e.g. suppose I have a partition of Ubuntu installed, immediately after taking the remastersys ISO, I will try to run it on that partition. But one thing that raises my concern is, my partition is of ext4. Will that create any problems?

Please advise. Also, I will try to run it in the debug mode and get back to you.

thanks again.

---

### Post by Fragadelic on 2010-04-22
Ext4 is fine as its a native linux filesystem.

One other thing I would like to see is the output of the following command:

sudo find /etc/skel

---

### Post by deeptiman.panda on 2010-04-22
> **Fragadelic said:**
> Ext4 is fine as its a native linux filesystem.

One other thing I would like to see is the output of the following command:

sudo find /etc/skel

This is the output you requested from my current system (installed Ubuntu system)

deeptiman@deeptiman-desktop:~$ sudo find /etc/skel
[sudo] password for deeptiman: 
/etc/skel
/etc/skel/.bashrc
/etc/skel/.bash_logout
/etc/skel/examples.desktop
/etc/skel/.profile

Please let me know , if you need anything else..

---

### Post by MCVenom on 2010-04-22
Haven't ever used it, but I've heard of it. I plan to use it when Mint 9 comes out to make a custom CD for a friend :D

---

### Post by deeptiman.panda on 2010-04-23
> **Fragadelic said:**
> From the livecd boot menu - arrow down to debug and boot with that.  It turns off splash and shows all messages generated during boot which will show you all the casper steps.  Casper is failing to create the user or something like that and you will see it on the screen.

Hi Again

I tried running the live CD in debug mode. But I could not find any debug messages which I can pass on to you? Is there something else, I need to do?

One small correction here, instead of wasting DVD's for my Remastersys live cd, I am converting them into usb flash drives, so that, I can try multiple tmes, without wasting media. Will that create any problems?

---

### Post by Fragadelic on 2010-04-23
It would be better to try it in a virtual machine in qemu, virtual box or vmware player.  Just make sure to give the virtual machine enough ram.

Not enough ram will also cause the issue of not being able to create the user.

---

### Post by wykedengel on 2010-04-23
I haven't had the need to use it, but I do have a question as I would like to try it after Ubuntu 10.4 hits. Can I back up to a USB and reinstall from there? My biggest problem with using CDs is that they get scratched over time.

---

### Post by Fragadelic on 2010-04-23
Once the iso is made you can use USB Creator to put it on a usb stick.

---

### Post by Alacrity on 2010-04-24
Remastersys is always one of the first software programs I add to a new Ubuntu version.  Extremely valuable to me.

---

### Post by mdmarmer on 2010-04-28
Hi Fragadelic,
I really appreciate your work with remastersys.  It's a great product.  The installer works really well -- I think writing an installer is the most difficult part of building your own distro.  If I wanted to use the installer from another distro, I would have to remove customizations -- but remastersys is set up to be general purpose and will work with any variety of debian or ubuntu.

Thanks so much for a great product!!

Mike

---

### Post by perspectoff on 2010-05-07
> **Twitch6000 said:**
> I use to like it,but seeing as it is one of the main causes of all these "new" distros... I hate it...

Hey dude -- you have the wrong avatar -- you need the one of the crotchety, fat comic guy (from the Simpsons)...

---

### Post by perspectoff on 2010-05-07
> **Fragadelic said:**
> It would be better to try it in a virtual machine in qemu, virtual box or vmware player.  Just make sure to give the virtual machine enough ram.

Not enough ram will also cause the issue of not being able to create the user.

You hit the nail on the head. There is no option for installation only, and by default the entire system runs (including my servers) as a live system (even during installation). This leaves absolutely no memory for the installation itself. I burn the backed up image onto a DVD, and have attempted to restore from it. This means everything has to happen in RAM (since there is no swap from a DVD). While it's nice to say to use Remastersys with drives with persistence and presumably some swap memory (such as hard drives, USB drives, or networked resources), once I go that route there are faster ways to clone a system. What I want is something that allows an image to be distributed on inexpensive DVDs.

When I used Remastersys it created the complete (and nicely compressed) .iso image onto the DVD fine, but it did not successfully re-install from the DVD, for this reason. It froze with "insufficient memory" errors soon after starting up the servers (that are integral parts of my system).

As an alternative I have instead turned to FSArchiver, which merely copies the filesystem and then restores it to a cloned partition (which I manually create with GParted or Partition Manager). I then change the UUIDs, Grub, and fstab files by hand and off I go.

If Remastersys had that sort of capability, it would be gold.

---

### Post by Slug71 on 2010-05-31
Id like to make a backup ISO of my current custom install so so that i can possibly/probably break it by further customizing and possibly to share too. 
I have Hulu Desktop, Sun-Java, Skype and Google Earth installed on my system. Will i need to remove those before i make the ISO? Not too worried about space as i have DVDs. More concerned about licensing. 
Also, do i need to install Ubiquity or does remastersys take care of the installer??

---

### Post by brucewagner on 2010-05-31
Remastersys does all the ubiquity for you. 
You don't need to remove anything - for your own backup use. 
For massive distribution, ask a lawyer. 
The size limit is 4GB for the entire COMPRESSED file system - even on a DVD image ISO. 
There's no way to predict the size. Trial and error is your friend.

---

### Post by Slug71 on 2010-05-31
> **brucewagner said:**
> Remastersys does all the ubiquity for you. 
You don't need to remove anything - for your own backup use. 
For massive distribution, ask a lawyer. 
The size limit is 4GB for the entire COMPRESSED file system - even on a DVD image ISO. 
There's no way to predict the size. Trial and error is your friend.

Thanks,
If i upgraded everything to maverick when btrfs lands in it, would i also have the option to install using btrfs?

Just checked and i dont have sun-java installed. Will probably just remove Hulu, Skype and Google Earth to play it safe.

---

### Post by MBybee on 2010-05-31
I use it, I like it, but I think it needs work :)

Don't get me wrong - you're a rockstar! :guitar:
However, the tool on Karmic has two quirks I think should be fixed.
1) The boot install screen is hideous. PLEASE make it more like the normal Ubuntu one!!!

2) I end up with a file on the desktop called ubiquity-gtkui.desktop. Not a show stopper, but still - a fix would be nice :)

If it helps any, this tool is a MASSIVE productivity booster for my office. I build a default image based on Ubuntu LTS plus all our patches and assorted apps (like SAP, bookmarks, etc). I create a remastersys backup with the 'backup' option, then use Ubuntu to create a LiveUSB image with a persistence store. We then use this in the event of hard drive issues (frequent) or having to borrow some non-imaged machine or whatever.
It's a total lifesaver (and I actually would like to donate some $$$ if you can direct me to a link!).

---

### Post by Slug71 on 2010-06-02
bump...

---

### Post by 101011010010 on 2010-06-05
Hello there,
Just tried a reinstall after another idiot error :redface: and worked perfectly for me.
Thank you Fragadelic for all your hard work.  :popcorn:

---

### Post by gordintoronto on 2010-06-05
I use it and like it very much!

I have hundreds of GB of media files, so I am not interested in using it to back up my data. However, I wish it would include my wallpaper and desktop settings in the ISO.

---

### Post by Austin25 on 2010-06-06
Gettin' it now.

---

### Post by Pinoy Tux on 2010-06-07
Awesome tool!  I use it to deploy my customized installation on several terminals.  It beats having to spend days configuring several terminals one at a time. :cool:

---

### Post by themarker0 on 2010-06-07
I've never heard of it, until today that is.

---

### Post by philinux on 2010-06-07
> **gordintoronto said:**
> I use it and like it very much!

I have hundreds of GB of media files, so I am not interested in using it to back up my data. However, I wish it would include my wallpaper and desktop settings in the ISO.

Fire up the app and choose modify, then from the option list choose e, files to exclude. Then exclude your media files.

---

### Post by arjunak01 on 2010-06-07
i use it to backup my entire pc, it is a really good tool

---

### Post by philinux on 2010-06-07
> **arjunak01 said:**
> i use it to backup my entire pc, it is a really good tool

Yes as long as the iso created is less then 4 gig.
[http://klikit.pbworks.com/Remastersys+-+Limitations+of+remastering](http://klikit.pbworks.com/Remastersys+-+Limitations+of+remastering)

---

### Post by murderslastcrow on 2010-06-07
I use it to make customized LiveCDs for friends and family who want to take advantage of my kindness in setting things up for them. Means that, when I do install it, all we need to figure out are drivers, and all their desired software (including specific Wine programs) is already there.

I think it's great, and if you can polish it and add a useful feature when you find one, it could be more than great. I think offering more options to customize specific names (mainly of the OS itself), or other generalizable aspects of the OS would also make it a more complete tool.

---

### Post by tdunlapjr on 2010-06-07
We depend on it heavily for our in-house development efforts. I was sad to see the domain is no longer active. However, I see it's on Sourceforge. Based on the dates, I assume it's still active.

Please do not abandon this project! Contact me directly if you do decide to stop development.

Keep up the great work!

Terry Dunlap

---

### Post by Slug71 on 2010-06-07
Gonna try this out and make a ISO of my current install later today.

---

### Post by Pinoy Tux on 2010-06-07
What happened to remastersys? Last time I used it was 2 days ago but today the home page is no longer there?

---

### Post by JedMeister on 2010-06-07
> **Pinoy Tux said:**
> What happened to remastersys? Last time I used it was 2 days ago but today the home page is no longer there?
The SourceForge site is still up. This post explains the current state of play. For background, read the whole topic.
[http://ubuntuforums.org/showpost.php?p=9424512&postcount=38](http://ubuntuforums.org/showpost.php?p=9424512&postcount=38)

---

### Post by Pinoy Tux on 2010-06-07
> **JedMeister said:**
> The SourceForge site is still up. This post explains the current state of play. For background, read the whole topic.
[http://ubuntuforums.org/showpost.php?p=9424512&postcount=38](http://ubuntuforums.org/showpost.php?p=9424512&postcount=38)

Yup saw it this morning.  Thanks! :)

---

### Post by lightningfox on 2010-06-08
I've read about it but I haven't tried it yet.

---

### Post by Fragadelic on 2010-06-09
The site is back up.

The host that we moved to dropped us due to my repository even though we cleared it with them beforehand.

We're back on godaddy now.

---

### Post by libssd on 2010-06-13
With Ubuntu 9.04 and legacy grub, I successfully created backups to both USB and DVD. With Ubuntu 10.04 and grub2, I have only been able to create usable bootable backups to DVD. All attempts to create a bootable remastersys backup to a USB have failed. Has anybody done this, and can you document a procedure?

---

### Post by Pinoy Tux on 2010-06-14
> **libssd said:**
> With Ubuntu 9.04 and legacy grub, I successfully created backups to both USB and DVD. With Ubuntu 10.04 and grub2, I have only been able to create usable bootable backups to DVD. All attempts to create a bootable remastersys backup to a USB have failed. Has anybody done this, and can you document a procedure?
I use Mint 9, which is based on Lucid (and grub2).  I just use usb-creator-gtk to write the remastered ISO to USB.  It works well.

---

### Post by anantshri on 2010-06-14
> **Phrea said:**
> +1

EDIT: I have heard and read about it, it seems interesting and I am planning on using it. :)

+1 looking for a way to keep my customized session on disk to be able to distribute it to my friends.

looking for all tools and remastersys is one one them to be tried in my list of options....

---

### Post by Rodney9 on 2010-06-14
I used for the first time today for my Xubuntu 10.4 laptop, worked brilliantly. I made a custom iso.

---

### Post by ganeshmallyap on 2010-06-14
I recently installed RemasterSYS on my Kubuntu Lucid AMD64 desktop.  It worked like charm.  I could never imagine this process could be so simple and straight forward.  Thanks a ton to Tony.

I have one question though.  One of my friends is using a old desktop and does not have a internet connection, so I intend to create a fully loaded xubuntu/lubuntu distro for him using RemasterSYS.  To do this , I want to know can I install xubuntu/lubuntu on a virtualbox with all added software, then remaster it using this software?  If yes, are there any limitations for that remastered distribution?  Thanks in advance.

Regards
Ganesh

---

### Post by slickvguy on 2010-07-16
I have used remastersys many, many times. It's terrific. I have made modifications to the script in order to make it more personal/customized for my specific situation. And now that I have a computer system that isn't from the dark ages, the entire process only takes me about 10 minutes or so.

Here's the reason it's so valuable to me...

Over the past year, I have been traveling back and forth between Canada and the USA for anywhere from 2 to 6 weeks. I do not have a laptop (nor do I want one - just don't like them). Using remastersys w/ a usb stick allows me to in essence "bring my pc with me" - while using someone else's hardware. Before I leave home, I run my modified remastersys and throw it onto my dedicated remastersys usb stick. While I'm away, I simply boot the usb stick on almost any laptop/desktop that I have use of, setup a few things (like wifi and video driver), and then I can do just about everything that I do on my home PC. Such a pleasure! 

For example, I don't have to wait until I get home to enter into Quicken (which I run with crossover) the (sometimes huge) batch of receipts I accumulate. I just do it wherever I am, every few days. Pay bills online and don't have to remember to enter the transactions when I get home. Send/receive e-mail from my home ISP's account (so that clients don't necessarily know I'm away). Do stock trades. etc. etc. 

And the best part is when I return home: I simply boot my remastersys usb live stick on my home system, copy all the changed datafiles (e.g. evolution data, firefox bookmarks, quicken stuff, etc.) to their corresponding directories on my home/HD ubuntu install, reboot...and voila, I'm completely caught up  and ready to go (aside from installing a ton of system updates that I missed while away. lol). 

There is no better solution for this scenario. Instead of lugging around a portable - I have my PC in my pocket!

Thanks for all your hard work, Tony. *VERY* much appreciated.

---

### Post by pinguy on 2010-07-16
It's a great tool. I use it to make Pinguy OS.

---

### Post by Timmer1240 on 2010-07-16
Yes I created a live Cd of my system and it works really well its a great program!

---

### Post by v1ad on 2010-07-16
will be using it from now on.

did not know this existed.

---

