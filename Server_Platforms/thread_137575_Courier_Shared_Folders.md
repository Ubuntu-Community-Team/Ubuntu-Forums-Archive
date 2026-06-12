---
title: "Courier Shared Folders"
date: 2006-02-28
forum: Server Platforms
---

### Post by SleightfulMind on 2006-02-28
I have installed Courier (IMAP and POP3 both SSL and non-SSL), postfix, spamassassin, mysql, TSL and SASL. I have now created a shared folder entitled PublicFolders that has 2 subfolders Spam and NOTSpam (my spam and ham buckets). The problem is that when a user copies an e-mail into the Spam or NOTSpam folder, it is readable to all users. I want these folders to be shared dropboxes for spam and ham. E-mails should not be accessible to other users. Please advise me on how to accomplish this.

Thanks!

---

### Post by SleightfulMind on 2006-02-28
So, once again, there was a simple solution to a simple problem staring me in the face... I was trying to use groups and user permissions to allow administrators to see the e-mails, but then I realized that is not necessary in order for spamassassin to learn... Just removing read permissions for all solved the problem. Now users can submit e-mail to spam and ham folders, but they cannot see the e-mails.

---

