---
title: "Ubuntu is not for me…yet"
date: 2006-01-26
forum: The Cafe
---

### Post by dpack on 2006-01-26
Okay geeks and geekettes, I honestly tried Ubuntu 5.10, which I didn’t even download or order. A co-worker gave me one of the many free discs he ordered from the web site. Yes, to this day I still have it and will probably play with it some more later.

Just so everyone knows I have come up the ranks with Microsoft being a steady user of: MS-DOS, Win3.11, Win9x, Win2K, and WinXP. I am an advanced Windows user and my career is in Information Technology supporting Microsoft networks. I know nothing about Linux nor have I even played with it until now.

I first did a test run via dual-booting Windows and Ubuntu. I played with it for I believe 3 days just to get a feel for it. I also went through looking at all my program alternatives. Everything looked pretty cool and I understood a lot right off the bat without having the first question. So then I decided that the only way I can learn it is to USE it. I wiped my hard drive clean and did a clean install of Ubuntu. I ran and used the OS for 2 weeks straight (everyday for hours at a time) before I ended up going back to Windows.

When I did have questions I was able to find my answers by searching this forum (great help forum by the way!), looking over official and unofficial guides, and Google searches. The roadblocks I encountered that took my experience to a halt was NOT because of me not understanding or not knowing how to do something. My problems were incompatibility between Ubuntu and hardware and software.

Some of the projects I do require me to use certain programs that are Windows only. While Wine did work for me on some programs, others I couldn’t even get installed or did get installed but then it did not run or run correctly. For hardware, Xine offered no support for my scanner and I certainly couldn’t install the manufacturer’s Windows only software. I also had issues with my external USB hard disk that I use for backup and file storage, which is critical to my operation.

So I guess if I was the “standard home user” of Internet browsing, emailing, IM’ing, and maybe making a few documents and spreadsheets, Ubuntu would have been PERFECT. Applause! A stable OS free of viruses and spyware and that is also FREE. But I’m not a standard user with all the intricate projects I do.

So, Ubuntu is not for me…yet. Most people I see complaining about Windows have good arguments of the issues they have/hate. So I’d like to address those issues Windows users have. By no means am I here to “preach” or shove Microsoft down your throat. What I am about to write is for the users who tried Ubuntu (or any other Linix distro for that matter) and couldn’t get it do what they wanted and were forced to go back to the OS everyone loves to hate. Since those users have to use Windows let me offer some suggestions of how to setup and run Windows to make it very stable and secure.

1. First things first, do a clean install of Windows! Don’t do OS upgrades! If you buy a new Windows OS, wipe that hard drive out and install clean.

2. After the clean install download all the latest hardware drivers from the manufacturer’s web sites and install.

3. Install all Windows service packs and critical updates.

4. Assuming you have a dedicated high speed connection: get a router that has a hardware firewall. This was something I didn’t even have to purchase. I signed up with Vonage (I’m not promoting or plugging anything here) and they sent me a Linksys router. By simply hooking that router up I can run a Shield’s Up test at grc.com and my PC shows Stealth Mode. The router hands out DHCP so my PC is on an internal LAN instead of sitting out there on the Net with a public IP.

5. The first program to install after you install Windows is ZoneAlarm! Let it configure your PC for Internet access. Then as you install your other programs you’ll be prompted to which programs you want accessing the web one-by-one verses multiple pop-ups all at once confusing you and not knowing what is what. I prefer ZoneAlarm over using the Windows XP firewall. I do use RealVNC (free version, yes I am aware this is not an encrypted connection, but it’s free) to connect to my PC remotely and not remote desktop, which most people know is over port 5900. I configured my Linksys router to do a port forward for 5900 to pass along the traffic. To secure that, I configure RealVNC to only allow connections from a certain IP range (my IP’s from work) and then place that range in the Trusted Zone in ZoneAlarm. That way ZoneAlarm blocks all incoming traffic over port 5900 except me at work. Windows is now secure.

