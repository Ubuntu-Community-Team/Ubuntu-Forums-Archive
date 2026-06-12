---
title: "gaming server"
date: 2013-10-21
forum: Server Platforms
---

### Post by ddewit1989 on 2013-10-21
Hi   ):P

First time Linux user trying to learn how to get around in this Server environment.

I tried ubuntu desktop for my gaming pc last week , altho it was failure duo drivers not working properly.
I didnt gave up on linux but just moved the idea of using linux to my little server adventures ... sorta speak :P

Im a ICT student but its all boring and basic stuff about repairing Windows systems only.
We had a lesson of installing a Linux OS and use a textwrite program.   Just to show students there is more then Windows.
But it got my attention !


Sinds i was already using a old Pentium 4 system for hosting small Battlefield 1942 Modded server (On Windows XP)
It was easy and fun so i wanted to move this to a linux system..... pretty simple i tought just gotta figure out linux.




Wel now u know my motivation and level of expertise =)

This linux Noobs wants to build a Server for games like : Killing Floor , Terraria , Battlefield 1942 (only because i know how it works on windows) or some other fun old low demanding games for the server! 

Things i have so far:

I have a system !   Spec:

Pentium 4 2,8Ghz  (x2 core threats)
Asus p4p800 Deluxe
2Gb ddr 400mhz Ram
3x 80GB HDD's
1x 120GB HDD
9600 ATI radeon 256mb Videocard

Installed :  Ubuntu Server 12.04 with LAMP on its own HDD



Sinds i have multiple HDD's im not sure how or what im gonna use them for... suggestions are welcome ;)   
Anything like a Multiboot to run multiple different kind of server or something fun and interesting i can use for gaming , music , or videomedia....  anything ;) 

But for starter id like to use 1 HDD to create a simple Server for any of the above mentioned games (other game suggestions are welcome)

I like to know if what i installed as server OS is a good choice for my goal?  And are there other Distro's that are more suiteble? 

And id like to find some BETTER guide on how to install server software from Steam (i know this is totaly off-topic , so skip this question if u want)

And id realy want to know how to browse or look at my Folders i created (because i forget certain directories i was trying to get working last week) 



Thanks for reading this , i hope u can help into the right direction because im only hitting Brick walls in every direction im going xD

---

### Post by TheFu on 2013-10-21
Servers don't have a GUI, so there is no "browsing" of directories as you think.  Find a UNIX/Linux CLI tutor and spend 30 minutes learning cd, ls, chmod, chown, sudo, du, df, history, tab completion, and other commonly used commands.

Learn to read "man pages" - which has all the answers to every question. They are on the machine already. 'man man' to learn more.

Learning to run a Linux server is like learning a new language.  You've just gone to China and need to learn Mandarin - best to find someone local to help.  There are LPIC books and online training, but the most recent books I've seen have incorrect information.

I don't game at all.  I don't think steam works on "server" - doesn't it require a GUI?

YOU need to unlearn all the bogus stuff you've been taught from MS.  Linux is NOT Windows. There is a very different overall philosophy for UNIX and Linux systems. I hope this link helps explain: [http://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed](http://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed) some of that required thought shift.

---

### Post by SGAZ on 2013-10-21
If you already have the Server up and running probably your best bet for getting the games served up is to look into the relevant Game Forums or Google "[Game] server Linux install".
The trick might be finding the install files for "Old Games".  Of Course, check the Repos.

Generally, the limitation is how many players you can have at once based on CPU and RAM. Each game should have that sort of info in the SysReqs.  I don't believe game servers really require too much disk space.
You also may want to look into a Dynamic DNS host to get yourself a Domain that can be updated to your (I assume) Home based DHCP IP your ISP gives you. That way you can play against friends from beyond the LAN and they were free for what you seem to have in mind last I checked.

I've got a machine setup to run ETQW (all of the "ET"s should have plenty of documentation for Linux servers.) and I run a Murmer/Mumble Com server as well.  

I separate the different servers out into the different TTY Terminals to run as much or little as desired.  (I think that would address your "Multiboot" comment)

I like to keep a GUI on my server for when I don't want to have to think or just edit a Conf File like I would on any other computer but you'll definitely want to do as TheFu said and take the few minutes to learn the CLI commands as that is all you'd want to use to run your DynDNS update, start/stop Com Server & Game Server. 

