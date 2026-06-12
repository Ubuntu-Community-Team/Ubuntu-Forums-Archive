---
title: "Intstall updates on the Ubuntu server in the DMZ zone"
date: 2012-03-09
forum: Server Platforms
---

### Post by rajeshv on 2012-03-09
Hi All,
 
 
Server is in the DMZ zone and 443 is open to below IPaddress. still can not download updates to Ubuntu server.
 
**[COLOR=red]Error:[/COLOR]**
------------
~# apt-get update
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg) Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2) Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2) Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2) Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2) Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg) Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2) Could not resolve 'us.archive.ubuntu.com'
W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
 
 
 
**IPADDRESS List**
--------------------
[COLOR=black][FONT=Georgia][SIZE=3]91.189.88.45, [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Georgia][SIZE=3]91.189.88.46, [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Georgia][SIZE=3]91.189.92.176, 91.189.92.177, 91.189.92.179, 91.189.92.180, 91.189.92.181, 91.189.92.182, 91.189.92.183,[/SIZE][/FONT][/COLOR]
[SIZE=3][FONT=Georgia][COLOR=black]91.189.92.184, [/COLOR][/FONT][/SIZE]
[COLOR=black][FONT=Georgia][SIZE=3]91.189.88.31, [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Georgia]91.189.88.40[/FONT][/COLOR]

---

### Post by volkswagner on 2012-03-09
What do the following files look like?

/etc/network/interfaces
/etc/resolv.conf


When running host command are you able to resolve names?
```
host google.com
```

---

