---
title: "KDE 3.5.4 backport ?"
date: 2006-08-02
forum: Ubuntu Backports
---

### Post by sorin7486 on 2006-08-02
What about backporting KDE 3.5.4... I don't know if it's posible but considering the great number of bugfixes I think it wold be useful for Dapper

---

### Post by mmcmonster on 2006-08-02
Likely impossible since there are a large number of "core" libraries that have to be modified.  The chances of things breaking is too high.  We'll just have to wait for edgy. ;-)

---

### Post by thor2002ro on 2006-08-02
repo for kde 3.5.4 :P

deb [http://kubuntu.org/packages/kde-354/](http://kubuntu.org/packages/kde-354/) dapper main

---

### Post by rumix on 2006-08-02
Before upgrading read [this!]("http://kubuntu.org/packages/kde-354/README")

---

### Post by rogeriovinhal on 2006-08-02
Nice, just did the upgrade and did not read that... :(

Kubuntu configurations all got messed up.

---

### Post by LordNikon9x on 2006-08-02
Yeah, _some_ configuration got messed up, but all in all, I am impressed with that new relese. One thing I miss is alblock list in konqueror. In previous versions it had comprehensive list already configured, but now I have only those that I configured myself.
But I must say Holy Cow!! If things are moving this way towards kde4 then kde4 _will_ blow your socks off! The speed improvement in this release is incredible. And also those little bells and whistles. I never thought transperant window decorations to be so .. cool 8-)
In 3.5.2 or 3.5.3 the konsole was slow, even grinding to halt on some cases. Try to compile your stuff on such thing! I had to use rxvt over konsole. Now konsole flyes like eagle.
Oh, this thing is getting little OT, but I can not stop ranting on new kde :)

---

### Post by szkodnik on 2006-08-02
In order to restore default settings I've downloaded kubuntu-default-settings package, unpacked it and copied its contents into .kde directory in home folder.

---

### Post by rogeriovinhal on 2006-08-02
> **szkodnik said:**
> In order to restore default settings I've downloaded kubuntu-default-settings package, unpacked it and copied its contents into .kde directory in home folder.

Thanks, I didn't need to download, just copied from the /usr/share directory.
It worked, but the KDE settings came back to what they were on Kubuntu installation, so my personal settings had to be redone, but nothing that I should take more than 5 minutes.

As said before, I found KDE 3.5.4 to be even faster than 3.5.3 in boot time and apps startup, so it is indeed nice to make the upgrade.
But for those who don't want to redo their configurations, they should wait for this bug to be corrected.

---

### Post by xinix on 2006-08-02
> **rogeriovinhal said:**
> But for those who don't want to redo their configurations, they should wait for this bug to be corrected.

Would backing up your kde configs before doing this upgrade and restoring them afterwards avoid having to do reconfigs?  Would the .kde directory be the right one to backup?

---

### Post by rogeriovinhal on 2006-08-02
Actually, I am having some problems to maintain the buttons and colors from Kubuntu, they work, and if I try to change something, they stop working...

Let's see if anyone manages to correct this...

---

### Post by RavenOfOdin on 2006-08-02
I wasn't aware there was a backport of 3.5.4 at the moment.

What would the risks be in using a backport as compared to waiting for the stable distribution, other than libraries missing?

---

### Post by Jucato on 2006-08-02
It's not a backport. It's a special repository made so that Kubunt users could enjoy the benefits of the new KDE release.

