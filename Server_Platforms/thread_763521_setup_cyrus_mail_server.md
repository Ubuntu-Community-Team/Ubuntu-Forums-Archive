---
title: "setup cyrus mail server"
date: 2008-04-23
forum: Server Platforms
---

### Post by doc_holiday on 2008-04-23
Dear,

When I try to add a the users doing the following

1. cyradm localhost

2. cm user.joebob  (for all the user joebob)


I get the following:

cyrus@mailserver:/usr/local/sbin$ cm user.steve
bash: cm: command not found


Any ideas?

---

### Post by doc_holiday on 2008-04-24
Nobody?

---

### Post by zobbo on 2008-05-19
Probably somewhat late but I'll give an answer here for anybody else who comes along. 

Note - I am just trying to get a simple cyrus install working so I can test some python code that wants a cyrus server. This is probably insecure, toxic, illegal in most countries and prone to spontaneous combustion. 

I suspect your problem was that cyradm was quietly dying. When you type the 'cm' command you are back at the shell prompt, not at the cyradm prompt. 

And the reason initially is that installing cyrus on Hardy gives a permission error. Do a "chown -R cyrus /var/lib/cyrus" and restart cyrus. Now it should ask you for a password. Now you've got another problem ;)

Do the following 
> 
apt-get install sasl2-bin

Then edit /etc/default/saslauthd as it suggests and set START=yes
> 
   /etc/init.d/saslauthd start
edit /etc/imap.conf and make sure that the following two settings are uncommented and with these values 

> 
   admins: cyrus
    ...
   sasl_pwcheck_method: saslauthd

restart cyrus and log in with 
> 
   cyradm -u cyrus --auth login localhost

Oh, you may need to set the cyrus user passwd first. Just become root and set it with passwd. Now you can login and create a mailbox. 
> 
localhost> cm ijc
createmailbox: System I/O error

Or maybe not - another permissions error it turns out. 
> 
chown -R cyrus /var/spool/cyrus

Log back in again and ... weeeeeeee
> 
localhost> cm ijc
localhost> lm
ijc (\HasNoChildren)
localhost>

There, nice and simple. Cough.

---

### Post by doc_holiday on 2008-05-22
When trying:

cyradm -u cyrus --auth login localhost

I get:

root@mailserver:/etc# cyradm -u cyrus --auth login localhost
IMAP Password: 
root@mailserver:/etc# lserver:/etc#

---

### Post by zobbo on 2008-05-22
are you seeing anything in /var/log/mail.err ?

---

### Post by doc_holiday on 2008-05-22
May 22 14:27:34 mailserver cyrus/imap[4086]: DBERROR: init() on berkeley
May 22 14:27:34 mailserver cyrus/imap[4086]: DBERROR: reading /var/imap/db/skipstamp, assuming the worst: No such file or directory
May 22 14:27:36 mailserver cyrus/imap[4086]: locking disabled: couldn't open socket lockfile /var/imap/socket/imap-1.lock: No such file or directory
May 22 14:27:36 mailserver cyrus/imap[4086]: IOERROR: creating /var/imap/proc/4086: No such file or directory
May 22 14:27:36 mailserver cyrus/imap[4086]: Fatal error: can't write proc file
May 22 14:27:36 mailserver master[4057]: process 4086 exited, signaled to death by 11
May 22 14:55:30 mailserver cyrus/ctl_cyrusdb[4112]: DBERROR: dbenv->open '/var/imap/db' failed: No such file or directory
May 22 14:55:30 mailserver cyrus/ctl_cyrusdb[4112]: DBERROR: init() on berkeley
May 22 14:55:31 mailserver cyrus/ctl_cyrusdb[4112]: DBERROR: reading /var/imap/db/skipstamp, assuming the worst: No such file or directory
May 22 14:55:31 mailserver cyrus/ctl_cyrusdb[4112]: DBERROR: couldn't checkpoint: Invalid argument
May 22 14:55:31 mailserver cyrus/ctl_cyrusdb[4112]: DBERROR: sync /var/imap/db: cyrusdb error
May 22 14:55:31 mailserver cyrus/ctl_cyrusdb[4112]: DBERROR: error listing log files: Invalid argument
May 22 14:55:31 mailserver cyrus/ctl_cyrusdb[4112]: DBERROR: archive /var/imap/db: cyrusdb error
May 22 14:55:31 mailserver cyrus/ctl_cyrusdb[4112]: DBERROR: couldn't checkpoint: Invalid argument
May 22 14:55:31 mailserver cyrus/ctl_cyrusdb[4112]: DBERROR: sync /var/imap/db: cyrusdb error
May 22 14:55:31 mailserver cyrus/ctl_cyrusdb[4112]: DBERROR: error listing log files: Invalid argument
May 22 14:55:31 mailserver cyrus/ctl_cyrusdb[4112]: DBERROR: archive /var/imap/db: cyrusdb error

