---
title: "Help with apache"
date: 2008-02-13
forum: Server Platforms
---

### Post by painejake on 2008-02-13
Hi i've installed Ubuntu 7.10 desktop and i want to access my files and music from my ubuntu pc on my Mac at work. I have installed apache and phpmyadmin and i was just wondering what to do now how do i set it up so i can veiw my files etc at work? Also i wanted to have to enter a user name and a password (thats what i think phpmyadmin is for)
This is the second time using linux so if somebody could explain it quite simple then that would be brilliant thanks

Jay:(

---

### Post by faulkes on 2008-02-13
> **painejake said:**
> Hi i've installed Ubuntu 7.10 desktop and i want to access my files and music from my ubuntu pc on my Mac at work. I have installed apache and phpmyadmin and i was just wondering what to do now how do i set it up so i can veiw my files etc at work? Also i wanted to have to enter a user name and a password (thats what i think phpmyadmin is for)
This is the second time using linux so if somebody could explain it quite simple then that would be brilliant thanks

Jay:(

phpmyadmin is for administrating mysql databases, so unless the solution you install/build uses mysql databases, it is of little use to you.

As for sharing files, apache does support directives for username / password authentication (although not specifically recommended).  You can read more about apache and usernames/passwords at [https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers).  I believe it is section 19 of the apache document there which deals with this subject.

Additionally, there is the official server guide, which covers apache as well available at [https://help.ubuntu.com/7.10/server/C/](https://help.ubuntu.com/7.10/server/C/).

it is also likely, that depending on your home system setup, you will need to learn how to port forward port 80 from your home router to your home linux machine.  I would also suggest you read up on using dynamic dns services unless your home machine is assigned a static ip address.

Faulkes

---

### Post by jman623 on 2008-02-13
Forget apache why not use SFTP (FTP over SSH), it's more secure than regular FTP or apache, plus easier to setup.

see:
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by faulkes on 2008-02-13
> **jman623 said:**
> Forget apache why not use SFTP (FTP over SSH), it's more secure than regular FTP or apache, plus easier to setup.

see:
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

SFTP is another option to use, although it all depends on what he wants to share.

While it may be easier to setup, setting up apache is also a good excersize in getting familiar with unbuntu server and how things work.  In the long run, that provides more benefit at the cost of a bit of time IMO.

Nothing preventing him from doing both as well.

Faulkes

---

### Post by painejake on 2008-02-14
Thanks for the sorces of info guys ill prob try them both out. 

Thank!!
Jay :)

---

