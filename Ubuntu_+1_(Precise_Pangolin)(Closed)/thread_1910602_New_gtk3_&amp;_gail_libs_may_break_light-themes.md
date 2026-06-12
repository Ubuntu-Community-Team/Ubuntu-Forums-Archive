---
title: "New gtk3 &amp; gail libs may break light-themes"
date: 2012-01-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mc4man on 2012-01-17
Certainly did here - r. click context is almost impossible to see, as is nautilus location bar/breadcrumbs
filed on light-themes though maybe something else?
[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/917734](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/917734)

---

### Post by TerryNewton on 2012-01-17
> **mc4man said:**
> maybe something else?

In addition to Ambiance menu text being unreadable,
eog (image viewer) crashes here with...
Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1607:20: Invalid animation description

That's with Radiance, with Ambiance same error but 1597:20, and
with Adwaita it's a shower of Gtk errors like...
Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1810:37: Unknown pseudo-class 'window-unfocused'

---

### Post by jppr on 2012-01-17
[https://launchpad.net/ubuntu/precise/+source/light-themes/0.1.8.26](https://launchpad.net/ubuntu/precise/+source/light-themes/0.1.8.26)

---

### Post by Harry33 on 2012-01-17
Eog definitely crashes now with this 3.3.8 version of GTK+3 + glib 2.31.10.

---

### Post by Harry33 on 2012-01-17
In order to get Eog working again, you need to downgrade:
- GTK+3 to the version 3.3.6-0ubuntu3
- glib2.0 to the version 2.31.8-0ubuntu2
- eog to the version 3-2-2--2ubuntu3

or just wait for the fix in eog.

---

### Post by mc4man on 2012-01-17
> **jppr said:**
> [https://launchpad.net/ubuntu/precise/+source/light-themes/0.1.8.26](https://launchpad.net/ubuntu/precise/+source/light-themes/0.1.8.26)

That fixed it as far as light-themes in unity*
(though will have to redo my modded ambiance theme

Edit: - breadcrumbs do seem a bit odd, intended don't know?

---

### Post by Harry33 on 2012-01-17
Eog is still very broken.

---

### Post by mc4man on 2012-01-17
> **Harry33 said:**
> Eog is still very broken.
A new eog came in here,  3.3.4-0ubuntu1,  but still no go, don't get a crash, just nothing

---

### Post by Harry33 on 2012-01-17
> **mc4man said:**
> A new eog came in here,  3.3.4-0ubuntu1,  but still no go, don't get a crash, just nothing

True, same here.

---

### Post by jbicha on 2012-01-17
The eog problem is a known GTK bug. I expect it'll be fixed tomorrow.

---

### Post by Harry33 on 2012-01-18
Rigth, this is the GTK+3 update to fix the "eog not starting" issue.
Here:
[https://launchpad.net/ubuntu/precise/+source/gtk+3.0/3.3.8-0ubuntu2](https://launchpad.net/ubuntu/precise/+source/gtk+3.0/3.3.8-0ubuntu2)

> **[SIZE=2]Changelog[/SIZE]**

          gtk+3.0 (3.3.8-0ubuntu2) precise; urgency=low    * debian/patches/git_revert_property_change.patch:     - revert the change that leaded to i.e eog not starting (lp: [#917940]("https://launchpad.net/bugs/917940"))  -- Sebastien Bacher <email address hidden>   Wed, 18 Jan 2012 11:34:43 +0100

---

