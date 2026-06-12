---
title: "Create user &quot;rsync&quot; to login and sync from remote machines"
date: 2009-07-19
forum: Security
---

### Post by nerr on 2009-07-19
Hey everyone, I'm fairly new to Linux but I've created a fairly solid Ubuntu Server 9.04 setup so far, and I'm always up for learning something new.  I'm at a point where I'm puzzled.  I'd like to create a special user on my server (rsync) for running rsync jobs from client machines, which I would like to have connect to my machine.  The clients are Windows machines, otherwise I would probably just connect from server-to-client, but in this case, I get the feeling client-to-server is a better approach.

I would like to be able to use the following example command to login the user rsync via SSH, and then transfer files to my server.

rsync -avz --progress --inplace --del --exclude desktop.ini --exclude thumbs.db --rsh='ssh -i id_rsa -pXXXXX' /cygdrive/f/music/ [EMAIL="rsync@mydomain.com"]rsync@mydomain.com[/EMAIL]:/srv/media/music/

The problem is that I need the user rsync to have a shell besides /bin/false to log in and create the SSH connection.  Is there any way around this problem, so I can prevent anything from being done with this account besides syncing data?  It will use an RSA key to automatically log in at a given time of day, so security is quite important.

Thanks for your help.

---

### Post by The Tronyx on 2009-07-19
If you are concerned about the shell access, you can either use rbash or scpsftprsynconly.

[http://www.freebsdwiki.net/index.php/SSH:_Limiting_to_SCP_or_Rsync_only](http://www.freebsdwiki.net/index.php/SSH:_Limiting_to_SCP_or_Rsync_only)

---

### Post by koenn on 2009-07-20
if you use ssh as transport for rsync, i think the user will always need a shell - in part because ssh is actually 'use a remote shell", partially because rsync needs to execute commands such as chmod, chown -, ln, ... in stead of actually copying links,  or in stead of copying files when all that needs to be done is sync the ownership or permissions on the remote copy. 

you could possibly enable and disable this account through a cron job with a timing that matches your rsync operations, but this could be clumsy and error prone. 

you could also run rsync as a daemon on the server. In this mode, rsync works as a client/server application. The clients use tcp for transport (in stead of ssh), and the daemon does what needs done under its own account.

---

### Post by nerr on 2009-07-20
I wasn't able to get scpsftprsyncnonly working last night, so let's see here...

koenn, how might I go about implementing your solution of running rsync in daemon mode, and allowing it to handle tasks itself?  I suppose transporting data over TCP wouldn't be a real dealbreaker since these machines I want to backup are all on my LAN anyway.  I could always send data using my laptop via SFTP if I really need to, since that'll be the only machine I backup to the server that won't be on this LAN most of the time.  I'll do some more searching on Google, but if you have any sort of definitive guide, then by all means, please share!  Thank you. :)

---

### Post by koenn on 2009-07-20
[http://sunsite.dk/info/guides/rsync/rsync-mirroring02.html#l4](http://sunsite.dk/info/guides/rsync/rsync-mirroring02.html#l4)
[http://users.telenet.be/mydotcom/howto/linux/rsyncservers.htm](http://users.telenet.be/mydotcom/howto/linux/rsyncservers.htm) (simple quick-start)
or man rsync and man 5 rsync.conf

basically all  you need to do is create /etc/rsync.conf, there is none by default. also check that there's an init script for rsync, there probably is but it doesn't do anything as long as rsync.conf doesn't exist. it runs 'rsync --daemon'.

rsync.conf is a lot like samba.conf : you set some globale options, and then you define modules (+/- like shares in samba)


on the clients, you call rsync with the module name, and double ::, 
like
so:
```

rsync /path/to/src  server::module_name[/subdir]

```


Don't know if rsync uses any encryption when you call it this way, you may want to look that up. You might want to try tunneling it through ssh 
(i.e. using the 'portforward' options of ssh)

---

### Post by nerr on 2009-07-20
Okay, I give up.  I've been screwing around with rsyncd for nearly four hours now, and it's still giving me all sorts of problems.  I think I'm going to just speak to my family in regards to security with this home server, set a password that they all know, and educate them on how to run the backup script.

Thanks for the help anyway, koenn.  I really appreciate your help with those links and such, but I suppose running this guy as a daemon just isn't for me.

---

### Post by Dave_Connor on 2009-07-21
You can run a cron script that runs once a week for backup purpose with ssh with key auth.

---

