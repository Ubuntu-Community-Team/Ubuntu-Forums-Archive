---
title: "Beta back to Beautiful and Punchy"
date: 2012-09-07
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-09-07
Beta 1 has really turned around. Unity desktop is comming out boom, boom , boom!!

Install <alongside> went seamlessly on this WDC WD400-AB-32BVA0 hdd.
EDIT: (That is Ubiquity appears to have it's act together.)

```

ventrical@ventrical-P4M266A-8237:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0a.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV350 AQ [Radeon 9600]
01:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI RV350 AQ [Radeon 9600] (Secondary)
ventrical@ventrical-P4M266A-8237:~$ 

```

An awesome experience.

---

### Post by wojox on 2012-09-07
> **ventrical said:**
> An awesome experience.

+1 very quick and snappy. My Firefox is much more responsive it seems. :popcorn:

---

### Post by jerrylamos on 2012-09-07
> **ventrical said:**
> Beta 1 has really turned around. Unity desktop is comming out boom, boom , boom!!

Maybe on your setup.  It was slug slug keyboard response on this 1366x768 TV VGA until I did:

#!/bin/bash
xrandr --newmode "1366x768_60.00"   85.25  1366 1440 1576 1784  768 771 781 798 -hsync +vsync
xrandr --addmode VGA1 "1366x768_60.00"
xrandr --output VGA1 --mode "1366x768_60.00"

and rebooted a couple times.  Took a little while to settle down.  Now running just like the A3 partition.

What goes boom boom on my pc's is LXDE.  Now the Marketing folks direction is for a very fancy book cover.  Some of us think once the book is open, the cover should get out of the way....

Running unity at the moment to check out some bugs.

---

### Post by jerrylamos on 2012-09-07
Just for giggles put firefox window side by side with a terminal window running "top".

With Unity, Xorg + Compiz ran 15% to 30% CPU doing somme usual internet stuff.

With LXDE, Xorg ran anywhere from 1% to maybe 15% CPU.  0% Compiz.

I don't have a print out.

Not that this matters to anyone but me, just interesting.

Back to Unity to check out some ubuntu bugs.  I don't have any with LXDE.

---

### Post by ventrical on 2012-09-07
> **jerrylamos said:**
> Maybe on your setup.  It was slug slug keyboard response on this 1366x768 TV VGA until I did:

#!/bin/bash
xrandr --newmode "1366x768_60.00"   85.25  1366 1440 1576 1784  768 771 781 798 -hsync +vsync
xrandr --addmode VGA1 "1366x768_60.00"
xrandr --output VGA1 --mode "1366x768_60.00"

and rebooted a couple times.  Took a little while to settle down.  Now running just like the A3 partition.

What goes boom boom on my pc's is LXDE.  Now the Marketing folks direction is for a very fancy book cover.  Some of us think once the book is open, the cover should get out of the way....

Running unity at the moment to check out some bugs.

 Could you put up your lspci

Thanks.

---

### Post by ventrical on 2012-09-07
> **wojox said:**
> +1 very quick and snappy. My Firefox is much more responsive it seems. :popcorn:

They have smooth scrolling now set to default. That is working a lot better.

 The workspace switcher  has a smoother transition.


 The dash icons scroll almost like Unity 2D, a lot smoother there.

 The Unity Panel icons have smoother definition when downsized.

---

### Post by BigSilly on 2012-09-07
Just installed the beta to a bootable USB, but when I try to boot the PC from it, I get a garbled mess and I can't do anything. I get the usual Ubuntu Plymouth screen, but when it gets past that the desktop is just a mishmash of icons from my actual OS that I have installed on my PC! I have to do a hard reboot to shut down. This happened when I tried this the other day with a daily build. I thought nothing of it and put it down to early teething problems, but now with the beta I'm very surprised that I'm still having the issue.

---

### Post by cariboo on 2012-09-07
@jerrylamos, just out of curiosity, what does cpu usage look like when running Windows (notice how I spelled it right) on that netbook, and it is the full version, or the Starter Edition?

---

### Post by jerrylamos on 2012-09-07
> **cariboo907 said:**
> @jerrylamos, just out of curiosity, what does cpu usage look like when running Windows (notice how I spelled it right) on that netbook, and it is the full version, or the Starter Edition?

It's Windows 7 Starter with lots of applications, Skype, Picasa, I don't know what all Asus put in it.  I run it so rarely I don't know how to check the cpu usage.  Any clue? I could try. 

I'm on my amd64 wide screen notebook/external monitor now, and it's Windows 7 hard drive is in a box somewhere.  Ubuntu development updates kept fouling up grub causing a bunch of recovery including once re-install from 4 DVD's so I just put in another SATA with only linux on it.  I haven't run Super Grub2 for recovery since A3 came out, Ubiquity bugs.

I do wonder how "ubuntu/unity everywhere" will run on tablet, pods, smart phones, ...  My current Android versions run O.K. with less hardware than I've seen some of the Quantal unity users quote.

---

### Post by jerrylamos on 2012-09-07
While I'm on it, this is a AMD dual processor E350 running amd64 Unity Beta 1 with 2G memory and AMD Radeon HD6310.

laptop screen is off.  External monitor 1289x1024 HP.

Firefox window looking at this forum with Bookmarks displayed, slowly scrolling up and down Compiz about 8% or so Xorg up around 30% or a little higher, according to "top".  Haven't tried LXDE.  It's installed.

---

### Post by cariboo on 2012-09-07
> **jerrylamos said:**
> It's Windows 7 Starter with lots of applications, Skype, Picasa, I don't know what all Asus put in it.  I run it so rarely I don't know how to check the cpu usage.  Any clue? I could try. 

I'm on my amd64 wide screen notebook/external monitor now, and it's Windows 7 hard drive is in a box somewhere.  Ubuntu development updates kept fouling up grub causing a bunch of recovery including once re-install from 4 DVD's so I just put in another SATA with only linux on it.  I haven't run Super Grub2 for recovery since A3 came out, Ubiquity bugs.

I do wonder how "ubuntu/unity everywhere" will run on tablet, pods, smart phones, ...  My current Android versions run O.K. with less hardware than I've seen some of the Quantal unity users quote.

The standard Windows Ctrl-Alt-Del will allow you to open the Task Manager to allow you to check your resource usage.

I can see why you rarley use Windows, because of the Starter Edition, I had a customer that purchased an HP netbook with it installed, within 2 weeks she had given it to her daughter and purchased a full sized laptop. :)

