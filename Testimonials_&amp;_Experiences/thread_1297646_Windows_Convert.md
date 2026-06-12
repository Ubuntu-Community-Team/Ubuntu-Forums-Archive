---
title: "Windows Convert"
date: 2009-10-22
forum: Testimonials &amp; Experiences
---

### Post by PaulInBHC on 2009-10-22
I read with interest the news of IBM and Canonical packaging Ubuntu with software for the mass market. I recently installed Ubuntu along side of XP Home SP3.

Some history, bear with me. I started working in auto parts in 1970. I saw card files, punch cards, inventory paper pads, 300 baud thermal printers, 1200 baud dot printers, CRTs, mainframes the size of refridgerators with reel tape backups, and so on to today's web based cataloging. DOS, Unix, Solaris, Windows.

I got burned by XP in 2002 when it would barely run on a computer with the stated minimum specs. Loved the OS though compared to 98 and ME. 

Built a computer in 2002 for XP and again in 2004. A few weeks ago, something happened to XP on the 02. A coworker had been touting Ubuntu and since I had been using Open Office and Firefox, it seemed like a dual boot was worth a try.

I'll try to keep this short. Followed 9.04 instructions to install. Could not figure out manual partitions, allowed automatic install. OS starts, popup for update, not enough space to update. Back to XP, google uninstall, fix mbr, google and read some more. Find intructions for 8.04 that lay out  step by step much better. Installed Ubuntu again , worked with it. Tried to drag a bookmark from the dropdown in Firefox and locked up. Back to XP, google, uninstall, reinstall. Repeat Firefox bookmark mistake. This time I go through the agony of trying everything to fix my XP. Finally move important bits to the D: partition and reinstall XP. Now the horror of trying to reinstall Ubuntu. No OS found. Finally after 2 plus weeks of reading and searching and trying all is well. Sort of.

I don't understand why I had to download 221mb of updates after installing from an ISO that I just downloaded? Also, why isn't there and firewall and anti virus preinstalled? On XP, Avast runs in realtime. I can't find one like that for Ubuntu. Why is Firefox and Open Office at 3.0.x when I have 3.5.3 and 3.1 on XP?

I had to learn alot to install games and such in Windows but it is quite a chore in Ubuntu if you want the latest version.

I am writing all of this because I want Ubuntu to succeed and grow. Like the IBM project, I have boxes that are not keeping up with the demands of newer games and webpages with demanding graphics. I'm not going to buy a new computer any time soon with the current economy. I'm glad I didn't have Vista and don't care to see 7.

The whole process is going to have to get more user friendly if the goal is to be mainstream.

I thank you for my new OS and wish you much success. Looking forward to 9.10

paul

---

### Post by Dark_Stang on 2009-10-22
There is an IP Tables firewall built in and you don't need an antivirus on Linux. Windows is the only OS that actually has major virus issues.

How are you installing? Booting off live CD or using Wubi? Also, that CD image is several months old which is why you update. Same as windows or Mac or solaris. And if you are installing off the Live CD I find the built in partitioner for Ubuntu (gparted) is MUCH more friendly and robust than the partitioners built into XP, Vista, and 7.

Also, your machine from 02. Something happened to it and now Linux isn't working either...? Is that right? Are you sure you don't have a failing hard drive?

---

### Post by SkyNet2029 on 2009-10-22
Hello and welcome to ubuntu. Glad you took the plunge. A few things though.
The downloading of updates after installing from a .iso file you just downloaded:
 
Ubuntu releases .iso files for download. Sometime between when that .iso was first pushed out onto the web, there are numerous security and patch updates that are released. Ubuntu downloads these to ensure you have the most recent software available for your distribution.
 
Antivirus...
Linux is not like windows. There are a few (in the lab) viruses for linux, but it is a hostile environment on the whole and does not need the constant antivirus of windows.

---

### Post by martrn on 2009-10-22
> **PaulInBHC said:**
> I don't understand why I had to download 221mb of updates after installing from an ISO that I just downloaded? Also, why isn't there and firewall and anti virus preinstalled? On XP, 

