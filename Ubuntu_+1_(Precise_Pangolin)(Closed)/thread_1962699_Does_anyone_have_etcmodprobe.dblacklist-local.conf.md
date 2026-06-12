---
title: "Does anyone have /etc/modprobe.d/blacklist-local.conf?"
date: 2012-04-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Yellow Pasque on 2012-04-21
I found this file on a test install of Kubuntu 12.04, and it only had one line, blacklisting fglrx module. I have no idea what created it, and I deleted the file (I should have run dpkg-query -S on it to see if it belonged to a package).

I'm thinking that jockey might have created it when removing the ATI proprietary driver, but I'm not sure. I'm wondering if anyone else has it?

---

### Post by bogan on 2012-04-21
Hi!, **temujin**.

Yes! my/etc/modprobe.d/ folder has  a "blacklist-local.conf" file, with just the one line in it, but mine says: "blacklist nvidia-current".

Like you I have no idea how it originated, but it is dated Wed 28 Dec 2011 so it is nothing to do with the current nvidia-current driver shambles.

Edit: 'dpkg-query -S' returns: ```
 sudo dpkg-query -S /etc/modprobe.d/blacklist-local.conf
dpkg-query: no path found matching pattern /etc/modprobe.d/blacklist-local.conf.
```
Chao!, **bogan**.

---

### Post by mc4man on 2012-04-21
It will be created when you remove a prop. driver   like nvidia-current, ect.

---

