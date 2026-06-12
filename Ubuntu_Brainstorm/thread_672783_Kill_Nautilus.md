---
title: "Kill Nautilus"
date: 2008-01-20
forum: Ubuntu Brainstorm
---

### Post by The Devil Is A Squirrel on 2008-01-20
Let's face it and replace it: Nautilus is totally outdated It's slow as hell and lacking in features. I know, now I will get something like:

[LIST]
[*]Why are you complaining, most of the user don't. That means you are wrong
[*]Then install this or this, run this and this script, then modify this file and this file..blablabla
[*]Go and f%%$ yrs
[*]Go and write a bug report
[/LIST]
I do know that Linux is free and I did not spend 1 cent for it. I know there are many many ppl who do this in their freetime. I know that and appreciate it. But there seems to be a clash in the "community". There are ppl who doing it because they want to change the way we work with computers/ppl and taking users as a vital thing and there are ppl who are just geeks and they give not a sh^& about the users...

The first time I used Linux (10 years ago) there were a lot of ppl saying things like "then Linux is not the right thing for you" or "we don't wanna be on desktops" and stuff like that. All those things changed drastically, especially with Ubuntu - and that's a really good thing!

So I'm curious what I will get on this. Can a user just make a user statement without ending up in a big technical discussion or manipulating stuff in a terminal/file? Can a user just be a user (aka is Linux major enough for the desktop)? Please remind, not every Linux-Newbie or user is a [DAU]("http://www.acronymfinder.com/acronym.aspx?rec={91FB3A0F-89E8-11D4-8351-00C04FC2C2BF}") and slow like a turtle when using a PC. There are actually ppl who can handle Linux pretty good but just don't want use a terminal or manipulating config files or even compiling stuff. I guess that's the vast majority. Now hit me! 8-)

 :popcorn:

---

### Post by smartboyathome on 2008-01-20
Since nautilus is so integrated into GNOME, I think it would be hard to change the default file manager, and even if we did, there isn't another one that comes with less dependancies (lets face it, thunar DOES depend on part of XFCE, and I don't think that Pcmanfm draws desktops and such). Right now, Nautilus is what we got.

---

### Post by The Devil Is A Squirrel on 2008-01-20
I know, therefore I suggesting to replace it. I don't care if this would need a year or two, but just stick with something that doesn't fulfill the job anymore isn't really a solution, right?

---

### Post by 23meg on 2008-01-20
To "kill" Nautilus in Ubuntu, you'll certainly have to "kill" it upstream (in GNOME) too. Given the general "stick with upstream unless absolutely necessary" mentailty in Ubuntu (which is hugely helping the free software world), which tracks GNOME closely, I don't see any chance that a component as central as Nautilus will be dropped unless it's also dropped upstream.

