---
title: ":popcorn: how will i know if someone is hacking me?"
date: 2007-10-25
forum: Windows
---

### Post by sayuki288 on 2007-10-25
i think im being haxed

---

### Post by sayuki288 on 2007-10-26
how will i know if some ******* is hacking me?

---

### Post by jusmurph on 2007-10-26
Perhaps it would be easier if you told us what makes you think your being hacked.

---

### Post by sayuki288 on 2007-10-26
oh ok.... 

i think im being hacked because my computer always stopping randomly

and im getting pissed off about it

---

### Post by Ice_Dragon on 2007-10-26
You're not being very specific.  Stopping how?  Blue screens?  Freezing up completely?  Just hanging at random times?   Please elaborate.

---

### Post by sayuki288 on 2007-10-26
it freezes up while im using it can't click anything and when i do it hangs completely and i need to restart my damn pc

---

### Post by Nythain on 2007-10-26
sounds about like microsoft windows :)

---

### Post by taurus on 2007-10-26
How about the spec of your machine (CPU, RAM, video card, etc.)?

---

### Post by sayuki288 on 2007-10-26
AMD 64 athlonX2 
m2n-sli deluxe
1024 mb ram
7600GS geforce

---

### Post by spookyone on 2007-10-26
Is Windows running?  Because this is an Ubuntu forum, I assume you are running Ubuntu.  If Windows is not running, whatever a ******* is can't "hack" Windows.  When you boot into Windows, it can be "hacked." I suspect, as a Linux newbie but something of a Windows hacker, that you mean cracker or script kiddy.  Hacking involves making systems do what you want and need, rather than what the original author wanted or needed.  In this sense, all GNU users are hackers, as the spirit of open source is that the code is open so you can do what you want with it.  People who break into systems--white or black hat--are crackers (or script kiddies if they do it with code they've "aquired" rather than written themselves).  Please don't insult hackers by implying we necessarily break into systems.

As to your question--unless Windows is running it can't be cracked.  Of this I can be sure.  Although I'm sure I'll be outcast on this, my first full day on the forum, for saying this, but your Linux system can be cracked, although this is unlikely.  Still, the first crackers were unix users, and 'nix systems are not immune.  From what I read before coming here to check out Ubuntu for my first installed Linux distro (I've used live CD's), Ubuntu (and OSX, which is a version of BSD) are fairly unique in their use of sudo, which appears to be more secure than using su, as you don't use root so there's a log of changes.  You could see in the log if a cracker had made changes to your system.  Please, someone who has used Ubuntu a while tell me if I have understood the difference between su and sudo correctly.

---

### Post by sayuki288 on 2007-10-26
im not running windows now im using ubuntu because my windows' whacked up

---

### Post by BrendanM on 2007-10-26
> **spookyone said:**
> Is Windows running?  Because this is an Ubuntu forum, I assume you are running Ubuntu.  If Windows is not running, whatever a ******* is can't "hack" Windows.  When you boot into Windows, it can be "hacked." I suspect, as a Linux newbie but something of a Windows hacker, that you mean cracker or script kiddy.  Hacking involves making systems do what you want and need, rather than what the original author wanted or needed.  In this sense, all GNU users are hackers, as the spirit of open source is that the code is open so you can do what you want with it.  People who break into systems--white or black hat--are crackers (or script kiddies if they do it with code they've "aquired" rather than written themselves).  Please don't insult hackers by implying we necessarily break into systems.


*Sigh* I'm really sick of hearing people talk about "crackers" as opposed to "hackers". You can't forcibly redefine a word, no matter how many times you post on a forum about it. In general English usage, "hacking" refers to subverting the original intent of a system, sometimes for good, sometimes for ill. If you want to be more specific, black-hat or white-hat will do nicely. Besides, "cracker" sounds stupid.