6. The next big complaint is viruses and spyware. This is easy to combat once you have Windows locked down and using good software, software that is FREE and STABLE I might add. I use AntiVir for virus scanning and Ad Aware for spyware scanning. Not once have I ever had either of these programs find something on my system. I practically don’t really need to run them. But to help keep your system free of junk use the following software:

a. For browsing the Internet I use FireFox/Opera. Do NOT use Internet Explorer. If you must use IE then most definitely refer to Step 7 below.

b. For email I use Mozilla Thunderbird and Sunbird minimized to tray for events and tasks.

c. For documents I use OpenOffice. So using the following software there is no need to use Microsoft Office. That is unless you must connect to an Exchange server. Most home users don’t that I know of.

d. For Instant Messaging I use Gaim. It’s one free program that connects me to all instead of running separately YIM, AIM, Google Talk, MSN, etc.

7. This is a biggie and most people are guilty of this. DO NOT run your Windows account with Administrator privileges! Linux users don’t run as Root all the time do they? Of course not! Yes, it is convenient to be able to install software on the fly, make hardware changes, adjust system settings, but you don’t do that all the time! They way I do it is I will run my account as an admin from day one of my Windows install. After about two weeks, I have everything I want installed and configured the way I want it. Then I log in as the Administrator and demote my account to being a standard User (not even a Power User). You don’t need admin rights to browse the Net, do email, IM, create/edit documents, etc. When you do need to do something that requires admin rights, log off and then in as administrator, or use fast user switching (XP only) to quickly go in as Admin so you don’t quit your session, or you can use the Run As command under the right-click menu.

a. Referring back to Step 6 part A, if you must use Internet Explorer you definitely want your account to have User only privileges. Say you do go to a web site that has malicious code. Well, it can’t install to your machine because it won’t have the rights too! That also goes for viruses.

b. A lot of people may take a little time getting used to running without admin rights, but I like to tell them this analogy. When you leave home you lock the door don’t you? Of course! You want your house secure! Well, isn’t it more convenient for you just to leave the door unlocked, or to just remove the door completely? Yes, but then anyone can get in. You make the sacrifice of carrying a key and locking the door every time you leave. It’s the same thing with Windows. It is less convenient to not run admin rights but it is way more secure that way. Microsoft is actually getting with the program on this and Vista will be doing a lot of this automatically.

8. The other security measure most home users don’t do is having a password on their account and/or the admin account, or if they do it is a simple password. Create a complex password for all accounts on the PC! It should not be a dictionary word or just a string of numbers.

9. The other argument is supporting a monopolistic company hell bent on taking over the world! It’s Pinky, Pinky and the Brain, Brain, Brain, Brain…sorry. The only support I am giving to Microsoft is a single user license purchase of an OS that does everything I need without issues. That’s it. I also have no plans of ever using Office at home either. I don’t even own an Xbox! LOL Other than installing critical updates that are automatically downloaded, I have no interaction with Microsoft or their web site. If me putting a product to use at its full potential doing all my computing needs that is stable makes me a Linux backstabbing monkey boy…well, then I guess so be it. LOL Windows just works for me.

Doing all of the above is NOT that difficult. Not only have I never had any spyware or a virus on my machine, Windows has never crashed either. I have a rock solid system that has 100% compatibility with all my hardware and software and is pretty much guaranteed to support any additions I make to it.

So, computer users that are forced to stay with Windows, I hope you take at least some or all of the points I have made into consideration. Doing the above WILL make Windows secure and solid. I’ll be keeping my eye out for future distros of Ubuntu. When I can get it to do everything I need, I will most definitely say bye, bye to Microsoft, at least at home. Got to deal with it at work.

Keep workin’ it Ubuntu developers! You got a great package coming up the ranks and great people who use it that are very friendly and supportive of others user here on this board.

David

---

