---
title: "Upgrading to Hoary"
date: 2005-03-10
forum: Ubuntu Backports
---

### Post by techn9ne on 2005-03-10
I want to upgrade to hoary. Is there any scripts I have to run or anything special I have to do?

---

### Post by bored2k on 2005-03-10
[QUOTE=techn9ne]I want to upgrade to hoary. Is there any scripts I have to run or anything special I have to do?[/QUOTE]
 [http://ubuntuguide.org/#upgradewartytohoary](http://ubuntuguide.org/#upgradewartytohoary)

---

### Post by techn9ne on 2005-03-10
Well I'm specifically talking about the backports. Will they mess up the upgrade in any way?

---

### Post by TravisNewman on 2005-03-11
the SAFE way to do it is to uninstall all the backports you've installed, reinstalling them with the Warty versions, if applicable, and then dist-upgrading. When I did it, however, I saw no problems.

---

### Post by techn9ne on 2005-03-11
Well the backports were mostly trivial stuff like beep, firefox and gaim. So if they break thats ok I can fix them individually.

I tried the preview cd and was impressed so I'm gonna upgrade tonight. I'll post here any problems I encounter.

---

### Post by jsgotangco on 2005-03-11
I upgraded to Hoary today via dist-upgrade (after changing my sources). No problems so far with regards to backports. It actually is worth upgrading. Gnome 2.10 & X.org is lightning fast. Everything just worked (including the wlan) with the exception of the problem I encoutered with XMMS (freezes when playing an mp3).

---

### Post by ubuntu_demon on 2005-03-11
[QUOTE=jsgotangco]I upgraded to Hoary today via dist-upgrade (after changing my sources). No problems so far with regards to backports. It actually is worth upgrading. Gnome 2.10 & X.org is lightning fast. Everything just worked (including the wlan) with the exception of the problem I encoutered with XMMS (freezes when playing an mp3).[/QUOTE]
 change xmms to esd instead of oss :)

---

### Post by jsgotangco on 2005-03-11
yeah I was about edit the post until you replied. it now works fine but i went back to using mpg321 :)

---

### Post by jdong on 2005-03-11
I've upgraded at least 5 Backports boxes to Hoary, and I've yet to see any problem. Warty's Synaptic seems to stick, though, but without any adverse side effects.

---

### Post by RastaMahata on 2005-03-11
I have only used the backports to "upgrade" my system in warty. Should I just remove the repositories from /etc/apt/sources.list, then do apt-get update, upgrade, and that will remove the things I installed from the repos?
And THEN I should update the repositories to upgrade to Warty? I'm confused, and now I think the backports could break my installation! :(

---

### Post by jdong on 2005-03-11
Change all instances of warty to hoary, including warty-backports to hoary-backports. You'll be set.

---

### Post by techn9ne on 2005-03-11
Problem... I don't think it has to do with backports though.

I'm stuck halfway through the upgrade with a package conflict

libgtksourceview is conflicing w/ libgtksourceview-cli over a file they both use.

Its stuck. Ive tried forcing it. I cant remove the packages 'cause they have so many dependencies.

Any ideas before I have to fresh install?

 #-o

---

### Post by jdong on 2005-03-11
This sounds extremely familiar... did I not just answer a similar question?

Find the name of the .deb file from the error output -- it should start with "/var/cache/apt", then, run **dpkg -i --force-all FULL_PATH_TO_PACKAGE.deb**.

This isn't really a backports-specific issue -- Firefox and lots of KDE packages cause this error, too, during big updates.

---

### Post by techn9ne on 2005-03-12
Got past that part, upgrade went ok. I had a kernel panic and a bunch of errors so I ended up just backing everything up and reinstalling hoary preview from cd.

---

### Post by dcstar on 2005-03-12
Does anybody know how much free disk space is required for the upgrade from Warty?

I only had a small partition for my initial install.

---

### Post by ubuntu_demon on 2005-03-13
[QUOTE=dcstar]Does anybody know how much free disk space is required for the upgrade from Warty?

I only had a small partition for my initial install.[/QUOTE]
 at least 500 mb if you do it with dist-upgrade(maybe more). You can offcourse upgrade things seperately but then you increase the risk of dependencies-hell.

---

### Post by jdong on 2005-03-13
When you type in "apt-get dist-upgrade", it'll say "Need to fetch X MB of archives". You  need X MB, plus an extra 100MB or so of buffer room.

If you don't have that much, I strongly urge that you get a external drive (or mount a Samba share) over /var/cache/apt, as that's the big space hog.

---

### Post by dcstar on 2005-03-15
[QUOTE=jdong]When you type in "apt-get dist-upgrade", it'll say "Need to fetch X MB of archives". You  need X MB, plus an extra 100MB or so of buffer room.

If you don't have that much, I strongly urge that you get a external drive (or mount a Samba share) over /var/cache/apt, as that's the big space hog.[/QUOTE]
Thanks for the info, I might wait until the Hoary CD ships and use that to do the upgrade (on the assumption that it can be done that way...........).

---

### Post by ubuntu_demon on 2005-03-15
[QUOTE=dcstar]Thanks for the info, I might wait until the Hoary CD ships and use that to do the upgrade (on the assumption that it can be done that way...........).[/QUOTE]
 you can also download the cd now and upgrade that way ... and after that upgrade with the internet. But then you need the room to download the cd ... but maybe someone else can do it for you.

---

### Post by dcstar on 2005-03-16
[QUOTE=demon666_nl]you can also download the cd now and upgrade that way ... and after that upgrade with the internet. But then you need the room to download the cd ... but maybe someone else can do it for you.[/QUOTE]
I do have space on a mounted Windows partition, but I don't have enough quota on my Internet connection at the moment.......

I'll wait, I want to pass on some Ubuntu CD's to some friends anyway.

---

### Post by johndoe on 2005-03-16
[QUOTE=techn9ne]Problem... I don't think it has to do with backports though.

I'm stuck halfway through the upgrade with a package conflict

libgtksourceview is conhttp://ubuntuforums.org/newreply.php?do=newreply&p=91343#flicing w/ libgtksourceview-cli over a file they both use.

Its stuck. Ive tried forcing it. I cant remove the packages 'cause they have so many dependencies.

Any ideas before I have to fresh install?

 #-o[/QUOTE]

Sure, I had the same thing. Try removing monodevelop (which is the only app I know of which triggers this dependancy in warty and the conflict when you have backports included).[INDENT]

*     apt-get remove monodevelop*[/INDENT]

Then try it again.

---

