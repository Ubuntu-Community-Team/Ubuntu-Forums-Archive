---
title: "A Macusers view on Ubuntu installation"
date: 2008-01-13
forum: Testimonials &amp; Experiences
---

### Post by mikasjoman on 2008-01-13
I thought that my view as a Mac user could help out the Ubuntu/Gnome/Debian communities by giving some insights into how one of the Mac newbies to Ubuntu feel when we install it. Ill use quite strong language, because this is how real users feel inside them. But, I also came with ideas for fixes with every issue I had.


1.The installation.
Everything went well, only minor issues had to be dealt with. At the end of the installation the installer just would not stop trying to update apt-get, so I had to turn my router of since Ubuntu does not let me close the connection from the wireless connection menu. 
Urgent fix to developers: Let me disconnect from the wireless menu please.

2.After the reboot experience
After reboot, I am now ready to get dirty with Ubuntu. I want software! And, since the Ubuntu team directly helps me to update my computer, with over 145 updates, I felt that that was like any mac update I ever done before.
To me, 145 updates sounds scary, to my father it looks like the computer is going to die. 
Fix: Please stop scaring us, and bundle the updates to one. And updates seem to come every day, irritating my day. Just install them for god damn sake. I am an Ubuntu beginner and I don't want to care about updates, just fix them when I close the computer if a reboot is necessary.

3.The irritation begins
I have a connection to the repositories that was chosen by the application to be the fastest one. Its still only about 20k/sec, so the update takes hours. Now I want to install software, but the “Add software” just keeps telling me another Synaptics is running and only one system management software is allowed to run at one time. WTF! I want to install software like I did under OSX. Remember: Download, copy to Applications folder, Done.
If there is anything that desperately needs to be fixed, then this is it. I dont care about dependencies, and neither should I have to. Mac OS X doesn't let me care about dependencies, neither should I under Ubuntu. If I want to install ten apps at the same time, let me! The current situations is simply a huge design flaw built into Ubuntu if you compare it to Mac OS X.
Fix: just make it work without showing me the problems. I dont care if two synaptics are running at one, and neither should I. And, how logical is the name Synaptics for installing software? Rename it, and if its not close to impossible, try to give me a Applications folder in the root.

4.So I stop the update, I want to install cool apps!
So to make it easier for me I install applications, I decide to install CNR.com on my Ubuntu desktop.  Now again, Grrrr! After downloading the CNR.com application, the Package Installer tells me I lack 17! package files. Dependencies again and again. I get so sick about them I could throw up. And they waste my time! A lot of my time. Slow slow slow, and again, I can not install more than one application before finishing the current installation process. From a normal user perspective, under Ubuntu it is also almost impossible to find where my Applications are located. What I propose, is that the Ubuntu team creates bundles, so that an application is located in a Applications folder in the root. Even if I have to get the dependencies, I have my applications stored in a easy manner, bundled, without all the mess currently making the user disorientated. In OSX I have four folders in the root, in Ubuntu I have the scary 21 files and folders visible. Thats asking for trouble, hide them!

5.So I move on to system administration
Preferences or Administration?? On the Mac they are one and the same since for the user the difference is tautology. Under the two scary menus, I find not less then 41 choices, some for the same purpose. The mac used to look something like that, but that was seven years ago. After installing AWN and some other apps, the menus get to the point of total disorientation. 
Let us again learn from the Mac, create a system preferences application. Under that one, lets have plugins that sort under smart categories: Sharing, Printing, Screen, Language, Startup, Sound, Other, Etc
.
6.So wuu... great software straight into my computer
I find a homepage to install the newly released KDE4 that looks really cool. Well, everything great, but there is one problem. They want me to go to the terminal and edit the /etc/apt/sources.list. And to make me even more scared they want me to use the terminal to install it via aptitude. After working with Ubuntu for a while, it seems that most of the software that people write on the internet is installed via the terminal! Thats back to the 90-s baby, not after the millennium.
Urgent fix: as long as the internet is flourishing with guides using the terminal Ubuntu or  Gnome will not stand a chance against Windows. At least 98% of the software has to be as easy as klicking a button. If everybody are making these guides with terminal commands, why can't the standard just be klick and install? Add the content to a .install file with all the necessary commands. I don´t want to know what is happening under the hood, I just want things working.

