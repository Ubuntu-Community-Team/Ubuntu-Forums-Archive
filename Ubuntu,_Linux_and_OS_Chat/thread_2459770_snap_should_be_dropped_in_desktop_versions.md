---
title: "snap should be dropped in desktop versions"
date: 2021-03-25
forum: Ubuntu, Linux and OS Chat
---

### Post by jim-o on 2021-03-25
snap packages add a new level of administration and required knowledge. In a non-technical desktop distribution, this is unacceptable. I've been using Linux for 40 years and Ubuntu for 10 of them. When I added and tried to use Keepassxc it couldn't access my database despite the fact that the Linux file system permissions should have allowed it. I assume it's a snap package limitation of some kind. I'll be darned if I'm going to learn snap administration in order to figure out what's wrong. If Ubuntu doesn't stop using snap, I will have to change distributions, which is a major pain to say the least.

I don't want to start a flame war. If someone can  suggest another venue to more effectively communicate with the developers, please let me know.

---

### Post by QIII on 2021-03-25
This is definitely not the venue to contact the developers.  You may try [this mailing list]("https://lists.ubuntu.com/mailman/listinfo/Ubuntu-devel-discuss").

---

### Post by mikewhatever on 2021-03-25
> **jim-o said:**
> snap packages add a new level of administration and required knowledge. In a non-technical desktop distribution, this is unacceptable. I've been using Linux for 40 years and Ubuntu for 10 of them. When I added and tried to use Keepassxc it couldn't access my database despite the fact that the Linux file system permissions should have allowed it. I assume it's a snap package limitation of some kind. I'll be darned if I'm going to learn snap administration in order to figure out what's wrong. If Ubuntu doesn't stop using snap, I will have to change distributions, which is a major pain to say the least.

I don't want to start a flame war. If someone can  suggest another venue to more effectively communicate with the developers, please let me know.

There are a few things I wanted to point out:
1. The linux kernel got started in 1991, which is not 40 years ago.
2. You don't even know what the problem is, just assumed it has something to do with snaps.
3. I doubt anyone will take you seriously with this attitude.

---

### Post by CatKiller on 2021-03-25
> **jim-o said:**
> I don't want to start a flame war.

Yes, you do.

Ubuntu isn't going to stop using snaps.

---

### Post by The Cog on 2021-03-25
keepassxc is available in both apt and snap format in 20.04. Just 'sudo apt install keepassxc'. I don't know what happens if you have both the snap and the apt packaged installed, so it's probably worth uninstalling the snap version first.

---

### Post by zebra2 on 2021-03-26
Snap basically runs applications in a sandbox.  I don't use it myself but it is running on my wifes 20.04 system and she has never heard the word snap or even knows that it exists. She is a non-technical person and uses what she gets. To this end it would be irresponsible for an OS developer to provide an OS to the non-technical public that wasn't rock solid secure. Since Ubuntu seems to be the named face of Linux for the general public I can see Canonical's reasoning behind using the snap packages. A non technical user doesn't need to know anything at all. 

For myself "systemctl stop snapd" seems to work just fine. And "sudo apt-get purge snapd" works even better.  I have always run the latest development version on my computer without too many surprise reinstalls and I'm happy. I am a technical minded person. 

My wife runs default LTS Ubuntu and she is happy. 

Life is good, be happy.

---

### Post by guiverc on 2021-03-26
Any credibility was lost with the "*using Linux for 40 years*" line... 

I may have been introduced to Unix in the 80s, but many years later when Linux was created, I had a hard time considering it anything but a *toy*, and that wasn't 40 years ago.

