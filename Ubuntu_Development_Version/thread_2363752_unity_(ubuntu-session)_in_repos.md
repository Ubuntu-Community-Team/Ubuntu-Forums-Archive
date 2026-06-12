---
title: "unity (ubuntu-session) in repos"
date: 2017-06-14
forum: Ubuntu Development Version
---

### Post by ventrical on 2017-06-14
After installing artful-desktop from the daily .iso you can still get unity7  (ubuntu-session) from the repos. Although not actively developed atm the infrastructure is there for unity7.5

[https://launchpad.net/unity/7.5](https://launchpad.net/unity/7.5)

Feel free to test it.

Regards..

---

### Post by ventrical on 2017-06-14
Side note:

If unity7 causes troubles , as Jeremy has indicated, with gnome3 this cycle or the 18.04 LTS cycle then it would be pulled from the archives.R

regards..

---

### Post by Frogs Hair on 2017-06-14
My 17.04-17.10 upgrade uses Unity 7.5 and I have experienced no conflicts with the Gnome session yet, but results may differ if added to Ubuntu Gnome.

---

### Post by ventrical on 2017-06-14
> **Frogs Hair said:**
> My 17.04-17.10 upgrade uses Unity 7.5 and I have experienced no conflicts with the Gnome session yet, but results may differ if added to Ubuntu Gnome.

Perhaps this cycle but not the next.


I am still using it in 16.04 and 17.10 upgrades and one artful-desktop daily with ubuntu-session installed from the archive. However , as I am advised, all focus will be upon Gnome-desktop and the other current ubuntu DE releases. 

 I am advised that if unity causes any problems it will be pulled from archives -(or it is suggested that it should be pulled). so this is a slight departure from what I originally assumed from previous correspondence, that being that unity7 will be in universe and maintained.. which it will not. 

Regards..

---

### Post by Chanath on 2017-06-14
> **ventrical said:**
> 
 I am advised that if unity causes any problems it will be pulled from archives -(or it is suggested that it should be pulled). so this is a slight departure from what I originally assumed from previous correspondence, that being that unity7 will be in universe and maintained.. which it will not. 

Regards..

Does that mean, we should pull the necessary packages to install Unity and keep them in our hard disk? What I mean is, I would like to install Unity on Ubuntu 18.04, when it arrives. If Gnome in it would trouble Unity to work, I would like to uninstall Gnome. You see, Gnome is available in all distros (Fedora, OpenSuse etc), but Unity is (still) only Ubuntu. In a way, Ubuntu was Ubuntu, because of Unity,

---

### Post by ventrical on 2017-06-14
> **Chanath said:**
> Does that mean, we should pull the necessary packages to install Unity and keep them in our hard disk? What I mean is, I would like to install Unity on Ubuntu 18.04, when it arrives. If Gnome in it would trouble Unity to work, I would like to uninstall Gnome. You see, Gnome is available in all distros (Fedora, OpenSuse etc), but Unity is (still) only Ubuntu. In a way, Ubuntu was Ubuntu, because of Unity,

But as of now there are no devs or maintainers and Mark  would like us to focus on gnome, xubuntu, kubuntu, lubuntu etc..Although unity7 is in the archive .. if it cause problems or breaks gnome3  (or causes troubles as Jeremy suggested) then it will be pulled. But unity7 will be maintained with security updates during and up to EOL with 16.04

regards..

---

### Post by Chanath on 2017-06-14
> **ventrical said:**
> But as of now there are no devs or maintainers and Mark  would like us to focus on gnome, xubuntu, kubuntu, lubuntu etc..Although unity7 is in the archive .. if it cause problems or breaks gnome3  (or causes troubles as Jeremy suggested) then it will be pulled. But unity7 will be maintained with security updates during and up to EOL with 16.04

regards..
Its not what "Mark would like us to focus on" is of any interest. Unity being in the repos is not going to break Gnome 3, if Unity is not coming in 18.04 as (depending) apps. What is not there cannot break it. But, if we would like to ditch Gnome 3 and install Unity, that should be allowed. Of course, if Unity is solely owned by Mark, he can do what he wants with it. Only, he shouldn't forget that for last 6 years lot of people used Unity.

---

### Post by ventrical on 2017-06-14
> **Chanath said:**
> Its not what "Mark would like us to focus on" is of any interest. Unity being in the repos is not going to break Gnome 3, if Unity is not coming in 18.04 as (depending) apps. What is not there cannot break it. But, if we would like to ditch Gnome 3 and install Unity, that should be allowed. Of course, if Unity is solely owned by Mark, he can do what he wants with it. Only, he shouldn't forget that for last 6 years lot of people used Unity.

I agree with you 100%. But there have been some engineering problems as well as philosophical and business issues that has led to the current direction in which ubuntu and the community are headed. I still hope that unity7 will be in the universe in 18.04 and that maintainers will come along but if depends are not updated and maintained then it will break.

Regards..

---

### Post by Chanath on 2017-06-14
> **ventrical said:**
> .

Have you noticed that very few people come here these days. About a year ago, this place was full of people, checking, experimenting. And, now that Unity's gone...

---

### Post by cariboo on 2017-06-14
> **Chanath said:**
> Have you noticed that very few people come here these days. About a year ago, this place was full of people, checking, experimenting. And, now that Unity's gone...

Actually it's a lot busier now than it was during the last development cycle.

---

### Post by mc4man on 2017-06-14
It's more likely that upgrades to gtk & glib will break or cause issues in the  unity session. So in that case there'll be no fixes forthcoming.

A slightly more relevant issue (as unity7 is unburied Dead),  would be what the presence of Xorg does to the use of gnome-wayland. That *may* be what's causing no nvidia prop driver support as Gnome unilaterally caved in to Nvidia concerning wayland  ( EGLStreams ), so prop drivers should work...

---

### Post by ventrical on 2017-06-14
> **Chanath said:**
> Have you noticed that very few people come here these days. About a year ago, this place was full of people, checking, experimenting. And, now that Unity's gone...

 I'm just trying to build bridges. I do not have any steering ability to this matter.  I must say I have attempted to make the case for unity , but, perhaps it is a bridge too far.  This may change suddenly (as things do with ubuntu) throughout the summer so I am still hopeful that unity will be in the universe come 18.04.  I would take up the challenge but I have spent so much time *testing* ubuntu that my programming skills in linux are not honed in or refreshed enough to tackle this problem efficiently, but our contributions of testing of the new .iso and default Gnome desktop intergration as flagship ubuntu can shape and influence gnome3 developers to incorporate some of the bright sparks that were developed in unity into the gnome3 desktop.

Regards..

---

### Post by ventrical on 2017-06-14
> **mc4man said:**
> It's more likely that upgrades to gtk & glib will break or cause issues in the  unity session. So in that case there'll be no fixes forthcoming.

A slightly more relevant issue (as unity7 is unburied Dead),  would be what the presence of X11  does to the use of gnome-wayland. That *may* be what's causing no nvidia prop driver support as Gnome unilaterally caved in to Nvidia concerning wayland  ( EGLStreams ), so prop drivers should work...

It would be a lot of work for a small group of volunteer maintainers to keep up to speed.

Regards..

---

### Post by cariboo on 2017-06-15
It must have been a hard decision, after putting in so much time in developing Unity, but I think it is for the best if Canonical wants to stay alive and keep moving forward. I was a big Unity fan, but I've converted to Gnome-shell on this system and I'm quite happy with the way it works.

---

### Post by ventrical on 2017-06-15
> **cariboo said:**
> It must have been a hard decision, after putting in so much time in developing Unity, but I think it is for the best if Canonical wants to stay alive and keep moving forward. I was a big Unity fan, but I've converted to Gnome-shell on this system and I'm quite happy with the way it works.

Hi Cariboo, all,

 Here is a message to Mark and I from  dev Will Cooke.  I hope this clears things up a bit more with some background.

> 
Hi Dale, Mark,

 
 Just to add a little more background here:
 
 
 
 Unity 7 in 16.04 LTS will naturally be supported until 2021 by the  Desktop team with security updates and critical bug fixes.  These would  very likely be forward-portable to Unity 7 in 17.04, 17.10 etc.
 
 
 The problems for U7 arise in 17.10 and beyond because of the way we  have patched the Gtk libraries & apps to get them to integrate well  with Unity 7.  For example, we patch out header bars and client side  decorations & patch in support for the global menus.  This are fundamentally incompatible with GNOME Shell, and so we need to  make a decision about whether to add more patches to make these apps  work well in both Unity 7 and GNOME Shell or drop the patches and focus  on the GNOME Shell experience.  The current preference is drop the patches.
 
 
 There are some other incompatibilities in the desktop session  between GNOME Settings Daemon & Unity Settings Daemon, or GNOME  Online Accounts & Ubuntu Online Accounts.  We need to use the GNOME  version in the GNOME session, so these would be prime candidates for a community team to maintain in the future for the U7 session.
 
 
 Where does this leave Unity 7 in 17.10 then?  At the moment we are  testing Unity 7 alongside GNOME Shell to spot when something we land  causes Unity 7 to break.  While we can probably work around some of  these issues, the overall experience will be hampered by the incompatibility between our U7 patches & services and GNOME  Shell, and this will, unfortunately, degrade the U7 experience on  17.10.  We're still looking at what changes could be made to keep U7  working in the archive so I can't make any promises of functionality yet.  I'd like to make that call before Beta 1 so people  know what to expect.
 
 
 Any community teams who'd be interested in helping out with that  would be very welcome and I'd be very happy to help get them set up with  the access they need and support from the Desktop Team.
 
 
 Cheers, Will
 

@mac4man and all U+1 team and others,

If you think you can help test in the capacity as Will is explaining in his message then please feel free to engage  in the conversation here, specifically "testing Unity 7 alongside GNOME Shell" to spot things which causes Unity 7 to break. If any have any ideas that they would like to form a sub-team and take up some of the maintainers responsibilities then I'm listening.

@Canath,

 I'd like to hear some more of your ideas.

Regards..

@Cariboo

could you (or other mod) fix the font prob in the quoted text? Thanks.

---

