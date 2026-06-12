---
title: "Sounding out Server 9.04"
date: 2010-08-29
forum: Server Platforms
---

### Post by LiLoather on 2010-08-29
I love Linux - every single thing one could want to do with a machine is a never-ending intellectual battle in which the obvious is the least likely, vis:

have been playing with Ubuntu 9.04 Server.  Managed eventually to get basic network functions and Squid working, then thought I'd use the machine as my VoIP connection to the outside world.

First problem - get a working sound card.  Installed PCI sound card and rebooted.

Nothing from OS to say I have a working sound card, or a installed card, or if drivers installed, needed, available, pie-in-the-sky.

How do I test to see?  Spent some time on Google.  All tell me how to carry out checks in Gnome/KDE/etc.  I don't have a desktop.  It's a server.

So which obscure, arcane, far-from-obvious and pseudo-mystical package might I need to actually cater for that rarity in a PC, a sound-card, and what esoteric incantation do I have to invoke in a terminal console in order to discover if I have a sound card, and to configure it if I have?

Just point me at it, please.  I've nothing else to do for a few days but learn the language of Linux SoundCardSpeak.

Thanks.

---

### Post by spynappels on 2010-08-29
Can you explain a little more what you are trying to do? Any voip gateway I've set up has had SIP phones, ATAs or physical analogue phones connected through a Digium card, but none have required the server to have a sound card? 
Have you had a look at what Asterisk can do?

---

### Post by LiLoather on 2010-08-29
> **spynappels said:**
> Can you explain a little more what you are trying to do? 

OK. I've an old, much-loved PC and shiny new flash one. (Did the same with women, once.  PC's take it better!)

Don't want new flash one to be seduced or molested by any low-life out on Internet, so old one sits next to new one connected to the Internet and networked to new one.  Old one's running Ubuntu 9.04 server with Bacula keeping back-ups of new one, and Squid, Postfix, DNS, &tc as a gateway/gatekeeper to the internet and chastity-belt to the new one.

New getting into Skype and VoIP (2Talk) I face the headache of either running two sound-cards in new one so I don't have to keep crawling under the desk to change the mike/headphone plugs over with the loudspeaker ones every time I get a call in the middle of a game or Mahler's Fifth Symphony, (or forking out for a switch), or running Skype/VoIP on the old one with the mike/headphone permanently attached to the sound card, so's when people I don't want to talk to call I can bury them under Das Lied von der Erde.

See?

OK, I spent another headbanging hour on the net and it seems the solution is something called alsa?  A thread on this site called Comprehensive Sound Problem Solutions Guide v0.5e gave some help; following it I get:

tony@Debbie:~$ aplay -l
aplay: device_list:217: no soundcards found...

but, lo and behold, lspci -v finds - Tah Dah - a soundcard!
   
00:0c.0 Multimedia audio controller: Ensoniq 5880B [AudioPCI] (rev 02)
        Subsystem: Ensoniq Device 2003
        Flags: bus master, slow devsel, latency 64, IRQ 5
        I/O ports at d000 [size=64]
        Capabilities: <access denied>
        Kernel driver in use: ENS1371
        Kernel modules: snd-ens1371

As suggested I went "to [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) and search for your sound card (chipset) manufacturer in the dropdown box"  but all I found was a FTP index with no dropdown boxes or manufacturer's information in sight, and the site itself is one of those degree-level affairsthat would fart in the faces of more mortals if it could.

However, assuming that the module I want is the one the kernel has already in its wisdom selected, I pressed on only to run full tilt into the brick wall that, apparently, I have to install X-windows and Gnome, a video card and a display just so that I can run alsamixer.

At which point I gave up!

---

### Post by scorp123 on 2010-08-29
> **LiLoather said:**
>  then thought I'd use the machine as my VoIP connection to the outside world.  I fail to see what you need a soundcard for on a server?? VoIP are ultimately just network packets that need to go to your SIP provider. All you need is a SIP client on a desktop machine or a SIP hardware phone. No idea what you want with that soundcard in the server !!?

And if that's too complicated for you ... What's wrong with just using Skype on your desktop machine? :D

