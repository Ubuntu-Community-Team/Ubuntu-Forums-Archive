---
title: "SSH/SFTP users configuration permissions"
date: 2010-06-06
forum: Server Platforms
---

### Post by MasterCard on 2010-06-06
I have 3 friends who will use my **Ubuntu 8.04 Server** for their websites. They will have hosting accounts wth SSH/SFTP access. 

user1
user2
user3

Here is what I need:

- I need to jail them in /srv/www/partners so that they can see only filesystem inside the /srv/www/partners folder. I want them to have permissions to edit upload etc. inside /srv/www/partners folder (to use it like everage hosting account). [SFTP]

- I need them to use ssh COMMAND LINE [ONLY WITHIN /srv/www/partners folder]: only **WGET**, **TAR**, **LN**, **CD**, **VI**, **MKDIR**, **MV**, **CP**, **CAT**, **MORE**, **RM** etc. I mean all general most used commands like everage hosting account with SSH access. [SSH]

How my dream can come true? Please help me ... this is first time I need to do it :confused:

---

### Post by MasterCard on 2010-06-06
I would very much appreciate an answer. Please help.

---

### Post by MasterCard on 2010-06-07
How can I update from OPENSSH 4.7 to OPENSSH 5.5???
How can I do that on **Ubuntu 8.04 Server**???

I guess the latest version **OPENSSH 5.5** will make my task much easier but it is not present in Hardy Heron [https://lists.ubuntu.com/archives/ubuntu-backports/2008-October/009945.html](https://lists.ubuntu.com/archives/ubuntu-backports/2008-October/009945.html)

I also posted my questions here [http://ubuntuforums.org/showthread.php?p=9423407](http://ubuntuforums.org/showthread.php?p=9423407)

Please support me for openssh upgrade in backports for **Ubuntu 8.04**

---

### Post by lavinog on 2010-06-07
> **MasterCard said:**
> How can I update from OPENSSH 4.7 to OPENSSH 5.5???
How can I do that on **Ubuntu 8.04 Server**???

I guess the latest version **OPENSSH 5.5** will make my task much easier but it is not present in Hardy Heron [https://lists.ubuntu.com/archives/ubuntu-backports/2008-October/009945.html](https://lists.ubuntu.com/archives/ubuntu-backports/2008-October/009945.html)

I also posted my questions here [http://ubuntuforums.org/showthread.php?p=9423407](http://ubuntuforums.org/showthread.php?p=9423407)

Please support me for openssh upgrade in backports for **Ubuntu 8.04**
You will need to update to Ubuntu 10.04 if you want the latest versions.  Is there any reason why you want to stay with 8.04?

The important thing is to chmod the folders you don't want them to access, and don't add them to a group that has that access.

You can set their home folder to /srv/www/partners/username

Does each user need to access the same folder or individual folders?

If they need shared access, you should make a wwwpartners group and add each user to that group, then chgrp the /srv/www/partners to that group.

---

### Post by duceduc on 2010-09-02
mastercard,

This is exactly what I need to do. If you are still following this thread and or accomplished it, please share your find.

Anyone can help as well. Thank you.

---

### Post by duceduc on 2010-09-08
> **duceduc said:**
> mastercard,

This is exactly what I need to do. If you are still following this thread and or accomplished it, please share your find.

Anyone can help as well. Thank you.
I've figured it out.

---

### Post by intel352 on 2011-01-03
Please share your solution then.

---

### Post by duceduc on 2011-01-03
It's been awhile and i can't remember the steps. However, I followed this [tutorial](http://ubuntuforums.org/showthread.php?t=518293) on setting up vsftp.

---

