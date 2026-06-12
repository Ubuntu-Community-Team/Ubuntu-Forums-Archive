---
title: "I can't access Webmin by hostname."
date: 2011-07-22
forum: Server Platforms
---

### Post by aroldgre on 2011-07-22
Hello Fellows,
I installed Ubuntu server 11.04 with no problem
Then I installed Webmin on it with no problem

I can only access Webmin by the IP address on my network
I can't access it using the hostname (ubuntuserver)

I am not that savvy in Ubuntu server
Can someone please tell me the areas that I can check to correct this problem?:confused:


Thank you so very much
aroldgre

---

### Post by BbUiDgZ on 2011-07-22
> **aroldgre said:**
> Hello Fellows,
I installed Ubuntu server 11.04 with no problem
Then I installed Webmin on it with no problem

I can only access Webmin by the IP address on my network
I can't access it using the hostname (ubuntuserver)

I am not that savvy in Ubuntu server
Can someone please tell me the areas that I can check to correct this problem?:confused:


Thank you so very much
aroldgre

add ubuntuserver to your host file "/etc/hosts" on your netbook

---

### Post by aroldgre on 2011-07-22
Hey BbUiDgZ

Hey man, your are a genius.

I took at my /etc/hosts

I saw
127.0.0.1 localhost
127.0.1.1 ubuntuserver

I changed the 127.0.1.1 to 127.0.0.1 for ubuntuserver

Then it works perfectly

Thank you very much
Aroldgre

---

