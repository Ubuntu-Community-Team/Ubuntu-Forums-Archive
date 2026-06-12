---
title: "Console Logon Loop"
date: 2009-02-05
forum: Server Platforms
---

### Post by arapozo on 2009-02-05
I'm testing CUPS and SAMBA to replace a windows server for file sharing and printing in a windows network. I'm using VMWare Server 2.0 in a linux host with a linux guest to do testing first. I installed ubuntu linux 8.10-server and checked the options for ssh, samba and printer server.

So i log on the server enter the CUPS page [http://localhost:631](http://localhost:631) and enable remote administration, then remotely i connect and add a printer and test the printing and it works prefectly. I do a package update and then restart the machine, when it comes back up without any errors on the console, i try to log on to CUPS remotelly and it doesn't let me, so I go to the console and try to log in and it doesn't let me. If i put the username and password correctly it just asks for it again, but if i try a wrong username and password it says login incorrect.

So basically the server is broken. Any ideas?

[SOLVED]
For those that could be curious this post helped me.
[http://ubuntuforums.org/showpost.php?p=6678740&postcount=24](http://ubuntuforums.org/showpost.php?p=6678740&postcount=24)
Basically renamed the file /var/lib/samba/secrets.tdb.

[NOT SOLVED]
After doing some testing I've found out that the culprit is CUPS, as soon as I removed a printer that was previously installed the server had the same issue.
I'm at a loss of what could be happening. Maybe cups web interface is causing this problem.

---

### Post by arapozo on 2009-02-06
Nobody has seen this problem?

---

