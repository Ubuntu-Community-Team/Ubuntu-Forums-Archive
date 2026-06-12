---
title: "Team Fortress 2 --&gt; Micro Stuttering"
date: 2011-06-17
forum: Wine
---

### Post by Muffel2k on 2011-06-17
Hi everyone
after a long period using Windows XP and Windows 7 I would like to go back to Ubuntu since I don't do anything beside surfing, folding (F@H) and playing some TF2. So I tried to get Team Fortress 2 up and running but I've been disappointed by unbearable stuttering.
 
_My hardware specs_
i7 2600K @ 4.6Ghz (stable overclock)
GTX 570 Windforce
8GB 1600 Ram
 
_What I have done so far_
I've been using Ubuntu 10.10 and 11.04 and Wine versions 1.2 and 1.3. For my graphics card I installed the latest Nvidia driver to ensure the latest support.
I always got Steam up and running, so far nothing special. I managed to install TF2 and connected to a server without any problem. Here it starts --> I tried different tweaks (-dxlevel 81, -gl, some entries inside the registry, vSync on and off, low details, disabling ingame community) but I always get micro stuttering (hopefully it's the right word --> I can run around on a map and every 10-15 secs my fps dropping down from 150 to 20 which results in micro stuttering)
 
_What I expect_
If neccessary I can lower the details and stuff, no problem. I would even play in a window or not, Full HD resolution or not but these micro stutterings have to go! I think it's just a small option I have to enable, a small tweak I have to do. My system should be powerful enough to compensate the performance lag caused by Wine. The option to use a dual boot system is NOT possible, had a few bad situations so I won't do it again. *g*^
 
_My idea_
Would it help to try the crossover version of TF2?
Which tweak or option did I missed?
 
Hopefully you can help me
Kind regards
Muffel2k
 
*PS:*
*Currently I have Windows 7 up and running, so it could take a few minutes to reinstall Ubuntu 10.10*

---

### Post by Muffel2k on 2011-06-20
Anyone got a clue?


Spoke with a friend and he told me Steam is working on a native Linux client (tbh I don't think so). His advice was to wait until the release it.

But why is it working for a lot of people and I got in trouble Oo
Still think about the Crossover games, are they rebuild for an easier use within Ubuntu / Linux?

---

### Post by bobwyajnr on 2011-06-20
Hi **Muffel2k**

I'm not a big fan of TF2 (actually I played it about twice :-) ) but I'll happily try and help with you little problem.

I certainly can't fault the hardware :) What's the SSD/harddisk you are running Steam off like though? Also what filesystem are you using?

Are you using Ubuntu 11.04 or 10.10?? Are you using Gnome-2/Compiz, Unity/Compiz or KDE+KVM? I would advice against using Unity for gaming - since it is known it won't be stable till the 12.04 LTS...

It is important to know what version of Wine 1.3.x you are using. Since Wine 1.3.20- onwards introduced a xinput2 patch for mouse input that subsequently broke a lot of games. This has a common characteristic of jerking mouse look across games. I believe Wine 1.3.19 is best option if this problem affects you... Or you can mess about rebuilding Wine with xinput2 off (not too hard really - since Wine now uses the wonderful Git version control system :P ).

I presume you have done the obvious stuff (undirect 3D applications in Compiz, turn off console debugging). Maybe run TF2 at higher priority?

I maintain the Steam client on Wine AppDB (OK just a glorified moderator :) ). I'm hearing a lot of people with problems running the Steam client on Unity or Gnome 3. That's just ghosting/reflected images of windows (due to the way the Steam client allocates a very large X-Y canvas to draw to). I haven't actually been following game performance recently :) It might interest you to know that the Wine-run Steam client now supports system info/hardware spec. uploading, SSL game purchases and flash-playback of game trailers :popcorn:

I can't see Valve releasing a Steam for Linux till they get some big issues sorted out (like the mess that is ALSA/Linux sound).[There were tests in the original beta/alpha Mac client source code for a Linux kernel.]("http://www.phoronix.com/scan.php?page=article&item=steam_linux_script&num=1") Valve were subsequently very vocal in quashing the rumour about a future Linux Steam client release - even in the longer term.

Sorry 'bout the waffle.
Bob

---

### Post by Muffel2k on 2011-06-20
Hey bob

I can exclude the whole hardware part. Everything is running fine except this little problem with Wine and Steam ^^

As I wrote before I was using 11.04 and 10.10 (and even 10.04) and different version of Wine (1.3.x and 1.2.x) always the same micro stuttering. Don't get me wrong, I DON'T blame Wine. Wine is a nice example how free software should be!

I have set a few registry tweaks and stuff but without success. Well I could try to give the whole process a higher priority. At the moment I am too lazy to install Ubuntu again so here is a deal:

I will write a short list what I am going to do within this week and try to collect a few tweaks. After it's I will install Ubuntu 10.04 (think it's the most stable one atm) and Wine 1.3.x ( the newest version). I get Steam up and running and log every single step to solve the stuttering problem to determine the problem.


That's my 2 cent too .... Valve won't give us an ETA ... why should they ^^

Thanks in advance
Muffel2k

---

### Post by bobwyajnr on 2011-06-20
Hmmm. Talking of re-installing again. I keep trying to role my own striped down uber kernel version and running into problems with the stupid ATI blob driver... That is an option for you if you have an Nvidia card. Strip out everything you don't need, enable the pre-emptive 1000Hz settings, etc. I had a very fast boot into the radeon mesa driver :popcorn:

I guess it would be difficult to debug TF2? If you attempt to attach the debugger to the process - it will kill performance too much for you to stay on a server. The +relay debug option would generate way too much output and slow the game down too much... Hmmm interesting problem!

