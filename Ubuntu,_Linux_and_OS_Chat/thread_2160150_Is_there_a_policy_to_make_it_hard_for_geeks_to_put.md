---
title: "Is there a policy to make it hard for geeks to put back stuff that's been removed?"
date: 2013-07-05
forum: Ubuntu, Linux and OS Chat
---

### Post by elastomer on 2013-07-05
It seems as though every time the user interface is simplified, those of us who've been using Linux a while lose some functionality we like--for instance the removal of the Nautilus status bar: it's been turned off by default for quite a while now, but in the latest versions, it's just gone. There's still an entry for it in Dconf, but it doesn't seem to affect the bottom of the Nautilus window. Is there a policy that when things are simplified, functionality is actually removed, rather than just made more difficult to turn on? I've been using Linux since before kernel v. 1.0, back when we had to write our own mode lines for the X server, so I don't mind mucking about with config files and the rest. It's just disappointing when the developers totally remove functionality that was useful. It's also interesting to come across undocumented features that seem to be difficult to deliberately change, like the option to have the user's desktop wallpaper be reproduced on the welcome screen. I've accidentally turned that on a couple times, and I sort of like it, but when I wander in to the dconf listings, the settings seem to be there to be able to turn it on, but they don't seem to do much, either.

---

### Post by pqwoerituytrueiwoq on 2013-07-05
edit the source code and compile it, or use different software that is not managed by the gnome developers
you may want to try a different DE like mate or xfce where features are being added instead of removed, they still need the eye candy compiz had though cinnamon is ok as well, i don't have any exp with kde

---

### Post by buzzingrobot on 2013-07-06
No.  Software is being designed to appeal to mainstream users. The majority of users, for instance, make only the most basic use of a file manager. 

I also remember editing X config files, and coping with a lot of other inadequacies, especially hardware support. Glad those days are gone.

The capabilities exposed in a GUI are always going to be limited compared to using the shell.  Open a terminal and have at it.

(FOSS projects typically are always starving for personnel, so eliminating options rather than making them optional reduces the support burden.)

---

### Post by Sef on 2013-07-06
Moved to U,L,&OSC because this is not a support thread.

---

### Post by grahammechanical on 2013-07-06
Some of us recently found out the gksu is not installed by default in Saucy Salamander. It is depreciated and to be replaced by something called pkexec. One of us had a conversation about this on developer irc and a developer expressed surprise that users want to edit configuration files anyway. What is wrong with using Vi? He asked.

I sit on the middle with this. I appreciate Ubuntu for being for humans but it is still Linux and it is still possible to do things the geeky way, to use your expression, if we want.

It is nice to be informed about future developments but that can lead to speculation and gossip about things that do not always come about.

Regards.

---

### Post by buzzingrobot on 2013-07-06
> **grahammechanical said:**
> .... developer expressed surprise that users want to edit configuration files anyway.


More developers need to spend more time with more users who are not developers. :)

I used to "liase" with in-house software developers as a part of my job.  While they usually preferred to stay away from users and design and code to a written requirements document, I insisted that they spend at least one full day sitting with the employees who would, eventually, use the software they'd write.  Typically, what I saw was that most of those developers began to go back to those employees for feedback on the work in progress. When we had formal evaluation sessions, I brought employees, too. Results?  Better software, that users played a role in creating and did not think was being forced on them.

---

### Post by MadmanRB on 2013-07-06
Most of this for me is proof that the gnome developers have gone totally insane and lost touch with the common user, in my not so humble opinion.

---

### Post by mips on 2013-07-06
Oh shut up :D

[img]http://img.metro.co.uk/i/pix/2011/11/02/article-1320234956360-0DA6B3C100000578-955066_466x310.jpg[/img]

Use something that works for you!

---

### Post by MadmanRB on 2013-07-06
> **mips said:**
> Oh shut up :D

Use something that works for you!

Just dont blame me when gnome becomes just one single button that only opens up a terminal.

---

### Post by buzzingrobot on 2013-07-06
> **MadmanRB said:**
> Most of this for me is proof that the gnome developers have gone totally insane and lost touch with the common user, in my not so humble opinion.

How, specifically?  

What is there about Gnome Shell that keeps someone from running the software they want to run?

Not whether or not they like Gnome Shell.  That's opinion. But, what is it that people who go out of their way to assert thair hatred of Gnome Shell want to do that it prevents them from doing?

