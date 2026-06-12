---
title: "Blankbuntu, An idea that occurs to me."
date: 2009-12-02
forum: The Cafe
---

### Post by Warpnow on 2009-12-02
I was considering today the prospect of using remastersys to make an XFCE based ubuntu distribution that was truly lightweight (under 50 megs of ram), so I started thinking, what applications do most people want?

Then it hit me...most people don't want the same applications. They add whatever applications they want on the first boot. Now, the developers are very bright, so that's why ubuntu uses mostly gnome applications, rather than randomly throwing in KDE apps or else into it, causing a myriad dependencies, which is (I guess) why you don't see many distributions by default mixing gtk/qt apps too much, as well as alot of other things.

But its all for naught. If a KDE app is better, the user is going install it anyway, be damned with the dependencies, unless it slows down their system. Wouldn't it be better, then, if Ubuntu came with no applications?

This is the part where you scream at me, "But Warpnow! There's a minimal install CD just for that!!"

My response is simply, the minimal install cd *scares* people, so what if there were blank versions of ubuntu? Install Blankbuntu- Gnome edition, and you get just Gnome, and add/remove software. You install Blankbuntu KDE- And get just KDE, and adept.

Or, better than that, would be installing, and then having the first boot immediately run a simple program that asks you what Desktop environment/Window manager you prefer, and it install it for you, and uses a default configuration scripts we all make (some of the WMs have godawful defaults), or better yet, the user is shown a series of window managers, clicks on one, and up pops a screenshot and a description. 

That way, once the user gets into his system, he doesn't have all these useless programs he'll never ever use. *cough*Ekiga*cough*.

Just an idea. I don't know how to actually make the program I talked about.

---

### Post by -grubby on 2009-12-02
Minimalistic, but not totally bare. I kinda like it.

---

### Post by Dark_Stang on 2009-12-02
I <3 my minimal installs. Run that, then the following command.
```
sudo aptitude install x-window-system-core gnome-core gdm firefox synaptic xubuntu-system-tools gnome-app-install powernowd
```
Then I pretty much do what I want from there.

---

### Post by Cam42 on 2009-12-02
so, KDE, Adept, and that's it? Maybe a terminal as well?

Most people would start it up, and pop sudo apt-get install firefox into a terminal, and be done.

---

### Post by Warpnow on 2009-12-02
> **Cam42 said:**
> so, KDE, Adept, and that's it? Maybe a terminal as well?

Most people would start it up, and pop sudo apt-get install firefox into a terminal, and be done.

Yeah, terminal'd be good, hehe. But, yeah, I think alot would, so why waste resources with applications the user didn't want, didn't ask for, and won't use?

---

### Post by killa.fr0gg on 2009-12-02
I like that idea. I inevitably spend days add/removing software to create the desktop I want, and it would be nice to not have to remove a bunch of orphaned packages afterwards. A unified install like this that would enable people to choose their desktop environment would be quite nice. But you wanna talk about scaring users? You better make sure all the back-end Ubuntu stuff happens in your install (i.e. wireless and driver setup, that kind of thing, automatic networking), and make sure people know that it doesn't come with any software and that they'll need an internet connection to do ANYTHING worthwhile, because otherwise you'll just be delivering a completely useless system. Ubuntu tries to strike a nice balance between simplicity and utility (including "essential" software, but not in the same (bloated) manner as Fedora!), and taking away ANY of that automatic system functionality is gonna completely defeat the purpose.

BUT, if you can truly implement what you want, I'd be very interested!

---

### Post by Crunchy the Headcrab on 2009-12-02
> **killa.fr0gg said:**
> I like that idea. I inevitably spend days add/removing software to create the desktop I want, and it would be nice to not have to remove a bunch of orphaned packages afterwards. A unified install like this that would enable people to choose their desktop environment would be quite nice. But you wanna talk about scaring users? You better make sure all the back-end Ubuntu stuff happens in your install (i.e. wireless and driver setup, that kind of thing, automatic networking), and make sure people know that it doesn't come with any software and that they'll need an internet connection to do ANYTHING worthwhile, because otherwise you'll just be delivering a completely useless system. Ubuntu tries to strike a nice balance between simplicity and utility (including "essential" software, but not in the same (bloated) manner as Fedora!), and taking away ANY of that automatic system functionality is gonna completely defeat the purpose.

