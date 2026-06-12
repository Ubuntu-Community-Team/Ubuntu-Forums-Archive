---
title: "firefox 1.5.0.6 released today"
date: 2006-08-02
forum: The Cafe
---

### Post by TheRingmaster on 2006-08-02
Firefox 1.5.0.6 is a stability update that is part of our ongoing program to provide a safe Internet experience for our customers. We recommend that all users upgrade to this latest version.

    * Fixed an issue with playing Windows Media content 

Release Date: August 2, 2006

---

### Post by TheRingmaster on 2006-08-05
I guess no one cares :cry:

---

### Post by Christmas on 2006-08-05
I'm waiting for version 2 to come out, I really need that spellchecking feature. 1.5.0.5 was out about 1 week and a half and 1.5.0.6? Very fast developing :)

---

### Post by jason.b.c on 2006-08-05
So then why is **"Check for updates"** blanked out in mine..???

> Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.0.5) Gecko/20060719 Firefox/1.5.0.5

How do i make it automaticaly update..??

:confused:

---

### Post by GStubbs43 on 2006-08-05
Jason, you need the Mozilla version for automatic update, not the ubuntu version. ;)

---

### Post by mikeoh on 2006-08-05
> **Christmas said:**
> I'm waiting for version 2 to come out, I really need that spellchecking feature. 1.5.0.5 was out about 1 week and a half and 1.5.0.6? Very fast developing :)

That should be nice feature, but as an interim you can use the google firefox toolbar which does spellchecking.

---

### Post by jason.b.c on 2006-08-05
> **GStubbs43 said:**
> Jason, you need the Mozilla version for automatic update, not the ubuntu version. ;)

Well that sucks..!!

So what do i have to do..??  Manually update/install it..?

---

### Post by lazyd2 on 2006-08-05
> **jason.b.c said:**
> Well that sucks..!!

So what do i have to do..??  Manually update/install it..?That, or you could wait and update it through synaptic ;)

---

### Post by GuitarHero on 2006-08-05
Just go get the Mozilla version off of getfirefox.com

---

### Post by Polygon on 2006-08-06
gksudo firefox in terminal

then go to help > check for updates

---

### Post by edisav on 2006-08-06
Aren't there certain differences between the original version of firefox and the ubuntu version? Would a direct upgrade from firefox webite keep all dependencies in order without messing up something?

---

### Post by ubuntu_demon on 2006-08-06
> **Polygon said:**
> gksudo firefox in terminal

then go to help > check for updates
AFAIK this doesn't work. Let's hope it doesn't work. **This is not the correct way of upgrading firefox.**

(security) fixes will always be available through regular upgrades.  You will get notified when there are updates available. Just use the update-manager.

Sometimes it takes a bit longer for security fixes for firefox to become availabe. Some of the reasons for this could be : 
- firefox updates also sometimes introduces new features (whereas in an ideal world this would be only bug fixes for the current branch (in this case 1.5) and new features in the development branch
- Ubuntu uses a slightly patched (different) version of firefox. An example of such a patch is that the built-in firefox upgrade functionality is turned off because this is not the proper way to upgrade firefox in Ubuntu. It's common for Linux distributions to slightly patch (some) software they distribute.

---

### Post by BWF89 on 2006-08-06
I got the updated version.

Firefox is vastly improved from what it was a  year ago. I used to have problems where anytime the power went out (we loose utilities like crazy where I live) and I was useing Firefox or the computer froze up and I had to to a hard reboot, Firefox got messed up and I lose all my settings and all my bookmarks. This hasn't the last 2 times my power went out while useing Firefox.

You have to let Windows do a dskchk because theres always a few of the Mozilla files that get corrupted but it's nothing major like it was before.

---

### Post by hpklett on 2006-08-06
Release Notes:
> Firefox 1.5.0.6 is a stability update that is part of our ongoing program to provide a safe Internet experience for our customers. We recommend that all users upgrade to this latest version.

    * Fixed an issue with playing Windows Media content 

Release Date: August 2, 2006

It's a bugfix for the Windows version.  That's the only change I could find, so really, just let Synaptic upgrade when it feels like it.

I do wonder though, how long does it take for high profile projects to hit the (official) repositories?

---

### Post by TheRingmaster on 2006-08-06
> **hpklett said:**
> Release Notes:


It's a bugfix for the Windows version.  That's the only change I could find, so really, just let Synaptic upgrade when it feels like it.

I do wonder though, how long does it take for high profile projects to hit the (official) repositories?
at the max, it takes a week.

---

### Post by srunni on 2006-08-07
So we don't need to upgrade Firefox at all?

---

### Post by TheRingmaster on 2006-08-07
> **srunni said:**
> So we don't need to upgrade Firefox at all?
not this release I guess. Don't worry I didn't know either that's why I started this thread.

---

### Post by oyvindaa on 2006-08-11
Taken a while now hasn't it..

---

### Post by PingunZ on 2006-08-11
One week passed yet ?

---

### Post by bruce89 on 2006-08-11
1.5.0.6 has not released in Ubuntu as such, but if you look at the changelog for firefox:
[QUOTE=changelog]firefox (1.5.dfsg+1.5.0.5-0ubuntu6.06.1) dapper-security; urgency=low

  * Fix to non-HTTP loading of <object ...>'s (eg, streaming media
    files).  Mozilla Bugzilla #346167.  Expected to be the sole
    change in Firefox upstream 1.5.0.6.

 -- Ian Jackson <iwj@ubuntu.com>   Mon, 31 Jul 2006 13:55:56 +0100 [/QUOTE] - [https://launchpad.net/distros/ubuntu/dapper/+source/firefox/+changelog](https://launchpad.net/distros/ubuntu/dapper/+source/firefox/+changelog)
you'd find out the sole bug was fixed on last monday.  In fact, it was fixed in Ubuntu two days before 1.5.0.6 was released officially.

The bug was only for Windows Media videos, so it's not very important on Ubuntu.

---

### Post by JarG0n on 2006-08-13
> **Polygon said:**
> gksudo firefox in terminal

then go to help > check for updates

I just tried this, and the "Check for Updates" link is STILL greyed out.  

Does anyone know why the Ubuntu Firefox ] version (or any other version in the repository) _has not_ been upgraded to 1.5.0.6 ?!?!

](*,)

