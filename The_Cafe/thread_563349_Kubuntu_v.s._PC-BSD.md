---
title: "Kubuntu v.s. PC-BSD"
date: 2007-09-29
forum: The Cafe
---

### Post by RAV TUX on 2007-09-29
I thought I would share this:

> [IMG]http://userimages.ittoolbox.com/user/s_964720.jpg[/IMG]Kubuntu v.s. PC-BSD
 [Dru]("http://www.ittoolbox.com/profiles/dlavigne6") (SysAdmin, Technical Writer, Technical Trainer) Posted 8/18/2007
[Comments]("http://blogs.ittoolbox.com/unix/bsd/archives/kubuntu-vs-pcbsd-18431#comments") (68 ) | Trackbacks (0)


I played a bit with Kubuntu this morning in preparation for the article "PC-BSD for Ubuntu Users". It made sense to me to compare the two operating systems if they were both running the same window manager (KDE) so I wouldn't be distracted by Gnome v.s. KDE issues. That was my first mistake....

I wanted to test on the same hardware to get an idea of performance/responsiveness (I have other PC-BSD systems in my home lab for side-by-side comparisons). So yesterday I did a fresh install of the latest [ snapshot]("http://snapshots1.pcbsd.org/") of PC-BSD 1.4 (which is still in beta) on my test system. Took about 15 minutes. This morning I did a fresh install of [ Kubuntu 7.04]("http://www.kubuntu.org/download.php#latest") on the same system, this one took over an hour. And it was one boring install, but I digress as those who have installed both know what I mean.

Being the meticulous type, I went through the KDE menus side-by-side to see what each operating system installed and was surprised to see that PC-BSD installed about twice as much software out-of-the-box. For those who want the boring details:[LIST]
[*]Both provided Log Out, Lock Session, Switch User, Run Command, Help, and Find Files/Folders
[*]Kubuntu placed the following under System Settings (this wasn't menu style but a separate screen of icons): Personal had About Me, Regional & Language, Accessibility, and Default Applications icons; Look & Feel had Appearance, Desktop, Splash Screen, Window Behavior, and Notifications icons; Computer Administration had Date & Time, Keyboard & Mouse, Monitor & Display, Sound System, Printers, and User Management icons; Network Connectivity had Network Settings, Sharing, and Bluetooth icons
[*]PC-BSD called this Settings and provided nearly 70 options within its submenus; for that reason I'll just list the names of the submenus: Control Center, Appearance & Themes, Desktop, Internet & Network, KDE Components, Peripherals, Regional & Accessibility, Security & Privacy, Software & Updates, Sound & Multimedia, and System Administration
[*]the next 6 menu items had the same names but different applications where the existing applications were almost the same between PC-BSD and Kubuntu and the main difference being the amount of installed software. PC-BSD installed 21 more Utilities, 1 more System application, 5 more Multimedia applications, 4 more Internet applications, and 9 more Graphics applications. The other noticeable difference is that Kubuntu installs OpenOffice by default
[*]PC-BSD also includes an Editors menu (with 3 applications) and a Desktop menu with 6 applications; these menus don't exist in a Kubuntu install[/LIST]So far, so good. I'm the type who likes to install my own software anyways. Firefox is usually the first thing I install as I detest Konqueror. On PC-BSD I clicked the desktop icon Get Software (while connected to the Internet). Clicking on the hyperlink "The PBI Directory" took me to the PC-BSD software repository. Firefox happened to be listed under Latest Software but I also could have used the search box. After choosing a mirror, the installation program downloaded, prompted me for the administrative password I chose during the install of the operating system, asked if I wanted a desktop icon and an entry in the menu, and informed me when the installation was complete. Took all of two minutes.

Now for Kubuntu. I selected Add/Remove Programs from the K menu which prompted for my user's password (Ubuntu doesn't create a root password as **sudo** is used for administrative access). This started the Adept Installer. Firefox was listed, but was greyed out, along with all of the other software currently not installed. Hmmmm.... I opened up Help from the help menu to see if I needed to add a repository. Help indicated that I could do so from System -> Administration -> Software Sources. Unfortunately, Administration was nowhere to be found in the System menu or in any other menu. So, off to the Kubuntu website to see if the documentation was complete. After a bit of digging it became apparent that the documentation was complete, but for an Ubuntu (i.e. the gnome version) install. The Kubuntu instructions are totally different which made me wonder why they weren't included with the Kubuntu installation. Oh well, at least I had found the proper instructions, They told me to go to the View menu within Adept and select Manage Repositories. I would have loved to have been able to do that, but as you may have guessed by now, that menu option didn't exist either.

