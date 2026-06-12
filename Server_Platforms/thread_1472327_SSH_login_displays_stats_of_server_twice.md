---
title: "SSH login displays stats of server twice"
date: 2010-05-04
forum: Server Platforms
---

### Post by Smigma on 2010-05-04
This is a very trivial thing, but when I SSH into my newly updated 10.04 server, the stats of the server are displayed on the screen twice. How can i fix it to just display once? This is what it is doing.

> Linux xxxxx 2.6.32-21-generic-pae #32-Ubuntu SMP Fri Apr 16 09:39:35 UTC 2010 i686 GNU/Linux
Ubuntu 10.04 LTS

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

  System information as of Tue May  4 08:41:22 EDT 2010

  System load:    0.9                 Memory usage: 38%   Processes:       261
  Usage of /home: 38.2% of 439.19GB   Swap usage:   0%    Users logged in: 1

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

1 package can be updated.
0 updates are security updates.

Ubuntu 10.04 LTS

Welcome to the Ubuntu Server!
 * Documentation:  [http://www.ubuntu.com/server/doc](http://www.ubuntu.com/server/doc)
Last login: Tue May  4 08:40:20 2010 from ashgw.emcor.net
Linux xxxx2.6.32-21-generic-pae #32-Ubuntu SMP Fri Apr 16 09:39:35 UTC 2010 i686 GNU/Linux
Ubuntu 10.04 LTS

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

  System information as of Tue May  4 08:41:22 EDT 2010

  System load:    0.9                 Memory usage: 38%   Processes:       261
  Usage of /home: 38.2% of 439.19GB   Swap usage:   0%    Users logged in: 1

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

1 package can be updated.
0 updates are security updates.

Ubuntu 10.04 LTS

Welcome to the Ubuntu Server!
 * Documentation:  [http://www.ubuntu.com/server/doc](http://www.ubuntu.com/server/doc)

Thanks in advance! Loving the new release!

---

### Post by anglican on 2010-05-04
> **Smigma said:**
> This is a very trivial thing, but when I SSH into my newly updated 10.04 server, the stats of the server are displayed on the screen twice. How can i fix it to just display once? This is what it is doing.



Thanks in advance! Loving the new release!
I'm not sure it will get rid of all of this, but commenting out "PrintMotd yes" and "PrintLastLog yes" (by putting a # in front) in the file /etc/ssh/sshd_config then restarting sshd should help.

H

---

### Post by Smigma on 2010-05-04
That did it! 

Thank you so much, anglican!

---

### Post by hyperfitz on 2011-05-05
I just tried that method on my servers and now they print the stats 4 times. :grin:

It does seem minor, however one of the printouts (two now) displays incorrect stats.

An explanation would be helpful if anyone has one.

---

### Post by stmiller on 2011-05-05
FWIW I started seeing this as well recently. Weird! Help!?

Edit: trying to comment out those options in sshd_config has no effect, strangely enough.

---

### Post by CharlesA on 2011-05-06
Easier fix: Delete /etc/motd.tail

There is a bug that causes that file not to be overwritten.

---

### Post by Shotgun Ted on 2011-05-10
> **CharlesA said:**
> Easier fix: Delete /etc/motd.tail

There is a bug that causes that file not to be overwritten.

Thanks - that worked fine for me.

ST

---

### Post by Lloyd_mcse on 2011-05-11
Thanks CharlesA that did the trick :)

---

### Post by hyperfitz on 2011-05-11
That did the trick, CharlesA; much appreciated.

---

### Post by MK++ on 2011-05-26
Guys, these are not duplicate stats, these are "Right-Now-Stats" and "Last-Login-Stats", yet,  CharlesA is totally right: /etc/motd.tail contents will be displayed in whatever case! So, if it has got same stats as "Right-Now" it would look like being displayed twice.

BR

---

### Post by CrusaderAD on 2011-06-07
> **CharlesA said:**
> Easier fix: Delete /etc/motd.tail

There is a bug that causes that file not to be overwritten.

This worked for me, thank you!

---

### Post by brettg on 2011-06-08
My wishes;

1) That people would google a problem before asking the same question that has been answered a 1000 times before

2) People would mark their threads as solved

I know, I know, it's too much to ask.

---

### Post by StygianAgenda on 2011-09-15
> **brettg said:**
> My wishes;

1) That people would google a problem before asking the same question that has been answered a 1000 times before

2) People would mark their threads as solved

I know, I know, it's too much to ask.

I'll second that.  It's getting so bad in fact that we're beginning to need a "solutions wiki" or something along those lines that contains a concise reference to many of the problems people have faced and fixed in each release.  I've considered putting something together like that, but my domain cannot support the traffic that it would bring due to the cap enforced by my ISP (Comcast).  And really, it's something that would be more appropriately hosted by Canonical.  :-k

Anyways, for myself, Google is the first stop for anything related to troubleshooting any Linux problem, regardless of the platform or vendor.  It's sort of a no-brainer... Google is a data-mining engine (technical a step above a search engine), and if used correctly (see the book, Google Hacking for Penetration Testing, and [http://en.wikipedia.org/wiki/Google_hacking](http://en.wikipedia.org/wiki/Google_hacking) for more details on how to use Google's advanced capabilities), it can unearth just about any information that isn't completely locked down. :wink:

---

