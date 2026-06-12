---
title: "My Ubuntu has virus thats blocking virus scanner detector"
date: 2011-05-09
forum: Security
---

### Post by sesquipedalian on 2011-05-09
I open a google image, a pop up came up saying something to the effect of "windows is experiencing a virus and will need to be scanned now" I react by shutting down my computer hoping to cut the virus off, somewhat. Then when I restart my virus scanner programs wont open, so im worried if I don't nip this in the bud it will get worse, anyone know what I can do?

---

### Post by fballem on 2011-05-09
> **sesquipedalian said:**
> I open a google image, a pop up came up saying something to the effect of "windows is experiencing a virus and will need to be scanned now" I react by shutting down my computer hoping to cut the virus off, somewhat. Then when I restart my virus scanner programs wont open, so im worried if I don't nip this in the bud it will get worse, anyone know what I can do?

A very basic question - are you currently running Windows or Ubuntu? The reason that I ask the question is that what I think you encountered is a spoof virus - I've seen it before on both Windows and Ubuntu. In either case, it is a spoof and you should not run the scan.

If you are running Windows, then please do a full system scan using your antivirus software. If you are running ubuntu, then just continue running as before - as of now there are no active viruses in the linux world.

I hope this helps,

---

### Post by techunit on 2011-05-09
> **fballem said:**
> A very basic question - are you currently running Windows or Ubuntu? The reason that I ask the question is that what I think you encountered is a spoof virus - I've seen it before on both Windows and Ubuntu. In either case, it is a spoof and you should not run the scan.

If you are running Windows, then please do a full system scan using your antivirus software. If you are running ubuntu, then just continue running as before - as of now there are no active viruses in the linux world.

I hope this helps,
There is no way he got a virus. It isn't anything to worry about. Like we said there are no active viruses in the linux world. Hey good luck.

---

### Post by sesquipedalian on 2011-05-09
Thanks. I am using ubuntu, the pop up said "Windows had a virus and needed a scan", a friend of mine who had windows, and had the same pop up and she had to clear her hard drive. Since I have Ubuntu though, I am hoping you are right and there are no current active virus's, thanks.

---

### Post by fballem on 2011-05-09
> **sesquipedalian said:**
> Thanks. I am using ubuntu, the pop up said "Windows had a virus and needed a scan", a friend of mine who had windows, and had the same pop up and she had to clear her hard drive. Since I have Ubuntu though, I am hoping you are right and there are no current active virus's, thanks.

Rule 1. If you are running Windows, and you get a notification from someplace _other than your antivirus software_ that you have a virus, then you don't have a virus. The correct action is to close whatever window you are running (usually a website) and immediately do a full system scan using your installed antivirus software. These popup notifications are spoofing software, designed to panic users. They will usually be offered some program, which is itself a virus or a trojan.

Rule 2. If you are running Linux, including Ubuntu or Fedora, there are currently no active viruses. You may safely shutdown the window that is notifying you of the virus and the application (usually your browser). Do not go back to that website.

The primary reason for Rule 1 is that the Windows user is usually an administrator, and many programs need the user to run as the administrator in order to work. Because the user is the administrator, or can be easily made the administrator, they have full access to their machine.

The primary reason for Rule 2 is that the Linux user is not usually running with Administrator privileges, so in the absolute worst case scenario, they may damage their own files, but not much else.

Think of the difference between what you have to do to install a program on Windows (really easy, quick confirmation) and what you have to do to install a program on Linux (notified that you are installing a program and a requirement to enter either a root password (Fedora) or a sudo password (Ubuntu)). That's an oversimplification, but I believe it is accurate based on more that 20 years experience with Windows and more than three years experience with Ubuntu.

Hope this helps,

---

### Post by bodhi.zazen on 2011-05-09
The popup you are concerned about is basically malicious javascript and is best blocked, IMO, with noscript =)

---

### Post by rookcifer on 2011-05-09
> **sesquipedalian said:**
> Thanks. I am using ubuntu, the pop up said "Windows had a virus and needed a scan", a friend of mine who had windows, and had the same pop up and she had to clear her hard drive. Since I have Ubuntu though, I am hoping you are right and there are no current active virus's, thanks.

This is nothing but a script on a webpage trying to social engineer unknowing Windows users into installing some BS trojaned AV package.  What you need to do on a Linux box is simply ignore it and continue about your business.

---

### Post by georgemc on 2011-05-10
When I come across these pop-ups my response is "Oh - really!", some times I hit the scan button just to see what it scans and then LMAO.

