---
title: "Untrusted Repositories"
date: 2006-11-11
forum: Repositories &amp; Backports
---

### Post by BLTicklemonster on 2006-11-11
Um... any of you ever seen one of these?

wtf, eh?


*EDIT:

Please note that since this thread has begun, it has been determined that the wallpaper was from Ion's, and austensibly was no threat, and Trevino's svn is clean and clear. However, there remains the question of sudoers, which is mentioned further on. There is a likelyhood that nothing whatsoever is on any of these repos that could cause real harm, then again, one never knows.

The gist of this all is, is no matter how safe and secure you know Linux is, it only takes one slip up.

---

### Post by DirtDawg on 2006-11-11
> **BLTicklemonster said:**
> Um... any of you ever seen one of these?

wtf, eh?

Is that a wallpaper? What's going on there?

---

### Post by BLTicklemonster on 2006-11-11
I used some questionable repositories while I was TRYING TO GET THAT PRETTY FLAME EFFECT IN BERYL, I guess. Anyway, as I did an upgrade, it rewrote my sudoers file, and I was not able to use sudo because I wasn't listed in sudoers. So I booted to recovery in order to edit /etc/sudoers, and once done, typed startx, and voila, that was my wallpaper.

I've since rebooted and it's gone, but that was a bit unsettling, let me tell you.

---

### Post by NeoGreen on 2006-11-11
Man, that's crazy.  I am really having a hard time understanding exactly what repositories do.  I for my self have tried to change my repositories when I wanted to upgrade to Dapper (I am still using Breezy). Sorry about asking a quesiton in your thread.  I just read it and saw what came up on your desktop and wonder if I mess with my respositories I will probably screw it up.  Did you try to update your repositories?

---

### Post by ciscosurfer on 2006-11-11
> **BLTicklemonster said:**
> I used some questionable repositories while I was TRYING TO GET THAT PRETTY FLAME EFFECT IN BERYL, I guess. Anyway, as I did an upgrade, it rewrote my sudoers file, and I was not able to use sudo because I wasn't listed in sudoers. So I booted to recovery in order to edit /etc/sudoers, and once done, typed startx, and voila, that was my wallpaper.

I've since rebooted and it's gone, but that was a bit unsettling, let me tell you.

Spooky! :neutral:  Which repo did you use?  Was it an svn beryl repo?  Do tell.

---

### Post by BLTicklemonster on 2006-11-11
Well, I was trying to get the flame effect, blah blah blah, and I used this 

[http://ubuntuforums.org/showthread.php?t=279456&highlight=beryl+svn](http://ubuntuforums.org/showthread.php?t=279456&highlight=beryl+svn)

and looked around and found Trevino's sources.list maker deb and used it.


So ah, anyone know where a feller could get them real nifty flame effects for beryl without having to change their underwear? ](*,)

---

### Post by hikaricore on 2006-11-11
roflmfao

anyone know if they fixed the plugin data package yet?

---

### Post by BLTicklemonster on 2006-11-11
> **NeoGreen said:**
> Man, that's crazy.  I am really having a hard time understanding exactly what repositories do.  I for my self have tried to change my repositories when I wanted to upgrade to Dapper (I am still using Breezy). Sorry about asking a quesiton in your thread.  I just read it and saw what came up on your desktop and wonder if I mess with my respositories I will probably screw it up.  Did you try to update your repositories?

Repositories tell your computer where to look for downloads, and when you do an update, it downloads information on what is in the sites listed in the repositories and how it is suited to the software on your computer. Editing /etc/apt/sources.list and adding repositories of dubious reliability can cause you problems. 

Now I don't know if that's just a wall paper someone at ubuntu put in to freak people out if repositories don't meet some kind of criteria, or if something from Trevino's repositories put that there.

---

### Post by d3v1ant_0n3 on 2006-11-11
Well i'm using trevino's repos for SVN Beryl, and haven't had any trouble, personally.

The plugin package that was missized/corrupted yesterday is fixed now.

---

### Post by ciscosurfer on 2006-11-11
> **d3v1ant_0n3 said:**
> Well i'm using trevino's repos for SVN Beryl, and haven't had any trouble, personally.

The plugin package that was missized/corrupted yesterday is fixed now.

