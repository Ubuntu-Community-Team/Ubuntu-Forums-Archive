---
title: "feedback: do you like dash forgeting the last lens you were using ?"
date: 2011-11-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by madjr on 2011-11-24
Need some quick feedback guys (for unity/dash in **precise** and beyond).

Right now imo is rather **annoying** that the dash **forgets** the last lens you were browsing.

You need to do extra clicks to get back where you were. Those **extra clicks** is something that many users have been _complaining_ about unity.

Is like if every time you minimize and restore your browser it goes back to the home page. i.e. you're browsing **UF**, you find a good thread, minimize browser, restore and you're **somewhere else**.

The dash feels similar, as it ignores where you were.

The dash now **remembers** your search terms and filters used on a specific lens (awesome!), but still **forgets** that you were browsing that lens. 

Do you feel this behavior ok,  inconsistent or something else?

---

### Post by matt_symes on 2011-11-24
I think it should be configurable.

---

### Post by godhika on 2011-11-24
Actually thats on the list for precise. the talk was about somewhere between 5 to 10 minutes time out. It should also be possible to put different lenses on the launcher again (as far as I remember from listening via the audio stream at the UDS).  We will see what this cycle will bring ;)

---

### Post by effenberg0x0 on 2011-11-24
I don't like it, it's a waste of time and annoying. Now that they denied the use of custom shortcuts in Dash home (dash home will be excluded as it seems), I need to find the time to move my custom shortcut code to a lens if I still want to use it (and I do - it's a time saver for me). 

But meanwhile, I got back to the boring search/scroll process to find apps, cause I want to be up-to-date with trunk... I immediately noted the lens resetting thing.

But I won't sign-up to launchpad discussion on this. All interface discussion are eternal, boring and, in the end, they do what they want.

> **madjr said:**
> Need some quick feedback guys (for unity/dash in **precise** and beyond).

Right now imo is rather **annoying** that the dash **forgets** the last lens you were browsing.

You need to do extra clicks to get back where you were. Those **extra clicks** is something that many users have been _complaining_ about unity.

Is like if every time you minimize and restore your browser it goes back to the home page. i.e. you're browsing **UF**, you find a good thread, minimize browser, restore and you're **somewhere else**.

The dash feels similar, as it ignores where you were.

The dash now **remembers** your search terms and filters used on a specific lens (awesome!), but still **forgets** that you were browsing that lens. 

Do you feel this behavior ok,  inconsistent or something else?

---

### Post by matt_symes on 2011-11-24
> **godhika said:**
> Actually thats on the list for precise. the talk was about somewhere between 5 to 10 minutes time out. It should also be possible to put different lenses on the launcher again (as far as I remember from listening via the audio stream at the UDS).  We will see what this cycle will bring ;)

I think the timeout should be configurable :)

---

### Post by madjr on 2011-11-24
> **effenberg0x0 said:**
> I don't like it, it's a waste of time and annoying. I want to be up-to-date with trunk... I immediately noted the lens resetting thing.

But I won't sign-up to launchpad discussion on this. All interface discussion are eternal, boring and, in the end, they do what they want.

that's probably why gnome2 had (and other DEs have) a good amount of customization options: to avoid these eternal discussions.

Yeah am also pretty tired of the discussions and justification for some inconsistent or annoying behaviors. :confused:

---

### Post by cariboo on 2011-11-24
> **madjr said:**
> that's probably why gnome2 had (and other DEs have) a good amount of customization options: to avoid these eternal discussions.

Yeah am also pretty tired of the discussions and justification for some inconsistent or annoying behaviors. :confused:

Keep in mind that Gnome 2.X had a 9 year run, so there was lots of time to create customizing options, we are now into the second year of development of unity, and there are more and more customization options available almost daily.

I've been having a look at different lenses that are available, so far the only one I've kept for any amount of time is the [run lens]("http://www.webupd8.org/2011/11/2-unity-applications-lens-alternatives.html"), and plan on installing the unity-bliss-lens a little later on.

Truthfully when the first unity netbook interface was released back at the start of Maverick development, I really thought that it wouldn't work well on the desktop, but with the rewrite and new options continually being added, I'm a reasonably happy unity user. :)

---