After a month: Well I actually feel the same way and because of the lack of graphical tools I had to move back to my mac sometimes. 
I have also tried to install OpenGroupware with no success and well as with many other applications. I feel it´s great that my Ubuntu looks like a OSX now, Mac4Lin and AWN, and I am getting more used to the terminal (I think that is a bad thing). I wish that Hardy would be called Easy, but then it would have to be called hEasy I guess ;) But, mainstream users will not choose Ubuntu if they need to go once to the terminal. Think about it, Windows is easier from that perspective.

I, as many other of my friends cant seem to get the microphone working. And the Partition tool was not installed from scratch. I think this is because the menus are to filled up because they either does not have sub menus or a application as KDE or OSX which I prefer in logical sections. I really wish that Gnome would switch to a nice System preferences application insted of seeing two menus filling up.

Another thing I am missing is the beautiful vector graphics both OSX and KDE4 now has. I know this is a message more to the Gnome people, but still. I guess that with system wide vector graphics there also quickly would be developed vector graphic tools close to Illustrator.

I have now installed Ubuntu on three machines. Two of them are the most popular in the world; a Sony Vio and my MacBook. The Ubuntu Macbook page, looks more like a warning than a welcome message. A smart thing to do could be to make a Macbook tool, which fixes all those problems I have had, since people want one-click solutions not guides. I understand that guides are better than nothing, and yes I am greatfull for these too. The Ubuntu installer already knows I have a Macbook, so fix the problems ;)

And at the end, a big thank you for a great operating system! I just wish the stupid easy would have been a bigger focus for the Hardy version. And, please change that name. Anyone working with marketing knows you cant sell anything that sounds “hard” to do. Even “Ubuntu Happy” would have been a better name.

---

### Post by kebes on 2008-01-13
Thanks for the comments. You've touched upon many issues that should really be improved in Ubuntu. However I don't agree with all of your complaints.

> **mikasjoman said:**
> 
2. ... Just install them for god damn sake. I am an Ubuntu beginner and I don't want to care about updates
That should be fixed. There should probably be a mode (maybe even the default) where the updates get applied in the background without user intervention. (Since updates on Linux never require immediate rebooting, this can be done quite transparently.)

