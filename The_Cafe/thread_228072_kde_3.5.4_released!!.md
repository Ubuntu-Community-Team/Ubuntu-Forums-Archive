---
title: "kde 3.5.4 released!!"
date: 2006-08-02
forum: The Cafe
---

### Post by TheRingmaster on 2006-08-02
This is another building block to kde 4. [http://www.kde.org/announcements/announce-3.5.4.php](http://www.kde.org/announcements/announce-3.5.4.php)

(when will this be available with kubuntu?)

---

### Post by arizonagroovejet on 2006-08-02
There are Kubuntu packages already but they have a bug and hence are not recommended for use. For details see

[http://ubuntuforums.org/showthread.php?t=227777](http://ubuntuforums.org/showthread.php?t=227777)

---

### Post by Rackerz on 2006-08-02
3.5.4 wont be added to the repositries will it?

---

### Post by Jucato on 2006-08-02
New  versions of KDE, Amarok and KOffice are never included into the main repositories. I don't know why.

Oh, and if it hasn't been said enough: 
**DO NOT upgrade to KDE 3.5.4 *yet***

:D

---

### Post by NeoChaosX on 2006-08-02
> **Fenyx said:**
> Oh, and if it hasn't been said enough: 
**DO NOT upgrade to KDE 3.5.4 *yet***

:D
Yeah, I learned that the hard way. :p

---

### Post by Jucato on 2006-08-03
KDE 3.5.4 is **officially** available in Kubuntu.

[http://www.kubuntu.org](http://www.kubuntu.org)

Since it has been added to the front page, and RSS feeds have been sent, it's presumably safe to upgrade now.

---

### Post by TheRingmaster on 2006-08-03
You need a key to get it.

this is how you get it
```
wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg
 sudo apt-key add kubuntu-packages-jriddell-key.gpg
```

---

### Post by emuman on 2006-08-03
I upgraded to 3.5.4 yesterday. Today an apt-get upgrade holds the following packages back:
kdelibs, kdelibs4-dev and kdelibs4c2a. 
kdelibs4c2a cannot be installed because it needs libcupsys2 >= 1.2.1

---

### Post by golfbuf on 2006-08-03
> **emuman said:**
> I upgraded to 3.5.4 yesterday. Today an apt-get upgrade holds the following packages back:
kdelibs, kdelibs4-dev and kdelibs4c2a. 
kdelibs4c2a cannot be installed because it needs libcupsys2 >= 1.2.1

It seems ok here (using kubuntu.org/packages/kde-354), so maybe you just tried before it was fully uploaded or synced.

---

### Post by Kimm on 2006-08-03
I can also report that it works here.
Although I had to reconfigure Fonts (antialiasing was gone for some reason), but that was easily done in the control center

---

### Post by givré on 2006-08-03
> **emuman said:**
> I upgraded to 3.5.4 yesterday. Today an apt-get upgrade holds the following packages back:
kdelibs, kdelibs4-dev and kdelibs4c2a. 
kdelibs4c2a cannot be installed because it needs libcupsys2 >= 1.2.1
libcupsys was update with dapper-update. Check that you have dapper-update enable, or show your /etc/apt/source.list

---

### Post by TheRingmaster on 2006-08-03
why didn't I get the update yet?

I am on the us update servers.

here is MY sources.list

> 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe 
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) kubuntu main 


---

### Post by croak77 on 2006-08-03
> **jpazindustries said:**
> why didn't I get the update yet?

I am on the us update servers.

here is MY sources.list

Cause it's on a Kubuntu repo not Ubuntu.

[http://kubuntu.org/announcements/kde-354.php](http://kubuntu.org/announcements/kde-354.php)

---

### Post by TheRingmaster on 2006-08-03
I had a little trouble at first with adept but now i am fully updated. My fonts were messed up after I updated to 3.5.4 but i fixed it. the problem was that the upgrade turned off subpixel hinting. other than that everything went cool.=D>

---

### Post by arox on 2006-08-04
When i try to upgrade Synaptic wants to remove the kdelibs-bin package... is it safe?

---

### Post by Jucato on 2006-08-04
yes. kdelibs-bin is replaced by kdelibs4c2.

---

### Post by Terracotta on 2006-08-04
KDE 3.5.4 up and running, and wel woooooooow ;-) me like it :p. Although the new amarok version (1.4.x not on that repo) doesn't seem to be able to play flac files :|.

---

### Post by Jucato on 2006-08-04
The problem of Amarok 1.4.1 not playing FLAC files has been there ever since Amarok 1.4.1 has been released. AFAIK, this was due to some problems between Amarok and Xine.

Frankly I'm disappointed that it hasn't been solved until now. There are other ways to work around it, mostly compiling a new libxine/xine-lib. But shouldn't the solution come from the devs/maintainers?

---

### Post by Terracotta on 2006-08-04
> **Fenyx said:**
> The problem of Amarok 1.4.1 not playing FLAC files has been there ever since Amarok 1.4.1 has been released. AFAIK, this was due to some problems between Amarok and Xine.

Frankly I'm disappointed that it hasn't been solved until now. There are other ways to work around it, mostly compiling a new libxine/xine-lib. But shouldn't the solution come from the devs/maintainers?

Yup I agree here, I just wonder why they don't create a multimedia repository that contains for example: new amarok and amarok-xine, xine, kaffeine and kaffeine-xine and kaffeine-mozilla perhaps.
Since kaffeine isn't part of KDE and has a different release schedule as well. But ha I'm just happy Kaffeine 0.8.1 is in the new KDE repos :p so I'm not complaining ;-).

---

### Post by l.capriotti on 2006-08-04
I''m not able to upgrade:

l.capriotti@ubuntu:~$ sudo apt-get update
( ... )
l.capriotti@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  kaudiocreator: Depends: kdemultimedia-kio-plugins (= 4:3.5.3-0ubuntu0.1) but 4:3.5.4-0ubuntu2~dapper1 is installed
  konqueror: Depends: kcontrol (= 4:3.5.4-0ubuntu1~dapper2) but 4:3.5.3-0ubuntu0.2 is installed

Any hints?

Cheers
Luigi

---

### Post by Jucato on 2006-08-04
> **Terracotta said:**
> Yup I agree here, I just wonder why they don't create a multimedia repository that contains for example: new amarok and amarok-xine, xine, kaffeine and kaffeine-xine and kaffeine-mozilla perhaps.
Since kaffeine isn't part of KDE and has a different release schedule as well. But ha I'm just happy Kaffeine 0.8.1 is in the new KDE repos :p so I'm not complaining ;-).

Both Amarok and Kaffeine are part of KDE Extragear ([http://extragear.kde.org/)](http://extragear.kde.org/)), a collection of KDE apps associated with KDE, but not part of KDE main, but still a part of KDE. But since Amarok is quite popular, it has its own repository in Kubuntu whenever a new version is released. The Kubuntu Amarok repository does contain amarok-xine ([http://kubuntu.org/packages/amarok-141/pool-dapper/)](http://kubuntu.org/packages/amarok-141/pool-dapper/)). 

libxine, however, is quite a different story. It would be quite inappropriate it put it under just Amarok or a general  repository, since xine is also used by other non-multimedia apps, for example in notifications and system sounds.

That being said, I heard that the solution to the problem with FLAC support in Amarok 1.4.1 simply involves compiling the latest xine-lib/libxine. And it seems to me that there have been no side effects with that workaround. So I'm quite baffled why it's taking the appropriate devs/maintainers this long to come up with a patch.

@l.capriotti: try sudo apt-get dist-upgrade ?

---

### Post by givré on 2006-08-04
> **Fenyx said:**
> Both Amarok and Kaffeine are part of KDE Extragear ([http://extragear.kde.org/)](http://extragear.kde.org/)), a collection of KDE apps associated with KDE, but not part of KDE main, but still a part of KDE. But since Amarok is quite popular, it has its own repository in Kubuntu whenever a new version is released. The Kubuntu Amarok repository does contain amarok-xine ([http://kubuntu.org/packages/amarok-141/pool-dapper/)](http://kubuntu.org/packages/amarok-141/pool-dapper/)). 

libxine, however, is quite a different story. It would be quite inappropriate it put it under just Amarok or a general  repository, since xine is also used by other non-multimedia apps, for example in notifications and system sounds.

That being said, I heard that the solution to the problem with FLAC support in Amarok 1.4.1 simply involves compiling the latest xine-lib/libxine. And it seems to me that there have been no side effects with that workaround. So I'm quite baffled why it's taking the appropriate devs/maintainers this long to come up with a patch.

@l.capriotti: try sudo apt-get dist-upgrade ?
since amarok-1.4.1 is not officially support in ubuntu, i'm not really surprise. they can't do change in the main repo just for a non official one. 
But i think they should provide an upgrade of libxine in the amarok repo. We should ask that.

---

### Post by Jucato on 2006-08-04
Hmm... I also thought about that, but let's see...

- Amarok 1.3.9 is in Dapper main.
- Firefox 1.5.0.3 is in Dapper main.

- When Firefox released 1.5.0.4 and 1.5.0.5, the updates were added to dapper-security.
- When Amarok released 1.4 and 1.4.1, a special repository had to be created to host it. The Amarok 1.4 and 1.4.1 repositories are in Kubuntu Dapper main.

Am I the only one seeing the discrepancy?

This calls for a new thread. See you at the Ubuntu Cafe. :D

---

### Post by givré on 2006-08-04
Security update of firefox are important because it is the door to the net.
Amarok 1.4.1 & kde 3.5.4 add new feature so they can't put them in main, but they are kind enough to creat a special repo for them.
But you will probably ask why they update gnome and not kde. In fact the update of gnome to 2.14.3 are just bug fixing update, not like kde one.
In my view, all update that just fix bug and don't add feature (that could add bug) can be push in main, but not the other.
The excpetion will probably be openoffice 2.0.3 which is for the moment in dapper-proposed.

---

### Post by ash211 on 2006-08-04
> **jpazindustries said:**
> My fonts were messed up after I updated to 3.5.4 but i fixed it. the problem was that the upgrade turned off subpixel hinting. other than that everything went cool.=D>

Could you please explain how to turn subpixel hinting back on?  I seem to have run into the same problem.

EDIT: Found it.  kcontrol -> Appearance & Themes -> Fonts.  Click configure, then check sub-pixel hinting.

---

### Post by Jucato on 2006-08-04
> **givré said:**
> But you will probably ask why they update gnome and not kde. In fact the update of gnome to 2.14.3 are just bug fixing update, not like kde one.

Hmm... Probably, I can understand that reason for Amarok, but KDE 3.5.4 isn't about just new features, although it does have some. According to the site, there were over 10 new features added, but more than 100 bug fixes.

[http://www.kde.org/announcements/announce-3.5.4.php](http://www.kde.org/announcements/announce-3.5.4.php)
[http://www.kde.org/announcements/changelogs/changelog3_5_3to3_5_4.php](http://www.kde.org/announcements/changelogs/changelog3_5_3to3_5_4.php)

I thought the backports are supposed to be there for this kind of situation?

Anyway, I made a separate thread for this question, so as not to go off-topic:
[http://www.ubuntuforums.org/showthread.php?t=229360](http://www.ubuntuforums.org/showthread.php?t=229360)

---

### Post by givré on 2006-08-04
Yeah right, i think i'll move to the other thread.
See you :cool:

---

### Post by ElijahLofgren on 2006-08-05
> **l.capriotti said:**
> I''m not able to upgrade:

l.capriotti@ubuntu:~$ sudo apt-get update
( ... )
l.capriotti@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  kaudiocreator: Depends: kdemultimedia-kio-plugins (= 4:3.5.3-0ubuntu0.1) but 4:3.5.4-0ubuntu2~dapper1 is installed
  konqueror: Depends: kcontrol (= 4:3.5.4-0ubuntu1~dapper2) but 4:3.5.3-0ubuntu0.2 is installed

Any hints?

Cheers
Luigi
Someone says running "sudo apt-get --fix-broken install" fixed that problem. [http://ubuntuforums.org/showpost.php?p=1341350&postcount=23](http://ubuntuforums.org/showpost.php?p=1341350&postcount=23)

I have yet to try that fix myself.

---

### Post by jamadagni on 2006-08-22
> **Fenyx said:**
> yes. kdelibs-bin is replaced by kdelibs4c2.
Fenyx, how do you say that? I compared kdelibs4c2 for dapper and edgy and both contain the same number of packages, at least according to packages.ubuntu.com.

---

### Post by jdong on 2006-08-22
As the backports guy around here, maybe I should chime in a bit.


The update from KDE 3.5.2 to KDE 3.5.4 is available through kubuntu.org for those who desire it. These packages are provided by the kubuntu team, and is therefore quite trustable.

This update will not be in official Ubuntu repositories because of stability reasons -- in order for the stable Ubuntu release to be suitable for enterprise usage, you cannot risk any introductions of bugs or defects through providing too many updates.



As far as "why Firefox 1.5.0.x is in dapper-security and amarok isn't", Firefox is a special exception because their point releases are very specific to what they fix (basically security updates and critical bug patches). Not all packages are so tightly regulated in their point release updates.




And I know at this point someone's going to ask why Backports haven't started compiling in Dapper yet. The reason is that alongside Dapper the developers switched to a new build infrastructure, and they haven't written the routines on the new infrastructure to handle Backports. This is currently being addressed and I hope it'll be fixed ASAP.

---

### Post by Jucato on 2006-08-23
@jdong:

Thanks for your input. Those are the same answers I got from Jonathan Riddell when I got the chance to talk to him over the IRC: [http://www.ubuntuforums.org/showpost.php?p=1360787&postcount=14](http://www.ubuntuforums.org/showpost.php?p=1360787&postcount=14)

@jamadagni: I forgot where I got that bit of info. I'll try to look for it and post it later.

---

### Post by grizzly on 2006-09-12
Is it ok to update to kde 3.5.4 now?

---

### Post by ElijahLofgren on 2006-09-12
> **grizzly said:**
> Is it ok to update to kde 3.5.4 now?
I'd say so. I'm running it here without problems.

---

### Post by elettronicha on 2006-09-12
> **grizzly said:**
> Is it ok to update to kde 3.5.4 now?
Yeah!

---

