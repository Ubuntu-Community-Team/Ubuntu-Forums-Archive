---
title: "The future of Ubuntu's Window Managers"
date: 2009-02-11
forum: Ubuntu Brainstorm
---

### Post by Yashiro on 2009-02-11
With some of the recent problems and re-organization going on within the guys working on Compiz would it not be a good idea for Canonical to get involved or fork the project for themselves?

If, for example, Compiz dev went into meltdown, what are we left with? Metacity.

While Metacity's OK for average desktop work it doesn't scale at all well with graphic card enhancements. 
I guess more importantly for Ubuntu it offers little in the way of 'pizazz' that keeps the Ubuntu desktop in touch with modern equivalents like OS X and Vista.

I think it would be beneficial to ensure we have a working modern window manager for the future. Whether it be Compiz or a much better replacement.

---

### Post by smartboyathome on 2009-02-11
Compiz++ is replacing Compiz, so we may see it replace Compiz in Ubuntu in the future. Right now, I would say that we really don't have anything besides Compiz that fits within what Ubuntu wants.

---

### Post by Yashiro on 2009-02-11
It's not. Compiz++ is being merged back into the main branch, as is Fusion and the other spinoffs. Development of Compiz on the whole is a little lost currently.

---

### Post by cardinals_fan on 2009-02-12
The problem is that only a finite amount can be done with random bling and flashiness.  The Compiz folks had a tremendous amount of momentum to integrate a large number of glitzy effects, but there are only so many ways to burn down a window.

A few more focused subprojects, such as the group working on head tracking, are still doing well within the Compiz community.

Overall, what would you like to see added?  I believe that the primary value of compositing WMs is that they defer some of the resource load to the GPU instead of your CPU.  Metacity's compositing manager already handles this.

---

### Post by Yashiro on 2009-02-12
It's not really a case of what I want. I am just concerned about the direction it's heading and the lack of alternatives.

Metacity doesn't offload anything does it? It's all software/cpu which is why it's so slow and doesn't need an Opengl stack to run.
(Just booting into the vesa driver and turning it on in metacity works.)

---

### Post by bruce89 on 2009-02-13
Compiz won't be around for much longer, because of Mutter [Metacity-Clutter] (used in GNOME 3.0 ATM).

---

### Post by CarpKing on 2009-02-20
> **bruce89 said:**
> Compiz won't be around for much longer, because of Mutter [Metacity-Clutter] (used in GNOME 3.0 ATM).

I don't think Compiz will go away any time soon.  People will still want to use it, and there are plenty of other window managers still out there (even Sawfish is still lurking in the repositories).  However, if they do Mutter right, it could take away most of the usefulness of Compiz and most Gnome-based distros would probably transition away from the latter as a default WM.

---