BUT, if you can truly implement what you want, I'd be very interested!Granted it's a bigger download, but since you mentioned fedora I thought I'd mention that the install dvd allows you to pick and choose what you install :D

---

### Post by marshmallow1304 on 2009-12-02
Sounds like Arch.  Archbuntu, perhaps? :D

---

### Post by markp1989 on 2009-12-02
i like the idea, i like arch aswell.the roling release does tend to bite me in the **** ocaisionaly lol . 

I like the sound of blankbuntu just comming with the default DE, and no programs, it makes alot of sence, on ubuntu i normaly replace mplayer with mpd, empathy with pidgin, so having nothing pre installed would be nice :D

---

### Post by killa.fr0gg on 2009-12-02
> **Crunchy the Headcrab said:**
> Granted it's a bigger download, but since you mentioned fedora I thought I'd mention that the install dvd allows you to pick and choose what you install :D

Too true. I was referring (complaining about?) more to the idea that there is simply too much there to make heads or tails of at install, and besides you're gonna need to update all those applications... 

I do secretly love Fedora, though, don't get me wrong! It's a nice option to have, if a bit pointless for most living in the information age. I will say, though, I'd rather be stranded with an install disc of Fedora than with an install disc of Ubuntu for exactly that reason.

---

### Post by Warpnow on 2009-12-02
> **marshmallow1304 said:**
> Sounds like Arch.  Archbuntu, perhaps? :D

What I'm talking about would not ever *require* the user to use the command line.

---

### Post by the yawner on 2009-12-02
> **Warpnow said:**
> What I'm talking about would not ever *require* the user to use the command line.
Though I've never used Arch, I believe you'll have to get to a working CLI stage before you could proceed to building a working desktop.

What you're proposing is to come up with a working desktop (perhaps during a live CD session) that would provide the tools to immediately customize the installation to the user's liking. Correct?

I like the idea btw.

---

### Post by Warpnow on 2009-12-02
> **the yawner said:**
> Though I've never used Arch, I believe you'll have to get to a working CLI stage before you could proceed to building a working desktop.

What you're proposing is to come up with a working desktop (perhaps during a live CD session) that would provide the tools to immediately customize the installation to the user's liking. Correct?

I like the idea btw.

Is it necessary to do so during install? It seems to me like it would be alot easier to do once its been installed. If they choose gnome, just a simple apt-get is executed.

Edit: I'm referring to an application that automatically runs on first boot.

---

### Post by the yawner on 2009-12-02
Mmkay, just to clarify, I was referring to this specific part of you post:
> 
Or, better than that, would be installing, and then having the first boot immediately run a *simple program* that asks you what Desktop environment/Window manager you prefer, and it install it for you, and uses a default configuration scripts we all make (some of the WMs have godawful defaults), or better yet, the user is shown a series of window managers, clicks on one, and up pops a screenshot and a description. 

So uhm, I'm not exactly sure but if your going to have a simple program - one with a GUI - run at first boot, that would mean you'll have X installed by default, and perhaps a light windows manager that will display the program at first boot. Don't take my word for it though. I haven't read much yet on how some distros run a first boot wizard (ex. CentOS) for further configuration of their system.

---

### Post by Simian Man on 2009-12-02
I kind of like this idea too, but I think the real problem is the dependencies of some of the default applications in Ubuntu.  Removing all the stuff you don't need is easy unless it tries to take everything down with it.

Likewise adding just what you want will be hard when the dependencies require you to add stuff you don't want whether it was originally there or not.


> **the yawner said:**
> 
So uhm, I'm not exactly sure but if your going to have a simple program - one with a GUI - run at first boot, that would mean you'll have X installed by default, and perhaps a light windows manager that will display the program at first boot. Don't take my word for it though. I haven't read much yet on how some distros run a first boot wizard (ex. CentOS) for further configuration of their system.

