---
title: "Windows Dapper"
date: 2006-06-02
forum: The Cafe
---

### Post by Brunellus on 2006-06-02
After a long absence from these forums, I thought I'd come back with some good, old-fashioned trolling.

Why must we now absolutely depend on update-manager to update to dapper?  There seems to be this idea going about that the good, old-fashioned apt way of doing things is no longer the "official" upgrade path to Dapper.

I happen to use GNOME, so I'm not fussed, but I also prefer doing things like updates/upgrades from the commandline--faster, less clutter. 

I dist-upgraded to dapper close to the *original* release date, back when it was going to be 6.04....and while the dist-upgrade was not perfect initially, it wasn't anything I didn't know how to fix.  So my questions are

What's so damn special about update-manager?

What commands is it running in the backround automagically?

---

### Post by Juanito on 2006-06-02
The point is to minimize the use of the commandline. I don't particularly like this path that Linux is taking. It's making Linux more usable to mainstream users, but it makes things too easy to be fun for geeks. And the hardcore distros like Gentoo and Slackware are way out of my league.

---

### Post by Brunellus on 2006-06-02
"fun" isn't what I'm after.  I'm after being able to accomplish stuff without having a GUI all over everything.  

It used to be that there were CLI apps, then GUI frontends.  are we now moving to GUI-everything, and screw the guys who don't want to bother with the chrome?

---

### Post by Rackerz on 2006-06-02
You don't have to absolutely depend on it, you can still use the CLI to upgrade if you wish, as far as I know anyway. The update manager just makes it easier for those of us who are abit new to Linux.

---

### Post by mostwanted on 2006-06-02
[QUOTE=Brunellus]"fun" isn't what I'm after.  I'm after being able to accomplish stuff without having a GUI all over everything.  

It used to be that there were CLI apps, then GUI frontends.  are we now moving to GUI-everything, and screw the guys who don't want to bother with the chrome?[/QUOTE]

They haven't removed apt-get, nano, sed/awk, etc. which means there's absolutely nothing stopping you from upgrading the old-fashioned way so stop complaining.

---

### Post by Rikostan on 2006-06-02
[QUOTE=Rackerz]You don't have to absolutely depend on it, you can still use the CLI to upgrade if you wish, as far as I know anyway. The update manager just makes it easier for those of us who are abit new to Linux.[/QUOTE]


Exactly.. Like Rackerz said, it's just another choice. You don't have to use it if you do not want to.

---

### Post by kanem on 2006-06-02
I was under the impression that the new update-manager was actually an improvement (though I haven't tried it). 

Everytime I've updated Ubuntu to a new version (I started with warty) I had to kill X and gdm and do it from the command line. If I didn't the whole graphical part would crap out at some point when their libraries were being removed and replaced. And like the OP said, some problems would need fixing. This includes the breezy-dapper transition.

The fact that update-manager doesn't have these problems suggests to me that it's a bit more sophisticated.

---

### Post by Dragonbite on 2006-06-02
My Ubuntu system is a general-purpose system used by the family and the GUI method makes things easier to run, plus I can possibly teach my wife how to use it.

I've done Gentoo and it was great for getting me comfortable with CLI.

---

### Post by prizrak on 2006-06-02
Brunellus, 
I don't think they are removing any CLI functionality at all. That is actually what I love about Ubuntu. It is GUI enough to be easily usable by those who are former Windows users or just plain computer novices but still keeps all the power of a hardcore Linux.

---

### Post by Brunellus on 2006-06-02
[QUOTE=prizrak]Brunellus, 
I don't think they are removing any CLI functionality at all. That is actually what I love about Ubuntu. It is GUI enough to be easily usable by those who are former Windows users or just plain computer novices but still keeps all the power of a hardcore Linux.[/QUOTE]
I am given to understand that update-manage does "extra shiny stuff" that plain old apt doesn't.  Which makes me uneasy, because I want to know how it's done from the command line.

---

### Post by rado_london on 2006-06-02
All extra hard core geeks to shut up. GUI is very good thing. You still get the CLI and users get the GUI. What the hell do you complain for?

---

### Post by Brunellus on 2006-06-02
[QUOTE=rado_london]All extra hard core geeks to shut up. GUI is very good thing. You still get the CLI and users get the GUI. What the hell do you complain for?[/QUOTE]
My complaint isn't about the hardness of my core or anybody else's.

Essentially, the word is now rapidly getting out that, while it is possible to dist-upgrade as usual, it is recommended to use the GUI upgrade manager.  When anybody asks "what makes the GUI upgrade manager so much better?" the only answers I seem to get are:

1) It's better because it's better, STFU.

