---
title: "virus cleaning on clients computer"
date: 2011-06-28
forum: The Cafe
---

### Post by polardude1983 on 2011-06-28
So your client has a virus on their pc and your at their house. How do you guys/gals clean viruses off their pc. I mean yes you run a virus scanner but sometimes that could take hours. But you really don't wanna sit at a clients house for hours. So is there some sort of remote scanning or anything?

I know the best kind of virus scanning is from a live cd so that you have access to all files in the windows drive.

Anyways any ideas?

Anybody also know what windows directory/folder is the most susceptible to viruses? is it the C:Windows/Temp? wanting to find a directory that would have the most probability of having viruses but not take more then 15 min to scan ideally.

---

### Post by Bandit on 2011-06-29
FORMAT C:



I am not a house cleaner, I will offer to reinstall windows if they have the original CDs. You can however get live linux CDs that come with Virus scanning software that will allow you to go on thier harddrive and remove personal files and put them on a USB stick and then scan them. Then you can reinstall windows. 

I however charge a nice premium for this starting at $75 USD for the first hour and $50 USD every hour after that I have to screw with their system. If I come out to their house and they dont have what I need in advance, I still charge the $75. You will be suprised at what people can find they couldnt find before if they know you charge $75 for the first hour weather your there 5mins or 59m.

---

### Post by doas777 on 2011-06-29
I don't usually do housecalls, but if I am looking at it, I will generally make recommendations to them (make a checklist for them) asking them to purchase the needed software, uninstall any stupid stuff, etc. if they don;t think they can do it, its all the easier to convince them to let me take it home to work on. I have no real problem cleaning up their messes for a remarkably reasonable donation, as long as I can do it in my den.

get the [sysinternals suite]("http://technet.microsoft.com/en-us/sysinternals/bb842062"), and extract it to a cd with some other malware tools. don't use a thumb drive or any other writable media. (I once disinfected the same box 4 times in rapid sucession before I realized somthing had rooted the thumbdrive I had my toolbox on....)

use procexp to kill any oddball processes so you can work. autoruns is also very handy for identifying autostarting code. if you notice somthing in autoruns that is also going haywire in procexp, disable it in autoruns, and then reboot to clear it.

To speed up your task, always start with CCLeaner. kills all the unneeded temp files (where malware often live before first reboot after infection) and reduces the number of files you need to scan. empty the trash and run disk cleanup while you are at it.

[HijackThis]("http://free.antivirus.com/hijackthis/") is getting a little aged, but is still a good tool for finding hooks into your system. be aware, most of the findings in hjt are not problems. it dumps info, some of which may be malicious. research findings as needed before removing them. 

the Add/remove programs applet (appwiz.cpl) is a good next stop. uninstall anything stupid (browser toolbars, ad-supported software, and anything with a random looking filename that you cant otherwise recognize.)

next I would check their virus scanner. usually it is expired. i uninstall it and then download [msse ]("http://www.microsoft.com/en-us/security_essentials/default.aspx"). turn up all the settings, and start it on a full scan.
tell them to call you if it finds anything. 

many folks on the forums say that using AV is worse than not, because it provides a "false sense of security", but in the long run, no infected pc can be trusted ever again, unless it is completely rebuilt, and I dont' know about your relatives, but mine will reinfect it soon enough.

---

### Post by 3rdalbum on 2011-06-29
If it's one of those viruses that are highly visible and display fake anti-virus warnings ("Your PC is INFECTED! Click this balloon to buy Viruscleaner Pro 2010 today!") I usually do a Google search for that message and then follow the directions to remove files and registry entries associated with the virus.

---

### Post by wizard10000 on 2011-06-29
I use malwarebytes.  Hasn't failed me yet.

---

### Post by wizard10000 on 2011-06-29
> **Bandit said:**
> FORMAT C:

I am not a house cleaner, I will offer to reinstall windows if they have the original CDs. You can however get live linux CDs that come with Virus scanning software that will allow you to go on thier harddrive and remove personal files and put them on a USB stick and then scan them. Then you can reinstall windows. 

I however charge a nice premium for this starting at $75 USD for the first hour and $50 USD every hour after that I have to screw with their system. If I come out to their house and they dont have what I need in advance, I still charge the $75. You will be suprised at what people can find they couldnt find before if they know you charge $75 for the first hour weather your there 5mins or 59m.

