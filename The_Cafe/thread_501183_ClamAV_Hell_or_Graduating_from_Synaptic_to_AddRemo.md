---
title: "ClamAV Hell or Graduating from Synaptic to Add/Remove"
date: 2007-07-14
forum: The Cafe
---

### Post by keyboardashtray on 2007-07-14
So how do programs graduate from the sloppy mess of Synaptic to the nice and tidy world of Add/Remove? Case in point: ClamAV - I mean, when you look at the LiveCD from within Windows, when you first burn it, ClamAV is mentioned, along with Firefox, etc. one of these great examples of the open source world. You get the feeling it would be on there already, and if not, at least in the Add/Remove that we are encouraged by Ubuntu (maybe not so much the community though) to use.

Well, not only is it not there, I don't think it's possible to have a painless installation through Synaptic, either. I'm new, but I know I checked all the right boxes for ClamAV there. And let me tell you something, I'm no computer expert - but I know plenty, plenty of people far worse than me, and they would just vomit if they even just saw that list through Synaptic - forget the fact that even if they checked all the right boxes they'd still be in hell getting it to work. Errors come up on install, then FreshClam doesn't work, files are missing, then when you can get it to update the definitions, well you don't have the most up-to-date install. ClamTK, the GUI for Clam AV (which, oddly enough, IS in Add/Remove) tells you you need to be at the root level, so you type in the Terminal command and it works once, tells you you are up to date, but on next restart of it you're back at square one.

And I don't want to hear how I don't need an antivirus. I find some comment like that on every ClamAV thread and quite frankly I find it at worst naive and at best inconsiderate. Naive because, sure, for your own personal needs if you are strictly running Linux you may not need it, now, but that isn't looking very far into the future: we might be safe at the moment but the more Linux/Ubuntu catches on the more likely our small numbers won't protect us from being targets. And in that regard, it's a pretty pessimistic view of Linux/Ubuntu, too - it assumes we'll always be some novelty. Not to mention the fact that many of us ARE using Linux and Windows, whether sharing files on dual boot or a home network. Inconsiderate in that just because a virus can't hurt you, doesn't mean you shouldn't care - we all communicate and depend on others' computers that are vulnerable, and if some of us want to take an extra step to make sure viruses aren't proliferated then we don't deserve to be shot down for it. I'm not saying all of you going commando-style without an AV are inconsiderate, I'm not using one either, just that telling someone who does want one not to bother isn't perhaps the most open view.

I think Ubuntu has done a very good job of covering all the basics in Add/Remove, with the one glaring omission of an anti virus. For the bulk of people coming from Windows, it has been ingrained into us as dogma, you just have to be running an anti virus, and I think it would represent Ubuntu well to make sure at least one hassle-free option is in the Add/Remove list.

Add/Remove is painted as a selling point of Ubuntu, "look how safe and easy installing and removing programs can be!" and on first glance it seems great - indeed it does trump the method through Windows. However it doesn't take long to realize it can't get you very far and from that point on in is a steep drop down for ease of installing new programs.

Just an impression - and I realize this is very idealistic and probably doesn't take into account the long rich traditions of Debian, or the options for the advanced user -  having so many package managers seems to unnecessarily complicate things. Why does there need to be Add/Remove, Synaptic and Apt-get (not to mention third party installers)? I mean, why not just push one GUI and then the console way for the advanced user? My guess is that Add/Remove doesn't let developers have customization they want, or it is too strict for what makes the cut. I think Add/Remove could stand to be a little more complicated, if it would mean more programs make the cut. And for all that couldn't handle, Apt-get and tarballs, etc. could handle the rest. But right now it has that feeling of a perfect-world feature I've seen in countless other products that slowly phase out and die because it simply isn't compatible enough.

I didn't put this in testimonials because if I write up a testimonial I plan to include all the things I love about Ubuntu that far outweigh this little shortcoming.  (obligatory I <3 Ubuntu 4ever disclaimer)

---

### Post by Griff on 2007-07-14
So... do you have clamav working yet?  I can't really tell from the tone or content of your thread.  I personally don't use the add/remore app thing because I find it quicker to do something like the following:
```
sudo apt-get install clamav
```
Did you try that?  It should grab the necessary dependencies for you so you wouldn't have to try to look for what you think you might need.

-Griff

---

### Post by RomeReactor on 2007-07-14
Hi. If you search for **clam** or **virus**, clam tk shows up in Add/Remove. It doesn't cover the totality of software found through Synaptic because it's aimed at more of a friendly "suggestion" tool. It gives you a selection of applications that you're most likely to be searching for, as opposed to Synaptic's overwhelming catalog. Each has its uses. Also, I don't see applications as "graduating" to Add/Remove. It's purpose, as I said before, is to make suggestions, and having all applications there would kind of defeat its purpose.

---

### Post by H.E. Pennypacker on 2007-07-14
I am of the opinion that Synaptic needs to be removed entirely.  It is far too user-unfriendly to come standard with Ubuntu.  Installing stuff is very easy, and straight forward, but it can use changes, such as getting rid of the left panel, adding more information to the bottom (an application's information), adding a review tab (reviews from other users), several screenshots, and a way to run sudo apt-get clean (a button that runs this command so you don't have to use the terminal - a user should be able to do all package management from Synaptic, and sudo apt-get clean is a glaring omission - remarkable that it is left out).

---

