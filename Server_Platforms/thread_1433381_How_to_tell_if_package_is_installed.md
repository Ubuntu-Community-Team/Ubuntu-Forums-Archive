---
title: "How to tell if package is installed?"
date: 2010-03-19
forum: Server Platforms
---

### Post by osx on 2010-03-19
What's the best way to tell if a package is already installed? I can't seem to find a way to do it with apt-get.

Thanks.

---

### Post by whoop on 2010-03-19
I have mutt installed. If I type: "sudo aptitude search mutt" it gives me (amongst other things):
```

i   mutt      - text-based mailreader supporting MIME, GPG, PGP and 

```
The "i" means it is installed...

---

### Post by startrekker on 2010-03-19
dpkg -l | grep packagename

---

### Post by osx on 2010-03-19
> **whoop said:**
> I have mutt installed. If I type: "sudo aptitude search mutt" it gives me (amongst other things):
```

i   mutt      - text-based mailreader supporting MIME, GPG, PGP and 

```
The "i" means it is installed...

Thanks, that's what I am looking for.

Thanks also, startrekker, your suggestion works well too.

---

### Post by dudumomo on 2010-03-19
I usually use apt.
apt-cache policy mypackage

---

### Post by osx on 2010-03-19
> **dudumomo said:**
> I usually use apt.
apt-cache policy mypackage

Thanks. I like the output of this one, too.

---

