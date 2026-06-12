---
title: "UFW port forwarding Woes"
date: 2011-10-04
forum: Server Platforms
---

### Post by hawk2010 on 2011-10-04
Hi all,

I'm running a real time collaboration called Openfire. However I'm having issues when connecting to its web console which is in 9090 since the provider blocks that port. So I thought I could use ufw to redirect the traffic coming to port 80 so it gets redirected to 9090 internally. I read the tutorials and added the following to /etc/ufw/before.rules but still when I type the URL on the browser it doesnt appear to be redirecting. I tried telnetting too. Hope someone could assist.

*nat
:PREROUTING ACCEPT [0:0]
-A PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 9090
COMMIT

---

### Post by hawk2010 on 2011-10-06
Anyone help?

---

### Post by Dangertux on 2011-10-06
If you're going to do that you need a FORWARD -P ACCEPT as well.

---

### Post by hawk2010 on 2011-10-06
Can you be kind enough to let me know the full syntax?
> **Dangertux said:**
> If you're going to do that you need a FORWARD -P ACCEPT as well.

---

### Post by Dangertux on 2011-10-06
I'm not at a computer on my phone  but that is the full iptables syntax. 

If you were going to do it in ufw you are just setting a policy for forward like you did prerouting

So I would assume it would be the same you'd have to look it up to be sure I don't really know for sure in ufw. I just know iptables won't do anything with prerouting if your forward policy is drop or reject.

---

