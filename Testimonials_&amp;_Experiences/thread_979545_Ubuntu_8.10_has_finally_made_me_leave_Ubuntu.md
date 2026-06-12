---
title: "Ubuntu 8.10 has finally made me leave Ubuntu"
date: 2008-11-12
forum: Testimonials &amp; Experiences
---

### Post by RossDV8 on 2008-11-12
Installing Ubunutu 8.10 has caused so much mischief on my main computer I have to remove Ubuntu altogether and move to another distro.
yesterday I posted a question about why Ubuntu killed my /home directory.  For those who read it, I installed 8.10 to replace 7.something that I had been using successfully.  I had expected 8.10 to be up to Ubuntu's usual standerd (i.e pretty well perfect).

Instead, when I told it to use hda6 as /home, it created /home with a nice new set of standard directories, but ognored hda6.  I eventually gave up messing with it when I found a heap of other problems with the install, and installed 8.04 instead.

8.04 also refused to mount hda6 as /home, but I managed to force it by messing with fstab.  However, all the permissions were now wrong, so I couldn;t access any files and changing permissions on 90gb of directories and files locked the system time after time, so i went through and changed them all one directory at a time.  here we are two days later....

Now I have access to my /home and I even have all my mail for the last 6 years or so back again.  Let's try networking.  Hmm.  No way to share files.  Check if samba is installed - Yep.  Do we have smb4k in case we need it? - Yep.  Hit the forums and search the error messages.  Hmm.  Lots of people with the same problem and lots of advice from forums leading to - responses like "thanks, but that doesn;t work".

Try a few things and we can finally use gnome to set folders as shared, although there is no way to make kde share because the kde-cache user file is owned by 0 instead of 1000.  Check permissions, and the file is owned by user, readable and writeable by user, nobody else is able to read or write to it, so it satisfys all the requirements of the error message.  Google on this and hey presto - lots of people with the same problem and no solutions.

