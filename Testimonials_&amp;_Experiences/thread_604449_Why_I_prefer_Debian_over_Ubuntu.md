---
title: "Why I prefer Debian over Ubuntu"
date: 2007-11-06
forum: Testimonials &amp; Experiences
---

### Post by thedonvaughn on 2007-11-06
Morning/Evening/Afternoon all,

Disclaimer: This post means nothing;  I am merely bored and can't sleep.

I have been following Ubuntu since the Breezy days.  Mainly out of curiosity because of their innovations where the desktop lays.  However, I must say up front that I have been a Debian user and admin for approx. 10 years.

The thing about Ubuntu that bothers me the most, and the reason I can't make myself use it as my main desktop; Ubuntu's goal is to be a "Windows alternative" rather than a "UNIX Alternative". 

I believe this whole goal to be wrong and pointless in itself.  

The biggest strength of Linux, at least to those of us who found it in the 90's, is it's power, flexibility, and UNIX-like performance.  This was a philosophy that innovation in an operating system should not be directed toward easy of configuration, dumbing down decisions, and hiding the internals of your system/services.  

This is what preciously Windows has done over the years.  They have focused more on 'easy of use' and 'quick configuration with little options' than on performance.  All in all, hiding the internals of your system and giving the operator less control.

Since Ubuntu is geared as a  "Windows Alternative', it follows the same guidance as Microsoft.  Ease of use and easy configuration is most important.  Bloat and instability seem to be abroad while it yields less power than it's neighboring alternatives. 

 Besides that Ubuntu is free, is it a better OS?  (Ok, I'm not that crazy.  It is definitely better.  It's still based on debian.  Just asking a question to think about :) 

For example, Why is it that most of the Ubuntu community find it important to never touch /etc/X11/xorg.conf?  This is considered a 'bad distro' or a 'bug' if you have to touch the configuration file.  This is wrong and incomplete.  I do not like any distro with goals of dumbing down the power of a service or application.  Linspire, Mint, Mandriva, PCLinuxOS all do this as well.

There is a reason Xorg created the xorg.conf file.  It is meant to be edited, to give the user power over their X server. 
The encouraged path of use should not be to hide the configuration file, but to _LEARN_ how to configure X.  You have just accomplished one of the greatest things about UNIX.  No need for a developer to waste time on a bloated GUI configuration tool, when they could be focused on the internals of their server and applications.
  
Now, I know... I know... "but Xorg 7.3+ is making xorg.conf deprecated."    Fine, this is true.  But leave it up to the upstream developers to decide the direction of their server/service or application.  Why do you want your OS distribution to dumb down this decision for you?  This is merely the point I'm trying to make.

I'd also like to point out, that like Windows, Ubuntu seems to enable every service and user applet under the sun by default.

It's nice to include compiz-fusion and the gnome applets such as tracker, but why have all this stuff turned on by default?  This is just more evidence of direction that I feel should be 'un-learned' from your days of using Windows.

Debian, while having it's community issues as well, definitely proves to be a wiser choice for the reasons I am discussing.  It is extremely powerful, flexible, and can be anything you setup.  I can setup a Debian desktop like Ubuntu's default.  (i.e. anti-aliased fonts, compiz, etc).  I can also setup Debian to be an enterprise worthy server.  This is a _TRUE_ alternative to Windows.  Power vs. Lack of Power.  Innovation vs. Ease of Use.  

To sum up, Ubuntu successfully pursues it's goals and missions with great growth.  However, it's goal and mission is to be a "Windows Alternative" rather than a "UNIX Alternative".  I feel in the end, it's user base will look else where just like they did when they came to Ubuntu to begin with.  The true "Alternative OS" is the one that offers power, that does not hide it's system, and that chooses performance over 'ease of configuration'.

< /end cant sleep rant >
/endrant

---

### Post by scrooge_74 on 2007-11-06
Nice rant, I just got up myself.  Last night I was up late trying to compile my own kernel.  I am a new user compare to you (only about 2 years of use). I started my learning experience with Debian Sarge. After I went with Ubuntu for a good while until the the speed of the changes that are been made started to be too much work for me.  So I went back to Debian. 

Your rant covers about everything I myself feel.  The direction things are taking I don't like.  New users will come to Ubuntu just because of the point and click and nothing else.  Every week there are more new users asking the type of questions they could solve themselves if they took the time to read.

By the time I made my first post I was able to get my PC going from scratch, the new users ask questions in a way you can't understand.

"I want to like log as with Remote Windows, like I go to My computer, like I want to use the other PC"  That is not good in the long run.

The really good things about Ubuntu is the documentation and this forum

---

### Post by OoooMatron on 2007-11-06
The point is to make Ubuntu accessible to non geeks. I have been a solid computer user for a lot of years and struggled to switch to linux in the beginning. At least now i can run and configure ubuntu and put it on friends machines and not have to touch it again.

The point you make I don't find so valid since you can still edit all the same config files in exactly the same way. I always edit my xorg file manually.

Do you have the same complaints regarding Suse then?

Computing is supposed to be intuitive. There is nothing intuitive about having to look up google for an explanation on how to make a config file that makes your network function properly. There is something intuitive about searching for an icon in a control panel and playing with the settings and finding you can actually make it work. rarely do you "discover" things about config files (particularly if the config files arent commented and only contain information relevant to the current setup). Sometimes the converse is true though about config files.

I configure debian for my webbased servers and I could never do it without the guides for me to copy and paste all the right bits. Even with the guides, setting up a fully functional server for email (particualry when it comes to multi user emails on postifx) takes hours and hours and at the end of it I only have the skills to remember what to look up the next time to accomplish the tasks.

Computers are supposed to be tools. i want to maintain the computer for it to do what i want to do, not have it maintain me into insisting i must learn everything to get it up and running.

---