> 3.I want to install software like I did under OSX. Remember: Download, copy to Applications folder, Done.
The repository system is one of the huge advantages of Linux. Yes, it takes getting used to, but many of us much prefer it (I have a Macbook Pro and a Linux desktop, by the way, so I'm familiar with both approaches).

In Linux, you can pick dozens of apps from a list and they all get installed immediately. That's much better (in my opinion) than searching all over the net for files to download and drag-and-drop.

The installation system on Linux is not going to change, since it is central to how Linux works, and most of us love it (once we get used to it).

> I dont care about dependencies, and neither should I have to. Mac OS X doesn't let me care about dependencies, neither should I under Ubuntu. If I want to install ten apps at the same time, let me!
This point confuses me, since the package manager in Linux takes care of all dependencies automatically (that's the point), and it allows you to install many apps at the same time (whereas on Mac and Windows you have to manually download and install each one separately).

> I dont care if two synaptics are running at one, and neither should I.
That's a good point. There should be some way for Synaptic to know that another copy is running, and either bring that copy to the foreground (so the user knows he's waiting for the last thing to install) or kill the other copy. In any case, the user needs more meaningful feedback in that case.


> 5.Let us again learn from the Mac, create a system preferences application.
That's how it's organized in KDE and I do prefer it.

> 6. I find a homepage to install the newly released KDE4 that looks really cool. Well, everything great, but there is one problem. They want me to go to the terminal...
That's not really fair. Installing KDE4 is not a "run of the mill" installation: it's more for people who want to test the "latest and greatest." You can install KDE 3.5 from Synaptic easily.

Also, I should note that you'd be hard-pressed to replace your desktop manager on OS X without using the terminal, too.

> At least 98% of the software has to be as easy as klicking a button. If everybody are making these guides with terminal commands, why can't the standard just be klick and install?

The vast majority of software on Linux just involves a click (in Synaptic). Some more complex stuff may require using the terminal, but that's true on Mac OS X, also. (I have lots of command-line only software on my Mac.) If you don't like the terminal, then wait until that software is added to the repositories.



Again, I'll emphasize that I agree with many of your points. I think those are things that will indeed be worked on for future versions. I hope this doesn't turn into a flamewar! I'm not saying you're wrong: merely saying that some of us prefer Linux the way it is. If you change it too much, it stops being Linux (in which case, just use OS X or whatever!)...

---

### Post by mikasjoman on 2008-01-13
Hi, yeah I really do not hope this would create a flame war. The way I wrote it was how it felt, and I also get some of your points. Some I do agree to and some I don't, but thats life ;)

I really wish I could sit working with Ubuntu all the time you see. I really like free and open software, and the thing I wrote was just to show how I felt without trying to be nice. Try my girlfriend, when I installed Ubuntu on her computer she flipped out after the installation. The first thing she saw was the black GRUB, and she went mad on me. Now she kind of starts liking Ubuntu, but it´s a hard way to go.

The only thing I can´t get is that "Add/Remove" and how good everybody says that is. I do agree that it´s nice, but it lacks much of the great software out there. Synaptics is a super long list of software, and I just cant agree that one is user friendly compared to lest say [www.download.com](www.download.com) or my favourite versiontracker.com. People like the web, so why not let them use it for installing the software? Just have a firefox plugin that takes care of that?

Actually I want to help out, so I guess I just have to download some books about how to program under linux and get my hands dirty. Thanks for the response and the great software!

---

### Post by voteforpedro36 on 2008-01-13
Hmmm... I'm just wondering if you know that Linux is not Windows, and it isn't Mac either.

Be prepared for a learning curve if you want to switch,

---

### Post by mikasjoman on 2008-01-13
I am :) 

And I made myself a new years promise to switch at least 20 people this year to the Ubuntu camp from win/osx camps. But that is quite easy, my father is an ex principal so I guess I could just run in there and show how nice their computers could be....

---

### Post by kebes on 2008-01-13
> **mikasjoman said:**
> The only thing I can´t get is that "Add/Remove" and how good everybody says that is. I do agree that it´s nice, but it lacks much of the great software out there. Synaptics is a super long list of software, and I just cant agree that one is user friendly compared to lest say [www.download.com](www.download.com) or my favourite versiontracker.com. People like the web, so why not let them use it for installing the software? Just have a firefox plugin that takes care of that?

When I started out with Linux, I had the same reaction. I found it very, very frustrating that I couldn't just search the web for an application and then install it.

One of the advantages of the repository system, though, is that all the software in the repositories is "vetted" and so you can trust it. (You can add other repositories if you have reason to trust them, too.) This makes it harder to get malware onto a person's computer, because most of the time they install software from a trusted list rather than a random web-page.

I know malware isn't a very big problem on Mac, but at least on Windows one of the "problems" with the software installation method is that it is actually *too easy* to install software. Downloading random apps is not usually a good idea.


That having been said, there are efforts to create the "easy software installation" you speak of for Linux. It's called "AutoPackage" and if it's something you really want to catch on, you could help out that project:

[http://autopackage.org/](http://autopackage.org/)

---

### Post by mikasjoman on 2008-01-13
Just for the sake of it, I still think Ubuntu totally rocks compared to XP/Vista.

---

### Post by mikasjoman on 2008-01-13
sounds great, maybe I will :)

---

### Post by jdrodrig on 2008-01-13
I am kind of confused about the argument "in linux you cannot just download apps from the web"...I might be wrong, but isnt spype and acrobat and other similar stuff downloadable from the web?...aren't .deb files supposed to be installable, including dependencies?

---

### Post by Sephoroth on 2008-01-13
Not to mention many programs include scripts that will do all or most of the terminal work for you...
For me, getting used to Synaptics was done in a very short amount of time and I prefer it by far than searching the net (especially when I am on a poor/unstable internet connection) and using a drag/drop method to install programs.

