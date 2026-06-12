---
title: "Postfix ignoring config in main.cf"
date: 2011-04-21
forum: Server Platforms
---

### Post by infecticide on 2011-04-21
Background:

I have virtualized my Ubuntu Server infecticide (192.168.2.100) on Xenserver but because there is no P2V migration available for Ubuntu I did the works by hand.  New machine infecticide-vm ( 192.168.2.108 )


I have amavis setup for mail filtering with the following in the 
main.cf
```

content_filter = smtp-amavis:[127.0.0.1]:10024

```

Amavis is running as confirmed by:
```

amavis   30896  0.0  2.2 227116 93520 ?        Ss   12:38   0:00 amavisd (master)
amavis   30907  0.0  2.2 228396 92232 ?        S    12:38   0:00 amavisd (virgin child)
amavis   30908  0.0  2.2 228396 92232 ?        S    12:38   0:00 amavisd (virgin child)

```
```

tcp        0      0 127.0.0.1:10024         0.0.0.0:*               LISTEN      30896/amavisd (mast

```

I'm getting this error in the mail.log:
```

relay=none, delay=6918, delays=6888/0.22/30/0, dsn=4.4.1, status=deferred (connect to 192.168.2.100[192.168.2.100]:10024: Connection timed out)

```

Why is Postfix not reading this config?   I have restarted services and even rebooted the machine.

---

### Post by elico on 2011-04-21
is amavis service started?
can you connect it using telnet?

---

