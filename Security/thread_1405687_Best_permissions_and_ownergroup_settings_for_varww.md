---
title: "Best permissions and owner:group settings for /var/www"
date: 2010-02-12
forum: Security
---

### Post by ForumCat on 2010-02-12
What are the best permissions and owner:group settings for the /var/www directory?  Also, how can I configure the server so that all new files and subdirectories added via Samba or FTP automatically have the proper permissions and owner:group settings?

Currently, I have the permissions for /var/www and all recursive contents set to 775.  Is that secure?    I wanted the group to have write privileges so my Samba users could write to the Samba share set up for /var/www.

For owner:group, I have /var/www and all recursive contents set to root:web-editors but whenever I add new files via Samba the owner of the new files is the Samba user, not root.  Is that a problem?

I just want everything nice and tidy.  Please advise.

Thanks,
ForumCat

---

### Post by Barriehie on 2010-02-12
Default permissions are the safest. root:root and 755

Barrie

---

### Post by ForumCat on 2010-02-14
I understand, but how are my FTP users supposed to upload files if the permissions are 755 and root:root for owner:group?  They're obviously not FTP-ing in as the user root, so they wouldn't be able to upload, right?

I set up a www-editors group and put all my ftp users in there that need write privileges, with www-editors as their primary group.  So now, when they upload, the default owner:group is [uploader_username]:www-editors.  This way all the other www-editor folks have write access to those files, because they're in the same group, so they can delete the files if necessary, overwrite, etc.  And I used proftpd.conf to set the default mode of uploaded files to 665 using a umask of 002 since proftpd has a default mode of 666 and the umask is used to alter that (by subtracting from 777) to arrive at the actual default mode for uploaded files.  After all, I should never need a file to be executable, right?  And if I do, I can use CHMOD to change those few exceptions.

Does this all seem like a sound approach?  Please advise.

Thanks,
ForumCat

---