### Post by starcraft.man on 2007-07-15
> **keyboardashtray said:**
> So how do programs graduate from the sloppy mess of Synaptic to the nice and tidy world of Add/Remove? Case in point: ClamAV - I mean, when you look at the LiveCD from within Windows, when you first burn it, ClamAV is mentioned, along with Firefox, etc. one of these great examples of the open source world. You get the feeling it would be on there already, and if not, at least in the Add/Remove that we are encouraged by Ubuntu (maybe not so much the community though) to use.

Well, not only is it not there, I don't think it's possible to have a painless installation through Synaptic, either. I'm new, but I know I checked all the right boxes for ClamAV there. And let me tell you something, I'm no computer expert - but I know plenty, plenty of people far worse than me, and they would just vomit if they even just saw that list through Synaptic - forget the fact that even if they checked all the right boxes they'd still be in hell getting it to work. Errors come up on install, then FreshClam doesn't work, files are missing, then when you can get it to update the definitions, well you don't have the most up-to-date install. ClamTK, the GUI for Clam AV (which, oddly enough, IS in Add/Remove) tells you you need to be at the root level, so you type in the Terminal command and it works once, tells you you are up to date, but on next restart of it you're back at square one.

Synaptic is not sloppy... it is a great package managers (I think so) and combined with Aptitude it forms an excellent tool for installing anything. Please consult blue link in my sig to understand installing. Clam is in the universe so make sure those repositories are enabled. I don't know why you had so much trouble, I just installed clam with the klam front and had no issue.
> 
And I don't want to hear how I don't need an antivirus. I find some comment like that on every ClamAV thread and quite frankly I find it at worst naive and at best inconsiderate. Naive because, sure, for your own personal needs if you are strictly running Linux you may not need it, now, but that isn't looking very far into the future: we might be safe at the moment but the more Linux/Ubuntu catches on the more likely our small numbers won't protect us from being targets. And in that regard, it's a pretty pessimistic view of Linux/Ubuntu, too - it assumes we'll always be some novelty. Not to mention the fact that many of us ARE using Linux and Windows, whether sharing files on dual boot or a home network. Inconsiderate in that just because a virus can't hurt you, doesn't mean you shouldn't care - we all communicate and depend on others' computers that are vulnerable, and if some of us want to take an extra step to make sure viruses aren't proliferated then we don't deserve to be shot down for it. I'm not saying all of you going commando-style without an AV are inconsiderate, I'm not using one either, just that telling someone who does want one not to bother isn't perhaps the most open view.

The first argument that simply because we are small protects us is flawed. The Mac install base is now about 30 Million users (pretty big target to me) I believe from last estimates (Mac Books + Towers). I see no rampant amount of viruses for them either. As for communicating Viruses... the only way to transmit a virus through a linux box efficiently is really through email attachment forwarded by an unwitting user, which is the primary purpose of Clam, to scan those. I quite simply don't open attachments anymore from anyone. In the end though, Ubuntu really doesn't need an AV to protect itself, merely to protect Windows users which isn't technically Ubuntu's problem.

> I think Ubuntu has done a very good job of covering all the basics in Add/Remove, with the one glaring omission of an anti virus. For the bulk of people coming from Windows, it has been ingrained into us as dogma, you just have to be running an anti virus, and I think it would represent Ubuntu well to make sure at least one hassle-free option is in the Add/Remove list.

Just because users are ingrained with something doesn't mean it's right. I would equally submit Windows users believe the exe format should work out of the box on Ubuntu at the beginning, and that it's Ubuntu's fault that drivers don't work... both are flawed beliefs. An AV isn't needed because there quite simply aren't viruses in the wild that can infect Ubuntu with any efficacy.

> Add/Remove is painted as a selling point of Ubuntu, "look how safe and easy installing and removing programs can be!" and on first glance it seems great - indeed it does trump the method through Windows. However it doesn't take long to realize it can't get you very far and from that point on in is a steep drop down for ease of installing new programs.
I don't think it's that important, I all but ignored Add Remove in my blue guide. I also don't see it selling Ubuntu.... do we go to different places/sites?

> 
Just an impression - and I realize this is very idealistic and probably doesn't take into account the long rich traditions of Debian, or the options for the advanced user -  having so many package managers seems to unnecessarily complicate things. Why does there need to be Add/Remove, Synaptic and Apt-get (not to mention third party installers)? I mean, why not just push one GUI and then the console way for the advanced user? My guess is that Add/Remove doesn't let developers have customization they want, or it is too strict for what makes the cut. I think Add/Remove could stand to be a little more complicated, if it would mean more programs make the cut. And for all that couldn't handle, Apt-get and tarballs, etc. could handle the rest. But right now it has that feeling of a perfect-world feature I've seen in countless other products that slowly phase out and die because it simply isn't compatible enough.

Aptitude is the base foundation, the bottom layer that installs everything. Synaptic and Add Remove are simply frontends on top of Aptitude (they have different takes on how to install). The third party installers are just that unofficial. There are different ways to install in Ubuntu because that's a main belief, freedom of choice. I encourage you to read my blue guide... it explains in detail aptitude and synaptic. Ultimately, I think you just had a bad anomalous experience.

---

### Post by keyboardashtray on 2007-07-15
> **Griff said:**
> So... do you have clamav working yet?  I can't really tell from the tone or content of your thread.  I personally don't use the add/remore app thing because I find it quicker to do something like the following:
```
sudo apt-get install clamav
```
Did you try that?  It should grab the necessary dependencies for you so you wouldn't have to try to look for what you think you might need.

