---
title: "Cannot change file permissions on server"
date: 2010-08-25
forum: Server Platforms
---

### Post by gewitty on 2010-08-25
I'm working on a remote Ubuntu 9.10 server, which is accessed via VPN. I installed Joomla, but had difficulty uploading new components, which I traced to a file permissions problem.

I used FileZilla to FTP onto the site and tried to make the chmod changes I needed, but the commands kept failing. Eventually, I contacted the sys admin and told him I thought that there was an ownership problem with the directories. He checked and told me that I was logging in with exactly the same user name and password that he was using (it's not a live system currently) and that he could make chmod changes without any problems. Because all my attempts were still failing, he eventually did the following:

chown -R administrator:administrator /var/www

/var/www is where all the Joomla files are stored and Administrator is the user name.

Now I find that when I run a chmod command in FileZilla, the server reports that it worked (see below):

Status:	Connected
Status:	Retrieving directory listing...
Command:	CWD /etc
Response:	250 Directory successfully changed.
Command:	PWD
Response:	257 "/etc"
Command:	TYPE I
Response:	200 Switching to Binary mode.
Command:	PASV
Response:	227 Entering Passive Mode (192,168,111,7,181,61).
Command:	LIST
Response:	150 Here comes the directory listing.
Response:	226 Directory send OK.
Status:	Directory listing successful
Status:	Set permissions of '/var/www/tmp' to '755'
Command:	CWD /var/www
Response:	250 Directory successfully changed.
Command:	SITE CHMOD 755 tmp
Response:	200 SITE CHMOD command ok.

However, if I go back and check the tmp folder permissions, I find that they are still set to 777.

This still looks like an ownership problem to me, but I don't understand why the server seems to think that the chmod changes are working, when they aren't.

---

### Post by quixote on 2010-08-27
I believe /tmp is 777 by default and is supposed to be 777.  Check the permissions on your /var/www directories.  If they're 777, there's a problem, but they probably won't be.  (i.e. when you checked "tmp" are you sure you weren't looking at the top-level tmp?  And, possibly, the same default applies to /var/www/tmp??)

---

### Post by gewitty on 2010-08-28
The sys admin ran this command: 

chown -R administrator:administrator /var/www

Which immediately allowed me to change the permissions of all files and folders in the /var/www directory when using the file manager in WebMin. However, I still couldn't make changes using FileZilla.

The strange thing is that the following day, I found that I _was_ able to make changes using FileZilla. Niether I nor the sys admin can explain why this happened, but at least everything is working now.

---

### Post by quixote on 2010-08-28
Always a bit unsettling when things work for no reason.  Still, it's better than them not working for no reason :D.  Glad to hear it sorted itself.

---

### Post by Lars Noodén on 2010-08-28
Be sure that the directories under /var/www do not allow write access to 'other', the directories should be 775 or 755  Otherwise, it is likely that random visitors might be able to leave their calling card...

---

