---
title: "passwd vs Gnome About me"
date: 2009-05-18
forum: Security
---

### Post by Gingalone on 2009-05-18
I am experiencing a problem with passwords in Ubuntu (from Hardy to Jaunty): if I change my password from Gnome System>Preferences>About Me my pw is correctly changed; but, if I change it with passwd from terminal, the terminal says: passwd: password updated successfully but the password is NOT changed  and afterwards I must login with the old one and provide that every time I give the sudo command...

What about???
Thank you in advance for any illumination!
Gingalone

---

### Post by pawnrocket on 2009-05-18
Not that this is any help to you, but I would consider checking the bug tracking system. If there are no bugs reported perhaps you should fill one out. 

Sorry I can't be more help.

---

### Post by cariboo on 2009-05-19
When changing user passwords, you have to be root, which you are when you use the gui applications. To change a password on the command line you would type:

```
sudo passwd <username>
```

where <username> is the user you want to change the password for.

---