### Post by karellen on 2007-11-06
some people obsessively fail to understand that some (let's not say most) people just want to **use** their computers as easy as possible, to to **something,** not to fiddle with the os. if you want pure unix, go to slackware. I'm sure it will satisfy all your demands, but to pretend that all distros should be as non-intuitive as possible seems a very very narrow way of thinking for me

---

### Post by buellman on 2007-11-06
I don't understand why some ppl think that it always must be as it always was? Whats wrong with a Desktop that just works? I myself would be happy if Linux would be as intuitive to use as maybe OSX. Btw: I use Linux since 6 or 7 years now and I am happy about any new development that allows me to just use my PC than manipulate conf-files.
I can't see any advantage in modifying xorg.conf to just get an external monitor to work if it would be possible to just plug it in and maybe change some settings for screen-resolution in a gui on the fly without restarting X or similar.
Same with the deskbar-applet and tracker: why the hell should I open a cmd type updatdb and locate to find a file which I would find on the fly with the deskbar-applet?

There are ppl out there that really just need their PC to get things done. But maybe it's just the feeling of losing control about what the PC does? But why? You have the advantage of using a simple Gui to get things done and when the Gui fails you have your knowledge to fix things with the cmd. I mean hey... Linux merges the best things of both worlds!

Last point: I think that Ubuntu is one of that distros that really don't bloat things up. When I start after an fresh installation I have about 6 applets in the bar. Not to much or do you use a screen-resolution of 640x480 :-) ? Than I would understand.

Greets. Buellman

---

### Post by ericartman on 2007-11-06
While I understand what your saying.For me it's  cars. I build cars, fast cars. I have all my life, but it is my hobby, I don't drive the car everyday that I play with I only drive it on special occasions, like at a  racetrack. I have a car for everyday use like everybody else. Like everybody else I don't have the time anymore to dedicate to my hobby like I should or want to. So yeah my race car is better in so many ways than my day- to- day car I couldn't list them. But if I HAD to choose one to keep it would be my day to day car. I need that one for family and work. I need Ubuntu to be there everyday to do the mundane tasks of computing, and I don't want to learn x-org. Just as most don't want to learn why the grind in my camshaft is 10 degrees retarded (more midrange) Anytime spent learning x-org is time spent away from my hobby, no thanks. I came to Linux for the stability and security it offered, Ubuntu offers both and so I really like it. Maybe as I get older(!) my hobby will switch to computers, out of necessity, as I am developing arthritis in both hands. It is nice to have so much to learn in something I like to do , just not now, Ubuntu is fine for me and I guess a whole lot of other people. BTW can't sleep either and garage is too darn cold.

Cart

---

### Post by scrooge_74 on 2007-11-06
I myself I am not against things been easy (i do love when I can just click on things).  But it goes so far until things get to easy for a user and the same problems which plague Windows start to appear in Linux.  If users dont educate themself at list a bit they will start to run into security problems.

Point taken not everybody wants to get down and dirty, if a users just needs a desktop Ubuntu is there, but then they should not be asking for complex setups to just be point and click and then complain when it does not happens.

Following the idea of ericartman about cars. I drive myself a day to day family car, but at least I know how to change tires, change the oil, if I heard a strange sound I have a fairly good idea what is about to break (or at least I hope to) and I do understand how things work in an engine and what are those cables sticking out of the engine block are for.

In a sense I am not a full time mechanic, but at least I try to understand my car.  Same concept I apply to my PCs since I got the first one.  I am not a coder, nor an IT person, but I do know the ins and outs of a PC and their OS

---

### Post by Arthur Archnix on 2007-11-06
I jut came by to say thanks. I should have known to stop reading at "I'm doing this because I'm very bored", or some such, so I'm at least partly to blame.

The next time you're bored may I suggest these equally as interesting follow-up topics:

1. Cell phones shouldn't have cameras in them because they were originally designed to call people only. 

2. Self-cleaning ovens only cost more in the long run and make for lazy owners.

3. Hybrid cars are misguided because they are trying to be a "car alternative", but we already have bikes.

All three should make for similarly enjoyable reading.

---

### Post by ericartman on 2007-11-06
Well said Scrooge_74, well said.

Cart

---

### Post by wolfen69 on 2007-11-06
if it werent for a "dumbed down" version of linux, millions of people probably wouldnt be using it. and if alot less people use it, alot less advancements are made. did you know that Dell and Google both contribute to the advancement of linux? without widespread use and interest in linux, these companies wouldnt give 2 carps about it. so what if joe average doesnt wan to use the command line? some people actually have lives and dont care about the inner workings of an OS. but at the same time, they want a stable, secure environment in which to work.

the beauty of linux is there is a distro for everybody. have nothing better to do in life? use LFS/Arch/Slackware. people with jobs and families to raise would be better served with something along the lines of linux mint or sabayon.

ubuntu will only help linux in the long run. as Dell pushes companies to write device drivers, these will be passed along to every other distro to use. is that a bad thing?

from what ive seen in the debian message boards, it seems they are a bit close-minded. too bad, as we all should get along and try and make things better.

---

### Post by rykel on 2007-11-06
While I love the power of the commandline (and is Windows itself not a commandline-based OS at the end of the day... sort of?), we must all not forget that users want "dumbed down" ease of use.

Just like how refridgerators, televisions and ovens are user-friendly.

It is as simple as that.

---

### Post by Arthur Archnix on 2007-11-06
I ran debian lenny for a while, but when I tried to troubleshoot problems using their forums, every second or third search would return one thread called "don't feed the trolls", or something similar, which was a several hundred comment long thread about whether or not to respond to newb questions. 

Now, I realize that we wouldn't have Ubuntu without Debian, so thank God that community exists. But from everything I read on that forum I realized that it wasn't a community I wanted to be a part of. I didn't post a message on their forum telling them anyone this. Why would I? I just came back to Ubuntu.

I'm regretting dignifying this bored meaningless rant with a response, but heck, I'm bored too.

---

### Post by scrooge_74 on 2007-11-06
I also feel you get a lot more help in this forum than in Debian's.  They have a little over 10,000 users, about 100,000 post and at any given time there's about 50 users and most of them are guests.

And if your question is not very interesting it may go unanswer for weeks on end.  I am currently running Etch, but I look for my answers here :D and then I translate them to the "Debian Way".

That forum is more of a developers and power users forum than anything else. At least here we can get dumbed down replies :lolflag:  But I still feel is good to know your way around the command line.

i do vacuum the grill of my refrigerator and clean my oven from time to time :lolflag:

But in the long run Ubuntu is a good thing for Linux since it has attracted a lot more users than i think all of the distros put together.

---

### Post by DrumScum on 2007-11-06
I love both. Coïncidentially I just set up a minimalistic debian install (dwm as windows manager, iceweasel to browse the internet and pan to read news) to see if the debian Kino package works fine (the ubuntu 7.10 version is seriously broken). To my joy it worked perfectly, and a nice side effect was that doing audio/video stuff with tools like lame, mencoder, audacity, ffmpeg... is very snappy on such a minimalistic set-up. So now I just boot into my debian install when I'm up for some audio/video work, and really have a ball at it. Because i want to keep the install clean and tidy I also try to e.g. deal with vim, mounting storage media manually and do my file management at the cli, so I learn that stuff too along the way.

That's what great about GNU/Linux: you can swing either way.

---

### Post by Naan Yaar on 2007-11-06
After having used Unix systems for well over 20 years and Linux since '95, I have a vastly different perspective on this. IMO, computers are a tool to get something done. If it is necessary to learn how to work with XF86Config or xorg.conf in order to set up your X display, so be it. However, if the system (NB. I do not mean the OS in its restrictive sense, but the entire Ubuntu system, including its configuration utilities) is able to take care of these arcane bits intelligently, I am more than happy to use it. I do not see much benefit in exercising my brain cells in learning something that I do not really have to. I really do not understand the real virtue (to me, at least) in learning the intricacies of xorg.conf to change your display settings. Carrying this argument further, one could argue that we should not have an xorg.conf file at all, but should directly dive into the X server code and make changes directly in there; I am sure this is even more educational :).

Having evolved from RedHat to Gentoo to Ubuntu, I really appreciate the fact that things that were previously harder and required manual intervention (kernel recompiles, printcap magic, CUPS tweaking, SANE settings, XF86Config, mount/umount removable media,...) have all become so much easier. The less time I spend doing system maintenance, the more time I have to do something else.

Also, I would argue with those who insist that tweaking configuration files or recompiling the system with the most optimal CFLAGs is the "way to learn Linux." It would be far more educational to pick up a book on X11, Xt, network programming, OS theory, Linux internals, etc.

---

### Post by goodtimetribe on 2007-11-06
The best part of this is that everyone has different learning styles. To me, using an operating system has nothing to do with learning everything about it. I don't know everything about the way my cable company and it's box gets the picture and sound i want, nor do i really care... i've got an idea on some of concepts, but when it comes down to it, i don't think i'm going to invest that much effort into it. It turns on, i flip the channels, i hear and see what i want.

With a tool as immense as an operating system, there's a lot to learn, and perhaps learning to use it better would save me a lot of time and energy in the future, thus an attempt to discover a better method is usually worth the investment, because in my short linux experience, I've learned *nix has many different ways of accomplishing the same tasks.

---

### Post by scrooge_74 on 2007-11-06
> **goodtimetribe said:**
> The best part of this is that everyone has different learning styles. To me, using an operating system has nothing to do with learning everything about it. I don't know everything about the way my cable company and it's box gets the picture and sound i want, nor do i really care... i've got an idea on some of concepts, but when it comes down to it, i don't think i'm going to invest that much effort into it. It turns on, i flip the channels, i hear and see what i want.

With a tool as immense as an operating system, there's a lot to learn, and perhaps learning to use it better would save me a lot of time and energy in the future, thus an attempt to discover a better method is usually worth the investment, because in my short linux experience, I've learned *nix has many different ways of accomplishing the same tasks.

Another reason to learn how to do things is because basically Tech support where I live sucks! big time. It doesn't matter is it to get your Cable Tv, or the Cable modem, heck the phone itself, not to mention PC maintenance.  The average "Tech guy" has no clue how to help you and then you have to wait for it to scale up until they find the only guy in the company who nows how to do things.  That is really sad, but is the way companies are run this days.

So I learned a long time ago how to do my own tech support (for Windows and for Linux)

You should have hear the voice of the phone when I said I needed to have different router because I had Linux installed, or the time I asked to have the router forward a port so I could do things remotely from home.  They were clueless (took like 5 or 6 persons to get me a good answer) :lolflag:

---

### Post by thedonvaughn on 2007-11-06
Well,
as I stated.  Most of the people who disagree with me use responses like "Well what about non-geek people?"  "What about Ubuntu Bug #1?"  etc etc.  "What's wrong with things just working?"

See this is the point.  If you are going to use Linux, you have to learn Linux.  Simple.

I do not care nor want Linux to be the #1 desktop OS.  I hate to break it to you, UNIX is for geeks.  Linux is for geeks.  When you try to make it mainstream, things will go wrong.  Your community is looked at as a bunch of 14 year olds and the "professionals" have a hard time respecting the project.

Why do you want Windows users flooding our user forums, IRC channels, news groups?  Refusing to read the documentation?  Refusing to actually learn Linux and then complain when it's not like their Windows OS.

I work for a corporation that serves 18,000 - 20,000 different Linux servers.  
RHEL, CentOS, and Debian are by far the most popular distributions.  Ubuntu isn't even on the map.   This is the thing that most Ubuntu users do not realize.
In fact, in the professional corporate world, you will be looked down if you advocate Ubuntu.  Advocating Ubuntu is like advocating Windows or like advocating Mac OS X.  Yes, Mac OS X is horrid crap too.   Who wants a shiney kitchen box that is only good for drawing pretty pictures?  Have you ever seen Mac OSX scale nicely?  It's a horrid OS as well.

Anyway, enjoy your spinny 3D cube :)