Now, I'm a power user who can easily **sudo apt-get install firefox**. My deeper question is why include a GUI which doesn't work, provide the documentation for a different operating system (even though the website insists its not a fork so I guess that is why), and why provide documentation which refers to non-existent menu options? If I was a new user, I would have bitterly regretted the hour I wasted on the install and would have literally re-burned that Kubuntu CD with a match. I would have then reinstalled another operating system where double-clicking an installation wizard or using an add/remove programs actually does something.

Instead, I downloaded the [ Ubuntu]("http://www.ubuntu.com/getubuntu/download") version and waited another hour for that install to finish. This install was even more boring as the progress bar didn't work--the only indicator that something was actually happening was the blinkety lights on my cdrom drive. Once installed, it was not hard to tell that the developers are concentrating on the gnome version as the difference in functionality is night and day between Ubuntu and Kubuntu. Adept works and a working version of Synaptic is also installed.

Still wishing to pursue the KDE theme, I installed kubuntu-desktop from Synaptic. I'm still waiting for the 225 packages to download and install. Synaptic looks very similar to Yum--I'll let you know if it works any better or if it also breaks half the software on the system. (you don't want to get me started on yum....)

/* begin rant

If I'm sounding fiesty (pun intended) it is because installing software shouldn't be rocket science, even for new users. It's the job of the package manager to properly handle dependencies, not the user, not even the superuser. And having software repositories spread all over god's half-acre is a lousy way to distribute software. Give me pbidir.com or freshports.org anyday.

*/ end rant[http://blogs.ittoolbox.com/unix/bsd/archives/kubuntu-vs-pcbsd-18431](http://blogs.ittoolbox.com/unix/bsd/archives/kubuntu-vs-pcbsd-18431)

---

### Post by southernman on 2007-09-29
What is the point? Anyone can compare an apple to an orange and come up with the differences.

Useless IMO

---

### Post by RAV TUX on 2007-09-29
> **RAV TUX said:**
> I thought I would share this:

[http://blogs.ittoolbox.com/unix/bsd/archives/kubuntu-vs-pcbsd-18431](http://blogs.ittoolbox.com/unix/bsd/archives/kubuntu-vs-pcbsd-18431)

Having used both Ubuntu and PC-BSD I have to say that I understand what she's talking about, not the install part but the pbiDIR for new users. 

As a new user PC-BSD is much easier.

For a more seasoned user like myself I prefer apt-get and the terminal over any GUI application.

I currently have an old computer that I have installed PC-BSD on, it is not my primary computer.

In fact I specifically put PC-BSD on it because I am giving it away. I'm giving it to my Mom & Dad, they are 68 and 71 respectively and this will be their very first computer.

I honestly am not into the DISTRO_A VS DISTRO_B paradigm. I find that K/X/Ubuntu are quite awesome all though I currently use a Debian Lenny enabled Elive. I also find that PC-BSD is also great. What the author did not touch on was activating GNOME on PC-BSD which can also be done.

It boils down to community in the end and aside from fedoraforums I have yet to find a community that can compare to ubuntuforums.

---

### Post by cogadh on 2007-09-29
I can't tell you how many of these things I have already read before. 9 times out of 10 they are little more than people who are fans of the distro that Ubuntu is being compared to trying to find some reason why "their" distro is better than Ubuntu, despite the fact that it has been eclipsed by Ubuntu in popularity. Its really not a matter of one being better than the other (let's face, all Linux distros are basically the same at the core), its a matter of what you prefer. Frankly, more people are preferring Ubuntu over other distros every day and that is (for some reason) threatening to loyal fanboys and fangirls of those other distros.

---

### Post by RAV TUX on 2007-09-29
> **southernman said:**
> What is the point? Anyone can compare an apple to an orange and come up with the differences.

Useless IMO

It is notable because PC-BSD has decided to put this on the front page of their website:

[http://www.pcbsd.org/](http://www.pcbsd.org/)

I don't see it as negative, but something that Ubuntu can learn from. Constructive criticism is always good but only if the positive is extracted from it and strength is built.

To respond in a negative, or aloof way whether it be from a user or development is not very constructive overall. Like it or not these are our peers.

---

### Post by RAV TUX on 2007-09-29
> **cogadh said:**
> I can't tell you how many of these things I have already read before. 9 times out of 10 they are little more than people who are fans of the distro that Ubuntu is being compared to trying to find some reason why "their" distro is better than Ubuntu, despite the fact that it has been eclipsed by Ubuntu in popularity. Its really not a matter of one being better than the other (let's face, all Linux distros are basically the same at the core), its a matter of what you prefer. Frankly, more people are preferring Ubuntu over other distros every day and that is (for some reason) threatening to loyal fanboys and fangirls of those other distros.

PC-BSD is not Linux, but I get your point and it is something that came to mind, following the recent PCLinuxOS article. 

Is this from a fangirl of PC-BSD or a developer of PC-BSD?

Regardless, any criticism should be learned from objectively not defensively.

---

### Post by southernman on 2007-09-29
Well, I don't think [Dru]("http://www.ittoolbox.com/profiles/dlavigne6") would appreciate being called a "he" for starters. :p

My point still remains, *BSD is BSD, *buntu is GNU/Linux. While they have some similarities, they aren't something anyone should try to do a side by side review and make sense of it. The few BSD'ers I know, makes their skin crawl to be grouped into the GNU/Linux category. I know it's painting with a broad brush, but the ones I know are definately more inclined to be in the elitist group. Perhaps even... rightfully so. Full of RTFM's! ;)

FWIW, I tried PCBSD back a good while ago (couple of years now I think) and was impressed then at how easy it was to install for someone with little to no *nix experience. I didn't really keep it around long though, and their was no particular reason that comes to mind.

I am NOT trying to discount either of the two mentioned. It again, is like comparing an apple to an orange...

---

### Post by southernman on 2007-09-29
> **RAV TUX said:**
> It is notable because PC-BSD has decided to put this on the front page of their website:

[http://www.pcbsd.org/](http://www.pcbsd.org/)

I don't see it as negative, but something that Ubuntu can learn from. Constructive criticism is always good but only if the positive is extracted from it and strength is built.

To respond in a negative, or aloof way whether it be from a user or development is not very constructive overall. Like it or not these are our peers.Perhaps you read to much into the reply you quoted from me.

---

### Post by RAV TUX on 2007-09-29
> **southernman said:**
> Well, I don't think [Dru]("http://www.ittoolbox.com/profiles/dlavigne6") would appreciate being called a "he" for starters. :p

My point still remains, *BSD is BSD, *buntu is GNU/Linux. While they have some similarities, they aren't something anyone should try to do a side by side review and make sense of it. The few BSD'ers I know, makes their skin crawl to be grouped into the GNU/Linux category. I know it's painting with a broad brush, but the ones I know are definately more inclined to be in the elitist group. Perhaps even... rightfully so. Full of RTFM's! ;)

FWIW, I tried PCBSD back a good while ago (couple of years now I think) and was impressed then at how easy it was to install for someone with little to no *nix experience. I didn't really keep it around long though, and their was no particular reason that comes to mind.

I am NOT trying to discount either of the two mentioned. It again, is like comparing an apple to an orange...

Thanks for the heads up...edited the he's to she's ;)