and

2) It's a GUI.

Neither of which bothers to explain all the nice improvements that supposedly make it a superior method for updating.  Nor does either of the above explain what equivalent, non-GUI steps could be/have been/might be taken.

---

### Post by Kimm on 2006-06-02
A GUI is a GOOD thing!

If we ever what Linux to become mainstream anywhere other than embeded devices or servers, we Must make it more friendly for new users.

And as everyone else said, if you want to have fun, the old tools are allways there.
A GUI makes you more productive, use it.

---

### Post by Lord Illidan on 2006-06-02
A GUI doesn't have to be more productive. I too would like to know if there is any truth in these statements. If there is, I'll be extremely annoyed.

---

### Post by BoyOfDestiny on 2006-06-02
[QUOTE=Kimm]A GUI is a GOOD thing!

If we ever what Linux to become mainstream anywhere other than embeded devices or servers, we Must make it more friendly for new users.

And as everyone else said, if you want to have fun, the old tools are allways there.
A GUI makes you more productive, use it.[/QUOTE]

Agreed. I love using the CLI, but I'm glad the GUI is there and handles it. 

If you don't like the update manager, disable it:

System -> Administration -> Software Properties
Under Internet Update.

AFAIK the only difference is that it's capable of upgrading to the next release without manually changing sources.list. Although you have to pass a parameter (at least that's how it was from breezy) for it to acknowledge alpha/beta releases.

I personally did a 
sudo apt-get update && sudo apt-get dist-upgrade

It works. Hopefully it always will. 

I hope every single task gets a GUI to make it easy (in the point and click sense). 

I'm more than happy using terminal, there are many things that can be done faster. 
However, you have to know the commands and locations of files you want to manipulate, otherwise you are just parroting...
Why make a user that go to terminal, edit their sources list, then run update and dist-upgrade, I guess when they feel like checking for an update... The update manager handles it. Let it be.

---

### Post by xtacocorex on 2006-06-02
I think I read somewhere on the forums that the update-manager is set to automatically download security updates whenever they are released.

While that is nifty, I don't know if I want my computer connecting to the internet when I don't want it to.

I think Brunellus raises a valid point, I too like to know what the program does before I use it. Knowing how it (or any other OSS) does something is one of the prime reasons some of us use Linux. 

As a last resort, we could always apt-get the source package and look through it to see what it does.

---

### Post by B0rsuk on 2006-06-02
[QUOTE=Kimm]A GUI is a GOOD thing!

If we ever what Linux to become mainstream anywhere other than embeded devices or servers, we Must make it more friendly for new users.
[/QUOTE]

I think this is not only ignorant, but simply dangerous. At the moment a large part of  Linux's better security is that more knowledgeable people use it.  People with some basic technical knowledge don't fall to trojans. If people who actively resist knowledge become more common, security advantages of linux will vanish. Security is a process, not a product. I wonder how many Ubuntu users upgrade system packages. If you fail to update your system, it doesn't matter much how is it called. Breezy Badger for example has user password written in plain text in install log, (extremely critical) and you need to update to fix that.

