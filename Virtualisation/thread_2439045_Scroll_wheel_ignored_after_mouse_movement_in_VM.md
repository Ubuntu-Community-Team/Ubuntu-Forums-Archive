---
title: "Scroll wheel ignored after mouse movement in VM"
date: 2020-03-22
forum: Virtualisation
---

### Post by XSource on 2020-03-22
**TL;DR:** the first click of the scroll wheel after moving the mouse is ignored in some programs (e.g. chrome and terminal) but not all (e.g. firefox) since at least Ubuntu 16.04 and in Vbox and VMWare.

Hello. Weird mouse problem, as explained in the "TL;DR". This makes scrolling in chrome and the terminal incredibly frustrating, since it's pretty natural to move the mouse some while scrolling and that movement effectively stops the scrolling almost entirely. I ran into this problem years ago and never found a solution, but I did find a post online (even then ancient) about the problem that helped me realize it was the system ignoring the first click of the scroll wheel after a mouse movement. I can replicate that exactly (move the mouse, scroll one click nothing happens, scroll a second click the screen moves).

For years I've just used Debian for virtualization as the problem doesn't happen there. I tried virtualizing Ubuntu (19.10) again today on a Win 10 host with VMWare hoping the problem has been fixed but it hasn't been and makes it really hard to use the system.

I'm not even sure how to begin debugging the problem and could really use some help. If any logs or other info is needed I'm happy to provide them. I have open-vm-tools installed right now, and have had the equivalent tools or additions installed every time in the past that I've had this problem.

---

### Post by XSource on 2020-04-08
bump

Also wanted to share a thought. I'm surprised that more people haven't had this problem, because I seem to have it perfectly consistently across versions of host, guest, and VM manager. And granted, I've found some posts over time from others who have it, but it is only a few people and this seems like it should be affecting everyone? idk

---

### Post by XSource on 2020-05-03
Does anyone have advice on how I can get some traction on this? No one is even looking at this thread (it has 2 views right now and they might both be mine?). I get that this is a niche problem (although as I said in my last post I don't understand how it could be) but is there anything I can do? Should I be asking somewhere else? Or is it just normal for stuff like this to take this long to get feedback on?

---

