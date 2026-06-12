---
title: "How to upgrade wordpress after apt-get install?"
date: 2008-07-10
forum: Server Platforms
---

### Post by helzer on 2008-07-10
Hi,

I installed wordpress using apt-get install.
This got me wordpress 2.3.3.

What would be the correct 'debianish' way to upgrade to the recent wordpress from wordpress.org? (e.g. download the tar.gz file and run over some directories).

My concern is that apt-get will detect any changes I do in the installed package and would later make a big salad out of it when doing 'apt-get upgrade'.

Thanks,
Helzer

---

### Post by jdavis on 2008-07-10
If I were you I would uninstall the wordpress package and just grab the tar.gz package from wordpress.org. The package is probably good for people who don't want to tinker too much, and just want their blog to be kept up to date through the repo's.

I'm not sure what problems the apt-get update might cause if you manually updated in future, but as you said, it could get very messy. IE: if you're on 2.3.3 and update the files manually today to 2.5.1, then the ubuntu repo's later updates to 2.4 (OK, I know 2.4 doesn't exist, but you get my drift).

I also find that installing manually is a lot more flexible as you get to choose where it's installed and it would make running multiple instances (if you wanted to do that in the future) much easier!

---

### Post by highonv8splash on 2008-07-10
```

become root
apt-get update
apt-get upgrade wordpress

```

---

### Post by jdavis on 2008-07-10
> **highonv8splash said:**
> ```

become root
apt-get update
apt-get upgrade wordpress

```

That would work if version 2.5.1 was available in the repositories, but since hardy's [wordpress package]("http://packages.ubuntu.com/hardy/wordpress") is only at 2.3.3 this would not update it.

Jonathan

---

### Post by highonv8splash on 2008-07-10
> **jdavis said:**
> That would work if version 2.5.1 was available in the repositories, but since hardy's [wordpress package]("http://packages.ubuntu.com/hardy/wordpress") is only at 2.3.3 this would not update it.

Jonathan

it's still the correct 'debianish' way to do, like he asked. :) I'm sure it won't be too long before the new version hits the repositories, they're usually really good about keeping things up to date on them.

---

### Post by jdavis on 2008-07-10
> **highonv8splash said:**
> it's still the correct 'debianish' way to do, like he asked. :) 

Very true, that would definately be the correct and quicker method, and also slightly more secure since the config file is stored in '/etc/wordpress' and other slight modifications made.

But with it being a Universe package it may take time for this, and there's no guarantees about when it'll be out. Also, as I mentioned earlier running multiple instances might be tricky using the 'wordpress' package, and there's no 'wordpressmu' package that I know of.

I've done a quick google and the only link I can find which relates to this is from last month:
[https://answers.launchpad.net/ubuntu/+source/wordpress/+question/35786](https://answers.launchpad.net/ubuntu/+source/wordpress/+question/35786) 

So it's a personal choice really, I just prefer the manual method as it gives me the latest features straight away.

Jonathan

---

### Post by helzer on 2008-07-10
Thanks for answering so quickly.

What I did was to manually install wordpress from tar in a different directory. It uses the same database tables as the debian install so the blog is fine.

I changed the apache config file to point at it. Now, I'll see. If the repository updates to the recent version I can switch back, otherwise, the older debian package is going to sit there doing nothing.

Helzer

---

### Post by jdavis on 2008-07-15
> **helzer said:**
> 
What I did was to manually install wordpress from tar in a different directory. It uses the same database tables as the debian install so the blog is fine.


This sounds OK, although I would perhaps make a copy of the database created by the 'apt-get install' and use that instead, as it's possible that a future repository upgrade could break the database if significant changes are made.

---

### Post by sciurus on 2008-07-20
One possibility would be to overwrite the package's files with the archive from wordpress.org and then pin the package so that it is never updated.

E.G. in /etc/apt/preferences

> 
Package: wordpress
Pin: version 2.3.1-1
Pin-Priority: 1000


if 2.3.1-1 is the version of wordpress you installed through apt.

---