I've been in the deskside support business for almost 20 years - I have 25 helpdesk analysts and 13 deskside techs working for me and if any of them suggested formatting a hard drive as a first course of action we'd be doing some serious technician retraining - and at your hourly rate if you offered to format my hard drive I guess I'd show you the door.

I wouldn't pay a professional to "screw with" my system - I pay him to fix it - and any time a tech offers to format a hard drive I know the tech has no idea what he's doing.

The rule in my organization is that it takes an average of four hours to archive, reimage, reinstall and restore files, applications and settings but at the end of the day the desktop had better look the same as it did before the technician touched it.  Reimages are only authorized if it'd take less time to reimage a PC than it would to fix it - and that never happens.  The only person in the company who can authorize blowing away somebody's hard drive is me, and with 3,300 users that happens about twice a month.

I get a feeling I'd have to fire you after a couple weeks  :D

---

### Post by Nyromith on 2011-06-29
I like the AVG rescue CD. It scans the computer before boot time, so viruses can't use many of their hiding and remove-resistance technics.
[http://www.avg.com/ww-en/avg-rescue-cd](http://www.avg.com/ww-en/avg-rescue-cd)

---

### Post by alphacrucis2 on 2011-06-29
> **wizard10000 said:**
> I use malwarebytes.  Hasn't failed me yet.

+1. If malwarebytes doesn't do the trick then its reinstall time.

---

### Post by cprofitt on 2011-06-29
> **wizard10000 said:**
> I use malwarebytes.  Hasn't failed me yet.


I have had it fail several times recently... then again if you do not 'know' you have a virus you would never know it failed... and the virus I was working on was only seen due to a wireshark capture.

---

### Post by Bandit on 2011-06-29
> **wizard10000 said:**
> I've been in the deskside support business for almost 20 years - I have 25 helpdesk analysts and 13 deskside techs working for me and if any of them suggested formatting a hard drive as a first course of action we'd be doing some serious technician retraining - and at your hourly rate if you offered to format my hard drive I guess I'd show you the door.

One, I stated I dont do house cleaning.
Two, I used to get constant calls as late or early as you want to call it, 3am in the morning. The Fee I now charge was to stop that ****.

You dont call a rocket scientist to fix you lawn mower, you dont call me unscrew your computer. See my point. 

I guess I should have pointed out I send everyone that first comes to me to my friend that runs a PC shop for a living. If they insist they want me then I tell them my Fees. I DONT WANT to pick maleware from a users computer all day long, thats not my thing. But if its that important to them they can pay, or else **** off.

Until you start getting 3 or 4 random people most you dont know calling you all hours of the night because their idiots you prob will not understand this.

That being said, of the off chance I did work for  you. I would boot live CD, remove the clients files best I could and scan them to make sure their clean, try to repair the ones that wasnt. Making sure they are safe, then try to first update the virus software if any is installed, scan. blahh blahh, If need boot live CD and do a better scan. Then if thats not working, try to remove them manually(and have done this many times when its just one or two PITA programs), if that doesnt work or cant remove them for some crazy duplicating issue see if its possible to restore or reinstall windows back to their lovely desktop back before they tried to run every virus on the face of the earth. I am A+ certified I can tell you the "proper way" of doing this all day long. But its not what I want to do in life and rather avoid at all cost.


But lets be honest, quickest and easiest way is to copy and scan their important files to USB and then re install windows. It will take about 30 mins, and normally when they get back their system its running all new and spiffy and that makes the customer very happy. But keep in mind a server I would never do this to, I am in referring to average peoples computers that just email and upload pics 99% of the time.



> The rule in my organization is that it takes an average of four hours to archive, reimage, reinstall and restore files, applications and settings but at the end of the day the desktop had better look the same as it did before the technician touched it. Reimages are only authorized if it'd take less time to reimage a PC than it would to fix it - and that never happens. The only person in the company who can authorize blowing away somebody's hard drive is me, and with 3,300 users that happens about twice a month.

I get a feeling I'd have to fire you after a couple weeks 

4 hours, Bubba, you gota get some new gear hehe..  Dont worry though, what I do personal and what I do professional is two different things. :)

---

