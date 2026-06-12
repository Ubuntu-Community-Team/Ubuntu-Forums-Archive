---
title: "Firefox and Thunderbird are not working well since yesterday's updates"
date: 2017-01-11
forum: Ubuntu Development Version
---

### Post by fthx on 2017-01-11
Hi,

I noticed that I cannot read some emails on TB. But that's not all : I cannot read some emails too with Gmail on FF.
And that's not all ! : I did not succeed to write this new thread using FF, input fields are blank and I cannot enter any text sor the subject, e.g. .

With Chrome, all is ok.

I think to pixbuf or gtk updates, but I'm far from being an expert. I have deleted xserver-xorg-video-intel too, but I believe it was no more used some time ago ?

I know that Jeremy Bicha read this forum... ;-)

---

### Post by fthx on 2017-01-24
Ok I got it : it was a font issue.
I've simply reinstalled fontconfig to regenerate all fonts stuff.
Solved for FF+TB.

I did not hack any font recently so why did this happen is still open.

---

### Post by jbicha on 2017-01-26
I had a similar [bug]("https://bugs.launchpad.net/ubuntu/+source/fontconfig/+bug/1651922") but only as I upgraded from 16.10 to 17.04 Alpha.

Someone should test the upgrade again to see if we can reproduce the issue.

---

