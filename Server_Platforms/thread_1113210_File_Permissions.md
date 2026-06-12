---
title: "File Permissions"
date: 2009-04-01
forum: Server Platforms
---

### Post by mregister on 2009-04-01
Hello All,

I am having what I belive is a file permission issue. I wrote a script that basically runs a mysqldump and copies that file to a folder on root /backup/mysql. I have set that script to run via a daily cron job. Now that all works great but I cannot download the file using Bitvise Tunnlier. I can go into that directory and create a test file and download it just not any of the dump files my scrpit creates. I know that there are better ways than to manually download the file but I am curious as to why I can't. The script, directory, and crontab were all setup with the same user, so why can't I download the files created by the script?

Also, why is the background on the fourm hot pink? Is it just me?

Thanks to all,

Mark

---

### Post by BkkBonanza on 2009-04-01
You'll need to look specifically at the owner/group and permissions of the file you created. How it was created and by whom has a bearing on the final permissions set on the file. If you're not sure about that then just post the permission string,

rwx rw r  user1:user2 

for the final file and how your user is related to the file. Also what user you login as in tunnelier.

---

### Post by mregister on 2009-04-01
That's the thing that I don't understand. Everything is done with the same user. It's the only user there is. Like I said I can download a file that I create manually in the directory but not any of the files that the scpript creates?

---

### Post by cdenley on 2009-04-01
```

ls -l /backup/mysql

```
Tell us which files you can or can't download, and which were created by the cron job.

---

### Post by mregister on 2009-04-01
The permissions on all the files are:

> -rw-r--r-- 1 root      root 5232369 2009-04-01 00:00 dlbd.01-04-2009-00:00:02.sq

So I guess I would have to login as root to download them? I am currently logging in with Tunnelier with the same account that created the folder and the script, and the cronjob.

So after the job runs the files are in effect created by root? Or maybe I setup the cronjob with sudo so that means that the cronjob runs as root making root the owner of the files that are created which means that I can't download them? 

How do I tell what user the cronjob runs under?

---

### Post by cdenley on 2009-04-01
> **mregister said:**
> So I guess I would have to login as root to download them? I am currently logging in with Tunnelier with the same account that created the folder and the script, and the cronjob.

So after the job runs the files are in effect created by root? Or maybe I setup the cronjob with sudo so that means that the cronjob runs as root making root the owner of the files that are created which means that I can't download them? 

How do I tell what user the cronjob runs under?

Those permissions indicate that any user can read that file. Unless that server (Tunnelier) does something strange, or a parent folder has restrictive permissions, or you're using ACL's, you should be able to download it.

There are a few different ways to create cronjobs. How did you create yours? If you use the "crontab -e" command, then the jobs you create will run as the user the crontab command is run as. Running "sudo crontab -e" runs the command as root.

---

### Post by mregister on 2009-04-01
Yes I did crontab -e but I can't rember for sure if I put sudo in front or not. I know this is something goofy. Thanks for the input cdenly, I will report back when I figure someting out.

---

### Post by BkkBonanza on 2009-04-02
You probably did create the cronjob as root. You can tell by doing crontab -l and then sudo crontab -l, and seeing which one lists the job. You may have done that because your normal user doesn't have rights to the mysql data. In any case the file has been created with r perm on "any" user, so it outght to be copyable by anybody.

How are you using tunnelier to copy the files? By sftp or rsync/ssh? Are you sure that it isn't a problem with permissions on the receiving end? Just more things to check. The exact error message you get may be helpful as sometimes the wording can be mis-interpreted. It doesn't appear that you should be having permission trouble.

---

### Post by mregister on 2009-04-02
Tunnelier uses SFTP. The cronjob was setup with root. But the permissions seem fine like cdenly says. The Tunnelier error log says:
> Getting local file size failed. The filename, directory name, or volume label syntax is incorrect.

I am not using ACL's. I'll keep looking and report back. Thanks to all.

Mark

---

### Post by cdenley on 2009-04-02
I don't think openssh-server < 5.1 supports determining a filesize using SFTP. I would try downloading the file with sftp or scp, or viewing it through ssh. Determine whether it is a filesystem problem, SSH problem, or Tunnelier problem.

---

### Post by mregister on 2009-04-02
LOL. The deal is that the dump files are named with a time stamp and my windows box can't deal with that. Ex: backup-03-21.09-00:00:01. Windows can't deal with the colon. Duh! I knew it was something simple or something I was overlooking.

Thanks cdenly and BBKbonaza for the input.

Mark

---

