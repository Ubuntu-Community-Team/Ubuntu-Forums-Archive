---
title: "Merged two &quot;Maildir&quot; folders and now cant login"
date: 2014-09-06
forum: Server Platforms
---

### Post by bsrcube on 2014-09-06
Hey there folks,

I have 2 systems running Ubuntu 12.04 LTS. Lets call them Old and New.

Old system had - sendmail + dovecot + squirrelmail as the mail server setup.
New system has - postfix + dovecot + squirrelmail for the same.

The user accounts created on the new system is the same as it is in the old system. This gave me the same folder structure in the new system. I needed some mails present in the old system. So, I merged the contents of the **Maildir **folderfrom the old to the new using the command,
```
 rsync -aP  /oldserver/home/userA/Maildir /newserver/home/userA/Maildir 
```

After this, I cant login to the account. The error on the login page is as follows,

**[COLOR=#cc0000]ERROR: Could not complete request.[/COLOR]**[COLOR=#cc0000]
Query: SELECT "INBOX"
Reason Given: [SERVERBUG] Internal error occurred. Refer to server log for more information. [2014-09-06 08:51:32][/COLOR]

Which server log file is this error referring to? I cant find any at /var/log/.

I want to use some old mails, so I tried doing this. Am I doing it the wrong way? Or is there a better/different proper way to do it? 
I guess I must've mucked up the user configurations somehow by copying the dovecot specific files along with the mails. Correct me if I am wrong.

PS: I am not sure if this is relevant, but there is this peculiar behavior happening. The users for whom the Maildir has NOT been merged from the old system are getting multiple copies of the mails. Are these issues related? 

Thanks!

---

### Post by nerdtron on 2014-09-07
Try using cp command instead of rsync. Be sure to merge the Maildir folder of the users.
Also check the permissions and ownerships of the files and folders on the Maildir folder. I remember when migrating I changed the ownership of the files and the permissions just so the webmail can read the new files.

---

### Post by bsrcube on 2014-09-09
Hi Nerdtron,

Thanks a bunch! 

That's all the problem was and its fixed now.

---

