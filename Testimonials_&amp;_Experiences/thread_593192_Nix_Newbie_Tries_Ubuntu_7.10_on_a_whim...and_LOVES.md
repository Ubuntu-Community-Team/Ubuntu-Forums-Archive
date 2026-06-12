---
title: "Nix Newbie Tries Ubuntu 7.10 on a whim...and LOVES It!"
date: 2007-10-26
forum: Testimonials &amp; Experiences
---

### Post by BattleKat on 2007-10-26
[FONT=FreeSans, sans-serif]I am a brand spanking new *nix user.  I've always used Windows at home and at work...it pays the bills.  I've seen different flavors of *nix over the years and have to say that Ubuntu really caught my eye.  My BF has been using it for over a year now (don't know which version sorry) and his PC has been very stable ever since.  He's a programmer type and knows *nix like the back of his hand.  I however, have only just seen it...never used it....always thinking how 'hard' it would be having to do all the command line stuff.  Well, my eyes have been opened...wide...in awe of Ubuntu 7.10.[/FONT]
 

 [FONT=FreeSans, sans-serif]The date of it's release I was sitting at work reading dailytech and I saw mention of a new version of Ubuntu.  Knowing that the BF was using that I read a little more about it before I shot him an email about this new version.  As I read the article I was thinking to myself “I might be able to do this.”  I jumped right over to the website and read all the descriptions of the new stuff.  The more I read, the more I thought “why not?”  I have a notebook that I only use for internet/email/chat while sitting in the living room so I'm not tied to my computer room.  When I read that my notebook might run cooler and I would be able to use Compiz 3D Cube, I was sold.[/FONT]
 

 [FONT=FreeSans, sans-serif]When I got home that very night I went to download the .iso.  Took me 6 tries to find a site that wouldn't freeze up on me.  I know I probably shouldn't have tried to d/l on the day it was released but I had nothing better to do.  I got it downloaded and burned to a CD and was too excited to let it sit until the next day.  I threw it in the notebook and started up the LiveCD part just to see it.  I clicked around for a little while but saw I needed an nVidia driver and one for my Broadcom 4306.  I left it until the next day.[/FONT]
 

 [FONT=FreeSans, sans-serif]Friday evening I imaged my HD and blew that image over to my desktop for storage.  I inserted the Ubuntu CD and just installed it.  It was a full install..no dual boot.  I went for broke.  I couldn't get the wireless to connect so I wired it up with my 50ft ethernet cable and started digging in the forums on how to get the wireless to work.....how to get compiz to work...etc.  I wanted Compiz to work first and I knew my Geforce FX Go5700 would work with it.  I had installed the restricted driver but no “fancy stuff” happened.  I was over on Compiz's website and found instructions on installing the latest nVidia driver and getting Compiz stared.  Well, after 4 tries (reinstalled 4 times....don't laugh), I installed Ubuntu using safe graphics and followed some really nicely laid out instructions...all command line mind you.  Got the driver installed and DAMN did my desktop look good.  It was able to get the desktop to do some neat stuff but not the cube.  Frustrated I read countless posts and about 4 days later came across a little snippet that said something about starting up the compiz desktop manager.  I found it in the Synaptic Package Manager and applied/installed it.  After that I was off and running....cubing to my little hearts content.  HA!  Well, with that little chore done it was time to seriously tackle the wifi issue.[/FONT]
 

 [FONT=FreeSans, sans-serif]A very kind person from one of the gaming clans I hang out with offered to help me get it working.  We worked on it for 3 night straight...following everything written here but it just wouldn't connect.  It 'saw' my network...it even transmitted some packets but other than that...nada.  So, after getting really annoyed and fed up with that and almost killing myself tripping over my ethernet cable every night, something had to give.  I found a nice list of wireless adapters that people had tried and gave good information about.  One of the adapters was the D-Link WNA-2330.  Best Buy had it locally so I went to buy it.  While there I picked up a new router at the same time...the D-Link WBR-2310.  Brought both home and started in on the new project.  Got the router installed and configured then tackled the notebook.  No sooner did I plug in the wifi pc card adapter and Ubuntu recognized it and was asking me for my network info.  I inputted all the and VIOLA!!! I was wireless for the first time since the night of the version release.  YAY!!!!  That was last night and I've been going crazy ever since. [/FONT] 
 

 [FONT=FreeSans, sans-serif]All the applications I've found so far in the Add/Remove area have been perfect.  I found a really nice IRC client (Konversation), XMMS, a few more games, and other things to make me feel 'at home'.  I will be Ubuntu on the notebook.  I can comfortably have it on my lap and not start sweating to death...yes, it runs much cooler.  The whole machine runs much better than it ever did under Windows.[/FONT]
 

 [FONT=FreeSans, sans-serif]My only task left is getting my windows and my ubuntu machines to see/like each other and share their files.  I mainly want to just grab image or music files from my Windows machine.  I've tried a couple ways, but it's still a no-go.[/FONT]
 

 [FONT=FreeSans, sans-serif]This is what I'm running Ubuntu 7.10[/FONT]
 

 [FONT=FreeSans, sans-serif]HP Pavilion zd7000 CTO[/FONT]
 [FONT=FreeSans, sans-serif]Intel Pentium4 3.0GHz Hyperthreaded[/FONT]
 [FONT=FreeSans, sans-serif]2GB RAM[/FONT]
 [FONT=FreeSans, sans-serif]100GB Hard drive[/FONT]
 [FONT=FreeSans, sans-serif]nVidia GeForce FX Go5700[/FONT]
 [FONT=FreeSans, sans-serif]D-Link WNA-2330 WiFi Card[/FONT]
 

 [FONT=FreeSans, sans-serif]So, thank you thank you thank you to whomever worked on this version.  I'm totally in love with it.  I have a loooooooooooooong road ahead of me on my journey down Linux Lane...but I'm going to have fun along the way with Gutsy. :)  [/FONT]

---

### Post by fain on 2007-10-27
Thats great im glad you liked ubuntu!!!! You just need a samba client to access shares on windows. 
```
sudo apt-get install smbclient
```
you can type in the address bar of nautilus
```
smb://ip-address-here/windows-share
```

the host name, instead of the ip should work as well.
the share might be in >places>network from the gnome menu

---

### Post by ukripper on 2007-10-27
Welcome to ubuntu. A helpful guide on Samba in the link-
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by BattleKat on 2007-10-29
Thank you fain and ukripper.  I'll be working on the samba thing this week.  I have to find out why my wireless adapter is no longer connecting to my network.  It was working Friday night.  Before I went to bed I put the notebook in Hibernate.  When I got up on Saturday and brought it out of hibernate I no longer had connectivity to my network and haven't been able to get it to connect since.  Any advise on how to clean up network configs and whatnots instead of having to completely reinstall again??

---

### Post by fain on 2007-10-29
you could use wireless tool for some trouble shooting

iwconfig


ifconfig

check to see if you have a valid ip address, probably 192.168.*.* 

try to ping your router if you get a reply its most likely your dns.

what kind of wireless card do you have?
what does your network manager say?
is your card listed in ifconfig and iwconfig?

this is all i can think of right now.

---

### Post by Monstroxus on 2007-10-29
I like your attitude, you didn't give up. It feels good doesn't it, when you finally installed everything correctly? I am sure that sooner or later your internal broadcom card will work. I also bought a wireless adaptor (the internal didn't work), but a few days later I figured out how to get the internal wireless card to work. I am quite sure it will be the same for you.

Try the below link, see if it works for the internal wireless card.

[http://ubuntuforums.org/showthread.php?t=405990&highlight=Broadcom+4306](http://ubuntuforums.org/showthread.php?t=405990&highlight=Broadcom+4306)

Good luck.

---

### Post by BattleKat on 2007-10-30
Fain, I'll try and get all that information in the next couple of days.  I have some work projects that are taking me away from my personal 'fun' projects at the moment.
 
Monstroxus, thanks.  It does feel good.  Right now I am trying to figure out what happened and why my new adapter card isn't connecting to my network anymore.  It sees it...it pegs 100%...but it refuses to connect.  Other than that I really like Ubuntu.  Thanks for the link but I've been there done that...no go.  Tried just about every HowTo dealing with the BCM4306 and it just refuses to connect.  The D-Link WNA-2330 adapter card now refuses to work.  I just don't know enough about linux itself to know what I did so I can undo it and start over.  I really don't want to have to reinstall.  The nVidia driver was a bear to get working :)
 
Oh well, I'll keep at it until it works again.  I will not, however, EVER put my notebook in hibernate or suspend it again.  LOL :)

---

### Post by ukripper on 2007-10-30
> **BattleKat said:**
> Fain, I'll try and get all that information in the next couple of days.  I have some work projects that are taking me away from my personal 'fun' projects at the moment.
 
Monstroxus, thanks.  It does feel good.  Right now I am trying to figure out what happened and why my new adapter card isn't connecting to my network anymore.  It sees it...it pegs 100%...but it refuses to connect.  Other than that I really like Ubuntu.  Thanks for the link but I've been there done that...no go.  Tried just about every HowTo dealing with the BCM4306 and it just refuses to connect.  The D-Link WNA-2330 adapter card now refuses to work.  I just don't know enough about linux itself to know what I did so I can undo it and start over.  I really don't want to have to reinstall.  The nVidia driver was a bear to get working :)
 
Oh well, I'll keep at it until it works again.  I will not, however, EVER put my notebook in hibernate or suspend it again.  LOL :)

Try using wlassistant very powerful kde app for wireless conections.

---

### Post by BattleKat on 2007-11-02
I am once again back to loving my *nix notebook.  After reading about a gazillion posts on here and gleening all kinds of good and helpful tips/tricks, I reinstalled the OS and was back up and running w/wifi...and configured the way I wanted it...in about 3 hours.  
 
Now that I know more about Add/Remove Programs and the Package Manager, I'm good to go....well, for the time being.
 
Oh, btw, my wifi adapter card worked immediately after I pushed it in the slot.  I didn't have to do anything.  The driver was found and enabled via the Restricted Driver Manager thingie (<--technical term).  I did, however, have to reboot my router.  Once network was back up, the D-Link card saw the network and I added/selected the info needed.  It connected almost immediately.  Like I said above, I will NOT be putting  my notebook into hibernate or suspend mode anymore.  It will either stay on or it will be off...no inbetween.  HA!

---

