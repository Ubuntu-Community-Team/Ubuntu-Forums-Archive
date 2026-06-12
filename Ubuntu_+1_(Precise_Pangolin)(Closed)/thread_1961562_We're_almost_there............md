---
title: "We're almost there..........."
date: 2012-04-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by PaulW2U on 2012-04-19
So:

```
paul@R720:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04 LTS
Release:        12.04
Codename:       precise

```

shows that we're almost there and the development phase is coming to an end. :p

---

### Post by ventrical on 2012-04-19
> **PaulW2U said:**
> So:

```
paul@R720:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04 LTS
Release:        12.04
Codename:       precise

```shows that we're almost there and the development phase is coming to an end. :p


...and wow .. what a ride eh ...

---

### Post by robgraves on 2012-04-19
what's an lsb module?

---

### Post by VinDSL on 2012-04-19
> **ventrical said:**
> ...and wow .. what a ride eh ...
Bah!  12.04 has been a snooze...

I can't wait for the 12.10 toolchain test builds to be uploaded!

Pre-alpha is where it's at!  :)

---

### Post by VinDSL on 2012-04-19
> **robgraves said:**
> what's an lsb module?
Nuttin' honey...

That command is just a ghetto way of sucking info out of /etc/lsb-release

```
vindsl@Zuul:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
```

---

### Post by kaldor on 2012-04-19
> **ventrical said:**
> ...and wow .. what a ride eh ...

Right on. Gonna need a stiff drink by the time 12.10 gets on the roll.

---

### Post by VinDSL on 2012-04-19
> **kaldor said:**
> Right on. Gonna need a stiff drink by the time 12.10 gets on the roll.
Chardonnay is a pleasant drug!  LoL!  :D

---

### Post by alphacrucis2 on 2012-04-19
> **VinDSL said:**
> Bah!  12.04 has been a snooze...

I can't wait for the 12.10 toolchain test builds to be uploaded!

Pre-alpha is where it's at!  :)

Actually pre alpha is often fairly boring too. The real fun will start when and if Ubuntu migrate from X to Wayland. I'm eagerly anticipating awesome breakage.

---

### Post by VinDSL on 2012-04-19
> **alphacrucis2 said:**
> Actually pre alpha is often fairly boring too.
I totally agree with you!

It doesn't get any better than pre-alpha, IMO.

The devs are regrouping, and we got the house all to ourselves.

It's the calm before the storm...  :)

---

