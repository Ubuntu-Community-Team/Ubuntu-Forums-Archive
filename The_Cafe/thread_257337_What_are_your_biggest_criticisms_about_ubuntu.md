---
title: "What are your biggest criticisms about ubuntu?"
date: 2006-09-14
forum: The Cafe
---

### Post by ewaguespack on 2006-09-14
What are your biggest criticisms about ubuntu?

I have been using ubuntu for awhile now... probably over a year, and I was curios what areas people believe Ubuntu is weakest in.

Here is my list:

Lack of server side configuration documentation (I know we have it, but our docs pale in comparison to Red Hat)

Suspicion that we do things weird (I seem to get a lot of errors when I compile from source... I have a suspicion that Ubuntu puts libraries in unexpected places, furthermore I have read that installing the vanilla kernel on ubuntu breaks it... if this is true, I think that it is bad)

Too many install CDs (there are a lot... desktop, server, alternative, mac, spark, 64bit, etc) I realize that we can't fit all these on 1 cd, but it would be nice to reduce the number.

---

### Post by skymt on 2006-09-14
My list:

* Many packages don't come with menu entries
* The installer doesn't ask you if you want to enable (Uni|Multi)verse.
* Not enough users! :)

---

### Post by kinematic on 2006-09-14
can't get it to work with my nvidia fx5200 :(

---

### Post by coffeecat on 2006-09-14
> **kinematic said:**
> can't get it to work with my nvidia fx5200 :(

Ubuntu and the proprietary nvidia driver works fine with my FX5200. Which method did you use to install the driver?

---

### Post by wkulecz on 2006-09-14
My biggest critism is its based on Debian and my experience is while apt/dpkg looks good and seems to work great initially, my experince with Debian, Knoppix and now Ubuntu, is that its fragile -- any significant updating or installations from other that the installer default repositories quickly leads to a system so hosed its easlier to reformat and start over.  Its almost as bad as I remember Windows 3.1 being!

I had intended to set up half a dozen Ubuntu boxes, the first two went smoothly at first now both are hosed, the first for a totally unknown reason won't start gdm, the second, a kernel "security" update was pushed at me this morning, I bit, and now its useless to me since I can no longer get the Nvidia Proprietary driver to run!

I need the Nvidia driver because the X.org nv driver that ships with Ubuntu has a performance regression with Xvideo extensions.   Fedora Core 5 has has a fix for months!  With the Nvidia driver my xserver uses less CPU than the Fedora open source driver does, but both are fast enough with sufficient headroom for my application.  The Ubuntu open-source nv driver is utterly useless to me.

--wally.

---

### Post by wkulecz on 2006-09-14
> Ubuntu and the proprietary nvidia driver works fine with my FX5200. Which method did you use to install the driver?
Reply With 

You've identified problem #1  Like the immortals in Highlander, version-numbers and install-methods THERE CAN BE ONLY ONE!

--wally.

---

### Post by greatshape on 2006-09-14
The big thing missing in (K)ubuntu is an administration tool.
Something to configure the firewall, grub, servers, services, etc.
Suse has such a control center, mandriva has it,fedora too i guess.
Such an administrative tool would be a nice add-on.


Steve

---

### Post by aysiu on 2006-09-14
My criticisms of Ubuntu are the following, and the developers don't care about these (yes, I've filed bug reports):

**Automounting** with a click **Windows partitions** with the correct permissions. I can't tell you how many *unable to execute pmount* threads I've answered...

**Visual feedback from the terminal when entering your password**... or, if it really is a "security concern"--I actually think this is a BS reason--then *take away* visual feedback from the graphical authentication (Synaptic, BUM, Users and Groups, etc.), but *be consistent*. I can't tell you how many "my password doesn't work" threads I've answered.

Include **a *gksudo nautilus* or *kdesu konqueror* launcher button** in the menus. If you want to include a warning (the first time the button is clicked) about the dangers of using these buttons, that's fine, but without that button, we constantly get new users asking how to log in as root. When they're told to *sudo* whatever, they often take that to mean that everything has to be done through the terminal, and you either have to explain to them how to create the "browse as root" launcher or enable a graphical root login.