---

### Post by matthew on 2007-11-06
Debian is wonderful. Ubuntu is wonderful, too. I have had wonderful experiences with several other Linux distros as well and also several of the BSDs.

Why all the grumpiness?

Isn't FOSS about choice? I wouldn't want to force someone to use a Linux distro they didn't like any more than I appreciate people being forced to use some other OS.

Seriously, if you find something in Ubuntu that you don't like and that you don't feel like the community feels is important, then please find a distro you can appreciate.  That's what I would do. Don't feel like you need to troll our forums. Thanks.

---

### Post by Arthur Archnix on 2007-11-06
> I do not care nor want Linux to be the #1 desktop OS.  I hate to break it to you, UNIX is for geeks.  Linux is for geeks.  When you try to make it mainstream, things will go wrong.  Your community is looked at as a bunch of 14 year olds and the "professionals" have a hard time respecting the project.

If this were a much cooler forum, the admin's would change your Avatar to an old man, and your signature to "get off my linux!:

---

### Post by thedonvaughn on 2007-11-06
> Don't feel like you need to troll our forums. Thanks. 

Eh.. I do apologize if I seem like a troll.  Not honestly trying to troll.  Just merely discussing.

.. and I do agree FOSS is about choice.  All the more power to you, and I am not trying to say that Ubuntu is worthless.  The reason I am "trolling" is because Ubuntu has a huge enough community that positive things do happen in FOSS with Ubuntu's developers.   Launchpad is one of the greatest tools ever written for a FOSS community.  I wish Canonical would release it's source to allow all projects to benefit from such a great tool.   This is the only reason I'm "trolling", just like FOSS is about choice, it's also about the users voicing their opinion to create change for the better.   Of course, using a user support forum isn't the proper medium I admit :)

