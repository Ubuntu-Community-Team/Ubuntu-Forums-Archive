---
title: "SSHFS Client for windows"
date: 2011-09-09
forum: Server Platforms
---

### Post by DanHorniblow on 2011-09-09
Hi, I am running a Ubuntu server at home and I connect to it from my colleges debian machines to access my files.

But sometimes I have to use the colleges Windows machines :( anyone know of a way to connect to sshfs in windows?

---

### Post by Entilza on 2011-09-09
You can just SFTP to it?

---

### Post by DanHorniblow on 2011-09-09
Cheers for your reply Entilza.

Yea I can do that as filezilla is installed on all the windows machines, but when im in debian I can mount a directory on my server to the client something like "/home/user/homeStorage/".

I can then easily work from that directory.

Im looking for a possible method to map my server sshfs to a maped drive in windows so I can work directly off the server.

Can it be done?

---

### Post by Entilza on 2011-09-09
Some googling showed a project called Dokan that may work?  I tried to install it but I think it needs to install his libraries as well and didn't go further.

[http://dokan-dev.net/en/download/](http://dokan-dev.net/en/download/)

---

