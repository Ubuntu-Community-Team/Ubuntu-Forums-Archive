---
title: "Network Backup server"
date: 2008-10-31
forum: Server Platforms
---

### Post by chemicall on 2008-10-31
Howdy all,

I'm wondering, are any network backup softwares available that know what is new on my network and back it up without the old data on the backup server?
As I want to backup each couple weeks, and have them autoburned to DVD, and the old data deleted from HD. 

anyone ever do anything like this?
 
Thanks!

---

### Post by Lars Noodén on 2008-10-31
You could make your own with cron, rsync (or dump/restore, or tar) and ssh.

Here are some simple examples which can be used in a script:
 * [http://ultra.ap.krakow.pl/~bar/DOC/ssh_backup.html](http://ultra.ap.krakow.pl/~bar/DOC/ssh_backup.html)

You'll want to use keys with ssh.  Be extra careful to restrict the commands that can be run.  See
 * [http://linux.die.net/man/5/sshd_config](http://linux.die.net/man/5/sshd_config)

If you do keep a passphrase, you'll probably want to use ssh-agent to avoid having to do the backups manually:
 * [http://linux.die.net/man/1/ssh-agent](http://linux.die.net/man/1/ssh-agent)
 * [http://linux.die.net/man/1/ssh-add](http://linux.die.net/man/1/ssh-add)

Once the script is going along nicely, you can put it into a cron job.

---

### Post by Lars Noodén on 2008-10-31
Bacula might be another option:

[https://help.ubuntu.com/community/Bacula](https://help.ubuntu.com/community/Bacula)

---

