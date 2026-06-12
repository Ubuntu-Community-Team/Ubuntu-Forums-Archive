---
title: "Sudo 'no password' with SSH"
date: 2012-04-23
forum: Server Platforms
---

### Post by Simoo on 2012-04-23
Hi, I'm wanting to automate an rsync over ssh command between two ubuntu server boxes.

I have exchanged ssh keys and the command below works fine:

```
backup-user@hostname:~$ rsync -anve ssh /home backup-user@192.168.0.100:/home/storage/backup/files/
```

But I'd like the backup-user to be able to 'read' everything on the server when using the rsync command so I added the following to the sudoers file:

```
backup-user     ALL=NOPASSWD:   /usr/bin/rsync
```

then ran the same command but with 'sudo' in front (hoping rsync would then be able to read everything I'm trying to backup):

```
backup-user@hostname:~$ sudo rsync -anve ssh /home backup-user@192.168.0.100:/home/storage/backup/files/
```

The problem is that when I run the command with 'sudo' in front I get a password prompt:

```
backup-user@192.168.0.96's password:
```

Could someone explain why this might be?

Thanks,

---

### Post by papibe on 2012-04-23
Hi Simoo.

I think what is going on is this: since you're sudoing the default key is being looked at ~root/ instead of your user home.

You can explicitly point to an specific key using the option -i on the ssh part of the rsync.

For instance:
```
sudo rsync -anv **-e "ssh -i /home/backup-user/.ssh/id_rsa"**  /home backup-user@192.168.0.100:/home/storage/backup/files/
```
Adjust the command accordingly if you saved your key with another name, or if you used dsa instead of rsa.

I hope that helps, and tell us how it goes.
Regards.

---

### Post by hawkmage on 2012-04-23
Another thing is sudo is picky about the command, since you put "/usr/bin/rsync" as the allowed command in the sudoers file then you will need to use the fully qualified path in the invocation of of rsync using sudo.

---

### Post by Simoo on 2012-04-24
Brilliant, thanks for the quick response guys, really appreciate it, Papibe using the command you suggested fixed it.

I seem to have got away with the difference between '/usr/bin/rsync' and 'rsync' this time but I'll make sure they're the same for good practice anyway.

Thanks again

---

