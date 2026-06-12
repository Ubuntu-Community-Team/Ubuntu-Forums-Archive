---
title: "Just got VPS cant seem to apt-get update"
date: 2015-10-28
forum: Server Platforms
---

### Post by adept-james on 2015-10-28
Hello i just got a vps it is ubuntu 14.04 and i was about to install lamp stack and the first thing on the list of instructions is apt-get update. 

I get this error 

```

Err http://archive.ubuntu.com trusty InRelease
Err http://archive.canonical.com trusty Release.gpg
  Temporary failure resolving 'archive.canonical.com'
Err http://security.ubuntu.com trusty-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err http://archive.ubuntu.com trusty-updates InRelease
Err http://archive.ubuntu.com trusty Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Err http://archive.ubuntu.com trusty-updates Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty/InRelease
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/InRelease
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/trusty/InRelease
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/trusty/Release.gpg  Temporary failure resolving 'archive.canonical.com'
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg  Temporary failure resolving 'security.ubuntu.com'
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg  Temporary failure resolving 'archive.ubuntu.com'
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg  Temporary failure resolving 'archive.ubuntu.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.
root@server123:~#
```

I'm a bit perplexed but i supposed to have this server up and running and put a site on there pronto for work and i look like a scrub nub right now and so dont know where  else to turn. Many thanks for your patience and time. All suggestions/flames welcome. James

---

### Post by darkod on 2015-10-28
Doesn't look like you have dns working. Have you tried to see if any domain resolving works?
ping yahoo.com
nslookup google.com

Could they have provided the vps with "wrong" network settings?

---

### Post by slickymaster on 2015-10-28
Hi adept-james, welcome to the forums.

I've moved your thread to the **Server Platforms** sub-forum, which is the proper venue for it.

As for your issue, I think you're facing a DNS problem. Try to add a new line to your **/etc/resolv.conf** file, with the value **nameserver 8.8.8.8** (it's a Google Name Server). In a terminal window, run the following commands```
sudo -i gedit /etc/resolv.conf
```You'll be asked for your password, enter it and the file will be open in your text editor. Add the new line```
nameserver 8.8.8.8
```save and close the file. Then, try again to install the LAMP stack.

---

### Post by adept-james on 2015-10-28
URMAGURDDD no gedit installed. I've submitted a ticket to hosts thanks for the quick response i really appreciate it. I'm going to try with nano that comes pre-installed if im not mistaken.

---

### Post by darkod on 2015-10-28
The server version would not have gedit installed by default, that's normal. No gui on server. Use nano instead.

---

### Post by slickymaster on 2015-10-28
> **adept-james said:**
> URMAGURDDD no gedit installed. I've submitted a ticket to hosts thanks for the quick response i really appreciate it. I'm going to try with nano that comes pre-installed if im not mistaken.

> **darkod said:**
> The server version would not have gedit installed by default, that's normal. No gui on server. Use nano instead.
My bad, of course the server version doesn't have it. That's a force of habit, mentioning gedit that is.

---

