---
title: "Linux-Anti-Theft"
date: 2009-04-27
forum: The Cafe
---

### Post by Scormen on 2009-04-27
Hi all,

I have made a "linux-anti-theft" system, users can register themself and their systems. Visit it at [www.linux-anti-theft.net]("http://www.linux-anti-theft.net")


**Linux-anti-theft in 4 steps**

   1. Register yourself and get your personal codes.
   2. Download and install the Linux anti-theft client.
   3. The client sends at each startup of your system the internal and external (unique for each internet user) IP address to your account. This happens even before a user is logged in.
   4. Is your system stolen? Consult your personal account and localise your system using the IP broadcast address. So you can follow your system, it doesn't matter where it is located.


> **Tour**
Hardware can be replaced, but your personal files may be priceless; both for self-employed persons, employees and home users. Today we increasingly hear about the theft of computer systems. The victim will report to the police, but there is only little chance that a stolen system is found and returned to the legal owner.

**What Linux-Anti-Theft.net does? **
In order to to improve the chances of return of your system after a theft, your system can be monitored. Each time when your laptop or desktop system starts up it will automatically send the internal and external IP adresses of the network it is connected to. These data send by your sytem will be collected in our database and can be consulted through your personal control panel. For local authorities this will be very helpful in tracing back your system.