Where are the fixed .deb files?  [His Edgy page still hasn't been fixed]("http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/").

---

### Post by d3v1ant_0n3 on 2006-11-11
No idea- I was having trouble with the updates yesterday (beryl-plugins-data was showing as 'mismatched size'), I ran updates later in the day and it was fixed and installed.

I've not seen any Beryl updates in the last day or so tho.

*edit* I'm on beryl-plugins-data SVN20061110-r111 if thats of any consequence

---

### Post by BLTicklemonster on 2006-11-12
When I go to do an update, using his repositories, I get this:

```
W: W: GPG error: http://ubuntu.beryl-project.org edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E


```

And I've used the keys he provides.

Not only that, but weird stuff is still happening. I had to boot to xp to talk to a freind (yahoo voice chatting still does not work in gyache) and when I came back to edgy, my fstab had been rewritten. I had to edit my mount point for edgy from /media/hdd1/ to / for some reason.

---

### Post by ciscosurfer on 2006-11-12
Yikes!  I think I may just stick to the regularly updated Beryl for now and steer clear of the bleeding edge.

And it seems like Trevino is AWOL.

---

### Post by BLTicklemonster on 2006-11-12
Here's the repository for the new Beryl

deb [http://ubuntu2.lupine.me.uk](http://ubuntu2.lupine.me.uk) edgy all
deb-src [http://ubuntu2.lupine.me.uk](http://ubuntu2.lupine.me.uk) edgy all

just add to sources.list

---

### Post by BLTicklemonster on 2006-11-12
Bloody hell, it's on my normal boot desktop now, and it's changed.

And yes, it's coming from trevino's list for sure.

---

### Post by ciscosurfer on 2006-11-12
> **BLTicklemonster said:**
> Here's the repository for the new Beryl

deb [http://ubuntu2.lupine.me.uk](http://ubuntu2.lupine.me.uk) edgy all
deb-src [http://ubuntu2.lupine.me.uk](http://ubuntu2.lupine.me.uk) edgy all

just add to sources.listThat's just a Beryl mirror, correct?  Not the lastest/greatest svn stuff, right?

> **BLTicklemonster said:**
> Bloody hell, it's on my normal boot desktop now, and it's changed.

And yes, it's coming from trevino's list for sure.And that really sucks, man!  Kinda scary, too!

---

### Post by scrooge_74 on 2006-11-12
I wonder if you have tough about changing your login passwords to something else? I have the impression that some else may know it by now

---

### Post by BLTicklemonster on 2006-11-12
I have a feeling that anything I do from here on out will be known to someone. I'm going to wipe this drive and start over. Oh, and I dual boot to xp and dapper. I can't see the drive with dapper on it, even with pysdm.

Oh, and get a load of this, they made it so that I can't change my desktop, either.

---

### Post by scrooge_74 on 2006-11-12
yep, do yourselve a favor and wipe that drive and install fresh again.  And don't use the same password you have just in case. Because if your ip address is always the same they can get to you again

---

### Post by jki on 2006-11-12
> **BLTicklemonster said:**
> I have a feeling that anything I do from here on out will be known to someone. I'm going to wipe this drive and start over.

That wallpaper in itself doesn't mean someone has hacked your computer. It's just a friendly warning. You get rid of it by 1) removing the crap from sources.list and 2) running ```
sudo apt-get install edgy-wallpapers/edgy
```

On the other hand, there's no telling what the **other** repositories in that horrible list have done to your computer. If things like sudo or kernel are replaced by some random repository that was added to sources.list because some dude's blog told to do so, that sounds worrying.

---

### Post by ubuntu27 on 2006-11-12
Man! Can we trust Linux, now>? :P

hehe. This just demonstrates that WE have to be careful about what we add in the repos, and what software we install.


I bet that scared you off. It will do to me.

---

### Post by BLTicklemonster on 2006-11-12
I've wiped it from Dapper using gparted. I'll install edgy back on it later. In the meantime, how does one go about changing a password? Of course I use the same one for Dapper as I do Edgy, so yeah, I need to change it post haste!

---

### Post by BLTicklemonster on 2006-11-12
> **ubuntu27 said:**
> Man! Can we trust Linux, now>? :P

hehe. This just demonstrates that WE have to be careful about what we add in the repos, and what software we install.


I bet that scared you off. It will do to me.

Nah, I'm cool. I'll just wait for known sources to put up repos from now on. When I ran his little program that changed my sources, I new I was probably asking for trouble. And yeah, I accept full responsibility for this happening. Perhaps nothing was done that could hurt me, but for crying out loud, if someone changes your desktop and locks you out from using it, it's high time to wipe everything out and start over, because there's no telling what else that A$$HOLE could have done. I think Trevino needs to check out his sources, though.

---

### Post by scrooge_74 on 2006-11-12
to change passwords type passwd on a terminal window

Or when installing use another password

---

### Post by scrooge_74 on 2006-11-12
> **ubuntu27 said:**
> Man! Can we trust Linux, now>? :P

hehe. This just demonstrates that WE have to be careful about what we add in the repos, and what software we install.


I bet that scared you off. It will do to me.

You can trust linux not yourselve.

Is like posting on a forum your IP, your username and passw.  Somebody will come bashing at your door soon after

---

### Post by HAARP on 2006-11-12
Before you wipe your hard drive, we should try to find out which package from which repo did this.

edit: I've got every repo you have, and I'm not willing to remove all of them just to be sure it'll be ok. We really should try to find out which one did this. Synaptic maintains a history of upgraded packages. Which ones did you upgrade right before it happened?

---

### Post by BLTicklemonster on 2006-11-12
Sorry Haarp, it's gone.

---

### Post by HAARP on 2006-11-12
So, if someone puts your house on fire, you just buy a new one and live on? Sorry, but that was a foolish thing to do :/

---

### Post by BLTicklemonster on 2006-11-12
I know that it would have been helpful to diagnose the problem for others, but my edgy is used by me as a tinker toy, though I use it primarily because it's formatted reiser fs and it's quick, and I have Dapper as my standard fall back for ubuntu when things go south and I need a way to edit files in the edgy system. For me it's a matter of time and frustration. It's easier to take it from scratch and put it back. Besides, you should have seen all the problems. Dependencies were screwed up left and right, every time I rebooted, I was hit with some new malady, etc. My tinker toy got bent, so I got a new one. Sorry, but you're on your own with this. I know that isn't helpful, and I kind of wish I'd stuck it out now so I could have helped you.

---

### Post by leech on 2006-11-12
What happened here, I think is that Trevino's repositories were hacked.  I tried to run updates today for beryl, and it kept saying that the package wasn't there, and also it was saying that the file it was looking for was in the dapper directory (I'm running edgy) and on the website, if you look at the package it should be in the edgy directory.

We could always do a apt-get source beryl and check through the source.  

I know there have been a few times that Debian's repository machine had been hacked, they took it offline, ran audits to make sure the packages weren't compromised, then put it back up about a week later.

Leech

---

### Post by jki on 2006-11-12
> **HAARP said:**
> So, if someone puts your house on fire, you just buy a new one and live on?

So, if you have mailed the keys to your house to 200 unknown people (you found their addresses from some dude's blog) and then one of them leaves a friendly message for you warning about what the others might do now that they have the key, you blame the messenger?

Not only that, you mailed them a signed contract that states they're free to do anything they ever want with your house and any property within.

If someone wanted to do something bad, she would have installed a freaking rootkit and a keylogger, or removed your files, or downloaded your files, or whatever.

Instead you got a wallpaper that informs you exactly that could be done by **any** maintainer of **any** of the 50 repositories you not only 1) added to your sources.list, but also 2) downloaded their PGP keys and 3) added them to the apt-key database (declaring "I trust this person to do whatever she wants with my computer").

---

### Post by BLTicklemonster on 2006-11-12
> **jki said:**
> So, if you have mailed the keys to your house to 200 unknown people (you found their addresses from some dude's blog) and then one of them leaves a friendly message for you warning about what the others might do now that they have the key, you blame the messenger?

Not only that, you mailed them a signed contract that states they're free to do anything they ever want with your house and any property within.

If someone wanted to do something bad, she would have installed a freaking rootkit and a keylogger, or removed your files, or downloaded your files, or whatever.

Instead you got a wallpaper that informs you exactly that could be done by **any** maintainer of **any** of the 50 repositories you not only 1) added to your sources.list, but also 2) downloaded their PGP keys and 3) added them to the apt-key database (declaring "I trust this person to do whatever she wants with my computer").

Possibly, yes, but what of the other repositories? Do we know what they might have done? [www.fraggednation.com](www.fraggednation.com) got hacked a while back, and the little $hits left a nice page in place stating it had been hacked. Do you think it was just to let the admins know they were vulnerable? I'm a bit more heavy handed than some, and when I see something compromised like that, I'll smash it. (In windows, though, I'll work my butt off to find out exactly what happened in order to save the os. Why? I don't ever fix my computer, it's always someone elses. If it were mine, I'd give it a once over, and if that didn't do it, save my files, then reinstall.)

So yeah, maybe just the wallpaper was changed, but I don't trust people, and you ought not either.

---

### Post by scrooge_74 on 2006-11-12
> **jki said:**
> So, if you have mailed the keys to your house to 200 unknown people (you found their addresses from some dude's blog) and then one of them leaves a friendly message for you warning about what the others might do now that they have the key, you blame the messenger?

Not only that, you mailed them a signed contract that states they're free to do anything they ever want with your house and any property within.

If someone wanted to do something bad, she would have installed a freaking rootkit and a keylogger, or removed your files, or downloaded your files, or whatever.

Instead you got a wallpaper that informs you exactly that could be done by **any** maintainer of **any** of the 50 repositories you not only 1) added to your sources.list, but also 2) downloaded their PGP keys and 3) added them to the apt-key database (declaring "I trust this person to do whatever she wants with my computer").

You should change the lock, the door, move the house to another state, painted in a different color, change your name, and only use paper money... LOL

---

### Post by jki on 2006-11-12
> **BLTicklemonster said:**
> Possibly, yes, but what of the other repositories? Do we know what they might have done?

Great! You understood exactly the point. The changed wallpaper never was a sign of aggression, but a friendly gesture to inform people about the dangers of dumping fifty untrusted repositories to their sources.list.

---

### Post by BLTicklemonster on 2006-11-12
Yeah, jki, I saw that post from two perspectives, but I did see your point. I'll be more careful using repositories from now on.

---

### Post by Bullwinkle_Moose on 2006-11-12
For another perspective, I'll reprise what I said in the [other thread]("http://ubuntuforums.org/showthread.php?t=265326") on this topic:

