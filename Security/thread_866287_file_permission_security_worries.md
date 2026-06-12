---
title: "file permission security worries"
date: 2008-07-21
forum: Security
---

### Post by sp0nge on 2008-07-21
Hello, I'm not sure if this belongs here or in another area, please forgive me and move if necessary. 

I have configured a LAMP server to experiment with hosting my own web sites that are currently costing me to be hosted. 

So far, I think I have configured everything correctly and securely. Apache server docs from /var/www, which is owned by user and group root. I presume it is more secure to chown the directory and add users that I want to access it rather than to add users group root. Is there a more secure or better way to do this, and will Apache need to be configured if I change the permissions of the directory?

---

### Post by sp0nge on 2008-07-23
Ok, let's try a different angle. Can anyone tell me their experience or preferences in regards to virtual hosts?

---

### Post by hyper_ch on 2008-07-24
change ownership and files in /var/www to your apache user/group

---

### Post by sp0nge on 2008-07-24
Thank you for the input. I may do so, but I would like to get more information o virtual hosts. While I only have one site in mind while I learn, I'd like to server multiple sites from one server. From what I understand so far, the "best" way to do this is via virtual hosts. 

Any input on the contrary?

---

