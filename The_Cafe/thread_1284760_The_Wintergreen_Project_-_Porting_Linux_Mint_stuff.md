---
title: "The Wintergreen Project - Porting Linux Mint stuff to Ubuntu"
date: 2009-10-07
forum: The Cafe
---

### Post by earthpigg on 2009-10-07
***_--EDIT--_***

Update:

given the following statement [here]("http://ubuntuforums.org/showpost.php?p=8071598&postcount=36") by the head dude at Linux Mint...

> Now, when it comes to Debian itself... there are a few incompatibilities between Ubuntu/Mint and Debian, so for this we usually open a development branch (we do that for some tools already, and we're planning to do for almost all of them since it's in our intention to maintain a Debian-based edition in the near future).

***The Wintergreen Project is being put on hold. ***Depending on how the above works out, the Wintergreen Project may or may not resume.

It is a very real possibility that the project becomes simply aimed at seperating the packages from the Linux Mint repositories and trying to get them in Debian repositories.

> If you want to help with the code, please use git and fork our projects. Try to stick to small atomic commits. When you're happy with your changes, notify us and we'll look into integrating them in either the main branch or the debian branch.


I don't know how to program, but there is a very real possibility that I will eagerly help test and file bug reports.

(It's amazing how much is possible when working with Debian-based stuff without actually knowing how to program, huh? ie: see my sig. Debian truly is the Universal Operating System.)

The .deb for wintergreen-menu will be left up [here]("http://sites.google.com/site/wintergreenproject/wintergreen-packages"), in case anyone wants to take a look or play with it.

***ORIGINAL POST:***

Hello, I would like to share/launch yet another project:

[SIZE="4"][COLOR="YellowGreen"]The Wintergreen Project[/COLOR][/SIZE]

If you don't want to read all of the below, go ahead and just check out the screen shot attached at the bottom of this post. If that gets your interest, go ahead and read the rest. If not, then have an enjoyable October. :)

Copy-pasta from the site [(link)]("http://sites.google.com/site/wintergreenproject/"):
> 
The Wintergreen Project is eventually aimed at porting many of the unique features of Linux Mint upstream to Debian Testing from whence they will eventually find their way into the official Ubuntu repositories.

For now, this is a one-man project, and the interim goals are more limited: create Ubuntu .deb packages of the above in order to get the attention of others to assist me.

The only package that is together as of the 6th of October is [COLOR="YellowGreen"]wintergreen-menu[/COLOR] ([link]("http://sites.google.com/site/wintergreenproject/wintergreen-packages")):

> wintergreen-menu is a port of Linux Mint's mintMenu and supports filtering, favorites, easy-uninstallation, autosession, and many other features. This is version 7 of wintergreen-menu because it's base is Linux Mint 7 (Gloria). 

A screen shot of the wintergreen-menu in action is attached.

Long-term governance of this project is to be determined based on how many (if any) volunteers assist.

Copy-pasta of the ***very tentative and very up-in-the-air*** design philosophy and goals ([link]("http://sites.google.com/site/wintergreenproject/home/design-philosophy")):

>     * **Giving Credit Where Due**. The only way to have Linux Mint installed is to install Linux Mint. This project will not be a replication of effort.
    * **Needless Modifications Will Be Avoided**. At this stage, the goal is not to improve anything. Unless there is a specific reason for a given modification, there will not be one. Suggestions for improving any given port and individuals volunteering their coding efforts towards possible improvements will be directed to the folks at Linux Mint.
    * **Each ported item should have as short a list of dependencies as realistically possible**.
    * **Debianisation**. Each ported item will become a source tarball and a 64 and 32 bit .deb that is compatible with Debian Testing. Ideally, the source code will be compilable onto any of the dozen or so architectures supported by Debian, but this is not a priority. Once our presence is established at Debian, each ported item will have a package maintainer.
    * **Transparency**. There will be as few private discussions about this project as possible. A list of all discussions that pertain to this project will be established to allow anyone full access to all information.
    * **Community-centered development**. Mailing lists are great, but supporting the above goal would be best accomplished by keeping the discussions at the already-existing discussion forums of Debian, Ubuntu, and Linux Mint.
    * **Release Cycle**. After each release of Linux Mint, efforts will be made as quickly as possible to begin porting the latest improved Linux Mint packages upstream to Debian Testing. Given how the Ubuntu, Linux Mint, and eventually Wintergreen Project release cycles work, the end-state will be that 9.10-based Linux Mint's ported wintergreen packages will appear in 10.04. As neither the Debian, Ubuntu, or Linux Mint release cycles can be expected to be radically modified just to support this project, wintergreen packages in Ubuntu will always be one release behind the latest-and-greatest from Linux Mint.
    * **Clearly Named, Intuitive, and Non-Invasive wintergreen packages**. As an example, the first package completed and submitted to Debian will be the wintergreen-menu package. Once installed, this package will add an entry in the right click on gnome-panel -> add to panel interface called "Wintergreen Menu". If a user adds this to the gnome-panel, the result will be a menu nearly identical to the one featured in Linux Mint. 



Well, that is all I have for now. I will shortly be posting something similar over at the official Linux Mint forums and probably the Debian Forums to keep everyone in the loop.


I know that mintMenu is a modified version of something else (from SuSE, I think?).... it's a proof of concept, and as stated the primary goal of this first package is to attract the attention of potential volunteers.


The only testing i have done is with Ubuntu 9.04 32bit. The same package should work on 64 bit as well, in addition to any Ubuntu-derivative using gnome-panel. If and when you get it working on something else, please let me know how it works!


[CENTER]:guitar::guitar:[/CENTER]

---

### Post by aysiu on 2009-10-07
I don't get this whole "porting" business.

Linux Mint is loosely based on Ubuntu, uses Ubuntu repositories mainly, and is fully binary-compatible with Ubuntu.

If you want Linux Mint features, just add the Linux Mint repositories to System > Administration > Software Sources (or /etc/apt/sources.list): ```
deb http://www.linuxmint.com/repository gloria main upstream import 
``` Then MintMenu, MintUpdate, and all that other Mint stuff can be installed with Synaptic Package Manager.

More details here:
[http://packages.linuxmint.com/#7main](http://packages.linuxmint.com/#7main)

---

### Post by earthpigg on 2009-10-07
> **aysiu said:**
> I don't get this whole "porting" business.

Linux Mint is loosely based on Ubuntu, uses Ubuntu repositories mainly, and is fully binary-compatible with Ubuntu.

If you want Linux Mint features, just add the Linux Mint repositories to System > Administration > Software Sources (or /etc/apt/sources.list): ```
deb http://www.linuxmint.com/repository gloria main upstream import 
``` Then MintMenu, MintUpdate, and all that other Mint stuff can be installed with Synaptic Package Manager.

More details here:
[http://packages.linuxmint.com/#7main](http://packages.linuxmint.com/#7main)

in the trivial example of mintMenu -> wintergreen-menu,

-package dependencies need to be changed. installing mintMenu with its depends would have essentially resulted in Linux Mint taking over your system. good for some, but not all. the Mint packages, by default, are not modular at all.

-there was a reference to mintInstall in the mintMenu by default, which needed to be removed.

extract the .deb, make those changes, dpkg --build it back, install it. done.



Trivial changes? ***_yes_***, absolutely.

Trivial for ***_all_*** Ubuntu users? no sir, not at all. knowledgeable folks such as you are not the primary target benefactor of the project.


and if we can get this in the official Ubuntu repositories? even better, even less trivial.

more novice-friendly and more Ubuntu-like. in my humble opinion.

does that make sense?

---

### Post by hoppipolla on 2009-10-07
> **aysiu said:**
> I don't get this whole "porting" business.

Linux Mint is loosely based on Ubuntu, uses Ubuntu repositories mainly, and is fully binary-compatible with Ubuntu.

If you want Linux Mint features, just add the Linux Mint repositories to System > Administration > Software Sources (or /etc/apt/sources.list): ```
deb http://www.linuxmint.com/repository gloria main upstream import 
``` Then MintMenu, MintUpdate, and all that other Mint stuff can be installed with Synaptic Package Manager.

More details here:
[http://packages.linuxmint.com/#7main](http://packages.linuxmint.com/#7main)

oo! *adds* :)


EDIT -- Owh I couldn't get that to work, it failed to find the Packages.gz file ._.

---

### Post by keiichidono on 2009-10-07
I might join, this might be great. I'd work together with Mint developers and maybe improve the stuff we "port". I tried to get into the paper cuts thing but it was too much for me. If you're willing to mentor me then I'll be willing to work with you.

---

### Post by NoaHall on 2009-10-07
Sure, I'm in, 64 bit.

---

### Post by toupeiro on 2009-10-07
So you want to port something into ubuntu that was originally ported from ubuntu.  I think I called this OS inbreeding in another thread.  It still sounds like OS inbreeding.  It's called a repository. Add it.

---

### Post by unknownPoster on 2009-10-07
> **toupeiro said:**
> So you want to port something into ubuntu that was originally ported from ubuntu.  I think I called this OS inbreeding in another thread.  It still sounds like OS inbreeding.  It's called a repository. Add it.

This could also result in infinite recursion. :P

---

### Post by bruno9779 on 2009-10-07
> **toupeiro said:**
> So you want to port something into ubuntu that was originally ported from ubuntu.  I think I called this OS inbreeding in another thread.  It still sounds like OS inbreeding.  It's called a repository. Add it.

Do you mean we should give up modularity to avoid "OS incestuous cross-inbreeding"???

Does it matter what road a package took to get to full functionality? even more so if it is GPL IMHO

---

### Post by themusicalduck on 2009-10-07
Well I installed the mintmenu package you posted. When first using the menu I get this message in the window:

```

Couldn't load plugin: applications

Traceback (most recent call last):

  File "/usr/lib/linuxmint/mintMenu/mintMenu.py", line 249, in PopulatePlugins
    MyPlugin = X.pluginclass( self, self.toggle )

  File "/usr/lib/linuxmint/mintMenu/plugins/applications.py", line 255, in __init__
    self.menuFileMonitors.append( filemonitor.addMonitor(f, self.onMenuChanged, mymenu.directory.Filename ) )

  File "/usr/lib/linuxmint/mintMenu/plugins/filemonitor.py", line 27, in addMonitor
    mask = pyinotify.EventsCodes.IN_DELETE | pyinotify.EventsCodes.IN_CREATE | pyinotify.EventsCodes.IN_MODIFY

AttributeError: type object 'EventsCodes' has no attribute 'IN_DELETE'

```

I am using Karmic mind if it makes a difference.

---

### Post by Tristam Green on 2009-10-07
> **toupeiro said:**
> So you want to port something into ubuntu that was originally ported from ubuntu.  I think I called this OS inbreeding in another thread.  It still sounds like OS inbreeding.  It's called a repository. Add it.

When the family tree starts looking like a circle, the Ubuntu logo makes sense.

Horrible, horrible joke.  I know.  And I'm only kidding.

I don't really see the point in this either, seeing as like aysiu (and others) said, the repositories are compatible.  Just add them and blammo, you have your select components of Mint.

---

### Post by NormanFLinux on 2009-10-07
Ubuntu is more bleeding edge. Mint Linux is based on Ubuntu's LTS versions so there is an incompatibility between Ubuntu packages and those on their system.

---

### Post by LowSky on 2009-10-07
> **NormanFLinux said:**
> Ubuntu is more bleeding edge. Mint Linux is based on Ubuntu's LTS versions so there is an incompatibility between Ubuntu packages and those on their system.

What re you talking about? Mint 7 is based on 9.04, and Mint 8 will be based on Ubuntu 9.10
[http://en.wikipedia.org/wiki/Linux_Mint#Releases](http://en.wikipedia.org/wiki/Linux_Mint#Releases)

---

### Post by Tristam Green on 2009-10-07
> **NormanFLinux said:**
> Ubuntu is more bleeding edge.

This is about the most laughable thing I think I've ever seen written on these forums, ever.

The two are mutually exclusive of each other.

---

### Post by NormanFLinux on 2009-10-07
Mint follows a couple of months behind Ubuntu. Mint 8 for example - will not be released when the official Ubuntu version debuts.

---

### Post by NormanFLinux on 2009-10-07
Really? I don't think it makes sense to port features from derived distros over to Ubuntu. That's the reason distros exist.

Duh

---

### Post by aysiu on 2009-10-07
> **earthpigg said:**
> in the trivial example of mintMenu -> wintergreen-menu,

-package dependencies need to be changed. installing mintMenu with its depends would have essentially resulted in Linux Mint taking over your system. good for some, but not all. the Mint packages, by default, are not modular at all.

-there was a reference to mintInstall in the mintMenu by default, which needed to be removed.

extract the .deb, make those changes, dpkg --build it back, install it. done.



Trivial changes? ***_yes_***, absolutely.

Trivial for ***_all_*** Ubuntu users? no sir, not at all. knowledgeable folks such as you are not the primary target benefactor of the project.


and if we can get this in the official Ubuntu repositories? even better, even less trivial.

more novice-friendly and more Ubuntu-like. in my humble opinion.

does that make sense? If those are genuine dependencies, they should be brought over. Otherwise, the package is badly put together and should be re-written even in Mint so that it depends on only the packages it **needs**. That isn't porting. That's fixing a bug.

---

### Post by LowSky on 2009-10-07
> **NormanFLinux said:**
> Mint follows a couple of months behind Ubuntu. Mint 8 for example - will not be released when the official Ubuntu version debuts.

NormanFLinux, before you say its based on LTS, now you say its a couple of months behind. Clearly you barely know what your talking about. 

Linux Mint has one advantage over Ubuntu and that is eye candy. I wish the Ubuntu developers would spend the time making simple things like  Grub and the boot screen look beautiful.

---

### Post by Mehall on 2009-10-07
> **aysiu said:**
> If those are genuine dependencies, they should be brought over. Otherwise, the package is badly put together and should be re-written even in Mint so that it depends on only the packages it **needs**. That isn't porting. That's fixing a bug.

Where do we sort the multiple issues of this in Ubuntu then?

The kind of ones where a single app drags in the entirety of Gnome (often including other stuff like Pulse Audio)

No, I can't think of an example off the top of my head, but there are a few.

---

### Post by unknownPoster on 2009-10-07
> **Mehall said:**
> Where do we sort the multiple issues of this in Ubuntu then?

The kind of ones where a single app drags in the entirety of Gnome (often including other stuff like Pulse Audio)

No, I can't think of an example off the top of my head, but there are a few.

The whole idea with the ubuntu-desktop meta-package confuses the heck out of me. If I want to remove something like Ekiga, it shouldn't remove the rest of Gnome with it...

Granted, I haven't used Ubuntu Desktop Edition since 8.04 so things could have changed since then.

---

### Post by NormanFLinux on 2009-10-07
The main advantage of Linux Mint it has multimedia codecs installed by default as well as its own package manager and control panel. Not the eye candy.

You can install Mint theme in Ubuntu by downloading it and tweaking the settings. Nothing special there.

---

### Post by aysiu on 2009-10-07
> **NormanFLinux said:**
> The main advantage of Linux Mint it has multimedia codecs installed by default as well as its own package manager and control panel. Not the eye candy.

You can install Mint theme in Ubuntu by downloading it and tweaking the settings. Nothing special there.
You can also download the Mint package manager and control panel as well.

Mint is about 95% Ubuntu (with the actual Ubuntu repositories, too) and only 5% Mint, and that 5% you can easily add to Ubuntu by adding the Mint repositories.

---

### Post by handy on 2009-10-07
Mint is slick.

I really like the extra polish that the Mint team has put on Ubuntu; the installation was slick & quick, (on my difficult hardware too) it is the easiest system install I have ever experienced, & that's apart from the fact that the proprietary stuff was incorporated in the process.  (There is a version without the proprietary packages, for those that require it that way for whichever reason)

The Mint-6-Xfce system install really knocked me out, I can't remember any install that was simpler than Mint's, not since I started with these dreadful machines in 1986.


Though personally I think the Wintergreen Project is a waste of time.

If you want Mint then just install & use Mint?

---

### Post by OpenGuard on 2009-10-07
What's the purpose of all this show ? Mint menu .. it's a customized gnome-main-menu, which is, of course, in Ubuntu repositories. Simply, if you want your Ubuntu to look exactly like Mint, install Mint, not some ported crap.

---

### Post by Luke has no name on 2009-10-07
> **OpenGuard said:**
> What's the purpose of all this show ? Mint menu .. it's a customized gnome-main-menu, which is, of course, in Ubuntu repositories. Simply, if you want your Ubuntu to look exactly like Mint, **install Mint, not some ported crap**.

Another encouraging remark from the open source community.

You troll on a level surpassed only by Sean Hannity and Michael Moore.

---

### Post by OpenGuard on 2009-10-07
> **Luke has no name said:**
> 
You troll on a level surpassed only by Sean Hannity and Michael Moore.

Intelligence ..

---

### Post by Greg Xix on 2009-10-07
I for one like Linux Mint a lot. I use it on my laptop.

For the Original Poster:

I think I see what you are trying to do. But I think your "project" is splitting hairs a bit too much. As people have pointed out: LinuxMint is just Ubuntu with Multimedia Codecs and Plugins pre-installed, with a different Software Manager and a nice "Green" default theme.

It would only take a few minutes to port over Mint OS features: The theme is available on Gnome-Look.org for example. So why would anybody want to go through the hassle?

Linux Mint had beginners in mind(Like grandpa or Auntie B.) who don't want to learn a whole lot about Linux, but just want to browse the Internet, email, watch DVD's(on the road in the RV), save photos, do general word processing, and printing. And do it without having to tweak right out of the box.

*Ubuntu is good for Beginners who want to **LEARN** Linux. LinuxMint is for beginners who want to just **USE** Linux.*

---

### Post by earthpigg on 2009-10-07
hi,

i get the impression some folks here aren't actually reading the thread, as many posts are restating things i mentioned in the original post, and others are objecting and not addressing in any way things in the original post that i put in there in anticipation of these objections.

> Well I installed the mintmenu package you posted. When first using the menu I get this message in the window:


I am using Karmic mind if it makes a difference.

im downloading the karmic beta right now, ill take a look.


> I don't really see the point in this either, seeing as like aysiu (and others) said, the repositories are compatible. Just add them and blammo, you have your select components of Mint.

see above about dependencies doing this will pull.

> If those are genuine dependencies, they should be brought over. Otherwise, the package is badly put together and should be re-written even in Mint so that it depends on only the packages it needs. That isn't porting. That's fixing a bug.

well, maybe it is fixing a bug. the 'porting' part is trying to get the stuff (and not just mintMenu) in Debian Testing and in the Ubuntu repos.

please recall this:
> For now, this is a one-man project, and the interim goals are more limited: create Ubuntu .deb packages of the above in order to get the attention of others to assist me.

> Mint is about 95% Ubuntu (with the actual Ubuntu repositories, too) and only 5% Mint, and that 5% you can easily add to Ubuntu by adding the Mint repositories.

again, dependencies. 

> If you want Mint then just install & use Mint?

correct. in my OP, see:
> The only way to have Linux Mint installed is to install Linux Mint. This project will not be a replication of effort.


and what of people that are quite happy with Ubuntu but perhaps would like to use mintUpload?

or maybe it is possible to get mintUpdate (with it's nice numbered tiers listing the risk of a given update) to work in Ubuntu?


again, just in the trivial example of the menu:

***it is impossible to install vanilla mintMenu without also installing mintsystem and mintinstall. this is not modularity. ***

mintsystem, among other things, will change your up-splash theme and make your system recognized as Linux Mint and not Ubuntu.

rather invasive when all you want is a menu...

---

### Post by earthpigg on 2009-10-07
if you add mint repos and start installing mint stuff, a python script will be added to your init.d.

here are the comments of "mint-adjust.py":

```
# Prepare the log file
# Restore LSB information
# Restore /etc/issue and /etc/issue.net
# Restore Splash screens
# Restore CTRL+ALT+BACKSPACE
# Restore execution permission on /usr/sbin/update-grub
```

'restore', huh...?

---

### Post by koenn on 2009-10-07
> **earthpigg said:**
> 
well, maybe it is fixing a bug. the 'porting' part is trying to get the stuff (and not just mintMenu) in Debian Testing and in the Ubuntu repos.

I think I get it. 
While I was still using Dapper (I tend to stick with LTS), I onece tried to install a couple of Edgy universe packages that did not exist for Dapper. In 2 out of 3 cases, i could pull it of be removing or reducing version numbers in the dependency list - apparently ubuntu tends to set version numbers on dependency packages to make tie the package version to a release, while it technically is not alaways required to do so.
Mint might do something similar.

So basically you want to ubuntufy and debianize the 5% of the Mint packages that are not Ubunutu / Debian. Sounds reasonable.

Both Ubuntu and Debian have rules, procedures and quality requirements re. submitting packages to their repos. I don't know that just editing a  control file will meet those requirements (eg you might have to recompile against your modified dependencies rather than just repackage)
You might want to look into those things before you get to far into this.

---

### Post by handy on 2009-10-07
I don't know what other changes the Mint people have made, but it is certainly more than just superficial, as Mint-6-Xfce is fast, when compared to Xubuntu.

I haven't bothered upgrading Mint-6-Xfce to 7, as I hardly ever use it, Mint is mostly just for emergency web reference using No.2. if my main box has a serious problem.  As such it was perfect, as I've previously mentioned, its install was the simplest I've experienced in just shy of 24 years.

I can see that it would be nice for people to be able to get the Mint menu & such into Ubuntu in a simple fashion from the repo's though.

---

### Post by earthpigg on 2009-10-07
> **handy said:**
> It would be nice for people to be able to get the Mint menu & such into Ubuntu in a simple fashion from the repo's though.

that is an outstanding summary of the long-term desired end-state.

for the folks interested in helping:

>     * Give yourself a task. [Pick something from Linux Mint]("http://packages.linuxmint.com/") and start playing with it. See how far you can get and what you can do.
    * Let us know what your already know and what you are willing to learn and let yourself be tasked out.
    * Let us know your opinion on the project.


("us" refers to me at this point, of course :D )

---

### Post by keiichidono on 2009-10-08
Gonna ignore my post eh?

---

### Post by koshatnik on 2009-10-08
Maybe people should spend less time dicking about with their OS and more time using it.

---

### Post by handy on 2009-10-08
> **koshatnik said:**
> Maybe people should spend less time dicking about with their OS and more time using it.

Why?

Very little of what we do in our entire lives amounts to anything at all. (no matter how important we think we are) 

So where does one get the ticket that says they are qualified to see through the various social, cultural & genetic paradigmatic limitations of humanity?

Productive? According to who?

---

### Post by clemyeats on 2009-10-08
Hi, 

The technology we develop is intended to work and be compatible with Ubuntu. So if something doesn't work well, consider it a bug. 

The dependency between mintmenu and mintsystem for instance (which includes the adjustment system you mentioned, and which in turn can be configured and de-activated) is a known issue in Linux Mint 7, which we are addressing at the moment for Linux Mint 8. 

The issue related to pyinotify is basically a regression due to upstream changes in Ubuntu. We're working on it right now. 

So as far as Ubuntu compatibility is concerned, we're responsible for it and we're happy to fix the bugs. 

Now, when it comes to Debian itself... there are a few incompatibilities between Ubuntu/Mint and Debian, so for this we usually open a development branch (we do that for some tools already, and we're planning to do for almost all of them since it's in our intention to maintain a Debian-based edition in the near future).

If you want to help with the code, please use git and fork our projects. Try to stick to small atomic commits. When you're happy with your changes, notify us and we'll look into integrating them in either the main branch or the debian branch. 

Our git repositories are here: [http://github.com/linuxmint](http://github.com/linuxmint)
And for mintMenu: [http://github.com/linuxmint/mintmenu](http://github.com/linuxmint/mintmenu)

Clem.

---

### Post by Tristam Green on 2009-10-08
> **koshatnik said:**
> Maybe people should spend less time dicking about with their OS and more time using it.

+12

Tweaking the OS is great, and being able to do so is a nice touch.  Actually making it usable (for everyone) is an entirely different thing, though.

Performance is jack if it's not usable.

---

### Post by handy on 2009-10-08
> **Tristam Green said:**
> +12

Tweaking the OS is great, and being able to do so is a nice touch.  Actually making it usable (for everyone) is an entirely different thing, though.

Performance is jack if it's not usable.

For you that is the truth.

For someone else it is not the truth.

We can generalize the truth, but how truthful is that?

It is only a reflection of our current general consensus.

Which will be completely different later, just as it was completely different earlier.

---

### Post by Tristam Green on 2009-10-08
Metaphysical discussions in a supposedly light-hearted forum appear, at first glances, to be serious business.  Then it is proven through inference that they are, in actuality, not.

---

### Post by Chronon on 2009-10-08
> **Tristam Green said:**
> +12

Tweaking the OS is great, and being able to do so is a nice touch.  Actually making it usable (for everyone) is an entirely different thing, though.

Performance is jack if it's not usable.

How does the act of making more software available make anyone's system less usable?  If you aren't interested then don't pursue it, but I don't understand how this poses usability problems for anyone.

---

### Post by earthpigg on 2009-10-09
> **CalvinB said:**
> Gonna ignore my post eh?

no, not at all!

actually, my eyebrow rose a bit at the thought that i am qualified to mentor anyone with this type of stuff, and i wasn't sure how to respond.

im still not, to be honest.... though i do appreciate the compliment! :D

---

### Post by earthpigg on 2009-10-09
> **clemyeats said:**
> Hi, 

The technology we develop is intended to work and be compatible with Ubuntu. So if something doesn't work well, consider it a bug. 

The dependency between mintmenu and mintsystem for instance (which includes the adjustment system you mentioned, and which in turn can be configured and de-activated) is a known issue in Linux Mint 7, which we are addressing at the moment for Linux Mint 8. 

The issue related to pyinotify is basically a regression due to upstream changes in Ubuntu. We're working on it right now. 

So as far as Ubuntu compatibility is concerned, we're responsible for it and we're happy to fix the bugs. 

Now, when it comes to Debian itself... there are a few incompatibilities between Ubuntu/Mint and Debian, so for this we usually open a development branch (we do that for some tools already, and we're planning to do for almost all of them since it's in our intention to maintain a Debian-based edition in the near future).

If you want to help with the code, please use git and fork our projects. Try to stick to small atomic commits. When you're happy with your changes, notify us and we'll look into integrating them in either the main branch or the debian branch. 

Our git repositories are here: [http://github.com/linuxmint](http://github.com/linuxmint)
And for mintMenu: [http://github.com/linuxmint/mintmenu](http://github.com/linuxmint/mintmenu)

Clem.

thanks for the response.

im visiting family this weekend, but will re-read your response and fully process it and respond mid/late next week.

:guitar:

---

### Post by earthpigg on 2009-10-09
one last thing:

i got some really good feeback over on the linux mint forums, too:

[http://forums.linuxmint.com/viewtopic.php?f=152&t=34038](http://forums.linuxmint.com/viewtopic.php?f=152&t=34038)

(if you are going to respond to husse's or emorrp1's comments, please do so there so the discussion doesn't get all sorts of jubled :D )

---

### Post by earthpigg on 2009-10-14
Update:

given the following statement...

> Now, when it comes to Debian itself... there are a few incompatibilities between Ubuntu/Mint and Debian, so for this we usually open a development branch (we do that for some tools already, and we're planning to do for almost all of them since it's in our intention to maintain a Debian-based edition in the near future).

The Wintergreen Project is being halted for the time being.

Depending on how the above works out, the Wintergreen Project may or may not resume.

It is a very real possibility that the project becomes simply aimed at seperating the packages from the Linux Mint repositories and trying to get them in Debian repositories.

> If you want to help with the code, please use git and fork our projects. Try to stick to small atomic commits. When you're happy with your changes, notify us and we'll look into integrating them in either the main branch or the debian branch.

I don't know how to program, but there is a very real possibility that I will eagerly help test and file bug reports.

(It's amazing how much is possible when working with Debian-based stuff without actually knowing how to program, huh? ie: see my sig. Debian truly is the *Universal Operating System*.)

---

### Post by Jesus_Valdez on 2009-10-14
I have some problems with the mintmenu from the link a few post back.

I can't open Synaptic and it doesn's close when I click on an item from the menu, like a software, and it's annoying.

---

### Post by Lukios on 2009-10-14
Not understanding the point of the project. If you want Mint, download Mint. If you want a few of their programs, download them. If want codecs and pretty themes download them or Switch to Mint.

---

### Post by earthpigg on 2009-10-14
> **Lukios said:**
> Not understanding the point of the project. If you want Mint, download Mint. If you want a few of their programs, download them. If want codecs and pretty themes download them or Switch to Mint.

you could have saved yourself some typing by simply saying "I didn't read a single post in this thread, but I'd like to go ahead and post anyways."

:D

---

### Post by NTolerance on 2009-10-14
Is the Mint menu the best "Start menu" for Ubuntu?  I have seen some others but I'm not sure how they compare.  

I'd like a "Start menu" for Ubuntu because the default Applications-Places-System menu takes up too much screen real estate and is clumsy to customize.

---

### Post by earthpigg on 2009-10-14
> **NTolerance said:**
> Is the Mint menu the best "Start menu" for Ubuntu?  I have seen some others but I'm not sure how they compare.  

I know it's wrong and all, but I'd like a "Start menu" for Ubuntu because the default Applications-Places-System menu takes up too much screen real estate and is clumsy to customize.

"best" is very subjective.

what is best for you is not best for joe down the street.

Free Software and Linux are both all about choices.

My objective is/was simply to make mintTools available to more folks (for some of whom, mintMenu ***may*** be the "best"), without adding repositories, and without requiring invasive modifications to one's system.

essentially, do however much or however little is required for compliance to [this]("http://en.wikipedia.org/wiki/Unix_philosophy#McIlroy:_A_Quarter_Century_of_Unix"):
> Write programs that do one thing and do it well. Write programs to work together.

---

### Post by Lukios on 2009-10-14
Actually I did read the posts, but I still don't agree that this is the quite the right way to go about this project as emorrp1 said. I personally used to use mint exclusively, then I started installing everything from the mini.iso installing only what I need plus a few things from Mint. Nothing an average user can't do. I've also installed some stuff from mint on to debian as well, still not seeing the point of this project. Like I said, use mint if you want to use it.

---

### Post by NTolerance on 2009-10-14
> **earthpigg said:**
> "best" is very subjective.

what is best for you is not best for joe down the street.

Free Software and Linux are both all about choices.

My objective is/was simply to make mintTools available to more folks (for some of whom, mintMenu ***may*** be the "best"), without adding repositories, and without requiring invasive modifications to one's system.

essentially, do however much or however little is required for compliance to [this]("http://en.wikipedia.org/wiki/Unix_philosophy#McIlroy:_A_Quarter_Century_of_Unix"):

You're correct about subjectivity, and I understand this, which is why I'm soliciting opinions from users.  

Can the Mint menu be easily customized?  Looking at the screenshot, the very first thing I'd want to do is make icons/fonts as small as possible to get more items visible in the menu.  Is this possible?  

Thanks for your efforts on this project.  I do support any extra apps that can make Ubuntu better and give its users more choices.  Furthermore, any chance this project could work together with [www.getdeb.net](www.getdeb.net)?  That's the first place I go to look for apps that aren't in the Ubuntu repositories.

---

### Post by earthpigg on 2009-10-14
> **NTolerance said:**
>  Furthermore, any chance this project could work together with [www.getdeb.net](www.getdeb.net)?  That's the first place I go to look for apps that aren't in the Ubuntu repositories.

great idea!

i had not thought about that before.

depending on how Clem's objectives stated above work out, will keep that in mind.

---

### Post by Lukios on 2009-10-14
need to know some python for customization.

---

### Post by FrostyC on 2009-10-28
Quick question Ubuntu users of mintMenu, when you mouseover the button does the tooltip say Ubuntu or Linux Mint?
[img]http://i33.tinypic.com/kah9vm.png[/img]

---

### Post by estyles on 2009-11-01
I love this idea - everytime I've upgraded Ubuntu lately, I always try to find a way to get MintMenu - it's the one thing I "can't live without" from Mint.  

Anyway, I downloaded and installed the deb, but it doesn't seem to work on Karmic yet.  Does anyone know of a workaround, or another way to get mintmenu working for Karmic?

The error I get is:
```

Couldn't load plugin: Applications
Traceback (most recent call last):

  File "/usr/lib/linuxmint/mintMenu/mintMenu.py", line 249, in PopulatePlugins
    MyPlugin = X.pluginclass( self, self.toggle )

  File "/usr/lib/linuxmint/mintMenu/plugins/applications.py", line 255, in __init__
    self.menuFileMonitors.append( filemonitor.addMonitor(f, self.onMenuChanged, mymenu.directory.Filename ) )

  File "/usr/lib/linuxmint/mintMenu/plugins/filemonitor.py", line 27, in addMonitor
    mask = pyinotify.EventsCodes.IN_DELETE | pyinotify.EventsCodes.IN_CREATE | pyinotify.EventsCodes.IN_MODIFY

AttributeError: type object 'EventsCodes' has no attribute 'IN_DELETE'

```

---

### Post by slaol_121 on 2009-11-10
> **estyles said:**
> I love this idea - everytime I've upgraded Ubuntu lately, I always try to find a way to get MintMenu - it's the one thing I "can't live without" from Mint.  

Anyway, I downloaded and installed the deb, but it doesn't seem to work on Karmic yet.  Does anyone know of a workaround, or another way to get mintmenu working for Karmic?

The error I get is:
```

Couldn't load plugin: Applications
Traceback (most recent call last):

  File "/usr/lib/linuxmint/mintMenu/mintMenu.py", line 249, in PopulatePlugins
    MyPlugin = X.pluginclass( self, self.toggle )

  File "/usr/lib/linuxmint/mintMenu/plugins/applications.py", line 255, in __init__
    self.menuFileMonitors.append( filemonitor.addMonitor(f, self.onMenuChanged, mymenu.directory.Filename ) )

  File "/usr/lib/linuxmint/mintMenu/plugins/filemonitor.py", line 27, in addMonitor
    mask = pyinotify.EventsCodes.IN_DELETE | pyinotify.EventsCodes.IN_CREATE | pyinotify.EventsCodes.IN_MODIFY

AttributeError: type object 'EventsCodes' has no attribute 'IN_DELETE'

```


I'm getting this same result in Karmic as well....

---

### Post by earthpigg on 2009-11-10
> **slaol_121 said:**
> I'm getting this same result in Karmic as well....

once Linux Mint 8 (which will be based on Ubuntu 9.10) comes out, ill try putting a similar noninvasive[COLOR="Red"]*****[/COLOR] .deb together in the interests of:

a) keeping the 'pilot' project of the overall project alive.
b) it would appear that some folks want to use it. :D

**[COLOR="Red"]*[/COLOR]** To recap, [this]("http://ubuntuforums.org/showpost.php?p=8069183&postcount=29"), from the vanilla mintMenu, is what i personally consider to be a bit invasive. in addition to having mintInstall as a dependency. opinions will vary. And this all assumes that the Linux Mint folks wont ***already*** have done this on their own as part of the LM 8 release.

---

### Post by toaste on 2009-12-16
> **slaol_121 said:**
> I'm getting this same result in Karmic as well....

Recent changes to the Python inotify binding API are to blame here.  I'm guessing Linux Mint is holding a few packages back until they get this fixed.

***Edit #2 - Fix isn't necessary anymore***
Accidentally grabbed an older version of mintMenu to install instead of the latest.
Get the one from Helena, which depends on mint-translations and mint-common. It should work out of the box, if not run the mintmenu command to open it with a terminal attached to check the debug output.

Here's a quick-and-dirty fix*:

The file is /usr/lib/linuxmint/mintMenu/plugins/filemonitor.py
Search ".EventsCodes.IN_" replace with ".IN_"

*EDIT: Okay, so the buttons now load, the action on click doesn't occur. Will edit again if I find more stuff to fix, but for now it's progress.

Credit to David Wagner for noting the changes in pyinotify 0.8 when this bug bit Exaile: [https://bugs.launchpad.net/exaile/+bug/382283](https://bugs.launchpad.net/exaile/+bug/382283)

---

