---
title: "sub folder wrongly appear on the list"
date: 2012-04-10
forum: Server Platforms
---

### Post by ali888 on 2012-04-10
Hi,

I am transferring all IMAP mails from my old mail server to the new mail server which is running on Ubuntu Server 10.04 LTS using imapcopy.

The transfer was success, however I noticed that all the INBOX sub folders do not appear on the left panel list of squirrelmail 1.4.20 under the INBOX folder. I checked all the subfolders of INBOX have INBOX. prefix.

For example, it should have appeared as follows
INBOX
     Football
     Swimming
Deleted Items
Drafts
Sent Items

But instead,
INBOX
Deleted Items
Drafts
Sent Items
    Football
    Swimming
    
I then went to double check to see if it is what I think is happening by creating another sub folder on the squirrelmail. I chose create folder "Harry" as a subfolder of INBOX, and clicked OK. Guess what, it came up underneath the Sent Items folder rather than INBOX folder. I think there must be something wrong in my squirrelmail config but I do not know exactly what it is. I wonder if anyone here might be able to help me out.

Any help or input is greatly appreciated. Thank you

---

