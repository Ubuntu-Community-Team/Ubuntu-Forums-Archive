---
title: "What is something you wish you knew about Ubuntu when you first started using it?"
date: 2019-05-08
forum: Ubuntu, Linux and OS Chat
---

### Post by jsmt-media on 2019-05-08
I am new to ubuntu and looking for friendly advice. What's something you learned with experience that you wish you knew about ubuntu when just starting out?

---

### Post by deadflowr on 2019-05-08
*Thread moved to **Ubuntu, Linux and OS Chat** *

---

### Post by TheFu on 2019-05-08
> **jsmt-media said:**
> I am new to ubuntu and looking for friendly advice. What's something you learned with experience that you wish you knew about ubuntu when just starting out?

90% of Ubuntu is Unix.  $1 Unix books for shell stuff are great.
95% of all Linux is the same as Ubuntu, from the shell.  If you learn the shell methods, you don't have to re-re-re-re-relearn GUIs every few years when some team decides to swap out your favorite GUI for something else.

Don't get hung up on "Ubuntu" It is just a flavor of Linux. The GUIs can be swapped out, as you like, in about 3-5 minutes.  I've chosen to use a very simple GUI to avoid as many of the bloated changes that the "official" Ubuntu flavors keep picking.  To me, functionality matters, not eye candy.  Everyone has a different opinion about this, so YOUR correct answer is 100% fine, kewl, great.  It is YOUR computer. Make it your own.

80% of the power from computers comes through automation, not point-n-click. Unix automation doesn't use any GUI. This means to get the most from a computer, learn to script, just a little, so tasks can be automated, batched, run daily, weekly, as you like.

But, if you plan to be an end-user, not a power-user, with Linux, then you can point-n-click to do most things that other OSes can do. It will just take longer and not be 100% repeatable. I still use tiny scripts that I wrote in the early 1990s that still work.  Every time you solve a little problem, make a script, put it into your ~/bin/ directory and you'll have it forever, including the next time you need it or something very similar.
[B]
And the most important thing - daily, automatic, versioned, backups are mandatory.[/B] This is more important than anything else above.

---

### Post by VMC on 2019-05-09
> **jsmt-media said:**
> I am new to ubuntu and looking for friendly advice. What's something you learned with experience that you wish you knew about ubuntu when just starting out?
Interesting statement. If your new, then there is nothing you should have known before starting out. One always has to start from some point. 
As TheFu stated rely on commands and how to make them work for you. 

I started out with Linux with a long history in Unity, so "vi" was second nature. In Unix we had "ed" before "vi" and "sed" and a few other commands. I do use some gui or create my own.
Everything you need is just a google away, books, YouTube(which I personally con't like.hate the music), forums. Many forums. Get second, third views of the same topic.

---

### Post by mastablasta on 2019-05-09
i wish i knew more about permissions. they still seem a bit confusing to me. this is likely because English is not my first language.

---

### Post by TheFu on 2019-05-09
> **mastablasta said:**
> i wish i knew more about permissions. they still seem a bit confusing to me. this is likely because English is not my first language.

Can't believe I didn't mention that.  Unix permissions are the cornerstone for all Unix/Linux security.  

Learning them will save hours, days, weeks, months, of frustration.  Work through a tutorial, should take about 45 min.  Then open 3 terminals, create 3 new userids, put them into 2 shared unix groups and play around with every possible combination of permissions, groups, and NOT being a member of the group.

---

### Post by oldrocker99 on 2019-05-09
The most important thing for new Ubuntu users is to ask questions right here, and it saved my hash more than once in the first year or two.

Look for the problem, to see if anyone has a solution. Look for [SOLVED] threads.

And if you can't find that problem, by all means ask a question. We all are benevolent volunteers, and I for one love helping anyone with a problem I can solve, or make easier.

---

### Post by crip720 on 2019-05-15
Learning that a lot of other newbies had questions and most of them can be found by using google, then I can come here or to another forum, to maybe explain the answer better or adjust it for my setup.

---

### Post by rbmorse on 2019-05-15
You will find a great resource in the "New to Ubuntu" section on this forum. The search function works great (hint: set the time threshold to three months or so) and the people there are expecting "new user" questions and issues.

---

### Post by drvshrm on 2019-05-15
Ubuntu is Debian based Linux platform, I think this is the first thing you should know. Before considering any Linux to use, you should first decide which repository system you want to use. RPM and Debian based systems are commonly used ones.

---

### Post by Claus7 on 2019-05-16
Hello,

> **VMC said:**
> Interesting statement. If your new, then there is nothing you should have known before starting out. One always has to start from some point. 


I agree in general, so now that you have started out the ps ux command in order to see active processes and then the kill -9 xxx, in order to stop an annoying application refusing to close can come up really handy.

edit: and startx, when there are those days, that you are tweaking your system, and no gui shows up after some... overtweaking!

Regards!

---

### Post by ClickTek on 2019-05-16
I would have to say more about the "flavors" -- it was a whole new world back when I discovered the different DE's.

---

### Post by SeijiSensei on 2019-05-16
As an experienced Linux user, I'd have to say the ever-changing methods for managing client-side domain name resolution have been the most annoying feature so far.  This isn't a problem that most ordinary users will encounter.

It wouldn't have kept me from using Ubuntu instead of Fedora or some other Linux flavor though.  Even though I use KDE and Kubuntu rather than the default interface, I still find Ubuntu easy to install, maintain, and use.

If you're shopping around for a Linux distribution, one option is to install [VirtualBox]("https://www.virtualbox.org/") and then install the various Linux options as virtual machines.  Going this route means you don't even need to burn DVDs or write USB devices. You just need to point to the distribution's ISO image during installation.  VirtualBox has some limitations in advanced areas like video performance, but it's a quick way to try out multiple distros.

---

