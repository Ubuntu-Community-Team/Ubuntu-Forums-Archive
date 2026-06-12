---
title: "My Dad on Ubuntu...A Desktop Experimentation"
date: 2009-03-02
forum: Testimonials &amp; Experiences
---

### Post by greenrubberducky on 2009-03-02
[INDENT]Hello! I'm Aaron, and I've been a Linux user since 2001 (hi Aaron!). Started on Redhat during college, really cut my teeth on Gentoo, and am now an avid Ubuntu fan. Right now I dual boot my main machine to 8.10 and XP, and have two Ubuntu web servers in my basement (one is an 8.04 test server; the other is 8.10 ([www.kurchev.com](www.kurchev.com)) and is currently down with hardware issues). [/INDENT]

[INDENT]ANYWAYS, I have a unique opportunity, and I thought I would share the upcoming experience with the community. [/INDENT]

**My Dad needs a new laptop.** 

[INDENT]Simple, right? He doesn't like to use his office laptop (Win XP) for personal stuff, and he travels all week. "Just get me a laptop for surfin' the web and getting on Skype", he said. Whatever. So off to Best Buy I go, and I walk home with the $500 weekly special. This week it was a Toshiba Satellite. Not too shabby, 250GB hard drive, 3GB RAM, built in mic and webcam. Model L305D-S5934 if anyone want's to check the full specs. Best Buy link: [http://www.bestbuy.com/site/olspage.jsp?skuId=9163772&type=product&id=1218040476935]("http://www.bestbuy.com/site/olspage.jsp?skuId=9163772&type=product&id=1218040476935")[/INDENT]

[INDENT]This is perfect for his needs. By that I mean it was relatively cheap. I considered a Netbook, but the tiny screen is no good for a 59 year old that doesn't like reading tiny print. [/INDENT]