---

### Post by Peter09 on 2007-11-06
Many people (most) consider their computers as a tool, not a toy. When I go to do something on my computer I want it to do it quickly and efficiently, I do not want to have to put effort into getting it to work.

So, yes, people want it to look good but, they do not care about the internals, they want it to do the job that needs doing.

Just imagine if every time you wanted to watch a program on the television you had to spend an hour tuning it to the correct channel.!

---

### Post by thedonvaughn on 2007-11-06
> Many people (most) consider their computers as a tool, not a toy. When I got the do something on my computer I want it to do it quickly and efficiently, I do not want to have to put effort into getting it to work.

So, yes, people want it to look good but, they do not care about the internals, they want it to do the job that needs doing.

Just imagine if every time you wanted to watch a program on the television you had to spend an hour tuning it to the correct channel.!

I believe this to be a bad analogy.  The point is that setup is valued for a workstation.  So what if it takes a few hours to setup your workstation vs. 30 minutes.  You know it's done right, you didn't trust application packagers to setup _your_ PC for you.  This sounds wrong to me.  I know my PC and my workstation better than anyone in Ubuntu does.  Why would I allow them to enforce what they think my PC should be setup as?  This is Windows thinking.  The Ubuntu community can not seem break free of this.

Sure, programming your TV everytime you want to use it would be a pain.  But do you have to re-setup your PC everytime you use it?   No just the initial setup.  There is definitely something to be said about setting up your OS.  Knowing every single piece of it.  This is the correct way of 'just working'.

Again, why do you insist on an OS that just works?  Does Windows not just work? 
 It's ok.   I see that my point will not be taken seriously by most in this crowd.
 I'll stick with my own.  I really see that the user base of Ubuntu is basically just average Windows people who want a free Windows.  They want to watch youtube and talk to their friends on yahoo.   Which is fine, more power to you.  
But this will forever and always make Ubuntu not a great Linux distro, but a great Windows alternative.

---

### Post by matthew on 2007-11-06
> **thedonvaughn said:**
> Eh.. I do apologize if I seem like a troll.  Not honestly trying to troll.  Just merely discussing.Thank you.

> **thedonvaughn said:**
>  .. and I do agree FOSS is about choice.  All the more power to you, and I am not trying to say that Ubuntu is worthless.  The reason I am "trolling" is because Ubuntu has a huge enough community that positive things do happen in FOSS with Ubuntu's developers.   Launchpad is one of the greatest tools ever written for a FOSS community.  I wish Canonical would release it's source to allow all projects to benefit from such a great tool.   This is the only reason I'm "trolling", just like FOSS is about choice, it's also about the users voicing their opinion to create change for the better.   I understand. This is why I tried not to come on too strong, and why I didn't threaten any specific action...there are ways to express these ideas that won't elicit negative responses. Let's work on finding them. :)

> **thedonvaughn said:**
> Of course, using a user support forum isn't the proper medium I admit :)Yeah, that's probably true.

---

### Post by DrumScum on 2007-11-06
> **Peter09 said:**
> 
Just imagine if every time you wanted to watch a program on the television you had to spend an hour tuning it to the correct channel.!

No kidding, but I actually liked the days where you had to find yourself a frequency table and install your TV manually. Nowadays my shiny LCD display has a pretty GUI that looks up all the channels for me, displays the names of those channels and gives me an option to order them to my liking. I'd really like to see the frequencies again, and be able to tune them manually :)

I actually recall having an SBR set back in the days with only 6 presets, so we actually had to tune manually between stations :lolflag:

---

