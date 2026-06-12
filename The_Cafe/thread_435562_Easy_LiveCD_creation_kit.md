---
title: "Easy LiveCD creation kit?"
date: 2007-05-07
forum: The Cafe
---

### Post by nigelenki on 2007-05-07
I'm still waiting.  Creating a LiveCD still looks like this:

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

Sorry, I'm too lazy.  My boss isn't going to do this.  My cousin was going to, but she decided it'd be easier to figure out how to install Gentoo.

I've built a LiveCD once.  That's quite enough for me, really, I'm FAR too lazy to want to do this ever again.  I know a lot of other people who want to but are scared off by the instructions.  And why do I have to customize an existing LiveCD anyway, why can't I start from scratch, where are the instructions for that?

Is anyone else in the same boat?  Too lazy, too hard, too I-really-think-a-tool-should-exist-for-this?  I just wrote a spec but you know, all talk no action nothing gets done; but I'm just curious enough to ask, does anyone really have much interest in seeing this happen?

[https://wiki.ubuntu.com/LiveCDCreator](https://wiki.ubuntu.com/LiveCDCreator)

I've attached a poll too.  I love numbers.

---

### Post by aysiu on 2007-05-07
Where's the poll option for "it already exists"?

Try Reconstructor:
[http://reconstructor.aperantis.com/](http://reconstructor.aperantis.com/)

---

### Post by nigelenki on 2007-05-07
> **aysiu said:**
> Where's the poll option for "it already exists"?

Try Reconstructor:
[http://reconstructor.aperantis.com/](http://reconstructor.aperantis.com/)

Now make a Fluxbox based CD from that ;)  Xubuntu as a base maybe?  Strip it down to Ubuntu-Minimal?  Start without the LiveCD, and build the official LiveCDs from scratch?

I'm still amazed at the customization mentality to be honest.  I made a Gentoo LiveCD once; I used the Catalyst tool or something, a command line tool that takes some sort of file you build by hand with a list of packages and builds a LiveCD out of it (and stage 1, 2, and 3 G entoo tarballs).  It was what the maintainers were using.  As far as I can tell, the Ubuntu maintainers brute-force it all the way.

---

### Post by euler_fan on 2007-05-07
This looks like fun. I might do it just to set up a custom install disk rather than need to go through and install a bunch of stuff from scratch. It always seems faster to update than to install cleanly.

---

### Post by aysiu on 2007-05-07
> **nigelenki said:**
> Now make a Fluxbox based CD from that ;)  Xubuntu as a base maybe?  Strip it down to Ubuntu-Minimal?  Start without the LiveCD, and build the official LiveCDs from scratch? Why would I do that? Someone else already has:
[http://fluxbuntu.org/](http://fluxbuntu.org/)

Sounds as if you just like creating a lot of extra work for yourself.

---

### Post by TravisNewman on 2007-05-07
I think te point is that this just doesn't make things easy. I'd love to be able to heavily customize a livecd easily. reconstructor really doesn't work well for that unfortunately.

---

### Post by aysiu on 2007-05-07
> **panickedthumb said:**
> I think te point is that this just doesn't make things easy. I'd love to be able to heavily customize a livecd easily. reconstructor really doesn't work well for that unfortunately.
Can you be more specific? I used Reconstructor only once, and it seemed pretty easy to me (all point-and-click).

What features is it missing?

---

### Post by TravisNewman on 2007-05-07
Sorry, I mistyped. It IS easy, it's just that you can't customize heavily. I was looking for a way to do this easily before the Ubuntu Studio project took off.

For example, it doesn't look like you can install anything that isn't in the repos that you add. If I had a deb file that wasn't in any of the repositories I wanted to add, (Cedega for example) it doesn't look like there's a way to install that. It looks like I can select the theme, but I can't install any themes from gnome-look, etc. And the only thing you can really customize other than package management is gnome's look. (I could be wrong... perhaps if I were to start with xubuntu it would offer customization for xfce, but I'd like to be able to customize and install all of them and create a dvd image).

---

### Post by aysiu on 2007-05-07
> **panickedthumb said:**
> Sorry, I mistyped. It IS easy, it's just that you can't customize heavily. I was looking for a way to do this easily before the Ubuntu Studio project took off.

For example, it doesn't look like you can install anything that isn't in the repos that you add. If I had a deb file that wasn't in any of the repositories I wanted to add, (Cedega for example) it doesn't look like there's a way to install that. It looks like I can select the theme, but I can't install any themes from gnome-look, etc. And the only thing you can really customize other than package management is gnome's look. (I could be wrong... perhaps if I were to start with xubuntu it would offer customization for xfce, but I'd like to be able to customize and install all of them and create a dvd image).
As far as I know, you can do all that... just not through the Reconstructor wizard. You may want to contact mhancoc7 (aka Jereme) about what he did to get customization done on Ubuntu Christian Edition. I think Linux Mint also uses Reconstructor, but I could be wrong about that.

