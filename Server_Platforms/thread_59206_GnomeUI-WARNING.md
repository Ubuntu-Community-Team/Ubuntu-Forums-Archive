---
title: "GnomeUI-WARNING"
date: 2005-08-23
forum: Server Platforms
---

### Post by ahmedbirry on 2005-08-23
Hi there
if you may excuse me if i bosted this in the wrong place, but i am getting some kind of   :roll:  with a problem with my installation...... when ever i try to run any application of administer a configuration (like login manager, user management,etc) after asking for changing user, and typing the password, it does nothing, and leter on, when retrying, it gives me a strange error (Failed to run users-admin:
 Child terminated with 1 status) which i do not understand !!!

But... when using a su termenal..... and using the command based order (like users-admin) it gives me a detailed error or WARNING.... (GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.)  and the users administration window comes up.... it opens !!!!

can you guys help me understand where did i went wrong ? how to correct this ? as i really gave up. :roll: 

Thanks

Birry

---

### Post by jsvidyad on 2005-09-03
Hi,


     I was having similar problems after I deleted the list of hosts from my network tools. Type in gedit /etc/hosts. If your computer name is local (say), then there should be a line which reads 

127.0.0.1  local

If you do not have such a line, just enter a line like this and save the file, of course substituting your computer name for local. In case you have forgotten your computer name, just type in hostname in the terminal and it will give your computer name

  BTW, you will have to be logged in as root to modify the hosts file.

---

### Post by ahmedbirry on 2005-09-15
thanks....   :smile:

---

