---
title: "Server or Desktop Edition"
date: 2008-06-08
forum: Server Platforms
---

### Post by dsmith8 on 2008-06-08
Hi guys,

I'm pretty new to Ubuntu and Linux in general(about a year or so dual booting), and am trying to make a file server/MAME cabinet.  Would server or desktop be better for this situation or is it a bad combination all together?

Thanks in advance,

Dan

---

### Post by molotov00 on 2008-06-08
This question is asked a lot and there are many different (complex) answers.

1) A desktop installation will meet your needs.
2) A default server installation has no GUI, but you can install one after the fact.
3) People will say that not using a GUI teaches you more; this is true. But it can also be overwhelming, so it's up to you.

There are security and performance considerations that are also considered in larger environments but your your purposes I think the above points cover what's most important. In your position, I'd install the server edition with a light GUI (sudo apt-get install xubuntu-desktop) if you're mainly using it for serving. I'd also install the ssh server (sudo apt-get install openssh-server) so you can admin the server from another computer, and it'll get you used to the command line.

M

---

### Post by hyper_ch on 2008-06-09
> **molotov00 said:**
> 3) People will say that not using a GUI teaches you more; this is true. But it can also be overwhelming, so it's up to you.

You just have to find the right guide and then it's not overwhelming anymore :)

---

