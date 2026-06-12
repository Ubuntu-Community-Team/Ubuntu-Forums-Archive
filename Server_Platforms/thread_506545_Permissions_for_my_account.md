---
title: "Permissions for my account"
date: 2007-07-21
forum: Server Platforms
---

### Post by lugos on 2007-07-21
Hello,

I have setup a 7.04 LAMP server and I am trying to FTP files over to it from my Windows XP machine using Dreamweaver.  I have already installed openssh-server.  In Dreamweaver, I am using my user name to transfer files over.  I will be the only one transfering files.  I want to only give my account the permissions necessary to create and delete files and directories.  How can I go about doing that?

Thanks in advance for the assistance.

---

### Post by nichipet on 2007-07-21
That should be enabled by default, I would think. First do this:

```
ls -l /home/yourusername
```

It should say something like

```
dwrx------ /home/yourusername
```

(I'm not at home, so I can't just copy/paste from mine, so my example may be pretty far off, but you're looking for the dwrx). d is directory, w is write permission, r for read permission, and x for execute permission.

If it doesn't have that, try this:

```
chmod 700 /home/yourusername
```

And do the same for any directories in your home that you will put files into. You could do it recursively for your entire home, but that can get complicated with files you don't want to alter.

---

### Post by lugos on 2007-07-21
Thanks for the reply.  The files and directories will not be created in my home directory though; they will be created in the root directory for my website.  Does that make a difference?  I would actually like it to be recursive in this case.  I want to create *n* number of directories and files.

---

### Post by sunset_studies on 2007-07-22
if your site is at /var/www/mydomain.com/ as I suspect, I'd recommend simply using winscp to transfer the files. Just use the root user and root pass. It's an internal server right? No security concerns...

---

### Post by lugos on 2007-07-22
> **sunset_studies said:**
> if your site is at /var/www/mydomain.com/ as I suspect, I'd recommend simply using winscp to transfer the files. Just use the root user and root pass. It's an internal server right? No security concerns...

That is correct, my site is /var/www/mydomain.com/.  The server is internal, but the site is available on the internet.  What are the risks of doing a chmod 777 on the mydomain.com directory?  Does that open it up to hackers, etc?

---

### Post by sunset_studies on 2007-07-22
sudo chown yourusername:www-data -R /var/www/mydomain.com/
sudo chmod 770 -R /var/www/mydomain.com/

then you should be able scp your files as yourusername

---

### Post by lugos on 2007-07-22
Awesome, that worked.  Thank you Sir.

---