I had to learn alot to install games and such in Windows but it is quite a chore in Ubuntu if you want the latest version [..]I thank you for my new OS and wish you much success. Looking forward to 9.10

You have answered your own question, albiet that you possibly didn't realise it such.  

Ubuntu is updated fast and furious, particularly relating to security updates and fixes.  The 221mb of updates, will include some of which are security fixes.

Look at the situation differently, in an open environment where the source code is open you have a lot more eyeballs looking at the security of the software. That means there are more people looking at the code to find security problems that their would otherwise be in a closed source environment.  For the long therm this means there are less security loopholes, although there will be more updates than in a closed source environment.  The free with ubuntu means as in freedom, not as in cost.

Why would you need an anti-virus (or perminant ant-virus) if the system is more secure ?

RE: [COLOR="Silver"]"..The whole process is going to have to get more user friendly if the goal is to be mainstream..."[/COLOR] Is it really that non user friendly as you make out or are you just having a more difficult time picking up a new operating system. ?? If at a guess I would say the latter.

There is a lot more power in an ubuntu system than windows, click --> click --> click --> click --> click --> click --> click --> click 
 ----- arrrggggghhhhhh.

---

### Post by ad_267 on 2009-10-22
Ok so it looks like you got your installation problems sorted. I have to say it shouldn't usually be that hard though. You can use the guided installation but you have to make sure you give both Ubuntu and Windows enough space each.

There is a firewall running by default but it isn't configured to do much. There's also no anti virus because there aren't any Linux viruses in the wild. The only reason to run an anti-virus is when you're sharing a lot of files with Windows users.

There are a lot of different applications that go into Ubuntu, and the developers make sure everything works well together for each release. Software usually only receives security updates throughout the lifetime of a release in order to keep everything running smoothly. If you want the latest and greatest all the time then try a rolling release distribution, or always use the testing version of Ubuntu. You can also add separate software sources, called PPAs, to get newer versions of certain software.

---

### Post by PaulInBHC on 2009-10-22
Thank you for the replies. All is well at the moment and I left out the gory details on my install story. The good news is that it (Ubuntu) was quick and easy once I figured out what was wrong. XP on the other hand, took hours to reinstall the OS, SP1, SP2, SP3 and on and on...
If I wasn't on beta teams for some Windows games with managed .net and DX I probably would have formatted the whole drive.

I still have my copy of Windows 98 for Dummies. Maybe someone will do an online version for Ubuntu.

---

### Post by ad_267 on 2009-10-22
There's the Ubuntu pocket guide, which can be downloaded for free: [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

It's probably also a good idea to read this page too: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware). There are some other good tutorials at that site too.

---

### Post by craig10x on 2009-10-22
You can install the gui version of the Ubuntu firewall, using the program GUFW which you will find in both package manager and also the Add/Remove programs directory....just type GUFW in the search or the word Firewall....

Once installed, you will find it under  "System" "Administration" "Firewall Configuration"  then you can simply turn it on...and there is also advanced settings if you desire (though i personally don't use them)....

As far as Virus Scanners...not needed on Linux....it's nothing like Windows at all in that regard....it's a VERY SECURE SYSTEM...unlike Windows....much like the Mac OSX system..probably even better..... :)

Old windows habits are hard to break...aren't they?  (lol)....
Congratulations and Welcome to the SECURE and STABLE world of LINUX and UBUNTU...

I'm fairly a newbie myself..but have been on it for about 6 months now...started with a WUBI 8.10 and the went Ubuntu 9.04 full hard drive install and decided to wipe out windows completely...don't miss it a bit ;-)

---

### Post by ibuclaw on 2009-10-22
The first 3 months of using a new operating system always conjures teething issues.

When I started out on Debian Woody, my first three months of using Linux were in the terminal (I dropped Windows cold turkey, and used nothing but Linux and man - latter the internet once I figured out how to setup wireless), as I was learning / reformatting / re-installing / trying to setup and configure my system on a near daily basis.