If you only want one application to run at a time, you don't need a window manager.  X alone will work fine.

---

### Post by the yawner on 2009-12-02
Ahh.. There you go. Thanks much, Simian uhm.. Man.
So, I suppose this is doable. :)

---

### Post by Sealbhach on 2009-12-03
> **Warpnow said:**
> Yeah, terminal'd be good, hehe. But, yeah, I think alot would, so why waste resources with applications the user didn't want, didn't ask for, and won't use?

Would you include a file manager, Thunar or Nautilus or something. Thunar works very well in Gnome.

The only concern I would have is not having the correct packages installed to handle events like attaching and mounting a USB device or mounting a CD.

.

---

### Post by Nerd King on 2009-12-03
You can do this from the minimal Ubuntu CD easy enough. You won't get it under 50MB RAM with xfce though, your best bet is something like fluxbox (usable but still tiny) which will give a nice base on which to build.

---

### Post by ve4cib on 2009-12-03
I think rather then producing an essentially bare-bones graphical system it might be more practical to simply add an extra couple of optional steps to the Live-Disc installation that will let the user pick-and-choose applications to install.  Fedora already does this, so it shouldn't be too hard to pilfer some of their code (since it's all open-source).

When you're installing Ubuntu you'd get your usual setup steps (disc-partitioning, language, time zone, etc...), but you'd add a "Customize software to be installed" step (which could be skipped to install the standard applications).

The new step would likely mimic the new Software Centre in terms of layout and organization.  Applications would have a short description, maybe a screenshot, and a checkbox indicating whether or not you want to install it.  This could, in theory, let you install Kubuntu from the Gnome live disc, simply by checking off some different options.  Or you could replace Totem with VLC, install Gnome-Do by default, etc...

Essentially the end result is the same; you have Ubuntu with customized packages installed.  But changing the installation method makes the concept more user-friendly for people who want to tweak what's installed by default, but aren't necessarily as comfortable navigating their way around a bare-bones system as others.  It also means that all the package-customization options can be found on the live CD, rather than adding another CD to the collection.

---

### Post by MaxIBoy on 2009-12-03
> **Warpnow said:**
> Or, better than that, would be installing, and then having the first boot immediately run a simple program that asks you what Desktop environment/Window manager you prefer, and it install it for you, and uses a default configuration scripts we all make (some of the WMs have godawful defaults), or better yet, the user is shown a series of window managers, clicks on one, and up pops a screenshot and a description. That sounds pretty easy to do. Little Gtk program in Python for selecting a DE/WM, plus the standard graphical Ubuntu wizard, plus absolutely nothing else, all on a minimalist bootable environment with a lightweight WM like Fluxbox.

---

### Post by Aflack on 2009-12-03
ubuntu that came with gnome, terminal, and some system things like keyboard and mouse and such. (that might be included with gnome)

Id like that. but atm i got kde and gnome in the same install. about to remove kde though, not good with ubuntu. might try opensuse.

---

### Post by AllRadioisDead on 2009-12-03
> **ve4cib said:**
> I think rather then producing an essentially bare-bones graphical system it might be more practical to simply add an extra couple of optional steps to the Live-Disc installation that will let the user pick-and-choose applications to install. Fedora already does this, so it shouldn't be too hard to pilfer some of their code (since it's all open-source).
 
When you're installing Ubuntu you'd get your usual setup steps (disc-partitioning, language, time zone, etc...), but you'd add a "Customize software to be installed" step (which could be skipped to install the standard applications).
 
The new step would likely mimic the new Software Centre in terms of layout and organization. Applications would have a short description, maybe a screenshot, and a checkbox indicating whether or not you want to install it. This could, in theory, let you install Kubuntu from the Gnome live disc, simply by checking off some different options. Or you could replace Totem with VLC, install Gnome-Do by default, etc...
 
Essentially the end result is the same; you have Ubuntu with customized packages installed. But changing the installation method makes the concept more user-friendly for people who want to tweak what's installed by default, but aren't necessarily as comfortable navigating their way around a bare-bones system as others. It also means that all the package-customization options can be found on the live CD, rather than adding another CD to the collection.
 I second this, I've been wondering about this for a while now.

