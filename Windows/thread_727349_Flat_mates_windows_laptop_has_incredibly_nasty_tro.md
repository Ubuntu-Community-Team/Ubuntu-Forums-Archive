---
title: "Flat mates windows laptop has incredibly nasty trojan"
date: 2008-03-17
forum: Windows
---

### Post by dynamethod on 2008-03-17
Hi i just need some input on this but here go's

My flatmate came over last night and asked me to take a look at his laptop, flatmate does not know anything about computers, he pretty much knows how to browse the interenet and use ms word and thats the limits of his pc knowledge.

So i took a look, and it appears his avg anti virus scanner detected a trojan called Trojan.Dropper.VUZ and Trojan.Dropper.Generic, so i waited for avg to finish the scan and to delete the trojans it picked up, i tried rebooting the laptop, only to find the trojans have quadraupled - to put it very mildly.

Im talking 12,000 infections detected by avg after the reboot, before the reboot there was about 1200 trojans detected all of the Trojan.Dropper.VUZ and Trojan.Dropper.Generic variant, and its using up the internet bandwidth - big time.

So im thinking about backing up my flatmates most valuable files, namely his study documents, and formatting the PC, because avg isnt able to cope with this  trojan

Just need some input on this though, how would you go about getting rid of this nasty trojan?  because the problem is that hes here on work permit from england, and he has to get his original copy of winxp sent from england to load back on to his laptop once ive formatted his laptop

---

### Post by BDNiner on 2008-03-17
Search google for Trojan.dropper, you will find several removal instructions for this trojan. I would suggest rebooting in safe mode and then trying to scan and remove the viruses from safe mode. also disable system restore so that the virus doesn't try and reinfect the computer from a file at an old restore point.

---

### Post by intense.ego on 2008-03-17
> **dynamethod said:**
> Hi i just need some input on this but here go's

My flatmate came over last night and asked me to take a look at his laptop, flatmate does not know anything about computers, he pretty much knows how to browse the interenet and use ms word and thats the limits of his pc knowledge.

So i took a look, and it appears his avg anti virus scanner detected a trojan called Trojan.Dropper.VUZ and Trojan.Dropper.Generic, so i waited for avg to finish the scan and to delete the trojans it picked up, i tried rebooting the laptop, only to find the trojans have quadraupled - to put it very mildly.

Im talking 12,000 infections detected by avg after the reboot, before the reboot there was about 1200 trojans detected all of the Trojan.Dropper.VUZ and Trojan.Dropper.Generic variant, and its using up the internet bandwidth - big time.

So im thinking about backing up my flatmates most valuable files, namely his study documents, and formatting the PC, because avg isnt able to cope with this  trojan

Just need some input on this though, how would you go about getting rid of this nasty trojan?  because the problem is that hes here on work permit from england, and he has to get his original copy of winxp sent from england to load back on to his laptop once ive formatted his laptop

Assuming he has a legal license for Windows XP, I see no problem in downloading a "backup." It is quite common for people to lose their windows disks or for it to die, and downloading a backup should work.

---

### Post by Lord Illidan on 2008-03-17
[I]My flatmate came over last night and asked me to take a look at his laptop, flatmate does not know anything about computers, he pretty much knows how to browse the interenet and use ms word and thats the limits of his pc knowledge.

[/I]Sounds like he's ripe for an Ubuntu conversion.

---

### Post by BDNiner on 2008-03-17
> **intense.ego said:**
> Assuming he has a legal license for Windows XP, I see no problem in downloading a "backup." It is quite common for people to lose their windows disks or for it to die, and downloading a backup should work.

Yes and if you have the license sticker on the computer somewhere then you can just call M$ and activate it if it gives you problems after installing with another CD. It is an automated system that takes about 10 minutes to activate. sometimes you may actually get a human being. If that happens then good luck.

---

### Post by dynamethod on 2008-03-17
yeah ill propose to him the Ubuntu option, though his girlfriend uses iTunes, so as long as that runs fine on Ubuntu, ill have them try out the live cd

the problem is with the downloading a backup suggestion is that this trojan has used up about %80 of this months internet cap already, (which im quite pissed off about actually) so we have about 1gig to spare between the 8 students including myself using the lan until the 1st of april - which is bugger all. this trojan downloaded all sorts of files into this laptop

---

### Post by sub2007 on 2008-03-17
There are plenty of forums out there who are experts at removing trojans and other malware and have easy access to some of the Internet's leading malware removal experts (some of which have Microsoft MVPs). Take your pick from one of these: [http://asap.maddoktor2.com/](http://asap.maddoktor2.com/). I'd do this anyway because even if AVG says you are clean, another scan might reveal a backdoor or a keylogging rootkit or some other nasty.

If the trojan is running up high Internet usage then it will be doing one of three things
1. downloading more malware
2. acting as a bot (spam bot or performing DDoS attacks)
3. backdoor activities (keylogging, taking screenshots, allowing remote access etc)

Any of these are bad and you would be best advised to pull this laptop from the Internet immediately, until you can get further help.

If there's anything you can do to save the laptop then that's probably better than a format, at least you won't have to go through the hassle of reinstalling everything. Some people though find that with the time it can take to do malware cleanups (can take weeks working with the forums in some cases) and it's a particularly heavy infection then you might well want to consider a reformat. At the end of the day, it's the only way you can guarantee that you will be clean.

