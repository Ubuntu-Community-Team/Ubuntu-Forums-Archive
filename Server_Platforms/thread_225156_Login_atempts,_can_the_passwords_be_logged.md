---
title: "Login atempts, can the passwords be logged?"
date: 2006-07-29
forum: Server Platforms
---

### Post by paultjeb on 2006-07-29
It is too funny, all these logint attempts from all over the world to my Ubuntu-server. 
Most of them try to login as root. Is there any posiibility I can store all these attempts in a bit more human readable format, together with the password they tried and the originating IP?

---

### Post by Swab on 2006-07-29
I wouldn't think there is a way to log the passwords... 

Just change the port ssh uses to some obscure port.  And limit who can login to one username.

---

### Post by Lord Illidan on 2006-07-29
How would you know that they tried to log in to your computer? Just curious, and a bit anxious.

---

### Post by Swab on 2006-07-29
> **Lord Illidan said:**
> How would you know that they tried to log in to your computer? Just curious, and a bit anxious.

/var/log/auth.log

---

### Post by Lord Illidan on 2006-07-29
> **Swab said:**
> /var/log/auth.log
Thanks!

---

### Post by paultjeb on 2006-07-29
There is just one user on my system, with an ex-treme-ly hard to guess password. I am just curious which passwords those fools who try to login use with all the obvious usernames they try... (root, admin, user, user1, wwwdata, guest, etc).
Storing their ip's and or hostnames us just an added bonus ;)

---

### Post by Lord Illidan on 2006-07-29
> **paultjeb said:**
> There is just one user on my system, with an ex-treme-ly hard to guess password. I am just curious which passwords those fools who try to login use with all the obvious usernames they try... (root, admin, user, user1, wwwdata, guest, etc).
Storing their ip's and or hostnames us just an added bonus ;)

I don't think passwords get logged, at least not as cleartext. Otherwise, it would be a massive security hole...imagine all those times, you wrote your password only to misspell a letter or something. From just reading that file containing those logged passwords, an attacker can get a very good idea of what those passwords are.

Unless they are randomized, of couse.

---

### Post by paultjeb on 2006-07-29
I guess you are right, haven't thought of that. 
I will go on the lookout now for something that puts an ip on some kinda blocklist after x failed login attempts within y minutes.

---

### Post by Lord Illidan on 2006-07-29
> **paultjeb said:**
> I guess you are right, haven't thought of that. 
I will go on the lookout now for something that puts an ip on some kinda blocklist after x failed login attempts within y minutes.

Do you need ssh open?

---

### Post by paultjeb on 2006-07-29
yes, ssh needs to be open. I am not too worried about the failed logins, I just want to piss them off and have some idea how much script kiddies try this.. Thats all.

---

### Post by Lord Illidan on 2006-07-29
Ah, ok...I dunno, perhaps a firewall would be a good idea?

---

### Post by paultjeb on 2006-07-29
I googled and foud some leads. Thanks for the help!
[http://ubuntuforums.org/archive/index.php/t-20551.html](http://ubuntuforums.org/archive/index.php/t-20551.html)
[http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts](http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts)

---

