---
title: "yast4ubuntu"
date: 2006-07-26
forum: The Cafe
---

### Post by pirast on 2006-07-26
Hey guys,
maybe you heard of yast4debian some time before. The project tried to port YaST to debian, but sadly the developers didn't have enough time and ressources so the project had been stopped.

I though a little bit about YaST and Ubuntu and I believe that it would be perfect when Ubuntu could deliver it. And YaST isn't just a control center, no it is modular. That means that everybody can hack new modules to configure services and system settings or can hack on a new fronted (for example GTK, someone is currently hacking on it) or that we could have our old System -> x configuration system. The menu entry would load the correct YaST module and everybody would be happy.

So I tried to compile YaST on Ubuntu - but sadly I am not that good so I stuck.

Maybe we can plan/dream a little bit here - and when we are really lucky, some people can start a yast4ubuntu project.

That would be really great :-D 

The sourcecode can be found here:
[YaST sourcecode download]("http://developer.novell.com/wiki/index.php/YaST")

And that is the YaST development mailing list, if there are questions to the developers, this is probably the right place.
[YaST development mailing list (low traffic)]("http://forge.novell.com/mailman/listinfo/yast-dev")

Some screenshots of YaST can be found [here]("http://shots.osdir.com/slideshows/slideshow.php?release=637&slide=43")

Martin

---

### Post by T700 on 2006-07-26
Why would you want YaST on Ubuntu?  I'm serious--I'm trying to understand the advantages.

Paul

---

