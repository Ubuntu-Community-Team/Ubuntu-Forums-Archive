---
title: "Why I gave up on Linux and returned to Windows XP"
date: 2010-07-22
forum: Testimonials &amp; Experiences
---

### Post by dforionstar on 2010-07-22
I am a senior IBM mainframe software engineer and database administrator and in its day I was highly proficient in MS-DOS line commands. I have written thousands of lines of computer code and tested hundreds of thousands of lines of computer code. I recently tried several Linux distributions and after too much time wasted chasing solutions for issues which simply work or work simply in Windows, I made the decision to return to Windows XP to catch up on other projects.
   
  I would like to begin by complementing all the software engineers, developers, and testers that have diligently worked and contributed to Linux. 
   
  On the positive side, Linux is void of one of the key architectural design faults of all MS Windows versions since Windows 95, that being  the Windows Registry or what I often refer to as the Windows Landfill. The issue is waste of RAM, operating inefficiency, stability, and OS portability. Fortunately, Linux is leaner and smarter.
   
  On the negative side, I encountered a persistent font-rendering issue with Ubuntu, Kubuntu, Xubuntu, and Linux Mint. I live on an HP nc8430 notebook PC with 1680x1050 WXGA resolution, where increasing font size is a must. The feature works for system fonts, but did not work for key applications like Firefox. My research revealed that the issue has already been documented throughout the Web and is related to these distributions failing to update the standard configuration file which Firefox and other applications rely upon for their font settings. While the Ubuntu folks are aware of it, they seem uninterested in fixing it. The issue is also present in Linux Mint which is based on Ubuntu. The fonts worked as expected for both Gentoo and PCLinuxOS. However I was unable to get my Intel 3945 ABG Wireless card to work with PCLinuxOS (both Gnome and KDE versions). 
   
In every incarnation of Linux that I tried, my _notebook fan was ALWAYS ON_ even when no applications were running with CPU near 0%. This issue may be related to CPU throttling and fan throttling. Linux needs to resolve this before I can use Linux on a notebook without the associated side effects related to the annoying noise of the fan always on max, increased fan wear, and reduced battery life. 

I found myself spending more time searching for solutions than enjoying Linux. There is nothing more this user would like than to depart the world of Microsoft Windows for Linux, but the path will have to be paved with far fewer rivers to cross or mountains to climb just to get there.

---

### Post by ST3ALTHPSYCH0 on 2010-07-22
Whether you stay or go is, obviously, in your field. I'm primarily a Win7 guy myself. [Here's](http://intellinuxwireless.org/) a driver for your wireless, and if you haven't given OpenSUSE a try, I recommend it. The downside, it's a DVD .iso. The upside, of the distros I've played with (admittedly in VM) it's the absolute nicest, easiest OOTB. I'd seriously consider a dual boot if you have the HDD space.

---

### Post by Mark Phelps on 2010-07-23
Hey, I understand where you're coming from. We share very similar backgrounds ...

Some folks enjoy spending untold hours hacking away getting something trivial like tablet screen rotation to work; others just want it to work "out of the box" and have no interest diving into the bowels of the OS infrastructure.

I joined the Linux (actually, Ubuntu) community back in the days when stability appeared to be a key characteristic.  I loaded one machine with 8.04 and it worked so well "out of the box", that I loaded several others as well.

But now, every Ubuntu release seems to be obligated to introduce something new and radical ... and that's "good" if you want to spend hours (or days) reworking your painfully-built customizations, but if you don't feel like going through that exercise every six months, it can be a real pain staying current.

I didn't use to build much from source, preferring the .deb approach. But now, I find I have to build more stuff from source every release. And while that is interesting, it places an added burden on staying current.

In contrast, I converted an MS Windows box recently directly from XP to Win7 ( I was told what awful fate would await me if I dared to convert it to Vista!!) and, surprise, surprise, all the XP-era applications and XP-era hardware continued to work "out of the box"!

Whereas, I have a tablet PC that came with XP, worked great with Ubuntu 8.04, and hasn't worked well with any Ubuntu release since that.

So, like I said, I can understand you wanting to go back to an environment where everything works.

---

### Post by Golem XIV on 2010-07-23
I definitely do not agree.  My experience is as follows:
- For most Linux distros I've played with: Boot Live CD, click on the installer, run the process and in 30-60 minutes have a working system complete with applications software.  In several cases some tweaking is needed to get it to "fully functional" state.
-For any Windows, including 9x, 2k, XP, Vista and 7: Boot CD, install system.  Install chipset drivers from manufacturer's CD. Reboot. Install graphics driver from manufactrer's CD. Reboot. Install sound driver from manufactrer's CD. Reboot. [and so on and so forth.  God help you if you don't have the drivers on hand on a CD or a pendrive]. Install a good firewall. Reboot.  install a good AV. Reboot.  To cut a long story short, I need about 4-6 hours to get to a working Windows installation, and then I have to start installing the applications.

