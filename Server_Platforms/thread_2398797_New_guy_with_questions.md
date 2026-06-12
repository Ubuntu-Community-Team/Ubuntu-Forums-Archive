---
title: "New guy with questions"
date: 2018-08-17
forum: Server Platforms
---

### Post by pujo3 on 2018-08-17
Morning gang,
I was injured in an accident recently and this have given me a lot of time to learn something new!
I don't need to be spoon fed as I can read however, I just need to be put on the right path here.

I have several working older PC's and figured I would do something with one of them while I have time.
My goal here is to have either Ubuntu Desktop or Ubuntu Server running the unit as a web server with WordPress and the associated applications.
The PC I want to use has the following specs. Intel Core 2 Due 64 bit processor, 8 GB Ram, 1TB hard drive. 

After doing some google searching, I think I may need a LAMP image or the Server image however I am just not sure which way to go.
So, if someone wants to point me in the right direction, I would appreciate the assistance!

Also, as the new guy, I hope I didn't post this in the wrong forum..

Cheers!
PuJo

---

### Post by QIII on 2018-08-17
Moved to Server Platforms.  The people who are more expert in servers will likely spot you here.

Use the server version for that.  A desktop runs a lot of services not needed for such a machine -- and more surfaces means more attack vectors.

Is this for serving in a home network or do you plan to expose it to the web?

I personally mistrust WordPress.  People seem to constantly find security holes.  My reports from my web servers indicate a lot of attempts to attack WordPress vulnerabilities.  Fortunately, I don't use WordPress.

---

### Post by pujo3 on 2018-08-17
The entire idea is for educational purposes only however I will have it exposed to the world wide web...
Thanks for the reply. I have just started the install of Ubuntu Server 18.04

---

### Post by QIII on 2018-08-17
If you are using it for educational purposes, I recommend that you stick to your internal network for now.  

Exposure to the web can lead to a significant and instantaneous increase in the cost of your education!  Somewhat like Poker lessons in the smoky back room of a pub.

---

### Post by LHammonds on 2018-08-17
For learning, you could just run everything on your PC if you have enough RAM.  You could use virtualbox to install a Ubuntu Server 18.04 LTS instance, create a snapshot, and then learn how to install MariaDB.  Once done playing with it, revert the snapshot and you have a clean OS before installing MariaDB.  Then you can try out apache, etc.

Doing your initial installs to get familiar with it in a Virtual Machine can save you a lot of time.

In my sig, you can find my web site that has several in-depth tutorials on installing Ubuntu and various applications.  I am still working on the 18.04 versions though.  Currently working on WordPress documentation.

LHammonds

---

### Post by pujo3 on 2018-08-17
So I should install Ubuntu 18.04 Desktop instead of Server?

---

### Post by SeijiSensei on 2018-08-17
Install Server 18.04.  I believe all the LAMP pieces are there already, but if not, you can add them with
```
sudo apt install lamp-server^
```

I use WordPress for a few sites; other apps I write natively in PHP.  It's possible to run WP sites pretty securely if you don't permit the webserver to write into the WP directories.  I wrote little scripts that I run before a WP update that enables write-permissions so the update (or other process like installing an add-on) can take place and disable them when it is complete.  

Pre-update
```

#!/bin/sh
chmod g+w wp-admin wp-includes wp-content -R
chmod g+w *
echo "Run update now"

```

Post-update
```

#!/bin/sh
chmod g-w wp-admin wp-includes wp-content -R
chmod g-w *

```

Both of these are designed to be run from the top of wordpress directory.  All my sites have group "www-data" so giving that group write permissions lets the server update the files.
 
I also apply updates pretty quickly after they are released.  I don't use any fancy plugins or the like, which also limits my exposure.

---

### Post by pujo3 on 2018-08-17
> **SeijiSensei said:**
> Install Server 18.04.  I believe all the LAMP pieces are there already, but if not, you can add them with
```
sudo apt install lamp-server^
```

I use WordPress for a few sites; other apps I write natively in PHP.  It's possible to run WP sites pretty securely if you don't permit the webserver to write into the WP directories.  I wrote little scripts that I run before a WP update that enables write-permissions so the update (or other process like installing an add-on) can take place and disable them when it is complete.  

Pre-update
```

#!/bin/sh
chmod g+w wp-admin wp-includes wp-content -R
chmod g+w *
echo "Run update now"

```

Post-update
```

#!/bin/sh
chmod g-w wp-admin wp-includes wp-content -R
chmod g-w *

```

Both of these are designed to be run from the top of wordpress directory.  All my sites have group "www-data" so giving that group write permissions lets the server update the files.
 
I also apply updates pretty quickly after they are released.  I don't use any fancy plugins or the like, which also limits my exposure.

I appreciate the info and the scripts. I may try to use them if I can get WP installed.

Doest this line also install WP?
```
sudo apt install lamp-server^
```

I ran into some trouble following a tutorial on installing Ubuntu Server 18.04 & WP. I abandoned it and installed Ubuntu Desktop.
I will be trying again to get the server OS installed with WP. 

If you have any tips/tricks for installing lamp-server & WP I would appreciate it.

---

### Post by LHammonds on 2018-08-18
> **pujo3 said:**
> So I should install Ubuntu 18.04 Desktop instead of Server?
That's not what I was saying.  I assume you already have a working desktop on a good PC (not one of those old clunkers).

My point was to learn how to install Ubuntu Server inside a VM on a PC you are comfortable working with already.

I do not use Ubuntu desktop on any of my servers for security reasons...that and I have no need for the GUI when everything can be done via the terminal.

But there is nothing wrong either with installing directly to the target machines.  Things just go a bit faster (when learning) if you use a fast PC...in combination with doing snapshots in a VM that you can quickly revert back to.

LHammonds

---

### Post by SeijiSensei on 2018-08-18
No, installing lamp-server won't install WordPress.  While Ubuntu maintains a version of WordPress, I just download the ZIP file from [https://wordpress.org/latest.zip](https://wordpress.org/latest.zip) and expand it into the directory where I want the site to be housed.

For starters you can unzip it into the folder /var/www/html which is the default website location in Ubuntu.  You'll need to use sudo for this.

---

### Post by pujo3 on 2018-08-18
LHammonds & Seiji

Thanks guys, I value the info you provide.
I will get back on the project on Monday. Having some pain management issues today. 

I do plan on trying to reinstall the server version and play with it, I read so many different tutorials, I think confused myself.
Can you guys recommend and good literature to read before attempting the install again?

FWIW: I am a 46 yr old control engineer (PLC programmer), I understand ladder and script logic however, I don't know jack about this....lol

---

### Post by LHammonds on 2018-08-19
Tutorial I have created:

[How to install Ubuntu Server 18.04 LTS]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=244") - This is not a "throw a server quickly together" tutorial.  It is how I setup a production-level server that will run for many years.
[How to install MariaDB on Ubuntu Server 18.04 LTS]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=245") - I would recommend setting up one of those machines to be a dedicated database server. Although, you could install on the web server.
[How to install WordPress on Ubuntu Server 18.04 LTS]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=249") - This is still a work-in-progress but the basic steps are there.  I am adjusting it to include a "developer" site with relaxed permissions and a "production" version with tighter security.

Most of my other 16.04 tutorials will be updated to 18.04 as I migrate my servers.

LHammonds

---

### Post by pujo3 on 2018-08-19
Awesome and thanks!

---