There is a discussion of this problem right on [Treviño's page]("http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/"), if you scroll down in the comments, starting with comment number 139.

Basically, the problem files are kubuntu-default-settings and possibly kubuntu-artwork-usplash. If you revert these back to version 1:6.10-61 the ominous messages should disappear.

However, it troubles me (as it apparently does some commenters) that someone would do something like this in an attempt to keep Ubuntu users in a "walled garden." This "helpful warning" could be seen by some as an attempt to start a Ubuntu "cult", where you're not allowed to seek out any information or software from outside the "cult" without fear of repercussion from within.

Whoever came up with these bogus packages needs several good swift kicks in the posterior, IMHO!

Additional comment:  I also would like to know which repository these came from - whoever operates that repository should be blacklisted by the Ubuntu community, unless they can prove they were hacked and can take steps to keep it from happening again.  But saying that users should not ever use untrusted repositories would be like telling Windows users they should only obtain software from Microsoft... in theory it might be a good idea but in practice it ain't gonna happen.

---

### Post by cjwatson on 2006-11-12
Installing particular individual packages is one thing, and is fine. Adding a huge slew of stuff to sources.list is **not** analogous to a Windows user installing some applications from somebody other than Microsoft, though; it's more like pointing Windows Update at a different source and saying that they get to replace your whole operating system. (It's possible to limit the effects of extra repositories using pinning, but it's fiddly; we (the Ubuntu developers) should probably work on making that procedure easier.)

It's possibly worth noting that Treviño didn't talk to the maintainers of all those repositories before publishing his giant list. It seems clear that at least one of the maintainers doesn't feel that his repository is suitable to be used in this way.

---

### Post by ciscosurfer on 2006-11-12
> **Bullwinkle_Moose said:**
> [...]Additional comment:  I also would like to know which repository these came from - whoever operates that repository should be blacklisted by the Ubuntu community, unless they can prove they were hacked and can take steps to keep it from happening again.  *But saying that users should not ever use untrusted repositories would be like telling Windows users they should only obtain software from Microsoft... in theory it might be a good idea but in practice it ain't gonna happen.*

That's an interesting point.  Though we should all be careful about what we use and how we use it.

---

### Post by BLTicklemonster on 2006-11-12
> **ciscosurfer said:**
> That's an interesting point.  Though we should all be careful about what we use and how we use it.

Exactly. I take full responsibility for not using trusty repos. But on the other hand, I hope Trevino is looking into this.

Let me be the poster monster for "hey stupid". :mrgreen:

---

### Post by cjwatson on 2006-11-12
I gather from this thread and discussion on IRC that a different repository (not the same one as included the changed wallpaper) causes changes to /etc/sudoers and /etc/fstab on upgrade, so the changed wallpaper has served a useful purpose as a timely warning that your system may well be broken.

It's possibly worth noting that our package management system has never really supported downgrades properly (at least not without very significant care in the maintainer scripts, which in practice developers don't generally take). Undoing whatever damage was caused here would require somebody to install everything in a sandbox, downgrade all the packages again, and then work out what changes need to be reverted manually ...

---

### Post by BLTicklemonster on 2006-11-12
Java, wine, media codecs, beryl of course, and many lib files are what I remember seeing upgraded. The lib files themselves... well, that could be anything, really.

And yes, I am thankful that the wallpaper was there! Nice wakeup call for sure, but the other problems totally spooked me. Had it only been the wallpaper with no other indication of anything being wrong, I'd have most likely stuck it out and been of more help to others. Sooo, ... under the circumstance, thank goodness for the wallpaper, huh?

I would like to make clear at this time, that my intentions in posting have been to throw up a red flag and alert people to what happened "just in case". At any time if I sounded accusatory at all, I want to clear that up. Trevino is just trying to be helpful, for sure.

---

### Post by ciscosurfer on 2006-11-12
> **cjwatson said:**
> [...]It's possibly worth noting that our package management system has never really supported downgrades properly (at least not without very significant care in the maintainer scripts, which in practice developers don't generally take). Undoing whatever damage was caused here would require somebody to install everything in a sandbox, downgrade all the packages again, and then work out what changes need to be reverted manually ...

What sort of work is being done by devs like yourself to mitigate these issues?  A new and improved, or at least updated, package management system?

---

### Post by sweener on 2006-11-12
ok i had the same problem with trevino's repo list and my wallpaper being set to the skull and not being able to change it but i believe i have fixed the issue

remove the text from /etc/gconf/gconf.xml.mandatory/%gconf-tree.xml

then gconftool-2 --shutdown

---

### Post by jki on 2006-11-12
[The Treviño Story]("http://soijabanaani.net/tmp/the_trevino_story")

---

### Post by zas on 2006-11-12
Is there a way in synaptic or apt-get to show what repository a package is coming from?  Using some of these bleeding edge repositories has got me thinking about this a lot lately.  For example, I can't find any notice in synaptic for whether the repository I added for a music player is upgrading some patched core gnome file.  I understand that it would not be ideal to limit a repository to a specific set of packages when you add it.  But what is there to stop any of the added repositories from upgrading any other package?  

If you got some notice that a repository that you added for a beryl plugin of the month build was upgrading your wifi drivers or whatever, I think that would go a long way to minimizing the damage of this kind of breach.  I'm a relative noob, so if I'm missing something here please let me know.

---

### Post by BLTicklemonster on 2006-11-12
> **zas said:**
> Is there a way in synaptic or apt-get to show what repository a package is coming from?  Using some of these bleeding edge repositories has got me thinking about this a lot lately.  For example, I can't find any notice in synaptic for whether the repository I added for a music player is upgrading some patched core gnome file.  I understand that it would not be ideal to limit a repository to a specific set of packages when you add it.  But what is there to stop any of the added repositories from upgrading any other package?  

If you got some notice that a repository that you added for a beryl plugin of the month build was upgrading your wifi drivers or whatever, I think that would go a long way to minimizing the damage of this kind of breach.  I'm a relative noob, so if I'm missing something here please let me know.

You, and only you are the one in charge of your repos. And that's the whole point. I saw that flame effect in beryl a long while back and have been itching to get it, and was looking all over when I finally found that trevino had a repo listed that would get me the new beryl. My bad, because Price Child had already posted repos in his excellent thread, I just missed them. If I'd have been patient, I'd not have had the problem.

---

### Post by leech on 2006-11-13
I'd hate to say it, but I agree with the one who made the wallpaper.  Simply put, I was wondering why the hell Trevino had that huge sources.list anyhow, generally speaking when you start getting that many third party repositories, it breaks a lot of things.  I really only wanted the Beryl-svn and the linux-restricted-modules for the new nvidia driver.  There were at least three different versions of the linux-restricted-modules within the sources.list repositories, which is just plain stupid.  There were also at least two different Frozen Bubble 2 packages, etc.  Duplicate packages from repositories is NOT a good idea in general.  

All these different repositories should actually try to combine themselves and put it on a 'experimental' server, in which people can do code audits.  Or there should be submissions to the official repositories.

This whole "Ooh, there's a scary cult that is controlling our software!" is Bull crap.  You honestly don't WANT a list of that many repositories, as already stated, you will start having far too many dependency and conflicting problems.  

Leech

---

### Post by rushin_911 on 2006-11-13
If one wants to downgrade the programs which had been updated through "untrusted repositories" then perhaps if one comments all those repositories, and then opens up synaptic and goes to status and highlight "Installed (local or obsolete)", he or she could then go through each program and library and downgrade them to edgy's version.

---

### Post by Treviño on 2006-11-13
Well... Finally I'm here...

