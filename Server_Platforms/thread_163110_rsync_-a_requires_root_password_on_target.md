---
title: "rsync -a requires root password on target"
date: 2006-04-20
forum: Server Platforms
---

### Post by aylwyn on 2006-04-20
Just noticed that in order to correctly run remote rsync backups using the archive (-a) option, which preserves ownerships and permissions, you need to run as root on the target machine. I don't know of a way to get rsync to sudo on the target... does anyone else?

So in other words, if the target machine is an Ubuntu box (as is the case for me), you need to run
[FONT="Courier New"]target-host> sudo passwd[/FONT]
and specify a root password on that machine first, so that an rsync command such as
[FONT="Courier New"]source-host> rsync -a $SOURCEDIR root@target-host:$TARGETDIR[/FONT]
will work correctly.

---

### Post by cgjones on 2006-04-20
Try setting the SUID and SGID on the rsync binary. I'm not sure if/how this will affect the permissions on the files being rsync'd, but it will force rsync to run as root. Run the following command on the target host. I think rsync will be in /usr/bin, but I'm testing this on Fedora Core, so make sure where rsync is located.

```
sudo chmod ug+s /usr/bin/rsync
```

And you might want to check out this link. It explains the above process in more detail.
[http://www.linuxforums.org/security/file_permissions.html](http://www.linuxforums.org/security/file_permissions.html)

---

### Post by tageiru on 2006-04-20
[QUOTE=aylwyn]Just noticed that in order to correctly run remote rsync backups using the archive (-a) option, which preserves ownerships and permissions, you need to run as root on the target machine. I don't know of a way to get rsync to sudo on the target... does anyone else?[/QUOTE]
Thats not true, -a works without being root.

---

### Post by nagilum on 2006-04-20
[QUOTE=aylwyn]Just noticed that in order to correctly run remote rsync backups using the archive (-a) option, which preserves ownerships and permissions, you need to run as root on the target machine. I don't know of a way to get rsync to sudo on the target... does anyone else?[/QUOTE]
Does the user you use to call rsync own all the files you try to copy? Since you can only create files belonging to yourself superuser privileges are necessary to recreate files not owned by yourself. Just an idea...

---

### Post by aylwyn on 2006-04-20
[QUOTE=tageiru]Thats not true, -a works without being root.[/QUOTE]

Not according to [FONT="Courier New"]man rsync[/FONT].

And whenever I've tried
```
rsync -a $SOURCEDIR ruser@target-host:$TARGETDIR
```
all files in the resulting archive have been owned by [FONT="Courier New"]ruser[/FONT], not by their correct users or numeric uid's.

Remember I'm talking about *remote* rsync tasks - not local ones run using sudo.

---

### Post by aylwyn on 2006-04-20
[QUOTE=nagilum]Does the user you use to call rsync own all the files you try to copy? Since you can only create files belonging to yourself superuser privileges are necessary to recreate files not owned by yourself. Just an idea...[/QUOTE]

well yes -  If rsync logs in to the remote system as a non-root user then all the files it creates there are owned by that user. This is not the desired behaviour when creating a remote backup archive. The problem is that in Ubuntu there is no superuser login by default, and I'm not aware of any way (apart from setting the binary SUID and SGID as suggested by cgjones) of making it run with superuser privileges without specifying root as the login user.

But maybe I've missed something obvious - which is why I posted here..

Here's a link to when
[someone else had a related problem in these forums before]("http://ubuntuforums.org/showthread.php?t=38578&highlight=rsync+owner")

---

### Post by nagilum on 2006-04-20
Well, it doesn't really matter if the UID on the remote machine doesn't match the local one of you use the same mechanism (i.e. rsync -a) to restore the backup.
I still don't understand why you should need superuser privileges to use rsync -a. For me it works perfectly fine, local and remote. Can you cite the part of the man-page that sais otherwise? I can't find it...

---

### Post by tageiru on 2006-04-20
[QUOTE=aylwyn]Not according to [FONT="Courier New"]man rsync[/FONT].

And whenever I've tried
```
rsync -a $SOURCEDIR ruser@target-host:$TARGETDIR
```
all files in the resulting archive have been owned by [FONT="Courier New"]ruser[/FONT], not by their correct users or numeric uid's.

Remember I'm talking about *remote* rsync tasks - not local ones run using sudo.[/QUOTE]
Ah right, I assumed that the user had the same name on both machines.
But does it matter? I would not consider the specific user/uid as useful metadata.
I can not find the relevant section in man rsync, could you please quote?

---

### Post by aylwyn on 2006-04-20
[QUOTE=nagilum]I still don't understand why you should need superuser privileges to use rsync -a. For me it works perfectly fine, local and remote. Can you cite the part of the man-page that sais otherwise? I can't find it...[/QUOTE]

[QUOTE=tageiru]I can not find the relevant section in man rsync, could you please quote?[/QUOTE]

Sure.

Line 330
        -a, --archive               archive mode, equivalent to -rlptgoD

Line 347
        -o, --owner                 preserve owner (root only)

And line 671:
  -o, --owner
              This option causes rsync to set the  owner  of  the  destination
              file  to  be the same as the source file.  On most systems, only
              the super-user can set file ownership.

Does the behaviour I described above really not happen for you? I mean when you rsync a file to a remote machine using the -a option, is that file not always owned by the remote user specified in the rsync command (when that user is not root)? And if it is, how are you able to recover the original ownerships when restoring?

---

### Post by nagilum on 2006-04-21
[QUOTE=aylwyn]Line 347
        -o, --owner                 preserve owner (root only)

And line 671:
  -o, --owner
              This option causes rsync to set the  owner  of  the  destination
              file  to  be the same as the source file.  On most systems, only
              the super-user can set file ownership.[/quote]
Ah, thanks.

[QUOTE=aylwyn]Does the behaviour I described above really not happen for you? I mean when you rsync a file to a remote machine using the -a option, is that file not always owned by the remote user specified in the rsync command (when that user is not root)? And if it is, how are you able to recover the original ownerships when restoring?[/QUOTE]
Of course the files are owned by the remote user, not the local one. But as I said, it doesn't matter as permissions etc. are actually maintained. To restore the files you can do
```

rsync -a ruser@target-host:$TARGETDIR $SOURCEDIR

```
Just reverse the two arguments, then the files will again belong to your local user and everything should be exactly as before the backup.

---

### Post by LordHunter317 on 2006-04-21
[QUOTE=cgjones]
```
sudo chmod ug+s /usr/bin/rsync
```[/quote]***NO, NO, NO.  This is as bad, if not worse than, chmod 777.  Never, ever, ever suggest this.*** 

[quote=aylwyn]The problem is that in Ubuntu there is no superuser login by default,[/quote]Yes, there is, it's just not interactive.  It can still run batch jobs and processes can elevate themeslves to root through the proper mechanisms.

> and I'm not aware of any way (apart from setting the binary SUID and SGID as suggested by cgjones) of making it run with superuser privileges without specifying root as the login user.There are several ways.  If you'd read the documentation more closely you'd learn one.  Alternatively, 'rsync sudo' yields a correct result in the second answer.

[quote=nailgum]I still don't understand why you should need superuser privileges to use rsync -a. [/quote]You only do if you're trying to backup files with different owners.  Otherwise, you don't.  Same applies to every archiving program out there, just about.

The correct way to do this is complicated, but does work.  Here, "server" means whatever is receiving the backups and client means the side sending the backups.[list=1][*]Create a user on the remote side to run the backup jobs.  backup is a fine name, or even rsync.  Give it a home directory, but no password.[*]Create a *passwordless* SSH keypair for this user.  Do this on the local machine, as whatever user will kick off the job.  Put the public key in ~/.ssh/authorized_keys on the remote box, with the following restrictions added:```
no-port-forwarding,no-agent-forwarding,no-pty,no-X11-forwarding
```And perhaps a from="192.0.0.1" where that is your local IP or DNS entry.  The sshd(8) manpage describes the restictions in more detail.[*]Add the following entry to /etc/sudoers on the remote side:```
backup ALL = NOPASSWD: /usr/bin/rsync
```You could change the ALL host designation to just that host, if you prefer.[*]Run rsync on the local side like so:```
rsync -e 'ssh -l  backup -i /home/example/.ssh/id_dsa_backup' --rsync-path='sudo rsync' -a /home/backup remote:/home/backup
```[/list]Done.  Modify as appropriate.  Not tested recently, but I'm fairly confident it will work.

---

### Post by aylwyn on 2006-04-21
[QUOTE=LordHunter317]

There are several ways.  If you'd read the documentation more closely you'd learn one.  Alternatively, 'rsync sudo' yields a correct result in the second answer.[/QUOTE]

Not sure I understand the tone of that, or the content, but never mind, your subsequent suggested solution using a passphraseless ssh login is useful. Thanks for that.

I currently use a similar method for automated backups, but your method is nicer because the passphraseless login is restricted to the remote host.

I would say that for a one-off manual snapshot, the workaround I originally suggested (adding an interactive login for root on the remote host) is simpler, and  is therefore useful for some purposes.

---

### Post by aylwyn on 2006-04-21
[QUOTE=nagilum]

Just reverse the two arguments, then the files will again belong to your local user and everything should be exactly as before the backup.[/QUOTE]

Ah now I see the confusion. You're assuming all the files belong to a single user on the local system;  I'm talking about a backup including files belonging to multiple users. These ownerships will not be preserved if the remote process doesn't have superuser permissions.

---

### Post by LordHunter317 on 2006-04-21
[QUOTE=aylwyn]Not sure I understand the tone of that, or the content, but never mind,[/quote]You're lambasting people for not reading the documentation when it's apparent you haven't sufficently read it or researched your question yourself.  

> I would say that for a one-off manual snapshot, the workaround I originally suggested (adding an interactive login for root on the remote host) is simpler, and  is therefore useful for some purposes.It's infinitely less secure and pointless.  The correct way really isn't that much harder, given all you have to do in Ubuntu to enable root, enable root SSH, and start the process.

---

### Post by aylwyn on 2006-04-21
[QUOTE=LordHunter317]You're lambasting people for not reading the documentation when it's apparent you haven't sufficently read it or researched your question yourself. [/QUOTE]

That's ridiculous, no-one was 'lambasting' anyone; you completely misread the tone of thread. We're all friends here, remember?

---

### Post by nagilum on 2006-04-22
[QUOTE=aylwyn]Ah now I see the confusion. You're assuming all the files belong to a single user on the local system;  I'm talking about a backup including files belonging to multiple users. These ownerships will not be preserved if the remote process doesn't have superuser permissions.[/QUOTE]
Ah, I see. You never mentioned this little fact before.

---

