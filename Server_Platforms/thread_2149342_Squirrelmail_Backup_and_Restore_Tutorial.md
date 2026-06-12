---
title: "Squirrelmail Backup and Restore Tutorial?"
date: 2013-05-28
forum: Server Platforms
---

### Post by lingpanda on 2013-05-28
So I followed this tutorial with success some time back. [http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-nginx-bind-dovecot-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-nginx-bind-dovecot-ispconfig-3) How do I create a backup of squirrelmail data and restore? The only info I have been able to find is posted here [http://www.howtoforge.com/forums/showthread.php?t=61116](http://www.howtoforge.com/forums/showthread.php?t=61116) Is it really that simple to back up all data? Thanks for any and all assistance.

---

### Post by SeijiSensei on 2013-05-29
The really important data are the mailboxes.  Usually the inboxes are in /var/mail and any personal folders in the users' home directories.  SquirrelMail itself resides in /usr/share/squirrelmail.  Only the config directory is unique to your site.

---

### Post by lingpanda on 2013-07-15
> **SeijiSensei said:**
> The really important data are the mailboxes.  Usually the inboxes are in /var/mail and any personal folders in the users' home directories.  SquirrelMail itself resides in /usr/share/squirrelmail.  Only the config directory is unique to your site.

So I located the mail in /var/vmail/mydomain.com. I do not see any user home directories however. I do see additional data here /var/lib/squirrelmail/data/tuser@mydomain.com.abook and /var/lib/squirrelmail/data/tuser@mydomain.com.pref. Does this seem correct? Thanks.

---

### Post by SeijiSensei on 2013-07-16
Those files are the address books and preferences for each user that SquirrelMail maintains.  They don't contain any messages.

The mail itself might be delivered to the users' home directories.  Implementations vary depending on the type of delivery system you use, for instance, whether the mail is stored in mbox or Maildir folders.  Take a look at /home/username and see if a mail or Maildir exists.

---

### Post by lingpanda on 2013-07-16
> **SeijiSensei said:**
> Those files are the address books and preferences for each user that SquirrelMail maintains.  They don't contain any messages.

The mail itself might be delivered to the users' home directories.  Implementations vary depending on the type of delivery system you use, for instance, whether the mail is stored in mbox or Maildir folders.  Take a look at /home/username and see if a mail or Maildir exists.

No luck in the home directories but I do see mail folders in

 ```
/var/vmail/mydomain.com/tuser/Maildir/.Test Folder/maildirfolder
```

This must be it?

---

### Post by nerdtron on 2013-07-17
Look inside that folder or look for Maildir/ folder. Also, dig in deeper until you see some files named like this 1338794060.17775.mail.mydomain.net,S=1767:2,
That is an actual email filename of a user. You can even view it in the text editor and see the contents. This way, you'll be sure that you are going to copy the correct mail folder.

---

### Post by lingpanda on 2013-07-18
> **nerdtron said:**
> Look inside that folder or look for Maildir/ folder. Also, dig in deeper until you see some files named like this 1338794060.17775.mail.mydomain.net,S=1767:2,
That is an actual email filename of a user. You can even view it in the text editor and see the contents. This way, you'll be sure that you are going to copy the correct mail folder.

Thank you nerdtron and Seiji. I found data here:



```
/var/vmail/mydomain.com/tuser/Maildir/cur#
```

Will a simple copy of all folders/subfolders be enough to restore? 

```
cp -r /var/vmail/mydomain.com/
```

or this?

```
cp -r -p /var/vmail/mydomain.com/
```

---

### Post by nerdtron on 2013-07-18
cp command?
Is the backup drive and the destination drive on the same computer?

Also, remember the syntax
```
cp -r -p [source] [destination]
```
You may not need the -p option if the folder is already created but it's good to have.

In my case, as with recent my migration (from Squirrelmail to iRedMail Roundcube) it's better to use the rsync command. It works even on separate computers on the network (one is the old mail, and the other is the mail server).

BUT if you are just doing a one time backup and restore, it would be a lot better if you use a zip (or tar) the whole folder. This way, you just unzip the file when you want to restore the emails. The advantage of this it that it preserves file ownership and permissions and saves a lot of hard drive space. I strongly suggest this way since permission on email files are important.

---

### Post by lingpanda on 2013-07-18
nerdtron I'm going to be using rsync but wasn't sure how to express the command options with it. What's your rsync command?

---

### Post by nerdtron on 2013-07-19
This commmand is issued on the receiving server. Meaning, the copied files will come from remote server.
```
rsync -avrh --progress  --delete-excluded --delete  root@192.x.x.x:/remote/mail/path/to/Maildirs /local/destination/path/Maildir/ 
```

-avrh - a means to copy attributes, permissions and ownerships, v for verbose to see what is currently copying, r for recursive to copy the inner diretories, and h for human readable format (the file sizes)

--progress - to show the progress of the whole process

--delete-excluded and --delete - I used this since I used rsync a lot of times, and the data from the sender changes, some are deleted so I added this to delete the non-existent files from the sender but the were present on the receiver.

root@192.x.x.x:/path/ - the sender (or rather the SOURCE location), or the old email server and the path to the location you want to copy.

/local/destination/ - the path on the receiving machine (the DESTINATION) where the copied files will be located.

You're rsync command may vary, but this will do the trick if you want to copy from one server to another. If you will run rsync just once, do not include --delete-excluded and --delete in the command.
You can also check the manual for rsync (I read it carefully and tested some commands before doing the real copy).
```
man rsync
```

Keep us updated on your progress.

---

### Post by lingpanda on 2013-07-19
nerdtron,

Thanks for the detailed explanation of the rsync commands. I used it in the past with some success to test file transfer from server to server. I will attempt the back up and then eventually restore. Will keep thread posted.

---

### Post by lingpanda on 2013-07-31
nerdtron do I need to kill any processes before running the rsync command? I needed Ubuntu Forums to come back up so I could reference the commands. My target date is this Sunday.

---

### Post by nerdtron on 2013-08-01
Here's how i did it to minimize the downtime on our mail server migration. Execute rsync on the live system with running processes. I t won't affect much of the performance. Also, it will copy the bulk of all emails which could take several minutes.
After that, make the 2 servers offline, the old and the new servers. This will cause email services to stop so please send a notification to them that you'll do a server maintenance.
Now do the rsync again to copy the extra emails that were left out while you were doing the first rsync. You'll do this to make sure you copied everything. This will only take a few minutes (or seconds) depending on the amount of new data that needs to be copied.
Connect the new server to the network to receive the new mails.

OR if you are just going to do a backup and not migration, no need to kill any processes. Just execute the rsync command and it'll do the backup for you.

---

### Post by lingpanda on 2013-08-02
> **nerdtron said:**
> Here's how i did it to minimize the downtime on our mail server migration. Execute rsync on the live system with running processes. I t won't affect much of the performance. Also, it will copy the bulk of all emails which could take several minutes.
After that, make the 2 servers offline, the old and the new servers. This will cause email services to stop so please send a notification to them that you'll do a server maintenance.
Now do the rsync again to copy the extra emails that were left out while you were doing the first rsync. You'll do this to make sure you copied everything. This will only take a few minutes (or seconds) depending on the amount of new data that needs to be copied.
Connect the new server to the network to receive the new mails.

OR if you are just going to do a backup and not migration, no need to kill any processes. Just execute the rsync command and it'll do the backup for you.

I've successfully backed up the data. Or so it appears. If I am to understand correctly. The --delete-excluded and --delete switch will make a 1 to 1 copy? meaning if a file is present on the backup but not on the source. It will delete the backup file?

Now how will I go about setting up a cron job/script to automate this? Thanks again for all the help.

---

### Post by nerdtron on 2013-08-02
> **lingpanda said:**
>  The --delete-excluded and --delete switch will make a 1 to 1 copy? meaning if a file is present on the backup but not on the source. It will delete the backup file?

Now how will I go about setting up a cron job/script to automate this? Thanks again for all the help.

Yes. You are correct on the --delete and --delete-excluded switch. If you finished rsync today and then some files where deleted on the source, the next day you rsync, the files on the backup will also be deleted.

I haven't tried this yet but I think it should work. Please make sure that you can login without via ssh without password to the remote server from the local server you are going to execute the rsync command.
Generate keys and don't enter any password. Then copy the keys to the remote server.
```
ssh-keygen
ssh-copy-id user@remoteserver
```
Try to ssh to the remote server and you should not be asked for a password.

Create an empty file and make it executable. Name it rsync.sh and put it in /home/username/rsync.sh
Put in this file you rsync command.
Edit the crontab.
```
crontab -e
```
Add a line like this.
```
@daily /home/username/rsync.sh
```

If you want more control over the crontab schedule, read [here]("http://www.debianhelp.co.uk/schedulejobs.htm") and [here]("http://www.jveweb.net/en/archives/2011/02/using-rsync-and-cron-to-automate-incremental-backups.html").

---

### Post by lingpanda on 2013-08-12
nerdtron I believe I have everything set and ready to go. My crontab options for this are "* 6 * * 0". My understanding is this will run @6am every Sunday? If correct I'm good to go and I thank you for your assistance.

---

### Post by Cheesemill on 2013-08-12
> **lingpanda said:**
> My crontab options for this are "* 6 * * 0". My understanding is this will run @6am every Sunday?

No.

You need...
```
0 6 * * 0
```

What you have will run your crontab every minute during the hour of 6AM on a Sunday.

---

### Post by SeijiSensei on 2013-08-13
> **nerdtron said:**
> Create an empty file and make it executable. Name it rsync.sh and put it in /home/username/rsync.sh
Put in this file you rsync command.
Edit the crontab.
```
crontab -e
```
Add a line like this.
```
@daily /home/username/rsync.sh
```

Any scripts that need to be run with root privileges like comprehensive backups should be referenced in crontabs owned by root, not by an ordinary user.  The simplest solution is to put the scripts, or symlinks to them, in the appropriate /etc/cron.* directories.  To run a job once a week, put the script in /etc/cron.weekly.  The daily and weekly scripts are run just before 7 am by default.  To change these times, edit (as root with sudo) the file /etc/crontab and change the entries appropriately.

---

### Post by lingpanda on 2013-08-14
> **Cheesemill said:**
> No.

You need...
```
0 6 * * 0
```

What you have will run your crontab every minute during the hour of 6AM on a Sunday.

Cheesemill thanks for the clarification.

---

### Post by lingpanda on 2013-08-14
> **SeijiSensei said:**
> Any scripts that need to be run with root privileges like comprehensive backups should be referenced in crontabs owned by root, not by an ordinary user.  The simplest solution is to put the scripts, or symlinks to them, in the appropriate /etc/cron.* directories.  To run a job once a week, put the script in /etc/cron.weekly.  The daily and weekly scripts are run just before 7 am by default.  To change these times, edit (as root with sudo) the file /etc/crontab and change the entries appropriately.

SeijiSensei I did make sure to have root run the script. Thanks for the clarification as well.

---