So you're basically saying that you want more GUI options.

---

### Post by TravisNewman on 2007-05-07
A lot more :) Well, I don't care if it's a gui or not. If they're incorporated into Reconstructor then I guess that's how it would be accomplished yeah.

---

### Post by nigelenki on 2007-05-07
Heh, people totally ignore my ad-hominem "I think the developers brute-force it all the way" statement too.  Each cycle, they debbootstrap it a system and build a LiveCD from scratch; it's apparently not hard once you've done it a dozen times.  Thing is, it's hard for us to do, so we "remaster" the LiveCD, in limited ways.

My point is that it'd be nice if procedural changes were made in a body of code for a tool.  Kernel gets moved around appropriately, SquashFS gets built based on a package list and some .debs, bootstrap process is applied, you select "Install" or "Live" output, add Ubiquity to LiveCDs if you like... and in the end, the official CDs are just a template that gets thrown at this and built.

I'd like to see it possible to quickly pull together an "Official" Ubuntu release CD, reliably, from scratch at any point, rolling in the latest updates (security/bugfix).  I'd like to see it possible to pull in 'non-free' packages like MP3 support or Flash.  You can do this with some of the tools that are out there.

What you can't do is build the CDs "clean" without upgrading packages, installing packages, removing packages, etc.  If I want to strip down the CD, I have to manually run through tons of packages; once I pull ubuntu-desktop, I have to whittle out OpenOffice.org, gnome-games, tomboy, gimp, and evolution.  Then I've got to tear out all 15 or 20 Mono libs, not needed without Tomboy.  Then I've got to figure out which GNOME libs I don't need any more, as I don't really have to support Evolution.

Through all of this, I've got to be careful not to remove whatever package supplies all the nice features like X11 detection on the LiveCD.  If I want to deploy an Alternate Install CD (i.e. for a slipstream roll-out), I have to repeat the entire process again using an Alternate Install CD as a base; and the 'remastering' process is different, the stuff isn't really installed.

I suppose the process is the same for casual, non-technical users.  In my world it would be picking the Ubuntu "official" template, adding the package you want, and recreating the CD; this is similar to just using Reconstructor.  Only power users slipstream; and only developers completely customize the CD by changing the window manager and application base drastically.

---

### Post by nigelenki on 2007-05-12
I've had a chance to use Reconstructor now.

I tried removing Evolution and Mono ("Novel software"), and OpenOffice, and adding OpenSSH server.  Also removed the Win32 software.  It came back with a 587MB (instead of 700MB) estimated ISO size; the actual output was 554MB.

I also made Main, Restricted, and Universe available.  This worked, but it didn't give me an interface to chose packages from.  I need to go into a terminal or enter apt lines, or write an 'rmod' script to apply.

I also have to use GNOME, can't use XFCE or whittle down the distribution very far.  Again, might as well be doing this manually, and probably a whole lot cleaner to do it from scratch anyway.

I can't automatically update all the packages and kernel on the LiveCD.  Apparently I need to do this with a manual 'apt-get upgrade' command.  There's a line to enter 'apt-get uninstall' or 'apt-get install' commands (what you enter is prefixed by one or the other), but you need a terminal to upgrade.