### Post by mstlyevil on 2006-01-26
Bravo! I must say that was an intelligent and thoughtful post. Windows can be secure if a person knows how to make it secure. I have always said a person should use what works for their needs. I dual boot Win XP and Ubuntu, yet I spend almost all my time on Ubuntu. I use Windows primarily for gaming and on the rare occasion that I have a multimedia item on the net that Ubuntu does not support that well. I never get viruses or malware because I practice most of the very things you listed in your post. The exception is I still run as admin but I have a few games that do not like to play on a limited account. I hope you continue to dual boot and play with Ubuntu to see  if you can work out some of your other issues. There is nothing like a challenge to get the adrenaline pumping.

---

### Post by Lord Illidan on 2006-01-26
But Xine is not intended for scanners.... You mean Xsane? I think you should have tried Kubuntu. It is more windows like, you could say, and in terms of compatibilty, KDE seems better than GNOME (for me at least).

Also, why didn't you dual boot?? it makes more sense than just formatting your hdd.

---

### Post by aysiu on 2006-01-26
I love this post.

It's long, but good...

---

### Post by Lord Illidan on 2006-01-26
[quote=aysiu]I love this post.

It's long, but good...[/quote]

You mean, he is not a well intentioned troll, lol..

No, this post sums up what is wrong with Linux and what we have to change, imho. And it is not biased towards either side, something we Linuxers have to fix.

---

### Post by midwinter on 2006-01-26
[QUOTE=Lord Illidan]You mean, he is not a well intentioned troll, lol..

No, this post sums up what is wrong with Linux and what we have to change, imho. And it is not biased towards either side, something we Linuxers have to fix.[/QUOTE]

What does this post sum up that is wrong with Linux, exactly?  That Windows software and drivers don't work all that well on it? :)

---

### Post by TechSonic on 2006-01-26
*clap clap clap*  1 up!

Great post, but I've done all that type of configuration on my own XP when I used it.  It helped a little, but not enough.  Not rock solid, but at least more like tin foil over it's paper like security just in admin all the time.

---

### Post by mstlyevil on 2006-01-26
[QUOTE=midwinter]What does this post sum up that is wrong with Linux, exactly?  That Windows software and drivers don't work all that well on it? :)[/QUOTE]

Hardware support is hit and miss and commercial software for Linux is lacking for the Bussiness sector. These are not the fault of Linux but we as Linux users need to make more noise to get better drivers and commercial software available.

---

### Post by Lord Illidan on 2006-01-26
[quote=midwinter]What does this post sum up that is wrong with Linux, exactly?  That Windows software and drivers don't work all that well on it? :)[/quote]

Exactly. The lack of hardware drivers and software. Well, ok, not exactly wrong with Linux, rather a fault of the programmers/device manufacturers, but also, could it be that we are not putting enough pressure on them to start supporting Linux?
And again.. for some people Linux works perfectly.. example - me.

---

### Post by Lord Illidan on 2006-01-26
[quote=Lord Illidan]Exactly. The lack of hardware drivers and software. Well, ok, not exactly wrong with Linux, rather a fault of the programmers/device manufacturers, but also, could it be that we are not putting enough pressure on them to start supporting Linux?
And again.. for some people Linux works perfectly.. example - me.[/quote]

EDIT : Need to type faster

---

### Post by dpack on 2006-01-26
Whoops! You're right! I meant Xsane and not Xine. Also, I really can't dual-boot. Between my two physical hard drives I have 112GB. I find that I sometimes get very close on maxing that space out because sometimes I deal with files that are in the Gigs size range. So instead, when I want to play with Ubuntu some more I pop in the Live CD.

Sorry to hear some of you still have Windows issues though. I can really only account for my experience. Although I guess it would be good to mention that I do not have a off the shelf PC either. I ordered every component of my PC separately and built my own machine from the ground up. It's a power house box that can pretty much take anything I can throw at it. Windows 2000 and XP sit very happily on my hardware.

David

---

