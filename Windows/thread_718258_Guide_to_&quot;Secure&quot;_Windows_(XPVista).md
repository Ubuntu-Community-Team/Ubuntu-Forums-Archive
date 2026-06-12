---
title: "Guide to &quot;Secure&quot; Windows (XP/Vista)"
date: 2008-03-07
forum: Windows
---

### Post by ShinHadoken on 2008-03-07
[CENTER][COLOR=black][U][SIZE=6]How To "Secure" Windows

[/SIZE][/U][/COLOR][LEFT][COLOR=black]Okay, now everyone knows that, in the end, this Winblows operating system is never going to be secure. But, I think this guide comes a close as it gets without spending a lot of money on security software. So, let's get started!

[U][B]I. Web Browser - Firefox

[/B][/U]Probably about 87% of hacking/virus/spyware incidents are related to the web browser. That stresses the importance of having a secure browser. [Firefox]("http://www.firefox.com/") is that browser. Not only is it natively more secure than Internet Explorer, it has many security addons that make it even safer. Here's my list:

[/COLOR][LIST]
[*][COLOR=black][Adblock Plus]("https://addons.mozilla.org/en-US/firefox/addon/1865") - THE BEST adblocker out there! Unbelievable how great this works! And if an ad gets through your filter, all you have to do is right-click it and block it! Go to [adblock.jonasjohn.de]("http://ubuntuforums.org/adblock.jonasjohn.de") and make your own custom filterset (This tool isn't any good if you don't make a filterset for it).[/COLOR]
[*][COLOR=black][CustomizeGoogle]("https://addons.mozilla.org/en-US/firefox/addon/743") - Allows you to customize Google preferences like SafeSearch, remove google ads, and disable harmful Google-Analytics software.[/COLOR]
[*][COLOR=black][Fasterfox]("https://addons.mozilla.org/en-US/firefox/addon/1269") - Not a security addon, but provides a few performance tweaks for Firefox to make it run a little faster.[/COLOR]
[*][COLOR=black][Firekeeper]("http://firekeeper.mozdev.com/") - A browser-based intrusion detection tool. 
[/COLOR]
[*][COLOR=black][NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722") - Winner of the "2006 PC World World Class Award", this is a must have for Firefox users. Disables harmful scripts from running in the back of webpages. Allows whitelisting of good scripts (NoScript will block almost all scripts by default).[/COLOR]
[*][COLOR=black][WOT]("https://addons.mozilla.org/en-US/firefox/addon/3456") - A very handy addon that warns you about unsafe sites. Allows you to rate websites based on your own experience.[/COLOR][/LIST][COLOR=black]As you can see, with all these options, Firefox is the best browser around, especially when it comes to addons.[/COLOR][COLOR=black]

[B][U]II. Antivirus - AVG Free

[/U][/B]When you're using freeware, it really doesn't matter what AV you use, as long as you have one. I prefer AVG Free. You can get it from [free.grisoft.com]("http://free.grisoft.com/"). This AV suite for Windows has all the expected features: antivirus scanner, virus vault, scheduler, auto-updates, email scanner, the works. It's pretty straight-forward installing, so I'm not going to explain it.

[U][B]III. Anti-Spyware - Spybot S & D

[/B][/U]For antispyware, Microsoft's Windows Defender doesn't cut it. So, I did a LOT of homework, and I found SpyBot - Search and Destroy was the best for me. You can get it at [www.spybot.com]("http://www.spybot.com/")[/COLOR][COLOR=black]. It has auto-updates, spyware scanner, secure file shredder, and a resident application that is constantly protecting you. It also alerts you about any unauthorized registry changes.

[U][B]IV. Anti-Rootkit - AVG Anti-Rootkit Free

[/B][/U]Rootkits aren't a real problem in Windows, but just in case, you can get AVG's free rootkit tool [here]("http://free.grisoft.com/doc/download-free-anti-rootkit/us/frt/0"). It doesn't have anything automatic, just the rootkit scanner, but I would only run it on a Windows box every 6 months at the most. 

[B][U]V. Email - Thunderbird

[/U][/B]Email security should not be a problem for you, whatever OS you use. You only get viruses and stuff through email when you fall victim to social engineering. In other words, be careful where you put your email address. If you absolutely have to disclose your email address to a sketchy site, use a junk account. But, if you're OCD and you have to have a secure email client, use Thunderbird from [Mozilla]("http://www.mozilla.org/"). With that and AVG's email scanner, you should be ok.

[B][U]VI. Firewall - COMODO Firewall Pro

[/U][/B]Let's face it - the Windows "Firewall" SUCKS!!! At the time of writing, [COMODO's firewall]("http://www.personalfirewall.comodo.com/download_firewall.html") seems to be the most popular. I use it on my Windows boxes, and I love it. When you install it, right click on the icon in the taskbar and change the Firewall Security Level to "Training Mode". Then, open up your IM app, email client, web browser, and access any other pc's on your network. Basically, run any app that connects to the network or the internet. This will automatically create rules to allow those applications. When you're done, change the security level back to "Train with Safe Mode" to enforce the firewall. If you have any difficulty getting any other applications to connect, just change to Training Mode, run the app, and then switch back. Also, change the Defense+ Security Level to "Disabled". When active, Defense+ conflicts with Spybot, and Windows won't recognize Defense+ as a Anti-Spyware
app anyway.

