---
title: "Setting up FTP for a single user"
date: 2010-12-12
forum: Server Platforms
---

### Post by mrwooster on 2010-12-12
I apologise for this being a bit of a noob question but there are so many different ways of setting up FTP out there that I have got a bit lost. 

I wish to set up an FTP server on my machine that will allow a single user to connect to a specified directory on the server. This is the one and only requirement.... (basically it is so I can access some of the files on my server via FTP rather than ssh). 

What would be the simplest and most secure way of doing this? (security as in making sure only 1 user can connect to a specific folder, not as in ssl)

Thanks

G.

---

### Post by CharlesA on 2010-12-12
Why not just use sftp? It's easier to set up a jail and is more secure then ftp, as it is encrypted.

---

### Post by mrwooster on 2010-12-12
Unfortunately I can't use sftp as the client I have to use does not support it

---

### Post by CharlesA on 2010-12-12
> **mrwooster said:**
> Unfortunately I can't use sftp as the client I have to use does not support it
What client are you using?

---

### Post by mrwooster on 2010-12-12
It's an FTP client for the iPad :D

---

### Post by CharlesA on 2010-12-12
> **mrwooster said:**
> It's an FTP client for the iPad :D
If that's the case, check here:
[https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html)

---

### Post by HermanAB on 2010-12-12
Howdy,

There is a simple trick to it:
1. Install vsftpd or proftp and don't make any changes to the setup.  Leave it at the defaults.
2. Now create a new user account and set the home directory to the one that user has to use for FTP.

That is it!

---

### Post by Vegan on 2010-12-12
I use vsftp but I fiddled with the settings to support a user account generally. This way friends can upload crap etc

---

### Post by mrwooster on 2010-12-12
Thanks for the help, looks like a fairly simple vsftp install should do it.

---

