---
title: "Antivius on server."
date: 2007-11-12
forum: Server Platforms
---

### Post by frodemt on 2007-11-12
Hi there!

I have a Ubuntu 6.10 server that rocks! But I see a problem if a user uploads a file that contains a virus. Not for the server, but for thouse who use windows as a client :(.

My question is therefore; Is it possible to install a antivirus-program on my server that scans new files (or at least scans the entire disk on schedule) on server?

It is a benefit if this antivirus manages itself and does auto-update.

---

### Post by p_quarles on 2007-11-12
```
sudo apt-get install clamav
```It's not automated, but you can take care of that yourself by making it a cronjob.

In any case, a lot of people here feel that viruses are not really the Linux user's responsibility. If Windows users are downloading random files and not scanninng them, they're going to get viruses *anyway*. Installing an AV scanner on your server isn't going to protect them. 

Basically, the main reason that *nix AV scanners exist at all is for e-mail servers. That's the one case where pre-filtering for viruses makes sense.

---

### Post by reckless2k2 on 2007-11-12
[https://help.ubuntu.com/community/ClamAV?highlight=%28clamav%29](https://help.ubuntu.com/community/ClamAV?highlight=%28clamav%29)

that'll do ya along with daemon setup and all. have fun. 

MARK IT SOLVED BABY..if anyone is keeping track...800...800...i need a life..or more cups.

---