---

### Post by JarG0n on 2006-08-13
THANK YOU!  :-D 

This was my first suspicion.  I can now rest easy.

> **ubuntu_demon said:**
> AFAIK this doesn't work. Let's hope it doesn't work. **This is not the correct way of upgrading firefox.**

(security) fixes will always be available through regular upgrades.  You will get notified when there are updates available. Just use the update-manager.

Sometimes it takes a bit longer for security fixes for firefox to become availabe. Some of the reasons for this could be : 
- firefox updates also sometimes introduces new features (whereas in an ideal world this would be only bug fixes for the current branch (in this case 1.5) and new features in the development branch
- Ubuntu uses a slightly patched (different) version of firefox. An example of such a patch is that the built-in firefox upgrade functionality is turned off because this is not the proper way to upgrade firefox in Ubuntu. It's common for Linux distributions to slightly patch (some) software they distribute.

---

### Post by bruce89 on 2006-08-13
> **JarG0n said:**
> Does anyone know why the Ubuntu Firefox ] version (or any other version in the repository) _has not_ been upgraded to 1.5.0.6 ?!?!

It has, see my [earlier post]("http://www.ubuntuforums.org/showpost.php?p=1367064&postcount=20").

---

### Post by givré on 2006-08-13
It's funny to see that we had the firefox 1.5.0.6 before it was release :cool:

---

### Post by bluntu on 2006-08-16
So what this means is that I can and should continue using the Ubuntu version which is 1.5.0.6?

---

### Post by givré on 2006-08-16
I don't know why you shouldn't use the ubuntu version ?

---

### Post by bluntu on 2006-08-16
Sorry I was a bit confused there.

Right now I'm using Ubuntu version which is **1.5.0.5** and there is version 1.5.0.6 out there.

What should I do?

---

### Post by givré on 2006-08-16
version 1.5.0.5 of ubuntu is in fact the 1.5.0.6 because the apply the patch before the official release, so yeah you can keep the ubuntu one.
From the changelog (/usr/share/doc/firefox/):
> firefox (1.5.dfsg+1.5.0.5-0ubuntu6.06.1) dapper-security; urgency=low

* Fix to non-HTTP loading of <object ...>'s (eg, streaming media
files). Mozilla Bugzilla #346167. [B]Expected to be the sole
change in Firefox upstream 1.5.0.6.[/B]

-- Ian Jackson <iwj@ubuntu.com> Mon, 31 Jul 2006 13:55:56 +0100 
And it was in fact the only change

---

### Post by aysiu on 2006-08-16
> **bluntu said:**
> Sorry I was a bit confused there.

Right now I'm using Ubuntu version which is **1.5.0.5** and there is version 1.5.0.6 out there.

What should I do?
[Install the Mozilla version](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5).

---

### Post by givré on 2006-08-16
Come on aysiu, that's stupid, what you gain in installing the mozilla version when Ian Jackson is working hard to make security patch of firefox on time. (and sometimes even before time)

---

### Post by aysiu on 2006-08-16
Why is that stupid?

People who get nervous about not getting the most up-to-date Firefox immediately should use the Mozilla version, which is self-updating. Yes, today it's 1.5.0.6, but then it'll soon be 1.5.0.7, then 1.5.0.8, then 2.0. Do you want this person asking every time, "When do I get the update?"

---

### Post by givré on 2006-08-16
I understand what you want to say, but i still consider that stupid, since every security update will always go in dapper, and i don't understand why people can't wait, at more 1 week, for a security patch.
Anyway, if people get nervous and can't wait for the new version of firefox... :cool:

---

### Post by aysiu on 2006-08-16
> **givré said:**
> I understand what you want to say, but i still consider that stupid, since every security update will always go in dapper, and i don't understand why people can't wait, at more 1 week, for a security patch.
Anyway, if people get nervous and can't wait for the new version of firefox... :cool:
I don't understand either why people can't wait a week, but some people are anxious, and if they are, why not just give them what they want instead of dealing with them complaining after every update?

---

### Post by pcolamar on 2006-08-21
> **aysiu said:**
> Why is that stupid?

People who get nervous about not getting the most up-to-date Firefox immediately should use the Mozilla version, which is self-updating. Yes, today it's 1.5.0.6, but then it'll soon be 1.5.0.7, then 1.5.0.8, then 2.0. Do you want this person asking every time, "When do I get the update?"

Well, it's not always a question of being anxious or not.
e.g.: I have since today a shared WinXP/Linux profile configuration for both Thunderbird and Firefox.
Now everytime I switch back to Win from Linux I get the Firefox "Welcome update"  page. I guess Linux leaves trace of it own release number (1.5.0.5) and the Win Firefox (1.5.0.6) perceives it has a just performed upgrade.

It took me 5 min to understand why but ....

I know, nothing to worry. Just annoying .

I guess playing with about:config in the Ubuntu version should solve it.
I'll have a look later today.

Regards

---

