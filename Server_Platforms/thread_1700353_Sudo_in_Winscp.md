---
title: "Sudo in Winscp"
date: 2011-03-04
forum: Server Platforms
---

### Post by Code9 on 2011-03-04
Whenever I try to edit my index.html file with Winscp (SSH), it says I don't have the permission to do so. Is there anyway I can change that?

---

### Post by elico on 2011-03-04
get root access using:
[php]sudo su
passwd

enter new  password.. etc..
[/php]
and you can login using root.
dont forget to limit the hosts\ip that can use root user.

---

### Post by Code9 on 2011-03-04
I ran it on the machine itself, and it worked.
I tried to run it via SSH and it gave me:
sudo: no tty present and no askpass program specified

---

### Post by Code9 on 2011-03-05
Nevermind, I was still logging into my other account. How do I limit the IP's? Also, can I give my underprivileged account temp root?

---

### Post by flickerfly on 2011-08-02
I believe you just used a jack hammer to shave with. 

Wouldn't it be better to add your user the www-data group so that your user has access to all the data without opening up root? There are very real reasons why root is heavily restricted by default on Ubuntu servers. I run lots of them and very, very rarely run into a situation requiring me to set and know a root password.

If you edit your sudoers file, you can find ways to permit certain access to certain resources or even everything by simply using the account password, not the root password. I believe that is the answer to your last question. sudo visudo will open that for editing. You'll probably want to wander around the man pages for sudoers and other example configs around the web to be sure you know what it is you are providing to the user.

---

