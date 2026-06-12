---
title: "Set up a webserver.....trying to connect to it"
date: 2009-01-27
forum: Server Platforms
---

### Post by Maheriano on 2009-01-27
I set up 32 bit Ubuntu 8.1 server edition on a Pentium 3 machine that's about 8 years old but it works! Now I can use Connect To Server under the Places menu on my main Ubuntu box to connect to it no problems but that only gives me a file listing. How do I connect to it so I can install applications on it like Webmin and other things? I guess the Terminal is what I'm after?

---

### Post by cariboo on 2009-01-27
Install openssh-server on your server, you can then use ssh to access your server.Ssh is installed by default in the desktop version. If you are accessing the server from Windows you need to install Putty, it is a free download.

To access your server, using the default setup in a terminal type:

```
ssh <user>@<server>
```

Jim

---

