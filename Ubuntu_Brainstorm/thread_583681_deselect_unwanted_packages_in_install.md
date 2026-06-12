---
title: "deselect unwanted packages in install?"
date: 2007-10-20
forum: Ubuntu Brainstorm
---

### Post by leetrefz on 2007-10-20
Maybe I'm wierd, but I'd like to have a list of check boxes as an install stage so that I can avoid installing packages I'll never use. Maybe Gimp, accessibility, stuff for types of hardware I don't have, etc.

I'm thinking for ultra resource thrifty xubuntu users, maybe installing to little flash drives or just on ancient equipment.

---

### Post by gruvsyco on 2007-10-20
I'd like to one-up this... I think a lot of stuff should be moved to optional installs.  I honestly kind of like that MS Windows ships relatively stripped.  It's great that all this software is available but I think we could do with a lot less installed by default.  On the same note, in the Add/Remove packages they could have something like "Ubuntu Recommends" or something like that.

Hell, they could even put them into bundles... Ubuntu Graphics, Ubuntu Games, Ubuntu Office...

Out of the box, I really think we need less though...  Oddly, I would leave the Eye Candy in, Web Browser, Email, Image Viewer, Media Player, IM...  The stuff that most people ultimately use.  Stuff like image editing and office apps are all great but, not all users really have a need for them.

And on the "this would be really cool" front.  If an app is installed that could replace the functionality of something else... say, installing Banshee on System where Rhythmbox is installed, it could prompt if you'd like to set it as the default app for that type.  I recently installed Hotwire and I would love it if anywhere a terminal get's called, it would use that instead.

---

### Post by 23meg on 2007-10-20
[QUOTE=gruvsyco]I honestly kind of like that MS Windows ships relatively stripped. [/QUOTE]

Windows ships stripped because it's not in the interests of its vendor to ship you loads of extra software by default, not due to a design decision to ship a minimal set of software. But Windows also doesn't ask you whether you want a particular piece of software or not at install time, and that's definitely a conscious design decision: many people don't need some of the extras that come with it, but the point of not asking people whether they want them or not at install time is that the installation process should be kept as simple and to the point as possible, and that they probably won't be able to make an informed choice without ever trying those software. Installing a new OS is a scary enough process for non-technical people, and you don't need to worry about technical people at install time, because they can add and remove stuff themselves afterwards.

Ubuntu is all about sane defaults for the majority of users, and if you don't like the Ubuntu defaults, they're easy to change *after installation*. Similarly, in Windows, you can remove unwanted OS components somewhere in the Control Panel once you've installed the OS.

[Here]("http://mpt.net.nz/archive/2007/05/16/desktop") is a relevant blog post by Matthew Paul Thomas that I like, on offering or not offering software choices at install time.

---

### Post by gruvsyco on 2007-10-20
> **23meg said:**
> [Here]("http://mpt.net.nz/archive/2007/05/16/desktop") is a relevant blog post by Matthew Paul Thomas that I like, on offering or not offering software choices at install time.

I kinda like what he has to say and agree to an extent... My comment wasn't actually suggesting prompting at install time like the OP... I think we should get a default install of "more basic" stuff and then have suggested bundles available via add/remove.  For brand new users they could even have a full screen intro play like XP does when the OS is first run after install.  This could then explain how to add recommended apps and what's available.

---

### Post by 23meg on 2007-10-20
[QUOTE=gruvsyco]My comment wasn't actually suggesting prompting at install time like the OP...[/QUOTE]

I know; I just quoted that bit from your post to comment on it; the rest of it wasn't really directed at you, or anyone else in particular.

---

### Post by leetrefz on 2007-10-21
Maybe we could have a bare-bones xubuntu version? I like (x)ubuntu for the community, debian base, sudo etc, but I need it as light as possible. No gimp, no games etc

---

### Post by smartboyathome on 2007-10-21
> **leetrefz said:**
> Maybe we could have a bare-bones xubuntu version? I like (x)ubuntu for the community, debian base, sudo etc, but I need it as light as possible. No gimp, no games etc

Use the Alternate Desktop Ubuntu installer to install a command line environment, and then install xfce on that with whatever apps you want. I find it lighter this way.

---

### Post by leetrefz on 2007-10-21
hmm, that sounds harder to do. I'm an average person/computer user. I have too many things to do in my life & profits to pursue to have time to learn much command line. Guess I'm still in the minority with linux. Well if no one else wants an easily installed x-tra lite system, as I thought xubuntu was supposed to be, forget I ever posted.

