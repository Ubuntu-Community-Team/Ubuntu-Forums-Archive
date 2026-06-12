---
title: "Help please!!! Got a virus on Vista, dont know what to do, or where to go."
date: 2008-09-15
forum: Windows
---

### Post by -spy on 2008-09-15
I just got a virus of some sort on vista, trojan, malware. Norton AntiVirus didn't prevent it from being installed i guess, but warning did come up. I was downloading photoshop(I know) with BiTorrent, it was in the file I assume. I scanned it with Norton and no viruses where detected, I shut down and went into safe mode and rescanned, still nothing. 

The virus consists of two porn icons that keep appearing on my desktop, also a Norton notification will appear at the bottom mention trojan, some type of ad, and something about Malware and my cpu. Also a warning window and java window popup.

I am currently using ubuntu, but on the same laptop the virus is on, am I ok using it?

I have absolutely no idea what to do. Anyone know my options or a specific site that I can ask this? Also I'm not too good with computers.

:(

---

### Post by Vadi on 2008-09-15
The virus won't affect Ubuntu, don't worry.

But I don't know how to clean it from Vista. Perhaps a more knowledable person will answer.

---

### Post by philinux on 2008-09-15
Stick to gimp or gimpshop.

Maybe install avg for windows and rescan. Your better off turning off system restore as some viruses lurk in there too.

---

### Post by Tatty on 2008-09-15
As long as you are in Ubuntu there is no need to worry.

There are some anti-virus applications in the repos... Try installing them and scanning your vista partition.

---

### Post by WRDN on 2008-09-15
The virus/ nasty won't work under Ubuntu so you don't need to worry.

I would recommend you download the trial for [NOD32]("http://www.eset.com/") which has THE best virus detection rate in the world.

You could also scan the infected Windows partition from Ubuntu, using a program like Clam-AV (in repos).

---

### Post by k33bz on 2008-09-15
do you have any virus scanners, trojan scanners, spyware sweepers, etc, installed on your vista?

---

### Post by kansasnoob on 2008-09-15
#1. Run House-call!

#2. See what's infected!

#3. See if can just be deleted!

[http://housecall.trendmicro.com/](http://housecall.trendmicro.com/)

If it's a file that can't just be deleted then I dunno! Actually there are things that can be done, but they're all potentially damaging to Windows!

---

### Post by jerome1232 on 2008-09-15
It's probably a trojan, this is why you don't torrent illegal files :)

A) delete that file you torrent'd.

B) I've had alot of luck with just booting into safe mode and restoring my system to a few dates back.

---

### Post by cpetercarter on 2008-09-15
As you already have Norton installed on your machine, you could run a virus scan and see what it finds. It may be able to identify and quarantine the virus.

Alternatively, go to [http://onecare.live.com/site/en-us/default.htm]("http://onecare.live.com/site/en-us/default.htm")and run the free Microsoft Live Care scan.It will take about 12 hours to complete, but it is pretty good at dealing with the sort of malware you seem to have picked up.

---

### Post by malachi1990 on 2008-09-15
In ubuntu:
Read the other advice first.

In vista:

Main thing is when you boot into vista, make sure your internet connection is manually unplugged.  Then try to go back 3-6 weeks in your system restore function, and hopefully, that will get rid of it.  If you have recovery console available on your computer, use that as that is usually on a different partition, so 9 times out of 10, it won't be affected.

---

### Post by AmericanYellow on 2008-09-15
You might want to try Microsoft's Online Safety Scanner. It's free.

---

### Post by PocketDog on 2008-09-15
It's just adware, no need to worry. Get Nod as mentioned before, and Spybot - traditional anti-virus won't pick up spyware. Scan with those two, and Windows Defender, and they'll pick up any nasties. If you still have problems after that (doubtful) then you can remove them with a combination of HijackThis and Google.

---

### Post by -spy on 2008-09-15
> **philinux said:**
> Stick to gimp or gimpshop.

Maybe install avg for windows and rescan. Your better off turning off system restore as some viruses lurk in there too.

How do I turn off system restore?

> **WRDN said:**
> The virus/ nasty won't work under Ubuntu so you don't need to worry.

I would recommend you download the trial for [NOD32]("http://www.eset.com/") which has THE best virus detection rate in the world.

You could also scan the infected Windows partition from Ubuntu, using a program like Clam-AV (in repos).

Do I just use vista and download that, while the virus is still there? Should I use safe mode?

> **k33bz said:**
> do you have any virus scanners, trojan scanners, spyware sweepers, etc, installed on your vista?

Norton is the only one I think...

> **kansasnoob said:**
> #1. Run House-call!

#2. See what's infected!

#3. See if can just be deleted!

[http://housecall.trendmicro.com/](http://housecall.trendmicro.com/)

If it's a file that can't just be deleted then I dunno! Actually there are things that can be done, but they're all potentially damaging to Windows!

thanks

> **jerome1232 said:**
> It's probably a trojan, this is why you don't torrent illegal files :)

A) delete that file you torrent'd.

B) I've had alot of luck with just booting into safe mode and restoring my system to a few dates back.

