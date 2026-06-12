---
title: "Backup Hardware"
date: 2007-12-10
forum: Server Platforms
---

### Post by CulleyS on 2007-12-10
Hey all,

I have two somewhat related questions.  I will have two identical servers soon.  Identical hardware specs, that is.  And am turning them into Ubuntu Servers.  I plan to use 7.10.  One will be production, one will be a test environment.

Here are my questions:

1. What backup hardware setup are folks using?  USB to External Harddrive?  Anybody using Firewire?  To Tape Drive?  For the current method you use, could you give reasons?  Currently, we use Firewire to External Harddrive, but have run into  problems in the past with other Linux distros playing nicely with Firewire.  Is anybody aware if Canonical has a recommended/ideal backup procedure written up somewhere?

2. Are there any "one-click" or "one-step" methods to sync all content between two servers?  So, say, once the test server shows a particular update/change is good to go, a "one-click" sync can duplicate the efforts in the production environment.

Thanks in advance for your help,

Culley

---

### Post by mustang357 on 2007-12-10
For point one, I use rsync and mysql-dump to backup the web application and mysql files to an offsite server.  I do this between daily and weekly depending on the critical nature of the server.

For your second point, rsync would fit the bill as well, assuming you tell it to sync all the files you changed in the staging environment.

Hope it helps.

---

