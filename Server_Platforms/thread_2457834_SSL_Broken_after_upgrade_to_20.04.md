---
title: "SSL Broken after upgrade to 20.04"
date: 2021-02-10
forum: Server Platforms
---

### Post by astarmathsandphysics on 2021-02-10
I upgraded to from 19.04 to 20.04 at xmas, and that broke sll for all  my websites.
I changed no setiings in apache2 or sll, saved the config files etc, spent more than a month trouble sghooting but no joy.
Am usncloudflare, and have reinstalled apache2, php7.4, openssll again,, going through to rewrite config giles with riginal settings, whiich worked for years.
Any ideas?

---

### Post by astarmathsandphysics on 2021-02-10
Tries to post terminal output but code not accepted.

---

### Post by astarmathsandphysics on 2021-02-15
After a lot of PFAFFING AROUND everything working after amending /etc/hosts to read like this

127.0.0.1	localhost
127.0.1.1	server-1.astarmathsandphysics.com server-1
192.168.0.10

#Virtual Hosts
127.0.0.1:443 astarmathsandphysics.com
127.0.0.1:443 courseworkbank.info
127.0.0.1:443 theeducationchannel.info
127.0.0.1:443 theeducationdirectory.org
127.0.0.1:443  tutoragency.org

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

---