But, I had the time and the optimism back then.

There are still some things around in the installation process that assume you already know what to do (as you mentioned, partitioning). And you are probably aware now that you use the 'Partition Manager' to manage the partitions **before** you install, and select 'Manual' when the ubiquity installer asks you how you'd like to format your disk.

But it is still easier now, in comparison to how it was 3-4 years ago.

---

### Post by Tibuda on 2009-10-22
> **PaulInBHC said:**
> I don't understand why I had to download 221mb of updates after installing from an ISO that I just downloaded?
This is easy to answer that ISO was built in 200**9** april (**04**). We got six months of security updates in meantime.

> Why is Firefox and Open Office at 3.0.x when I have 3.5.3 and 3.1 on XP?
You can grab the last version from those apps website, but Ubuntu itself only provides and supports (this includes security fixes, which are backported) the version from the date when the Ubuntu version was released (or freezed). Major updates may bring incompatibilities (eg my bank have a security firefox addon that don't work with 3.5).

---

### Post by Mike_IronFist on 2009-10-22
> **PaulInBHC said:**
> 

I don't understand why I had to download 221mb of updates after installing from an ISO that I just downloaded? Also, why isn't there and firewall and anti virus preinstalled? On XP, Avast runs in realtime. I can't find one like that for Ubuntu. 

Antivirus...for...Ubuntu? AHAHAHAHAHAHAHAHA!

Viruses don't exist on Linux and never will. Unlike Windows, Linux is extremely virus-resilient and doesn't need much additional protection.

> **PaulInBHC said:**
> Why is Firefox and Open Office at 3.0.x when I have 3.5.3 and 3.1 on XP?

I had to learn alot to install games and such in Windows but it is quite a chore in Ubuntu if you want the latest version.

I am writing all of this because I want Ubuntu to succeed and grow. Like the IBM project, I have boxes that are not keeping up with the demands of newer games and webpages with demanding graphics. I'm not going to buy a new computer any time soon with the current economy. I'm glad I didn't have Vista and don't care to see 7.

The whole process is going to have to get more user friendly if the goal is to be mainstream.

I thank you for my new OS and wish you much success. Looking forward to 9.10

paul

If you're worried about installing newer versions, you should be worried about what the developers of those apps do, rather than the makers of Ubuntu themselves. What's bundled in XP? Internet Explorer, Windows Media Player, some low level tools like Notepad, etc. All stuff made by Microsoft.
Ubuntu is made up from other peoples' software, and thus, with software versions, it frankly doesn't work like it does on XP. Canonical doesn't make Firefox, so they don't really push out updates for Firefox, etc.

The developers make newly-updated versions of apps for what OSes they want to make them for. Just because the developer makes the installer for their new program easy to use on Windows doesn't mean that it's thanks to Windows. The developer can make an installer just as easy to use on Ubuntu as it is on Windows, or even easier. It's possible to get the latest OpenOffice for Ubuntu in a .deb package much like a Windows .exe package, from the OpenOffice website.

But Ubuntu has a new version every 6 months. That's a whole new batch of software, every six months. It's actually far more up-to-date, and faster, than Windows is when it comes to technology.

As for the 221MB of Updates, try a fresh install of XP with no preinstalled service packs, and then updating. It takes more than 2 GB to do so. I mean the newest version of Ubuntu, with all the latest software, comes out in a week. So the reason you had so much updating to install was because you're getting updates to an OS version that's about to be displaced and made obsolete by the newest version.

---

### Post by solwic on 2009-10-22
> **Mike_IronFist said:**
> Antivirus...for...Ubuntu? AHAHAHAHAHAHAHAHA!

Viruses don't exist on Linux and never will. Unlike Windows, Linux is extremely virus-resilient and doesn't need much additional protection.


Actually there are viruses for Linux, and you can get a virus on Linux.  You just have to try really, really hard to first catch it, and then let it infect your system.  :P

---

### Post by Mike_IronFist on 2009-10-22
> **iRun said:**
> Actually there are viruses for Linux, and you can get a virus on Linux.  You just have to try really, really hard to first catch it, and then let it infect your system.  :P

Hahahaha! That's true. If you WANT a virus, you can get one. Now THAT's user control!

---

### Post by solwic on 2009-10-22
> **Mike_IronFist said:**
> Hahahaha! That's true. If you WANT a virus, you can get one. Now THAT's user control!

:biggrin:

---

### Post by running_rabbit07 on 2009-10-22
Firefox 3.5 can be installed with this ```
 sudo apt-get install firefox-3.5
``` It will install alongside the FF 3.0, but works great.

You can install Fire Starter which is the Ubuntu Firewall with ```
sudo apt-get install firestarter
```And ClamAV can be installed with ```
 sudo apt-get install clamav
```ClamAV is a command line tool. To add the GUI tool use ```
sudo apt-get install clamtk
``` For better functionality and nicer fonts, you may want to install Ubuntu Restricted Extras ```
sudo apt-get install ubuntu-restricted-extras
``` (add the x or k in front if you are using Xubuntu or Kubuntu)
You can also install all of the above programs within Synaptic Package Manager.

---

### Post by solwic on 2009-10-22
> **running_rabbit07 said:**
> Firefox 3.5 can be installed with this ```
 sudo apt-get install firefox-3.5
``` It will install alongside the FF 3.0, but works great.

You can install Fire Starter which is the Ubuntu Firewall with ```
sudo apt-get install firestarter
```And ClamAV can be installed with ```
 sudo apt-get install clamav
```ClamAV is a command line tool. To add the GUI tool use ```
sudo apt-get install clamtk
``` For better functionality and nicer fonts, you may want to install Ubuntu Restricted Extras ```
sudo apt-get install ubuntu-restricted-extras
``` (add the x or k in front if you are using Xubuntu or Kubuntu)
You can also install all of the above programs within Synaptic Package Manager.

Firestarter is old.  Isn't there a newer version of the front-end for iptables?

---

### Post by running_rabbit07 on 2009-10-22
> **iRun said:**
> Firestarter is old.  Isn't there a newer version of the front-end for iptables?
I don't know, that's just what I have been using. If I ever suspect foriegn traffic, I start up WireShark and see what packets are moving. Install Wireshark with ```
sudo apt-get install wireshark
``` and then you can watch all of your communications within your local network.

I love all of this free sh*t in Ubuntu. (Wireshark is free for all OSes, but last I tried, it would not run on 64 bit Windows 7.)

---

### Post by HappyFeet on 2009-10-22
Clamav is one of the worst virus scanners available. Don't waste your time. [AVG for Linux]("http://free.avg.com/ww-en/download?prd=afl") is much better.

---

### Post by running_rabbit07 on 2009-10-22
> **HappyFeet said:**
> Clamav is one of the worst virus scanners available. Don't waste your time. [AVG for Linux]("http://free.avg.com/ww-en/download?prd=afl") is much better.

I know bitdefender is great, too. After watching a friend's system go down while using the free AVG, I don't trust it anymore. That is bound to happen on any Windows system though. Thanks for bringing that up though. I've only done on scan in the past 5 months.

---

### Post by Tibuda on 2009-10-22
> **HappyFeet said:**
> Clamav is one of the worst virus scanners available. Don't waste your time. [AVG for Linux]("http://free.avg.com/ww-en/download?prd=afl") is much better.

I don't use an AV in Linux, so I don't know if this applies to AVG for Linux, but AVG for Windows is annoying.

---

### Post by Tibuda on 2009-10-22
> **iRun said:**
> Firestarter is old.  Isn't there a newer version of the front-end for iptables?

[gufw]("apt:gufw") is a Gtk+ frontend for **ufw** which is a cli frontend for iptables.

---

### Post by craig10x on 2009-10-22
Avast (linux version) would probably be better, assuming it is anything like it's Window's version (which is excellent i found when i was on Windows)....

However, i really can't see the need for it...since Linux doesn't really have any problems with viruses or malware and adaware.....

I certainly can understand that coming from Windows...you feel somehow you are "naked and exposed" if you don't add on some kind of virus scanner....but not to worry...you can read various articles on the internet which technically explain how Linux is vastly different from Windows and doesn't have the vulnerability that Windows does for that type of problem...

GUFW is a nice simple program to activate the Built in Linux Firewall...even that's not really needed..but i just like to turn it on....and it does make you "Stealth"  (i know cause i checked it on one of those "test your firewall" sites....LOL) :)

---

### Post by running_rabbit07 on 2009-10-22
> **craig10x said:**
> Avast (linux version) would probably be better, assuming it is anything like it's Window's version (which is excellent i found when i was on Windows)....

However, i really can't see the need for it...since Linux doesn't really have any problems with viruses or malware and adaware.....

I certainly can understand that coming from Windows...you feel somehow you are "naked and exposed" if you don't add on some kind of virus scanner....but not to worry...you can read various articles on the internet which technically explain how Linux is vastly different from Windows and doesn't have the vulnerability that Windows does for that type of problem...

GUFW is a nice simple program to activate the Built in Linux Firewall...even that's not really needed..but i just like to turn it on....and it does make you "Stealth"  (i know cause i checked it on one of those "test your firewall" sites....LOL) :)

The only reason I run AV on my system is to protect the files I share with Windows systems.

---

### Post by solwic on 2009-10-22
> **danielrmt said:**
> [gufw]("apt:gufw") is a Gtk+ frontend for **ufw** which is a cli frontend for iptables.

Yeah, that's it.  Couldn't remember the name.  

Thanks.  :)

