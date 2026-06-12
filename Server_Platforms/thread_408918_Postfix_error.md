---
title: "Postfix error"
date: 2007-04-13
forum: Server Platforms
---

### Post by bsharp on 2007-04-13
hey everyone, I'm hosting a website out of my house and I'm trying to install postfix so the PHP mail() function can use that instead of sendmail (went down that road and I felt like killing my dogs...). When I try to install it, ubuntu asks for the server cd, I put it in, and it proceeds with the installation. I go through the basic config towards the end of the install, and then it stops and gives me this error:

E: postfix: subprocess post-installation script returned error exit status 1

When I try to configure it later, it tells me that the postfix installation is corrupt (or something to that effect). I'm wondering if my cd is corrupt and if there is a way to tell it to download from the repository instead of the cd.

Thanks

---

### Post by bmathis on 2007-04-14
im pretty sure you can purge the failed install of postfix by doing a ```
sudo aptitude purge postfix
``` Next, if you havent done so already, I would edit **/etc/apt/sources.list** and comment out the CD (first 2 entries i think) and uncomment the rest of the repositories, this will give you the latest package for whatever version of Ubuntu you are using. For the final step, just do a```
sudo aptitude update && sudo aptitude install postfix
```

Remember not to setup your email server as an open relay... thats a no no!

---

### Post by bsharp on 2007-04-14
ahh ty very much, got it installed and it seems to be working.:D

---

### Post by bmathis on 2007-04-14
Great to hear... have a good one!

---

