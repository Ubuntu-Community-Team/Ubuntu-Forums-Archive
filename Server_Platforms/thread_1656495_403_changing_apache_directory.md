---
title: "403 changing apache directory"
date: 2010-12-31
forum: Server Platforms
---

### Post by cosine_omerta on 2010-12-31
I have read a hundred posts, and tried a hundred solutions. I can't get any of them to work for me. Thanks in advance for any suggestions.

I have ubuntu 10.10 running as a server, with the LAMP and SSH installed. I want to move the default folder for web pages from /var/www to /home/user/public_html

I have gone through all of the steps that are listed in multiple areas. Copy the default, change the DocumentRoot, change the Directory, a2ensite, reload, etc etc.

I have changed permissions of the /home/user folder so that all levels can be executed, as well as the /public_html etc, but I still get a 403 forbidden error if I am not logged onto the server. If I am logged onto the server then it works fine.

What am I missing?

---

### Post by cosine_omerta on 2010-12-31
How do I see if apache has permission to /home/user?

---

### Post by CharlesA on 2010-12-31
Have you tried setting up a virtualhost? That's what I did for mine:

```
charles@lucid:~$ cat /etc/apache2/httpd.conf 
<VirtualHost *:80>
DocumentRoot /home/charles/site/
</VirtualHost>

```

Apache should have access if your home directory is not encrypted and the permissions are set to 755 - rwxr-xr-x

---

### Post by cosine_omerta on 2010-12-31
Encrypted home directory! Is this what it asks to encrypt during setup? Because I said yes. How would I check this, or disable it, or whatever is necessary for apache to use it?

---

### Post by CharlesA on 2010-12-31
Yep. As far as I know the only way to get rid of an encrypted home directory is to reinstall.

However, you can create a folder in /var/www/ and chance the owner and group so that you have write access to that folder.

If you don't want to reinstall, that would probably be the easiest to do.

---

### Post by cosine_omerta on 2010-12-31
So if I wanted to have multiple users with webpages in their /home/user directory, it would be best to reinstall and not encrypt the home directory?

---

### Post by CharlesA on 2010-12-31
Probably.

Are you giving each user their own virtualhost?

---

### Post by cosine_omerta on 2010-12-31
That was the plan. Then I could enable and disable as necessary.

---

### Post by CharlesA on 2010-12-31
You could always give them a folder in /var/www, but I think confining them to their home directory is a better idea. :)

---

### Post by cosine_omerta on 2010-12-31
That was my thought. Thanks so much! I've been wrestling with this for days.

---

