---
title: "Easy FTP setup?"
date: 2008-06-25
forum: Server Platforms
---

### Post by skunkbad on 2008-06-25
I just installed 8.04. Router is configured to forward ports 80 and 2222. I'm using ddclient and zoneedit.com. Not much else has been done, but I have verified that everything is working so far. I'd like to be able to use FTP to upload files to my /var/www, but would like to know what is the best way to do this. I want to stay simple and safe, so maybe secure FTP is best?

Whatever is best, I'd appreciate a link to a tutorial to get it set up. I'm CLI challenged, so I need all the help I can get!

---

### Post by skunkbad on 2008-06-25
I figured out that if I use FileZilla version 3 that I can connect with SSH. So I don't even need to install FTP, but I was getting permission errors when trying to upload. I chowned the /var/www directory, and that allowed me to upload, but I'm wondering if I went about doing this the right and safe way.

---

### Post by molotov00 on 2008-06-25
Yeah. You're fine. SSH File Transfers are more secure than FTP in fact.

The only thing I'll add is that if you own /var/www/ then apache (running as user www-data) might have some issues so you should double check that Apache has the permissions it needs. This will only be an issue if you're running scripts that need to edit files.

---

### Post by skunkbad on 2008-06-25
> **molotov00 said:**
> The only thing I'll add is that if you own /var/www/ then apache (running as user www-data) might have some issues so you should double check that Apache has the permissions it needs. This will only be an issue if you're running scripts that need to edit files.

I don't know how to check that. Do I just chown /var/www to a group and add www-data and myself to it?

---

### Post by molotov00 on 2008-06-25
There's no way to "check" right now but it is something that should be in the back of your mind if (in the future) Apache/PHP/etc gives you "permission" errors. For now just make sure that Apache can read the directory, but if you can view pages then that's already the case.

---

### Post by Journeyman on 2008-06-25
you should set the owner of /var/www to your user via chown command.  Then you want to make sure the permissions for it are good for other users to read the files, so you should use chmod a+rx /var/www
and that should take care of it.

---

### Post by skunkbad on 2008-06-25
Yes, the contents of www can be viewed by a browser, both on the local network 192.168.1.XXX, and also by name [www.whatever.com](www.whatever.com), so I believe I am good.

Thanks for the replies.

---

### Post by Journeyman on 2008-06-25
oh and for checking the persmissions use ls -l and that will give you the output showing permissions

---

