---
title: "X or XMir as default in Trusty?"
date: 2013-11-08
forum: Ubuntu Development Version
---

### Post by sacridex on 2013-11-08
Hello folks,

are there any news yet about X or XMir being default in 14.04?
Given that XMir is not standard in 13.10, there might be some changes about that in Trusty as well?
Especially about removing the X fallback option?

Thanks

---

### Post by grahammechanical on 2013-11-08
I would suggest that we wait until we see what comes out of UDS. I have noiticed only 3 session that might have something to say about Mir and 14.04.

_Wednesday_
General X.org plans fot T
Planning hardware enablement strategy for 14.04
[U]Thursday
[/U]Release process review and discussion.

I am not surprised that there is little being said directly about Mir. To start with the intention is for Mir and Unity 8 to be in 14.10 and not 14.04. Secondly, Mir and Unity 8 are now in Ubuntu Touch for the Phone and there now needs to be a push for Ubuntu touch for the tablet. Third, Convergence is the big target. The time to get back to MIr will be in the 14.10 development cycle.

There will be talk during UDS of getting Touch apps running under Unity 7. Some of us already have Ubuntu Web Browser running under Unity 7 on Trusty and the software centre has a download of Unity 8 shell. That brings in some of the Touch apps. They are very limited in what they can do on the desktop but this is where I see the effort being directed up the release of 14.04 and beyond with Mir being scheduled for 14.10.

As an side, I have been seeing Wayland libraries being upgraded. I do not see this as keeping the options open but more like being friendly to the neighbours.

Regards.

---

### Post by Bibek on 2013-11-21
update: They have decided to stick with the good old x and unity 7 for 14.04.

---

### Post by kansasnoob on 2013-11-21
> **Bibek said:**
> update: They have decided to stick with the good old x and unity 7 for 14.04.

+1!

That seems to be a wise decision.

---

