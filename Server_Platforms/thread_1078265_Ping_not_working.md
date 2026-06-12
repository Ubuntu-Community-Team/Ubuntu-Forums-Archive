---
title: "Ping not working"
date: 2009-02-23
forum: Server Platforms
---

### Post by happyhacker on 2009-02-23
I use Webmin and under Command Shell I type in any of our PCs IP addresses and it just hangs with no result. If I type in "ls" the same happens. I do not have a terminal connected and only manage the server from a networked laptop.

Can anyone advise?

---

### Post by sahabcse on 2009-02-23
Are you able to ping loopback address???

---

### Post by beno1990 on 2009-02-23
Unfortunately, Webmin's command shell doesn't like commands which produce a streaming output. It basically waits on the output stream to complete and produce a new prompt, and doesn't output the stream to the network until it recieves the new prompt, meaning it looks like it's hung, when it's actually just waiting for the program to complete before it sends you the output (which ping won't do, because it requires a terminal ctrl+c to end its execution).

If you want to use programs like ping on your server, you should install ssh on the server, or use the Java ssh applet included in Webmin.

---

### Post by happyhacker on 2009-02-23
I was trying to see why backuppc was complaining about not be able to ping my laptop. I cured this by configuring the client ip address in it's config. It then went on to a different error report. Basically I'm fed up with trying to get backuppc to work with rsync or smb so am now going over to synctoy backup to the server vis a mapped network drive. All the PCs in the office work this way. So I suspect I shall uninstall backuppc soon.

Thanks.

---

