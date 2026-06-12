---
title: "per Filezilla must update vsftpd 2.0.6 to 2.0.7"
date: 2008-09-24
forum: Server Platforms
---

### Post by winklebe on 2008-09-24
I have been using Filezilla and Ubuntu vsftpd successfully for some time. Filezilla client at 3.0.10 works fine. Switched to new Filezilla client 3.1.3 and fails with:

Response:	150 Here comes the directory listing.
Status:	Server did not properly shut down TLS connection
Error:	Could not read from transfer socket: ECONNABORTED - Connection aborted
Response:	226 Directory send OK.
Error:	Failed to retrieve directory listing

Filed bug report with Filezilla. Report rejected. Told update to vsftpd 2.0.7 . Ran apt-get update, apt-get upgrade and apt-get install vsftpd. Reports newest version already installed. ran dpkg -p vsftpd and found package is 2.0.6 .  How the heck do I get vsftpd 2.0.7 loaded?

---