---

### Post by karellen on 2008-01-13
what I always failed to understand is why people who start using Ubuntu begin to say something like "in windows/mac os x things were different/worked well etc". is you people are satisfied with the actual os you use, why on earth you switch to other os? stick with something that works for you, give up the "headaches" Linux is giving you and everybody will be happy

---

### Post by S3Indiana on 2008-01-14
> **mikasjoman said:**
> 4.So I stop the update, I want to install cool apps!
So to make it easier for me I install applications, I decide to install CNR.com on my Ubuntu desktop.  Now again, Grrrr! After downloading the CNR.com application, the Package Installer tells me I lack 17! package files. Dependencies again and again. I get so sick about them I could throw up. And they waste my time! A lot of my time. Slow slow slow, and again, I can not install more than one application before finishing the current installation process. From a normal user perspective, under Ubuntu it is also almost impossible to find where my Applications are located. What I propose, is that the Ubuntu team creates bundles, so that an application is located in a Applications folder in the root. Even if I have to get the dependencies, I have my applications stored in a easy manner, bundled, without all the mess currently making the user disorientated. In OSX I have four folders in the root, in Ubuntu I have the scary 21 files and folders visible. Thats asking for trouble, hide them!CNR Client package management does not come preinstalled on ubuntu builds, so it requires [additional]("http://community.cnr.com/docs/DOC-1035") repositories to install the package:
```
# Additional Sources
deb     http://apt2.freespire.org/CNRUbuntuExtra gutsy-extra main restricted
deb-src http://apt2.freespire.org/CNRUbuntuExtra gutsy-extra main restricted
# Uncomment the following two lines to add software from the 'backports' repository
deb     http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

```

---

### Post by matthewcraig on 2008-01-14
I like how you have given Ubuntu a fair assessment.  You've used it quite a bit, pinpointed your pain-points, and you've even thought through how to get them fixed.  Some of your concerns sound like, "It's not like MacOS", but if Ubuntu is going to be an easy-to-use operating system then there is lots to learn from the Macintosh ways.

I have to say that I find myself in agreement with some of your points, even without experiences with the MacOS.  Even after using Ubuntu for a long while, I sometimes question whether a configuration change is under either the Preferences menu, the Administration menu, or the System Tools menu.  For example, why are read-only tools such as System Monitor and System Log not under the Applications menu tree?  Unfortunately, these are GNOME-related questions and may be out of the scope of changes that Ubuntu can make.

As for your concerns about Synaptic, I am sure the right people are reading this thread and taking your thoughts into consideration.  Thanks for taking the time to observe your initial experiences and relay your thoughts in a way that isn't immediately hostile.  I think they key here is that you aren't giving up on Ubuntu, and the tone of your message reflects how you are wanting Ubuntu to improve for your continued use.

---

### Post by mikasjoman on 2008-01-15
Thanks. I know that I am not supposed to compare with Mac by many linux guys, but since that Is my background I do.

I belive in simplicity. Work on computers should be simple, even for complex tasks. The mac and also windows nowadays stands for that for the users who now are used to those platforms.

I insist on following the users behavior, if they want to use the web to install the apps - let them. Synaptics will never be the alternative for the mainstream. And in Ubuntu there is two places to install, why not one? Is one not good enough?  Can they be combined at least into one application with Beginner/advanced view?

Thanks for your replies!

---

### Post by 3rdalbum on 2008-01-15
Your first point about the apt-get update going on forever during the install is something I've noticed, and it needs urgent attention.

The rest are a bit iffy; "Synaptics will never be the alternative for the mainstream... how would anybody know that Synaptics is how you add programs". Eh? Synaptic Package Manager (to use the name in the menus) gives you thousands of programs that are 100% malware-free, and available at the click of a button. How is that less desirable than trawling the Internet trying to find applications that might be malicious?

The separation between "Preferences" and "Administration" is quite simple. Linux is a multi-user operating system, OS X is written as if it was a single-user operating system. Preferences apply only to the current user, Administration applies to all users.

