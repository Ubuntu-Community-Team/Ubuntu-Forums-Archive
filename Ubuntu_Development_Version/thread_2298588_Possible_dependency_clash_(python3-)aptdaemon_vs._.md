---
title: "Possible dependency clash: (python3-)aptdaemon vs. gir1.2-packagekitglib-1.0 = 0.9.5"
date: 2015-10-12
forum: Ubuntu Development Version
---

### Post by syntaxerror74 on 2015-10-12
```

my@my-lubuntubox:~$ apt-cache policy python3-aptdaemon
python3-aptdaemon:
  Installed: 1.1.1+bzr982-0ubuntu8
  Candidate: 1.1.1+bzr982-0ubuntu13
  Version table:
     1.1.1+bzr982-0ubuntu13 0
        500 http://archive.ubuntu.com/ubuntu/ wily/main i386 Packages
 *** 1.1.1+bzr982-0ubuntu8 0

...

my@my-lubuntubox:~$ sudo apt-get install python3-aptdaemon

The following packages have unmet dependencies.
 python3-aptdaemon : Depends: gir1.2-packagekitglib-1.0 (< 0.9) but 0.9.5-0ubuntu1 is to be installed
...

```

A major conflict has been detected. :(

In human readable words: The latest python3-aptdaemon (1.1.1+bzr982-0ubuntu13) has implemented a **version control** for the version of the packagekitglib-1.0 package of GIR v1.2, i. e. **it must be a version prior to 0.9.**

And before anyone asks, I apparently did not run into this conflict this time by using packages from wily-proposed ! 
This conflict might even occur with users who stick to the stock main repos.

And to add insult to injury, in far away CHINA the Ubuntu users are getting the very same as I'm getting on their terminal output:
[https://forum.mobile.ubuntu.org.cn/viewtopic.php?f=49&t=473050](https://forum.mobile.ubuntu.org.cn/viewtopic.php?f=49&t=473050)

Isn't Google wonderful. (LOL) (2 out of 2 hits, I'm not kidding)

---

### Post by tista on 2015-10-12
Hi syntaxerror74,

Sounds strange... 
Because Wily still stacks with Packagekit **0.8.17-4ubuntu6~gcc5.3**, as launchpad showed:
[https://launchpad.net/ubuntu/+source/packagekit](https://launchpad.net/ubuntu/+source/packagekit)

So where did you do install version 0.9.5 (though I'm hosting 1.0.8 on my PPA: [https://launchpad.net/~tista/+archive/ubuntu/wayland](https://launchpad.net/~tista/+archive/ubuntu/wayland))?
And yep, today aptdaemon package 1.1.1+bzr982-0ubuntu13 has a version control in debian/control as packagekit (<< 0.9).

Regards.
Tista

---

### Post by syntaxerror74 on 2015-10-12
It's on launchpad, and I repeat again, it's NOT in "proposed" branch:
[https://launchpad.net/ubuntu/+source/packagekit/0.9.5-0ubuntu1](https://launchpad.net/ubuntu/+source/packagekit/0.9.5-0ubuntu1)

OMG, it was uploaded on 9/11, maybe that's because it broke :P

But for real, this is really peculiar. 
Found the version you spoke of, and yes, it IS for Wily:
[https://launchpad.net/ubuntu/+source/packagekit/0.8.17-4ubuntu6~gcc5.3](https://launchpad.net/ubuntu/+source/packagekit/0.8.17-4ubuntu6~gcc5.3)

So we see to be having **both **0.8.17-4-something and 0.9.5-0 at the moment, and both for Wily.
That means, apt just grabbed the newer one (which is normally a wise thing to do ;))

My assumption is that one packager didn't know about what the other packager was doing at the same time. A classic case of misinformation.
But wait...

[https://launchpad.net/ubuntu/wily/+source/packagekit](https://launchpad.net/ubuntu/wily/+source/packagekit)

This page lists *Current Version* as 0.8.17-4ubuntu6~gcc5.3, whilst it lists 0.9.5-0 under *Releases in Ubuntu*.
And "Releases" (for me) means: main releases, so no "proposed" ones.
Pretty illogical, all that....

```
tl ; dr
```Fair enough:
For some reason, **apt-get has found a package version which it was not supposed to find in the first place.**

-----------------
**QUICK "FIX"**: ```
dpkg -i...
```[i386] [https://launchpad.net/ubuntu/wily/i386/gir1.2-packagekitglib-1.0/0.8.17-4ubuntu6~gcc5.3](https://launchpad.net/ubuntu/wily/i386/gir1.2-packagekitglib-1.0/0.8.17-4ubuntu6~gcc5.3)

[amd64] [https://launchpad.net/ubuntu/wily/amd64/gir1.2-packagekitglib-1.0/0.8.17-4ubuntu6~gcc5.3](https://launchpad.net/ubuntu/wily/amd64/gir1.2-packagekitglib-1.0/0.8.17-4ubuntu6~gcc5.3)

---

### Post by tista on 2015-10-12
Ah, it might be a rare case unfortunately... ;)

Regards.
Tista

---

### Post by syntaxerror74 on 2015-10-12
Very rare, but even these do want to be treated adequately...We do not want any unwanted surprises when Wily will be out on *Back To The Future Day + 1 *[1], do we? :)

[SIZE=2][1] To understand this date, travel in time, back to 1989, at the release of *Back To The Future II* in theaters, when Marty McFly (Michael J. Fox) traveled to October **21**, 2015, which was a day "far away in the future" back 26 years ago. Now, reality will soon have overtaken fiction! (Just the hoverboards have not been made reality yet.) And hey, Wily release day - be it coincidence or intention - will be happening that day PLUS ONE, i. e. 0ctober **22**. Cool, huh. *Th-th-th-th-that's all, folks!*[/SIZE]

---

### Post by mc4man on 2015-10-12
It's more likely your install and or whatever source mirror you use was not updated very often. In regards to gir1.2-packagekitglib-1.0 (0.9.5-0ubuntu1) it is not in Ubuntu currently & has not been for some time. So there is only one version available, current is 0.8.17-4ubuntu6~gcc5.3
reference - [https://launchpad.net/ubuntu/+source/packagekit/0.9.5-0ubuntu1/+publishinghistory](https://launchpad.net/ubuntu/+source/packagekit/0.9.5-0ubuntu1/+publishinghistory)

edit: in case you go to link but don't expand, screenshot

---

