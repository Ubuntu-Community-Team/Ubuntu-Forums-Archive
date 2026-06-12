---
title: "XP user trying Ubuntu - mixed feelings"
date: 2007-07-23
forum: Testimonials &amp; Experiences
---

### Post by stevebroski on 2007-07-23
Preface - I'm a pretty happy XP user.  I've no doubt there are flaws to the OS but I'm a fairly experienced computer user and those flaws don't seem to affect me.  My XP system isn't filled with spyware, I can't recall the last time XP truly crashed on me, and the $150 I paid for the OS seems like a reasonable amount  especially given the obscene amounts paid I've paid for Adobe products and MS' SQL Server (which was really, really ridiculous).  Sure there are things I don't like - the 'Windows Updates' forces too many reboots and, while I'm somewhat sympathetic to the entertainment industry's concerns, DRM practices are a bit over the top.  But, all in all, I've found XP to be more than satisfactory.

At the same time I'm a huge fan of open source in at least one context and doubt I'll ever shift to MS in it's role.  I do primarily web development at my job for about 10 years now and that's always been on a LAMP environment (well... WAMP environment for development, LAMP for production).  I've always been impressed with that setup, particularly given the cost of similar functionality if I had to buy the equivalent commercial MS products.

For the past 6 years I've had a dedicated server at my disposal, starting with a Cobalt Raq3 (some flavor of Linux-based, a bit pricy, but easy to maintain) and more recently a much more powerful, much less expensive Mandriva-based server running open-source WebMin - which is more difficult for my limited-Linux knowledge to administer.  Frankly, with just ssh shell access to the server or the confusing WebMin interface, and limited Linux knowledge it's sort of scary for me to update things as if something goes wrong.. I struggle to fix it.  About twice a year I bring Apache down in the process of doing something that I thought would be trivial and have to google allover to find the cure.  On the last occasion trying to get my syslog logs to rotate correctly brought down Apache.  What the hell?  Anyhow...

The server still on MySQL 5.04 Beta and PHP 5.04 as they're working just fine and to this point I'd rather deal with 14-month old versions then risk bringing down the server.  Odds are upgrading either of those would be simple, but.... the worst-case scenario exists and I don't want to risk it.  But that approach won't work forever so I decided it's about time to get more comfortable with Linux hoping perhaps dealing with the dedicated server won't be so daunting in the future.  Strolled over to Digg's linux section and 80% of the posts seemed to be Ubuntu-based, so figured that might be the version to try.

I decided to try Ubuntu at home as moving off XP at work simply isn't an option for me.  I need Photoshop, period, and I routinely work with massive print-ready 11"x17" files at 300dpi - which puts such a strain on PS within XP I really can't picture working on them within a virtual XP environment.  Add to that we're a travel company and the airline reservation systems work on IE and IE-only (guess they actually like the proprietary IE stuff), and can't make that switch.

So I decide to setup a dual-boot Ubuntu installation on my home desktop.  The effort to do so was really minimal - I was impressed.  Defrag the hard drive to move files to the 'beginning' of the drive, download and burn that RescueCD app that's commonly referenced and repartition the drive all in a GUI environment.  Piece of cake.  Installing Ubuntu was smooth as silk as well.  In about 45 minutes my former XP system was now a full-fledged dual boot system.  Very nice!

Booted up to Ubuntu and everything looked dandy.  Played around a bit, OpenOffice has come a LONG way from last time I experimented with it.  GIMP seems to have improved.  Firefox looked like I'd expect... if it could actually connect to the internet.

Turned out my wireless connection was going to be an issue.  I use a linksys WUSB54G on an simple unsecured wireless network, but apparently the WUSB54G is a common sticking point.  There was a 12-page thread in the Ubuntu forums about this piece of hardware.  Talked of nsiwrapper or something and blacklisting entries.  But I couldn't get a grasp on the issue in *my* context.  The thread was a hodge podge of Draper and Edgy and Feisty, mostly talking of no OS acknowledgement of the card or getting DHCP working.  However my issue didn't seem to mesh.  Ubuntu recognized the hardware just fine, I could see all networks in range, I connected to my network just fine (showing 75%-81% quality), I was assigned an IP within the correct IP range and there was even a correct entry for my ISP's DNS server that Ubuntu could only have gotten with a valid connection.  But I was still dead to the outside world, and even local network IPs.

