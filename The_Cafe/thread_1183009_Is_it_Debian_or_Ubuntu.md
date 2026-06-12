---
title: "Is it Debian or Ubuntu"
date: 2009-06-09
forum: The Cafe
---

### Post by Tews on 2009-06-09
I recently installed Linux/Mint and  while it feels like Buntu, its being identified as Debian/Lenny/Sid.  So what is it??

---

### Post by collinp on 2009-06-09
Linux Mint. Mint is based off Ubuntu, and Ubuntu is based off Debian, but each distro is its own.

---

### Post by chris200x9 on 2009-06-09
it's neither it's based off ubuntu which is based off of debian

---

### Post by Screwdriver0815 on 2009-06-09
How do you identify it as Debian?

Mint is based on Ubuntu and Ubuntu is based on Debian. Thats why both (Mint and Ubuntu) have the same or similar basic structure as Debian.

---

### Post by Tews on 2009-06-09
> **Screwdriver0815 said:**
> How do you identify it as Debian?

Mint is based on Ubuntu and Ubuntu is based on Debian. Thats why both (Mint and Ubuntu) have the same or similar basic structure as Debian.

Look at the screenlet on the right .. it shows the distro as Debian ...

---

### Post by Twitch6000 on 2009-06-09
> **Tews said:**
> Look at the screenlet on the right .. it shows the distro as Debian ...

Did you get the debain community edition?

I know there was one last I checked.

---

### Post by Screwdriver0815 on 2009-06-09
> **Tews said:**
> Look at the screenlet on the right .. it shows the distro as Debian ...
thats strange because when I start this screenlet on Ubuntu, it says "Ubuntu" - I assume it is the one from the screenlets app?

---

### Post by mikewhatever on 2009-06-09
Interesting. What's the output of cat /etc/lsb-release?

I swear it used to say Mint was Debian based on their site, can't find it now.

---

### Post by koenn on 2009-06-09
> 
#  It is a Debian-based distribution and as such it is very solid and it comes with one of the greatest package managers.
# It is compatible with and uses Ubuntu repositories. This gives Linux Mint users access to a huge collection of packages and software.
[http://www.linuxmint.com/about.php](http://www.linuxmint.com/about.php)

---

### Post by Tews on 2009-06-09
> **mikewhatever said:**
> Interesting. What's the output of cat /etc/lsb-release?

I swear it used to say Mint was Debian based on their site, can't find it now.

```
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=6
DISTRIB_CODENAME=felicia
DISTRIB_DESCRIPTION="Linux Mint 6 Felicia - Main Edition"

```

---

### Post by Yashiro on 2009-06-09
*cat /etc/lsb-release*
should return mint strings

*cat /etc/debian_version*
will return lenny/sid

---

### Post by mikewhatever on 2009-06-09
I wonder if there is /etc/ubuntu_version.

---

### Post by Yashiro on 2009-06-09
That's what lsb-release is for.

---

### Post by Tews on 2009-06-09
> **Yashiro said:**
> *cat /etc/lsb-release*
should return mint strings

*cat /etc/debian_version*
will return lenny/sid

Yep ... it returns lenny/sid

---