It's important to have only one package manager open at a time. The package manager can (and does) remove packages as well as add them. If you added a package in one manager and removed it in another, you would get bad breakage. You *can* install more than one program at a time. Just mark them all in Synaptic Package Manager and click Apply.

Click And Run is not something I'd recommend for use with Ubuntu. I don't think there are any benefits to using it anyway.

If you don't want to be notified of package updates, go to System > Administration > Software Sources, go to the Updates tab, click "Check For Updates", and go to "Apply security updates in the background". Rolling multiple updates into one package is VERY BAD practice with an enterprise operating system. It involves witholding updates until you've got a large bunch of them. It's what Apple does, and it's an unbelievably bad thing to do as it means Apple's customers are running their systems with known security flaws. Ever wonder why Mac OS X isn't a popular server operating system? This is partly why.

When you have to use the terminal to install software, it's generally third party software (Flash Plugin, anyone?) by companies that "don't get it". Or it's development software that you wouldn't be running on Windows or Mac OS X anyway, because developers for those platforms don't have the transparency of process that Linux-based developers do. If you're uncomfortable with compiling software, don't - there's plenty of good software in the repositories, and plenty of third-party repos too.

A lot of the time too, instructions on these forums are given as "type: sudo apt-get install fooblah". This is the shorthand way of doing it. If you're not comfortable with the terminal, just go into the Synaptic Package Manager and install it the GUI way. If you're uncomfortable with manually editing the sources.list, then go into Software Sources.

Remember that Ubuntu is Linux, and Linux is not like Mac OS X. There is reason to what we do this side of the divide. I know, as I was a Mac user quite a few years ago, and like you I switched directly to Ubuntu (no Windows in-between).

Also remember that the biggest thing keeping people from Linux is not a lack of vector graphics or the 2 extra steps required to enable DVD playback. It's fear of having to learn new skills.

---

### Post by SunnyRabbiera on 2008-01-15
> **mikasjoman said:**
> 
1.The installation.
Everything went well, only minor issues had to be dealt with. At the end of the installation the installer just would not stop trying to update apt-get, so I had to turn my router of since Ubuntu does not let me close the connection from the wireless connection menu. 
Urgent fix to developers: Let me disconnect from the wireless menu please.

Apt sometimes has issues I admit, sometimes mirrors go down and it takes time for things to set themselves.
Luckily for you after you get things settled you can choose what mirror you want to use

> 2.After the reboot experience
After reboot, I am now ready to get dirty with Ubuntu. I want software! And, since the Ubuntu team directly helps me to update my computer, with over 145 updates, I felt that that was like any mac update I ever done before.
To me, 145 updates sounds scary, to my father it looks like the computer is going to die. 
Fix: Please stop scaring us, and bundle the updates to one. And updates seem to come every day, irritating my day. Just install them for god damn sake. I am an Ubuntu beginner and I don't want to care about updates, just fix them when I close the computer if a reboot is necessary.

well please consider that most linux developers are right on top of security patches, I know it looks less secure at first but by keeping the system up and secure is what makes linux great (in my opinion)

> 3.The irritation begins
I have a connection to the repositories that was chosen by the application to be the fastest one. Its still only about 20k/sec, so the update takes hours. Now I want to install software, but the “Add software” just keeps telling me another Synaptics is running and only one system management software is allowed to run at one time. WTF! I want to install software like I did under OSX. Remember: Download, copy to Applications folder, Done.
If there is anything that desperately needs to be fixed, then this is it. I dont care about dependencies, and neither should I have to. Mac OS X doesn't let me care about dependencies, neither should I under Ubuntu. If I want to install ten apps at the same time, let me! The current situations is simply a huge design flaw built into Ubuntu if you compare it to Mac OS X.
Fix: just make it work without showing me the problems. I dont care if two synaptics are running at one, and neither should I. And, how logical is the name Synaptics for installing software? Rename it, and if its not close to impossible, try to give me a Applications folder in the root.