---

### Post by scorp123 on 2010-08-29
> **LiLoather said:**
>  tc as a gateway/gatekeeper to the internet and chastity-belt to the new one.  So far, so good.

> **LiLoather said:**
>  I face the headache of either running two sound-cards in new one so I don't have to keep crawling under the desk to change the mike/headphone plugs over with the loudspeaker ones every time I get a call in the middle of a game or Mahler's Fifth Symphony, (or forking out for a switch), or running Skype/VoIP on the old one with the mike/headphone permanently attached to the sound card, so's when people I don't want to talk to call I can bury them 

Why two soundcards?? Skype works tip top on the same soundcard your game is running on. And if you don't want people to Skype you ... just leave Skype off, and nothing will interrupt your game or your good taste of music. I do it like that. Skype off = no chats, no calls when I don't want them.


> **LiLoather said:**
>  OK, I spent another headbanging hour on the net and it seems the solution is something called alsa?  That's desktop stuff ... if you installed the Ubuntu server edition then yes, it's obviously missing.

The easiest way would probably be to simply install a desktop distro such as the normal "Ubuntu Desktop"? Just because it says "desktop" it doesn't mean you can't run all the services you want on it -- in fact that will work tip top. The advantage being that the "Ubuntu Desktop" installer will (hopefully ...) correctly auto-configure your sound card for you so you don't have to reinvent the wheel and the fire by doing all these things manually.

> **LiLoather said:**
>  I have to install X-windows and Gnome, a video card and a display just so that I can run alsamixer. At which point I gave up! Yes! Because that's desktop stuff. And if you installed "Ubuntu Server" then all those bits are missing.

For a pure VoIP you absolutely do not need any soundcard in a server :D ... A SIP phone should suffice. Please read here:

