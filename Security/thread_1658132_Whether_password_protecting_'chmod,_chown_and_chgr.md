---
title: "Whether password protecting 'chmod, chown and chgrp' is possible?"
date: 2011-01-02
forum: Security
---

### Post by s.a.patil on 2011-01-02
Respected Ubuntu Community Members, Kindly bear with me, I just have a really another wired question. Previously I asked whether we can set separate Password for 'sudo' and 'User Account' after much discussion with learned member of community I was enlightened that we cannot do so. I now have another wired question.
Can we password protect the permission given to the file? To make matter clear I give an instance.
I have created a directory called /protectme/ in /home/myhomedirectory/ so the path will be /home/myhomedirectory/protectme/, now I log into terminal and 'sudo' the /protectme/ folder to 'chmod 700' after doing so can I protect this permission with another secondary password so that if I want to change the permission, first I have to give 'sudo' my secondary password which protect the file permission and later 'User Account' password? In the sense the permission of /ptotectme/ will be encrypted by second password.
Will the encrypting directory will have similar effect? 
Sorry I'm really a nerd to ask. Thanks a lot in advance.

---

### Post by ajgreeny on 2011-01-02
You can make the folder into an archive in zip format and password protect that with a different password to your system password very easily.

Other users will be able to see the zip archive, but even with root permissions will not be able to open the files in it without your zip password.

---

### Post by rookcifer on 2011-01-02
> **s.a.patil said:**
> Respected Ubuntu Community Members, Kindly bear with me, I just have a really another wired question. Previously I asked whether we can set separate Password for 'sudo' and 'User Account' after much discussion with learned member of community I was enlightened that we cannot do so. 

Who told you that you can't?  They're wrong, you can.  All you have to do is unlock the root account (I don't recommend it, but you CAN do it).


> I now have another wired question.
Can we password protect the permission given to the file? To make matter clear I give an instance.
I have created a directory called /protectme/ in /home/myhomedirectory/ so the path will be /home/myhomedirectory/protectme/, now I log into terminal and 'sudo' the /protectme/ folder to 'chmod 700' after doing so can I protect this permission with another secondary password so that if I want to change the permission, first I have to give 'sudo' my secondary password which protect the file permission and later 'User Account' password? In the sense the permission of /ptotectme/ will be encrypted by second password.
Will the encrypting directory will have similar effect? 
Sorry I'm really a nerd to ask. Thanks a lot in advance.

Just encrypt the directory.

---

### Post by bodhi.zazen on 2011-01-02
> **s.a.patil said:**
> Respected Ubuntu Community Members, Kindly bear with me, I just have a really another wired question. Previously I asked whether we can set separate Password for 'sudo' and 'User Account' after much discussion with learned member of community I was enlightened that we cannot do so.

Who told you that ? This is incorrect, read the man page for sudo and sudoers, specifically targetpw.

> I now have another wired question.
Can we password protect the permission given to the file? To make matter clear I give an instance.
I have created a directory called /protectme/ in /home/myhomedirectory/ so the path will be /home/myhomedirectory/protectme/, now I log into terminal and 'sudo' the /protectme/ folder to 'chmod 700' after doing so can I protect this permission with another secondary password so that if I want to change the permission, first I have to give 'sudo' my secondary password which protect the file permission and later 'User Account' password? In the sense the permission of /ptotectme/ will be encrypted by second password.
Will the encrypting directory will have similar effect? 
Sorry I'm really a nerd to ask. Thanks a lot in advance.

There are several issues here.

First each user should have a separate account. In that event permissions are sufficient for all but wo scenarios, root and physical access.

You can restrict the root account with acl and tools such as selinux and apparmor.

For protection form those with physical access you need to use encryption.

The concept of password protecting something is likely from Windows and no there is no similar mechanism in Linux (and password protection without encryption is not much protection at all).

---

### Post by s.a.patil on 2011-01-02
Respected ajgreeny, rookcifer, bodhi.zazen, many thanks for the thread. I really feel very thankful to Almighty himself because he gave an wonderful opportunity to interact with such a good community, thank you very much, I really feel good to having migrated from Microsoft Windows. Thanks flocks for such a great support. I will let know my approach to great community.

---

### Post by s.a.patil on 2011-01-02
Sorry post repeated!!!

---

