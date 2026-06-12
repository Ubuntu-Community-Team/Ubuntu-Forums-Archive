---
title: "Using NFS in a LVM"
date: 2012-02-17
forum: Server Platforms
---

### Post by mmoore on 2012-02-17
Hi everybody,

I am trying to work on the following scenario:

I have one server, which is going to be used to serve webpages and to host eMail. It is a regular server install and during partitioning I have put /var on a LVM since it might need to be extended.

Additionally I have a storage system which can be used to provide additional storing space as needed. This storage system provides the additional space as a NFS share.

Is it possible to extend the Volume Group inside the LVM with a NFS share, and if, how can it be done?

Thank you for your kind help.


Manuel

---

### Post by SeijiSensei on 2012-02-17
I can't answer this question; I've never tried to add an NFS share to a VG.

However one alternative would be mounting the NFS share to house one of the major subdirectories of /var.  You can easily mount your NFS share as /var/www and place all the web content on it.  Putting /var/spool on NFS is controversial because of [locking issues]("https://www.google.com/search?q=%2Fvar%2Fspool%2Fmail+on+nfs") in /var/spool/mail with mbox-formatted mailboxes.  If you use Maildir instead of mbox, using NFS for /var/spool would be fine.  

The other big devourers of /var are logs in /var/log and, if you use databases, /var/lib, where /var/lib/mysql and /var/lib/pgsql can be found.  /var/cache contains all the downloaded .deb files from package updates and can sometimes be large as well.

I'd suggest you leave the NFS partition alone for a while and just run the machine with the /var you have now.  In a couple of months you'll have a much better sense of file storage patterns and can make a better strategic decision about what to do with the NFS share.

---

### Post by mmoore on 2012-02-21
Thank you for your reply.

I was intending to keep /var as small as possible so that as little data as possible remains on the server itself. 

Goal of this exercise is to make this server a bit more secure, so that the data is seperated from the server. Another issue there is to make sure that /var can easily be extended, which should be possible by using a LVM setup.

Would you happen to know if there are any issues using iSCSI-connections to extend the space?

Thank you for your kind help.

---

### Post by SeijiSensei on 2012-02-21
> **mmoore said:**
> I was intending to keep /var as small as possible so that as little data as possible remains on the server itself.

I think it's worth thinking a bit about which data are so important or private that they should be stored elsewhere.  You could just put all of /var on NFS I suspect, though there may be locking issues.  Just for a server offering web content and mailboxes I think this is a bit of overkill to be honest.  You won't thwart anyone who gets root on the machine; at best you're protecting against physical seizure of the machine.  For that, using an encrypted file system makes more sense.

In addition, if you use IMAP for your primary mailbox protocol, the users' mail folders will end up in /home/username or /home/username/mail depending on how you set things up.  Only the inboxes will be stored in /var/spool/mail.  On a web/mail server I'd only be concerned about protecting the mailboxes and folders.

If your web server will be collecting personal information about visitors and storing it in a database, you might want to put that database somewhere else and connect to it over the network.  

> Would you happen to know if there are any issues using iSCSI-connections to extend the space?

I'm sorry, but I don't know anything about those either. 

> Thank you for your kind help.

You're quite welcome!

---