---

### Post by glotz on 2007-10-22
To me this is a very good idea. Ditto services.

---

### Post by Xbehave on 2007-10-22
it should be in an advanced mode, most users are going to be better off installing defaults, but a list of programs to install in the installer ( i rember something like this in win98 days) would help advanced users avoid gimp and un needed programs.

This would also be useful for people that don't like the defaults, e.g i don't want kopete, konqueror so desect them then because im an advanced user (otherwise i wouldnt of opened advanced right) i know how to install pidgin and Firefox

i know this can be done from a chroot or command line install but there are users who know what they want but dont like/know CLI (this is very common for ex-windows users(a.k.a people who got vista:P))

---

### Post by BradwJensen on 2007-11-07
I don't see why OS's (especially Ubuntu) still don't have this amazing, yet simple feature..

Please, make it so one can CHOOSE which programs they want installed along with Ubuntu. (whether it installs when Ubuntu installs or on the First bootup.)  This way people will not have to remove the default apps and install their own after the install, it would speed up the whole installing of Ubuntu and Setting everything up.

[B]Heres The Idea:
[/B]- Make a scrollable page during the Ubuntu install with choices of apps to be installed or not at all with check boxes.. 
- Have a default set checked for people who are new/unsure what apps they want installed when Ubuntu installs.

Simple as that..
Heres somewhat what it could look like.
-------------------------------------
Mockup Below (the bullets would be check boxes.)
---------------------------

                                                            *Please select any/all program(s) you want installed with Ubuntu.*
 [SIZE=1](if you're new/not sure, just click &#8220;next&#8221; to have the default apps installed.)[/SIZE]
 

 _**INTERNET:**_
 

 **Web Browser(s)**[LIST]
[*]Epiphany
[*]Firefox
[*]Opera
[*]None[/LIST]**Instant Messenger(s)**[LIST]
[*]Pidgin
[*]None[/LIST]**Email App(s)**[LIST]
[*]Evolution
[*]Thunderbird
[*]None[/LIST]**BitTorrent App(s)**[LIST]
[*]Azureus
[*]BitTorrent
[*]Deluge
[*]Frostwire
[*]Limewire
[*]None[/LIST]
 _**MEDIA:**_
 

 **Music Player(s)**[LIST]
[*]Amarok
[*]Banshee
[*]Rhythmbox
[*]None[/LIST]**Video Player(s)**[LIST]
[*]Totem
[*]FLV
[*]None[/LIST]**Office App(s)**[LIST]
[*]Abiword
[*]Open Office
[*]None[/LIST]**Graphic App(s)**[LIST]
[*]Gimp
[*]None[/LIST]**Game(s)**[LIST]
[*]Solitaire
[*]None[/LIST]**Extras**[LIST]
[*]Compiz-Fusion Settings Manager
[*]Flash Plugin
[*]Java (jre) 6
[*]None[/LIST]----------------------------------------
[SIZE=5]**Who likes it?**

[/SIZE]

---

### Post by pay on 2007-11-07
This is sort of like what Fedora does. The only problem is to have room for all those apps we would have to use a DVD iso. Maybe have the version we have now and a dvd version with the ability to choose which software we have (if the current dvd version lacks that feature).

---

### Post by 23meg on 2007-11-07
[QUOTE=BradwJensen]I don't see why OS's (especially Ubuntu) still don't have this amazing, yet simple feature..[/QUOTE]

Many OSes have it. Ubuntu doesn't, by design.

Ubuntu is all about sane defaults that work for most of its audience, simplicity and easy customizability for the use cases where the defaults don't work. There's a lot of merit in keeping the installer as simple as possible; package selection isn't something that should happen at install time. With other distros, it can be a good idea; with Ubuntu, which is a one CD distro that ships a limited amount of hand picked software, and has a target audience that includes a large amount of people with little experience of the GNU/Linux platform, it's not.

---

### Post by 23meg on 2007-11-07
I've merged the two threads where the same idea is discussed.

---

### Post by BradwJensen on 2007-11-07
_[U]Dead post._[/U]

---

### Post by BradwJensen on 2007-11-07
> **23meg said:**
> I've merged the two threads where the same idea is discussed.

Ah i noticed that.. At first i was confused on why mine was coming here.. lol

Thanks for fixing that.  You think we have a good chance at getting something like my mockup put in place anytime soon?
It seems even simpler looking to use than the OpenSUSE one is, with the layout as typical as it is and all..
Plus it has a default set picked for people who are new or unsure.  Piece of cake for anyone who could ever install a OS from CD anyways, so i really doubt its that big of a deal for such a nice simple feature.
------------------
I think instead of all the apps being on a DVD - we could just have Ubuntu possibly download them during the install and install them, or have Ubuntu make a list of what would be installed on the first boot up of Ubuntu.

It really is a pain when OS's depend on a specific program.. Like Windows and IE are.
In Ubuntu if one tried to uninstall specific programs like bittorrent it auto wants to uninstall Ubuntu-Desktop.. thats just not right and definitely needs fixed.

---

### Post by glotz on 2007-11-07
The ubuntu-desktop is a meta package. Go ahead, uninstall anything you like. I remember I was spooked and dumbfounded by it when I first saw it too... ;)