### Post by Ricardo Cruz on 2006-07-26
Since you Ubuntu guys prefer Gnome, just want to point out the upcoming Yast-GTK interface: [http://en.opensuse.org/YaST2-GTK](http://en.opensuse.org/YaST2-GTK)

Besides being interface frontend independent, Yast also allows you to run the backend and frontend in two different machines. This means that you may setup another computer from the confort of the graphical interface. Of course, using the ncurses interface through ssh (or whatever) is also possible.

More about Yast: Yast-core is a programming language (that is byte-code compiled and interpreted at run-time ala Python) that serves as a platform to make configuration tools easy to develop and confortable to use. So, you should be able to get the core and interfaces modules working fairly easily.

The actual work would be on the applications (ie. the configuration tools) of the said platform. For instance, Inetd.ycp (the services config tool) calls functions from Service.ycp that relies on how Suse organizes deamons under /etc/init.d (I believe other distributions have them organized under directories or something).

I am not a Yast developer guru, I have just been introduced to the code as part of my Summer of Code project for the development of the GTK+ interface. Anyway, even if I am a Suse user, I would like to have Yast being shared between desktops and I will follow this thread and offer my help to the best of my knowledge.

As I already commented on yast-public, I don't think a fork like Yast4Debian is the way to go, because then you will have a lot of added work to merge changes on main Yast. Instead, something like adding a pre-processor to Yast language (YCP) or some other technics that allows us all to work on the same space may prove to be a more sustainable project (for all I know, Yast4Debian is dead).

---

### Post by Zelut on 2006-07-26
Last time I used SuSE and YaST, which I will never do again, I realized the superiority of aptitude.  Why anyone would want to use a bloated, slow and un-intuitive system like YaST I don't know.

I've recently re-compared Ubuntu with other big players like Fedora 5 and SuSE 10.1.  I wish these other groups would realize that Linux doesn't **have** to be complicated.

Just use Ubuntu, stick with efficient & fast aptitude and be happy.

---

### Post by Terracotta on 2006-07-26
> **kuyaedz said:**
> Last time I used SuSE and YaST, which I will never do again, I realized the superiority of aptitude.  Why anyone would want to use a bloated, slow and un-intuitive system like YaST I don't know.

I've recently re-compared Ubuntu with other big players like Fedora 5 and SuSE 10.1.  I wish these other groups would realize that Linux doesn't **have** to be complicated.

Just use Ubuntu, stick with efficient & fast aptitude and be happy.

There's more to yast than just a program installer...

---

### Post by Brunellus on 2006-07-26
> **Terracotta said:**
> There's more to yast than just a program installer...
indeed, as I recall, YaST was a terrible program installer, but an EXCELLENT system administration tool.

---

### Post by pirast on 2006-07-26
...too late


wait, i didn't plan to get away from apt, it should stay of course. you are complaining about rpm, and i can fully agree with you. it is really slow.

but in my opinion yast itself is a great tool to configure services and programs, the package management is really bad but that doesn't have to be debianized..

did you ever had 2 soundcards and wanted the second one to be the output device? I can tell you that with yast it is really easy to configure - but in Ubuntu I have to change the modprobe order myself..

and you forget that yast would be an option to fine tune your system. everything stays as it - everything is detected and configured automatically and apt stays of course, too.

but if you want to fine tune your system, for example change your soundcard configuration you can use yast..

here are some examples of gui modules of yast that Ubuntu does not have yet:
ntp-server
xorg settings
xen (of course ubuntu's kernel would have to support it )
pppoe configurator (yeah it already exists in Ubuntu but it is a commandline application - not that good for beginners)
dns server
dhcp server
http server
firewall

and that is only a cut of the list.. there are many more. As already said it can be extended with ubuntu modules, and they work steamless integrated with kubuntu and ubuntu.


Martin

---

### Post by Terracotta on 2006-07-26
> **Brunellus said:**
> indeed, as I recall, YaST was a terrible program installer, but an EXCELLENT system administration tool.

Was what I ment, but for programs we already have adept and synaptic :D. But the administrtion tools in kubuntu are rather weak in my point of view. They're going to improve it, but still, yast and sax could help, especially if they decide to cooperate with Novell on this one.

---

### Post by mkw87 on 2006-07-26
Instead of porting yast, why not simply get these functions implemented in ubuntu?  GUI's for various settings are a want from a lot of users, I have seen various threads requesting the upcoming ubuntu to have a GUI setup for xorg.  As ubuntu progresses more GUI's will be created, it just takes time to develop :P

---

### Post by Brunellus on 2006-07-26
> **mkw87 said:**
> Instead of porting yast, why not simply get these functions implemented in ubuntu?  GUI's for various settings are a want from a lot of users, I have seen various threads requesting the upcoming ubuntu to have a GUI setup for xorg.  As ubuntu progresses more GUI's will be created, it just takes time to develop :P
because yast is a perfectly good tool, and is now open to be developed and adapted by the community.

---

### Post by pirast on 2006-07-26
I think that porting yast and getting the functions implented in Ubuntu is nearly the same:

- Getting it to compile with Ubuntu
- Make it work with Ubuntu

Getting the functions sounds easier but I doubt because a new gui would have to be created. When porting YaST it is easy to merge new YaST versions and it can be flawlessly integrated (QT Engine for Kubuntu, GTK Engine for Ubuntu, ncurses Engine for command line - everything is available yet)

I believe that it should work like that: An Ubuntu developer develops at YaST upstream and makes sure that it is possible to compile and run YaST in Ubuntu. Thus newer versions would run in Ubuntu, too and YaST would just have to be packaged.

A fork like yast4debian wouldn't be that good because it just uses too much manpower.

---

### Post by Virogenesis on 2006-07-26
yast is good i liked yast from my suse days and to be perfectly honest when yast is sorted out for gtk i'll be interested in getting it sorted for my system.

---

### Post by linuksamiko on 2006-07-26
The whole thing about Yast is that you have a GUI to control your computer (hardware, security etc). Maybe you don't have to compile Yast. There is something that is interesting for everyone who wants/needs a GUI to control his computer.

I didn't install it yet so I have no idea how good or bad it is but many people like it.

[http://ubuntuforums.org/showthread.php?t=207894](http://ubuntuforums.org/showthread.php?t=207894)

---

### Post by Virogenesis on 2006-07-26
> **linuksamiko said:**
> The whole thing about Yast is that you have a GUI to control your computer (hardware, security etc). Maybe you don't have to compile Yast. There is something that is interesting for everyone who wants/needs a GUI to control his computer.

I didn't install it yet so I have no idea how good or bad it is but many people like it.

[http://ubuntuforums.org/showthread.php?t=207894](http://ubuntuforums.org/showthread.php?t=207894)
its good i use it myself and it is worth installing but its not as powerful as yast but thats because its not intended to be

---

### Post by SuperMike on 2006-07-28
Guys, check out my work at:

[http://sourceforge.net/projects/ust/]("http://sourceforge.net/projects/ust/")

[IMG]http://sourceforge.net/dbimage.php?id=82030[/IMG]

---

### Post by Ricardo Cruz on 2006-07-29
Just want to say that Yast is not just about the setup tools, but the platform. Even if you don't like the tools ("very rpm oriented" or whatever) you may want to use Yast as the platform for UST that SuperMike is doing.

I am the Yast-GTK guys and I haven't really programmed much in YCP. But from what I am I aware, it allows things like accessing configuration files like if they were data structures. It should allow things like going to a configuration file and only change the value of some parameter of some group, creating it if it isn't set, and the thing is all abstract (it supports various different syntaxes).

About interface programming, is has a good set of available widgets and they are pretty rich (eg. even editable combo boxes support filtering). You design the interface in a syntax similar that resembles Lisp and is really confortable to use, and you can do things like get or set proprieties, as well as replacing widgets.
As an example, here is how you would do a simple editor with a HTML preview:

```
{
	UI::OpenDialog (
		`VBox (
			`RichText (`id (`rtext), ""),
			`MultiLineEdit (`id (`source), `opt(`notify), "Source code", ""),
			`PushButton (`id (`close), "&Close")
		)
	);

	any ret = nil;
	repeat
	{
		ret = UI::UserInput();

		if (ret == `source)
		{
			UI::ChangeWidget (`id (`rtext), `Value,
			                  (string) UI::QueryWidget(`id(`source), `Value));
		}

	} until (ret == `close || ret == `cancel);

	UI::CloseDialog();
}
```

 Result:
[IMG]http://rpmcruz.planetaclix.pt/trash/yast-editor.png[/IMG]

 The user also get the bonus of having the interface for GTK+, Qt and ncurses. As well as some other goodies like macros. (It is possible for an administrator setup a machine with some Yast tool and then apply that to other machines.)

 Currently, Yast developers are on vacations, so if you have questions of technical nature you'll have to wait. Anyway, I can try to help with what I know.

---

### Post by gruvsyco on 2006-07-29
I think Yast is pretty damn slick although, the package management portion leaves A LOT to be desired.  If Synaptic functionality could be integrated into it, I think it would be awesome on Ubuntu.

---

### Post by SuperMike on 2006-07-29
By the way, I need developers to help me. Unfortunately I don't have the time to complete and maintain this. The menuing system I have built in Bash might just be "good enough" for someone else to build upon, although I wish I could have built it in PHP-cli so that I could widen the base of programmers to the huge PHP market. I'm just not clear how to use PHP-cli to take console input reads and hold the session in a loop. Most of my PHP work has been web-based.

I'm deeply sunk in a project for a PHP-based CRM right now and can't commit any more time, although I would hope that someone could own the project and run with the ball.

Via Launchpad and other means, I've mentioned it to the Ubuntu core team and am awaiting callback on their interest.

Some tasks that people could do:

* Rewrite what I have done in PHP-cli with almost the same look and feel.

* Using the same red header at the top, create simplistic black and white data entry screens that one can tab around in and then press function keys like F3 to exit, F5 for back, F6 for next, F8 for form reset, F9 to cancel, and F10 to commit.

* Once the data entry is completed and stored in variables, another module needs to be written to edit existing text files for doing things like adding users in password, shadow, NIS, or LDAP modes; editing runlevels; etc.

And if people send me demos for any of this in either Bash or PHP-cli, I might be able to build upon that.

Just note the project is GPL and is meant to be community-driven.

---

### Post by Ricardo Cruz on 2006-07-29
> **gruvsyco said:**
> I think Yast is pretty damn slick although, the package management portion leaves A LOT to be desired.  If Synaptic functionality could be integrated into it, I think it would be awesome on Ubuntu.
 What don't you like about the package selector? If it is the interface, I would really like to hear about it as I am still designing the GTK+ interface for it.

 Here is a message I sent to the opensuse mailing list with a first thought on the interface:
[http://lists.opensuse.org/archive/opensuse/2006-Jul/0372.html](http://lists.opensuse.org/archive/opensuse/2006-Jul/0372.html)


 SuperMike, your menu looks really slick, but I think that's the least important thing when starting such a project. I think you should start by making a library for easy edition of configuration files. Also, the ncurses library is not really that friendly for RAD and a wrapper would be a must I would say, especially because it could then be adapted for graphical interfaces. You don't really need to create a whole new programming language like Yast does, but c'mon, a menu is something you can do in 15 minutes and doesn't really make the project more sustainable.

 Btw, nobody has mentioned yet the Yast manual, which seems very good, and is important to have a look to have a constructive thread:
[http://forgeftp.novell.com//yast/doc/SL10.1/tdg/](http://forgeftp.novell.com//yast/doc/SL10.1/tdg/)

 It should be said that Yast Qt interface really looks ackward, which gives a bad image to Yast, but this is something that can be worked out (and will for the GTK+ one).
 All in all, Yast is a top-quality, free software platform, but even if you don't use Yast, the way to develop setup tools is to make a platform first. Else, your applications will be a lot, and I mean a *lot*, harder to do and you'll have to re-invent the wheel over and over, if you want to have more than one interface [1], the macros I mentioned or remote administration [2].

[1] just started to imagine how would it be to have a web interface for Yast... Seems doable.
[2] I have never heard of anyone using this, since admins just prefer ssh and yast-ncurses, but this is surely possible as the code that reads and makes changes to the system runs independently from the interface.

---

### Post by gruvsyco on 2006-07-29
> **Ricardo Cruz said:**
> What don't you like about the package selector? If it is the interface, I would really like to hear about it as I am still designing the GTK+ interface for it.
Hi Ricardo,

I don't know if it's a function of SuSE, their repos, RPM or what but package management just seems difficult in SuSE compared to Ubuntu/Synaptic.  I like how everything just seems to work... Search is my best friend.  If you have broken packages, it's easy to find and fix and it's easy to pin a file so it doesn't get flagged for future upgrades.

I think it's great that you're over here on the Ubuntu boards looking for feedback too.  I think the various distros really can learn alot from each other.

---

### Post by lotusleaf on 2006-07-29
> **Brunellus said:**
> because yast is a perfectly good tool, and is now open to be developed and adapted by the community.

Agreed, and last year in [another thread](http://www.ubuntuforums.org/showthread.php?t=110161) I mentioned how I wished that "**Ubuntu had something like [color=red]sax2[/color] (SuSE advanced X Window System-configuration)**". Sure people can edit their xorg config to adjust their monitor's resolution, but I'm betting that a good majority of Linux newbies would prefer a GUI solution for what should be a simple task.

To sidetrack to Kubuntu for a second, the past few versions I've tried (and still use with delight) have been missing the resolution changing feature in the desktop settings unless one finds, modifies, and saves the correct file. Why is this happening? IMO that's about as dumb as removing the shortcut to the KDE Control Center in favor of one small menu. Hello, McFly?

I used to use SUSE but left it for Ubuntu, and while I disliked YaST's package management, I still miss some of the easy-to-use tools YaST offered, such as sax2, especially when I'm setting up Ubuntu for new Linux users.

Why don't we forget about discussing YaST's package management offerings since threads about yast4debian/yast4ubuntu/etc. usually get mired in useless oceans of "I hate YAST's package manager" nonsense and eventually drown the thread with negativity. YaST has a lot of useful utilities to offer ASIDE from the package management, so why don't we focus on what USEFUL offerings YAST may have for Ubuntu if ported?

---

### Post by Ricardo Cruz on 2006-07-30
> **lotusleaf said:**
> Agreed, and last year in [another thread](http://www.ubuntuforums.org/showthread.php?t=110161) I mentioned how I wished that "**Ubuntu had something like [color=red]sax2[/color] (SuSE advanced X Window System-configuration)**". Sure people can edit their xorg config to adjust their monitor's resolution, but I'm betting that a good majority of Linux newbies would prefer a GUI solution for what should be a simple task.
 I can check that for you, but I am pretty sure that Sax isn't really a Yast tool. I mean, it is integrated in the Yast control center, but it isn't really made using Yast. There is some more integration in the installer, but I believe is made possible through a set of Sax command line options and output.

 Anyway, if you guys get serious about a Yast port, it should be possible to get people from Suse exciting and doing that for you. Text mode isn't really desirable because you really want to see changes on the fly, neither is macros, since graphical card / monitor is just too specific and automatic detection should be safer. But I see a couple of advantages: file editing could be made better (hopefully getting rid of the "# PLEASE DO NOT EDIT THIS FILE!") and one would get the upcoming GTK+ interface.
 The main advantage for you would of course be that it would be easier to port.

---

### Post by SuperMike on 2006-07-30
With the UST project on SourceForge, I'm currently experimenting offline with converting the menu demo entirely over to PHP-cli. I just found a way to do this today using fopen, fgets, and system('stty echo') and system('stty -echo') but am working out the kinks. Once it's in PHP-cli with wrapper functions, it's going to be a lot easier to get others to sign up and finish out the data entry forms and the "file configurator".

You may see a news item on fridge.ubuntu.com soon about this. Stay tuned. The Ubuntu Fridge editor emailed me back.

---

### Post by pirast on 2006-08-11
It's real :)

---

### Post by hogman23 on 2006-08-11
> **T700 said:**
> Why would you want YaST on Ubuntu?  I'm serious--I'm trying to understand the advantages.

Paul

Thank You Paul, I was about to type the same exact line when I read this post.  I almost threw up when I saw the title.  Why would you put something as intrusive as Yast on a perfectly good linux distro.  Yast is the whole reason that we aren't putting SUSE servers in production other than those servers that are replacing NetWare boxes.  Apt is a good part of the reason that we are moving our RedHat boxes to Ubuntu.
Please don't ruin a good thing with an intrusive piece of dung!

---

### Post by hogman23 on 2006-08-11
> **kuyaedz said:**
> Last time I used SuSE and YaST, which I will never do again, I realized the superiority of aptitude.  Why anyone would want to use a bloated, slow and un-intuitive system like YaST I don't know.

I've recently re-compared Ubuntu with other big players like Fedora 5 and SuSE 10.1.  I wish these other groups would realize that Linux doesn't **have** to be complicated.

Just use Ubuntu, stick with efficient & fast aptitude and be happy.

Exactly.....
Dude if you want a bubbly, dumbed down interface for end-user administration of machines, then go back to Windows!!!

---

### Post by %hMa@?b&lt;C on 2006-08-11
> **hogman23 said:**
> Exactly.....
Dude if you want a bubbly, dumbed down interface for end-user administration of machines, then go back to Windows!!!

you may feel that way, but many people dont.  I personally tried SuSE, and found it adequate, but Found that i had fallen into dependancy hell rather quickly. Never again will i use a non Debian distro.  But back on the topic, you may not need YaST, I for one dont need YaST for ubuntu, but it would be nice, becuase it does bring a certain user-friendlyness to linux for those of us who need it or who have family members who need it *cough*my dad*cough*

---

### Post by pirast on 2006-08-11
You muddle up RPM with YaST!

Martin

> **hogman23 said:**
> Thank You Paul, I was about to type the same exact line when I read this post.  I almost threw up when I saw the title.  Why would you put something as intrusive as Yast on a perfectly good linux distro.  Yast is the whole reason that we aren't putting SUSE servers in production other than those servers that are replacing NetWare boxes.  Apt is a good part of the reason that we are moving our RedHat boxes to Ubuntu.
Please don't ruin a good thing with an intrusive piece of dung!

---

### Post by ice60 on 2006-08-11
i had to install SUSE becuase Ubuntu can't see my HDDs. i don't know what the difference beteen Yast and Yast2 is :confused: , but i think SUSE uses Yast2 now.

i think the fastest Yast2 will startup is just over one minute on 10.1 i hope it's faster on debian based systems.

---

### Post by pirast on 2006-08-11
Yeah, I have it currently starting in ~ 1 second.. The user module starts in ~ 5 seconds :) I was amazed of the speed since I used SuSE a long time ago, too.

Here is a new screenshot, I just got the user module running.

Martin

---

### Post by peanut butter on 2006-08-11
first Yast is the terminal version of Yast2 while Yast2 is the GUI i think.
i liked useing yast when i had suse. but i didnt know you could use it to connect from computer to another. if i could help in any way sign me up. sadly i dont know python but if there is any way i can help by putting the paths right or anything like that that a non programmer can do ill gladly help.

---

### Post by Terracotta on 2006-08-11
> **pirast said:**
> Yeah, I have it currently starting in ~ 1 second.. The user module starts in ~ 5 seconds :) I was amazed of the speed since I used SuSE a long time ago, too.

Here is a new screenshot, I just got the user module running.

Martin

Wow Yast4ubuntu is really getting along? How about the QT-version? Or is the one you use the QT-version?

---

### Post by win_zik on 2006-08-11
> **hogman23 said:**
> Thank You Paul, I was about to type the same exact line when I read this post.  I almost threw up when I saw the title.  Why would you put something as intrusive as Yast on a perfectly good linux distro.
Maybe because contrary to you they actually know what yast is? :???:

---

### Post by pirast on 2006-08-11
> **Terracotta said:**
> Wow Yast4ubuntu is really getting along? How about the QT-version? Or is the one you use the QT-version?

The thing on the second screenshot is the Qt one. :) I am currently trying to get the GTK one working, too. Maybe I have to contact Ricardo tomorrow since I stuck.

I do not want to make any promises since it is just for fun. I am currently finding out how hard it would be to run it on Ubuntu (a bunch of modules does not run - and they require the most work I believe). Furthermore the .debs of YaST I created are not as clean as they should be so there is a lot of work to do.

Martin

---

### Post by pirast on 2006-08-12
Okay, I got the YaST GTK module running, too:

---

### Post by Virogenesis on 2006-08-12
what did you have to do to get the gtk version running and does it work well?

---

### Post by pirast on 2006-08-12
I got the yast2-gtk code from svn, created the debian dir with debhelper and modified it a little bit, built it, changed line 14 in ycc.sh to

module=`/usr/bin/zenity --title "Yast Control Center" \ 

ran it and selected a working module.

a list of parts that i have running is available on [http://en.opensuse.org/Porting_YaST](http://en.opensuse.org/Porting_YaST) , I do not know which ones you need in order to run the gtk one, they maybe are yast2-devtools liby2util yast2-core  yast2-testsuite yast2-pkg-bindings  libzypp  yast2-perl-bindings and yast2

it (the gtk gui) works well but it is in an early stage - that means that there is no control panel or something like that, you have to select the module that should be loaded manually.

martin

---

### Post by denver on 2006-08-21
Yast is extremly useful! Package management s**ks big time, but the rest is perfect for system configuration. I moved from Suse to Kubuntu after ~ 1 year of using linux. I chose Suse because of yast. Back then (when i was just starting to learn about Linux) i had no ideea what xorg.conf is...hell i had no idee what X was! 
Yast really helped me configure my system to the point were i felt confortable enough to dump windows for good.
You cant actualy expect a new user, that has probably used Windows all his life, to go arround editing conf files...i can tell you from my experience that it scares the s**t out of them.
Yast helped me configure my computer and learn about whats happening(the info on the left side of yast always explayned things in an idiot-proof language).
I have no problem configuring my Linux box without yast...but i had time to learn without getting discouraged.
Yast should be OPTIONAL for whom ever wants it.

just my 2 cents

---

### Post by Ramaddan on 2006-09-01
Hi,

Any updates on this so far?

Any available .deb?

Thanks.

---

### Post by pirast on 2006-09-01
yeah, i am currently waiting for the debian mainteaner of hwinfo to fix a hwinfo problem.. it detects every pci device as an isdn adapter. the user module works fine already, i will see if i can provide debs.

martin

---

### Post by pirast on 2006-09-01
debs are available on [http://rapidshare.de/files/31571341/yast4ubuntudebs0-000000001.tar.gz.html](http://rapidshare.de/files/31571341/yast4ubuntudebs0-000000001.tar.gz.html)

its a tar.gz archive.. the debs should be installed at the same time with dpkg -i *.deb for example.

please note that it is in a very early stage and that i know that a lot of things do not work. but i find it amazing to see some things already working on ubuntu :D

although it should not shoot up your system i cant guarante it

---

### Post by Ramaddan on 2006-09-01
Thanks, it's very nice of you. I think you're doing great work.

Also, would you know how I can get in touch with the Ubuntu developpers?

Thanks for your help.

---

### Post by jpowermacg5 on 2006-09-08
This yast4ubuntu project looks pretty good. I still have SuSE 10.0 installed, and really liked what the YaST control center did thru the terminal and SSH. I think that's 1 of the nice features from YaST (Besides it's installer being the best in class installer i've ever seen, especially in terms of configuration u can do in the installer also. Like setup X and stuff.).

I've been looking for a YaST like program for other non SuSE distro's, that I could get remote administration stuff thru a SSH or just terminal command. YaST used to run really nicely thru the shell, allowing u to do everything u can setup from YaST GUI.

Now I see someone here is making a YaST4Ubuntu... can't wait till it's finished.


And yeah, I can agree with you guys on the package management for YaST... but not because I've actually used it.... I've just never figured out how to get it to work online... lol.... works good from the DVD... but never got it working online... but I havn't booted it up in a while either to try to fix it with online instructions.

---

### Post by pirast on 2006-09-12
okay, ncurses seems to work too.. thanks for the kind help of the novell guys..

---

### Post by Sammi on 2006-09-12
You really should get this registered in the [3rd Party Ubuntu Projects]("http://www.ubuntuforums.org/forumdisplay.php?f=46") sub-forum! It would mean more exposure and more help for the project.

---

### Post by pirast on 2006-09-13
yeah but first i want to create an automatic build server with svn sync of the yast svn and that probably will take some time.

then i can image yast4ubuntu being listed as an ubuntu 3d party project

---

### Post by atrus123 on 2006-09-13
Yast is a great tool and one of the things that makes SuSE a enterprise level distribution.  The installer is pretty slow, this is true, but Yast does much more than just install stuff.  That said, while I wouldn't mind seeing it ported over, I doubt I'd use it.  

If I wanted Yast, I'd just use SuSE (and I do, on my production tower).

---

### Post by Terracotta on 2006-10-04
> **pirast said:**
> yeah but first i want to create an automatic build server with svn sync of the yast svn and that probably will take some time.

then i can image yast4ubuntu being listed as an ubuntu 3d party project

If you register the project in Launchpad (which works with bazaar rather than subversion), you might not need to set up an extra server. Most projects around here seem to use it.

---

### Post by pirast on 2006-10-04
my problem is tha I need to sync the yast svn somehow :(

---

### Post by Terracotta on 2006-10-04
> **pirast said:**
> my problem is tha I need to sync the yast svn somehow :(

darn that's a shame. Ah well, I'll try to read svn-stuff instead of bzr stuff then.

---

### Post by ComplexNumber on 2006-10-04
ubuntu desperately needs something like yast.

---

### Post by bonzodog on 2006-10-04
as an alternative, the OTHER good admin system is the Drake tools from Mandriva. We could port them to Ubuntu....

---

### Post by ComplexNumber on 2006-10-04
> **bonzodog said:**
> as an alternative, the OTHER good admin system is the Drake tools from Mandriva. We could port them to Ubuntu....
i guess it wouldn't be that much of a problem. its written in gtk-perl.

---

### Post by dca on 2006-10-04
I'm still waiting for YaST to display the Software I have installed on my laptop *looking at watch*....

---

