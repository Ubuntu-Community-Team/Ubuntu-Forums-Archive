---
title: "DenyHosts"
date: 2009-09-08
forum: Server Platforms
---

### Post by Cardale on 2009-09-08
DenyHosts is continuously blocking my from logging in via ssh and sftp by placing my ip in the hosts.deny file even though I read the faq at DenyHosts regarding the issue it said to add a file allow_hosts file and place that ip in the file.  I placed the ip in there and it is still doing it.  I have already placed this ip in the hosts.allow file as well.  How do I remedy?

---

### Post by im_an_elf on 2009-10-29
I have the same problem with Jaunty.  They had some info on how to stop this from occurring on the denyhosts.sourceforge.net.  The problem is that they suggest going to the WORK_DIR which I couldn't find.  There seems to be specifics in regards to Ubuntu that aren't covered in their FAQ.

My work around is that I run the daemon and allow the program to scan the ip addresses in the log and place them in the /etc/host.deny file.  Then I turn off the daemon.  At least the ip addresses that are flagged are blocked for now.

---

