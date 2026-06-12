---
title: "how can I make this PC faster?"
date: 2008-08-02
forum: The Cafe
---

### Post by Exershio on 2008-08-02
I have Ubuntu 8.04 running on my mother's PC, but it's running slow as hell.

The PC's specs:
Celeron processor (I don't know the speed, how can I find it out? System Monitor only says "Celeron (Coppermine)"
256mb 133mhz RAM
ATI Radeon 7000 64mb

edit: The Computer is a Compaq Presario 5300US, if that helps.


I was thinking of upgrading the RAM to 512mb 133mhz, but I'm looking in system monitor, and RAM usage is only like 165mb used for physical and 40mb used for swap, so would more RAM even help?

I have her running a GNOME desktop because it's the most user friendly IMO and she's totally computer clueless, so I need it to be very user friendly. (So sorry, no fluxbox)

Any ideas? We can't afford a new computer right now, so that's out of the question.


edit: P.S. if anyone has any unneeded 128/256mb 133mhz sticks they dont want, I'll gladly take them :) They're expensive as hell nowadays retail, when you can even find them. Or if you know a place where I can get them at a decent price, that'd be good as well.

---

### Post by GreenN00b on 2008-08-02
Same problem is discussed here [http://ubuntuforums.org/showthread.php?t=869979](http://ubuntuforums.org/showthread.php?t=869979)

---

### Post by tamoneya on 2008-08-02
first of all amazon says that is a 1.1 GHz processor so that other posters know. 

The thing I want to increase the most on that computer is the RAM speed which unfortunately cant be upgraded.  However it is also nice to have NOTHING in swap so the 512 MB upgrade definitely wouldnt hurt: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820220138](http://www.newegg.com/Product/Product.aspx?Item=N82E16820220138)

Could we also see what the output of running "top" in terminal.  1.1 GHz should be okay but it couldnt hurt to upgrade.  Running top will show us how hard its working.  For a new CPU I would go with this one:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819116038](http://www.newegg.com/Product/Product.aspx?Item=N82E16819116038)

---

### Post by tamoneya on 2008-08-02
just saw your edit and I am now picking through my box of ram that I have scavenged and I found one labeled:
256 MB -PC100/133.  If you want it PM me.

---

### Post by tom66 on 2008-08-02
To get the CPU speed type this into the terminal:

```
cat /proc/cpuinfo
```

It will also give you other information, such as the make. You'll see something like cpu Mhz; this is the speed it is currently running at, it may be throttled. So look at the model name for the max speed.

---

### Post by Linuturk on 2008-08-02
Make sure non-essential services that are aren't using are off.

ie, 

compiz
bluetooth
cups
and others

---

### Post by Naralas on 2008-08-02
Okay, I can get XP running reasonably well on a computer with an old AMD processor and 128 or 256 megs of RAM. I cannot get Ubuntu to even open Firefox in an acceptable time (like, I could run a lap around my house, pour and drink a glass of water, and still get back in time to be pissed off with the load time)

Ubuntu is not lightweight anymore. Even Xubuntu really pushes that definition. I mean REALLY pushes that definition. It's a good OS, but small and light: nay.

Once you get it on a strong computer, sure it takes up less RAM, but thats because XP will take a bit more when it gets a bit more to optimize itself. Really, unless its a P4, don't try ubuntu, unless you want to see the flaw in Ubuntu in a very very painful way.

---

### Post by Exershio on 2008-08-02
> **Naralas said:**
> Okay, I can get XP running reasonably well on a computer with an old AMD processor and 128 or 256 megs of RAM. I cannot get Ubuntu to even open Firefox in an acceptable time (like, I could run a lap around my house, pour and drink a glass of water, and still get back in time to be pissed off with the load time)

Ubuntu is not lightweight anymore. Even Xubuntu really pushes that definition. I mean REALLY pushes that definition. It's a good OS, but small and light: nay.

Once you get it on a strong computer, sure it takes up less RAM, but thats because XP will take a bit more when it gets a bit more to optimize itself. Really, unless its a P4, don't try ubuntu, unless you want to see the flaw in Ubuntu in a very very painful way.
Yeah I noticed that. Ubuntu definitely seems slower than XP.

But really, XP is from 2001. Ubuntu is currently from 2008. You can't compare something like that. Compare Ubuntu 8.04 with Vista. :)

---

### Post by gn2 on 2008-08-02
[**Arch**]("http://www.archlinux.org/").

---

### Post by dogbert176 on 2008-08-03
Sidux is also a debian based system, that focuses on speed.
There's a XFCE-edition, that's more "light-weight" than Xubuntu.

See links below

[http://linuxgeeksunited.blogspot.com/2008/06/on-sidux-200802-xfce.html]("http://linuxgeeksunited.blogspot.com/2008/06/on-sidux-200802-xfce.html")

[http://sidux.com/]("http://sidux.com/")

---

### Post by billgoldberg on 2008-08-03
> **Exershio said:**
> I have Ubuntu 8.04 running on my mother's PC, but it's running slow as hell.

The PC's specs:
Celeron processor (I don't know the speed, how can I find it out? System Monitor only says "Celeron (Coppermine)"
256mb 133mhz RAM
ATI Radeon 7000 64mb

edit: The Computer is a Compaq Presario 5300US, if that helps.


I was thinking of upgrading the RAM to 512mb 133mhz, but I'm looking in system monitor, and RAM usage is only like 165mb used for physical and 40mb used for swap, so would more RAM even help?

I have her running a GNOME desktop because it's the most user friendly IMO and she's totally computer clueless, so I need it to be very user friendly. (So sorry, no fluxbox)

Any ideas? We can't afford a new computer right now, so that's out of the question.


edit: P.S. if anyone has any unneeded 128/256mb 133mhz sticks they dont want, I'll gladly take them :) They're expensive as hell nowadays retail, when you can even find them. Or if you know a place where I can get them at a decent price, that'd be good as well.

You can put almost any WM on there and tweak it to make it easy to use.

I suggest fluxbox.

It will run **a lot** faster.

--

Change some apps.

Use vlc instead of totem, use sonata (set up mpd first) instead of rythmbox.

Change nautilus for pcmanfm, ...

Remove unneccasary startup items in "system -> preferences -> sessions".

---

### Post by wolfen69 on 2008-08-03
computers with those specs, i have installed xubuntu 7.04 (alternate cd) with good success. speed was very acceptable.

---

### Post by RedSquirrel on 2008-08-03
> **billgoldberg said:**
> You can put almost any WM on there and tweak it to make it easy to use.

I suggest fluxbox.

It will run **a lot** faster.

I agree.

@OP:

If Fluxbox is not suitable, try something else. IceWM, or Openbox with fbpanel.

To get the most out of your system while using Ubuntu, build up from a minimal installation, for example:

[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by F1y3r3 on 2008-08-04
Openbox is easier to use, gnome is easier to configure but you can do it yourself. 
If you won't be able to find a cheap CPU or RAM maybe try this [http://www.newegg.com/Product/Product.aspx?Item=N82E16813121342](http://www.newegg.com/Product/Product.aspx?Item=N82E16813121342). It uses DDR2 which is cheaper than DDR which is cheaper than SDR.
P.S. If anyone has any unneeded SDR 133mhz sticks or Coppermine PIIIs **in Europe**, I'll gladly take them as well :)

---

### Post by gjoellee on 2008-08-04
I will suggest that moving over to Xubuntu will be much better

check out this video: [http://www.youtube.com/watch?v=_qddueXkD8E](http://www.youtube.com/watch?v=_qddueXkD8E)

---

### Post by mikjp on 2008-08-04
Ever tried [Zen computing?](http://www.zenwalk.org/). Or try some other [lightweight distro](http://lightlinux.blogspot.com/2008/06/top-10-of-lightweight-linux_24.html).

Or just remove OpenOffice and install Abiword. Remove Firefox and install Opera. Cut down unnecessary services. Is CUPS really needed? Avahi? Does your mom really need seven virtual terminals (they take up memory)? Turn off all desktop effects. Remove all unnecessary effects from GNOME (hint: gconf-editor). Who needs animated menus? Why delays before showing menu? Does she need Bluetooth services running in the background? Shadows under windows? Transparent menus?

* [Tweak Ubuntu for peak performance](http://news.cnet.com/8301-13880_3-9874006-68.html) by  Dennis O'Reilly.
* [ Ubuntu Ultimate. Tweaking Ubuntu Ultimate](http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html)
* [[http://www.ubuntugeek.com/how-to-make-gnome-menus-faster-in-ubuntu.html]How](http://www.ubuntugeek.com/how-to-make-gnome-menus-faster-in-ubuntu.html]How) to make Gnome menus Faster in Ubuntu[/url]

More ideas? 
 

Greetings,

mikko

---

### Post by chucky chuckaluck on 2008-08-04
> **Exershio said:**
> I have her running a GNOME desktop because it's the most user friendly IMO and she's totally computer clueless, so I need it to be very user friendly. (So sorry, no fluxbox)

there's nothing user-**un**friendly about fluxbox, or openbox. if you were willing to install gnome for your mother, then you could install openbox, or fluxbox. you can set up a right-click menu for her with the apps she uses. what else would she need? gnome is going to stay slow on that machine. openbox, or fluxbox, will be less slow (but still slow).

---

### Post by mikjp on 2008-08-04
> **Naralas said:**
> Okay, I can get XP running reasonably well on a computer with an old AMD processor and 128 or 256 megs of RAM. I cannot get Ubuntu to even open Firefox in an acceptable time (like, I could run a lap around my house, pour and drink a glass of water, and still get back in time to be pissed off with the load time)

I think there is something seriously misconfigured in your system. Problems with network?

I have no problems in using Firefox on a iBook 600 MHz & 384 MB RAM with Debian. 

Greetings,

mikko

---

### Post by mikjp on 2008-08-04
> **chucky chuckaluck said:**
> what else would she need? gnome is going to stay slow on that machine. openbox, or fluxbox, will be less slow (but still slow).

Add pypanel to any *box and you have a taskbar. On the other hand, IceWM's default installation has a start menu and taskbar.

---

### Post by Hallvor on 2008-08-04
Extra RAM and a lighter distro will do the trick.

I suggest using TinyMe (with Openbox). It is very light, very easy to use, has the Mandriva Control center and has a GUI for almost everything (including making a full backup of your system to a livecd).

I suggest installing a different browser from the repository than the default Opera. Kazehakase is located in the testing repository and is much lighter and better suited. Firefox is also a little lighter on RAM than Opera, i think.

---

### Post by scottuss on 2008-08-04
> **Naralas said:**
> Okay, I can get XP running reasonably well on a computer with an old AMD processor and 128 or 256 megs of RAM. I cannot get Ubuntu to even open Firefox in an acceptable time (like, I could run a lap around my house, pour and drink a glass of water, and still get back in time to be pissed off with the load time)

Ubuntu is not lightweight anymore. Even Xubuntu really pushes that definition. I mean REALLY pushes that definition. It's a good OS, but small and light: nay.

Once you get it on a strong computer, sure it takes up less RAM, but thats because XP will take a bit more when it gets a bit more to optimize itself. Really, unless its a P4, don't try ubuntu, unless you want to see the flaw in Ubuntu in a very very painful way.

+1, Ubuntu runs great on my quad core beast but on my older laptop and my grandmother's PC (which ran XP at the speed of light!) it is quite slow. 

In fact Ubuntu is a bit slower on my gradmother's PC of a better spec than my laptop. Nothing wrong with the install or services running, that's just how it is

---

### Post by mikjp on 2008-08-04
> **scottuss said:**
> +1, Ubuntu runs great on my quad core beast but on my older laptop and my grandmother's PC (which ran XP at the speed of light!) it is quite slow. 

Why compare Ubuntu of 2008 to XP released in 2001? You get a lot more functionality in Ubuntu than in an ancient XP.

I cannot see any great difference between the performance of XP and openSUSE 11.0 when using it with my "new" Pentium 2400 with 512 MB RAM.

Greetings,

mikko

---

### Post by chucky chuckaluck on 2008-08-04
> **mikjp said:**
> Add pypanel to any *box and you have a taskbar. On the other hand, IceWM's default installation has a start menu and taskbar.

the only problem with icewm is that the startmenu and the taskbar come preconfigured with some pretty odd entries. (at least it did about four months ago.)

---

### Post by scottuss on 2008-08-04
I appreciate that they are very different, all I'm saying is that a lot of people try to argue Ubuntu is faster than Windows XP, which it is not on some machines.

Don't get me wrong I prefer Ubuntu to Windows any day, I just had to point out that for my grandmother her PC is decent enough and runs Ubuntu quite slowly, thus reinforcing the fact that Ubuntu is no longer as light as it used to be

---

### Post by sharks on 2008-08-04
[http://ubuntuforums.org/showthread.php?t=850927](http://ubuntuforums.org/showthread.php?t=850927)

Dont use too much eye candy

---

### Post by mikjp on 2008-08-04
> **chucky chuckaluck said:**
> the only problem with icewm is that the startmenu and the taskbar come preconfigured with some pretty odd entries. (at least it did about four months ago.)

It takes two minutes with a text editor to get rid of the unnecessary entries and add only those needed.

-> [http://www.icewm.org/FAQ/IceWM-FAQ-4.html#ss4.1](http://www.icewm.org/FAQ/IceWM-FAQ-4.html#ss4.1)

Greetings,

Mikko

---

### Post by snowpine on 2008-08-04
Xubuntu would be noticably faster on that computer, and 99% as user-friendly. I would also recommend checking out Crunchbang, because in my opinion it is the most "mom-friendly" openbox distro out there (especially if you change the default black & white artwork to happy flowers or something).

---