-Griff
No. I didn't bother yet, somewhere I read that it is going to be included in a future release. I might pick it up then, or I might try apt as you suggested if I get impatient.

> **RomeReactor said:**
> Hi. If you search for **clam** or **virus**, clam tk shows up in Add/Remove. It doesn't cover the totality of software found through Synaptic because it's aimed at more of a friendly "suggestion" tool. It gives you a selection of applications that you're most likely to be searching for, as opposed to Synaptic's overwhelming catalog. Each has its uses. Also, I don't see applications as "graduating" to Add/Remove. It's purpose, as I said before, is to make suggestions, and having all applications there would kind of defeat its purpose.
It does more than just search - it Adds and Removes in a very user friendly way. And while I'm not claiming to know for certain what process makes an application on Synaptic also on Add/Remove, what is in Add/Remove is in Synaptic, but only a handful of what is in Synaptic is in Add/Remove, which suggests some sort of criteria/making the grade.

> **H.E. Pennypacker said:**
> I am of the opinion that Synaptic needs to be removed entirely.  It is far too user-unfriendly to come standard with Ubuntu.  Installing stuff is very easy, and straight forward, but it can use changes, such as getting rid of the left panel, adding more information to the bottom (an application's information), adding a review tab (reviews from other users), several screenshots, and a way to run sudo apt-get clean (a button that runs this command so you don't have to use the terminal - a user should be able to do all package management from Synaptic, and sudo apt-get clean is a glaring omission - remarkable that it is left out).
I agree :)

> **starcraft.man said:**
> Synaptic is not sloppy... it is a great package managers (I think so) and combined with Aptitude it forms an excellent tool for installing anything. Please consult blue link in my sig to understand installing. Clam is in the universe so make sure those repositories are enabled. I don't know why you had so much trouble, I just installed clam with the klam front and had no issue.
It feels sloppy to me. Running down a checklist and assembling your program by hand with a few suggestions on the way vs. installing a complete program and choosing options just feels sloppy. Of course, coming out of the ordeal with a program that didn't work doesn't help either. I hear this universe talk - yes, I'm sure I enabled the universe at some point, because there was a ClamAV there. And if it wasn't the right one, well, then the "wrong one" still being in the list there makes me think one thing: sloppy.

> **starcraft.man said:**
> The first argument that simply because we are small protects us is flawed. The Mac install base is now about 30 Million users (pretty big target to me) I believe from last estimates (Mac Books + Towers). I see no rampant amount of viruses for them either. As for communicating Viruses... the only way to transmit a virus through a linux box efficiently is really through email attachment forwarded by an unwitting user, which is the primary purpose of Clam, to scan those. I quite simply don't open attachments anymore from anyone. In the end though, Ubuntu really doesn't need an AV to protect itself, merely to protect Windows users which isn't technically Ubuntu's problem.
Just because you're willing to give up email attachments doesn't mean the rest of us are. I myself would much rather use an antivirus vs. not being able to use attachments. As far as the Mac Install base, well, just because viruses aren't rampant doesn't mean they don't exist - and even in that example you're working off of the core assumption of Linux being under Mac, or Mac being under Microsoft. I'm simply saying that reasoning we are small, we aren't a target protects us now but it isn't a very long term outlook. And just because I'm in the Ubuntu boat now doesn't mean I can't concern myself with Windows users, I'm still one, and lots of good people are, it is in everyone's best interest to fight viruses.

> **starcraft.man said:**
> Just because users are ingrained with something doesn't mean it's right. I would equally submit Windows users believe the exe format should work out of the box on Ubuntu at the beginning, and that it's Ubuntu's fault that drivers don't work... both are flawed beliefs. An AV isn't needed because there quite simply aren't viruses in the wild that can infect Ubuntu with any efficacy.
Yes, some Windows users probably do miss the million and one warnings/threads/documents talking about proprietary drivers and files, come here, have issues and "blame" Ubuntu. Many more probably read it and never come at all. But proprietary drivers and file formats are one thing - it is both philisophical and legal why those aren't included in Ubuntu. An antivirus is quite another thing, there is no reason why there can't be a token easy antivirus if it makes some former Windows users happy. And now you fall back on the old "we don't need antivirus" - I don't "need" mp3 either, but if it makes some other users happy, you won't hear me complain there's a way. If my language here sounds harsh it's because I see a lot of logic of why one doesn't need AV in Linux to (seemingly) defend why it doesn't need to be easy to get an AV when the point in my initial rant was about people who come into "Help me with Clam" threads and start saying why you don't need one. I know that the lack of viruses is a selling point of Linux/Ubuntu, and something to take pride in, but if someone *wants* an AV, they don't need a lecture of why they don't *need* one. I realize you edited and added a comment about how you just installed Clam, and how it went alright for you - that is to my benefit, you took your own time to test out installing a program just to help me, and I appreciate it. I don't want to come across as ungrateful or a jerk, I just feel like I have to defend why it is important to some people to have an AV.

> **starcraft.man said:**
> I don't think it's that important, I all but ignored Add Remove in my blue guide. I also don't see it selling Ubuntu.... do we go to different places/sites?
Just because you don't use it, doesn't mean it shouldn't be supported better. You also don't use email attachments, does that mean I can't? It's a very user-friendly feature that is the first way they recommend you install programs in the help - the easiest, in their words.

