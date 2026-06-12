---
title: "Raid controller web GUI"
date: 2013-11-26
forum: Server Platforms
---

### Post by nerdtron on 2013-11-26
Hi all,
I have this raid controller card.
```
user@node150:~$ lspci | grep -i raid
04:00.0 RAID bus controller: LSI Logic / Symbios Logic MegaRAID SAS 2108 [Liberator] (rev 04)

```

Is there a program I can use to monitor the hard drives and raid configuration of the server it is installed to? I have seen the docs of LSI and there is a provided Megaraid Storage Manager which is a web gui tool. 
The installer is also provided by LSI but it only supports Red Hat, Fedora and OpenSuse distros.
Any other alternatives that will work in Ubuntu?

---

### Post by rubylaser on 2013-11-26
I usually use megacli.  Here are [some directions]("https://calomel.org/megacli_lsi_commands.html") for setting it up, and some nice supporting scripts.

---