---

### Post by openuniverse on 2009-12-03
.

---

### Post by bailout on 2009-12-03
When I first tried linux (before high speed internet) distros came on multiple cds and during install you selected de and apps. Ubuntu has pushed the one install cd with limited apps and no choice. I think the one cd with a basic selection of apps is good but have never understood why they couldn't just put an optional stage in the installer where you could deselect apps. I seem to remember this being raised early on on here and there were howls of protest that allowing choice would somehow be detrimental. Never understood it myself.

---

### Post by Tibuda on 2009-12-03
> **marshmallow1304 said:**
> Sounds like Arch.  Archbuntu, perhaps? :D

There's nothing sounding like Arch. Ubuntu minimal could sound, but it is not rolling, which makes a big difference (not for good or for bad, only different).

---

### Post by madjr on 2009-12-03
sounds like a jolicloud/chromeos/ubuntu supa remix thingie

minimun install, a browser and bunch of links to webapps to get quickly firedup. i like it.

but the user has the power to install common native apps later on :)


the advantage of this is it's easy, lightweight, updates faster, etc.

people can try the damn thing quicker (cuz the download is small) n see if their hardware works or not.

it's how linux distros should b :)

---

### Post by Simian Man on 2009-12-03
> **bailout said:**
> When I first tried linux (before high speed internet) distros came on multiple cds and during install you selected de and apps. Ubuntu has pushed the one install cd with limited apps and no choice. I think the one cd with a basic selection of apps is good but have never understood why they couldn't just put an optional stage in the installer where you could deselect apps. I seem to remember this being raised early on on here and there were howls of protest that allowing choice would somehow be detrimental. Never understood it myself.

Most distros include a DVD/Multiple CD option that does exactly this.  Try the Fedora DVD install, it's fantastic.

---

### Post by Skripka on 2009-12-03
> **bailout said:**
> When I first tried linux (before high speed internet) distros came on multiple cds and during install you selected de and apps. Ubuntu has pushed the one install cd with limited apps and no choice. I think the one cd with a basic selection of apps is good but have never understood why they couldn't just put an optional stage in the installer where you could deselect apps. I seem to remember this being raised early on on here and there were howls of protest that allowing choice would somehow be detrimental. Never understood it myself.


Why?

It is simple really.  Why should you download 4 GB of obsolete apps for a DVD, only to have to RE-download updated versions of them  again on you 1st update?  That truely makes no sense.

---

### Post by lykwydchykyn on 2009-12-03
This project sounds more and more like the debian installer in graphical mode.  Why not just see if you can get the graphical version of the debian installer themed for Ubuntu?  The ncurses version is what the server disk uses.

I use this installer (the non-graphical one) with my pxe server at work, and at the end I get a menu allowing me to install a bunch of different meta-packages.

'course you'd need to create meta-packages for minimal DE installs, or somehow add them to tasksel.  But it makes more sense to utilize the existing tech than reinvent the wheel.

---

### Post by SpriteSODA on 2009-12-03
It's called Arch.

---

### Post by Skripka on 2009-12-03
> **SpriteSODA said:**
> It's called Arch.

Now you've gone and done it...

---

### Post by Ric_NYC on 2009-12-03
> **Warpnow said:**
> I was considering today the prospect of using remastersys to make an XFCE based ubuntu distribution that was truly lightweight (under 50 megs of ram), so I started thinking, what applications do most people want?

Then it hit me...most people don't want the same applications. They add whatever applications they want on the first boot. Now, the developers are very bright, so that's why ubuntu uses mostly gnome applications, rather than randomly throwing in KDE apps or else into it, causing a myriad dependencies, which is (I guess) why you don't see many distributions by default mixing gtk/qt apps too much, as well as alot of other things.

But its all for naught. If a KDE app is better, the user is going install it anyway, be damned with the dependencies, unless it slows down their system. Wouldn't it be better, then, if Ubuntu came with no applications?

