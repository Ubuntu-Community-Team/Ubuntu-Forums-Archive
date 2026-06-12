---
title: "Why does Midori hate OMG! Ubuntu?"
date: 2010-10-30
forum: The Cafe
---

### Post by devondashla on 2010-10-30
I loooove Midori, but I can't stand having to use another browser JUST to check OMG! Ubuntu. When i open it in Midori, it takes forever to load and treats the page like a computer with 1mg of RAM treats KDE 4; so sluggy it's unrealistic. What causes that in Midori, but not with ANY OTHER BROWSER (Chrome, Firefox, etc.)

---

### Post by Windows Nerd on 2010-10-30
> **devondashla said:**
> I loooove Midori, but I can't stand having to use another browser JUST to check OMG! Ubuntu. When i open it in Midori, it takes forever to load and treats the page like a computer with 1mg of RAM treats KDE 4; so sluggy it's unrealistic. What causes that in Midori, but not with ANY OTHER BROWSER (Chrome, Firefox, etc.)
You should contact them to notify them about this issue, for a start:

[http://www.omgubuntu.co.uk/contact-us/](http://www.omgubuntu.co.uk/contact-us/)

---

### Post by NightwishFan on 2010-10-30
I have already filed a bug here:
[https://bugs.launchpad.net/ubuntu/+source/webkit/+bug/655012](https://bugs.launchpad.net/ubuntu/+source/webkit/+bug/655012)

Though you should contact their end as well.

---

### Post by del_diablo on 2010-10-30
Tsk, because Midori is not green............

---

### Post by XubuRoxMySox on 2010-10-30
> **del_diablo said:**
> Tsk, because Midori is not green............

Midori *means* [COLOR="DarkGreen"]green[/COLOR]!

---

### Post by del_diablo on 2010-10-31
> **dixiedancer said:**
> Midori *means* [COLOR="DarkGreen"]green[/COLOR]!

Midori is not colored green!

---

### Post by pwnst*r on 2010-10-31
Because of the name of the site.

---

### Post by LADmaticCA on 2010-10-31
I tried Midori yesterday and because of this exact issue, I stopped using it. Hopefully it gets fixed.

---

### Post by ajy0852 on 2010-10-31
It's a problem with gtk-webkit choking on large box-shadows (like the one around their main div). Epiphany, Midori, Uzbl, and other gtk-webkit browsers all have the same problem. I believe they know about the problem. Given their target audience, you'd think they would've fixed it, and I'm actually pretty annoyed that they haven't yet. (edit, actually looks like they didn't know exactly what causes it, so I'm eating my words).

As a workaround, create a custom stylesheet for Midori (Sorry, I don't have Midori at the moment so I can't remember exactly how to do this, maybe someone else can help out) and add:
```
#main { -webkit-box-shadow: none !important; }
```

I think you'll have to restart Midori.

---

### Post by tkluck on 2010-11-01
How to add a custom style sheet is in the FAQ for Midori:

[http://wiki.xfce.org/midori/faq#common_problems](http://wiki.xfce.org/midori/faq#common_problems)

It has the same recommendation as ajy0852's.[U]
[/U]

---

### Post by Jesus_Valdez on 2010-11-01
Why does Midori hate Google Reader?

...
Forget it, I just checked and today's update seems to have solved the problem with google reader.

---

