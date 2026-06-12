---
title: "Is this system of adding repositories for unusual software installations abit sloppy?"
date: 2009-09-09
forum: The Cafe
---

### Post by hoppipolla on 2009-09-09
I was just thinking about this, I mean like I have found Ubuntu at present VERY easy-to-use and friendly, but isn't it a bit much to expect your average user to add a new repository, and often then a key for authentication, just to search for and install a less common new program?

Surely a better system can be devised - I mean in Windows programs just update independently of others, which has it's pros and cons but at least it means software installations are nice and simple!

It will probably improve as Ubuntu as a distro matures and evolves... what do you think? :)

Hoppi!

---

### Post by blueturtl on 2009-09-09
Adding a new repository is not necessary. You can download and double click to install debs from many repositories without adding them, or use sources such as GetDeb.

---

### Post by hoppipolla on 2009-09-09
> **blueturtl said:**
> Adding a new repository is not necessary. You can download and double click to install debs from many repositories without adding them, or use sources such as GetDeb.

Yes but will they then update themselves? Many programs seem to greatly recommend you add the repository! :)

---

### Post by 23meg on 2009-09-09
[http://ubuntuforums.org/showthread.php?t=1213538](http://ubuntuforums.org/showthread.php?t=1213538)
[https://blueprints.launchpad.net/ubuntu/+spec/apt-firefox-archive-handler](https://blueprints.launchpad.net/ubuntu/+spec/apt-firefox-archive-handler)

---

### Post by Tibuda on 2009-09-09
Developers can add a repository and a key using a deb file. Opera already does this.

---

### Post by snowpine on 2009-09-09
Just because you don't understand something doesn't make it "sloppy." ;)

The "windows method" of surfing the web and downloading random, untrusted applications works in Ubuntu, too. Or, you can use trusted, signed and keyed repositories. The choice is yours...

---

### Post by Screwdriver0815 on 2009-09-09
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

so now with 23meg's posting we have 3 Links who provide information on repositories.

How many does an "average user" need? ah yes I forgot: [www.google,com](www.google,com) and [http://www.google.com/support/websearch/bin/answer.py?hl=en&answer=134479](http://www.google.com/support/websearch/bin/answer.py?hl=en&answer=134479)

oh dear... sometimes I can't help myself and think that anybody thinks that "average users" must be stupid like 10 metres of dirt road. 

Why is it so difficult to search for information regarding a specific topic?

conclusion: no, the way like it is now, is the best.

---

### Post by sertse on 2009-09-09
2meg links point to ways Ubuntu is considering adding external repos easier, answering your topic title. It is a sign that Ubuntu is aware of this issue and is trying to fix it. If you want to help how it go about doing this, go there and participate. 

On principle though, adding PPA is not "easy", *nor is it meant to be* because it's meant to be something that understand what they're doing when doing it. No matter how you twist it, external repos are less "trustworthy" can official ones.

---

### Post by blueturtl on 2009-09-09
> **hoppipolla said:**
> Yes but will they then update themselves? Many programs seem to greatly recommend you add the repository! :)

Well no, you'd have to use repositories for that. 

To counter your idea, built-in updaters are a bad idea because of redundancy. It leads to the same kind of nightmarish bloat that we have on Windows today: the average user's desktop is clogged with little auto-updater applets going off.

So far the best means to accomplish software updates has been to simply allow the operating system's core utilities to take care of the process. Adding a repository really isn't that difficult a task on a modern Linux desktop.

Can you further elaborate why you think repositories are difficult for new users?

---

### Post by Screwdriver0815 on 2009-09-09
> Can you further elaborate why you think repositories are difficult for new users?

[sarcasm]

because the user has to think about what he/she is doing and also has to think about how to do something.
And (to make it far worse) he/she has maybe to search for additional information

[/sarcasm]

---

### Post by ynnhoj on 2009-09-09
> **blueturtl said:**
> So far the best means to accomplish software updates has been to simply allow the operating system's core utilities to take care of the process. Adding a repository really isn't that difficult a task on a modern Linux desktop.

Can you further elaborate why you think repositories are difficult for new users?
i don't think that adding a new repository to the sources list is particularly difficult either; however, i do think that the process could be a bit more seamless. (the things 23meg linked to seem promising)

---

### Post by 3rdalbum on 2009-09-09
> isn't it a bit much to expect your average user to add a new repository, and often then a key for authentication, just to search for and install a less common new program?

You should try compiling from source!

I don't see anything wrong with adding extra repositories, as long as you trust them. They are/can be easy to add - just double-click a small Debian package that adds the repository and key, and then the program is available in Synaptic.

---

### Post by bluenova on 2009-09-09
Whilst I love the way Debian based systems handle software installation and updates (It's the reason I use Ubuntu over a non-deb based system) the method of authenticating a PPA is far from streight forward and could use some revising. Perhaps I'm missing something obvious but I always have to copy the key into a text file, save it then go to the import screen and import the text file, then delete it again. So why when I click add key can it not open a text box to paste the key into directly rather than faffing about with text files? Yes I know I could use the terminal but as I don't add PPA's everyday I would have to look up the syntax which is silly.

[quote=3rdalbum]They are/can be easy to add - just double-click a small Debian package that adds the repository and key, and then the program is available in Synaptic.
[/quote]
Where can this magical .deb be found on a PPA page?

---

### Post by Screwdriver0815 on 2009-09-09
> **bluenova said:**
> Whilst I love the way Debian based systems handle software installation and updates (It's the reason I use Ubuntu over a non-deb based system) the method of authenticating a PPA is far from streight forward and could use some revising. Perhaps I'm missing something obvious but I always have to copy the key into a text file, save it then go to the import screen and import the text file, then delete it again. So why when I click add key can it not open a text box to paste the key into directly rather than faffing about with text files? Yes I know I could use the terminal but as I don't add PPA's everyday I would have to look up the syntax which is silly.


Where can this magical .deb be found on a PPA page?

yes, I think you miss something obvious. On the site, where the deb-line for adding a ppa to the software source is provided, there is an explaination, how to easily install the key. Its just a command, to be copy-pasted into a terminal.

something in this style

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 12345678
```

whilst replacing "12345678" with the actual key-combination. It is really easy. Just click on "what is this?" next to the key-combination in the ppa-Site - in the small window, which pops up, everything is explained again.

---

### Post by Skripka on 2009-09-09
> **3rdalbum said:**
> You should try compiling from source!


Yea, that is one thing I hated about how *buntu does things.  They make it completely un-elegant to compile source, and update apps installed from source code.

---

### Post by steveneddy on 2009-09-09
Here's my .02

I install ppa's to add software that I either require or that I want.

ppa's will install automatically with the update manager and i don't have to think about updating at a later date.

I believe that only an advanced user would choose to install the ppa anyway. 

Some people prefer to double click a .deb and install in this manner, but when there is an update, you must redownload the .deb again and reinstall, again.

ppa's are quick, easy and for the advanced user (my opinion)

If I like the version of the software in a ppa, I just comment out the line and it won't update.

AAMOF, I lock down my machine from kernel, graphics driver and network driver updates when working on a critical project. Once the machine is where I need it I don't need updated software unless it will help me.

---

### Post by hoppipolla on 2009-09-09
I'm not saying this stuff was hard for ME... (and yes I have compiled software and even kernels from source) I'm saying it may be a bit much to expect someone with no real computer knowledge to do all this when on Windows all you need to do is click.

I'm glad that plans are being made to make the process a little more seamless, as most of the user-experience in a modern Ubuntu desktop is very friendly now :)

And I'm sorry, the PPA repository was a bad example, but this issue does exist for more standard program installations as well.

---

### Post by hoppipolla on 2009-09-09
> **blueturtl said:**
> 
To counter your idea, built-in updaters are a bad idea because of redundancy. It leads to the same kind of nightmarish bloat that we have on Windows today: the average user's desktop is clogged with little auto-updater applets going off.


It's bloated at times, but it IS simpler in my opinion.. =\

---

### Post by Tibuda on 2009-09-09
> **hoppipolla said:**
> I'm not saying this stuff was hard for ME... (and yes I have compiled software and even kernels from source) I'm saying it may be a bit much to expect someone with no real computer knowledge to do all this when on Windows all you need to do is click.

Now ask yourself: "someone with no real computer knowledge" really need/want the latest version from an app, if it already does everything he/she wants?

The only case I can think is for IM, because those proprietary networks (MSN/Yahoo) are always changing the protocols to break third-party clients like Pidgin.

---

### Post by hoppipolla on 2009-09-09
> **danielrmt said:**
> Now ask yourself: "someone with no real computer knowledge" really need/want the latest version from an app, if it already does everything he/she wants?

The only case I can think is for IM, because those proprietary networks (MSN/Yahoo) are always changing the protocols to break third-party clients like Pidgin.

So, we should not give casual users the opportunity to install software they discover online on their computer? o.O lol

I think the solution is in refining the process, I mean as people have implied this may be underway anyway - a lot of the software installation system is receiving an overhaul I believe :)

---

### Post by Regenweald on 2009-09-09
> **hoppipolla said:**
> I'm not saying this stuff was hard for ME... (and yes I have compiled software and even kernels from source) I'm saying it may be a bit much to expect someone with no real computer knowledge to do all this when on Windows all you need to do is click.

I'm glad that plans are being made to make the process a little more seamless, as most of the user-experience in a modern Ubuntu desktop is very friendly now :)

And I'm sorry, the PPA repository was a bad example, but this issue does exist for more standard program installations as well.

I don't think that it is very practical nor sensible to criticize the repository system based on a model as insecure and troublesome and windows. The existing system in place and the new mechanism for adding ppas encourages at least a low level of system understanding and administration.

A user should always be aware of where their software is coming from. please put forward a viable new model rather than the tiresome windows comparison.

---

### Post by blueturtl on 2009-09-09
> **hoppipolla said:**
> It's bloated at times, but it IS simpler in my opinion.. =\

Someone earlier in the thread said that repositories can be added via debs also, so this means that the application will in fact update after it has been installed "the Windows way".

I searched for an example and came up with at least one: Google Chrome.

If you install Chrome from Google's website (download deb and double click) you will also get the Google repository which means that apt-get will automatically update Chrome too.

I guess this means that we should just expect vendors outside the community to use this feature when packaging their applications.

Simple enough? :P

edit:

I'm correcting myself here too, I previously thought that double clicking a deb would automatically mean there'd be no way to update the software automatically from thereon.

---

### Post by hoppipolla on 2009-09-09
> **blueturtl said:**
> Someone earlier in the thread said that repositories can be added via debs also, so this means that the application will in fact update after it has been installed "the Windows way".

I searched for an example and came up with at least one: Google Chrome.

If you install Chrome from Google's website (download deb and double click) you will also get the Google repository which means that apt-get will automatically update Chrome too.

I guess this means that we should just expect vendors outside the community to use this feature when packaging their applications.

Simple enough? :P

Perfect :)

Although I am also sure the Ubuntu guys will present a way of actually adding repositories easier in future too, such as simply clicking them in Firefox :)

All in good time, they're doing a great job anyway and things take time!

---

### Post by koenn on 2009-09-09
> **hoppipolla said:**
> I'm not saying this stuff was hard for ME...  I'm saying it may be a bit much to expect someone with no real computer knowledge to do all this when on Windows all you need to do is click.

I happened to be helping someone with no real computer knowledge, recently. Her problem was that people would send het pdf files, and she couldn't open them, and every time this happend  windows (XP) kept asking questions she didn't understand, and so on, and on and on. 
So I downloaded and installed Acrobat Reader for her :)

I've head similar experience with Office 2003 users that receive Office 2008 docx files and can't quite figure out they need to find and install the converters that MS provides.

Conclusion: someone with no real computer won't be able to install software on Windows either  ( at best they'll get toolbars and browser helpers installed because that is actually easier than preventing those things from installing themselves)

So, If someone can work out the "figure out what you need, search the web for it , download, install" thing on Windows, they'll probably get the hang of using repo's in Ubuntu without much difficulty, and even if they don't, they'll still have a fully functioning system *and*  additional software in Add/Remove. 

So which one here 'just works' ?

---

### Post by hoppipolla on 2009-09-09
> **koenn said:**
> I happened to be helping someone with no real computer knowledge, recently. Her problem was that people would send het pdf files, and she couldn't open them, and every time this happend  windows (XP) kept asking questions she didn't understand, and so on, and on and on. 
So I downloaded and installed Acrobat Reader for her :)

I've head similar experience with Office 2003 users that receive Office 2008 docx files and can't quite figure out they need to find and install the converters that MS provides.

Conclusion: someone with no real computer won't be able to install software on Windows either  ( at best they'll get toolbars and browser helpers installed because that is actually easier than preventing those things from installing themselves)

So, If someone can work out the "figure out what you need, search the web for it , download, install" thing on Windows, they'll probably get the hang of using repo's in Ubuntu without much difficulty, and even if they don't, they'll still have a fully functioning system *and*  additional software in Add/Remove. 

So which one here 'just works' ?

We still should make it as simple as possible, without sacrificing security or functionality :)

---

### Post by Screwdriver0815 on 2009-09-09
> **hoppipolla said:**
> We still should make it as simple as possible, without sacrificing security or functionality :)

it already is, my friend ;) :D

what is the common wording? ah yes: **if it ain't broke, don't fix it!**

---

### Post by hoppipolla on 2009-09-09
> **Screwdriver0815 said:**
> it already is, my friend ;) :D

what is the common wording? ah yes: **if it ain't broke, don't fix it!**

I dunno man, I think we'll have to agree to disagree on this!! :)

---

### Post by Screwdriver0815 on 2009-09-09
> **hoppipolla said:**
> I dunno man, I think we'll have to agree to disagree on this!! :)

okay, let's do this then :D

---

### Post by zekopeko on 2009-09-09
> **koenn said:**
> I happened to be helping someone with no real computer knowledge, recently. Her problem was that people would send het pdf files, and she couldn't open them, and every time this happend  windows (XP) kept asking questions she didn't understand, and so on, and on and on. 
So I downloaded and installed Acrobat Reader for her :)

I've head similar experience with Office 2003 users that receive Office 2008 docx files and can't quite figure out they need to find and install the converters that MS provides.

Conclusion: someone with no real computer won't be able to install software on Windows either  ( at best they'll get toolbars and browser helpers installed because that is actually easier than preventing those things from installing themselves)

So, If someone can work out the "figure out what you need, search the web for it , download, install" thing on Windows, they'll probably get the hang of using repo's in Ubuntu without much difficulty, and even if they don't, they'll still have a fully functioning system *and*  additional software in Add/Remove. 

So which one here 'just works' ?

The problem your friend had is easily fixable with Packagekit. You just look at the MIME type and offer to install applications that can open said type. This would rock and I'm sure that Ubuntu Software Store is going to get it at some point.

---

### Post by zekopeko on 2009-09-09
> **Screwdriver0815 said:**
> it already is, my friend ;) :D

what is the common wording? ah yes: **if it ain't broke, don't fix it!**

That phrase is a road into mediocrity. Thinking that the current way is the best is simply absurd. I'm sure that people before thought that the command line is the best user interface on the planet at some point. Yet I'm betting you are very much happy that somebody decided that the situation is far from perfect and made steps to redeem it.

---

### Post by Screwdriver0815 on 2009-09-09
> **zekopeko said:**
> That phrase is a road into mediocrity. Thinking that the current way is the best is simply absurd. I'm sure that people before thought that the command line is the best user interface on the planet at some point. Yet I'm betting you are very much happy that somebody decided that the situation is far from perfect and made steps to redeem it.

okay, when you say that thinking that the current way is the best is absurd, the current status must be hell on earth then.

This is ridiculous.

the current way is nothing more than following the link to the ppa, copying a deb-line into the software source manager and running a command to get the key working. And the last step you can leave away if you don't care about warnings.

The other way, however it should look like, is "I just want to click on an icon" - without switching on the brain-engine. 

This is the way, which leads into stupid installing of everything and this way prepares the road for security risks.

Users who do not think about what they are doing.

**THIS** is absurd

---

### Post by doorknob60 on 2009-09-09
It's not bad, but I prefer AUR, it's just awesome with yaourt, since everything's all in one spot instead of spread out among hundreds of PPAs. It would be nice if there was a more automated way of adding repositories though, maybe something similar to apturl but to add repos? That would be cool.

---

### Post by hoppipolla on 2009-09-09
> **Screwdriver0815 said:**
> okay, when you say that thinking that the current way is the best is absurd, the current status must be hell on earth then.

This is ridiculous.

the current way is nothing more than following the link to the ppa, copying a deb-line into the software source manager and running a command to get the key working. And the last step you can leave away if you don't care about warnings.

The other way, however it should look like, is "I just want to click on an icon" - without switching on the brain-engine. 

This is the way, which leads into stupid installing of everything and this way prepares the road for security risks.

Users who do not think about what they are doing.

**THIS** is absurd

I'm afraid I totally agree with zekopeko here (cool name hehe :) )

Can you imagine a little old lady, who has just had her nice new desktop pc set up so she can write her letters, or contact her friend by email, even beginning to comprehend how to install a deb line repository into Synaptic, or an Authentication key, or opening a prompt and typing sudo apt-get update ?

My point is, if it can be made simpler, which it can, why not do it? It is silly to leave complications like this in day-to-day use of the OS, as most people just don't want/need it. But, again, we may have to agree to disagree :)

---

### Post by Screwdriver0815 on 2009-09-10
> **hoppipolla said:**
> I'm afraid I totally agree with zekopeko here (cool name hehe :) )

Can you imagine a little old lady, who has just had her nice new desktop pc set up so she can write her letters, or contact her friend by email, even beginning to comprehend how to install a deb line repository into Synaptic, or an Authentication key, or opening a prompt and typing sudo apt-get update ?

My point is, if it can be made simpler, which it can, why not do it? It is silly to leave complications like this in day-to-day use of the OS, as most people just don't want/need it. But, again, we may have to agree to disagree :)
okay, but beside agreeing to disagree:

seriously: why should an old Lady add a ppa? To write a letter? In Ubuntu and the normal software repos, there are TONS of software for the average user. 
Now ask yourself seriously: when and why did you ever add an additional repo? I did it three times in my whole Linux-life: Medibuntu, ppa for the Arora browser and ppa for the KDE 4.3 backports. Thats it. 
The average user would do it once, for Medibuntu. And as nearly nobody talks about Medibuntu and where to get it, the user has to do research on this anyway. And during this research, he for sure finds out how to install a repo. Besides that, it is explained in the Ubuntu Helpcenter and also in the wiki and tutorials all over the place.

my point is: it is simple now. You have the instructions on how to do it available and it is reasonably safe. 
When you do it "easier", whatever this means, you always have the risk of security flaws and (what is more important) the user does not think about what he is doing anymore. So then we are on the Windows track: failure messages won't be read anymore, just click "ok"... and so on... and then we have the rootkits in the systems. 
And when this happens, these guys who do not want to think about what they are doing with a computer, are the first in the row to scream and yell, what a stupid operating system this Linux is.

and that's why I say: if it ain't broke, don't fix it. Because it is not broken.

Do you get my point?

but anyway: we still can agree to disagree ;) :D

---

### Post by hoppipolla on 2009-09-10
> **Screwdriver0815 said:**
> okay, but beside agreeing to disagree:

seriously: why should an old Lady add a ppa? To write a letter? In Ubuntu and the normal software repos, there are TONS of software for the average user. 
Now ask yourself seriously: when and why did you ever add an additional repo? I did it three times in my whole Linux-life: Medibuntu, ppa for the Arora browser and ppa for the KDE 4.3 backports. Thats it. 
The average user would do it once, for Medibuntu. And as nearly nobody talks about Medibuntu and where to get it, the user has to do research on this anyway. And during this research, he for sure finds out how to install a repo. Besides that, it is explained in the Ubuntu Helpcenter and also in the wiki and tutorials all over the place.

my point is: it is simple now. You have the instructions on how to do it available and it is reasonably safe. 
When you do it "easier", whatever this means, you always have the risk of security flaws and (what is more important) the user does not think about what he is doing anymore. So then we are on the Windows track: failure messages won't be read anymore, just click "ok"... and so on... and then we have the rootkits in the systems. 
And when this happens, these guys who do not want to think about what they are doing with a computer, are the first in the row to scream and yell, what a stupid operating system this Linux is.

and that's why I say: if it ain't broke, don't fix it. Because it is not broken.

Do you get my point?

but anyway: we still can agree to disagree ;) :D

But WHY make it complex? Why?  What is the ADVANTAGE to making this lesser-used feature complex? Surely the OS needs to be the best and easiest it can be...

I would be willing to bet pretty much anything that Canonical is actually working on this issue anyway... lol

Besides, most changes in the OS come down to making previously manual linux OS routines automatic... I think this will end up being one of many o.O

---

### Post by Screwdriver0815 on 2009-09-10
> **hoppipolla said:**
> But WHY make it complex? Why?  What is the ADVANTAGE to making this lesser-used feature complex? Surely the OS needs to be the best and easiest it can be...

I would be willing to bet pretty much anything that Canonical is actually working on this issue anyway... lol

Besides, most changes in the OS come down to making previously manual linux OS routines automatic... I think this will end up being one of many o.O

it is NOT complex ;) It is an routine which has to be followed. Like doing defrag, scanning virus and chkdisk in Windows. There nobody is complaining about... why? Its a stupid task isn't it? No, "it has to be done to maintain the system"...

so it is with adding repos: it needs to make sure that security is maintained 

I repeat myself: 

1. adding a repo for an average user... it is once in a liftime

2. doing this is copying a deb line and a terminal command - thats it, in medibuntu, you even don't need to do the terminal command, its just installing the medibuntu keyring...

how do you want to have it?

just clicking on an icon? No key signed for security? No asking for the root password? each and every hacker should be able to create an automated repo-adder?

why should we then have software repos? Then we also could surf the internet and install all the packages from dubious sites... like in windows... 

when you ask, what the advantage is, in doing it "complex": I would like to ask you: how do you want to do it "less complex" and in the same time maintain the security for the user?

and complex... it sounds like adding a repo is rocket science these times... :lolflag: SCNR

---

### Post by zekopeko on 2009-09-10
> **Screwdriver0815 said:**
> it is NOT complex ;) It is an routine which has to be followed. Like doing defrag, scanning virus and chkdisk in Windows. There nobody is complaining about... why? Its a stupid task isn't it? No, "it has to be done to maintain the system"...

Users shouldn't defrag,chkdsk and scan for viruses. The system should do it for them in a simple and invisible way.

> so it is with adding repos: it needs to make sure that security is maintained 

I repeat myself: 

1. adding a repo for an average user... it is once in a liftime

2. doing this is copying a deb line and a terminal command - thats it, in medibuntu, you even don't need to do the terminal command, its just installing the medibuntu keyring...

how do you want to have it?

just clicking on an icon? No key signed for security? No asking for the root password? each and every hacker should be able to create an automated repo-adder?

why should we then have software repos? Then we also could surf the internet and install all the packages from dubious sites... like in windows... 

when you ask, what the advantage is, in doing it "complex": I would like to ask you: how do you want to do it "less complex" and in the same time maintain the security for the user?

and complex... it sounds like adding a repo is rocket science these times... :lolflag: SCNR

Your whole problem is that you saw a potential security problem and then, instead of trying to solve the security implication, you decided that the best solution is to simply leave it in it's user-unfriendly state and hope that it will stop people from adding PPAs.

The Ubuntu developers have already found a couple of solutions to said security problems. Read the blueprints on LP about apt.

---

### Post by Screwdriver0815 on 2009-09-10
> **zekopeko said:**
> 
Your whole problem is that you saw a potential security problem and then, instead of trying to solve the security implication, you decided that the best solution is to simply leave it in it's user-unfriendly state and hope that it will stop people from adding PPAs.

The Ubuntu developers have already found a couple of solutions to said security problems. Read the blueprints on LP about apt.

no the current way is not made in the intention to "stop users from doing this". BTW: this is ridiculous again... 

The current way is a procedure, which has to be followed: introduce the repo to the package manager and adding a **SECURITY** key. And I still ask myself: what the hell is difficult in this?

adding a ppa: on the site, where you copy the deb-line, is **WRITTEN AND EXPLAINED** how to add this ppa. Why the hell can't a user open his eyes and read **two lines** of text? Is this really too much? Really? Seriously? Why do you get up then in the morning? Its too much work! 

additionally it is written down here [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) additionally it is written down in the ubuntu helpcenter (installed on each ubuntu system) in the topic "adding, updating, removing applications"

sorry, I really don't get this. And I always ask myself: why do thousends of people sit down and write a documentation when the user

1. does not read it

2. is too lazy to learn how to do things and always needs big windows "jumping into his face" to at least recognise things

I am really curious how the Canonical guys have "fixed" this "bug". If it is the same as with the update notifications, then I have to find a workaround again. 
I rather would like to see that real bugs are fixed, instead doing things which are solved by simple reading.

---

### Post by hoppipolla on 2009-09-10
Screwdriver man, you've lost lol  They're doing it anyway lol

---

### Post by Screwdriver0815 on 2009-09-10
> **hoppipolla said:**
> Screwdriver man, you've lost lol  They're doing it anyway lol

its okay for me. If it is like a stupid windows-thing or a security risk, I will find a way to the old way of doing it ;) :D

but my general plea to "average users" and new users and so on is:

please open your mind, please open your eyes, please read documentation (its not done because the author was bored), please think about what you are doing, please do not try to re-educate Linux to a second windows (because Linux exists because it is different).... to be continued...

---

### Post by SunnyRabbiera on 2009-09-10
Personally I like the idea of extra repositories, most of them are trustworthy anyway.

---

### Post by blueturtl on 2009-09-10
[LIST]
[*]System -> Administration -> Software Sources
[*]Click on the 'add' button.
[*]Copy & paste the repository address from the website that you found it.
[*]Click on Ok.
[/LIST]

I can't see how it could get any simpler than this besides including the repositories in a deb file that you just download a double click (which is also possible already!).

edit: Ok, being able to click on a repository address via a web browser might be a feasible way to make it even more straight forward.

---

### Post by zekopeko on 2009-09-10
> **blueturtl said:**
> [LIST]
[*]System -> Administration -> Software Sources
[*]Click on the 'add' button.
[*]Copy & paste the repository address from the website that you found it.
[*]Click on Ok.
[/LIST]

I can't see how it could get any simpler than this besides including the repositories in a deb file that you just download a double click (which is also possible already!).

edit: Ok, being able to click on a repository address via a web browser might be a feasible way to make it even more straight forward.

That's what they want to do (your edit part). A simple apt url for people to click, add the ppa and install the package or update the package(s) contained in the PPA.
The security problem (e.g. trust) would be done with having keys already in the keyring for some of the official PPAs (like the ones from Ubuntu devs or from creators of software).
You could also have rating systems for PPAs and sharing options to know if any of your friend use that particular PPA.

---

### Post by zekopeko on 2009-09-10
> **Screwdriver0815 said:**
> its okay for me. If it is like a stupid windows-thing or a security risk, I will find a way to the old way of doing it ;) :D

but my general plea to "average users" and new users and so on is:

please open your mind, please open your eyes, please read documentation (its not done because the author was bored), please think about what you are doing, please do not try to re-educate Linux to a second windows (because Linux exists because it is different).... to be continued...

If the user has to read the documentation to do a basic operation I consider that a bad usability design. Documentation should only supplement the user interface for complex operations, most of the things the users want to do should be simple and intuitive.

And I'm very much opposed to the whole "Linux isn't Windows so let's make everything either different or complex to do". If somebody does something better then Linux does then we should re-evaluate how we do it. This whole "we must not copy Windows or we are tainted" attitude is very counter-productive for end users.

---

### Post by Screwdriver0815 on 2009-09-10
> **zekopeko said:**
> If the user has to read the documentation to do a basic operation I consider that a bad usability design. Documentation should only supplement the user interface for complex operations, most of the things the users want to do should be simple and intuitive.

And I'm very much opposed to the whole "Linux isn't Windows so let's make everything either different or complex to do". If somebody does something better then Linux does then we should re-evaluate how we do it. This whole "we must not copy Windows or we are tainted" attitude is very counter-productive for end users.

ah okay... so when you don't know how to do certain things in Windows... this is simply not possible and even when there are things, you don't know: the system is so designed that Aunt Minny can easily fullfill every task, right? :lolflag:
No windows user has ever learned how to install software. No, this is grown into the genetic code of any person on this planet, right? :lolflag:

adding a software source is no "every day task". An "every day task" is surfing the internet, writing letters, playing games.

How many software sources do you have enabled? 

In the german ubuntuusers portal there are always warnings, to not add too many software sources and especially no unknown sources because they can compromise the system. 
Face it! Adding software sources randomly is a security risk!

> "Linux isn't Windows so let's make everything either different or complex to do"

this is ridiculous and I think you know that. Because it is not like that. Linux has a task: to be safe. When your sentence means: lets do it like windows, even when we get into the virus, rootkit and spyware hell, just for the sake of being "userfriendly" and just for the fact that the user has not to inform himself about how things to do and about the system in general: then please, please use your favourite system! Its not Linux, for sure.

---

### Post by blueturtl on 2009-09-10
> **zekopeko said:**
> If the user has to read the documentation to do a basic operation I consider that a bad usability design. Documentation should only supplement the user interface for complex operations, most of the things the users want to do should be simple and intuitive.

And I'm very much opposed to the whole "Linux isn't Windows so let's make everything either different or complex to do". If somebody does something better then Linux does then we should re-evaluate how we do it. This whole "we must not copy Windows or we are tainted" attitude is very counter-productive for end users.

You're right you know, but in this case we're already ahead of the competition (repositories and debs are simpler than the exe file mess on Windows).

However I do share the concern of Screwdriver0815 that making things any easier than they already are will head us down the path of bad security. I'm not sure I'd want a person who can't handle the current procedure (a simple copy&paste!) administering a computer in this way.

Is click-to-add repository really any safer than ActiveX or .exe on Windows?

---

### Post by zekopeko on 2009-09-10
> **blueturtl said:**
> You're right you know, but in this case we're already ahead of the competition (repositories and debs are simpler than the exe file mess on Windows).

Repositories are a great way of having a single update mechanism. But they aren't perfect. What if I want to install a newer version of an app that has a great deal of newer versions of dependencies that are shared with many apps on my system? The potential for breaking things goes through the roof.

> However I do share the concern of Screwdriver0815 that making things any easier than they already are will head us down the path of bad security. I'm not sure I'd want a person who can't handle the current procedure (a simple copy&paste!) administering a computer in this way.

Copy&paste is a dangerous method of doing anything when system level commands are in play. A few months ago there was the whole "sudo rm -rf /" thing that resulted in at least one individual deleting her's entire system. There was no warning what that command can do to the system.

Making things hard for users is also a security risk since users want to do things and will find ways to do them. And there are always people that want to "help" with "sudo rm -rf /". Isn't it better to make things simple for users in a secure and officially supported manner?

Copy&pasting something into the console isn't going to pop-up a warning that this is a security risk since we can't know what the user wants to do. But by clicking on a PPA link we know what the user wants to do and can take corrective measures to stop any mistakes from happening and ensure their safety.

The spec for adding PPAs with apt url links is seriously considering all the implications of such a decision. And they have provided a way to make users as safe as possible from potential mistakes. Actually they didn't implement this since they are still developing security model for such usage.

> Is click-to-add repository really any safer than ActiveX or .exe on Windows?

Is a deb any safer then a .exe? If it came from an Ubuntu approved repository it is far safer then if it came from a random blog on the internet. Read the blueprint specs for apt-url and you will understand that security is the primary concern of developers.

---

### Post by zekopeko on 2009-09-10
> **Screwdriver0815 said:**
> ah okay... so when you don't know how to do certain things in Windows... this is simply not possible and even when there are things, you don't know: the system is so designed that Aunt Minny can easily fullfill every task, right?
No windows user has ever learned how to install software. No, this is grown into the genetic code of any person on this planet, right?

adding a software source is no "every day task". An "every day task" is surfing the internet, writing letters, playing games.

Easy installation of software is being done with the Ubuntu Software Store.
And your argument is that just because a majority of users doesn't install applications the task should be hard to accomplish?

> How many software sources do you have enabled? 

In the german ubuntuusers portal there are always warnings, to not add too many software sources and especially no unknown sources because they can compromise the system. 
Face it! Adding software sources randomly is a security risk!

You are acting like there is no security model planned if there is going to be easy adding of PPAs. You didn't even read the specs for apt-url. And yes it's always a security risk when adding software. It could be either intentional or a bug. But the risk is always there no matter the trust.


> 
this is ridiculous and I think you know that. Because it is not like that. Linux has a task: to be safe. When your sentence means: lets do it like windows, even when we get into the virus, rootkit and spyware hell, just for the sake of being "userfriendly" and just for the fact that the user has not to inform himself about how things to do and about the system in general: then please, please use your favourite system! Its not Linux, for sure.

No, Linux doesn't have a task of being safe. That's just a consequence of the operating system model it is being built on. And has it ever occurred to you that perhaps having a 1-2% share has something to do with virtual non-existence of viruses and rootkits for Linux?
Perhaps Linux's model isn't all that great but nobody took the time to properly abuse it?

---

### Post by Screwdriver0815 on 2009-09-10
> **zekopeko said:**
> Repositories are a great way of having a single update mechanism. But they aren't perfect. What if I want to install a newer version of an app that has a great deal of newer versions of dependencies that are shared with many apps on my system? The potential for breaking things goes through the roof.


ah, okay... thats what I mean...and additionlly: Rootkits, viruses... but this is still better than "intentionally doing things wrong = not the windows way", right?

> **zekopeko said:**
> 
Copy&paste is a dangerous method of doing anything when system level command are in play. A few months ago there was the whole "sudo rm -rf /" thing that resulted in at least one individual deleting her's entire system. There was no warning what that command can do to the system.

Making things hard for users is also a security risk since users want to do things and will find ways to do them. And there are always people that want to "help" with "sudo rm -rf /". Isn't it better to make things simple for users in a secure and officially supported manner?


copy-paste in general is no security risk. Copy-paste **WITHOUT** **thinking** - this is a security risk

and I repeat myself: the current way is **NOT** hard. It requires thinking and thats too much effort...

> **zekopeko said:**
> 
Copy&pasting something into the console isn't going to pop-up a warning that this is a security risk since we can't know what the user wants to do. But by clicking on a PPA link we know what the user wants to do and can take corrective measures to stop any mistakes from happening and ensure their safety. 


copy pasting this command to add the keyring requires sudo-permissions. When asked for the root-password, the user (assuming he has a brain) knows that he can damage the system. So this "security risk" is at a certain minimum.

Ah yes, I forgot: How the hell can this with the sudo be??? adding a repo is a basic operation, like sending an email and it has zero influence on the system!! Am I right? :lolflag:



> **zekopeko said:**
> 
Is a deb any safer then a .exe? If it came from an Ubuntu approved repository it is far safer then if it came from a random blog on the internet. Read the blueprint specs for apt-url and you will understand that security is the primary concern of developers.

no, a .deb is not safer than an .exe. Thats why you always should install .deb's from a trusted source. Thats why repos exist, thats why keyrings exist for these repos... but... no its not right because it is "difficult"

I still hope that Ubuntu does not risk the security and with it its reputation. This would be a huge pitty.

---

### Post by Screwdriver0815 on 2009-09-10
> **zekopeko said:**
> Easy installation of software is being done with the Ubuntu Software Store.
And your argument is that just because a majority of users doesn't install applications the task should be hard to accomplish?


the only answer on this is (again): ridiculous.

> **zekopeko said:**
> 
You are acting like there is no security model planned if there is going to be easy adding of PPAs. You didn't even read the specs for apt-url. And yes it's always a security risk when adding software. It could be either intentional or a bug. But the risk is always there no matter the trust.

I don't trust this security model because the old way is proven to be secure. Additionally I think that this is an answer on a question which was never asked. Waste of development capacity. Because it is not necessary. 



> **zekopeko said:**
> 

No, Linux doesn't have a task of being safe. That's just a consequence of the operating system model it is being built on. And has it ever occurred to you that perhaps having a 1-2% share has something to do with virtual non-existence of viruses and rootkits for Linux?
Perhaps Linux's model isn't all that great but nobody took the time to properly abuse it?

guess why this model was built like this? For the sake of being complicated? For sure! :lolflag:
And: no, it does not have anything to do with a marketshare. Imagine what would be the reputation of a hacker who has cracked the "secure" Linux? He will be a hero among his friends.
There are a number of rootkits out there. And they easily install from untrustworthy sources.

---

### Post by purgatori on 2009-09-10
I'd say yes... I don't mind having repositories for things like Google Chrome, but my beef with ppas and such is that they can often upgrade packages during a general upgrade, which you might not necessarily wanted to be replaced by unofficial packages. If there's something that I want that's not in the repos, I generally prefer to install from a deb, or build from source.

---

### Post by Screwdriver0815 on 2009-09-10
> or build from source

[sarcasm]
as I don't know how to do this, I assume an "average user" also doesn't know how to do this... therefore this opportunity should be forbidden and banned from the system
[/sarcasm]

:lolflag:

:D

---

### Post by hoppipolla on 2009-09-10
I am out of this debate, it's become so silly it's practically painful to read!

They are doing it anyway and I believe the reasons are sound.. like it or lump it, Ubuntu is becoming simpler and easier for the end-user with every release, including the way software is installed and repositories are handled and added to the system. :)


EDIT -- And sorry if that sounded blunt lol, I agree completely with everything zekopeko has said :)

---

### Post by zekopeko on 2009-09-10
> **Screwdriver0815 said:**
> [sarcasm]
as I don't know how to do this, I assume an "average user" also doesn't know how to do this... therefore this opportunity should be forbidden and banned from the system
[/sarcasm]

You really are dense. Nobody wants to remove the ability to add repos by copy&pasting them to the sources.list or software sources. Devs just want to have a simpler and more secure way of doing it graphically.

---

### Post by zekopeko on 2009-09-10
> **hoppipolla said:**
> I am out of this debate, it's become so silly it's practically painful to read!

They are doing it anyway and I believe the reasons are sound.. like it or lump it, Ubuntu is becoming simpler and easier for the end-user with every release, including the way software is installed and repositories are handled and added to the system. :)


EDIT -- And sorry if that sounded blunt lol, I agree completely with everything zekopeko has said :)

Agreed. I guess I'm just to masochistic for my own good :)

---

### Post by aysiu on 2009-09-10
I have an idea.

You know how when you double-click a .deb file, GDebi launches and resolves dependencies for you?

What if the .deb specification was modified so as to include a repository line as well?

GDebi could then double-check that you have the appropriate repository for that file already in your /etc/apt/sources.list file, or prompt you to add it.

---

### Post by hoppipolla on 2009-09-10
> **aysiu said:**
> I have an idea.

You know how when you double-click a .deb file, GDebi launches and resolves dependencies for you?

What if the .deb specification was modified so as to include a repository line as well?

GDebi could then double-check that you have the appropriate repository for that file already in your /etc/apt/sources.list file, or prompt you to add it.

Exactly :)  Personally, I hope this is the kind of thing they have in the works, although, as we have discussed, some .debs may already have it?

Anyway, I hope things do change a bit and I am actually really looking forward to seeing the whole OS become steadily more user-friendly :)

---

### Post by Tibuda on 2009-09-10
> **aysiu said:**
> I have an idea.

You know how when you double-click a .deb file, GDebi launches and resolves dependencies for you?

What if the .deb specification was modified so as to include a repository line as well?

GDebi could then double-check that you have the appropriate repository for that file already in your /etc/apt/sources.list file, or prompt you to add it.

It already can. Some debs, like Opera and Google Chrome (not Chromium) install a file in /etc/apt/sources.list.d directory with the "deb" line you paste in Software Sources, so it can update itself using ubuntu update manager.

This is a file created when I installed Opera:
```
$ cat /etc/apt/sources.list.d/opera.list
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades

deb http://deb.opera.com/opera/ stable non-free

# The line above will make sure you get all final public releases.
# Uncomment the following line if you want to get alpha and beta
# releases, too.

# deb http://deb.opera.com/opera-beta/ stable non-free
```

---

### Post by aysiu on 2009-09-10
> **danielrmt said:**
> It already can. Some debs, like Opera and Google Chrome (not Chromium) install a file in /etc/apt/sources.list.d directory with the "deb" line you paste in Software Sources, so it can update itself using ubuntu update manager.

This is a file created when I installed Opera:
```
$ cat /etc/apt/sources.list.d/opera.list
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades

deb http://deb.opera.com/opera/ stable non-free

# The line above will make sure you get all final public releases.
# Uncomment the following line if you want to get alpha and beta
# releases, too.

# deb http://deb.opera.com/opera-beta/ stable non-free
```
How about we make that standard, then?

---

### Post by koenn on 2009-09-10
> **aysiu said:**
> How about we make that standard, then?
it puts you dangerously close to "arbitrary code execution".
once that source line is added, the person that controls that repo could add to that repo a package that already exists in a default ubuntu, but with a higher version number, and a doctored executable, or some extra programs. The update system will install that rouge package automatically, during a future update  ...

granted that it still the user's "deccision" to add the original package and the repo, and this technique is alreay possible with click-to-install debs anyway, but making it the standard, expected behavior, sounds like lowering the barriers even more, ...

---

### Post by aysiu on 2009-09-10
> **koenn said:**
> it puts you dangerously close to "arbitrary code execution".
once that source line is added, the person that controls that repo could add to that repo a package that already exists in a default ubuntu, but with a higher version number, and a doctored executable, or some extra programs. The update system will install that rouge package automatically, during a future update  ...

granted that it still the user's "deccision" to add the original package and the repo, and this technique is alreay possible with click-to-install debs anyway, but making it the standard, expected behavior, sounds like lowering the barriers even more, ... I disagree.

It's no more dangerous than actually asking users to paste in repository lines manually. As you have said, once the repository line is in there, whoever is in charge of the repository can mess up your installation or put in newer "versions" of existing software.

By putting in a repository, you are putting your trust in the software provider. In fact, by double-clicking a .deb file and entering your *sudo* password, you are already giving that .deb file full access to your system files.

So I don't see this as any more dangerous than what exists now. If you don't trust the software you're installing, don't install it.

If I might offer an analogy, it would seem like going up to a valet to have your car parked for you, except instead of just giving your keys to the valet to park the car, you have to ask the valet where the secret code is hidden, go to that place, find the code, and then say the code back to the valet, and only at that point will your valet take your keys and park the car.

It's a lot of trouble for the person who wants her car parked, but either way (the valet just taking the car, or the valet giving you the location of some secret code you have to recite) you're still trusting the valet to actually be a valet (and not a clever car thief con artist) and park your car.

---

### Post by hoppipolla on 2009-09-10
> **koenn said:**
> it puts you dangerously close to "arbitrary code execution".
once that source line is added, the person that controls that repo could add to that repo a package that already exists in a default ubuntu, but with a higher version number, and a doctored executable, or some extra programs. The update system will install that rouge package automatically, during a future update  ...

granted that it still the user's "deccision" to add the original package and the repo, and this technique is alreay possible with click-to-install debs anyway, but making it the standard, expected behavior, sounds like lowering the barriers even more, ...

It's a matter of working out a clever way around that I think, as this would be a good thing to make standard if we want to make the experience smoother for a user.

I'm sure security problems can be dealt with and worked around, it can be made to work :)

---

### Post by zekopeko on 2009-09-10
> **koenn said:**
> it puts you dangerously close to "arbitrary code execution".
once that source line is added, the person that controls that repo could add to that repo a package that already exists in a default ubuntu, but with a higher version number, and a doctored executable, or some extra programs. The update system will install that rouge package automatically, during a future update  ...

granted that it still the user's "deccision" to add the original package and the repo, and this technique is alreay possible with click-to-install debs anyway, but making it the standard, expected behavior, sounds like lowering the barriers even more, ...

There are ways to give the user a piece of  mind in this scenarios. One of them is proposed in one of the blueprints concerning apt url functionality.
The idea is that Ubuntu would vet the PPAs that are theirs (like xorg-edgers or another Ubuntu project) or that are official from upstream (like an official empathy PPA or vlc PPA). The keys would be installed in the keyring by default and you would get a nice dialog stating what exactly are you trying to do and what are the implications.

You could also have people sharing PPA trust levels with their friends. Something like: I'm friends with Mark and Alex and once I try to install a PPA from David, I'm informed that Alex and Mark also have the PPA installed.

---

### Post by zekopeko on 2009-09-10
> **aysiu said:**
> I have an idea.

You know how when you double-click a .deb file, GDebi launches and resolves dependencies for you?

What if the .deb specification was modified so as to include a repository line as well?

GDebi could then double-check that you have the appropriate repository for that file already in your /etc/apt/sources.list file, or prompt you to add it.

I think Suse (or perhaps Package kit?) has something like that. You click on a yum link and are prompted to install the repo.

EDIT: Here are the link to some apt-url specs

[https://blueprints.launchpad.net/ubuntu/+spec/apturl-omnipresence](https://blueprints.launchpad.net/ubuntu/+spec/apturl-omnipresence)
[https://blueprints.launchpad.net/ubuntu/+spec/jaunty-apturl-add-repo](https://blueprints.launchpad.net/ubuntu/+spec/jaunty-apturl-add-repo)

---

### Post by koenn on 2009-09-10
> **hoppipolla said:**
> It's a matter of working out a clever way around that I think, as this would be a good thing to make standard if we want to make the experience smoother for a user.

I'm sure security problems can be dealt with and worked around, it can be made to work :)
yes, of course, "all problems will be dealt with".

---

### Post by koenn on 2009-09-10
> **aysiu said:**
> I disagree.

It's no more dangerous than actually asking users to paste in repository lines manually. As you have said, once the repository line is in there, whoever is in charge of the repository can mess up your installation or put in newer "versions" of existing software.

By putting in a repository, you are putting your trust in the software provider. In fact, by double-clicking a .deb file and entering your *sudo* password, you are already giving that .deb file full access to your system files.
yes, I know,technically there is no difference.
It's just that an actual attack would by slightly stealthier, as it will happen some time in the future during normal operations (a routine update), not at the moment you click on that deb, a moment that you might be a bit more alert to what's happening

I'm not really sure _how much_ worse that is, but it does feel worse.

---

### Post by zekopeko on 2009-09-10
> **koenn said:**
> yes, of course, "all problems will be dealt with".

I'm going to take the quotes as a sign of sarcasm and respond on that.

But they are (at least theoretically). Read the link I provided.

---

### Post by koenn on 2009-09-10
> **zekopeko said:**
> I'm going to take the quotes as a sing of sarcasm and respond on that.
Good call.
But the sarcasm was directed at hoppipolla simply waiving the problems in stead of discussing them.

> **zekopeko said:**
> 
But they are (at least theoretically). Read the link I provided.
It's late, I should ' gone to bed at least a half hour ago :)
maybe tomorrow.

---

### Post by hoppipolla on 2009-09-10
> **koenn said:**
> Good call.
But the sarcasm was directed at hoppipolla simply waiving the problems in stead of discussing them.

Thing is though man the developers probably not only are working on this in their own way regardless of what we say in this thread, but probably have ALREADY devised a fix... I dunno I guess I'm personally just quite content accepting the current system is a little "raw", and trusting them to come up with a good solution :)

I am quite happy to discuss potential solutions, I just don't think that I for one have the expertise to come up with anything better than they could.

---

