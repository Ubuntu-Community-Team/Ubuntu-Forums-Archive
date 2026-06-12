---
title: "XAMPP or stand alone installation"
date: 2008-09-27
forum: Server Platforms
---

### Post by tatewaki on 2008-09-27
Hey i'm planing on setting up a web server, but i'm not sure on what would be the best way of doing this. I will run a normal webserver (apache) with MySQL and PHP. Also i will set up a FTP server.
I like to have SSL support for apache and the FTP.

Now my question is, should i install all the packages from the repo or should i just get XAMPP? I have done both things in the past but i'm just not sure on witch option is the best?

---

### Post by Iowan on 2008-09-27
No experience w/ XAMPP, but saw a thread that claimed  it put things in nonstandard places - making updates difficult .  I've done a couple of LAMP installs that were pretty painless. I've never tried a package-type installation.  LAMP-server comess without GUI.

---

### Post by Dr Small on 2008-09-27
In my experience, some things were missing from the repositories, so I went with XAMPP, and I haven't ever regretted it. Everything resides in /opt/lampp and no where else on the system.

It comes with Apache, MySQL, PhpMyAdmin, ProFTP, SSL support, Php, gd2 support and it is easy to update if you ever need to. I use it on my server, and my friend nathangrubb also uses it on his system for a localhost. I find it works smooth, has everything already configured, and is easy to use.

Dr Small

---

### Post by tatewaki on 2008-09-27
Okay thanks, my main concern was that it would be hard to update the services when/if i needed too. But i can hear that it should be easy so i think i will be going with XAMPP.

Oh and Iowan XAMPP is just LAMP and WAMP put together.

---

### Post by Dr Small on 2008-09-27
Yes. Upgrading should be simple. When XAMPP comes out with a new version (which is basically an update of the different software), you can backup /opt/lampp/htdocs and the different settings directories, and you should be good to go. They may even have a special 'upgrade' tarball that excludes the settings directories, so the only things get updated are the binaries.

Dr Small

---

### Post by lykwydchykyn on 2008-09-27
Not that you can't use whatever you wish, but personally I've never cared for the idea of using XAMPP.  Setting up a basic LAMP server on Ubuntu is not that hard (apt-get about six or seven packages, configure MySQL password... and that's it, really.  Am I missing anything?), and you probably learn a bit about the system in the process (which is not a bad idea overall, especially if you're potentially going to set up servers exposed to the internet).

Once it's installed, it gets updated through your normal apt upgrades, there are no tarballs to mess with.  Plus, tools like phpmyadmin and webmin will work out of the box with no additional setup.   

That's just my 2 cents in favor of normal LAMP; it always seemed to me like XAMPP is a small savings of time/effort in the initial setup, but more trouble in the long run.

---

### Post by Dr Small on 2008-09-27
> **lykwydchykyn said:**
> Not that you can't use whatever you wish, but personally I've never cared for the idea of using XAMPP.  Setting up a basic LAMP server on Ubuntu is not that hard (apt-get about six or seven packages, configure MySQL password... and that's it, really.  Am I missing anything?), and you probably learn a bit about the system in the process (which is not a bad idea overall, especially if you're potentially going to set up servers exposed to the internet).

Once it's installed, it gets updated through your normal apt upgrades, there are no tarballs to mess with.  Plus, tools like phpmyadmin and webmin will work out of the box with no additional setup.   

That's just my 2 cents in favor of normal LAMP; it always seemed to me like XAMPP is a small savings of time/effort in the initial setup, but more trouble in the long run.
Speaking from experience, I have had no issues with XAMPP in the long run, for almost 2 years.

---

### Post by cariboo on 2008-09-27
I also have a problem with using software that isn't in the repositories. At least when there is an update you don't have back everything up and then install a comepletely new version, If you install third party software, you either have to be on their mailing list, or keep looking to see if there is an update. With lamp if there is an update it gets included in your regualr updates without you having to go look for it.

I've been using lamp for 3-4 years and never had a problem installing it.

Jim

---