### Post by effenberg0x0 on 2011-11-24
One of the things that I am sort of preoccupied (and I'm not sure if they are, but I have expressed this opinion in Launchpad discussions), is that eventually we will have people running Ubuntu Lenses Edition. 

Why? Well, since so few customization proposals are considered for being absorbed by the main code, it's coders are moving their customizations to lenses at PPAs. It makes no sense. If they were absorbed by trunk, a dash-lenses config interface to enable/disable the features provided by these additions would be easy to do. 

I don't have any problem with lenses, but what worries me is:

1. Lenses are not reviewed by Unity coders. One can put whatever he wants in the code and all the Ubuntu hax0r blogs, etc will recommend it with no concern on code quality. The thing can be a resource killer, but that's just fine. OMG!

2. add-apt-repository is such a magic command for the end user. He just pastes it and a new feature is added. Great. Now find me one (1) individual in General Help that is capable of:[INDENT]a) Remembering the name of the PPAs he added and associating each PPA with one lens. 
b) Finding a PPA file location and fixing it's internals (OO->PP) to fix apt-update;
c) At a dep breakage or apt failure, conclude that an offending PPA might be the cause;
d) Know of apt-purge and how to use it;
d) Even if he finds the PPA files, he's not able to transform the ppa-file-name into the ppa-name, in a way that he can use it with ppa-purge (I actually [made a script]("http://ubuntuforums.org/showpost.php?p=11403493&postcount=75") to help users with this automatically)
[/INDENT]My conclusions: 

1. A typical user will run for PPAs in search of basic features. Once installed, he will never be able to remove them. If this tactic continues to be adopted, are we gonna have to scroll the lensesbar horizontally? A typical install will have how many external lenses? 10, 20? Which user has which lenses? Added from where? Is the lens code trash? Which is eating his resources? Who will keep track of this? 

2. How many individuals with broken /etc/apt/sources.list.d (and broken apt, broken deps, etc) have you seen lately? Are you capable of giving them support without knowing how many PPAs he added and what they are? And when you ask the question and the user says he don't know for sure?

3. Is anyone gonna be capable of providing support, once the state of user sources is unknown and users are not capable of informing us about it? Honestly, it will be hell break loose in General Help.

I really hope for a more flexible approach by PP+1. I like Unity and everybody knows how much I defend it and support it. But, right now, seeing this things, I'm beginning to loose faith...

---

### Post by madjr on 2011-11-26
> **effenberg0x0 said:**
> One of the things that I am sort of preoccupied (and I'm not sure if they are, but I have expressed this opinion in Launchpad discussions), is that eventually we will have people running Ubuntu Lenses Edition. 

Why? Well, since so few customization proposals are considered for being absorbed by the main code, it's coders are moving their customizations to lenses at PPAs. It makes no sense. If they were absorbed by trunk, a dash-lenses config interface to enable/disable the features provided by these additions would be easy to do. 

I don't have any problem with lenses, but what worries me is:

1. Lenses are not reviewed by Unity coders. One can put whatever he wants in the code and all the Ubuntu hax0r blogs, etc will recommend it with no concern on code quality. The thing can be a resource killer, but that's just fine. OMG!

2. add-apt-repository is such a magic command for the end user. He just pastes it and a new feature is added. Great. Now find me one (1) individual in General Help that is capable of:[INDENT]a) Remembering the name of the PPAs he added and associating each PPA with one lens. 
b) Finding a PPA file location and fixing it's internals (OO->PP) to fix apt-update;
c) At a dep breakage or apt failure, conclude that an offending PPA might be the cause;
d) Know of apt-purge and how to use it;
d) Even if he finds the PPA files, he's not able to transform the ppa-file-name into the ppa-name, in a way that he can use it with ppa-purge (I actually [made a script]("http://ubuntuforums.org/showpost.php?p=11403493&postcount=75") to help users with this automatically)
[/INDENT]My conclusions: 

1. A typical user will run for PPAs in search of basic features. Once installed, he will never be able to remove them. If this tactic continues to be adopted, are we gonna have to scroll the lensesbar horizontally? A typical install will have how many external lenses? 10, 20? Which user has which lenses? Added from where? Is the lens code trash? Which is eating his resources? Who will keep track of this? 

2. How many individuals with broken /etc/apt/sources.list.d (and broken apt, broken deps, etc) have you seen lately? Are you capable of giving them support without knowing how many PPAs he added and what they are? And when you ask the question and the user says he don't know for sure?

3. Is anyone gonna be capable of providing support, once the state of user sources is unknown and users are not capable of informing us about it? Honestly, it will be hell break loose in General Help.