---

### Post by BradwJensen on 2007-11-07
> **glotz said:**
> The ubuntu-desktop is a meta package. Go ahead, uninstall anything you like. I remember I was spooked and dumbfounded by it when I first saw it too... ;)


Thanks! :-) paha.

---

### Post by 23meg on 2007-11-07
I maintain that having anything in the way of software selection at install time isn't a good idea for Ubuntu, and that keeping the installer as simple as possible is. For most new users, terms like "Amarok", "Banshee" and "Abiword" are just words; they don't ring a bell. The user doesn't have an idea which is more suited to their purposes, so bugging them with that choice at install time, which is a scary enough phase, is unnecessary, especially when they can uninstall and install stuff easily after the OS installation.

---

### Post by BradwJensen on 2007-11-07
> **23meg said:**
> I maintain that having anything in the way of software selection at install time isn't a good idea for Ubuntu, and that keeping the installer as simple as possible is. For most new users, terms like "Amarok", "Banshee" and "Abiword" are just words; they don't ring a bell. The user doesn't have an idea which is more suited to their purposes, so bugging them with that choice at install time, which is a scary enough phase, is unnecessary, especially when they can uninstall and install stuff easily after the OS installation.


Alright, but you would think that if someone is Smart enough to download Ubuntu, burn it to a disc, and is not too scared to install it from that disc  and partition a hard drive that they are smart enough to read the part that says "if you are unsure, just click next to have the default apps installed". 

I have a big feeling that there are more smarter than that people running Ubuntu right now than the other.  I also have the feeling that if someone is too dumb to understand something that simple, they would never be in the process of installing an operating system by themselves anyways. 

Most people i've ever talked to don't even know what an Operating System is.  They have no clue that Windows is a system that your computer apps run on.  I doubt those kinds of people would ever install an OS themselves and that they would quite easilier understand the App choosing / "default click next" choosing **than** **partitioning** a hard drive / backing up data and installing an Operating System.

---

### Post by BradwJensen on 2007-11-07
Also, maybe there can just be a button on the installation somewhere called "Advanced Options" if this is such a big problem.  The Advanced Options button could go to this App Choosing feature for all those that have used Ubuntu before and know what they want. It'd be like the advanced installing of Firefox on Windows, sort of.

But i still think that anyone who can install an Operating System can understand a simple either "check what you know you want & uncheck what you know you don't want", or "click next to have defaults installed if you're unsure/new (you can always change later)".

---

### Post by glotz on 2007-11-07
This would also make the installation process faster when you could deselect stuff you don't need. Also, you wouldn't need as much space to install. The default process should be simple but there should be choice for the advanced users too.

---

### Post by 23meg on 2007-11-07
> **BradwJensen]Alright, but you would think that if someone is Smart enough to download Ubuntu, burn it to a disc, and is not too scared to install it from that disc and partition a hard drive that they are smart enough to read the part that says "if you are unsure, just click next to have the default apps installed".

I have a big feeling that there are more smarter than that people running Ubuntu right now than the other. I also have the feeling that if someone is too dumb to understand something that simple, they would never be in the process of installing an operating system by themselves anyways.

[/QUOTE]

