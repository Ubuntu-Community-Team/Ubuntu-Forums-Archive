---
title: "Administrator blank screen after moving joomla to new server"
date: 2009-12-30
forum: Server Platforms
---

### Post by pmla on 2009-12-30
Ubuntu 9.19 64b and joomla

I have been using joomla for more than one year now, and I have 5 websites. 4 hosted at my home server and 1 serving as intranet at my work.

And this is where I'm having my problem, the intranet server.
I got a newer better box Ubuntu server 9.10 64b to host the intranet joomla webpage and decided to move my website to this newer server. I followed one or two tutorials to accomplish this.
Basically
1. Move the joomla folder from /var/www/joomla to the same folder in the new server
2. Export the joomla database from the old server, and import the database in the new server

No problems, I think :)

The result:
the frontpage is working fine but when I try to login to the administrator backend I only see a blank page (the login page shows and I can insert my login user&pass)

Already google until 4am this problem. Could not fix it. check and rechecked my php5 settings, specially the memory_limit 200M.

But have no idea of what is going on. Anyone had this problem?

---

### Post by hessiess on 2009-12-30
Only thing I can think of is if you missed copying some hidden files (anything starting with a dot)

---

### Post by pmla on 2009-12-30
Thanks... I used the cp command using ssh.

Something like:

#scp -r /var/www/joomla/* user@newbox:/var/www/

will this copy everything?

---

### Post by hessiess on 2009-12-30
Should do.

Have you tried creating a second fresh install of joomla in a different folder/subdomain to see if that has the same problem?

Do both servers run under the same user? if no you may need to chown/chmod the files.

---

### Post by pmla on 2009-12-30
Well I don't want to but I guess I have to ;)

will edit this post in one hour with the results of a fresh installation.
Do you have a php.ini with error reporting activated? if so could you post it here? because a blank screen is very hard to troubleshoot, lol and I can't seem to make my php.ini to store logs in /var/log/
thanks

---

### Post by pmla on 2009-12-30
The new installation went smooth and I can access the administrator backend in this installation.
The one I moved from the old server I just see a blank screen. maybe the php error log would help here.

Any ideas?

---

### Post by hessiess on 2009-12-30
> **pmla said:**
> The new installation went smooth and I can access the administrator backend in this installation.
The one I moved from the old server I just see a blank screen. maybe the php error log would help here.

Any ideas?

Not really, are any of the paths or system/database users different?

Have you tryed asking on the Joomla forum?

---

### Post by pmla on 2009-12-30
Yes have a post in joomla. No help so far. brrrr
Also checked al apache logs, found no problems there.

Just strange a blank screen?! no error messages!guessing the php error reporting would help. Can someone provide a php.ini version5 with error reporting activated?, just that part. Might be some crazy component or module going crazy?

---

### Post by hessiess on 2009-12-30
Just change `display_errors' to `On'

---