As to the OP's question, it's quite hard to tell from the information you've posted what's going on with your Windows partition. You might try running ClamAV from within Ubuntu and using it to scan your Windows partition for viruses. You'll probably need to enable NTFS write-support so ClamAV can clean anything it finds. IIRC, there's also a version of AVG (free as in beer) that will run from Linux. Good luck.

---

### Post by spookyone on 2007-10-26
> **sayuki288 said:**
> im not running windows now im using ubuntu because my windows' whacked up

I hate to sound like previous posters, but what do you mean by "whacked up?"

Windows being corrupt in any way shouldn't affect your Ubuntu install, especially if you installed Ubuntu AFTER Windows "whacked up."  Perhaps you should back up your data and reinstall BOTH  XP AND Ubuntu.  If both Windows and Ubuntu don't boot, maybe Puppy or DSL will work for you to get data backed up as they both run entirely in RAM?

---

### Post by sayuki288 on 2007-10-26
> **BrendanM said:**
> *Sigh* I'm really sick of hearing people talk about "crackers" as opposed to "hackers". You can't forcibly redefine a word, no matter how many times you post on a forum about it. In general English usage, "hacking" refers to subverting the original intent of a system, sometimes for good, sometimes for ill. If you want to be more specific, black-hat or white-hat will do nicely. Besides, "cracker" sounds stupid.

As to the OP's question, it's quite hard to tell from the information you've posted what's going on with your Windows partition. You might try running ClamAV from within Ubuntu and using it to scan your Windows partition for viruses. You'll probably need to enable NTFS write-support so ClamAV can clean anything it finds. IIRC, there's also a version of AVG (free as in beer) that will run from Linux. Good luck.

just one question man does it have to do with svchost beacuse im blocking some svchost in my firewall

---

### Post by Gone fishing on 2007-10-26
If you are running Ubuntu it's unlikely that you have a virus or been hacked - your problem is more likely to be hardware;

Is you processor overheating - heat sink full of dust? fan working properly?
video card overheating?
RAM problems? try some new ram from another PC and checking its in its slot.
Are the SATA controllers properly clicked into the hard drives?

---

### Post by spookyone on 2007-10-26
> **sayuki288 said:**
> just one question man does it have to do with svchost beacuse im blocking some svchost in my firewall

Simple answer.  No. svchost.exe is simply what Windows calls many different system processes that are basically running anonymously in the background.  If you call up the Windows task manager you will generally see several instances of svchost.exe running at any given time.  Stopping any one instance is a crapshoot because you can't know which program is running it.  Your firewall shouldn't be involved at all, but if you are stopping any instance of svchost.exe that could cause Windows to "whack up."  What it did would depend on what service it is, and you can't tell.  Most likely you need a clean install of Windows.

---

### Post by BrendanM on 2007-10-26
I think SVCHost is a normal windows process, but I've also heard of some viruses disguising themselves as SVCHost. Do you have more than one instance of SVCHost in your task manager?

Also, not to be a jerk, but this isn't a windows tech support forum. People here are generally nice and will try to help you out, but if you have windows-specific questions you're much better off posting on a windows forum.

Edit: Apparently having multiple instances of svchost isn't a bad thing. Nevertheless, there are viruses that masquerade as svchost.

---

### Post by CaptainInsaneO on 2007-10-26
Try unblocking that entry.

svchost is a process name for any DLL that's running in Windows (in other words, you need those).

---

### Post by spookyone on 2007-10-26
> **BrendanM said:**
> *Sigh* I'm really sick of hearing people talk about "crackers" as opposed to "hackers". You can't forcibly redefine a word, no matter how many times you post on a forum about it. In general English usage, "hacking" refers to subverting the original intent of a system, sometimes for good, sometimes for ill. If you want to be more specific, black-hat or white-hat will do nicely. Besides, "cracker" sounds stupid.

As to the OP's question, it's quite hard to tell from the information you've posted what's going on with your Windows partition. You might try running ClamAV from within Ubuntu and using it to scan your Windows partition for viruses. You'll probably need to enable NTFS write-support so ClamAV can clean anything it finds. IIRC, there's also a version of AVG (free as in beer) that will run from Linux. Good luck.

