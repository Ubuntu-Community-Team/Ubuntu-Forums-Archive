---
title: "upcoming ?? nautillus"
date: 2012-07-11
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mc4man on 2012-07-11
While still in progress as of today so interesting things

The toolbar is  using gtk button/boxes, looks ok in Radiance but at least for me  Ambiance looks poor. 

The sidebar is using symbolic icons, they're ok though I liked the previous better, doesn't matter much

At least four items of 'convenience' have been removed,  one is worthy of an upstream bug attempt

extract here 
compress
open with on folders
menu item & keyboard shortcut for 'Open Parent'

The open with on folders is easily restored in source though I don't think I'll file on upstream, or maybe I will...

The missing parent item can be placed in the 'cog's' Bookmarks submenu though it's value there isn't much, 3 clicks to use is excessive. 
However once there the previous Alt+up becomes active again, though I may try placing it  in the top 'cog' menu instead
(and seeing what it takes to add an up button

Edit: placing the 'Open Parent" item anywhere in the menu is trivial so put it as the 1st option in the cog dropdown where it has some use


So that seems worth a bug on returning the menu item  to the cog menu somewhere, there hasn't been any interest in recent past about an up icon or now a button

Will be curious to see what changes, if any, Ubuntu makes.

(the missing app menu, preferences, which has been returned thru todays g-s-d update does show in the unity panel with the git - where the now missing global menu was.

---

### Post by screaminj3sus on 2012-07-11
Gnome is going to be butchering nautilus removing more and more features:

[http://www.muktware.com/3821/nautilus-get-major-make-over-gnome-36](http://www.muktware.com/3821/nautilus-get-major-make-over-gnome-36)
[http://worldofgnome.org/nautilus-extreme-makeover/](http://worldofgnome.org/nautilus-extreme-makeover/)

I think ubuntu should look into a new file manager in the future or a nautilus fork.

---

### Post by mc4man on 2012-07-11
> **screaminj3sus said:**
> 

I think ubuntu should look into a new file manager in the future or a nautilus fork.
The only possible is another FM, don't see Ubuntu having the resources to 'fork nautilus' (or any desire to 

I think they're both (Gnome & Ubuntu), narrowing the path

---

### Post by sammiev on 2012-07-11
> **mc4man said:**
> The only possible is another FM, don't see Ubuntu having the resources to 'fork nautilus' (or any desire to 

I think they're both (Gnome & Ubuntu), narrowing the path

I think you are correct on both points.

---

### Post by lolpenguin on 2012-07-12
*Licks lips*
Please post output of
```
nautilus --version
```
Well, the icons are made for the GNOME icon theme, and the top toolbar is for Adwaita. It will probably look a _lot_ better in Adwaita.

---

### Post by ronacc on 2012-07-12
> **lolpenguin said:**
> *Licks lips*
Please post output of
```
nautilus --version
```
Well, the icons are made for the GNOME icon theme, and the top toolbar is for Adwaita. It will probably look a _lot_ better in Adwaita.

I don't give a hoot what it looks like , I do care about how badly they cripple it in the name of simplification and eyecandy .

---

### Post by ventrical on 2012-07-12
dale@dale:~$ nautilus --version
GNOME nautilus 3.5.3
dale@dale:~$

---

### Post by MG&amp;TL on 2012-07-12
> **ronacc said:**
> I don't give a hoot what it looks like , I do care about how badly they cripple it in the name of simplification and eyecandy .

So they want to try simplification. What's the problem with that? If you don't like it, you're entirely free to choose something else.

Eyecandy...not really. The old nautilus looked better.

---

### Post by lolpenguin on 2012-07-12
> **MG&TL said:**
> So they want to try simplification. What's the problem with that? If you don't like it, you're entirely free to choose something else.

Eyecandy...not really. The old nautilus looked better.

Part of GNOME's goals is that GNOME can be used on a tablet. To achieve this they have to limit the usefulness of the right click, get rid of most menubars, and reduce overall chrome for applications. Which, in many ways, is counter-productive for desktop users...
Which really divides the community down the middle. Some of us love it, some of us hate it.

---

### Post by MG&amp;TL on 2012-07-13
> **lolpenguin said:**
> Part of GNOME's goals is that GNOME can be used on a tablet. To achieve this they have to limit the usefulness of the right click, get rid of most menubars, and reduce overall chrome for applications. Which, in many ways, is counter-productive for desktop users...
Which really divides the community down the middle. Some of us love it, some of us hate it.

Maybe people can learn to use a desktop like a touchpad. It's only by pre-conditioning that we learned to make precise clicks on small menubars, I'm sure we can unlearn that.

I'll be watching carefully. :)

---

### Post by Elfy on 2012-07-13
> **MG&TL said:**
> Maybe people can learn to use a desktop like a touchpad. It's only by pre-conditioning that we learned to make precise clicks on small menubars, I'm sure we can unlearn that.

And they should do that why?

---

### Post by MG&amp;TL on 2012-07-13
> **Elfy said:**
> And they should do that why?

I'm not saying they (we?) should. I'm just saying it's a design choice by the GNOME developers (who I respect) and if they decide to do so, we have one of two choices:

-Adapt (to GNOME's way of thinking)
-Change (to something else)

Ultimately, if GNOME's interface changes prove that unpopular, then it will slowly die out and become less popular. KDE's 'clicky' interface will no doubt become more popular in that scenario, as will XFCE/LXDE's similiarly mouse-oriented approach.

And I'm not a fan of bashing developer choices; I felt someone needed to speak up for them.

---

### Post by dino99 on 2012-07-13
designing a single gnome for all the so different hardwares (desktop/tablet) will only create unsatisfied users in both categories  :confused:

---

### Post by lolpenguin on 2012-07-13
> **dino99 said:**
> designing a single gnome for all the so different hardwares (desktop/tablet) will only create unsatisfied users in both categories  :confused:

Windows is doing that too.

---

### Post by pt123 on 2012-07-13
Perfect example of the retardation of Gnome, lol talking about touchscreen when there are just 8 people in the world using Gnome on touchscreen, while there are millions using it on the desktop.
The tree view is useful for accommodating people trying to move from Windows.

There is a reason Apple keeps two separate interfaces for their touchscreen and desktop market.

---

### Post by mc4man on 2012-07-13
There was no intention here to bash Gnome, nor to represent this as how it will be per se in Ubuntu. Simply just the current, (as of a few days ago) git of nautilus running _unmodified_ in the _current_ 12.10

Even when the next release lands in Ubuntu it's quite possible that the way the buttons look/react, particularly in ambiance, won't be the way it ends up. (other fm's show some poor behavior atm in ambiance as far as toolbar buttons, take a look at the Marlin daily  

As far as the few things mentioned that have been removed, there is no reason why users can't & shouldn't criticize & or bug them, that's not bashing. In all likelihood Gnome will not revert any, whether Ubuntu chooses to return anything remains to be seen, certainly premature to even consider.

What's more of interest here is what, if anything, does Ubuntu do to adapt some of these changes for use in Unity

For the curious there are well described commits viewable here, good, bad or whatever
 [https://code.launchpad.net/~vcs-imports/nautilus/master-git](https://code.launchpad.net/~vcs-imports/nautilus/master-git)

---

### Post by Elfy on 2012-07-13
I'll close this now.

---