### Post by mivo on 2007-11-06
The thing is, you can tweak and manually configure Ubuntu as much as you desire . The difference is only that you do not have to do this to get up a good looking, functioning and usable desktop. I honestly do not know if I had permanently switched to Linux without Ubuntu. It wasn't even so much the distro itself. It was the community. Here, you can really dare to ask questions without having to worry that someone tells you to RTFM or ridicules you for not knowing the answer to a problem that may be obvious to more experienced Linux users -- even if the question had been answered a dozen of times before. That is rare on the internet today, where everyone seems so impatient and prone to sarcasm and flaming.

Differently put, Ubuntu as a whole (OS plus community plus resources) is a gentle entry into the Linux world, and it scales with your needs and experience. I never felt that they are trying to "be like Windows". Besides, not all Windows concepts are "bad" or inefficient. There are reasons why it became the dominant OS on desktops, and it is not only because of bundling practices and other dubious activities (though this played a large role as well).

---

### Post by rsambuca on 2007-11-06
> **thedonvaughn said:**
> I believe this to be a bad analogy.  The point is that setup is valued for a workstation.  So what if it takes a few hours to setup your workstation vs. 30 minutes.  You know it's done right, you didn't trust application packagers to setup _your_ PC for you.  This sounds wrong to me.  I know my PC and my workstation better than anyone in Ubuntu does.  Why would I allow them to enforce what they think my PC should be setup as?  This is Windows thinking.  The Ubuntu community can not seem break free of this.

Sure, programming your TV everytime you want to use it would be a pain.  But do you have to re-setup your PC everytime you use it?   No just the initial setup.  There is definitely something to be said about setting up your OS.  Knowing every single piece of it.  This is the correct way of 'just working'.

Again, why do you insist on an OS that just works?  Does Windows not just work? 
 It's ok.   I see that my point will not be taken seriously by most in this crowd.
 I'll stick with my own.  I really see that the user base of Ubuntu is basically just average Windows people who want a free Windows.  They want to watch youtube and talk to their friends on yahoo.   Which is fine, more power to you.  
But this will forever and always make Ubuntu not a great Linux distro, but a great Windows alternative.
Are you going to build every component in your home from scratch before you move in?  Are you going to build your own cars?...  Hey, I like the customization from gentoo installs too, but to criticize people for not wanting the same things as you is simply an inflated sense of self-importance on your part.  The philosophy of Ubuntu is not shared by you, we get that.  It doesn't mean that it is wrong.  It is different.

---

### Post by Peter09 on 2007-11-06
Jayson,
there is no problem in wanting to tune your PC to be the equivalent of a racing car or a standard model which has been built to a better specification. I do understand what you are saying. 

The problem is, like many things, that to compete Ubuntu must provide a capable OS to those who just want it as a tool and do not want to spend a lot of effort in understanding the internals of the system.

It must be a suitable tool for the Granny who just wants it to send email and browse the Web.  After all what percentage of us actually use our computers to the limits of their performance, not many I guess. As I type here I am using 1% or 2% of the machine capacity. The eye-candy is loading the system more.

So, I agree that Linux should ensure that it can appeal to those that want to delve deeper, but it is critical that it also collects the passing user who just want to 'use it', otherwise they, and the hardware manufacturers will stick with windows.

P.S.
I believe windows is an easy target here, how many times have 'we' been asked to go and fix someones windows machine because it has suddenly gone wrong. Once Ubuntu is running it is rock solid, very different to windows XP.

---

### Post by g2g591 on 2007-11-06
I think the debian does an excellent job, keeping apps mostly unchanged from upstream versions, like vanilla compared to ubuntu's double chocolate swirl deluxe,

---

### Post by wolfen69 on 2007-11-06
> **thedonvaughn said:**
> I believe this to be a bad analogy.  The point is that setup is valued for a workstation.  So what if it takes a few hours to setup your workstation vs. 30 minutes.  You know it's done right, you didn't trust application packagers to setup _your_ PC for you.  This sounds wrong to me.  I know my PC and my workstation better than anyone in Ubuntu does.  Why would I allow them to enforce what they think my PC should be setup as?  This is Windows thinking.  The Ubuntu community can not seem break free of this.

Sure, programming your TV everytime you want to use it would be a pain.  But do you have to re-setup your PC everytime you use it?   No just the initial setup.  There is definitely something to be said about setting up your OS.  Knowing every single piece of it.  This is the correct way of 'just working'.

Again, why do you insist on an OS that just works?  Does Windows not just work? 
 It's ok.   I see that my point will not be taken seriously by most in this crowd.
 I'll stick with my own.  ***I really see that the user base of Ubuntu is basically just average Windows people who want a free Windows.***  They want to watch youtube and talk to their friends on yahoo.   Which is fine, more power to you.  
But this will forever and always make Ubuntu not a great Linux distro, but a great Windows alternative.

you sir, know nothing of what I and others want in an OS. you have alot of nerve assuming anything. maybe you should go back to the debian boards where they pee on anything or anyone that doesnt use debian. why don't you install Linux From Scratch and pee on debians parade? then you could tell them they are not using a "real" operating system.

---

### Post by karellen on 2007-11-07
> **thedonvaughn said:**
> Well,
as I stated.  Most of the people who disagree with me use responses like "Well what about non-geek people?"  "What about Ubuntu Bug #1?"  etc etc.  "What's wrong with things just working?"

See this is the point.  If you are going to use Linux, you have to learn Linux.  Simple.

I do not care nor want Linux to be the #1 desktop OS.  I hate to break it to you, UNIX is for geeks.  Linux is for geeks.  When you try to make it mainstream, things will go wrong.  Your community is looked at as a bunch of 14 year olds and the "professionals" have a hard time respecting the project.

Why do you want Windows users flooding our user forums, IRC channels, news groups?  Refusing to read the documentation?  Refusing to actually learn Linux and then complain when it's not like their Windows OS.

