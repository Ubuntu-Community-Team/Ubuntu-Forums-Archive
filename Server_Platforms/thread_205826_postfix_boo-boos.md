---
title: "postfix boo-boos"
date: 2006-06-29
forum: Server Platforms
---

### Post by samuelkarush on 2006-06-29
I edited the main.cf posftix file and got myself into trouble. Postfix will not work, and when I try to resintall postfix, mailx, and mysqlserver I get this error:

E: postfix: subprocess post-installation script returned error exit status 1
E: mailx: dependency problems - leaving unconfigured
E: mysql-server: dependency problems - leaving unconfigured

this is an error I get in terminal window with synaptic package manager, and also when trying to restart postfix manually.

config variable inet_interfaces: host not found: all

Is there a way to get out of this?

thanks,
sam

---

### Post by samuelkarush on 2006-06-29
well, for some reason uninstalling postfix, mialx, and mysql thru terminal instead of synaptic package manager worked. Here's the command for beginners like me:

 sudo apt-get remove --purge postfix

Here's a question for someone more experienced:

 I'm running a discussion forum, and postfix is required for the email activation. I'm also experimenting with setting up a mail server on the same machine, via the excellent how-to's found in this forum.
 I don't want people to not recieve the confirmation emails while I am working on this. What can i do to make this as seamless as possible? Is anyone else running a similar setup?

thanks,
sam

---