Figured I could post to the forums and try and battle, but didn't bother.  My laptop was sitting next to me and I figured I'd try that.

Same process.  Cleared some hard drive space, repartitioned, installed.  Took about 25 minutes as already had the .iso's and had been through the process already.  Once again, extremely simple and a massive improvement from my last Linux attempt 3 years ago or so.

Booted it up and everything looked the same.  Did the wireless connection to my network, everything looked the same as the desktop, opened Firefox and... whoa... the Firefox home page came up.  Excellent! Connectivity!  That afforded me the opportunity to install some other programs that looked of interest and I did just that (and I really do like the software search and install process).

The monitor looked a bit odd.  Turned out it was running at 1024x768 rather than the native 1280x800.  Searched on that and prepared for a new battle, as posts about a '915resolution' app, manually edited config files and more blacklisting abounded.  I installed 915resolution and rebooted, prepping for the battle.  But no battle needed.  Upon reboot that native resolution was now a given option and the OS looked immensely better at the correct resolution.  That was easy.

I installed and played with 'beryl' which is pretty neat, albeit not really necessary.  I'm not sure whether the multiple desktops are a beryl function or a core Ubuntu function, but they're really nice either way.  Installing Apache with PHP was a breeze.  Almost too much of a breeze as kind of wanted to do it the hard way as practice for my dedicated server.  But I can experiment with this at least.

Overall, I'm quite impressed.  I've always liked Linux as a server, but Ubuntu seems like a realistic alternative for the desktop - which is a first for me.

That said, and honestly not trying to stoke the flames of an OS war, I can't see a real switch away from XP in favor of Ubuntu.

First off, $150 or so spread over a five year lifespan or so is pretty trivial - so while I appreciate the free nature of Ubuntu/Linux, it's simply not much of a factor.  It's great... 150 bucks is 150 bucks... but not an massive issue.

Second, I don't have stability issues with XP.  I believe people who say they do, but I honestly don't.

Finally, I'm not at all wary about the security of XP but I'll admit that's only because I'm more experienced than the average computer user.  My mother is 400 miles from me and I do worry about her ability to keep a clean XP install (more on her in a sec), but I personally am not.  Absent concerns about price, stability or security, I don't see why I would make the switch.  Bottom line is there's no "killer app" that would make me need/want to move.  Apache and MySQL are killer apps, OpenOffice is pretty close to a killer app - but they're available for Windows as well.  Photoshop and MS' OneNote 2007 are killer apps (in my view), and not accessible in Ubuntu sans a hack-like configuration that wipes out the OS cost savings benefit even if you choose to take that approach.  When all is said and done, I'll pay the pro-rated $30 a year for a commercial OS and devote a bit of attention to security for access to virtually any software I could desire.  But that's just me as I have some specialized computing needs.

Back to my mother... I'd love to set her up with an Ubuntu system.  All she's really going to do is some surfing, email, light word processing, etc.  This is easily handled by any OS, and using Ubuntu I could set her up and head on home totally comfortable in the fact she's not going to get trojan'ed or crippled in spyware/adware.  It's truly an appealling thought.  The problem in my head though, is down the line.  It's when she gets some new digital camera and the CD that allows automatic transfer from the camera to her PC and one-click upload of the photos to some Kodak site or similar, and that software isn't an option for her.  Do I really want to try and walk my mother through installing via synapsis, using a photo editing program, transferring and uploading files to a website?  Honestly, no. Easier to throw AVG Free on her system configured to auto-update, install AdAware, and show her the absolute basics of using them once a month or so.