*Sigh* Hacker, in the computer sense, originally meant someone who was especially good at programming, and was already forcibly redefined by those who don't trust those who can write code.  Hacker, as computer jargon, predates systems that could be conceivably be broken into.  Call those who break in crackers or not, but I was a hacker before the word meant "to subvert the original intent of the system,"  and I have never forcibly entered any system that I did not have the expressed permission of the system owner to enter.  But I was writing code in four languages before realtime and GUI's were conceived.  Words are redefined all the time.  Unless gay still means just means happy?

---

### Post by Maestro23 on 2007-10-26
> **BrendanM said:**
> I think SVCHost is a normal windows process, but I've also heard of some viruses disguising themselves as SVCHost. Do you have more than one instance of SVCHost in your task manager?

Also, not to be a jerk, but this isn't a windows tech support forum. People here are generally nice and will try to help you out, but if you have windows-specific questions you're much better off posting on a windows forum.

Edit: Apparently having multiple instances of svchost isn't a bad thing. Nevertheless, there are viruses that masquerade as svchost.

SVChost: [http://support.microsoft.com/kb/314056](http://support.microsoft.com/kb/314056)

---

### Post by kulturloseramerikaner on 2007-10-26
Anything specifically going on that's got you thinking that?

---

### Post by Crafty Kisses on 2007-10-26
> **sayuki288 said:**
> oh ok.... 

i think im being hacked because my computer always stopping randomly

and im getting pissed off about it

The only way you can really be hacked and the hacker has control of your computer is if you have a back-door on your computer, if your scared, just reformat your computer, and be done with it.

---

### Post by afeasfaerw23231233 on 2007-10-26
it may be a hardware problem. it happened to my old pIII box. it freezed randomly. i checked inside the box and found out 2 capacitors on the motherboard and 1 in the psu were ''poped''. i looked for the components and replaced them . it works fine until now. hope this help

---

### Post by dca on 2007-10-26
Run the 'memtest' just to be sure memory is not to blame.  You know, there's like twenty thing OS related that can freeze Windows.  Pagefile set too low, etc, etc...   What does the 'event-viewer' under Settings -> Control Panel -> Administrative Tools -> Event Viewer say?  Check and see if Windows references a particular piece of software under Applications (app hangup) or if a piece of hardware is out of it under System....

---

### Post by happysmileman on 2007-10-26
> **spookyone said:**
> *Sigh* Hacker, in the computer sense, originally meant someone who was especially good at programming, and was already forcibly redefined by those who don't trust those who can write code.  Hacker, as computer jargon, predates systems that could be conceivably be broken into.  Call those who break in crackers or not, but I was a hacker before the word meant "to subvert the original intent of the system,"  and I have never forcibly entered any system that I did not have the expressed permission of the system owner to enter.  But I was writing code in four languages before realtime and GUI's were conceived.  Words are redefined all the time.  Unless gay still means just means happy?

Yes, but it's quite clear that the OP would rather have help identifying a problem than a speech on grammar

---

### Post by Depressed Man on 2007-10-26
Usuallly the fake SVChost is called SCVhost. You can also spot it by where it's running from (usually not SYSTEM).

---

### Post by spookyone on 2007-10-28
> **Depressed Man said:**
> Usuallly the fake SVChost is called SCVhost. You can also spot it by where it's running from (usually not SYSTEM).

It is true that many SVChost imposters are are misspelled to appear that they belong, so look closely to that. But it often happens that processes are called by user accounts rather than SYSTEM so just stopping processes because they are running under a user account can and often does cause system instability.  I still think you need a format and a clean install of both Windows and Ubuntu.

---

### Post by spookyone on 2007-10-28
> **happysmileman said:**
> Yes, but it's quite clear that the OP would rather have help identifying a problem than a speech on grammar

I did offer assistance.  I also took an opportunity to point out that I, as well as many hackers in my generation, are insulted by the term we applied to ourselves before many of you were born now being used to imply that we break into systems.  Just as I am hurt by the word gay, which once meant happy or joyful and later was "forcibly redefined"
to mean homosexually oriented--a meaning I applied to myself at about the same time I adopted the word "Hacker", again being redefined to mean "lame, or stupid."

---

### Post by Alterax on 2007-10-28
Actually, I think it's quite abnormal that WinFirewall detects a svchost.exe trying to get out of the network.  Usually, if it's stock system DLLs, Windows already has a good idea of what needs in and what needs out.

Here's what to do:
Try running a spyware scan and a virus scan/removal from Windows while in safe mode.  Failing that, you may be able to scan your system from ubuntu, provided that you have the NTFS write support enabled; you can use ClamAV or similar to handle this.  (Check the repositories).

Another poster mentioned the capacitors.  By all means, check your motherboard for anything that looks strange.  Capacitors are small cylinders, if they are swollen or have "popped", take it to an electronics shop and have them replaced.  But since the problem isn't occuring in Linux, just Windows, I'm willing to rule out "hardware problem".

That should get you up and going.  If you have any trouble with getting into safe mode, running a virus scan, et cetera, by all means take your computer to the computer shop across town.  It'll save you a lot of headaches.

Now as for if you are being hacked....That's just old school.  Hackers have no interest of breaking into your computer system, one by one.  They (that would be the malicious hackersl, for those that require a difference) are a lot more likely to write worms/viruses, find exploits, and set up things like botnets to infect and control large amounts of PCs at once.  Then they sell all of that raw processing power off to the highest bidder.  That processing power can be used to crack passwords, for example.  Or have you ever received spam?  The vast majority of spam doesn't come from big mail servers.  It comes from hundreds of thousands of compromised/infected PCs.  Like yours.

One PC just isn't worth the time and effort.  So while I doubt someone across the world is hacking into your computer to look at your pictures, I have a lot less doubt that your Windows system has been infected.  Which is why I chose Ubuntu; it's a lot less vulnerable to this kind of trouble.

---

### Post by inversekinetix on 2007-10-29
reinstall, config windows properly (if you dont know how to look it up), install only the drivers you need, install the apps you need,  ghost it and be done.

---

### Post by sayuki288 on 2007-10-30
think i should mark the thread solved :lolflag:

already solved the problem CPU just need a fresh pair of arctic silver cause i never noticed it burning so it's telling me by whacking up my OS

---

### Post by iamsobored0056 on 2007-10-30
> **sayuki288 said:**
> think i should mark the thread solved :lolflag:

already solved the problem CPU just need a fresh pair of arctic silver cause i never noticed it burning so it's telling me by whacking up my OS

hm, well if you didn't find out that it was a hardware problem, you could have just disconnected your computer from the internet and see if it would still crash and shutdown.  if it still crashes and shutdowns, its a hardware or a virus problem, if it doesn't, then its a "hacking," hardware, or network driver problem

---

### Post by sayuki288 on 2007-10-30
just found out that its not a damn hardware problem i think its a virus dang it froze again

---

### Post by sayuki288 on 2007-10-30
just changed my antivirus and found lots of stupid critters hidding in my folders

---

### Post by RuB3N on 2007-11-01
Ubuntu Is The Best Operating System Anyways, Get Rid Of Windows! Windows Is Slow And Anyonging. Especialy Vista. Vista Can Go Burn In Hell. rephrase, Windows can go to hell.

---

### Post by bluesrocker on 2008-02-20
Do you have a firewall? Have you tried using Firestarter? Firestarter will let you know if attacks are being made and on what port the attack took place. it will provide you the IP addresses, the time, and if the port attacked. Pretty Cool. Give it a shot.

---

### Post by Kingsley on 2008-02-20
He's on Windows, so I don't think Firestarter will do much good. I suggest ZoneAlarm.

---