[http://www.asterisk.org/](http://www.asterisk.org/)

... But that's a lot of work, and you will have to spend money for a SIP phone or find a suitable SIP client for your desktop PC.

It would be by far far far easier if you used Skype on your primary desktop, and left your old PC "as is". Simply don't turn Skype on if you don't want to be disturbed.

Or maybe you could get yourself a Skype phone? I bought this:

**SMC WSKP1000 WiFi Skype Phone:**
[http://www.smc.com/index.cfm?event=viewProduct&cid=14&scid=78&pid=1564](http://www.smc.com/index.cfm?event=viewProduct&cid=14&scid=78&pid=1564)

And I also have this:

**DualPhone 3088 for Skype:**
[http://dualphone.net/DUALphone_3088_for_Skype-789.aspx](http://dualphone.net/DUALphone_3088_for_Skype-789.aspx)

... and I have the Skype app on my iPhone. That one works too tip top. Result: I don't need a PC whatsoever to use Skype. Those phones are easy to setup and it shouldn't even remotely be as complicated as what you tried with your old PC there ...

---

### Post by LiLoather on 2010-08-29
Well, SiP 'phones - at least the ones I know about - are USB devices and the thought of trying to get USB working on the old girl under Ubuntu promises a re-run of Napoleon's invasion of Russia.

I have a mike/headset combination which I want to use for both Skype and 2Talk in order to have both hands free I case I need to molest a girlfriend in person while talking to one of the others VoIPly (am I boasting?) - but a mike/headset combination needs a soundcard.  And with every soundcard I have you can either plug loudspeakers into it or a mike/headset combination but you can't have both at once.

Theoretically you can run two or more soundcards in the same machine in Windows, but I tried it and like many things in Microsoft the space between what you can do theoretically and what you can actually do has been the ruin of many a poor boy.

So if I want to use the new girl for games (and who doesn't) I need the loudspeakers attached to the soundcard.  In addition most games won't be very happy running with Skype etc in the background.

---

### Post by scorp123 on 2010-08-29
> **LiLoather said:**
> Well, SiP 'phones - at least the ones I know about - are USB devices No, there are also stand-alone Ethernet phones. They look and feel and work like ordinary phones ... but instead of connecting them to your phone line, you'd connect them to your Ethernet hub. And last but not least there are also soft-clients that you could install in your OS.

> **LiLoather said:**
>  and the thought of trying to get USB working on the old girl under Ubuntu promises a re-run of Napoleon's invasion of Russia.  Hmmm ... actually I think it's more gonna be like a quick visit by Genghis Khan ... :D


> **LiLoather said:**
>  In addition most games won't be very happy running with Skype etc in the background. Turn Skype off? When I'm gaming ... I'm gaming. I don't want to talk to anyone. And Skype remains off. Wouldn't that be the easiest solution? Just use Skype when you really really want to use it ... ?

Or you get one of those Skype phones ... they are not *that* expensive and they work independent of any PC's or soundcards. Given that they are easier to use and to setup than VoIP stuff on your old PC I'd say they're worth that little bit of cost ... ?

---

### Post by LiLoather on 2010-08-29
> **scorp123 said:**
> 
 Turn Skype off? When I'm gaming ... I'm gaming. I don't want to talk to anyone. And Skype remains off. Wouldn't that be the easiest solution? Just use Skype when you really really want to use it ... ?


I'm actually not that bothered about Skype. If I can get it to work without a GUI it would be useful and there's something called Bitlbee which seems to offer it, but what I'd really like to do is to give up my PSTN line with its huge monthly charge, and use a SIP provider instead - and I'm sure you don't disconnect your 'phone even while you're gaming.  

Which is why I need an always-on system - and the old girl sans video card and monitor is a lot less expensive to run over 24 hours than the new one even if she's not doing anything.  Funny, I seem to recall women are like that too.

---

### Post by scorp123 on 2010-08-29
> **LiLoather said:**
>  and use a SIP provider instead In that case ... you could just install the needed soft-client on your desktop OS and then just turn it on if and when you want to? e.g. something like this: [http://www.qutecom.org/](http://www.qutecom.org/) ... your "old girl" could then just continue to do what she does best, e.g. act as router & firewall. No soundcard needed.

> **LiLoather said:**
>  and I'm sure you don't disconnect your 'phone even while you're gaming. I definitely do power down the SMC WiFi phone. And the other phones can be set to silent mode .. or I simply don't pick up any calls when I'm gaming. All Skype software clients are off ... so one might argue that I in fact do disconnect my phone when I'm gaming. :D

> **LiLoather said:**
>  Which is why I need an always-on system  That's another reason why I went with those Skype phones ... they will "just work", no matter what OS I booted into, no matter what distro I just crashed, no matter what hick-up I just caused ... 

> **LiLoather said:**
>  Funny, I seem to recall women are like that too. Men are not really much different, to be quite honest :D :D :D

---

### Post by LiLoather on 2010-08-29
> **scorp123 said:**
> In that case ... you could just install the needed soft-client on your desktop OS and then just turn it on if and when you want to? e.g. something like this: [http://www.qutecom.org/](http://www.qutecom.org/) ... your "old girl" could then just continue to do what she does best, e.g. act as router & firewall. No soundcard needed.


But that's not achieving what I want.  The boxes to be ticked are:

1.  On 24/7 (old girl is, new girl isn't.)
2.  Handsfree operation (rules out VoIP 'phones)
3.  When I'm in new girl is running and I can use a Putty terminal from her to old girl to make and received calls via SIP (major) and Skype if it will play ball (minor)
4.  When I'm not home (or at play) old girl can run as TAD.

Should be simple.  I've Windows SBS 2003 I could install on old girl which would give me all the above functionality with bells on via VNC, but she'd be groaning under the weight a bit.  I should surely be able to do the same with a leaner, meaner Linux distro but it looks as if I'd need to invest about a year of my time to get it running.

---

### Post by spynappels on 2010-08-30
If you are using a SIP account, it really would be simpler and more reliable to get a separate SIP phone which looks just like a normal phone. Most of these have hands free, it will just plug into your network and can be always on. They can often work with headsets if that is what you want. I recently bought 20 of these for about £23 each incl delivery from eBay, might that not be a better option?

---

### Post by scorp123 on 2010-08-30
@spynapples:

Exactly. :)

---

### Post by spynappels on 2010-08-30
FYI, look up Swissvoice IS10 IP Phones, these are what I got and they really are great budget IP Phones.

---

### Post by LiLoather on 2010-08-30
I appreciate the thoughts but, once again, Linux has beaten me.

The PJSIP project at least offered the prospect of a console controlled softphone, and a preliminary look at bitlbee-skype hinted at the possibility of running Skype on a headless machine, but they were steps too far when I fell at the first step and couldn't even get a sound card working on a headless machine!

Putting VoIP aside for the moment I had a look at another possible use for the old girl, running Bacula or such-like with SAMBA and her tape backup.

Three hours Googling and head-banging and I've still no idea how you mount a SATA tape deck and get Bacula to even find it, let alone use it.  And as for SAMBA....

It's now been a decade since I burned my first Linux installation disk.  I was on Windows '98 SE then.  Now I'm on Windows 7 and I still don't have a working Linux installation that does anything like what I use Windows for.  Every eighteen months or so I have a machine and/or a purpose for it and give Linux (I settled on Debian and then Ubuntu) a go and it always defeats me - in part because I always have to go back and spend hours reminding myself of the esoteric rituals for mounting devices, configuring networks and using Vi.

So Ubuntu's coming off and SBS 2003's going on, and within a couple of hours I'll have a working gateway, web-proxy, POP server, tape backup, Softphone with Soundcard for headset and mike &tc. all on a headless machine.

And I'll have time to play games again.

---

### Post by scorp123 on 2010-08-30
> **LiLoather said:**
>  I've still no idea how you mount a SATA tape deck and get Bacula to even find it, let alone use it.  You don't mount tapes. You either write to or read from them. But you never mount them. Tapes are usually devices such as **/dev/st0, /dev/nst0, /dev/rst0, /dev/mt0** ... or **/dev/rmt0**

st0: SCSI tape 0
rst0: rewinding SCSI tape 0
nst0: non-rewinding SCSI tape 0
mt0: magnetic tape 0
rmt0: rewinding magnetic tape 0

=> The difference between the "rewinding" tape devices and the other ones is that the "rewinding" ones will auto-rewind back after each operation; whereas the others won't, they will stay on the last position ... It's a historical thing.

And you will need the "**mt**" utility to operate the tape.

Read here:
[http://ubuntuforums.org/showpost.php?p=6339495&postcount=8](http://ubuntuforums.org/showpost.php?p=6339495&postcount=8)
[http://ubuntuforums.org/showpost.php?p=6341610&postcount=11](http://ubuntuforums.org/showpost.php?p=6341610&postcount=11)
[http://ubuntuforums.org/showthread.php?t=726875](http://ubuntuforums.org/showthread.php?t=726875)

Once you get the "mt" to work with your tape, you could use something simple as "tar" and pipe it through ssh (e.g. 'new girl' pipes its backup through to 'old girl's tape ...)

[http://ubuntuforums.org/showpost.php?p=4760998&postcount=5](http://ubuntuforums.org/showpost.php?p=4760998&postcount=5)

---

### Post by LiLoather on 2010-08-30
Thanks Scorp123.  That tells me more than I learned from two hours of Googling last night.

But I know that would be only the first of many steps and much head-banging before I could actually use the thing - for eg. I have in /dev an entry for everything you list as possible, plus a /st0a, an /st0m and a folder for 'tape' which contains a folder /by-path.  I've a vague recollection of getting a list of devices yesterday which included the tape drive but I was at that point looking for the soundcard so didn't take much notice of it, and I've now no idea what the command was which produced that list.

Mt is now mt-st which says it's for SCSI tapes which this one isn't - it's SATA.  And installing mt-st I get a message that it fails because Bacula isn't properly configured, which could be because having installed Bacula I couldn't properly configure it in the apparent absence of a tape device!  So once again Linux has me chasing my tail when I could be wasting my time drinking, eating, chasing girls, exploring monster-riddled dungeons or sleeping.

I'm sure that with the patient help of you and others on this forum I could get everything working over the next two or three days but with Windows SBS I could do it in two hours AND have a sporting chance to fix any problems that crop up subsequently.

I regret it, but I' going to have to put Linux back in its box and put the box back in the toy cupboard.  I'll probably get it out again for another play on a rainy day in eighteen months time, 'tho.

---

### Post by scorp123 on 2010-08-30
> **LiLoather said:**
>   I have in /dev an entry for everything you list as possible Because your Linux kernel supports all possible and impossible devices. That doesn't necessarily mean that the devices are physically there.

> **LiLoather said:**
>  plus a /st0a, an /st0m and a folder for 'tape' which contains a folder /by-path. Good. What does this command say about your devices?
```
sudo lsdev
``` (... maybe you will have to install that tool first?? **sudo apt-get install procinfo**  ...)

> **LiLoather said:**
>  Mt is now mt-st which says it's for SCSI tapes which this one isn't - it's SATA.  And I bet you also don't have SCSI disks in your system? :D  And yet when you access ***/dev/sda1, /dev/sda2, /dev/sdc4*** and so on you are accessing SCSI disks (at least by name) .... **_sd_** = **_S_**CSI **_D_**isk.

To the Linux kernel it's all the same now. Yes, the connectors are different, a SATA connector looks different than Ultra-wide SCSI-3 and so on ... But logically and from a OS point of view they are the same, they work the same way ... Hence why at some point more or less everything became a SCSI device (at least the Linux kernel sees everything like that). SATA disks and drives too :D

> **LiLoather said:**
>  And installing mt-st I get a message that it fails because Bacula isn't properly configured Precise error message please? And what if you trigger this command:
```
sudo dpkg --configure -a
```

> **LiLoather said:**
>  So once again Linux has me chasing my tail  Linux is all about reading error messages and posting them verbatim to a forum like this one ... then all problems will disappear :D

> **LiLoather said:**
>  when I could be wasting my time drinking, eating, chasing girls, exploring monster-riddled dungeons or sleeping.  You can still do all that while messing with Linux. I am Unix + System Admin. You don't *really* think I am really *really* working 100% 8-9 hours every day?? :D  Trust me. One doesn't exclude the other. You just shouldn't do stuff as "root" while you're drunk. If your smell didn't give you away as being drunk ... the horrible BS you just typed into the "root" terminal definitely will :D :D :D

> **LiLoather said:**
>  I regret it, but I' going to have to put Linux back in its box and put the box back in the toy cupboard.  The toy box is where I keep my Windoze disks :D

Have fun.

---

### Post by LiLoather on 2010-08-30
> **scorp123 said:**
> 
Have fun.

That's what life's for.

Anyway the Gods of Linux have taken a hand.  I thought I'd give it a last go and install a desktop so's I could see what I was doing, and chose LXDE to try to keep the weight down.  Did an apt-get install LXDE and now have a completely uncommunicative machine.  Grub boots ordinarily to the point where, presumably, it tries to install the graphic's drivers where it has a bit of a hiccup.  Then it resumes for a bit more with the usual arcane ritual then - nothing. A blank screen, no curser, nothing.  No response to the keyboard.  NIC appears active but can't PUTty to it and no response to ping.  The last boot messages I get are starting Gnome and starting Squid.  Even a ctl>alt>del has no effect.  And that, says Alice, is that.

So as I assume a complete re-install is the only way out of this one I might as well install something reliable that works.

---

### Post by scorp123 on 2010-08-31
> **LiLoather said:**
>  I might as well install something reliable that works. Have fun with Solaris :D

(And no, you can't be talking of Windows ... because that one is neither reliable, neither does it work, and neither will you get a 100'000 € per year job with it ...)

---

### Post by LiLoather on 2010-08-31
> **scorp123 said:**
> H
(And no, you can't be talking of Windows ... because that one is neither reliable, neither does it work, and neither will you get a 100'000 € per year job with it ...)

Actually I am.  I've had no problems with its reliability since Win 2000 -(OK, I skipped Vista and I'm still using XP though I can dual-boot into Seven to see how it goes) - and everything works straight out of the box because software and hardware producers know that their reputations - and profits - depend on it doing so.  And the reason I wouldn't get a 100,000 whatsit job with it is because the averagely computer-literate muffin like me can get Windows to do what I want without having to employ a highly-paid expert!

That said, I would really, really like to get Linux working on Elaine because the old girl should be enjoying her twilight years with a bit of light knitting rather than struggling with the burden of Windows SBS, and I really, really have given Ubuntu a go yet again - but getting it to do anything beyond the bog-standard desktop with clock, calendar and calculator is still an uphill struggle against arcane learning and incomprehensible jargon to the averagely computer-literate muffin like me.

Sorry.

---

### Post by sh1ny on 2010-08-31
> **LiLoather said:**
> Actually I am.  I've had no problems with its reliability since Win 2000 -(OK, I skipped Vista and I'm still using XP though I can dual-boot into Seven to see how it goes) - and everything works straight out of the box because software and hardware producers know that their reputations - and profits - depend on it doing so.  And the reason I wouldn't get a 100,000 whatsit job with it is because the averagely computer-literate muffin like me can get Windows to do what I want without having to employ a highly-paid expert!

That said, I would really, really like to get Linux working on Elaine because the old girl should be enjoying her twilight years with a bit of light knitting rather than struggling with the burden of Windows SBS, and I really, really have given Ubuntu a go yet again - but getting it to do anything beyond the bog-standard desktop with clock, calendar and calculator is still an uphill struggle against arcane learning and incomprehensible jargon to the averagely computer-literate muffin like me.

Sorry.

You don't seem to be struggling with the OS, you're in a fight with yourself, on trying to memorize a few simple commands and "learn" something new. There's quite a few things that linux CAN do and windows can't, not to mention the prices involved ( or the support for that matter ).

But that's just me, in my most optimistic views. The truth is, some people are stuck with windows, and will be stuck there forever.

---

### Post by scorp123 on 2010-08-31
> **LiLoather said:**
>  That said, I would really, really like to get Linux working on Elaine because the old girl should be enjoying her twilight years with a bit of light knitting rather than struggling with the burden of Windows SBS  Why not try a distro that might be more suitable for you? I don't know why everybody thinks that Ubuntu is a good distro for beginners ... It just isn't IMHO. It's lacking a lot of polish in a lot of places.

IMHO if you're used to Windows and its setup wizards, control panels and what not then e.g. OpenSUSE or Mandriva might be far far better for you. Both Mandriva and OpenSUSE have a "Control Panel"-like application which makes the experience far more "Windows-like". You'll be visiting the command line far less than on Ubuntu. You can still give Ubuntu another try when you grow tired of OpenSUSE and its constant "let me hold your hands, let me do this for you" approach. But then again it's also OK to never get tired of it. I personally prefer Ubuntu as desktop OS but for things like LDAP/SAMBA servers I still prefer Novell openSUSE or its commercial variation: Novell SLES. Simply because on openSUSE I can do things like configure a new LDAP user group and new file shares with a few simple clicks whereas on Ubuntu I'd be forced to type everything by hand in cryptic commands ... 

Ultimately the "right tool" is the one that gets the job done. If you really really want to try out Linux maybe Ubuntu is the wrong answer for you right now and you really should take a look at friendlier distros such as OpenSUSE or Mandriva .... but then again "using the right tool" may absolutely also mean that you stay on Windows. If this is what gets the job done for you ... why not.

---

### Post by LiLoather on 2010-08-31
> **sh1ny said:**
> You don't seem to be struggling with the OS, you're in a fight with yourself, on trying to memorize a few simple commands and "learn" something new.

I came here for help to get a soundcard working under Linux.  No-one has yet been able to help me.  

Every time I pick up Linux I remember a bit more from what I had to learn the last time but I don't wrestle with it every day and, for me, my computer's OS is a tool I use to do other things with, not an end in itself.

How would you have gone about adding a tape back-up drive to your system?  

> **sh1ny said:**
>  There's quite a few things that linux CAN do and windows can't, not to mention the prices involved ( or the support for that matter ).

No argument there.  

> **sh1ny said:**
> But that's just me, in my most optimistic views. The truth is, some people are stuck with windows, and will be stuck there forever.

I think that's right.  I also think it's significant that many, many more people use Linux today than did a decade ago (when I first tried Corel Linux) because with distros like Ubuntu and PC Linux the OS has moved closer and closer to Windows.

As I say, the OS I use is a means to an end.  While I can do everything I need and want to under Windows, being 'stuck' with Windows is hardly a problem.

---

### Post by LiLoather on 2010-08-31
> **scorp123 said:**
> 
Ultimately the "right tool" is the one that gets the job done. If you really really want to try out Linux maybe Ubuntu is the wrong answer for you right now and you really should take a look at friendlier distros such as OpenSUSE or Mandriva .... but then again "using the right tool" may absolutely also mean that you stay on Windows. If this is what gets the job done for you ... why not.

A most realistic view.

I have in my CD repository distros by Corel, Red Hat, CentOS, FreeBSD, SuSE, Debian, Caldera, Ubuntu, Kubuntu and PCLinux 2007 as well as various Ubuntu Servers and SME, and I've spent time on them all.  They all got the job done much like their contemporary Windows and the only reason I stuck with Windows was because there was no Linux version of my favourite games.

I take Shiny's point - there are things Linux can do that Windows can't - and the only occasions I look to Linux is when I want to do those things.  The trouble is that as soon as you look for Linux to be 'unWindows-like' you - well me, anyway - run full tilt into the unfriendlyness of Linux ie:

I had forgotten the command that lists your devices.  How do I find out what it is?

I want to install a tape drive.  Where is the obvious place to go to read up how Linux deals with such things? 

There are probably simple answers to both questions - simple when you know the answers, anyway - but the folks that know the answers very often have forgotten how thick and tangled the wood is when you're looking at it from the outside.

---

### Post by sh1ny on 2010-09-01
> **LiLoather said:**
> I came here for help to get a soundcard working under Linux.  No-one has yet been able to help me.  

Every time I pick up Linux I remember a bit more from what I had to learn the last time but I don't wrestle with it every day and, for me, my computer's OS is a tool I use to do other things with, not an end in itself.

How would you have gone about adding a tape back-up drive to your system?  



No argument there.  



I think that's right.  I also think it's significant that many, many more people use Linux today than did a decade ago (when I first tried Corel Linux) because with distros like Ubuntu and PC Linux the OS has moved closer and closer to Windows.

As I say, the OS I use is a means to an end.  While I can do everything I need and want to under Windows, being 'stuck' with Windows is hardly a problem.

I'd rather had you do the rumble in the jungle alone, not being told by anyone. That's when people learn things, not when they just copy-paste stuff that someone told them to and they don't have the slightest idea what the command does. When you gain understanding on how linux works, things will become much more clear. Anyway, after a quick 5 minute search i came up with this :

[http://ubuntuforums.org/showthread.php?t=907571](http://ubuntuforums.org/showthread.php?t=907571)

In that thread there's another link that shows this :

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

It might be very old, but still most of it is true.

By the looks of it, your sound card is unsupported by alsa, so you might get it working or you might not.
Here's the link of the supported Ensoniq devices :

[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Ensoniq](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Ensoniq)

Remember, almost any question you might come up with has been asked before. You just need to find the right answers for you.

---

### Post by LiLoather on 2010-09-01
> **sh1ny said:**
> I'd rather had you do the rumble in the jungle alone, not being told by anyone.

So would I.  

>  Remember, almost any question you might come up with has been asked before. You just need to find the right answers for you.

Often asking the right question itself supplies the answer.

But even if I did list all the alsa mods I'd have no idea if they were right, or all there, or properly configured, so short of relying on free advice from some long-suffering Linux expert on a forum like this I'd have no option but to become an expert on how alsa works, and how my sound card works.  Sorry, but I've other things to do with my life.

Anyway, as I've said, trying to install a lite desktop seems to have crashed the whole system, and as I need a working OS rather than a restoration project as a hobby it's back to Windows SBS.

But thanks for your trouble.

---