---

### Post by jerrylamos on 2012-09-07
> **ventrical said:**
> Could you put up your lspci

Thanks.1Asus Aspire 1 netbook 

Dual processors, both
Intel(R) Atom(TM) CPU N455   @ 1.66GHz

MemTotal:        1016268 kB

 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller

lspci is attached I think.

---

### Post by ventrical on 2012-09-08
> **jerrylamos said:**
> 1Asus Aspire 1 netbook 

Dual processors, both
Intel(R) Atom(TM) CPU N455   @ 1.66GHz

MemTotal:        1016268 kB

 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller

lspci is attached I think.

 I am not sure that this would apply to you , but I found this:

[https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+question/196239](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+question/196239)

 I  have a Dell Opti GX27G  (as 1 of my machines) and it worked great up until Oneiric when all of a sudden Unity 3D would just not load up. The graphics chip was not longer supported. Lubuntu and Xubuntu work great though.

---

### Post by rigel4 on 2012-09-08
+1 I have to agree, the experience for me so far is really good.

---

### Post by jerrylamos on 2012-09-08
Benchmarks - I used them extensively with IBM mainframe computers where development was very interested in performance results.  I don't know what if anything ubuntu development uses for performance evaluation.  

I tried gtkperf with ubuntu for a while which showed some xorg and ubuntu performance problems and regressions with updates and releases however I stopped doing that when there was no visible interest from ubuntu development.

I do notice some differences with different desktops on quantal and quantal vs. precise 2D however since development isn't interested I don't waste any time on it.  I stick to bugs reportable to launchpad that an ordinary user would see.

---