As far as I'm concerned, ANY Linux distro out there (with a few intentional exceptions like Slackware and LFS) is a lot more complete and functional "out of the box" than any Windows setup.

And yes, I'm aware of pre-installed OEM systems with recovery disks, but let's compare apples with apples - if you want to compare a pre-installed Windows OEM system, compare it to a similar Dell or System 7 box.

---

### Post by Vaphell on 2010-07-23
about throttling - thank manufacturer of your laptop. There is no standarized way of control, every manufacturer does it differently, and even among the models of the same company stuff often varies. If there are no specs, there is a lot of guesswork and you can't expect bug-free drivers. I'd like to see how windows manages that mess in a situation when manufacturers don't bring finetuned drivers in their teeth to MS.

I don't agree that everything works in Win ecosystem. A lot of hardware got abandoned in the transition period from XP to Vista/7 - older hardware never got its drivers updated to the new architecture, new stuff never got it's drivers backported to XP. It happened to many many printers, scanners and such.

---

### Post by 98cwitr on 2010-07-23
I can do 95% of my job (I'm a systems analyst for state gov) on Linux. Now I admit, about 90 of that 95% is done via Citrix ICA Client. If I could get evolution or thunderbird to work with our Exchange OWA and get DNS working properly...I'd be set. I am Windows free @ home and work off a Ubuntu VM @ work (on my own accord).

---

### Post by SeePU on 2010-07-23
I agree with the OP and those that are at least confessing to the pitfalls. 

I'm not sure what the others are talking about but laptops are especially troublesome in linux.  It seems too many devs of various distros are working on the 'visual side' to make things look pretty instead of concentrating on practical mechanisms that people need to work.   Power management especially in laptops including fans, hibernate/suspend issues and the like have been problem areas in Linux for years.  Sure, some of the new laptops might have some of the things work but a lot of these also 'break' or stop working after a while.  That's what those guys above aren't admitting to.

In addition, there are many situations in which you better already be an expert or you will be spending most of your time googling and going through posts/articles and trying to find one that is similar enough to your problem.  When you're doing this, you'll come across a lot of people who aren't patient, who are elitist or otherwise don't have time for new users who are getting their feet wet or aren't proficient in every area of Linux.

There's a lot of reasons people go back to Windows and that's only a few of them.

---

### Post by prodigy_ on 2010-07-23
> In every incarnation of Linux that I tried, my notebook fan was ALWAYS ON even when no applications were running with CPU near 0%.
Yeah, this seems to be a common problem. However, for my Toshiba power management started to work better when I moved to 9.10 (kernel v2.6.31).

---

### Post by rollin on 2010-07-23
The fan problem does sound seriously irritating and I agree with what your saying that Linux does require quite a lot of research to keep finding solutions. That said it took me about 5 minutes to find this thread on Google and at least a head start to a solution: [http://forums13.itrc.hp.com/service/forums/questionanswer.do?admit=109447627+1279910373524+28353475&threadId=1041766](http://forums13.itrc.hp.com/service/forums/questionanswer.do?admit=109447627+1279910373524+28353475&threadId=1041766) (search ubuntu / yannick)

---

### Post by cgb on 2010-07-23
Sorry to see your experience has not gone smooth to say the least.  My laptop actually works great, power management and all, with Ubuntu but I know a lot of others are not so lucky.  As far as your firefox font issue, I'm thinking I'm missing something with your particular issue but you can adjust the text size on the fly within firefox by holding Ctrl and mouse wheel up or down.  Unless you meant the toolbar font then thats another story...

---

### Post by ssulaco on 2010-07-23
> **dforionstar said:**
> 
I found myself spending more time searching for solutions than enjoying Linux. There is nothing more this user would like than to depart the world of Microsoft Windows for Linux, but the path will have to be paved with far fewer rivers to cross or mountains to climb just to get there.
May I suggest trying Hardy Heron(LTS),She's been around since 4-24-08 and will reach EOL April 2013 (Desktop)....April 2015 (Server),I personally believe LTS's are significantly more stable because of the 3yr(desktop),5yr(server)life cycle,Lucid is also an LTS
[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

---

### Post by aysiu on 2010-07-23
> **ssulaco said:**
> May I suggest trying Hardy Heron(LTS),She's been around since 4-24-08 and will reach EOL April 2013 (Desktop)....April 2015 (Server),I personally believe LTS's are significantly more stable because of the 3yr(desktop),5yr(server)life cycle,Lucid is also an LTS
[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)
From your wiki link: > A new LTS version is usually released every 2 years. With the Long Term Support (LTS) version you get 3 years support on Ubuntu Desktop, and 5 years on Ubuntu Server. That means Hardy's end-of-life is April 2011 for the desktop and April 2013 for the server. It came out in 2008. 2008 + 3 = 2011. 2008 + 5 = 2013.

That means there's less than a year left for Hardy support.

---

### Post by lancest on 2010-07-23
[QUOTE=dforionstar;   
In every incarnation of Linux that I tried, my _notebook fan was ALWAYS ON_ even when no applications were running with CPU near 0%. This issue may be related to CPU throttling and fan throttling. Linux needs to resolve this before I can use Linux on a notebook without the associated side effects related to the annoying noise of the fan always on max, increased fan wear, and reduced battery. 
[/QUOTE]

Ok agreed Linux should improve. But then why aren't you obtaining notebook hardware specifically tuned for Linux or submitting improvements yourself (since you say you can code)? 
If you're gonna complain- then it comes down to that. 
Newbie or Windows pro the answer is always the same.

---

### Post by Elmer Fudd on 2010-07-23
Some hardware is just going to be tougher than others. I run 10.04 on a desktop a laptop and a tablet without problems. I live in Linux but have dual boot for my Aviation software which Jeppesen refuses to port to OSX (somewhat surprising) or Linux (not surprising). I support Win,OSX and Linux users. The Win people that I have converted to Linux (usually dual-boot) are now the least demanding of support and rarely boot to Win.
But.. you have to go with what works and it looks like your hardware is problematic for a smooth Linux expirience.
Hope that you will revisit it and contribute should you upgrade your equipment.

---

### Post by ssulaco on 2010-07-23
> **aysiu said:**
> From your wiki link:  That means Hardy's end-of-life is April 2011 for the desktop and April 2013 for the server. It came out in 2008. 2008 + 3 = 2011. 2008 + 5 = 2013.

That means there's less than a year left for Hardy support.

](*,)My mistake,I must have been thinking Lucid EOL

---

### Post by ST3ALTHPSYCH0 on 2010-07-23
It always amazes me the number of people who act *offended* that Ubuntu doesn't work for some people. Seriously, I doubt that many people make money one way or the other if other members run Ubuntu, some other distro, Windows, BSD, Solaris, OSX, or some cobbled together OS that utilizes BASIC. It's HIS OS on HIS equipment, and it doesn't make a bit of difference in the grand scheme of things what he runs. It's not "us vs. them" or even "open source vs. closed source". The grand theme of this forum is tech support.... if you're gonna take it personal that a piece of software, THAT YOU DIDN"T CODE, didn't work for someone else, then it's time to smash your computer equipment with a big hammer and go get a real life.
/rant

---

### Post by lancest on 2010-07-23
This section of the forum isn't about tech support.   
Human beings are always going to have opinions - it's what makes the world go round. 
If you can argue the ideal Linux user mindset- then let's see it.

---

### Post by bigboy_pdb on 2010-07-23
> **lancest said:**
> But then why aren't you obtaining notebook hardware specifically tuned for Linux or submitting improvements yourself (since you say you can code)?

People aren't going to throw money away on new computers when they already have one especially if they have other financial obligations (such as education, mortgages, car payments, children, and so on). The same thing goes for their time.

> **lancest said:**
> This section of the forum isn't about tech support.

This section is for testimonials and experiences and he gave both.

Please stop trying to cause trouble.

---

### Post by cariboo on 2010-07-24
This is the only post/thread the op has created, with a join date, the day he created this thread. There isn't much sense in continuing, as the op obviously doesn't want any help. Closed.

Thank you everyone for your participation.

---

