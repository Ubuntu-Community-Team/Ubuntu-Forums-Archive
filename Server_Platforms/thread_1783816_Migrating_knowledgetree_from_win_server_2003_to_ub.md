---
title: "Migrating knowledgetree from win server 2003 to ubu server 64bit 10.04"
date: 2011-06-16
forum: Server Platforms
---

### Post by baz.g on 2011-06-16
Hi guys, I have managed to move the documents to what I believe is the correct directory (/var/lib/knowledgetree-ce/Documents) and imported the SQL dump using phpmyadmin successfully.

I then tried to get to the kt login page but had an error which I managed to translate to the fact that certain logs were still trying to be found in c:\program files\... Etc. So I ran the change directory scripts from [http://www.knowledgetree.org/Migrating_KnowledgeTree_from_Windows_to_Linux](http://www.knowledgetree.org/Migrating_KnowledgeTree_from_Windows_to_Linux) 
and I put these directories which I am not sure if they are correct or not:

Document root: /var/lib/knowledgetree-ce/Documents
Var directory: /usr/share/knowledgetree-ce/var
Log directory: /usr/share/knowledgetree-ce/var/log

Then restarted all the kt services using dmsctl.sh. Now when I try to login all I get is a blank page for [http://localhost/knowledgetree/login.php](http://localhost/knowledgetree/login.php)

Please help :-)

---

### Post by baz.g on 2011-06-16
Please can anybody help?

---

