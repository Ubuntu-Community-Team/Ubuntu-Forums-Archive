---
title: "Accessing /var/www from SFTP"
date: 2011-06-27
forum: Server Platforms
---

### Post by WiFlag on 2011-06-27
I've searched for this topic, and have seen a lot of posts on it, but none seem to really give a definitive answer. 

I host a couple sites out of /var/www on my server. I do the development work on a computer on the 2nd floor, and the server is in the basement. I used to run slackware on the server, and would just sftp (via Filezilla) into the server as root to upload files. This always made me vaguely uncomfortable, so I'm happy with ubuntu's method of disabling the root user by default. However, this has removed my ability to sftp webpages to /var/www with a normal user account (/var/www belongs to root).

What is the preferred way to do this without enabling root on the server?
My first thought was to change the group that owns /var/www, but in my prior experience that confuses apache (granted, slackware used an older version). I'm wondering if there's a more elegant solution overall.

---

### Post by Dry Lips on 2011-06-27
Do you need one user account able to sftp, or several? If you only need one user
 able to sftp, you could create a user called &#8220;webmaster&#8221; or something similar that owns /var/www.

```
sudo -i 
useradd webmaster -d /var/www 
chown -hR webmaster /var/www 
passwd webmaster 
exit
 
```

---

### Post by gdonwallace on 2011-06-27
Another option is to use scp (ssh cp)  It creates an encrypted connection between your computer and the computer you want to copy the file too and uses SSH for the connection.  You have to have ssh running on both machines and a directory that you have read/write access too on the target machine.

---

### Post by CharlesA on 2011-06-27
sftp and scp are practically the same for all intents and purposes - They both use ssh to make the connection and to send files via ssh.

+1 to creating a new user.

---

### Post by WiFlag on 2011-06-28
I like the idea of a webmaster user, but I was concerned about having apache not own the /var/www folders. However, it seems that mine is already root/root, so apache must not care.
I made a webmaster user, and it seems to still work, thanks.

---

### Post by CharlesA on 2011-06-28
> **WiFlag said:**
> I like the idea of a webmaster user, but I was concerned about having apache not own the /var/www folders. However, it seems that mine is already root/root, so apache must not care.
I made a webmaster user, and it seems to still work, thanks.

I checked my /var/www folder and it's owned by root with 755 permissions (rwxr-x-r-x).

If you don't want to give global read-only access, you can always change the owner to "webmaster" and add "www-data" to the "webmaster" group and go from there.

---

### Post by Lars Noodén on 2011-06-28
> **CharlesA said:**
> ...and add "www-data" to the "webmaster" group and go from there.

Be careful that www-data is not inadvertently given write access to any of the directories.

---

### Post by CharlesA on 2011-06-29
> **Lars Noodén said:**
> Be careful that www-data is not inadvertently given write access to any of the directories.

Good point there.

I meant add it to the webmaster group and make sure that the permissions were just r-x. That's the default isn't it?

---

### Post by WiFlag on 2011-06-29
It was previously owned by root:root, so I just changed it to be chown webmaster, but left the group as root - I only need one webmaster.

Permissions are 755 by default, so it was relying on the global r-x permission before.

---

### Post by Lars Noodén on 2011-06-29
> **CharlesA said:**
> Good point there.

I meant add it to the webmaster group and make sure that the permissions were just r-x. That's the default isn't it?

The default is that the directory is owned by root, with a group of root and with permissions set to 755.  

I'm wondering if it might not be a good idea for the web server packages to include a group "webmasters" to reduce the likelihood that www-data gets used by mistake.

---

### Post by CharlesA on 2011-06-29
> **Lars Noodén said:**
> The default is that the directory is owned by root, with a group of root and with permissions set to 755.  

I'm wondering if it might not be a good idea for the web server packages to include a group "webmasters" to reduce the likelihood that www-data gets used by mistake.

Thanks for checking on that. :)

I agreed that adding a new group would be a good idea. That way you don't potentially open yourself up to bad things.

---