---

### Post by coldswede on 2008-03-17
Well, this might not be tons o fun.

I would advise you not reformat right away, and since he has no reinstall disc is would be pointless.  Besides most new machines have a"safe", "secure" or "hidden" partition the OEM puts on the disc that the Trojan is most likely hiding in now.

First thing to do is for you to get some  anti-malware software on his computer.  I would suggest SpyBot and Registry Mechanic as a good start.  However, don't download it with his machine, in fact don't let his machine on the internet until you get this fixed!  Just down load it to your machine and write him a copy to a CD or DVD or umm floppy (?!)

Last thought is, if he can have someone just email him the  validation code from his XP disc he can reinstall from any disc.  Unless Heaven forbid his machine uses some OEM reinstall disc and not a Windows disc.

But to repeat fix the infection FIRST then reinstall, or it will likely survive the format

---

### Post by dynamethod on 2008-03-17
How about if i use the Ubuntu lived disk to format the entire HD clean?, then try resintsall the OS, and unfortunatly yes its OEM, also we dont have enough bandwidth left this month to dl any OS anyhow :S

---

### Post by Lord Illidan on 2008-03-17
iTunes on Ubuntu? I doubt that will work fine. For what does she use it? Music?

---

### Post by dynamethod on 2008-03-17
> **Lord Illidan said:**
> iTunes on Ubuntu? I doubt that will work fine. For what does she use it? Music?



She has an ipod, and uses itunes, and quite stubborn about it

---

### Post by Lord Illidan on 2008-03-17
The newest generation Ipods? Does it work with rhythmbox? Anyway, I doubt she'll switch if she's so obsessed with iTunes.

Anyway, good luck with the trojan removal, mate.

---

### Post by dynamethod on 2008-03-17
ya thanks to everyone for their input

---

### Post by coldswede on 2008-03-17
What make and model is this machine, if I may ask?

---

### Post by dynamethod on 2008-03-17
> **coldswede said:**
> What make and model is this machine, if I may ask?

Im not sure atm im at a lecture lol, but when i get home ill check it out and post the model/make here

---

### Post by JDorfler on 2008-03-18
If you have Ubuntu, install Clam AV and ClamTK.  (make sure you edit the launcher for ClamTK that gksudo is in the command line.)  Then, access her HDD via external HDD encasement, and start getting rid of that bad boy.  Ubuntu sees all.

---

### Post by seanc7 on 2008-03-19
Regarding the Internet usage. First rule if you suspect you have a virus, pull the network cord or phone cord out of your computer.

---

### Post by tadcan on 2008-03-19
> **dynamethod said:**
> How about if i use the Ubuntu lived disk to format the entire HD clean?, then try resintsall the OS, and unfortunatly yes its OEM, also we dont have enough bandwidth left this month to dl any OS anyhow :S

XP doesn't like installing over linux. I tried it and the XP disk wouldn't load.

---

### Post by dynamethod on 2008-03-19
> **tadcan said:**
> XP doesn't like installing over linux. I tried it and the XP disk wouldn't load.

no i mean i'd use the ubuntu live cd to format the HD clean, then install winxp

---

### Post by cprofitt on 2008-03-19
iTunes -- that is the likely cause of the virus.

---

### Post by dynamethod on 2008-03-19
Limewire actually

---

### Post by Bungo Pony on 2008-03-19
My Win partition got infected a while back and I tried to clean it for three weeks. And that's not just running all kinds of AV software, it's deleting exe and dll files using Ubuntu, going through the registry, running in safe mode, using HiJackThis (when the damn trojan wasn't preventing it from running) and I've been unsuccessful. I'm doing a re-format of everything when Hardy comes out next month. Until then, Windows will sit and rot on it's own partition.

One thing I didn't try was running a virus scanner in Ubuntu. You might wanna try that with your live cd - install a linux virus scanner and run it. Other than that and everything I've tried, a re-format is probably your best bet.

---

### Post by ax1m on 2008-03-25
The best tool I have ever come accross for removing that kind of cr*p from XP is a little program by a Frenchman:

Smitfraudfix by S!ri

It is available here: 

[http://siri.geekstogo.com/SmitfraudFix.php](http://siri.geekstogo.com/SmitfraudFix.php)

Just follow the instructions.

I have used this tool a number of times and, although it takes a sledgehammer to the Win Registry, it has never broken anything and never failed to remove a piece of stubborn spyware/adware/general cr*p that Windows attracts like a magnet.

I hope this is useful, although I see the original query is quite old.:)  

Oh, and once you've cleaned up the PC, don't go straight back to Limewire for more episodes of South Park - that's probably where the nightmare started.:(

---

### Post by blane2 on 2008-03-26
get the OEM disk, or buy a copy of XP and just wipe the drive. Let this be a lesson to him to  be more careful on the internet. 

Cut your losses a new copy of XP is going to cost way less than the time you'll put in to trying to remove the more advanced trojans out in the world today. Even if you get it from everyfile, there will always be one little piece of it sitting in some registry file just waiting for you to turn it back on so it can start over again. It really never fails. 

Save time, bite the bullet and by a copy of XP pro and teach him about internet security.

---

