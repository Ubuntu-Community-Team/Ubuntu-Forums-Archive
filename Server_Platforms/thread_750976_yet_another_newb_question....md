---
title: "yet another newb question..."
date: 2008-04-10
forum: Server Platforms
---

### Post by chuck jessup on 2008-04-10
ok i have my server going- one last problem it now wont stop, and gives me an error, "sudo: /etc/sudoers is mode 0777, should be 0440" i cant get it to sudo anything and i cant stop my server. and i cant chmod "chmod: changing permissions of '/etc/sudoers' : Operation not permitted" 

1. i need to stop the server . with out sudo or reload, so that i can start and stop the server as needed.

2. get to a point where i can change permissions, so peopel cant start writing stuff and changing it. and so it operates smoothly...


any help offered would be greatly appreciated.
thank you in advance :)

---

### Post by tamoneya on 2008-04-10
```
su
chmod 0440 /etc/sudoers
exit
```
This does not use sudo because instead you are logging in as root user temporarily.  Dont forget to log out.

---

### Post by bluefrog on 2008-04-10
as you are using ubuntu, su will not work (except if you have fiddled with the root account password)

Shutdown your computer the hard way. restart in recovery mode and change the permissions of the sudoers file.

James Dupin

---

### Post by chuck jessup on 2008-04-10
neither worked, su would not autenticate in ubuntu, and my grub some how got messed up so it boots directly to server ubuntu desktop

any way thanks i am just reloading the server...

---

