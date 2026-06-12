---
title: "Dell OMSA"
date: 2009-01-14
forum: Server Platforms
---

### Post by petersenmde on 2009-01-14
Hello,

I installed an update this morning for dellomsa from version 5.4 to version 5.5. Now I can't get the web browser version or the command line version to work. It appears that Ubuntu is too efficient and has already deleted version 5.4 from /var/cache/apt . I'm hoping somebody has the dellomsa_5.4.0-1_amd64.deb on their system that I could get a copy of, or instructions on how to download it from the sara.nl ftp site as I have tried without success.

Thanks

Mark

Dell PowerEdge 2900 Perc6/i
Ubuntu 8.04 amd64

---

### Post by aaron.d on 2009-01-14
> **petersenmde said:**
> Hello,

I installed an update this morning for dellomsa from version 5.4 to version 5.5. Now I can't get the web browser version or the command line version to work. It appears that Ubuntu is too efficient and has already deleted version 5.4 from /var/cache/apt . I'm hoping somebody has the dellomsa_5.4.0-1_amd64.deb on their system that I could get a copy of, or instructions on how to download it from the sara.nl ftp site as I have tried without success.

Thanks

Mark

Dell PowerEdge 2900 Perc6/i
Ubuntu 8.04 amd64

well ... 

wget [ftp://ftp.sara.nl/pub/sara-omsa/dists/dell/sara/binary-amd64/dellomsa_5.4.0-1_amd64.deb](ftp://ftp.sara.nl/pub/sara-omsa/dists/dell/sara/binary-amd64/dellomsa_5.4.0-1_amd64.deb)


but really, what kind of issues are you having? details?

---

### Post by petersenmde on 2009-01-14
When I run omreport storage controller from the command line I get;

No controllers found

When I log in using the web interface, I get web pages but no pertinent information.

I would add a screen shot but, I'm not sure how.

Thanks for the tip on downloading. I had brain fart and forgot to add the command wget?!

Mark

---

### Post by aaron.d on 2009-01-15
is it possible you are missing modules (they arent loaded)? Im not super knowlesged on OM but I believe it depends on mptctl/mptbase.

Did the rollback work? If not, can you supply the output of 

```
$/sbin/lsmod
```

---

### Post by petersenmde on 2009-01-15
I finally got back around to do some checking on this. Turns out that the dataeng had not been restarted after the update. /etc/init.d/dataeng restart did the trick.

It looks like I am going to have update the megaraid driver as I am running version .03.13 and the new omsa is listing .03.20 as the minimum.

Thanks for your assistance aaron.d

Mark

---