Some may find it inconvenient, and some may find it convenient.  Some may like how it looks, other may not.  Again, that's not relevant. Everyone uses what they like, for all kinds of reasons.

But, the animosity Gnome Shell has prompted -- sustained for more than two years -- suggests that its critics can't use it to do what they want to do.  If so, what is it?

---

### Post by MadmanRB on 2013-07-06
It all goes down to how many use gnome as its default DE, like Fedora and up until now Debian.
Most of the majors either use KDE or Gnome, and while KDE has actually become better Gnome just gets worse.

---

### Post by buzzingrobot on 2013-07-06
> **MadmanRB said:**
> It all goes down to how many use gnome as its default DE, like Fedora and up until now Debian. 

How does rate of use by distributions equate to anything other than rate of use by distributions?

If anything, it measures popularity with distribution builders, which can be influenced by many things that are not important to users.

Debian 7 defaults to Gnome Shell.

 > ...KDE has actually become better Gnome just gets worse.

Sure looks like an opinion in search of evidence to me. :)

---

### Post by MadmanRB on 2013-07-06
> **buzzingrobot said:**
> How does rate of use by distributions equate to anything other than rate of use by distributions?

If anything, it measures popularity with distribution builders, which can be influenced by many things that are not important to users.

Debian 7 defaults to Gnome Shell.

 

Sure looks like an opinion in search of evidence to me. :)

Debian does offer XFCE too

---

### Post by monkeybrain2012 on 2013-07-06
> **buzzingrobot said:**
>  But, what is it that people who go out of their way to assert thair hatred of Gnome Shell want to do that it prevents them from doing?

Some may find it inconvenient, and some may find it convenient.  Some may like how it looks, other may not.  Again, that's not relevant. Everyone uses what they like, for all kinds of reasons.

But, the animosity Gnome Shell has prompted -- sustained for more than two years -- suggests that its critics can't use it to do what they want to do.  If so, what is it?

I don't know about others, but for me the main issue is not so much a change of UI and different ways of navigating the system, in fact I like most of them and would prefer that over gnome2 (Unity is my favourite DE, so I don't have an issue with the radical change of UI ) My main issue with gnome is the relentless removal of useful features such as f3 for split screen in Nautilus. That is a crippling of functionality and as long as Unity is built on top of gnome it affects the latter as well.

---

### Post by mikodo on 2013-07-06
> **MadmanRB said:**
> Debian does offer XFCE too
And is very nice! (IMO)

---

### Post by kurt18947 on 2013-07-06
> **buzzingrobot said:**
> More developers need to spend more time with more users who are not developers. :)

I used to "liase" with in-house software developers as a part of my job.  While they usually preferred to stay away from users and design and code to a written requirements document, I insisted that they spend at least one full day sitting with the employees who would, eventually, use the software they'd write.  Typically, what I saw was that most of those developers began to go back to those employees for feedback on the work in progress. When we had formal evaluation sessions, I brought employees, too. Results?  Better software, that users played a role in creating and did not think was being forced on them.

That others would adopt your involving users in the process.  This thinking is desperately needed and not just in software development.

---

### Post by mikodo on 2013-07-06
> **kurt18947 said:**
> That others would adopt your involving users in the process.  This thinking is desperately needed and not just in software development.
^^ That! 

I work for a government. When a new one comes in, they direct how things are going to be done, with no regard on how it is supposed to be achieved. Drives me nuts.

---

### Post by deadflowr on 2013-07-07
> **MadmanRB said:**
> Just dont blame me when gnome becomes just one single button that only opens up a terminal.

You might be more optimistic than me.:)

I expect all gnome apps to open and close with randomly changing hot corners, whack-a-mole style.

---

### Post by Copper Bezel on 2013-07-07
> **buzzingrobot said:**
> No.  Software is being designed to appeal to mainstream users. The majority of users, for instance, make only the most basic use of a file manager.
And there's still a "status bar," it just appears as a pseudo-tooltip....

I have to say that as of 3.6, I really *like *the changes to Nautilus. I used Marlin as a choice until 3.4. Then Nautilus became, feature-for-feature, Marlin, and I just had fewer choices and no pressing need to bother installing Marlin, which had confusingly changed names and things around the same time anyway and wasn't worth the bother. Now, Nautilus has the first sensible search I've *seen* in a Linux file browser, and I don't even mind it replacing my beloved typeahead functionality, because it's *just that awesome*. 