First of all... **The wallpaper modification you've got isn't due to my repositories**. With *«my repositories»* I mean the only listed here: [http://3v1n0.tuxfamily.org/index.html](http://3v1n0.tuxfamily.org/index.html) (_those that I really built_); so what you see in that html-front end is what I really have in my repo... You only have to check!

The **author of this hack** is [J&#959;han Kiviniemi]("http://johan.kiviniemi.name/") who wanted to demostrate what everyone can do with a repository... A very known thing, but actually never (?) tested on ubuntu...

My known [Ubuntu Edgy Eft (6.10) Repository List (sources.list)]("http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/") listed his repo (I've found that on the web... So after looking what it was packaged there I added to the list also if it was a small repo)... I coulnd't know that "Ion" whould have used his space to "break" (just graphically, fortunately) the systems of the users using his repo.

The packages provided using the list above haven't made any other "damage" (I've installed all the packages provided, except the ones which made this and I've no problems; no /etc/fstab or /etc/sudoers have been edited...); so I think that we can trust on these repositories, btw anyone must always know what he does....
So, don't daemonize me, please... Just use your mind before any action... I can't know/imagine what other people have in their minds about their repositories... 

**My list is always on**, I _cleaned_ it a little, btw the majoirty of the repositories listed there are really very known in this forum (most are here...) and in the ubuntu community; as I've said ***use that at your own risk***, btw you can always use it only to see the repo available that _you_ *may* add...

And, again, *remember* that the **repositories I maintain are, and will always be, &#8220;clean&#8221;**.

---

### Post by BLTicklemonster on 2006-11-13
Thank you, Trevino. I tried to make it plain that it is my fault for plowing through without thinking, and not come across as blaming you or anyone, but I was a bit excited as it all unfolded.

---

### Post by ciscosurfer on 2006-11-13
> **BLTicklemonster said:**
> Thank you, Trevino. I tried to make it plain that it is my fault for plowing through without thinking, and not come across as blaming you or anyone, but I was a bit excited as it all unfolded.

Ah, the excitement.

@Treviño,
Was wondering where you had gone to...glad to see you're back.

A couple of questions though:[LIST=1]
[*]I'm on Edgy but used your Dapper beryl-svn .deb's...was that okay to do?  Should I revert back to Edgy .deb's now that it's back up?
[*]I seem to get artifacts on the screen (loss of cursor, square color box around cursor, etc.)...do you know how to fix this issue?  "HWCursor" "off" and/or "SWCursor" "on" don't seem to do the trick. :-k
[*]Why were your Edgy beryl-svn .deb's offline for so long?[/LIST]

---

### Post by Treviño on 2006-11-13
1. They are the same package, so... Use the dapper repo if you want; set it to edgy not to lose it on future updates (not planned but realistic)

2. Mh.. I don't know... Try asking in beryl forum or post the bug (mabybe with a screnshot) in the beryl Bug Trac

3. Have been offline? :o I had an upload problem durning the past weekend, but not more than 12 hrs I think...

---

### Post by ciscosurfer on 2006-11-13
> **Treviño said:**
> 1. They are the same package, so... Use the dapper repo if you want; set it to edgy not to lose it on future updates (not planned but realistic)

2. Mh.. I don't know... Try asking in beryl forum or post the bug (mabybe with a screnshot) in the beryl Bug Trac

3. Have been offline? :o I had an upload problem durning the past weekend, but not more than 12 hrs I think...Sounds good on all fronts.  Thanks for the reply.

---

### Post by BigWillyT on 2006-11-15
> **BLTicklemonster said:**
> I have a feeling that anything I do from here on out will be known to someone. I'm going to wipe this drive and start over. Oh, and I dual boot to xp and dapper. I can't see the drive with dapper on it, even with pysdm.

Oh, and get a load of this, they made it so that I can't change my desktop, either.

Not sure whether you already wiped and reinstalled or not but I would seriously check [this](http://www.usalug.org/phpBB2/viewtopic.php?t=22) out.  Sounds to me like you got rooted and that's why stuff keeps changing on you, especially those permissions on the Desktop.

---

### Post by raycast on 2006-11-15
> **Treviño said:**
> 
So, don't daemonize me, please... Just use your mind before any action... I can't know/imagine what other people have in their minds about their repositories... 


Treviño, I DO blame you, for encouraging users to add lots and lots of untrustworthy third party repositories to their list. You shouldn't do that, and you should espcially not *encourage* newbies to do these things. For the very reason you are stating: you can't know what other people will do.

The message for newbies is, and should always be:

**WAIT** for the Ubuntu community to verify the software to some extend and provide clean packages.

Believe it or not: you'll be able to survive without having the latest glitz. You'll be even better off without the problems you're bound to get by using these packages.

Security issues is just one thing. There is also stability (I'd count the sudoers/fstab modifications some people reported to this section) and there is reliability and ease of use (for example upgrading issues).

If you are a computer expert, and have a play machine to test software on, THEN you can probably get these third party packages to toy around with. If you don't know how to fix arbitrary errors and problems and are willing to risk losing all your data on that machine: DON'T USE THIRD PARTY REPOSITORIES. They are untrusted for a reason, you know...

Using this repository list compiled by Treviño is like having your computer auto-install all software found on CNet, Tucows and other freeware pages via windows-update.

---

### Post by BLTicklemonster on 2006-11-15
> **raycast said:**
> 

The message for newbies is, and should always be:

**WAIT** for the Ubuntu community to verify the software to some extend and provide clean packages.

Believe it or not: you'll be able to survive without having the latest glitz. You'll be even better off without the problems you're bound to get by using these packages.

Security issues is just one thing. There is also stability (I'd count the sudoers/fstab modifications some people reported to this section) and there is reliability and ease of use (for example upgrading issues).

If you are a computer expert, and have a play machine to test software on, THEN you can probably get these third party packages to toy around with. If you don't know how to fix arbitrary errors and problems and are willing to risk losing all your data on that machine: DON'T USE THIRD PARTY REPOSITORIES. They are untrusted for a reason, you know...




MEANING: the best bet for a new user is to only use synaptic package manager to install stuff. If you want something that is not listed there, check the forums, and be very careful about what repositories you add to sources... 

Now that all is said and done (for me, that is), it dawned on me last night as I was trying to get the stupid browser tabs to show back up, that .. hey, I don't give a flying rat's patootie about eyecandy anyway, wtf am I doing? 

So I removed Beryl, Emerald, and the k-somethingwhateveritis dock utility that you have to manually configure by knowing all kinds of stuff to use. Once again, a strike against Linux as far as "can this os be used by your average Joe?" is concerned. (okay, technically that's not the operating system, rather programmers who don't turn out idiot friendly packages, so it's the linux mindset that is the problem)

OT: Ubuntu is great for bringing Linux to the masses. But until developers for linux stuff realize that they need to make stuff for the common man; user friendly stuff that the average person off the street can use without someone looking over their shoulder prompting them what to do... until then, linux will always be an oddity in the eyes of the world. I know you hard core people don't get this and never will, so please, stay out of any discussion on this topic you ever see. Yes, your linux is fine the way you have it. Command lines, etc. Whoopee, go amaze your peers, you don't do anything but obfuscate the issue for those who are trying to bring a viable alternative to the masses. Please stay in your little world and let the powers that be bring Linux to the masses. I don't care if Linux is or isnt' Windows. That is not the point. The point is: for basic usability, Windows and Mac win, hands down. Now what can the linux community do to counter that? DROP THE DEPENDENCY ON THE COMMAND LINE. It's that simple. Do that, and Linux wins. 

IT'S THE GUI STUPID!

Not that I mind using the command line, but I know that will make linux sell. I know what the people I try to get to use Linux see as the problem. Never have any of my friends who use Windows or Mac ever had to use a command line or anything like it for any reason. That alone, in their eyes, is worth the price of admission. 

I should have posted that somewhere else, but we right brainers sometimes have to say it while it's on our mind. lol

G'day.

---

### Post by The Warlock on 2006-11-15
> DROP THE DEPENDENCY ON THE COMMAND LINE.

The fact that Linux has a command line capable of actually *doing* stuff is what puts it above Windows. I dunno about you, but typing in a command is a lot more "usable" to me than diving through sub-sub-submenus to find the right program shortcut. After you learn some extremely basic bash skills, using the command line is many times faster than using a GUI for most tasks, especially important system-modifying ones. Example: decompressing a tarball. 

command line:
tar -xzf whatever.tgz

GUI:
click on Places menu
click on Home Folder
wait for Nautilus to load
double-click on whatever.tgz
click on Extract icon in toolbar
click on Extract button in resulting dialog box

Now, I ask, which one of these is more "usable"? Hint: "IT'S **NOT** THE GUI, STUPID!"

---

### Post by ciscosurfer on 2006-11-15
> **The Warlock said:**
> The fact that Linux has a command line capable of actually *doing* stuff is what puts it above Windows. I dunno about you, but typing in a command is a lot more "usable" to me than diving through sub-sub-submenus to find the right program shortcut. After you learn some extremely basic bash skills, using the command line is many times faster than using a GUI for most tasks, especially important system-modifying ones. Example: decompressing a tarball. 

command line:
tar -xzf whatever.tgz

GUI:
click on Places menu
click on Home Folder
wait for Nautilus to load
double-click on whatever.tgz
click on Extract icon in toolbar
click on Extract button in resulting dialog box

Now, I ask, which one of these is more "usable"? Hint: "IT'S **NOT** THE GUI, STUPID!"Of course, right-click Extract Here works pretty good, too. 8)

But yes, the command line is *very* resourceful is you know how to use it. ;)

I think the old (or new) adage applies here: "Whatever works best for you..."

---

### Post by BLTicklemonster on 2006-11-15
> **The Warlock said:**
> 

Now, I ask, which one of these is more "usable"? Hint: "IT'S **NOT** THE GUI, STUPID!"

Looking back over my post, I think I misled you. It was not my intention to say, "remove the command line from linux and never ever ever bring it back", which is what most of you hear when someone applies logic to the question, "what is keeping linux from being mainstream", and the reply is, "the command line". In that there's an element who thinks that a gui means dropping the command line is troubling. So allow me to be a bit more concise:

In response to the age old question, "what is the biggest stumbling block keeping linux from being accepted by the mainstream?", allow me to shout from the rooftops, "IT'S THE LACK OF GUI-S TO INSTALL AND UNINSTALL PROGRAMS, YOU NINNIES" .. which translates to, "IT'S THE COMMAND LINE, EINSTEIN". Which rhymes. Which is a nice way to end.


Besides, what noob do you know who actually can state, within 8 hours of loading linux for the first time, how to use an rpm in gnome, or what a tarball is? They can wait for an installation program, don't doubt it. Some will move along and learn the command line and it's usefullness (remember, I like the command line, so don't get me wrong), and some will not. But for too long, Linux was all about the command line, wooooo, bfd.

---

### Post by The Warlock on 2006-11-15
But there *are* GUIs to install programs. Synaptic has been around for years, and graphical interfaces for .deb packages are trivial to make, and I'm pretty sure that one is already installed in Ubuntu as well (gdebi or something? don't remember the name). 

The stumbling block for most new users is that Linux is fundamentally different than Windows, whereas most people walk into it thinking that it's like a Winamp skin, and everything under the surface is the same. It's not. It will never be. There's a reason why there aren't drive letters, and programs are installed into two different folders, and packages are used instead of install excecutables, and all that stuff. New users need to be able to learn stuff about their new system if they want to use it, and that's going to be true of anything.

---

### Post by ciscosurfer on 2006-11-15
> **The Warlock said:**
> But there *are* GUIs to install programs. Synaptic has been around for years, and graphical interfaces for .deb packages are trivial to make, and I'm pretty sure that one is already installed in Ubuntu as well (gdebi or something? don't remember the name). 

The stumbling block for most new users is that Linux is fundamentally different than Windows, whereas most people walk into it thinking that it's like a Winamp skin, and everything under the surface is the same. It's not. It will never be. There's a reason why there aren't drive letters, and programs are installed into two different folders, and packages are used instead of install excecutables, and all that stuff. New users need to be able to learn stuff about their new system if they want to use it, and that's going to be true of anything.And to continue along this line of thinking, this loose analogy can be added: People drive cars everyday.  They get used to their cars.  But in the beginning, when they first start driving (either for the very first time or after buying a new car) they must get used to how the car handles.  They must adjust the drivers seat to fit their overall posture and needs.  They must learn how to drive in the rain; the braking power of their new vehicle; how much time it takes to come to a complete stop.  All of these things take getting used to.  

To further this analogy, you go from driving a car (let's call it a Taurus-XP) to driving an SUV (let's call it an OpenSourceHybrid).  Are there differences?  You bet!  Does it take getting used to?  Of course.  The same holds true with operating systems.  Do you remember when you first starting using DOS?  It took a little time to get used to, right?  Anything new (on the scene or to you and I) takes getting used to.  Once you get the hang of it, things become second-nature.

---

### Post by BLTicklemonster on 2006-11-15
> **ciscosurfer said:**
> And to continue along this line of thinking, this loose analogy can be added: People drive cars everyday.  They get used to their cars.  But in the beginning, when they first start driving (either for the very first time or after buying a new car) they must get used to how the car handles.  They must adjust the drivers seat to fit their overall posture and needs.  They must learn how to drive in the rain; the braking power of their new vehicle; how much time it takes to come to a complete stop.  All of these things take getting used to.  

To further this analogy, you go from driving a car (let's call it a Taurus-XP) to driving an SUV (let's call it an OpenSourceHybrid).  Are there differences?  You bet!  Does it take getting used to?  Of course.  The same holds true with operating systems.  Do you remember when you first starting using DOS?  It took a little time to get used to, right?  Anything new (on the scene or to you and I) takes getting used to.  Once you get the hang of it, things become second-nature.
??? dude, except for filling up the tank, the drive the same. And is what part of what percentage of what percent of the people who use computers in the world do you think know what dos even is? the command line is a very powerful tool. But when in Rome, do as the Romans do. And in the world of computing, I'm sorry to say, Windows is Rome.

---

### Post by ciscosurfer on 2006-11-15
> **BLTicklemonster said:**
> ??? dude, except for filling up the tank, the drive the same. And is what part of what percentage of what percent of the people who use computers in the world do you think know what dos even is? the command line is a very powerful tool. But when in Rome, do as the Romans do. And in the world of computing, I'm sorry to say, Windows is Rome.You must be joking :-k  There's learning curves with everything and that was the point of my last post.  And all cars don't drive the same.  Maybe I should have substituted the hybrid I listed above with a truck instead.  So now do the comparison.  Car vs. Truck.  They don't drive the same.  Never have, never will.  But the point is about getting used to something.  Whether it's a car or an operating system.  It takes time.

I couldn't tell you how many people know what DOS is.  Probably a significant number though.  Remember, and I'm sure I don't have to tell you, it was the precursor to win3.1 -- and quite honestly, is still a part of Windows as a shell to the OS and kernel.  Those of us who administer Windows machines, be they XP, Server, what have you, use the command line there -- and it's DOS.  So, not sure what else to tell you.  But I'm pretty sure we've now diverted way beyond the Untrusted Repositories idea of this thread.  The dialog is nice though.

---

### Post by BLTicklemonster on 2006-11-16
> **ciscosurfer said:**
> You must be joking :-k  There's learning curves with everything and that was the point of my last post.  And all cars don't drive the same.  Maybe I should have substituted the hybrid I listed above with a truck instead.  So now do the comparison.  Car vs. Truck.  They don't drive the same.  Never have, never will.  But the point is about getting used to something.  Whether it's a car or an operating system.  It takes time.

I couldn't tell you how many people know what DOS is.  Probably a significant number though.  Remember, and I'm sure I don't have to tell you, it was the precursor to win3.1 -- and quite honestly, is still a part of Windows as a shell to the OS and kernel.  Those of us who administer Windows machines, be they XP, Server, what have you, use the command line there -- and it's DOS.  So, not sure what else to tell you.  But I'm pretty sure we've now diverted way beyond the Untrusted Repositories idea of this thread.  The dialog is nice though.

They all drive basically the same, steering wheel in one place, pedals in the other. But I see what you mean, and yes, there are differences. I'm licensed to drive anything with wheels, and have been around the block, but they are all basically the same. Nuances, yes. Many nuances.

Anyway, I'm not advocating anything other than making it easier to install stuff. Yeah, I installed a file earlier that was an sh file, and yes, I right clicked it and let it open in the terminal, and all went well. But noobs would have been lost at that point.

---

### Post by ciscosurfer on 2006-11-16
Okay.  And I don't want to beat a dead horse, but maybe an even better analogy would be learning to drive an automatic vs. driving a stick shift or even vs. learning how to ride a motorcycle.  I think your point about nuances really hits it on the head though -- and basically what I was trying to get at. :D

I fear some admins might see that our posts should be in the Backyard, but I would disagree.  We converse on topics that are on point and ultimately relevant to our original discussion (or maybe they aren't.  I suppose it's all in how you read them) -- installing/using 3rd party repos can sometimes be risky, and should always be used sparingly and with caution.  And using them presents other problems too: how does one deal with things when they go awry.  It's a constant learning experience.  Was this whole last paragraph a stretch?  I don't really think so, at least I hope it isn't. 8)

---

### Post by BLTicklemonster on 2006-11-18
Good points, all, but I still say if there were some kind of useful interface that made sense to the common one brain cell monster type, then Ubuntu would be more accepted. Take setting up a shared folder... in windows, it's a breeze. In linux... I have yet to get it to work right. Yes, I've gotten it to work once, but it was totally wrong the way it was set up, as in: I didn't name it that, wtf is it named that for? (I can set up windows networking with ease, and do for friends who buy routers and get stuck). Oh, and dvd rip. Yep, nice interface. I have yet to get it to work. An interface in propeller-head speak is as useless as a just leaving it at the command line as far as the casual user is concerned. So it's not just the absence of gui, it's the application of gui-s also that causes problems. Yep, it's different, and I know I'll have to get used to subtle differences, but God all mighty, I want this dvd drive to be used as a source for ripping, to go to that folder and then that folder as the source when burning to go right back to that dvd drive. Yet dvdrip confounds me at every turn. (k9 copy, k3b and all work just fine, though) 

Hey, it's like playing myst or something. I need a book to figure out how to open the door, turn around twice, close the door, turn the knob three times left, one time right, walk backwards three spaces, move the book on the shelf to the desk then fart the national anthem in c flat (try that! lol) before I can open the portal leading to the dock and the next level? Like how many people would ever figure that out on their own? 5 out of a million.... nice. 

So you see what I'm saying? Nothing wrong with the command line for people who want it. It should always be there, and remain there for ever. But there are people who will use ubuntu from now on and love it, if only it were more user friendly. Which is exactly where it is heading, which is great. (so I'm basically wasting my breath, I suppose, seeing as how this will probably all be addressed soon enough anyway, I reckon)

So ah, you all have a great weekend, and for you Umercuns, happy Thanksgiving!

---

### Post by JayTee on 2006-11-19
I saw several salient points here about making linux more friendly for the masses and I also saw several good points made in posts in this thread about how all OS's have learning curve. I think Ubuntu has done an amazing job of lowering that learning curve and I expect it to only improve with future releases. The only areas I'd like to see more improvement in is in the distribution upgrade method and more rigorous testing of new releases perhaps with a slightly longer development and testing cycle. 
I work in I.T. and we run M$ Windows. XP is on all the desktops. I work with the users all the time so I have a pretty good feel for what their experience levels are and what they would accept easily vs what they would resist. I'm not feeling very optimistic about moving users to Vista if the decision is made to do so and unfortunately I have little say in the matter. My boss pushes the lastest and greatest with little regard for stability and easing the users into a new OS. Little to no grasp of the best policies and practices of I.T. in regards to migrations and testing and yet the man makes close to double what I make :-(
My users are a varied bunch but for the most part they are somewhat lazy and resistant to change so when they see Vista for the first time it's going to be difficult for them no matter how much pre-training our department does to get them all ready for it. Fortunately some of our older apps won't run in Vista well or at all so that is putting the brakes on the deployment for now. No matter how soon the call is made to move to Vista I expect a good amount of turmoil and negative feedback from the users in my workplace.

---

### Post by Bullwinkle_Moose on 2006-11-20
Okay, if you guys are going to use car analogies, let's use something more appropriate.  Going between Windows and Linux is NOT like going from a passenger car to an SUV.

Windows is like the sort of passenger car you could give your daughter and know that she will be able to use it.  It is strictly automatic transmission, with idiot lights to tell you if something is wrong, and designed to be relatively low maintenance.  Unfortunately, there's a recall notice for it about once a month, and if you ignore the recalls, very bad things can happen - in fact, someone could take control of your car remotely, and drive you places you don't want to go.

Linux is more like a race car with a highly tuned engine, stick shift, optional nitro, etc.  It is simply not something you can give the average person and expect them to use it.  Oh, sure, if you start it up for them, they might be able to drive it around the block, or even make a trip to the store.  But sooner or later, something is going to happen that neither they, nor the average camel jockey mechanic (think big box store service department) is going to be able to fix, and then they're going to be stranded.

It not a matter of which operating system is better.  Look at Betamax vs. VHS.  Better does not always win in the marketplace.  In the case of computers, it's which is more usable.  Almost anybody can use a Windows box.  Your 5 year old kid can use it.  Your grandma can use it, if her mind is still fairly sharp.  And more to the point, the guy who has clocks blinking 12:00 in his house because he can't figure out how to set them can still install and use 99% of the software packages written for Windows.

I have said it before and I will say it again, people who cut their teeth on Linux just do not realize what a big turnoff the command line is to most people.  Yes, it may be powerful, but I guarantee you that many of you will come to rue the day that you promoted the command line as the best thing since sliced bread.

Want to know why?

Because, and I hate to break this to you, but YOU are getting older.  And for many of you, the day will come that things start making less sense.  You'll start having those "senior moments", when you go out to the kitchen and then can't recall what you went there for, or when you are sitting in front of a computer screen trying to remember what the heck you were about to do.

And when you reach that point - whether it's five years from now, 25 years from now, or 50 years from now - you will suddenly realize the value of a point and click interface.  The very REASON that GUI's are so popular with most folks is because WE CAN'T REMEMBER THE DAMN COMMANDS. Linux command lines are a WONDERFUL thing for people with excellent memories and good typing skills, but not all of us are so blessed, and even those of us who have those things now may not always have them.  I'm just telling you folks, don't get so cocky about the command line, because one day you may have to eat those words, along with your morning oatmeal.

The command line is the #2 roadblock to widespread adoption of Linux, in my opinion.  Want to know what #1 is?

Shared libraries.

See, in the Windows world, when new software (or an updated version of old software) comes along, all you have to do is click on it and it will install itself.  And the reason it can do that is because most of the time, it can depend on certain core components being present in the Windows system directory.  But where there is a chance that a component might not be present, or that the software may need a particular version of that component, the component is packaged with the software and if necessary, placed in the same directory as the software.  I'm not saying there are never conflicts, but you don't get this infuriating situation which has happened to me far too many times:

Start with a program I really want to use, and hey, it's actually in the official repositories - but - it has bugs that make it nearly unusable.  Go to the software developer's site and discover that these are known bugs, and oh joy, they've been fixed in the most recent version.  And look, there's even a .deb file, which in theory means it can be installed by right clicking on it and installing it.  That joy lasts about two seconds, when you realize that there ain't no way it's going to install, because it has a bunch of dependencies that can't be resolved, since it's using newer versions of libraries than what you have.  And for me at least, that is a show stopper, because I have found that even if you can actually figure out what it's wanting, and find those libraries and install them, often it breaks existing software and sometimes even makes the entire operating system unusable.  WTF is with that?  I have actually totally destroyed a working Linux installation just trying to upgrade ONE software program to the latest version.  In the over a decade that I've been using Windows, I don't think I've ever wiped out the OS just by trying to upgrade a piece of software.

An honorable mention in the "why Linux sucks sometimes" category is the fact that multimedia software just hasn't caught up with Windows.  Of course, when you have guys waxing ecstatic over the command line, it doesn't surprise me that  multimedia isn't a high priority.  But to give an example, one program I use a lot in Windows is a very simple program called Screamer Radio.  Screamer radio does four things that, when combined in one package, make it very useful:

1) It will tune in streaming audio programs INCLUDING those that normally require Windows Media Player.
2) It will save streams to an MP3 file, so you can time shift (great for talk radio programs that come on at inconvenient times. I wish it had a built-in timer function so it could be set to start and stop recording in the user's absence, but even Windows software isn't perfect). ;-)
3) When you click the Record button during a stream you've had playing, it starts the recording five minutes BEFORE you clicked the button (not a time machine, just a five minute buffer).  Great for those "WHAT did he just say?" moments. I've used that feature on several occasions when I wasn't paying close attention and realized, after the fact, that something interesting had just been said.
4) And, it has a mute button that doesn't affect recording.  So if you want to record one program while listening to another, you can do both on the same computer.

