---
title: "compiz, emerald, &amp; WMs ..."
date: 2010-11-02
forum: The Cafe
---

### Post by user1397 on 2010-11-02
so correct me if i am wrong, but my understanding is the following:

-compiz is a window manager, like metacity or openbox or kwin.

-emerald is a window decorator (which is what exactly? like, what are the default window decorators for gnome, kde, etc)

-compiz and kwin are compositing window managers, while metacity and openbox etc are stacking window managers

is this all correct?

---

### Post by slackthumbz on 2010-11-02
> **ubuntuman001 said:**
> so correct me if i am wrong, but my understanding is the following:

-compiz is a window manager, like metacity or openbox or kwin.

-emerald is a window decorator (which is what exactly? like, what are the default window decorators for gnome, kde, etc)

-compiz and kwin are compositing window managers, while metacity and openbox etc are stacking window managers

is this all correct?

No, Metacity can also be used as a window decorator in compiz (I think) either that or the default compiz window decorator uses metacity settings (since it responds appropriately to any gconf changes to metacity)

---

### Post by Spice Weasel on 2010-11-02
There are very few non-tiling WMs that don't also work as window decorators. EvilWM is one of them, so is Compiz.

This is a very good explanation of how these things work:

[http://www.youtube.com/watch?v=tvbAawBGmgE](http://www.youtube.com/watch?v=tvbAawBGmgE)

---

### Post by Pogeymanz on 2010-11-02
> **slackthumbz said:**
> No, Metacity can also be used as a window decorator in compiz (I think) either that or the default compiz window decorator uses metacity settings (since it responds appropriately to any gconf changes to metacity)

Metacity is not a decorator. gtk-window-decorator can inherit metacity's themes.

Most WM's are their own decorators, but Compiz is just a WM so you need a decorator.

---

### Post by 3Miro on 2010-11-02
Most WM come with their own decorators, compiz can use one of Emerald, gtk-window-decorator or kde-window-decorator (the last two use metacity and kwin themes).

Openbox is the only strictly stacking manager that I know of. Compiz is the only strictly composing WM. The others can have composition either enabled or disabled. Kwin, Metacity and Xfwm4 can go either way.

---

### Post by Pogeymanz on 2010-11-02
> **3Miro said:**
> 
Openbox is the only strictly stacking manager that I know of.

You don't know of very many window managers, do you? ;-)

Openbox, Blackbox, PekWM, Fluxbox, IceWM, JWM, EvilWM, Sawfish...

---

### Post by 3Miro on 2010-11-02
> **Pogeymanz said:**
> You don't know of very many window managers, do you? ;-)

Openbox, Blackbox, PekWM, Fluxbox, IceWM, JWM, EvilWM, Sawfish...

Yes. I have heard of many of those, but I have only used Openbox so I didn't want to make assumptions.

---

