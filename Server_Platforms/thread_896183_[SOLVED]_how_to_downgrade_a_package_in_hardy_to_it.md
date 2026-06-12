---
title: "[SOLVED] how to downgrade a package in hardy to it's gutsy or feisty version"
date: 2008-08-20
forum: Server Platforms
---

### Post by nandix on 2008-08-20
Hello, 

While migrating a LAMP project to ADODB, introducing some MySQL stored procedures, I came across what I think is [[COLOR="Navy"]**this**[/COLOR]]("http://bugs.php.net/bug.php?id=42548") bug. 

I'm not 100% sure, but the same app works perfectly on a feisty machine, which has version 5.2.1 for package php-mysql, while my development machine (hardy) has version 5.2.4, and if you read the bug description, it was introduced in 5.2.4. 

I've added the gutsy repositories to my development machine, done apt-get update and them tried to force the gutsy version for php5-mysql from synaptic, since it's version 5.2.3, but once I force that version, the apply button is grayed out. 

I don't have much experience administering Ubuntu, I came to it after 8 years of Red Hat & Friends usage and I've been falling in love with it, but due to my workload, I've only gained experience as an end user, so any help with this issue is greatly appreciated. I'd love to solve this from within the package manager, since I'm sure an update will be available sometime in the future (The link I've included says the bug is already fixed in CVS). 

Thanks in advance for any help. 

Fernando.

---

### Post by Sef on 2008-08-20
Moved to Server Platforms.

> (The link I've included says the bug is already fixed in CVS).


Is there any reason that you don't want to download from CVS?

---

### Post by nandix on 2008-08-21
> **Sef said:**
> Moved to Server Platforms.



Is there any reason that you don't want to download from CVS?

My main concern is that Ubuntu is a package based distribution, and I'm trying not to manually change software that's included in the repositories. 

I don't have a problem with compiling code, in fact, that's part of what I do for a living :), but I really wouldn't want to apply a fix and then have a global upgrade bring me back to a broken version. That's why I thought installing an older version through apt-get/synaptic was the way to go. 

I had to do this with wine, the last version has a bug that prevents printers from working in some situations, and since I need to test sites in Internet Explorer and use the Print to File feature, I just downgraded it,  and have been leaving it unmarked at every update since, until a new (and hopefully fixed) version comes along. 

Of course, if there's no way to install the gutsy or feisty version in hardy, I'll have to go with your option. 

Thanks for your reply!

Fernando.

---

### Post by koenn on 2008-08-21
The mechanism you're looking for is called apt-pinning.
Forcing apt to do a downgrade is hard, it may be easier to uninstall the current version, and then pin and install the older version so that it's not upgraded until you want it to be. 

Here's a howto: 
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html)
the relevant parts are 3.8 and 3.10, but you'll want to read the whole chapter for background.

It's a Debian howto, but technically it would work just the same on Ubuntu.
But as Ubuntu is designed to resolve dependencies within a release, not across releases, there's no guarantee this will work.

Have fun.

---

### Post by nandix on 2008-08-21
> **koenn said:**
> The mechanism you're looking for is called apt-pinning.
Forcing apt to do a downgrade is hard, it may be easier to uninstall the current version, and then pin and install the older version so that it's not upgraded until you want it to be. 

Here's a howto: 
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html)
the relevant parts are 3.8 and 3.10, but you'll want to read the whole chapter for background.

It's a Debian howto, but technically it would work just the same on Ubuntu.
But as Ubuntu is designed to resolve dependencies within a release, not across releases, there's no guarantee this will work.

Have fun.

Thank you very much!
I'm giving this a try right now, so you'll know if it works just the same in Ubuntu :)

Regards

---

### Post by nandix on 2008-08-21
> **koenn said:**
> 

It's a Debian howto, but technically it would work just the same on Ubuntu.
But as Ubuntu is designed to resolve dependencies within a release, not across releases, there's no guarantee this will work.

Have fun.

It works, all I had to do was create an /etc/apt/apt.conf file
with the proper APT::default-release="release"; entry (hardy for me), 
add the additional repository(ies) to my sources, and begin forcing versions. 

The only issue is that apt-get didn't resolve the dependencies while downgrading, so I had to manually downgrade every involved package, but it still worked so I'm really happy with it. 

Thanks again!

---

### Post by koenn on 2008-08-21
glad to hear you got it working

---