[INDENT]This thing does of course come with Vista, which doesn't fit the bill. I don't (won't) use it, so I can't be his tech support over the phone. So I wiped the HDD clean, and tried to install XP Pro. Crash after crash, no luck. A little research turns up the fact that this thing has a SCSI drive, and the XP install CD doesn't load drivers for that. Okay...I can slipstream an install CD, or order a USB floppy drive (which I did anyways...sweet). USB drive won't work as the bios is kinda weird....look, the point is, XP will be a real tough nut to crack on this thing, and the conspiracy thickens. [/INDENT]

[INDENT]I was bored tonight, so I loaded 8.04 on to it. To my amazement, it installed flawlessly.  It updated flawlessly. THE ATI PROPRIETARY DRIVERS INSTALLED PERFECTLY, and the resolution looks GREAT! Skype...a cinch. It immediately recognized the built-in webcam and mic. Called my Mom 1 minute after installing the program. [/INDENT]

[INDENT]Let me pause to say that I didn't expect major problems or anything. There's just usually some small idiosyncrasy that bugs the hell out of me and requires research to solve. Notta this time. Wow!  [/INDENT]

[INDENT]So I think to myself, why does he need Windows? Is Ubuntu close enough in feel and function that he wouldn't notice? Let's consider this a test. He's relatively useful on a PC. He's been using one since MS-DOS 3.2 (our first IBM compatible...ah the memories). He went through Win 3.1, 95, 98, 2000 and XP. This is my personal Ubuntu usability test. [/INDENT]

[INDENT]I'm handing the laptop over to him this weekend. I'll document and report in on the progress as he starts using it. Will it be a seamless transition? Will he try installing some inane program, get frustrated and give up quickly? We'll see. Subscribe to the thread and keep up with the progress. Suggestions for useful apps would be appreciated.[/INDENT]

Aaron

**Update - 3/3/2009:** Installed some basic plugins, Foxmarks, other things to get this to a nice, easy use state. BIG problems right now with the Atheros wireless chipset. No-go entirely. I'm wading through the various methods of setup. I'm afraid that I'll need to find a nice clean GUI for the wireless setup, or this is not going to work. He'll be using wireless everywhere. Suggestions welcome on this. The articles I've found ont he forum have been very intense. I can handle manually editing my network config file and manually restarting the network. My dad cannot.

**Update - 3/4/2009:** I think I have the wi-fi working. This laptop has the Atheros AR500x card (couldn't even figure out which one), and required the madwifi drivers. Fortunately I'm only running the 32-bit version...the 64-bit fix seemed WAY worse to troubleshoot. Link to the Atheros fix thread:[http://ubuntuforums.org/showthread.php?t=792158]("http://ubuntuforums.org/showthread.php?t=792158"). Anyways, not quite there. Wifi is on, it can see my wireless network SSID, but will only get a ipv6 address, not a ipv4. Still working. On a side note, thanks for all the interest here. I've enjoyed reading the suggestions and whatnot so far. Can't wait til I get to the real meat of the article.

**Update - 3/8/2009:** Alright...day of reckoning. I'm dropping off the laptop to my dad this morning, and then he's off to Virginia again. Since Wednesday night, I've upgraded to the 8.10 release. I was just having such a bad time with wireless on 8.04. Still haven't configured it properly, but getting there. Also, I've just decided that the quality of the on-board mic and speakers SUCKS. So, I'll be sending a pair of Logitech gaming headphones with mic so he can use Skype. Wish me luck!

**Update - 3/9/2009:** Day of reckoning came and went. I put the laptop in front of him, watched the Ubuntu load screen come up, and then promptly hang for an eternity. WTF! So I dropped into the load detail only to see it hanging on the network driver load. Not sure if my loading WICD on it was the culprit, but I'm really getting tired of this whole wifi situation. So, he'll  be back in town next weekend. I've still got the laptop. I've tried madwifi, the 5xxx drivers, the native ath_pci drivers...bubkus. This thread is turning into a documentation of my frustrations, rather than my dads adoption of Linux.He was open too it, too, so the initial let down really irks me. On to next weekend.

**Update - 3/15/2009:** YES! SUCCESS! I've got the wireless working. Ready to go now. I'm on my way to my parents house to drop off and explain the basics. Here's the how-to I used for the Atheros 5007 card: 
[http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work-2/#before]("http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work-2/#before")
Thanks to the forum for all the help and encouragement. Now comes the real test.

**Update - 3/15/2009:** Okay...explanations done, laptop is handed off. He's headed back to the job in the morning. I expect I'll get the first tech support calls in the evening. The initial walkthrough was surprisingly easy. The only real comment he made was that he'd like the upper menu bar at the bottom. I knew there was a way to do that, but I didn't want to derail the conversation after 30 seconds. I'll remote in and change it later, or just email him the quick how-to. Anyways, finally off and running.

**Update - 3/23/2009:** Well, Dad has had the laptop for over a week now. He was home this past weekend, and I didn't hear a peep about it. The only problem he has had so far was when he first plugged it in. The power cord wasn't working. He jiggled it around for a while, finally got it to power up. As far as using Ubuntu, things have gone well. Granted, he's not a demanding user. So, I'll say things are going very well so far.

**Update - 5/6/2009:** Wow...things have gone really well. Dad has been using the laptop now for well over a month. The constant flood of questions I expected never came. He had one initial one, wondering if he could move the menu bar from the top to the bottom. By time I returned his call, he'd figured out to just drag it down. Couple weeks ago the wireless died. Atheros 5007. I wasn't surprised, it was such a pain to install. At this point, he's just plugging in. Otherwise he's either figured things out on his own, or things have just worked the way he expected. I upgraded him to 9.04 the other weekend. Taught him how to check for updates and to run the update manager. Things are fine. For his level of use, Ubuntu is essentially the same as Windows. Nice. If anyone has any specific questions they'd like asked, let me know.

---

### Post by wolfen69 on 2009-03-02
most people have no problem adjusting to ubuntu if they don't *need* a windows only app. in fact, most find it easier to use. anyway, hope everything goes well.

---

### Post by K7522 on 2009-03-03
Very cool, hope everything goes well for you guys. Great story, tell us how he likes it.

---

### Post by yther on 2009-03-03
Heh, sounds like a great machine!  If he only needs Skype and web access, it should be totally fine.  Plus, free OS, free tech support (ha ha), how can he lose?  ;)

I guess it will depend on how stubborn he is.  Must he have Windows, because that's what he's always had, or is he open to doing the same things in a different way&#8212;even if it's only a little bit different?

Good luck with the jungle music!  (Hm, I've never heard that... silly Kubuntu just has some chimes.)

---

### Post by lykwydchykyn on 2009-03-03
Undoubtedly there will be SOMETHING that he will come across apart from surfing and skyping that he won't immediately know how to do.  When that happens, if you're quick to have a solution, it should all go well.

---

### Post by wolfen69 on 2009-03-03
I have a customer that had 2 xp machines and used one of them to search for, ummm, well it starts with a p.

but constant viruses and malware impeaded his "hobby". But long story short, I turned him onto Ubuntu and he could not be happier. Now he can "surf" safely and actually enjoy his computer.

---

### Post by Crafty Kisses on 2009-03-03
Please keep us posted! Very nice story. Thanks for the read.

---

### Post by orethrius on 2009-03-03
I find this interesting, as it's apparently the ideal dual-boot situation.  Though I voted for "a few months down the road", I figure it has roughly an equal chance to swing either to "I want Windows back" or "this Ubuntu thingy isn't so bad".

Here's hoping for the latter.  :-)

---

### Post by Testrum on 2009-03-03
Interesting experiment. I wish I could do the same for my Mother and Sister :p but their all about their Windows :p I hope your Dad loves it.

---

### Post by greenrubberducky on 2009-03-03
Thanks for the interest, everyone. I think the most important part of this will be that I don't make a big deal about it. A very nonchalant  attitude, not a big deal, just point and click like normal...you know how to do this. If I spend too much time on it, he'll start to assume that it is too different or complicated to be worth his time. Looking forward to this.

---

### Post by sports fan Matt on 2009-03-03
Once my dad gets his new laptop Im going to try and install Ubuntu on it.  I was just there a week ago and noticed he had both Comcast and AT&T internet and noticed it was slowly dying.  (a dinosaur of a pc only with 192 mb ram, running xp..How I have no idea.).  The only thing he uses in Windows is MSN (Email) and some corporate program that launches Home Depot's database im guessing.  Although I cant remember the name iof it.

---

### Post by gymophett on 2009-03-03
Awesome, I'll keep checking back to this thread :D

---

### Post by blueridgedog on 2009-03-03
Be certain you install all the media items so he can view most web content...I assume you know how, if not, just ask.

---

### Post by Fenris_rising on 2009-03-03
Changing my dad from Win ME to XP was traumatic enough for him (this is before I saw the light). Sadly It's not possible to even contemplate giving him the best thing since sliced bread....sadly this also means I will atill be getting frantic phone calls because he can't follow his 'crib' sheets that we worked so hard on to make it easier for him.Of course the biggest problem now is because I am windows free I am forgetting all the fluff I needed to know to keep it all running :D

regards

Fenris

---

### Post by stchman on 2009-03-03
If the L305D-S5934 works perfectly OOB with Ubuntu it needs to be entered in the Ubuntu laptop wiki.  Does Compiz function?

As far as SCSI, that laptop has a SATA controller and XP does not support SATA without the use of SATA drivers on a floppy.  XP interprets SATA as SCSI.

If all your dad needs is web browser and Skype then Ubuntu is the way.  Ubuntu will have Openoffice and a lot of other useful apps.

---

### Post by Teamgeist on 2009-03-03
Make sure you install the **ubuntu-restricted-extras** package and add the medibuntu-repositories ([www.medibuntu.org](www.medibuntu.org)), if you haven't done this yet.

Also I recommend Cheese (Webcam) and Parcellite (awesome Clipboard) to be installed.

---

### Post by stchman on 2009-03-03
> **Teamgeist said:**
> Make sure you install the **ubuntu-restricted-extras** package and add the medibuntu-repositories ([www.medibuntu.org](www.medibuntu.org)), if you haven't done this yet.

Also I recommend Cheese (Webcam) and Parcellite (awesome Clipboard) to be installed.

I prefer Glipper for my clipboard.

---

### Post by aysiu on 2009-03-03
Power users (which I generally consider anyone who is the point-person for unofficial tech support or computer advice for families and friends) who leave Linux to go back to Windows generally do so for a legitimate reason (with a few exceptions) - hardware incompatibility, a Windows-only application.

Ordinary users (which I generally consider as the folks who ask for tech support from the power users) will be frustrated with pretty much anything that isn't familiar. Move the Windows toolbar to the top of the screen and they think a virus has attacked the machine. Delete a few shortcut icons from the desktop, and they think the program they use most is now uninstalled from the machine.

If your dad is very tied into habits, switching to another operating system (even if all the programs suit his needs, even if there are no hardware incompatibilities) may be too much for him. I'd say the same for Vista, for OS X, and for Ubuntu.

Some people just aren't good for change.

If your dad considers the Internet Explorer icon to be "the internet," then I wouldn't wager he'd last too long on Ubuntu.

If he's open-minded, though, it sounds as if Ubuntu may be the perfect solution for him.

---

### Post by Old_Grey_Wolf on 2009-03-03
I find this thread amusing. :)

I am one of those senior computer users in the 60+ year category. Some of us have a lot of free time to learn about computers. Some of us have reasons to do so; such as, family research, communication with relatives, and so forth. Some of us had the first of the home computers before they become a necessity. :)

And, YOU DON'T HAVE TO YELL AT US BECAUSE OUR HEARING IS GOING BAD!!! It is a stereotype in most cases.

:lolflag::lolflag::lolflag:

---

### Post by greenrubberducky on 2009-03-03
> **blueridgedog said:**
> Be certain you install all the media items so he can view most web content...I assume you know how, if not, just ask.

Yeah...I've been putting it through it's paces tonight. Setting up Firefox with his Foxmarks account, getting the plugins installed...you know. I also set OpenOffice to save to MS Office extensions, so he doesn't have to worry about flipping files back and forth. 5 days until hand-off.

---

### Post by aysiu on 2009-03-03
> **Old_Gray_Wolf said:**
> I find this thread amusing. :)

I am one of those senior computer users in the 60+ year category. Some of us have a lot of free time to learn about computers. Some of us have reasons to do so; such as, family research, communication with relatives, and so forth. Some of us had the first of the home computers before they become a necessity. :)