### Post by grahammechanical on 2012-09-08
As a live CD Beta 1 is a 2 out of 3 failure as far as I am concerned. I have not installed it yet but I still need to select the nomodeset option to get to the live CD desktop top.

As a test I just ran the live CD versions of 10.0.4; 11.10 and 12.4.1 and If I leave them to do their stuff I get to the warty-final-ubuntu background screen with the option to Try or to Install. If I select Try, then I get a working desktop. There is no need to select nomodeset as a boot option.

Until this is fixed then the ordinary user will have a bad experience trying out quantal beta 1 and that is not good.

Regards.

---

### Post by jerrylamos on 2012-09-08
> **grahammechanical said:**
> As a live CD Beta 1 is a 2 out of 3 failure as far as I am concerned. I have not installed it yet but I still need to select the nomodeset option to get to the live CD desktop top.I mistakenly thought ubuntu/ubiquity would be dead pipe simple and iron bound solid.  My impression, not so.  Development seeems to be concentrating on making ubiquity a marketing tool with fancy slide show instead of making sure install will work on lots of configurations that will run ubuntu once installed.  Usual rebuttal I get on this forum, "this is still develoment better things are coming."  Over the past 6 years, sometimes.

---

### Post by ventrical on 2012-09-08
> **grahammechanical said:**
> As a live CD Beta 1 is a 2 out of 3 failure as far as I am concerned. I have not installed it yet but I still need to select the nomodeset option to get to the live CD desktop top.

As a test I just ran the live CD versions of 10.0.4; 11.10 and 12.4.1 and If I leave them to do their stuff I get to the warty-final-ubuntu background screen with the option to Try or to Install. If I select Try, then I get a working desktop. There is no need to select nomodeset as a boot option.

Until this is fixed then the ordinary user will have a bad experience trying out quantal beta 1 and that is not good.

Regards.


Obviously there is a video-driver detect problem going on.  I do not understand why the developers who compile the image just don't take that part of the snapshot from Precise or a  previous stable and start from there.? Make no sense to me.

---

### Post by MG&amp;TL on 2012-09-08
> **ventrical said:**
> Obviously there is a video-driver detect problem going on.  I do not understand why the developers who compile the image just don't take that part of the snapshot from Precise or a  previous stable and start from there.? Make no sense to me.

Rule 1 of *coding while depending on other code* - you can't just mix versions and hope it will work. Code tends to be fragile like that. :)

Unless I misunderstand you?

---

### Post by smartboyhw on 2012-09-08
> **MG&TL said:**
> Rule 1 of *coding while depending on other code* - you can't just mix versions and hope it will work. Code tends to be fragile like that. :)

Unless I misunderstand you?
Well editing a bit of things shouldn't be difficult.

---

### Post by ventrical on 2012-09-08
> **MG&TL said:**
> Rule 1 of *coding while depending on other code* - you can't just mix versions and hope it will work. Code tends to be fragile like that. :)

Unless I misunderstand you?

 The LTS versions have <sub_routines> that work.!! You take the working sub-routine and patch it to the newer version. If  the code is *that* fragile then it should not even be used. I highly doubt that there are trying to re-write Ubiquity. This problem has been systemic for the most part, even during Lucid testing. Why, all of a sudden, during Beta 2 it's starts to work is beyond me.

  All I have to say is: "Linux for Human Beings - not Linux for Turing Machines!"

---

### Post by GreatDanton on 2012-09-08
Beta is really more stable then previous versions. I was lucky because almost everything worked out of the box even in Alpha. However after I installed the latest updates I noticed that it took more time to shutdown (before about 3 seconds, now about 15 seconds), and processors are sometimes busy, even if I am not doing anything special (like writing here). Anyone noticed same thing?

Regards.

---

### Post by MG&amp;TL on 2012-09-08
> **smartboyhw said:**
> Well editing a bit of things shouldn't be difficult.

No, but if you're trying to make it even better than Precise, you're not going to fix all the other bits you've broken by reverting just so you can revert to something theoretically inferior. Better to fix the bugs as instead. 

You of all people should know that. :P

