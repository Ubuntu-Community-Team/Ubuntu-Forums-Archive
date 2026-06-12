---
title: "Chromium or google Chrome on Ubuntu Unity 8 (BQ M10)"
date: 2017-01-06
forum: Ubuntu Phone and Tablet
---

### Post by obroden on 2017-01-06
Hi, I've been trying to install Chromium and Google Chrome on my BQ M10 Ubuntu edition in a libertine box. When I install Chromium (chromium-browser) It crashes when I try to start it and i says Google Chrome (google-chrome-stable) is not availeble.

I really need to use google chrome for work because the program we are using for data base stuff is running on chrome :(.

Has anyone else managed to get Chromium running on Ubuntu Unity 8?

/Oskar

---

### Post by g33zr on 2017-01-10
Chromium and Chrome are both available in Synaptic Package Manager, however they won't run properly if you don't have all the proper packages/dependencies that go with them. I'd recommend going with Chrome. If you're having problems with it, try uninstalling and then re-installing Chrome. You can do this via SPM or cli: sudo apt install google-chrome-stable. Good luck.

---

### Post by makouser on 2017-01-17
This is something I want too. Chrome on Touch that is.

I may be over simplifying this, but surely this is a chip issue. Where are you getting Chrome for Mediatek? I'm impressed that you have got as far as installing.

---

### Post by krusty8 on 2017-01-17
> **makouser said:**
> 
I may be over simplifying this

I think you are over complicating it. I don't think a browser needs to be compiled to a specific chip vendor. Arm architecture, called armhf if I'm not mistaken should suffice. And Ubuntu has large arm repositories.

---

### Post by makouser on 2017-01-18
Krusty8

You're probably right - over thinking again:-(

But thinking about it, does the Touch device only expect Snap apps? That might explain why it says stuff is missing. How would you even go about installing it? I'd like to give it a try on my N4.

Edit: Hmm, never mind the N4, I wouldn't mind running Chrome under Unity 8 on my laptop. How do you even go about that?

---

### Post by krusty8 on 2017-01-18
> **makouser said:**
> does the Touch device only expect Snap apps? 
Clicks normally, but debs are possible via libertine.

> That might explain why it says stuff is missing. How would you even go about installing it? I'd like to give it a try on my N4.

Check out libertine-container-manager --help . Its not super widely used and documented, but if you do a bit of internet search you'll find tips.

> 
Edit: Hmm, never mind the N4, I wouldn't mind running Chrome under Unity 8 on my laptop. How do you even go about that? I've never used chrome, nor U8 on desktop, so I'm not the best to advise.

---

### Post by makouser on 2017-01-18
I tried Libertine on the desktop without much success. Didn't try very hard to be honest. Figured I'd wait until it was a bit more mature.

Maybe I'll give it a go on the N4 if I get a bit bored ;-)

---

