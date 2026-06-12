---
title: "Changed root and can't login to ftp"
date: 2008-10-06
forum: Server Platforms
---

### Post by wattaman on 2008-10-06
Hi!
I'd like a suggestion from someone who want to help.
I've recently changed the *root *username to *rotz* and since then I can't login to ftp.
Before that, I was using the *root *as username (obviously), and SFTP/SSH as server connection, with the IP as address.
After I've changed the *root *name, I've noticed I can't login using this as username and changed it in *rotz*.
Shouldn't it work?
Is there another way to access, through FTP, the entire server?
Please explain me in noob terms or send me some tutorial links if you want to help.
Thank you!

---

### Post by wattaman on 2008-10-06
I forgot to say that the Ipswitch login error is
> Server Welcome: 
SSH Transport closed.

---

### Post by cdenley on 2008-10-06
> **wattaman said:**
> Hi!
I'd like a suggestion from someone who want to help.
I've recently changed the *root *username to *rotz* and since then I can't login to ftp.
Before that, I was using the *root *as username (obviously), and SFTP/SSH as server connection, with the IP as address.
After I've changed the *root *name, I've noticed I can't login using this as username and changed it in *rotz*.
Shouldn't it work?
Is there another way to access, through FTP, the entire server?
Please explain me in noob terms or send me some tutorial links if you want to help.
Thank you!

How did you change the name of root? That probably isn't a good idea. Many scripts and programs probably assume root is actually called root. Also, it's not a good idea to allow remote users to have root access to your filesystem. If you must have root, perhaps a cleaner solution would be to create a new user with root access.

create the script /bin/sudobash
```

#!/bin/sh
sudo /bin/bash $*

```
```

sudo chmod 755 /bin/sudobash
sudo adduser --shell /bin/sudobash newroot
export EDITOR=nano && sudo -E visudo

```
add a line like this to the end
```

newroot ALL = (ALL) NOPASSWD:/bin/bash

```

Now the user newroot has a shell with root access, which basically makes newroot an alias for root. I would not recommend doing this, though.

---

### Post by wattaman on 2008-10-07
Thanks, m8!
It didn't worked, though.
I've changed the name again, to *root*, but still can't access FTP with it.
Not with *newroot*, either.
So I've deleted it in the end.

---

### Post by cdenley on 2008-10-07
> **wattaman said:**
> Thanks, m8!
It didn't worked, though.
I've changed the name again, to *root*, but still can't access FTP with it.
Not with *newroot*, either.
So I've deleted it in the end.

Well obviously your FTP server is messed up because you "renamed" the root account. First undo whatever changes you made, get FTP working again, then follow my instructions. I can't give you instructions for undoing what you did because you never told what exactly you did.

---

### Post by wattaman on 2008-10-07
I've figured it out.
So, to make an image and give a *'Don't do like him*' example, that's what happened from the start:
- found some irc bots and scanners in the home/admin folder;
- changed the name of user *admin *and *root * and get rid of the scripts;
- noticed I can't login through FTP or SSH.

Well, since I'm a linux starter I thought I was doing right. Obviously I was wrong.

Cdenley, if you still want to help, I appreciate that. If you could give me some tips on _how to prevent this from happening_, it would be great.
Thank you!

---

### Post by cdenley on 2008-10-07
> **wattaman said:**
> I've figured it out.
If you could give me some tips on _how to prevent this from happening_, it would be great.

Don't allow root to authenticate remotely. Don't use weak passwords. Don't use FTP unencrypted. Use something like fail2ban to stop dictionary attacks. Attackers will try to guess your password thousands of times if you let them.
[http://cdenley.yi.org/ftp_honey/hosts.php](http://cdenley.yi.org/ftp_honey/hosts.php)
Could an attacker have gained shell access? If so, then you can't trust your install anymore.

---

### Post by wattaman on 2008-10-07
Just to ensure I did right so far:
- I've disabled the root access in the SSH server's config. (using webmin);
- I've changed passwords to root, admin, and the webmin administrator;
- I've installed denyhosts;

About the attacker gaining shell access, I'm lost... I've found a folder in the home/admin folder with no name - actually a space as a name - and deleted it.
Anyway, if I disable the SSH server and enable it only when I need it, like when transfering files, would that block the  attackers?
Thank you!

---

### Post by cdenley on 2008-10-07
> **wattaman said:**
> Just to ensure I did right so far:
- I've disabled the root access in the SSH server's config. (using webmin);
- I've changed passwords to root, admin, and the webmin administrator;
- I've installed denyhosts;

About the attacker gaining shell access, I'm lost... I've found a folder in the home/admin folder with no name - actually a space as a name - and deleted it.
Anyway, if I disable the SSH server and enable it only when I need it, like when transfering files, would that block the  attackers?
Thank you!

The folder in /home/admin was not placed there by you, correct? Somebody uploaded it through FTP or SSH, meaning they had the password for the admin user? If you were running SSH, he could have logged in to your ssh server, and assuming admin has sudo access, he would have root. He would be able to do anything to your system, like installing a rootkit or keylogger.

I would do more than change those passwords and disable root login through ssh. The root account should not be enabled.
```

sudo usermod -p ! root

```
You should not use "admin" as a user account since it is commonly guessed by attackers. You should always use strong passwords.
[https://cdenley.yi.org:444/pwstrength/ajax.php](https://cdenley.yi.org:444/pwstrength/ajax.php)

Disabling your ssh server when not needed would help, since they can't attack it if it's not running. An attacker can still guess passwords through your FTP server, though.

---

### Post by wattaman on 2008-10-07
Well, I don't want to use *admin *as an user account. I just found it there :) and dunno how to get rid of it
Is there a way to stop them guessing the password through FTP?

---

### Post by cdenley on 2008-10-07
> **wattaman said:**
> Well, I don't want to use *admin *as an user account. I just found it there :) and dunno how to get rid of it
Is there a way to stop them guessing the password through FTP?
I don't think there is an "admin" user on a default ubuntu install. I you didn't create it, maybe someone logged in as root through ssh and created it.
```

sudo deluser admin

```
> **wattaman said:**
> 
Is there a way to stop them guessing the password through FTP?
fail2ban!

---

### Post by wattaman on 2008-10-07
Well, I've deleted the admin user and installed fail2ban, too. Hopefully will work with denyhosts, which is already installed.
Still don't know how to disable anonymous ftp, though. Or it doesn't matter anymore?!
Also, I've disabled the *root *for SSH - Putty it opens the window but it seems to refuze the password and, eventually, denyhosts or fail2ban should add the IP to the black list.
This is how is supposed to work or it shouldn't login as root at all?
Btw, after logging as a different user I can change to root.
Thanks, cdenley!
All those advices means a lot for a noob like me. You're on my white list :)
Thanks again

---