### Post by ammofreak on 2012-04-19
Hi ):P
Go to this link for info on LSB: _[http://www.unixtutorial.org/commands/lsb_release/](http://www.unixtutorial.org/commands/lsb_release/)_

And/or go here: _[http://en.wikipedia.org/wiki/Linux_Standard_Base](http://en.wikipedia.org/wiki/Linux_Standard_Base)_

---

### Post by ranch hand on 2012-04-20
> **VinDSL said:**
> Nuttin' honey...

That command is just a ghetto way of sucking info out of /etc/lsb-release

```
vindsl@Zuul:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
```
Just information for the interested, the above command is kind of Ubuntu specific.

Running it in Debian Squeeze will give you;
```

tom@main:~$ cat /etc/lsb-release
cat: /etc/lsb-release: No such file or directory

```
which is true.  There is no such file.

Running PaulW's command gives this;
```

tom@main:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Debian
Description:    Debian GNU/Linux 6.0.4 (squeeze)
Release:    6.0.4
Codename:    squeeze

```
I have yet to find out even where it gets this info.  /etc/debian_version only gives 6.0.4.

man lsb_release gives no file(s) where the info comes from.

There is a /etc/lsb-base directory on here but it is empty.

Boils down to "lsb_release -a" should work on any lsb compliant distro.

---

### Post by Harry33 on 2012-04-20
> **ranch hand said:**
> 
...

I have yet to find out even where it gets this info.  /etc/debian_version only gives 6.0.4.

man lsb_release gives no file(s) where the info comes from.

There is a /etc/lsb-base directory on here but it is empty.

Boils down to "lsb_release -a" should work on any lsb compliant distro.

In Ubuntu it is this package:
base-files
> This package contains the basic filesystem hierarchy of a Debian system, and
 several important miscellaneous files, such as /etc/debian_version,
 /etc/host.conf, /etc/issue, /etc/motd, /etc/profile, /etc/nsswitch.conf,
 and others, and the text of several common licenses in use on Debian systems.


---

### Post by zika on 2012-04-20
What's the name for 12.10 QQ?

Update&#8321;: [http://www.omgubuntu.co.uk/2012/04/guess-the-name-of-ubuntu-12-10-and-win-an-ubuntu-t-shirt/](http://www.omgubuntu.co.uk/2012/04/guess-the-name-of-ubuntu-12-10-and-win-an-ubuntu-t-shirt/)

---

### Post by flapane on 2012-04-20
> **PaulW2U said:**
> So:

```
paul@R720:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04 LTS
Release:        12.04
Codename:       precise

```shows that we're almost there and the development phase is coming to an end. :p

Yep, I noticed it today.
Being a LTS I guess it will be my main rig for at least a couple of years.
Thank God they still let me use the good ol'style Gnome DE.
[[IMG]http://i.imgur.com/uiUKxs.jpg[/IMG]]("http://i.imgur.com/uiUKx.jpg")

---

### Post by kansasnoob on 2012-04-20
> **VinDSL said:**
> Bah!  12.04 has been a snooze...

I can't wait for the 12.10 toolchain test builds to be uploaded!

Pre-alpha is where it's at!  :)

I'd almost agree except for the improvements in both Unity and Lubuntu :)

Unity is now totally usable for me out-of-box, though I do prefer disabling the global menu, and Lubuntu 12.04 (compared to 11.10) is like the difference between a partly cloudy day and a day with continuous sunshine :D

It's even gotten a bit easier to switch to "classic" in Ubuntu so those who can't or won't adjust to Unity have another 5 years to use a classic DE :biggrin:

I know there are always corner issues with hardware, and some people will never be satisfied, but I truly think Precise owned up to it's name.

---

### Post by VinDSL on 2012-04-20
> **kansasnoob said:**
> Unity is now totally usable for me out-of-box[...]
I've never tried OOTB Ubuntu, so I'll take your word for it.  ;)

One thing my "Frankenstein's Monster" still won't do (as of yesterday) is "burn" an .iso to a USB stick, via "Startup Disk Creator".  I have to burn it in Ubu 10.10, or use UNetbootin in 12.04.

HUD is a DUD, IMO.  And, you cannot choose a background color for the Launcher.  Mysterious remnants get locked behind the panel, blah, blah, blah ... but there's no reason to go negative.

We'll fix Unity's little purple wagon in 12.10!  :D

---

### Post by Squonk07 on 2012-04-20
> **kansasnoob said:**
> ...and Lubuntu 12.04 (compared to 11.10) is like the difference between **a partly cloudy day** and a day with **continuous sunshine** :D

It's amazing the difference changing the LXPanel from dark to light can make. :)

---

### Post by jefsview on 2012-04-20
Well, 11.10 was sort of the Ubuntu Vista for any desktop.

12.04 is solid and so much faster.

-- Jeff

---

### Post by chrissywissy on 2012-04-23
> **jefsview said:**
> Well, 11.10 was sort of the Ubuntu Vista for any desktop.
 

 
Concurs with my experience. I persevered on my desktop, but I'm still looking forward to 12.04 LTS

---

### Post by VinDSL on 2012-04-24
SOURCE:  [Ubuntu Linux 12.10 'Quantal Quetzal' Is Born]("http://www.markshuttleworth.com/archives/1121")

 > *"I give you the Quantal Quetzal, soon to be dressed in tessellated technicolour, **[COLOR="DarkRed"]now open for toolchains, kernels and other pressing preparatory packages[/COLOR]**."  ~ Mark Shuttleworth, 23-MAR-2012*

---

### Post by VinDSL on 2012-04-24
> **zika said:**
> What's the name for 12.10 QQ?
Quantal Quetzal

Looks like the toolchain is going to be uploaded on 3-May.

SOURCE:  [https://wiki.ubuntu.com/QuantalQuetzal/ReleaseSchedule?action=show&redirect=QReleaseSchedule](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseSchedule?action=show&redirect=QReleaseSchedule)

---

### Post by zika on 2012-04-24
> **VinDSL said:**
> Quantal Quetzal

Looks like the toolchain is going to be uploaded on 3-May.

SOURCE:  [https://wiki.ubuntu.com/QuantalQuetzal/ReleaseSchedule?action=show&redirect=QReleaseSchedule](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseSchedule?action=show&redirect=QReleaseSchedule)
Cool! Since I'm on a trip from Friday to  6th of May I'll be on a trip for the duration of testing-withdrawal crisis... ;)

BTW name is: [COLOR=Black][COLOR=#32CD32][COLOR=#006400][COLOR=#4B0082][COLOR=Black]Quantal Quetzal... ;)[/COLOR]
[/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by VinDSL on 2012-04-24
> **zika said:**
> Cool! Since I'm on a trip from Friday to  6th of May I'll be on a trip for the duration of testing-withdrawal crisis... ;)
Heh!  "Developer Summit" aka UDS starts on 7-May.

We could go party with the devs, for a week (hop skip & jump for me - one-day drive away)...  :D

SOURCE:  [http://uds.ubuntu.com/event/](http://uds.ubuntu.com/event/)

---

### Post by Frogs Hair on 2012-04-24
It's bit of a long drive or flight for me . It's nice that the major updates have stopped for me last week . If that is the case for everyone we may almost there.

---

### Post by zika on 2012-04-24
> **VinDSL said:**
> Heh!  "Developer Summit" aka UDS starts on 7-May.

We could go party with the devs, for a week (hop skip & jump for me - one-day drive away)...  :D

SOURCE:  [http://uds.ubuntu.com/event/](http://uds.ubuntu.com/event/)It would take me a bit more than a day... ;)

---

