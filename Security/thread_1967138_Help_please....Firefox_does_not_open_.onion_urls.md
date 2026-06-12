---
title: "Help please....Firefox does not open .onion urls"
date: 2012-04-27
forum: Security
---

### Post by cece88 on 2012-04-27
I installed everything following the installation guides  on the torproject page.

No problems at all. The [https://**check**]("https://%3Cb%3Echeck%3C/b%3E").**tor**project.org/ page says that my browser is configured to use Tor.

Every other application connected through 'Socks' works fine.

The only problem is that i can not connect to any .onion url. 

It works with the TBB, so the servers are not down.

I have absolutely no idea what the problem could be.

A little help from the experts aroud here would be nice. :)

Thanks!

---

### Post by Hungry Man on 2012-04-27
Are all of them broken or is it just some? Tons of .onion sites are super slow/ completely dead so it wouldn't be surprising.

Are you using the TOR browser bundle? I suggest you try it with that as it's built entirely for TOR use.

It's probably just misconfigured proxy settings but TOR browser bundle is the best way to do it.

---

### Post by cece88 on 2012-04-27
Thanks for the fast reply...:)

When i open them with the configured Firefox, they are all dead.

Like i said, they work with the TBB(Tor browser bundel)

The TBB is fine for surfing but it is not good when you want other applications accessing the net through Tor.

There are not many proxy setings that could be wrong. Socks5 127.0.0.1/9050 in the 

Firefox settings. thats it!

also [https://**check**]("https://%3Cb%3Echeck%3C/b%3E").**tor**project.org/ tells you when your browser is configured right. usually.

---

### Post by ottosykora on 2012-04-29
hmmm, AFAIK you should then be using the dns of the torproject.org too, apparently the TBB does it , well I know it is lot of readme on the torproject  site and all is mixed, old and new documentattion , but when I find time I will look for the solution. There is a readme about that definitely and yes, it is not supposed to work otherwise then either systemwide use of tor or with the TBB.

---

