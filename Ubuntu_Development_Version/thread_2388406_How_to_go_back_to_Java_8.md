---
title: "How to go back to Java 8?"
date: 2018-04-02
forum: Ubuntu Development Version
---

### Post by jorritTyb on 2018-04-02
Hi, since last update in bionic it seems that java 8 was upgraded to java 9. Problem is that many things are not yet java 9 compatible (more in particular Minecraft which I'm developing mods on). How can I switch back to java 8 or install java 8 alongside java 9?

Thanks

---

### Post by slickymaster on 2018-04-02
If you have both Java versions on your system just run```
sudo update-alternatives --config java
```and choose the one you want.

---

### Post by jorritTyb on 2018-04-02
Thanks! That seemed to have worked

---

