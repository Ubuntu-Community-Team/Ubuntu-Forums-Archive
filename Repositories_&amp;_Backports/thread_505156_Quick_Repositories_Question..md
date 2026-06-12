---
title: "Quick Repositories Question."
date: 2007-07-19
forum: Repositories &amp; Backports
---

### Post by VolvoPunch on 2007-07-19
I am using Xubuntu and i want to know how i can tie apt-get into the [http://packages.ubuntu.com/](http://packages.ubuntu.com/) site. Don't ever want to have to install software by visiting a site i just want to use apt-get because it keeps everything clean. How can i do this. :)

---

### Post by splintercellguy on 2007-07-20
apt-get should already come with all the Ubuntu repos. There's little reason for you to be installing prior or beta packages.

---

### Post by grishenko2000 on 2007-07-20
Try[ URL="http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories"]http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories[/URL]

---

### Post by Frak on 2007-07-20
Synaptic, does the same thing.

---

### Post by Wim Sturkenboom on 2007-07-20
> Synaptic, does the same thing.

And if you don't have X running ??

---

### Post by Frak on 2007-07-20
apt-get or aptitude
```
sudo apt-get update
sudo apt-get cache search <package to search for here>
```

---

### Post by VolvoPunch on 2007-07-20
I have updated my sources.list file and run apt-get update yet i still cannot download and install zabbix-server-mysql using apt-get install. Althrough i find the package on the Ubuntu package site. Is there a Debian source i can add to my list and pull packages from?

---

### Post by Frak on 2007-07-20
Have you enabled extra repo's

---

### Post by VolvoPunch on 2007-07-20
> **Frak said:**
> Have you enabled extra repo's

By extra repo's do you mean have i removed the # sign in front of all the addresses in the sources.list file. If so yes i have.

---

### Post by Frak on 2007-07-20
> **VolvoPunch said:**
> By extra repo's do you mean have i removed the # sign in front of all the addresses in the sources.list file. If so yes i have.
Go [here]("http://www.ubuntu-nl.org/source-o-matic/"). And replace your source.list with the one this creates.

---

### Post by VolvoPunch on 2007-07-20
> **Frak said:**
> Go [here]("http://www.ubuntu-nl.org/source-o-matic/"). And replace your source.list with the one this creates.

How come i did not know about this before? I will certainly give this a try when i get home.

---

### Post by VolvoPunch on 2007-07-21
That site worked! Thanks :guitar: Now the server is off and running!

---