I work for a corporation that serves 18,000 - 20,000 different Linux servers.  
RHEL, CentOS, and Debian are by far the most popular distributions.  Ubuntu isn't even on the map.   This is the thing that most Ubuntu users do not realize.
In fact, in the professional corporate world, you will be looked down if you advocate Ubuntu.  Advocating Ubuntu is like advocating Windows or like advocating Mac OS X.  Yes, Mac OS X is horrid crap too.   Who wants a shiney kitchen box that is only good for drawing pretty pictures?  Have you ever seen Mac OSX scale nicely?  It's a horrid OS as well.

Anyway, enjoy your spinny 3D cube :)

are you angry because, thanks to the work of canonical, opensuse, fedora and so on, everybody can use Linux, without having to understand the difference between a monolithic kernel and a hybrid one? yes, it's no more the tool of tech savvy people. and you can complain as much as you want, things won't change, for good. and I'm not talking about servers here, ok? Ubuntu's success can be seen primary on desktops. what's your problem? use whatever hardcore distro you want and stop pretending and everyone else should do the same. it's called choice. respect the others if you want respect. zealotry, exaggerations like 'advocating Ubuntu is like advocating Windows' don't tell good things about your way of reasoning. there are distros for everyone's tastes, use them, enjoy them, feel "the Unix way" and don't try to enforce your values to others

---

### Post by panaretos22 on 2007-11-07
and this is the reason mate that linux distributions is not famous to the citizens.Ubuntu brought me to the world of Linux.Is more easy to understand manage a detskop pc than the other distributions.My bestman also had for many years debian ....but beleive me i cannot find any reason to use debian or other distribtution when ubuntu offer me a complete solution for my needs.Keep going programmers of Ubntu in the near futuru ubuntu will be better and with great success globally
Best wishes
Loucas

---

### Post by Samhain13 on 2007-11-07
> In fact, in the professional corporate world, you will be looked down if you advocate Ubuntu. Advocating Ubuntu is like advocating Windows or like advocating Mac OS X. Yes, Mac OS X is horrid crap too. Who wants a shiney kitchen box that is only good for drawing pretty pictures? Have you ever seen Mac OSX scale nicely? It's a horrid OS as well.

This is a very unfair comment. Some of us here actually make a living by "drawing pretty pictures" and we're as professional as any out there. And in the professional world that I know of, it's not about whether one uses a Mac, Windows or any other OS-- it's about how pretty our pictures turn out regardless of what tools or media we use.

I just want my machine to work as I would have it. Ubuntu makes my machine work. What I do with my Ubuntu run machine is what gives me a living-- not the machine itself. So I care more about improving what I know about what I do than improving my machine's performance, because even without the machine, I can always use something else like paper and crayons.

---

### Post by karellen on 2007-11-07
I'd suggest to stop posting in this thread. it's obviously how things are and we won't do anything but to feed a useless dispute

---

### Post by blackcp on 2007-11-07
At the same time there is nothing wrong with sharing one's thoughts on how an operating system should be.

Some people in this board take the thread starter and the people who talk of Ubuntu being too user-friendly, way too personally. 

However, I don't seriously think that Ubuntu aims to be "windows without spyware". The GUI doesn't even look like windows unlike Linspire =P. 

Ubuntu is based on open source which means you can do whatever you want to it and distribute it along with the source code. windows doesn't. 

For Linux to go mainstream isn't bad at all. In fact the only company that truly criticizes Linux is microsoft. Linux forces bill gates to change his shady business tactics if he still wants to stay on top.

---

### Post by bruce89 on 2007-11-07
> **karellen said:**
> are you angry because, thanks to the work of canonical

You forget where the vast majority of packages are copied from. Pretty much all Canonical does is turn it brown and claim it's original (well, they don't acknowledge their sources).

> **karellen said:**
> use whatever hardcore distro you want and stop pretending and everyone else should do the same.

Debian isn't hardcore, in fact, you're using it now (sort of).

I don't think the GUI is evil, but people shouldn't grow to rely on it, in case something goes wrong.

---

### Post by mivo on 2007-11-07
> **bruce89 said:**
> You forget where the vast majority of packages are copied from. Pretty much all Canonical does is turn it brown and claim it's original

The dissatisfaction of Debian developers with Canonical is not a new issue, though I, as someone who is only watching from the outside, find it hard to see where the reasonable concerns end and the envy begins. Ubuntu is not just "Debian in brown", it is a complete distro with quite a few changes and own concepts. Canonical also advertises the distro (and thus Linux), even ships CDs for free to anyone who asks, and has raised Linux awareness to a level that had been reached before. They are not taking money from the end user even though they obviously have expenses. 

As I said before, Ubuntu is also more than just the distro. It is a huge community where new Linux users are actually welcome and treated friendly, without anyone expecting them to possess a large amount of experience before they are permitted to seek help and assistance. In fact, Joe User, who works 9 hours a day, has a family life, and doesn't have time to spend many hours reading up on and researching problems, can ask a simple question about his wireless or sound issues, without having to worry about being treated like a clueless intruder.

Ubuntu is really **Linux + community + resources + accessibility + PR effort**, and it is the combination that has made it so successful. Without the last four aspects, Ubuntu would only be "yet another Debian-based distro". It is much more than just that. There is applied philosophy, lifestyle, movement. Ubuntu is a child of Debian, but it has long moved out of its parent shadow and started to write its own story. Sometimes it is hard to accept for parents that their off-spring is more "successful" (or in different ways) than they were, but without them, none of the child's achievements would have been made. Ubuntu's success is also Debian's success, and something Debian can be proud of.

The Linux world owes a lot to the Debian project. I am sure everyone acknowledges that. The never-ending political issues that plague Debian, the inaccessible web site and the lack of a strong desire to appeal to Joe User (have you tried finding something as simple as a current Live CD for Debian?) are responsible for its lack of success in the broad desktop market (as its own distro).

