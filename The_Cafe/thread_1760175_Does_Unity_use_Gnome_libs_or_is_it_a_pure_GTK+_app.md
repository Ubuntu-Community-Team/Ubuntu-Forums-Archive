---
title: "Does Unity use Gnome libs or is it a pure GTK+ app?"
date: 2011-05-16
forum: The Cafe
---

### Post by visionaire on 2011-05-16
So, if Unity is Gnome-less, they can take decisions of ubuntu design interface in more details than what they can do with a Gnome DE?

---

### Post by Quadunit404 on 2011-05-16
Unity is a shell for GNOME 2 and starting from Oneiric, GNOME 3. It pretty much requires GNOME to exist to work.

---

### Post by visionaire on 2011-05-16
> **Quadunit404 said:**
> Unity is a shell for GNOME 2 and starting from Oneiric, GNOME 3. It pretty much requires GNOME to exist to work.

Ahhhh thanks for the input, so in 11.10 when Gnome 3 arrives unity wil be gone?

---

### Post by mcduck on 2011-05-16
> **visionaire said:**
> Ahhhh thanks for the input, so in 11.10 when Gnome 3 arrives unity wil be gone?

No, it will be updated to work with Gnome 3 libraries. So in 11.10 you'll be able to switch between Unity and Gnome Shell just like you are now able to switch between Unity and the old Gnome interface

(by the way, Unity is actually a Compiz plugin, just like Gnome Shell is a Mutter plugin)

---

### Post by NormanFLinux on 2011-05-16
Yup. Canonical wanted a more accessible shell for GNOME. There were disagreements with GNOME over how the shell should function so Canonical came up with a new one for Ubuntu and that is known as Unity.

---

### Post by visionaire on 2011-05-16
I see, so, for Gnome 2 I can tell the improvement in the GUI, but what would be the advantage of Unity over Gnome shell? In fact, I recently try the Gnome 3 and is very nice, I just returned to Unity cause some empathy notification issue I got on Gnome 3

---

### Post by visionaire on 2011-05-16
> **NormanFLinux said:**
> Yup. Canonical wanted a more accessible shell for GNOME. There were disagreements with GNOME over how the shell should function so Canonical came up with a new one for Ubuntu and that is known as Unity.

I understand now

---

### Post by Tibuda on 2011-05-16
See the deps yourself: [http://packages.ubuntu.com/natty/unity](http://packages.ubuntu.com/natty/unity)

I have not seen anything gnome-specific but gconf.

---

### Post by visionaire on 2011-05-16
> **Tibuda said:**
> See the deps yourself: [http://packages.ubuntu.com/natty/unity](http://packages.ubuntu.com/natty/unity)

I have not seen anything gnome-specific but gconf.

Very interesting! Maybe they get rid of all gnome libs after all,

---

### Post by Quadunit404 on 2011-05-16
Actually when Oneiric (11.10) comes out they're dumping GNOME 2 in favor of GNOME 3.

---

### Post by visionaire on 2011-05-16
> **Quadunit404 said:**
> Actually when Oneiric (11.10) comes out they're dumping GNOME 2 in favor of GNOME 3.

I supposed that, but if Gnome 3 is by default also gnome-shell, what will happen?

---

### Post by Quadunit404 on 2011-05-16
GNOME Shell will be an optional package, Unity Compiz will be based on vanilla GNOME 3 and Unity 2D will be based on Qt and a non-compositing Compiz... and sorta vanilla GNOME 3 (it's sorta vanilla because it's normal G3 except with all the GTK libraries replaced with Qt libraries)

---

