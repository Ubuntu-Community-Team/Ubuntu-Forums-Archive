---
title: "What is the recommended way to set up FTP users that access the same files?"
date: 2010-03-23
forum: Server Platforms
---

### Post by coheed on 2010-03-23
Okay, so maybe I'm going about this the wrong way...

Here's what I'm doing:

I have a server setup with all my web development stuff in /var/www and in several sub-folders within that. (each project having it's own folder)

It works great with one FTP account. But recently I've been getting help on a projects from a buddy of mine that freelances, and have made him an FTP user account as well. All is fine, except for when he tries to edit a file and gets a permissions error.

Here's the issue, I don't want us to have the same FTP login, but all the files are currently owned by my user name. So, when he logs in to edit a file, he can't because I'm the owner, and the files are set to 744. Will I cause any harm by adding both users to the same group (www-data) and chmod'ing the files to 775 so that we can both access and modify the files?

Is group read and write a bad idea?
Is there a better solution?

---

### Post by KB1JWQ on 2010-03-23
Could work.  Security implications would depend on you...

---

### Post by JT9161 on 2010-03-23
What group are the files owned by ?

---