---

### Post by bruce89 on 2007-11-07
> **mivo said:**
>  Ubuntu is not just "Debian in brown", it is a complete distro with quite a few changes and own concepts.

It was artisic exaggeration.

> **mivo said:**
> The Linux world owes a lot to the Debian project. I am sure everyone acknowledges that. The never-ending political issues that plague Debian, the inaccessible web site and the lack of a strong desire to appeal to Joe User (have you tried finding something as simple as a current Live CD for Debian?) are responsible for its lack of success in the broad desktop market (as its own distro).

Debian isn't for the "Joe user".

I think much of the "jealousy" is because Ubuntu doesn't market itself the right way -  acknowledging much of the work is Debian's (or GNOME, X.org etc.).

---

### Post by julian67 on 2007-11-07
Ubuntu isn't Debian in brown. Ubuntu is Debian done right. :)

---

### Post by mivo on 2007-11-07
> **bruce89 said:**
> Debian isn't for the "Joe user". I think much of the "jealousy" is because Ubuntu doesn't market itself the right way -  acknowledging much of the work is Debian's (or GNOME, X.org etc.).

But its "ease of use" and the "Joe User" appeal were the aspects that the topic starter criticized. I agree that Debian and Ubuntu are not aimed at the same core audience, but Ubuntu isn't really a dumbed-down Linux distro, either. It is more like a swimming pool with gradually increasing depth. It starts at a foot, not at six feet like other swimming pools.

In terms of success in the market, awareness and getting publicity (for Linux), Ubuntu markets itself in exactly the right way. Let's face it: the large majority of computer users today has no interest in details like where the packages come from, what X is, who designed the packaging system, etc. They want an OS that "just works" and that meets their needs. The aspects of "political correctness" are important only to a few, but would not be understood by Joe User who might even get confused by them. 

What could Canonical do to please everyone? Add a list of credits to the splash screen? (This is a serious question, I'm not trying to be polemical). Canonical's contributions are open source, and they employ and pay developers. I really do feel that everyone is benefiting from what Canonical does. Linux needs market share to get better support from manufacturers and commercial software developers. The present situation that people can't get their wireless to work or that they have to dual-boot to play a game is not very satisfying.

Prior to Ubuntu, Linux market share was a little stagnating. It is only now that it loses the stigma of being an OS from freaks for freaks, but not for "normal people". Some parts of this discussion remind me of the time when AOL enabled even average people to get online. There are many other factors, like Vista's issues and perhaps more awareness of the public of DRM and other restrictive visions of TPTB, but many, many people who now use Linux only do so because of Canonical's efforts and courage to take some "new ways"  (and Mark Shuttleworth's funding).

Anyway, I'm not saying Canonical is saving Linux. ;) There are many other companies (Red Hat, Novell, IBM etc.) and organizations that have done and do a lot toward the end of providing a real and speech-free desktop alternative. I merely believe that Canonical is a Good Thing for Linux and feel that "fighting" within the Linux world does more harm than good. Linux needs more unity, not separation.

---

### Post by SomeGuyDude on 2007-11-08
Windows and OSX are made for people who don't want to have to do ANYTHING to make their computers work.

The difficulty of Linux is why people haven't hopped in until now. I wouldn't be on Ubuntu right now if it were as hard as Red Hat used to be. I don't understand why people think "ease" is bad. As long as all the functionality is still there, what's the problem?

Besides, it opens the gates for people like me who have never used anything but Windows for the past 10 years. By giving me an OS I can play with and get my feet wet without being overwhelmed, I'll be more apt to look at other distros since I know I can get it working.

Honestly, who would use Linux if they all required command-line configuration? If you want that answer, look at who DID use Linux when that's how it was.

---

### Post by karellen on 2007-11-08
> **bruce89 said:**
> You forget where the vast majority of packages are copied from. Pretty much all Canonical does is turn it brown and claim it's original (well, they don't acknowledge their sources).



Debian isn't hardcore, in fact, you're using it now (sort of).

I don't think the GUI is evil, but people shouldn't grow to rely on it, in case something goes wrong.

I know exactly what Debian is, as I'm using Linux for more than 3 years, in which I've tried all kind of distros. but bashing Ubuntu because is easy to use and user-friendly seems very awkward to me. what I fail to understand is why do you people criticize a distro because it's not like other distro you prefer. use the distro you like most and that's it

---

### Post by qamelian on 2007-11-08
> **thedonvaughn said:**
> Well,
as I stated.  Most of the people who disagree with me use responses like "Well what about non-geek people?"  "What about Ubuntu Bug #1?"  etc etc.  "What's wrong with things just working?"

See this is the point.  If you are going to use Linux, you have to learn Linux.  Simple.

I do not care nor want Linux to be the #1 desktop OS.  I hate to break it to you, UNIX is for geeks.  Linux is for geeks.  When you try to make it mainstream, things will go wrong.  Your community is looked at as a bunch of 14 year olds and the "professionals" have a hard time respecting the project.

Why do you want Windows users flooding our user forums, IRC channels, news groups?  Refusing to read the documentation?  Refusing to actually learn Linux and then complain when it's not like their Windows OS.

I work for a corporation that serves 18,000 - 20,000 different Linux servers.  
RHEL, CentOS, and Debian are by far the most popular distributions.  Ubuntu isn't even on the map.   This is the thing that most Ubuntu users do not realize.
In fact, in the professional corporate world, you will be looked down if you advocate Ubuntu.  Advocating Ubuntu is like advocating Windows or like advocating Mac OS X.  Yes, Mac OS X is horrid crap too.   Who wants a shiney kitchen box that is only good for drawing pretty pictures?  Have you ever seen Mac OSX scale nicely?  It's a horrid OS as well.

Anyway, enjoy your spinny 3D cube :)

