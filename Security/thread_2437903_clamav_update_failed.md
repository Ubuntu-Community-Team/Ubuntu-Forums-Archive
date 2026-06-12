---
title: "clamav update failed"
date: 2020-03-03
forum: Security
---

### Post by ipv on 2020-03-03
since the last 1 month clam av is not getting updated.

clamtk reports antivirus signatures outdated.

sudo freshclam starts the update which is about 56 mb but the update fails at around 17-18 mb.

this is with a fresh install of both 18.04.4 & 19.10.

tried various repositories but to no avail.

```
clamscan -V
```

gives me this : **ClamAV 0.102.2**

please have a look here :

[ATTACH=CONFIG]285167[/ATTACH]

& here :

[ATTACH=CONFIG]285168[/ATTACH][URL="https://postimg.cc/D83BSkqs"]
[/URL]

---

### Post by webaake on 2020-03-03
A bit down on this page, there's some tips about freshclam:
[https://www.clamav.net/documents/clamav-virus-database-faq](https://www.clamav.net/documents/clamav-virus-database-faq)

My Freshclam updates have been working fine.

---

### Post by EuclideanCoffee on 2020-03-03
Freshclam works in my environment. Appears to be a network issue on your side.

---

### Post by SeijiSensei on 2020-03-03
Check /etc/freshclam.conf and make sure it has a line like this:
```
DatabaseMirror db.local.clamav.net
```

I responded to a post here a couple of weeks back where someone reported having troubles with freshclam, and he had a different DatabaseMirror entry. I know this works because my ClamAV installation updates every day.

I believe db.local.clamav.net points to a Cloudflare instance that routes to the proper server depending on where you're located.  The server that freshclam reports using 
```
Database updated (6768029 signatures) from db.local.clamav.net (IP: 104.16.218.84)
```
is in Cloudflare's range of IP addresses (see "whois 104.16.0.0").

---

### Post by ipv on 2020-03-04
> **EuclideanCoffee said:**
> Freshclam works in my environment. Appears to be a network issue on your side.

on the same machine with the same internet connection with debian buster clamav has absolutely no issues.

this problem has surfaced on ubuntu since a month & is also prevalent on neon which is an ubuntu derivative. 

> **SeijiSensei said:**
> Check /etc/freshclam.conf and make sure it has a line like this:
```
DatabaseMirror db.local.clamav.net
```


here is what i did :

```
sudo nano /etc/freshclam.conf
```

it was empty not even a single letter / word in it. so i pasted what you wrote, saved & exited. here is what it looks like now :

[ATTACH=CONFIG]285174[/ATTACH]

---

### Post by SeijiSensei on 2020-03-04
freshclam.conf should definitely not be empty, so maybe it's in a different location on your system.  Use "locate freshclam.conf" to find it.

(My servers run CentOS, not Ubuntu, so Ubuntu may store the freshclam.conf in a different location.)

It's always good practice to examine any configuration files for new software you are using.

---

### Post by deadflowr on 2020-03-04
freshclam.conf should be in the /etc/clamav directory.
Or at least that's were is was last time I ran clam.

---

### Post by ipv on 2020-03-04
> **SeijiSensei said:**
> freshclam.conf should definitely not be empty, so maybe it's in a different location on your system.  Use "locate freshclam.conf" to find it.

(My servers run CentOS, not Ubuntu, so Ubuntu may store the freshclam.conf in a different location.)

It's always good practice to examine any configuration files for new software you are using.

> **deadflowr said:**
> freshclam.conf should be in the /etc/clamav directory.
Or at least that's were is was last time I ran clam.

```
sudo nano /etc/clamav/freshclam.conf
```

gives me this :

[ATTACH=CONFIG]285175[/ATTACH]

does it require any corrections?

---

### Post by ipv on 2020-03-08
bug reported on launchpad ubuntu. bug acknowledged. work in progress.

---

### Post by uRock on 2020-03-08
> **ipv said:**
> sudo nano /etc/clamav/freshclam.conf gives me this :

[https://postimg.cc/GHtX3nNZ](https://postimg.cc/GHtX3nNZ)

does it require any corrections?

Why make people go to intrusive sites when you can post images here?

---

### Post by ipv on 2020-03-09
> **uRock said:**
> Why make people go to intrusive sites when you can post images here?

i could not figure out the attachments thingy.

have rectified all my posts.

---

### Post by ipv on 2020-03-22
bug fix released.

---

