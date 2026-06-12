---
title: "vsftpd chroot, creates 550 error on CHMOD command"
date: 2010-07-14
forum: Server Platforms
---

### Post by artheus on 2010-07-14
Hi!

I've been searching the web, without finding any sollution to my problem.

vsFTPd is acting really weird. I've never seen this problem before, and I've been using vsftpd for some years now.

Well.. The thing is, I've made a user that chroots to the folder /var/www on my server. And when I then try to chmod the file /var/www/htdocs/testsite/index.html through my ftp-client, I only get the error "550 SITE CHMOD command failed.", and when I then check in my /var/log/vsftpd.log it says

```
FAIL CHMOD: Client "192.168.50.58", "/htdocs/testsite/index.html 777"
```

Which I think would mean that it tries to chmod the file "/htdocs/testsite/index.html" instead of chmod the file "/var/www/htdocs/testsite/index.html" as the user is chrooted to the folder /var/log.

Are there any explanation for this, and maybe even an easy solution?

Cheers,
Artheus

---

### Post by cdenley on 2010-07-14
Are you logged in as a local user? Have you set "chmod_enable" to "NO" in your configuration file? Does the local user have write permission on the file?

Since the user is chroot'ed to /var/www, the path provided by the user would be "/htdocs/testsite/index.html", so they are trying to chmod "/var/www/htdocs/testsite/index.html".

---

### Post by artheus on 2010-07-14
Thanks!

Yes I am logged in as local user.
No, I have set "chmod_enabled" to "YES"
Yes, I have set the file permissions to 775 and the ftp users are all in the same group "webdev".

Ok, thank you for that.

---

### Post by cdenley on 2010-07-14
> **artheus said:**
> 
Yes, I have set the file permissions to 775 and the ftp users are all in the same group "webdev".

Actually, I think simply having write permissions on the file is not enough. You need to be the owner of the file in order to change permissions.

---

### Post by artheus on 2010-07-14
oh.. ouch!

Is there any way around that?

I mean ANY way?

Cheers

---

### Post by cdenley on 2010-07-14
I don't think there is any way to allow your FTP users to chmod files they don't own. You can change the default permissions for uploaded files, though.

---

### Post by artheus on 2010-07-15
Hmm... Okay...
But is there any way of letting your local users be able to chmod files they to not own?

Cheers

---

### Post by artheus on 2010-07-15
Well.. I solved this an "ugly" way. On the server I use samba for that ftp location. And that is why the owner is not always the same on files. So now I changed the samba settings to "force user = username" in addition to all of the other force attributes I've set for that folder.

It works, and I've set the owner of all the files to the required username. So now I'm satisfied with the fact that it works.

But I have an additional question.. Could this solution mess other things up?

Cheers,
Artheus

---

