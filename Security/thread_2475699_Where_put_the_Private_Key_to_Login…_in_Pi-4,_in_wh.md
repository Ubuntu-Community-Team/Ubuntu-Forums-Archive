---
title: "Where put the Private Key to Login… in Pi-4, in what folder, and how insert it???"
date: 2022-06-05
forum: Security
---

### Post by lsepolis123 on 2022-06-05
[InstallNextcloud on a Raspberry Pi - Ubuntu Appliance | Ubuntu]("https://ubuntu.com/appliance/nextcloud/raspberry-pi#ubuntuos")
[https://ubuntu.com/appliance/nextcloud/raspberry-pi#ubuntuos](https://ubuntu.com/appliance/nextcloud/raspberry-pi#ubuntuos)

After insert Publickey to: [https://login.ubuntu.com/ssh-keys](https://login.ubuntu.com/ssh-keys)

Where put thePrivate Key to Login,&#8230; in Pi-4, in what folder, and how insert it???

---

### Post by The Cog on 2022-06-05
This is how you can do it the hard way:
Put your public key in the file /home/pi/.ssh/authorized_keys on the pi. Or if it already exists, just append your public key to that file. The 
The .ssh folder must have the right parmissions: chmod 700 .ssh, and the file must have the correct permissions: chmod 600 .ssh/authorized_keys

Having done this you can log into the pi as user pi and will not be asked for a password. Your private key must be kept private, and never leaves your laptop/desktop where you made it. Only the public key goes anywhere else.

The above can be a little confusing and things don't work unless you get it right, so here is a link to using a utility ssh-copy-id that will make the right files and permissions for you. You need to know user pi's password when you run the script so it can log into the pi as user pi (or whatever other account you wish to use), and it sets up the ssh config on the pi for you. [https://askubuntu.com/questions/46930/how-can-i-set-up-password-less-ssh-login](https://askubuntu.com/questions/46930/how-can-i-set-up-password-less-ssh-login)

---

### Post by lsepolis123 on 2022-06-05
What is the default Username & Password for OS:  

[https://ubuntu.com/appliance/nextcloud/raspberry-pi#ubuntuos](https://ubuntu.com/appliance/nextcloud/raspberry-pi#ubuntuos)

???

---

### Post by The Cog on 2022-06-05
I think I remember that the defaults for a Raspberry Pi are username pi and password raspberry. You should of course change the password, and once you get passwordless login working, you should disable using a password to log in.

---