---

### Post by jerrylamos on 2012-09-08
> **GreatDanton said:**
> Beta is really more stable then previous versions. I was lucky because almost everything worked out of the box even in Alpha. However after I installed the latest updates I noticed that it took more time to shutdown (before about 3 seconds, now about 15 seconds), and processors are sometimes busy, even if I am not doing anything special (like writing here). Anyone noticed same thing?

Regards.Oh, yes, as time goes on Unity and Compiz get more and more main line code, and Compiz is quite happily buzzing along even though I'm in full screen applications and nothing Compiz does is visible.  Oops, don't mean to infringe on the COC.  I have desktop choices so I do.

---

### Post by wojox on 2012-09-21
> **ventrical said:**
> The workspace switcher  has a smoother transition.
Well todays updates brought back the orange border. Must be a way to turn it off.

 > **ventrical said:**
> The dash icons scroll almost like Unity 2D, a lot smoother there.

 Finally the white has vanished from the boxes around the icons. Now light gray. Much better. :p

---

### Post by BertN45 on 2012-09-21
I have a relative old PC and I run it using Virtualbox, but it seems much slower then 12.04. I saw that to get the fading in/out it writes the window approx. 10 times. On the other side I did not see any real advantages compared to 12.04. I am a little bit old fashioned but fading windows in/out is a useless gimmick, comparable to VISTA AERO and slows the system down. Also bug reporting seems to be much slower. Note that I assign 700MB of memory to the VM and I use 3D acceleration with 32MB of memory.

I do have the feeling that the system is less reliable then the 12.04 Beta. Until two weeks ago I could not install the system here under VirtualBox nor on my Dell Inspiron 1521 laptop hardware. It has been the first time in say 4 years, that I had those type of problems.

---

### Post by mc4man on 2012-09-21
> **wojox said:**
> Well todays updates brought back the orange border. Must be a way to turn it off.