They usually scan my "C:" drive and my "C:\WINDOWS\SYSTEM32" files etc. and come up with all these .exe and .dll files that are infected with various trojans and worms.  Yeah right!

In a morbid way kinda amusing.

Then for $29.95 or some thing close I can purchase the cure ..... and so on.

I then switch on "No-script", because I most-likely switched it off earlier and forgot to switch it back on, and then continue web surfing.

Using U10.04, FF4, and "NoScript" plugin, and of course no "wine" on this system.

DO NOT DO THIS on a Windows system, those fake Virus Scanners are a pain to remove.

Enjoy Linux and happy surfing.

George

---

### Post by wilee-nilee on 2011-05-10
> **sesquipedalian said:**
> I open a google image, a pop up came up saying something to the effect of "windows is experiencing a virus and will need to be scanned now" I react by shutting down my computer hoping to cut the virus off, somewhat. Then when I restart my virus scanner programs wont open, so im worried if I don't nip this in the bud it will get worse, anyone know what I can do?

If your running avast you have to do some tweaking or it wont run.

From the Avast forum.

I have Avast in Lucid 10.04, had the same problem, lotsa workarounds out there, but I have found after experimenting with 3 different computers and several versions of Linux, that all you need to do is edit /etc/sysctl.conf by adding this:
kernel.shmmax = 128000000

So you from the terminal run, 
gksudo gedit /etc/sysctl.conf
then add this line 
kernel.shmmax = 128000000

Try bitdefender it is a nice scanner.
[http://www.bitdefender.com/business/antivirus-for-unices.html](http://www.bitdefender.com/business/antivirus-for-unices.html)

As has been suggested a few addons will block the popup av and scripts in general, I would take note of that.

---

### Post by deconstrained on 2011-05-10
> **bodhi.zazen said:**
> The popup you are concerned about is basically malicious javascript and is best blocked, IMO, with noscript =)
Hahaha, exactly what I was thinking. It's a wonder those damn internet pop ups still exist.

---

### Post by cprofitt on 2011-05-10
> **bodhi.zazen said:**
> The popup you are concerned about is basically malicious javascript and is best blocked, IMO, with noscript =)

No-Script for the win. I never even permanently approve a site either... always have to temporarily enable.

---

### Post by demilord on 2011-05-10
I run it with adblock plus :)

---

### Post by Timmer1240 on 2011-05-10
I just cleaned that off a friends vista laptop vista antispyware 2011 it pretty much bogged down the computer and wouldnt let her go to any websites except for their page wanting a credit card number.I was surfing last night looking for some wallpaper and I clicked on the link and that same crap popped up on mine Im running Mint Debian so it bounced right off me its good to run Linux of any flavor!Bad part of it is she lets her kid use the computer and he always ends up with some kind of crapware I think he got scared and installed it thinking it would help then I got a phone call as usual!LINUX POWER FOREVER!

---

### Post by jramshu on 2011-05-10
[COLOR=Red]Have patience with me moderators, I try and limit Windows help. But since it is being labeled an Ubuntu problem I had to reply.[/COLOR]


> **sesquipedalian said:**
> Thanks. I am using ubuntu, the pop up said "Windows had a virus and needed a scan", a friend of mine who had windows, and had the same pop up and she had to clear her hard drive. Since I have Ubuntu though, I am hoping you are right and there are no current active virus's, thanks.


You may be using Ubuntu now, but this is definitely a Windows issue and should be addressed in a Windows Forum.
I have had a few family members have this happen to. This is how I handled the virus/trojan.

