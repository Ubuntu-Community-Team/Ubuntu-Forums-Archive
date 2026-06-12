---
title: "Ubuntu 12.10 Samba Issue"
date: 2012-10-04
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by TheMixtureMedia on 2012-10-04
Hi there I am not 100% sure were to put this but my samba stopped working. When I tried to put a share directory it comes up with this issue "net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. The connection was refused. Maybe smbd is not running". Can someone give me a hand with this issue.

---

### Post by Morbius1 on 2012-10-04
You will in fact get this error is samba is not running:
> 'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. The connection was refused. Maybe smbd is not running.Did you try starting smbd?
```
sudo service smbd start
```

---

### Post by TheMixtureMedia on 2012-10-04
Thank you for getting back to me it did not work. I also tried stopping samba and starting it back and it came up with the same error.

---

### Post by TheMixtureMedia on 2012-10-04
Anyone?

---

### Post by Morbius1 on 2012-10-05
Go into your /etc/samba/smb.conf file and place a "#" sign in front of these 2 lines so that it looks like this:
> [COLOR=Blue]**#**[/COLOR]interfaces = 10.3.3.2/8, eth0
[COLOR=Blue]**#**[/COLOR]bind interfaces only = YesThen restart smbd and try to create the share again.

If that doesn't do it stop your firewall:
```
sudo ufw disable
```

---

### Post by Bucky Ball on 2012-10-05
*Thread moved to **Ubuntu +1***

---