I would agree about 10.04. The best release Canonical has put out. The Linux-Mint version is probably one of the most usable/functional releases out there - period. I certainly didn't feel able to switch away from Windows for daily usage - before using that version.

Rambling again... Anyway post when you have an update! :P

Bob

---

### Post by Muffel2k on 2011-06-21
Yeah I guess you wouldn't do it for just a "game" ^^
 
Well I would like to support the whole Linux (Ubuntu) community and take a break from Windows, but I need my TF2, otherwise I feel soooo naked ^^
 
ok, gonna post an update when I'm done



[U]Edit
[/U]I am only writing a few documents or excel sheets at home. Mostly I am folding or playing TF2 so eliminate Windows should be possible ... has to be possible ... must be possible ^^

---

### Post by darklegion on 2011-06-21
I don't use Ubuntu, but you should be using the 275x series nvidia drivers (which have slightly improved performance for me)

In addition, as you are using a nvidia card, disabling GLSL will likely be around 20-30% faster.
You can do it with winetricks:

```

winetricks glsl=disabled

```

Or manually with regedit:

[http://wiki.jswindle.com/index.php/Wine_Registry#GLSL](http://wiki.jswindle.com/index.php/Wine_Registry#GLSL)


Finally, it could be a CPU scheduler issue, and using BFS may or may not help with this. The CK patchset includes it:

[http://users.on.net/~ckolivas/kernel/](http://users.on.net/~ckolivas/kernel/)

I'm not sure of the procedure for installing external kernels with Ubuntu these days, although it shouldn't be too difficult.


EDIT: Performance increase for glsl=disabled was a little optimistic. It's closer to a 10-15% increase (which is still quite decent).

---

### Post by Muffel2k on 2011-06-21
Thank you ... gonna try it as soon I have Ubuntu installed again (probably at the weekend cause I want to play a little bit TF2)

---

### Post by Muffel2k on 2011-06-22
[U]First Reply

[/U]I've installed Ubuntu 10.04, the newest nVidia drivers and "Crossover Games" (which is based on the newest Wine release). After installing Steam and TF2 I connected to a server (without changing anything) and set all details to max .... NO LAGS ..... WTF?

So I will switch now to Wine and try to get it working there too ... It has to be just a small switch I have to turn on ... Will keep you updated

---

### Post by Muffel2k on 2011-06-22
_Second Reply_

Tried to get it working with the newest Wine Release but I am getting this stuttering again ... I decided to test Crossover for a week and check if it's worth to buy it ... Think I am not skilled enough (atm) to get it working with Wine


Thanks for your help :)

---

### Post by bobwyajnr on 2011-06-24
> **Muffel2k said:**
> _Second Reply_

Tried to get it working with the newest Wine Release but I am getting this stuttering again ... I decided to test Crossover for a week and check if it's worth to buy it ... Think I am not skilled enough (atm) to get it working with Wine


Thanks for your help :)

Re the research I was going to do on Deus Ex 1. I have finished my Git bisection regression test (basically a binary tree search to see which code revision breaks Wine). As many other people have confirmed the fatal one is:```

fd4ad5a60433b8314dce684b9d52f43769cd5867 is the first bad commit
commit fd4ad5a60433b8314dce684b9d52f43769cd5867
Author: Alexandre Julliard <julliard@winehq.org>
Date:   Fri May 13 12:40:19 2011 +0200

    winex11: Don't use raw events for button events so that we get the right coordinates.

:040000 040000 d046b97119984a1e2a0591144ff6ed2bc15e3ea4 465eb2f383428394793525fde1d7f7934da0d08a M	dlls
```

So basically anything after the release 1.3.19 has broken mouse input handling (technically it's actually due to an XOrg XInput2 mouse bug - but in practice Wine appears to be broken).

Would be quite happy to take you through installing Wine 1.3.19 or you can download a PPA (links available in the stickies for this subforum). TBH it's probably easier to compile the Wine source (thanks to Mr Linus Tholvald's wonderful Git thingy) than getting programs to actually work under Wine. :popcorn:

If you've got the spare cash lying around to pay for CrossOver then go for it!! :popcorn:

Bob

---

### Post by darklegion on 2011-06-25
> **Muffel2k said:**
> _Second Reply_

Tried to get it working with the newest Wine Release but I am getting this stuttering again ... I decided to test Crossover for a week and check if it's worth to buy it ... Think I am not skilled enough (atm) to get it working with Wine


Thanks for your help :)

Have you tried wine with a fresh/separate wineprefix?

For example:
```

WINEPREFIX=~/.wine.tf2 wine <filename>.exe 

```

Perhaps your wine installation is corrupted in some way, and thus is causing stuttering issues. So a new prefix would fix such an issue.

---

### Post by Muffel2k on 2011-06-27
Yeah tried it but without success :/

Played a few hours yesterday and I will buy Crossover Games .... Seems to be the best solution for me ;)

---

### Post by bobwyajnr on 2011-06-27
> **Muffel2k said:**
> Yeah tried it but without success :/

Played a few hours yesterday and I will buy Crossover Games .... Seems to be the best solution for me ;)

np

Just out of interest what version of Wine does CrossOver use for running TF2?

Thanks
Bob

---

### Post by Tweak42 on 2011-06-28
> **bobwyajnr said:**
> np

Just out of interest what version of Wine does CrossOver use for running TF2?

Thanks
Bob

CX version 10.0.0 (Jan 24) uses 1.3.9.  However the latest CX 10.1.0 (Mar 16) doesn't mention using a newer wine version, thus it probably uses a modified version of 1.3.9.

[http://www.codeweavers.com/products/cxgames/change_log/](http://www.codeweavers.com/products/cxgames/change_log/)

---

