---
title: "Block proxy"
date: 2009-10-23
forum: Security
---

### Post by Boris Gelbukh on 2009-10-23
Hello!

I want to create an ubuntu computer on which the user must not be distracted off the work browsing the distracting websites (eg. youtube.com). It is important to do it from the terminal because it should be fast and work on many computers.

So, I need to block some websites for a specified user and redirect him to "access denied" page.
Then, to prevent using proxy I want to block it (for a specified user too).

Can anybody help me?

---

### Post by Sarmacid on 2009-10-23
You should look into squid, it's a proxy server and it can be used to deny users from going to certain sites and you can even specify hours when those sites can be accessed.

---

### Post by update_manager on 2009-10-25
> **Boris Gelbukh said:**
> Hello!

I want to create an ubuntu computer on which the user must not be distracted off the work browsing the distracting websites (eg. youtube.com). It is important to do it from the terminal because it should be fast and work on many computers.

So, I need to block some websites for a specified user and redirect him to "access denied" page.
Then, to prevent using proxy I want to block it (for a specified user too).

Can anybody help me?


The simple (lame) way to do this is below:

sudo iptables -I FORWARD -p tcp --dport 80 -m string --string "x-shockwave-flash
" --algo bm -j REJECT

sudo iptables -I FORWARD -p tcp --dport 80 -m string --algo bm --string "application/x-javascript" -j REJECT

sudo iptables -A FORWARD -p tcp ! -d <whitelist> --dport 443 -j REJECT


One of the browse-through-sites at work could get through these, and making users browse without HTTPs is kind of silly. However, dropping any packet with those MIME types will block youtube and webmail systems with minimal effort on your part. Evasion would require a technical user.

---