For all the supposed versatility of Linux, show me any Linux-based program that can do all that.  This isn't rocket science, it's just combining  features in a user-friendly way.  If you could achieve the same effect in Linux, my bet is that it's not going to be nearly as easy (typing something in on the command line doesn't count as "easy").

Linux promoters just seem blind to these faults of Linux that are so obvious to any long-time Windows user.  Thing is, a lot of us really hate Windows, and especially the nagging feeling that any second some intruder is going to break into our system and do who know what sort of nasty things. We'd love to love Linux, but we just can't because it fights us ever step of the way.  I can't count the number of times I've spent HOURS trying to figure how how to do something that would have taken me 30 seconds (or at most, a couple of minutes) in Windows.  If I want a puzzle, I'll go buy a Rubik's Cube.

Oh, and then there is the "helpful" Linux community.  You know the type, you ask a question and they give you some smart-*** response like "F---in' Google it."  Well, if I had any idea WHAT to search on in Google, or which returned result (out of the 300,000 or so that Google found) I should be looking at, I wouldn't be asking. I know that in some cases these guys know the answer, but they have some mentality that says, "Nobody ever told me the answers so I'm not going to tell you", or something to that effect. At least throw me a bone, suggest some relevant search terms or maybe the title of a page or the name of a site that might contain the answer!

