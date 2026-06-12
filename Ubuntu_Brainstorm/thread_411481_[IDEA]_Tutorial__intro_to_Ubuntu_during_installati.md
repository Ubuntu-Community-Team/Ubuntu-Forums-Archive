---
title: "[IDEA]: Tutorial / intro to Ubuntu during installation"
date: 2007-04-16
forum: Ubuntu Brainstorm
---

### Post by aysiu on 2007-04-16
**Summary:**
A slideshow with screenshots introducing new users to Ubuntu while the installation process is happening.

**Rationale:**
New users are often disoriented and don't really know the real advantages of Ubuntu or even how to use some of its basic functions (Add/Remove instead of setup.exe). An orientation would help them.

A couple of ideas for how to help them have come up, including [this idea about having pop-ups for every new application that's open](http://ubuntuforums.org/showthread.php?t=410929). The pop-up idea has a few downsides, of course, not the least of which being that pop-ups are annoying to many users, both new and experienced.

One relatively unobtrusive way to introduce new users to the basic functions of Ubuntu is to show a slideshow during the installation process. New users would probably watch the slideshow (they're waiting for the installation to finish--what else are they going to do?), while experience users might have the option to turn off the slideshow... or they may just get up and leave, knowing that the installation won't take more than fifteen minutes.

**Scope and Use Cases:**
Runa installs Ubuntu. While installing, she learns that you add and remove programs using the Add/Remove, which will download and install the program for you. She now knows not to go to through the web browser to download an installer file separately. She learns a bit about Free software and the Ubuntu philosophy. She also gets some handy tips on how to get more help if she needs it.

Sharon installs Ubuntu. This is her fourth Ubuntu installation. Before Gutsy, she'd already installed Feisty, Edgy, and Dapper. She likes clean reinstalls (with a separate /home partition) instead of upgrades. She installs Ubuntu, answering all the standard questions (time zone, username, partitioning, etc.), then she walks away and cooks dinner, knowing the installation will be done in fifteen minutes. She isn't bothered at all by the tutorial/intro slideshow because she isn't even watching the installation.

**Implementation Plan:**
Modify Ubiquity to include a slideshow on the side. Other Linux installers (for example--OpenSuSE... see attached screenshot) have this, and I believe Windows XP also has something like this (see other attached screenshot).

**Blueprint**
[https://blueprints.launchpad.net/ubuntu/+spec/ubiquity-slideshow](https://blueprints.launchpad.net/ubuntu/+spec/ubiquity-slideshow)
[https://blueprints.launchpad.net/ubuntu/+spec/tutorial-during-installation](https://blueprints.launchpad.net/ubuntu/+spec/tutorial-during-installation)

---

### Post by 23meg on 2007-04-16
I strongly support this, and it should be trivial to implement. A first step could be to survey how various other operating systems have done this in the past and learn from them.

---

### Post by Shin_Gouki2501 on 2007-04-17
I think thats basically a nice idea. but i see a problem:
IMO it would be to static if the slideshow would be static. Its necessary to offer the user a minimum choice about WHAT he wantes to be instructed like:
*frist steps in office
*first steps in image editing
*first steps in installing new apps within ubuntu
*frist steps in networking
*frist steps with driverconfiguration
(if u include a tutorial how to setup 3D Drivers a lot of people will read it!)
If u offer an option to choose it will work much better!

wbr Shin Gouki

---

### Post by chakkaradeep on 2007-04-17
I really agree that we need something like this. This would help many new users to get a feel about Ubuntu !

---

### Post by slayerboy on 2007-04-17
I love this idea.  But...

what about if we could implement a way to make it almost a "mandatory" part of the install process.

By this, I mean following all the steps we go through to install already, but when it is starting the install after asking all the necessary questions, start the slideshow which is interactive.  Users could skip around, sort of like a visual wiki, or go in order.  Now, I don't know how easy this would be, but I think Flash would be really useful in this situation, or "web 2.0" style at least.  At the bottom of the window, it would show the installation progress.  If the user is familiar with Ubuntu/Linux, then all they would do is when the install starts the actual installation and the slideshow comes up, they could select the option that says they are familiar with ubuntu.  at this point, if they are familiar, they would see a screen that waits for the install progress to finish and then continue on.  If the user says they are not familiar, the install finishes, but does not bother them until they are done with the slideshow and then it continues on.

Definitely a good idea to have a slideshow.  I always thought the Windows "shows" were more hype than informative.  We need to stay away from this.  We need something quick, but informative that will last the duration of the install, 20 mins tops. This is so we don't give the impression that the install takes longer than it actually does.

Depending on my schedule and if this sees light, I would be willing to help with screenshots as I have an external hard drive where I can store those screenshots easy.

---

### Post by maniacmusician on 2007-04-17
I'd definitely be able to help with some of the writing that goes into this. This is something that can make it through UDS effectively, I think. I think we'll be adding it to the list of small specs that will be written up for UDS. Good  job on this one aysiu.

---

### Post by Thiesen on 2007-04-17
I don't know if you have seen the Mandriva installer? I do not endorse using Mandriva although it's still built on Linux but when I was toying around with Mandriva I saw the installer and it had an option to either show a slideshow or view the installation progress. Ofcourse I only viewed through the slideshow once and then turned to the progress view but I kind of liked the slideshow.

Now this would mean that other stuff would have to be removed from the livecd so I don't think we will see such a thing

---

### Post by 23meg on 2007-04-17
A bitmap-heavy slideshow would take too much disk space, so let's discard that idea straight away. The point isn't to do a visual walkthrough of Ubuntu anyway; the user is already seeing the real thing, since Ubiquity works in a live session. It also isn't to outline Ubuntu's features; some may be highlighted, but it's not the main focus. We assume the user already knows those, since they have decided to install Ubuntu in the first place.

The main focus is familiarizing people who have never used Ubuntu or a similar OS with the new tools that they'll have to use in this new paradigm, and the new usage habits they'll need to adopt. [This post]("http://ubuntuforums.org/showpost.php?p=2465283&postcount=20") illustrates the point better than I can at the moment.

---

### Post by Skeletonix on 2007-04-17
nice :D

---

### Post by Rinzwind on 2007-04-17
I would not mind having this :)
So: ++1

Oh, could we also have a playable Tetris? >:)

---

### Post by troymcdavis on 2007-04-17
This is a good idea, but there is only so much you can fit during the install. I think that the LiveCD should come with an interactive tutorial, that way the user can do it at their own pace before they install. 

You know that fish program, xfishtank? We could use similar methods to overlay arrows and dialog boxes so the user can learn how to install software, access programs, etc in the actual Ubuntu environment. Of course, this would be completely optional, maybe a shortcut on the desktop labeled "How to Use Ubuntu". 

The user would click the shortcut, and it would say "Show me how to..." with options such as "install software", "type a document", "update my system", "access the internet", "send an e-mail", etc, and the big one: "do everything!" You would need a quit/stop button for the last one (probably for all of them), of course.

These two plans (the original and my modification) are by no means mutually exclusive. In fact, they could do well to supplement one another. Hmm... should I make some mock-ups?

---

### Post by wersdaluv on 2007-04-17
That's really great.

When I tried OpenSuSE, I liked the installation because it is comprehensive and it takes every necessary steps for installation including configurations.

---

### Post by eentonig on 2007-04-17
I like this very much, as long as it doesn't slows down the install to much. It's good marketing because the user is watching the screen anyway. so better give him something to do so time passes faster.

Another idea could be to pop up an interactive introduction ti ubuntu, right after install (and only then. If you want it afterwards, activate it manually).

If you install XP, you get this as well.

---

### Post by aysiu on 2007-04-17
> **eentonig said:**
> 
Another idea could be to pop up an interactive introduction ti ubuntu, right after install (and only then. If you want it afterwards, activate it manually). I proposed this idea in order to avoid any pop-ups after installation.

---

### Post by PriceChild on 2007-04-17
I really really like this idea... Even if its just small pieces of text explaining the huge wealth of software availiable from the menu: System > Administration > Synaptic or how media applications can automatically download and install codecs as needed. Litle things that will make even an "experienced" user not reach for 3rd party install scripts without thinking.

---

### Post by aysiu on 2007-04-17
By the way, to those who are concerned about it not fitting on the disk--the tutorial/intro doesn't necessarily have to include screenshots. Pictures would be nice, but something is better than nothing, especially to a new user.

---

### Post by Turgon on 2007-04-17
I really support this idea. A little bit of text would both be educating and make the installation less boring. It should say somthing about open source and free software (give the user some info on why they don't get mp3 support out of the box, etc), what application they can use for different taskes, introduce the add/remove tool and perhaps recomend a program or two so the new user easily can learn how to download and install a program.

Done right, this could really help answering most of the questions new users ask in the forums and thereby make their experience with ubuntu more pleasnt.

---

### Post by rai4shu2 on 2007-04-17
Actually, doing a few partial screenshots for the really basic concepts wouldn't use much space at all if done properly. For the 3 or 4 things that illustrate usage, installation, and basic configuration, it might be worth it.

---

### Post by Lucifiel on 2007-04-17
Also, I suggest something like what Mozilla Firefox does.

For all Windows and Mac users, show a page during the installation that explains what the Ubuntu equivalent of certain commands/programs are and where to find them. 

For example(this is only for Windows. I don't know anything about other Linux builds or about Mac.): 

Windows : Add/Remove Programs

Ubuntu: Add/Remove, Synaptic Package Manager or Terminal

The most basic form of installing and removing programs is by using Add/Remove. You can find Add/Remove by clicking on "Applications" from the Menu bar at the top of the Screen. For a slightly more advanced method of programs, you can use Synaptic Package Manger. From the Menu bar, you can find Synaptic Package Manager by going to "System" and then choosing Administration from the drop-down list. The most advanced form of installing programs would be entering commands via Terminal. 

Windows : Ms-dos 

Ubuntu: Terminal

Terminal is a highly advanced tool which is similar to Ms-dos, also known as Command Prompt in Windows. By pasting or entering various commands, one can install and modify programs, view data or even delete certain files. Terminal uses purely text and therefore, it makes use of a Command Line Interface(CLI).

Edit again:

Some more ideas:

The tutorial should also explain a little about what directories like /usr , /home are and the Windows/Mac equivalent of Documents and Settings, Windows, etc., are.

Also, perhaps, Ubuntu could create or use a mascot which could act as a Wizard for all interactive guides and tutorials, etc. :p However, not something as annoying as the animated wizards within Microsoft Office: remember the Paper clip? :P And also, allow people to turn off the animated Wizard. That is, below the animated Wizard would be a message like : Click on me to disable me!!!!

---

### Post by eentonig on 2007-04-18
> **aysiu said:**
> I proposed this idea in order to avoid any pop-ups after installation.


If after the original install I have once an 'introduction' to Ubuntu opening up by itself, I don't think anybody will be offended. It only starts being annoying if you get this every time you start the computer. Or you get pop-ups every time you touch the pc (like MS sometimes does.)

But it doesn't even have to be auto-started. Just put a big-nice looking icon to that application on the Desktop. That way, everybody can choose at any time if he wants the introduction or not.

PS. I read the original topic leading to this one. But I personally see a big difference between pop-ups (annoying) and 'introduction animation' after install.
PPS. The slides during install is a very good feature that should be easy to implement. Hell, If needed, I would volunteer to contributing to this.

---

### Post by Bavo on 2007-04-18
I don't really like the idea.

People who are able to download a cd, burn it, boot it, install a new OS themselves should also be able to figure out how to get started with a new OS.

The people who this kind of tutorials should be made for are people who let someone else install a tutorial for them.

I really like the idea of a beginners tutorial, but you should be able to click trough it and run it whenever you like. If its integrated in the installer you're kind of obligated to sit wait and watch, instead of just putting a disk in the cd drive and watch some tv or whatever until the installer has finished.

I think we should do it the way windows XP does it, show a popup that offers you to go trough a beginners tutorial.

---

### Post by 23meg on 2007-04-18
> **Bavo]
People who are able to download a cd, burn it, boot it, install a new OS themselves should also be able to figure out how to get started with a new OS.[/QUOTE]

Not necessarily. Assuming there are no stopping issues, there's a good chance that a non-technical user can install Ubuntu, especially with help available online, such as these forums. Many users come here asking for advice on partitioning *before* installing Ubuntu, for example. But the same people don't know what Synaptic is, how repositories work, what a home folder is and why they don't have permission to write outside it. These are alien concepts if all they've used so far is Windows or Mac OS. We see people in this situation every day in the beginner forum said:**
> this post[/URL] does a good job of describing it.

[QUOTE=Bavo]I really like the idea of a beginners tutorial, but you should be able to click trough it and run it whenever you like. If its integrated in the installer you're kind of obligated to sit wait and watch, instead of just putting a disk in the cd drive and watch some tv or whatever until the installer has finished.

The rationale of having it run during install is for the user to take notice if they don't have anything else to do at that moment. If there's nothing interesting going on during an OS install, the user probably won't sit watching the status text and progress bar; they'll open a browser and surf the net, look around in the menus and panel to get acquainted, or just leave the computer. If the user doesn't pay attention to the introduction, it's up to them; it should be collapsible and easily avoidable, and also be available through the help system or elsewhere for viewing later on (the user can be notified of this if they choose to collapse/skip it).

---

### Post by Bavo on 2007-04-18
> **23meg said:**
> Not necessarily. Assuming there are no stopping issues, there's a good chance that a non-technical user can install Ubuntu, especially with help available online, such as these forums. Many users come here asking for advice on partitioning before installing Ubuntu, for example. But the same people don't know what Synaptic is, how repositories work, what a home folder is and why they don't have permission to write outside it. These are alien concepts if all they've used so far is Windows or Mac OS. We see people in this situation every day in the beginner forum; again, this post does a good job of describing it.
There is indeed a good chance that they can, but will they?
But you are right about users coming from Windows or OSX or even other distro's. It's just to easy and logical once you're used to it, i forgot that everyone has to learn the first steps :)


> **23meg said:**
> The rationale of having it run during install is for the user to take notice if they don't have anything else to do at that moment. If there's nothing interesting going on during an OS install, the user probably won't sit watching the status text and progress bar; they'll open a browser and surf the net, look around in the menus and panel to get acquainted, or just leave the computer. If the user doesn't pay attention to the introduction, it's up to them; it should be collapsible and easily avoidable, and also be available through the help system or elsewhere for viewing later on (the user can be notified of this if they choose to collapse/skip it).

You've got a point, but i think this introduction should be available elsewhere also, it would be a waste of energy if it was only displayed during install.
It can be hidden somewhere in the help or whatever.

---

### Post by 23meg on 2007-04-18
> **Bavo]There is indeed a good chance that they can, but will they?[/QUOTE]

We're talking about the part of the installation process where the user no longer interacts with the installer, where the installer does the job of copying and configuring packages said:**
> You've got a point, but i think this introduction should be available elsewhere also, it would be a waste of energy if it was only displayed during install.
It can be hidden somewhere in the help or whatever.

I was saying the same thing:

[QUOTE=23meg]and also be available through the help system or elsewhere for viewing later on (the user can be notified of this if they choose to collapse/skip it).[/QUOTE]

---

### Post by plb on 2007-04-18
Well it's not that I don't support the idea, I just wonder why we "need" it. Seems like more of a "want." The reason I say this is because once you hit install, that's it...the installer does the rest. You don't have to sit in front of the computer waiting for a popup to answer a question. Windows XP on the otherhand has a few questions during the install you have to complete which means you have to sit there and wait which is probably the reason they have that little slideshow..to keep you occupied lol.

---

### Post by 23meg on 2007-04-18
You don't absolutely *have to* sit down and wait; neither with Windows XP, nor with Ubuntu. If there's something interesting displayed that you'd benefit from, however, you may *want to*. 

This proposal would have a win-win outcome; those who would benefit from the primer, *and* would be willing to sit at their computer during installation (which is pretty quick in Ubuntu), win. Those who wouldn't benefit from it and those who don't want to sit and wait, lose nothing.

---

### Post by plb on 2007-04-18
> **23meg said:**
> You don't absolutely *have to* sit down and wait; neither with Windows XP, nor with Ubuntu. If there's something interesting displayed that you'd benefit from, however, you may *want to*. 

This proposal would have a win-win outcome; those who would benefit from the primer, *and* would be willing to sit at their computer during installation (which is pretty quick in Ubuntu), win. Those who wouldn't benefit from it and those who don't want to sit and wait, lose nothing.

Eh? I was always asked questions during XP install...e.g. timezone, network setup, then all that registration and create user crap.

---

### Post by 23meg on 2007-04-18
> **plb said:**
> Eh? I was always asked questions during XP install...e.g. timezone, network setup, then all that registration and create user crap.

Are those not at the beginning? You're asked questions during the Ubuntu installation too, but at the beginning. If the Windows XP installer asks questions at the end too, you still don't absolutely have to wait; you can leave the computer and answer them when you came back, to finalize the install. No sensible installer would ask questions halfway into the installation.

---

### Post by plb on 2007-04-18
> **23meg said:**
> Are those not at the beginning? You're asked questions during the Ubuntu installation too, but at the beginning. If the Windows XP installer asks questions at the end too, you still don't absolutely have to wait; you can leave the computer and answer them when you came back, to finalize the install. No sensible installer would ask questions halfway into the installation.

Well I guess that depends on what you consider the beginning. After putting in the serial # I had to wait about 5-10min for timezone then wait again for network setup. Ubuntu after you hit install, everything goes straight through to the end...no questions.

---

### Post by 23meg on 2007-04-18
Weird. Anyway, we're dealing with the Ubuntu installer, which asks things only at the beginng; the rest of the installation is completely non-interactive.

---

### Post by plb on 2007-04-18
Well in my opinion I think the developers efforts could be put to better use elsewhere. I mean isn't there already some kind of tutorial under system>help anyway?

---

### Post by rai4shu2 on 2007-04-18
I think we've wasted more time discussing it than it would take for a developer to implement.

---

### Post by plb on 2007-04-18
> **rai4shu2 said:**
> I think we've wasted more time discussing it than it would take for a developer to implement.

Doubtful, implementing this would require recoding parts of the installer. Not only that, but then deciding what tutorials to put in..screenshots and whatever else. Honestly, is this a need or a want? Would such a thing appeal to businesses?

---

### Post by aysiu on 2007-04-18
> **Bavo said:**
> 
People who are able to download a cd, burn it, boot it, install a new OS themselves should also be able to figure out how to get started with a new OS. Really? Have you taken a look at the Absolute Beginner section of our forums?

---

### Post by 23meg on 2007-04-18
[QUOTE=plb]Doubtful, implementing this would require recoding parts of the installer.[/QUOTE]

Just some additions to the non-interactive part. Quite trivial.

[QUOTE=plb]Not only that, but then deciding what tutorials to put in..screenshots and whatever else.[/QUOTE]

Those could come from the community. People interested in the idea right here can do them, actually. 

[QUOTE=plb]Honestly, is this a need or a want? [/QUOTE]

Depends entirely on your definition of both. I'd call it an enhancement.

[QUOTE=plb]Would such a thing appeal to businesses?[/QUOTE]

Why does it have to appeal to businesses?

---

### Post by plb on 2007-04-18
Because Mark wants to get Ubuntu out there in the corporate level as well..not just the desktop level. What I mean by the statement "Would businesses want it" is would it be a feature they would want or could the effort to do this be better spent elsewhere such as security which is something all companies look for?

---

### Post by aysiu on 2007-04-18
> **plb said:**
> Because Mark wants to get Ubuntu out there in the corporate level as well..not just the desktop level. What I mean by the statement "Would businesses want it" is would it be a feature they would want or could the effort to do this be better spent elsewhere such as security which is something all companies look for?
Why don't we leave it up to the developers to figure out how many resources they have and where to use them?

---

### Post by sharperguy on 2007-04-18
I really like this idea

Just a few screenshots during the non-interactive part of the installer could go a long way helping new users get started with ubuntu.

The implementation would be easy, and it would be good to make it collapseable because i quite often have the progress bar running over another window with an app I'm using to pass the time.

The hardest part would be choosing what images/text to include, it should be streamlined and informative.

Information about add/remove would be helpful, but it doesn't have to be a full blown tutorial, because I believe once you know that its for installing apps, gnome-app-install should be pretty self explanitory to use. Some information about the ubuntu/free software philosophy would be nice too.

---

### Post by rai4shu2 on 2007-04-18
I think probably the hardest part would be getting the text and having it all translated properly, but that could be done well after the code part.

---

### Post by 23meg on 2007-04-18
[QUOTE=plb]could the effort to do this be better spent elsewhere such as security which is something all companies look for?[/QUOTE]

It's pretty easy to implement, assuming all the content, including translations, comes from the community. It won't steal much developer time from other things; it would be us and the doc team who would have to do the real hard work.

---

### Post by Bavo on 2007-04-19
> **aysiu said:**
> Really? Have you taken a look at the Absolute Beginner section of our forums?

To be fair, no I haven't recently.
Anyway, the more i'm thinking about it, the more i start to like the idea.

[QUOTE=plb]Well in my opinion I think the developers efforts could be put to better use elsewhere. I mean isn't there already some kind of tutorial under system>help anyway?[/QUOTE]
I don't think it requires a lot of coding. The most time consuming part would be creating and translating the documentation. (Do screenshot get taken in other languages for these things??)
But that would't be a waste of the developers time, because it can be done by someone who can't code.

---

### Post by HornedBeast on 2007-05-22
I strongly agree with this idea.

I think it would help new users get to grips with basic principles and usages of Ubuntu.

Tali another score from me!

---

### Post by Bou on 2007-05-22
I'm all for it. So, is someone gonna open a thread to decide WHAT has to go in the tutorial, or are we just gonna sit here forever? Is someone gonna contact Ubiquity devs to ask them if they're gonna include the tutorial, should they be provided the text and stuff?

---

### Post by 23meg on 2007-05-22
[QUOTE=Bou]Is someone gonna contact Ubiquity devs to ask them if they're gonna include the tutorial, should they be provided the text and stuff?[/QUOTE]

I've done that weeks ago, but forgot to post here about it, it seems. There's an existing blueprint that set out to accomplish (something close to) this long before this thread was started:

[https://blueprints.launchpad.net/ubuntu/+spec/ubiquity-slideshow](https://blueprints.launchpad.net/ubuntu/+spec/ubiquity-slideshow)

It's been approved, but it seems work on it has halted after a while; it's now proposed again for Gutsy. I'll talk to Colin Watson and have him review the ideas in this thread, as well as getting the details of the latest UDS discussion on it. We can probably reinforce the existing blueprint with the ideas here, and even if his priorities for Gutsy don't allow him to work on it, we can probably get someone else to do it.

---

### Post by alex_anthony on 2007-05-24
you mentioned businesses...
surely there could be an adapted version which people could launch in buinesses to familiarise themselves with ubuntu (adapted in that it wouldn't go into installing software etc.)

---

### Post by happysmileman on 2007-06-13
> **alex_anthony said:**
> you mentioned businesses...
surely there could be an adapted version which people could launch in buinesses to familiarise themselves with ubuntu (adapted in that it wouldn't go into installing software etc.)

I think the idea of the slideshow is completely harmless, while it may not be suited for businesses most businesses would either know how to do that stuff or would benefit from it anyway...

I like the idea of a "Getting Started" file on Desktop which would start an introduction program, for example:
> 
What would you like to learn about? (tick all that apply)

The Basics:
[ ] Introduction to the terminal (recommended)
[ ] Installing software (recommended)
[ ] Basic file structure on Linux
[ ] Using Firefox web browser
[ ] Using Thunderbird email client
[ ] Using OpenOffice office suite

More advanced tutorials:
[ ] Enabling mulitmedia (mp3, wma etc...)
[ ] Installing drivers
[ ] Installing from source
[ ] Mounting other drives/partitions
[ ] File permissions
[ ] Beryl/Compiz setup

PS. I can't remember setting up multimedia so don't know whether it'd fall under anced... but as you can see the basics is just for people who have absolutely no clue what they're doing... I think this is obviously not enough for such a file, but I just thought those up now, and I think having instructions for how to use Firefox etc.. would be helpful as they may seem different compared to IE and stuff at first, despite being very similar, if possible the tutorials should use knowledge of IE and stuff to help show... Example: > Reload (equivalent of refresh in IE) is a ..........

PPS; I apologise for bringing back a 2 week dead thread, but just giving my 0.02

---

### Post by sabrewolf2006 on 2007-06-14
> **23meg said:**
> Weird. Anyway, we're dealing with the Ubuntu installer, which asks things only at the beginng; the rest of the installation is completely non-interactive.

This is where I was coming from with the whole 'like anaconda' idea.. anaconda explains what needs to be done (a bit like SuSes yast2 but not quite) in the left pane while the install takes place (asking you questions etc.) in the right.. we could take the same tact.. but put our explanations in the bottom of the window.. with graphics to illustrate whats happening (a house with 'partition' walls being put in to illustrate partitions (heh) - for example)

Then the rest of the actual install [the non-interactive bit] can be slides/whatever

The idea in the above post though (the introduction to ubuntu proggie) sounds brilliant :D

---

### Post by aysiu on 2008-02-11
Seeing that this spec was approved for Gutsy (and obviously not implemented) and seeing a proliferation of "pop-up tutorial" ideas here in the Idea Pool, I'm curious as to what the status of the slideshow is right now. Anyone know? Is this coming up for Hardy?

---

### Post by 23meg on 2008-02-11
Mr. Picklesworth has [produced some code]("http://ubuntuforums.org/showthread.php?t=679427"). I'm not sure about whether he got in touch with the installer team and started integrating it into Ubiquity. Specs for Hardy have been finalized months ago, and we're very close to feature freeze; it's extremely unlikely that this can make it to Hardy.

---

### Post by SonnySee on 2008-02-11
Being a long time Windows user and a relatively recent Linux convert I would have to agree that something along the lines of a tutorial would be very helpful to many.  I understand that a feature freeze is looming near on the horizon, however this is something that could be implemented in a slightly different way perhaps.  A way that I do not believe would require drastic changes, nor would it involve adding space hungry videos and/or pictures to the Live CD. 
  After reading through the post I began to think back on my own personal experience with Linux:    Having inserted the live CD and with this entirely different operating system working on my computer what was the first thing I would do? Well of course, I clicked on the icon to open up Firefox.  And what lay before me as my opening page but a great big 'ol "Welcome to Ubuntu 7.04!"  And on that same page was a link to this site:
 [http://help.ubuntu.com/](http://help.ubuntu.com/)
  From there, a new or experienced user can access a wealth of information that is well thought out and easy to understand and follow.  
However, while that link existed, I overlooked it for weeks.  And so, here is what I propose: If it is too late to change the installation process and add a video or tutorial there -  how about re-designing the Welcome to Ubuntu 8.04 front page on FireFox?
I know that I would personally have liked to have seen something like" Welcome to Ubuntu 7.04 - Now What?" , or perhaps "Welcome to Ubuntu 7.04! - Would you like to see a walkthrough / screencast / video tutorial on getting the most out of your new Operating system? If so Click here".
At that point the user could be directed to a series of Screencasts or other type of media that would suit there needs.  

Little or no added content to the live CD.

You don't have to go there if you don't want to.

Easy for anyone to find with a 'this link is so obvious that you would have to try hard to miss me type of feel to it'.

just my .04 cents. :)

---

### Post by pacsum on 2008-02-13
I don't know why this haven't happened yet.

---

### Post by 23meg on 2008-02-13
[QUOTE=SonnySee]how about re-designing the Welcome to Ubuntu 8.04 front page on FireFox?[/QUOTE]

Merely adding a link to [screencasts.ubuntu.com]("http://screencasts.ubuntu.com"), where the user can find walkthroughs? Sure, good idea, assuming that the walkthroughs can be prepared before release and maintained for the lifecycle of the release (3 years).

[QUOTE=pacsum]I don't know why this haven't happened yet.[/QUOTE]

I'll tell you: because nobody made it happen. It can't happen by itself.

---

### Post by Mr. Picklesworth on 2008-02-13
Launchpadified now.

[https://launchpad.net/ubiquity-slideshow](https://launchpad.net/ubiquity-slideshow)

...right now, I am pondering how to make this an approachable project. This is my first time setting up bzr, or registering projects / teams on Launchpad, so it may take a little while. [Suggestions are welcome.](https://blueprints.launchpad.net/ubiquity-slideshow/+spec/sensible-project-structure)
Obvious fix is to just have a different project for the Ubuntu slideshow, where ubiquity-slideshow is all about the slide projector code and maintaining a branch to integrate it with Ubiquity, but it feels weird for some reason. Right now, ubiquity-slideshow-ubuntu lives in trunk there.

Integrating with Ubiquity is, so far, rather irrelevent until some content exists. My plan there is to make sure it's possible in a generic way by touching up the Python script as a proper library with simple exposed functions.
Planning to bounce more pointed messages to various mailing lists, as I am sure there are a few creative, artistic individuals looking to contribute. This would be a great way to do it! If you want to do so yourself *right now*, feel free to checkout the [trunk branch with bzr](https://code.launchpad.net/~ubiquity-slideshow/ubiquity-slideshow/trunk) (Olive works if you're not a command line person), where there is a lot of stuff to start off with.

Though it would have been nice, I am definitely not aiming for Hardy unless a miracle occurs. Having an installer slideshow introduced with an LTS would be a beautiful thing, but the next LTS will still be before Windows 7, so the pressure isn't *that* bad.

---

### Post by 23meg on 2008-02-13
[QUOTE=Mr. Picklesworth]Integrating with Ubiquity is, so far, rather irrelevent until some content exists. [/QUOTE]

I don't think it's technically irrelevant. You can start integrating it with dummy content and sorting out the technical issues, if any. In the meantime, others can work on content.

---

### Post by pro-rsoft on 2008-02-14
Fully agree with the idea. I personally dislike the current ubiquity because it doesn't offer much customization (like no option to set compiz on/off and such)

---

### Post by Bou on 2008-03-25
I might be saying something dumb here, but couldn't something like [Salasaga]("http://www.salasaga.org/") be used to create the tutorial?

---

### Post by aysiu on 2008-10-14
For months this has been identified on Brainstorm as being planned for 8.10. Now that 8.10 is on the cusp of release, I see the Brainstorm idea has been deferred to 9.04 instead. Argh!

---

### Post by MadsRH on 2008-10-15
> **aysiu said:**
> For months this has been identified on Brainstorm as being planned for 8.10. Now that 8.10 is on the cusp of release, I see the Brainstorm idea has been deferred to 9.04 instead. Argh!

Spot on right. The first post in this thread is from April 2008.

I know the installer team has had other more crucial issues to attend, and that is of course understandable. I really really hope the look and feel or the slickness of Ubuntu will change dramatically for 9.04 (slideshow installer, new theme, new sounds...)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=88443&d=1224108801[/IMG]
In the style of OpenSUSE, here's a mockup I created in PS
[B]
//MadsRH[/B]
anotherubuntu.blogspot.com

---

### Post by olskar on 2008-10-18
> **MadsRH said:**
> Spot on right. The first post in this thread is from April 2008.

I know the installer team has had other more crucial issues to attend, and that is of course understandable. I really really hope the look and feel or the slickness of Ubuntu will change dramatically for 9.04 (slideshow installer, new theme, new sounds...)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=88443&d=1224108801[/IMG]
In the style of OpenSUSE, here's a mockup I created in PS
[B]
//MadsRH[/B]
anotherubuntu.blogspot.com

Wow, that is really nice

---

### Post by olskar on 2009-01-23
Is this being worked on?

Brainstorm says "A slideshow during the installer was planned for 8.10, but has been deferred to 9.04." :)


[http://brainstorm.ubuntu.com/idea/136/](http://brainstorm.ubuntu.com/idea/136/)

---

### Post by Yashiro on 2009-01-26
It's a decent idea, but I don't think it will help new users learn anything. Can you recall what it says on the matching Windows installer screens?

In the pursuit of completeness and making the boot process look more professional it's a fine idea. But it won't help people with their first steps into Ubuntu. 

This has to be done on the desktop when they log in. Hand holding.
The screencasts link was good idea, as was a better 'start page' in firefox.

---

### Post by gspat on 2009-01-27
If it becomes a question of space on the CD, the examples folder could be the first thing to go.

---

### Post by Yashiro on 2009-01-27
The CD is already 'too big'. It's over 650Mb which can be a stumbling block for some people.

---

