---
title: "Ubuntu 8.1 server Mysql question (joomla)"
date: 2008-12-28
forum: Server Platforms
---

### Post by ericunicast on 2008-12-28
I am attempting to install joomla on Ubuntu server through this turtorial...

[https://help.ubuntu.com/community/Joomla](https://help.ubuntu.com/community/Joomla)

Everything else seemed to go ok besides having to change the socket that the mysql client was connecting to manually. (duh)

anyways, I get a syntax error on this. I attached a screenshot of the error I am getting along with the syntax I used.

Please help!!!!

Thanks in advance.

---

### Post by spiderbatdad on 2008-12-28
maybe edit command to ```
...to 'mail'@'%' identified by...
``` either that or mysql doesn't like one of your rules like Lock Tables...

---

### Post by ericunicast on 2008-12-28
Ok so I corrected the syntax near the CREATE TEMPORARY TABLES but now I am getting a syntax error on ''

see attached picture

---

### Post by spiderbatdad on 2008-12-28
it might be helpful to post the command you are using. Screenshots of errors are ok, but don't show the complete command you are issuing. Example:
Alter Create Temporary Tables are separate commands. Have you a comma between them?

---

### Post by joebeasley on 2008-12-28
...identified by 'somepassword';

You must use the ' ' around the password.

---