It's not about being smart or stupid said:**
> 
[*]the fact that keeping the installer simple and generic (without plaform-specific information that's alien to most people at this point) has allowed non-technical people to "survive" the installation 

[*]and the fact that people who can comfortably handle one general computing related task (OS installation) can very well fail in another (getting to know and install applications, enable devices, etc. in an alien environment).
[/list]

[QUOTE=BradwJensen]Most people i've ever talked to don't even know what an Operating System is. They have no clue that Windows is a system that your computer apps run on. I doubt those kinds of people would ever install an OS themselves


Sure, they *wouldn't*, rather than that they *couldn't*; it wouldn't even appear as an option to them.

> **BradwJensen]and that they would quite easilier understand the App choosing / "default click next" choosing than partitioning a hard drive / backing up data and installing an Operating System.
[/QUOTE]

Of course they would said:**
> Also, maybe there can just be a button on the installation somewhere called "Advanced Options" if this is such a big problem. The Advanced Options button could go to this App Choosing feature for all those that have used Ubuntu before and know what they want. It'd be like the advanced installing of Firefox on Windows, sort of.

There are a few good reasons why modal interfaces are avoided in Ubuntu and GNOME in general, which I had [mentioned]("http://ubuntuforums.org/showpost.php?p=3581845&postcount=14") in another context some time ago.

[QUOTE=BradwJensen]But i still think that anyone who can install an Operating System can understand a simple either "check what you know you want & uncheck what you know you don't want"[/QUOTE]

Again, the more important problem is with assuming that the user actually is informed on what they want and what they don't, and restricting this to an install-time question.

And one more thing: the software installed doesn't come in packages on the live CD; the installer just extracts an image of the whole thing. Thus you'd need to first copy the whole thing, and then uninstall unwanted packages.

---

### Post by BradwJensen on 2007-11-07
> **23meg said:**
> 
And one more thing: the software installed doesn't come in packages on the live CD; the installer just extracts an image of the whole thing. Thus you'd need to first copy the whole thing, and then uninstall unwanted packages.

So here you are saying that the Whole Ubuntu CD/DVD is extracted as one when installed, and has the default apps kind of what we could say "hard coded" into the OS to be installed with Ubuntu?  So, it would need to install those apps then uninstall them to do what apps we wanted anyways?

If thats not right, please clarify a bit more.. Thanks.

---

### Post by 23meg on 2007-11-08
That's right; that's the case with the desktop CD. In the alternate CD, there are actual packages.

---

### Post by DizzyTech on 2007-12-02
Right now, the LiveCD Installer copies the exact LiveCD image to your computer.  Therefore, the Ubuntu LiveCD must contain all of the files in the default system.  As a result, we can't put too many extra things onto the LiveCD... we can't have special hardware support, or wizards, and speeder-uppers.

I suggest that a new wizard be created that starts when Ubuntu loads for the first time on its new install.  This wizard could have basic options and would install (and configure) certain packages, like OpenOffice.  This could allow us to remove certain packages from the entire LiveCD and free up space.

Another feature of the wizard could be freedom.  By this, I mean you could choose to install OpenOffice or GNOME Office (Gnumeric, Abiword, etc...), or not install GIMP or something.

I know that having these sorts of items in the install would complicate things and therefore be bad.  However, putting this sort of wizard in place (possibly integrated into a Welcome to Ubuntu walkthrough) could be better for usability.  Other features of this could be automatic setting-up of drivers, and explanations.

The main point?  Cleaning up the LiveCD, and giving users more choice.  Thank you for listening.

---

