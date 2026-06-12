---
title: "Almost switched to Ubuntu ..."
date: 2011-11-20
forum: Testimonials &amp; Experiences
---

### Post by wickedchris on 2011-11-20
Hi all, I have been testing Ubuntu from time to time since version 9.04.

Though I decided to give a try to Ubuntu 11.10, so I installed it ... it didn't lasted and I went back to Win 7 after a week.

A few things were bugging me, nothing important, until I tried to share my "TV show" folder ... see, I download a few TV shows for me and my wife, she listen to her TV shows from her laptop (running Win 7).

Thing is, I tried for a week to have the sharing working, but nothing, I lurked many forums, tried a good dozen of solutions, none worked. I could never log into the shared folder (that is when I was able to see it!).

Also, I listen often to my TV shows on my phone, so I convert them to MP4 ... tried different softwares for converting but it was either too much of a pain (typing a 50-60 character long command in the terminal) or way too long to convert (30 minutes to convert a 45 minutes file). In Win 7, it takes me seconds (about 4 clicks) and 10-12 minutes to convert the same kind of files.

In the end, Ubuntu is really not what I was expecting nor does it fit my needs ... this saddens me because I would have gladly switched from Windows!!!

---

### Post by mastablasta on 2011-11-21
> **wickedchris said:**
>  
A few things were bugging me, nothing important, until I tried to share my "TV show" folder ... see, I download a few TV shows for me and my wife, she listen to her TV shows from her laptop (running Win 7).
 
Thing is, I tried for a week to have the sharing working, but nothing, I lurked many forums, tried a good dozen of solutions, none worked. I could never log into the shared folder (that is when I was able to see it!).

you should have posted on the forum instead of lurked and trying solutions. Sharing with windows mashcine is easy in Ubuntu. Now Debian that's abnother matter, but Ubuntu there is no problem to get it working. The issue is that sometimes they forget to install a package needed to do that.
 
>  
Also, I listen often to my TV shows on my phone, so I convert them to MP4 ... tried different softwares for converting but it was either too much of a pain (typing a 50-60 character long command in the terminal) or way too long to convert (30 minutes to convert a 45 minutes file). In Win 7, it takes me seconds (about 4 clicks) and 10-12 minutes to convert the same kind of files.

 
CLI based converters do need command line. again if oyu posted people would give advice on easy to use GUI converters. Also typing in terminal is not necessary as you can copy paste it.
 
but in the end you found out same thing as i did. it's not that Linux can't do these things propperly it's that they hide them from users. and i am really not sure why they do this. such as sharing. it should offer to install when you click a folder and want to share it with windows mashine. once installed it should work just like in windows. i say install because not everyone needs this function. but many do.

---

### Post by Black_Sector on 2011-11-21
Unity is not really ideal for people who dont know the name of what they are looking for. It looks like a poorly designed cell phone, not a work station. Id consider using it on a tablet, but if that is the end game then I resent the way it was 'tested' on desktop users. Unity is slightly more usable than Gnome3 vanilla, but Gnome 3 with an extra dock or MSGE panel along the bottom is by far more function, imo.

I know this isnt about Unity, but I cant help but feel like tinkering is easier with a proper drop down menu. Mint Menu was the most comprehensive I have seen in Linux, and they eliminated the need for 2 panels in Gnome2.

Anyway, to network with Windows you need to install Samba.

Another way, if its on a different computer, is to use Bluetooth devices. For some reason its not as hard to share files with bluetooth as it is with wifi, as long as you have the files to enable NTFS read/write functions.


The easiest thing to do though is get yourself a quality USB stick, like a Patriot X-porter, and just transfer the files that way. Use fat32 for maximum compatibility, or NTFS if you only are using more modern 'heavy' Linux and Windows.

---

### Post by mörgæs on 2011-11-21
Wickedchris, there are many options for solving your problem, and atop of that Mythbuntu might be interesting to you. If you want I can move the thread to a support forum.

---

