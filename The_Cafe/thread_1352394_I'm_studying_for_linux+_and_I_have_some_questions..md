---
title: "I'm studying for linux+ and I have some questions..."
date: 2009-12-11
forum: The Cafe
---

### Post by ant2ne on 2009-12-11
My process is to take each and every entry from the **_CompTIA Linux+ objectives (2009 Edition) Certification Exam Objectives_**, and create a flash card for each. Then I hit the man pages and google to learn about each concept.

So far I've gone through Domains 1.0 and 2.0 (Installation & configuration, and System Maintenance & Operation) and things are going well. There are only a few things that I can't seem to find information on, or the information I find is not geared towards the Linux+ or is not specific enough. I'm hoping that the knowledgeable users of this forum could help me gain general knowledge, or (even better) Linux+ specific knowledge about these topics.

Below, are the sections that I require help with.

1.10 Troubleshoot boot issues using the following tools
Kernel Options (What? How?)


2.1 Given a scenario, use the following fundamental linux tools, techniques and resources.
I/O redirection (What? How? example? for each of the following)
= 
==
; 
xargs (the man is pretty confusing on this one, a simple exaple would help)

2.1 Given a scenario, use the following fundamental linux tools, techniques and resources.
Processes Management - Signals (What signals? How do the manage processes?)

2.3 Common log files
(What are the purposes to these logs ?)
/var/log/lastlog
/var/log/messages
/var/log/syslog
/var/log/maillog
/var/log/secure
/usr/log

2.4 Conduct and manage backup and restore operations
How to write to media CD / DVD? (What utility or command is Linux+ looking for?)

2.5 Explain the following features and concepts of X11
xorg.conf. (How much detailed knowledge is expected?)
Difference between X11 Server & Client (What?)