---

### Post by PaulInBHC on 2009-10-22
Wow I didn't expect this many replies. Lots of enthusiasm here.

I had some false starts but now understand the Synaptic package manager and a few other tools. I saw today how the auto update works. I did not see Firestarter installed and installed it myself. I look for better things after 9.10.

Thanks for the sudo posts. I tried to install clamav and the GUI is there but I'm not sure it is working. I think I'll go with the Avast as that is what I use in windows. Recently a game website had it's banner ad hacked. When I went to the site, Avast popped up that it stopped a redirect from a malicious site. Another fellow had Norton and got a nasty infection. Can this happen with linux?

I read the release notes for 9.10 and see some good things coming. It will take me a while to get used to the terminal lingo and abreviations. So did DOS et al.

I still suggest that you read through the 9.04 install instructions webpage with a mindset that you don't know anything about linux. Then read the 8.04 page and see the difference. I've trained, taught, mentored people and sometimes the master skips what he assumes the student knows, only to find out that the student doesn't have a clue.

---

### Post by HappyFeet on 2009-10-22
> **danielrmt said:**
> AVG for Windows is annoying.

AVG for windows is only 1/10th as annoying as Norton or McAfee though.

---

### Post by HappyFeet on 2009-10-22
> **PaulInBHC said:**
> Another fellow had Norton and got a nasty infection. Can this happen with linux?