well the installer process in linux is different, in some ways its better and in other ways its not.
The advantage of linux is that its packages are maintained by whoever owns that distribution, where as on OSX or windows you have to go hunting and possibly install something malicious.
The two synaptic thing is more of an issue with apt then there is with synaptic.
To make sure the system doesnt get phracked apt allows only one package manager at a time, i know its annoying if you want to get stuff working right off the bat but let updates run their course, dont just rush in or you might mess something up.

> 4.So I stop the update, I want to install cool apps!
So to make it easier for me I install applications, I decide to install CNR.com on my Ubuntu desktop.  Now again, Grrrr! After downloading the CNR.com application, the Package Installer tells me I lack 17! package files. Dependencies again and again. I get so sick about them I could throw up. And they waste my time! A lot of my time. Slow slow slow, and again, I can not install more than one application before finishing the current installation process. From a normal user perspective, under Ubuntu it is also almost impossible to find where my Applications are located. What I propose, is that the Ubuntu team creates bundles, so that an application is located in a Applications folder in the root. Even if I have to get the dependencies, I have my applications stored in a easy manner, bundled, without all the mess currently making the user disorientated. In OSX I have four folders in the root, in Ubuntu I have the scary 21 files and folders visible. Thats asking for trouble, hide them!

CNR is really not the way, if you want apps use the repositories.
really there is nothing much more CNR can offer that ubuntu already does with the exception of "legal" codecs and such
> 
5.So I move on to system administration
Preferences or Administration?? On the Mac they are one and the same since for the user the difference is tautology. Under the two scary menus, I find not less then 41 choices, some for the same purpose. The mac used to look something like that, but that was seven years ago. After installing AWN and some other apps, the menus get to the point of total disorientation. 
Let us again learn from the Mac, create a system preferences application. Under that one, lets have plugins that sort under smart categories: Sharing, Printing, Screen, Language, Startup, Sound, Other, Etc
well this part is still being developed, Gnome is getting more simplified by the day
.
> 6.So wuu... great software straight into my computer
I find a homepage to install the newly released KDE4 that looks really cool. Well, everything great, but there is one problem. They want me to go to the terminal and edit the /etc/apt/sources.list. And to make me even more scared they want me to use the terminal to install it via aptitude. After working with Ubuntu for a while, it seems that most of the software that people write on the internet is installed via the terminal! Thats back to the 90-s baby, not after the millennium.
Urgent fix: as long as the internet is flourishing with guides using the terminal Ubuntu or  Gnome will not stand a chance against Windows. At least 98% of the software has to be as easy as klicking a button. If everybody are making these guides with terminal commands, why can't the standard just be klick and install? Add the content to a .install file with all the necessary commands. I don´t want to know what is happening under the hood, I just want things working.

well right now i would stay away from KDE4, it is still too early and its nowhere near where gnome and kde3 is, latest doesnt always mean "greatest"

> After a month: Well I actually feel the same way and because of the lack of graphical tools I had to move back to my mac sometimes. 
I have also tried to install OpenGroupware with no success and well as with many other applications. I feel it´s great that my Ubuntu looks like a OSX now, Mac4Lin and AWN, and I am getting more used to the terminal (I think that is a bad thing). I wish that Hardy would be called Easy, but then it would have to be called hEasy I guess ;) But, mainstream users will not choose Ubuntu if they need to go once to the terminal. Think about it, Windows is easier from that perspective.

well not every apple or windows app will work on linux, remember linux is a OSX and windows alternative, not a replacement...

> I, as many other of my friends cant seem to get the microphone working. And the Partition tool was not installed from scratch. I think this is because the menus are to filled up because they either does not have sub menus or a application as KDE or OSX which I prefer in logical sections. I really wish that Gnome would switch to a nice System preferences application insted of seeing two menus filling up.

this is certainly a possibility in the future, like i said gnome is getting simpler by the day.

> Another thing I am missing is the beautiful vector graphics both OSX and KDE4 now has. I know this is a message more to the Gnome people, but still. I guess that with system wide vector graphics there also quickly would be developed vector graphic tools close to Illustrator.
well there is a good alternative for linux to illustrator, give inkscape a shot, I think its pretty good myself.

---