### Post by Stew2 on 2006-01-26
Fantastic post. As said before, use what works best for you. I have had very good luck with 3 very stable Windows systems, 2 XP and 1 2Kpro. The only time I had major headaches was when I ran Windows ME for about 6 months. Yikes! I also have 1 Ubuntu box and the whole works are networked together and get along very well. I like fiddling around with Ubuntu though because I love the open source concept, but there are things I can do easier (for me) in Windows so I use them both :), at least until I learn more about Ubuntu.

---

### Post by cityismine on 2006-01-27
You can also use a program called pc-cillin, it's got firewall, anti-virus, and anti-spyware. I like it's firewall, as doesn't need a setup process, you just turn it on. Another option is to get a router with a built-in hardware firewall.

---

### Post by fuscia on 2006-01-27
i used to use firefox, gaim, gimp (dumped photoshop for it) and a bunch of free 'get rid of the crap' programs when i still used my beloved windows ME. i never bothered with the firewall stuff as i never had anything on my machine that was worth anything. i had forgotten how much of my time was spent getting rid of stuff and cleaning up the registry. i don't miss it at all. most of my time now is spent writing e-mails, surfing and writing stupid crap on the internet, and constantly redecorating my desktop. 

this was a refreshing thread, btw.

---

### Post by poofyhairguy on 2006-01-27
[QUOTE=dpack]
So I guess if I was the “standard home user” of Internet browsing, emailing, IM’ing, and maybe making a few documents and spreadsheets, Ubuntu would have been PERFECT. Applause! A stable OS free of viruses and spyware and that is also FREE. But I’m not a standard user with all the intricate projects I do.[/QUOTE]

I guess the most we can ask is that if you run across one of these "standard users" that is having trouble maintaining a Windows box, please install Ubuntu and Automatix on their system and send them our way.

Great post otherwise.

---

### Post by Iandefor on 2006-01-27
Hey, it happens. I'm really glad to hear that you listed specifically what it was your problem was; you have programs you need to use that are Windows only, and don't have any (acceptable, perhaps?) Free alternatives. You have hardware compatibility problems. Those are both perfectly good reasons for moving from one platform to another. 

[quote=dpack]So I guess if I was the “standard home user” of Internet browsing, emailing, IM’ing, and maybe making a few documents and spreadsheets, Ubuntu would have been PERFECT. Applause! A stable OS free of viruses and spyware and that is also FREE. But I’m not a standard user with all the intricate projects I do.[/quote] Ubuntu really is great for standard home use; again, you don't seem to have standard uses for your computer.

May I ask what applications you needed? I'm just curious.

---

### Post by dpack on 2006-01-27
It’s been a while since I used Ubuntu, but from memory the programs I could not get working under Ubuntu were AutoCAD 2000i, Citrix Web Client (I got it installed but wouldn’t work), Digital Media Converter, Flash MX, Ulead DVD MovieFactory, and Ulead VideoStudio. That is a lot of software I use but not software I use all the time, but I do use them. My hardware issues with my USB hard disk was really the axe to the situation ignoring the fact the Ubuntu rendered my scanner unusable.

I could do a dual-boot station if I added another hard drive to my system and do all the things in Windows I need to and then use Ubuntu for everything else, but why should I separate my PC in half just to use an OS when Windows does it all for me? I am just not ready to make sacrifices I don’t have to make in the first place.

Unfortunately, commercial software is being programmed for Windows based systems. I really do wish that it was 50/50 and just not biased towards Windows. But the people who make this software make it for what people use most and at this point in time, it’s not Linux.

But anyway, I don’t want to be drawn into a debate over this. I am most proud that Ubuntu does all that you need. It is about 80% of the way for what I need, but it just doesn’t cut the mustard for me yet. When it does, I would certainly love to use it because I really do miss it!

---

### Post by matthew on 2006-01-27
This was an intelligent, thoughtful post with appropriate amounts of detail and demonstrated an open mind. I wish Ubuntu would have been for the poster, but I think he has a great attitude and I wish him well.

