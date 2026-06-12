---
title: "domain login and home folder mount"
date: 2010-04-01
forum: Server Platforms
---

### Post by macpraveen on 2010-04-01
Hello
I have Ubuntu Server installed in one machine and ubuntu desktop in 3 more machines. What I would like to have is, authenticate the clients using a central user DB and also the home folder for a user should be available in any client machine in which he logs.

I see that openLDAP takes care of authenticating clients but what application to use to mount the user's home folder from the server to the client machine on logging.

Please help me out in this regard.

Thanks
Praveen

---

### Post by fang0654 on 2010-04-01
There are a couple of things you can do.  I used to have a little network that authenticated via OpenLDAP.  I had one server hosting all of the home directories over NFS.  Instead of worrying about mounting the various user's home directories at login time, I just mounted the entire /home directory at boot.

Another option is to check out libpam-mount, which would allow you to mount a folder at login.

---

### Post by macpraveen on 2010-04-01
This is what I exactly required. I will give it a try.

Thanks

---

