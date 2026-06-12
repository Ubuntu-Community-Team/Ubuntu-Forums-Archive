---
title: "Upgrade 10.04 -&gt; 12.04?"
date: 2012-06-25
forum: The Cafe
---

### Post by Duncan J Murray on 2012-06-25
Disclaimer - my laptop is a Thinkpad T40 with Mobility Radeon 7500 32MB card - it's old!

I was 'sorting out' a Windows Vista laptop for a friend of mine - and installed Ubuntu 12.04 on it.  Unfortunately, Unity 3D doesn't really run properly (not the newest machine), and Unity 2D is in fact a bit slow.  So I thought I'd give Gnome 'classic' (no compiz) a go, and I'm really impressed!  (typing from it now).  It's really not much different to gnome 2.

Which got me thinking.  My main laptop is still running 10.04 - I find gnome2 to be ideal for work.  As much as I think Unity has come a long way and shows a lot of promise, I simply find it a bit too slow still.  I don't like gnome 3 either (not that it would run), so was thinking along the lines of moving to XFCE / cinnamon / MATE / KDE.  I was going to give it a year to think about before support ran out.

My question is - Do you think gnome-session-fallback is a viable linux desktop environment for the future?  And why aren't people touting it as an alternative to unity or gnome-shell?  Is it doomed already?

---

### Post by Version Dependency on 2012-06-25
> **Duncan J Murray said:**
> My question is - Do you think gnome-session-fallback is a viable linux desktop environment for the future?

It's included in 12.04 LTS which is supported for 5 years...so it has at least a 5-year future.  So you use it if you like it.  It sounds like your hardware may be a little old to be installing anything based on Gnome on it though (this includes Gnome Shell, Unity, and Cinnamon).

A better option might be XFCE, which is a mature desktop that is in active development and isn't going anywhere.  Plus XFCE works on almost any hardware unless it's VERY ancient.  Alot of the old Gnome 2 crowd has moved over to it.

---

### Post by sudodus on 2012-06-25
> **Duncan J Murray said:**
> Disclaimer - my laptop is a Thinkpad T40 with Mobility Radeon 7500 32MB card - it's old!


I run Lubuntu 12.04 on a Thinkpad T41, and it runs quite well. I guess you can use Xubuntu too, depending on your amount of RAM. Both of these flavours of Ubuntu 12.04 are distributed with a non-pae kernel, which is necessary for my T41 (and maybe/probably for T40).

Run the following command and check in the 'capabilities' list, if pae is included or not

```
sudo lshw -class cpu
```

---

### Post by KingYaba on 2012-06-26
Try out XFCE or OpenBox.

---

### Post by drawkcab on 2012-06-26
Xubuntu or Mint with the Mate DE.

---

### Post by ExSuSEusr on 2012-06-26
> **Duncan J Murray said:**
> Disclaimer - my laptop is a Thinkpad T40 with Mobility Radeon 7500 32MB card - it's old!

I was 'sorting out' a Windows Vista laptop for a friend of mine - and installed Ubuntu 12.04 on it.  Unfortunately, Unity 3D doesn't really run properly (not the newest machine), and Unity 2D is in fact a bit slow.  So I thought I'd give Gnome 'classic' (no compiz) a go, and I'm really impressed!  (typing from it now).  It's really not much different to gnome 2.

Which got me thinking.  My main laptop is still running 10.04 - I find gnome2 to be ideal for work.  As much as I think Unity has come a long way and shows a lot of promise, I simply find it a bit too slow still.  I don't like gnome 3 either (not that it would run), so was thinking along the lines of moving to XFCE / cinnamon / MATE / KDE.  I was going to give it a year to think about before support ran out.

My question is - Do you think gnome-session-fallback is a viable linux desktop environment for the future?  And why aren't people touting it as an alternative to unity or gnome-shell?  Is it doomed already?

Because progress is the equivalent of evolution, which in turn implies change.  Unity is something new and it is the way that we need to go.  The days of "clicking the start menu" need to die.  

As more people use Unity and really give it a chance they are realizing it is actually better.  I loved Gnome, I hated Unity at first - but now?  I see it for what it is - a bit of innovation and a change in the thought process of where computing (in terms of the desktop environment) is going.  And, that is a good thing.

