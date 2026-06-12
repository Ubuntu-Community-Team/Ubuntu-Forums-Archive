---
title: "PDC ldap setup script"
date: 2006-04-13
forum: Server Platforms
---

### Post by oly on 2006-04-13
I spent a bit of time creating a bash script that will automatically setup a samba PDC with an ldap backend, it also installs phpldapadmin.

be warned this is my first ever bash script, and i am very new to samba and openldap myself.

if anyone sees any mistakes bugs or problems, or has suggestions for improvement let me know.

before using this script makesure universe and probably multiverse are enabled in synaptics, then run the command

sudo sh setup.sh 

this will start the install and setup process, when it completes you shoudl have a working PDC i hope. :D 

[PDC Server Setup Files]("http://www.d0t.co.uk/files/scripts/PDC-Server.tar.gz")

---

