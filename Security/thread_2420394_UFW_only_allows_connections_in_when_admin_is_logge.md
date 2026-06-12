---
title: "UFW only allows connections in when admin is logged in"
date: 2019-06-04
forum: Security
---

### Post by noventium on 2019-06-04
Hello.


I have a fresh install of Ubuntu 18.04 on a computer that I have set up with 4 accounts, one of which being an admin account. When I set up ufw under the admin account with the following commands, everything works fine; the other three users are able to log in remotely to the computer. 


```
sudo ufw enable
sudo ufw allow to any port 22 to tcp from x.x.0.0/16 (I removed the first two numbers for privacy reasons)
sudo iptables-save
sudo ufw status numbered 

```

However, once I log out of the admin account, the other three accounts are no longer able to log in remotely via PuTTY (or otherwise) to the computer, until I sign back into the admin account. I would like it so that the other three users are still able to log in and access the computer even while the admin account is logged out. I appreciate any help that you can provide. Thank you.

---

