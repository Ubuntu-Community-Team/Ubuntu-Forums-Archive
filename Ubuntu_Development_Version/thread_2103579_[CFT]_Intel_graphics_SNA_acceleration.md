---
title: "[CFT] Intel graphics SNA acceleration"
date: 2013-01-10
forum: Ubuntu Development Version
---

### Post by nomenkultur on 2013-01-10
this should have already happened so please default it to SNA and don't revert to the old one




[http://www.phoronix.com/scan.php?page=news_item&px=MTI3MTI](http://www.phoronix.com/scan.php?page=news_item&px=MTI3MTI)

---

### Post by grahammechanical on 2013-01-10
Excuse me, but are you asking this of us? We are not the developers. These decisions are not taken by us.

> "late" might also mean "for alpha2", we haven't decided yet.

That would put it from February onwards. Anyone who would benefit from an implementation of this code, can do this:

> If you want to help, one thing you can do right now is to install the xorg-edgers PPA, enable SNA, and report any SNA-specific bugs you find to upstream.

That invitation was dated: Tue Jan 8 19:33:29 UTC 2013.

Regards.

---

### Post by dino99 on 2013-01-10
Some hopes coming

[http://www.phoronix.com/scan.php?page=news_item&px=MTI3MTU](http://www.phoronix.com/scan.php?page=news_item&px=MTI3MTU)

---

### Post by tepsipakki on 2013-01-10
Hi!

  The Ubuntu X team would like people running raring on machines with Intel graphics to try the new acceleration method called 'SNA'. It should have slightly better performance and less bugs than the current default. Check this wiki page for further details on how to participate:

[http://wiki.ubuntu.com/X/Testing/IntelSNA](http://wiki.ubuntu.com/X/Testing/IntelSNA)

thanks!

---

### Post by nomenkultur on 2013-01-10
that's my bad, I just assumed... because of that post about 13.04 not showing the intel driver without mesa util and it immediately getting fixed... that 13.04 developers were reading these forums.


  
 anyone have any idea how one goes about doing what they said would help?

"                              If you want to help, one thing you can do right now is to install  the xorg-edgers PPA, enable SNA, and report any SNA-specific bugs you  find to upstream."


 edit:  just saw the ubuntu dev thread

 fell free to edit delete merge thread as you see fit

---

### Post by grahammechanical on 2013-01-10
You can find out about the PPA from here:

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa")

There are instructions. 

Regards.

---

### Post by ventrical on 2013-01-10
I am going to try this now.

---

### Post by nomenkultur on 2013-01-10
I don't have a launchpad account:

 Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)


 no issues


 
 I was, however, hoping for a more noticeable performance gain :/

---

### Post by ventrical on 2013-01-10
I'm in.

ventrical@ventrical-PY028AA-ABA-A1106N:~$ grep "SNA init" /var/log/Xorg.0.log
[    21.131] (II) intel(0): SNA initialized with gen3 backend
ventrical@ventrical-PY028AA-ABA-A1106N:~$

ventrical@ventrical-PY028AA-ABA-A1106N:~$ lspci -nn | grep VGA | sed 's/.*Intel Corporation //'
82915G/GV/910GL Integrated Graphics Controller [8086:2582] (rev 04)
ventrical@ventrical-PY028AA-ABA-A1106N:~$

---

### Post by Carlos Araujo on 2013-01-10
Inspiron-5420:~$ grep "SNA init" /var/log/Xorg.0.log
[    33.712] (II) intel(0): SNA initialized with IvyBridge backend
12.10 Quantal

---

### Post by ventrical on 2013-01-10
gtkperf with "uxa"

GtkRadioButton - time:  0.61
GtkTextView - Add text - time:  1.88
GtkTextView - Scroll - time:  0.38
GtkDrawingArea - Lines - time:  4.96
GtkDrawingArea - Circles - time:  5.35
GtkDrawingArea - Text - time:  5.97
GtkDrawingArea - Pixbufs - time:  1.70
 --- 
Total time: 37.81

gtkperf with "sna"


GtkRadioButton - time:  0.50
GtkTextView - Add text - time:  1.07
GtkTextView - Scroll - time:  0.27
GtkDrawingArea - Lines - time:  1.51
GtkDrawingArea - Circles - time:  1.55
GtkDrawingArea - Text - time:  0.73
GtkDrawingArea - Pixbufs - time:  0.18
 --- 
Total time: 15.30

so, according to gtkperf there appears to be an increase in speed, however I don't notice it by the naked eye.

---

### Post by ventrical on 2013-01-10
> **Carlos Araujo said:**
> Inspiron-5420:~$ grep "SNA init" /var/log/Xorg.0.log
[    33.712] (II) intel(0): SNA initialized with IvyBridge backend
12.10 Quantal


This is Raring Ringtail beta testing.

kind regards..

---

### Post by mcellius on 2013-01-10
Got it:

```
mdk@Savina:~$ grep "SNA init" /var/log/Xorg.0.log
[    19.125] (II) intel(0): SNA initialized with Broadwater/Crestline backend
``````
mdk@Savina:~$ uname -r
3.7.0-6-generic
mdk@Savina:~$ lspci -nn | grep VGA | sed 's/.*Intel Corporation //'
Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 03)
mdk@Savina:~$ 

```

---

### Post by cariboo on 2013-01-10
Merged two threads on the same subject.

---

### Post by grahammechanical on 2013-01-11
@nomenkultur

We do not need a Launchpad account to test. Just join in any way you can. To make a bug report we do need a Launchpad account. And it is easy to get one. Just need an email address.

[https://help.launchpad.net/YourAccount/NewAccount]("https://help.launchpad.net/YourAccount/NewAccount")

Regards

---

### Post by nomenkultur on 2013-01-11
thanks graham but I'm not tech savy enough to go into launchpad.

 anyway here are my numbers:

[    26.086] (II) intel(0): SNA initialized with Broadwater/Crestline backend


GtkEntry - time:  0.06
GtkComboBox - time:  1.00
GtkComboBoxEntry - time:  0.59
GtkSpinButton - time:  0.10
GtkProgressBar - time:  0.23
GtkToggleButton - time:  0.44
GtkCheckButton - time:  0.10
GtkRadioButton - time:  0.16
GtkTextView - Add text - time:  0.71
GtkTextView - Scroll - time:  0.10
GtkDrawingArea - Lines - time:  0.67
GtkDrawingArea - Circles - time:  0.70
GtkDrawingArea - Text - time:  0.28
GtkDrawingArea - Pixbufs - time:  0.03
 --- 
Total time:  5.18


 I'd be lying if I say that I can notice any huge improvement or difference but everything is nice and stable so there's that...

 kernel 3.8 had a much more significant impact as now dash is much smoother for me

---

### Post by cariboo on 2013-01-11
My gtkperf results dropped by better than 10 seconds after enabling SNA, on my Atom powered COmpaq netbook.

---

### Post by John_Swing on 2013-01-11
I can't tell the difference but performance in gtkperf is indeed better for me too with SNA activated :

[4.979] (II) intel(0): SNA initialized with IvyBridge backend
3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)

- Without SNA :
GtkEntry - time:  0.02
GtkComboBox - time:  0.77
GtkComboBoxEntry - time:  0.31
GtkSpinButton - time:  0.06
GtkProgressBar - time:  0.14
GtkToggleButton - time:  0.41
GtkCheckButton - time:  0.07
GtkRadioButton - time:  0.10
GtkTextView - Add text - time:  0.54
GtkTextView - Scroll - time:  0.06
GtkDrawingArea - Lines - time:  0.68
GtkDrawingArea - Circles - time:  0.69
GtkDrawingArea - Text - time:  0.68
GtkDrawingArea - Pixbufs - time:  0.11
 --- 
Total time:  4.64

- With SNA :
GtkEntry - time:  0.02
GtkComboBox - time:  0.44
GtkComboBoxEntry - time:  0.26
GtkSpinButton - time:  0.06
GtkProgressBar - time:  0.09
GtkToggleButton - time:  0.26
GtkCheckButton - time:  0.08
GtkRadioButton - time:  0.12
GtkTextView - Add text - time:  0.44
GtkTextView - Scroll - time:  0.05
GtkDrawingArea - Lines - time:  0.26
GtkDrawingArea - Circles - time:  0.23
GtkDrawingArea - Text - time:  0.15
GtkDrawingArea - Pixbufs - time:  0.02
 --- 
Total time:  2.48

---

### Post by ventrical on 2013-01-11
@cariboo907&John_swing

How many 'rounds' do you have your default gtkperf set for??

thanks in advance

---

### Post by John_Swing on 2013-01-11
@ventrical

It was 100 rounds for me, the default value.

---

### Post by ventrical on 2013-01-11
> **John_Swing said:**
> @ventrical

It was 100 rounds for me, the default value.


Thanks .. thats what I have also.

---

### Post by John_Swing on 2013-01-11
@Ventrical

The difference between my result of gtkperf and yours seems huge! What kind of machine did you run it on? (If I may ask)

---

### Post by cariboo on 2013-01-11
> **ventrical said:**
> @cariboo907&John_swing

How many 'rounds' do you have your default gtkperf set for??

thanks in advance

I just use the default 100 rounds.

I just finished installing the Gnome-Remix, and updating to Raring, then enabling the staging ppa. There are still a few things that need sorting, but I really don't see much difference in overall performance when compared to Unity without SNA enabled.

---

### Post by ventrical on 2013-01-11
> **John_Swing said:**
> @Ventrical

The difference between my result of gtkperf and yours seems huge! What kind of machine did you run it on? (If I may ask)

  I am using 11 different machines. Those previous results came off an HPa1106n which has a slower Intel card (but is faster with sna.) I can't use my nvidia machine because the test is not designed for that.  I am now testing my Dell D 3100 and there is an increase here also. Only 3.GHz.

 with sna

GtkEntry - time:  0.08
GtkComboBox - time:  3.33
GtkComboBoxEntry - time:  1.64
GtkSpinButton - time:  0.32
GtkProgressBar - time:  0.64
GtkToggleButton - time:  1.57
GtkCheckButton - time:  0.26
GtkRadioButton - time:  0.43
GtkTextView - Add text - time:  1.16
GtkTextView - Scroll - time:  0.27
GtkDrawingArea - Lines - time:  1.94
GtkDrawingArea - Circles - time:  2.37
GtkDrawingArea - Text - time:  1.00
GtkDrawingArea - Pixbufs - time:  0.26
 --- 
Total time: 15.28
on Dell D 3100

With "uxa"
GtkTextView - Add text - time:  1.44
GtkTextView - Scroll - time:  0.29
GtkDrawingArea - Lines - time:  3.77
GtkDrawingArea - Circles - time:  4.65
GtkDrawingArea - Text - time:  2.01
GtkDrawingArea - Pixbufs - time:  0.80
 --- 
Total time: 24.63
and I just noticed that uxa will not include a lot of the tests that sna did.

---

### Post by ventrical on 2013-01-11
> **cariboo907 said:**
> I just use the default 100 rounds.

I just finished installing the Gnome-Remix, and updating to Raring, then enabling the staging ppa. There are still a few things that need sorting, but I really don't see much difference in overall performance when compared to Unity without SNA enabled.


  I got about the same 10 second improvement with "sna" but my machines are a little bit older so I expect some  large diff with some of the users here who have faster machines.

Thanks.

---

### Post by watsbe on 2013-01-11
This seems unnaturally fast. It's not a particularly high-spec machine.

3.8.0-0-generic

2nd Generation Core Processor Family Integrated Graphics Controller [8086:0102] (rev 09)

GtkPerf 0.40 - Starting testing: Sat Jan 12 11:20:51 2013

GtkEntry - time:  0.02
GtkComboBox - time:  0.48
GtkComboBoxEntry - time:  0.27
GtkSpinButton - time:  0.04
GtkProgressBar - time:  0.04
GtkToggleButton - time:  0.13
GtkCheckButton - time:  0.04
GtkRadioButton - time:  0.07
GtkTextView - Add text - time:  0.37
GtkTextView - Scroll - time:  0.05
GtkDrawingArea - Lines - time:  0.26
GtkDrawingArea - Circles - time:  0.23
GtkDrawingArea - Text - time:  0.14
GtkDrawingArea - Pixbufs - time:  0.01
 --- 
Total time:  2.17

---

### Post by cariboo on 2013-01-11
The only system I have with Intel graphics is my Atom N270 powered netbook. Here are the results I got.

Without SNA:

```
GtkPerf 0.40 - Starting testing: Fri Jan 11 19:33:43 2013

GtkEntry - time:  0.42
GtkComboBox - time:  4.88
GtkComboBoxEntry - time:  3.25
GtkSpinButton - time:  1.05
GtkProgressBar - time:  1.09
GtkToggleButton - time:  1.26
GtkCheckButton - time:  0.53
GtkRadioButton - time:  0.77
GtkTextView - Add text - time:  1.34
GtkTextView - Scroll - time:  1.06
GtkDrawingArea - Lines - time:  5.64
GtkDrawingArea - Circles - time: 10.89
GtkDrawingArea - Text - time:  4.34
GtkDrawingArea - Pixbufs - time:  0.46
 --- 
Total time: 36.99
```

With SNA:

```
GtkPerf 0.40 - Starting testing: Fri Jan 11 19:28:48 2013

GtkEntry - time:  0.42
GtkComboBox - time:  4.78
GtkComboBoxEntry - time:  3.69
GtkSpinButton - time:  1.08
GtkProgressBar - time:  1.08
GtkToggleButton - time:  1.25
GtkCheckButton - time:  0.53
GtkRadioButton - time:  0.71
GtkTextView - Add text - time:  0.97
GtkTextView - Scroll - time:  0.97
GtkDrawingArea - Lines - time:  4.24
GtkDrawingArea - Circles - time:  4.14
GtkDrawingArea - Text - time:  1.64
GtkDrawingArea - Pixbufs - time:  0.15
 --- 
Total time: 25.65
```

---

### Post by ventrical on 2013-01-12
> **cariboo907 said:**
> The only system I have with Intel graphics is my Atom N270 powered netbook. Here are the results I got.

Without SNA:

```
GtkPerf 0.40 - Starting testing: Fri Jan 11 19:33:43 2013

GtkEntry - time:  0.42
GtkComboBox - time:  4.88
GtkComboBoxEntry - time:  3.25
GtkSpinButton - time:  1.05
GtkProgressBar - time:  1.09
GtkToggleButton - time:  1.26
GtkCheckButton - time:  0.53
GtkRadioButton - time:  0.77
GtkTextView - Add text - time:  1.34
GtkTextView - Scroll - time:  1.06
GtkDrawingArea - Lines - time:  5.64
GtkDrawingArea - Circles - time: 10.89
GtkDrawingArea - Text - time:  4.34
GtkDrawingArea - Pixbufs - time:  0.46
 --- 
Total time: 36.99
```With SNA:

```
GtkPerf 0.40 - Starting testing: Fri Jan 11 19:28:48 2013

GtkEntry - time:  0.42
GtkComboBox - time:  4.78
GtkComboBoxEntry - time:  3.69
GtkSpinButton - time:  1.08
GtkProgressBar - time:  1.08
GtkToggleButton - time:  1.25
GtkCheckButton - time:  0.53
GtkRadioButton - time:  0.71
GtkTextView - Add text - time:  0.97
GtkTextView - Scroll - time:  0.97
GtkDrawingArea - Lines - time:  4.24
GtkDrawingArea - Circles - time:  4.14
GtkDrawingArea - Text - time:  1.64
GtkDrawingArea - Pixbufs - time:  0.15
 --- 
Total time: 25.65
```


Thanks cariboo907. :) I don't feel so bad now :)

---

### Post by serdotlinecho on 2013-01-12
OK, here's another gtkperf results on netbook ):P

Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller [8086:a011]

[http://paste.ubuntu.com/1523623/](http://paste.ubuntu.com/1523623/)

---

### Post by Alan F on 2013-01-12
SNA enabled OK. No problems noted to date.

alan@ubuntu:~$ uname -r
3.8.0-0-generic

alan@ubuntu:~$ lspci -nn | grep VGA | sed 's/.*Intel Corporation //'
Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)


Gtkperf &#8211; UXA

GtkPerf 0.40 - Starting testing: Sat Jan 12 14:56:02 2013 

GtkEntry - time:  0.02 
GtkComboBox - time:  0.73 
GtkComboBoxEntry - time:  0.32 
GtkSpinButton - time:  0.08 
GtkProgressBar - time:  0.15 
GtkToggleButton - time:  0.20 
GtkCheckButton - time:  0.06 
GtkRadioButton - time:  0.07 
GtkTextView - Add text - time:  0.52 
GtkTextView - Scroll - time:  0.16 
GtkDrawingArea - Lines - time:  0.89 
GtkDrawingArea - Circles - time:  1.16 
GtkDrawingArea - Text - time:  0.84 
GtkDrawingArea - Pixbufs - time:  0.14 
 --- 
Total time:  5.35 

Gtkperf &#8211; SNA

alan@ubuntu:~$ grep "SNA init" /var/log/Xorg.0.log
[     5.429] (II) intel(0): SNA initialized with Broadwater/Crestline backend

GtkPerf 0.40 - Starting testing: Sat Jan 12 15:11:20 2013

GtkEntry - time:  0.03
GtkComboBox - time:  0.42
GtkComboBoxEntry - time:  0.36
GtkSpinButton - time:  0.06
GtkProgressBar - time:  0.07
GtkToggleButton - time:  0.12
GtkCheckButton - time:  0.05
GtkRadioButton - time:  0.07
GtkTextView - Add text - time:  0.44
GtkTextView - Scroll - time:  0.09
GtkDrawingArea - Lines - time:  0.70
GtkDrawingArea - Circles - time:  0.71
GtkDrawingArea - Text - time:  0.19
GtkDrawingArea - Pixbufs - time:  0.02
 --- 
Total time:  3.32

---

### Post by nomenkultur on 2013-01-12
strange how Alan has the same exact chip (a gm45 I take it) and has better results than I do :/

 still I can't complain

 since they included mesa util and tweaked the intel driver my performance has gone from terrible to acceptable

[http://youtu.be/qNxrP3BI_DE](http://youtu.be/qNxrP3BI_DE)

[http://youtu.be/u1y8_XpVkwU](http://youtu.be/u1y8_XpVkwU)

---

### Post by pqwoerituytrueiwoq on 2013-01-12
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1098955](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1098955)
anyone able to reproduce it?

---

### Post by Starks on 2013-01-13
I've been using SNA for months on Sandybridge.

Aside from ocassional visual artifacts on progress bars with the Ambiance theme, it's great and stable.

---

### Post by dino99 on 2013-01-18
Canonical decision : SNA activation coming next week

[https://lists.ubuntu.com/archives/ubuntu-devel/2013-January/036339.html](https://lists.ubuntu.com/archives/ubuntu-devel/2013-January/036339.html)

---

### Post by ft_ on 2013-01-18
great !

testing SNA for integrated intel graphics causes (for my case) :
- a faster graphic experience ;
- the end of the Gnome-shell's black-background bug when showing windows with the hot top-left corner ;
- the end of the slow scroll of bookmarks menu in Firefox.

So, "trying it is keeping it" as we say in french...

---

### Post by mcellius on 2013-01-18
I've been testing SNA, too, on a four-year-old laptop, and it's been great.  It's been flawless as far as I'm concerned: fast, stable, error-free.  I also run 12.04LTS and 12.10, and 13.04 is much better than either of those, largely due to SNA.  (And also because of those annoying error messages in the other two.)

I'm looking forward to seeing how SNA works with 12.10 and 12.04, too.

---

### Post by kevpan815 on 2013-01-19
Most of the Ubuntu Employees do NOT read these Forums, as this is a Peer to Peer Forum, NOT a Peer to Ubuntu Forum. These Forums are simply here for users to get help from other users when they have a problem with the Alpha/Beta and usually even the Moderators in this Special Forum are NOT actual Ubuntu Employees either. With that said, welcome to the Ubuntu Plus 1 Forum. :D

---

### Post by ft_ on 2013-01-19
yeah yeah yeah...
In my case, it does matter to read some other raring users talking about their SNA experience and about the SNA Canonical testing (-> experience added to the OFFICIAL Canonical SNA wiki).
;)

---

### Post by BigCityCat on 2013-01-19
[    25.848] (II) intel(0): SNA initialized with SandyBridge backend

2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)

Just for some real world differences. Using Kubuntu 12.10 I notice some better rendering on desktop widgets. Also I have been using citrix with some rendering glitches that are now gone after enabling xorg edgers ppa. Definitely better Citrix performance.

---

### Post by kevpan815 on 2013-01-20
Message for NoMenkultur: The Ubuntu Developer's usually do NOT read these Forums as mentioned in one of the Sticky's above. Therefore, if you want something fixed, you have to file a Bug Report with Launch Pad.

---

### Post by kevpan815 on 2013-01-20
> **ft_ said:**
> yeah yeah yeah...
In my case, it does matter to read some other raring users talking about their SNA experience and about the SNA Canonical testing (-> experience added to the OFFICIAL Canonical SNA wiki).
;)