This is the part where you scream at me, "But Warpnow! There's a minimal install CD just for that!!"

My response is simply, **the minimal install cd *scares* people, so what if there were blank versions of ubuntu? Install Blankbuntu- Gnome edition, and you get just Gnome, and add/remove software. You install Blankbuntu KDE- And get just KDE, and adept**.

**Or, better than that, would be installing, and then having the first boot immediately run a simple program that asks you what Desktop environment/Window manager you prefer, and it install it for you**, and uses a default configuration scripts we all make (some of the WMs have godawful defaults), or better yet, the user is shown a series of window managers, clicks on one, and up pops a screenshot and a description. 

That way, once the user gets into his system, he doesn't have all these useless programs he'll never ever use. *cough*Ekiga*cough*.

Just an idea. I don't know how to actually make the program I talked about.




Red Hat's Anaconda... 1998.

---

### Post by cascade9 on 2009-12-03
@ Warpnow - good idea, I've been thinking something similar for a while. 

> **Skripka said:**
> Why?

It is simple really.  Why should you download 4 GB of obsolete apps for a DVD, only to have to RE-download updated versions of them  again on you 1st update?  That truely makes no sense.

2 reasons- 
1- Not everyone has internet. I ran Debian sarge totally offline for ages. (I actually had internet, but by 56K via a winmodem that refused to work under linux) 

2- Its faster to get 'obsolete apps' off a DVD than it is to dl them with a crappy connection (which lot of people have). Then, when you get updates, just update the most needed things 1st (security updates) and the rest later..if at all. Just because theres newer version of open office, VLC, mplayer, etc doesnt make the old ones stop working.  

BTW, you dont have to dl DVDs (or install CDs etc), theres other ways to get them (friends, magazines, ordering them)

---

### Post by forrestcupp on 2009-12-03
This is a great idea, but I can see one problem with it.  A lot of people don't know what software they need to install to get their system running properly.  I install the minimal system, but then I need to get my wireless and sound working, and I don't have any idea what all I need to install to get everything working properly.  

These are things that a lot of people just take for granted when they install Ubuntu, and they wouldn't have any idea what needs to be installed when they're faced with a blank system.

If you could overcome that obstacle and make it still easy to set up a workable system, you'd have a good thing.

---

### Post by the yawner on 2009-12-03
> **SpriteSODA said:**
> It's called Arch.
Right. That's why a lot of newbies go to Arch.

As for the providing a *customize* option on the official live CD, I'm for it. But can we assume that the users will not expect good support from Canonical/Ubuntu  for packages they add during the install that are outside the main repository?

---

### Post by beastrace91 on 2009-12-03
I'd like to throw out there that I also think this is a fantastic idea - give the user simply the DE of their choice, a terminal, and the software center :D

Anyone put up a remastered ISO yet?

Cheers,
~Jeff

---

### Post by beastrace91 on 2009-12-03
> **SpriteSODA said:**
> It's called Arch.

I really wish people would stop posting this in this thread - everyone who has done so obviously has NEVER installed Arch. What is described at the start of this thread is NOTHING like installing Arch - for starters it'd be an Ubuntu base - so it'd use .deb installers and would *not* be a rolling release distro...

Plus it would install a DE by default & it would be using apt-get not pacman.

~Jeff

---

### Post by openuniverse on 2009-12-03
.

---

### Post by earthpigg on 2009-12-03
i agree with you, Warpnow.

the most direct and easiest way to do this would be for you yourself to fill the bare-bones-xfce-ubuntu niche by releasing a livecd on your own.

someone who likes gnome fill the gnome niche.

i'm already working the lxde niche. (needed because Lubuntu aims to be exactly like kubuntu or xubuntu... so, not filling the niche we are discussing)

someone else take care of kde.

and so on.

[this]("http://sites.google.com/site/masonux/home/notes-to-myself") may be helpful to you, or others. i detail the process i use for my basic-lxde-with-ubuntu .iso remix. nothing mind blowingly unique there, but there may be something new to you... and maybe later on you will have something i can learn from? :D

