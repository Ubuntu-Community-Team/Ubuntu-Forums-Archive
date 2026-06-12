---
title: "Is anyone else having problem with software center in 12.04 Alpha 1?"
date: 2011-12-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by irv on 2011-12-05
I can install apts from apt-get, but the software center will not install apts. Anyone else having this problem.
I did the upgrades but this did not help. I know there is a bug in software center, but I had it working in 11.04 and 11.10 but not in 12.04 yet.

---

### Post by fjgaude on 2011-12-05
Yes, we are having troubles with USC... it seems they are making major changes to it through using AI, Artificial Intelligence techniques. Likely not unlike IBM's Watson computer that beat Jeopardy contestants on TV a few weeks ago. Watson is now being configured to work with medical doctors!

---

### Post by irv on 2011-12-05
> **fjgaude said:**
> Yes, we are having troubles with USC... it seems they are making major changes to it through using AI, Artificial Intelligence techniques. Likely not unlike IBM's Watson computer that beat Jeopardy contestants on TV a few weeks ago. Watson is now being configured to work with medical doctors!

Thanks for the information. I will wait until a later release of the software center and won't file a bug report. Also I noticed the update manager does not work. I will do updates from the command line.

---

### Post by irv on 2011-12-05
I ran: 
```
sudo apt-get update
```
from the command line and then ran update manager and it started to run. It is now doing a upgrade.
[ATTACH]208573[/ATTACH]

---

### Post by irv on 2011-12-05
Ok after doing the update/upgrade the software center is still not working, but now it has the progress icon, but after a while it went away, I believe it tried to do an install but quit.
Now I can't get the icon to re-appear.
[ATTACH]208577[/ATTACH]    [ATTACH]208578[/ATTACH]

---

### Post by kaldor on 2011-12-05
I have issues, but they seem inconsistent. Sometimes USC refuses to start, sometimes it exits, others it just keeps spouting error popups saying it crashed when it has not. Anything regarding updating or installing refuses to work.

I usually do not pay attention to USC, so the bugs don't affect me too much.

---

### Post by irv on 2011-12-05
> **kaldor said:**
> I have issues, but they seem inconsistent. Sometimes USC refuses to start, sometimes it exits, others it just keeps spouting error popups saying it crashed when it has not. Anything regarding updating or installing refuses to work.

I usually do not pay attention to USC, so the bugs don't affect me too much.

I just finished installing the lamp server on my local machine but I did it from the terminal. I do some develoment for the web so I thought I would test to make sure this would work in 12.04. It seems to be OK.
When I do testing on Alpha and Beta releases I like to try differnt software packages. I had some issue with my wifi drivers, but I have this problem with all releases, (because of the Broadcom card).I have my work around for this, so the only issue I have a the moment is with the USC. It always work on all the other releases I have tried. I see there was a bug report files but it never effected me before.

---

### Post by irv on 2011-12-13
Periodically I startup the software center and try to install something but as of today it is still now working.
Is this going to be the case until the finial release like other version before? Hopefully by the Beta release.
It would be interesting to see if the speed has improved. I know many of us have used the package manager or command line to install packages because of the slowness of the software center. It would be nice to see a great improvement in the software center on this release.

---

### Post by wolfen69 on 2011-12-15
> **irv said:**
> Also I noticed the update manager does not work.

I had the same problem until a few minutes ago, but after doing a boatload of updates through the terminal, it seems to work now. I havn't used the software center yet, but will have to check it out.

---

### Post by wolfen69 on 2011-12-15
I just checked the Software Center and it does not work for me either. [Here]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/898931") is the bug report if you would like to add yourself as affected.

---

### Post by effenberg0x0 on 2011-12-15
Although I don't particularly like the software in its current development state (it slow even in a powerful machine and net connection), I found myself browsing, finding and downloading software from Ubuntu that I had never heard of. I was kinda beginning to like it. But the thing is broken for me too, for a couple weeks now I think.

Actually a bunch of things that rely on Python and Python-apt are not working at all or failing more than normal.

---

### Post by mc4man on 2011-12-15
There's a whole series of bugs affecting SC, probably be fixed by A2

The 1st which is likely still valid - 
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/849745](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/849745)

That was trumped by this one which occurs before the ^ can occur
 - 
[https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/898756](https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/898756)

The effect of the above one (resolver) is that when closing SC this crash occurs which Bug #898931 should be duped to
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/767361](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/767361)

