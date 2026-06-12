---
title: "Linux Mint Saucy Gnome 3.8"
date: 2013-05-18
forum: Ubuntu Development Version
---

### Post by Chanath on 2013-05-18
I wanted to check out Linux Mint 15RC, so downloaded and installed it. I don't really like Cinnamon, too old fashioned.
Still to love Unity, maybe with Unity Next. I like Gnome 3 very much. There are enough menus to use, from classic gnome-menu, Unity Dash, Gnomenu, Slingshot in the extensions. It also has the window list.

Then uninstalled Cinnamon, Nemo went with it, not a big deal as Nautilus had  come with Gnome 3.8. Changed Raring to Saucy In the sources.list, marked  off Olivia repos, updated and upgraded. I have now the bleeding edge  Linux Mint Saucy Gnome 3 edition with Linux kernel 3.9.0.2.  Don't know how  to call it, maybe Mint 16 RC or just Saucy-Mint. So far so good! It  works. It is bleeding edge. It can break any time, but I won't believe  it would do that. I was with Raring all the way until it was finally  released. Nothing broke down in that, so I'm sure nothing would break in  Saucy-Mint. It'd be fun!:)

I also have Saucy Gnome from Ubuntu--not the Ubuntu-Gnome edition--with kernel 3.9.0.2
Let's see which one is more "polished." :)

---

### Post by grahammechanical on 2013-05-18
Well done! That's testing! From some of the posts I have seen recently on the forum problems come when people try to undo what they have done instead of re-installing. They take things off and put things on and then take other stuff off and come here and say, I just want my Ubuntu back.

It is at the bleeding edge that the men get separated from the boys. Oh, and women from the girls. We got to be politically correct. There was a time in the English language when girl was gender neutral. Male children were called girls.

---

### Post by ventrical on 2013-05-18
btrfs just saved my hide big time .

---

### Post by Chanath on 2013-05-18
I thought I can't just say I don't like Unity without working with it, so I decided to have the Ubuntu Saucy bleeding edge with Unity, until Saucy's final release. I'm sure I'd start liking it by that time. I am going to have the bleeding edge Saucy-Mint with Gnome 3 to work with Gnome 3.8, maybe later 3.9, for it is Ubuntu anyway. I am going to consider as though I've just discovered Unity, enjoy it and test it, and also test myself.

I think my problem with Unity happened with the autohiding of the launcher bar, which was not quite responsive, however much I make the pressure sensitive. This time, I am keeping it visible and would make it thinner, say 24 pixels.
Have a good day!:)

---

### Post by fantab on 2013-05-18
UNITY Launcher cannot go below 32 pixels. Autohide works great here... no issues. Congrats on your Saucy-Mint.

---

### Post by cariboo on 2013-05-18
> **fantab said:**
> UNITY Launcher cannot go below 32 pixels. Autohide works great here... no issues. Congrats on your Saucy-Mint.

Actually you can set the Unity launcher icon size to smaller than 32px, by using ccsm, see the screenshot.

---

### Post by Chanath on 2013-05-18
I tried to work with 24 & 26 pixel icons in the launcher, but they are too tiny, so I am now learning to work with the autohiding launcher. Pretty tired of hitting hard at the left side of the screen and trying to hold the launcher in place. I will use this bleeding edge Ubuntu only with Unity.
Good day!

---

### Post by cariboo on 2013-05-18
> **Chanath said:**
> I tried to work with 24 & 26 pixel icons in the launcher, but they are too tiny, so I am now learning to work with the autohiding launcher. Pretty tired of hitting hard at the left side of the screen and trying to hold the launcher in place. I will use this bleeding edge Ubuntu only with Unity.
Good day!

When I had Unity on my netbook, I found setting the launcher icon size to 22px, quite useful. Now I should learn how to make the gnome-shell icons smaller, as on the small 10" screen with 1024X600 resolution they are to big.

---

### Post by Chanath on 2013-05-19
Maybe you try this to change the icons & icon grid;
>  /usr/share/gnome-shell/theme/gnome-shell.css 

>  

 /* Apps */ 

 .icon-grid {

     spacing: 36px;                     # [ Change the value to its half eg; 36 is replaced by 18]

     -shell-grid-item-size: 118px;      # [ Simillarly 118 is replaced by 96]

 }

 .icon-grid .overview-icon {

     icon-size: 96px;                   # [96 is replaced by 48]

---

