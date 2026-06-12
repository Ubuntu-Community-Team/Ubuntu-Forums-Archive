---
title: "GTK+ Designer"
date: 2010-01-15
forum: The Cafe
---

### Post by k64 on 2010-01-15
Is there a GTK+ Designer like there is a Qt Designer? I certainly want to know, and want to see whether it really is the case. Maybe I should test it out in Apt-Get.

---

### Post by user1397 on 2010-01-15
> **k64 said:**
> Is there a GTK+ Designer like there is a Qt Designer? I certainly want to know, and want to see whether it really is the case. Maybe I should test it out in Apt-Get.someone correct me if I'm wrong, but maybe GTK+ Glade?

---

### Post by chris200x9 on 2010-01-15
> **ubuntuman001 said:**
> someone correct me if I'm wrong, but maybe GTK+ Glade?

+1 that's all I know of.

---

### Post by k64 on 2010-01-16
I installed Gazpacho, which does (somewhat) what I want. Didn't try Glade as it is broken in Lucid.

---

### Post by Mr. Picklesworth on 2010-01-16
Yep, what you want is Glade (in particular Glade 3). It'll give you a fairly confusing choice of libglade or gtkbuilder at first. Go for gtkbuilder; it's the newer format, which was recently blessed and provided as a default piece of GTK.

Remember that name: *GTKBuilder*! It's important :)

---

### Post by k64 on 2010-01-16
> **Mr. Picklesworth said:**
> Yep, what you want is Glade (in particular Glade 3). It'll give you a fairly confusing choice of libglade or gtkbuilder at first. Go for gtkbuilder; it's the newer format, which was recently blessed and provided as a default piece of GTK.

Remember that name: *GTKBuilder*! It's important :)

Attached is what I got for attempting to install gtkbuilder in Lucid Lynx.

As I said before, I have Gazpacho, which also accesses GTK+ libraries and provides a rapid build environment.

---

### Post by Mr. Picklesworth on 2010-01-16
> **k64 said:**
> As I said before, I have Gazpacho, which also accesses GTK+ libraries and provides a rapid build environment.

Well, search for it in Software Centre and I'm sure it will pop up. The Glade 3 package has been named just "glade" for a while now, not "glade3". As a general rule, the current accepted standard version of an application gets the normal package name, while older versions kept for legacy compatibility / bleeding edge users get the weird names with version numbers.

---

### Post by legends2k on 2010-01-16
**@k64:** **glade** is the package name and not GtkBuilder (which is the API you will use to get the interface from a glade ui file).
This is what you need: [http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)

---

### Post by matthew.ball on 2010-01-16
Anjuta has a Glade plugin available.

---

