---
title: "Xubuntu default network security"
date: 2010-12-24
forum: Security
---

### Post by chrisw71 on 2010-12-24
Can anyone comment as to how secure a default install of Xubuntu desktop 10.04 is when connected to the internet with a routable, public ip address. If anyone can give some recommendations on any changes/additions they would make to improve security I'd appreciate it.
 
Thanks

---

### Post by cariboo on 2010-12-24
It all depends on what services you are running. If you are running a default install, enabling ufw with the default rules should be enough.

---

### Post by bodhi.zazen on 2010-12-25
> **chrisw71 said:**
> Can anyone comment as to how secure a default install of Xubuntu desktop 10.04 is when connected to the internet with a routable, public ip address. If anyone can give some recommendations on any changes/additions they would make to improve security I'd appreciate it.
 
Thanks

1. ```
sudo ufw enable
```

2. Read the security sticky. Out of the box, Ubuntu (Xubuntu) is IMO rock solid.

3. Beyond the defaults the best thing you can do is to educate yourself.

---

