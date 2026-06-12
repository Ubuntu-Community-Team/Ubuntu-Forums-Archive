---
title: "Our school's server got hacked :("
date: 2007-03-22
forum: Server Platforms
---

### Post by tomplast on 2007-03-22
First let me give you some background information on this. I'm working at a gymnasium (sort of high school) in Sweden where I administrate (when needed) some web servers together with a guy.

It started yesterday when suddenly the server couldn't be reached. I tried some stuff and I found that there were no software / hardware problem on the server, in the evening I found out that the IP address which belongs to that server had been taken down (ping worked nothing else).

The cause: they (some steps upon the ladder) said that the server had most likely been hijacked.  We later found out that our server supposedly should have tried to hack some ftpservers a 1000 couple of times and therefore the IP had been taken down (have no better word for it).

We checked several logs and couldn't find anything ouf of order. The root password were still the save, the logs didn't spoke about any massive traffic sent out... Perhaps the hacker were clever, or maybe it's a question of IP spoofing, I haven't a single clue...

Anyway, to ensure myself that this isn't some sick thing done by any of the students I have removed execution permission on ftp, ping, telnet, ssh and other outgoing services.

And before I end this, there is something weird with the system. Sometimes when I'm logged out a message appears on the screen quite often, it's something about that the log system has been restarting or something like that (don't remember the exact words but something like that).


If anyone could give me some help here and perhaps tip of anything I should do to secure the system and prevent things like this in future I would be very happy.

---

### Post by nocturn on 2007-03-22
If you have been hacked, I can make only one recommendation.  Do a FULL reinstall.

Don't use services like telnet and FTP, they transmit passwords in clear text.

---

### Post by tribaal on 2007-03-22
I second that - use SSH instead, it's much safer.

- trib'

---

### Post by tomplast on 2007-03-22
Yeah I know about the security concerns around telnet and ftp, it's just that I haven't just removed them yet. Telnet isn't in use but ftp is, mainly because our school uses Internet Explorer and we have currently no software for connection with like sftp. It's a installation issue, not a technological, it's just that it's not always so simple to change such things in a school environment :(

I will take your advices to me, reinstall is a must I can see now. It would be better if I do it right from the start. Removing everything unnecessary, setting up a restrictive firewall, disabling hazardous services etc.

Btw, is is possible to use the migration assistant on an Edgy Eft system? And can I migrate user accounts from a partition that I'm about to delete?

---

