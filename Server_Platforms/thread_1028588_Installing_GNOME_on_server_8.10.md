---
title: "Installing GNOME on server 8.10"
date: 2009-01-02
forum: Server Platforms
---

### Post by PE1600SC on 2009-01-02
I have decided to set up a server using ubuntu 8.10. I am a complete novice with linux:confused::confused:, not getting on well with CLI. I notice from other post you can install GNOME using:

sudo apt-get install ubuntu-desktop 

I get the message - couldn't find package

help please

---

### Post by cdenley on 2009-01-02
Are you sure you typed it correctly? Have you disabled the main repository? Do you have an internet connection?
```

grep -v \# /etc/apt/sources.list

```
Did you try updating the package index?
```

sudo apt-get update

```

---

### Post by PE1600SC on 2009-01-07
Thanks, I have connected to the internet and know it works.

---

