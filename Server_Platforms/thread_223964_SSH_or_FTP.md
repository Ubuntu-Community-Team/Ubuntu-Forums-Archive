---
title: "SSH or FTP?"
date: 2006-07-27
forum: Server Platforms
---

### Post by Tadhg on 2006-07-27
Excuse me if im getting things a bit confused but I'll try anyway.

I'm setting up webserver and i want to be able to control it remotely as it'l  be stuffed away in a closet. I also want to be able to upload files to the home folder so i can change the webpage on the go, and hopefully be able to upload files in general and use it as a little file store.So initially i was just going to set up an FTP server, but it seems a little smarter to use an SSH server. 

So what are the advantages/disadvantages of using SSH (again, if this is completely wrong tell me!). Which is safer, and generally better for a webserver.

---

### Post by MJN on 2006-07-27
SSH is far more secure and dead simple to set up - indeed it works securely, and well, straight out of the box.
 
It's also a damn site easier if you've any firewalls and/or NATs in the way too. (For FTP, google active and passive connections for an insight to the problems they cause)
 
Mathew

---

