---
title: "Microsoft: Windows Server to Outpace Linux 3:1 by 2010"
date: 2007-05-16
forum: Windows
---

### Post by marx2k on 2007-05-16
[http://www.betanews.com/article/Microsoft_Windows_Server_to_Outpace_Linux_31_by_2010/1179330859](http://www.betanews.com/article/Microsoft_Windows_Server_to_Outpace_Linux_31_by_2010/1179330859)

By Scott M. Fulton, III, BetaNews
May 16, 2007, 11:54 AM

WinHEC Big WhiteLOS ANGELES - A video just shown here during the Day 2 morning keynote session at WinHEC showed Microsoft's "crack" server team working hard on the critical task of naming its new server operating system. After considering such candidates as "Windows Server Server Edition" and "I Can't Believe It's Not Windows NT," the team leader ends up tinkering with the name "Windows Server 2003" on the whiteboard, changing the "3" to an "8."

The message of the video was well-taken: Microsoft's taking itself a little less seriously now, coming to grips with its own legendary geekiness.

As the company's new general manager for Windows Server 2008, Bill Laing, took the stage, he started making a little news, shedding light on the company's server roadmap. **Citing IDC numbers predicting Windows Server installations overall to outpace the growth of Linux, at 8 million versus 2.75 million by 2010**, Laing said his company has established a "predictable rhythm of releases" going back to Windows 2000, and that this rhythm will not change going forward.

Laing's statement puts to rest any speculation that WS2K8 will be Microsoft's last "major release" of the operating system, and that the company would begin adopting a regular pattern of semi-annual server upgrades or service packs. He firmly said the company will continue its pattern of major releases every four to five years, with update releases in the two-to-three year intermediate timeframe.

With Microsoft's kernel development now synchronized between client and server lines, this timeframe pattern will likely apply to "Blackcomb" and future Windows client editions.

He followed up by saying that WS2K8 will be the company's final 32-bit operating system, with all future releases moving to 64-bit.

9:15 am PT - Midway through, Laing and product manager Alex Balcanquall revealed some news regarding the "Anywhere Access" program - the ability for networked or remote users to run Windows applications without their actually being installed on their systems. Laing said the company is leveraging some of its virtualization technology to that end, having invested (probably meaning, purchasing from elsewhere) a concept called SoftGrid. It's not ready to demonstrate yet, but it involves being able to "stream" application content from a server to a remote or networked client and have it run within a virtual machine envelope, dedicated exclusively to that application.

Last year at TechEd, we saw the first demonstrations of Vista's ability to run Windows apps via Terminal Services - a browser-based envelope within which Microsoft Office apps can be run on a remote or lower-order client. At that time, when the floor was opened for questions, a number of people shouted, "Printer drivers??" The presenters at that time looked a little red-faced, as if it was the first time they'd encountered the topic.

This year, Balcanquall showed an updated version of the Terminal Services demo. In that demo, a relatively unequipped Vista-based client ran Visio remotely, logging into the terminal server through a single prompt (a big advance for many of you familiar with Terminal Services). After pulling up a graph (for those of you keeping score at home, Visio ran in the Vista Basic theme, not the full Aero scheme), Balcanquall then proceeded to print the graph using the native local printer driver - not a generic or bypass driver. The demo garnered the most applause of the day thus far.

---

### Post by Yoooder on 2007-06-21
Lol, where do they get their Linux installation-base numbers from?  Really... find a definitive source for that one.

MS has the advantage of being able to track their product sales and product installations through SKUs, Updates, and WGA.  Few Linux distro's require any kind of activation/registration.  Most Linux distros can easily be fitted to run as a Server OS, whereas anyone running WinXP Home on a production server is nuts--unless perhaps they're running apache on it :-P

---

### Post by eentonig on 2007-06-21
I heard to funiest comment on Windows Server 2008 by our Windows Sysadmin.

He was full of love and telking about it. And the key points he mentioned? It's going to be a server which works almost completly on CLI. Not with all those GUI options that can be hacked.

I couldn't resist the comment. "So, they're going to bring out a linux server?"

---

### Post by StarsAndBars14 on 2007-06-21
Hah.  They wish!

---

### Post by crazyjx23 on 2007-06-22
That was so funny I had to change my pants lol. The irony kills me.

---

### Post by arvevans on 2007-06-22
This site gives some indication of the number of Linux based servers versus the number of MS based ones.

[INDENT][http://news.netcraft.com/archives/web_server_survey.html]("http://news.netcraft.com/archives/web_server_survey.html")[/INDENT]

---

### Post by kamaboko on 2007-06-22
> **arvevans@earthlink.net said:**
> This site gives some indication of the number of Linux based servers versus the number of MS based ones.

[INDENT][http://news.netcraft.com/archives/web_server_survey.html]("http://news.netcraft.com/archives/web_server_survey.html")[/INDENT]

Interesting trend.  See how MS market share has increased since March 2006 and Apache has decreased?

---

### Post by BoyOfDestiny on 2007-06-23
> **kamaboko said:**
> Interesting trend.  See how MS market share has increased since March 2006 and Apache has decreased?

Indeed, but i would be wary of some of the numbers...

> 
Microsoft has been paying the large domain resellers to move their "parked" sites to IIS on Microsoft Server. Moving the parked customers of a single large reseller, GoDaddy.com, caused a shift of 4.5 Million domain names, or 5% of total server share from Apache to Microsoft IIS in the Netcraft report. This is an "appearance" change only, because the sites involved have no content. But managers believe figures like those in the Netcraft report, and act on them. It's time for the Free Software / Open Source community to fight back.

[http://arstechnica.com/news.ars/post/20060419-6628.html](http://arstechnica.com/news.ars/post/20060419-6628.html)

As for the initial predictions, to be honest I'm not sure how I feel about it. I imagine Linux will continue to improve at a good pace, 
[http://www.linux-watch.com/news/NS8296942554.html](http://www.linux-watch.com/news/NS8296942554.html)

Only time will tell I guess.

---

### Post by kamaboko on 2007-06-23
> **BoyOfDestiny said:**
> Indeed, but i would be wary of some of the numbers...


Only time will tell I guess.

Without fail, any numbers indicating a larger share of anything to MS are wrong, but...if they indicate a larger share to Linux they're dead on accurate and without refute.  :lolflag:

---

### Post by blastus on 2007-06-25
For IIS to gain market share over Apache it has to enter the adult space. This is not something I imagine Microsoft will heavily market. So when the inevitable day comes when porn overtakes the Internet, IIS will be history.

---

### Post by cunawarit on 2007-06-26
> **blastus said:**
> For IIS to gain market share over Apache it has to enter the adult space.

lol, this is not something I've ever thought about. 

Is there any particular reason porn sites don't run on IIS more often? Are there even any CMSs tailored for porn portals? Is it price? The price disparity between renting a Linux and a Windows server is not that large nowadays.

---