I see your point I think she wanted to compare another popular distro that uses KDE, that is why Kubuntu was picked. There is perception that Ubuntu and it's derivatives are geared to new users, I think the point she is making is that if this is true Ubuntu is missing the mark.

Honest constructive criticism is all that I see it as.

---

### Post by p_quarles on 2007-09-29
That is really strange that Firefox was greyed out in the add/remove menu. I've installed the straight-up version of Kubuntu a couple times, and i've never seen that happen.

I will say, though, that Kubuntu is not as polished as the Gnome-based distro. And I say that as a KDE user. The inclusion of the wrong documentation is a good example of this, especially since KDE includes a very user-friendly and extensive manual by default. 

Advanced users can easily do a command-line installation and then add exactly what they want, but the average Vista-refugee doesn't think of that as a "fun" way to spend a Sunday. :D  

The bottom line is that KDE has some apps that simply work better than their Gnome counterparts (and vice versa). I think more attention to Kubuntu on the part of the development teams would be beneficial for overall adoption of Ubuntu.

---

### Post by RAV TUX on 2007-09-29
> **southernman said:**
> Perhaps you read to much into the reply you quoted from me.ahh, yes you are right, my apologies. I did infer too much there.

---

### Post by RAV TUX on 2007-09-29
> **p_quarles said:**
> That is really strange that Firefox was greyed out in the add/remove menu. I've installed the straight-up version of Kubuntu a couple times, and i've never seen that happen.

