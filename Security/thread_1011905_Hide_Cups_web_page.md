---
title: "Hide Cups web page"
date: 2008-12-15
forum: Security
---

### Post by white_shadow on 2008-12-15
Hi
I have the cups working fine.

But now i only want to hide the cups web administration.

I don't want that other people see cups web page:

[http://my_server_name.something:631](http://my_server_name.something:631)

It's posible?

Thank's in advance

Marco

---

### Post by Nepherte on 2008-12-15
Just block access to the port cups uses (631) in the firewall. If you use ufw, you can type this in the terminal:
```
sudo ufw deny 631
```

---

