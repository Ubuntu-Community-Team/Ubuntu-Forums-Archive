---
title: "security concern"
date: 2011-05-01
forum: Security
---

### Post by killerloop8 on 2011-05-01
hi everyone,

I'm bit confused whether to use my ubuntu machine to access my bank accounts and other personal information coz lately ubuntu has become very popular and malware might already be on. I don't find any promising security software just to be on safer side and to have piece of mind.

Please share your thoughts or suggestions.

thanks

---

### Post by rookcifer on 2011-05-01
> **killerloop8 said:**
> hi everyone,

I'm bit confused whether to use my ubuntu machine to access my bank accounts and other personal information coz lately ubuntu has become very popular and malware might already be on. I don't find any promising security software just to be on safer side and to have piece of mind.

Please share your thoughts or suggestions.

thanks

You don't need "security software."  That's a windows thing.  More important is just to use common sense -- make sure when you login to your bank's website that you use HTTPS.  I highly recommend the FF add-on "certificate patrol."

If you want to enhance browser security look into add-ons like Noscript.  You can also enable the AppArmor profile.

---

### Post by EGamerHDK on 2011-05-02
> **killerloop8 said:**
> hi everyone,

I'm bit confused whether to use my ubuntu machine to access my bank accounts and other personal information coz lately ubuntu has become very popular and malware might already be on. I don't find any promising security software just to be on safer side and to have piece of mind.

Please share your thoughts or suggestions.

thanks

Yes, if you are primarily concerned about on line accounts (especially the important ones like banking), my first tip is just to be on a secured home network. WPA2-AES. Don't attempt to log on to anything valuable in the public. All banks I know of use "SSL" which basically changes http:// to [https://.](https://.) What this means is that everything going on is encrypted in that session. A couple of sites that do have https:

amazon.com
ebay.com
sovereignbank.com

Most websites with transactions really do have SSL but just make sure.

