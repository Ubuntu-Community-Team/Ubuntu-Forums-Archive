---
title: "Problem running DSPAM with Dovecot/Postfix in Ubuntu 9.04"
date: 2009-09-12
forum: Server Platforms
---

### Post by storwalle on 2009-09-12
Hi!

Twice have I followed this instruction ([https://help.ubuntu.com/community/Postfix/Dspam](https://help.ubuntu.com/community/Postfix/Dspam)) on how to install and configure DSPAM for integration with Dovecot/Postfix. Everything seems fine until it is time to reload and start everything. It brokes my mail server and it refuses to receive any emails.

The reason for the problem is given as "Connection refused for localhost on port 11124", if I write it in more and clearer text. Since I have had to uninstall and reconfigure my mail system to get it working again I do not have the exact lines from the mail server log.

Anyone that does understand why this is happening? There seems to be extremely few postings on the topic, at least judging from what I can find googlin'...

I am not a magician in Linux, so please explain as I am 5 years old... ;-)

Kind regards
Michael

---

### Post by Sascha Henken on 2010-10-15
Sorry to bring up this old thread and sad nobody else found a way to this one. I´ve tried the exact same tutorial several times and it does not work whatever Jack wrote there. The only thing that works is that incoming mails are scanned and the DSPAM ID is added to the message body end of line and you have DSPAM Header Information as well. But what does not work is if you want to forward messages to learn them as SPAM or HAM, the Perlscript is unable to find the designated DSPAM ID so the message goes down the drain and you have no benefits out of it.
 
I´m using Ubuntu 8.04.4 LTS and thought to give DSPAM again a try since it was taken over by a new company.
 
I would like to keep this discussion going here so maybe we find a suitable solution :)

---