[B][U]VII. User Accounts

[/U][/B]I also forgot, as [Jimmey]("http://ubuntuforums.org/member.php?u=47331") reminded me, to talk about user accounts. I usually don't have to worry about this because Ubuntu has the root account disabled by default, and you can specify which accounts can use sudo. But in Windows, most people use the admin account all the time without knowing it. This is very dangerous. Do yourself a big favor and set up a regular account without admin privilages. If you need to install some software or something, then you can switch to the admin user, but never use it all the time. Thank [Jimmey]("http://ubuntuforums.org/member.php?u=47331")!

[U][B]VIII. Conclusion

[/B][/U]Well, I hope you have enjoyed this guide! Don't forget, all these measures are no substitute for a Linux box, just a way to secure those Windows boxes that you may be dual-booting or something.
[/COLOR][/LEFT]
[/CENTER]

---

### Post by steveneddy on 2008-03-07
Won't help.

---

### Post by Glaxed on 2008-03-07
I personally have almost nothing protecting my windows, and everything runs just fine (surprised? you should be, im 14 XD).
I do use a2 to make sure everything is spiffy. It's very simple.
[batch file]
"C:\a2\a2cmd.exe" /f="C:\" /h /m /t /c /r /a /n /d"
"C:\a2\a2service.exe"
[/batch file]
Output;
C:\#>a2cmd.exe /f="C:\" /h /m /t /c /r
/a /n /d

a-squared Command Line Scanner v. 3.0.0.126
(C) 2003-2007 Emsi Software GmbH - [www.emsisoft.com](www.emsisoft.com)

a-squared Command Line Scanner - Version 3.0
Last update: N/A

Scan settings:

Objects:           Memory, Traces, Cookies, C:\
Scan archives:     On
Heuristics:        On
ADS Scan:          On

Scan start:        3/7/2008 11:36:00 PM

[2020] C:\WINDOWS\system32\CLBCATQ.DLL

I've tried NOD32, Avast, COMODO, ZoneAlarm, Spybot, AdAware, Spyware terminator, and a LOT of other crap. It's all just crap.
All I need is BOClean and a2 and I feel very safe.
A2 is particularly a very complete and effective product compared to pricy ones. And the CLI version is essentially the pro version, without the GUI (which is fine, cuz its faster this way). And its free :D.

Then again, I'm no security expert.

---

### Post by NightwishFan on 2008-03-08
There is no such thing as a "secure windows". Even if you block out everything else. Microsoft is still watching.

---

### Post by Jimmey on 2008-03-08
I think you forgot the most important thing!

You can set up non-admin accounts on Windows, and a single administrative account for things like installing software, etc.

Some applications won't work without administrative privileges, but for those applications you can use the "Run as user.." dialog. This is far safer than running the entire session as an admin.

---

### Post by ShinHadoken on 2008-03-08
[COLOR=black]> **NightwishFan said:**
> There is no such thing as a "secure windows". Even if you block out everything else. Microsoft is still watching.
_____________________

First two sentences in my guide:

> **ShinHadoken said:**
> [/COLOR]  [COLOR=black]Okay, now everyone knows that, in the end, this Winblows operating system is never going to be secure. But, I think this guide comes a close as it gets without spending a lot of money on security software.[/COLOR]

---

### Post by LaRoza on 2008-03-08
I would just recommend using Comodo Firewall to do all protection. It has some very neat features, that make other software not needed.

Plus, it won't slow things down much.

(And I recommend Opera as the browser)

---

### Post by Kernel Sanders on 2008-03-08
Firefox is not necessarily more secure on Vista. Remember that IE7 on vista is sandboxed.

---

### Post by zetetic on 2008-03-08
This is ridiculous. It's impossible to secure windoze.

Just use Linux and save your and our time.

---

### Post by LaRoza on 2008-03-08
> **zetetic said:**
> This is ridiculous. It's impossible to secure windoze.

Just use Linux and save your and our time.

It isn't ridiculous, Windows needs help, sure, but brains and some helpful software go along way.

---

### Post by andrewjoy on 2008-03-09
If you are willing to pay for it or have acess to it form a work / university licence i would go for sophos antivirus. It is expensive £133 for 5 users but if you have a small busness that runs windows it is worth it imo best av i have used for windows does not slow the system down and nothing has got past it when i have been using it. It also supports mac osx.

Stay away form norton at all costs and the nvidia firewall.

A good hardware firewall in your router also helps alot.

---

### Post by chewearn on 2008-03-09
1. Turn on auto-update; you pay for Microsoft OS, make sure you get the full bang-for-buck from Microsoft.

2. Scan your internet ports using ShieldsUp at grc.com to make sure you are do not have open ports that can be attacked.