It's set in the expo options (ccsm > expo > Appearance)  though it's possible on some that changing will have no effect 
(on my main user it's white & won't change unless I reset back to unity compiz defaults

---

### Post by jbicha on 2012-09-21
> **BertN45 said:**
> I have a relative old PC and I run it using Virtualbox, but it seems much slower then 12.04. I saw that to get the fading in/out it writes the window approx. 10 times.

I believe it's because your VirtualBox doesn't support 3D graphics so Ubuntu is using software rendering (llvmpipe). The tracking bug for that is [bug 1039157]("http://pad.lv/1039157"). Using VirtualBox on an old PC is probably going to be painfully slow and 700 MB of memory isn't adequate for doing much work in Ubuntu.

---

### Post by wojox on 2012-09-22
> **mc4man said:**
> It's set in the expo options (ccsm > expo > Appearance)  though it's possible on some that changing will have no effect 
(on my main user it's white & won't change unless I reset back to unity compiz defaults

Thanks that did it. I've never messed with compiz much before. :p

---

### Post by mc4man on 2012-09-22
> **wojox said:**
> Thanks that did it. I've never messed with compiz much before. :p
If ever inclined to mess around in ccsm with stuff you're not familiar with it's sometimes better to create a new user & test/fool about there.
You can always delete that user if something goes wrong or when finished, ect.

---

### Post by Stinger on 2012-09-23
> **BertN45 said:**
> I have a relative old PC and I run it using Virtualbox, but it seems much slower then 12.04. I saw that to get the fading in/out it writes the window approx. 10 times. On the other side I did not see any real advantages compared to 12.04.
Phoronix seems to confirm your observations look here:
**[Ubuntu's Unity/Compiz Gets Even Slower]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_unity_64&num=1")**

IMHO compiz is a bad choise, hadn't had a stable release [since March 30th, 2011]("http://wiki.compiz.org/"), to many developer resources used to maintain [old dead code]("http://www.techrepublic.com/blog/opensource/rip-compiz/3402")

---

### Post by exploder on 2012-09-23
Kind of early to benchmark a release that has not gone final yet.

---

### Post by zika on 2012-09-23
> **exploder said:**
> Kind of early to benchmark a release that has not gone final yet.Nothing new. Done almost every time before... ;)

---

### Post by bird1500 on 2012-09-23
> **Stinger said:**
> Phoronix seems to confirm your observations look here:
**[Ubuntu's Unity/Compiz Gets Even Slower]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_unity_64&num=1")**

IMHO compiz is a bad choise, hadn't had a stable release [since March 30th, 2011]("http://wiki.compiz.org/"), to many developer resources used to maintain [old dead code]("http://www.techrepublic.com/blog/opensource/rip-compiz/3402")
Sure.
A Canonical dev said it's because after some code refactoring the partial repaint was broken and they didn't yet figure out how to re-implement it, maybe it's already fixed.

And yes, compiz is a hairy old dog from the times when only Nvidia's drivers were somewhat good, and as time went by compiz didn't manage well enough to remove the workarounds that aren't needed any longer. Plus trying to support a gazillion of plugins was also a bad idea.

The writing was on the wall that as drivers get better a clean up was needed for compiz too. But instead of doing a big cleanup Canonical it seems is trying to break up compiz into plugins, that's not a cure, rather a painkiller.

Using Fedora/Gnome3's compositor isn't OK for Canonical either since the folks from Gnome/fedora made it clear that they see Canonical's work (Unity) as a threat to their Gnome desktop so it didn't make sense for Canonical to base Unity on top of Gnome3's compositor.

---

### Post by BigSilly on 2012-09-23
> **bird1500 said:**
> Sure.

Using Fedora/Gnome3's compositor isn't OK for Canonical either since the folks from Gnome/fedora made it clear that they see Canonical's work (Unity) as a threat to their Gnome desktop so it didn't make sense for Canonical to base Unity on top of Gnome3's compositor.

Really? I'm not up on this. Cinnamon uses a custom version of Gnome's compositor doesn't it? Why wouldn't that be an issue for Gnome too?

---

### Post by bird1500 on 2012-09-23
> **BigSilly said:**
> Really? I'm not up on this. Cinnamon uses a custom version of Gnome's compositor doesn't it? Why wouldn't that be an issue for Gnome too?
Cinnanmon is a fork of Gnome 3 using clutter, they don't have the developer and financial power to be really independent from Gnome3 and clutter, unlike Canonical. Unity is a project from scratch using nux (instead of clutter) which is also created from scratch by Canonical.

---

### Post by BigSilly on 2012-09-23
I'm up on the differences, but what I meant was I'm not up on the politics behind them. I didn't realise that Gnome was not happy about Ubuntu using Mutter to create Unity. I thought it was all free software. I know Canonical created Unity as a Compiz plugin, but I didn't know why they did it this way.

For me, I've never had a great experience with Compiz, though I accept many have and still do. I would have preferred Ubuntu to have not really created Unity this way, and instead tailored Shell (if this is even possible) to suit, and stayed as close as possible for them to the upstream developments, especially as Gnome Shell turned out so well. I had little idea of the politics behind it all, though I was aware of some sort of fall out between Shuttleworth and Gnome.

It's all very confusing. :D

---

### Post by bird1500 on 2012-09-23
> **BigSilly said:**
>  I didn't realise that Gnome was not happy about Ubuntu using Mutter to create Unity. 
I didn't mean this.
The Gnome devs see Unity as a threat and they don't wanna cooperate on something that poses a threat to Gnome, which means they're likely to not accept random or any patches from Canonical which as time goes by might become a maintenance hell for Canonical. Hence if Canonical uses Mutter the Gnome devs won't likely argue against it, but Canonical will certainly need to tailor Mutter to its needs, and that's where it gets murky since the Gnome devs are unlikely to merge Canonical's patches upstream, so it doesn't make sense for Canonical to keep a heavily patched Mutter forever, they would rather have their own compositor.

Of course this is a simple train of thought, the reality is more complex.

---

### Post by BigSilly on 2012-09-23
It was certainly much easier back when Ubuntu just took Gnome2 and stuck a brown theme on top of it. Those were the days...

:D

---

### Post by Stinger on 2012-09-23
> **BigSilly said:**
> It was certainly much easier back when Ubuntu just took Gnome2 and stuck a brown theme on top of it. Those were the days...
Yeah now it got orange and big lenses  :biggrin: :biggrin:

---

### Post by MG&amp;TL on 2012-09-23
> **Stinger said:**
> Yeah now it got big lenses and orange  :biggrin: :biggrin:

s/orange/bright purple/

:lol:

> IMHO compiz is a bad choise, hadn't had a stable release since March 30th, 2011, to many developer resources used to maintain old dead code


Is it just me that fails to see why we couldn't:

1) Rewrite compiz from the base up to make it wayland-compatible, ironing out the issues at the same time.

OR

2) Rewrite unity to use mutter.


Neither is technically impossible.

---

### Post by ventrical on 2012-09-23
> **wojox said:**
> Well todays updates brought back the orange border. Must be a way to turn it off.

 

 Finally the white has vanished from the boxes around the icons. Now light gray. Much better. :p


  Perhaps it may seem that my comments are over-enthusiastic and I can appreciate that ccsm(compiz) may be a real horror for some but on the majority of my boxes I have had only  excellent desktop experiences. This quantal phase has certainly been a rocky ride with graphics issues and yes, results have been unpredicatable, but, it appears that from day to day the devs are trying to render Unity to a faster, smarter and lighter state. 

  Iv'e been hanging around since hardy Heron (actually a lot longer than that) :) and I have noticed Unity becoming snappier on some of the older machines that I had used in the past. I just think it is an affirmative point of interest to note.

---

### Post by ventrical on 2012-09-23
> **MG&TL said:**
> s/orange/bright purple/

:lol:




Is it just me that fails to see why we couldn't:

1) Rewrite compiz from the base up to make it wayland-compatible, ironing out the issues at the same time.