---

### Post by SpriteSODA on 2009-12-03
I'm sorry if it came out as if I mock your arguments, I too think that many of the apps coming with Ubuntu are unnecessary or even absolete, but in order for Ubuntu to be an Out-of-the-Box OS, with competative features like the word proccecing of OpenOffice, photo editing of Gimp, desktop effects of Compiz and Firefox web browser - It should keep it's current line. 
However, it might still be a good idea to eliminate some old and absolete apps from the collection.

---

### Post by earthpigg on 2009-12-03
> **openuniverse said:**
> metapackages not entirely unlike "ubuntu-minimal," say, bb-wireless-support (bb = blankbuntu,) or bb-wireless-guis could help here. as for "it's called arch" (another post) cool if it is, but no one told me that using arch was exactly like using ubuntu except that you could choose which packages go in. sounds great!

it also would potentially be helpful to release general purpose .deb metapackages on our own.

so, two alternative ways to get bb-wireless-9.10 out to folks...

1) go through the process of getting it into the *community* repo. this may take months, i honestly have no idea how this whole process works.

2) any of us can use dropbox's as a ghetto repository. today, someone interested in this, go ahead and make the metapackage ([it isn't hard]("http://sites.google.com/site/masonux/home/notes-to-myself/metapackage")) and put it on your public dropbox.... instead of typing "sudo apt-get install bb-wireless," users would need to be told to type "wget http://dropboxblabla/bb-wireless-9.10.deb" and then resolve the dependencies to install.

---

### Post by openuniverse on 2009-12-03
.

---

### Post by earthpigg on 2009-12-03
> **SpriteSODA said:**
> I'm sorry if it came out as if I mock your arguments, I too think that many of the apps coming with Ubuntu are unnecessary or even absolete, but in order for Ubuntu to be an Out-of-the-Box OS, with competative features like the word proccecing of OpenOffice, photo editing of Gimp, desktop effects of Compiz and Firefox web browser - It should keep it's current line. 
However, it might still be a good idea to eliminate some old and absolete apps from the collection.

he isn't talking about changing ubuntu from the great "general purpose" distribution it is now. he is talking about an alternative. give folks that may be intimidated by a command line install a choice.

easiest way to do the at-install-time-choose-your-DE idea i can think of...

a remastered .iso that comes with a python script launched first time you boot.... x is installed at this point, but no particular DE or WM. it presents simple little checkboxes the user can click on.

---

### Post by earthpigg on 2009-12-03
also, the thought occurs to me that we could make a metaproject out of this.

a loosly held together central organization/structure that encompasses various bare-DE ubuntu remixes.

BlanketBuntu works for a tentative name, but we will need a name that doesnt include "buntu" to avoid trademark issues.

the most obvious place to put this? remastersys. the head dude offered to host my project there (something i am still very seriously considering taking him up on).

---

### Post by Sin@Sin-Sacrifice on 2009-12-03
Shoot... Blackbuntu? I want a Bloatbuntu live dual-layer Blue-ray.

---

### Post by the yawner on 2009-12-03
> **Sin@Sin-Sacrifice said:**
> Shoot... Blackbuntu? I want a Bloatbuntu live dual-layer Blue-ray.
You're knocking at the wrong door.

@earthpigg
I suppose the only way to get about with this is to start with a document spec. I'd rather the goals of the project are clearly defined before anyone starts going about with the array of tools/instructions to deliver the project.

---

### Post by marshmallow1304 on 2009-12-03
> **Warpnow said:**
> What I'm talking about would not ever *require* the user to use the command line.

Of course.  That's why it's a good idea.  Minimal-install distros are a dime a dozen, but few or none have a nice GUI for customizing what programs are installed right off the bat.

> **danielrmt said:**
> There's nothing sounding like Arch. Ubuntu minimal could sound, but it is not rolling, which makes a big difference (not for good or for bad, only different).

I should probably learn to qualify my statements.  I was merely equating the minimal aspects of Arch and this Blankbuntu idea (which I like very much).

---

