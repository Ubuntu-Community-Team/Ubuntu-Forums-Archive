---
title: "I've got a virus on windows"
date: 2008-08-31
forum: Windows
---

### Post by balanovich on 2008-08-31
hi
I recently got a virus on windows and I wander if there is any way I can delete it from linux.
I've got linux 8.04 and windows xp.

thanks

---

### Post by Oldsoldier2003 on 2008-08-31
you can run clamav or avg on your windows partition. Linux antivirus programs check for windows viruses since there are so few instances of "in the wild" linux viruses due to the security model and nature of the linux operating system.

---

### Post by HermanAB on 2008-08-31
The best way to fix windows is with BartPE:
[http://nu2.nu/pebuilder/](http://nu2.nu/pebuilder/)

Put clamwin, spybot s&d and hijackthis on a CD and reboot.

---

### Post by Cato2 on 2008-08-31
What I would do is boot into Linux and buy a good commercial antivirus - NOD32 and Kaspersky are what I normally recommend as they have good coverage and don't slow the PC too much.  Download this to your Windows partition.  The suite versions should include antispyware and firewalls.  Using Ubuntu ensures you aren't giving your credit card to some malware - often there is more than one virus involved.

While I like Clamav in theory, I wouldn't expect it to have the up to the minute coverage of the zillions of variants of malware on Windows - even the commercial tools can't cover all the variants of a single virus, but they should do better.  Clamav is OK as a 2nd scan from Ubuntu, but the version in the Hardy repository is out of date (0.92 vs 0.93), and the PPA for Clamav didn't have a GPG key, so I couldn't check the Clamav package signature.  

Also download SUPERAntiSpyware, and Secunia PSI (checks for applications with security holes), etc, putting these on Windows partition as well.

Then reboot into Windows, and install these tools, as well as Firefox and Thunderbird if not used exclusively.  Within Firefox, install Adblock Plus (prevents ads which are a frequent vector for malware) and NoScript (blocks JavaScript, can re-enable quite easily - less convenient but adds a lot of security).

Once you've done a full scan in Windows using the new AV product, do another full scan using an online version of NOD32 or Kaspersky (whichever one you didn't install earlier.)

Then just use Ubuntu instead to avoid all this hassle :) ...  I recently switched an elderly relative over from XP to Ubuntu and she really likes it.

---

### Post by balanovich on 2008-09-01
Things are getting worst.
After a while in windows, everything jams. Everything's slow, nothing gets done. I can't run AVG. I had run AVG  and It found a few things, it deleted them, but it didn't fix anything. Probably becaus it didn't do a full scan.

I never manage fully scan my computer with avg. Is it normal that It can take more than 8 hours?
I tried spybot S&D. I managed to do a full scan.  It too found a lot of things, it fixed almost all. It had to reboot to fix a fes that were in use. I let it reboot, it scan my pc again, I finds the unfixed problems, I click on "fix the problem" it jams... I can move my mouse, but nothing else works.


I'd try the advised online scan, but most website are blocked.I guess the are blocked, becaus for some reason, firefox can't acces them when I'm on windows, but there's no problem on linux.

since I can't do nything on windows, I must try through linux. I installed clamAV, it said that the signature was more 200 days old but that before I could update it I needed to change or update something in /etc . What do I do?

I none the less scanned my windows partition but it didn't find anything.

---

### Post by aysiu on 2008-09-01
The only sure way to get rid of malware in Windows is to reinstall.

Once you do that, I'd recommend using a SuRun to set up a proper privilege escalation system (similar to the *sudo* that Ubuntu and Mac OS X have).

---

### Post by benny bronx on 2008-09-01
> Also download SUPERAntiSpyware,

Although you may have to do a reinstall. I would definitely  try to download the free version and run a scan.  It is that good.  Try clearing your Firefox cache and private data and see if you can download the program.

---

### Post by Thelasko on 2008-09-02
> **aysiu said:**
> The only sure way to get rid of malware in Windows is to reinstall.

Once you do that, I'd recommend using a SuRun to set up a proper privilege escalation system (similar to the *sudo* that Ubuntu and Mac OS X have).

Yes, the key to securing Windows is your initial installation.  Create one user account that is an "administrator" and **NEVER USE IT.**  Any account that you use to browse the internet and do day to day work should be set as "users" and you should have very few problems.

In order to install software and make any changes to the system, you will have to log in as the administrator.

I use this setup on my parents' machine and have never had a problem.  They don't even know the password to the administrator account, so they can't install software without my knowledge.  I've only had to go over to their house once in the past year for a computer related issue.  (I suppose I could have them run Ubuntu, but I think they would resist.)

