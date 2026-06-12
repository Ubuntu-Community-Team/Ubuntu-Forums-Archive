---
title: "How to adjust mouse wheel scroll?"
date: 2016-04-13
forum: Ubuntu Development Version
---

### Post by psychedelicwonders2 on 2016-04-13
Seems there isn't an option to adjust the mouse wheel scroll inside of system settings>mouse & touchpad, only button & overall speed

And as it is now, the scrolling affect is far too much and skips content and jumps to far on the webpage/whatever

So how do I ease up the mouse wheel scrolling?

---

### Post by sgage on 2016-04-13
> **psychedelicwonders2 said:**
> Seems there isn't an option to adjust the mouse wheel scroll inside of system settings>mouse & touchpad, only button & overall speed

And as it is now, the scrolling affect is far too much and skips content and jumps to far on the webpage/whatever

So how do I ease up the mouse wheel scrolling?

Are you dual-booting with Windows, and do you have a MS wireless mouse? If so, after rebooting into Ubuntu after a Windows session, you can just unplug and replug the USB transceiver (or shutdown and cold boot). Windows leaves the transceiver hardware in a hyper state.

If not, I can't help you - but I'll bet there's some xorg.conf incantation that will do what you need...

---

### Post by psychedelicwonders2 on 2016-04-13
Yes in fact I am dual booting (on separate SSDs) and using a MS mouse/keyboard.  I'll do as you suggest and hopefully that clears up the problem.

Thanks.

---

### Post by izznogooood on 2016-04-15
Sorry for hijacking your thread but I have a similar problem, I want to increase scroll speed. (No MS/Mouse).

---

### Post by psychedelicwonders2 on 2016-04-17
It seems this is hit or miss as once I shut it down, even if I haven't booted to windows, the mouse wheel scrolling goes crazy until I unplug the USB and plug it back in - even during live use of OS without having to reboot, it fixes itself.

But it's frustrating to even have to continue to do this.

Any idea on a permanent fix?  Perhaps once 16.04 is in final LTS and not just in beta this kink will be worked out?  Or is there something else I can try now instead of having to manually & physically remove it and plug it back in every time?

---

### Post by sgage on 2016-04-18
As far as I know, there is no permanent fix. I agree that it's a pain, and would love to find a permanent fix. Perhaps there's some X configuration magic that would do it, but I haven't found it.

Strange that shut down/boot to Linux doesn't work for you... works every time here.

---

### Post by vasa1 on 2016-04-18
OP, which version of *buntu are you using? And are you seeing issues across the board (gtk2, gtk3, and qt apps)? Or only when using gtk3 apps?

[https://bugs.archlinux.org/task/35348](https://bugs.archlinux.org/task/35348)
[https://bugzilla.redhat.com/show_bug.cgi?id=1242251](https://bugzilla.redhat.com/show_bug.cgi?id=1242251)
[https://lists.debian.org/debian-user/2015/07/msg00918.html](https://lists.debian.org/debian-user/2015/07/msg00918.html)
[https://bugzilla.mozilla.org/show_bug.cgi?id=958868](https://bugzilla.mozilla.org/show_bug.cgi?id=958868)

---

### Post by psychedelicwonders2 on 2016-04-18
I'm using the latest version of 16.04 (well at least of last night) and not sure what gtk2, 3 or qt apps means - how do I find the answer to this for you?

---

### Post by vasa1 on 2016-04-18
Here's someone addressing that question: [https://www.reddit.com/r/linux/comments/1x6lce/eli5_what_are_the_prime_differences_between_gtk2/cf8or5w](https://www.reddit.com/r/linux/comments/1x6lce/eli5_what_are_the_prime_differences_between_gtk2/cf8or5w)

And here's a bit comparing gtk and qt: [https://www.wikivs.com/wiki/GTK_vs_Qt](https://www.wikivs.com/wiki/GTK_vs_Qt)

When I searched for mouse scroll issues, I came across references to how the toolkit (/gtk/gtk3/qt) could possibly have a role. Hence the links.

Getting a bit specific, our systems, even 16.04, have both applications that use gtk2 or gtk3: Till some time ago, Firefox and LibreOffice used gtk2. The LibreOffice version with 16.04 is gtk3. I think Firefox is still at v45 on 16.04 and so that's still gtk2. Fx 46 will be released a few days after 16.04 and that will be gtk3.

So if you could isolate your scrolling issues to a particular toolkit, that would be a pointer. OTOH, if what you're seeing is across the board, then the answer will be elsewhere.

---

