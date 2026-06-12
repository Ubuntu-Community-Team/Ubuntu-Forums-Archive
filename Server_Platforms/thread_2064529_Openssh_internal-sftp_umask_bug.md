---
title: "Openssh internal-sftp umask bug?"
date: 2012-09-29
forum: Server Platforms
---

### Post by MReptile on 2012-09-29
Dear Community

I have the following problem:

Basically it should be possible to alter the Umask of newly created files over sftp using the following command in the sshd_config file

Subsystem sftp internal-sftp -u 0007

Unfortunately this does not work. Using the libpam_umask package in the /etc/pam.d/sshd does not wrok either.

I tried all the available tutorials out there. (Google Search)
Is this a bug? Because on every other OS except Ubuntu it seems to work properly this way?

Can someone help me?
Or send a bugreport to the right persons?

---

### Post by Lars Noodén on 2012-09-29
I'm able to get umask to work in 12.10 using the line you provided.  What version of Ubuntu are you using?  Also are you restarting the ssh server and logging out from your SFTP client between changes to your settings?

---

### Post by MReptile on 2012-09-29
I am using Ubuntu 12.04 LTS
All updates installed without the "proposed".
Yes I in addition even restartet both computers.

I enabled ACL's in this folder. But this should not affect the UNIX based rights.

---

### Post by Lars Noodén on 2012-09-30
Sorry I meant restarting just sshd not the whole machine or restarting the sftp client.  

Can run the sftp-server in verbose mode to see what's happening when you connect and upload a file?  It might give some clues in /var/log/auth.log then.

```

Subsystem sftp internal-sftp -u 0007 -l info

```

---

### Post by MReptile on 2012-09-30
There is no info stored in auth.log after logging in.

Or are you looking for this lines:

Sep 30 07:40:03 kocro-server CRON[18218]: pam_unix(cron:session): session closed for user root
Sep 30 07:45:01 kocro-server CRON[18242]: pam_tally2(cron:account): unknown option: reset
Sep 30 07:45:01 kocro-server CRON[18242]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 30 07:45:04 kocro-server CRON[18242]: pam_unix(cron:session): session closed for user root

Furthermore I installed the quantal openssh-package to see if the problem is in the actual release. It is not.
The Problem is the same with the newest version. I reverted back of course.

Do I have to change anything else to get this to work.
I really only changed this line

Subsystem sftp internal-sftp -u 0007

I want newly created files to be 700.
It does not work so far.
Are there files on the local harddisk overwriting the umask again?
Or do I have to enable a pam_module somehow that this option works?
What have you done to make it work?
Which steps exactly?

I am using the EXT4 Filesystem
ACL's enabled.

---

### Post by Lars Noodén on 2012-09-30
> **MReptile said:**
> 

I want newly created files to be 700.


For that you need umask 0077.

```

Subsystem sftp internal-sftp -u 0077

```

---

### Post by MReptile on 2012-09-30
Of course sorry.
I wrote it incorrectly 
I want to have newly created files with 770
then umask -u 0007 is correct.

Unfortunately it does not work.
This was not the problem. The files remain 
readable by others.

As I asked you before:
Have you made any additional steps in SSH to make it work?
Probably enabled a pam_module?

I copy/pasted your line. Restarted SSHD with
service ssh restart.
It does not work

---

### Post by Lars Noodén on 2012-09-30
I've used stock openssh-server with only one line of sshd_config modified as above.  For umask 0007, it uploads files like this:

```

-rw-rw----    0 1002     1002          30B Sep 30 14:04 z

```

Maybe it should be -rwxrwz--- instead, but at least it is not readable by Other.

---

### Post by MReptile on 2012-09-30
Why the heck is this not working for me.
I have installed Ubuntu 12.04 unchanged.
Normal updates.
+ openssh-server as available in repositorys.
Only thing that I changed was the same line.

I use Windows to connect.
With WinSCP Does the Umask only affect Linux Clients?

---

### Post by GrayJack on 2013-05-21
If it is still an issue, I believe here is the source of your problem and possible solution: [http://sysadmin.circularvale.com/server-config/setting-a-umask-for-chrooted-sftp-users/](http://sysadmin.circularvale.com/server-config/setting-a-umask-for-chrooted-sftp-users/)

---