I will say, though, that Kubuntu is not as polished as the Gnome-based distro. And I say that as a KDE user. The inclusion of the wrong documentation is a good example of this, especially since KDE includes a very user-friendly and extensive manual by default. 

Advanced users can easily do a command-line installation and then add exactly what they want, but the average Vista-refugee doesn't think of that as a "fun" way to spend a Sunday. :D  

The bottom line is that KDE has some apps that simply work better than their Gnome counterparts (and vice versa). I think more attention to Kubuntu on the part of the development teams would be beneficial for overall adoption of Ubuntu.

This is one of the most important points here if Kubuntu and Xubuntu are official Ubuntu derivatives they should be the best KDE and XFCE distros in Linux. 

No short cuts should be taken, and no little issues overlooked. It comes down to the overall marketing success of Ubuntu as a whole.

This is not just fanboy speak from other distro users, this is time to wake up and smell the coffee.

Canonical needs to take this seriously.

Someone on the Isle of Man needs to pick up the phone and make this priority, starting now.

---

### Post by southernman on 2007-09-29
> **RAV TUX said:**
> 

Thanks for the heads up...edited the he's to she's ;)

No problem... it happens.
> **RAV TUX said:**
> 
I see your point I think she wanted to compare another popular distro that uses KDE, that is why Kubuntu was picked. There is perception that Ubuntu and it's derivatives are geared to new users, I think the point she is making is that if this is true Ubuntu is missing the mark.

Honest constructive criticism is all that I see it as.



I do think their is some fangirl stuff happening here. And perhaps the biggest thing to come from it, is the overall state of documentation for *buntu... it is generally outdated and not really targeted to those refugee's GNU/Linux would love to see come aboard. More of it now makes sense to me, after spending countless hours searching high and low through google and these forums, picking up tidbits along the way to finger things out.

Again your right, suggesting this should be priorities seems to be a little out of kilter!

---

### Post by RAV TUX on 2007-09-29
> **southernman said:**
> No problem... it happens.


I do think their is some fangirl stuff happening here. And perhaps the biggest thing to come from it, is the overall state of documentation for *buntu... it is generally outdated and not really targeted to those refugee's GNU/Linux would love to see come aboard. More of it now makes sense to me, after spending countless hours searching high and low through google and these forums, picking up tidbits along the way to finger things out.

Again your right, suggesting this should be priorities seems to be a little out of kilter!

being out of kilter may be my natural disposition. ;)

I was being a bit flamboyant there, mostly for effect. Part of my personality.

So it comes down to listen guys lets get the Kubuntu documentation down and pay more attention to detail.

Next time we get a fanboy or fangirl trying Ubuntu, Kubuntu, Xubuntu for the first time lets knock their socks off. ;)

---

### Post by southernman on 2007-09-29
> **RAV TUX said:**
> being out of kilter may be my natural disposition. ;)

I was being a bit flamboyant there, mostly for effect. Part of my personality.

So it comes down to listen guys lets get the Kubuntu documentation down and pay more attention to detail.

Next time we get a fanboy or fangirl trying Ubuntu, Kubuntu, Xubuntu for the first time lets knock their socks off. ;)o_0 are you of the female persuasion to? dunno why I get that vibe. It's so hard to tell with a nic floating about.

<--- has been out of kilter for a while now. 

<--- is reconnecting to the source of all living things.

<--- is using the "power of intention" to stay connected and effect the desired changes. It's worthy! [Authors Website]("http://www.drwaynedyer.com/"). If you can find the quoted title, it's quite informative IMHO.

When I referred to the fangirl part of my last reply, I meant Dru.

Was supposed to have started working with the USDF team, things seem to have been setup and a go, but sending an email to get login issues sorted out, fell on deaf ears. Figured if they needed more help, they knew how to get in touch... had my email, and other ways to contact me through here and the occasion of being on IRC.

---

### Post by RAV TUX on 2007-09-29
> **southernman said:**
> o_0 are you of the female persuasion to? dunno why I get that vibe. It's so hard to tell with a nic floating about.



It's my avatar throwing you off. :lolflag:

---

### Post by Frak on 2007-09-29
OK
1. The author's hardware isn't fully compatable, boohoo, it happens to everybody no matter what you use.
2. The author's comparison on what comes included is BS, especially when it comes to Kubuntu, because its been stated before that because it started late, it would take some time to get fully off the ground for mainstream. Also, you should never compare upon lines of "Software Installed". Its nifty, but its not the OS.
3. Sure, PC-BSD might be good now, but I've ran into many problems using it. Especially the latest release. Its just plain buggy.
Also, when you do run into problems, don't expect the community to help you, I've tried. They either critisize you on your choice, or call you a n00b for not being able to fix "that simple problem"

