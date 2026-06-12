---
title: "Star Trek Nut"
date: 2009-01-03
forum: Wine
---

### Post by johnno56 on 2009-01-03
Greetings,

I have a LCARS shell that I downloaded from [www.lcarsx32.com](www.lcarsx32.com) and trying, without success, to run it via Wine.

The application was written in either VB 2005 or VB.NET. I suspect both was used.

What applications would have to be preloaded to enable VB or VB.NET applications to execute?

Sorry if this sounds too noobish. I am.

Regards

J

ps: Running with Ubuntu 8.04 on a E2200 Intel dual core with 3gig ram and heaps of disk space.

---

### Post by kaivalagi on 2009-01-03
What about GLCARS: [http://www.opendesktop.org/content/show.php/show.php?content=54708](http://www.opendesktop.org/content/show.php/show.php?content=54708) edit: theme and widget set

What you have linked to would need to be recompiled using mono (.net in Linux) I think.

---

### Post by directhex on 2009-01-03
> **kaivalagi said:**
> What you have linked to would need to be recompiled using mono (.net in Linux) I think.

If an app has been written in a portable manner, then there's no need to recompile - CLI binaries are cross-platform. If it's not been written in a portable manner, then recompiling won't help anyway.

---

### Post by kaivalagi on 2009-01-03
> **directhex said:**
> If an app has been written in a portable manner, then there's no need to recompile - CLI binaries are cross-platform. If it's not been written in a portable manner, then recompiling won't help anyway.

Sorry, you're right, what was I thinking...

Does mono support all of the .net framework yet?

I mess around with python in Linux so am not aware of what mono can support from the windows world

[COLOR="Blue"]Edit: needs microsoft.visualbasic v8 which I can't find (in the repos anyway):
** (./LCARSmain.exe:16508): WARNING **: Could not load file or assembly 'Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' or one of its dependencies.
The entry point method could not be loaded[/COLOR]

---

### Post by directhex on 2009-01-03
> **kaivalagi said:**
> [COLOR="Blue"]Edit: needs microsoft.visualbasic v8 which I can't find (in the repos anyway):
** (./LCARSmain.exe:16508): WARNING **: Could not load file or assembly 'Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' or one of its dependencies.
The entry point method could not be loaded[/COLOR]

[http://packages.ubuntu.com/jaunty/libmono-microsoft-visualbasic8.0-cil](http://packages.ubuntu.com/jaunty/libmono-microsoft-visualbasic8.0-cil)

---

### Post by kaivalagi on 2009-01-03
> **directhex said:**
> [http://packages.ubuntu.com/jaunty/libmono-microsoft-visualbasic8.0-cil](http://packages.ubuntu.com/jaunty/libmono-microsoft-visualbasic8.0-cil)

mmmmm

So the best suggestion is for johnno56 to hold off until 9.04 final or mono backports, and hope for the best.

Any way to get those new libraries into 8.10 with minimal fuss?

edit: mono 2.01 is available on the suse 11 livecd, LCARS could be tried with that I guess to see whether it will be feasible in the future...

---

### Post by directhex on 2009-01-03
> **kaivalagi said:**
> Any way to get those new libraries into 8.10 with minimal fuss?

The package from Debian Unstable ought to install without fuss (the Jaunty package won't due to a useless dependency on post-intrepid libc)

---

