---
title: "Windows and Linux Permission Issues"
date: 2008-05-07
forum: Server Platforms
---

### Post by azurepancake on 2008-05-07
I still consider my self fresh fish in the Linux world so please excuse my ignorance!

We use a simple Ubuntu Hardy based file server for our four computer network. All the files are saved in one directory, "/home/user/Documents". The 'Documents' has been altered with the 'chmod 777' command. The other machines (Windows Vista and XP Professional) access the directory under the 'others' category (at least that is how I think it works).

Everything runs well, but the problem is that when a new folder is created in the 'Documents' directory by one of the Windows systems, the new folder doesn't inherit permissions. Then when one of the workstations tries to access the files in that folder, there are permission errors.

I really don't know what I should do now. Perhaps have them log into the server?

I would be ever grateful if anyone has any tips, advice or answers.

Thanks!

---

### Post by lswest on 2008-05-07
you could set up a cron script (a script that runs regularly) to run ```
sudo chmod -R 777 ~/Documents
``` which will recusively (therefore also sub-folders) set the permissions to 777 for the folder, and it will happen every so often, so it would be accessible.  Just a thought.  (Never used cron jobs, so someone else would have to post how to do it).

---

### Post by bluefrog on 2008-05-07
need to change umask but that would be quite horrible in my mind or play with acl

---

### Post by azurepancake on 2008-05-07
> **bluefrog said:**
> need to change umask but that would be quite horrible in my mind or play with acl

Hmm.. Editing the ACL might be what I need to do.. How and where does one access ACLs? Or am I missing concept of them?

Thanks!

Edit: I believe I found a way to solve my problem. I have edited the "Directory Mask" and have set it as '0777'. Now I just need to restart the samba service and hopefully it will solve my issue. I will let you guys know how it goes.

Thanks again!

---

