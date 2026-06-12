---
title: "Google Chrome[dev] now has integrated Flash Player"
date: 2010-03-30
forum: The Cafe
---

### Post by Knowle on 2010-03-30
This is just the initial integration of Flash Player with Chrome in the developer channel. Now when Chrome is downloaded[dev] you'll get the latest version of Flash Player(10.1 beta 3) and updates for Flash can be pushed out as well. I'm kind of torn between liking it and hating it. Thoughts?

[http://blog.chromium.org/2010/03/bringing-improved-support-for-adobe.html](http://blog.chromium.org/2010/03/bringing-improved-support-for-adobe.html)

---

### Post by Psumi on 2010-03-30
10.1 has GPU accelerations right? I don't think my FireGL 9000 will be happy with that.

---

### Post by garvinrick4 on 2010-03-30
In Windows Google has figured a way to get into Windows Task Scheduler for a while now.
I have seen no other scheduled tasks except for Windows tasks. So it is probably nice for
Adobe to ride into Windows on Googles back. Will it effect Chromium the Linux browser?
Maybe effect the Google Linux OS when it comes out for sure. Not quite Open Source is it.
Was hoping to get html5 but what are you going to do.

---

### Post by dragos240 on 2010-03-30
So, is it in chromium too? If so, flash src code?

---

### Post by Cracauer on 2010-03-30
I would have preferred if they put getting a HTML5 solution into the Chrome browser (to watch youtube) on the fast track.

Chromium OS comes with Flash standard for a while, BTW.

---

### Post by papangul on 2010-03-30
> **Knowle said:**
>  I'm kind of torn between liking it and hating it. Thoughts?[/url]

It is sufficient if there is a button somewhere to disable flash, because the current state of the web is such that flash is indispensable; but it's a nuisance most of the time.

---

### Post by Knowle on 2010-03-30
> **Psumi said:**
> 10.1 has GPU accelerations right? I don't think my FireGL 9000 will be happy with that.That's right, 10.1 has GPU acceleration. It will only work on supported cards as far as I'm aware. For example, [http://www.nvidia.com/object/gpus_supporting_adobeflash.html](http://www.nvidia.com/object/gpus_supporting_adobeflash.html)

> **dragos240 said:**
> So, is it in chromium too? If so, flash src code?As of right now, I believe not.

> **papangul said:**
> It is sufficient if there is a button somewhere to disable flash, because the current state of the web is such that flash is indispensable; but it's a nuisance most of the time.Currently in the Dev channel you have to enable it with the --enable-internal-flash command line flag. In the future should you want to disable flash or any other plugin you can do so from the about: plugins page. With the help of Adobe the Chrome team plans on extending Chrome's sandbox to web pages with Flash content.

---