Anyhow, that's my view.  Ubuntu is a truly impressive product with flaws that only exist due to circumstances outside it's control.  I believe the "Criticism FAQ" says the same, but figured I'd vouch for that conclusion as a Windows fan.

I'd cheerfully recommend any Windows user who wants to try Ubuntu give the dual-boot setup a shot.  It's really simple and odds are good you'll have Ubuntu up and running in under and hour - and then you can make the decision for yourself whether it will handle your needs.

Best regards, and thank you for a great product.  I still plan on using it, just in a secondary role.

Steve

---

### Post by wolfen69 on 2007-07-23
from what i see, not everyone can kick windows to the curb so easily. but that's OK. everyone uses their computer in different ways. right now i'm 99.99% using linux. the .01% in windows is for printing my business cards. someday i'll buy an HP printer and go 100% linux. glad to hear you had a decent experience in ubuntu. rock on!

---

### Post by freebeer on 2007-07-23
Nice synopsis!  I equate OSes just like a tool... some tools are better in some circumstances than in others.  People have no problem with the concept of a dedicated gaming machine (PS2, Gameboy, etc.) so why can't they envision the same kind of thing for general computing needs?  If dual-boot works for you, by all means use it!

---

### Post by HermanAB on 2007-07-23
The right tool for the job.  That is the important thing.  Windows is basically a game platform that has been forced into a business role.  

MS has a problem with security and networking, so I use Linux for web browsing, email and everything but those one or two applications that XP can do in a virtual machine.  So I have used XP once this year, to do my taxes.

---

### Post by zdude on 2007-07-24
I use Ubuntu about 99.99% of the time since I switched from XP in February. I've now got four machines running in my house all Ubuntu, two being servers and the other my daughters computer - she really liked my setup soooo. As far as costs, it takes only a few hours, at most, to setup a new machine with Ubuntu (sometimes less). Windows XP, though, used to take at least two or three days to completely setup and that had to be done once a year (it seemed) or with any major hardware change. I switched out my Ubuntu server last night, upgraded the drives to a mirrored raid, new motherboard and cpu, etc. I was done in a couple of hours and my mail, ssh, apache, mysql, mythtv, ftp, etc. servers were all back on-line. Really freaking cool. No way can anyone do that in Windows in that short of time span. 
Bottom line, from my perspective, there are a lot more to costs than what you pay for the software! 
My $0.02

---

### Post by por100pre1 on 2007-07-25
Good to read such a good point of view on Ubuntu an Windows. It's pretty logical to say "if it is not broke, don't fix it" and Windows works for him. I got to say that Windows XP actually worked fine to me too, I wasn't the happiest Windows XP user, but it worked... It's important to say that many users are gonig back to Windows because of compatibility issues many are facing. Happily for me I didn't have such issues and now I use Ubuntu Studio most of the time.:)

---

### Post by rich.bradshaw on 2007-07-25
I guess the main thing is not having to run unnecessary services all the time such as antivirus, Genuine Advantage, IE Phising Filter etc. I don't have to report to Microsoft about everything I do - meaning I can use my computer without having resources tied up doing pointless tasks...

No maintenance is nice as well, no defrag, antivirus etc - easy.


I can get on with using my PC instead of fixing it.

---

### Post by Ralob on 2007-07-25
> **por100pre1 said:**
> Good to read such a good point of view on Ubuntu an Windows. It's pretty logical to say "if it is not broke, don't fix it" and Windows works for him. I got to say that Windows XP actually worked fine to me too, I wasn't the happiest Windows XP user, but it worked... It's important to say that many users are gonig back to Windows because of compatibility issues many are facing. Happily for me I didn't have such issues and now I use Ubuntu Studio most of the time.:)

you know, you make a good point. XP worked for me too but the problem came when I questioned the efficiency of the OS. both OS's do similar things, but it is HOW they do them that made me switch to Ubuntu. why deal with all the extra BS when there is no need, ya know?

---