OR

2) Rewrite unity to use mutter.


Neither is technically impossible.

  Perhaps even re-write a seperate version of compiz for Unity, and/or I thought this was why they had Unity 2D fallback.  Actually it doesn't make much sense to have removed Unity 2D - but here we are now at this stage of the game. Perhaps big things for 13.04??

---

### Post by balloons on 2012-09-24
> **MG&TL said:**
> s/orange/bright purple/

:lol:




Is it just me that fails to see why we couldn't:

1) Rewrite compiz from the base up to make it wayland-compatible, ironing out the issues at the same time.

OR

2) Rewrite unity to use mutter.


Neither is technically impossible.

Remeber Ubuntu is upstream for compiz :-) Since wayland is being discussed so heavily (it's not ready for primetime), option 1 (at this point!) this likely to happen. I love the term re-write though. There's no reason to believe a re-write has to happen for compiz in order to run in wayland, nor for the more important piece, unity, to run in wayland.

---

### Post by Stinger on 2012-09-24
> **guitara said:**
> Remeber Ubuntu is upstream for compiz
I'll remember that, but where are the stable releases ? 

Or are you telling us that Compiz is now developed for Unity only, as it's own compositing window manager entirely, and support for other plugins has ceased ?

---

### Post by cariboo on 2012-09-24
> **Stinger said:**
> I'll remember that, but where are the stable releases ? 

Or are you telling us that Compiz is now developed for Unity only, as it's own compositing window manager entirely, and development for other plugins has ceased ?

Sam was the only compiz developer left, when the decision was made to use compiz instead of mutter for Unity. At the moment, he is actively looking for plugin maintainers See his blog post [here]("http://smspillaz.wordpress.com/").

---

### Post by Stinger on 2012-09-24
@cariboo907
Thanks for the link, very informative, but it seems to me that compiz is one step behind it's compeditors ?
> It also means that we’ll be able to deploy compiz on any other platform that implements OpenGL|ES 2.0.

We’re a bit late to the party on this one – KWin has had support for OpenGL|ES for about two years now, and GNOME-Shell has had it through clutter 
Regarding the status of the plugin's i found this.
> Of course, in order to port us over to OpenGL|ES, we have to use a subset of OpenGL which is common to both implementations. [COLOR="Red"]This meant that a number of plugins have been heavily altered to do this, and some plugins do not work at all at the moment. They are disabled for building and will be ported later if there is enough demand for them to work[/COLOR].
So I guess that compiz is a Unity mostly component.
The future of compiz as a stand alone component seems a bit fuzzy ?

---

### Post by MG&amp;TL on 2012-09-24
> **ventrical said:**
> Perhaps even re-write a seperate version of compiz for Unity, and/or I thought this was why they had Unity 2D fallback.  Actually it doesn't make much sense to have removed Unity 2D - but here we are now at this stage of the game. Perhaps big things for 13.04??

Yeah, it's a good thing (IMO), but a bit weird. Oh well, I guess time will tell.

> **guitara said:**
> Remeber Ubuntu is upstream for compiz :-) Since wayland is being discussed so heavily (it's not ready for primetime), option 1 (at this point!) this likely to happen. I love the term re-write though. There's no reason to believe a re-write has to happen for compiz in order to run in wayland, nor for the more important piece, unity, to run in wayland.

It's arguably ready for primetime. It works great on my machine, it just needs toolkits and things porting. Wayland itself seems to be very stable.

Of course it doesn't have to be entirely rewritten, but as it's going to need to be shaken down to the core for wayland anyway, I think it's a good idea for that to happen. Of course, it doesn't have to happen at all, (X on wayland?) but that would rather defeat the point of wayland.

---

### Post by jerrylamos on 2012-09-24
> **ventrical said:**
> ... but, it appears that from day to day the devs are trying to render Unity to a faster, smarter and lighter state ... Some of us (me) see "Unity Compiz" getting more and more complex and more and more features added 3D, animation, complex views, default shopping, music web apps, stuff I've never heard of and won't ever use, the whole candy store. I presume the idea is everything for everybody.  I don't know how this direction will pay out in the long run. I'm a bystander picking out what I'm able to, which is more like an evolution of original linux fitted to internet browsing for news and health, email, some shopping on sites of my choice.  

We've been doing pc's since 1982 pc software ever more complex since then - a bit of fresh air when linux came in, now Ubuntu is joining the ever more complex...Your choice.

Oh on the "smarter and lighter" I do see info from Ubuntu community that our "older" pc's are no longer of interest to them because they won't run unity/compiz or else they are too slow for the desired unity/compiz experience.  Your choice.  This is a full Ubuntu/unity/compiz install plus the lxde desktop, my choice at the moment.

---

### Post by BigSilly on 2012-09-25
Just tried a daily build of 12.10 on USB on my desktop (spec below). Blimey it's fast. Really fast! Really caught me by surprise. I love the slightly tweaked look, very nice, and the new shopping thing is neither here nor there really, despite the fuss.

I may be persuaded to move from Gnome Shell to this release. Might install Beta 2 on Thursday in fact.

---

### Post by ventrical on 2012-09-27
> **BigSilly said:**
> Just tried a daily build of 12.10 on USB on my desktop (spec below). Blimey it's fast. Really fast! Really caught me by surprise. I love the slightly tweaked look, very nice, and the new shopping thing is neither here nor there really, despite the fuss.

I may be persuaded to move from Gnome Shell to this release. Might install Beta 2 on Thursday in fact.


 I really appreciate everyone's veiw.  I look at the Unity 3D desktop more as an advanced assistive technology. I started my TV service apprenticeship in 1962 and have worked with all types of monitors. Through the height of the PC revolution it was mostly mono-chrome, CGA, EGA monitors etc.  I have seen lots of 'blue'.  I have seen a lot of code fly by and after a while it can really strain the eyes. So, perhaps  I meant to say that even though Unity 3D may have bugs and be somewhat resource happy with compiz, it's the easiest to look at . With a little tweaking there is a lot less strain on my eyes (and my brain) :) lol

 And yes , it is snappy .. way more snappier than any commercial program since 1995. We call  it 'uptime' in PC science. Unity provides uptime. mabey not a whole lot by some peoples standards, but enough to make it comfortable on the eyes.

---