> **starcraft.man said:**
> Aptitude is the base foundation, the bottom layer that installs everything. Synaptic and Add Remove are simply frontends on top of Aptitude (they have different takes on how to install). The third party installers are just that unofficial. There are different ways to install in Ubuntu because that's a main belief, freedom of choice. I encourage you to read my blue guide... it explains in detail aptitude and synaptic. Ultimately, I think you just had a bad anomalous experience.
I also believe in freedom of choice, and one of choices I would make is the user friendly option. Having two ways, the easy way and the right way, really isn't a choice. Just because I elect the dumbed-down interface now doesn't mean I won't take the more advanced route down the road. I'm trying to suggest how Ubuntu can be more friendly to the new user, and you're trying to help the new user become an advanced user. They don't have to be mutually exclusive.

Listen, Starcraft.man, I realize you are trying to help - and I promise I will go read your tutorial right now. Heck, a few months from now I might completely agree with you. But I will no longer be a brand new user then, and essentially that is what my OP was about - a couple ideas that would make it easier and more appealing to new users 1.)There should be an antivirus in Add/Remove 2.) Add/Remove is really nice and I'd like to see more programs in it

---

### Post by igknighted on 2007-07-15
Ick... How about we remove add/remove?  It is completely against the linux way of doing things... which is giving the user choice.  Synaptic is easy enough that anyone can operate it.  If you cannot figure out synaptic, then you will struggle more with everything else in linux (really... If you can't use synaptic, lots of other things are much harder.  Not intended to be mean, but it is one of the easier apps).  Think about it, synaptic lets you manage repositories, pick out libraries and dependencies and gives you about as much control as you can expect from a GUI.  Add/Remove has no options and often errors out, leaving users with a broken package management system and no idea why.  Plus, there's always klik or CNR if you want "easy" package management.  Both of these are far superior in terms of being user friendly than add/remove.

---

### Post by keyboardashtray on 2007-07-15
> **igknighted said:**
> Ick... How about we remove add/remove?  It is completely against the linux way of doing things... which is giving the user choice.  Synaptic is easy enough that anyone can operate it.  If you cannot figure out synaptic, then you will struggle more with everything else in linux (really... If you can't use synaptic, lots of other things are much harder.  Not intended to be mean, but it is one of the easier apps).  Think about it, synaptic lets you manage repositories, pick out libraries and dependencies and gives you about as much control as you can expect from a GUI.  Add/Remove has no options and often errors out, leaving users with a broken package management system and no idea why.  Plus, there's always klik or CNR if you want "easy" package management.  Both of these are far superior in terms of being user friendly than add/remove.

Oh here we go with the leet uzer - I thought Ubuntu was about being user friendly Linux? So I make a comment on Synaptic being sloppy, in my opinion - as a brand new user, first impression - and getting me the wrong/bad Clam - which it did - and now I'm not good enough for Linux...pfft. And do a quick search on Clam - I'm not the only one who had trouble here.  And Linux being about choice, I guess you mean your choice? I like Add/Remove - hasn't done me wrong yet, apparently someone higher up the totem pole than myself likes it, because it exists. I'd improve it. But you'd do away with it. Well, as dumb as I might be to you, I guarantee there are plenty more people who have/do/will balk at their first use of Synaptic. 

And obviously you didn't read the OP - clearly the last paragraph says its just an impression and doesn't take into account the traditions or options of the advanced user.

So you'll forgive me if I disregard *your* disclaimer "not intended to be mean".

---

### Post by RomeReactor on 2007-07-15
Is it just me, or is this taking a turn for the worse here? Good thing this is the Cafe...

> **keyboardashtray said:**
> Just because you're willing to give up email attachments doesn't mean the rest of us are. I myself would much rather use an antivirus vs. not being able to use attachments. As far as the Mac Install base, well, just because viruses aren't rampant doesn't mean they don't exist - and even in that example you're working off of the core assumption of Linux being under Mac, or Mac being under Microsoft. I'm simply saying that reasoning we are small, we aren't a target protects us now but it isn't a very long term outlook.

I agree on this point. Reasoning that a small user base is immune to viruses is an argument that won't have a leg to stand in some 10 odd years (at most, in all likelihood less); that's the future though, however close it may be.

> And just because I'm in the Ubuntu boat now doesn't mean I can't concern myself with Windows users, I'm still one, and lots of good people are, it is in everyone's best interest to fight viruses.

This is where we differ. It's in the best interest of windows users to fight viruses, because they are affected by them. Ubuntu is here to provide for the interests of Ubuntu's users, not windows users. That may sound harsh; but you don't see microsoft providing better interoperability (both [free]("http://en.wikipedia.org/wiki/Free_as_in_beer") and [Free]("http://en.wikipedia.org/wiki/Free_software")) between Linux and windows (by providing appropriate tools to interact with NTFS, or by opening up their windows media formats) because it's in the collective best interest (and no, please don't mention deals with Novell and others). Still, just a search of Add/Remove or Synaptic away, you *do* find software to remove those pesky windows viruses.

> ...there is no reason why there can't be a token easy antivirus if it makes some **former** Windows users happy.

If they *only* use Linux, sure they can install and use an antivirus; regarding **their Linux system**, however, and for the time being, unless there's a sudden, fantastically dramatic flow of Linux viruses (brace yourself to hear this comment for the 100th time), you don't need it. It would take just that--a massive outburst of Linux-specific malware--to bring your **up-to-date** Linux system (choose your flavor) close to the level of vulnerability of windows, or (worst case scenario) render your system useless. Linux's growth rate (as concerns adoption and actual desktop use) works to the advantage of kernel hackers and application developers, who can spot vulnerabilities (yes, they *do* happen) and patch them usually within hours. You could call Linux a secure system, not through obscurity--but through inherent design, and to a **much** lesser degree, relegation and derision.

---

### Post by starcraft.man on 2007-07-15
> **keyboardashtray said:**
> 
It feels sloppy to me. Running down a checklist and assembling your program by hand with a few suggestions on the way vs. installing a complete program and choosing options just feels sloppy. Of course, coming out of the ordeal with a program that didn't work doesn't help either. I hear this universe talk - yes, I'm sure I enabled the universe at some point, because there was a ClamAV there. And if it wasn't the right one, well, then the "wrong one" still being in the list there makes me think one thing: sloppy.


Well, if you find the Package Manager so sloppy feel free to go code one on your own, a lot of work has been put into Synaptic and I find it does everything everyone (including me) needs. So do a lot of people around here like it, in fact you may be the only person to have used sloppy in describing it. The list of packages isn't about being sloppy, the packages are there to allow easy customization and modularity (i.e. there are many plugins and other extras you can choose to have or not). In addition, the package system is very easy to change and update, you can easily update them on the go (on the repository) where as with Windows you'd have to issue a whole new exe either to install or update. Your thinking of an exe (complete program choosing options) and those don't exist in the Linux world. 

> Just because you're willing to give up email attachments doesn't mean the rest of us are. I myself would much rather use an antivirus vs. not being able to use attachments.

I never suggested everyone give up email attachments, did I say that? I did say that Clam's main goal was mail attachment, for those people who use massive amounts of mail it is very useful. 

> As far as the Mac Install base, well, just because viruses aren't rampant doesn't mean they don't exist - and even in that example you're working off of the core assumption of Linux being under Mac, or Mac being under Microsoft. I'm simply saying that reasoning we are small, we aren't a target protects us now but it isn't a very long term outlook.

No there quite simply aren't many viruses at all for OSX (in direct comparison to the number of malware floating around targeting Windows, the number is negligible non-existent)... a select few (about 20 I think) have been made as "concept viruses" by different firms and hackers to prove it's possible. They've themselves haven never made it into the wild, nor have other viruses from other sources. I would submit as an extra note that OSX and XP were released around the same time (mid-late 2001), so it's not like either has been exposed any longer.

I am not working under any assumption that OSX/Linux remain small or under anyone. They're built to be more secure than Windows, that's simply the case. Windows was built from the ground up (you can go look at the history) as a single user interface and hacked for multiple users, BSD (the foundation of OSX) and Linux are both multiuser systems (derived/inspired by Unix) at their core and were designed to be secure that way. This of course led to the su/sudo system for them, and Windows only recently "hacked" in the UAC. The list goes on, but in the end security is a foundation thing and Windows with all it's legacy and history hasn't proven very secure ever (even with all the firewalls, AVs and spyware cleaners) .[ For more info.]("http://www.psychocats.net/ubuntu/security")

> And just because I'm in the Ubuntu boat now doesn't mean I can't concern myself with Windows users, I'm still one, and lots of good people are, it is in everyone's best interest to fight viruses.
Again, I never said not to scan your attachments to protect Windows users if you like... I don't know where you get this stuff. I specifically noted Clam's main purpose is email scanning. My main statement was that Ubuntu itself isn't inherently susceptible to those email viruses.

> Yes, some Windows users probably do miss the million and one warnings/threads/documents talking about proprietary drivers and files, come here, have issues and "blame" Ubuntu. Many more probably read it and never come at all. But proprietary drivers and file formats are one thing - it is both philisophical and legal why those aren't included in Ubuntu. An antivirus is quite another thing, there is no reason why there can't be a token easy antivirus if it makes some former Windows users happy.

Ubuntu isn't coded to make "Windows users happy", it is to be a good distribution for everyone (and everyone isn't just Windows folks). I don't know what your point is anyway... Clam is easy to install and works easily. 

> And now you fall back on the old "we don't need antivirus" - I don't "need" mp3 either, but if it makes some other users happy, you won't hear me complain there's a way. If my language here sounds harsh it's because I see a lot of logic of why one doesn't need AV in Linux to (seemingly) defend why it doesn't need to be easy to get an AV when the point in my initial rant was about people who come into "Help me with Clam" threads and start saying why you don't need one. I know that the lack of viruses is a selling point of Linux/Ubuntu, and something to take pride in, but if someone *wants* an AV, they don't need a lecture of why they don't *need* one. I realize you edited and added a comment about how you just installed Clam, and how it went alright for you - that is to my benefit, you took your own time to test out installing a program just to help me, and I appreciate it. I don't want to come across as ungrateful or a jerk, I just feel like I have to defend why it is important to some people to have an AV.
Uh, I don't fall back on anything... My statement stands on it's own. I tell people that they don't need an AV _except_ for scanning email, I don't believe people should waste their time unless they need to. I certainly don't give bad advice to people to cover up flaws in installing things... that would be incredibly selfish.

> Just because you don't use it, doesn't mean it shouldn't be supported better. You also don't use email attachments, does that mean I can't? It's a very user-friendly feature that is the first way they recommend you install programs in the help - the easiest, in their words.
Ok lets get something straight... I'm a volunteer, like all other volunteers I support what I feel is the best option (some people support Automatix and I strongly disagree with them on that). Your free to support whatever you like, but it's my opinion that Add/Remove is a very limited program with respect to installing in Ubuntu. I prefer people understand the foundations that form Aptitude and how to use CLI/Synaptic to install anything, it gives them greater control and they will be more likely to be autonomous and able to install anything without questions.

> I also believe in freedom of choice, and one of choices I would make is the user friendly option. Having two ways, the easy way and the right way, really isn't a choice. Just because I elect the dumbed-down interface now doesn't mean I won't take the more advanced route down the road. I'm trying to suggest how Ubuntu can be more friendly to the new user, and you're trying to help the new user become an advanced user. They don't have to be mutually exclusive. Ummm, well the moment you join the dev team you can make it any way you like (i.e. more user friendly)... or start your own project. Suggestions on what should be changed go in the development forum for Gutsy this is the cafe. Secondly, I don't aim to make users advanced, I aim to educate them. If you read my guide you would see I carefully laid out everything to build up and teach them how to use their OS. You don't have to be advanced to use synaptic right, you just have to know what everything does and understand concepts, all of which were in my guide.

> Listen, Starcraft.man, I realize you are trying to help - and I promise I will go read your tutorial right now. Heck, a few months from now I might completely agree with you. But I will no longer be a brand new user then, and essentially that is what my OP was about - a couple ideas that would make it easier and more appealing to new users 1.)There should be an antivirus in Add/Remove 2.) Add/Remove is really nice and I'd like to see more programs in it

