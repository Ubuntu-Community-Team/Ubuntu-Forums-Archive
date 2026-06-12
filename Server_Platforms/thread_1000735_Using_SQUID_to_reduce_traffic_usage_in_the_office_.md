---
title: "Using SQUID to reduce traffic usage in the office - how effective?"
date: 2008-12-03
forum: Server Platforms
---

### Post by FractalizeR on 2008-12-03
Hello.

We are working in the office where about 5-6 machines have Internet access. We pay for each GB of traffic we consume and that's quite expensive. Almost no worker download files. Just surfing websites (including our corporate one that is located outside of local network thus we pay for accessing it too).

I am thinking of purchasing low-end cheap PC to install SQUID and setup NAT to direct all office internet traffic through it.

Should I expect traffic consumption reduce counted by ISP in this case at all? If yes, what is the estimated factor of bandwidth consumtion reduce? I understand, that that depends on what internet sites are the staff surfs etc etc. I just care about something average coming from someone's practice. Increasing SQUID HDD cache to 10-20Gb is not a big problem I think. HDDs are pretty big and cheap nowadays.

---

### Post by hictio on 2008-12-03
I don't have exact figures, sorry, but, if I may so, and even if this is the Ubuntu forum, I would recommend you to use a ready made solution like [IPCop](http://www.ipcop.org/).
I use that at work, and it couldn't be any simpler to install, setup and administer.
And it's free :D

---

### Post by FractalizeR on 2008-12-03
Yes, you are right. I will think about it. I guess noone has any exact fugures about SQUID cache effectiveness...

---

### Post by shieldw0lf on 2008-12-03
It's entirely dependent on the surfing patterns of your users.  If people go to the same static content day after day, your web usage will become zero.  If they each access different dynamic content on a daily basis, the effect can be negligible.  The reality will be somewhere in between.

---

### Post by FractalizeR on 2008-12-03
> **shieldw0lf said:**
> It's entirely dependent on the surfing patterns of your users.  If people go to the same static content day after day, your web usage will become zero.  If they each access different dynamic content on a daily basis, the effect can be negligible.  The reality will be somewhere in between.

I understand. ;)

---

### Post by HermanAB on 2008-12-03
In my own tests, Squid-cache will save about 30% bandwidth in its default configuration.  You can make it more effective (50% to 60%), by combining it with Dansguardian (or SquidGuard) and blocking evil content and advertisements.

So, it is well worth the effort to set it up. With most other Linux distros you can set it up with one or two clicks in a wizard, but it is a bit more of a schlep with Ubuntu.

Cheers,

Herman

---

### Post by FractalizeR on 2008-12-03
Thanks a lot, friend! I will try ;)

---

