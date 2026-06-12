---
title: "Configuring simple local mail"
date: 2009-01-16
forum: Server Platforms
---

### Post by gcornett on 2009-01-16
I have setup a simple FTP server. I want to run ddclient on the server so I can access it from the internet using dyndns.org. According to it's docs, ddclient needs to be able to send email confirming updates. I have sendmail, postfix, and mailx installed.

How do I set up mail to allow ddclient to do this? I'm not at all interested in setting up a full fledged mailserver which seems to be all I can find searching the forums. And I admit that sendmail configuation is way over my head.

---

### Post by gcornett on 2009-01-25
Ok. Nobody loves me.  :(

Sendmail is very difficult for someone of my skill level. I guess hoping for a simple answer was unreasonable.

My solution was to simply save all my data to another system and reinstall the OS, but this time I checked the mailserver option. Then during the mailserver configuration on install I selected local mail only. Good enough for now.

---