HOWEVER, the official announcement from Kubuntu has not yet been released (it's not on the main page yet), and for good reason. 

[http://kubuntu.org/announcements/kde-354.php](http://kubuntu.org/announcements/kde-354.php)
> 
**Important Note**: these packages have a bug which stops kubuntu-default-settings from applying.  We currently do **not** advise upgrading to them unless you are willing to work around this bug.

To those giving out the new repositories, please also caution them about what may happen when the upgrade to KDE 3.5.4.

---

### Post by Sokraates on 2006-08-03
> **xinix said:**
> Would backing up your kde configs before doing this upgrade and restoring them afterwards avoid having to do reconfigs?  Would the .kde directory be the right one to backup?

Probably, since according to rogeriovinhal the kubuntu config-files in /usr/share are not affected. 

But I still don't get the nature of this bug.

How are the settings initiated, if /etc/kderc is not used? Is it a kubuntu-specific file? If so, which file is used to point to your personal config (shouldn't it be .kde on all KDE-systems?)?

Or does it simply mean, that /etc/kderc is not used when upgrading, so that .kde is overwritten with the kde (not kubuntu) defaults? 

Are other config-files affected, too? :-k

---

### Post by Jucato on 2006-08-03
AFAIK, it is the kubunt-default-settings that are affected. Kubuntu/KDE follows a sort of "heirarchy" of settings, where it looks for configurations first. It starts with the user's personal settings, then with the kubuntu-default-settings, then in /etc/kde3 and /usr/share/apps.

Since most of Kubuntu is using the kubuntu-defualt-settings (unless you have customized/changed each and every thing), you're going to have a messed up system. Haven't tried it out yet, though. I'm not as daring as some. :D

---

### Post by NeoChaosX on 2006-08-03
Oh, believe me I have a customized Kubuntu desktop, and the upgrade to KDE 3.5.4 messed it up anyway. My wallpaper is missing and there's nothing on the kicker except for a short cut to Konsole.

---

### Post by Jucato on 2006-08-03
KDE 3.5.4 is **officially** available in Kubuntu.

[http://www.kubuntu.org](http://www.kubuntu.org)

Since it has been added to the front page, and RSS feeds have been sent, it's presumably safe to upgrade now.

---

### Post by xinix on 2006-08-03
> **Fenyx said:**
> KDE 3.5.4 is **officially** available in Kubuntu.

[http://www.kubuntu.org](http://www.kubuntu.org)

Since it has been added to the front page, and RSS feeds have been sent, it's presumably safe to upgrade now.

Yes it seems to be safe to upgrade.  Just did it and all settings remained the same.  One thing though,  I now have a .kde directory at the root level.

---

### Post by l.capriotti on 2006-08-04
Anyone having this?

l.capriotti@ubuntu:~$ sudo apt-get update
(...omissis...)
l.capriotti@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  kaudiocreator: Depends: kdemultimedia-kio-plugins (= 4:3.5.3-0ubuntu0.1) but 4:3.5.4-0ubuntu2~dapper1 is installed
  konqueror: Depends: kcontrol (= 4:3.5.4-0ubuntu1~dapper2) but 4:3.5.3-0ubuntu0.2 is installed

L

---

### Post by Jucato on 2006-08-04
Have you tried sudo apt-get dist-upgrade ?

---

### Post by Sokraates on 2006-08-04
Yep, had the same problem. I simply used Synaptic's "fix broken packages" and then the new plugins together with a new kaudiocreator were installed.

I've already ripped a [new CD]("http://www.amazon.com/gp/product/B000G75AE8/sr=8-1/qid=1154697372/ref=pd_bbs_1/104-0218141-3501563?ie=UTF8") and it worked perfectly.

---

### Post by l.capriotti on 2006-08-04
> **Fenyx said:**
> Have you tried sudo apt-get dist-upgrade ?

yes, same result.
L

---

### Post by Sokraates on 2006-08-04
> **l.capriotti said:**
> yes, same result.
L

Did you try Synaptic's "fix broken packages"? I think the correct code is
```
[SIZE=-1]sudo apt-get --fix-broken install[/SIZE]
``` 
On a sidenote: After restarting, my Kubuntu-default-settings (e.g. theme) were gone. All my personal settings (desktop background, etc.) were still there, so it took me just a few minutes to mend this.

---

### Post by l.capriotti on 2006-08-05
> **Sokraates said:**
> 
```
[SIZE=-1]sudo apt-get --fix-broken install[/SIZE]
```

Whoa! Tks a million, it worked perfectly!

Cheers

Luigi

---

### Post by Sokraates on 2006-08-05
Drats! Whenever I login, the KDE-setup-manager starts and all settings but my peronal changes are set to KDE-default.

I even reinstalled kubuntu-default-settings, but that didn't help at all.

Any ideas, which file needs to be created or written to?

---

### Post by Sokraates on 2006-08-05
Well, I just found out the solution.

Obvously the file ~/.kde/share/config/startupconfig wasn't updated correctly.

After the first start the line
[HTML]kpersonalizerrc_general_firstlogin="true"[/HTML]
should be changed to
[HTML]kpersonalizerrc_general_firstlogin="false"[/HTML]

After doing that manually, everything worked fine. Remember, that you'll have to do this for each user.

---

