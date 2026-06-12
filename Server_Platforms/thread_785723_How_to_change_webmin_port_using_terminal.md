---
title: "How to change webmin port using terminal??"
date: 2008-05-07
forum: Server Platforms
---

### Post by rado3105 on 2008-05-07
Hi I would like to ask how to change webmin port, because I changed it in browser to 21 and after I cant get there over that port(browser knows that it is not port for browsing) so he cant allow me to get there.
I need to change it using putty, can you tell me where is config file with port changing.

---

### Post by quelx on 2008-05-08
```
sudo nano -w /etc/webmin/miniserv.conf
```

---

