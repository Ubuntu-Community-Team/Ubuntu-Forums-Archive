---
title: "User Problems"
date: 2008-03-13
forum: Server Platforms
---

### Post by michio on 2008-03-13
I installed a 7.10 server today and I when I went through the install it never asked me for a username / pw...odd

So I rebooted into recovery mode and change my root password and I am able to log into my system as root. I would (for obvious reasons) like to create a regular user that I can log in as and perform admin tasks with the  sudo command.

I have attempted to useradd but when I log in with that account the command line is just a $ instead of a <username>@<hostname># and when I attempted to issue a command with a sudo it asks for my password and then does not perform the command; no error; no incorrect password. 

thanks in advanced. sorry I am noobish.

edit: I did a usermod -s /bin/bash and that got me a <username>@<hostname># but still no ability to run sudo commands

---

### Post by astrotech226 on 2008-03-14
Did you add the new user to the "admin" group?  They need to be to perform the sudo functions.

---

### Post by shahansudu on 2008-03-14
you have to be a sudo user to perform sudo commands. But if you are not and you used sudo then it would have given you a error saying that you are not a sudo user....

---

### Post by michio on 2008-03-14
I ended up adding the user account to the /etc/sudoers file and everything is working out now.

is this not an acceptable solution? securitywise or as far as allowing this account to perform certain options?

---

### Post by Iowan on 2008-03-15
Sounds like you already fixed the problem, but [here]("http://www.psychocats.net/ubuntu/sudo") is an interesting link about SUDO

---

