---
title: "How to make Apache can listen multi port?"
date: 2007-03-24
forum: Server Platforms
---

### Post by explorer1979 on 2007-03-24
Hi all,

I want to my apache can listening port 80 and port 8000 at the same time.

Do it is possible? If so, how to setting?

Thank you for time read this

Best Regards,
Jimmy Chan

---

### Post by pppetter on 2007-03-24
I do think that you need to different instances of apache in that case. 

Just out of curiosity, why would you want such a setup?

---

### Post by Wallace on 2007-03-24
Edit /etc/apache2/ports.conf and add a line, so it looks something like:

```
Listen 80
Listen 8000
```

Restart or reload apache and that should be it.

---

### Post by explorer1979 on 2007-03-24
pppetter,

Why I need that, since my ISP have not block the Port 80, but it post is used by my company's IP Camera Security System of my Boss.

And the server are installed on LAN for intranet testing. We using ADSL with NAT, so it is why when I need go outside to test the server or build something base on it, I need Apache listening multi ports at the same time, one for the public web site port 8081 and the Port 80 or the intranet LAN.

:-)

---