I have news for you. You have no idea what you are talking about. I know for a fact that there are a number of fairly sizable organizations and corporations who *are *considering Ubuntu seriously. And I work with professionals every day who realize the value and capabilities of Unix/Linux. The attitude you describe may exist where you work, but it most certainly is not the prevalent way of thinking amongst any of my corporate clients.

---

### Post by MNICY on 2007-11-13
I want a computer that works.
If i can customize/tweak it, that is great!
I will. But, at the end of the day, if it works i am happy.
Ubuntu is great. This is about Choice. It is great if you prefer Debian over Ubuntu. I prefer Ubuntu over Debian. People have difforent opinions, and the fact that you can choose Debian, and i can choose Ubuntu is simply amazing.

---

### Post by garba on 2007-11-15
i kind of agree, but bear in mind that ubuntu and debian are aimed at different targets, anyway yes, i think that debian is way more sysadmin friendly than ubuntu is

---

### Post by joshuachad on 2007-11-15
I think the bottom line is that 80% of the population wants everything done for them and you see that a lot on this forum with some of the questions I see. Bottom line is. If Im trying to market a "desktop OS" then I am going to build it for the 80% who want it spoon fed to them. The person who started this thread is prolly some dude who sits in the basement and pops hotmail accounts all day. Ok that was a joke. At any rate go to distrowatch and see that the top 3 distros are marketing for the ease of use crowd. Thats because there is more of them then geeks who want to compile Open Office from source.

Cheers

---

### Post by mivo on 2007-11-15
> **joshuachad said:**
> At any rate go to distrowatch and see that the top 3 distros are marketing for the ease of use crowd.

I'd question the numbers there for PCLinuxOS. The system can easily be tricked by using bots. Ubuntu is by far the most popular distro, and if PCLinuxOS were more popular, we'd read more about it in the news, at Digg, etc., and they would have more active forums.  Even the guy who runs Distrowatch warns against taking the numbers seriously.

---

### Post by Fanless_Puppy_Fan on 2007-11-16
> **thedonvaughn said:**
>  The true "Alternative OS" is the one that offers power, that does not hide it's system, and that chooses performance over 'ease of configuration'.

There's always gentoo for you.

---

### Post by karellen on 2007-11-16
> The true "Alternative OS" is the one that offers power, that does not hide it's system, and that chooses performance over 'ease of configuration'.

the true alternative os for you maybe. you're entitled to an opinion. and that's all, not more or less

---

### Post by linuxlizard on 2007-11-17
Your points are flawed.
Why? Because ubuntu doesn't prevent me from doing anything you do on debian, if I want to, plus I'm not forced to do some things if I don't want too. Want to edit your xorg.conf in ubuntu like you do in debian? Go ahead- nothing's stopping you but you. 

As far as "dumbed down"- I think of it as "smartened up". A "dumbed down" system can't do anything unless I tell it too. Something to config? I do it myself- that's a pretty "dumb" system. On the other hand, if the system can do things like make an xorg.conf for itself, that's a pretty smart system. If a person is dumb, you have to tell them what to do and how to do it. If they are smart, they figure out what needs to be done and figure out how to do it and then do it. Seems to me versions of linux are the same...

---

### Post by youthforlinux on 2007-11-17
A lot of my friends that use linux are on the side of the peole who think that ubuntu is to bloated and easy to use but linux is all about choice and if I want a system that doesnt need 2 hours of config when i reinstall then I should have a choice.  I have had a recent linux success story with my aunt who has barely used a computer in her life and prefers my ubuntu pc to he windows pc so I gave her ubuntu and it came out great. i truly believe that what ubuntu is doing in the linux community is great and should be continued.  If you dont like that ubuntu is bloated...well then you can make your decision to change to different distro.


LINUX IS CHOICE AND CHOICE RULES

---

### Post by MNICY on 2007-11-17
Ubuntu may be bloated compaired to other Linux distros, but compared to Windows, its amazing.
like youthforlinux says, its is about CHOICE

---

### Post by julian67 on 2007-11-18
I find it hard to consider as bloated an OS that runs live from CD and installs to Hard Disk from the same CD and gives you just enough widely used applications and tools to get you productive within 30 minutes of loading the CD in the tray.  Bloated is one of those words that gets used by people without any thought as to what it might mean or imply. To me it suggests inefficiency, apps and tools which use too much RAM/CPU cycles for the facilities they provide, lots of uncalled for features that are there mostly for the marketing and not actually that good for the end user. I don't find Ubuntu bad in this respect.  If people want to say Gnome and KDE desktops can be slow then that's another issue related to the DEs more than the specific Ubuntu distribution or the Linux kernel but Ubuntu is not bloated. If you're a true minimalist there is always DSL (or similar) for a super lean  distro but you don't get the same richly featured applications and nice facilities.

---

### Post by cmnorton on 2007-11-21
In the words of 1975's SNL's Schimmer Floor Wax Desert Topping Commercial, You're both (all of you)  right .

For those of us with 4+ years Linux experience or less, Ubuntu might be the right mix, not as bloated as RH EL, but not as lean as other distros like Debian. With Ubuntu, I have to remember to grab build-essential. It almost comes by default with RH EL and Fedora, and who can live without make and sed? But, I don't get a lot of garbage with Ubuntu, at least none that has prevented me from working.

For those of you who grew up with Linux and have the time to read source code; immerse yourselves in your environment; and as a result become as knowledgeable as you are, I understand why you think Ubuntu is bloated, and you are probably right. 

Please understand for those of us who are trying to pitch saving license fees (replacing Office with OpenOffice), we need something like Ubuntu to sell the whole open source idea as well as replacing some Windows clients with Ubuntu. 

My job entails sustaining engineering and systems integration with sysadmin and db admin thrown in. I do need to know more about Linux, but there is also a time constraint on how much "point and click" saves me to go do other things.

---

