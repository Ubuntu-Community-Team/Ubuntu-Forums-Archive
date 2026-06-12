---
title: "Install JRE in 10.10"
date: 2011-01-08
forum: Server Platforms
---

### Post by dz93 on 2011-01-08
I've tried every tutorial out there and cant install JRE on my VPS. Can someone please help me.

---

### Post by wojox on 2011-01-08
```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner";apt-get update -y;apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

No go?

---

### Post by dz93 on 2011-01-09
It worked. Will this also work under 10.04? Im installing minecraft but the hMod wont install on 10.10 however on a friends server (10.04) it installed fine. So will that code work for 10.04 ubuntu?

---

### Post by wojox on 2011-01-09
Actually that code is for 10.04 (Lucid).

Change it to maverick for 10.10.

---

### Post by dz93 on 2011-01-09
Okay sorry for all the changes. This will be final. I need help installing JRE on 9.04. I had to switch VPS providers because the one I had was just awful in support and reliability. So my new one only offers Ubuntu 9.04 64bit. Well it offers other versions but 9.04 is the latest on there. So once and for a all can someone provide me with the command to install JRE on 9.04? Thanks so much.

---

### Post by wojox on 2011-01-09
You had better switch providers again. Ubuntu 9.04 64bit is EOL and not supported anymore.

---

### Post by dz93 on 2011-01-09
What about 9.10?

---

### Post by wojox on 2011-01-09
> **dz93 said:**
> What about 9.10?

Sure

```
sudo add-apt-repository "deb http://archive.canonical.com/ karmic partner";apt-get update -y;apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

```

---

### Post by dz93 on 2011-01-09
Okay so I tried 9.10 using the command above and 10.04 using the very first command. However each time I get this.

sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner";apt-get update -y;apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
sudo: add-apt-repository: command not found
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg [198B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg [198B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release [57.2kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release [44.7kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release [38.5kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages [1383kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages [6193B]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages [5430kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages [425kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages [3267B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages [175kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages [119kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages [14B]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages [54.4kB]
Fetched 7736kB in 26s (291kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate

---

### Post by wojox on 2011-01-09
Okay then we need to edit sources.list manually.

```
sudo nano /etc/apt/sources.list
```

And add to the bottom:

For 9.10

```
deb http://archive.canonical.com/ karmic partner
```

For 10.04

```
deb http://archive.canonical.com/ lucid partner
```


If you not familiar with nano, Ctrl+O saves and Ctrl+X exits.

Now try:

```
sudo apt-get update; sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

Sorry I gave you commands for the Desktop version. :oops:

---