And, YOU DON'T HAVE TO YELL AT US BECAUSE OUR HEARING IS GOING BAD!!! It is a stereotype in most cases.

:lolflag::lolflag::lolflag: I don't understand why you're making this point. No one said anything about age here.

---

### Post by lykwydchykyn on 2009-03-03
I'm trying to remember how exactly I got my wife switched over to Linux.  I bought her a laptop and just kind of put it on there and showed her how to use it.  It was dual boot but somehow she just ended up using Linux (Mepis at the time) because it had more stuff built in.  Ok, maybe I purposefully left the windows install a bit thin...

But now she won't go back.  She has to boot back to windows to listen to the DRM audio books from the public library's website, and she usually ends up screaming at it because it gets an update and reboots right in the middle of an exciting part.

If you make Ubuntu the path of least resistance on the machine, your dad will cope with it.  People can be surprisingly adaptable when they need to be.

---

### Post by lisati on 2009-03-03
Suggestion for an option for similar polls in the future: "What's 'Windows'?" (This is someting said by someone I know who has been using Windows machines a lot longer than I have and who still does)

---

### Post by old fert on 2009-03-03
If all your dad needs is web surfing and email, he won't have a problem.  

My first computer was a comadore 64.  I do the debugging and virus killing for my two 30 + yr old kids, son in law, and 12 yr old grandson.

