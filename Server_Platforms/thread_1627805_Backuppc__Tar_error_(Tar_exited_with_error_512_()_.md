---
title: "Backuppc  Tar error (Tar exited with error 512 () status)"
date: 2010-11-21
forum: Server Platforms
---

### Post by Jersey-Fresh on 2010-11-21
I have installed backuppc on Ubuntu server 10.04 amd 64 with the purpose of backing up just the localhost using tar and whenever i try to start a full backup i get 
2010-11-21 19:43:33 User backuppc requested backup of [localhost]("http://192.168.1.2/backuppc/index.cgi?host=localhost") ([localhost]("http://192.168.1.2/backuppc/index.cgi?host=localhost"))
2010-11-21 19:43:34 Started full backup on [localhost]("http://192.168.1.2/backuppc/index.cgi?host=localhost") (pid=1944, share=/etc)
2010-11-21 19:43:42 Backup failed on [localhost]("http://192.168.1.2/backuppc/index.cgi?host=localhost") (Tar exited with error 512 () status)
2010-11-21 19:43:42 Running BackupPC_link [localhost]("http://192.168.1.2/backuppc/index.cgi?host=localhost") (pid=1957)
2010-11-21 19:43:42 Finished [localhost]("http://192.168.1.2/backuppc/index.cgi?host=localhost") (BackupPC_link [localhost]("http://192.168.1.2/backuppc/index.cgi?host=localhost"))

i have tried to make tar run as sudo , some forum posts suggested so although im kinda skeptical of doing so since i fear it could leave me open to a possible attack:shock: 

$Conf{TarClientCmd} = '/usr/bin/sudo $tarPath -c -v -f --ignore-failed-read - -C $shareName+ --totals';

although im not sure thats even close to being right. The backup archive is located at /bkup/backuppc
if anything else is needed just let me know ill post it as soon as possible.
Thanks,
Matt

---

### Post by random_id on 2010-12-04
> **Jersey-Fresh said:**
> I have installed backuppc on Ubuntu server 10.04 amd 64 with the purpose of backing up just the localhost using tar and whenever i try to start a full backup i get 
2010-11-21 19:43:33 User backuppc requested backup of [localhost]("http://192.168.1.2/backuppc/index.cgi?host=localhost") ([localhost]("http://192.168.1.2/backuppc/index.cgi?host=localhost"))
2010-11-21 19:43:34 Started full backup on [localhost]("http://192.168.1.2/backuppc/index.cgi?host=localhost") (pid=1944, share=/etc)
2010-11-21 19:43:42 Backup failed on [localhost]("http://192.168.1.2/backuppc/index.cgi?host=localhost") (Tar exited with error 512 () status)
2010-11-21 19:43:42 Running BackupPC_link [localhost]("http://192.168.1.2/backuppc/index.cgi?host=localhost") (pid=1957)
2010-11-21 19:43:42 Finished [localhost]("http://192.168.1.2/backuppc/index.cgi?host=localhost") (BackupPC_link [localhost]("http://192.168.1.2/backuppc/index.cgi?host=localhost"))

i have tried to make tar run as sudo , some forum posts suggested so although im kinda skeptical of doing so since i fear it could leave me open to a possible attack:shock: 

$Conf{TarClientCmd} = '/usr/bin/sudo $tarPath -c -v -f --ignore-failed-read - -C $shareName+ --totals';

although im not sure thats even close to being right. The backup archive is located at /bkup/backuppc
if anything else is needed just let me know ill post it as soon as possible.
Thanks,
Matt

I had a similar problem and I am hoping this helps.  Try removing the '+' in your Tar command.  I use the following command with success on the localhost as entered into the web config.

sudo $tarPath -c -v -f - -C $shareName --totals

When the + is used on the localhost, it has a hard time handling directory paths with spaces (e.g., "/media/drive/some folder").

---

### Post by Jersey-Fresh on 2010-12-08
> **random_id said:**
> I had a similar problem and I am hoping this helps.  Try removing the '+' in your Tar command.  I use the following command with success on the localhost as entered into the web config.

sudo $tarPath -c -v -f - -C $shareName --totals

When the + is used on the localhost, it has a hard time handling directory paths with spaces (e.g., "/media/drive/some folder").

Thanks for the reply and the suggestion. I entered the command as you suggested although its still failing. It seems as though its still not even  getting started with the backup. Could it be that tar itself is the problem and not the command?

---

### Post by Jersey-Fresh on 2010-12-08
I just ran a manual backup using tart just to have some kind of backup  this is the command i used 
```
tar -cvpzf 12-8-10.tar.gz --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/media --exclude=/dev --exclude=/bkup /
``` it has worked flawlessly so it cannot be tar it has to be something with either the command or backuppc right?

---

### Post by egpetrich on 2010-12-09
I'm not familiar with BackupPC, so I can't say what's going on behind the scenes. I *do* use tar a lot at work, though.
> **Jersey-Fresh said:**
> 
$Conf{TarClientCmd} = '/usr/bin/sudo $tarPath -c -v -f --ignore-failed-read - -C $shareName+ --totals';

This command doesn't look quite correct. When you use the "-f" flag, you need to follow it immediately with the filename that you want. From what I can see, the desired filename is "-", or standard output. With that in mind, I would try using:
```

/usr/bin/sudo $tarPath -c -v -f - --ignore-failed-read -C $shareName+ --totals

```
It's also not clear to me that you can run "sudo" here without problems. "sudo" usually prompts for a password.

The docs for BackupPC are here, if you haven't already seen them:

[http://backuppc.sourceforge.net/faq/BackupPC.html](http://backuppc.sourceforge.net/faq/BackupPC.html)

---

### Post by random_id on 2010-12-11
I am sorry I omitted this before.  You may have to edit 'visudo' to add the backuppc user.  This will allow it to run the tar command without a password, and will allow tar to backup all files, regardless of the permissions.

This link [http://backuppc.sourceforge.net/faq/localhost.html](http://backuppc.sourceforge.net/faq/localhost.html) has information about the line to add in visudo.  I followed the steps in the link, but I still had to remove the '+' from the end of $shareName.

---

### Post by Jersey-Fresh on 2010-12-12
Thanks, I am still having the problem im not sure if its backuppc or not so i created a cron job to back everything up. i know its simple but it works . Thank you to everybody for the help. If i find out a solution ill post it . Thanks again :p

---

### Post by click4851 on 2010-12-22
just for ref, this is my localhost tar command:

TarClientCmd: /usr/bin/sudo $tarPath -c -v -f - -C $shareName+ --totals

I thought I saw a howto of backing up the server If I find it I'll post it.

---

### Post by Jersey-Fresh on 2010-12-22
> **click4851 said:**
> just for ref, this is my localhost tar command:

TarClientCmd: /usr/bin/sudo $tarPath -c -v -f - -C $shareName+ --totals

I thought I saw a howto of backing up the server If I find it I'll post it.
Thank you. That would be great.:P

---

### Post by click4851 on 2010-12-23
I'm sure you saw this from BackupPC's page, but if not here it is:

[http://backuppc.sourceforge.net/faq/localhost.html](http://backuppc.sourceforge.net/faq/localhost.html)

still looking for that howto....

---

### Post by click4851 on 2010-12-23
I DID NOT use this howto, but it does talk about backing up the server specifically. Not all howto's are perfectly written ( let the reader beware ):

[http://www.mantic.org/wiki/Installing_BackupPC](http://www.mantic.org/wiki/Installing_BackupPC)

---