Edit:
crash 2 was fixed with new aptdaemon which should allow it to work. That leaves crash 1,3 which are still active. So SC can be used to install/remove but likely will only  work one time per session *restart (screen shows working again 

(it's also auto adding to launcher by default now, previously would offer to but not add unless specified

---

### Post by jerrylamos on 2011-12-16
Nope.  Don't use the software center.  I do use synaptic.

I've been looking at the top 10 software downloads from the software center and am  not interested in any of them.  Stellarium maybe.

Jerry

---

### Post by bfb on 2011-12-22
Hasn't been working for a while, and update manager is also very buggy

---

### Post by irv on 2011-12-22
> **bfb said:**
> Hasn't been working for a while, and update manager is also very buggy

Hopefully they will have these two going by the Beta release or before. One good thing, seeing there are not working, I have been doing everything at the command line and I am finding it much faster and easier.

---

### Post by mc4man on 2012-01-04
S-C should now be working again without issue with latest aptdaemon updates (as should update-manager if not previously.

---

### Post by irv on 2012-01-04
> **mc4man said:**
> S-C should now be working again without issue with latest aptdaemon updates (as should update-manager if not previously.
OK I just did a update/upgrade 1 minute ago and installed VLC via Software Center and all went well. It is now working.

Edit: not so, I just got an error when the Software Center closed. It said it had trouble closing.

---

### Post by mc4man on 2012-01-04
> **irv said:**
> OK I just did a update/upgrade 1 minute ago and installed VLC via Software Center and all went well. It is now working.

Edit: not so, I just got an error when the Software Center closed. It said it had trouble closing.

Well now that it's working it 'allows' you to come across add.  - 
see this on closing
[https://bugs.launchpad.net/ubuntu/+source/pygobject/+bug/907568](https://bugs.launchpad.net/ubuntu/+source/pygobject/+bug/907568)

And occasionally on 'more info'
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/888669](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/888669)
(both are fix committed, not yet released

Also am seeing with the new 'auto add, don't ask' to unity launcher the possibility of apps without .desktops being improperly added to the launcher

---

### Post by ventrical on 2012-01-05
It's actually working very well here on a Unity 2D station.

---

### Post by 1roxtar on 2012-01-06
As of this morning's updates (01-06-12), the Software Center is loading up much, much faster for me.  I have been able to install various programs a lot quicker, as well, and I have yet to get a crash notification.  Keep it up guys!!!

**My Rig:**
Dell Dimension E521, AMD64 Athlon X2, 5 Gigs of RAM, Nvidia Geforce 9500 GT video card.

---

### Post by sk8brding on 2012-03-04
Thanks IRV, the "sudo apt-get update" fix worked for me.
It enabled the software center to work again and updates to go smoother (there were a few that were not downloading).

---

### Post by clisting on 2012-03-10
I try to click on the Icon in the gnome dock in the application area and  it does nothing Ive uninstalled fully and reinstalled the software center and nothing happens will not open up please help ..

---

### Post by az44 on 2012-03-10
The Ubuntu folks have fixed it as of 03/10/12 when I did an update via the terminal.
Cheers...

---

### Post by oldos2er on 2012-03-10
Moved to Ubuntu +1 (Precise Pangolin).

---

### Post by matt_symes on 2012-03-10
Hi

Open a terminal and type

```
software-center
```

Post back errors. 

You know 12.04 is still in development and liable to breakage ?

Kind regards

---

### Post by matt_symes on 2012-03-10
Hi

Open a terminal and type

```
software-center
```

Post back errors. 

You know 12.04 is still in development and liable to breakage ? This is not your main OS but you are testing ?

Kind regards

---

### Post by Baldrick_NZ on 2012-03-10
I'm having the same prob too...

```
bryan@bryan:~$ software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 140, in <module>
    from softwarecenter.ui.gtk3.app import SoftwareCenterAppGtk3
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 83, in <module>
    from softwarecenter.ui.gtk3.panes.installedpane import InstalledPane
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/installedpane.py", line 37, in <module>
    from softwarecenter.ui.gtk3.models.appstore2 import (
  File "/usr/share/software-center/softwarecenter/ui/gtk3/models/appstore2.py", line 33, in <module>
    from softwarecenter.backend.reviews import get_review_loader
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 32, in <module>
    from bsddb import db as bdb
  File "/usr/lib/python2.7/bsddb/__init__.py", line 67, in <module>
    import _bsddb
ImportError: No module named _bsddb

```

It looks like a bug, as it was working fine before the latest updates. I'm sure it'll get fixed soon, but in the meantime, how about using Synaptic instead? That's working fine here..

From terminal..
```
sudo apt-get install synaptic
```

---

### Post by cariboo on 2012-03-10
Merged two threads on the same subject.

---

### Post by kaziweb on 2012-03-11
I'm also facing...... Software center not working after upgrading from 11.10 to 12.04LTS. Someone please advise.. what to do?

---

### Post by Johnny3 on 2012-03-11
> **kaziweb said:**
> I'm also facing...... Software center not working after upgrading from 11.10 to 12.04LTS. Someone please advise.. what to do?

Do what NZ said 
From terminal..
Code:

sudo apt-get install synaptic

Then reinstall software center in synaptic package manager.
Good Luck and God Bless Johnny3 65+++

---

### Post by kaziweb on 2012-04-08
Hi, I'm facing problem with software center. It's a different types of problem.

I'm using Cairo-Doc (with open GL). Often, when I click on the applet of "Application menu" on the Doc, Ubuntu Software Center opens automatically. I reported this as a bug before not yet solved. Don't know what is happening actually. I'm not an expert user of Ubuntu.

---