---

### Post by greenrubberducky on 2009-03-03
> **stchman said:**
> If the L305D-S5934 works perfectly OOB with Ubuntu it needs to be entered in the Ubuntu laptop wiki.  Does Compiz function?

As far as SCSI, that laptop has a SATA controller and XP does not support SATA without the use of SATA drivers on a floppy.  XP interprets SATA as SCSI.

If all your dad needs is web browser and Skype then Ubuntu is the way.  Ubuntu will have Openoffice and a lot of other useful apps.

YES! Very smoothly, too.
[IMG]http://photos-d.ak.fbcdn.net/photos-ak-snc1/v2568/5/70/1378236890/n1378236890_30307723_7809579.jpg[/IMG]

---

### Post by greenrubberducky on 2009-03-03
> **Old_Gray_Wolf said:**
> I find this thread amusing. :)

I am one of those senior computer users in the 60+ year category. Some of us have a lot of free time to learn about computers. Some of us have reasons to do so; such as, family research, communication with relatives, and so forth. Some of us had the first of the home computers before they become a necessity. :)

And, YOU DON'T HAVE TO YELL AT US BECAUSE OUR HEARING IS GOING BAD!!! It is a stereotype in most cases.

:lolflag::lolflag::lolflag:

Not yelling. Just using caps as surrogates for bold font. I just prefer to write that way for emphasis.

