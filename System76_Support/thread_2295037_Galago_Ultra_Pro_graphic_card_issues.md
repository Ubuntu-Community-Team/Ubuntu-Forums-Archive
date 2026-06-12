---
title: "Galago Ultra Pro graphic card issues"
date: 2015-09-15
forum: System76 Support
---

### Post by KSmooth on 2015-09-15
Hey guys,

First of all, sorry about my english, I give my very best!
I bought a Galago Ultra Pro with an Intel Iris Pro 5200 last year.

1. The biggest problem is the graphic glitches in many 3D applications.
Is here someone who can reproduce this problem? Unitl today I thought that this problem is a configuration problem of compiz, but today I tried a live stick and looked at the threejs.org demo applications and I saw the glitches again.
Does anyone know what I can do against that?

Three free 3d games to reproduce this problems are: 
[https://www.cubeslam.com/oujxqy](https://www.cubeslam.com/oujxqy) 
[http://www.playmapscube.com/](http://www.playmapscube.com/)
or
0ad from the software center


2. The graphic performance is really weak if you compare it with windows.
The performance is a lot better if I plug it into the power socket but it:s obviously slower than a windows on the same machine.
Is here anyone who can help me?



Thank you very much for your time!

best regards,
michael

---

### Post by fallenshadow on 2015-09-18
Hi Michael,

I also got myself a Galago UltraPro last year. I don't really use mine for games but I did read up some place online that the Iris Pro graphics chip gets underclocked when the Laptop is plugged out in order to save battery power. Windows may not be doing that in comparison.

I hope someone else has more detailed information for you.

---

### Post by jweber53 on 2015-09-18
Hi,
I have a kudu pro and my graphics performance became really bad after a system update after I had upgraded to Ubuntu 15.04. Somewhere I found to install a package called "xdiagnose". I ran it from the command line as root (or use sudo) and it opens a small window. Under the options "Workarounds" are three items with check boxes. I checked all 3 and my graphics seems fine again. I don't know why it works or what the options mean...I just did it.

```
$ sudo xdiagnose
```

I attached a screenshot of xdiagnose.

```
 # dpkg -l xdiagnose
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                        Version            Architecture       Description
+++-===========================-==================-==================-===========================================================
ii  xdiagnose                   3.7.2              all                X.org diagnosis tool

```

---

### Post by KSmooth on 2015-10-04
Thank you for your answers but this tipps doesn't help me. :(

It's a little bit sad because I bought a laptop with an open source driver from a company that sell ubuntu laptops and I have more issues compared with my desktop pc. :/

---

### Post by fallenshadow on 2015-10-12
I would recommend you contact their support directly with your issue. People here can't help unless we experienced the same issue.

[https://system76.com/support]("https://system76.com/support")

---

