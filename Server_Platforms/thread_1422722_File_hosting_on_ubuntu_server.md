---
title: "File hosting on ubuntu server"
date: 2010-03-05
forum: Server Platforms
---

### Post by hotpancakes on 2010-03-05
Hi,

I have a remote VPS with 9.10 installed and would like to host some files on it. I'd like to be able to download the files from a browser using a login name and password. Could anyone tell me how I would go about doing this? Thanks!

---

### Post by Bachstelze on 2010-03-05
Most Web browsers today support FTP, so you could go with that. Apache with an authentication mechanism would also work, but might be a little trickier to configure if you want multiple users, for example.

---

### Post by HermanAB on 2010-03-06
Depends on how fancy you want to be.  The simplest way is to use Apache simple authentication (user name and password).  You could also install a ducument management system such as OpenDocMan.

---

