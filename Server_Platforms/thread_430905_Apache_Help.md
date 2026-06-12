---
title: "Apache Help"
date: 2007-05-02
forum: Server Platforms
---

### Post by ecochran on 2007-05-02
I started with my company about five months ago.  It was one week after they had a contractor stand up a LAMP server.  I haven't had to do too much with it since it was put up.  Developers do the html and php coding over sftp and I just make sure that backups run.  Normally when you browse to the site you receive a simple search engine screen but today when I came in it was prompting for login credentials.  Everyone that works on it claims to have not touched it in serveral days and I can't seem to figure out what is going on.  Also since I am fairly green when it comes to linux I don't know where to start trouble shooting.  Can anyone point me in the right direction?

Also SSH is no logger working, telnet is now working and it didn't use to but it won't accept my credentials, and the sftp server is not working.

Could I have been hacked?

Thank you,

Ethan

---

### Post by vmikalinis on 2007-05-03
Take a look at some of the logs of the offending services, they may give you an idea as to what's happening.

logs are in:
/var/log

if there are any strange authentication errors, etc.

---

