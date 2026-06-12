---
title: "Can't remove apt-get installed packages... That and I cant re-install them either!"
date: 2006-08-29
forum: Server Platforms
---

### Post by JD_2020 on 2006-08-29
Hi -

I am running Ubuntu v6.06.1 LTS (x64 Server edition). My problem is simple, but the solution appears to be non-existent. I installed Apache2 on my server using

```
apt-get install apache2
```

It installed it, but something went wrong and I couldn't get PHP to work properly. So I figured I would re-install Apache2.

So I used

```
apt-get remove apache2
```

which said was removing Apache2 - it even told me how much disk space I would clear. But it didn't remove it. The /etc/apache2/ directory still existed.

So I manually deleted the /etc/apache2/ directory and then tried to install apache2 again. It said that it installed successfully, but it did not re-create the /etc/apache2/ directory, so obviously nothing was working...

So my question is, how do I get it to re-install Apache2? It looks like it thinks I still have Apache2 installed, so it doesn't actually re-download the files again.

I tried using the --purge flag and that didn't do the trick.

If you haven't noticed, I am VERY new to linux and was told Ubuntu would be the easiest to start with. I just don't know what the problem is here. Even my friends who are Gentoo buffs said they didn't know, and told me to post on forums (which is what I am doing now!).

I just need to know how to install Apache2 again. Once I can get that part, I will post for a guide to help me actually configure my Apache2 server :P.

Thanks!
-Josh

---

### Post by mlind on 2006-08-29
apt-get/aptitude remove will leave "configuration" files behind, that's why /etc/apache2 was not removed. It's useful if you decide to reinstall package, you'll keep the same configuration files.
If you want to remove configuration files as well, use --purge flag with apt-get or aptitude purge *package*.

If you want to fully reinstall apache2
```

sudo aptitude purge apache2
sudo aptitude install apache2

```
(or use apt-get --purge)

---

### Post by chrisfay on 2006-08-29
I think he already tried that:

> I tried using the --purge flag and that didn't do the trick.

What syntax did you use when using --purge?

```
sudo apt-get --purge remove apache2
```

or something else?

When reinstalling, try Mlind's suggestion of using aptitude instead of apt-get.

Here's the difference.
[http://yalb.net/wp/?p=77](http://yalb.net/wp/?p=77)

---

### Post by gertmul on 2006-08-29
try 
apt-get remove apache2-common
and 
apt-get install apache2-common

---

### Post by mlind on 2006-08-29
> **gertmul said:**
> try 
apt-get remove apache2-common
and 
apt-get install apache2-common

Yeah, you're right. apache2 is just a meta package purging apache-common should do it.

---