### Post by cprofitt on 2011-06-29
> **wizard10000 said:**
> The rule in my organization is that it takes an average of four hours to archive, reimage, reinstall and restore files, applications and settings but at the end of the day the desktop had better look the same as it did before the technician touched it.  Reimages are only authorized if it'd take less time to reimage a PC than it would to fix it - and that never happens.  The only person in the company who can authorize blowing away somebody's hard drive is me, and with 3,300 users that happens about twice a month.

I get a feeling I'd have to fire you after a couple weeks  :D

Wow... I guess in my organization we have a better process for imagine as our process takes only 1 to 1.5 hours. I do agree with you though that removing a piece of malware is easier than a reimage 99% of the time. We just had our first re-image due to a virus in over two years.

---

### Post by aaaantoine on 2011-06-29
I had a fun one yesterday.  Vista AntiVirus 2011 or some crap like that.

It changed the default .exe opener to the AntiVirus app so it would yell that the app is infected with a keylogger before opening it -- if it opened it.  To get around the constant barrage of pop ups I sniffed out and found the .exe file that was doing this, and renamed it to something like .exe.evil

But now, I couldn't open anything at all, because Windows would keep asking what program I wanted to use to open .exe files.  Fortunately, I had a command prompt open, and using this I was able to work around that nonsense.

Sure enough, MalwareBytes caught and erased the rogue, along with about 150 other issues.  It also repaired the exe functionality.  Total time was less than 2 hours.  It could have been shorter but the PC was running slow.

---

### Post by wizard10000 on 2011-06-29
> **cprofitt said:**
> Wow... I guess in my organization we have a better process for imagine as our process takes only 1 to 1.5 hours. I do agree with you though that removing a piece of malware is easier than a reimage 99% of the time. We just had our first re-image due to a virus in over two years.

Nope - not necessarily a better process.  We can reimage in less than an hour easily - identifying, archiving and restoring user data and settings and reinstalling applications is what takes the time.  We have about 300 custom applications that store data in weird places - plus techs restore the user's entire profile - favorites, cookies, start menu, all application settings, yadda yadda.  Like I said, when the tech leaves you'e never know he was there and that takes time.

---

### Post by LowSky on 2011-06-29
When it comes to personal PC repairs most people only call when things get bad. They dont run virus scans or do their own backups, so when things go bad they go really bad.

I rather do a full reinstall of Windows than sit there scanning away. Most normal users don't have much on their computers anyway. Its why today's PC rarely have hard drives over 500GB, even when 1-2TB is realistically cheap. Most home users worry more about Facebook access than using Outlook. So if i do a complete wipe its cleaner than fishing with antivirus or antimalware programs that might not find everything.

---

### Post by Primefalcon on 2011-06-29
sudo apt-get install clamav

to update use:
sudo freshclam

to scan
clamscan file
or
clamscan -R directory

---

