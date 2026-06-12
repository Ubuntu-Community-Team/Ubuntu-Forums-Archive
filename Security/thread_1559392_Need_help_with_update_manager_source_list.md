---
title: "Need help with update manager source list"
date: 2010-08-23
forum: Security
---

### Post by Mat11 on 2010-08-23
Hi i need help with my update manager software source list in Karmic 9.10
Think something is not right.
Hope you can help.Here's the output i have :

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic restricted main universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates restricted main universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates restricted multiverse #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-security restricted main universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-security restricted multiverse #Added by software-properties
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-security multiverse
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-proposed restricted multiverse main universe
matt@matt-laptop:~$ 

Am i right to be concerned at all ?



Mat

---

### Post by mhgsys on 2010-08-23
What is the problem / error?

Edit: Saw you edited the OP

Since I'm on lucid I can't compare exactly, but there seems to be nothing wrong with your sources.

---

### Post by Mat11 on 2010-08-23
> **mhgsys said:**
> What is the problem / error?

Think i do not have the original standard Karmic main line can you advise ?
Have posted output info above thanks.

---

### Post by Mat11 on 2010-08-23
Hi thanks for your reply.
I think its the third paragraph down mentioning deb and deb-src relating to karmic updates.
Is that one standard ?

---

### Post by mhgsys on 2010-08-23
Compare; 

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Ubuntu_Resources](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Ubuntu_Resources)

(ps: in firefox .. press ctrl+f and find sample sources.list.)

---

### Post by Mat11 on 2010-08-23
> **mhgsys said:**
> Compare; 

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Ubuntu_Resources](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Ubuntu_Resources)

So much info where do i start ?

---

### Post by mhgsys on 2010-08-23
Sorry; I guess you overlooked my edit; 

in firefox .. press ctrl+f and find sample sources.list

(At the end have been added repositories for Medibuntu and Google)

---

### Post by Mat11 on 2010-08-23
> **mhgsys said:**
> Sorry; I guess you overlooked my edit; 

in firefox .. press ctrl+f and find sample sources.list

(At the end have been added repositories for Medibuntu and Google)


No joy with the Firefox added search box below the page it just highlights your writing and i have to admit i've never used this extra thing in Firefox.

Thanks for your help have to go. Think my Comp is becoming progressively unstable especially rufusing to boot/start up, blank pages have reappeared on start up.I had this problem a year ago and a few months ago and i have changed what my update manager does to a limit updates for now.Some of the problem maybe to do with the update manager changes and the new headers etc that are updated/choosen -- both conflicting together before reboot i'm not entirely sure.My last reboot was an old problem nightmare trust me !

---

### Post by mhgsys on 2010-08-23
Yes; It highlights the word sample sources.list
 You're suppose to do that on [http://ubuntuguide.org/wiki/Ubuntu:Karmic#Ubuntu_Resources](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Ubuntu_Resources)

edit:
And If you scroll just a little bit down after that you'll see the entire list .

---

### Post by Mat11 on 2010-08-24
> **mhgsys said:**
> Yes; It highlights the word sample sources.list
 You're suppose to do that on [http://ubuntuguide.org/wiki/Ubuntu:Karmic#Ubuntu_Resources](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Ubuntu_Resources)

edit:
And If you scroll just a little bit down after that you'll see the entire list .

Think if i interfere with any of that stuff being a newbie i'll **** it up.
Theres something quite wrong in the Ubuntu set up and it does not refer to you but theres an assumption that you have unlimited time to read stuff when things go wrong and that you have to be an expert in editing stuff that is critical to your comp.
Why is there no easy way of checking that your software sources and keys that may  have been compromised with regards to security ?
I really think if Ubuntu and its entire set up don't realise that as someone new to Linux what they need is someway of checking validity of keys in update manager and new software sources and relating them to the original default values.At the moment i feel insecure about my system and i need an expert to check to see if they are correct values.

Thanks

---

### Post by cariboo on 2010-08-24
If you don't want to take the time or make the effort to learn how to use Ubuntu, maybe [paid support]("http://http://shop.canonical.com/index.php?cPath=41") is the way to go for you.

---

### Post by Mat11 on 2010-08-26
> **cariboo907 said:**
> If you don't want to take the time or make the effort to learn how to use Ubuntu, maybe [paid support]("http://http://shop.canonical.com/index.php?cPath=41") is the way to go for you.


At the moment i feel my security has become questionable and i'm thinking of moving on at this moment.Have seen comments from others about added security permissions to files etc over the last year making things harder and which where not needed.The software update manager source list is a completely different kettle of fish.
Thanks for your help.

---

### Post by cariboo on 2010-08-26
What makes you think your sources lists/keys are compromised? Linux is just like Windows, it takes time to learn to use it properly, you didn't just magically know how to use Windows the first time you sat down in front of a computer. Remember most of the knowledge you you have gained using Windows doesn't transfer to Linux or OSX. 

From what I could see of your sources list, it looks like a default list, the only thing I see is that you have a couple of source repository uncommented, you can fix that by adding a # to the start of that line. Or you can go to System->Administration->Software Sources->Ubuntu Software, and make sure there isn't a check mark beside Source code.

---

