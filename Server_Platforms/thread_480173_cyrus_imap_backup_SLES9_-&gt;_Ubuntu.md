---
title: "cyrus imap backup SLES9 -&gt; Ubuntu"
date: 2007-06-21
forum: Server Platforms
---

### Post by dexter2 on 2007-06-21
Hi,
i'm trying to make backup of Cyrus imap server (Version: 2.2.3-83.5) running on SLES 9 to Cyrus imap (Version: 2.2.13-10ubuntu2)  running on Ubuntu server 7.04.
I have exported mailboxes database on SLES server by: 
su - cyrus -c 'ctl_mboxlist -d' > /var/lib/imap/backup/mailboxes.txt
and imported it in Ubuntu server:
su - cyrus -c '/usr/sbin/ctl_mboxlist -u < mailboxes.txt'
User mailboxes directories under SLES 9 are stored directly in /var/spool/imap/user/username.
User mailboxes directories under Ubuntu are stored in /var/spool/cyrus/mail/x/username, where 'x' is first leter of username.
So i have saparetely copy each user mail directory: 
sles9server:/var/spool/imap/user/username/* -> ubuntuserver:/var/spool/cyrus/mail/x/username/ 
Than I have removed all 'cyrus.*' files from /var/spool/cyrus/mail/ tree. 
I have run reconstruct from Webmin for all mailboxes at once. 
Everithing looks ok, but there is a problem. In webmin i see all subfolders as in original, but when i access maibox with Thunderbird (or Outlook) client, i don't see subfolders. I can see only email directly in mailbox.
Did i forget something?
Thanks a lot for advice.
    Dexter2

---

### Post by dexter2 on 2007-06-21
So, answering myself.
Problem is not in backup steps. Problem is in imap clients. Imap client by default display only folders created in them. If you want to display all folders than in 
Thunderbird: Acount settings - account - server setting - advanced -unclick " Show only subscribed folders".
Outlook: right click on server folder - imap folders - unclick  " Show only subscribed folders".

---

