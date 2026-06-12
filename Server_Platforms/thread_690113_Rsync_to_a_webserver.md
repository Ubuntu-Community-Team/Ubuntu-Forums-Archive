---
title: "Rsync to a webserver"
date: 2008-02-07
forum: Server Platforms
---

### Post by wh33t on 2008-02-07
I'm wanting to use Rsync (or whatever is easiest) to back up a webserver.

I was hoping some kind brave soul out there would be willing to share with me how can I make the Back up server copy a directory recursively from the webserver to the back up servers harddrive.

In other words, I don't want the webserver to send the data to the back up machine. I want it so that if I take the back up machine offline the webserver won't be looking for it.

I have already set the back up machine to ssh with out password to the webserver, I just need the rsync command now... 

Anyone wanna take a stab at this?

---

### Post by starfry on 2008-02-07
To the backup server from the web server:

On the backup server do:

rsync -zr user@web-server:/srv/www/htdocs /path/to/backup

where "user" is an account you have at "web-server" which can be an ip address or a host name.

You can then cron this to automate it.

If the web server is running an rsync server daemon then you can set up config in /etc/rsync.conf on that server to define a service, see man rsync.conf. You can then access that service from the backup server machine using an rsync command like

rsync -zr web-server::website-backup-service /path/to/backup

Hope this helps!

---

### Post by MJN on 2008-02-07
You might wish to use the -a flag to ensure ownerships, permissions, timestamps etc are kept (this also implies recursion so no need to separately state it).

Mathew

---

### Post by wh33t on 2008-02-07
Yes I had this going once before but I couldn't remember the command and it was late last night and I couldn't make anything work when I posted this. 

Thank you so much for your replies.

I remember before I used -azr. Thank you very much guys! U rock.

---

### Post by viniciusfs on 2008-02-12
rsnapshot [1] could be great.

[1] [http://www.rsnapshot.org/](http://www.rsnapshot.org/)

---