Understanding *containerization *I consider a general basic technology knowledge step (just like cloud, it's a *modern* topic in any organizations approach to reducing the cost of IT/technology). I don't see *snaps* as needing anything beyond that general knowledge (ie. *they run in a container, thus the file-system they see is restricted and isn't the real one*).

Snaps are a *tool* that do achieve some intended goals, and does provide extra software alternatives.

I'm using a 2009 dell desktop, so my box isn't *rich* with spare resources, so I avoid *snaps* if I can, but I still find *snaps* useful as the do provide easy fixes for some problems.  My default desktop (Lubuntu) doesn't *ship* with any *snaps* installed anyway (*so any installed are my choice*).

---

### Post by DuckHook on 2021-03-27
My initial ambivalence towards snaps has gradually shifted to ambivalent usage (if that makes any sense). In an ideal world, I would still prefer that all apps reside in the highly audited, disciplined and transparent confines of the traditional repos. This practice is a huge part of what has kept Linux distros so enviably safe all these years. But I also recognize that nothing in life is ideal, and computing especially so. It's easy for me to pine after the transparency of open source code and binaries spun only out of that source, but I'm not one of the devs charged with maintaining—what?—at last count, some 20,000 pkgs?

Like the OP, I'm a beggar getting free room and board, and I have no right to make such demands. Theirs is a largely thankless grind. I can see why they are taking the position that app authors can maintain their own apps; devs have more productive things to do with their time—especially on an OS they don't charge a nickle for.

---

### Post by VMC on 2021-03-27
What surprises me, is that it took the guy over 7 years before he made his first post.
Just 'apt' remove snap, then if installs requests snap program. You'll know.

---

### Post by grahammechanical on 2021-03-27
I use the snap version of Zoom client and unlike the Linux version on the zoom web site it is kept up to date by whoever is producing the snap version. I even get some controls over permissions when I open the zoom client page in the Ubuntu software store. Oh, by the way, I have just checked and Zoom client is at version 5.6. Thank you Oliver Grawert for building and maintaining this snap. I certainly feel safer than using the Debian package version supplied by the zoom people.

[https://snapcraft.io/zoom-client](https://snapcraft.io/zoom-client)


Regards

---

### Post by MartyBuntu on 2021-03-28
I think everyone is following the lead that snaps are the culprit here...

> **mikewhatever said:**
> 
2. You don't even know what the problem is, just assumed it has something to do with snaps.


I'm with mikewhatever...I think snaps might not be the source of the problem.

---

### Post by zebra2 on 2021-03-28
I personally don't think anyone here actually cares what the culprit is. I like most will use what is convenient and comfortable. If it works I don't want to be bothered with anything new. As I have stated my wife is comfortable with what she has (snap apps) so that is what works in her case. She has no administrative roll in the matter so she doesn't know anything about this concern if there is one.  I personally like to operate on the cutting edge. I have never had a problem that a simple reinstall wouldn't fix, so I tend to not be concerned with security and the other issues reasoned for using snaps. Hence, delete. If I see a good idea on this forum I try it if I think it will move me forward. If not I go to the next topic. I don't care if the whole thing crashes on me but I want my wife's computer to be stable. Snaps have worked ok in her case.

---

### Post by mikewhatever on 2021-03-28
> **zebra2 said:**
> I personally don't think anyone here actually cares what the culprit is. I like most will use what is convenient and comfortable. If it works I don't want to be bothered with anything new. As I have stated my wife is comfortable with what she has (snap apps) so that is what works in her case. She has no administrative roll in the matter so she doesn't know anything about this concern if there is one.  I personally like to operate on the cutting edge. I have never had a problem that a simple reinstall wouldn't fix, so I tend to not be concerned with security and the other issues reasoned for using snaps. Hence, delete. If I see a good idea on this forum I try it if I think it will move me forward. If not I go to the next topic. I don't care if the whole thing crashes on me but I want my wife's computer to be stable. Snaps have worked ok in her case.

...but why move forward if the old works, and you "don't want to be bothered with anything new"? 
May I sugges an abacus insted of a computer. Also, doesn't "cutting edge" mean "new" by defenition? 

Also, next time you ride a buss, train or car, consider that horses, mules and walking work just fine.
:popcorn:

---

### Post by zebra2 on 2021-03-28
You make some good points. I like being on the cutting edge but I don't create it or decide what it will be.  I just adapt when it appears.  The problem for me with snaps is that they are packed with the dependencies that are appropriate to them when they are published and they don't change with the cutting edge.  I have used every development version of linux as my primary OS since my first installation of Ubuntu. I like instability when it shows itself.  But like I have already said I like my wife's experience to be stable. It doesn't need to be up to date. She is oblivious to what goes on here in these forums.  Regarding the abacus business, I have a degree in electronics so I don't care too much for the analog stuff.

---

### Post by grahammechanical on 2021-03-28
> The problem for me with snaps is that they are packed with the  dependencies that are appropriate to them when they are published and  they don't change with the cutting edge.

My understanding of the idea behind snaps is that it should be easier for the application developer to get an updated version of his app published. And there are different channels that the snap of the app can be published to. These are Stable; Candidate; Beta; Edge. It is a progression from low risk to a higher level of risk. 

Snaps short circuit the usual code auditing that deb packaged applications have to go through to get into a Ubuntu repository and it is usually the repositories of the next release of Ubuntu. So, to keep up to date with most deb packaged apps we have to upgrade Ubuntu even though we might be running a version that is still in life support.

There are a few exceptions to this. Firefox, Libreoffice and Thunderbird are three that come to mind.

Regards

---

### Post by cybereality on 2021-04-23
I actually like snaps. They stay updated and are less prone (or impervious) to dependency hell. 

Snaps are sand-boxed, so they don't have access to the file system by default. You can easily fix this in the GUI or command-line.

See here for how to enable read/write access on a snap: [https://ubuntu.com/blog/a-guide-to-snap-permissions-and-interfaces](https://ubuntu.com/blog/a-guide-to-snap-permissions-and-interfaces)

---

### Post by scorp123 on 2021-04-24
> **mikewhatever said:**
> 1. The linux kernel got started in 1991, which is not 40 years ago.

That caught my attention too :lolflag:

But seriously though and back to the topic: "snaps" are cool. :cool:

I was also very very sceptical at first but after running into dependency hells a few times when I tried to install software packages that were "too new" (they required lots of new libraries that were not available yet for my old installation) I gave the "snap" versions a try ... aaaaand it just worked. No dependency hell, no package conflicts, it all just works.

Since then I really started to appreciate "snap" packages more and more. They definitely have their uses.

---

### Post by TheFu on 2021-04-25
I don't like change either, especially when it breaks things that have worked for 40+ yrs. ;)
Snaps definitely have issues, especially for corporate installations that use NFS for HOME directories. Snaps don't work there. Not at all. The errors thrown are next to useless. For example:
```
$ snap list
Name    Version   Rev    Tracking       Publisher   Notes
core18  20210309  1997   latest/stable  canonical&#10003;  base
lxd     4.13      20037  latest/stable  canonical&#10003;  -
snapd   2.49.2    11588  latest/stable  canonical&#10003;  snapd
```

Great lxd is installed!
```
$ lxc list
Command 'lxc' is available in '/snap/bin/lxc'
The command could not be located because '/snap/bin' is not included in the PATH environment variable.
lxc: command not found
$ /snap/bin/lxc list
Sorry, home directories outside of /home are not currently supported. 
See https://forum.snapcraft.io/t/11209 for details.
```

```

$ echo $HOME
/u/t/thefu

$ pwd
/u/t/thefu
```
Basically, if 
a) the **getent passwd {user}** doesn't have /home/{user} 
or
b) that is NFS storage, then snaps won't ever work for the user.
Not ever. Period.

The idea that anyone local should be able to relax snap confinement to support NFS HOME directories isn't an option to Canonical.  Fortunately, flatpaks do allow local control. At the end of the day, it is a Unix Philosophy issue.  Unix is about the users being able to get work done.  For decades, users have been able to install programs into their HOME directory even if the sysadm didn't like it. Power to the users!  

Update: That came out harsher than intended. Sorry.  For a typical home user, running recent CPU with 8G+ RAM, with 3 storage devices connected to their system ....
```
/ - ssd
/home - HDD
/media/backups - external HDD
```
then snaps are nearly there for the desired goals.  When HOME directories are supported over CIFS mounts with NTFS storage on Windows, next year, I wonder what that will do for snaps.

---

### Post by grahammechanical on 2021-04-25
Remember the Ubuntu phone/tablet OS? That was supposed to eventually get something called media hub. An app that wanted to access folders and files outside of the user's home directory would get intercepted by the media hub and the media hub would in turn ask the user to authenticate the action. This is not necessary on a deb based OS but it would be a requirement on a snap based OS or to allow a snap app on a deb based OS to access folders outside its confinement. But it does not exist. May be it never will.

On the other hand. Fedora have been working on an Immutable Desktop where the system folders and files cannot be changed during run time and it will use Flatpak for confined apps. And I recently heard that Canonical is also working on an Immutable Desktop version of Ubuntu with, of course, snap apps for confinement.

This discussion sounds a little like discussions held years ago over whether it was better to make changes using the terminal or a GUI app.

Regards

---

### Post by zebra2 on 2021-04-25
I give up!  [COLOR=#000000]This discussion sounds a little like discussions held years ago about whether Ubuntu should abandon the CD install disk and switch to a DVD Install. Or abandon [/COLOR]Gnome 2 Desktop and go with Unity Desktop.  
Just for kicks I'm reinstalling and going with snaps this week when the Impish 21.10 tool chain arrives in the time space continuum. This Hirsute is getting too tame for me. Yay! Hoo! Off to the Snaps I go!

---