3. Turn off CD-ROM autorun.  Before loading any Audio CD or DVD-Video into the drive, make sure it's not loaded with DRM rootkit.

---

### Post by LittleLORDevil on 2008-03-09
I have been looking for a good firewall and I think I may have found it.  Thanks!

---

### Post by seshomaru samma on 2008-03-12
I think [this i]("http://forums.windowsforum.org/index.php?showtopic=33716")s the definative guide to securing Windows
the guy cliams he makes it as secure as Linux and he uses the  CIS TOOLs results to prove it

---

### Post by Calash on 2008-03-12
> Adblock Plus - THE BEST adblocker out there! Unbelievable how great this works! And if an ad gets through your filter, all you have to do is right-click it and block it! Go to adblock.jonasjohn.de and make your own custom filterset (This tool isn't any good if you don't make a filterset for it). 

Not sure my feelings on this one, as it ends up being a bit of a hot topic if you get too deep into it.  The problem is not ads, but scripts that execute in what look to be ads.  Standard ads are just that, advertisements tailored to your viewing experience.  Some have cookies attached, some look-up from your IP.

Many malicious scripts and spyware do act as ads, so I can see taking the broad approach and blocking them all...don't like it very much but I can see the reason.

> 
CustomizeGoogle - Allows you to customize Google preferences like SafeSearch, remove google ads, and **disable harmful Google-Analytics software.** 

This one I have to ask for more info.  Harmful?  Analytics is a website statistic program that uses a Google Javascript app to record info on your sites visitors.  How is this any more harmful than the logs that Apache makes?  How is it harmful at all?

The benefit of a firewall is a bit over-hyped if you ask me.  Any firewall software on your computer is only as strong as the operating system it's self.  If a hacker can exploit XP, they can bypass the firewall.  It is better than nothing, but it is not a cure-all for securing your computer.

---

### Post by NightwishFan on 2008-03-12
My approach to security is the classic ninja, You cannot catch what you can't see.

---

### Post by r76 on 2008-03-12
> **Calash said:**
> This one I have to ask for more info.  Harmful?  Analytics is a website statistic program that uses a Google Javascript app to record info on your sites visitors.  How is this any more harmful than the logs that Apache makes?  How is it harmful at all?

I agree.  Blanket ad-blocking doesn't do the sites you're visiting any help.  Funding from advertising helps with server costs and is thus important to some of us.  If you like the site I think you should accept the ads that come with it otherwise you are leeching content in whatever form without contributing anything.  If you don't like the ads you are free (as in freedom) to not visit the site.

But on the whole this is a useful guide to securing Windows, despite some negative comments in this thread - if more people acted this way then viruses and malware wouldn't spread so fast, enabling the timely deployment of software security updates.  The setup described will give you a setup quite adequate for safe everyday use, as long as you don't have risky internet behaviour or run software of dubious origin.  As has been said before, some hardware routers offer great protection as well as reducing the CPU overhead associated with software-based solutions.

As pointed out before, Opera is also a good alternative browser (and very easy to block Flash, javascript, etc if you're into that sort of thing).

---

### Post by Calash on 2008-03-12
Ad blocking is it's own discussion...probably one that has happened here a couple of times....and probably in the backyard :)

I do agree with the majority of the guide as well.  Just a few sticking point with me.  Also, IE7 so far seem very secure, especially in Vista.  Still needs time to really find the exploits, but nothing huge that I have seen yet.

---

### Post by karellen on 2008-03-13
> **zetetic said:**
> This is ridiculous. It's impossible to secure windoze.

Just use Linux and save your and our time.

the OP was for people who use Windows and need some advice regarding this. the recommandations seemed useful

---

### Post by Glaxed on 2008-03-15
> **LaRoza said:**
> I would just recommend using Comodo Firewall to do all protection. It has some very neat features, that make other software not needed.

Plus, it won't slow things down much.

(And I recommend Opera as the browser)
I like COMODO v3 very much. Only issue is that it caused my computer to take 9 minutes to log in, every time I powerd up. After a month of the abuse, I switched to sp2 firewall.

---

### Post by NightwishFan on 2008-03-15
Completly disconnect the windows based pc from the internet and search for the hidden wireless chip that transmits all the data to micro soft.

---

### Post by sverdlov on 2008-09-25
I would like to mention a video guide site where you could see some video and non-video tutorials on securing Windows XP - and yes - there is "secure Windows", you just need time setting it up. 
check it out - [www.securityguy.org]("http://www.securityguy.org") - this blog is THE blog, guys!

---

### Post by lukjad on 2008-09-25
This may have been said, but have you heard of SuRun?

---

### Post by aysiu on 2008-09-25
> **lukjad007 said:**
> This may have been said, but have you heard of SuRun?
SuRun is the best way I've seen to secure XP.

---

### Post by Louis de Broglie on 2008-09-26
I would also recommend visiting this site :

> 
[http://www.grc.com/lt/leaktest.htm](http://www.grc.com/lt/leaktest.htm)


---