Have fun!

---

### Post by ddewit1989 on 2013-10-21
Thanks for that link TheFu
From what i understand i type in( Man Man ) in the system for more info?
And [COLOR=#000000]UNIX/Linux CLI tutor , is that a tool you are talking about or a teacher :3 ?

I get the idea its pretty neat actualy reading that.

But cant i also just create a dual boot a server Ubuntu and a one with a Gui =)  i like to actualy use the system ,cant i install a dual boot with another Server with Gui? or Desktop version ?[/COLOR]

---

### Post by outofnicks on 2013-10-22
You can use the Desktop version as a server, you still may need to learn the command-line in the terminal.
You really need to connect up with people who have hosted the games you want on Linux, just search for "hosting [game name] Linux" on google or in these forums. Games generally have a client version and a server version, you want the latter. You might just find something in Synaptic Package Manager, use the search box at the top.

---

### Post by TheFu on 2013-10-22
> **ddewit1989 said:**
> Thanks for that link TheFu
From what i understand i type in( Man Man ) in the system for more info?
And [COLOR=#000000]UNIX/Linux CLI tutor , is that a tool you are talking about or a teacher :3 ?

I get the idea its pretty neat actualy reading that.

But cant i also just create a dual boot a server Ubuntu and a one with a Gui =)  i like to actualy use the system ,cant i install a dual boot with another Server with Gui? or Desktop version ?[/COLOR]

A few answers and opinions : 

"find" ---> insert "use whatever search engine you like to find it online."  That could be a person or a website or a book or whatever that has "tutor CLI" on the page returned.

"man man" - it is case sensitive - ALL FILES ON UNIX/LINUX are CaSe SenSitivE. Case, CaSE, case, and caSE are each different files. Programs, data, configurations, settings, devices, and virtual file systems - all case sensitive. Know it, use it, love it.

You can do whatever you like, if you have the skill. It isn't my place to say what cannot be done. The code is available for you to build on - have fun!  Often, it isn't even a coding thing, just enough skill to modify the config and/or get the necessary software installed.  

Dual Booting - I stopped dual booting in any significant way in the 1990s - been using virtual machines ever sense. Once in a while, I have to boot some other OS on a machine for some reason ... BIOS updates, to check spinning HDDs for errors, to fix an NTFS partition ... IMHO, dual booting has caused more issues than almost any other technology commonly used with Linux-PCs.  Lots of people completely wipe their OS - I've seen it .... recently ... like ... 2 weeks ago.  Smart people wipe their HDD without having good backups all-the-time.  Please don't be one of those people.  One guy posted here asking for help. He had never tested his restore process, but had been backing up over a year.  Huh?  Backups are 10% of the job ... Restores are 90%. A backup that cannot be restored is ... er ... just creating heat and of little other use.

Yes, you can run a desktop on a server or a server on a desktop. For toy systems, fine.  IMHO, if you are going to run a server, then RUN A SERVER.  Learn the skills that make it possible to manage a server anywhere in the world - no GUI. I suspect lots of people will disagree with me on this.  For servers, system availability is important. The more software you add to it, the more likely it is to have a failure that impacts availability.  Not good in the real world, perhaps this is fine for a dorm room, but I'd be fired over something stupid like that. Learn it sooner than later.  Some systems matter to 1 person, others matter to millions. It isn't always clear which is which and it isn't clear which costs more $$$ when it is down - sometimes that single person is performing stock trading worth $10M+ daily.

I didn't really tell the truth about my gaming.  I used to run a TF server long ago. Eventually, I became interested in other things - must have been 10+ yrs ago.  Also hosted LAN parties at the compound - a few friends would come over and we'd kill each other and talk smack. Good times, until we got married, kids, dogs, responsibilities. Life moves forward, right?

So - you can do whatever you like with your stuff. The best lessons are learned thru failure.  I've failed many times.  As I drop in a few new HDDs this week to one of the systems here, I expect in 2-4 yrs, that I won't be happy with some of the decisions made. Oh well.  Partitioned with GPT and loaded LVM2 on the drives for the added flexibility. OTOH, only Linux can use that, so is it really more flexible?

You get the point. ;)

---