I don't think anything can really smooth out the transition from Windows to Linux. They are fundamentally different and have their own pro's and con's, and you have to show users the differences. No matter how much is added to Add/Remove you'll still have folks who don't get it. I try my best to help, remember that I like most folks here are unpaid volunteers... I just suggest/advise with what I know.

---

### Post by Darkcloud on 2007-07-15
Quote:
Listen, Starcraft.man, I realize you are trying to help - and I promise I will go read your tutorial right now. Heck, a few months from now I might completely agree with you. But I will no longer be a brand new user then, and essentially that is what my OP was about - a couple ideas that would make it easier and more appealing to new users 1.)There should be an antivirus in Add/Remove 2.) Add/Remove is really nice and I'd like to see more programs in it >>


This is a really inaccurate statement   by going to my ADD/Remove  and chosing all availiable applications and then typing Clam   guess what shows up   yep thats right  CLAMAV

---

### Post by wolfen69 on 2007-07-15
.

---

### Post by argie on 2007-07-15
Darkcloud, your experience is very strange. I have installed clam in the past. However, I installed only the clamav package. To run the program you have to run clamscan. I never did update it because I was only playing around. Perhaps what you should do is talk to the maintainer of the clam-tk package and tell him to put clamav on the dependencies. All you have to do is select the clam-tk package then and you'll get clamav too.