---

### Post by lisati on 2009-03-03
> **greenrubberducky said:**
> Not yelling. Just using caps as surrogates for bold font. I just prefer to write that way for emphasis.

**Pardon?**;)

---

### Post by greenrubberducky on 2009-03-04
> **lisati said:**
> **Pardon?**;)

Exactly...I'm just going to stay focused on the article, and ignore the chatter.

---

### Post by Martje_001 on 2009-03-04
Buy something like this:
[IMG]http://www.qfonic.com/images/products/lw053/image01.jpg[/IMG]
if you can't get wireless to work. It's working fine on my sisters laptop (which hasn't got any wireless capabilities on it's own).

You could also try loading the windows driver (.inf-file) with ndiswrapper, there's even a nice GUI for it called ndisgtk.

---

### Post by stalkingwolf on 2009-03-04
I keep a couple netgear usb adapters handy all the time. i get them on ebay
for about 5 dollars.  I also use the DLink DWL G650 air cards ( about $15
on ebay) .   A nice little app for wifi is WIFI Radar.  It in the repository.

---

### Post by greenrubberducky on 2009-03-04
To expand on my wireless issue, the drivers work, the wireless card (ath0) can detect my SSID, and even get a bogus ipv6 address, but no ipv4 address. Kinda hard to manage it with the included network manager. Can anyone suggest an easy to use network management tool? This is going to be a critical aspect of the project...a make or break, I'd say. If my dad can't easily open a window, pick a network, enter then key (depending on encryption) and go...well, that's not good.

---

### Post by greenrubberducky on 2009-03-09
Quick update...

I've had too much trouble with the wireless install (Atheros AR242.x card), and I'm really not sure where I am. I'm going to sleep on it, but I'm between struggling for a couple more days, and just dropping on a fresh 8.10 install. I'm really kinda frustrated with the fact that I can't even get this configured right. How can I expect pops to be hunky dory with this thing if I can't even get something simple like wifi to work. I hate to say it, but this is an example of why Linux (not just Ubuntu specifically) is not *quite* there yet. Believe me, I'm a firm believer that Ubuntu has brought Linux MILES closer to mainstream computing and LIGHT YEARS into the future. 85-90% there, you know. Still a dollar short. On I trudge.

---

