---
title: "HELP! Samba Problems"
date: 2008-03-12
forum: Server Platforms
---

### Post by ndicostanzo on 2008-03-12
I'm fairly new to Linux and Ubuntu and am trying to create a share on my local network called "keynote". I am running Ubuntu 7.10 and installed Samba and NFS. I created a user called keynote, and then I "shared" it's home folder. Then when I go to another computer on my network, it shows up as part of my subnet, when I click it, it prompts me for a user name and password. I type in the login information for the keynote user and I get a invalid user name or password message. I have even tried using the admin account, but still no luck. I have gone in and tweaked the config file a little, but to be honest, I really don't know what I am doing. Can anyone offer and advice? I attached the config file. Any help would be very greatly appreciated.

---

### Post by jetsam on 2008-03-12
You probably just need to add a user to the samba users database.  Samba keeps a secondary password database of its very own.  On the ubuntu machine, open a terminal and do:
```
sudo smbpasswd -a <username>
```
Replace <username> in the above with the user you want to log in as.  The user needs to have an account on the ubuntu machine as well.

---

### Post by ndicostanzo on 2008-03-18
Yep, that did that trick. Thank you so much!

---

