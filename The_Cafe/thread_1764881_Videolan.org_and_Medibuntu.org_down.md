---
title: "Videolan.org and Medibuntu.org down?"
date: 2011-05-22
forum: The Cafe
---

### Post by CoreyB. on 2011-05-22
I haven't been able to go to [videolan.org]("http://www.videolan.org") or [medibuntu.org]("http://medibuntu.org") for around two weeks.  But according to [downforeveryoneorjustme]("http://downforeveryoneorjustme.com"), both of them are up.

[http://www.downforeveryoneorjustme.com/videolan.org]("http://www.downforeveryoneorjustme.com/videolan.org")

[http://www.downforeveryoneorjustme.com/medibuntu.org]("http://www.downforeveryoneorjustme.com/medibuntu.org")

Are these sites up for you guys are is it really just me?

Thanks!

---

### Post by kostkon on 2011-05-22
Yeap, everything's fine here.

---

### Post by CoreyB. on 2011-05-22
Huh, that's weird.  Whenever I try to go to those sites I get a connection timeout.  That is also probably why my medibuntu repo on my ubuntu installations haven't been able to connect for weeks.

Anyone know how to go about troubleshooting/fixing this issue?

---

### Post by Fedz on 2011-05-22
Could be your ISPs dns!

Maybe change your dns to **_[OpenDNS](http://OpenDNS.com)**_ IPs (208.67.222.222 & 208.67.220.220) & or use [http://www.surf-anon.com](http://www.surf-anon.com) to access the site :)

---

### Post by CoreyB. on 2011-05-22
> **Fedz said:**
> Could be your ISPs dns!

Maybe change your dns to **_[OpenDNS](http://OpenDNS.com)**_ IPs (208.67.222.222 & 208.67.220.220) & or use [http://www.surf-anon.com](http://www.surf-anon.com) to access the site :)

I switched to OpenDNS but that still doesn't work. :(

---

### Post by Fedz on 2011-05-22
> **CoreyB. said:**
> I switched to OpenDNS but that still doesn't work. :(
Did you disconnect then reconnect for the dns IPs to take effect? :)

What about accessing the sites via [http://www.surf-anon.com?](http://www.surf-anon.com?)

Cheers,

---

### Post by CoreyB. on 2011-05-22
Yeah, I reset everything and the opendns welcome page says I am using opendns.  The surf-anon website works.

Both Videolan and medibuntu have ip addresses that start with 88.191.xxx.x, is that just a coincidence or do I have an issue with this range of addresses?

---

### Post by jerenept on 2011-05-22
> **CoreyB. said:**
> I switched to OpenDNS but that still doesn't work. :(

Try setting your proxy server to: [http://jerenept.homeftp.org:8118/](http://jerenept.homeftp.org:8118/)

Might help (that's my havp/privoxy setup), my computer can access those sites...

---

### Post by CoreyB. on 2011-05-22
Videolan's ip address is 88.191.250.2 and Medibuntu's ip address is 88.191.127.22.

Is it possible that my ISP might be blocking things coming from that ip range or something?  If so, maybe I'll see what my ISP knows.

---

### Post by d2btoo on 2011-05-23
I can access videolan.org main pages, but forums and wiki's are inaccessible for weeks now. ;(

---

### Post by sdowney717 on 2011-05-23
everything is fine for me

---

### Post by d2btoo on 2011-05-23
Ah! It's opera turbo causing the problem for me, I can now access the forum using fox or google-chrome. Thanks.

---