I kinda like sleeper apps, like Nautilus and Chrome, that have friendly, barebones interfaces and hidden superpowers a keystroke away.

(That's all not to condone the crap that's happened in Gnome wholesale. I just like Nautilus.)

Edit: Nautilus has tabs, as well as (recently) tear-off tabs, which means it can play MDI or multi-window SDI at will. I don't understand the role of F3 splitscreen at all. What does it do that the other two options don't?

---

### Post by mips on 2013-07-07
> **MadmanRB said:**
> Just dont blame me when gnome becomes just one single button that only opens up a terminal.

It was a joke. The girl is from "the only way is essex" and the way she says "oh shut up" always got me smiling for some weird reason.

---

### Post by monkeybrain2012 on 2013-07-07
> **Copper Bezel said:**
> And there's still a "status bar," it just appears as a pseudo-tooltip....



Edit: Nautilus has tabs, as well as (recently) tear-off tabs, which means it can play MDI or multi-window SDI at will. I don't understand the role of F3 splitscreen at all. What does it do that the other two options don't?

Well if you want to compare two opened instances of Nautilus on different directories and maybe  moving files it is more compact to use f3 than to open two windows. tabs don't allow file transfer by dragging. Also, I don't know if it is a bug or a feature, in 13.04 if I open an instance of nautilus for an external storage (usb drive or hard drive) and then minimize it, I can't maximize it again by clicking the Unity launcher, it just open a new instance of nautilus, Only way to get this instance of nautilus back is to use alt-tab or some other switcher. I posted a thread long time ago on the beginner section but no one seems interested so I kind of stop bothering bumping the thread.

---

### Post by Copper Bezel on 2013-07-07
Files can be dragged into another tab- you can either drop them onto the tab itself or drag the item up to hover the tab, which switches to that tab, then drop them wherever you want. It's not quite as quick as the split-pane view for some actions, of course. 


The weirdness with Nautilus windows opened to mounted drives (something I'd never noticed before) is definitely a bug, and I've submitted a bug report - come ["also affects" me]("https://bugs.launchpad.net/unity/+bug/1198726") if you would.

---

### Post by monkeybrain2012 on 2013-07-07
> **Copper Bezel said:**
> Files can be dragged into another tab- you can either drop them onto the tab itself or drag the item up to hover the tab, which switches to that tab, then drop them wherever you want. It's not quite as quick as the split-pane view for some actions, of course. 

Hey I didn't know that before, it is great, thanks for the tip!

> 

The weirdness with Nautilus windows opened to mounted drives (something I'd never noticed before) is definitely a bug, and I've submitted a bug report - come ["also affects" me]("https://bugs.launchpad.net/unity/+bug/1198726") if you would.

I added the "affect me too", see I wasn't sure whether it was a bug or by design (some designs are pretty weird nowadays) and I wasn't sure if it was my setup being corrupted somhow as no one replied to my thread, not even a "me too"

---

### Post by Copper Bezel on 2013-07-07
Re: drag and drop - very cool. = )

Re: the bug report - thanks for chiming in. It's a weird case that I'm guessing not a lot of folks run into, but it's definitely a bug - if it was by design, the windows would appear under the mounted drives on the Launcher instead of under Nautilus. I normally have mounted drives hidden, and I expect bugs when I'm tweaking, but displaying the drive icons didn't change the behavior. I don't see any unusual behavior in Gnome Shell - all Files windows are treated as ordinary Files windows no matter what they point to - so I'm guessing that this is a Unity feature that hasn't been fully implemented.

---

### Post by monkeybrain2012 on 2013-07-09
> **Copper Bezel said:**
> 

The weirdness with Nautilus windows opened to mounted drives (something I'd never noticed before) is definitely a bug, and I've submitted a bug report - come ["also affects" me]("https://bugs.launchpad.net/unity/+bug/1198726") if you would.

Just found out there was already a bug filed
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1170647](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1170647)

---

### Post by Copper Bezel on 2013-07-09
Oh, thanks. I didn't think to look under Nautilus bugs, only Unity bugs, because ... I have no idea. Thanks. It's good to see that there's some work being done with this (and an explanation of the reasons it happens.)

---