/* rant
I'd rather stay with my *Buntu, or stay with a real version of BSD, OS X. Even though its only very partialy BSD, it still gets the job done much faster than PC-BSD can think of doing.
*/ rant

---

### Post by RAV TUX on 2007-09-29
> **Frak said:**
> OK
1. The author's hardware isn't fully compatable, boohoo, it happens to everybody no matter what you use.
2. The author's comparison on what comes included is BS, especially when it comes to Kubuntu, because its been stated before that because it started late, it would take some time to get fully off the ground for mainstream. Also, you should never compare upon lines of "Software Installed". Its nifty, but its not the OS.
3. Sure, PC-BSD might be good now, but I've ran into many problems using it. Especially the latest release. Its just plain buggy.
Also, when you do run into problems, don't expect the community to help you, I've tried. They either critisize you on your choice, or call you a n00b for not being able to fix "that simple problem"

/* rant
I'd rather stay with my *Buntu, or stay with a real version of BSD, OS X. Even though its only very partialy BSD, it still gets the job done much faster than PC-BSD can think of doing.
*/ rant

I like your re-use of /*rant */rant tags...

---

### Post by Frak on 2007-09-29
> **RAV TUX said:**
> I like your re-use of /*rant */rant tags...
Thanks, the harder part was coming up with the rant :P

---

### Post by southernman on 2007-09-30
> **RAV TUX said:**
> It's my avatar throwing you off. :lolflag:

You are indeed looking a bit sheepish! baaaaaahaaaaa ;)

*looks around for Chuck*

---

### Post by stephenbrazier on 2008-01-07
> **p_quarles said:**
> That is really strange that Firefox was greyed out in the add/remove menu. I've installed the straight-up version of Kubuntu a couple times, and i've never seen that happen.



Strange, this always happened to me on all my Kubuntu installs, i thought it did it to everyone :) To fix it i just did an update from the termial and it magicaly un-greyed it.

Anyways, this PC-BSD sounds interesting.

:guitar:

---

### Post by fuscia on 2008-01-07
it took her an hour to install kubuntu? how'd that happen?

---

### Post by lespaul_rentals on 2008-01-07
What's that?  Do you hear that?  I think it's the bias alarm!  Run from the flames!

It's obvious this lady was a PC-BSD fan and was trying out a new distro -- a different kernel, at that -- and had no intention of getting to know it.  The only time Firefox has ever been greyed-out for me was when I hadn't updated my APT.  Oh, that was a hard fix, just run "sudo apt-get update" in command-line.

---

### Post by forrestcupp on 2008-01-07
> **lespaul_rentals said:**
>   The only time Firefox has ever been greyed-out for me was when I hadn't updated my APT.  Oh, that was a hard fix, just run "sudo apt-get update" in command-line.

I'm pretty sure you can even update APT from Adept without touching the command line.

---

### Post by sajro on 2008-01-07
Am I missing something or did that idiot attempt to install a program already installed? When I installed Kubuntu 7.04 it had Firefox by default.

---

### Post by -grubby on 2008-01-07
> **sajro said:**
> Am I missing something or did that idiot attempt to install a program already installed? When I installed Kubuntu 7.04 it had Firefox by default.

kubuntu doesn't have firefox by default

---

### Post by MountainX on 2008-01-16
I have tried to install Ubuntu on 4 different computers without success. Most recently I purchased a ThinkPad T61p because the laptop meets my needs and because I saw that people had successfully installed Ubuntu on it.

I'm a fairly experienced Windows user (C# developer and P/T sys admin), but even after spending a lot of time trying to get Ubuntu working I have not had any success (except in VMWare).

However, PC-BSD installed and the GUI came up (working at the correct resolution of 1920 x 1200) for me in about 15 minutes. I have more than 15 hours invested in failed Ubuntu installations in just the last 2 days.

Ubuntu is being marketed as an easy to use OS. To a newbie like me, Dru's article is right on the money. Maybe it would help to take her observations to heart.

---

### Post by SunnyRabbiera on 2008-01-16
yeh but you dont have flash in PC-BSD, a big factor of attracting doze users

---

### Post by MountainX on 2008-01-16
I would rather install Ubuntu, but I can't get it to work.
[http://ubuntuforums.org/showthread.php?p=4147414#post4147414](http://ubuntuforums.org/showthread.php?p=4147414#post4147414)

---