### Post by philinux on 2013-11-22
All here.
[http://www.phoronix.com/scan.php?page=news_item&px=MTUxOTQ](http://www.phoronix.com/scan.php?page=news_item&px=MTUxOTQ)

Another take on this.
[http://arstechnica.com/information-technology/2013/11/stability-first-ubuntus-mir-wont-replace-x-in-14-04-desktop/](http://arstechnica.com/information-technology/2013/11/stability-first-ubuntus-mir-wont-replace-x-in-14-04-desktop/)

---

### Post by grahammechanical on 2013-11-22
If you are running Trusty (and we should be) then try running this command

```
grep -i xmir /var/log/Xorg.0.log
```

I get

> [    17.540] (WW) "xmir" is not to be loaded by default. Skipping. 

The trusty software centre has unity-system-compositor in it and I have installed it but it does not load the xmir module, even when unity-system-compositor is run as a command. Which is what software centre instructs to do. So, I think that the code is there in Ubuntu but it is switched off. And we know from our own testing that there are issues with proprietary videos drivers

Mir and Unity 8 are running on the phone. And Unity 8 shell is in the software centre and I am sure that I heard something about there being an option in 14.04 of bringing in Unity 8 and Mir. 

We get what we are given. Let us wait and see what we get.

Regards.

---

### Post by verymadpip on 2013-11-22
> **Bibek said:**
> update: They have decided to stick with the good old x and unity 7 for 14.04.

Fantastic!
I was startting to panic (yes, this early) about my RAT5 mouse, which currently needs an edited xorg.conf to work properly.

---

### Post by Alan F on 2013-11-22
Does this mean that we can now expect that Mir will be removed from Trusty repos and that the Devel repos will diverge and forge on with Mir and Unity 8 eventually turning into U***** (14.10) when Trusty goes mainline?

---

### Post by grahammechanical on 2013-11-22
The last time I checked my Trusty install with devel repositories updates were coming from four main repositories that were either Saucy or Trusty repositories. Without any evidence I think that things will remain this way until close to Trusty release date at which point the code base will start to divulge. I am good at guessing but not so good at guessing correctly. :)

Regards

---

### Post by fantab on 2013-11-22
As far as I know there is resistance to Mir out there, especially with 'other' developers and hardware manufacturers. Only Canonical is in favor of Mir, while most of them out there have their bets on wayland. Intel, for one, has refused to work with Mir.
If everyone sticks to their guns, we may end up with a situation where application developers may be forced to code for both Mir and Wayland to support their software. Redhat had committed itself to wayland and so have other distros, in a way.

Will application developers commit to work with both Mir and Wayland?
Will Hardware manufacturers write drivers for both Wayland and Mir?

Interesting times ahead for Linux world.

Nevermind if a bit off-topic.

Regards...

---

### Post by ventrical on 2013-11-22
There will be no Mir or Unity 8 in 14.04 (for the desktop) nor will there be any point releases during it's duration. It will all be Vanilla X.

Quoting Mark Shuttleworth:

"The question is whether we will adopt Mir and Unity 8 for the desktop in a point release of 14.04. No."

You can hear it here:

[http://www.youtube.com/watch?v=D4kHQeu4SJk](http://www.youtube.com/watch?v=D4kHQeu4SJk)


 and please start at '48:50'

 .. as we say in North America, .. 'That's all she wrote'.

Regards..

edit:

 I see that Phillinux has already adressed this :)

---

### Post by kansasnoob on 2013-11-22
> **ventrical said:**
> There will be no Mir or Unity 8 in 14.04 (for the desktop) **[COLOR="#FF0000"]nor will there be any point releases during it's duration[/COLOR]**. It will all be Vanilla X.

Quoting Mark Shuttleworth:

"The question is whether we will adopt Mir and Unity 8 for the desktop in a point release of 14.04. No."

You can hear it here:

[http://www.youtube.com/watch?v=D4kHQeu4SJk](http://www.youtube.com/watch?v=D4kHQeu4SJk)


 and please start at '48:50'

 .. as we say in North America, .. 'That's all she wrote'.

Regards..

edit:

 I see that Phillinux has already adressed this :)

As far as I know there will still be point releases during this LTS but they're reconsidering how to handle the [Hardware Enablement Stack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")  :)

I could of course be wrong because those exchanges have been in PM's ;)

---

### Post by cariboo on 2013-11-22
The way I understood it, was that there will be point releases, but none of them will include Mir and Unity 8.

---

### Post by philinux on 2013-11-22
> **cariboo907 said:**
> The way I understood it, was that there will be point releases, but none of them will include Mir and Unity 8.

+1 thats exactly what was said.

---

### Post by kansasnoob on 2013-11-22
> **cariboo907 said:**
> The way I understood it, was that there will be point releases, but none of them will include Mir and Unity 8.

Correct :D

They may also reconsider how to handle kernel stack upgrades, I mean this was kind of a nightmare:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

I'm still using 12.04.1 discs for reinstalling Precise so I don't have to deal with downgrading or upgrading the kernel or X-stack ;)

---

### Post by ventrical on 2013-11-22
> **philinux said:**
> +1 thats exactly what was said.

That's what I meant! :) lol

---

### Post by ventrical on 2013-11-22
> **cariboo907 said:**
> The way I understood it, was that there will be point releases, but none of them will include Mir and Unity 8.

 Yes.. that is what I meant. :)

 However.. as I thought about Mark's keynote, he left some doors open, in a sense , doors that would have to be opened by a community effort.  So I do not think it is unreasonable to be hopeful, depending on patches being built and that they are stable, that they(Canonical/Ubuntu) could possibly turn this around before freeze. I was trying to make some points in a similar thread about all this convergence and I think what I  will try out (just to see) is to try and load a trusty slate .iso on one of my desktops and see what happens :)lol

Regards..

edit:

Ha! .. Wrong type of format... :)

---

### Post by philinux on 2013-11-22
Mir and unity 8 are destined for 14.10.

---

### Post by Mateusz Stachowski on 2013-11-22
> **grahammechanical said:**
> If you are running Trusty (and we should be) then try running this command

```
grep -i xmir /var/log/Xorg.0.log
```

I get

```
[COLOR=#000000]*[ 17.540] (WW) "xmir" is not to be loaded by default. Skipping.*[/COLOR]
```

