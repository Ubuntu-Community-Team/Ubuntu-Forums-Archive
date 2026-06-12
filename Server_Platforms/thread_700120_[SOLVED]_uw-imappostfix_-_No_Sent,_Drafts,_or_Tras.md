---
title: "[SOLVED] uw-imap/postfix - No Sent, Drafts, or Trash folder."
date: 2008-02-18
forum: Server Platforms
---

### Post by uncannybuzzard on 2008-02-18
ok, i have postfix, uw-imap and some pop3 daemon up and running for the most part. i can send and receive messages using everything, either unencrypted or using SSL, however, when i send using IMAP, it cannot save messages to the Sent folder. in fact, the olny folder i have in my email client is Inbox, which works perfectly. i don't understand enough about uw-imap config or file structure to troubleshoot this. i do know that mail is being delivered to /var/mail/[username] successfully. where is the Sent folder supposed to be located in relation to this. i had assumed it was a different section of the same file, but apparently not.

---

### Post by MJN on 2008-02-18
Firstly, I would consider an alternative to uw-imap - it's starting to show its age and is far from being particularly configurable. I'd personally recommend Dovecot, or Courier is another popular one.
 
Regarding folders these are normally stored within the user's home directory i.e. not with the Inbox in /var/mail/. The 'special' folders you speak of are sometimes created automatically by the IMAP server however you should be able to get your client to create them.
 
Before getting too far down the road reconsider replacing uw-imap with Dovecot as this step alone may well solve your problem.
 
Mathew

---

### Post by uncannybuzzard on 2008-02-18
fix'd. the /var/mail/[username] file was corrupted. deleted it and uw-imap recreated OK.

---

### Post by MJN on 2008-02-18
Ah good.
 
I'd still recommend a change of IMAP server though, particularly given the opportunity to use Maildir-style message storage as opposed to the mbox format that uw-imap uses (at the very least it is not susceptible to this sort of problem due to 'corrupted' files).
 
Mathew

---

### Post by uncannybuzzard on 2008-02-18
yeah, it was my fault to begin with. i was messing around with the home directory of this particular user in /etc/passwd
i have ispconfig installed on this server an i am wary to mess with the internals too drastically for fear of breaking it. i set the home directory back to what it should be and it worked fine, now i just have to figure out how to break the ~ chroot jail for this user for proftpd so i can upload to /var/www

---

