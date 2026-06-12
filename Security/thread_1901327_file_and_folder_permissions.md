---
title: "file and folder permissions"
date: 2011-12-28
forum: Security
---

### Post by a2j on 2011-12-28
I'd like to have a directory on my web server, where I can host my random images that I can quickly upload using php script. but I have concerns about the security of this deal.

in a "root" directory I have two folders, "uploader" and "files". "uploader" is where my php upload scrips are. Its protected with .htaccess. And "files" where it uploads images. www-data has RWX and everyone else is R-X.
would it be possible for somebody to upload any files to "files" folder and possibly execute them? after all, apache can read write and execute. but my php scrips allows only image uploads.

please, give me a possible scenarios of what could happen. Thank you.

---

### Post by CharlesA on 2011-12-28
I wouldn't give www-data write access for that reason.

I'm not sure how your uploader works, but you can set it to be run as a different user and give only that user rwx access?

---

### Post by a2j on 2011-12-28
looks like that is how most content management systems run. uploads directory is writable by www-data user. :???:

---

### Post by CharlesA on 2011-12-28
> **a2j said:**
> looks like that is how most content management systems run. uploads directory is writable by www-data user. :???:
Hrm, if that's the case, I would just leave it.

*shrug*

---

### Post by TheFu on 2012-02-02
> **a2j said:**
> please, give me a possible scenarios of what could happen. Thank you.

A poorly written upload script or file permissions could allow someone else to take over your server.  Sound bad?

You probably want to use someone else's, mildly popular, upload script if you insist on doing this with PHP over the web.  Perhaps running a well used CMS like Drupal or Joomla would be a better choice?  Regardless, check for updates a few times every week and install them so your box isn't owned.  

If you will be the only person uploading image files, consider using rsync over ssh to push the files from your non-internet machine - perhaps automatically every day using ssh-key authentication to your host?

There are probably thousands of ways to accomplish what you want, but only 10 ways to do it securely.

-- I approved this message. ;)

---

### Post by a2j on 2012-02-02
not exactly what I was asking about... but I found my solution. owncloud will do what I need.

---

