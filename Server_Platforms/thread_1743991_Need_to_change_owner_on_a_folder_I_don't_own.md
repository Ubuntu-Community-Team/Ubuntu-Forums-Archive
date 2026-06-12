---
title: "Need to change owner on a folder I don't own"
date: 2011-04-30
forum: Server Platforms
---

### Post by Maheriano on 2011-04-30
I have a website hosted remotely and someone hacked it to change the permissions on public_html/images to 000. I try to change the permissions back but I don't have access so I imagine they must have changed the owner of the folder as well. I have FTP access, control panel access and SSH access but not even CHOWN/CHMOD works because I need to be root and (obviously) I'm not part of the sudoers on the remote hosting box.

How can I fix this while waiting for the hoster to get back to me?

---

### Post by dtfinch on 2011-04-30
Changing an images folder's permissions to 000 doesn't seem like a usual goal when hacking a server. But if it was hacked, you might want to take the whole thing offline long enough to investigate what else they might have done, like installing exploit packs to use against your visitors.

However, if you just want to get an images folder up, without changing everything that links to it, and you have a backup, you could try uploading the backup to a new folder (like images2), then, if the host has installed/enabled mod_rewrite for apache, you could upload a ".htaccess" file to public_html with a rewrite rule to send all /images/ requests to the new folder. I think it would look something like this:```
Options +FollowSymlinks
RewriteEngine on
RewriteRule ^images/(.*) /images2/$1
```

---

### Post by rubylaser on 2011-04-30
dtfinch, that's a good quick howto for routing to the new images directory.  I really would consider what dtfinch said first though, and take the server down.  You need to determine how the system was compromised, patch the vulnerability and then restore from backup to ensure that your application is free of stuff left behind from the compromise.

---

### Post by Maheriano on 2011-05-01
The client requested an OSCommerce theme that uses an older version of the core software. I him it was going to get hacked, now it happened. Last week they did the same thing to the public_html folder, now it's just images. There are 800 files in the folder with encoding injected into the top of them, I just need to get it back up for now until I can get the new version up.

---