*Highly* improbable. I tell people that I compare it to getting struck by lightning. Sure, it can happen, but what are the odds? Or better yet, you'll probably win the lottery before you get a virus in linux. I search all the linux news sites everyday, and have never heard of anyone getting one. Anti-virus in linux is a waste of resources, if you ask me.

The only linux users that might benefit from an anti-virus, are those that will be passing on downloaded files to windows machines.

---

### Post by HappyFeet on 2009-10-22
> **PaulInBHC said:**
> 
I still suggest that you read through the 9.04 install instructions webpage with a mindset that you don't know anything about linux. Then read the 8.04 page and see the difference.

Once you've done a few installs and figured out the file system, they are all pretty much the same. I can do linux installs in my sleep at this point.

---

### Post by craig10x on 2009-10-22
gotta go along with HappyFeet...if it's going to make you feel better...put on that virus scanner....but it's really just a waste of resources on Linux and really unnecessary....

A windows virus cannot infect Linux, and while it is possible to pass it on to a windows computer, i'd assume that anyone you would be sending something to who has a windows computer, already has a virus scanner on their computer, anyway.....

While i don't have a scanner on mine, so technically i can't confirm..i can tell you that i have been on Ubuntu for like 6 months now, and my computer hasn't done anything funny...slowed down in performance... got "hijacked" to  a website...programs operating strangely, or anything that would give any indication of having anything bad running around in the system....