So, completely uninstall KDE including libs and config files.  reboot and reinstall KDE to see if there is now a clean config and if we can share folders.  Nope - no way.  Still get that little message saying you have to have permission to configure sharing and asking for a password.  of course, there is no password that works here (as evidenced by the fact that people all around the world are complaining about the same error.

I know this isn;t just a Ubuntu issue, but my system was working perfectly before Ubuntu 8.10 killed it.

I have the choice of returning to Ubuntu 7.something if I can find the disk, then doing heaps of upgrades, or changing to one of my other distros that doesn;t have these problems.

As I mentioned in the post about /home being killed, I'm not abandoning Ubuntu - just waiting until it works.  

It is kind of sad when a distro as broken as 8.10 is actually available as a 'release' rather than as a beta.

If I couls remember what release I was using before I installed 8.10 I would gladly reinstall that, but I have no idea.

So, a suggestion for Ubuntu and indeed other Linux distibutions.  Why not have a "Help > About>" as software has, which displays the distro and version?

I'll be keeping an eye on the forums in case either 8.10 is fixed, or a new release without these problems comes out.

Also, I realise Ubuntu is a community project and I admire Canonical for making it "freely" available.  I have spent quite a bit of money supporting Linux distros over the last 10 years, more in fact than I have spent on Windows licences (and No - I don;t pirate).  Ubuntu has been one distro I've supported, although not recently - so I am keen to see it working.

RossD

---

### Post by Flag on 2008-11-12
Are you sure you did everything you should do ?
Am using Ubuntu for a couple of years now, with for abt a year my home on a separate partition without any trouble.
8.10 installed fine, but a couple of things I use frequently don't work, so I have 8.10 on one partition, 8.4 on the other, home on the third. Using 8.4 till 8.10 is able to run what I want.

---

### Post by RossDV8 on 2008-11-12
I'm pretty sure I did.  I started using Linux on all of my business systems in 1998 when I decided it was pretty well as good as Unix had been, and have been using it for well over 10 years.

I booted 8.10 from the CD, told the partitioner to use sda6 as /home and not to format anything other than /.

When I found things like Internet not working after the software updates instelled (and I KNOW I'm not the only person who had this problem) and the /home problem I tried to fix them using basic stuff.

When that didn't work I installed 8.04 from CD in exactly the same way and that is what I am using now.

As I mentioned above, I like Ubuntu enough to have supported it financially in the past, as i did with a few other distros that I was keen on, so I'm NOT deliberately or maliciously knocking Ubuntu.  Just disappointed that it does not work properly.

No way I can get the thing to share files over the network.  The earlier 7.xx Ubuntu distro was serving files to Vista happily.  All my other distros (I am running 6 other computers) are happily sharing files by just right clicking on the folder and setting share names.

Ubuntu in KDE is telling me I need permission to share and asking for a user name and password.  Entering my user name and password results in the same thing coming up again.  Entering my user name and password again results in the same thing coming up again.  Entering my username and password yet again results in ...  you guessed it!

In Gnome, I can right click a folder and select share, but on the Vista machine it then asks me for..  (drum roll) a user name and password.  Of course, entering my user name and password (this time on the BVista machine) results in...  The same thing again.

It sort of becomes a little boring after a while, especially when I have no problem doing this with any other distro.

I assumed there may have been a glitch in the installation so since my earlier post in this thread I uninstalled and reinstalled 8.04 and let it make its own /home just to test it.  Obviously I formatted "/".  I then tried to share a folder in the new /home through Gnome and KDE.  This, by the way, was after I made sure samba was installed and running.  The folder I chose to share initially was "Public".

I just ran smb4k and it sees the computer and sees all the printers as shares.  It will even see "Public" but when I try to mount it guess what?  It asks for a user name and password in smb4k before it will mount it.  

Guess what user name and password don't work????

So, I have come to the conclusion that:
1 - It isn't 'just' my computer, because other distros work on it.
(having said that, their may be some hardware incompatibility that causes this problem in 8.04 and 8.10 that didn;t exist in 7.xx)
2 - I probably isn;t me, because I am doing the step by step fresh installation with all the bits that should be needed.
3 - Something somewhere is weird about the 8.xx series of Ubuntu.

Thanks though to the people that answered the "why did 8.10 kill /home.  I was not pleased that it has happened to other people, but glad I wasn;t the only one.

Cheers,

RossD

I'm not looking forward to changing to another distro - I LOVE Ubuntu  :-(

p.s.

Just tested one laptop running 8.04 and another running an earlier version.  Neither have been on the network before because one lives in my van and the other lives on my yacht.  The one with 7.xx needed samba installed then it was simply a right click > share and Vista allowed connection.  The one with 8.04 has done exactly the same thing as the desktop machine.  :-(

---

### Post by RossDV8 on 2008-11-12
Ok, I've finally scrapped Ubuntu for the moment. 

After wasting a little over 2 days and a night and a half trying to make it work, I found my copy of XUBUNTU 8.04 and installed it in exactly the same way as I installed Ubuntu 8.10 and 8.04.

It has taken about 30 minutes to install codecs and get the network talking to Vista.

So rather than Ubuntu, I will use Xubuntu until Ubuntu 8.04 and 8.10 are working properly.

Now, my questions are...

Aren't Xubuntu and Ubuntu basically the same ting except for the desktop manager?

Why did Xubuntu 8.04 work before I installed Ubuntu 8.10, and why when I installed Ubuntu 8.04, did it fail to work when Xubuntu 8.04 works straight away?

Weird stuff.

RossD

---

### Post by sickenmcsluggets on 2008-11-12
> **RossDV8 said:**
> 

So, a suggestion for Ubuntu and indeed other Linux distibutions.  Why not have a "Help > About>" as software has, which displays the distro and version?


RossD

System->Administration->System Monitor

---

### Post by RossDV8 on 2008-11-12
Thanks.

Weird place to hide it, but at least it is there.

In the mean time, Xubuntu is running perfectly, all my machines are talking to each other, because I removed Ubuntu from the laptops and installed Xubuntu on those as well.

As soon as I tried System > Shared Folders, they both downloaded Samba and one worked right away.  On the other I had to manually edit /etc/samba/smb.conf to add my shared folder, but it worked.  

I still don;t understand why Xubuntu is installing and running perfectly and Ubuntu is playing up, but I'll live with that.

I winder if Kubuntu also works in situations where Ubuntu won't?

Cheers,

RossD

---

### Post by mkvnmtr on 2008-11-12
8.10 seems to be working great for some people. I can't even get it to install and quite a few like you are having problems that are a deal killer. I think the real problem is trying to get it to work on every piece of equipment in the world in time for the release date. I seems from other releases in a few weeks most of us will be able to use it with no more than a few small problems. For that I have to thank the guys that put up with the big problems when it first come out.

---

### Post by wolfen69 on 2008-11-12
i peruse these forums all the time and have not heard of the problem your having with /home. i believe it was bad luck, bad burn, etc. a problem like that would not make sense. even if one other person had this problem, it does not mean it is a bug. remember, there are millions of people using it without issue.

---

### Post by jerrylamos on 2008-11-12
A whole pile of people have a bunch of different problems with Intrepid 8.10 at release code level, in my opinion worse than 8.04, 7.10, 7.04, ...

Me too.  I finally got it going by booting in rescue mode then doing sudo apt-get remove compiz compiz-core.  Compiz "eye candy" code is on by default.  There's an update, after release code, which disables compiz for the affected Intel (heard of them?) video chips.

Compiz on 8.10 uses a code path not used by anyone else which fails on many Intel video graphics chips, see Launchpad Bug #259385.  I also see many changes were made in X windows which caused people trouble compared to 8.04 Hardy.  People running on 8.04 Hardy didn't expect upgrade to turn their pc into a vegetable.

Seems to me 8.10 goal was "fancy features" instead of "it should at least boot and run".  Ubuntu won't increase its coverage unless it runs.

Having said that, Intrepid is finally running better on my IBM Thinkpad than any Ubuntu all the way back to Dapper Beta.  With compiz removed.  And a USB mouse, since the track point mouse code is buggy from Feisty on.

Jerry

---

### Post by blackmail on 2008-11-12
I am sad to hear that from you but now i am just running the xubuntu live cd listening to a infected mushroom on youtube, and yes installing it, just because intrepid ibex does not want to run as hardy did!And am installing suse11 after this to see what it does, I never tryed it, but hope it will work, but just as you i don't know what got me on ubuntu, maybe because it was my first distro that i tryed...or i don't know but i 2 am waiting for something less windows-like and more linux-like!
Oh and i just had a revelatin while lighting my cigar, I tryed to lite a match and it did not light, and i tryed severakl after, and i finally succeeded, this being the brand of matches that always lit up even in wind...they are much like ubuntu is now...dissapointing...but hey there is always a new release with new problems..:guitar:
Guess we just solve them!
...now i am sure my post did not help, actually it is just a post floating around in this thread, but at least i posted something:lolflag:
...best wishes

---

### Post by thomascj on 2008-11-12
i'm experiencing similar difficulties with 8.10 -- have downgraded to 8.04, then upgraded from the fresh install to 8.10, and am still experiencing the same problems.

thankfully it works fine (for the most part) -- just wont start until i let it start in "low graphics mode", no apparent way to get my fglrx stuff going (no entries in "hardware drivers"), and no compiz..  i'm just keeping my eye on the updates manager hoping this all gets resolved soon.

---

### Post by Tamlynmac on 2008-11-13
This post reminds me of a statement I was told as a child: "Patience is a Virtue"

I listened to many of the voices on this forum that emphasized waiting to upgrade. They reminded me to practice the wisdom of the above statement shared with me as a child.

I did endeavored to install 8.1 on one of our 5 home systems and immediately canceled the install when informed (by a pop-up box) that my NVIDIA card was not supported. The only reason I was going to upgrade one system was to monitor 8.1's progress and evaluate when to install on all systems. Now I'm just going to follow the advise of other forum members and wait (as in patient).

---

### Post by ECPCLINUX on 2008-11-13
Hello, u can also find your version by: System/About Ubuntu. There it says:Thanks you for your interest in 8.10 Intrepid Ibex... 

I consider myself lucky, cause my problem in 8.10 and 8.04 was Skype not working with Pulseaudio. I found a Thread that helped me remove Pulseaudio. As for Vista I'm still trying to get XP to see Vista's shared files,lol. Just not as interested in trying to get that working anymore.

---

### Post by DrMega on 2008-11-13
> **wolfen69 said:**
> i peruse these forums all the time and have not heard of the problem your having with /home. i believe it was bad luck, bad burn, etc. a problem like that would not make sense. even if one other person had this problem, it does not mean it is a bug. remember, there are millions of people using it without issue.

That fact that millions of people are using it without an issue doesn't mean that there is no issue.

Many people have reported problems. I wonder how many more tried it for the first time, and then just threw the disk away and accepted that the stigma about Linux being complicated is just true, vowing to never try it again.

Also, the fact that millions are using a piece of software with issue does not mean that there is no bug in their version. It just may not have encountered the circumstances that manifest the bug. I am a professional programmer and can tell you that from time to time, a bug is reported by one user in a system that is used by many people on a daily basis. I have on occassion looked at the code in question, and puzzled over how it ever worked at all, conceding that I or my colleagues can't have had enough coffee the day that piece of code was written.

---

