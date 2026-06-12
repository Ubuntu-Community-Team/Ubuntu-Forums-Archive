---
title: "Searching in the dash - Legal notice"
date: 2012-10-12
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by wojox on 2012-10-12
How can I turn this off? I like the Dash, but don't really care for the icon. I searched dconf but no luck.

---

### Post by philinux on 2012-10-12
> **wojox said:**
> How can I turn this off? I like the Dash, but don't really care for the icon. I searched dconf but no luck.

I just got the unity update which refers to this bug.

[https://bugs.launchpad.net/unity/+bug/1065652](https://bugs.launchpad.net/unity/+bug/1065652)

I guess turning off the shopping lens in privacy would do it.

---

### Post by mc4man on 2012-10-12
I'd think it's there for good. I guess if the icon itself bothers you, -  you could make it (the icon) disappear. (the link would still be there, unseen
```
sudo mv /usr/share/unity/6/information_icon.svg /usr/share/unity/6/information_icon.svg.bak
```

---

### Post by wojox on 2012-10-12
> **philinux said:**
> [https://bugs.launchpad.net/unity/+bug/1065652](https://bugs.launchpad.net/unity/+bug/1065652)
I guess turning off the shopping lens in privacy would do it.
Thanks for the link phil. 

> **mc4man said:**
> I'd think it's there for good. I guess if the icon itself bothers you, -  you could make it (the icon) disappear. (the link would still be there, unseen
```
sudo mv /usr/share/unity/6/information_icon.svg /usr/share/unity/6/information_icon.svg.bak
```
Thanks mc4man that did it.

---

### Post by mc4man on 2012-10-12
To note - 
any update to unity would require doing the mv again 
(& maybe rm the current .bak 1st.

---