---

### Post by zobbo on 2008-05-22
What version of Ubuntu are you running? Looking at Hardy here those files it's trying to find in /var/imap are located in /var/lib/cyrus
> root@ijcdev:/var/lib/cyrus# ls
annotations.db  db.backup2  mailboxes.db  quota            user
db              deliver.db  msg           socket
db.backup1      log         proc          tls_sessions.db
root@ijcdev:/var/lib/cyrus# pwd
/var/lib/cyrus

Try "sudo find / -name mailboxes.db" to locate the directory. How did you install cyrus?

---

### Post by doc_holiday on 2008-05-22
sudo find / -name mailboxes.db
/var/lib/cyrus/mailboxes.db
/var/lib/cyrus/db.backup1/mailboxes.db
/var/lib/cyrus/db.backup2/mailboxes.db
/var/imap/mailboxes.db
/var/imap/db.backup1/mailboxes.db
/var/imap/db.backup2/mailboxes.db


Sorry, can't find the site any more that I followed to install cyrus.

Another error that I found is:

cyradm> info
info: no connection to server

---

### Post by zobbo on 2008-05-22
I'm no expert but it looks to me as if you have two versions of cyrus installed. Was one installed from source? On the cleanish Heron version here I just have /var/lib/cyrus

You could try:

   chown -R cyrus.cyrus /var/imap

(which might help) but to be frank, I'd go back to a clean system and do a straight 

   sudo apt-get install cyrus-imapd-2.2 

If you are not on hardy do a 

   apt-cache search cyrus | grep imap 

to find the name of the package you require. 

If you have cyrus installed from both apt and source it's going to get mighty confusing. 

Ian

---

### Post by doc_holiday on 2008-05-22
chown -R cyrus.cyrus /var/imap
chown: `cyrus.cyrus': invalid user
root@mailserver:/etc# apt-get install cyrus-imapd-2.2 
Reading package lists... Done
Building dependency tree... Done
cyrus-imapd-2.2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
root@mailserver:/etc# 


But I'll clean install the system during the weekend. 
I only have one version of cyrus on it but had another mailserver on it before.
I'll try the clean install and let you know how it goos.
Thank you for your help.

---

### Post by hutzelfix on 2008-06-02
this is quite a mess...:confused:

it was a fresh install, don't forget:
apt-get install libsasl2 sasl2-bin 

I had to:
chown -R cyrus:mail /var/lib/cyrus
chown -R cyrus:mail /var/spool/cyrus

(most files belonged to root:root ...)

edit the /etc/imapd.conf to make cyrus an admin (this has been this way some years already...):lolflag:

at this very moment it seems to work.

---

### Post by zobbo on 2008-06-03
I ended up doing 

[http://blog.cottee.org/2008/05/cyrus-imap-on-hardy-heron.html](http://blog.cottee.org/2008/05/cyrus-imap-on-hardy-heron.html)

AND

[http://blog.cottee.org/2008/05/cyrus-imap-on-hardy-heron-2.html](http://blog.cottee.org/2008/05/cyrus-imap-on-hardy-heron-2.html)

Just to get it running. Must revisit this and get some proper understanding.

---

