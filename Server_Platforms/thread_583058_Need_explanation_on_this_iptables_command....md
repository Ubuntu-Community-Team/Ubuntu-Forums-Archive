---
title: "Need explanation on this iptables command..."
date: 2007-10-20
forum: Server Platforms
---

### Post by Overbyte on 2007-10-20
```
iptables -A INPUT -p tcp –dport $TORRENT_CLIENT_PORT –tcp-flags RST RST -j DROP
```

I found it on some old blog with some disgruntled posts about Comcast doing what they do best: shaping Bittorrent traffic. :)

Although I'm not on Comcast (I don't live in the US), I'm just curious to what that iptables command does...and if it works.

And what's an RST flag?

Thanks in advance!

---

### Post by jlintz on 2007-10-20
This drops all incoming packets going to bittorrent ports with the RST flag set I believe. Although I don't know how well this would work since the ports are randomized alot of the times.  I guess his ISP's method of traffic shapping was to break his bittorrent connections?  Doesn't sound right

---

### Post by Overbyte on 2007-10-21
Yeah, the blog said that's how Comcast was able to prevent people from seeding their torrents. They can normally upload in a torrent, but once the download reaches 100%, the upload speed drops to 0 kbps flat.

We may never know... :)

---

### Post by MJN on 2007-10-21
Some further info at [http://www.msnbc.msn.com/id/21376597/](http://www.msnbc.msn.com/id/21376597/) and the slashdot discussion at _[http://slashdot.org/article.pl?sid=07/10/19/1417238](http://slashdot.org/article.pl?sid=07/10/19/1417238)_

Note it is likely that both ends would need to ignore the RST packets as it seems Comcast are sending them to both source and destination.

Mathew

---