Technical consideration, Reconstructor runs entirely as root.  it creates a root-owned directory I need to delete from the shell (with sudo) or log into X as root (you can't on Ubuntu)... you need to use the command line to run 'gksudo nautilus' at the very least to clean its mess out of your home directory.  Using fuse-iso may solve this; although building from scratch would avoid the need to mount an existing LiveCD image.

Overall, pretty useless.  I could start with a Xubuntu CD but Reconstructor won't work with it, at all; the whole process will require manually pulling in packages with apt-get.  Reconstructor can theme GDM for me, which is about as useful as it gets.

---

### Post by nuclear_eclipse on 2007-05-12
As the newest Reconstructor dev (and the only one still alive it seems), I can say that I worked long and hard on creating a from-scratch design for Reconstructor that would have solved a lot of the problems and used a lot of the ideas that have been discussed here.  However, the creator of Reconstructor (Evan) has practically gone MIA, and hasn't responded to me in almost two monthes, and the other dev is also noticeably absent.  

I think I'm the only one that still actively visits the IRC channel to help others.  But because of the lack of other developers and a really busy schedule the past quarter at university, I haven't been able to get any work done on Reconstructor.  And with Evan gone, I personally feel he's abandoned the project.  And quite frankly, the Reconstructor code base is about as worthless as rotten banana peel.  It's nasty to look at, and you can't even get a laugh by using it against someone else!  :-P

What I'm getting at is this:  I would *love* to lead the charge in developing this new project, or at least offer a supporting role if someone else wants to take control.  I've got enough experience with program design and the whole process that I feel I could easily adapt my unused design for Reconstructor to the new project specifications.  

The only piece I'm lacking is familiarity with the way Launchpad and Bazaar work, but since I'm quite used to using Mantis and Subversion for professional and personal work, I feel it will be a simple conversion.

Anyways, I would like to know who else is interested and/or committed to the project, we could take this up together, and it shouldn't be too much work to get the ball rolling on this.

---

### Post by nigelenki on 2007-05-12
If the main dev has gone MIA, you can always fork.  My main perogative is to determine if there is passive or active desire for such a thing, and stir up the community to see the reaction; my life has become a wasted effort since I got a job doing nothing useful (which eats all my time and makes me wish I was a genius enough to work in a research lab doing something useful for society).

Right now I'm seeing passive desire; people seem to think the idea is good in many cases, but are in no way motivated to actually care one way or the other until something actually happens.  It's like candy; you like it, but you're not going to rally the whole IT staff to demand your employer keep a steady supply of blowpops and twix in the breakroom (although you will eat them if they appear one day).

I hadn't looked at Reconstructor's code.  That's considerably amusing.  ;)  As always, if you actually want to lead a project I suggest you get two things:

[list]
[*]A lot of free time
[*]A book on project management
[/list]

You will benefit from both, and possibly may enjoy Gnome 'planner' (I'd love to see full project management tools integrated with Launchpad, and planner taught to talk with it.. want Launchpad source code released...)

---

### Post by nuclear_eclipse on 2007-05-12
[QUOTE=nigelenki]If the main dev has gone MIA, you can always fork.[/quote]

That's the thing, we haven't started any real work on the new design, so there's nothing to fork.  :-P

[QUOTE=nigelenki]As always, if you actually want to lead a project I suggest you get two things:

[list]
[*]A lot of free time
[*]A book on project management
[/list]

You will benefit from both, and possibly may enjoy Gnome 'planner' (I'd love to see full project management tools integrated with Launchpad, and planner taught to talk with it.. want Launchpad source code released...)[/QUOTE]

Well, since I'm mostly done with my studies at university, which focus on project management, and since I'm the lead developer on a web application where I work, I've got a good hang on project design and management, so no worries there.

My real concern is whether or not I can find at least one or more other developers besides myself actively working on the project.  I don't want to sink a lot of hours into a one-man project and never finish.  Are you currently interested in helping out, or is it just something you want to see taken up as a project by others?

---

### Post by MRiGnS on 2007-05-12
UCK - Ubuntu Customization Kit

UCK is a tool that helps you customizing official Ubuntu Live CDs (including Kubuntu/Xubuntu and Edubuntu) to your needs. You can add any package to the live system, for example language packs, or applications.

[http://uck.sourceforge.net/](http://uck.sourceforge.net/)

---

### Post by nuclear_eclipse on 2007-05-12
> **MRiGnS said:**
> UCK - Ubuntu Customization Kit

UCK is a tool that helps you customizing official Ubuntu Live CDs (including Kubuntu/Xubuntu and Edubuntu) to your needs. You can add any package to the live system, for example language packs, or applications.

[http://uck.sourceforge.net/](http://uck.sourceforge.net/)

I think the biggest difference to point out about the idea for this thread and the associated hypothetical project is that it will be separate from the "remastering" method that Reconstructor and UCK both utilize, instead favoring a hand-holding method of "build-from-scratch" style of Live [i]generation/[i].

---

### Post by nigelenki on 2007-05-12
Haven't got the time or skill myself... skill is no problem (I'd like to take up something to learn python or whatnot, although I can't stand perl or ruby); time is a showstopper.  Trying to move to a full time job and find time to study for my CEH and PMP, then maybe find a new job where I can use both.

My job is in the next state so I sink about 11 hours a day into it if you include travel, more if you include things like showering and finding time for breakfast and the fact that nothing productive can be done when you first wake up or have just gotten back from a day of awaken-drive-work-drive (fatigue is a horrible motivator) :(  Hoping to move soon.

Excuses, excuses..

---

### Post by kyzh on 2007-05-17
hi I'm really  interested by a "linux from scratch" ...base on a debian/ubuntu distro... 
I'd like to have a tool to build a distro without lots of technical knowledge  (doing script,check dependences one by one)... 
           someone who try to customize his favorite ubuntu knows the packages he wants (....not to re-install every time he get a disk-crash).I'm not  really convinced  that I save my time writtng a script ...I 'll probably do .. but for non-geeks i think they'll prefer avoided and use the old way  .

            I  'd like  to choose  desktop, kernels,and package from repository , but  add my own sauce too . I don't really know every packages installed , but the interest of starting from scratch or from a basic one is to understand a bit more how does it work.I see lot of people interested by biobuntu, on a french blog, (biologeek.com). there is lots of people there who are in need of a personal distro including their tools , but none really have technical skills  to build it. Such distro exist but as you can see [here]("http://www.biologeek.com/journal/index.php/biobuntu-un-live-cd-pour-la-bio-informatique") it always seem to miss something . the first reply is dated of 2005, the last reply date is a month ... but it seems that no one succed .
 
             gui / not gui  it isn't the issue ... if it builds a basic system ,use a "synaptic like" (aptitude like) to check packages and dependences,and allows to include others .deb (see even  to add / customize themes etc..)

            I have a bit time , but not lots of skills ...I made few thing in C language ,  python  ( and - [-o< pardonner moi- vb.net for  ](*,) f*** school...   --where_is_the_door_please )             I can learn c++ and qt , fox or gtk (I know some people  who can help me for ) ....I have knowledge in  shell...and I 'm able to translate from English to French ...(and make mistakes or misspell when I write  English).....    If you lead me , I will probably do the job ( I hope your not too pressed )...  perhaps I'll find friends to help us (with real skills )   I actually try to be understandable, but google translation is .... --i think you know what i mean --.   if my text has an interest for somebody  so that he responds to me : the shorter the sentences are , the easier I understand.

---

### Post by FuturePilot on 2007-05-17
How about something that will let you install the desktop environment that you want? I would like to re master an Ubuntu .iso and have the E17 desktop by default. I know there is Elive, but Debian hates my computer:-? and Ubuntu just works.

---

### Post by walmartshopper67 on 2007-05-21
I've used reconstructor, and while it's fairly nice it seems to be almost dead. I'm still using it in fact, but i've found myself working around the limitations of the tool itself. I think reconstructor had the right idea - a wizard like tool for customizing a live CD, it just had a lot of bugs. 

I personally think we should find a tool that exists for other distros (i've seen some around) and modify it for Ubuntu. It should be especially easy if the tool is used for Debian. No sense in reinventing the wheel.

---

### Post by spottraining on 2007-05-22
[http://www.linuxmint.com/wiki/index.php/Remastersys](http://www.linuxmint.com/wiki/index.php/Remastersys)
Remastersys is also one option.

---

### Post by SgtDude on 2007-05-22
Reconstructor does give you command-line access to the LiveCD root (it's a button on the lowwer left corner of the window).  From here you can do anything you want to the LiveCD environment, to include adding your own repos (nano /etc/apt/sources.list), installing packages from these repos (apt-get install *packagex*), removing packages (apt-get remove *packagex*), etc.  I don't know the command line tool to install a gnome theme, but I'm sure it exists (it seems everything in linux is command line driven with GUI shells built to run those commands).  So, with Reconstructor, you should be able to do whatever you want with the Ubuntu LiveCD, you just might have to do a little research on some command line tools.

---

### Post by smartboyathome on 2007-06-10
> **spottraining said:**
> [http://www.linuxmint.com/wiki/index.php/Remastersys](http://www.linuxmint.com/wiki/index.php/Remastersys)
Remastersys is also one option.

I have tried it, and as of right now, it works! The only problem I have with it is that it requires a lot of space on a CD for the CD to be created. I was greatly limited by this when I tried making a LiveCD of my Ubuntu (i had to get rid of almost everything, and even got rid of GNOME because I wasn't using it anyway). Anyway, Just giving everyone who wants to try this for a LiveCD.

> **SgtDude said:**
> Reconstructor does give you command-line access to the LiveCD root (it's a button on the lowwer left corner of the window).  From here you can do anything you want to the LiveCD environment, to include adding your own repos (nano /etc/apt/sources.list), installing packages from these repos (apt-get install *packagex*), removing packages (apt-get remove *packagex*), etc.  I don't know the command line tool to install a gnome theme, but I'm sure it exists (it seems everything in linux is command line driven with GUI shells built to run those commands).  So, with Reconstructor, you should be able to do whatever you want with the Ubuntu LiveCD, you just might have to do a little research on some command line tools.

I have tried this tool as well. I feel there are still some flaws, though. Say you wanted to get stuff from the Ubuntu repositories, but have already added everything else. You would not be able to, as there are no keys for you to access it. This, and the fact that I do not know everything about command line, warded me away from Reconstructor.

I would just like to say I have never used UCK, but from what I heard, it is basically the same as Reconstructor. It shares some of the same strengths and weaknesses.

---

