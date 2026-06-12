---
title: "Question about ease of program installation"
date: 2005-10-28
forum: The Cafe
---

### Post by brutaldrummer on 2005-10-28
I'm confused as to why linux doesnt have a standard installer to install programs that you would download off the internet. I know synaptic installs, but can you download a file from the internet and extract it just like you would in windows, and then have something like an exe file?

I think one thing that windows has over linux is the ability to cater to people who are not familiar with computers and operating systems. They make it extremely easy to install and uninstall programs. I just think that if linux wants to truly compete with windows on a user level everything is gonna have to be extremely easy to install. No command line stuff.

---

### Post by 23meg on 2005-10-28
Take a look at this document and let us know if it changes your mind:

[http://www.psychocats.net/essays/winuxinstall.php](http://www.psychocats.net/essays/winuxinstall.php)

---

### Post by aysiu on 2005-10-28
You may also want to read [If you have ever wondered why Linux lacks something like an exe](http://www.ubuntuforums.org/showthread.php?t=54227)

---

### Post by brutaldrummer on 2005-10-28
Ok so I read the articles. Can someone post a very very very easy to follow guide on how to install programs then? I'm a gamer and to me linux is almost worthless to me unless I can play games on it. So what do I need to to play games, for instance currently I would like to play battlefield 1942 on my linux machine. Can someone help me out?

---

### Post by aysiu on 2005-10-28
Okay, so you don't really care about installing programs. You just want to play games? So why are you interested in Linux? Linux is notoriously not a set of gaming OSes. No one says, "Hey, I want to switch to Linux for the games." Okay, I did... but I'm not a serious gamer. My games are Pioneers, Gnometris, and Supertux.

If you're serious about games, and that's really important to you, stick with Windows, dual boot, or learn to figure out Cedega. This link may help. I'm not sure it will, though:

[http://www.ubuntuforums.org/showthread.php?t=15476&highlight=battlefield+1942](http://www.ubuntuforums.org/showthread.php?t=15476&highlight=battlefield+1942)

Linux may, in fact, be useless to you. It's not for everybody.

---

### Post by 23meg on 2005-10-28
That being said, you may also be wondering what native Linux games there are. Here are two good resources:

[http://www.ubuntuforums.org/showthread.php?t=5153](http://www.ubuntuforums.org/showthread.php?t=5153) 
[http://happypenguin.org/](http://happypenguin.org/)

---

### Post by brutaldrummer on 2005-10-28
[QUOTE=aysiu]Okay, so you don't really care about installing programs. You just want to play games? So why are you interested in Linux? Linux is notoriously not a set of gaming OSes. No one says, "Hey, I want to switch to Linux for the games." Okay, I did... but I'm not a serious gamer. My games are Pioneers, Gnometris, and Supertux.

If you're serious about games, and that's really important to you, stick with Windows, dual boot, or learn to figure out Cedega. This link may help. I'm not sure it will, though:

[http://www.ubuntuforums.org/showthread.php?t=15476&highlight=battlefield+1942](http://www.ubuntuforums.org/showthread.php?t=15476&highlight=battlefield+1942)

Linux may, in fact, be useless to you. It's not for everybody.[/QUOTE]

I did not say "I don't care about installing programs". I just want to play games as well. I'm also a studio engineer and a web developer..... BUT I feel that if there is to be an alternative to windows that people are actually going to be interested in, and be interested in replacing windows. It'd better be able to do everything windows can do. Also new users who come into linux and all they have heard is "Linux is way better than windows!" from tons of people, they expect that linux is going to be way better than windows, not only with stability and security, but also with useability and EASE. So far ubuntu is the best and easiest distro I've played with. I personally would like to spread the word about it. I'm probably going to learn how to install using the terminal anyhow, but it would be nice if there were an easier route OR if there was a better tutorial in the "help" dialog. If there is one I cannot find it.

---

### Post by Jengu on 2005-10-28
Short version: There is no cross-distro easy way of installing applications.

Long version: For a long time it looked like things would converge around rpm as a standard, but Ubuntu breaks that trend shamelessly. There are a few attempts to make a standard for distributing desktop software, like autopackage.org.

In my opinion, linux lacks it and needs it. 23meg's link is a poor argument. Centralized repositories simply put a massive burden on distribution maintainers compared to letting software makers distribute their software. The link tries to make it sound like typing the name of the software into google, finding the installer, downloading it, and running it is a major chore. Compared to synaptic, it is. But synaptic doesn't get you the latest version. It gets you the latest version that the packagers of your distribution have hobbled together. Which often is not the version you want. A better comparison would be the easy windows installer versus downloading the source for the app, decompressing it, compiling and installing it from the command line, getting errors, searching for packages for the dependencies, maybe finding those, compiling them from source...

People need to stop apologizing for linux distributions having to repackage every single piece of software that comes out. It's stupid.

---

### Post by aysiu on 2005-10-28
Jengu, you're making a lot of assumptions, and frankly you're insulting me. That link you're talking about--I wrote it. I think it's very evenly balanced, as I admit that it's easier to install a lot of applications through Synaptic but concede that if you don't use Synaptic, it's a lot more difficult. You're assuming, though, that everyone wants the absolute cutting edge version of the software she uses. That assumption is faulty for most users I know. I still see plenty of people in my office (Windows users) using Adobe Acrobat 6.0, Firefox 0.9, and Thunderbird 0.7, despite having administrative privileges on their computers--and their software needs are not usually so sophisticated that what they would have to compile apps from source (if they were using Linux).

Synaptic is wonderful for everyday users who don't have sophisticated needs, especially since you can update your applications all at once with one command instead of having to re-download installers for each application you have and go through the set-up one by one with each one (which is why I suspect many people don't keep their applications up-to-date in the first place).

Is Synaptic the solution to everything for everyone? No. Did I say it was? No. You're fighting a straw man because you're assuming I'm making an argument I was not--that Synaptic can solve all your program installation needs. I never said or implied that.

[quote=Jengu]The link tries to make it sound like typing the name of the software into google, finding the installer, downloading it, and running it is a major chore. Compared to synaptic, it is.[/quote] So you're agreeing with the article, because really that's all I was trying to say.

> But synaptic doesn't get you the latest version. It gets you the latest version that the packagers of your distribution have hobbled together. Which often is not the version you want. See, this is where you're making faulty assumptions. Who's "you"? You is Jengu. Maybe *you* is Brutaldrummer, too--I don't know, but depending on the repositories, you usually get a fairly stable, up-to-date version. If you want bleeding edge, there are backports repositories. These are two separate issues, and you're confusing them. One is ease of software installation. One is sophisticated needs (obscure software or bleeding edge versions). My whole point was all these dumb arguments that software is always difficult to install in Linux, which we know is not true. Can it be? Yes. Is it always? Not even most of the time, depending on the kinds of programs you want.

To Brutaldrummer, it sounds as if someone was misrepresenting Linux to you. It's probably best if you read [Is Ubuntu for You?](http://www.ubuntuforums.org/showthread.php?t=63315). I wrote it specifically for people who may have been misinformed about Linux by their Linux zealot friends. Linux is not a replacement for Windows, and it is not the be-all and end-all of operating systems. It's excellent for some things for many people.

---

### Post by brutaldrummer on 2005-10-28
[QUOTE=aysiu]Jengu, you're making a lot of assumptions, and frankly you're insulting me. That link you're talking about--I wrote it. I think it's very evenly balanced, as I admit that it's easier to install a lot of applications through Synaptic but concede that if you don't use Synaptic, it's a lot more difficult. You're assuming, though, that everyone wants the absolute cutting edge version of the software she uses. That assumption is faulty for most users I know. I still see plenty of people in my office (Windows users) using Adobe Acrobat 6.0, Firefox 0.9, and Thunderbird 0.7, despite having administrative privileges on their computers--and their software needs are not usually so sophisticated that what they would have to compile apps from source (if they were using Linux).

Synaptic is wonderful for everyday users who don't have sophisticated needs, especially since you can update your applications all at once with one command instead of having to re-download installers for each application you have and go through the set-up one by one with each one (which is why I suspect many people don't keep their applications up-to-date in the first place).

Is Synaptic the solution to everything for everyone? No. Did I say it was? No. You're fighting a straw man because you're assuming I'm making an argument I was not--that Synaptic can solve all your program installation needs. I never said or implied that.

 So you're agreeing with the article, because really that's all I was trying to say.

 See, this is where you're making faulty assumptions. Who's "you"? You is Jengu. Maybe *you* is Brutaldrummer, too--I don't know, but depending on the repositories, you usually get a fairly stable, up-to-date version. If you want bleeding edge, there are backports repositories. These are two separate issues, and you're confusing them. One is ease of software installation. One is sophisticated needs (obscure software or bleeding edge versions). My whole point was all these dumb arguments that software is always difficult to install in Linux, which we know is not true. Can it be? Yes. Is it always? Not even most of the time, depending on the kinds of programs you want.

To Brutaldrummer, it sounds as if someone was misrepresenting Linux to you. It's probably best if you read [Is Ubuntu for You?](http://www.ubuntuforums.org/showthread.php?t=63315). I wrote it specifically for people who may have been misinformed about Linux by their Linux zealot friends. Linux is not a replacement for Windows, and it is not the be-all and end-all of operating systems. It's excellent for some things for many people.[/QUOTE]


I see how you look upon Linux, but I highly doubt you are speaking for all linux users or developers. There are certainly developers and users out there that do want to make linux a replacement for windows, the way the article was written and the way you are representing yourself is as if you are a spokesperson for linux as a whole. Even in the thread that I read people argue your statement which shows me that there are different levels of linux users. I know that a lot of people use linux because it's unique and not just the average person can use it so it makes them feel special. 

The truth is that if linux is to be taken to a higher level it will have to be easier to use. Microsoft has a monopoly on the industry, but if linux becomes easier to use and it is free, or even just way cheaper than windows people are going to switch. Ubuntu is taking linux to that next level and it will only get better. I love to game but another reason why I'm interested in linux is the stability of it. When in a studio recording the last thing you want is your computer to crash and lose all of that valuable information, and the fact that people are paying you by the hour doesnt help much. I know that Macs are a standard in the music industry, but they are also extremely expensive and overpriced IMO, so I'm moving on to the next best thing and that is linux. So far I think it's great other than the lack of information shared on installing programs, not using synaptic.

---

### Post by aysiu on 2005-10-28
I never said Linux will never be a replacement for Windows or that that isn't a worthy goal for Linux. I just said it isn't (as in *currently*) a replacement for Windows. If people gave you the impression you can do everything you did on Windows in Linux and with the same ease and same software, they misled you, and no Linux developer or user is going to disagree. You can't just pop in whatever 1942 game you want and start using it as you did in Windows.

---

### Post by brutaldrummer on 2005-10-28
I didn't expect to be able to pop in a game and play, but at the same time I didn't expect the how to info to be so scarce. Hell I am still new to the linux world and maybe I just don't know where to look for the HOW TO INSTALL LINUX PROGRAMS FOR DUMMIES articles. I'm just stating that from a novice point of view that linux is extremely confusing and finding the right information is difficult.

---

### Post by seethru on 2005-10-28
the howto info isn't scarce if you pay for cedega, unfortunately thats the only option atm that doesn't require a lot of work. At the same time, the guys over at TG deserve the money, and I HIGHLY suggest paying for it. I play BF Vietnam perfectly through Cedega.

---

### Post by brutaldrummer on 2005-10-28
well I was searching through google and I found this 

[http://www.tldp.org/HOWTO/Software-Building-HOWTO.html](http://www.tldp.org/HOWTO/Software-Building-HOWTO.html)

I'm not sure if it applys to ubuntu or not. 

How much does one month of cedega cost? I may have to check it out.

---

### Post by seethru on 2005-10-28
you have to pay for a minimum of 3 months, which totals $15. The $15 entitles you to tech support, and all upgrades which occur while your account is active.

---

### Post by aysiu on 2005-10-28
[QUOTE=brutaldrummer]I didn't expect to be able to pop in a game and play, but at the same time I didn't expect the how to info to be so scarce. Hell I am still new to the linux world and maybe I just don't know where to look for the HOW TO INSTALL LINUX PROGRAMS FOR DUMMIES articles. I'm just stating that from a novice point of view that linux is extremely confusing and finding the right information is difficult.[/QUOTE] My link about Synaptic is the how-to-install-Linux-programs-for-dummies article. Unfortunately, it doesn't work for all programs, especially when you're trying to install a cost-free version of a program you have to pay for in order to use other programs that are not even made for Linux.

Again, if you want to install regular programs (a very vast array, actually), Synaptic will cover most ground. What I was trying to tell you before is that maybe Ubuntu (or Linux in general--I'm not sure which) isn't for you. Linux in general tends to not be very well suited for people who have extremely sophisticated needs and only beginner Linux skills. You probably fall into what a lot of us refer to as "the middle group." Middle group folk aren't best served by Linux right now (maybe in the future... who knows?). The people best served by Linux *right now* are these two groups:

1. People with basic needs (check email, surf the internet, word process, organize pictures, maybe even some light graphic design) and basic means (can point-and-click, copy and paste a few commands).

2. People with any kind of needs but a lot of knowledge/skill/time to learn things. These people may be programmers fluent in several different programming languages. Maybe they already have a background in unix-like systems and aren't afraid of the command-line.

I don't know that much about you, but if you are similar to what I'm about to describe as group #3, you may have a very difficult time in Linux, and I'd suggest you either suck it up or come back later:

3. People who seriously game, do heavy graphic design/web design (especially with Flash), and use relatively obscure but commercial programs that have no Linux equivalent yet want everything to be cost-free and point-and-click in Linux.

It's up to you to decide. Are you more like #1, #2, or #3? Group #1 really just needs Synaptic. Occasionally someone in that group may have to manually install a .deb file. Group #2 won't mind a little ./configure make make install--in fact, they may prefer it.

Unfortunately for group #3, the programs will probably require a little ./configure and such, and they may need Cedega and Crossover Office but may not be willing to pay for it and/or those helper programs may not work entirely with the Windows programs they want to "help."

P.S. I've moved this to Community Chat. It started off being a question about how to install programs, but it's moved away from that now.

---

### Post by brutaldrummer on 2005-10-28
I fall under all of those categories, I actually do all of it, I do the basic stuff. I also do some php programming, and graphic design for webpages, and also flash. I would love to run Nuendo 2.0 on ubuntu for the studio I work in. I also love to play games. So I kind of fall into all of those. I honestly want to replace my windows with linux, and I know it's possible if I just learn linux of course.  I am just stumped at this installing process is all. I did find that article I posted I have not had time to run through it yet. I have been running around all day. I do have to say the community for linux is great,  frustration just takes a hold and I find myself in a posting spree. I guess what I could ask for from experienced people is some great tutorials on installing stuff, and I'll read through them and hopefully come to a good understanding. So I'll just do my best.

---

### Post by aysiu on 2005-10-28
A little frustration is to be expected when you're learning something new. A very quick way to learn stuff is to search for things on this forum with the word HowTo. For example, if you want to know how to install Opera, you'd do a Google search for

*site:ubuntuforums.org howto opera*

Keep asking questions, and people will try to help. If you feel the documentation is inadequate or disorganized, make some of your own (that's what I do) or help contribute to what's there. A lot of "help" out there is just volunteer efforts.

---

### Post by aysiu on 2005-10-29
[QUOTE=brutaldrummer]Hell I am still new to the linux world and maybe I just don't know where to look for the HOW TO INSTALL LINUX PROGRAMS FOR DUMMIES articles. I'm just stating that from a novice point of view that linux is extremely confusing and finding the right information is difficult.[/QUOTE] Okay. Here's a second crack at it: [How to install Linux programs for dummies (Ubuntu style)](http://www.psychocats.net/linux/installingsoftware.php)

---

### Post by crypto178 on 2005-10-29
[QUOTE=brutaldrummer]There are certainly developers and users out there that do want to make linux a replacement for windows[/QUOTE]

It depends on what you consider to be a replacement. ReactOS for instance, (there is a topic about it in this forum) clearly aims to be a replacement. 
Linux has it own evolution and I think that the general stance towards windows is more in the lines of "use what you see fit". 
Most open-source programs are available in the repositories and therefore, very easy to install. For the proprietary stuff (ie. commercial games), the publishers use whatever install method they want, nobody can do much about it.
Are repositories a bad idea because we can't have the latest packages all the time? I'm not the sure the problem lies there. Sure, it annoys me sometimes (I compiled tomboy 0.33 for instance, which came out recently and fixed a very noticeable bug), but I don't think that repositories are to blame because we are not forced to use them. We can still install deb files ont the side.
It would be nice to be able to get (and produce) some debs for the latest stuff in a slightly easier way than now, but I can live without it.
If it really annoys you, I think that there are distributions out there keeping up with the latest versions of most programs.

---

### Post by brutaldrummer on 2005-10-29
[QUOTE=aysiu]Okay. Here's a second crack at it: [How to install Linux programs for dummies (Ubuntu style)](http://www.psychocats.net/linux/installingsoftware.php)[/QUOTE]

Thank link helped me a lot thanks.

---

### Post by aysiu on 2005-10-29
[QUOTE=brutaldrummer]Thank link helped me a lot thanks.[/QUOTE] Thanks for letting me know there was a need. I did a little search around these forums and Googled some other Linux sites and couldn't find anything like that, so I decided to do it myself.

---