### Post by orethrius on 2009-03-10
[http://ubuntuforums.org/showpost.php?p=6836976&postcount=30](http://ubuntuforums.org/showpost.php?p=6836976&postcount=30)

From a run prompt (hold Alt and hit F2):

```
xterm -e 'gksudo apt-get install wifi-radar'
```

Wifi Radar doesn't help at all?

---

### Post by stalkingwolf on 2009-03-11
I was just going to suggest wifi-radar.  and for windows easy wifi-radar
one of the best utilities ive found.

---

### Post by greenrubberducky on 2009-03-11
Um...I'm kinda unclear on what wifi-radar is supposed to do. I had it installed for a bit, but it had to be uninstalled/disabled when I tried out WICD. I'll read into it a bit tonight.

---

### Post by wolfen69 on 2009-03-11
wifi-radar is supposed to do what wicd does. only not as good.

---

### Post by greenrubberducky on 2009-03-12
Yeah...so I did a complete fresh install from a new 8.10 CD. Still not able to get wifi out of the box. I'll work on this for another day or two, that's it. Then it's just going to have to be plugged in. Whatever. Only one strike. Everything else is working fine. Must just be this particular Atheros chipset.

---

### Post by orethrius on 2009-03-12
> **greenrubberducky said:**
> Yeah...so I did a complete fresh install from a new 8.10 CD. Still not able to get wifi out of the box. I'll work on this for another day or two, that's it. Then it's just going to have to be plugged in. Whatever. Only one strike. Everything else is working fine. Must just be this particular Atheros chipset.

Have you tried ndiswrapper with the appropriate Windows driver?  I know it's not really a solution, and I suspect it's kinda taboo, but it's decent as a stop-gap.

---

### Post by Jakadinho on 2009-03-12
My mother have no clue about computers and i installed linux for her. She use it only for web browsing and printing and she said its easy and simple.

Also i didnt have problems with computer for almost 2 years. Before i have to fix fer computer once per week/month

---

### Post by terry_gardener on 2009-03-12
this is a very interesting experiment.

i have converted my parents and my nephews to ubuntu. 

i have been wondering about your wireless issue, found this might of interest to you. 

[http://www.interstice.com/drewes/20090224-toshiba-l305d.html](http://www.interstice.com/drewes/20090224-toshiba-l305d.html)

---

### Post by hashimoto on 2009-03-12
> **greenrubberducky said:**
> Quick update...

I've had too much trouble with the wireless install (Atheros AR242.x card), and I'm really not sure where I am.

At least someone has got something Atheros 242-based running, See
[http://ronymattar.com/blog/?p=9](http://ronymattar.com/blog/?p=9)

---

### Post by greenrubberducky on 2009-03-12
> **orethrius said:**
> Have you tried ndiswrapper with the appropriate Windows driver?  I know it's not really a solution, and I suspect it's kinda taboo, but it's decent as a stop-gap.

Can't unpack the driver from the windows exe. Also can't find it in the wild.

---

### Post by greenrubberducky on 2009-03-13
> **terry_gardener said:**
> this is a very interesting experiment.

i have converted my parents and my nephews to ubuntu. 

i have been wondering about your wireless issue, found this might of interest to you. 

[http://www.interstice.com/drewes/20090224-toshiba-l305d.html](http://www.interstice.com/drewes/20090224-toshiba-l305d.html)

DUDE! Awesome link! Leads me to a different method of install here. I'm going to try tonight. It sounds like he just used the standard 242.x drivers, ignored the 5xxx drivers, and installed linux-modules-backports to get it working. Nice.

---

### Post by Azhtabak on 2009-03-13
I'm not sure if it's still relevant at all, but if it is, have you tried a jaunty 9.04 alpha cd? I had the same wireless problem, and it worked out of the box with Jaunty (though I'm having problems with another network, it works perfectly with my main one)

---

### Post by greenrubberducky on 2009-03-14
> **Azhtabak said:**
> I'm not sure if it's still relevant at all, but if it is, have you tried a jaunty 9.04 alpha cd? I had the same wireless problem, and it worked out of the box with Jaunty (though I'm having problems with another network, it works perfectly with my main one)

I'm very excited about the upcoming Jaunty release, but I'm going to stay away from it on this laptop until it goes to distribution.

---

### Post by ugm6hr on 2009-03-14
Not really the best place for support issues - but...

If lspci reports it as AR242x, this is a useful read:
[http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default](http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default)

Explains why wifi doesn't work out of the box.

[linux-backports-modules-intrepid-generic]("apt:linux-backports-modules-intrepid-generic")

Then blaclist **ath_pci** and **ath_hal**.

Add **ath5k** to /etc/modules

A reboot should do it.

Now... back on topic...

Has your dad ever even experimented with Ubuntu?  I introduced my mum to Ubuntu over a weekend, and get the occasional phone call or email for help.  I left her dual-booting, so that she can mess up one OS and still have a working computer; it was a virus-fest on Windows that first disabled her laptop prompting the Ubuntu installation.  Now Windows is reserved for specific websites only (mainly gmail); although I did have a bit of scare when she called me saying that she was surfing and got a virus alert (which sounded like a scam website alert).

---

### Post by greenrubberducky on 2009-03-23
Bump for a new update!

Also, please send me some questions as I will try and conduct a formal user interview in a couple weeks.

---

### Post by Hortichris on 2009-03-26
Its possible to get cross, I'm a Dad.  As it happens, I came across Unix long before Windows was on the scene.  Around 1980 IRRC.

I have introduced three of my sons to Linux!  One of them has progressed to OS X.  None of them hanker after good old windows.

Bashing at a terminal?  I was a mainframe operator back in the early 70's.

Some Dads are way ahead of the game.  (But I still can't get my [expletive] AR242 to work, will wait for 9.04)

---

### Post by KCG102282 on 2009-03-26
> **Hortichris said:**
>   One of them has progressed to OS X.

If you call that progress

---

### Post by uptheirons1 on 2009-05-04
Cpu fan control does not work for L305D-S5934 with ubuntu jaunty. So it really isn't perfect out of the box. Does the fan go up and down according to cpu temp out of box with 8.10?

---

### Post by rrashkin on 2009-05-05
Just a minor point (in reference to the original comment about a "netbook").  My wife and I are both 59 and we love our ASUS eeePC (running Linux), small screen and all.

---

### Post by Garrovick on 2009-05-05
Well, I'm a Dad and I use Linux. (And I may know your Dad.:))  Linux is okay for regular simple everyday use...

But,as a single simple example...

For "iTunes" like programs and "iPods", Linux gets a big red zero over a big red F.  Some times the problem isn't the OS it's self, but what it doesn't do.

Think of it as if Ubuntu doesn't do iPods the way they were designed to be used. And if all that's important is the iPod. Then OSX or Windows is the only solution.

But I ended my Ubuntu iPod disastrous traumatic ordeal with the purchase of an Acer One XP machine.

As as the age old saying goes, one buys the machine that runs the software they want to use. Not the other way around.

---

### Post by MartyBuntu on 2009-05-05
> **Garrovick said:**
> 
Think of it as if Ubuntu doesn't do iPods the way they were designed to be used. And if all that's important is the iPod. Then OSX or Windows is the only solution.


The other solution is to not buy iPods. Which I don't.

I wouldn't change my entire computer experience for a finicky music player to dictate how I get my songs on the player.
That's why, after researching, I bought a Sansa which works perfectly with Ubuntu and my needs.

---

### Post by gtr32 on 2009-05-05
> **Garrovick said:**
> For "iTunes" like programs and "iPods", Linux gets a big red zero over a big red F.  Some times the problem isn't the OS it's self, but what it doesn't do.

Hmmm, I have to try that myself, I have an iPod laying around somewhere. I did install 8.10 on a friends computer and I tested it to work with iPod, but I didn't do a full test. Have not heard any complaints yet and it's been a few months now so I am assuming she's able to use it.

What kind of problems did you experience? (so I can try them out)

---

### Post by Garrovick on 2009-05-05
> **gtr32 said:**
> Hmmm, I have to try that myself, I have an iPod laying around somewhere. I did install 8.10 on a friends computer and I tested it to work with iPod, but I didn't do a full test. Have not heard any complaints yet and it's been a few months now so I am assuming she's able to use it.

What kind of problems did you experience? (so I can try them out)

Well, you can fill it with hundreds or thousaands of mp3s. And Ubuntu handles that fine, you can do some tagging and it does pretty good arranging by album and there is playlist support.

But there is no bookmarking or resume where left off capability. It's like listening to two hours of a book, and then having to remember or make a note on paper of where I stopped listening.

Audio books are not separated from music, nor are podcasts and video support is, lets' say non-existent. (Even though I'm sure there is some sort of script to enter in terminal to install and remove them. And that's a big yawn))

Plus the default Rythmbox does a horrible job of removing files, that means the gktpod is mandantory, but gtkpod doesn't play music.

On the other hand, it Ubuntu had come before the iPod, I wouldn't have bothered buying the iPod. I would have bought an very simple mp3 only player.

Then Ubuntu creates some sort of "trashcan" on the iPod hard drive that took up almost 8 gigs of space on mine, and I believe that almost caused it to crash.

Basicaly if all that's on the iPod is music, then it's good to go. But then my $250.00 iPod becomes a $30.00 mp3 player.


PS: Also if Apple comes out with a bug fix. Forget it. Linux doesn't update iPods.
Like I posted, I bought a netbook for the iPod. Problem solved.

---

### Post by blueridgedog on 2009-05-05
> **Garrovick said:**
> Well, I'm a Dad and I use Linux...

But I ended my Ubuntu iPod disastrous traumatic ordeal with the purchase of an Acer One XP machine.


One man's ordeal...as a mater of fact one of the main reasons I was driven back to Linux was my frustration with iTunes.  I tend to think that if you want to manage you music, then iTunes gets in the way, but if you want to have it managed, then it is a decent application.  I love the way my iPod is managed under Linux with Floola.  My 60 gig iPod is full and I rotate audio books and films while keeping my base of music constant.

---

### Post by Garrovick on 2009-05-05
> **MartyBuntu said:**
> The other solution is to not buy iPods. Which I don't.

I wouldn't change my entire computer experience for a finicky music player to dictate how I get my songs on the player.
That's why, after researching, I bought a Sansa which works perfectly with Ubuntu and my needs.

I have a Fuze and a E-280.

Try and update the firmware using linux. But downloading the update as bin file and draging it to the Sansa works too. Sansas work well with Linux in drag and drop mode.

And how do you convert the pictures and videos to put on the Sansa with Linux?  I don't put those items on mine, just curious.

---

### Post by Garrovick on 2009-05-05
> **blueridgedog said:**
> One man's ordeal...as a mater of fact one of the main reasons I was driven back to Linux was my frustration with iTunes.  I tend to think that if you want to manage you music, then iTunes gets in the way, but if you want to have it managed, then it is a decent application.  I love the way my iPod is managed under Linux with Floola.  My 60 gig iPod is full and I rotate audio books and films while keeping my base of music constant.

My iPod is set to manually manage music and videos and disk mode. No auto for me. I like my folders in iTunes they way I want them arranged.

And have you managed the book marking and resume functions?

It's easy in Linux just to stack files on the iPod or a Sansa or any other mp3 player, but an entirely different matter getting it to function as an iPod.

The reason for the netbook.

---

### Post by greenrubberducky on 2009-05-06
My dad has a Sony mp3 player. I loaded it up once with a bunch of music I ripped of his old vinyls, and he just listens to it in the car. It will plug into his PC, and act like a jump drive, so no issues if he wants to add new songs. 

BTW, I upgraded him to 9.04 over the weekend. The upgrade went flawlessly, but still no wireless. It might work if I do a clean install, but he has it set up the way he likes, no need to derail things when the rest is going well. Besides, he's just using it at home, and doesn't migrate far from the couch. He doesn't mind plugging it in. Other than that, I've gotten no reports of things that he wished it did. Experience has been positive so far.

---

### Post by blueridgedog on 2009-05-06
> **Garrovick said:**
> And have you managed the book marking and resume functions?


To enable book marking and resume in an audio book, it has to be converted to an audiobook file type (m4b extension).  I convert mine just fine with linux, but I would say the process is pretty geeky and not foolproof, but I am satisfied.  The principle element is using faac to do the conversion rather than the Apple codec.

I listen to a part of an audiobook every night as I enjoy my daily cigar, so I have spent time converting many books.

---

### Post by RamonB on 2009-05-17
My problem is opposite of yours. I'm 57 years old and I have two sons and two stepsons (ages 27 to 33). 

I'm an Ubuntu fan since I installed Ubuntu 8.10 with Wubi 8 months ago. Now, I have dual boot 9.04 without Wubi (in both of my machines, the desktop and the note eeePC 1000H) and I don't remember the last time I booted my Windows (I need only 2 Windows programs. So, I installed an old XP-SP2 -- that I had from an old computer -- in VirtualBox to run this programs without booting Vista).

But none of my "boys" neither my wife want to hear anything about Ubuntu. They are Windows addicted...

---

### Post by blueridgedog on 2009-05-17
> **RamonB said:**
> 
But none of my "boys" neither my wife want to hear anything about Ubuntu. They are Windows addicted...

Well...if you are looking to adopt...papa.

Seriously though, I feel pain, however, kids under 10 don't care what it is called, they just have application or task specific needs that have to be met (my 10 y/o loves my netbook).

---

### Post by armandh on 2009-05-18
> **wolfen69 said:**
> I have a customer that had 2 xp machines and used one of them to search for, ummm, well it starts with a p.

but constant viruses and malware impeaded his "hobby". But long story short, I turned him onto Ubuntu and he could not be happier. Now he can "surf" safely and actually enjoy his computer.

that unsafe surfing gave the computer I loaned my brother in law a virus. now cured with ubuntu, his $34 printer was the only casuality

---

### Post by Adoran on 2009-05-18
Best of luck mate! Lol, I posted a thread a few minutes after yourself. The opportunity of a new niece gave me the leverage to convince my mum that irreplaceable photos should really be kept on a file system that is actually documented.

I hope he enjoys it - so far no complaints from my mum, dad only really uses it for the BBC iPlayer and since he doesn't download the shows Firefox suits him fine.

---