This is what I posted on another forum(Had to lay it out simpler for them as you can tell since the aren't computer savy at all) for someone else who recently caught this Windows infection.

I had a couple of family members do the same thing. They where browsing and the page _redirected_,  it showed their "My Computer" page in the browser alerting them they  had viruses in various folders, "Click here to scan and remove". Or  something similar to that.

It's a pretty nasty one I must say. It actually stopped their anti-virus  cold in its tracks. Nothing was accessible, every time they clicked on  anything it gave an alert that what ever they clicked on was infected,  even their av software, and shut down everything they tried to do. They  called me and I checked it out, then I had to laugh (not to be mean  though, I laugh because it is a clever trojan/virus). 

Here is what I did.

1. Got my virus free windows box. (Didn't run Linux at the time)
2. Installed the MalwareBytes installation file to a flash drive. There is another way to do this, but this should  work, if not I have a workaround for it. 
3. Started their computer in "safe mode, without networking."(Most times this works, if  not I have a workaround for this too.)
4. Installed MalwareBytes on their computer, in safe mode, and ran a  deep scan. I think it found a hundred or so viruses and the trojans  themselves. 
5. Restarted the computer, and SHAZAM! I won the fight, no more trojans, viruses, tracking cookies, spyware, etc.

When you try and close a page like that (malicious ones) in a browser a  pop up will appear saying something similar to this, "Are you sure you  wish to navigate away from this page".. and so on. _DON'T click on it either_.  Open task manager and let it "terminate the browser." ctrl+alt+delete  will open task manager or a screen that let's you select task manager.

[www.malwarebytes.org]("http://www.malwarebytes.org")

---

### Post by rookcifer on 2011-05-11
OP. look at my signature.  You have failed to take into account Occam's Razor. ;)

---

### Post by wilee-nilee on 2011-05-11
> **jramshu said:**
> [COLOR=Red]Have patience with me moderators, I try and limit Windows help. But since it is being labeled an Ubuntu problem I had to reply.[/COLOR]

**You may be using Ubuntu now, but this is definitely a Windows issue and should be addressed in a Windows Forum.**
I have had a few family members have this happen to. This is how I handled the virus/trojan.

This is what I posted on another forum(Had to lay it out simpler for them as you can tell since the aren't computer savy at all) for someone else who recently caught this Windows infection.

I had a couple of family members do the same thing. They where browsing and the page _redirected_,  it showed their "My Computer" page in the browser alerting them they  had viruses in various folders, "Click here to scan and remove". Or  something similar to that.

It's a pretty nasty one I must say. It actually stopped their anti-virus  cold in its tracks. Nothing was accessible, every time they clicked on  anything it gave an alert that what ever they clicked on was infected,  even their av software, and shut down everything they tried to do. They  called me and I checked it out, then I had to laugh (not to be mean  though, I laugh because it is a clever trojan/virus). 

Here is what I did.

1. Got my virus free windows box. (Didn't run Linux at the time)
2. Installed the MalwareBytes installation file to a flash drive. There is another way to do this, but this should  work, if not I have a workaround for it. 
3. Started their computer in "safe mode, without networking."(Most times this works, if  not I have a workaround for this too.)
4. Installed MalwareBytes on their computer, in safe mode, and ran a  deep scan. I think it found a hundred or so viruses and the trojans  themselves. 
5. Restarted the computer, and SHAZAM! I won the fight, no more trojans, viruses, tracking cookies, spyware, etc.

When you try and close a page like that (malicious ones) in a browser a  pop up will appear saying something similar to this, "Are you sure you  wish to navigate away from this page".. and so on. _DON'T click on it either_.  Open task manager and let it "terminate the browser." ctrl+alt+delete  will open task manager or a screen that let's you select task manager.

[www.malwarebytes.org]("http://www.malwarebytes.org")

But yet you give a solution for windows to a Linux user.

---

### Post by jramshu on 2011-05-11
> **wilee-nilee said:**
> But yet you give a solution for windows to a Linux user.

The virus he is talking about doesn't effect Linux or Mac. So I figured he was actually using windows at the time. Then to get it installed you have to click on it, shutting down the computer should have stopped it.(EDIT: Maybe the way he "shut the computer down" messed up his Ubuntu) The info will definitely help his friend or friends that do use windows.

If you can find an instance where a windows virus runs on a Linux machine, let me know I'd like to try it. I can't find one instance where it works on anything other than windows, except his post. 

Maybe through wine? Maybe a vb with windows as the host? But I can't seem to find anything on google about it. 

So why take a jab at me for pointing out what seems to be obvious?

---

### Post by Grenage on 2011-05-11
> **jramshu said:**
> The virus he is talking about doesn't effect Linux or Mac. So I figured he was actually using windows at the time. Then to get it installed you have to click on it, shutting down the computer should have stopped it. The info will definitely help his friend or friends that do use windows.

If you can find an instance where a windows virus runs on a Linux machine, let me know I'd like to try it. I can't find one instance where it works on anything other than windows, except his post. 

Maybe through wine? But I can't seem to find anything on google about it. 

So why take a jab at me for pointing out what seems to be obvious?

I believe you may be a bit confused; the OP runs Linux and probably experienced a classic pop-up scam, which told him that he had a virus - they are very common.  The OP took the pop-up at face value and panicked.

There really is nothing much to see or do here. :)

---

### Post by jramshu on 2011-05-11
> **Grenage said:**
> I believe you may be a bit confused; the OP runs Linux and probably experienced a classic pop-up scam, which told him that he had a virus - they are very common.  The OP took the pop-up at face value and panicked.

There really is nothing much to see or do here. :)
He says he runs Ubuntu.
Still I ask, what Windows virus effects Ubuntu?

I'm not confused. If this actually ran on Ubuntu or another Linux machine you would be able to find it. 

EDIT: Removed by poster. 
  
Someone please show something that actually shows this will run on Ubuntu so I can try it.

---

### Post by Grenage on 2011-05-11
> **jramshu said:**
> He says he runs Ubuntu.
Still I ask, what Windows virus effects Ubuntu?

I'm not confused. If this actually ran on Ubuntu or another Linux machine you would be able to find it. 

Someone please show something that actually shows this will run on Ubuntu so I can try it.

There is no Windows virus that runs on Linux; in this case, there isn't even a virus to begin with.

---

### Post by jramshu on 2011-05-11
> **Grenage said:**
> There is no Windows virus that runs on Linux; in this case, there isn't even a virus to begin with.

Thread Title:
> **My Ubuntu has virus thats blocking virus scanner detector**I'm confused!? The title says he has a virus in Ubuntu.

Here is what happens when you try and run this virus in Ubuntu.

[http://www.youtube.com/watch?v=fTRgH1iP460](http://www.youtube.com/watch?v=fTRgH1iP460)

---

### Post by CandidMan on 2011-05-11
It's been said before in this thread, but it's almost certain the OP doesn't have a Windows virus, and they probably don't have a Linux one.

All they've seen is a web page, that's all, a *web page*
I could write up a web page that says the sky is falling but would you believe it?

Shutting down the comp is overkill in this situation, at most kill your web browser and java, then delete the associated cache of files

---

### Post by jramshu on 2011-05-11
> **CandidMan said:**
> It's been said before in this thread, but it's almost certain the OP doesn't have a Windows virus, and they probably don't have a Linux one.

All they've seen is a web page, that's all, a *web page*
I could write up a web page that says the sky is falling but would you believe it?

Shutting down the comp is overkill in this situation, at most kill your web browser and java, then delete the associated cache of files

When someone starts a thread that says "[COLOR=Red]_**My Ubuntu has a virus**_[/COLOR] that blocks virus scanner detector" we are supposed to ignore that part and not believe it?

Jeez 

EDIT: You know what, I give. I'll go back to my confused make believe world where we read the title of a thread and actually believe it.

---

### Post by Grenage on 2011-05-11
> **jramshu said:**
> Now I'm confused. When someone starts a thread that says "[COLOR=Red]_**My Ubuntu has a virus**_[/COLOR] that blocks virus scanner detector" we are supposed to ignore that part and not believe it?

Jeez and I'm the one who is being accused of being confused. LOL!!!!!!!!!!!!!!!

EDIT: You know what, I give. I'll go back to my make believe world where we read the title of a thread and actually believe it.

Most people who come to the support forums are not all-knowing computer wizards; it's generally advised that people read the whole thread, rather than just read the title and jump right in.  That aside, there would have been no way to identify "this virus".

Best just to leave this one be.

---

### Post by jramshu on 2011-05-11
I apologize to all for assuming the OP may have actually been using windows and getting defensive. 

At least he will have the know-how to fix his friends computer next time.

---

### Post by bodhi.zazen on 2011-05-11
> **Grenage said:**
> There is no Windows virus that runs on Linux; in this case, there isn't even a virus to begin with.

Well some windows viruses will run in Wine, so you have to take care if you are running wine.

---

### Post by Grenage on 2011-05-11
> **bodhi.zazen said:**
> Well some windows viruses will run in Wine, so you have to take care if you are running wine.

That's true, although I am not aware of how many.  I imagine that their effect would be negligible, bar interaction with other Windows machines.

It's actually rather tempting to try and infect a Wine install, then see how it interacts with the local Wine, and a networked PC running Windows,

---

### Post by bodhi.zazen on 2011-05-11
> **Grenage said:**
> That's true, although I am not aware of how many.  I imagine that their effect would be negligible, bar interaction with other Windows machines.

It's actually rather tempting to try and infect a Wine install, then see how it interacts with the local Wine, and a networked PC running Windows,

By default, linux permission prevent havoc outside of $HOME.

But the problem with wine is that, bu default, there is a link in ~/.wine/dosdevices to /

So if you run wine as root then yes system files can be affected.

I made some notes in the security sticky about wine and if you google search there are some reviews of how good (or bad) some select viruses run under wine.

Personally I disable all links outside of ~/.wine (although I do not really run wine these days).

---

### Post by Grenage on 2011-05-11
A good enough reason not to run wine as root indeed, although I do wonder how a windows virus would react to that path.  I'm going to try some out on a laptop and see what occurs.  I'll also have a look for your sticky.

Cheers!

---