### Post by Ric_NYC on 2011-06-29
> **Nyromith said:**
> I like the AVG rescue CD. It scans the computer before boot time, so viruses can't use many of their hiding and remove-resistance technics.
[http://www.avg.com/ww-en/avg-rescue-cd](http://www.avg.com/ww-en/avg-rescue-cd)


Thanks. I didn't know about it.

---

### Post by Primefalcon on 2011-06-29
or even better than avg rescue dont forget the systemrescuecd

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

info here: [http://www.sysresccd.org/System-tools](http://www.sysresccd.org/System-tools)

it comes with testdesk (data recovery), virus scanners and far more

---

### Post by Dangertux on 2011-06-29
> I am A+ certified I can tell you the "proper way" of doing this all day  long. But its not what I want to do in life and rather avoid at all  cost.

Sounds like you know just enough to get yourself in trouble ;-)

If you don't like doing housecalls, don't do them. Unless of course you need the money, in which case beggars can't be choosers, right?

If I was a plumber, I wouldn't complain because my customer didn't know how to maintain their garbage disposal. I would shut up, fix it, and leave them with the bill.  If you work in the service and support industry, you are there for service and support not your opinion on why your customers are morons. 

Let's assume for a second that I called you for your services because I felt you were qualified to fix my problem. If you showed up in my home or place of business with that type of attitude, not only would I escort you to the door, I'd stiff you on the bill. If you don't like your job go do another, I'm so tired of mediocre IT techs with a sense of entitlement.

---

### Post by Gremlinzzz on 2011-06-29
> **Bandit said:**
> FORMAT C:



I am not a house cleaner, I will offer to reinstall windows if they have the original CDs. You can however get live linux CDs that come with Virus scanning software that will allow you to go on thier harddrive and remove personal files and put them on a USB stick and then scan them. Then you can reinstall windows. 

I however charge a nice premium for this starting at $75 USD for the first hour and $50 USD every hour after that I have to screw with their system. If I come out to their house and they dont have what I need in advance, I still charge the $75. You will be suprised at what people can find they couldnt find before if they know you charge $75 for the first hour weather your there 5mins or 59m.

At those prices you chose the right screen name:D YOU DO CHARGE ALLOT OF MONEY

[http://www.youtube.com/watch?v=cpbbuaIA3Ds](http://www.youtube.com/watch?v=cpbbuaIA3Ds)

---

### Post by tumbes2000 on 2011-06-29
> **cprofitt said:**
> I have had it fail several times recently... then again if you do not 'know' you have a virus you would never know it failed... and the virus I was working on was only seen due to a wireshark capture.


Malware is pretty good, but I have had it fail to remove viruses in the past.

---

### Post by wizard10000 on 2011-06-29
> **Dangertux said:**
> I'm so tired of mediocre IT techs with a sense of entitlement.

Fortunately that's the mark of a $30,000 desktop tech.  A $60,000 desktop tech knows better or gets unemployed  ;)

---

### Post by Bandit on 2011-06-29
> **Dangertux said:**
> Sounds like you know just enough to get yourself in trouble ;-)

If you don't like doing housecalls, don't do them. ..........
You miss understand me. What I do personal and professional is different. I wouldnt say I know just enough to get into trouble, thats kinda rude and a bad cal unless you actually know the person. Your just not understanding my point of view. If I work for a company and I get called in because of server issues, thats my job and its what I get paid for. When I get calls from people that I never meet before in my life wanting me to fix their computer all hours of the night. Thats running into my personal business. I actually tried and tried to tell people I dont do house calls, then folks tried bringing **** to me a night or during the day while I was working. I tried to tell them I dont work on peoples computers. That doesnt seem to click in most peoples head. But MONEY O' GOD everyone understands money. You mention $75 bucks and no one bothers you unless its a real emergency that cant wait until a PC shop opens.
In my area, I am too well known as being one of the foremost IT experts, schools and college instructors both listen to me when I make suggestions. The burden of this is what I mentioned above, which is why I have to make a line somewhere. $75 bucks is the only way to know if someone truly needs help, or f'n farmville want load... See my point.. ;-)

> **Gremlinzzz said:**
> At those prices you chose the right screen name:D YOU DO CHARGE ALLOT OF MONEY

[http://www.youtube.com/watch?v=cpbbuaIA3Ds](http://www.youtube.com/watch?v=cpbbuaIA3Ds)
LOL

---

### Post by wolfen69 on 2011-06-29
> **Bandit said:**
> FORMAT C:

I am not a house cleaner, I will offer to reinstall windows if they have the original CDs.

Exactly. I never scan for viruses. Doing that can take hours, and reinstalling is actually quicker. But I don't need the original discs, as I have all OEM and retail discs and just use their product key. Plus I have driver discs with over 100,000 drivers. Easy.

---

### Post by Dangertux on 2011-06-29
> **Bandit said:**
> You miss understand me. What I do personal and professional is different. I wouldnt say I know just enough to get into trouble, thats kinda rude and a bad cal unless you actually know the person. Your just not understanding my point of view. If I work for a company and I get called in because of server issues, thats my job and its what I get paid for. When I get calls from people that I never meet before in my life wanting me to fix their computer all hours of the night. Thats running into my personal business. I actually tried and tried to tell people I dont do house calls, then folks tried bringing **** to me a night or during the day while I was working. I tried to tell them I dont work on peoples computers. That doesnt seem to click in most peoples head. But MONEY O' GOD everyone understands money. You mention $75 bucks and no one bothers you unless its a real emergency that cant wait until a PC shop opens.
In my area, I am too well known as being one of the foremost IT experts, schools and college instructors both listen to me when I make suggestions. The burden of this is what I mentioned above, which is why I have to make a line somewhere. $75 bucks is the only way to know if someone truly needs help, or f'n farmville want load... See my point.. ;-)


LOL

First off the knowing just enough to get you in trouble was not an insult to you. However, a lot of techs throw around certs. It was meant as a joke hence the winking smiley face. Don't take it personally, you're right I don't know you, certainly not enough to judge you on based on a stereotype.

As far as what you do professionally versus personally I think it is wise to draw a line. If you really do have random people calling you at 3 am , then I would personally just change my phone # lol.

As I stated before, I am sick of mediocre IT techs with a sense of entitlement(As they are the ones whose mess I'm usually cleaning up). If the shoe fits , wear it. If not, I'm not talking about you ;-)

---

### Post by alphacrucis2 on 2011-06-29
In a corporate situation I agree the simplest way would be a clean reimage. Forget about user data. If the user was keeping important data only on their PC or laptop then the user should be fired.

---

### Post by Bandit on 2011-06-29
> **Dangertux said:**
> First off the knowing just enough to get you in trouble was not an insult to you. However, a lot of techs throw around certs. It was meant as a joke hence the winking smiley face. Don't take it personally, you're right I don't know you, certainly not enough to judge you on based on a stereotype.

As far as what you do professionally versus personally I think it is wise to draw a line. If you really do have random people calling you at 3 am , then I would personally just change my phone # lol.

As I stated before, I am sick of mediocre IT techs with a sense of entitlement(As they are the ones whose mess I'm usually cleaning up). If the shoe fits , wear it. If not, I'm not talking about you ;-)
All kewl.. :-)
I know how you feel on the mediocre techs, going back to college has got my arsh in flames. You got all the people that hound you in class like flys on s___t waiting for you to write code only to hear them trying to put in for jobs in the area that I put in for. Its coming to the point that I have started ignoring all them and being a jerk. Which in the long run will be better for them to learn the mess them selfs and not get a job based on my knowledge. /sigh.. Need my blood pressure pill.. hehe

---

### Post by wolfen69 on 2011-06-29
> **Gremlinzzz said:**
> At those prices you chose the right screen name:D YOU DO CHARGE ALLOT OF MONEY

[http://www.youtube.com/watch?v=cpbbuaIA3Ds](http://www.youtube.com/watch?v=cpbbuaIA3Ds)

That's not a lot of money. Most techs charge more. I charge about $90-100 for the reinstall regardless of the time involved. If I don't charge decently, I don't eat.

---

### Post by Bandit on 2011-06-29
> **wolfen69 said:**
> That's not a lot of money. Most techs charge more. I charge about $90-100 for the reinstall regardless of the time involved. If I don't charge decently, I don't eat.

Actually your right. Even one of my best friends is the one I mentioned before that owns his PC store. I accidentally (go a head and lol) partitioned the wrong drive in my system one day and almost lost all my files. I called him up and asked him how much to throw my drive on his block and pull the files off. He said $25 and I was happy to pay it. It took him less then 5 mins. I dont have a problem with that, I needed my files and he needs to eat and pay for hardware.

---

### Post by wolfen69 on 2011-06-29
> **Bandit said:**
> I accidentally (go a head and lol) partitioned the wrong drive in my system one day and almost lost all my files.

Try doing that to a customers computer. :( Luckily, I got his files back with MagicRescue (in the repos). But really, I think $100 is fair for a couple hours. 

My thing is, I just don't trust the install anymore once it gets infected and just backup their stuff to a ext HD and reinstall. I guarantee satisfaction, so a fresh install gives me the best chance to make them happy.

---

### Post by zer010 on 2011-06-29
I'm actually doing a job now...well, XP is updating...

Customer wanted the PC cleaned up and sped up.  I ran Malwarebytes and it came back with ~480 instances.  Not only that, but it was full of crap programs and toolbars among other things. I gave him a call and asked what exactly he wanted to keep and what to get rid of.  He said he only wanted the music that was on it. So I went ahead and backed all that up and went to reinstall XP.  

Besides a fresh install, I also clean out the dust bunnies from the case and fans and this one was BAD. Doesn't make much sense to clean up what's on the hard drive if the machine's gonna overheat and burn out down the road.  

Since I have no certs and this is just side work, I can't really charge a whole lot, but if I start getting more requests I'll have to go up on fees.

---

### Post by Bandit on 2011-06-29
> **zer010 said:**
> I'm actually doing a job now...well, XP is updating...



Dont know if they still have it for XP, but you can purchase a service pack CD or even a new copy of an existing CD with the current service packs. I got one of the newer XP CDs with all the service packs for like 5$ that they charge for shipping and handling. Some folks may not no this, but if you Windows disc get ruined, you can get replacements. As long as you have your serial codes at least.

---

### Post by wolfen69 on 2011-06-29
> **Bandit said:**
> Dont know if they still have it for XP, but you can purchase a service pack CD or even a new copy of an existing CD with the current service packs. I got one of the newer XP CDs with all the service packs for like 5$ that they charge for shipping and handling. Some folks may not no this, but if you Windows disc get ruined, you can get replacements. As long as you have your serial codes at least.

It doesn't really matter where you get your windows cd's from, it only matters if you use a genuine product key for install. I like torrents myself. 

Every pc repair shop uses 1 cd for let's say win xp pro oem. It will work on any number of computers as long as you have a legit license.

---

### Post by Bandit on 2011-06-29
> **wolfen69 said:**
> It doesn't really matter where you get your windows cd's from, it only matters if you use a genuine product key for install. I like torrents myself. 

Every pc repair shop uses 1 cd for let's say win xp pro oem. It will work on any number of computers as long as you have a legit license.
True that, I was refering to having a old damaged CD, or needing one with more recent service packs to be able to boot the system. I ran into this before were a friend had a existing copy of WinXP OEM that came out before SP1 and when we upgraded his system we went to do a fresh install and the system wouldnt boot, turned out after little research we needed at least SP2 for the mobo to be compatible. So we had to get a new WinXP CD from MS that included SP2 using his activation code, which happily booted up and worked. :)

---

### Post by Dangertux on 2011-06-29
You can also slipstream all the service packs in to the initial install. This is doable with any version of Windows. Just google it if you want to know how.

Saves you time after reinstall ; don't have to wait 2 hours for updates to download

---

### Post by Timmer1240 on 2011-06-30
I use malwarebytes cccleaner superantispyware spybot some online scanners it usually takes awhile to get all cleaned up then I toggle system restore to get rid of infected restore points and defrag the system when its all cleaned up.Glad i use Linux so I dont have to do all this nonsense to my own machine now!

---

### Post by Timmer1240 on 2011-06-30
And this is a very good guide for cleaning windows machines![http://forums.majorgeeks.com/showthread.php?t=35407](http://forums.majorgeeks.com/showthread.php?t=35407)

---

### Post by wolfen69 on 2011-06-30
> **Dangertux said:**
> You can also slipstream all the service packs in to the initial install.

You can get theses images from bittorrent. They are updated every month. No need to do it yourself. 

Once again, only do this if you have a valid windows license. I do not advocate stealing.

---

### Post by wolfen69 on 2011-06-30
> **Timmer1240 said:**
> And this is a very good guide for cleaning windows machines![http://forums.majorgeeks.com/showthread.php?t=35407](http://forums.majorgeeks.com/showthread.php?t=35407)

The only "good" windows machine is the one ***I*** installed. I trust no one else for how it *should* be done.

---

### Post by Thewhistlingwind on 2011-06-30
> **Dangertux said:**
>  I'm so tired of mediocre IT techs with a sense of entitlement.

Honestly, if my only solution I could offer was nuking someones hard drive, unless they explicitly told me that's what they wanted me to do, I'd tell them I can't fix it and I wouldn't charge.

Doubt they'll ever call you again after that.

---

### Post by PhillyPhil on 2011-06-30
> **Bandit said:**
>  You dont call a rocket scientist to fix you lawn mower, you dont call me unscrew your computer. See my point. 



Or alternatively: you don't call a lawnmower mechanic to fix your space shuttle...

---

### Post by zer010 on 2011-06-30
> **Bandit said:**
> Dont know if they still have it for XP, but you can purchase a service pack CD or even a new copy of an existing CD with the current service packs. I got one of the newer XP CDs with all the service packs for like 5$ that they charge for shipping and handling. Some folks may not no this, but if you Windows disc get ruined, you can get replacements. As long as you have your serial codes at least.
I currently have an XP SP2 OEM disc that's been quite useful.

> **Bandit said:**
> I ran into this before were a friend had a existing copy of WinXP OEM that came out before SP1 and when we upgraded his system we went to do a fresh install and the system wouldnt boot, turned out after little research we needed at least SP2 for the mobo to be compatible. 
Good info! I don't know if it applies, but I've run into a situation where I used my disc to install on a Dell laptop. Install went through without a hitch, but on the final reboot it was like nothing had been installed. I figured my disc might be tagged for desktops only. Haven't tried it on another laptop since to confirm though. 
*I ONLY install Windows with a valid Product code. If they don't have one.... it's time for Ubuntu! ~_^d

---

### Post by wizard10000 on 2011-06-30
> **Dangertux said:**
> You can also slipstream all the service packs in to the initial install.

This.

Slipstreaming SP3 onto a CD isn't particularly difficult - I personally won't connect an XP machine to the internet unless it's got at least SP2.

Back when XP was in beta I was part of a pretty good-sized group of testers who howled at MS about why XP's firewall wasn't enabled by default but the marketing guys won over the technical guys, which happens with MS fairly often. MS didn't turn the firewall on by default until SP2.

Sometimes MS gets hammered pretty good from the inside out, though.  Completely OT, but I used to be a Microsoft MVP - which if you're a Windows geek is a fairly coveted title.  Back in the day I was pretty heavily into Windows - in addition to the MVP I was also one of the 500 core beta testers for Microsoft Games, which ain't as much fun as you'd think it'd be - I also got into one MS hardware beta back before the Intellimouse came out - they sent me an brick-shaped mouse with some strange extra buttons cobbled on but I digress.

In addition to a bunch of other goodies MS had a three-day-long shindig for MVPs once a year in Redmond - they sprung for hotel and meals and all you had to do was get there.  I was able to convince my employer to buy me a plane ticket.

Anyway, they had a one-day seminar for MVPs on Windows XP.  When we got to the piece about Windows Product Activation I asked the presenter if MS was going to lower the price of Windows since the price of piracy was *already* built into the OS and that any money they made on WPA was pure profit.  Got a standing ovation from 600 MVPs and a "we haven't set the price of XP yet" from Microsoft  :D

Anyway, sorry for the derailment but I thought it was a pretty good story  ;)

---

### Post by wizard10000 on 2011-06-30
> **Bandit said:**
> True that, I was refering to having a old damaged CD, or needing one with more recent service packs to be able to boot the system. I ran into this before were a friend had a existing copy of WinXP OEM that came out before SP1 and when we upgraded his system we went to do a fresh install and the system wouldnt boot, turned out after little research we needed at least SP2 for the mobo to be compatible. So we had to get a new WinXP CD from MS that included SP2 using his activation code, which happily booted up and worked. :)

MS doesn't provide OEM CDs and won't exchange an OEM license for a retail license  - and using an OEM activation code on a retail CD is a pretty good trick but that's beside the point  :)

Got two questions.

1.  Who was responsible for determining hardware compatibility before doing the OS install?

2.  Why did the customer have to wait for a new CD from MS rather than the tech slipstreaming the required service pack onto a fresh CD?  Since we're talking about a retail CD it would be reasonable to to expect the tech to already have a CD with the current service pack available.

I'm not hammering on you, I would have asked any one of my people the same questions if they tied up a customer's hardware because they arrived at the customer's workspace unprepared.

---

### Post by Bandit on 2011-06-30
> **wizard10000 said:**
> Got two questions.

1.  Who was responsible for determining hardware compatibility before doing the OS install?

2.  Why did the customer have to wait for a new CD from MS rather than the tech slipstreaming the required service pack onto a fresh CD?  Since we're talking about a retail CD it would be reasonable to to expect the tech to already have a CD with the current service pack available.

I'm not hammering on you, I would have asked any one of my people the same questions if they tied up a customer's hardware because they arrived at the customer's workspace unprepared.

Not a customer, a friend that I have known for a long time. And he is the one that researched the mobo and purchased it. But to his defence it was listed on newegg as WinXP-Vista compatible. It just didnt mention that it had to be XP SP2 or higher.. Wasnt no way to slipstream anything, didnt have any other computers around to make a disc and I mainly run Linux on my system 10 miles away and he is on dail-up.. Not downloading anything from his house. The system would hang about 5 secs into booting off the XP disc. Plus this was all done in his home.

---