### Post by smartboyathome on 2007-12-02
I don't like this idea. What would be the point of a LiveCD if it doesn't contain the programs that run (if this is put in place, wouldn't the program be removed from the 'Live' part of the cd as well?).

---

### Post by DizzyTech on 2007-12-02
I completely understand your point. However, I'm not thinking Firefox would be removed.  I'm thinking more along the lines of The GIMP, F-Spot, or OpenOffice.  Things like F-Spot or Evolution require configuration to use regardless; what would be the point?

---

### Post by smartboyathome on 2007-12-02
To show the user what Ubuntu can do without them installing it on the system, that is the use. I think that if we uninstall programs, and then have the user install them later, they might think "why not just give it to me instead of asking first?".

---

### Post by 23meg on 2007-12-03
I've merged another thread on (almost) the same subject here.

---

### Post by DizzyTech on 2007-12-12
I feel that it would be worth mentioning (especially as F-Spot brings Mono into the picture) that applications that need to be set up should not be on the LiveCD.  Most users will not have their picture library with them when using the LiveCD (nor should they, if they're partitioning).

I mean, think of it this way.  There should be some sort of special system set up for when you first run Ubuntu, for introduction purposes.  A side effect of this, that saves install CD space, is that you could introduce a "But wait, there's more!"-type dialog.

---

### Post by Majorix on 2008-01-06
Why doesn't Ubuntu let the user choose which package sections to install, unlike most other Linux distros do?

It would make the distribution much more lightweight and would therefore favor especially Xubuntu a lot, not saying it wouldn't favor other flavors.

The only drawback I can think of is that this will add to the difficulty level of the install, but this could be overcome by letting the user choose between "beginner" and "advanced" install options. Beginner would probably install everything automatically, while in advanced you can choose packages or categories individually.

What do you think?

---

### Post by 23meg on 2008-01-06
[QUOTE=Majorix]What do you think?[/QUOTE]

Read my posts in the thread I merged yours into.

[QUOTE=Majorix]The only drawback I can think of is that this will add to the difficulty level of the install, but this could be overcome by letting the user choose between "beginner" and "advanced" install options. Beginner would probably install everything automatically, while in advanced you can choose packages or categories individually.[/QUOTE]

Modal interfaces aren't favored in GNOME and Ubuntu, [for good reason]("http://ubuntuforums.org/showpost.php?p=3581845&postcount=14").

---

### Post by smartboyathome on 2008-01-06
This has been discussed before, and the reason is because Ubuntu wants to give the user a stable system and then allow you to tweak it after the install.

---

### Post by Majorix on 2008-01-06
Sorry about the duplicate topic - there were no related topics showing up while I was typing the title..

@smartboyathome:
Having a few unneeded/unwanted software removed won't hurt the stability of your system.
And any OS (except for Windows maybe) would allow you to modify your system after the install, it's not just Ubuntu.

---

### Post by smartboyathome on 2008-01-06
Yes, and Ubuntu's LiveCD installer just uses the file system on the CD to install the system, and it would need to be modified.

---

### Post by jarrhed on 2008-03-08
What if after the installation finishes it will let you pick packages to install so that way you can install all your files and then update it all and have a ready distro in way less time kind of like in the OpenSUSE setup

---

### Post by smartboyathome on 2008-03-08
> **jarrhed said:**
> What if after the installation finishes it will let you pick packages to install so that way you can install all your files and then update it all and have a ready distro in way less time kind of like in the OpenSUSE setup

Because that is not how Ubuntu works. They give you a stable system and let you change it after it is installed. Besides, wouldn't it just be easier to use the package manager if you already installed it? After all, the CD is actually slower than the installed system.

---

### Post by timzak on 2008-03-13
I would like this idea if it was implemented like so during the install process:

Option 1: Install Ubuntu now with default applications.

Option 2: Choose which applications to install (advanced users).

If Option 2 is chosen, user is taken to a new screen with Categories (Accessories, Education, Games, Office, Internet, Graphics, etc).  The apps that are normally installed by default would all be listed here and the user would have the option of deselecting any apps they didn't want.  Note that the apps listed would be no different than the apps that are installed by default.  In other words, you wouldn't have the option of installing or removing an app that doesn't already come with Ubuntu by default (say XMMS).

If Option 1 is chosen, then the install would continue like normal (the way it does now).

---

### Post by fluxy.net on 2008-03-15
Ubuntu comes bundled with a variety of software, which while being a good thing, does not necessarily satisfy the needs/wants of many users, who may have preferences for alternate solutions. An example of this is the evolution v/s thunderbird debate or even the totem v/s vlc one. Most other GNU/Linux distributions provide package selection during the installation phase which caters for this problem but this involves a certain level of ambiguity, especially for new users, which is not desirable as far as Ubuntu is concerned.

Nonetheless the initial problem persists - that of user choice. This is where my idea begins: During the pre-install period, offer, besides "Default Install" , the user the option to take part in a small, simple and brief questionnaire, which will allow his/her needs/wants be taken into consideration (it is his/her OS after all!) without causing any real ambiguity. Added to that, it could allow selection of proprietary software (e.g Flash, Java & Restricted Drivers) to be installed, together with respective license agreements and regional filters (Multimedia Codecs in countries where they are not illegal). It could even allow the user choose the theme of his/her installation (for those who don't like the default one).

A sample questionnaire can be found here:
[Sample]("http://docs.google.com/Doc?id=ah8dtsntxxwc_68cpqw7469")

I have submitted this idea on brainstorm, please support it if it interests you. Thanks.

[[IMG]http://brainstorm.ubuntu.com/idea/4348/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/4348/)

---