### Post by 3rdalbum on 2007-07-26
The freedom of code and the exciting release cycle are good reasons to stick with Ubuntu over XP. You might not be able to write or even understand any source code, but the people who DO can make your computing time a whole lot better (more secure, more interoperable, bugs fixed, more accurate documentation etc).

Rapid release cycles, and the ability to try software that isn't production-ready yet, are part of what makes Linux so fun. You want to see your windows fold up into paper aeroplanes and fly off across your screen? Just compile the latest version of Compiz-Fusion and you can do it too!

---

### Post by por100pre1 on 2007-07-26
> **Ralob said:**
> you know, you make a good point. XP worked for me too but the problem came when I questioned the efficiency of the OS. both OS's do similar things, but it is HOW they do them that made me switch to Ubuntu. why deal with all the extra BS when there is no need, ya know?

You get no argument from me, in order to keep a Windows system working properly, you got to do a lot of things you don't need to do in Linux. That's a waste of time and resources. My experience with Ubuntu was great right [from the beginning]("http://ubuntuforums.org/showthread.php?t=447917"). But sometimes I think that everything has been too easy for me.:guitar:

---

### Post by ronnielsen1 on 2008-09-04
> Overall, I'm quite impressed. I've always liked Linux as a server, but Ubuntu seems like a realistic alternative for the desktop - which is a first for me.

That said, and honestly not trying to stoke the flames of an OS war, I can't see a real switch away from XP in favor of Ubuntu.
I didn't have the luck you did when I was using Windows. It seemed a constant struggle against something. I don't need to worry about that any more.
If you're impressed from a short time of evaluating linux, imagine once you learned how to get around. It's really a good system and for me I can relax on the security issues

---

### Post by Crafty Kisses on 2008-09-05
I'm glad you're impressed and sorry for the mixed feelings but Ubuntu does have learning curves.

---

### Post by ronnielsen1 on 2008-09-05
> Ubuntu does have learning curves.
Well, yeah. I remember staring at a dos, win 3.1, win 95, etc screen wondering what to do

---

### Post by armandh on 2008-09-05
I too have a stable & clean xp for some needs
and no intention of putting ubuntu on that machine [yet]

BUT no intention of going to vista either.
its not broke so I'm not "fixing" with it

---

### Post by tommygunner on 2008-09-21
Well, it seems to me that Ubuntu has a much steeper initial learning curve than XP but over the lifetime less maintenance will be required so less time will be spent.

---

### Post by karellen on 2008-09-21
very insightful comparison between XP and Ubuntu (or dare I say Linux as a whole). I agree with almost everything you've said. an OS is a tool - if it does its job right and the user is satisfied, no need to change it. but of course, there's always curiosity and desire for change (at least in my case. even when my Windows install works fine, I still need to get a glimpse of the "other side" :D). in the end, it all comes down to everyone of us, the amount of time someone is willing to spend in learning something new, the satisfaction of easily managing a whole different OS, with very few usability problems and so on.
as an advice, I'd say you should try other distros too, especially the friendly ones - OpenSuse, Mandriva (my distro of choice if you ask me), Mint, why not Fedora, Sabayon. you may be pleasantly surprised ;)
cheers :)

---

### Post by starcannon on 2008-09-22
> Preface - I'm a pretty happy XP user....At the same time I'm a huge fan of open sourceI think both of those statements can live in harmony. If your happy with XP, continue using it; and if you are a fan of Open Source, then simply choose the Open Source applications you enjoy, and run them on windows, many of them have Windows installers available for download. Certainly its true that if you choose to stick with XP, you will be limited a bit on Open Source application availability; but there is so much that IS available to XP that it probably isn't a deal breaker.

I'm a big Ubuntu fan, and no doubt, I'd like you to be able to be one as well; however, I do not believe that any one OS can be all things to all people, and if you've got something that you enjoy, then don't change. I think with a little searching you'll find that you can have your Windows XP cake, and Open Source frosting, and even get to eat it to.

GL and have fun.

---

