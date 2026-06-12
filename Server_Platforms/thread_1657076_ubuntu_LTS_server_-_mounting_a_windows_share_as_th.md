---
title: "ubuntu LTS server - mounting a windows share as the /home directory?"
date: 2010-12-31
forum: Server Platforms
---

### Post by wayneox on 2010-12-31
hi ya. basically i have set up an ubuntu server as a PDC for the office..
 
this machine is called "Login"
 
i am aware of how to use the smb.conf file to redirect a profile to a different server 
 
EG:
profile path = [\\SERVER\Users\%U\profile]("file://\\SERVER\Users\%U\profile")
home (H:) path = [\\SERVER\Users\Store]("file://\\SERVER\Users\Store")
 
NOTE: I DO NOT WANT THE FILES STORED ON "LOGIN" - This machine is only a small machine, and will be used for an email server, and login control only.
 
But when i add users i have to transfer files from the /etc/skel directory to the windows share. the best way i see of doing this is:
 
mount -t smbfs //Server/Users /home
 
i add users using
adduser NAME -m -g GROUP
smbpasswd -a NAME 
 
it would be a bit of an annoyance tot hen need to copy the /home/NAME directory to the //server machine, then set the access rights (Administrators FULL / EVERY ONE DENY / NAME FULL)
 
I do not have any need for the files to be actually stored on the linux box as i see? I want them stored ont he windows machine, as this machine currently is the server, it just doesnt auth logins, etc, no roamin profiles ETC *(this is an annoyance as we dont always use the same machine in the office, so its a case of musical chairs a lot of the time.
 
now can somebody clarify... will i need to mount the //server/users directory every time the server boots ? does this directory need mounting with root access?
 
does the created directories have permissions set so user X wont be able to access user Y directory? or will i need to modify this myself?
 
btw: //SERVER is a vista business machine - i did try testing at home but its tricky since my vista is home premium which cannot be joined to a domain - and with not being in the office till tues now ;) 
 
Hopefully what im asking is clear, if not i will try to explain better... thanks.
 
PS: The PDC is all working, as are user profiles etc stored on the [\\%N\%u\profile]("file://\\%N\%u\profile") share ([\\login\name\profile]("file://\\login\name\profile"))
 
its just for backup purposes, (backups r via the windows "server") it is easier to just keep the files on the server, not login machine. - surely somebody else has had this idea?
 
OH Additionally, when i create a user, does it automattically create an email account? or do i need to do that?

---

