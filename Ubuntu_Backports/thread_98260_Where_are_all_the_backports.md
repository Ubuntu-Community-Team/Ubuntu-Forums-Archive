---
title: "Where are all the backports?"
date: 2005-12-02
forum: Ubuntu Backports
---

### Post by btdown on 2005-12-02
Are they still held up or ? I dont see hardly anything released....

---

### Post by btdown on 2005-12-06
still waiting....

---

### Post by carlosqueso on 2005-12-06
They are working for me....a lot of behind the scenes stuff, and a new kernel.  Almost every day there's something from backports when I apt-get upgrade.   I don't think there's any special indication of whether or not new packages come from backports or the others.  Have you not gotten anything?

---

### Post by btdown on 2005-12-06
Not really..I get something every few days, but its all minor stuff, nothing big like the new VLC, gtk2 mplayer and other cool updates that Im looking for.
 
I liked backports better the old way...

---

### Post by macleod199 on 2005-12-07
[QUOTE=carlosqueso]They are working for me....a lot of behind the scenes stuff, and a new kernel.  Almost every day there's something from backports when I apt-get upgrade.   I don't think there's any special indication of whether or not new packages come from backports or the others.  Have you not gotten anything?[/QUOTE]

If you're getting new kernels it's either from security (which I don't think has happened yet), or you're using the Dapper repositories themselves.

---

### Post by duffman25 on 2005-12-07
[QUOTE=macleod199]If you're getting new kernels it's either from security (which I don't think has happened yet), or you're using the Dapper repositories themselves.[/QUOTE]

There seems to be some lag between the aproval of backports and the actual build of the package in the archives. I'm still waiting for some packages which are already aproved.

you can check here: [http://packages.ubuntu.com/breezy-backports/allpackages](http://packages.ubuntu.com/breezy-backports/allpackages) for updates/changes in the backports archive

---

### Post by btdown on 2005-12-07
> There seems to be some lag between the aproval of backports and the actual build of the package in the archives.
 
Exactly my point! Since this new process doesnt seem to be working, can we start the discussion of possible alternatives, or going back to the way it was? 
BT

---

### Post by carlosqueso on 2005-12-07
[QUOTE=duffman25]There seems to be some lag between the aproval of backports and the actual build of the package in the archives. I'm still waiting for some packages which are already aproved.

you can check here: [http://packages.ubuntu.com/breezy-backports/allpackages](http://packages.ubuntu.com/breezy-backports/allpackages) for updates/changes in the backports archive[/QUOTE]

It could be security....I like working with my computer too much to mess with Dapper yet, or any of the Debian repos.  I dunno, doesn't bother me.

---

### Post by duffman25 on 2005-12-07
[QUOTE=btdown]Exactly my point! Since this new process doesnt seem to be working, can we start the discussion of possible alternatives, or going back to the way it was? 
BT[/QUOTE]

A simple solution is to give access to the main archive to jdong & the other people in the backport team. That would make the backports work like it used to work.

---

### Post by duffman25 on 2005-12-08
[QUOTE=duffman25]A simple solution is to give access to the main archive to jdong & the other people in the backport team. That would make the backports work like it used to work.[/QUOTE]

Any news on why the backports are coming to the archive so slow?

---

### Post by shidai.liu on 2005-12-08
This renders backport close to useless.

---

### Post by jeremy on 2005-12-09
I have looked at
[http://packages.ubuntu.com/breezy-backports/allpackages](http://packages.ubuntu.com/breezy-backports/allpackages)
and see lots of tasty looking packages there, but where can I download them from?

---

### Post by arpunk on 2005-12-09
You can download the .deb directly from that site, read at the end of the page where it says *download*.

---

### Post by ember on 2005-12-09
Try adding:

#backports
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted
#deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports-staging main universe multiverse restricted

#backports-extras
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras-staging main universe multiverse restricted

to your sources.list. That works for me.

---

### Post by jdong on 2005-12-12
Guys, please try to be patient....

---

### Post by duffman25 on 2005-12-12
[QUOTE=jdong]Guys, please try to be patient....[/QUOTE]
We try to ;)

Thanxs for keeping us up to date with this issue.

---

### Post by jdong on 2005-12-12
Typically, James since Breezy has loved to approve 20 backports at a time, usually on a monthly/bi-monthly schedule. Either way, I'll continue to send requests to him, and if it gets too ridiculous I'll start complaining.

---

### Post by duffman25 on 2005-12-13
[QUOTE=jdong]Typically, James since Breezy has loved to approve 20 backports at a time, usually on a monthly/bi-monthly schedule. Either way, I'll continue to send requests to him, and if it gets too ridiculous I'll start complaining.[/QUOTE]

Wouldn't it be better if someone gave you upload rights to the backports archive? Once the whole main/backport teams agree a certain backport is suitable to be added? Maybe it could be brought to a CC meeting. Backports are a very valuable proyect for ubuntu and it was running better when it was a totally community driven proyect than now when it became a officiall proyect.

Anyway... my 2€.

---

### Post by Velvet Elvis on 2005-12-13
I think I liked it better when backports was unofficial as well.  I'm building a lot of my own packages as they come out for dapper now, but I can't do that with all of them, mostly because I'm on dialup and downloading all that source on a regular basis is out of the question.

The think I like least about debian is the beurocracy that comes with it.  Unfortunately, that's a part of the debian lineage that Ubuntu hasn't managed to shake yet.  There is absolutely no reason for "testing" packages to not be available within a week or so of an upstream update.  Apt-get and dpkg kick ass but are useless without packages to install.  I'm real close to going back to slackware and running bleeding edge packages and libraries without package management.

---

### Post by jdong on 2005-12-13
If you guys want, continue pressing James to do faster Backporting -- in the Hoary days, he was very responsive (<24hrs). Severing Canonical ties and becoming unofficial again is not a possibility that I'd want to pursue, but if things continue to be this bad I may start doing unofficial packages or granting SF.net upload access for a few more people around here.

---

### Post by jdong on 2005-12-13
[http://ubuntuforums.org/showthread.php?p=570804#post570804](http://ubuntuforums.org/showthread.php?p=570804#post570804)

Continue discussion in duplicate thread.

---

