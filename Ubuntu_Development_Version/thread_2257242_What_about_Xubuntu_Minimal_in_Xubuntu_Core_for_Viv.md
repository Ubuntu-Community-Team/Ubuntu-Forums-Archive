---
title: "What about Xubuntu Minimal in Xubuntu Core for Vivid Daily"
date: 2014-12-18
forum: Ubuntu Development Version
---

### Post by sudodus on 2014-12-18
I saw that ***Xubuntu Minimal in Xubuntu Core for Vivid Daily        ***is tested by *elfy* 2014-11-04 14:41.

[http://iso.qa.ubuntu.com/qatracker/milestones/326/builds/82898/testcases/1655/results](http://iso.qa.ubuntu.com/qatracker/milestones/326/builds/82898/testcases/1655/results)

but the link to download it does not work for me.

- How is this flavour/version different from standard Xubuntu?

- Where can the iso file be found? Or can it be installed via the Ubuntu mini.iso?

---

### Post by Elfy on 2014-12-18
There is no download at the tracker because we use the same test for 32 and 64 bit - the iso in question is in fact the mini.iso

[http://archive.ubuntu.com/ubuntu/dists/vivid/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/vivid/main/installer-amd64/current/images/netboot/)
[http://archive.ubuntu.com/ubuntu/dists/vivid/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/vivid/main/installer-i386/current/images/netboot/)

The testcase explains which option to choose to install Xubuntu Minimal

The difference between core and normal is the things installed by default.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=258667&d=1418894171[/IMG]

---

### Post by sudodus on 2014-12-18
Thank you Elfy :-)

---

### Post by Elfy on 2014-12-18
welcome :)

---

### Post by sudodus on 2014-12-18
I tried with this 'current' Vivid mini.iso,

```
md5check mini-vivid-alpha.iso f0565ed7c11f8814cea0742f93399e50
calculated md5sum=f0565ed7c11f8814cea0742f93399e50
should be  md5sum=f0565ed7c11f8814cea0742f93399e50
/home/sudodus/bin/md5check indicates SUCCESSFUL download :-)
```

but it got stuck because no mirror works. I tried with Swedish as well as the default language (US English), tried several mirrors, even archive.ubuntu.com, but no go.

Trusty mini.iso works better, but does not offer xubuntu-core, while for example lubuntu-core and xubuntu-desktop are available.

Can I expect better luck with an older version of mini.iso?

[TABLE]
[TR]
[TD][IMG]http://www.fr.php.net/icons/folder.gif[/IMG][/TD]
[TD][20101020ubuntu354/]("http://www.fr.php.net/ubuntu/dists/vivid/main/installer-i386/20101020ubuntu354/")[/TD]
[TD="align: right"]30-Oct-2014 10:08[/TD]
[TD="align: right"]  -[/TD]
[TD][/TD]
[/TR]
[TR]
[TD][IMG]http://www.fr.php.net/icons/folder.gif[/IMG][/TD]
[TD][20101020ubuntu355/]("http://www.fr.php.net/ubuntu/dists/vivid/main/installer-i386/20101020ubuntu355/")[/TD]
[TD="align: right"]24-Nov-2014 23:28[/TD]
[TD="align: right"]  -[/TD]
[TD][/TD]
[/TR]
[TR]
[TD][IMG]http://www.fr.php.net/icons/folder.gif[/IMG][/TD]
[TD][20101020ubuntu356/]("http://www.fr.php.net/ubuntu/dists/vivid/main/installer-i386/20101020ubuntu356/")[/TD]
[TD="align: right"]16-Dec-2014 01:28[/TD]
[TD="align: right"]  -[/TD]
[TD][/TD]
[/TR]
[TR]
[TD][IMG]http://www.fr.php.net/icons/folder.gif[/IMG][/TD]
[TD][current/]("http://www.fr.php.net/ubuntu/dists/vivid/main/installer-i386/current/")[/TD]
[TD="align: right"]16-Dec-2014 01:28[/TD]
[TD="align: right"]  -[/TD]
[TD][/TD]
[/TR]
[TR]
[TH="colspan: 5"][HR][/HR][/TH]
[/TR]
[/TABLE]

Is there a reason why the latest test is Nov 4? That the newer mini.iso files do not work?

---

### Post by Elfy on 2014-12-18
> Trusty mini.iso works better, but does not offer xubuntu-core It wouldn't - it was only available from the last cycle.

>  Can I expect better luck with an older version of mini.iso? Maybe.

> Is there a reason why the latest test is Nov 4? That was when I checked that all worked - nothing since because we've not pushed for it to be tested. Nor will we be likely to tbh.

Just checked - appears to be no go - nothing to do with the Xubuntu Minimal, don't get any further than it trying to find a kernel.

---

### Post by sudodus on 2014-12-18
So I'll wait until beta stage or later to check out xubuntu-core, whenever we can expect mini.iso to work. (Maybe it works to install it into Lubuntu, but that would make a bloated installation.)

---

### Post by Elfy on 2014-12-18
yep

Not sure who actually watches the mini iso's tbh.

---

### Post by sudodus on 2014-12-18
It works to install xubuntu-core into Lubuntu Vivid alpha and log into it, definitely well enough for a curious person to test it :-)

---

### Post by Elfy on 2014-12-18
Thanks for being curious :)

---

### Post by sudodus on 2014-12-18
Elfy, can you add 'affects me too' to this bug about the vivid 32-bit mini.iso, and maybe add/change text to make it more relevant

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1403982](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1403982)

---

### Post by Elfy on 2014-12-18
added some screenies - but I don't see quite the same thing

---

### Post by sudodus on 2014-12-18
Maybe you use another (earlier?) version, (check the list in post #5, do you use version 354, 355 or 356, or yet another one)? I get my mini.iso files from this mirror, that has seemed to be reliable

[http://www.fr.php.net/ubuntu/dists/vivid/main/installer-i386/current/images/netboot/](http://www.fr.php.net/ubuntu/dists/vivid/main/installer-i386/current/images/netboot/)

---

### Post by Elfy on 2014-12-18
oh yea - probably an old one

---

### Post by Elfy on 2014-12-18
posted again

---

### Post by sudodus on 2014-12-18
Posted again in the bug report

```
In screen 4 I get

 /tmp/net-retriever-2315-Release.gpg
gpgv: md_enable: algorithm 10 not available
Signature made ...
gpgv: Can't check signature: unknown unknown digest algorithm
...


              

```

---

