---
title: "connecting to cups using a easier url"
date: 2011-12-22
forum: Server Platforms
---

### Post by herbert tamayo on 2011-12-22
Hi, I'm always forget the defult port to connect to cups, so i would like to create an easier way to connect to it, for example I don't want to use:

```

http://localhost:631

```

I would like to use:
```

http://localhost/printers

```

I think this change has to be done in apache2.conf but honestly I don't know what lines should I write; so my question is:

what lines should I write in apache2.conf to work this?

regards

---

### Post by lykwydchykyn on 2011-12-22
Try this:
```

Redirect /printers http://localhost:631

```

Then restart apache.

---