**Include *build-essential* by default.** Every other distro has this, and no other distros' users have complained about having it. Ubuntu users who need it will be grateful it's there, and Ubuntu users who don't need it won't even notice it's there. I don't buy the reasoning that "those who are compiling should know easily how to install it"--the issue is that they often don't know that they *need* to install it. Then we got a slew of these "make command not found" threads where people say "Oh, you have to install *build-essential*."

These are common questions from new users, and they really shouldn't be, especially since other distros don't have these problems--it's not a Linux thing; it's a Ubuntu thing.

---

### Post by fontenot_1031 on 2006-09-14
Definitely how hard it is to set up a dial-up modem, or even have the OS autodetect it.

---

### Post by toasterofirony on 2006-09-14
> **aysiu said:**
> Include a *gksudo nautilus* or *kdesu konqueror* launcher button in the menus. If you want to include a warning (the first time the button is clicked) about the dangers of using these buttons, that's fine, but without that button, we constantly get new users asking how to log in as root. When they're told to *sudo* whatever, they often take that to mean that everything has to be done through the terminal, and you either have to explain to them how to create the "browse as root" launcher or enable a graphical root login.

Oh yeah, thats a goody.

Makes you learn how to navigate by the terminal though ;)

---

### Post by aysiu on 2006-09-14
> **toasterofirony said:**
> Oh yeah, thats a goody.

Makes you learn how to navigate by the terminal though ;)
And I don't think forcing users to navigate by the terminal is a good thing. If people want to explore the terminal, good for them.

Those people you *think* you're forcing to use the terminal will really just figure out how to enable a graphical root login instead. Better to just have a "browse as root" button within the user account--isolates the root activity to one window.

---

### Post by BLTicklemonster on 2006-09-14
Upon further reflection, and deep thought (then I woke up), I have come to the conclusion that my biggest criticism of Ubuntu is that it's different. I actually have to think. And learn. And find out stuff. This goes against my nature. I want my money back.




No, really, I don't think "criticism" would be a good word for what I'd say. More along the lines of "biggest bother". I can say that it's the only version of linux I've felt the least bit comfortable with. The one thing that eats me up, is every time I get close to "this is how I want it to be", I go dick something up and have to start allllll over again. One of these days, though... and I think I'm pretty close now. And all that learning and thinking stuff is actually okay with me. Keeps the old 84 year old brain cell wiggling around. (okay, I'm 48, but my dyslexic daughter says I'm 84, so who am I to argue?)

=D> for Ubuntu.

---

### Post by Irony on 2006-09-14
aysiu's is right on all 4 points - I figured them out as time went by via the forums. For example;

[PHP]gksudo nautilus[/PHP]

Is very useful so I've added it as a button to my accessories menu - however it was a long time before I realised that I didn't have to do stuff in a long winded terminal 'can I remember the commands' way.

---

### Post by Irony on 2006-09-14
Also I would like Ubuntu to have clearer fonts; the default fonts are nice but they strain the eyes because the eyes constantly try to focus on them because they think they are blurred.

I've currently got msfonts installed and they are crystal clear and a relief to the eyes.

---

### Post by turbojugend_gr on 2006-09-14
I agree with asyu on his topic, but these are not my biggest botther, as I am not forced to asnwer, while his is in a way. The "thing" is that I never seem to be able to install sth I saw in a magazine, or in a site, an app that is not in the repos... I always end up searching for hours to make up the libs... I know that's linux issue in general though I don't see many guys contributing to automatix packages who could turn ubuntu and Linux in general to a much more friendlier issue... since ubuntu is the most influential distro for over a year now (imho) I believe we  could push more devs into it... A vast amount of how-tos would be needless this way.

PS: I love ubuntu cause of all distros I 've used (Suse for about a year, Fedora for about a month and Mepis for about a day or two) it is by far the quickest and the best-supported. Let alone the fact ubuntu's releases always are by far the best thing when  they come out... everysingle next one seems more polished.I also love ubuntu due to these forums...you will always get a hand on any issue.

---

### Post by aysiu on 2006-09-14
You're right, turbojugend_gr.

I don't install outside the repos, though...

---

### Post by mtron on 2006-09-14
just to reply to some issues raised in this thread:

server docs: ubuntu IS debain sid, so the debian doc is 1:1 valid for ubuntu. The debian doc team is one of the best around (personal opinion :cool: ) i didn't come across one problem not documetated somewhere. 

The terminal is a very important and highly useful tool, so it's not bad to do some stuff this way. some operations are much easier via terminal and conf files than via a gui.

---

### Post by ProjectGod on 2006-09-14
"What are your biggest criticisms about ubuntu?"

the OS? i think its great. considering it's free! can't complain can really. :biggrin:

---

### Post by coffeecat on 2006-09-14
> **wkulecz said:**
> You've identified problem #1  Like the immortals in Highlander, version-numbers and install-methods THERE CAN BE ONLY ONE!

--wally.

Well obviously not. There must be two, namely the one that works - which was the one I used - and the one that doesn't work which may have been the one that the poster I was replying to used. :)

---

### Post by kaens on 2006-09-14
I think Ubuntu is a really good distro for someone who is new to linux. It worked for me, anyhow.

The first distro that I tried to install was Debian stable (A little bit before woody came out), and I could never get X to work. At all. I know why it wasn't working now (incorrect refresh rates in the Xf86 configuration file) but then it was a brick wall - and it worked out of the box with Ubuntu.

However, now that I have been using linux, and understand the way that the kernel works better - and understand more about POSIX file heirarchy. . . I feel like Ubuntu is bloated for my tastes.

I really don't like the fact that there's no obvious way to modify what packages are installed from an install-cd. I don't need or want OO.org, Gnome (I'll take the libraries for using the apps though), or most of the apps installed. I wish I could choose those (maybe an advanced install option?)

I agree with aysiu about the build-essential package. The first time I went to install a program, it took me a little while to figure out why make wasn't working, and then I was pondering why in the world that would be left out of a distro.

I've also run into problems with compiling programs and libraries that I have installed not being detected. A lot of times, I have to install the -dev versions of the libraries. . . which is fine, I wish that there was a decent way to install the dev version of a library by default. Like an option in Synaptic. There probably is a argument passable to apt that does this.

Those are my biggest complaints about Ubuntu. I'll probably be moving over to another distro soon - I feel like I should have more control of my system from the get-go. 

However, I love the community behind Ubuntu. There is a strong lack of elitism, which is nice - people are generally friendly and helpful. I post around here and help out, or try to when my knowledge allows me too, and frankly, I will continue to even if I do move to another distro - a lot of the problems answered on this site aren't Ubuntu specific, some of them are.

---

### Post by TiredBird on 2006-09-14
I install things using 'apt-get' or 'synaptic' but then I can't figure out how to run the program. Most of the time what I installed doesn't end up in the menu and then I have to go looking for it and I have no clue where to start. 

It seems there is all sorts of documentation in 'usr/share/doc' but I can't figure out how to access it. Are there some programs that read all that stuff? Most of the time I end up spending hours surfing the web or the forums for instructions. 

Lately, I've discovered that changes I make in my file system don't get reflected in Nautilus and sometimes I find that my changes didn't take at all. However, I don't see anybody reporting this as a bug so I assume that I'm doing something wrong - but I have no idea what it is.

It's a good thing I have a lot of time to deal with this. ](*,)

---

### Post by bigaltx on 2006-09-14
The biggest problem I've had with Ubuntu is that I've had two kernel updates break my system. Finally upgraded to a 686 kernel and just ignore kernel updates. Overall, I think Ubuntu works fairly well. It's the first Linux distro I've used where everything worked right off the bat, without alot of hassle. I've had my fun trying to get stuff working in Linux, and don't have the time or patience anymore.

---

### Post by Anduu on 2006-09-15
I just have one gripe with ubuntu...

The letters are wearing off on my "S" "U" "D" and "O" keys :p

Seriously though I can't think of anything in particular that bugs me.*Everything* "just works"

---

### Post by BLTicklemonster on 2006-09-15
> **Anduu said:**
> I just have one gripe with ubuntu...

The letters are wearing off on my "S" "U" "D" and "O" keys :p


[IMG]http://climbatizeut.users.btopenworld.com/f-smilies/f-roofle.gif[/IMG]

---

### Post by urbandryad on 2006-09-15
My biggest gripe about Ubuntu....SHIPIT TAKES SO LONG!

