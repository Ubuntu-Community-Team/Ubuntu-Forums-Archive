---
title: "Ubuntu on a windows home network"
date: 2005-11-06
forum: Testimonials &amp; Experiences
---

### Post by Ron Byers on 2005-11-06
A week ago I loaded Ubuntu on my linux machine. In my week's experience, admittedly not long, it has become apparent that ubuntu has some problems working as part of a home network. Specifically it needs an easy seamless method for allowing a windows machine to print from a local printer. Yes I know all about cups, but the average windows user doesn't. When you have to go to the command line to allow other computers on your home network to access your printer, the distro is not yet ready for prime time. It is difficult i my case because the command line editor didn't properly install. Second, samba also seems to require command line intervention. Not a problem for a Linux user, but hardly the thing to endear the distro to former Windows users. Finally, and most importanly I am having a heck of a time dealing with network passwords. When I want to access a windows computer on my home network, I want to be sure I don't have password problems. Again something I can deal with on a command line  basis, but something the average windows user will never understand. 

So far Ubuntu is unsurpassed as a stand alone Linux distribution but I need help, and I think Ubuntu needs improvements, making sure it easily interacts with windows machines in my a home network
__________________

---

### Post by dus10 on 2006-01-09
Maybe it's a pointless question, but since you say you are fairly familiar with linux I hope you will know the answer to my newbie question.  

Q: I can see my samba share on my home network through my windows xp machines, but when I try to access it I am asked for a user and password.  I don't know what these are.  How do I set my username and password or hopefully eliminate the need for one these if possible?

A: ?

Thanks.

---

### Post by shelsh on 2007-01-28
hi there - thought this might help...
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server")
i just successfully installed samba server on my machine n tested it with another pc with windows OS. :)
the username and password is meant to be username on ur linux machine which password u need to set by using the smbpasswd command.
:) let me know if u need more info.

---

### Post by jonandrews on 2007-01-28
I set out 6 months ago to have my first Ubuntu 'test' PC fully integrated with a pre-existing home network of Windows pc's, & capable of two-way file transfers, printing via a Windows pc, and media streaming.