The trusty software centre has unity-system-compositor in it and I have installed it but it does not load the xmir module, even when unity-system-compositor is run as a command. Which is what software centre instructs to do. So, I think that the code is there in Ubuntu but it is switched off. And we know from our own testing that there are issues with proprietary videos drivers


There is a new package for installing XMir in Trusty ubuntu-desktop-mir and it pulls xserver-xorg-xmir and unity-system-compositor. When you install that package the XMir module will load.

---

### Post by grahammechanical on 2013-11-22
@Mateusz

Thank you. That was the information I was hoping someone would provide. Software Centre says: "Settings package which installs everything Ubuntu Desktop needs to use Mir (via Xmir)."

I will try it out.

Regards.

---

### Post by ventrical on 2013-11-22
> **Mateusz Stachowski said:**
> There is a new package for installing XMir in Trusty ubuntu-desktop-mir and it pulls xserver-xorg-xmir and unity-system-compositor. When you install that package the XMir module will load.


Did this and all I get new is     plugin-containe while running top.

and


```

ventrical@ventrical-desktop:~$ grep -i xmir /var/log/Xorg.0.log
[    25.027] (WW) "xmir" is not to be loaded by default. Skipping.
ventrical@ventrical-desktop:~$ 

```

---

### Post by ventrical on 2013-11-22
After reboot:

```

ventrical@ventrical-desktop:~$ top
ventrical@ventrical-desktop:~$ grep -i xmir /var/log/Xorg.0.log
[    24.583] (II) "xmir" will be loaded by default.
[    24.963] (II) LoadModule: "xmir"
[    24.964] (II) Loading /usr/lib/xorg/modules/extensions/libxmir.so
[    24.982] (II) Module xmir: vendor="X.Org Foundation"
[    27.353] (II) [XMir] Handling focus event, new_focus = TRUE
ventrical@ventrical-desktop:~$ 



```

Thanks..

---

### Post by grahammechanical on 2013-11-22
Yes, it needs a reboot or a restart of lightdm. So, Xmir is not default in Trusty but it can be made default by user choice. So, although there is no intention of bringing Mir and Unity 8 into 14.04 by point releases I would not be surprised if sometime it proves possible for the user to bring them in.

Regards.

---

### Post by Mateusz Stachowski on 2013-11-22
I don't think that it wiil be possible. Look at the XMir in 13.10 since it's release there was no new packages and the Saucy branch of Mir didn't change at all and when you look at unity-system-compositor there is only trunk branch.

I think that with the release of 14.04 they will do the same thing and move all new things to 14.10 without any updates for packages in LTS repository.

---

### Post by ventrical on 2013-11-22
> **grahammechanical said:**
> Yes, it needs a reboot or a restart of lightdm. So, Xmir is not default in Trusty but it can be made default by user choice. So, although there is no intention of bringing Mir and Unity 8 into 14.04 by point releases I would not be surprised if sometime it proves possible for the user to bring them in.

Regards.

+1

 Mark did say somthing to this effect  in keynote if I recollect correctly.. but I think he was using some fuzzy logic of sorts.


Regards..

---

### Post by ventrical on 2013-11-22
> **grahammechanical said:**
> Yes, it needs a reboot or a restart of lightdm. So, Xmir is not default in Trusty but it can be made default by user choice. So, although there is no intention of bringing Mir and Unity 8 into 14.04 by point releases I would not be surprised if sometime it proves possible for the user to bring them in.

Regards.



[http://www.youtube.com/watch?v=D4kHQeu4SJk](http://www.youtube.com/watch?v=D4kHQeu4SJk)

49:20

Mark Shuttleworth:

"Now Mir and Unity 8 are in the archive and they will become , I imagine, more and more useful and usable and by not making them part of the base release we probably have more flexability to update them so they may become usable for people, but we will certainly not switch.."


Regards..

---

### Post by grahammechanical on 2013-11-24
More accurate information than my guesses comes from a developer.

[https://lists.ubuntu.com/archives/ubuntu-devel/2013-November/037820.html](https://lists.ubuntu.com/archives/ubuntu-devel/2013-November/037820.html)

I got the link from discourse.ubuntu.com.

Regards.

---

