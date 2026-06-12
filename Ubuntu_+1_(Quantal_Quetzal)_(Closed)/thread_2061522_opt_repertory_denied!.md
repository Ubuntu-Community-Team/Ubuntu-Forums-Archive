---
title: "/opt repertory denied!"
date: 2012-09-22
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Neo40 on 2012-09-22
Hello,

I'm using Ubuntu 12.10 Beta1, full upgraded. I then installed Mobile-media-converter from this site: [http://www.miksoft.net/mobileMediaConverterDown.htm](http://www.miksoft.net/mobileMediaConverterDown.htm)

The program is installed into /opt and for some reason, I have no permission to access to this directory.
Any one can help me?
Thanks in advanced!

---

### Post by cariboo on 2012-09-22
You can access the directory, by escalating your users privileges. Press Alt-F2 and type:

```
gksu nautilus
```

Type your password, and once nautilus opens navigate to /opt.

---

### Post by Neo40 on 2012-09-23
Thanks.

---