Already deleted the torrent file( only got to 2.8%) and deleted bittorent.

How do I restore system a few dates back?


Thanks for the help guys.

---

### Post by -spy on 2008-09-15
Should I just do a system restore or try and use the anti-spyware links you recommended? Any negatives with system restore?

---

### Post by PocketDog on 2008-09-15
Both. Disabling system restore is recommend so your computer doesn't, at a later date, restore itself to a time when the problems were still resident.

---

### Post by -spy on 2008-09-15
> **PocketDog said:**
> Both. Disabling system restore is recommend so your computer doesn't, at a later date, restore itself to a time when the problems were still resident.

so.. I do system restore in safe mode (how many days back?) then disable it, then download the anti-virus software all while in safe mode?

---

### Post by PocketDog on 2008-09-15
Disabling system restore isn't really essential, just don't restore to a point prior to removing the malware. Download and install the software, boot in safe mode, scan and remove, reboot, set a restore point (assuming your PC is now clean). That's it :-)

---

### Post by -spy on 2008-09-15
> **PocketDog said:**
> Disabling system restore isn't really essential, just don't restore to a point prior to removing the malware. Download and install the software, boot in safe mode, scan and remove, reboot, set a restore point (assuming your PC is now clean). That's it :-)

Ok, just to make sure... I dont want to screw anything up..

1.) boot Vista in safe mode
2.) Install anti-virus software
3.) Scan and remove
4.) System restore to before viruses. (how long is recommended)
5.) reboot to Vista normal mode

correct?

---

### Post by PocketDog on 2008-09-15
No, install before booting into safe mode - installing in safe mode almost always won't work. After scanning and rebooting, SET a restore point, don't restore to one you already have.

---

### Post by nkri on 2008-09-15
> **WRDN said:**
> The virus/ nasty won't work under Ubuntu so you don't need to worry.

I would recommend you download the trial for [NOD32]("http://www.eset.com/") which has THE best virus detection rate in the world.

You could also scan the infected Windows partition from Ubuntu, using a program like Clam-AV (in repos).

+1.

NOD32 is easily the best protection around.  It's very fast, catches everything malicious, is much cheaper than Norton (if you get it through amazon), and has totally free customer support.

Also, definitely try ClamAV from Ubuntu.

Good luck!
-nkri

---

### Post by -spy on 2008-09-15
> **PocketDog said:**
> No, install before booting into safe mode - installing in safe mode almost always won't work. After scanning and rebooting, SET a restore point, don't restore to one you already have.

sorry, did this before your post..

here's what i did, hope I didn't screw anything up.

1.) booted in Vista safe mode
2.) System restored to 2 days ago, using a restore point already on there..
3.) booted up into normal Vista
--- viruses do NOT appear, no icons, no warnings, nothing---
4.) Downloaded Norton updates, havent installed/restarted yet
5.) went to the NOD32 website to download, started to DL then it said I had to uninstall Norton... I stopped there.

So, is the virus gone? Nothing has came up, all *appears* to be normal.

---

### Post by frank002 on 2008-09-15
Go to Symantec.com and search for the name of the virus. They usually have programs that will take care of removing specific viruses.

---

### Post by modmadmike on 2008-09-15
My sister's boyfriend loves Vista and he says that virus's aren't a problem for him because he reformats it every month.

---

### Post by jerome1232 on 2008-09-16
> **modmadmike said:**
> My sister's boyfriend loves Vista and he says that virus's aren't a problem for him because he reformats it every month.

rofl

> 
sorry, did this before your post..

here's what i did, hope I didn't screw anything up.

1.) booted in Vista safe mode
2.) System restored to 2 days ago, using a restore point already on there..
3.) booted up into normal Vista
--- viruses do NOT appear, no icons, no warnings, nothing---
4.) Downloaded Norton updates, havent installed/restarted yet
5.) went to the NOD32 website to download, started to DL then it said I had to uninstall Norton... I stopped there.

So, is the virus gone? Nothing has came up, all appears to be normal.

Sounds like you got it to me, but a second scan would be advisable. Using the NOD32 or Norton (since you did mention Norton was aware of the trojan before)

---

### Post by HungryMan on 2008-09-16
i suggest using a limited account next time, though with the way you got infected, i dont think it will really help much. (my XP installation got infected with 90+ virii the same way yours did, only i got in from an installer of flash)
and possibly programs that monitor ALL running processess (like rootkits that could hide even from process explorer)

btw, clam-AV can detect linux and windows virii?? cool... wait, that means i wasted my money having that hard drive scanned outside?!?

---

### Post by fiddledd on 2008-09-16
Here's what I use on Vista:

[Zonealarm Free](http://www.zonealarm.com/store/content/company/products/znalm/freeDownload.jsp)

[Avast Free](http://www.avast.com/eng/download-avast-home.html)

Windows Defender (comes with Vista)

I also use [F-Secure Backlight](http://www.f-secure.com/security_center/) once a week to scan for rootkits.

All of the above cost nothing, I've had no infections since I started with Vista > 6 months ago.

---

