---
title: "Lubuntu 12.04 esword greek nt modules show up as gibberish"
date: 2012-06-13
forum: Ubuntu Christian Edition
---

### Post by ubume2 on 2012-06-13
I have some greek modules installed on my installs of Ubuntu Unity 12.04, Debian Squeeze, and Lubuntu 11.10. They view fine. I have either e-Sword 9.7.2 or the latest e-Sword 10.1.

On Lubuntu 12.04 only the SBLGNT module views properly. The Nestle-Aland 26, and others do not view properly.

Due to issues with the "installer script" and search function not working, I installed e-Sword directly using the Wine Programs Loader and followed the instructions here:

[http://ubuntuforums.org/showthread.php?t=1920862](http://ubuntuforums.org/showthread.php?t=1920862)  at post #2 by forrestcupp and had great results until Lubuntu 12.04.  

I am wondering now if there is another tweak I can do through winetricks to get the greek modules working on 12.04?  

On 11.10, Debian, and (Ubuntu Unity and Kubuntu 12.04) they just worked!

Forum at biblesupport.com suggests font problems with greek, but they appear independent of an OS.  Strange that the font problem exists on one version of Ubuntu and not another.

In Lubuntu 12.04 e-Sword fonts Titus cyberbitz basic greek seems to be barred out.  On 12.04 Unity it is not barred out.

Any suggestions?

Thank you

---

### Post by jonathonblake on 2012-06-15
> **ubume2 said:**
> On Lubuntu 12.04 only the SBLGNT module views properly. The Nestle-Aland 26, and others do not view properly.

What is displayed?

On my system, it looks like the wrong font encoding scheme is being used.

> On 11.10, Debian, and (Ubuntu Unity and Kubuntu 12.04) they just worked!

Whilst I don't see any obvious reasons why it would happen, I'm wondering if the window manager is affecting something in WINE?   I know that xcfe has several quirks that effect programs in ways other window managers don't.

###

Can you highlight text in Bible or Dictionary resources?

Have you found any other issues in using e-Sword on 12.04?

I've finally started stress testing 10.1.0, and found a couple of other things that work with one version of Xubuntu, but not other versions.

jonathon

---

### Post by ubume2 on 2012-06-17
Hi Jonathon,

What is displayed?
This is IGR-NT+

> (Joh 3:16)  ïõôùòG3779 ãáñG1063 FOR SO   çãáðçóåíG25 [G5656] ïG3588 LOVED   èåïòG2316 GOD   ôïíG3588 THE   êïóìïíG2889 WORLD   ùóôåG5620 ôïíG3588 THAT   õéïíG5207 áõôïõG846 HIS SON   ôïíG3588 THE   ìïíïãåíçG3439 ONLY BEGOTTEN   åäùêåíG1325 [G5656] HE GAVE,   éíáG2443 THAT   ðáòG3956 EVERYONE   ïG3588 WHO   ðéóôåõùíG4100 [G5723] BELIEVES   åéòG1519 ON   áõôïíG846 ìçG3361 HIM   áðïëçôáéG622 [G5643] MAY NOT PERISH,   áëëG235 BUT   å÷çG2192 [G5725] MAY HAVE   æùçíG2222 LIFE   áéùíéïíG166 ETERNAL. 


The strong # pop ups do render greek properly.

Yes, I can copy/paste in 12.04.

I am not able to download modules in any of them. When I had Ubuntu 10.04 I believe I could do that.  I save my modules and copy and paste them when installing a new distro, so haven't used the download option much.

I haven't noticed any other issues with E-Sword 10.1

Thanks for the effort from you and davidkt to make this most excellent app available in Linux.

---

### Post by ubume2 on 2012-06-20
greek fonts are garbled as above in Arch Linux GNOME, LXDE, and XFCE

---

### Post by jonathonblake on 2012-06-21
> **ubume2 said:**
> greek fonts are garbled as above in Arch Linux GNOME, LXDE, and XFCE

From here, it looks like a "simple" character encoding issue.

Where the issue/bug lies, I can't tell.  :(

Not all versions of WINE generate that error.  However, I could not tell which version of WINE I was using, when I didn't see that error.  :(
[Synaptic was showing that I had three different versions of WINE installed:  1.2, 1.4.2 (I think), and 1.5.6.  ]

Not all Greek resources display garbled text.  This implies that there is a difference in either the character encoding used within the resource, or how the resource was constructed.

I'm trying various options, in an attempt to find something that works.

jonathon

---

### Post by ubume2 on 2012-06-23
As I recall, I don't think I had the problem when only wine 1.0.1 and 1.2 was an option.(On 10.04).

With the newer distros 1.2 can't be installed without 1.4.

---

### Post by Drew1689 on 2012-08-01
Has anyone found a fix for this yet. I am running Ubuntu 12.04 and everything works pretty good except for the Greek fonts. Strongs works but TR+ and other Greek texts do not.

---

### Post by ubume2 on 2012-08-21
> **Drew1689 said:**
> Has anyone found a fix for this yet. I am running Ubuntu 12.04 and everything works pretty good except for the Greek fonts. Strongs works but TR+ and other Greek texts do not.

I don't know of any fix at this time.  For some reason, all of the greek modules work on my 12.04 (Unity) install, but they do not work on Lubuntu 12.04, Xubuntu 12.04.  It looks like the same version of wine is installed on all three.

These modules DO work for me on Xubuntu (to which I am slowly transitioning) and Lubuntu: SBLGNT & WH +TVM.  I think Josh authored these.  If I could get Nestle-Aland to work on Xubuntu, I would be happy.

Good luck. Keep us informed if you find one that works.

---

### Post by padeco on 2012-09-04
hi there,
i have the same issue. installed latest ubuntu and wine 1.4
greek text for GNT TR and GNT WH does not display. the strong's number are fine and commentaries also show greek text no worries. same applies for the hebrew OT (HOT+)

also, i am not able to conduct any search. has any one had any solution to these issues?
cheers,

---

### Post by jonathonblake on 2012-09-05
> **padeco said:**
> hi there,
greek text for GNT TR and GNT WH does not display.

Most of the user-created resources in Biblical languages have to be reconstructed, to display properly in e-Sword 10.1.x. The issue is that they weren't constructed correctly to begin with, but e-Sword 10.0.x, and earlier managed to overlook the faulty construction of those rsources.

When correctly constructed search can be done in Biblical languages. At least one Windows systems.  There is an issue with either e-Sword or Wine 1.4 that periodically prevents search from working as expected, when using e-Sword under Wine, and CrossOver.

jonathon

---

### Post by ubume2 on 2012-09-07
> **padeco said:**
> hi there,
i have the same issue. installed latest ubuntu and wine 1.4
greek text for GNT TR and GNT WH does not display. the strong's number are fine and commentaries also show greek text no worries. same applies for the hebrew OT (HOT+)

also, i am not able to conduct any search. has any one had any solution to these issues?
cheers,

If you used the installer script to install e-Sword, this solution might work. 

I manually installed e-Sword, rather than using the installer script, and followed instructions from this url:

[http://ubuntuforums.org/showthread.php?p=11673552#post11673552](http://ubuntuforums.org/showthread.php?p=11673552#post11673552)

The search function worked great after doing this.

Hope it helps.

---

