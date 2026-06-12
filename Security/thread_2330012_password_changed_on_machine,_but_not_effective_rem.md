---
title: "password changed on machine, but not effective remotely ?"
date: 2016-07-06
forum: Security
---

### Post by ButchMel on 2016-07-06
I succesfully changed password for my user name directly on Ubuntu server (using passwd command). On this machine, I now need this new password to log on.

However, if I log from another (Mac OSX) computer, same user name, the new password is not working - only old password allow me to enter... 

Have I missed something ? 

.

---

### Post by steeldriver on 2016-07-06
Are you using SSH to connect from the Mac? perhaps it uses keys and the "password" is actually a key passphrase that happens to be identical to the old password?

---

### Post by ButchMel on 2016-07-06
Humm, good question... How can I check this ? 

And why would it keep working only with that old password when on the Ubuntu machine itself, I'm no longer able o log on with that old password ?

If this can answer the question partly (yet I don't know how to change this...) when I connect from the Mac (Go to Server) :

Server address shown is: smb://UbuntuServerName
then the line below called ''Favorite Servers::'' show: smb://XXX.XXX.X.X  (obviously the IP address of the Ubuntu machine..)

It is the first time I do change a password. 

Thanks again,

---

