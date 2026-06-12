---
title: "DNS guidance. advance"
date: 2008-04-17
forum: Server Platforms
---

### Post by adamos on 2008-04-17
Its been a week that I am trying to setup a bind9 dns server with no result.. We are currently depending on a university dns server and we want to go independent. I saw a couple of tutorials but they are for intranets or they lack something.

i know how to install and run bind.. i know how they work but i cant get it working. i will update tomorrow with errors when i will dig it because i scratched the whole thing.

the plan is. 2 ubuntu 7.1 servers. one as primary and one as slave dns servers.

a third server will be a web server and a fourth server as a mail server.

lets say my domain is [www.mydomain.com](www.mydomain.com) from networksolutions.com

what would be the ideal configuration in named.conf and the rest of the conf files. any help it would be greatly appreciated.

Thanks.

---

### Post by greenstar on 2008-04-17
> **adamos said:**
> the plan is. 2 ubuntu 7.1 servers. one as primary and one as slave dns servers.

a third server will be a web server and a fourth server as a mail server.

I don't know the answer, either. If you don't mind, I'm pulling up a chair to learn along with you.

:popcorn:Got my popcorn, paper and pencil. Ready!

Greenstar

---

### Post by Iowan on 2008-04-17
Anything [here]("http://ubuntuforums.org/showthread.php?t=236093") of value?

---

### Post by adamos on 2008-04-18
did that before.. its very basic and its not what i want

---

### Post by hyper_ch on 2008-04-18
in the config files you have to enable zone transfer from primary to secondary server and does each server have a different public IP address? If so, make *.domain.com point to your webserver and mail.domain.com to your mailserver (or whatever you want to use for mail...)

---