Just make sure that you still file Bug Reports.

---

### Post by ft_ on 2013-01-20
About that : does someone use multi screen with SNA ?
I do have issues :
- screens confusion with hdmi output (=> I cannot uncheck "mirrored monitors" without bad display) ;
- black background with hot-corner (G-Shell) and some glitches with VGA (working ok though).

---

### Post by kevpan815 on 2013-01-20
> **ft_ said:**
> About that : does someone use multi screen with SNA ?
I do have issues :
- screens confusion with hdmi output (=> I cannot uncheck "mirrored monitors" without bad display) ;
- black background with hot-corner (G-Shell) and some glitches with VGA (working ok though).

I don't know if I have SNA, but you just helped me figure out what my Crashing Problem was with Today's Nightly Build, Second Monitor Plugged In.

---

### Post by brainwash on 2013-01-20
SNA in combination with dual monitor setup and/or compositing tends to freeze my system at some point. The minor visual glitches aren't a big deal, but for now I had to switch back to UXA.

Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

---

### Post by JMB74 on 2013-01-21
[https://launchpad.net/ubuntu/raring/+source/xserver-xorg-video-intel/2:2.20.19-0ubuntu1](https://launchpad.net/ubuntu/raring/+source/xserver-xorg-video-intel/2:2.20.19-0ubuntu1)

Now enabled.

---

### Post by ft_ on 2013-01-21
yep, I removed the sna xorg.conf and
grep "SNA init" /var/log/Xorg.0.log
gives the right SNA answer anyway.
I did not test it again with multi-screen.

---

### Post by Starks on 2013-01-22
USC progress bars with Ambiance are very hit-and-miss.

---

### Post by pqwoerituytrueiwoq on 2013-02-03
still having issues with my Intel B970 and SNA
using xubuntu 13.04 daily iso (03-03-2013)

---

