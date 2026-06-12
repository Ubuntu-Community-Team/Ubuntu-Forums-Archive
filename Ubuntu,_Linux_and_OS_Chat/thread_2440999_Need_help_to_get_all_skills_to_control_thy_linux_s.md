---
title: "Need help to get all skills to control thy linux system, write software, deb packages"
date: 2020-04-17
forum: Ubuntu, Linux and OS Chat
---

### Post by getting-power-or-powder on 2020-04-17
Hello, i get started. I need help with the library, knowladges, video and books. who can help? I have saw on rezults in google a lot of information, so decided ask here and want to get professional suggest. 

I want know all about linux. 
- how to create a core and architecture which from 0 string of code uses all library and output all data on the screen, desctop for users.
- how to write application and upload to ubuntu market.
- network catch all packages and write little games for multy players, bussiness app


From what i must to start? 
Which of programming languages i must know?
c, c++, c# 
What the language uses inside ctrl+alt+t ? terminal ?

Is it here beginners like i am ? Who want to increase skills and knowledges in linux core\ubuntu app\network and discuss in this theme?

---

### Post by slickymaster on 2020-04-17
Not a support request

*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by getting-power-or-powder on 2020-04-17
> **slickymaster said:**
> Not a support request

*Thread moved to **Ubuntu, Linux and OS Chat**.*

Thank you.

---

### Post by TheFu on 2020-04-17
This is a huge question.  Best to start smaller and eat a few bites every day.  Most people don't have the patience or background to jump into OS programming for something new.  

If you don't have any Unix experience already, start by getting end-user desktop experience.  When there is a problem, fix it. When there is something you don't know how to do, learn how to do that thing.  Do that for a month, though really it will be a lifetime.

Ubuntu is just a flavor of Linux and Linux is just a variant of Unix-like OSes, so there's really little need to only learn the exact, Ubuntu, method for anything.  90% of Unix-like OSes are the same. Only the system admin parts are slightly different, but they have the same big "ideas" in all of the different OSes.

I've been a programming since the mid-1980s, but never needed to know how to create a debian package. I've coded in about 30 different languages on over 20 different platforms.  There isn't just 1 language that gets used over all others today, but in general, if you want to learn to be a programmer and be able to create programs for almost any platform, then python should be the first language you learn.  Some more ideas about learning to program: [https://blog.jdpfu.com/2011/10/19/how-to-learn-to-program](https://blog.jdpfu.com/2011/10/19/how-to-learn-to-program)  Basically, learn python first, then C second, then get a job.  I see little reason to learn C#.

You probably also need to learn some system admin skills.  Here's a book for that: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  To be a good admin, you need to script a little. That will be in bash, python, awk, golang and perhaps a little perl or ruby.  Popular admin skills I saw in a job ad today were all about cloud deployments using AWS and GC with Kubernetes and Terraform.  These all use virtualization and containers, which would be something to learn AFTER you get the simple OS admin work down.

You are not the first person asking to learn about Linux: [https://blog.jdpfu.com/2014/12/28/learning-linux](https://blog.jdpfu.com/2014/12/28/learning-linux)

Within programming areas, there are specialists.
Within administration areas, there are specialists.
As a beginner, you really need to learn the general stuff before something else forces you to specialize.  Everyone becomes a specialist at something. That's how we get paid.

If you want to be an Admin, then a Linux certification of some sort might be useful.  Which would depend on the industry you want and where you will work in the world.  For example, financial industries and companies in the USA want RedHat certs.  Outside the USA, outside financial companies, the LPI certs are fine.  1 Cert alone isn't really all that good. Plan on getting 2-4 ... you'll want the "Architect" cert to have the most control, input, and earnings.

You'll also need to understand networking, but probably don't need any cert for that.  I've met lots of people getting Cisco Certs. Never understood why. Sure, the information is useful, but if you don't have a love for networking, then don't bother.

I have ZERO certs.  The world was different when I was starting out. My gray beard lets me claim all sorts of expertise at this point in my career.

Nobody follows the same path to a job as anyone else.  The main thing is to spend as much time daily doing stuff on Linux.  Perhaps 2 hrs learning programming and 2 hrs learning admin stuff, then the rest just screwing around with "what if" tasks.  Some examples: setup a printer for the network. Allow remote access over ssh with ssh-keys only, never passwords.  Setup a VPN.  Setup an apache web server and an nginx web server.  Learn about storage - zfs, lvm, and file systems.  Setup daily, automatic, incremental backups <--- that should be first.

You get the idea. Lots to do.  
Here's what I did yesterday morning:  [https://ubuntuforums.org/showthread.php?t=2438654&p=13947525#post13947525](https://ubuntuforums.org/showthread.php?t=2438654&p=13947525#post13947525)

---

### Post by CorporateMonkey on 2020-04-18
That is very nice reply from TheFu. Yes I agree that Python is probably the best choice for 1st language.

---

### Post by grahammechanical on 2020-04-18
I suggest that you also gain an understanding of the software licenses that Linux programs and applications are released under. Look up Free and Open Source Software (F.O.S.S) and Open Source Software.

Whilst it is true that most Linux software including Ubuntu is free to download and install it is still covered by a software license. Here is a common license.

[https://www.gnu.org/licenses/gpl-3.0.en.html](https://www.gnu.org/licenses/gpl-3.0.en.html)

Regards

---

### Post by TheFu on 2020-04-18
SW licenses are absolutely critical for every programmer to understand.  Even with your own code, should it ever be shared anywhere, the license selected really does matter more than most programmers understand.  Choose the wrong license or use someone else's code released under the wrong license and you are screwed.
i was lucky, only because most of my early professional coding was covered by itar regulations that are still effective today, so licenses didn't matter. Federal laws do.  My next job was completely different and we used GPL code like crazy, so being cautious about mixing different licenses was very important.

SW licenses are critical to understand.

---

### Post by Skaperen on 2020-04-18
just start by using Linux for all your uses that don't already require special programs that don't have Linux versions.  just install it and start using it.  this will get you started,  what you described is about 7 to 9 years of experience for the average techie and impossible for the average business manager.  you need to *chew* on smaller bites.

---