---

### Post by dpack on 2006-02-20
After typing that big post at the beginning of this thread, I wanted to really see what I could do with Ubuntu at work. I am still an Ubuntu noob so I guess I can count this post as bragging on what I WAS able to accomplish with no more help than what&#8217;s posted under Ubuntu guides, Ubunti wiki, and this forum. So if I can do all the below with the sections I just mentioned, you guys have EXCELLENT resources for Ubuntu users of all experience levels.

I setup a test box behind my station and started hammering away at it. I installed Ubuntu clean using ext3. The easiest part of the whole project really. I won&#8217;t go into all the detail of what I did but here are the highlights.

1. Joined Ubuntu to Windows 2003 domain. Now any user in Active Directory can sign into Ubuntu.

2. Setup Ubuntu to mount all needed Windows shares on boot.

3. Connected to our network laserjet printer.

Okay, I&#8217;m on the network and can see everything I need and can print. COOL DEAL! Now comes the hard part! The applications! Keep in mind I am not a regular computer user at work. I am in IT so we run more applications than anyone else and applications no one else runs!

1. In Windows we use Citrix Program Neighborhood to connect to all of our published applications and desktops. I went to Citrix web site and d/l Citrix ICA Client for Linux. After installing some missing libraries I am in business!

2. For our billing system we use Kea application. I did not bother installing Kea under Wine because all it does is establish a telnet session. I pulled up Terminal and telneted right into our OpenVMS Alpha server and was rockin&#8217; and rollin&#8217;.

3. For all the Microsoft Office documents to deal with, OpenOffice handled all that with ease. No problems there.

4. We have an Exchange server for email. I brought up Evolution and found it already had the Exchange component installed. Within 5 minutes I was viewing my Exchange mailbox in Evolution. Sweet!

5. I do sometimes need to connect to Query Analyzer and Enterprise Manager for SQL Server. On my Windows machine I have the client tools installed. But, since I rarely have to jump into those programs now days, I can just RDP to the SQL server and do my thing there.

That&#8217;s everything I was successful with. Intuit&#8217;s Track-IT Enterprise 6.5 was not so forgiving. We use this software to log help desk tickets and do PO&#8217;s. I got it installed under Wine after mounting the Windows share it needs to talk to the server, but get an OLE registration error when trying to launch. So that&#8217;s out. It does have a web interface, but requires you use Internet Explorer. I can&#8217;t even run the web interface on my Windows machine using FireFox or Opera, even if Opera is set to identify as IE6.0. I found IEs4Linux and installed IE6.0 in Ubuntu. I get the sign in screen for Track-IT but can&#8217;t get past the prompts to install two ActiveX components. I manually created the Downloaded Program Files under the Windows Wine install and copied over the INF and Object files Track-IT needs. Still no dice, but I saw several other non-functioning components in the IEs4Linux browser. But that is not too bad. I could easily log the calls in a text editor or OpenOffice and then RDP to a Windows box and enter the tickets at the end of the day.

I have lost the ability to do a Remote Assistance with XP machines so I can only rely on RDP and taking over their session. A Win2000 machine I don&#8217;t have NetMeeting so it&#8217;s no connecting and just have to talk them through it. I can deal with that and only using RDP.

