---
title: "Looking for an ownCloud alternative that actually works"
date: 2013-09-22
forum: The Cafe
---

### Post by semaphore45 on 2013-09-22
Hello there,

*first, I'm not sure if I should post that in "Server", but since it is not strictly related to Ubuntu-based solutions, I bet not.*

In my quest to cut my dependence on proprietary and/or insecure online services provider, I found ownCloud, that looked very promising as it respected the following basic requirements:
[LIST=1]
[*]No command line access required. That means, no package to be installed through apt-get or similar process. 
[*]No root access required 
[*]Has CalDAV, CardDAV and WebDAV functions 
[*]Based upon MySQL + PHP 
[*]server-side encryption of files, contacts, calendar, everything. 
[*]secure connection 
[*]Compatible with both iCal, Address Book, Thunderbird, Finder, Nautilus. In short, standards-compliant. 
[/LIST]

As you guessed, I wanted it to be hosted on a shared hosting, that shares its certificate across all accounts, obviously. Dedicated is not on my map at the moment because I don't want to take time to maintain it, and I excluded home-based servers out of reliability and speed concerns. I wanted it to be as transparent as possible.

However, I had many issues throughout the installation process as well as trying to operate it. Many debug processes require access to Apache logs (invalidating 2), especially getting a string of error 500 at various steps. Also, 5 never worked. CalDAV never worked neither.

So, I am now looking for solutions, even partial ones, that would allow me to host files and access them through WebDAV clients, sync'ed through a proper, native client (No Java here). Same for CalDAV and address book. And of course, a working server-side encryption. For example, SparkleShare, although having server-side encryption, cannot be installed.

What is your experience and advice here?

---

### Post by CharlesA on 2013-09-24
If you are on shared hosting (at least with Cpanel), you should have access the the error/access logs.

I really wouldn't run ownCloud on shared hosting, but it looks like it can be done, at least if you use GoDaddy: [http://simpleitnow.com/sites/km/?p=436](http://simpleitnow.com/sites/km/?p=436)

As far as getting 500 errors, that sounds like a problem with .htaccess. As far as the encryption goes, if you are using a shared SSL cert, you will probably get errors/warnings saying the site doesn't match the SSL cert. There is also an encryption plugin you can install from inside ownCloud, but I haven't tried it on a shared host.

Also note, if you are using shared hosting, most of the hosts I have used/looked into state you are only to store data related to your site and now to use the plan for the storage of data.

I've got ownCloud running on a Debian Wheezy VPS and haven't had any problems with it.

---