I'll stop here, sorry about being so long-winded, but I really wish some of you long-time Linux users would realize that one day you, too, will have to cope with declining mental abilities, and will realize that those little icons and drop-down menus are your friends, and that sometimes you need a little help to get by.

---

### Post by koenn on 2006-11-20
wow, that's a long post - I just can't resist some comments.

I remember the first time I sat in front of a Windows 95 computer. I had only seen Windows 3.1 until then. Believe me, I had no idea were to start, I couldn't find a single file, ... In Win 3.11 you had a Program Group where you could start applications, and a File Manager to get to your files. Simple, user friendly, idiot-proof. 
I did not see anything like that on the Win95 and it took my a while that with the "start" button I could start programs, one of which was called "explorer", which kinda looked like ... the File Manager. Hooray. 

The point : switching between OS's (or even just the visible part of it, the user interface) takes some getting used to. Even with windows. Microsoft knows this, and ever since win95 they've been offering the same kind of user interface, but with something added. The result is that you all your 'old' knowledge is still useful, and you gradually adjust to the newer things. 
That's where this 'I can find my way in any Windows version in 30 seconds' feeling comes from. 
Same goes for applications. Since the mid nineties, developpers of Windows applications adhere to common design principals so even in an application you've never used before, you probably find the menu options you need in the placve where you expect them. 