EDIT: I just checked and you just need to select avscan (the GUI package) to get clam antivirus and the GUI. Synaptic allows for people who don't want the GUI to have exactly that.

---

### Post by igknighted on 2007-07-15
> **keyboardashtray said:**
> Oh here we go with the leet uzer - I thought Ubuntu was about being user friendly Linux? So I make a comment on Synaptic being sloppy, in my opinion - as a brand new user, first impression - and getting me the wrong/bad Clam - which it did - and now I'm not good enough for Linux...pfft. And do a quick search on Clam - I'm not the only one who had trouble here.  And Linux being about choice, I guess you mean your choice? I like Add/Remove - hasn't done me wrong yet, apparently someone higher up the totem pole than myself likes it, because it exists. I'd improve it. But you'd do away with it. Well, as dumb as I might be to you, I guarantee there are plenty more people who have/do/will balk at their first use of Synaptic. 

And obviously you didn't read the OP - clearly the last paragraph says its just an impression and doesn't take into account the traditions or options of the advanced user.

So you'll forgive me if I disregard *your* disclaimer "not intended to be mean".

Umm, you didn't really read my post did you.

1) Add/Remove FAILS to properly install packages a LOT.  Thats why it isn't recommended.  I would bet you that the reason more apps aren't in there is because of this very reason.

2) There are EASIER choices.  First, Klik.  Might not be the best solution for Ubuntu/Xubuntu users because I think it is KDE based, but it downloads a single .klik file and it just works.  No dependencies, no nothing.  Want to get rid of it?  Delete the .klik file.  Done.  It's not super stable like an apt, but if Add/Remove can mess up and bork your system, all you gotta do with Klik is delete the file and try again (or look for it from another source)... no harm done.

3) CNR isn't quite Klik easy, but its better than Add/Remove.  I haven't used it on Ubuntu so I put it last, but it is much more promising.  Plus the repo is bigger.  Stability and whether or not it could screw up apt remains to be seen.

And yes, I still think that of all essential apps on Ubuntu, Synaptic is on the easier end.  Lets fix up gconf and networkmanager before we worry about synaptic, or build a decent 3d Desktop config tool (not a beryl-manager type thing, but to actually configure your system to use it in the first place).  These tools could easily be made, and would do more than ditching synaptic.

Finally, imagine if Synaptic was removed from Ubuntu (the line I wrote my first post about).  How many of those "1337 users" would stay with Ubuntu do you think (Or any distro which removes the advanced tools they use)?  Probably not too many.  Who's gonna write all the how to's then?  Or give aid on the forums?  Those members are at least as important as every new member that starts using Ubuntu.  So in general, getting rid of Synaptic would not be a good idea.

---

### Post by Darkcloud on 2007-07-15
> **argie said:**
> Darkcloud, your experience is very strange. I have installed clam in the past. However, I installed only the clamav package. To run the program you have to run clamscan. I never did update it because I was only playing around. Perhaps what you should do is talk to the maintainer of the clam-tk package and tell him to put clamav on the dependencies. All you have to do is select the clam-tk package then and you'll get clamav too.