---

### Post by aysiu on 2008-09-02
Actually SuRun makes it easy to temporarily escalate privileges from an otherwise limited user account. That way you don't have to keep switching user accounts to install software or Windows updates.

---

### Post by fiddledd on 2008-09-02
> **aysiu said:**
> Actually SuRun makes it easy to temporarily escalate privileges from an otherwise limited user account. That way you don't have to keep switching user accounts to install software or Windows updates.

Do you know, I knew you would post that. You always beat me to it with SuRun.:)

---

### Post by Thelasko on 2008-09-02
> **aysiu said:**
> Actually SuRun makes it easy to temporarily escalate privileges from an otherwise limited user account. That way you don't have to keep switching user accounts to install software or Windows updates.

Right, I forgot to mention that.  I've never used it personally.  For a user that's in the know, it sounds useful. 

My only concern is that people like my parents will haplessly enter their password while a virus tries to install itself.  All that needs to happen is some pop-up will tell them their computer is in danger and they would gladly enter their password.  It's helpful to have some other human make sure the program isn't a threat.

Personally, I haven't noticed any issues with updates on my parents' machine.

---

### Post by aysiu on 2008-09-02
Well, there's not much that can be done about social engineering, unfortunately. If you teach them to log in as the administrator to install software, they could always install the malware then or, worse yet, get in the habit of logging into the administrative account for convenience's sake.

The only way to prevent social engineering attacks is through education.

---

### Post by aysiu on 2008-09-02
Well, there's not much that can be done about social engineering, unfortunately. If you teach them to log in as the administrator to install software, they could always install the malware then or, worse yet, get in the habit of logging into the administrative account for convenience's sake.

The only way to prevent social engineering attacks is through education.

---

### Post by LaRoza on 2008-09-02
> **aysiu said:**
> Well, there's not much that can be done about social engineering, unfortunately. If you teach them to log in as the administrator to install software, they could always install the malware then or, worse yet, get in the habit of logging into the administrative account for convenience's sake.

The only way to prevent social engineering attacks is through education.

> **aysiu said:**
> Well, there's not much that can be done about social engineering, unfortunately. If you teach them to log in as the administrator to install software, they could always install the malware then or, worse yet, get in the habit of logging into the administrative account for convenience's sake.

The only way to prevent social engineering attacks is through education.

Not sure which post to address...

I agree 100%. I got my sister's family in the correct mindset, where the admin account is never used (and in fact, I heard of a few heated arguments when the other person was found using it...)

---

### Post by Thelasko on 2008-09-02
> If you teach them to log in as the administrator to install software
I don't do that.

I find it easier to make the trip to install software myself (which is a rare occurrence), than to deal with the effects of malware and identity theft.

I'm fortunate to live relatively close to my parents, it only takes me about an hour to drive over, install software, and drive home.  If they were to get a virus, I could easily spend a day getting their system back up and running securely.  Dealing with the effects of identity theft could take months.  I think it's a wise investment in both time, and peace of mind.

As far as I can tell, updates have always worked properly on that machine.

---

### Post by Cato2 on 2008-09-05
> **balanovich said:**
> I'd try the advised online scan, but most website are blocked.I guess the are blocked, becaus for some reason, firefox can't acces them when I'm on windows, but there's no problem on linux.


You really need to get onto a Windows security forum for help here - probably best to use Ubuntu to backup all important data and settings now, then do a full re-install wiping the Windows partition.  However if you can't do that for some reason:

- are you rebooting into Safe mode in Windows?

- have you tried simply downloading a trial version of NOD32 and installing that?  If you can boot into Safe mode you should be able to scan with NOD32 from there?  You need to have a complete NOD32 or Kaspersky installed and successfully scan the whole disk.  NOD32 is very fast so try that perhaps.

- have you run SuperAntispyware in safe mode as well?