Here is the BIGGIE that I need that is not working. Being on the front lines of Help Desk, I HAVE to have the ability to connect to Active Directory Users and Computers so I can reset user passwords. I can&#8217;t install the 2003 AdminPak to Ubuntu. I did find the adtool in Synaptic Package Manager and successfully implemented it. My problem is ldap continues to bark at me with invalid credentials and I know I have things right.
You can follow that thread here that so far no one has answered:
[http://www.ubuntuforums.org/showthread.php?t=132009](http://www.ubuntuforums.org/showthread.php?t=132009)

My other issue is not being able to subscribe to or view sub-folders in Evolution for Exchange public folders. You can follow that thread here that so far no one has answered:
[http://www.ubuntuforums.org/showthread.php?t=130948](http://www.ubuntuforums.org/showthread.php?t=130948)

So not bad for a linux noob huh? LOL I can deal with not running Track-IT but not being able to connect to AD Users and Computers and not seeing sub-folders in Public Folders prevents me from switching at work.

--David

---

### Post by fuscia on 2006-02-20
one question i have about #7 - when one is signed into another user account on xp, other than admin, isn't that just another interface, rather than another account? is that the same with linux? (i'm not sure how to ask this, so forgive my being vague.)

---

### Post by dpack on 2006-02-20
You are signed in with another account. If you right click on "My Computer" and left click on "Manage" you'll get the Computer Management screen. Click the + sign beside Local Users and Groups and then click on the Users folder. This shows all the user accounts on the local PC. Only the users listed here (that aren't disabled) can sign into the local machine. If the station is on a domain, then it authenticates by users listed in Active Directory.

Only one person at a time can be signed into an XP machine unless you have Fast User switching turned on. This is not an option if you are on a domain.

So, no its not sessions. Each user account has its own profile. You can see all the profiles under Documents and Settings.

Hope that helps!

---

### Post by dpack on 2006-02-21
I just found a thrid reason I can't use Ubuntu at work. I can successfully mount all the needed network shares, but they are all NTFS drives. I can read them but can't write to them. Permissions are already set 777 but I have seen so many posts on the drives shared between Ubuntu and Windows needs to be FAT32. I can't go reformat our server drives! LOL

Well, at least it's nice to know it's not my Ubuntu noob ignorance on why I can't use it. I gave it a good run for its money though!

---

### Post by Jason_25 on 2006-02-21
Well if you are using SMB (windows networking) then it's no problem to write to a remote ntfs share.  Your PC isn't doing the writing.  You are the sending the file to that pc and it is using windows to write to the ntfs disk.  Your setup is incorrect.  Try not to make the assumption that just because you didn't get it to work, that it doesn't work.

---

### Post by dpack on 2006-02-21
Well, I followed this guide:
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

I set it up for read and write permission for everyone and gave it the credentials file for it to use. I did no assuming.

---

### Post by xequence on 2006-02-21
> 1. First things first, do a clean install of Windows! Don&#8217;t do OS upgrades! If you buy a new Windows OS, wipe that hard drive out and install clean.

I aggree fully :P

> 3. Install all Windows service packs and critical updates.

Have my computer go really slow and have it auto downloading stuff at random times that I dont choose, but microsoft does? No way, I always turn off automatic updates, and I use XP SP1 :)

But I use SP1 for a couple reasons, one being SP2 is aparently slower.

> DO NOT run your Windows account with Administrator privileges! Linux users don&#8217;t run as Root all the time do they? Of course not!

The non admin account on windows is severly crippled. In linux you can do sudo to do stuff, even though its annoying.

Do you honestly think I should log in and out to do anything? I install programs all the time, mess around in the program files and windows directory all the time, etc :)

> When you leave home you lock the door don&#8217;t you? Of course!

It is easy to lock your door. You loose very little conveinience. With a non admin account in windows you loose alot of conveinence and the ability to do anything.

> This is easy to combat once you have Windows locked down and using good software,

No anti virus, no anti spyware, and my computer runs great, except for the little slowness I have from it being XP on an older computer.

No offense though, and nice write up. Just stating my opinion =) I run as admin, no anti-anything, no updates or security thingys, and my computer runs like I just did a clean install. Mostly because I probably did just do a clean install, since I have a habbit of getting bored and switching to another version of windows (Im thinking server 2003 next :P), but thats not the point.

The point is your rules are good if someone doesent know alot about computers and OSes and stuff, but if someone does, they can easily not use your rules and have everything work fine.

:)

---

