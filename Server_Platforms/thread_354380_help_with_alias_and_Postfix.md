---
title: "help with alias and Postfix"
date: 2007-02-05
forum: Server Platforms
---

### Post by bspratt on 2007-02-05
Just setup Postfix and Courier on Edgy. Can someone point me to a doc or give me the steps to create an alias?  Instead of my first initial and last name I also would like my nickname along with my wife's first name to be recognized and go to the inbox. The accounts in Edgy are setup with their MAIDIR folders. Also have Webmin - but the alias feature doesn't seem to work.  Any documents or steps to do this? Thanks, Bill

---

### Post by mwerlberger on 2007-02-07
aliases are done within the file /etc/aliases

nick: receiver
bla: receiver
sepp: receiver2


to tell postfix that new aliases are there call newaliases at the shell.

rgds,
 Manuel

---

