---
title: "LAMP server FTP login problem"
date: 2010-06-13
forum: Server Platforms
---

### Post by gewitty on 2010-06-13
I have a feeling I'm going to end up wearing a pointy hat and standing in the corner for this, but I've just installed Ubuntu 10.04 server, along with LAMP server option.

Everything went OK and the server is running. If I access it via a browser, I get the, 'It Works!" default page.

What I want to do now is upload a Joomla installation via FTP, but find that I can't get access as no user name and password combination I've tried is accepted and I just get "ECONNREFUSED - Connection refused by server".

What have I missed?

---

### Post by dapperdanny77 on 2010-06-13
hi,

the LAMP tasksel template don't include a ftp server.

check if you have a ftp server like proftpd installed.
if not 

apt-get install proftpd (or similar)

the standard install authenticates against OS users.

---

### Post by Ryan Dwyer on 2010-06-13
Connection refused usually means the service isn't running on the server or the port isn't forwarded. It's not getting to the point of asking for the username and password so whatever you put there won't work.

Check that your FTP service is running on the server, and if you're accessing it from outside the network check that port 21 is forwarded.

EDIT: Never mind, I opened this thread in a new tab about 30 minutes ago and didn't see the second post. The second post is correct - you need to install an FTP service.

---

### Post by gewitty on 2010-06-13
Great! Problem solved. Thanks for the help.

---

