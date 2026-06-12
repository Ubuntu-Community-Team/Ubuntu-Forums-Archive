---
title: "firestarter suddenly blocks all the connections from the router.any ideas?"
date: 2009-07-25
forum: Security
---

### Post by supadup on 2009-07-25
im on a netcafe right now so i cant give the output of command..
im looking for a way to "reset" firestarter
any ideas?

---

### Post by swoll1980 on 2009-07-25
> **supadup said:**
> im on a netcafe right now so i cant give the output of command..
im looking for a way to "reset" firestarter
any ideas?

Firestarter isn't a firewall. It's a graphical front end to the firewall program iptables. It's pretty complicated stuff. There's a good tutorial [here]("http://iptables-tutorial.frozentux.net/iptables-tutorial.html").

---

### Post by deadspider187 on 2009-07-25
From my understanding, Firestarted has been out of development for a long time, and probably shouldn't be used as a result.  There are a lot of replacements, but the closest one is [gufw]("http://gufw.tuxfamily.org/index.html").

---

### Post by bodhi.zazen on 2009-07-25
Hard to tell from your post.

You can configure firestarter from teh gui interface ```
gksu firestarter
```

You can flush your iptables with ```
sudo iptables -F
```

---