So, i'd say, if you do it...it's main purpose for you would be just to make you feel good (lol)....and that would be about it ;)

Probably, another thing that will shock you (coming from Windows) is that Linux doesn't need a defragger either.....and doesn't need any maintenance like Windows to keep it running at peak performance.....I know..hard to break those old "windows habits".....you are actually in a different "world" now, so to speak

---

### Post by PaulInBHC on 2009-10-22
lol I was going to look for a defragger. Thanks for that tip. I hear it cleans itself too.

Now if I can find drivers for my Microsoft mouse and keyboard, strangely, MS doesn't offer any.

---

### Post by HappyFeet on 2009-10-22
> **PaulInBHC said:**
> Thanks for that tip. I hear it **cleans itself too**.
Not quite, but every once in a while do:
```
sudo apt-get clean && sudo apt-get autoremove
```

> **PaulInBHC said:**
> 
Now if I can find drivers for my Microsoft mouse and keyboard, strangely, MS doesn't offer any.
Why? What's not working?

---

### Post by PaulInBHC on 2009-10-22
Both are PS2 wired, MS Natural Multi Media keyboard and MS Comfort optical mouse 3000.The only thing that I use on the keyboard is the volume control and mute, those both work. ctrl + alt + del does not, lol, jk. I do remember going from an Apple IIe to a PC and realising that it is the same as open apple closed apple delete.

My mouse has a side button that opens a magnifying window. It does not work. I do not see a scroll speed adjustment either.

---

### Post by cariboo on 2009-10-22
> **PaulInBHC said:**
> lol I was going to look for a defragger. Thanks for that tip. I hear it cleans itself too.

Now if I can find drivers for my Microsoft mouse and keyboard, strangely, MS doesn't offer any.

I use [this]("http://www.microsoft.com/hardware/mouseandkeyboard/productdetails.aspx?pid=043") keyboard and [this]("http://www.microsoft.com/hardware/mouseandkeyboard/ProductDetails.aspx?pid=112") mouse. The only thing that doesn't work on the keyboard is the zoom, and the mouse works as it should without having to install any drivers.

---

### Post by namluc on 2009-10-22
PaulInBHC

I first used ubuntu 6.06, Dapper Drake, for about six months or so. Then I came back to using it about six months ago. 

I found it really really quite difficult, it only took a lot of reading and rereading and trial and error, accidental xp wipes and reinstalls before I can say i feel comfortable with it. I've never had any formal training in computers, but definately was not scared of them either, otherwise i never would have touched the dapper drake installer!

Reading your posts, and talking to my friends i realize how far i have come, although i can't remember off hand many sudo commands, i am fairly comfortable with the computer now, and if it weren't for open office to word formatting issues, would be recommending this operating system to everyone i met! But it is true that I have ended up learning much more about computers than i ever planned on before i had heard of ubuntu!

Doing this, i've realized how difficult it is to learn something quickly and effectively over the internet, rather than have a teacher stand over ones shoulder.

now i have learnt that as soon as i have a problem i google it, then i google.co.uk it, then google.co.za it, until i get an answer. Because someone has more than likely had the same problem as me before me! The free downloadable book that someone has already showed you is also good to boost familiarity. 

If you are like me, you may be lucky enough to find that this operating system lets you do things you really really needed but other os' designers had never even considered as worth doing!

I downloaded karmic koala the other day, and unlike my windows7 beta, it isn't going to deactivate itself next year!

welcome to free software!

---

### Post by PaulInBHC on 2009-10-24
Thanks for all the posts.