In GNOME, there's plenty of activity surrounding Nautilus. The underlying library that handles all file operations, GnomeVFS, is getting replaced with GVFS/GIO (read lead developer [Alexander Larsson's blog]("http://blogs.gnome.org/alexl/") for details) in GNOME 2.22, and Nautilus is receiving the changes needed for that to happen. This will probably (but not surely; I haven't tested it yet) provide an overall performance boost, along with much saner handling of file operations all over the desktop, less stutters and lockups, etc.

The main problem I see with Nautilus is its sophisticated codebase, which translates to a hard time for new contributors. It's also slow, but has been getting better (for example, with asynchronous thumbnail loading in 2.20), and with a complete backend rewrite, one expects that at least some of the common gripes will disappear.

The short of it is: Nautilus is actively developed upstream, doesn't really have any competition within the GNOME world, and you'll have a hard time persuading people to drop it, perhaps unless you come up with a drop-in replacement that has significant advantages.

---

### Post by The Devil Is A Squirrel on 2008-01-20
Thanks for this!

Maybe a very naiv question, but why is GNOME not more modular built-on?

---

### Post by Tibor60 on 2008-01-20
I have not have such big problems with Nautilus earlier. But now when I changed to Ubuntu 7.10... after some work and browsing with nautilus the browser can not find anything, or to identify any file. The only solution: killall nautilus in terminal.
After this command the new nautilus works 5-10 minutes and I should kill again.
I tried to reinstall nautilus, but nothing changed. Is thee any solution but go to xfce or Kubuntu? Can somebody  recommend some solution?

---

### Post by olskar on 2008-01-20
I dont think replacing nautilus is necessary, nautilus improvements is however necessary..

---

### Post by smartboyathome on 2008-01-20
> **The Devil Is A Squirrel said:**
> Thanks for this!

Maybe a very naiv question, but why is GNOME not more modular built-on?

Because they aim to be more simplistic and easy to use rather than easily customizable (that is what KDE tries to do).

---

### Post by The Devil Is A Squirrel on 2008-01-20
Well, modularity is simplicity, at least for the user. Well then I have to move to KUBUNTU when KDE 4.1 is released...  :(

---

### Post by smartboyathome on 2008-01-20
> **The Devil Is A Squirrel said:**
> Well, modularity is simplicity, at least for the user. Well then I have to move to KUBUNTU when KDE 4.1 is released...  :(

GNOME believes otherwise, and that is why some people say there is a lack of options in GNOME.

---

### Post by The Devil Is A Squirrel on 2008-01-20
I see. Well, you know, you could have the best of both worlds. Just give "advanced" users an option to configure it more than a total newbie would or a user who just don't want spend time to configure a system.

Time will show.  :)

---

### Post by CarpKing on 2008-01-20
Wait, how did we get from modularity to configurability?  The two aren't related at all as far as I can tell.  

Nautilus doesn't need replacing, however it could certainly use some improvements.  The work that is currently going on should improve some things a lot.  It would be really nice if they'd add tabs, though. And perhaps different wallpapers on each workspace.

---

### Post by The Devil Is A Squirrel on 2008-01-20
Well, in my opinion they are related. Imagine you could technically indeed replace Nautilus flawless with another file manager, but you can't do it because there is nothing where you can configure that (still speaking as a user not as a tech geek).

My idea is to give the user a choice to configure that (tick here, tick there, no terminal commands), but to achieve that GNOME would have to be more modulare, it seems. I can't tell, no developer.

However, I just installed Kubuntu and for my purpose it's way better. Much faster and way more responsitive (talking about the file manager and the desktop environment).

I'm surprised I didn't get any kicks from the community (espacially with the chosen title), on the contrary, I got some very good explanations....it seems Linux is getting major  ;)

---

### Post by amano on 2008-01-21
You can technically replace Nautilus with Thunar and still use a GTK+ program. Although Thunar lacks some features, it might be a bit speedier than Nautilus.

But just have a look how the rewrite of the Nautilus backend (GIO and GVFS instead of gnome-vfs) turns out. After some time of silence there will be a lot of development in the nautilus world now.

But let's see if the rewrite makes it into Hardy. Up until now it is not available and Sebastien Bacher doesn't seem to be too convinced of its current stability.

---

### Post by 23meg on 2008-01-21
> **aman&#305 said:**
> You can technically replace Nautilus with Thunar and still use a GTK+ program.

Not completely. You can use it as a file manager, but some integration with GNOME will be missing.

[QUOTE=amano]But let's see if the rewrite makes it into Hardy.[/QUOTE]

If it makes it into GNOME 2.22, which is Larsson's goal, it should.

[QUOTE=amano]Up until now it is not available and Sebastien Bacher doesn't seem to be too convinced of its current stability.[/QUOTE]

Where did he state this?

---

### Post by amano on 2008-01-21
> **23meg said:**
> 
Where did he state this?

AFAIR he stated that in the last Desktop meeting. He described its current state as "tricky".

I will have a look.

Edit: See this IRC log: [http://irclogs.ubuntu.com/2008/01/17/%23ubuntu-meeting.html](http://irclogs.ubuntu.com/2008/01/17/%23ubuntu-meeting.html)

> 
...
14:34	seb128	that's really the bad cycle for a lts :/
14:34	seb128	nautilus is really tricky
...
14:53	seb128	Keybuk: does the decision to use the new nautilus in hardy or not has an impact on your team work? We discussed that during the platform meeting yesterday and that's really tricky
...
14:54	seb128	gio is already in the hardy glib
14:54	seb128	gvfs should be promoted that's no issue
14:54	seb128	libgnomeui has a gio fileselector variant now
14:54	seb128	all that is alright
14:55	seb128	what is tricky is nautilus
14:55	seb128	either we keep the old non maintained code using gnome-vfs
14:56	seb128	or we switch to the new one, what all the other distros seem to do, but that's new code and everything is not ready yet
...


This is from a week ago. It seems that the final decision isn't made yet and depends on the final behaviour of Nautilus 2.22

---

### Post by 23meg on 2008-01-21
I reckon the decision will probably be made in favor of gvfs/gio if it's feature complete, since it will perhaps be hard to maintain the old GnomeVFS code for the LTS lifecycle.

---

### Post by amano on 2008-01-21
Well. That's what I hope. Even more if "the adventures in the land of policykit" ([http://blogs.gnome.org/alexl/2007/11/23/file-operations-in-nautilus-gio-and-adventures-in-the-land-of-policykit/](http://blogs.gnome.org/alexl/2007/11/23/file-operations-in-nautilus-gio-and-adventures-in-the-land-of-policykit/) ) should be integrated. THAT would be a useful feature.

---

### Post by 23meg on 2008-01-21
If you mean PolicyKit integration in Nautilus for extra privileges when needed, absolutely.

---

### Post by oomingmak on 2008-01-21
> **23meg said:**
> The main problem I see with Nautilus is its **sophisticated **codebase
That's an interesting choice of word to describe it.

---

### Post by 23meg on 2008-01-21
How would you describe it?

---

### Post by oomingmak on 2008-01-21
> **23meg said:**
> How would you describe it?
I wouldn't describe it, as I have not looked at the codebase for Nautilus.

However, I have never heard of source code referred to as "sophisticated" before, so I found it a curious description (especially given the comments that I have read about Nautilus' origin and  Eazel Inc.).

---

### Post by 23meg on 2008-01-21
What I meant was that it's intricate GObject code that's relatively hard for new contributors to grasp and start working on. The combination of GObject and C, while very powerful, is already notorious for its steep learning curve. 

I've also heard people say it's poorly commented, and/or largely uncommented, but the little I've seen of it was fine in that regard.

---

### Post by kragen on 2008-01-21
> **The Devil Is A Squirrel said:**
> Let's face it and replace it: Nautilus is totally outdated It's slow as hell and lacking in features.

Sorry, but unless you manage to mention a feature its missing, a situation where performance is lacking, or an aspect on which its outdated, I find it hard to sympathise.

---

### Post by CarpKing on 2008-01-22
> **kragen said:**
> Sorry, but unless you manage to mention a feature its missing, a situation where performance is lacking, or an aspect on which its outdated, I find it hard to sympathise.

It doesn't do tabs, it can't restore from trash, it can't display a different wallpaper on each workspace, it can't arrange the desktop icons in a grid, and the only reason you can drag and drop files to it from file-roller is because someone got fed up and ripped the code out of Thunar.  

I don't think that that's enough to justify replacing it, though, especially when such a replacement does not already exist.

---

### Post by 23meg on 2008-01-23
The gvfs-enabled Nautilus is now in Hardy.

> nautilus (1:2.21.6-0ubuntu1) hardy; urgency=low

  * New upstream version
    - Regenerate thumbnails when files change
    - Fix crashes
    - New autorun and automount support
    - Allow unmount of current location if its a mountpoint
  * debian/control.in:
    - Depends on gvfs-backends
    - updated libglib requirement
  * debian/rules:
    - updated shlibs version
	
 -- Sebastien Bacher <seb128@canonical.com>  Tue, 22 Jan 2008 10:28:34 +0000

[http://stompbox.typepad.com/blog/2008/01/gvfs-enabled-na.html](http://stompbox.typepad.com/blog/2008/01/gvfs-enabled-na.html)

---

### Post by Jay_Bee on 2008-01-23
take a look at this file-manager, is it good to replace Nautilus?
[http://pcmanfm.sourceforge.net/intro.html](http://pcmanfm.sourceforge.net/intro.html)
EDIT: of course, it should be throughly tested first to fix possible bugs.

---

### Post by amano on 2008-01-23
[https://lists.ubuntu.com/archives/hardy-changes/2008-January/005173.html](https://lists.ubuntu.com/archives/hardy-changes/2008-January/005173.html)

A look at the patches lets us know, why the new Nautilus is "tricky". Most patches had to be updated to apply to the changes, some patches had to be dropped.

It will probably take some time so sort the most annoying issues out.

---

### Post by smartboyathome on 2008-01-23
> **Jay_Bee said:**
> take a look at this file-manager, is it good to replace Nautilus?
[http://pcmanfm.sourceforge.net/intro.html](http://pcmanfm.sourceforge.net/intro.html)
EDIT: of course, it should be throughly tested first to fix possible bugs.

No, because it lacks features that nautilus has and doesn't integrage into GNOME's functions very well.

---