EDIT: I just checked and you just need to select avscan (the GUI package) to get clam antivirus and the GUI. Synaptic allows for people who don't want the GUI to have exactly that.

What do you find strange about what I said ?   it was not me complaining that it couldn't be found in ADD/Remove  I just said it is there   that the remark made that it wasn't wasn't correct,

---

### Post by phrostbyte on 2007-07-15
> **keyboardashtray said:**
> Oh here we go with the leet uzer - I thought Ubuntu was about being user friendly Linux? So I make a comment on Synaptic being sloppy, in my opinion - as a brand new user, first impression - and getting me the wrong/bad Clam - which it did - and now I'm not good enough for Linux...pfft. And do a quick search on Clam - I'm not the only one who had trouble here.  And Linux being about choice, I guess you mean your choice? I like Add/Remove - hasn't done me wrong yet, apparently someone higher up the totem pole than myself likes it, because it exists. I'd improve it. But you'd do away with it. Well, as dumb as I might be to you, I guarantee there are plenty more people who have/do/will balk at their first use of Synaptic. 

And obviously you didn't read the OP - clearly the last paragraph says its just an impression and doesn't take into account the traditions or options of the advanced user.

So you'll forgive me if I disregard *your* disclaimer "not intended to be mean".

Is it really that hard to type "apt-get install avscan"?

It seems a lot easier to type then that 10 page rant of yours.

It's not that we are elitist, it's that you are being incredibly ridiculous. If you are going to use Ubuntu today, you are going to use console and you are going to use Synaptic.  If you have a problem with that, feel free to help the Ubuntu development team, or hell make your own Linux distro without Synaptic or command line - or just use Windows. You wont have to worry about Synaptic or other braindead automatic software installs to worry about.

EDIT: 
Any even more ridiculous is that anti-virus is in add/remove.

---

### Post by macogw on 2007-07-15
> **H.E. Pennypacker said:**
> I am of the opinion that Synaptic needs to be removed entirely.  It is far too user-unfriendly to come standard with Ubuntu.  Installing stuff is very easy, and straight forward, but it can use changes, such as getting rid of the left panel, adding more information to the bottom (an application's information), adding a review tab (reviews from other users), several screenshots, and a way to run sudo apt-get clean (a button that runs this command so you don't have to use the terminal - a user should be able to do all package management from Synaptic, and sudo apt-get clean is a glaring omission - remarkable that it is left out).

Synpatic includes all the less-needed-by-regular-users stuff like libraries.  Add/Remove is for regular applications only.  And there is a setting in Synaptic preferences to delete debs after install.  That's what apt-get clean does, and you can set it to do it automatically after each install completes.

---

### Post by ice60 on 2007-07-15
there's a script that puts clam in the right-click menu, and the updater runs in the background so you shouldn't have to worry about that (freshclam). there are some config files in /etc i think too if it's not working correctly.

i haven't read the thread very closely so sorry if i'm not making much sense :)

---

### Post by Darkcloud on 2007-07-15
> **phrostbyte said:**
> Is it really that hard to type "apt-get install avscan"?

It seems a lot easier to type then that 10 page rant of yours.

It's not that we are elitist, it's that you are being incredibly ridiculous. If you are going to use Ubuntu today, you are going to use console and you are going to use Synaptic.  If you have a problem with that, feel free to help the Ubuntu development team, or hell make your own Linux distro without Synaptic or command line - or just use Windows. You wont have to worry about Synaptic or other braindead automatic software installs to worry about.

EDIT: 
Any even more ridiculous is that anti-virus is in add/remove.

