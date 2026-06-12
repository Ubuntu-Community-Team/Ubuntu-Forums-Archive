---
title: "Ubuntu server apt-get issues"
date: 2009-11-12
forum: Server Platforms
---

### Post by deancasino on 2009-11-12
ok I got ubuntu server edition, but I cannot install anything as when I write the command sudo apt-get update, one of the items in the list gets stuck at 56%

how do I change the default update server?

Keep in mind I am using ubuntu server, so please no ubuntu desktop advice

---

### Post by phishie on 2009-11-12
> **deancasino said:**
> ok I got ubuntu server edition, but I cannot install anything as when I write the command sudo apt-get update, one of the items in the list gets stuck at 56%

how do I change the default update server?

Keep in mind I am using ubuntu server, so please no ubuntu desktop advice

Go under System -> Administration -> Software Sources

At 'Download from', choose **other**.

---

### Post by phishie on 2009-11-12
Whoops. Sorry. I didn't notice you got the server edition installed.

You will need to edit the sources.list (/etc/apt/sources.list) file and change all the urls to you desired url to get the update from. One easy way is to change all the country codes from say 'us' to 'uk'.

e.g. [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) -> [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/)

After changing the addresses, try apt-get update again.

Hope this helps =)

---

### Post by mudcow007 on 2009-11-12
i was having big isues trying to install the gui on my server
install until i changed my source.list from 
[http://gb.archive](http://gb.archive)...
to
[ftp://archive](ftp://archive)

it works much better now

---

### Post by wojox on 2009-11-12
Don't know how well you no your way around w3m but:

```
w3m -v http://repogen.simplylinux.ch/
```

You can edit a new sources list.

---