### Post by wickedchris on 2011-11-21
Thanks for the answers!
 
Just to be clear, I'm still using Ubuntu, it's just that it will not be my main OS as I thought it would be by now!
 
and for the record, I already have Samba up and running, but somehow it's not letting my windows machine and my Xbox360 in the share folders ... tried every solutions I could find (here and elsewhere), installed GUI for Samba, modded the conf through those GUI and Gedit but to no avail, I can't access it.
 
Same goes with the video convertions, tried ffmepg, winff, avidemux, and others I can't remember now with all the same result : they are all slower than the Win 7 software I'm using (some freeware I can't remember the name).
 
BUT, as I said, I'm still using Ubuntu, mainly for the hard to download Chinese torrent I "need" (my wife is Chinese and the TV Shows she wants are slow to download ... yeah I know it's not very legal but until I subscribe to some IPTV service it's the only solution for her!). Somehow in Windows those torrents idle at 5-10KB/s while in Ubuntu they easily get up to 50KB/s ... go figure!
 
 
So right now Ubuntu is on an external E-SATA hard drive running mainly at night and my main OS is still Win7.
 
I guess if I find a solution for Samba I might switch, but for now it's not looking good! :(

---

### Post by Perfect Storm on 2011-11-21
I urge you to start new threads regarding your issues. A good idea to split your problems, one problem each thread. The forums are there so you can get help ;)

---

### Post by mastablasta on 2011-11-23
> **wickedchris said:**
> I guess if I find a solution for Samba I might switch, but for now it's not looking good! :(
 
yah samba i way too complicated. been tinkering with it lost my temper, but finnaly found what was wrong (a command didn't register) and made the folder be seen in windows. The GUI for it can make it even more complicated as the config file get's fileld with various settings that we newbies dont' knwo what they do. nor have the time to find out.
 
often what could be is that you are:
 
1. missing a samba file (yup not all necessary files for sharing are installed if you install SAMBA)
2. user is not propperly maintained (usershares) and sharing is therefore not allowed/is blocked
 
why oh why can't they make it simple....i am still battling with it to get the windows printer recognised.
 
 
btw if you need help as suggested just post a thread, so we can give some hints. 
 
I found that KDE makes it simple to share but again fails to install crucial files needed for the share when you install SAMBA.

---

### Post by terry_gardener on 2011-11-23
> **wickedchris said:**
> 
A few things were bugging me, nothing important, until I tried to share my "TV show" folder ... see, I download a few TV shows for me and my wife, she listen to her TV shows from her laptop (running Win 7).

Thing is, I tried for a week to have the sharing working, but nothing, I lurked many forums, tried a good dozen of solutions, none worked. I could never log into the shared folder (that is when I was able to see it!).



i had a similar problem and i found that the problem was permissions because was trying to logon to the folder as guest, the other permission group was set to none and therefore wouldn't let the access it and sometimes not even see it from windows, i just changed the permissions and then after restarting samba all was well.

but i agree with the above and write some support thread in the correct and there is more chance it will get fixed.

---

### Post by Roasted on 2011-11-26
@ wickedchris,

We don't bite, bro. Many of us lurk these forums and answer questions like this all of the time. What do ya have to lose? :popcorn:

---

### Post by JamesFlamingo on 2011-11-26
I installed Samba and it shared every file in every folder between every user on the machine. It is things like this that make me realize i am a radical for continuing to use Ubuntu given all of its HUGE shortcoming. ;)

---

### Post by TenPlus1 on 2011-11-26
Control Panel - Administrative Tools - Local Security Policy 

Local Policies - Security Options 


Network security: LAN Manager authentication level 
 Send LM & NTLM responses 

Minimum session security for NTLM SSP 
 Disable Require 128-bit encryption 


my SMB server worked after changing those two options

answer from: [http://www.tomshardware.com/forum/75-63-windows-samba-issue](http://www.tomshardware.com/forum/75-63-windows-samba-issue)

---

