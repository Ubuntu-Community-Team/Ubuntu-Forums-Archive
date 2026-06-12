---
title: "SquirrelMail - problem on mail boxes"
date: 2008-06-15
forum: Server Platforms
---

### Post by satimis on 2008-06-15
Hi folks,


Ubuntu LTS 6.06 amd64
Cyrus
Postfix
SquirrelMail


I have problem on mail boxes.  Emails can be received.  But they can't be deleted.  On deleting following warning popup.```

ERROR: Could not complete request.
Query: COPY 13 "INBOX.Trash"
Reason Given: Permission denied

```


Also emails can be sent on SquirrelMail and received at destination.   But the emails sent can't be saved on the "Inbox.sent" mailbox with
the same warning popup.


$ sudo ls -al /var/spool/cyrus/mail/s/user/satimiscyrus```

total 24
drwx------ 2 cyrus mail 4096 2008-06-15 09:39 .
drwx------ 3 cyrus mail 4096 2008-06-09 16:35 ..
-rw------- 1 cyrus mail 1503 2008-06-15 08:50 13.
-rw------- 1 cyrus mail 1116 2008-06-15 09:39 cyrus.cache
-rw------- 1 cyrus mail  158 2008-06-09 16:35 cyrus.header
-rw------- 1 cyrus mail  136 2008-06-15 09:39 cyrus.index

```


$ sudo ls -ld /var/spool/cyrus/mail/s/user/```

drwx------ 3 cyrus mail 4096 2008-06-09 16:35
/var/spool/cyrus/mail/s/user/

```


$ sudo ls -ld /var/spool/cyrus/mail/s/```

drwxr-xr-x 3 cyrus mail 4096 2008-06-09 16:35 /var/spool/cyrus/mail/s/

```


Please advise how to fix the problem.  TIA


B.R.
satimis

---

### Post by MJN on 2008-06-15
Given your special folders are sub-folders of the Inbox this may not be applicable, but check the permissions of your user's mail folder areas (e.g. ~/Maildir/ or whatever you've set it at). I'm not familiar with Cyrus so this could be another factor which renders my suggestion futile.

Mathew

---

### Post by satimis on 2008-06-15
> **MJN said:**
> Given your special folders are sub-folders of the Inbox this may not be applicable, but check the permissions of your user's mail folder areas (e.g. ~/Maildir/ or whatever you've set it at). I'm not familiar with Cyrus so this could be another factor which renders my suggestion futile.

Hi Mathew,


On Cyrus the folders are not on ~/Maildir

They are on;

$ sudo ls -la /var/spool/cyrus/mail/s/user/satimiscyrus```

total 24
drwx------ 2 cyrus mail 4096 2008-06-11 08:30 .
drwx------ 3 cyrus mail 4096 2008-06-09 16:35 ..
-rw------- 1 cyrus mail 2054 2008-06-11 08:30 1.
-rw------- 1 cyrus mail 1760 2008-06-11 08:30 cyrus.cache
-rw------- 1 cyrus mail  158 2008-06-09 16:35 cyrus.header
-rw------- 1 cyrus mail  136 2008-06-11 08:30 cyrus.index

```

B.R.
satimis

---

### Post by MJN on 2008-06-15
Oh I see.

I cannot see your folders but obviously I'm misunderstanding how Cyrus works compared with Dovecot.

Can you create two folders for me, one as a sub-folder of the Inbox, and the other outside of the Inbox, then post the output from your directory listing again?

Mathew

---

### Post by satimis on 2008-06-16
> **MJN said:**
> Oh I see.

I cannot see your folders but obviously I'm misunderstanding how Cyrus works compared with Dovecot.

Can you create two folders for me, one as a sub-folder of the Inbox, and the other outside of the Inbox, then post the output from your directory listing again?

Hi Mathew,


Thanks for your advice.  Problem solved.


The problem is only accounting to Cyrus packages nothing involving SM.  There are something missing on the config files of Cyrus.  The permission and ownship of some files differ from their directory.


It tooks me couple days to trouble-shoot the causes.  My finding is not easy to manage Cyrus, better using Dovecot or Courier.  It is because I need Cyrus packages for a test on 2-factor One Time Password.


Remark:

It is NOT the problem of the packages on Cyrus office site.  But it is the problem of Cyrus packages on Ubuntu repo which have some modification on the official packages.   If interested on Cyrus better download the packages on their official site


B.R.
satimis

---

### Post by MJN on 2008-06-16
> **satimis said:**
> Thanks for your advice.  Problem solved.

That's excellent.
> The problem is only accounting to Cyrus packages nothing involving SM. That's right - it's an IMAP error - SM is merely passing you the output.> There are something missing on the config files of Cyrus.  The permission and ownship of some files differ from their directory.Can you elaborate on exactly what your fix was in case someone else has this problem?

Mathew

---

### Post by satimis on 2008-06-16
> **MJN said:**
> Can you elaborate on exactly what your fix was in case someone else has this problem?

Hi Mathew,


OK.  It is my pleasure.


I follow this guide;
[https://help.ubuntu.com/community/Cyrus](https://help.ubuntu.com/community/Cyrus)

to install/config Cyru.  At finish it won't work because some config files have been modified on Cyrus official copies, missing something.


Solution: -

/etc/cyrus.conf
adding following lines at end of the file```

admins: cyrus
unixhierarchysep: 0

```


/etc/imap.conf
adding following line at end of the file```

sasl_saslauthd_path: /var/spool/postfix/var/run/saslauthd/mux

```


$ sudo ls -l /var/run/cyrus/socket```

total 0
srwxrwxrwx 1 root root 0 2008-06-10 06:55 lmtp
srwxrwxrwx 1 root root 0 2008-06-10 09:09 notify

```
They are OK.


$ sudo ls -ld /var/run/cyrus/socket```

drwxr-x--- 2 cyrus mail 80 2008-06-10 09:09 /var/run/cyrus/socket

```


$ id postfix```

uid=107(postfix) gid=111(postfix) groups=111(postfix)

```


The socket can't be visited by postfix unless putting the latter on "mail group"


If w/o mail group on /etc/group create it and put postfix on this group.


The abovementioned are my solution making Cyrus to work.


B.R.
satimis

---

### Post by MJN on 2008-06-16
Thanks for that Satimis.
 
I'm curious as to why others aren't seeing this, as Cyrus is a commonly deployed platform.
 
Still, hopefully if/when others do come across this your solution will help.
 
Mathew

---