I'm certain that when I've created flash cards for the other 3 domains, I will have additional questions. :(

---

### Post by u.b.u.n.t.u on 2009-12-11
Best to do your own homework. At least show more effort than merely typing out questions. Merely rote learning answers is not sufficient for developing troubleshooting skills.

If you are helped with these questions, without at least having your own answers, then perhaps you need to consider some other career path.

---

### Post by toupeiro on 2009-12-11
I concur.  Us doing your work for you isn't helping you at all, and these answers are very basic across distro's.  If you don't have a study environment, I recommend getting a copy of virtualbox and building yourself one.

---

### Post by LowSky on 2009-12-11
> **toupeiro said:**
> I concur.  Us doing your work for you isn't helping you at all, and these answers are very basic across distro's.  If you don't have a study environment, I recommend getting a copy of virtualbox and building yourself one.
Totally agree.

If you can complete the task its easier to explain. Us giving you the answer is helpful how? What if one of us gives you the wrong answer and no one catches it and you fail your exam?

Maybe you should build take a copy of Ubuntu Server Edition and play with it. If you don't have a machine you can commit it to then use a virtual machine. Sun's Virtual box is free and is available for Linux and Windows.

Last thing I want to say is if you don't understand what you teacher is asking for. Ask him questions. You're paying him to teach you this stuff, make every penny count.

---

### Post by NoaHall on 2009-12-11
> **ant2ne said:**
> 

2.3 Common log files
(What are the purposes to these logs ?)
[B]/var/log/lastlog
/var/log/messages
/var/log/syslog
/var/log/maillog
/var/log/secure[/B]
/usr/log

2.4 Conduct and manage backup and restore operations
How to write to media CD / DVD? (What utility or command is Linux+ looking for?)



Guess. It's not hard to figure it out, promise ;) And why not take a look at them if you're stuck?
```
cat /var/log/$LOGFILENAME
```
or
```
gedit /var/log/$LOGFILENAME
```

---

### Post by oldgeekster on 2009-12-11
Creating flash cards seems a poor replacement for simple study IMO.

---

### Post by pricetech on 2009-12-11
The harder you work for it, the better it sticks.

But I'm glad Comp TIA finally updated Linux Plus.  I best get started.

---

### Post by ant2ne on 2009-12-11
WOW I expected more help from users of this forum!

> **u.b.u.n.t.u said:**
> Best to do your own homework. At least show more effort than merely typing out questions. Merely rote learning answers is not sufficient for developing troubleshooting skills.

If you are helped with these questions, without at least having your own answers, That doesn't even make sense. How can I have my own answers if I don't understand the subject matter? > then perhaps you need to consider some other career path. About 2.5 years ago I decided to go back to school to work in computers and networking. I'm already Network+, and A+. I completed my Associates degree program in Computer Networking last June and graduated with a 4.0. I've been working on a very large (2000+ node) and very complex network for over 2 years now. How, did I land this job without graduating? Because my instructor recommended me knowing I was pulling down a 4.0 in a complicated program. 

I've set up about 20 Windows Servers **in a production environment** and 6 linux servers in **a production environment**. My boss is very Windows biased, but I convinced him to set up these linux boxes. All are ubuntu servers. I've got 2 Squid Webcache proxy servers and 2 Moodle servers and 2 VM Host Servers. **I excel at my career path.** 

Unfortunately, both my school's lessons and my work environment favours Windows. In school, all that was offered was an intro to Unix class. Which I did get an A on. Before I landed my job, there were no linux servers on the network. Learning linux has been a challenge, and that is why I turned to these forums. My employer doesn't know linux. My instructors didn't know (much) about linux. Most I've learned has been trial and error and plugging away. But I love linux. I have more fun, and feel more at home in the linux OS. All of my home computers boot linux. (2 desktops, 2 laptops, 1 mac PPC laptop) I even have linux on my xbox and my router (DDWRT). I would like to build my resume so hopefully I can land a job working with linux.

> Creating flash cards seems a poor replacement for simple study IMO.  I did this same technique with A+ and Network+ certification. And I passed both of those. The A+ I passed with over a 90% **I have faith in my technique.** It's not just using the flash cards, but creating the flash cards that is the key.

I've already answered 85% of the exam objectives on my own and there are just a few issues I'm having problems with. I Apologise if the questions that I struggle with are the same things that you may find simple. But I guarantee there are many things that I would find easy that you might not understand. But I hope that I would be more willing to share my knowledge than you seem to be.

Some of you brought up valuable points, like distro specific commands. But I need some place to get this basic information and then expand my knowledge from there.

What would be helpful is someone who has linux+ certification stepped forward and offered study advice and exam tips. proprofs.com was helpful for my network+, but is lacking on my linux+

I'm simply amazed that you all talk a good game of expanding linux and want more support and more representation, but when someone honestly wants to learn more in a professional capacity, you go out of your way to shut them down.

All of you took the time to post responses in a negative way. But only one took the time to actually try to share some knowledge. You remind me of an "old boys club" where you are afraid to share what you know. Or maybe you are afraid to admit that you, as well, do not know.

---

### Post by u.b.u.n.t.u on 2009-12-11
> **ant2ne said:**
> WOW I expected more help from users of this forum!


Doing your homework for you is NOT helping you!

> **ant2ne said:**
> That doesn't even make sense. How can I have my own answers if I don't understand the subject matter?

Read. Take initiative and make an effort. I take it this is part of a recognized curriculum? Well, don't you have a teach or similar?! Problem solving skills are needed when dealing with computers. You need to develop those skills!

> **ant2ne said:**
> About 3 years ago I decided to go back to school to work in computers and networking. I'm already Network+, and A+. I completed my Associates degree program in Computer Networking last June and graduated with a 4.0. I've been working on a very large (2000+ node) and very complex network for over 2 years now.

One needs genuine skills. Also one ought to be able to apply what one has learned to new problems.


> **ant2ne said:**
> How, did I land this job without graduating? Because my instructor recommended me knowing I was pulling down a 4.0 in a complicated program. 

I've set up about 20 Windows Servers **in a production environment** and 6 linux servers in **a production environment**. My boss is very Windows biased, but I convinced him to set up these linux boxes. All are ubuntu servers. I've got 2 Squid Webcache proxy servers and 2 Moodle servers and 2 VM Host Servers. **I excel at my career path.** etc etc etc

A resume is worthless if one cannot apply skills to new problems.


> **ant2ne said:**
> 
I'm simply amazed that you all talk a good game of expanding linux and want more support and more representation, but when someone honestly wants to learn more in a professional capacity, you go out of your way to shut them down.

You are misrepresenting the facts. You do not want to learn so much as you have set homework that you want others to do for you. For which you want to take credit! Plagiarism where I come from that means automatic expulsion from university!

Ok here's the deal. The people that help you, you state on your homework that they helped you. In detail. Full credit where credit is due. Do not pass off other peoples work for your own! Admit that all you did was ask the questions and write down other people's answers. Now that is fair! You want an education, YOU work for it!

> **ant2ne said:**
> All of you took the time to post responses in a negative way. But only one took the time to actually try to share some knowledge. You remind me of an "old boys club" where you are afraid to share what you know. Or maybe you are afraid to admit that you, as well, do not know.

To just give you the answers, when you have shown no attempt whatsoever to do any of this work for yourself, is the furtherest from helping you!

The persons here, including myself, whom you have see fit to criticize are in actual fact helping you by making you stand on your own two feet. You really ought to reflect on that.

---

### Post by fancypiper on 2009-12-11
My method for learning Linux:
I have always been a "learn by doing" person, myself. So, I installed it, used it, broke it and fixed it. Repeat as needed.

I have no "paper" that states my qualifications, just 70 years experience in learning (I do have a paper that says I am a teacher), so I won't comment on your leaning method. Use what works for you.

Handy links:

[Google in a Linux frame of mind]("http://www.google.com/linux")

[Getting the Best Help on Linux Forums](http://www.psychocats.net/ubuntucat/getting-the-best-help-on-linux-forums/)

[Linux is not Windows](http://linux.oneandoneis2.org/LNW.htm)

[New to Ubuntu? Start here](http://ubuntuforums.org/showthread.php?t=801404)

[LINUX: Rute User's Tutorial and Exposition](http://rute.2038bug.com/index.html.gz)
(Install a local copy with **sudo apt-get install rute**)

[Linux Power Tools]("http://linuxdevcenter.com/pub/q/UnixPower")

[The Linux Documentation Project]("http://tldp.org/")

Hard copy book:

Oreilly's [Running Linux]("http://oreilly.com/catalog/9780596002725")

Good luck.

---

### Post by u.b.u.n.t.u on 2009-12-11
fancypiper, excellent post.

---

### Post by Exodist on 2009-12-11
> **ant2ne said:**
> WOW I expected more help from users of this forum!

You must understand where many of us stand on this. WE learned over many years and in most cases taught ourself. Now you wish us to simply supply you with quiz answers so you can take a test and be supposedly more qualified then US HERE... Heck No..  Its a slap in the face. Go learn your damn books..

---

### Post by jollyjollyroger on 2009-12-11
Aye...

Tell that to the youth o' today...

And they won't believe you...

---

### Post by pedja_portugalac on 2009-12-12
> **ant2ne said:**
> WOW I expected more help from users of this forum!
They already helped you putting you on right way. Your fist question, par example, can have so many scenarios it will take to long to explain each of them. There are things you can learn from the manuals but such serious things as troubleshooting broken OS or software demands real life experiences and practices. In my opinion, you need more time "heavy" using linux based OSs and if you do, believe me, you're on the chance of getting into such a trouble you'll learn, the best way, what tools you need and how to do. If you want to speed up this process, as of today start using Debian unstable and good luck to you. 

PS. If it's to hard, try ubuntus lucid alfa 1.   
> All of you took the time to post responses in a negative way. But only one took the time to actually try to share some knowledge. You remind me of an "old boys club" where you are afraid to share what you know. Or maybe you are afraid to admit that you, as well, do not know.
You see now, you don't understand. This is not microsoft or mac "world"! Here we share, we ask when we have to ask, we help each other FOR FREE and we try not to jump stages. Slow down, take a deep breath and try Debian unstable.

---

### Post by jacobs444 on 2009-12-12
if you have a good memory then do a brain dump. I won't post here because it would be considered piracy. but you can find them easy enough.

---

### Post by ant2ne on 2009-12-12
> &#8211;noun
1. 	the unauthorized use or close imitation of the language and thoughts of another author and the representation of them as one's own original work.
2. 	something used and represented in this manner.Asking questions and gaining knowledge is not plagiarism. As long as I'm not passing off someone opinions or work as my own.

> A resume is worthless if one cannot apply skills to new problems. This line stands out to me. How can I gain the skills without gathering the knowledge? I look at a certification not only as a badge on a resume, but also the challenge and path of learning. And when the certification is obtained I can confidently say, "I understand the basics of this field." Otherwise, I'd just pay the $45 for a braindump and cram that.

I'm fascinated how my request for knowledge somehow equates to some one else doing my work. I keep hearing this word "homework" as though this is for a class. This is not. This is something I'm doing on my own. I never in my life thought I'd be on this forum begging for information.

u.b.u.n.t.u., If you could please do me a favour, and stop replying to my thread I'd be grateful. I think that your opinion has been overstated enough. And I frankly am not interested. Anyone else who is of u.b.u.n.t.u. opinion should also refrain from replying. It has been stated, at great length, and I don't need to hear it any more. I'd prefer my thread not be completely ruined of any possibility of getting helpful input.

fancipiper, thanks for those links. I will check them out once I get some coffee in me. I should have mentioned that I have several books. I have the 2004 edition of the _CompTIA Linux+_, O'Reily. I have PC Worlds _Complete Linux Something or other_. I have _Linux Complete_, sybex. I have several Books on Samba, including the O'Reily book. And, _Hacking Ubuntu_ (mostly worthless) and the _Ubuntu Bible_. The problem is that these are for the 2004 or pre 2004, and the questions I've asked are not covered well in those books, and they are not easy to google. I'm not sure how to google "==".

I have got some good PMs from useful individuals. I thank you all for that info. I can only assume that they PMed me so they wouldn't be needlessly attacked.

---

### Post by hessiess on 2009-12-12
> 
Difference between X11 Server & Client (What?)

[http://tronche.com/gui/x/xlib/](http://tronche.com/gui/x/xlib/)

---

### Post by MasterNetra on 2009-12-12
> **ant2ne said:**
> Asking questions and gaining knowledge is not plagiarism. As long as I'm not passing off someone opinions or work as my own.

 This line stands out to me. How can I gain the skills without gathering the knowledge? I look at a certification not only as a badge on a resume, but also the challenge and path of learning. And when the certification is obtained I can confidently say, "I understand the basics of this field." Otherwise, I'd just pay the $45 for a braindump and cram that.

I'm fascinated how my request for knowledge somehow equates to some one else doing my work. I keep hearing this word "homework" as though this is for a class. This is not. This is something I'm doing on my own. I never in my life thought I'd be on this forum begging for information.

u.b.u.n.t.u., If you could please do me a favour, and stop replying to my thread I'd be grateful. I think that your opinion has been overstated enough. And I frankly am not interested. Anyone else who is of u.b.u.n.t.u. opinion should also refrain from replying. It has been stated, at great length, and I don't need to hear it any more. I'd prefer my thread not be completely ruined of any possibility of getting helpful input.

fancipiper, thanks for those links. I will check them out once I get some coffee in me. I should have mentioned that I have several books. I have the 2004 edition of the _CompTIA Linux+_, O'Reily. I have PC Worlds _Complete Linux Something or other_. I have _Linux Complete_, sybex. I have several Books on Samba, including the O'Reily book. And, _Hacking Ubuntu_ (mostly worthless) and the _Ubuntu Bible_. The problem is that these are for the 2004 or pre 2004, and the questions I've asked are not covered well in those books, and they are not easy to google. I'm not sure how to google "==".

I have got some good PMs from useful individuals. I thank you all for that info. I can only assume that they PMed me so they wouldn't be needlessly attacked.

[http://manuals.makeuseof.com.s3.amazonaws.com/MakeUseOf.com_-_Ubuntu_Karmic_Koala.pdf](http://manuals.makeuseof.com.s3.amazonaws.com/MakeUseOf.com_-_Ubuntu_Karmic_Koala.pdf) (courtesy of Google) 

Its Ubuntu Karmic Koala Bible. Idk if that will help any. Google is your friend.

---

### Post by fromthehill on 2009-12-12
> 
I've set up about 20 Windows Servers **in a production environment** and 6 linux servers in **a production environment**. My boss is very Windows biased, but I convinced him to set up these linux boxes. All are ubuntu servers. I've got 2 Squid Webcache proxy servers and 2 Moodle servers and 2 VM Host Servers. **I excel at my career path.** 

you can set up a linux server but you cannot open a log file?:)

> 
 I did this same technique with A+ and Network+ certification. And I passed both of those. The A+ I passed with over a 90% **I have faith in my technique.** It's not just using the flash cards, but creating the flash cards that is the key.

knowing the answers doesn't mean you understand them

> 
I've already answered 85% of the exam objectives on my own and there are just a few issues I'm having problems with. I Apologise if the questions that I struggle with are the same things that you may find simple. But I guarantee there are many things that I would find easy that you might not understand. But I hope that I would be more willing to share my knowledge than you seem to be.

all the answers are a single google search away
if you don't know how to find this on the web you're going to have a really hard time when you have to do something that isn't exactly documented in your books.

I can also give you the site that gives you all the answers

> 
Some of you brought up valuable points, like distro specific commands. But I need some place to get this basic information and then expand my knowledge from there.

[www.google.com](www.google.com)
linux <thing you wanna do> [console/gui]

> 
All of you took the time to post responses in a negative way. But only one took the time to actually try to share some knowledge. You remind me of an "old boys club" where you are afraid to share what you know. Or maybe you are afraid to admit that you, as well, do not know.
your answers are really easy to find. especially for _***[I]"individuals with a minimum of six to 12 months of practical Linux experience"***[/I]_(this is quoted from the linux+ certifcation description). 
what you need to do:
[LIST]
[*]google the question (first result already gives you the answer)
[*]open the file you need to know about
[*]type "man <file/program>" in your linux box
[*]look at the [linux+ guide]("http://www.mcmcse.com/comptia/linux/studyguide.shtml")
[/LIST]
and shouldn't all the things you need to know be in your [_training materials_]("http://www.comptia.org/certifications/testprep.aspx")

---

### Post by toupeiro on 2009-12-12
> **Exodist said:**
> You must understand where many of us stand on this. WE learned over many years and in most cases taught ourself. Now you wish us to simply supply you with quiz answers so you can take a test and be supposedly more qualified then US HERE... Heck No..  Its a slap in the face. Go learn your damn books..

This has a lot of merit.  We don't discourage you taking the path to get linux plus certified, but we certainly won't certify you.  If you don't even have the motivation to learn this stuff on your own, you're going to have a hell of a time supporting diverse environments.

---

### Post by koenn on 2009-12-12
I agree with all of the above. You're basically asking us to do your home work and make you pass this cerification, without minimal effort on your side. It's also pretty hard to imagine you learned to setup Linux servers while you don't know how to use google or wikipedia to find the info you need.  Sounds like a clueless Next, Next, Next, Finish install. 

Assuming you really want to learn but don't know where to start or what to look for, here are a few pointers. If it's not Linux+ specific enough, ask yourself: do you want to know linux system administration, or do you just want a piece of paper that says you past a test ? 



1.10 Troubleshoot boot issues using the following tools
Kernel Options (What? How?)

This is about passing options to the kernel at boot time. You can see this in action when you boot an installer (eg Knoppix, Ubuntu mini or alternate, ... : hit F2, ... for help). It also works on installed kernels, eg through grub. Have a look at it, it 'll give you some keywords to google with. 



2.1 Given a scenario, use the following fundamental linux tools, techniques and resources.
I/O redirection (What? How? example? for each of the following)
=
==
;

xargs (the man is pretty confusing on this one, a simple exaple would help)
"man xargs" + any tutorial on any of the common shells, eg bash : , and look for Redirection.
or just google it: [http://www.google.be/search?q=bash+redirection](http://www.google.be/search?q=bash+redirection)
or wikipedia: [http://en.wikipedia.org/wiki/Redirection_(computing](http://en.wikipedia.org/wiki/Redirection_(computing))



2.1 Given a scenario, use the following fundamental linux tools, techniques and resources.
Processes Management - Signals (What signals? How do the manage processes?)
```
man ps
man signal
```


2.3 Common log files
(What are the purposes to these logs ?)

wat NoaHall said.
Also, any linux system administration guide (google it) will have a section on logs.



2.4 Conduct and manage backup and restore operations
How to write to media CD / DVD? (What utility or command is Linux+ looking for?)

[http://www.google.com/search?q=linux+write+cd](http://www.google.com/search?q=linux+write+cd)



2.5 Explain the following features and concepts of X11
xorg.conf. (How much detailed knowledge is expected?)
Difference between X11 Server & Client (What?)

X11 is designd according to a "client-server architecture". 
[http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)

for conf files, 'man 5' usually works:
```
man 5 xorg.conf
```

---

### Post by ant2ne on 2009-12-12
There seems to be this consensus that either I should start off knowing it all, or I should give up and go home and not ask the questions.

fromthehill, Like I said, I don't need any more of this opinion.
> what you need to do:
    * google the question (first result already gives you the answer)
    * open the file you need to know about
    * type "man <file/program>" in your linux box
 Please re-read my second sentence where I say, "Then I hit the man pages and google to learn about each concept." I do thank you for the other links! I'm adding them to my list of resources.

Thanks koenn for the helpful info. Although, like I stated above, I could do without the opinion.

> **koenn said:**
> If it's not Linux+ specific enough, ask yourself: do you want to know linux system administration, or do you just want a piece of paper that says you past a test ? I think I answered this, at great length, above.

> 1.10 Troubleshoot boot issues using the following tools
Kernel Options (What? How?)

This is about passing options to the kernel at boot time. You can see this in action when you boot an installer (eg Knoppix, Ubuntu mini or alternate, ... : hit F2, ... for help). It also works on installed kernels, eg through grub. Have a look at it, it 'll give you some keywords to google with.Ahh thanks. I have had to do the F2 thing before, but I've never seen it referred to as "Kernel Options". I now have a staging point for further research.

> 2.1 Given a scenario, use the following fundamental linux tools, techniques and resources.
I/O redirection (What? How? example? for each of the following)
=
==
;

xargs (the man is pretty confusing on this one, a simple exaple would help)
"man xargs" + any tutorial on any of the common shells, eg bash : , and look for Redirection.
or just google it: [http://www.google.be/search?q=bash+redirection](http://www.google.be/search?q=bash+redirection)
or wikipedia: [http://en.wikipedia.org/wiki/Redirection_(computing](http://en.wikipedia.org/wiki/Redirection_(computing))Like I said, "the man is pretty confusing on this one, a simple example would help." And then you direct me to the man. *sigh* I read the man, and it is still kind of confusing. Fortunately, someone PMed me with some good info on xargs. I think I have a basic grasp. I'd still like to see an example other than "ls | xargs rm". Someone also PMed me with the = and == thing. Perhaps this isn't actual redirection, but variable value assigning (the =) and value comparison (the ==). The reason I couldn't find any good data on the redirection of = and == is that there isn't any. The Objective List is just poorly written. :-( It is also determined that ; isn't a redirection syntax, but a method to put more than one command on a given line of shell. Thanks, you know who you are ;-)

> 2.3 Common log files
(What are the purposes to these logs ?)Actually, the ones I specified are new in the 2009 exam. My 2004 book (and most of google) doesn't discuss them too much. I will continue to google though.

> 2.1 Given a scenario, use the following fundamental linux tools, techniques and resources.
Processes Management - Signals (What signals? How do the manage processes?)
```
man ps
man signal
```Hrmph the objectives list said signals not signal. I didn't know if this was a different command, or if there were some other 'signals' that the objectives list was hinting at and I'd never heard of. I will research the command signal. THANKS

> 
2.4 Conduct and manage backup and restore operations
How to write to media CD / DVD? (What utility or command is Linux+ looking for?)

[http://www.google.com/search?q=linux+write+cd](http://www.google.com/search?q=linux+write+cd)
 Sorry, I gotta argue this one. I did say "what utility or command is Linux+ looking for?" I guess this question needs to be answered by someone whith linux+ background. The google link you supplied isn't particularly helpful at pointing me to what utility I should study. I've written many CDs in my day. And alot of them from linux. A time or 2 from the command line as well. But I think for this one I need to know which command CompTIA is looking for.

> 
2.5 Explain the following features and concepts of X11
xorg.conf. (How much detailed knowledge is expected?)
Difference between X11 Server & Client (What?)
X11 is designd according to a "client-server architecture".I understand the architecture. I'm more confused on how one can discus the differences seeing as how they are completely different. I guess the problem is, that I don't understand what the CompTIA Objective list is asking. I think I'm just going to trash the specifics on this one and fall back on what I know.

> 
for conf files, 'man 5' usually works:
```
man 5 xorg.conf
```hey, thanks. I do recall reading something about the different levels of man. I had forgotten that. Thanks for that tidbit.

I've modified my xorg.conf on several occasions. And there is alot of stuff in there. I'm kind of wondering in how much detail CompTIA is expecting.

---

### Post by koenn on 2009-12-12
> **ant2ne said:**
> Thanks koenn for the helpful info. Although, like I stated above, I could do without the opinion.
well, the info comes with opinion.

---

### Post by kingbilly on 2009-12-12
Wow! For a Community Cafe thread you sure got ripped apart.  I figured since it was outside the Main Support Forums and not distracting other members from support questions, someone could have at least thrown you a link. At the very *least* they could have just ignored you.  Instead there are these nice responses:

> Now you wish **us** to simply supply you with quiz answers so you can take a test and be supposedly more qualified then US HERE...

Who is this "us" they speak of?  Not me, I never thought your intention was to be supposedly more qualified than me. Group-think can be so cruel.  Guess you got more "help" (Howto: Study, Howto: Ask Questions) than you asked for. Next time try mentioning you hate Microsoft, and leave out that you are taking a test.

Good Luck, I hope some of those PM's other members sent you are pointing you in the right direction - not spoon feeding, nor Google.

---

### Post by cariboo on 2009-12-12
The reason for some of the responses id because it is against forum policy to answer homework questions. If the op had done a search of the forums, most of his question would have been answered without him needing to ask them.

---

### Post by kingbilly on 2009-12-12
Great post, wish it was the first and only reply!

---

### Post by ant2ne on 2009-12-13
> figured since it was outside the Main Support Forums and not distracting other members from support questions, someone could have at least thrown you a link. That is kind of what I thought. That is why I posted in the cafe section. I thought if others can post things like What TV show to watch [http://ubuntuforums.org/showthread.php?t=1353365]("http://ubuntuforums.org/showthread.php?t=1353365") I maight be able to ask a few qestions. Thanks for the moral support. I think next time I'll just ask a simple question like "What are these logs used for?" in the general help section, and not mention Linux+ or anything else.

> **cariboo907 said:**
> against forum policy to answer homework questionsThere is that homework word again. This has nothing to do with any class. As I pointed out, I've completed my courses, and I'm perusing the linux+ on my own. I never asked for specific answers. I asked for information and to be pointed in the right direction to gain knowledge. Trust me, it will never happen again. :(

---

### Post by Frak on 2009-12-13
> **ant2ne said:**
> There is that homework word again. This has nothing to do with any class. As I pointed out, I've completed my courses, and I'm perusing the linux+ on my own. I never asked for specific answers. I asked for information and to be pointed in the right direction to gain knowledge. Trust me, it will never happen again. :(
I was told the same thing when I posted random trivia questions. Frankly, I never understood why it was a big deal in the first place.

---

### Post by Chame_Wizard on 2009-12-13
Self learning is always good.:lolflag:

---

### Post by ant2ne on 2010-04-26
I passed my Comptia linux+ certification today. I can say that with no formal training, and very little help here, I did it on my own.

It was a great learning process for me. And the knowledge gained on the journey of preparation for this exam (just like my A+ and Network+) was the true benefit. Not only do I have a certification of my knowledge, but I have greater and more in depth knowledge of Linux than when I began studying.

I owe much of my learning to my Slackintosh on the iBook and ubuntu iBook projects. You can read about them at [http://blog.computerant.com]("http://blog.computerant.com")  It is true what they say, if you want to learn linux, use slack.

> so you can take a test and be supposedly more qualified then US HEREBy your words, I am now more qualified than you. By CompTIA's words, I can now prove my qualifications. Can you?

Because of some of the miserly attitudes on this thread, It will be a goal of mine, to share any of my knowledge of Linux to anyone who wants to learn. I'm also contemplating starting a lug in my area or finding some other way to contribute to the community.

Associates degree in Computer Networking (with a 4.0 gpa), A+, Network+, Linux+, and now I'm dusting off that Security+ book.

:guitar:

---

