---
title: "Firestarter"
date: 2008-05-08
forum: Security
---

### Post by PaoloRicardo on 2008-05-08
Just installed Firestarter. I want it load up when I log on but the Firestarter icon doesn't appear in the Gnome panel and I have to start it manually.

Is there a way to get it to start up when I log on?

---

### Post by vishzilla on 2008-05-08
Firestarter is loaded at startup. If you check out Firestarter, it shows the activities right from when you log on.

---

### Post by hyper_ch on 2008-05-08
It is unnecessary to run firestarter all the time... firestarter is NOT a firewall but merely a front-end configuration tool for the actual firewall called IPTABLES which always runs...

Besides, do you have any compelling reasons to run firestarter at all?

---

### Post by didac on 2008-05-08
Check this page:

[http://www.howtoadvice.com/AutoFirestarter/](http://www.howtoadvice.com/AutoFirestarter/)

---

### Post by Kognit on 2008-05-08
> **PaoloRicardo said:**
> Just installed Firestarter. I want it load up when I log on but the Firestarter icon doesn't appear in the Gnome panel and I have to start it manually.

Is there a way to get it to start up when I log on?

If you want to know if the firestarter is running, type the following in terminal:

```
sudo /etc/init.d/firestarter status
```

---

### Post by PaoloRicardo on 2008-05-08
OK, thanks guys. I was not aware that the IPTables firewall started automatically. If that is the case then I don't need to see Firestarter - unless I want to reconfigure IPTables.

---

### Post by hyper_ch on 2008-05-09
> **PaoloRicardo said:**
> unless I want to reconfigure IPTables.
or directly monitor the activities

---