Sites like facebook.com do not have SSL (enabled by default. Which is weird but, that's facebook)

In a nutshell, make sure you're on a secure network.

Don't download anything stupid.

And you'll be good. Hope I helped. Have a good one.

P.S. Some people don't know why all websites don't use SSL (even ubuntuforums.com doesn't use SSL) but, it does cost money and apparently it's a little slower since everything has to be encrypted.

---

### Post by blind2314 on 2011-05-02
> **rookcifer said:**
> You don't need "security software." That's a windows thing. More important is just to use common sense -- make sure when you login to your bank's website that you use HTTPS. I highly recommend the FF add-on "certificate patrol."
 
If you want to enhance browser security look into add-ons like Noscript. You can also enable the AppArmor profile.
 
 
That's a fallacy that is thrown around far too often when Linux/Unix security is discussed. It's not simply a "windows thing"; there is malware and there are security vulnerabilities, and in most cases, they can wreak just as much if not more havoc than their Windows counterparts. I'm a sys-admin by profession, primarily Solaris and HP-UX, and I can vouch first-hand for just how many vulnerabilities are out there.
 
As stated above me, be careful about where you browse the internet (i.e., do NOT check personal information while you're sipping a latte at Starbucks) and don't visit suspicious sites unless you're in a sandbox environment or know what you're doing. Also ensure that your passwords for your computer and more importantly, your bank account, are strong. There are plenty of links on Google on how to choose a "strong" password, so I won't go into that here unless requested.

---

### Post by bodhi.zazen on 2011-05-02
> **killerloop8 said:**
> hi everyone,

I'm bit confused whether to use my ubuntu machine to access my bank accounts and other personal information coz lately ubuntu has become very popular and malware might already be on. I don't find any promising security software just to be on safer side and to have piece of mind.

Please share your thoughts or suggestions.

thanks

First, you should read the security sticky.

Second, there are layers of security and online commerce involves your box (client), internet protocols (networking), and the server you connect to.

So you can learn to secure your Ubuntu box. 

And you also need to learn to secure your browser. Use hhtps and NoScript.

Not much you can do about the server you connect to.

With all that said, probably the biggest threat is still Phishing or social engineering and no amount of "Security software" will help with that, you need to educate yourself re : https .

---

### Post by rookcifer on 2011-05-02
> **blind2314 said:**
> That's a fallacy that is thrown around far too often when Linux/Unix security is discussed. It's not simply a "windows thing"; there is malware and there are security vulnerabilities

A vulnerability != malware.  I have never, in my years of scouring Linux/Unix security forums, ever seen a single piece of serious Linux malware in the wild.  The one exception might be the malicious Ubuntu screensaver that somehow got on gnome-look.org a couple of years back.  However, it was short lived and removed in a couple of days. Only a few people were affected and it never "spread" beyond those unfortunate and (careless) people's machines.  Linux and Unix malware is extremely rare, to the point of almost being unheard of.  And this has very little to do with market share.

AV software on Windows has a very questionable success rate (and a high false positive rate to boot).  It's a marketing scam and a money making scheme which is why I don't see much benefit in using it.  I don't even use it on my Windows boxes (and I take security seriously).

A better way to stop the rare piece of malicious code is not to install it.  This means sticking with the official repos if at all possible and updating the machine when prompted.  It's really that simple.  Nothing is 100%, but in life there is always risk analysis and trade-offs.  When you move to California, you are at a higher risk of getting killed in an earthquake, yet the risk is small enough that few people consider it.  When you get pulled over by the police for speeding, there is always the risk that the cop is a serial killer out to get you, but the risk is small enough that most of us don't refuse to pull over out of that fear.  I would say the risk of getting "malware" on an updated Linux box where the admin takes care in installing only trusted software is equally as slim.  Am I saying it's utterly impossible?  No.  I am saying the risk is small enough to be negligible if basic steps are taken.  I am also saying "security software" will do very little good and there's no reason to start insisting that Linux become Windows with its plethora of expensive "security suites."

---

### Post by blind2314 on 2011-05-02
> **rookcifer said:**
> A vulnerability != malware.  I have never, in my years of scouring Linux/Unix security forums, ever seen a single piece of serious Linux malware in the wild.  The one exception might be the malicious Ubuntu screensaver that somehow got on gnome-look.org a couple of years back.  However, it was short lived and removed in a couple of days. Only a few people were affected and it never "spread" beyond those unfortunate and (careless) people's machines.  Linux and Unix malware is extremely rare, to the point of almost being unheard of.  And this has very little to do with market share.

AV software on Windows has a very questionable success rate (and a high false positive rate to boot).  It's a marketing scam and a money making scheme which is why I don't see much benefit in using it.  I don't even use it on my Windows boxes (and I take security seriously).

A better way to stop the rare piece of malicious code is not to install it.  This means sticking with the official repos if at all possible and updating the machine when prompted.  It's really that simple.  Nothing is 100%, but in life there is always risk analysis and trade-offs.  When you move to California, you are at a higher risk of getting killed in an earthquake, yet the risk is small enough that few people consider it.  When you get pulled over by the police for speeding, there is always the risk that the cop is a serial killer out to get you, but the risk is small enough that most of us don't refuse to pull over out of that fear.  I would say the risk of getting "malware" on an updated Linux box where the admin takes care in installing only trusted software is equally as slim.  Am I saying it's utterly impossible?  No.  I am saying the risk is small enough to be negligible if basic steps are taken.  I am also saying "security software" will do very little good and there's no reason to start insisting that Linux become Windows with its plethora of expensive "security suites."

I never said that vulnerabilities and malware are the same thing..so I'm not sure why your first sentence was worded that way. If you re-read my post, you see that I specifically mention malware AND vulnerabilities..not ever implying that they are the same thing. I also never advocated those "expensive security suites" that you mention, but simply gave tips to follow.

There are a plethora of security vulnerabilities out there for every platform, and I never made a direct comparison between any OS using actual numbers.  I never insisted that Linux become Windows; however, it's startling how many sys-admins (the ones you mention) seem to think that installing trusted software is enough, and that little hardening is needed..because it's Linux/Unix, not that silly Windows. I also wasn't targeting my attack at you, since it seems you took it that way. Either way, hopefully you see what I was saying now..if not, oh well.

---

### Post by bodhi.zazen on 2011-05-02
> **blind2314 said:**
> There are a plethora of security vulnerabilities out there for every platform, and I never made a direct comparison between any OS using actual numbers.  I never insisted that Linux become Windows; however, it's startling how many sys-admins (the ones you mention) seem to think that installing trusted software is enough, and that little hardening is needed..because it's Linux/Unix, not that silly Windows. I also wasn't targeting my attack at you, since it seems you took it that way. Either way, hopefully you see what I was saying now..if not, oh well.

I think there are two misunderstanding that occur.

1. New users coming from windows often want to apply "windows mentality" to Ubuntu, ie they want a firewall and antivirus.

2. Advice that Ubuntu (Linus) is not windows and that one does not need such things is then misunderstood as there is no need for security.

Most, if not all, experienced users / sys admin here emphasize security.

I see a bigger problem in that too many people can not be bothered with security. This is probably "OK" for the vast majority of Desktop users at the moment as Ubuntu is "secure enough" by default that most people do not have security problems related to the vulnerabilities you suggest.

If you are sysadmin a public server, yes you will need to learn to harden your server.

---

### Post by Jeff Root on 2011-05-03
Assuming that I'm smart enough to not be fooled by
phishing e-mails / websites trying to get credit card
numbers, passwords, or the like out of me, but not
smart enough to recognize a "suspicious site" when I'm
looking at it, what could a malicious website do to my
computer?  I visit websites almost every day that I've
never been to before.  There's no way I can tell ahead
of time which are safe and which are not-- especially
when I have no idea what might be unsafe about them.
Why are we being warned about "suspicious sites"?
 
   -- Jeff, in Minneapolis

---

### Post by perspectoff on 2011-05-03
Of course there's malware for Linux.

Just look at all the problems that Google has had (and Google is Linux).

Anyone who tells you there isn't malware for Linux is a fool. I'll capitalize that -- A FOOL.

Now, the modules that make up the Debian (and therefore Ubuntu) operating system are generally pretty well screened. All modules, however, have bugs and vulnerabilities (otherwise there wouldn't be a need for constant updates).

Nevertheless, an advantage of the large Debian community is that there are a lot of people that potentially may be hit by a security bug and can report it, or even sort out where the vulnerability in the code is. (While a vulnerability isn't malware, it's a security risk nevertheless. Just ask the poor slobs whose webservers were taken down, or databases hacked or destroyed, or Amazon Cloud installation snafu'd).

Still, a disadvantage of Ubuntu (and Debian) is that a lot of apps are rapidly updated before code vulnerabilities are found -- hence, zero-day attacks are still possible in the apps.

This is true for all software (without exception).

A lot of people who try to re-assure you that there are no risks from software are mostly spinning hype and marketing.

Most current malware isn't like the self-replicating viruses of 20 years ago. Even Windows users don't get hit by that very often anymore. (That's the type of virus that the dinosaurs say isn't prevalent in Linux, and on that score they're right). 

The problem is that backdoors are just as trivial to construct in Linux as they are in Windows. The Linux firewalls generally don't have deep packet inspection, so it is hard to detect unwanted backdoor traffic over standard ports (and most malware communicates over any open or standard port).

It is quite worthwhile, therefore, to be circumspect about which apps you obtain and use. There are tens of thousands of apps available for Linux -- it is not difficult to write malware for Linux. The question is whether someone will install it on their computer or not. Make sure you trust your software repository completely. That is why Apple, Google, and ubuntu are so rigorous about ensuring distribution channels. (When Apple and Google were lax with it, malware was everywhere, just as with Windows.)

Also, there are plenty of macros, Java, and Flash scripts that are well integrated into Linux these days, and I'll wager you have them on your system. These are good vectors for malicious code, too. I agree with the NoScript concept. It is probably the single most important module for being safe on the Internet.

It is trivial to install a keylogger, backdoor, and/or password cracker on any computer whatosever as part of a malicious downloaded app. Be careful. Lock your computer and secure it. Never use a public computer for sensitive transactions. Use secure passwords.

Suspect anyone who tells you any OS is perfectly safe. It's like the Midwest granny that thinks her neighborhood is perfectly safe and doesn't bother to lock the door. One day she comes home to find everything is gone.

I had a friend who thought his work computer was very secure. One day someone walked by with a USB drive with a Linux OS on it. They booted his computer from the USB drive, copied his hard drive onto a second USB drive, and walked away with all his info, to examine it at their leisure.

So, how many people have locked their OS against USB bootup? How many people have set privileges for the USB drive? 

Security isn't a matter of asserting something is safe. It is a matter of constantly thinking about and looking for all the weaknesses.

Having said all that, the biggest risk to your data at your bank isn't your computer. It's the bank.

Banks are hacked many times per year. They just don't publicize it. They build in a certain rate of loss to their projections and just live with it. It's been that way for years. (Why do you think they keep increasing your fees?)

Your security habits are small potatoes to the security breaches at large institutions. Think my USB drive scenario is rare? Think again. It's a daily occurrence.

I protected my data for decades. Two years ago I found all my personal data on the web, for the first time in 20 years. Where did it come from? My bank released all my mortgage info publicly. 

Cybersecurity is of national importance, but few in most sectors of government are educated enough to understand it (the military and CIA the exceptions, probably).

What can a paranoid user do?

Here's what I do:

I set up a secure partition with one installation of (K)Ubuntu and use it for my sensitive transactions only.

I set up another partition with a separate installation of (K)ubuntu on which I browse the Internet, play games, use social media, whatever. I never do both on the same OS installation. That way, if I unwittingly or inadvertently install a module (or dependency) that is not so safe, there is isolation between my sensitive partition and my "entertainment" installation.

Lately I have taken to keeping the installations on separate computers altogether, and using firewalls between them (on the LAN).

---

### Post by rookcifer on 2011-05-03
> **perspectoff said:**
> Of course there's malware for Linux.

Where is it?  Show me some malware out in the wild for desktop Linux.  I'll be waiting patiently.

> Just look at all the problems that Google has had (and Google is Linux).

Anyone who tells you there isn't malware for Linux is a fool. I'll capitalize that -- A FOOL.

Android is not Ubuntu. Android is not** desktop Linux.**  Android is a Linux-based OS specially designed for **smart phones**.

> It is quite worthwhile, therefore, to be circumspect about which apps you obtain and use. There are tens of thousands of apps available for Linux -- it is not difficult to write malware for Linux. **The question is whether someone will install it on their computer or not. **


Bingo.  Just don't install it.


> Also, there are plenty of macros, Java, and Flash scripts that are well integrated into Linux these days, and I'll wager you have them on your system. These are good vectors for malicious code, too. I agree with the NoScript concept. It is probably the single most important module for being safe on the Internet.

AppArmor is also effective.

> It is trivial to install a keylogger, backdoor, and/or password cracker on any computer whatosever as part of a malicious downloaded app. Be careful. Lock your computer and secure it. Never use a public computer for sensitive transactions. Use secure passwords.

Now you're getting into physical security which has nothing to do with the OS.

> Suspect anyone who tells you any OS is perfectly safe. It's like the Midwest granny that thinks her neighborhood is perfectly safe and doesn't bother to lock the door. One day she comes home to find everything is gone.

I don't know about others, but I've never said Linux is 100% safe.

> I had a friend who thought his work computer was very secure. One day someone walked by with a USB drive with a Linux OS on it. They booted his computer from the USB drive, copied his hard drive onto a second USB drive, and walked away with all his info, to examine it at their leisure.

Nothing to do with the OS.  He could have been running a TOP SECRET OS used by Area 51 and still succumbed to that attack.

> Here's what I do:

I set up a secure partition with one installation of (K)Ubuntu and use it for my sensitive transactions only.

I set up another partition with a separate installation of (K)ubuntu on which I browse the Internet, play games, use social media, whatever. I never do both on the same OS installation. That way, if I unwittingly or inadvertently install a module (or dependency) that is not so safe, there is isolation between my sensitive partition and my "entertainment" installation.

Lately I have taken to keeping the installations on separate computers altogether, and using firewalls between them (on the LAN).

The security benefit of that is not worth the convenience trade-off.  If your main OS was Windows, I might say it's worth it, but there are simply not enough threats in the wild for Linux boxes to bother.

---

### Post by Baumbart on 2011-05-03
> **perspectoff said:**
> 
 I agree with the NoScript concept. It is probably the single most important module for being safe on the Internet.

Except that NoScript itself can't be trusted since its attack on AdBlock Plus.

That's exactly what we are talking about. 
Security isn't about apps taking care of you. Not on Windows, not on Linux.
It's about attitude. 

So in my opinion no application should be suggested as "the single most" whatever, no matter how useful it may seem, if its author has shown a somewhat shady attitude towards security, as it is the case with NoScript.

Overall I'd subscribe most of what you write but here you are going like "Don't trust apps, so take this app to take care of it".

---

### Post by bodhi.zazen on 2011-05-03
> **perspectoff said:**
> 

What can a paranoid user do?



Learn to use apparmor (Ubuntu) or selinux (Fedora) or grsecurity (gentoo) or similar, but I think those are the "big 3" .

---

### Post by ChrisWells on 2011-05-03
I am no expert on security at all, but from my experience using Linux I feel 100% safe compared to Windows. Things like doing your banking online you shouldn't ever have to worry about. If my bank's site didn't use https, I'd instantly switch banks. As for malware, where is it suppsoed to come from? Websites that download dodgy files are almost all .exe Windows files that linux can't even read. Almost every single Linux app I have come across people have commented on, and there are so many popular apps for every job most people should be fine sticking with the top trusted programs. I'd say running Linux out of the box, even as root is a lot more secure than Windows. I never had any problems with viruses until a few months ago on Windows 7, I ran windows with full UAC, comodo firewall, avast AV, sandboxie, disabled services, fully updated etc etc never ever downloaded dodgy files or went on dodgy sites. I was doing daily routine boredom stuff and checked my startup items and found some file that looked like a system file, obviously a virus so I scanned it a removed it. But where did it come from? lol that put me off windows for good. Sorry for the tl:dr story but I spent 99% of my time on Windows maikng it uber paranoid security wise, only for a virus to slip in as easy as that

---

### Post by jramshu on 2011-05-03
I found, on Windows, that Zone Alarm Extreme Security works pretty darn good. I have had **a** virus, and found **a **trojan once. Others who use the other various av and firewall software(ex. Norton, AVG etc.) seem to get lots of infections. The infections they had shut down ALL their security software, stopped it from being able to run. I took care of theirs with some free software and completely, as far as we could tell, got rid of it. MalwareBytes. Haven't had any problems with Linux though.

---

### Post by ChrisWells on 2011-05-03
That's the only thing I miss about Windows- the constant maintenence to do when you're bored.

---

### Post by newbie2 on 2011-05-04
> **rookcifer said:**
> Where is it?  Show me some malware out in the wild for desktop Linux.  I'll be waiting patiently.
As a matter of fact, i was searching on the web for voip, and came on some regular website for voip-phones, and then some 'weird javascript' made me believe that i got several windows-virusses on my comp, but i have only ubuntu...:P ... so i wanted to close that site on my firefox, but i couldn't(got stuck), and had to 'hard reboot' my comp ... :
[http://ubuntuforums.org/showpost.php?p=10708426&postcount=30](http://ubuntuforums.org/showpost.php?p=10708426&postcount=30)

also there is some 'possibility-rumour' about linux for this :
[http://www.csis.dk/en/csis/blog/3195/](http://www.csis.dk/en/csis/blog/3195/)
:rolleyes:

---

### Post by spynappels on 2011-05-04
> **newbie2 said:**
> As a matter of fact, i was searching on the web for voip, and came on some regular website for voip-phones, and then some 'weird javascript' made me believe that i got several windows-virusses on my comp, but i have only ubuntu...:P ... so i wanted to close that site on my firefox, but i couldn't(got stuck), and had to 'hard reboot' my comp ... :
[http://ubuntuforums.org/showpost.php?p=10708426&postcount=30](http://ubuntuforums.org/showpost.php?p=10708426&postcount=30)

also there is some 'possibility-rumour' about linux for this :
[http://www.csis.dk/en/csis/blog/3195/](http://www.csis.dk/en/csis/blog/3195/)
:rolleyes:

The first is still not Linux Malware as such, it is just a Javascript which can be countered by running No-Script.

The second still requires some social engineering as the PBKAC still needs to (be tricked into) install(ing) it, and it would never get into the repositories. If you install software from untrusted sources, the problem is still between the keyboard and chair, not in Linux as such.

---

### Post by Linux&amp;Gsus on 2011-05-04
> **spynappels said:**
> ...the problem is still between the keyboard and chair...

And because of that, because **I AM** the problem, I convinced my Firefox to help me out a little bit...

In alphabetical order:

AdBlock Plus -> [https://addons.mozilla.org/en-US/firefox/addon/adblock-plus/](https://addons.mozilla.org/en-US/firefox/addon/adblock-plus/)
Better Privacy -> [https://addons.mozilla.org/en-US/firefox/addon/betterprivacy/](https://addons.mozilla.org/en-US/firefox/addon/betterprivacy/)
Flashblock -> [https://addons.mozilla.org/en-US/firefox/addon/flashblock/](https://addons.mozilla.org/en-US/firefox/addon/flashblock/)
NoScript -> [https://addons.mozilla.org/en-US/firefox/addon/noscript/](https://addons.mozilla.org/en-US/firefox/addon/noscript/)
RequestPolicy -> [https://addons.mozilla.org/en-US/firefox/addon/requestpolicy/](https://addons.mozilla.org/en-US/firefox/addon/requestpolicy/)

I think that it, or did I forget anything?

---

### Post by Baumbart on 2011-05-04
> **Linux&Gsus said:**
> 
I think that it, or did I forget anything?
Yes, you still don't care about said problem between keyboard and chair.

Installing Apps means **trusting** them and their authors.
These Apps can rip giant holes in the security of your browser instead of helping you out of anything.

So you need to ask yourself
1. Do I really need this app?
2. Which information give me reason to trust it?

You see the error in your attitude?
**You trust by default and only mistrust if you have reason.**
That makes you the biggest security risk on *any* OS and no app or OS can save your system from that.

A mistrusting user on Windows without firewall and antivirus is more secure than a too confiding user on Linux.

---

### Post by Linux&amp;Gsus on 2011-05-05
> **Baumbart said:**
> Yes, you still don't care about said problem between keyboard and chair.

But you did read my complete message, did you? I'll quote myself and make the relevant part obvious to observe...

> **Linux&Gsus said:**
> [SIZE="1"]And because of that, because **I AM** the problem,[/SIZE] [SIZE="2"]I convinced my Firefox to [SIZE="3"]_**help me out**_[/SIZE] a little bit...[/SIZE]


I hope that makes it obvious enough?




> **Baumbart said:**
> Installing Apps means **trusting** them and their authors.
These Apps can rip giant holes in the security of your browser instead of helping you out of anything.


Technically, that can happen with any update to any program, including the kernel itself.
If there would be no holes, no vulnerabilities, no security issues, then there would be no need to have a security update. It then needs only one 0-day exploit in the browser, the kernel, the app, to get spanked even by a trusted web site.




> **Baumbart said:**
> So you need to ask yourself
1. Do I really need this app?
2. Which information give me reason to trust it?

You see the error in your attitude?
**You trust by default and only mistrust if you have reason.**
That makes you the biggest security risk on *any* OS and no app or OS can save your system from that.


Nowhere did I say that I throw out my "common sense" and put all my trust in "this app".
I do not trust a single app as a all-powerful defence system. As you can see there are multiple points of blocking apps. Besides, those add-ons are not *trust-by-default*, as you put it. They are all in the *do-**NOT(!!)**-trust-by-default* category.

In the same sense I don't trust Linux as a single point of defence. Just because there is nothing in the wild for Linux at this moment, it doesn't mean that I get up in the morning leaving *common sense* sleeping in bed and click on every button I can find on a web site.

But at the end of the day, no matter how careful I am, having a 2nd or 3rd layer of security wont hurt. After all, this thread started in regards to online banking and the like. With things like that I even more so don't trust on a single point of defence.




> **Baumbart said:**
> A mistrusting user on Windows without firewall and antivirus is more secure than a too confiding user on Linux.

Let me fix that for you...
*A mistrusting user is more secure than a confiding user.*
Has IMHO nothing to so with the OS or anything else. See earlier comment, there are still security patches needed. In Windows, Linux, Oracle, Chrome, Safari, etc.

---

### Post by Baumbart on 2011-05-05
It wasn't my intention to attack you.
I just posted my 2c about that "install this, install that" talk that is going on here and _was my own mindset for way too long_.
So if I sounded like a complete smartass, sorry for that.

As I wrote, my turning point was when I read how the author of NoScript hacked AdBlock Plus in 2009 in order to show his ads everytime NoScript updated.

I learned from that, that I don't know **** about what a specific software supposed to help me really does. No matter how great its reputation.
I read a lot about what mozilla does to ensure the quality of the addons, which I'm ashamed not to have done earlier.
And to be honest, their standards are a sick joke. Authors should announce when they mess with other apps. Isn't that comforting?

If the human factor, user or author of software, is "flawed", you're screwed.

So I tried to direct this discussion to how we should behave rather than what we should install.

I didn't mean you personally but that "scareware-mindset", software to "help out", which in large part still is my own but nevertheless wrong.

---

### Post by Soul-Sing on 2011-05-05
> **Baumbart said:**
> It wasn't my intention to attack you.
I just posted my 2c about that "install this, install that" talk that is going on here and _was my own mindset for way too long_.
So if I sounded like a complete smartass, sorry for that.

As I wrote, my turning point was when I read how the author of NoScript hacked AdBlock Plus in 2009 in order to show his ads everytime NoScript updated.

I learned from that, that I don't know **** about what a specific software supposed to help me really does. No matter how great its reputation.
I read a lot about what mozilla does to ensure the quality of the addons, which I'm ashamed not to have done earlier.
And to be honest, their standards are a sick joke. Authors should announce when they mess with other apps. Isn't that comforting?

If the human factor, user or author of software, is "flawed", you're screwed.

So I tried to direct this discussion to how we should behave rather than what we should install.

I didn't mean you personally but that "scareware-mindset", software to "help out", which in large part still is my own but nevertheless wrong.

nah, this keeps "us" awake, i agree with you on many points.

---

