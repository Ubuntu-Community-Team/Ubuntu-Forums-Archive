---
title: "hybridfox"
date: 2011-04-22
forum: Ubuntu Cloud and Juju
---

### Post by shahin on 2011-04-22
Greetings
   I have setup hybridfox and it works really nice.  I noticed it used Remote Desktop to log into VMs.  That does not work for me yet.  I wonder if I am using the wrong image for my VMs?  Where can I get an image that would work with Hybridfox's remote desktop feature?  
   And does hybridfox work with other desktop applications like vnc?

---

### Post by anandchitravelu on 2011-05-09
Hi Shahin,

Can you update me with few more details of the connection? I mean, the instance's operating system and the operating system you use.

Please note that if you are using windows, hybridfox requires putty to connect to the linux instance and in linux, hybridfox requires rdesktop to connect to windows instance.

Regards,
Anand

---

### Post by Rusty au Lait on 2011-05-11
I have had problems in hybridfox highlighting a running image and trying to start a session with the image. I have always found the problem to be the ~/.ssh/known_hosts file.

Try to start a session from a command line outside of hybridfox (hybridfox never told me why it could not complete the connection). If you get a response that the host has a different key you need to edit the known_hosts file and delete the line in question (the error message will tell you which line needs to be deleted).

my 2¢

---