well you know something   I don't use AV  because I read it wasn't neccasary  but I did see it in ADD/Remove  what I saw was this  (my screen shot) that SAYS virus scanner  I am guilty of not paying any more attention to it  such as going to the web site  but I am sorry if I know how to read english  and so sorry two people had to get so ruffled about it   look at my screen shot    its in plain english:(

---

### Post by argie on 2007-07-17
> **Darkcloud said:**
> What do you find strange about what I said ?   it was not me complaining that it couldn't be found in ADD/Remove  I just said it is there   that the remark made that it wasn't wasn't correct,

Sorry then. I was under the impression you couldn't get it to work after installing.

---

### Post by keyboardashtray on 2007-07-21
> **starcraft.man said:**
> Well, if you find the Package Manager so sloppy feel free to go code one on your own
> **starcraft.man said:**
> Ummm, well the moment you join the dev team you can make it any way you like

Priceless... a little bit of feedback / criticism and the kid gloves come off...I've heard this strain of logic before, usually from die-hard conservatives in my country when you criticize the administration "If you don't like it, leave!"

> **igknighted said:**
> Add/Remove FAILS to properly install packages a LOT.  Thats why it isn't recommended.  I would bet you that the reason more apps aren't in there is because of this very reason.

Not recommended? Where?
[https://help.ubuntu.com/community/InstallingSoftware#head-15caaf57405bb0e6cf92aa9b5bf4a1a527f1ee6f](https://help.ubuntu.com/community/InstallingSoftware#head-15caaf57405bb0e6cf92aa9b5bf4a1a527f1ee6f)
"Easiest way" The documentations wording, not mine. I just happen to like it too.
> **phrostbyte said:**
> Is it really that hard to type "apt-get install avscan"?

It seems a lot easier to type then that 10 page rant of yours.
So is the message here if a GUI fails, or if you otherwise have any criticism, comment, or complaint about a GUI, don't blame the GUI, because you can use the console? Hmm...ok...so if your car doesn't work, it's ok, just walk!

> **phrostbyte said:**
> It's not that we are elitist, it's that you are being incredibly ridiculous. If you are going to use Ubuntu today, you are going to use console and you are going to use Synaptic.  If you have a problem with that, feel free to help the Ubuntu development team, or hell make your own Linux distro without Synaptic or command line - or just use Windows. You wont have to worry about Synaptic or other braindead automatic software installs to worry about.
And a little more "if you don't like it, leave". I know, I know, I'm being incredibly ridiculous - discussing some first impressions - how dare I? Perhaps I should switch to Sugar, I'm sure you'd agree it is more suited to my capabilities.
Look, it might not be the message here at the forums, but Ubuntu is being touted as the Linux for everybody, including the people who prefer graphic to console. And yes, plenty are saying you *won't* have to use the console. And if it is going to compete, never having to use the console must be an option for some, which leaves me to my original points: more software on Add/Remove is a good thing, would like to see more on there, and Synaptic is intimidating to a rookie user.


> **phrostbyte said:**
> EDIT: 
Any even more ridiculous is that anti-virus is in add/remove.

> **Darkcloud said:**
> well you know something   I don't use AV  because I read it wasn't neccasary  but I did see it in ADD/Remove  what I saw was this  (my screen shot) that SAYS virus scanner  I am guilty of not paying any more attention to it  such as going to the web site  but I am sorry if I know how to read english  and so sorry two people had to get so ruffled about it   look at my screen shot    its in plain english:(

Well, the plain English *I* read said "ClamTK is a **graphical front end** for Clam AV. So take a second look, and if you like, install it on your own, from Add/Remove and tell me, does it work out of the box for you? Because it didn't for me - and don't come back here telling me "well all I had to do was go find the other dependencies and then give it permanent Sudo priviledges for the updating after I updated to the most recent version because some of the definitions won't work with the old file" or some other gobbledegook because I will proudly hand my Moron Medal that you've all bestowed upon me over to you for not understanding out of the box.

Now, I have a confession! There is an antivirus in Add/Remove: Aegis 0.1.1-1. Is it new to the Add/Remove section? I honestly don't know, but I didn't see it back in my OP a week or so ago, and clearly no one in this thread mentioned it by name. Whether it works or not I have yet to see - but my original comments still stand.

---

### Post by starcraft.man on 2007-07-21
> **keyboardashtray said:**
> Priceless... a little bit of feedback / criticism and the kid gloves come off...I've heard this strain of logic before, usually from die-hard conservatives in my country when you criticize the administration "If you don't like it, leave!"


Well, no. I'm telling you your options. I guess it came off a bit wrong or not how I meant... If you really don't like Synaptic, try another package manager. There are at least 5 or 6 major different package managers and systems out there (with different GUIs) and if you find ours not to your liking try one of them (most are in different distros, so you'll have to change to get to try them). Fedora, openSUSE are two major distros (with yum and YAST respectively as their managers) to try (there are many others).  That's a **freedom** you have. Also, if you find things to your liking in Synaptic but want to improve it then join the team (after learning some coding and background) and code fixes and changes, or fork it and make a modified package manager based on it with another team. A third option if your really daring and bold is to make your own manager from scratch but that is probably too much. Those are equally options you can **freely** choose.

You seem to want to infer the worst from my words but I'm really only trying to tell you that Ubuntu is a community project. It makes choices based on what the majority of the community likes, there will always be minority opinions against what choices they make and that's the way it is (like your condemnation of Synaptic). That however has been dealt with, that is why there are so many packaging systems/managers in so many more distros (Linux is about choice after all). So yes, to a certain extent you do have to take Ubuntu "as is" just like if you bought Apple OSX and found a the Dock obnoxious or the Universal menu not to your liking well you bought into it "as that". 

In the end, your entitled to your criticism just like Windows and Apple user's criticize Linux. That doesn't mean serious change will come about though, that's a choice of the community to make.

As for the rest, I leave it to someone else to respond, I was only replying to your remarks on my words. Oh and I don't really know why your resurrecting this thread...

---

### Post by SunnyRabbiera on 2007-07-21
> **H.E. Pennypacker said:**
> I am of the opinion that Synaptic needs to be removed entirely.  It is far too user-unfriendly to come standard with Ubuntu.  Installing stuff is very easy, and straight forward, but it can use changes, such as getting rid of the left panel, adding more information to the bottom (an application's information), adding a review tab (reviews from other users), several screenshots, and a way to run sudo apt-get clean (a button that runs this command so you don't have to use the terminal - a user should be able to do all package management from Synaptic, and sudo apt-get clean is a glaring omission - remarkable that it is left out).
I dont see why Synaptic can be so hard for people, I mean how simplistic can you be without using fancy graphics and all that.
Synaptic is much easier then most of the package managers out there, and I like it better then click n run.
Its certainly better then YAST

---

### Post by kleo skywalker on 2007-07-26
If you haven't got clamav working, here's the simplest GUI way which worked for me (it may not work for you in which case sorry in anticipation): In Synaptic, check clamav and apply - whatever gets selected with it automatically will be ok. Then in add/remove, search for clamav, something called virus scanner will show up, install it. (I know that people have already gone over how to do this using the command-line, but some people like to use it as little as possible.)

---

