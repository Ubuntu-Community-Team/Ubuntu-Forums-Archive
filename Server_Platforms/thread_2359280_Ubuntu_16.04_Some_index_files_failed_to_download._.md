---
title: "Ubuntu 16.04: Some index files failed to download. They have been ignored, or old one"
date: 2017-04-22
forum: Server Platforms
---

### Post by tony19942171 on 2017-04-22
I am receiving this error after sudo apt-get update:
```
Err:1 [http://hk.archive.ubuntu.com/ubuntu](http://hk.archive.ubuntu.com/ubuntu) xenial InRelease
  Temporary failure resolving 'hk.archive.ubuntu.com'
Err:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
  Temporary failure resolving 'security.ubuntu.com'
Err:3 [http://hk.archive.ubuntu.com/ubuntu](http://hk.archive.ubuntu.com/ubuntu) xenial-updates InRelease
  Temporary failure resolving 'hk.archive.ubuntu.com'
Err:4 [http://hk.archive.ubuntu.com/ubuntu](http://hk.archive.ubuntu.com/ubuntu) xenial-backports InRelease
  Temporary failure resolving 'hk.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://hk.archive.ubuntu.com/ubuntu/dists/xenial/InRelease](http://hk.archive.ubuntu.com/ubuntu/dists/xenial/InRelease)  Temporary failure resolving 'hk.archive.ubuntu.com'
W: Failed to fetch [http://hk.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease](http://hk.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease)  Temporary failure resolving 'hk.archive.ubuntu.com'
W: Failed to fetch [http://hk.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease](http://hk.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease)  Temporary failure resolving 'hk.archive.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease](http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease)  Temporary failure resolving 'security.ubuntu.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.
```

Any help would be greatly appreciated:p

---

### Post by RobGoss on 2017-04-22
Hello and welcome, try changing your download source, go to Software & updates, click on the drop down menu and choose the best source for your location

---

### Post by tony19942171 on 2017-04-23
> **RobGoss said:**
> Hello and welcome, try changing your download source, go to Software & updates, click on the drop down menu and choose the best source for your location

Use Ubuntu Sources List Generator?

---

### Post by howefield on 2017-04-23
> **tony19942171 said:**
> Use Ubuntu Sources List Generator?

Load the "Software & Updates" application and from the Ubuntu Software tab > click on the  "Download from" drop down box and select "Main Server".

Then try the update again.

---

### Post by tony19942171 on 2017-04-23
> **howefield said:**
> Load the "Software & Updates" application and from the Ubuntu Software tab > click on the  "Download from" drop down box and select "Main Server".

Then try the update again.


Sorry. But I use command line for ubuntu server, do not have desktop mode.

---

### Post by howefield on 2017-04-23
> **tony19942171 said:**
> Sorry. But I use command line for ubuntu server, do not have desktop mode.

Cool, helpful of you to mention it.

Thread moved to the "*Server Platforms*" forum.

---

### Post by RobGoss on 2017-04-23
This might be of help to you, [https://askubuntu.com/questions/104695/how-do-i-change-mirrors-in-ubuntu-server-from-regional-to-main](https://askubuntu.com/questions/104695/how-do-i-change-mirrors-in-ubuntu-server-from-regional-to-main)

---

