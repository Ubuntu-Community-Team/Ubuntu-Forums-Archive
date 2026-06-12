---
title: "Show launcher when no windows are open"
date: 2012-04-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by palimmo on 2012-04-04
Hello!
I'm trying Ubuntu 12.04 beta 2 64 bit. It works really good!
But I have some questions and small problems. I'm going to open different threads to discuss about them.

First of all:
as in my previous Ubuntu versions, I decide to set the Launcher in auto-hide mode. 
But...when I see the desktop (all the windows are minimized or no windows are open) the launcher isn't visible. Why?
It's pretty ugly to see the bare desktop without launcher.
How can I set it in order to be shown during the desktop view?

thanks!

---

### Post by bluenova on 2012-04-04
The function you are referring to is not auto-hide it's called dodge and has been removed from 12.04. Reasons cited are it was buggy and was too much code to maintain. Personally I thought it was fine and loved it on my netbook but there we go.

[http://ubuntuforums.org/showthread.php?t=1937199](http://ubuntuforums.org/showthread.php?t=1937199)

---

### Post by Baldrick_NZ on 2012-04-04
Sad, but true.

Though this work around maybe of interest...
[http://www.webupd8.org/2012/04/real-window-dodge-unity-launcher.html](http://www.webupd8.org/2012/04/real-window-dodge-unity-launcher.html)

---

### Post by Hakunka-Matata on 2012-04-04
Right button on blank desktop
choose [B]Change Desktop Background
[/B]click on the **behaviour tab **and adjust things

---

### Post by palimmo on 2012-04-04
That's really sad! :(

And... can I restore this behavior via CCSM? It seems no longer possible too...

@Hakunka-Matata
that's not the point. But thank you anyway!

---

### Post by Hakunka-Matata on 2012-04-04
> **palimmo said:**
> Hello!
I'm trying Ubuntu 12.04 beta 2 64 bit. It works really good!
But I have some questions and small problems. I'm going to open different threads to discuss about them.

First of all:
as in my previous Ubuntu versions, I decide to set the Launcher in auto-hide mode. 
But...when I see the desktop (all the windows are minimized or no windows are open) the **launcher isn't visible. Why?**
It's pretty ugly to see the bare desktop without launcher.
How can I set it in order to be shown during the desktop view?

thanks!

You can't set the Unity Launcher Icons Bar using the **behaviour tab?**  What some people are calling the "Tablet like desktop", which, I agree with.  
What **launcher **are you referring to then?

---

### Post by palimmo on 2012-04-04
> **Hakunka-Matata said:**
> You can't set the Unity Launcher Icons Bar using the **behaviour tab?**
What **launcher **are you referring to then?

That launcher, yes!
But the point is that i would like to see it also when no windows are open.... 

In the previuos version of ubuntu was possible:
hide when windows were maximised, shown where no windows were open.

But now it appears only if I "call" it with the mouse indicator.

---

### Post by Hakunka-Matata on 2012-04-04
In the **behaviour Tab **the **auto hide mode **can be toggled.

---

### Post by palimmo on 2012-04-04
> **Hakunka-Matata said:**
> In the **behaviour Tab **the **auto hide mode **can be toggled.
I know. And I did it.

I like the auto-hide when I have an open window.
But if I have all the windows closed, i would like to see the launcher.
And that seems no longer possible in Ubuntu 12.04 (it was in 11.10).

---

### Post by Hakunka-Matata on 2012-04-04
OK, now I get it.  My desktop does not have that problem, I have the unity launcher visible even though no applications are open.  
I wonder why your's won't do that?

---

### Post by palimmo on 2012-04-04
> **Hakunka-Matata said:**
> OK, now I get it.  My desktop does not have that problem, I have the unity launcher visible even though no applications are open.  
I wonder why your's won't do that?

Yes! :mad:

---

### Post by palimmo on 2012-04-04
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/973170](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/973170)

---

### Post by palimmo on 2012-04-04
> **Hakunka-Matata said:**
> OK, now I get it.  My desktop does not have that problem, I have the unity launcher visible even though no applications are open.  
I wonder why your's won't do that?

That's really strange! And you have the Auto-Hide option enabled???
In my case this option is enabled and the laucher always hides!

---

### Post by Hakunka-Matata on 2012-04-04
see screenshots in post #s, 8 & 10

---

### Post by palimmo on 2012-04-04
> **Hakunka-Matata said:**
> see screenshots in post #s, 8 & 10

Hehe! It means you have the Auto-hide -> OFF

---

### Post by Hakunka-Matata on 2012-04-04
Ok palimmo, I guess I understand your wish:
i changed to auto-hide mode ON, it's pretty much a wash for me, but I agree you have a point.  Good luck
actually I switch back and forth, with all the options available, especially with workspace switcher <Ctrl-Alt-Right,left,up or down arrow> working so well, seems robust to me.

---

### Post by cariboo on 2012-04-04
> **Hakunka-Matata said:**
> OK, now I get it.  My desktop does not have that problem, I have the unity launcher visible even though no applications are open.  
I wonder why your's won't do that?

What palimmo is talking about is called *dodge windows* which is no longer available. In testing, it was found that new users were confused by the launcher disappearing when windows were maximized, and coming back when all windows were closed.  Baldrick_NZ posted a link to a patch in this[ post]("http://ubuntuforums.org/showpost.php?p=11816296&postcount=3").

---

### Post by santosh83 on 2012-04-04
> **cariboo907 said:**
> What palimmo is talking about is called *dodge windows* which is no longer available. In testing, it was found that new users were confused by the launcher disappearing when windows were maximized, and coming back when all windows were closed.  Baldrick_NZ posted a link to a patch in this[ post]("http://ubuntuforums.org/showpost.php?p=11816296&postcount=3").

But why not retain it as an **OPTION**, for those of us who won't be confused by this, and prefer this behaviour? Why altogether disable it? I do hope Canonical rethinks their stance regarding this, for dodge would be especially useful for smaller screens, and is not as annoying as auto-hide or always on either!

---

### Post by cariboo on 2012-04-04
> **santosh83 said:**
> But why not retain it as an **OPTION**, for those of us who won't be confused by this, and prefer this behaviour? Why altogether disable it? I do hope Canonical rethinks their stance regarding this, for dodge would be especially useful for smaller screens, and is not as annoying as auto-hide or always on either!

There was a huge discussion about it on the unity-design mailing list. The archives are [here]("https://lists.launchpad.net/unity-design/maillist.html"), if you want to have a look see.

---

### Post by santosh83 on 2012-04-04
> **cariboo907 said:**
> There was a huge discussion about it on the unity-design mailing list. The archives are [here]("https://lists.launchpad.net/unity-design/maillist.html"), if you want to have a look see.

Thanks! I will.

---

### Post by palimmo on 2012-04-05
Yes... I have interpreted this change as a bug....

---