Some very disappointing things about Ubuntu (no emphasis/not enough emphasis):
- not a single word about importance of upgrades.
- no firewall installed by default: no big deal as long as you don't have any extra network services open. But documentation doesn't mention that running some kind of server without a firewall is a security risk, and you should either continue keeping services down or use firewall.
- not even most basic info about how to debug programs (run via console). Forum is full of situations like this:
A: I click on program XYZ, cursor blinks for a while, nothing happens.
B: Run from console and paste messages here.
(Several hours later) A: (posts messages).
- not a single word justifying existence of text-based splash, or advantages of commandline interface. Many things simply can't be done with GUI, and will never be.
- no bookmark to [http://www.catb.org/~esr/faqs/smart-questions.html](http://www.catb.org/~esr/faqs/smart-questions.html) in browser. (It has to be said we'd need shortened version)

These are for your own good, really.

Linus Torvalds may be rude, I may be rude, but he got it right:
*This 'users are idiots, and are confused by functionality' mentality of Gnome is a disease. **If you think your users are idiots, only idiots will use it.***

For people with some experience, commandline interface is not only more powerful, but also faster and more convenient.

---

### Post by Brunellus on 2006-06-02
let me clarify my frustration/irritation once again:  

That there is a GUI, well, I'm not fussed about that, so long as I still have my commandline utilities.  What irritates me is the idea that the commandline way is now somehow "not recommended," and seems to be deprecated in favor of a GUI utility--which I know to be a frontend for *something*.

Well, I want to know what *something* is, and what *something* does, so that I can do it from the commandline.  Why bother?

1) The command line is quick, efficient, and clutter-free.  No bells, no whistles, no bull.  

2) I want to know what makes the utility nicer than plain old apt.

3) (selfish) I want to carry on learning about what makes my computer tick.

I'm particularly peeved that there seem to be no good answers coming up other than "it's better because it's a GUI and newbies won't be scared of it.  Also, it does neat stuff in the background that's better than plain old apt. you'll like it."

---

### Post by prizrak on 2006-06-02
[QUOTE=Kimm]A GUI is a GOOD thing!

If we ever what Linux to become mainstream anywhere other than embeded devices or servers, we Must make it more friendly for new users.

And as everyone else said, if you want to have fun, the old tools are allways there.
A GUI makes you more productive, use it.[/QUOTE]
I think you are missing the point. The biggest selling point for Linux is that it doesn't have to have a GUI like Windows and OS X and still be able to do everything. That is a huge advantage on a server since no additional resources are wasted. Having a GUI run against a CLI program is a good thing but not when the ONLY way to do it is GUI, it is especially problematic when it comes to system administration. The other issue is that I could be have installed ubuntu base and then thrown something like fluxbox on top of it w/o GNOME at all. This would mean that I do not have the update manager as it is a GNOME application. This is the problem Brunellus is talking about, if there is something that update manager does that is not doable through CLI, not that the GUI is bad.

Brunellus,
I don't think there is an actual difference between the two, possibly the only thing is not needing to edit the sources (as was mentioned earlier) other than that I don't think there is any added functionality.

---

### Post by tribaal on 2006-06-02
Your point is perfectly valid.

Isn't the GUI's "edge" over command-line only to automate stuff: instead of a user having to put up a cron job to check for updates (like I did), that can be a little intimidating for a total newbie, the update-manager takes care of it for him.

