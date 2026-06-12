---
title: "Quick questions about Apache and PHP5"
date: 2005-07-08
forum: Server Platforms
---

### Post by RagnArok on 2005-07-08
Hello, i've just installed Apache2 on my Ubuntu running computer, and now i wonder - where do I put the files that make the homepage? beacuse everytime i connect to [http://localhost](http://localhost) I get message that 'the file / could not be found' and even if I connect to a file i know lies in the folder /var/www/ i get the same message (except from the searchpath)

That was my first problem, my next question is how i fix the rights for the apache folders, what should i have and how do i make it happen? I want to be able to change the files from my regular user account (without using the sudo command)

My third problem is regarding PHP, i would like to have PHP5 support on my server - how do i fix this? I can only find PHP4 support in the APT database.

Thanks in advance! Btw, Ubuntu rocks! :-D

---

### Post by LordHunter317 on 2005-07-08
What is the exact error when you try to access  a known file in /var/www?  Do you get 404 (File not found) or 403 (Permission)?  That makes a big difference. 

As for filesystem permissions, the www-data needs read access on any files you want to serve.  Generally, it should never own any files.  To grant your user access, just sudo chown the directories/files you want him to be able to edit.  Doing:```
 sudo chown -R myuser /var/www
```Would give the user entire ownership of the main web root, and allow you to edit there, without sudo.

---

### Post by RagnArok on 2005-07-08
Oh, I knew i had forgot somethin, it's a 404 error :-P

---

### Post by RagnArok on 2005-07-08
I've solved the PHP5 problem, but i still can't access my files! ](*,)

So now I've restartet my computer - and now I can't even connect to [http://localhost](http://localhost) ! ](*,)  (Connection refused) but the firewall isn't blocking anything, and ther's nothing else I've done that might have screwed it up :(

---

### Post by RagnArok on 2005-07-08
Okey, i reinstalled Apache2 like 5 times, and NOW it actually works fine :-D PHP5 support to :-P

Thx for the help though ;)

---

### Post by ecadre on 2005-07-11
You might find this thread useful as well:

[http://www.ubuntuforums.org/showthread.php?t=47605](http://www.ubuntuforums.org/showthread.php?t=47605)

Setting up of access and multiple hosts on a local machine on Ubuntu (very useful).

---