### Post by Grifulkin on 2009-12-03
Honestly you could call it Blanket Linux.  Although on an unrelated note, the word Blanket makes me think of Michael Jackson.

---

### Post by earthpigg on 2009-12-04
> **Grifulkin said:**
> Honestly you could call it Blanket Linux.  Although on an unrelated note, the word Blanket makes me think of Michael Jackson.

i think, to be purely correct in all things, you would first need to get permission from the Linux Mark Institute prior to calling it (or anything else) Linux. odds are, they wouldn't prosecute you either way, but... well, thats why my little project doesn't have the word 'linux' in its name.

but im probably being overcautious.

---

### Post by openuniverse on 2009-12-04
.

---

### Post by Tibuda on 2009-12-04
> **marshmallow1304 said:**
> I should probably learn to qualify my statements.  I was merely equating the minimal aspects of Arch and this Blankbuntu idea (which I like very much).

As I said, you can have "minimal aspects" if go with the [Ubuntu Minimal CD]("http://www.psychocats.net/ubuntu/minimal") instead, which only installs a bash system and apt-get (so you can install stuff). It still doesn't have the best feature of Arch: rolling-release and AUR.

---

### Post by Paqman on 2009-12-04
> **Warpnow said:**
> Install Blankbuntu- Gnome edition, and you get just Gnome, and add/remove software.

I have an image at home of pretty much exactly that. IIRC I chucked in gedbi and gnome-codec-install too. You also might want:

indicator-session-applet
gnome-themes
network-manager

You'll want gnome-themes purely because gnome-core looks pretty horrible without it. The above runs on about 80MB (64-bit).

---

### Post by Grifulkin on 2009-12-04
> **earthpigg said:**
> i think, to be purely correct in all things, you would first need to get permission from the Linux Mark Institute prior to calling it (or anything else) Linux. odds are, they wouldn't prosecute you either way, but... well, thats why my little project doesn't have the word 'linux' in its name.

but im probably being overcautious.

How about Blanket OS instead?  Or Blanked OS?

---

### Post by Warpnow on 2009-12-04
So it comes to my attention there are two kinds of GUIs, those that can ran with and without the X-server.

We wouldn't have to boot X to get a modest gui, the dialog command can generate gui list you pick from and execute commands. You can run the following command in a terminal to see what I mean.

Something like this:
Code:
dialog --title "BlankBuntu Install" --menu "Which System Setup do you prefer?" 100 30 10 "1" "Gnome" "2" "KDE" "3" "XFCE" "4" "LXDE"

We could run multiple dialogs.

Do you want a WM or DE?

Do you want a pre-configured desktop setup or a a blank desktop environment?

Which preconfigured do you want?

ect, ect, ect. Could work, with descriptions and such.

Been toying with this versus a python gui. I know some python. Teaching myself now, but what I've been using for guis is glade...seems pretty dependency heavy, will have to research ways to create a gui python app without using too many dependencies.

Of course, our script could remove the dependencies once done, but that seems a bit roundabout to me. 

The main advantage of a gui, to me, is the ability to add screenshots. Let people see the default setups.

Does anyone know the best way to make a dependency-less Gui application?

---

### Post by juanvdb on 2009-12-07
There was an article in the Full Circle magazine a while ago on how to build your own Ubuntu from the minimal CD, include the apps you want, and build a new Ubuntu CD with those apps.
[http://fullcirclemagazine.org/issue-16/]("http://fullcirclemagazine.org/issue-16/")

---

### Post by earthpigg on 2009-12-07
> **juanvdb said:**
> There was an article in the Full Circle magazine a while ago on how to build your own Ubuntu from the minimal CD, include the apps you want, and build a new Ubuntu CD with those apps.
[http://fullcirclemagazine.org/issue-16/]("http://fullcirclemagazine.org/issue-16/")

make sure you skim the [remastersys forums]("http://geekconnection.org/remastersys/forums/index.php?board=7.0") a bit before diving in... the recent changes to gdm, grub2, etc, have complicated things a bit, and those directions are no longer verbatim accurate.

---

### Post by openuniverse on 2009-12-07
.

---

