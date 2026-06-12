---
title: "What does feisty-updates contain?"
date: 2007-07-02
forum: Repositories &amp; Backports
---

### Post by ankursethi on 2007-07-02
What does the feisty-updates repository contain? I cannot access the official Ubuntu repos and therefore I rely on an FTP mirror located in a university (IIT Madras). Running apt-get update shows 404 errors for this repository. I tried the UK Mirror Service as well, and even then I get the same 404 errors for that repo.

What happens if I simply comment out the feisty-updates repository? There is no way I can access any of the official repositories, so please suggest some other mirror that has this repository.

---

### Post by bapoumba on 2007-07-02
All the security notices get published in UF:
[http://ubuntuforums.org/forumdisplay.php?f=13]("http://ubuntuforums.org/forumdisplay.php?f=13")
They are related to packages from the regular ubuntu repos.

To find a mirror (there are zillions of them) run a search with the keyword "mirror feisty-updates" in google ;)

---

### Post by ankursethi on 2007-07-03
Humph...

No official mirror is working for me, except jp.archive.ubuntu.com. I think that one will work for a few days, and then stop working. This isn't rational! WTF?

---

### Post by bapoumba on 2007-07-03
> **ankursethi said:**
> Humph...

No official mirror is working for me, except jp.archive.ubuntu.com. I think that one will work for a few days, and then stop working. This isn't rational! WTF?
May be your ISP?

---

### Post by ankursethi on 2007-07-05
Nah. It's not the ISP. They don't even block BitTorrent or other P2P's, why would they block Ubuntu's repos? Anyway, I confirmed it, twice, once from the customer care and once from a technical engineer. They do not block any ports or websites.

---

### Post by bapoumba on 2007-07-05
> **ankursethi said:**
> Nah. It's not the ISP. They don't even block BitTorrent or other P2P's, why would they block Ubuntu's repos? Anyway, I confirmed it, twice, once from the customer care and once from a technical engineer. They do not block any ports or websites.
Okay.
Anything on your end then? A proxy? Can you ping the repos?
I cannot currently show you the ping stats because my corporate proxy does not allow them. I'll post the stats later on.
```
~$ ping archive.ubuntu.com
PING archive.ubuntu.com (91.189.88.31) 56(84) bytes of data.

--- archive.ubuntu.com ping statistics ---
7 packets transmitted, 0 received, 100% packet loss, time 6009ms
```

Could you please post the complete output to:
```
sudo aptitude update
```

Edit: one more thing. Do you have any file in /etc/at/sources.list.d ? Should be empty.

---

### Post by ankursethi on 2007-07-06
Pinging archive.ubuntu.com is currently working. As I said, the repo sometimes works and sometimes doesn't.
```
PING archive.ubuntu.com (91.189.89.6) 56(84) bytes of data.
64 bytes from forster.canonical.com (91.189.89.6): icmp_seq=1 ttl=51 time=351 ms
64 bytes from forster.canonical.com (91.189.89.6): icmp_seq=2 ttl=51 time=348 ms
64 bytes from forster.canonical.com (91.189.89.6): icmp_seq=3 ttl=51 time=347 ms
64 bytes from forster.canonical.com (91.189.89.6): icmp_seq=4 ttl=51 time=347 ms
64 bytes from forster.canonical.com (91.189.89.6): icmp_seq=5 ttl=51 time=347 ms
64 bytes from forster.canonical.com (91.189.89.6): icmp_seq=6 ttl=51 time=348 ms
64 bytes from forster.canonical.com (91.189.89.6): icmp_seq=7 ttl=51 time=347 ms
64 bytes from forster.canonical.com (91.189.89.6): icmp_seq=8 ttl=51 time=348 ms

--- archive.ubuntu.com ping statistics ---
9 packets transmitted, 8 received, 11% packet loss, time 7998ms
rtt min/avg/max/mdev = 347.252/348.311/351.282/1.231 ms
```
The same output for in.archive.ubuntu.com.

Updating the packages will just show "Connectiog to in.archive.ubuntu.com [91.189.89.6]" for 5 minutes or so, and then it might eventually get connected if I'm lucky. Otherwise it times out and I get a "Some packages failed to download" error. The directory /etc/apt/sources.list.d is empty. No proxies, nothing.

BTW, currently I'm using the Japan mirror, ie, jp.archive.ubuntu.com, which is working beautifully and hasn't failed me even once uptil now. I assume it will work fine in the future, too. So my problem is solved. But I'd still like to know what it is that has been going wrong with the other 2 sites, if anybody can guess.

---

