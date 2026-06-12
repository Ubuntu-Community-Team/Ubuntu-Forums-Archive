---
title: "PHP 5.2.* on 6.06"
date: 2008-11-10
forum: Server Platforms
---

### Post by robinc on 2008-11-10
Hello all,

I have a new hired dedicated server running Ubuntu 6.06 it has come with PHP 5.1.2. 

I would like to install PHP 5.2+, I tried

**sudo apt-get install php5**

```

Reading package lists... Done
Building dependency tree... Done
php5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 49 not upgraded.

```
So assume 5.1.2 is the newest version in the 6.06 repository. 

Is there any way to upgrade to 5.2 via aptitude?

Could I build from source using the instructions on the php site without messing up php?

Thanks all in advance! :)

---

### Post by cdenley on 2008-11-10
If you really want PHP 5.2, why not use Ubuntu 8.04? You should stick with the repos, especially if you want a stable server. If you need the latest version software, why are you using an ubuntu release 29 months old?

---

### Post by CP1256 on 2008-11-10
Use [DotDeb]("http://www.dotdeb.org") or add repos from newer Ubuntu releases. 
I use Intrepid repos in my Hardy server. 

> deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted universe multiverse

Use this if you want Intrepid repos.

---

### Post by robinc on 2008-11-10
> **cdenley said:**
> If you really want PHP 5.2, why not use Ubuntu 8.04? You should stick with the repos, especially if you want a stable server. If you need the latest version software, why are you using an ubuntu release 29 months old?

As I explained I'm using a rented server.

[http://www.fasthosts.co.uk/dedicatedservers/](http://www.fasthosts.co.uk/dedicatedservers/)

If you want to take issue please contact their customer-service I'm sure they will give you an explanation if you really need one.

I need PHP 5.2 because it offers features that aren't offered in 5.1. Where as the operating system version in its self on the server is not such an issue unless I can not run PHP 5.2.

---

### Post by cdenley on 2008-11-10
> **robinc said:**
> As I explained I'm using a rented server.

[http://www.fasthosts.co.uk/dedicatedservers/](http://www.fasthosts.co.uk/dedicatedservers/)

If you want to take issue please contact their customer-service I'm sure they will give you an explanation if you really need one.

I need PHP 5.2 because it offers features that aren't offered in 5.1. Where as the operating system version in its self on the server is not such an issue unless I can not run PHP 5.2.

Well, if you aren't allowed to upgrade to a newer version of ubuntu, but are allowed to upgrade php, you can follow CP1256's suggestion. However, I wouldn't recommend it. If you want to use php 5.2, you should run an ubuntu release it has been tested to work with (if stability is important).

---

### Post by robinc on 2008-11-10
Yeah it seems like a bit of a dodgy way to do thing.

Would building from source be a bad idea?

---

### Post by cdenley on 2008-11-10
> **robinc said:**
> Yeah it seems like a bit of a dodgy way to do thing.

Would building from source be a bad idea?

The problem you're going to have with building from source from php's website is it will probably try to install to different locations resulting in two different versions being installed. It may overwrite some or all of the php packages if they are installed. You won't be able to remove the source-installed version from apt. If you have problems, people will be reluctant to help since you will no longer be running pure ubuntu.

---

### Post by robinc on 2008-11-10
ok I see. If I wanted to update Ubuntu to the newest version via the terminal how would I do that? and if say my connection was lost half way through (as I'd be accessing through SSH) would that mess up the server?

---

### Post by cdenley on 2008-11-10
> **robinc said:**
> ok I see. If I wanted to update Ubuntu to the newest version via the terminal how would I do that? and if say my connection was lost half way through (as I'd be accessing through SSH) would that mess up the server?

[https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)

I think your ssh session will continue after the ssh service is upgraded and restarted. You might want to test this on a local computer first, though.

---