I installed 9.10 RC just now as a new install. It took an hour and a half. I changed my C: and D: and ext3 partiion sizes to make free space for ext4. The ntfs changed in a few minutes. The ext3 took about 25 minutes. Overall would have been quicker had I hit the skip button for the languages download.

How do I get ride of the awful pink or lavender colour of my webpages?

---

### Post by HappyFeet on 2009-10-24
> **PaulInBHC said:**
> 
How do I get ride of the awful pink or lavender colour of my webpages?
Screenshot?

---

### Post by PaulInBHC on 2009-10-24
Fixed it with the on screen monitor settings for the monitor. Don't know what it will look like when I go back to 9.04 or XP.

I spent a couple of hours looking for drivers for ATI Radeon 7000 and Cat Control center. I thought it was a gamma problem. No linux drivers from ATI and the open source didn't change anything.

Edit, my mouse scroll is now at a good speed. I think it is because of FF 3.5

---

### Post by stinger30au on 2009-10-24
> **PaulInBHC said:**
> 

I don't understand why I had to download 221mb of updates after installing from an ISO that I just downloaded? Also, why isn't there and firewall and anti virus preinstalled? On XP, Avast runs in realtime. I can't find one like that for Ubuntu. Why is Firefox and Open Office at 3.0.x when I have 3.5.3 and 3.1 on XP?


if it makes you feel better a few weeks ago for my birthday my wife gave me  brand spanking new toshiba l500d laptop with vista 64 on it

it downloaded almost 700 meg of updates when i finished setting it up

---

### Post by PaulInBHC on 2009-10-24
I remember the XP upgrade stating minimum 1.5g for install. I now have close to 7g after a fresh install plus SPs, Zonealarm and avast. No custom drivers either.

HappyFeet, I restarted, went into XP, couldn't remember why, back to 9.10. Now my system monitor opens in a box full of plaid. I can get tooltips for window and close. I'm hoping another restart will fix it. It worked the first boot after install and 9.10 is using a lot less resources. yippee

---

### Post by running_rabbit07 on 2009-10-24
> **stinger30au said:**
> if it makes you feel better a few weeks ago for my birthday my wife gave me  brand spanking new toshiba l500d laptop with vista 64 on it

it downloaded almost 700 meg of updates when i finished setting it up

Most people don't realise that until they have done it. That doesn't make anyone any less of a person though. Ubuntu is awesome.

---

### Post by twright on 2009-10-24
> **PaulInBHC said:**
> Both are PS2 wired, MS Natural Multi Media keyboard and MS Comfort optical mouse 3000.The only thing that I use on the keyboard is the volume control and mute, those both work. ctrl + alt + del does not, lol, jk. I do remember going from an Apple IIe to a PC and realising that it is the same as open apple closed apple delete.

My mouse has a side button that opens a magnifying window. It does not work. I do not see a scroll speed adjustment either.
The basic feature of all recently modern keyboards should work out of the box however all of the shortcut keys are not necessarily set to do anything by default and ctrl+alt+del does not do anything on Linux anyway. As for magnifying you can just do this by holding the control key and using the scroll wheel - you can control other settings in Mouse in preferences.

Good luck with Ubuntu and I hope you continue to enjoy Karmic as much as I am :-) .

---

### Post by PaulInBHC on 2009-10-24
You missed the lol and just kidding in my post about ctrl alt del.

I just tried the zoom and glad I found the reset. The button on the mouse is a nice feature sometimes but I'll live without it.

So far Karmic pluses include: newer versions of Firefox, Wine, and Wesnoth. I like the new Software Center.
minus: I had to figure out to install mplayer to get a radio station media player working. It worked fine in jaunty.

---

### Post by ibuclaw on 2009-10-25
> **PaulInBHC said:**
> You missed the lol and just kidding in my post about ctrl alt del.

I just tried the zoom and glad I found the reset. The button on the mouse is a nice feature sometimes but I'll live without it.

