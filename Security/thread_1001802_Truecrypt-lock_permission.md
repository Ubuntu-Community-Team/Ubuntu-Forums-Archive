---
title: "Truecrypt-lock permission"
date: 2008-12-04
forum: Security
---

### Post by uric on 2008-12-04
Hi all



I'm havings some problems with truecrypt. When I start truecrypt I get msg "lock file truecrypt-lock-ubuntu has incorrect permission". And then when I press ok it says truecrypt already started. 

It all started when I moved som old backup files with different permission to my home dir. So I changed users and permission for the whole home dir.

[B]
 chmod -R ubuntu:ubuntu /home/ubuntu/
 chown -R 750 /home/ubuntu/[/B]


Then I tried: 


**sudo chmod -Rv 777 /home/x/.TrueCrypt**


But its still same thing. Had some other strange problems with permissions but I think they are OK since I changed to 750. 

Anyone know how to fix this?



Thanks! ):P

---

### Post by disabled_20220313 on 2008-12-11
Hi,

Just had the same problem. Did a similar thing to you and made all the permissions of my Mum's home directory the same, and it broke her TrueCrypt.

Not sure what the actual problem is, but deleteing the file .TrueCrypt-lock-[user] solves the problem. It seems to be generated when you run TrueCrypt, and deleted again when it is closed. I'm guessing its a mechanism to stop multiple instances of TrueCrypt running.

Did a test myself after doing it and was able to mount my encrypted volumes still.

Hope that helps.

---

### Post by kdiddy on 2009-02-01
THANKS ! solved my problem , 
Kevin

---

### Post by scorpias on 2010-01-01
I had the same problem, but try change the type to (Application in Terminal) - this seems to fix the auto locking of the file.

It was a pain to rm the locked file in order to re-open the menu screen.

---

### Post by Soul-Sing on 2010-01-02
Uric which version of truecrypt do you use?
And on version 9.10 i assume?
Did you choose for an encrypted home during the install?

---

