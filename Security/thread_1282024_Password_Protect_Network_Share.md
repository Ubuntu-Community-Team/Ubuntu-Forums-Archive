---
title: "Password Protect Network Share"
date: 2009-10-03
forum: Security
---

### Post by Jason Cook on 2009-10-03
I am wondering if there is anyy way to password protect my network shares. I use a laptop and I don't want others to view my files when I am in a public place.

---

### Post by cariboo on 2009-10-03
If you are accessing the internet from a wifi hotspot, turn off file sharing before connecting, open a terminal and type:

```
sudo /etc/init.d/samba stop
```

---

### Post by Jason Cook on 2009-10-04
> **cariboo907 said:**
> ```
sudo /etc/init.d/samba stop
```

This is what I have done in the past but I don't always remember to do this. Is there a way I could set it to automatically stop file sharing when I'm not connected to certain networks. If not then I would like to be able to password protect them.

---

### Post by Jason Cook on 2009-10-05
I don't know what I have done but now whenever someone tries to connect to my computer from the network they need to enter a password.

---

