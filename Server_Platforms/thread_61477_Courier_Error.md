---
title: "Courier Error"
date: 2005-08-31
forum: Server Platforms
---

### Post by TheDanMan on 2005-08-31
Hi,

First of all, ubuntu has been so easy to transition into from redhat/windows environment it is insane.  I love just how easy Ubuntu makes everything.

Second:

I'm running an Ubuntu server that runs apache2 with php4, mysql, postgre, postfix for SMTP, and Courier.  I have webmin installed running virtualmin.  I can to mail to send, however pop3 fails and gives the error "Maildir: No such file or directory."  This is obviously a courier error as it is the server handling pop3 requests and Courier is the only thing that uses Maildirs other than qmail and that isn't installed.

I'd appreciate it if someone could point me in the right direction.  I've been without email for the later half of the day and would like it up by morning.  I don't want to put the old redhat server back up because it was slow and mail ins't an end all issue.

Thanks
Dan

---

### Post by TheDanMan on 2005-08-31
One thing of note, webmin seems to be able to read the mail from /var/mail just fine as my users have just been using that in the meantime.  They can both send and recieve just fine.  They just can't remote connect via pop3.

---

### Post by TheDanMan on 2005-09-01
[QUOTE=TheDanMan]One thing of note, webmin seems to be able to read the mail from /var/mail just fine as my users have just been using that in the meantime.  They can both send and recieve just fine.  They just can't remote connect via pop3.[/QUOTE]
 Issue resolved.  I switched to dovecot.

---