What does that mean ?
1- that switching from windows to ubuntu (or mandriva, or Mac, or ...) will always require some adjustment of the user. Ask someone who's been using nothing but Mac for 20 years to do something on a Windows PC, and you'll probably see the same struggle as a Windows user trying to get a handle on an Ubuntu desktop for the first time. 

2- To make it easier for new users to adjust to the new environment, some common GUI design in applications is not a bad idea. But that evolution has already started with the development of integrated desktops such as gnome and kde

Does that mean that ubuntu, or any 'linux for the masses' distro, should just try to resemble Windows as much as possible ? I don't think so. We can adpot the good things - and then preferably the underlying concept. Like : don't copy the design, but apply the design principles that make sense. 
As a slightly related anecdote:
My girlfriend uses Win XP, I use Ubuntu Dapper. When her PC broke down and she wanted to check her hotmail and do some surfing, I let her use my computer and just tolde her : here's the browser. She never new she was on a totally different system, she just wondered what 's with all that brown.
Which goes to show that ubuntu has already gone a long way towards "userfriendly Linux"

As for the "F***ing Google it" : I've answerd questions on Linux forums (other than this) about things i hardly knew about - by simple googling. Kinda makes one wonder how much research the poster did before posting his "tell me how to do this, and tell me right now". Look in this forum, and see how many times the same problem is posted. They could get the answer by searching the forum, right ? 
One of the reasons I (and probably some of those you call linux old timers)  look at forums, is to find interesting questions, and to learn about common problems and how to fix them. Things you find in google by choosing 3 adequate keywords then feel like a waste of time. But OK, that's my problem, not that of the guy who needs an answer ("RIGHT NOW")

As for the command line - I got nothing against it. Some things are easier with point and click, somethings are easier or more efficient with 1 or a few commands. Besides that, look at a few posts in the general support forum and count those that have something like "run this command and post the output" (so we can diagnose) or "you can fix this by running command so and so". Now imagene trying to handle these cases with : "do this and that, and then so and so, and post a screenshot of every window that appeared in the process, so we can see what's happening" or by posting screenshots of all relevant steps to a possible sollution. Even a textual description of the procedure to fixe it (go here, you'll see so and so, click this, then click that, now you'll see another window, etc etc etc)

But that's just a minor issue compared with this :
I've played with RedHat and Suse for a while, then started getting serious about learning Debian, and recently adopted Ubuntu as my desktop OS. I do not consider myself an expert, but I do know a couple of basic commands, and know roughly what the file system looks like and what /etc /var and /usr are.  I even had the opportunity once to diagnose a network problem by looking in de /etc/hosts file on an old SCO Unix server - no GUI there, strictly command line -, and use vi (the only text editor present on the system) to edit the file and fix the problem. 
The point : I can find my way on a Unix-like system, whatever distro, whatever GUI, no mather how the GUI has been customized, and even on a Unix without GUI,  simply because the command line is a user interface they all have in common. Doesn't that sound remarkably similar to the "I can find my way in any Windows version in 30 seconds"  mentioned earlier ? 
So, while a GUI / desktop is ok for fun and games, and the socalled "productivity applications" (Office ...), I don't think you can just dismiss the command line.

---

### Post by ciscosurfer on 2006-11-20
@Bullwinkle_Moose and @koenn,

You both make interesting points.  The dependency problems with any linux distro *can* be a pain.  But I'm not sure that detracts from an already "useable" system with "useable" apps.  If you want the latest and greatest, try something else--I guess use Windows--just know that things break in Windows too and "if they don't", you'll surely notice a slow-down at least that basically brings your system to a crawl.  Does this happen to everybody?  Probably not.  But for the vast majority of users, this has been and currently is a major deterrent and possibly a deciding factor when switching to a new OS.  Ever notice how your brand new XP runs quick right when you install it and then over the course of a few weeks, you notice things take longer to load?  I call this, and granted, not so poignantly, the 'slo-mo effect'.

As for the GUI versus Command line debate:
GUI's are nice because you're used to them and are useful and quicker (I suppose) in certain situations versus using a shell.  But the command line is more versatile and can do everything a GUI can do and more (when you know to use it correctly).  Which brings me to my next point:  The current setup with many Linux distro's makes use of GNOME or KDE or some other DE.  So, the functionality is already there in GUI glory.  Point and click away to your heart's content.  If you want to dig deeper, you can try your hand at the command line.  Sometimes (I would venture to say most of the time, if not always) diagnosing a problem, performing quick (and even very complex tasks) is/are best performed at the command line.  This debate will go on forever in the annals of linuxdom.