I found it very confusing to achieve, despite the excellent help in the Forum, in particular 'stormbringer's guide.
[http://www.ubuntuforums.org/showthre...etwork+windows](http://www.ubuntuforums.org/showthre...etwork+windows)


Since that time, I have done a dozen or so installations that repeatably work fine on my hybrid XP / Ununtu network, and simplified the process considerably.


I have just finished documenting the most simple process I can, written from the perspective of someone much more familiar with Windows than Linux. If you want to give have a look, you'll need to email me with your email address & I will forward my networking & printing guides.

If you find either of them helpful, I would like to put it on the forum somehow and see if it can help others.

---

### Post by rev_b on 2007-01-28
> **Ron Byers said:**
> 
When you have to go to the command line to allow other computers on your home network to access your printer, the distro is not yet ready for prime time.
__________________

You don't have to go to the command line in order to print from a windows machine... you just have to enable "share printers" in your gnome environement (administration -> printing), and then set up the windows machine to print into the IP adress of your Linux machine, with the port and printer name... like [http://192.168.1.2:631/printers/Deskjet-something](http://192.168.1.2:631/printers/Deskjet-something)... and having the windows drivers installed on your windows machine, of course.

I can't see how that can be that complicated; sure, you have to learn how to do it, but I guess you didn't figured it out how to set up a windows home network all by yourself... same thing applies to linux. And as I said, I can't see any need to even get a command line to have it done.

Anyway, when having a home network, by far the better solution is a network printer.

---

### Post by shaft350x on 2007-01-29
While it *should* be as simple as that sounds, it really isn't.  As someone who only used Windows before, I had quite a few difficulties getting my own network setup.  Granted I hadn't done much networking before, but in defense of Ron Byers, each network has its own quirks.  I had to install new drivers on the Win Laptop, just to get it to see my desktop (whether it was in Windows or Ubuntu).  Then I had to get into the command line to setup a user name and password for Samba because I didn't know what it was, or even if there was some default setting.  To top it off Windows said Samba wasn't sending the right driver, I ended up having Windows install a driver that was close and then switch the driver with the proper one (since it was already installed but Windows wouldn't show it).  Now it occurs to me that most of my issues stem from Windows being snooty and not playing well with others, but I spent a lot of time trying to figure things out on Ubuntu's side as well.

---

### Post by rev_b on 2007-01-29
Anyway, some networks can always be troublesome (dogdy switches, Lan cards, bad configured firewalls), but I must say Ubuntu is the easiest and most user friendly linux distro I tried in configuring networks. Try to do the same with Fedora.

I had my network configured very easily with ubuntu. I have my PC, 2 physical windows PC (one wireless laptop) and 2 virtual machines, one with windows XP and another with feisty fawn, each with its own IP and setting up the network was troubleless. In Ubuntu PC's, Just right click on one folder, select share folder, and it will automatically download, install and configure samba. Start nautilus Go -> Network -> windows network, and it'll display all the windows machines and Linux using Samba in the network. Windows machines print fine either to the network printer either to a printer connected to Linux. The opposite it's also true, it's very easy to configure Ubuntu to print on a shared printer connected to a windows machine; it even detects it automatically.

Of course I admit it won't be so easy all of the time, but that's true for every operating system (I had plenty of troubles trying to set up a home network in windows before). So I strongly disagree that "the distro is not yet ready for prime time" concerning home network configuration. My experience is the opposite. It's the most friendly and straightforward Linux distro I've tried setting up a network. Everything is done pointing and clicking.

---

### Post by ElMargaro on 2007-07-22
> **jonandrews said:**
> I set out 6 months ago to have my first Ubuntu 'test' PC fully integrated with a pre-existing home network of Windows pc's, & capable of two-way file transfers, printing via a Windows pc, and media streaming.

I found it very confusing to achieve, despite the excellent help in the Forum, in particular 'stormbringer's guide.
[http://www.ubuntuforums.org/showthre...etwork+windows](http://www.ubuntuforums.org/showthre...etwork+windows)


Since that time, I have done a dozen or so installations that repeatably work fine on my hybrid XP / Ununtu network, and simplified the process considerably.


I have just finished documenting the most simple process I can, written from the perspective of someone much more familiar with Windows than Linux. If you want to give have a look, you'll need to email me with your email address & I will forward my networking & printing guides.

If you find either of them helpful, I would like to put it on the forum somehow and see if it can help others.
Could you please send me your instructions to [email]adrian_cerda@gmail.com[/email]?

Thank you very much,

Adrián

---

### Post by littleerikwilson on 2007-07-29
> **ElMargaro said:**
> Could you please send me your instructions to [email]adrian_cerda@gmail.com[/email]?

Thank you very much,

Adrián

 I would also very much appreciate your instructions.  [email]ew46and2@yahoo.com[/email]

Thank you,

Erik Wilson

---

### Post by drewkeller on 2007-07-31
jonandrews
I would like to see your instructions, too. Why not just post them?

Thanks

---

### Post by olewy on 2007-08-23
> **jonandrews said:**
> I set out 6 months ago to have my first Ubuntu 'test' PC fully integrated with a pre-existing home network of Windows pc's, & capable of two-way file transfers, printing via a Windows pc, and media streaming.

I found it very confusing to achieve, despite the excellent help in the Forum, in particular 'stormbringer's guide.
[http://www.ubuntuforums.org/showthre...etwork+windows](http://www.ubuntuforums.org/showthre...etwork+windows)


Since that time, I have done a dozen or so installations that repeatably work fine on my hybrid XP / Ununtu network, and simplified the process considerably.


I have just finished documenting the most simple process I can, written from the perspective of someone much more familiar with Windows than Linux. If you want to give have a look, you'll need to email me with your email address & I will forward my networking & printing guides.

If you find either of them helpful, I would like to put it on the forum somehow and see if it can help others.
jonandrews:

Hi, can you forward the guide you made to [email]david.oloughlin@gmail.com[/email] please? Thanks.

---

### Post by ukripper on 2007-08-23
Try this guide - 
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Ubuntu is ready if you are ready!

---

### Post by Ron Byers on 2007-09-19
I dropped out of the Linux community in frustration. I figured out how to deal with a windows network,,but printing was never easy. It still isn't.  Maybe that is because my local printer is a canon and I am told the driver for my particular model "mostly works"  When you read that you know it is time for a new printer.  ;)  Thanks for all the help last year.  

Oh, I am back. I got bored with Windows.  I hope to get similarly bored with Ubuntu this time around.    

I have noticed one thing, the need to hand load "non-free" drivers makes Ubuntu less friendly than it should be.  I think that is a GPL issue.

---

### Post by ukripper on 2007-09-20
> **Ron Byers said:**
> I dropped out of the Linux community in frustration. I figured out how to deal with a windows network,,but printing was never easy. It still isn't.  Maybe that is because my local printer is a canon and I am told the driver for my particular model "mostly works"  When you read that you know it is time for a new printer.  ;)  Thanks for all the help last year.  

Oh, I am back. I got bored with Windows.  I hope to get similarly bored with Ubuntu this time around.    

I have noticed one thing, the need to hand load "non-free" drivers makes Ubuntu less friendly than it should be.  I think that is a GPL issue.

Welcome back. If you get bored with ubuntu then probably try some other distro. Choice is unlimited in linux world.

---

### Post by jonandrews on 2007-11-21
I've put my simple guide to integrating Ubuntu PC's into a wired Windows home network onto a website:

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)


Let me know if it is helpful.

---

### Post by mister_lister on 2007-11-21
I am using a fully updated "dapper drake (6.06) LTS" and I had a lot of fear about setting up ubuntu with my windows network. From previous attempts with other distributions I had to do alot configuration file diving.  My printers are all hp and shared of a windows computer that serves as the print server.

With some help, it was rather easy, I set up my Linux box and can share folders and files between my linux machine and windows machine.

The printer set up was SUPER easy. As easy as setting up a networked printer in any version of windows, easier infact because ubuntu had the drivers already for my desk jet, didn't have insert a cd rom or install a bunch of ****.  I just used the system menu to launch the "printers" setup, selected the name of the shared printer on the windows machine, selected the drivers and voila it was connected and printed out a test page.

My point is that is very possible to have a shared windows\linux network. You do have to do some configuring, but it is not rocket science, just asked questions here and have paitience.

I do everything I did with windows and have a fun new os to play with, alll for free. I do like to tinker and learn new things, so I do not expect instant gradification (akin to being a typical windows user).

Anyway, just hang in there and continue to ask questions.

---

### Post by zman58 on 2007-11-21
I have had a Linux network set up at home for years. My home network can easily accommodate Windows workstation systems as I have used several on this network. I documented my approach. The main network server, gatekeeper, provides many valuable network functions:
1. Firewall - logging and security - iptables
2. DHCP server - for automatic configuration of network clients
3. DNS server - with bind I have my own local name server and local naming for client systems.
4. Print server - printers shared across the local network
5. Network storage - 120 GB of local storage for documents and multi-media files.
6. Automated nightly backups to external USB drive - /home directories backed up efficiently every night using rsync.
7. Local web server - apache
8. ssh - remote access

Gatekeeper runs a desktop version of Ubuntu. It is incredibly reliable! I just checked the uptime and it has run for 86 days straight without a boot! Lots of other features as well. You can read more about "gatekeeper" at my website:
[http://home.neo.rr.com/zahorec/](http://home.neo.rr.com/zahorec/)
I have instructions and configuration files there as well.

Also, at my place of employment we use a Windows network with Active Directory and I have attached a Ubuntu desktop system to that network. I can access Windows network shares and other Windows machine shares just fine. I can print to printers on Windows network. I attach to the Internet through a Windows proxy server. Everything seems to be working very well. It is all very manageable with Linux today.

You need to have some patience to set things up. Once you get it working, then you realize what it takes and can do even more with confidence.

---

### Post by erlyrisa on 2007-11-22
You know what I hate....

When a Msoft certified pro tells me about how good MSoft is for networking!?

The sad part about Ubuntu is that, it's tailored toward making the Geek at home trying to make it work with thier existing setup... and yes it sometimes fails - just like a Mac (in the old days a Mac and PC had real difficulty with each other).

If the network was Unix based- believe me, it would be easier to administer...

many a time I have more problems with Msoft networks.... I mean you actually have to delete some defualt installed protocols in order to get Iconection sharing working. --Pretty complicated step if you ask me.

Then theirs the problem, if you decided to name your computers under a different workgroup, because you didn't know what that meant.. your computers never see each other. (and it's only on phreak events that they do)
And how about when the windows share just disappears... you can see the PC but it's stuff just don't exist, or when the PC's all go by by.

-comparing, that -- a home netwrok too

A unix/linux setup, where you can spread your hardrives over a network and group them together as one, or where the entire netwrok runs something as complex as Google's data base... 

nah - it's not Linux that's the problem... it's the grip of the monolpoly that's the problem, and the fact that Ubuntu is trying so hard to stay compatible.

---

### Post by armandh on 2007-11-22
I do sharing through a NAS [nslu2] and every thing sees it just fine. Ubuntu even will remember the passwords. every windohs seems to be different some don't seem to work with each other. the NAS seems to work with everything, and I'm too lazy to make the effort for windohs that will some day be gone.

---

### Post by AlanRogers on 2007-11-22
> **jonandrews said:**
> Let me know if it is helpful.That's a really good guide but were you aware that you don't have to reboot the computer to initiate the changes you've made in Samba? As you're already in the Terminal, just type:```
sudo /etc/init.d/samba restart
```and the changes will immediately take effect. Much quicker!

---

### Post by jonandrews on 2007-11-22
Hi Allan - yes, of course you're right. Old Windows habits die hard with us old 'uns...

---

### Post by AlanRogers on 2007-11-22
> **jonandrews said:**
> Hi Allan - yes, of course you're right. Old Windows habits die hard with us old 'uns...I agree the first part but I doubt you're much older than I am!

---

### Post by trekfan7 on 2008-03-07
> **jonandrews said:**
> 
I found it very confusing to achieve, despite the excellent help in the Forum, in particular 'stormbringer's guide.
[http://www.ubuntuforums.org/showthre...etwork+windows](http://www.ubuntuforums.org/showthre...etwork+windows)


Since that time, I have done a dozen or so installations that repeatably work fine on my hybrid XP / Ununtu network, and simplified the process considerably.


I have just finished documenting the most simple process I can, written from the perspective of someone much more familiar with Windows than Linux. If you want to give have a look, you'll need to email me with your email address & I will forward my networking & printing guides.

If you find either of them helpful, I would like to put it on the forum somehow and see if it can help others.

Please send me a copy of your guides, I assume they will work with Gusty. I have spent so much time  trying to accomplish this and just cannot get it working.
Thank you so much.  Please forward to [email]trekfan7@cox.net[/email]

---

### Post by 3rdalbum on 2008-03-08
I had a lot of fun trying to set up a Windows client to see a network printer. The Macintoshes were a piece of cake - the printer was plugged into the network, the computers were too, you'd just install the drivers, go to the Chooser and select the printer icon.

With the Windows computer, I had to install the printer driver for NT onto the NT server, and then install the drivers for XP onto the client and tell it how to point to the NT server. When you consider that the printer was just plugged *straight into the network* and not directly into the NT server, I can't understand why it needed to be done that way.

A couple of hours after beginning the job, I had finally read pages of documentation and realised that this was what had to be done.

Sharing printers on Windows isn't easy, it's just familiar to you.

---

### Post by ricksterinps on 2008-03-08
Great site.  When I originally began playing with Ubuntu a while ago, I was fortunate to have an additional computer, so I had one XP and one Ubuntu next to each other and I could switch back and forth.  It took forever for me to figure out how to network the two together.  I did use Stormbringer's guide and it would only work for short periods of time.  

I did resolve the issue though buy using the IP address only.  I guess Nautilus wasn't liking the name of the network I already had or it was something else, but in my home I already have 6 other machines running XP with the networks running fine and I didn't want to upset the family by changing things on them.  :)

So I have a link on my destop, the only one as I like to keep it clean, that is listed the Tower1 with the link as SMB://192.168.1.2 and I haven't had a problem since.  I also had to use that for the shared printer that is on the Tower1 as well.  

To make an easy access to the shared folders on Tower1, I went into it through the link on the desktop and added bookmarks.  This placed links into my Places, so I can use the links from any program.

Works great and I have since switched over 2 other computers and the laptops.  I will probably leave the XP machine as it is used for Media Sharing with my Directv box. Otherwise there really is no reason to keep it.

Maybe you can put that info in the bottom of the page for those that are experiencing problems with Nautilus.

---