I really hope for a more flexible approach by PP+1. I like Unity and everybody knows how much I defend it and support it. But, right now, seeing this things, I'm beginning to loose faith...

At an uds session they said lenses would load dynamically, so they wont be on memory unless you clicked on them.

as for the ppa mess you mentioned you're totally right.

but they also mentioned a website to showcase and install lenses, so that may be a better way to keep track of what lenses you have.

But i hope they make it as easy to add/remove as you would remove a widget in kde.

---

### Post by effenberg0x0 on 2011-11-26
I have a feeling that although there's this communication / marketing efforts to promote participation of the community in development for Ubuntu, like [http://developer.ubuntu.com]("http://developer.ubuntu.com/"), the use of the Quickly tool, etc, any program that somehow alters the functioning of the desktop will be rejected. It *seems* like you can create any application, as long as it is not targeted at reading/writing to the default config of the desktop...

I can't understand what is the big deal with adding an icon inside gnome-control-center to open compiz plugins settings, for example. I imagine gnome-control-center should also be the place to activate/deactivate/remove lenses as well as configure other things like plymouth and grub options and manage PPAs. Code-wise, it is really fast to put it together: the interfaces would simply be visual controls to core functionality that is already implemented and solid.

But the people I talked to have the same opinion as mine: Why would one go through the trouble of creating, investing your free time in development, bug fixing, maintenance, etc to make something good and cool, if it's not gonna get merged into trunk anyway? I hope this clear division/limitation between Ubuntu "trusted" developers club / Canonical and community developers one day disappears.

> **madjr said:**
> At an uds session they said lenses would load  dynamically, so they wont be on memory unless you clicked on them.

as for the ppa mess you mentioned you're totally right.

but they also mentioned a website to showcase and install lenses, so  that may be a better way to keep track of what lenses you have.

But i hope they make it as easy to add/remove as you would remove a widget in kde.

Me too, but I think it's more talk. I can't find projects like these undergoing strong development in launchpad. I really doubt we will see any of this in PP. IMO, the support problems that will arise regarding PPA management and lenses will have helpers here and other support forums completely lost. As PP is released, gets media attention and people download/install it for the first time, forums will be full of people complaining 1000Xmore than the small sample we see here now (how do I move the launcher, how do I customize shortcuts, how to I fix my sources.list, where are my traditional gnome-panels, ubiquity bug, plymouth bugs, etc). Nothing to address these is being done but the type of blur used in the dash seems to be a priority.

---

### Post by madjr on 2011-11-26
> **effenberg0x0 said:**
> I have a feeling that although there's this communication / marketing efforts to promote participation of the community in development for Ubuntu, like [http://developer.ubuntu.com]("http://developer.ubuntu.com/"), the use of the Quickly tool, etc, any program that somehow alters the functioning of the desktop will be rejected. It *seems* like you can create any application, as long as it is not targeted at reading/writing to the default config of the desktop...

I can't understand what is the big deal with adding an icon inside gnome-control-center to open compiz plugins settings, for example. I imagine gnome-control-center should also be the place to activate/deactivate/remove lenses as well as configure other things like plymouth and grub options and manage PPAs. Code-wise, it is really fast to put it together: the interfaces would simply be visual controls to core functionality that is already implemented and solid.

But the people I talked to have the same opinion as mine: Why would one go through the trouble of creating, investing your free time in development, bug fixing, maintenance, etc to make something good and cool, if it's not gonna get merged into trunk anyway? I hope this clear division/limitation between Ubuntu "trusted" developers club / Canonical and community developers one day disappears.



Me too, but I think it's more talk. I can't find projects like these undergoing strong development in launchpad. I really doubt we will see any of this in PP. IMO, the support problems that will arise regarding PPA management and lenses will have helpers here and other support forums completely lost. As PP is released, gets media attention and people download/install it for the first time, forums will be full of people complaining 1000Xmore than the small sample we see here now (how do I move the launcher, how do I customize shortcuts, how to I fix my sources.list, where are my traditional gnome-panels, ubiquity bug, plymouth bugs, etc). Nothing to address these is being done but the type of blur used in the dash seems to be a priority.


i agree.

as for the lenses here are some of the talks:

[https://blueprints.launchpad.net/ubuntu/+spec/desktop-p-100scopes](https://blueprints.launchpad.net/ubuntu/+spec/desktop-p-100scopes)

---

