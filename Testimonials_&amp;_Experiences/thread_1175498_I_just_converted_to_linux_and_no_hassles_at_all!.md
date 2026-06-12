---
title: "I just converted to linux and no hassles at all!"
date: 2009-06-01
forum: Testimonials &amp; Experiences
---

### Post by indigo_myst on 2009-06-01
[FONT=Verdana]Well I have to say i'm definitely converted... having taken the plunge from a linux virgin and completely changing from horrible windows to Ubuntu today, and so far all has gone well. 

Thanks to all the forum posts and pre-preparation I haven't had any real issues at all. And the learning curve has been pretty easy.  If I had reformatted the comp to windows xp I'd probably still be uploading the updates! 

Even got the ol bigpond cable working without any hassles!  I must add though - that if you are looking for configuration help - may I suggest that you use the command in the terminal: 

[COLOR=Purple]sudo gedit /etc/bpalogin.conf[/COLOR].  NOT sudo vi /etc/bpalogin.conf.  I was trying to edit on the later command and got frustrated till I found a post with the first command line.  Changing the password and username was a breeze after that. 

Also definitely recommend get a linux friendly wireless adaptor and save yourself heaps of hassles.  My other one was a netgear w111 v2... and after reading posts of all the hassles people had and a quick test in Live CD mode,  I just went and got a d-link DWA110 before the changeover and it worked a treat. I was connected to the cable within a minute and email all up and going in evolution.  

My only regret... not doing this a whole lot sooner.  Thanks Ubuntu! I can't believe how quick everything is now - AND compiz is sooo cool! The way you can change the design so easily and configure it how you want it is a big hit for me. 

**_My tips to make things go smoothly:_**

[/FONT]
[LIST=1]
[*][FONT=Verdana]if you can... print out all the documentation you will require to have on hand as easy reference. [/FONT]
[*][FONT=Verdana]Check your computer specks and see if they are compatible and check the forums for any issues.  Pre-download any drivers (just in case)  I did this but still didn't need them, but still pays to be cautious.[/FONT]
[*][FONT=Verdana]If you have bigpond cable - check your adapter - and through forums of known issues... I saw heaps with the netgear so researched into one what was.  Bought it and plugged in before I turned on computer to install. [/FONT]
[*][FONT=Verdana]Have your wifi key ready and any passwords and settings info ready this includes email details. [/FONT]
[/LIST]
Cheers

---

### Post by Tibuda on 2009-06-01
Welcome, and enjoy your new OS! ;)

---

### Post by meastp on 2009-06-01
Welcome! :)

About the terminal command :

try *nano* instead of *vi* for editing via terminal;
```
sudo nano /etc/bpalogin.conf
```

also, when you are using *sudo* with graphical programs, use *gksudo*.
```
gksudo gedit /etc/bpalogin.conf
```
( it has to do with file permissions, explained [here (link)]("http://www.psychocats.net/ubuntu/graphicalsudo"). )

---

### Post by Joeb454 on 2009-06-01
Moved to Testimonials & Experiences :)

Glad to hear your switch was a smooth one, don't hesitate to ask if you have any questions :)

---

### Post by arubislander on 2009-06-01
Welcome aboard!

Great to hear that all went so well.

---

### Post by norgeek on 2009-06-01
congrats :p I still use windows in a dual boot gaming is not for linux yet :(

---

### Post by DBrocks on 2009-06-01
Welcome! :D
Glad that you are enjoying Ubuntu. A few months ago, I jumped into Ubuntu CLI headfirst, when I picked up an old dell 486 from my school for free. I put a 500gb HDD in it, and made a home server, running DNS, DHCP, Postfix, SSH, and tons of other services. (I'm actually rebuilding it over the summer with 2X1TB in RAID 1 as a file sharing/mythtv box ^^). I had no GUI to learn with, and that was fine with me. Then when I decided to fully jump into Ubuntu GUI a month or two back, it was awkward for me to have pretty pictures. It was almost like learning a whole new OS. Guess I'll always be a command line monkey :lolflag: I find that Ubuntu has a great learning curve (almost a horizontal learning curve). I still dual-boot into XP for an hour or two a day to game a bit, then I'm back into ubuntu. I'm just happy to hear we have another convertee to the world of Linux. Enjoy!!

---

### Post by Dex73 on 2009-06-01
Glad you like it. I can't remember where I found it but you may think of downloading a pocket handbook for Ubuntu!

---

### Post by HappyFeet on 2009-06-01
> **Dex73 said:**
> Glad you like it. I can't remember where I found it but you may think of downloading a pocket handbook for Ubuntu!

[Free Ubuntu Pocket Guide]("http://www.ubuntupocketguide.com/download_main.html") 

Enjoy.

---

### Post by DrMelon on 2009-06-01
Hooray! Enjoy your stay at the No.1 OS!

---

### Post by Ms_Angel_D on 2009-06-02
Welcome and I'm glad your enjoying your Ubuntu experience. 

I also want to commend you on doing research first. Too many times in these forums we see users whom go jumping in head long without any preparation what-so-ever and then begin complaining because of the problems they have had and blaming Ubuntu for every issue. So Great Job on having the foresight to prepare yourself and your system, and I hope you continue to have fun with your new OS!

---

### Post by indigo_myst on 2009-06-03
Thanks for the well wishes everyone.  :)  I've been having a good ol play and still no real issues.  

I do believe I might grab the ubuntu pocket guide ;)  

I did have to install the IE, but only because I design and update a website, so needed it just for checking.  I am looking at using other applications to replace dreamweaver for the website - as I think it would be good to move away and try complete opensource, but I do have wine installed for those I have to use.  

I think using the terminal and understanding the code will be my biggest learning curve - mind you I was around in the days of DOS so i'm not quivering in fear at the thought of using it.  

Thanks again guys! 

Cheers

---

### Post by logos34 on 2009-06-03
> **indigo_myst said:**
> and so far all has gone well. 


just you wait

no good deed goes unpunished

---

### Post by khelben1979 on 2009-06-03
Welcome to the world of Linux!

---

### Post by Tamlynmac on 2009-06-05
> Ms_Angel_D
I also want to commend you on doing research first. Too many times in these forums we see users whom go jumping in head long without any preparation what-so-ever and then begin complaining because of the problems they have had and blaming Ubuntu for every issue. So Great Job on having the foresight to prepare yourself and your system, and I hope you continue to have fun with your new OS!

+1

Well said and to the point. I believe the adage "If you fail to plan, then you plan to fail" is appropriate here.

By investigating and performing some simple tasks, it's amazing how successful one can be. I have little sympathy for those that expect Ubuntu to be a Windows clone and then complain when it doesn't work. They refuse to spend any time prior to the install learning about the OS and appear shocked when (for what ever reason) it fails. :shock:

Assumption, is often the root of failure.

> indigo_myst

Thank You for sharing your story. It's refreshing (especially in this section of the forum) to read the exploits of a new user that actually investigated and spend time learning about the OS prior to installation.

Please keep us informed as to your progress and I look forward to reading your future posts.

---

