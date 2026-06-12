---
title: "WordPress File Permission"
date: 2009-06-30
forum: Server Platforms
---

### Post by insub2 on 2009-06-30
I'm having issues with a WorPress install that I'm using for development on my computer.  I have the directories set to 777 and I'm still getting permission errors when trying to use the WP Media Uploader.  But it's not having any issues writing the .htaccess file on it's own.

---

### Post by LepeKaname on 2009-06-30
Can you show the error message? 

Did you tried "chmod -R 777 directory" (with -R) ?
Also try to change the owner to www-data.

---

### Post by insub2 on 2009-06-30
LepeKaname, you were writing that as I was discovering my booboo.

I had switch the spaces to underscores in the directory holding WP and thought I had made all the appropriate changes to WP.  But, alas, there was one more thing. Settings -> Miscellaneous -> Store Uploads in this folder.  So it was trying to create a new directory in my web root--which is not writable by anyone but me.

All is well now.  Thank you for your help.

---