@@Bullwinkle_Moose,
The car analogy was a loose analogy and I made reference as such in my first post.  But the idea is sound: Things take getting used to.  I think koenn makes this point very clear.

I think your points regarding the GUI and getting older is one to take to heart and is a reasonable idea to consider as one matures in age.

You points on dependencies are well-taken.  This is a current problem with distros.  However, most users don't have a need for the latest and greatest 'whatever' and what comes with their distros is usually sufficient to get the job done.

@@koenn,
Good response all around.  Your points are expressed clearly and I agree with everything you mentioned.

As a side note: 
Discussions like these are what (in my opinion) keep the open source community alive and kickin' because they stimulate debate on issues that matter the most to us.  So, to the last two posters I say this:  Thank You!

---

### Post by glotz on 2006-11-20
Kudos for BLTicklemonster for posting this educational and fun thread.

And for J&#959;han Kiviniemi for teaching some newbies a valuable lesson and for the entertainment!

This is one of the threads I'll be showing to all the newbies I introduce to Linux.

---

### Post by Zer0Nin3r on 2007-01-15
Yeah, after reading a few posts from this thread and reading a post from PriceChild in the Easy-Ubuntu forums, I decided to uninstall Easy Ubuntu, the keys, and repositories.  Just seems like Easy Ubuntu doesn't work at all...

---

### Post by ComplexNumber on 2007-01-15
i once run a source rpm on fedora (i got it from somewhere on rpm.bone). in the terminal, it began saying things like "user David is not recognised"(or something like that), then proceded to delete everything on my hard drive before my very eyes. afterwards, i noticed that half the directories were gone from /usr. that forced a reinstall.

---

### Post by Cherry Cotton on 2007-06-14
I just read this story and I feel like, though the warning was warranted, changing people's wallpapers without their permission was immature and irresponsible, and I really hope it doesn't become somehow conventional wisdom that it's okay. Notice how people's reactions weren't, "hmmm I should probably take pragmatic solutions to improve my computer security" but rather "OMG WIPE HARD DRIVE CLEAN IMMEDIATELY!!!!"

Warning people is fine, especially when their security may very well have been compromised by another party... but when you add someone's repository to your sources list, its a show of trust, and to betray that trust by changing a user's settings without his or her permission--including to warn them of an immediate security concern--is something that absolutely should get you blacklisted from the Ubuntu community, and I'm with Bullwinkle on that.

If your credit card number is stolen, even due to your own negligence, and the card company knows about it, they have moral obligation to contact you immediately and warn you of the danger. What they shouldn't do is come to your house in the dead of night and leave a spooky message scrawled on your mirror saying "stop playing fast and loose with your credit card." Imagine if a new Ubuntu user saw the skull wallpaper... after being so proud of himself or herself for knowing how to add a long list of repositories at once, it is wise to temper that enthusiasm by pointing out to the new user the extreme dangers of signing up many repositories without checking them first. Changing his or her wallpaper without his or her knowledge or consent--_especially_ while disabling the ability to change it back--is not only immature and dangerous, it will be enough to make that new user leave Ubuntu--and Linux--forever.

Such a communiqué was warranted, but not in this form. If the message had been something polite and unobtrusive, if it had identified its source and the purpose for sending it, and if it had most certainly not changed a user's settings without the user's permission, I would most certainly support it. As it was, however, it was _vandalism_, and again, that violates a trust inherent in the repository system.

The _only way_ to maintain security of Ubuntu respositories is to make sure that any maintainer of a repository lives up to a very high standard of trust within the Ubuntu community. We're not Microsoft, we're not VeriSign, we have no centralized committee to advise newbies on which repositories are kösher and which aren't. The only way to measure the trustworthiness of a repository is how much your peers trust it.

And that's why I think that any Ubuntu repository member who thinks that he or she has the right to vandalize users' computers, especially in such an arrogant, spooky, and immature manner--even to note of an important and immediate security concern--**should be blacklisted, with prejudice, without appeal and without mercy**. Trust is so important in this community that breaching it should pay a high price. And the demonstrated belief that you have the right, under certain circumstances, to install software to change users' settings without their permission (I believe we call that "malware")--that the trust that users have given you is permission to do whatever you want with their computers--is something that should leave you, trust-wise, not only out of the community, but in a motel in a tub of ice and with no kidneys.

This maintainer installed this wallpaper on people's computers not to warn them, but to scare them, and to put them down. That's why the warning was neither polite nor respectful... there are a thousand ways he could have warned people of this impending danger and he picked the worst I can think of. To those who will inevitably argue that the message would not have gotten accross had it not been so harsh, well, the message got accross and it was "don't use Linux." I don't think that's the message we want to send.

When a user signs up for your Ubuntu repository, he or she is putting a spectacular amount of trust in you... and to betray that trust is exactly what should get you excised from the Ubuntu community postehaste. That warning contained no explanation of what it was, who sent it, or why it was there, only vague warnings to scare the crap out of the end user (mission accomplished). Worst of all, it replaced your desktop wallpaper and didn't allow you to change it back. (Yes, you _could_ change it back... if you read a specific page on the Internet telling you how to.) Our system of trust is all that protects Ubuntu users from malicious attacks... it's all we have. Breaking that trust must come with a heavy price, or that trust will mean nothing. I will never encourage a user to sign up for a repository whose owner thinks he can edit users' settings all he wants, and neither should you.

Think of the people who must have lost data in a mad rush to destroy anything they think might be compromised... users who wiped hard drives and otherwise drove themselves into a panic. Provoking that panic is something only an irresponsible maintainer would do (and provoking a panic is the wrong thing to do when warning of imminent and important security threats). And telling users its their fault for signing up for your repository is like saying its their fault for trusting you so much when you do bad things. Trust is all we have... it's how we stay secure. If you break that trust, you need to be blacklisted. Permanently.

(As for the Linux command line, I agree! The command line is wonderful and I love to use it, but when explaining complex concepts to new users, we should use the GUI whenever possible. The GUI facilitates understanding, whereas copying-and-pasting command lines is not only intimidating to new users--and dangerous for its inherent lack of context--it gives the user no idea of what he or she is doing and doesn't increase his or her confidence in his or her skills in the operating system. Seriously, if we want to see widespread Linux adoption, we need to focus on the GUI and keep the command line around, and prominent, because it's so simple and useful and extensible. I was just often frustrated as a new user to be given so many command-line instructions... it tells me _what I need to do_ to do something, but not _how_, you know?)

---

### Post by tim71 on 2007-06-14
One thing doesn't hurt anyone - at least I have update settings set to "notify only" and always check exactly what gets updated and where it is coming from. No way I would add whole this long list to my apt sources, but some of them I have already in use and doublechecking doesn't harm anyway. And even those few additional repos are used only for manual installations and are otherwise deactivated.

---

### Post by eentonig on 2007-06-15
Funny reading here.

Allthough an ancient topic, I will post my view on this matter.

I don't blame the owner from the repo that changed the wallpaper. Agreed, it's not the nicest and best way to sent out a warning. In this case, I understand him.

- He created an experimantel repo to be used by a few knowledgeable people to test out new apps (for the good of the community, because once stable, they would show up in the 'official' repo's). Since this was on his home connection, ressources are limited and I doubt he wanted hundreds off people to fill his connection. He got added to the list, without any warning or question.

Concerning the treviso list:
The way (it still is) was constructed, is a crime and I think he should be blacklisted. I see no problem in collecting that number of 'experimental' repositories. But I do object strongly in them being put in one list, with just "a warning" and stating that it's the end-users fault if things break. It would be wiser to list them one by one and explaining what is in it and why it might e beneficial to add them.

---

