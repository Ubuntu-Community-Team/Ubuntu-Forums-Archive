---
title: "Using Ubuntu as a Backup Mailserver?"
date: 2007-05-04
forum: Server Platforms
---

### Post by becatlibra on 2007-05-04
A friend of mine asked me for help with a project.  He and I use the same Mailserver software (Kerio Mail Server.)  He was looking for a way to setup a backup, offsite (at his house) in case anything happens to the main server.  He set up MX records and I told him to try out Ubuntu.  

He couldn't get it to work at all.  If the main server went down, Ubuntu wouldn't accept any messages.  I don't get it and I don't know that much about mail.  His PIX shows traffic attempting to reach the other machine.  Any suggestions of Tutorials for Ubuntu for this sort of project?  I'm sure SOMEONE has done this before.  My understanding is that the backup server just caches the mail until the other server comes back up.  That shouldn't be difficult (I wouldn't think.)

Any links or a walk through would be great.

I tried using some debian walk throughs to help him but couldn't get it going.

Thanks

Benjamin

---

### Post by rsermilik on 2007-05-04
This has nothing to do with Ubuntu, Debian, or whatever you use. 
Which MTA has been installed and configured on the backup mail server?
Try to do:  telnet backupmailserver 25 and see if the smtp daemon accept connections.
> My understanding is that the backup server just caches the mail until the other server comes back up
Thats depending on your configuration.

More information is needed to help you.

---

### Post by becatlibra on 2007-05-04
He was using sendmail I believe.

I will check with him to see.

---

