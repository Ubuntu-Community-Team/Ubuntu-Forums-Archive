---
title: "Permissions Help!"
date: 2010-03-30
forum: Server Platforms
---

### Post by Datamac on 2010-03-30
Need help maintaining permissions across multiple directories.  Have  Ubuntu 8.04 Hardy Heron.  O/S installed, updated and running with no  problems.  Why is it that my administrator user id doesn't seem to have  root permissions to create directories?  I am trying to setup hosting 3  separate websites and therefore create 3 separate directories to manage  all associated files for the 3 websites.  Also, I am attempting to read  through the tutorials located at: [http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412)

---

### Post by dudumomo on 2010-03-30
Hello Datamac,
Be sure that your user is a root member.
When you try to launch any command with sudo, do you have any problem ?

---

### Post by ravikalsi27 on 2010-03-30
use command by root
chmod 770 /"dir path where u wana keep u r files"

---

### Post by jrssystemsnet on 2010-03-30
> **Datamac said:**
> Need help maintaining permissions across multiple directories.  Have  Ubuntu 8.04 Hardy Heron.  O/S installed, updated and running with no  problems.  Why is it that my administrator user id doesn't seem to have  root permissions to create directories?  I am trying to setup hosting 3  separate websites and therefore create 3 separate directories to manage  all associated files for the 3 websites.  Also, I am attempting to read  through the tutorials located at: [http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412)
Because your administrator user id is not root, it is just capable of *assuming* root privileges.  If you want to assume root privilege, you need to use the **sudo** command as a prefix to whatever command you're trying to issue.

Example:

```
me@box:~$ **cd /usr**
me@box:/usr$ **touch test**
touch: cannot touch `test': Permission denied
me@box:/usr$ **sudo touch test**
[sudo] password for me:
me@box:/usr$ **ls -l | grep test**
-rw-r--r--   1 root root     0 2010-03-30 14:05 test
me@box:/usr$ **rm test**
rm: remove write-protected regular empty file `test'? **y**
rm: cannot remove `test': Permission denied
me@box:/usr$ **sudo rm test**
me@box:/usr$
``` 

See how that works?

---

### Post by Datamac on 2010-03-30
Thanks everyone.  Your information helped!

---

