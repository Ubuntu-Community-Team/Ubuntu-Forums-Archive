---
title: "Postfix - Procmail file not found"
date: 2009-09-21
forum: Server Platforms
---

### Post by timothy_tim on 2009-09-21
Hi,

A couple of weeks ago my mail-server worked just fine. At some moment I needed to change the userdb and added the following entry:
```
imap:{plain-md5}*some md5-hash*:501:501::/data/imap/mail
```Everything seemed to be fine. You could login with the user name 'imap'.
After time passed I noticed that no mail was received for the user 'imap', all other users received the e-mails send to them. When I looked at the log files I found this line in the log file '/var/log/mail.err':
```
abacus5 local[19177]: fatal: execvp /usr/local/bin/procmail: No such file or directory
```Strange, but easy to fix you may think. I thought this could easily be solved by making a sys-link to the correct location of the file: /usr/bin/procmail. But when 'solving' like this, all mail went down the drain. I never received an e-mail.
According to my postfix configuration all incoming e-mail should be delivered to 'procmail -a "$EXTENSION"' as the following code shows:
```
tim@abacus5:~$ postconf -n|grep mailbox_command
mailbox_command = procmail -a "$EXTENSION"
```I just can't find out why e-mails to the user 'imap' are not delivered to the procmail command as specified. I hoped replacing the config-files by some older versions would solve the problem, but seemed to work.
Is there some other file I overlooked or does anybody know what I did wrong?

~Tim

---

### Post by timothy_tim on 2009-10-15
I finally found out which file was troubling me.
It seems the file */data/imap/.forward* overwrites the config-file. When I removed this file every e-mail arrived at the right location. :-)

---