So far Karmic pluses include: newer versions of Firefox, Wine, and Wesnoth. I like the new Software Center.
minus: I had to figure out to install mplayer to get a radio station media player working. It worked fine in jaunty.

There are ways of detecting whether or not the mouse is working at a hardware level.

If it is, then you can configure the desktop to perform a certain action when that signal is received.

If I am correct in my understanding, and it is a mouse action that isn't working, this should show the information you need:
```
xev | grep -A3 ButtonPress
```

Put your mouse into the window, and try the action.

Regards
Iain

---

### Post by PaulInBHC on 2009-10-25
I don't get anything with any button in the window, in or out of the black box.

---

### Post by PaulInBHC on 2009-10-30
I guess I was pretty lucky with my 9.10 install. Lots of people complaining of problems. Glad I did a fresh install instead of the upgrade.
Now that I've had some time with ubuntu, happy I did it. I haven't gone back to XP and am ready to gobble up the disc space that 9.04 is taking up. Not going back.
I've just read the first chapter of the pocket guide. There still is not a better description of manually partitioning than this
[https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html)
I don't know what happened after 8.04 to muddy up the instructions.
Thanks to those who did all the work for me.

---

### Post by frank cox on 2009-10-30
> **martrn said:**
> You have answered your own question, albiet that you possibly didn't realise it such.  

Ubuntu is updated fast and furious, particularly relating to security updates and fixes.  The 221mb of updates, will include some of which are security fixes.

Look at the situation differently, in an open environment where the source code is open you have a lot more eyeballs looking at the security of the software. That means there are more people looking at the code to find security problems that their would otherwise be in a closed source environment.  For the long therm this means there are less security loopholes, although there will be more updates than in a closed source environment.  The free with ubuntu means as in freedom, not as in cost.

Why would you need an anti-virus (or perminant ant-virus) if the system is more secure ?

RE: [COLOR=Silver]"..The whole process is going to have to get more user friendly if the goal is to be mainstream..."[/COLOR] Is it really that non user friendly as you make out or are you just having a more difficult time picking up a new operating system. ?? If at a guess I would say the latter.

There is a lot more power in an ubuntu system than windows, click --> click --> click --> click --> click --> click --> click --> click 
 ----- arrrggggghhhhhh.

I have had a lot fewer problem and like Ubuntu, I don't see the fact you have to download the updates a problem , they are nothing like upgrading sp1 to sp3 in XP. On the other hand I am not sure that it is fair to malign windows so much for viruses. I never go on-line in windowas as admin if I can help it and have very little problem with viruses.  If Ubuntu gets a major slice of the market they will have probllems that way as well.

---

### Post by PaulInBHC on 2009-11-01
Latest news.
Booted to XP. Deleted 9.04 partition. Booted to Live CD to trial desktop. gparted to try to gobble up all the free space into 9.10. Restart, get grub restore> and don't know what to do. googled and tried a few suggestions with no success. Live CD boot to format ubuntu and reinstall. When it gets to language packages, I click the skip button and end up at trial desktop. Repeat process until 9.10 is installed again 5 hours later. Now trying to remember all the things I had installed before.

---

### Post by PaulInBHC on 2009-11-21
Two weeks later, a happy 9.04 user with a 37g partition.

I took yesterday off from work. Checked the Dev forum and found where to download 10.4. Had some trouble making the CD with brasero, ended up in XP using the recommended program. Booted to CD. Get to the partition page of the install and surprise, the default is to install along side of 9.10 and XP. Big surprise is that it shows that 10.4 will use a partition about 40-50% of the 37g. I can move the slider to my wishes. Forward we go and the install continues in about half an hour as opposed to the hour or so that 9.04 and 9.10 took. Then I had to remember what to install. Pulseaudio, restricted, flash, bookmarks for FF, and so on.

It's quick, hasn't crashed, and only a few new items that I can see. I put Sysmon on my top panel and it has a graph for cpu. Maybe I could have had that before.

Looking forward to seeing what gets added now that UDS is over.

---