And I believe the "recommended" method is only recommended because it's a little more userproof (like you don't "risk" typos and such). And then it reminds you that you should reboot your system after a kernel update. I know I should, you probably know that too, but some users might not... :(

It's just more pretty and convenient for user lambda (like my girlfriend, my brother....), but that doesn't make it superior.

Ah well... It's like asking a WRC pilot what is best between manual and automatic gear shifts :rolleyes: 

Cheers

- trib'

---

### Post by Kimm on 2006-06-02
> 
I think this is not only ignorant, but simply dangerous. At the moment a large part of Linux's better security is that more knowledgeable people use it. People with some basic technical knowledge don't fall to trojans. If people who actively resist knowledge become more common, security advantages of linux will vanish. Security is a process, not a product. I wonder how many Ubuntu users upgrade system packages. If you fail to update your system, it doesn't matter much how is it called. Breezy Badger for example has user password written in plain text in install log, (extremely critical) and you need to update to fix that.


So your saying that a new user with the root password is any less dangerous while using the CLI? You've got to be kidding...
The ability to use the terminal doesnt mean that you are any more knowledgable about what you are supose to do and what your not supose to do.

How could possibly "next... next... next" be any more dangerous than "dpkg -i"?

If Linux distributions keep deactivating the root account by default (as aposed to Windows) there wount be much more trubble than there is today.

When your saying that we should only make Linux friendly for users with some knowledge of technology... you can just as well tell new users "Your not smart enough! Bugger off!"

Stupid users will allways be a problem with ANY OS. If you run as root in Solaris, FreeBSD, NetBSD, OpenBSD, OS X or whatever, you Allways stand a chance of getting infected, the chance is neighter smaller nor bigger than if your using Linux! But I swear on all that is holy that a system will last longer if a new user is faced by an Intuitive Graphical User Interface rather than a black screen with letters.

Unless some wacked out hardware company desides to make unique processor architetures for every single computer, Malware will ALLWAYS be an issue if a system is not handled properly.

Besides, security is just one of the advantages of Linux. Choise, freedom, price, flexibility and Stability are a couple of others.

---

### Post by Brunellus on 2006-06-02
> So your saying that a new user with the root password is any less dangerous while using the CLI? You've got to be kidding...

Not the point.  You're talking about two different types of user in two different types of environment.  The user who deals with "headless" computers (no monitors) has no use for GUIs.

I am not saying that a GUI is bad.  I am saying that *total* dependence on the GUI is bad.  In this case, it's no good for someone running a remote system.

---

### Post by B0rsuk on 2006-06-02
[QUOTE=tribaal]Your point is perfectly valid.

And I believe the "recommended" method is only recommended because it's a little more userproof (like you don't "risk" typos and such). And then it reminds you that you should reboot your system after a kernel update. I know I should, you probably know that too, but some users might not... :(
- trib'[/QUOTE]

The other side of the story is that if you describe only GUI way of doing something, you
1....essentially need N versions of the guide, where N is number of window managers  . Have fun writing separate guides for Ubuntu, Kubuntu, Xubuntu. Commandline just works.
2....by learning the GUI only, you become addicted to one linux distribution and can't switch later. While Ubuntu may not take the path of Red Hat, it's still something to consider.  
You may come in contact with another distribution in a friend's home, at work, on university, on a device like laptop etc. You may not be able to use it at all if you stick to GUI. Linux is about choice, people use various software.
3. If all you know is GUI, you basically have to reinstall system (!) each time you break your xorg.conf configuration. This can happen when installing new kernel, graphics driver etc... and now I hear Dapper does these things automatically by default.

---

### Post by Kimm on 2006-06-02
> 
I am not saying that a GUI is bad. I am saying that *total* dependence on the GUI is bad. In this case, it's no good for someone running a remote system.


There we agree. But I never said that the CLI shoud be completely replaced. What I am saying is that there should be an alternative for new users.

I too find the CLI very usefull, but this was something I had to learn as I went along, and I am sure more people will notice this in the future. The GUI should always be there as a choise, for those new users that are just getting aquainted with the system.

> 
The other side of the story is that if you describe only GUI way of doing something, you
1....essentially need N versions of the guide, where N is number of window managers . Have fun writing separate guides for Ubuntu, Kubuntu, Xubuntu. Commandline just works.


But its just that the CLI wount dissapere, its a great part of the UNIX world and even if a user doesnt know how to use the terminal you can still tell him to "type this into that black box"

---

### Post by Brunellus on 2006-06-02
> 
I too find the CLI very usefull, but this was something I had to learn as I went along, and I am sure more people will notice this in the future. The GUI should always be there as a choise, for those new users that are just getting aquainted with the system.

update-manager (until someone points me to the relevant info, and I'll stfu) is different.  It allegedly does "better things" than a plain vanilla dist-upgrade...but nobody seems to want to tell me what it does do.  So until I find out, the command line is not a choice.  Or, if it is, it's a secondary, disfavoured choice, which vexes me.

---

### Post by Kimm on 2006-06-02
I dont know what the update-manager does better than a plain dist-upgrade (I too did this).

But I can imagine that perhaps it fixes broken packages? I know that some packages had changed names when I dist-upgraded to Dapper and that gave me some trubble.

---

### Post by imagine on 2006-06-02
[QUOTE=B0rsuk]Breezy Badger for example has user password written in plain text in install log, (extremely critical) and you need to update to fix that.[/QUOTE]
Of course Ubuntu 5.10 had security flaws, as every other GNU/Linux distribution. However I disagree that the mentioned flaw is "extremely cirtical" [1].

[QUOTE=B0rsuk]- no firewall installed by default[/QUOTE]
No matter how often this myth will be repeated it won't make iptables go away. A firewall *is* installed by default.

[QUOTE=B0rsuk]But documentation doesn't mention that running some kind of server without a firewall is a security risk[/QUOTE]
Because it isn't.
Of course it depends what you actually try to accomplish. However when you set up a daemon you usually *want* other people to be able to connect to it, so you won't tell your kernel to block them.

[QUOTE=B0rsuk]Many things simply can't be done with GUI, and will never be.[/QUOTE]
True. Also many things can't be done with the CLI and will never be.
Now what? =)

[QUOTE=B0rsuk]no bookmark to [http://www.catb.org/~esr/faqs/smart-questions.html](http://www.catb.org/~esr/faqs/smart-questions.html) in browser.[/QUOTE]
Thats just my take: This article is an ignorant and arrogant POS. Something I don't want to see in an Ubuntu installation.



[1] [http://www.ubuntuforums.org/showpost.php?p=825310&postcount=152](http://www.ubuntuforums.org/showpost.php?p=825310&postcount=152)

---

### Post by NeoChaosX on 2006-06-02
I think the gist of it is that update-manager also updates the system so that the shiny new features and or configuation for those features are enabled and set up by default. When you do a dist-upgrade from breezy, it simply upgrades your packages, it doesn't set up any of the new features from the new version (which owuld be enabled on a fresh install of Dapper). As an example, my friend tried upgrading his Breezy install to Dapper, but after the upgrade, some functions (like Firefox plugins) were horribly broken because many of the old Breezy config files and directories, especially the ones in his home directory, were still around. Had we gone with update-manager rather than a plain dist-upgrade, I think his transition would've gone  a bit smoother.

---

### Post by kanem on 2006-06-02
[QUOTE=Brunellus]update-manager (until someone points me to the relevant info, and I'll stfu) is different.  It allegedly does "better things" than a plain vanilla dist-upgrade...but nobody seems to want to tell me what it does do.  So until I find out, the command line is not a choice.  Or, if it is, it's a secondary, disfavoured choice, which vexes me.[/QUOTE]
I also believe it does "better things" from personal experience and anectodal evidence. Unfortunately I don't know how the backend works, or how to do it from the command line, and probably no one else does here either. You might have better luck by emailing the developers.

---

### Post by Brunellus on 2006-06-02
[QUOTE=NeoChaosX]I think the gist of it is that update-manager also updates the system so that the shiny new features and or configuation for those features are enabled and set up by default. When you do a dist-upgrade from breezy, it simply upgrades your packages, it doesn't set up any of the new features from the new version (which owuld be enabled on a fresh install of Dapper). As an example, my friend tried upgrading his Breezy install to Dapper, but after the upgrade, some functions (like Firefox plugins) were horribly broken because many of the old Breezy config files and directories, especially the ones in his home directory, were still around. Had we gone with update-manager rather than a plain dist-upgrade, I think his transition would've gone  a bit smoother.[/QUOTE]
that's the first good clue I've gotten...ever. 

Now, I wonder when that'll be doable from the commandline.

---

### Post by skunkpit on 2006-06-04
its good to have diversity in the open source community

but i dont like how there are inner wars of this distro vs this distro and linux vs bsd
they all have advantages and disadvantages

in general there really are too many egotistical people out there
people always thinking of "the future of an os"
it doesnt matter
its good to have choice i say we need more bsd distros and more linux distros
people who dont like an os, learn about others and switch

hence getting the hell away from microcrack

shouldnt really be in ubuntu forums complaining about not enough command line
when its always consist in pretty much every linux distro

i started with slackware then moved to gentoo then gave ubuntu a try

gentoo i must say is the fastest distro iv used to date and portage is pretty rock solid
it wasnt hard to install either, my first time i printed out the instructions and in a few hours or so had a system fully loaded with everything i need
not as fast as binary obviously but good things come for people who wait

i introduce people to linux through ubuntu or damnsmall linux, most of the time they go learn about other distros in time

USE="cannabis -religion -politics" emerge world
..if only

---

### Post by shamrock_uk on 2006-06-04
[QUOTE=Brunellus]that's the first good clue I've gotten...ever. 

Now, I wonder when that'll be doable from the commandline.[/QUOTE]

I thought it already was - I've done a dist-upgrade on a couple of computers and I was asked on numerous occasions whether I wanted to keep old configs or use the new ones - use the new ones every time and I think you reach the same result. 

The update manager really chokes whenever there are non-reachable apt sources though. It'll never be more functional than the good old-fashioned command line. 

And @whoever said it - the documentation *does* refer to the importance of updates. Whenever you click on the update manager (which a new user will when updates are available) you're given a couple of sentences about how updates protect your computer and add new features.

---

### Post by christhemonkey on 2006-06-04
The great thing about open source is, 

that if you want to know how program x (update-manager in this instance) works,

you can grab the source and have a look!

---

### Post by prizrak on 2006-06-04
[QUOTE=skunkpit]its good to have diversity in the open source community

but i dont like how there are inner wars of this distro vs this distro and linux vs bsd
they all have advantages and disadvantages

in general there really are too many egotistical people out there
people always thinking of "the future of an os"
it doesnt matter
its good to have choice i say we need more bsd distros and more linux distros
people who dont like an os, learn about others and switch

hence getting the hell away from microcrack

shouldnt really be in ubuntu forums complaining about not enough command line
when its always consist in pretty much every linux distro

i started with slackware then moved to gentoo then gave ubuntu a try

gentoo i must say is the fastest distro iv used to date and portage is pretty rock solid
it wasnt hard to install either, my first time i printed out the instructions and in a few hours or so had a system fully loaded with everything i need
not as fast as binary obviously but good things come for people who wait

i introduce people to linux through ubuntu or damnsmall linux, most of the time they go learn about other distros in time

USE="cannabis -religion -politics" emerge world
..if only[/QUOTE]
I suggest you read the thread before replying. The issue is that it is not clear what the GUI program (update manager) does that CLI (apt-get dist-upgrade) cannot. Due to that there was a question as to whether it is possible to do the same in the CLI and in this case it should be doable through CLI, simply because remotely administrated machines also need to be upgraded and most remote administration is done through the CLI for obvious reasons.

---

### Post by skunkpit on 2006-06-05
i know..

---

### Post by Brunellus on 2006-06-05
[QUOTE=christhemonkey]The great thing about open source is, 

that if you want to know how program x (update-manager in this instance) works,

you can grab the source and have a look![/QUOTE]
...which presupposes source-literacy from all users.  If that were so, we'd all be using LFS, and there would be no irritation, no RTFM posts, and we would live peacably in the brotherhood of man.

It ain't so.  I'm a user.  I'd like to think that I'm a fairly knowledgable user.  But I'm only that:  a user.  I have no development or programming experience.  Simply apt-getting the source package and grepping through it teaches me almost nothing, because I don't even know where to begin.

I can hear it now "well, fscking learn already!"  Well, what. My patience is finite as is my time.

---

### Post by sumadartson on 2006-06-05
Brunellus, definitely agreeing with you with regards to this issue.  I got exactly the same feeling from using the update-manager. I felt kind of dirty doing an upgrade from the GUI, while not knowing what was going on beneath the hood and why I wasn't using a CLI.

The main reason for using linux for me is that I feel in control of *my* computer. While update-manager is a great tool, the obscurity of its advantages and lack of a CLI equivalent take some of this feeling away.

In addition, women like a man who knows his way around the CLI. Trust me, it's manly. And, speaking from my own experience, every guy I know likes a geeky girl, myself included.

BTW, not starting a flame war here, but that Torvalds quote regarding KDE vs GNOME just reeks of arrogance. I'll take GNOME+CLI over the cluttered mess that is KDE any day.

---

### Post by pmj on 2006-06-05
[QUOTE=sumadartson]In addition, women like a man who knows his way around the CLI. Trust me, it's manly. And, speaking from my own experience, every guy I know likes a geeky girl, myself included.[/QUOTE]
So in other words, you like your women manly?

---

### Post by ssam on 2006-06-05
[QUOTE=Brunellus]After a long absence from these forums, I thought I'd come back with some good, old-fashioned trolling.

Why must we now absolutely depend on update-manager to update to dapper?  There seems to be this idea going about that the good, old-fashioned apt way of doing things is no longer the "official" upgrade path to Dapper.

I happen to use GNOME, so I'm not fussed, but I also prefer doing things like updates/upgrades from the commandline--faster, less clutter. 

I dist-upgraded to dapper close to the *original* release date, back when it was going to be 6.04....and while the dist-upgrade was not perfect initially, it wasn't anything I didn't know how to fix.  So my questions are

What's so damn special about update-manager?

What commands is it running in the backround automagically?[/QUOTE]

the main advantage of the upgrade to dapper with the update manager seems to be that it automatically updates your /etc/apt/source.list. i think it make sure that ubuntu-desktop is installed. then runs a dist-upgrade.

if you are happy to do those manually, then thats fine. you'll get the same result. (unless the update manager treats packages' recommends differently (a package can recommend or depends on another package)).

some one commented that a dist-upgrade will not get the new features, but only update installed packages. thats not true. a 'apt-get upgrade' will do that. (there a more details in man apt-get). you must have the ubuntu-desktop package installed to get newly introduced packages though, as it depends on the packages that make up a standard install.

i think a lot of people are not that comfortable with editing test files. and you can get in a mess if you make a syntax error in a config file. i have had to use live cds to recue systems after making mistakes in system files.

you comment that the command line is faster than the gui. in some cases i think thats because the gui is not good enough. even when it is faster it is far less discoverable. the habbit of new users typying in commands from untrust worthy websites is potentially a huge security risk. good gui tools could make linux safer.

it would be a sad day if the command line tools went away. but it would be a good one if people only needed to use them if they wanted to.

---

### Post by sumadartson on 2006-06-05
> So in other words, you like your women manly?

Next time, I should think before I write. Really, I'm making a fool of myself :D.

---

### Post by G Morgan on 2006-06-05
I think there is a lot of misunderstanding in this thread:

The OP is not complaining that a GUI exists only that it potentially has extra undocumented functionality over the CLI.

From my experience. I used dist-upgrade to get from 5.10 to 6.06 and it worked perfectly. The only difference (that I can see) is that via the CLI it asks for confirmation before blitzing old config files (while recommending against it, I feel this is why they recommend using update-manager for new users who'd otherwise be stuck with 5.10 config files).

There is no argument here (though the smart questions page does need toning down, the same information can be passed on without the arrogance and would be far more useful to the end user and the RTFM crew). The CLI works almost exactly like the GUI except the GUI forces updates of config files giving you less control.

---