I'm stuck on Windowz Y2Krash because I don't have a copy of Ubuntu 6.0 for this computer. Because I don't have a burner. And its been a month since I requested the CD. And I don't have a burner. Where is my freaking CD!!!? >:( I can't use the Mac version of it that I already got because this new laptop is a PC, and the 6.0 version isn't working on my Mac at all. It won't run. :( So I'm either stuck in Breezy on a 3 Gig HD Clamshell iBook with very little power, or Windowz in my PC Laptop. WAUGH!

*scratches her head*

---

### Post by wieman01 on 2006-09-15
I have to agree with user "wkulecz"... When you browse through the forum problems after updates are conspicuous. That's also my greatest criticism: Ubuntu seems to be _incapable_ of shipping well-tested updates. Even security updates turn out to be nasty from time to time (I therefore fixed my kernel version).

I saw a few statistics recently with Ubuntu being the most reliable & most responsive distribution when it comes to releasing security updates. But in my opinion they should spend a bit more time on & put more effort into testing their patches before releasing them.

That would waste less of our time & make Ubuntu even more worthwhile. They are simply too fast... And quality suffers.

---

### Post by 3rdalbum on 2006-09-15
The biggest problem with Ubuntu is that it's too addictive.

The second biggest problem is that too many programs that aren't available in Universe are only available in source form. I've compiled from source on a number of occasions, and some of these compiles haven't been easy, but I've also failed on a number of occasions. I'm glad that more developers are providing .debs and even repositories, but there should be more.

I've just realised that this isn't a criticism about Ubuntu.

Another critisism I have is that Ubuntu, out-of-the-box, seems to pretend that you don't need it to cooperate with other operating systems. New users need a HOWTO or Automatix to enable the restricted formats, there are no tools for setting up WINE, and most of the time your Windows-formatted drives don't automatically mount.

I'm sure there's a legal way to have a simple GUI program that enables restricted formats, and I *know* it's possible to write a program that mounts NTFS partitions (I've written one, and I'm not the first person to do that!).

---

### Post by mzilhao on 2006-09-15
well, i think that midi playback should work out of the box. it shouldn't be that hard.
there's also that cdrecord madness with SATA drives, but i guess that's a cdrecord thing and not a ubuntu thing. still i'd love to have my burner working properly...

---

### Post by colonelk on 2006-09-15
As a windows admin I'm learning just how powerful and versatile Ubuntu is.  In fact I'm trying hard NOT to use windows just to see if I can do my job with Ubuntu in an Active directory network.

My criticisms are:

* Wireless Networking isn't flawless (probably not just an ubuntu issue)

* There should be some graphical tool to help you install and configure everything necessary to use Ubuntu in an Active Directory domain.

* Printing to Windows shared printers seems flakey in Ubuntu.  Sometimes it works sometimes it doesn't and sometimes it spews page upon page of rubbish!

* I would like the Ubuntu device manager to be more like the windows device manager.  I want to see what hardware I have and have a way of configuring it through that tool (or at least be able to load the necessary GUI's to manage my hardware).

* I would like a little more control over the install process.  I've no idea how to start an "expert" install, or whether I want to.  I just want to be able to set networking properties during setup, resolutions for the display etc The important stuff!

* I want foolproof multi monitor support for nVidia and ATI chipsets manageable during install and subsequently with a GUI out of the box.


There are many things I do like about Ubuntu, but I'd like to see the IMO shortcomings addressed :)

---

### Post by Onyros on 2006-09-15
> **urbandryad said:**
> My biggest gripe about Ubuntu....SHIPIT TAKES SO LONG!

I'm stuck on Windowz Y2Krash because I don't have a copy of Ubuntu 6.0 for this computer. Because I don't have a burner. And its been a month since I requested the CD. And I don't have a burner. Where is my freaking CD!!!? >:( I can't use the Mac version of it that I already got because this new laptop is a PC, and the 6.0 version isn't working on my Mac at all. It won't run. :( So I'm either stuck in Breezy on a 3 Gig HD Clamshell iBook with very little power, or Windowz in my PC Laptop. WAUGH!

*scratches her head*Where are you from? Maybe I can set you up with a copy of 6.06.1 (yes, the update to 6.06), and all your woes will be washed away.

I also have a Mac version, but it's Breezy, not Dapper.

---

### Post by Kateikyoushi on 2006-09-15
My girlfriend complained about the look of it.
While the taskbar can be transparent the file browser has such big buttons like IE4, compared to Vista this is way too oldskool.

---

### Post by Bezmotivnik on 2006-09-15
> **aysiu said:**
> And I don't think forcing users to navigate by the terminal is a good thing. 
Yes, I was already using computers in 1982 and I don't relish doing it again.

I'm not a nostalia buff; I believe in progress, not doing everything in the hardest, most arcane, learning-intensive and error-prone possible manner.  I simply don't respect that retrograde outlook.
> If people want to explore the terminal, good for them.

Of course, and there are some things that are more efficiently done in terminal.  

A major *bad* reason to use terminal is that the GUI doesn't work properly or intuitively.  Unfortunately, it's still a major one in Linux distributions.  

The only sane objective for a general-user OS is to increase intuitiveness while reducing learning curves and possibilities for user error.  That means more comprehensive and reliable GUI.

---

### Post by aysiu on 2006-09-15
Well, ideally, the objective would be to make fully functional and efficient command-line programs with easy-to-understand *man* pages **and** accompanying graphical frontends that are intuitive and powerful--the best of both worlds.

---

### Post by Rhapsody on 2006-09-16
> **aysiu said:**
> **Automounting** with a click **Windows partitions** with the correct permissions. I can't tell you how many *unable to execute pmount* threads I've answered...
I used to have some problems with this myself. It's not a problem anymore (since Kubuntu is now the sole OS on this PC and has full access to all partitions) but it would've been nice to see it offer to help me mount those partitions.

> **aysiu said:**
> **Visual feedback from the terminal when entering your password**... or, if it really is a "security concern"--I actually think this is a BS reason--then *take away* visual feedback from the graphical authentication (Synaptic, BUM, Users and Groups, etc.), but *be consistent*. I can't tell you how many "my password doesn't work" threads I've answered.
I agree. My password is nine characters long, and I'll tell that to anyone. How many possible combinations of characters could go in a nine letter password? It's got to be somewhere in the quadrillions or quintillions. If I were a cracker, I'd say "Screw that" and try to find a nice, insecure Windows system to attack instead.

> **aysiu said:**
> Include **a *gksudo nautilus* or *kdesu konqueror* launcher button** in the menus. If you want to include a warning (the first time the button is clicked) about the dangers of using these buttons, that's fine, but without that button, we constantly get new users asking how to log in as root. When they're told to *sudo* whatever, they often take that to mean that everything has to be done through the terminal, and you either have to explain to them how to create the "browse as root" launcher or enable a graphical root login.
I'd probably not use this. I feel very uncomfortable inputting sudo commands into a terminal, and that's a good thing. Using the wrong command with sudo in front of it could totally hose my system, so it's best that I give such tasks my complete attention. Still, there are plenty of users who'd like it.

> **aysiu said:**
> **Include *build-essential* by default.** Every other distro has this, and no other distros' users have complained about having it. Ubuntu users who need it will be grateful it's there, and Ubuntu users who don't need it won't even notice it's there. I don't buy the reasoning that "those who are compiling should know easily how to install it"--the issue is that they often don't know that they *need* to install it. Then we got a slew of these "make command not found" threads where people say "Oh, you have to install *build-essential*."
**Yes.** I was trying to compile SDLMAME, and I was totally flumoxed about why Konsole wouldn't accept 'make' as a valid command. I was eventually told about the need to install *build-essential* and ended up wondering why the 48K download wasn't just installed with the OS. It's a tiny thing, and absolutely essential if you plan to compile anything (which you probably will, since a lot of neat Linux stuff comes as source-only).

---

### Post by H.E. Pennypacker on 2006-09-16
> **Irony said:**
> aysiu's is right on all 4 points - I figured them out as time went by via the forums. For example;

[PHP]gksudo nautilus[/PHP]

Is very useful so I've added it as a button to my accessories menu - however it was a long time before I realised that I didn't have to do stuff in a long winded terminal 'can I remember the commands' way.

I didn't even realize this!  Thanks.  I added "gksudo nautilus" to Accessories too.  It's not that big of a deal for me, because I don't need to browse as root that often, but when I do, its not exactly great that I have to start up the terminal or F2 my way to gksudo nautilus (pressing F2, and typing gksudo nautilus).

If you think about it, F2 can cut down on a lot of terminal use.  If you still need to use the terminal, with XGL/AIGLX, CTRL-F (which is usually used for finding stuff) brings up the terminal.

---

### Post by Irony on 2006-09-16
Another thing I would like is for there to be a separate repo where the latest updates for programs like Blender, Inkscape, Yafray, OpenOffice, etc can be installed - usually I have to search for these .debs from other people as my compiling skills seem to be largely unsuccessful and time consuming.

---

### Post by OffHand on 2006-09-16
A failing QA team. They will have to change their strategy.

---

### Post by kinematic on 2006-09-18
> **coffeecat said:**
> Ubuntu and the proprietary nvidia driver works fine with my FX5200. Which method did you use to install the driver?

i tried every method.... installed the driver from the nvidia site,from the repo and with envy.
it's just some freaky compatability issue with my asus k8s-mx MoBo and so far i can only get it to work on fedora core.
i'm probably just gonna buy another card because i've heard that the fx5200 can be problematic on some boards.

---

### Post by .t. on 2006-09-18
Threads Like This One!


EDIT1:And Why The Hell Does The Forum Mean I Cannot Post All In Full Capitals!



Just try it!

EDIT2: Hey Look It Lets Me When I Edit...

EDIT3: It lets me do it when I edit too. -zenwhen

---

### Post by zenwhen on 2006-09-18
My biggest gripes?

Wireless configuration could be much easier across a much broader range of chipsets. This is not the developers faults really, and is more a fault of hardware vendors not properly supporting the Linux platform with open specs or even proper binary drivers. I am not opposed to very functional binary blob drivers.

I would like to see more functional ATi drivers (ones that don't kill suspend) as well, but this is also not the fault of the developers. 

I have yet to find a major fault with Ubuntu that is Ubuntu's fault. 

I'd like to see more games released, more hardware supported, and more proprietary software offered to Ubuntu users even if the developers refuse to make use of fair and morally valid licenses such as the GNU GPL.

Ubuntu is growing with all odds against it. It would be amazing to see what could happen if the odds fell the other way, and all of the terrible practices of hardware and software vendors vanished.

---

### Post by John.Michael.Kane on 2006-09-18
I have no criticisms or gripes in reguards to ubuntu or any distro.

Should i have a problem i work through it. I don't let the problem work me.

**Note:** Most issues the enduser can adapt, and overcome.....

---

### Post by emarkay on 2006-09-18
> **colonelk said:**
> 

My criticisms are:

* Printing to Windows shared printers seems flakey in Ubuntu.  Sometimes it works sometimes it doesn't and sometimes it spews page upon page of rubbish!

* I would like the Ubuntu device manager to be more like the windows device manager.  I want to see what hardware I have and have a way of configuring it through that tool (or at least be able to load the necessary GUI's to manage my hardware).

* I would like a little more control over the install process.  I've no idea how to start an "expert" install, or whether I want to.  I just want to be able to set networking properties during setup, resolutions for the display etc The important stuff!

Well, this is my second post here, and I am halfway finished the Ubuntu .iso burn, and 3 of these critical comments bear repeating, IMHO.  

An OS needs to interface and configure the peripherals and hardware in an intuitive, and confident manner, and leave nothing hidden, obscured, or "geeked to the max"!  (I am dreading trying to get my HP psc1350 "all in one" configured as it took a few days of digging to get it to function in a native Windows environment!  Let's hope there's someone here or whom I can Google that has "been there, done that"!)

I have grown used to comprehensive "Install Wizards" and hope that concept is adapted for the Linux realm eventually.

It would be interesting to see some of these specific critical comments addressed by those much more familiar with Ubuntu than I. :)

MRK

---

### Post by Adamant1988 on 2006-09-18
I would say that my biggest gripes are the repositories... I just don't like the idea of them being "frozen" I want to know that when I start up my computer there may be more software in the repos than when I shut it off last night. 

There is so much excellent software out there, but a lot of it isn't in the repos... For instance: Flock.  Flock is an EXCELLENT browser... and the only distro I've seen that has it in the repos is Linspire/Freespire. 

Stuff like that makes a difference. ( I would also like to be able to buy legal DVD and codecs and such. )

---

### Post by pelle.k on 2006-09-18
My list would probably be;

*All damn free form text configuration files (give us a decent xml editor instead and use _some_ form of standard), but this goes for linux in general also.
*I would like more installation interaction, error events, and startup events to be more accessible, and not be lurking in some far off log file somewhere... without _any_ warnings.
*Give us something like pacman and ABS (and the aur) in arch linux!!! The best thing to hit the streets in ages really.

---

### Post by DigitalDuality on 2006-09-19
d

---

### Post by Cyraxzz on 2006-09-19
I've only encounterd one problem with ubuntu: 

* More settings for the wi-fi configuration, or simply just a better WLAN config.

---

### Post by Bezmotivnik on 2006-09-19
> **colonelk said:**
> 
My criticisms are:

* Wireless Networking isn't flawless (probably not just an ubuntu issue)
"Flawless" it isn't, indeed.  "Gawdawful" is more accurate, and yes, incredible but true, this is a problem that's even *worse* in other distributions. ](*,) 

"But never mind!  Look at the geeky new eye-candy!" :rolleyes:

---

### Post by pneaveill on 2006-09-19
> **emarkay said:**
> Well, this is my second post here, and I am halfway finished the Ubuntu .iso burn, and 3 of these critical comments bear repeating, IMHO.  

An OS needs to interface and configure the peripherals and hardware in an intuitive, and confident manner, and leave nothing hidden, obscured, or "geeked to the max"!  (I am dreading trying to get my HP psc1350 "all in one" configured as it took a few days of digging to get it to function in a native Windows environment!  Let's hope there's someone here or whom I can Google that has "been there, done that"!)

I have grown used to comprehensive "Install Wizards" and hope that concept is adapted for the Linux realm eventually.

It would be interesting to see some of these specific critical comments addressed by those much more familiar with Ubuntu than I. :)

MRK

I have two major beefs (1) is the apparent limitations of [FONT=Arial Black][COLOR=DarkSlateBlue]OCR[/COLOR][/FONT] with the HP  psc 1350; and (2) finding a way to get something to automatically check my yahoo and hotmail accounts. If anyone  has a workaround or  tweak,  hack or whatever, I would be most happy.

---

### Post by KhaaL on 2006-09-19
I'm pretty new to linux in general, but im afraid that its going to turn into a distro that it will become a OS that will babysit its user and hide options from them and limit their choices to not accidently confuse/scare them away.

---

### Post by croak77 on 2006-09-19
> **pelle.k said:**
> My list would probably be;

*Give us something like pacman and ABS (and the aur) in arch linux!!! The best thing to hit the streets in ages really.

Why pacman over aptitude? I've used Arch for quite awhile and would vote against a AUR for Ubuntu. Packages in AUR have been pretty hit or miss. Some are well packaged and maintained while others aren't. Not to mention the added security risk it would pose to Ubuntu. ABS is nice but so is deb-src.

---

### Post by bruce89 on 2006-09-19
Possibly not giving back changes upstream. (localisation especially)

---

### Post by pelle.k on 2006-09-19
Well, maybe not pacman. I agree apt-get is great (allthough i prefer aptitude). I would a better way to interface debfoster though.

OK, the PKGBUILDS can be a little flaky at times, but that's what the voting system is for. Also nothing gets into community without a "Trusted User".
The build system is SO clean. checkinstall is at best a hack (nor does it download build dependencies for you).
You don't have to use it. It requires you to configure ABS and download packagebuilds yourself. 

I'm not saying it should be installed, and ready to be used as a gui frontend, by unsuspecting n00bs, but it would for sure make it easier to package some exotic software, and get nice debs to install instead of a hit'n'miss .configure make make install solution that so many of us have to endure because of totally crazy compiler output and whatnot.

I see it as a team effort to figure out what is needed to compile a certain source-package, gathered in a text file. ready for output to a binary package for your favourite distro. wouldn't that be cool?

---

