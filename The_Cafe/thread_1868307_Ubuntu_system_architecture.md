---
title: "Ubuntu system architecture"
date: 2011-10-24
forum: The Cafe
---

### Post by Oxwivi on 2011-10-24
Following is the Android system architecture:

[IMG]http://upload.wikimedia.org/wikipedia/commons/6/63/System-architecture.jpg[/IMG]

Other than the kernel, what would be the Ubuntu components if we were to describe it in a similar diagram?

---

### Post by earthpigg on 2011-10-24
What happens when philosophy and computer science sleep in the same bed?

---

### Post by 3Miro on 2011-10-24
In Ubuntu the kernel would be the kernel, however, you would also have an Xorg layer that would contain half of the display driver as well as the drivers for the input devices. Libraries would be more commonly called ToolKit (as in QT or GTK), or if you wish a ToolKit is a unified interface for a collection of libraries. The Application Framework would be the Desktop Environment with the Windows Manager on top. Applications are the Applications.

More specifically in 11.10:
Firefox
Compiz (+Unity)
Gnome 3
GTK3
Xorg
Kernel

earthpigg is right thought. In many cases the boundaries between those are blurry.

---

### Post by makitso on 2011-10-24
This is the classical Technology Stack.  It would be great to see this for all the *ubuntu distros as well as for Unity / Gnome.

---

### Post by Mr. Picklesworth on 2011-10-24
There's a diagram of the software stack over here: [http://developer.ubuntu.com/resources/platform/documentation/platform-diagram/](http://developer.ubuntu.com/resources/platform/documentation/platform-diagram/)
It's a slightly different view on the stack, higher level than that image for Android, and focused on app developers. Similar idea, though.

[developer.gnome.org]("http://developer.gnome.org/") has a nice diagram, too.

---

### Post by Oxwivi on 2011-10-25
> **Mr. Picklesworth said:**
> There's a diagram of the software stack over here: [http://developer.ubuntu.com/resources/platform/documentation/platform-diagram/](http://developer.ubuntu.com/resources/platform/documentation/platform-diagram/)
It's a slightly different view on the stack, higher level than that image for Android, and focused on app developers. Similar idea, though.

[developer.gnome.org]("http://developer.gnome.org/") has a nice diagram, too.
Thanks for those!

---

