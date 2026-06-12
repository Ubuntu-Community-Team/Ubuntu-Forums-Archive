---
title: "shell lftp"
date: 2019-04-06
forum: Server Platforms
---

### Post by bazo22 on 2019-04-06
Hi, first excuse for my english, i never speak english with other people. So i have 2 servers, one at home with ubuntu server (16.04.1), and an other i have just an FTP access.

I want to sync folder and files to my home.

I search and i use this script with a cron every hour.

```
#!/bin/bash
HOST='host'
USER='login'
PASS='password'

TARGETFOLDER='/dossier serveur maison'
SOURCEFOLDER='/Dossier serveur distant'

lftp -f "
open $HOST
user $USER $PASS
lcd $TARGETFOLDER
mirror --only-newer --verbose --no-umask $SOURCEFOLDER $TARGETFOLDER
bye
"
```

It's the first time i use a script. 
For the moment the script work fine. But i have a problem for the folder.
Example : i have a file test.pdf and a folder test on the server cloud, the cron active and the script copy folder and file on my server home.
After few days i want to delete the test.pdf everything is ok i can. But the folder when i want to delete i can't. I don't have the permission.
I try execute the shell script with a user or with root, the same.

If you can help me, thanks.

---

### Post by TheFu on 2019-04-06
To sync files between two servers, **rsync** is the goto tool used.  rsync will use ssh tunnels and ssh authentication automatically, which is a bonus.
Using plain FTP over the internet is asking to be hacked.  The credentials are sent without any encryption over the internet, which is beyond a terrible idea.

If you setup ssh-keys between the systems, automation becomes trivial.

If computers are on the same LAN, you can setup an rsyncd which will connect and NOT use any ssh tunnelling. It is very fast.  Just change to :: instead of : in the command below.
```

# to pull the files, recursiving from the remote-server-IP using the bazo account
$ rsync -avz bazo@remote-server-IP:/Dossier-serveur-distant/ "/dossier serveur maison"
```

This won't fix permissions issues, if there are any.  If your userid on the remote system can't read the files, then they won't be copied.  If your local account doesn't have permissions to write to the local directory, that needs to be solved too.

If your goal is to accomplish backups, then using a backup tool would be better. Most of the commonly used backup tools on Linux work using librsync and support ssh tunnels in the same manner. Very similar commands to the rsync one above would be used for backup tools, which provides so much more.  You can push or pull backups. Pulling would be better from a security standpoint.
Also, having spaces in directory names and filenames will always cause problems with scripts.  Best to never do that or you'll need to be much better at scripting.  Are you certain those are the correct directories in the script above?  Should they not be relative from the login directory or are they really in the root directory?

I need to apologize. My knowledge of plan FTP tools is extremely limited since we stopped using it in the 1990s over security considerations. Nothing about plain FTP security has gotten better, however.

---

### Post by houstonbofh on 2019-04-07
You can try lftp, which is similar to rsync but for ftp.  Some info here.  [http://rajaseelan.com/2011/12/20/rsync-over-ftp/](http://rajaseelan.com/2011/12/20/rsync-over-ftp/)

---

### Post by bazo22 on 2019-04-08
Hi, i have just an access FTP so just LFTP can work.

---

### Post by TheFu on 2019-04-08
> **bazo22 said:**
> Hi, i have just an access FTP so just LFTP can work.

You don't have ssh access?  Really?!!!

---

### Post by bazo22 on 2019-04-08
> **TheFu said:**
> You don't have ssh access?  Really?!!!
On my serve at home i have all access but on the "cloud" i have Just ftp. It's not strange, look after webhosting it's Just ftp access

---

### Post by TheFu on 2019-04-08
> **bazo22 said:**
> On my serve at home i have all access but on the "cloud" i have Just ftp. It's not strange, look after webhosting it's Just ftp access

All my webhosts provide ssh. I had to send in a fax with photo ID before they'd enable it. Used that for a few years, then figured out that webhosts who allow plain FTP to anyone is destroying my security even if I don't use it.  That got me to fire them and move to a provider who better respected security. Since I was in the position to control the webhost, I did.  Not everyone can.  

But we all have different risk acceptance levels and limitations for what is possible.  Knowing the risks is always good, even if we can't directly address them. Any chance they support ftps?  It is not as secure as sftp/ssh/scp/rsync, but at least the credentials wouldn't be transferred without any encryption.

---

