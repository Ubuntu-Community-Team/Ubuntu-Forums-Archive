---
title: "Ubuntu Server (x64) Blocking Port 80 (HTTP)"
date: 2010-10-05
forum: Server Platforms
---

### Post by andersensam on 2010-10-05
Ok, I have Ubuntu Server (x64) installed on my box with Apache2 and Squid. For awahile port 80 (http) was fine, I could update packages and use wget. Then one random day port 80 became blocked for incoming traffic. I couldn't use apt-get and had to change to an ftp mirror to update. Also wget is not working. Where did I go wrong?

---

### Post by arrrghhh on 2010-10-05
Hmmmmm so can you hit the apache web server from another machine?

It sounds like you're getting outbound traffic blocked, but you say it's incoming traffic.  Wget doesn't work from the server?  Does it work for any other machines on the same switch/LAN?

I'm not sure what could do this, other than a change in your network.  I can't think of anything on Ubuntu config that would just prevent port 80 outbound traffic... there's plenty to check with incoming traffic issues...

---

### Post by andersensam on 2010-10-05
SOLVED: In the end I looked through the Apache config and Squid's and found nothing out of the ordinary. I ended changing my DNS to another provider and now everything works again! I guess the old DNS was having problems...Thanks anyway

---

### Post by arrrghhh on 2010-10-05
> **andersensam said:**
> SOLVED: In the end I looked through the Apache config and Squid's and found nothing out of the ordinary. I ended changing my DNS to another provider and now everything works again! I guess the old DNS was having problems...Thanks anyway

LOL that'll do it.  Glad it's workin again for ya!

---