### Post by dpack on 2006-02-21
Yeah that's cool. I break my own rules too. What I wrote is for the Windows noobs. I run my account with admin rights and no spyware scanner. I do have a virus scanner but I really don't need it. My company runs McAfee Enterprise and I copied it and installed it using a perpetual license so I have free lifetime updates. Hell, I'm not even running ZoneAlarm right now! I configured the XP firewall to only allow Remote Desktop conenctions from my work IP's. But to each his own!

---

### Post by mstlyevil on 2006-02-21
[QUOTE=dpack]Yeah that's cool. I break my own rules too. What I wrote is for the Windows noobs. I run my account with admin rights and no spyware scanner. I do have a virus scanner but I really don't need it. My company runs McAfee Enterprise and I copied it and installed it using a perpetual license so I have free lifetime updates. Hell, I'm not even running ZoneAlarm right now! I configured the XP firewall to only allow Remote Desktop conenctions from my work IP's. But to each his own![/QUOTE]

You evil sinner!   ;)   :twisted:

---

### Post by imagine on 2006-02-21
[QUOTE=dpack]Well, I followed this guide:
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

I set it up for read and write permission for everyone and gave it the credentials file for it to use. I did no assuming.[/QUOTE]
Is root able to write (sudo touch somefile)? Forgot to set the uid?
This may sound stupid but are you sure that the folder is really shared with write access on the server side and you used the right username and password?

---

### Post by dpack on 2006-02-22
[QUOTE=imagine]Is root able to write (sudo touch somefile)? Forgot to set the uid?
This may sound stupid but are you sure that the folder is really shared with write access on the server side and you used the right username and password?[/QUOTE]

What's weird is it is only certain drives I can't write to. I can write to the IT share but cannot write to the Install share. And yet, looking at the security permissions set on the shares from within Windows they are setup identical. I am a member of the same group on both shares that has full control.

In Ubuntu, root is the owner but the drive is set to 777 so the owner, group, and others has full rights. I shouldn't have to set the uid to a different account other than root.

I did try to create a directory using the sudo command and it reported back to me saying it can't create the directory because permission is denied.

But, all this really doesn't matter since no one has a fix to my other two threads concerning sub-folders in Evolution and the adtool.

---

### Post by palomar on 2006-02-23
I can totally agree with dpack's opinion. In fact, the only reason that I'm running Linux is that I'm getting bored of using Windows for such a long time (since 3.11) that I'm just curious to other operating systems. Also at university we get stimulated to use open source/Linux. We are learning java, gimp, blender and text manipulation using shell commands on Linux systems. This also affects me a bit to use Linux at home. 

I do like the open source principle and the fact that software is free and very customizable (I am a real tweaker ;)). On several machines I'm now using Ubuntu a lot (my laptop and my second PC), but only on my 'main'-PC I keep running windows XP because of some software that doesn't run on Linux (like games, some multimedia formats, some software for studies purposes). I do have dual boot on that machine, but it's a bit radical operation to reboot every time, so I don't use linux much on my main PC. 

I also think the interface of XP (classic theme that is) is still superior to KDE or Gnome. It's more responsive, sharper lines, more clear etc.. Only with lots of custom settings I can get KDE a bit to my own taste (i.e. using windows fonts, LOL). That's also a reason I can't really get used to Linux window managers. I know there are others like XFC, WM etc. but they have poor functionality. On other site, I really like the console. For configuration tasks I don't need a GUI. The console is very powerful. 

To recapitulate, for tweaking/testing/fun purposes I like Linux very much. I keep learning more every time I use Linux again. But, for serious, productive purposes (and games) I am still using windows. I don't care it is Linux or Windows for browsing the web, building a website or typing a report. I just want results and Windows does this task on the most familiar and fastest way (at this time). Just like dpack I have never had any problem with windows XP. It's just my curiously (or inquisitively <- is this the right word? English is not my native language :)) in other OS'es than Windows. I think Ubuntu is great, but at this time i'm such a windows poweruser that I will and can not use Linux full-time. But I keep dedicated to Linux and keep using it :)

