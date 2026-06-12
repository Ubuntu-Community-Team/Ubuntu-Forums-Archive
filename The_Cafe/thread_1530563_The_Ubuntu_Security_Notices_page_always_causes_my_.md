---
title: "The Ubuntu Security Notices page always causes my Firefow to hang"
date: 2010-07-13
forum: The Cafe
---

### Post by Sporkman on 2010-07-13
Whenever I open the page:

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

my Firefox always hangs for 5-10 seconds (and turns gray)... What's up with that??

---

### Post by Dustin2128 on 2010-07-13
move this to support, you'll get answers more quickly.

---

### Post by FuturePilot on 2010-07-13
It's an extremely large page. It froze for about 3 seconds for me on a Core 2 Duo.

---

### Post by Lucradia on 2010-07-13
> **FuturePilot said:**
> It's an extremely large page. It froze for about 3 seconds for me on a Core 2 Duo.

Hung for about 4 seconds on a core i7 (1.6 GHz > 2.8 Ghz turbo)

In windows... firefox.

---

### Post by FuturePilot on 2010-07-13
Odd, tried a second time and it hung for 13 seconds.

---

### Post by Mr. Picklesworth on 2010-07-13
That isn't a Firefox thing. The reason is pretty simple: it's an enormous page. 500kb with 11565 lines of HTML, in much need of fancy Javascript and / or separate pages.

I'm filing a bug report ;)

Edit:
Filed! [https://bugs.edge.launchpad.net/ubuntu-website/+bug/605238](https://bugs.edge.launchpad.net/ubuntu-website/+bug/605238)

---

### Post by ubunterooster on 2010-07-13
it hangs with CPU at 8oo MHZ or 4GHZ for the same amount of time...odd...

---

### Post by Colro on 2010-07-13
My i7 laptop running chrome on windows 7 loaded it instantaneously with zero delays whatsoever.

---

### Post by libssd on 2010-07-13
> **Colro said:**
> My i7 laptop running chrome on windows 7 loaded it instantaneously with zero delays whatsoever.
I believe that this is an illusion; Chrome is showing you the *beginning* of this page, while it's still loading the rest. Unless you have a multi-gigabit pipe, it's going to take more than instantly to transfer 500kb of HTML. 

I don't remember if this is a FF option or not, but some browsers won't render a page until the entire page has finished loading. This makes a huge difference in the *perceived* speed of a browser.

---

### Post by lovinglinux on 2010-07-13
> **Colro said:**
> My i7 laptop running chrome on windows 7 loaded it instantaneously with zero delays whatsoever.

Unfortunately I must admit Chrome doesn't choke with that page here, while Firefox does. I have a Core2Duo E7500, running 32bit Ubuntu with KDE.

---

### Post by lovinglinux on 2010-07-13
> **libssd said:**
> I believe that this is an illusion; Chrome is showing you the *beginning* of this page, while it's still loading the rest. Unless you have a multi-gigabit pipe, it's going to take more than instantly to transfer 500kb of HTML. 

I don't remember if this is a FF option or not, but some browsers won't render a page until the entire page has finished loading. This makes a huge difference in the *perceived* speed of a browser.

Is not just about time to load the page. Firefox becomes unresponsive. I guess this is the only time Chrome javascript engine speed made any difference for me :)

---

### Post by libssd on 2010-07-13
Here's an example of why I prefer Chrome to FF. Since posting my comment on the huge page about 45 minutes ago, I closed Firefox and put my netbook in suspend mode for about 20 minutes. When it resumed, I noticed that system monitor (which I run in a panel) was showing the CPU as pegged. I opened up system monitor, and took a couple of screen shots (attached). The *only* application running when I took these screen shots was system monitor, but as you can see, a Firefox process was hogging resources. As soon as I killed firefox-bin, CPU utilization dropped to normal levels -- and stayed there after starting Chrome to post this message.

---