Problem is we humans are creatures of habit and any time you introduce a new way of accomplishing something the inevitability of resistance well...  is a given. 

But, to answer your question - the best I can - I suspect that Unity haters are gradually realizing it's actually pretty damn good and thus leaving behind the 1990's and the "start menu." -- 'scuse me... "menu button."

---

### Post by zombifier25 on 2012-06-26
> **Duncan J Murray said:**
> My question is - Do you think gnome-session-fallback is a viable linux desktop environment for the future?  And why aren't people touting it as an alternative to unity or gnome-shell?  Is it doomed already?

GNOME Classic is definitely a viable solution. However, back in 11.10 it's still damn ugly and buggy, so people are not advertising it as the best alternative to Unity, and instead urge people to switch to another DE or Mint (which IMO is too much work just for getting classic GNOME).

With 12.04 GNOME Classic is much more stable and pretty, but it will take some time before the buggy reception goes away. I like Unity, but I'll take gnome-panel over Mint anyday.

---

### Post by Myrddin Emrys on 2012-06-27
For those unconvinced by Unity (which would include the entire Linux community outside Ubuntu!) there's really no reason not to continue using Gnome 2 in its current incarnation as MATE. It's my standard desktop for 12.04 and took about 5 minutes to install, with another few minutes spent tweaking it to make the default installation look more like the 10.x environment:

[http://ubuntuforums.org/showpost.php?p=11931784&postcount=20](http://ubuntuforums.org/showpost.php?p=11931784&postcount=20)

Alternatively, Mint 13 has a nice MATE version that works well out of the box. Otherwise, I'd use Xfce (the vanilla xfce4 rather than xubuntu-desktop).

---

### Post by Duncan J Murray on 2012-07-01
> **sudodus said:**
> I run Lubuntu 12.04 on a Thinkpad T41, and it runs quite well. I guess you can use Xubuntu too, depending on your amount of RAM. Both of these flavours of Ubuntu 12.04 are distributed with a non-pae kernel, which is necessary for my T41 (and maybe/probably for T40).

Run the following command and check in the 'capabilities' list, if pae is included or not

```
sudo lshw -class cpu
```

This is something I'm going to have to check.  If it is non-pae - does that mean I won't be able to run 12.04 on it?  What if I upgrade it straight from 10.04?

---

### Post by Duncan J Murray on 2012-07-01
> **ExSuSEusr said:**
> Because progress is the equivalent of evolution, which in turn implies change.  Unity is something new and it is the way that we need to go.  The days of "clicking the start menu" need to die.  

As more people use Unity and really give it a chance they are realizing it is actually better.  I loved Gnome, I hated Unity at first - but now?  I see it for what it is - a bit of innovation and a change in the thought process of where computing (in terms of the desktop environment) is going.  And, that is a good thing.

Problem is we humans are creatures of habit and any time you introduce a new way of accomplishing something the inevitability of resistance well...  is a given. 

But, to answer your question - the best I can - I suspect that Unity haters are gradually realizing it's actually pretty damn good and thus leaving behind the 1990's and the "start menu." -- 'scuse me... "menu button."

I can see it's potential, and I've been using it for a while on my non-work laptops.  Yes, it is a change, but at the moment, I don't find it an improvement.  I've tried it on two pieces of hardware which I thought should run it ok, but found it too slow.  My main laptop is around 5 years older than those laptops!

---

### Post by Duncan J Murray on 2012-07-01
> **Myrddin Emrys said:**
> For those unconvinced by Unity (which would include the entire Linux community outside Ubuntu!) there's really no reason not to continue using Gnome 2 in its current incarnation as MATE. It's my standard desktop for 12.04 and took about 5 minutes to install, with another few minutes spent tweaking it to make the default installation look more like the 10.x environment:

[http://ubuntuforums.org/showpost.php?p=11931784&postcount=20](http://ubuntuforums.org/showpost.php?p=11931784&postcount=20)

Alternatively, Mint 13 has a nice MATE version that works well out of the box. Otherwise, I'd use Xfce (the vanilla xfce4 rather than xubuntu-desktop).

I thought MATE was still gnome2?  Isn't this going to be a problem as applications become gtk3?  gnome-session-fallback seems to be using gnome3.

---

### Post by sudodus on 2012-07-01
> **Duncan J Murray said:**
> This is something I'm going to have to check.  If it is non-pae - does that mean I won't be able to run 12.04 on it?  What if I upgrade it straight from 10.04?
Yes, if you upgrade and keep the old kernel it should work. There are other alternatives too. But vanilla Ubuntu with Unity and Gnome 3 will need more horsepower anyway to run smoothly.

The best alternatives, if you want to stay with an Ubuntu flavour OS, are Lubuntu and Xubuntu. Try them live (booted from CD or USB).

---

### Post by Myrddin Emrys on 2012-07-01
> **Duncan J Murray said:**
> I thought MATE was still gnome2?  Isn't this going to be a problem as applications become gtk3?  gnome-session-fallback seems to be using gnome3.

Fallback does use gtk3 (as does Cinnamon), while Gnome 2/MATE, Xfce and LXDE use gtk2 (at least for now). But this needn't be a problem - most applications, no matter what toolkit they are built with, will run on any desktop, provided all the required libraries are installed. This is why even the KDE  guys can run Gnome apps if they want to, and just about anything will still run under twm. Some things might look prettier on particular desktops, though.

---

### Post by Duncan J Murray on 2012-08-27
Ok, I upgraded from 10.04 to 12.04 fallback.

The upgrade went without any problems - but I'm finding the interface all a bit slow.  Things like opening and closing applications, switching windows, alt-tabbing, changing workspaces, browsing web pages.

10.04 was very fast - any ideas why this might be?  I've tried uninstalling all the unity stuff, but there's not that much difference.

Anyway, taking suggestions about xfce/lubuntu/openbox a bit more seriously now!

D

---

### Post by sudodus on 2012-09-02
> **Duncan J Murray said:**
> Ok, I upgraded from 10.04 to 12.04 fallback.

The upgrade went without any problems - but I'm finding the interface all a bit slow.  Things like opening and closing applications, switching windows, alt-tabbing, changing workspaces, browsing web pages.

[COLOR="Red"]10.04 was very fast - any ideas why this might be?[/COLOR]  I've tried uninstalling all the unity stuff, but there's not that much difference.

Anyway, taking suggestions about xfce/lubuntu/openbox a bit more seriously now!

D
The desktop environment of Ubuntu 10.04, gnome2, has changed to gnome3 in 12.04, and it needs much more 'horsepower'. Gnome2 is no longer developed and maintenance will cease.

So for old computers I suggest that you use another desktop environment.

You have two choices.

1. The simple one is to make a fresh install with Xubuntu or Lubuntu.

2. But since you succeeded with the upgrade to 12.04, you can also install the Lubuntu desktop into that. At the login screen you will get three new choices: Lubuntu, Lubuntu Netbook and Openbox.

```
sudo apt-get install lubuntu-desktop
```

It works for me, and should work for you unless you have some very special software installed, that might break it.

---

### Post by pissedoffdude on 2012-09-02
The fallback session *might* be a viable option in the future, but at the moment, I wouldn't recommend it - it's missing so many features and customization options you were given with Gnome 2.  

Instead, I think you might want to look into Xfce or you can try adding the MATE repository if you want Gnome 2 back.  If unity and Gnome 3 are running too slowly, and you really want Gnome 2, go for MATE.  Otherwise, you're free to choose what you want.  If you're open to other DE's/Window Managers, try them out and pick whichever you like/are quickest on your rig.  Personally, I really like e17 because I find it super quick and beautiful, but you really just have to try them out and pick what you like.

---

### Post by vexorian on 2012-09-02
I think fallback is more viable than XCFE if you were more used to gnome2 than XCFE. Just saying... I am using it in my netbook without further problem. The customization missing hurts a little but it is not extreme.

unity-2d and unity were just not suitable for my old netbook but gnome fallback was feeling a bit more responsive to me than old gnome2 after I upgraded from 10.04 to 12.04, but I think it might need more memory.

---