- [http://forums.majorgeeks.com/showthread.php?t=35407](http://forums.majorgeeks.com/showthread.php?t=35407) - Majorgeeks guide to removing malware - recommends use of SuperAntiSpyware, Spybot S&D, ComboFix, MGTools. SuperAntiSpyware is free and worked very well - better than Spybot S&D which missed a few things.   You may have to try several of these, e.g. one Windows PC I decontaminated had a variant of Virtumonde that Vundofix did not remove.  I used Combofix and Superantispyware.

- find and install a good rootkit hunter (separate to antivirus, some include but some don't) in case you have those too

Some other info from my home wiki (see [http://twiki.org](http://twiki.org) or apt-get install twiki :) ):

   * [http://forums.spybot.info/showthread.php?t=16806](http://forums.spybot.info/showthread.php?t=16806) Spybot guide to spyware removal - Run Kaspersky online, Spybot S&D, and !HiJackThis, then post in forum

   * Good - [http://wiki.castlecops.com/Malware_Removal_and_Prevention:_Introduction](http://wiki.castlecops.com/Malware_Removal_and_Prevention:_Introduction) CastleCops on Malware removal and prevention - doesn't recommend tools, but has good list of links to available tools, including [http://wiki.castlecops.com/Malware_Removal:_Online_Anti-Virus_Scans](http://wiki.castlecops.com/Malware_Removal:_Online_Anti-Virus_Scans) - online antivirus scans

As you can see this is a lot of hassle - I would do a backup of all your data NOW and simply re-install.  As others have pointed out you can never be completely sure all the malware is gone (there are many variants within a 'single malware', some of which may not be detected), so switching to Ubuntu once you have this mess cleared up will really help.  (I switched an 83-year old relative a few weeks ago to Ubuntu and she loves it, and even runs one Windows app via WINE)

---

### Post by balanovich on 2008-09-05
All usefull sites are blocked.  I can't go on NOD32' site nor kaspersky 's. If I try, It says that firefow can't connect. deleting the cache or other things didn't work.

All the crashs, bugs, problem are still there in safe mode. (except one, my background was a link to a crapy site)

I downloaded NOD32 with linux and I'm gonna try to instal it with a USB key.

Anti-spyware and anti adware progams did a few thing, but the main virus wasn't touched.

Thanks for all the freeware info. I'll look into SuRun; I can't go only on linux, I play games.

And the free version of avg must not be very good. I know how I got the virus. I mounted a .iso that I downloaded. The second I did that, my background changed, I got popo-ups, new shortcuts were added etc etc. And if I scan that single file with AVG, It doesn't see anything wrong.


Anyways, I was planning to buy a new motherboard so reformating was innevitable. Next time, Ill just be sure that I have a few "defensive" programs on my windows partition.

Thank you very much

---

### Post by cardinals_fan on 2008-09-05
> **aysiu said:**
> The only sure way to get rid of malware in Windows is to reinstall.

Once you do that, I'd recommend using a SuRun to set up a proper privilege escalation system (similar to the *sudo* that Ubuntu and Mac OS X have).
+1

This is my recommendation.  Even if you manage to rid your Windows install of this virus, you'll get another one without some basic security.

---

### Post by Cato2 on 2008-09-06
> **balanovich said:**
> 
I downloaded NOD32 with linux and I'm gonna try to instal it with a USB key.
...
And the free version of avg must not be very good. I know how I got the virus. I mounted a .iso that I downloaded. The second I did that, my background changed, I got popo-ups, new shortcuts were added etc etc. And if I scan that single file with AVG, It doesn't see anything wrong.


AVG isn't very good in my experience, have had some friends who still got viruses when using AVG free, but that could happen with any antivirus.  

Since your Windows setup is so hosed, it might be good to create a BartPE CD that includes your copy of NOD32, so you can boot entirely from CD.  Or if you have another Windows PC simply install NOD32 there and connect your disk to that PC for scanning.

When you re-install Windows, be sure to download Microsoft TweakUI Powertoy and use it to turn off Autorun on all CDs and removable media.  This would have stopped the virus from infecting your PC.

While SuRun is a very good idea, it's not a panacea, as malware could still simply delete or corrupt files that the non-admin user has access rights to.

---

### Post by volkswagner on 2008-09-09
> **aysiu said:**
> The only sure way to get rid of malware in Windows is to reinstall.

Once you do that, I'd recommend using a SuRun to set up a proper privilege escalation system (similar to the *sudo* that Ubuntu and Mac OS X have).


Not a hijack:  Glad to see this.  I recently did a clean install of XP for my sister (her family computer).  I only heard of using under privileged accounts.  I set up individual limited user accounts for each family member.  What nightmare.  Wish I knew of SuRun (researching now).  

I was so frustrated with the multi user setup and the limited accounts.  The first warning was CA antispam did not have sufficient privileges (annoying).  Then having itunes for 4 users and one library took some added steps.  

One last note.  It was so sad to watch a clean install incrementally get slower and slower as updates, security measures, programs and services were added.

This weekend of windows admin, increased my appreciation for Linux ten fold.  Now I will think twice when getting caught in the middle of permission hell, there is a reason for it.

---

