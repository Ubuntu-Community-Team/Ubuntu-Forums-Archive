---
title: "Hive on Ubuntu Server 9.04"
date: 2009-06-05
forum: Server Platforms
---

### Post by jfmanamtr on 2009-06-05
I was wondering around the help section & stumbled across  the guide for installing hive ([https://help.ubuntu.com/community/Hive](https://help.ubuntu.com/community/Hive)). When I get to the part about installing the addition components using the following command:

```
sudo apt-get install apache2 mysql-server php5 php5-gd php5-mysql id3v2 imagemagick libgd2-dev libgd2 php-auth
```it tells me that it can't find an install candidate for libgd2-dev libgd2. I am kinda confused & would love to have this running on my PC. Any ideas?

~John

---

### Post by smileypaul on 2009-06-05
Ensure you have the proper repositories available and updated.

Those could have also been superceeded (sp?) by something a bit newer.

---

### Post by jfmanamtr on 2009-06-05
Ok. Sorry to sound stupid, but how do I check that? I know that I should check in sources.list. I just don't know where the packages libgd2-dev & libgd2 would be pulled from.

~John

---

### Post by cdenley on 2009-06-05
libgd2 has been forked into two packages, libgd2-xpm and libgd2-noxpm. They are the same thing, except one has xpm support and the other doesn't. There is no transitional package called libgd2-dev. There is libgd2-noxpm-dev and libgd2-xpm-dev. That guide must be outdated.

---

### Post by jfmanamtr on 2009-06-05
It would look that way. I am going to try installing those 4 packages & see if it will play nice. I will post again if I need any help. Thanks y'all!

~John

---

### Post by cdenley on 2009-06-05
> **jfmanamtr said:**
> It would look that way. I am going to try installing those 4 packages & see if it will play nice. I will post again if I need any help. Thanks y'all!

~John

You can't have libgd2 with xpm AND without xpm. You must choose one or the other. I'm not sure which would be most appropriate for hive.

---

### Post by jfmanamtr on 2009-06-05
Oh. Well, I guess I could try it with both & see if either works. I guess it didn't dawn on me that they both couldn't coexist. I will let you know how it goes.

~John

---

### Post by jfmanamtr on 2009-06-05
Ok. So I have tried it with both & dpkg still tells me that it can't install because the dependency on libgd2-dev failed. That happens if I use either package. So it looks like it will not let me install it. Any ideas on how to fix this?

~John

---

### Post by jfmanamtr on 2009-06-06
So, no ideas?

~John

---

### Post by cdenley on 2009-06-07
> **jfmanamtr said:**
> Ok. So I have tried it with both & dpkg still tells me that it can't install because the dependency on libgd2-dev failed. That happens if I use either package. So it looks like it will not let me install it. Any ideas on how to fix this?

~John

What package depends on libgd2-dev? As I already said, that package no longer exists. If a package depends on it, file a bug report for that package.

---

### Post by jfmanamtr on 2009-06-08
That happens when I try to install the package [FONT=monospace]using this line:

[/FONT]```
sudo dpkg -i ubuntucenter-alpha-01.deb
```

That is supposed to be Hive (formally Ubuntu Center). Ok. so I need to submit a bug report? How do I go about doing that (relatively new to all this, sorry)?

~John

---

### Post by cdenley on 2009-06-08
That package was created over 3 years ago. At the time, that dependency existed in the ubuntu repos. Since that package (ubuntucenter-alpha-01.deb) is not supported by ubuntu (not in the repos), you can't file a bug report with the ubuntu devs. You can file a bug report with the [Hive project]("https://hive.bountysource.com/"), but since the project appears to be dead, it probably won't do much good.

---

### Post by jfmanamtr on 2009-06-08
So, I guess that means that I should not worry about it & see if I can find something similar to Ubuntu Center. Oh well. Back to the drawing board!

~John

---

### Post by solitaire on 2009-06-21
> **jfmanamtr said:**
> So, I guess that means that I should not worry about it & see if I can find something similar to Ubuntu Center. Oh well. Back to the drawing board!

~John


Drat!

I just came across Hive today and it look very usefull! pitty it's dead! :(

---

### Post by carlosrve on 2009-06-26
> **jfmanamtr said:**
> So, I guess that means that I should not worry about it & see if I can find something similar to Ubuntu Center. Oh well. Back to the drawing board!

~John

Hi,

From the Ubuntu Community Documentation I read that:

> Hive is a Digital Life Management System which runs on apache, mysql and php. With it, you manage various aspects of your life using calendars and schedules. It also lets you access your media such as music, pictures and eventually videos from virtually any internet connected computer in the world.

Isn't that what a groupware with file server support is supposed to do? I didn't find any concrete feature list nor screenshots of Hive. But from that description I think it isn't that difficult to set a groupware (eGroupware, Horde, Kolab, ...) with a file server app (FTP maybe, or some html/ajax view) that does the trick pretty easily.

Hope that helps.

---