---

### Post by dpack on 2006-02-24
palomar, get ready to get flamed! ;)   LOL

For now I am finished testing Breezy Badger. But I am still anticipating the Dapper Drake release and will be one of the first ones dowloading the image file for it to play with.

Then I can be singing: "Hello my baby, hello my honey, hello my valentine!" \\:D/ 

And then after the release I get a ripped copy of Windows Vista and play with it too! :D

---

### Post by NinjaMidget on 2006-03-13
This is a good thread.   I knew and had already implemented all of your points with the exception of one...not working under the Admin account...duh!    It makes perfect sense to work under a standard user account, and XP makes it really easy to do things as Admin without logging out of your session.   Thanks for the tips

---

### Post by dpack on 2006-03-19
It's been a while since I've had to do any special projects. I just couldn't forget about Ubuntu though! I got too much of a good impression from it. So I have rebuilt my home system to continue my learning experience. I built it so I have the best of both worlds: Windows/Ubuntu, but Ubuntu is my main OS. I'll do everything in it that I can and the things I cannot, I'll reboot into XP. My system has two physical SCSI hard drives and I configured it this way:

SCSI Drive 1
Primary 1: 15GB NTFS (WinXP)
Logical 1: 20GB (FAT32 for sharing files between XP & Ubuntu, auto-mounted on boot)

SCSI Drive 2
Primary 1: 40GB ext3 (Breezy)
Logical 1: 3GB (Breezy Swap)
Logical 2: 30GB (NTFS – for special projects done in XP)

I have to tell ya, I've never been more excited about using any software package until Ubuntu! :D 

At the beginning of this thread I wrote the “how to secure and stabilize Windows” for the users who are forced to use it. Does anyone have tips along the same lines as my Windows guide for Ubuntu users I can follow? Just curious.

David

---

### Post by Horizon on 2006-04-16
Well i for one can feel your pain. Throughout my education i have been plagued with teachers that live and breath Microsoft Visual Studio and it really gets on my nerves. Why can't you teach us something else? Is C# and VB the only language there is? I'd personally love to learn something as useful as python. But i can see that's never going to happen, the closest they'll ever get away from Windows for anything non-web-based is Java. We learn about web design and even touch on apache but we can't even touch on Linux?

Well that's the end of my little rant, i just hope to god i don't end up having a job like yours which focuses specifically on Windows or at one of those companies that work ONLY with Microsoft lanuages. And with the way the education system is here in London,  where kids that are in higher education, which are being taught programming have only ever heard of Operating Systems other than Windows when the teacher had to give them a few arbitrary names for a certain test which *may* ask them to name more than two Operating Systems (Windows and DOS), i'd be lucky if i managed to keep myself from becoming "Microsoft Cerified".

LMAO nowadays they're even using those Microsoft Certifications in return for some cheap labour and ruining people's lives. They train you for a field of your choice for two months whilst you go to college and if you want to stay afterwards full-time (as in stop your education) you get a Microsoft Certification and get to finish your training. LMAO £1000 ($1700?) a month sounds good to most college students until it's a year later and they fire your *** and all you're left with is a Microsoft Certification and only enough knowledge to perform this one specific job that doesn't even exist anywhere else.

Well anyway for now, there's no way i can stop using Windows at home if i want to finish University. I mean sure i have formatted the windows partition to ext3 in a rage once but i spent the next two days trying to reinstall everthing in tears because Open Office wouldn't open that damn word document :evil: .

Ok Ok, really, this time my rant is over :p

PS: i really don't have anything against Microsoft, they're just doing what any company would do. That said i also think people have a right to dislike them for it, it's just human nature, heck it's just nature.  But i don't like how our education system is so skewed. And i'm not saying they should specifically teach Linux related things, just anything that isn't Windows Only(TM)

---