If you would prefer to host it on your own webserver, you can download the script here: [http://www.linux-anti-theft.net/lat_self-en.tar.gz](http://www.linux-anti-theft.net/lat_self-en.tar.gz)
For that, you need a server running Apache, PHP and MySQL. This script has a extra functionality: you can upload a webcam picture by FTP.

---

### Post by jpeddicord on 2009-05-11
Moved to Cafe from Tutorials & Tips - please see the thread criteria: [http://ubuntuforums.org/showthread.php?t=677396](http://ubuntuforums.org/showthread.php?t=677396)

(And sorry for the long delay on action!)

---

### Post by monsterstack on 2009-05-11
> **Scormen said:**
> Hi all,

I have made a "linux-anti-theft" system, users can register themself and their systems. Visit it at [www.linux-anti-theft.net]("http://www.linux-anti-theft.net")


**Linux-anti-theft in 4 steps**

   1. Register yourself and get your personal codes.
   2. Download and install the Linux anti-theft client.
   3. The client sends at each startup of your system the internal and external (unique for each internet user) IP address to your account. This happens even before a user is logged in.
   4. Is your system stolen? Consult your personal account and localise your system using the IP broadcast address. So you can follow your system, it doesn't matter where it is located.

This sounds like something I could be interested in doing. My assumption is, though, that thieves will mostly like nuke the hard disk. Does this system of yours employ some sort of hardware-based detection stuff?

---

### Post by Scormen on 2009-05-11
Thanks for the move, jacobmp92. The delay is no problem.

monsterstack, there is no hardware-based detection. Only the hostname, external- and internal IP will be saved.

I have also a version what you can download and set up on your own webserver. If you have a webcam, you can also upload the images to your FTP server. The script is in dutch, I'll do my best to translate it asap into english. To use this script, you need a external webserver with Apache, PHP and MySQL.
You can download it [here](http://www.linuxontdekt.be/files/linux_anti_diefstal.tar.gz).

Edit: translation complete. Download the english version [here](http://www.linux-anti-theft.net/lat_self-en.tar.gz).

If you don't have a server, you can still use the webservice at [www.linux-anti-theft.net](www.linux-anti-theft.net)

---

### Post by fatality_uk on 2009-05-11
How can you narrow down a laptop say using an IP address?

Even if your laptop were left in an "open" state and the thief stole it, they might not be on a fixed IP and therefore that IP would change each time they switched on? Or am I missing something in your application? Might just me being a "thicko" again :lol:

---

### Post by monsterstack on 2009-05-11
> **Scormen said:**
> Thanks for the move, jacobmp92. The delay is no problem.

monsterstack, there is no hardware-based detection. Only the hostname, external- and internal IP will be saved.

I have also a version what you can download and set up on your own webserver. If you have a webcam, you can also upload the images to your FTP server. The script is in dutch, I'll do my best to translate it asap into english. To use this script, you need a external webserver with Apache, PHP and MySQL.
You can download it [here](http://www.linuxontdekt.be/files/linux_anti_diefstal.tar.gz).

If you don't have a server, you can still use the webservice at [www.linux-anti-theft.net](www.linux-anti-theft.net)

My lappy has SSH to my server, which has all the necessary Apache gubbins and what have you. My lappy doesn't have a webcam, though. Makes me rather want to get one now just in case it ever does get stolen. :)

---

### Post by Redache on 2009-05-11
> How can you narrow down a laptop say using an IP address?

Even if your laptop were left in an "open" state and the thief stole it, they might not be on a fixed IP and therefore that IP would change each time they switched on? Or am I missing something in your application? Might just me being a "thicko" again :lol:

I'm assuming that the Anti-Theft Software is in fact a Daemon that starts up and broadcasts the Unique ID assigned to the Laptop and then sends the IP Address it has been assigned after it connects to the net. Granted it's useless if it's been nicked by a thief with no internet. 

It's actually quite a good idea. The Thief would have to know explicitly that you have this Anti-Theft software installed.

---

### Post by Scormen on 2009-05-11
> **fatality_uk said:**
> Even if your laptop were left in an "open" state and the thief stole it, they might not be on a fixed IP and therefore that IP would change each time they switched on? Or am I missing something in your application? Might just me being a "thicko" again :lol:
No, good question :).
Like written in the FAQ, DHCP is required:
> Q. A thief doesn't know my systems username or password. How can he connect then=,
A. The connection to the network is made before you login. It is required that the system uses DHCP.
I know that this is a restriction, but necessary.

> **monsterstack said:**
> My lappy has SSH to my server, which has all the necessary Apache gubbins and what have you. My lappy doesn't have a webcam, though. Makes me rather want to get one now just in case it ever does get stolen. :)
The webcam should of course best be built in ;-)
A SSH connection is not necesarry.

> I'm assuming that the Anti-Theft Software is in fact a Daemon that starts up and broadcasts the Unique ID assigned to the Laptop and then sends the IP Address it has been assigned after it connects to the net. Granted it's useless if it's been nicked by a thief with no internet.
Indeed. The software is just started as a background proces and will try each 10 seconds again to connect to the internet.

---

### Post by monsterstack on 2009-05-11
> **Redache said:**
> I'm assuming that the Anti-Theft Software is in fact a Daemon that starts up and broadcasts the Unique ID assigned to the Laptop and then sends the IP Address it has been assigned after it connects to the net. Granted it's useless if it's been nicked by a thief with no internet. 

It's actually quite a good idea. The Thief would have to know explicitly that you have this Anti-Theft software installed.

And if you have SSH access to said laptop, you can go right ahead and have some fun with your thief.

---

### Post by Wiebelhaus on 2009-05-11
This is slick , thanks mate.

---

### Post by Scormen on 2009-05-11
> **monsterstack said:**
> And if you have SSH access to said laptop, you can go right ahead and have some fun with your thief.
Yes, if the thief was able to hack into your account.
If you like, you can also make a crontab which download e.g. every hour a shell script of your server and execute it. This script is just empty and will do nothing. If your system is stolen, you can rewrite the script on your server to take screenshots of your stolen desktop, or just delete your whole laptop... It's all to you :)

Here is a screenshot of the webinterface of the script if you host it on your own server, here shown together with the webcam upload function:
Again, I'll do my best to translate it as soon as possible into english.
[[img]http://www.linuxontdekt.be/wp-content/uploads/2009/03/schermafdruk-overzicht-van-de-systemen-mozilla-firefox-300x177.png[/img]](http://www.linuxontdekt.be/wp-content/uploads/2009/03/schermafdruk-overzicht-van-de-systemen-mozilla-firefox.png)

---

### Post by Scormen on 2009-05-12
Hi all,

Like promised, here is the english version of Linux-Anti-Theft to host on your own server.
See the README for all information to set it up.
Download: [http://www.linux-anti-theft.net/lat_self-en.tar.gz](http://www.linux-anti-theft.net/lat_self-en.tar.gz)

If you don't have a own server, everyone is still welcome at the webservice [www.linux-anti-theft.net](www.linux-anti-theft.net) which has the same functions, except uploading a webcam picture.

Kris

---

### Post by Redsandro on 2011-04-09
I've set up something similar for myself and since it's just a blushworthy ping at the moment, I was interested to take a look at this script. I know I am late to the party and everything is down, but I was wondering if someone still has a copy they can attach?

:KS

---

### Post by undecim on 2011-04-09
Necro'd thread is necro'd

If you need an anti-theft system, you need to make it hardware based. Software based security cannot stop a physical compromise.

---

### Post by Redsandro on 2011-04-09
> **undecim said:**
> If you need an anti-theft system, you need to make it hardware based.

You sound like a Filezilla programmer, denying a master password function contrary to popular demand:

*"If it´s not safer than Maria´s virginity, it´s useless."*

Ofcourse you´re wrong. Any slight hint of dial-home security is better than none at all. I´m just curious to improve my own ping.

I´m open for clever ideas, but nay-saying is synonymous for not saying anything at all.

Meanwhile, here´s a more advanced useless software solution:
_[Prey Project (Windows, OS X, Ubuntu)](http://preyproject.com/)_

And you should watch this:
_[YouTube: Never steal a hackers computer](http://youtu.be/U4oB28ksiIo#at=3m16s)_

:)

---

### Post by uRock on 2011-04-09
Necromancy. Start a new thread.

Thread Closed

---

