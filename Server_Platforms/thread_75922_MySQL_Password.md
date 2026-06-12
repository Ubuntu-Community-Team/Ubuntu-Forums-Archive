---
title: "MySQL Password"
date: 2005-10-14
forum: Server Platforms
---

### Post by TheDanMan on 2005-10-14
I've tried my sudo password and the username root.  Does ubuntu use something else as the root username to mysql by default?

---

### Post by TomB on 2005-10-14
connect to mysql in a terminal like so

mysql -u root -p
press enter at the password prompt 

then type the following to create a root password

set password for root = password("passwordhere");

press enter and you're done

---

### Post by LordHunter317 on 2005-10-14
I'll say this here because it seems as a good of place as any, and it trips people up often:

MySQL accounts aren't the same as system accounts, even if they have the same name.

IOW, root on your MySQL database is not the same as the root user on your system.  They don't share passwords, or anything else.  It's just coincidence they have the same name.

MySQL ships with a blank root password by default.  You can use the method given above to change it.

You do not need to be the root user on your system (via sudo or anything else) to login to MySQL as root.  You can be any user you want and login to MySQL as anything you want, assuming the account exists.

---

### Post by TheDanMan on 2005-10-17
I think I figured out why this happened.  I upgraded mysql.  While it was working before, it seems to have reset the root password to blank.  Since everything was working fine until I needed to access mysql as superuser.  Though you guys didn't exactly spell out the answer I needed, you still gave me enough to help me figure it out and I thank you.

---

### Post by thoms on 2005-10-20
When I do this, I get

ERROR 1045: Access denied for user: 'root@localhost' (Using password: NO)

---

### Post by transactionlogfiller on 2005-10-20
[QUOTE=thoms]When I do this, I get

ERROR 1045: Access denied for user: 'root@localhost' (Using password: NO)[/QUOTE]

After a default mysql install

mysql -u root
or
mysql -u root -p 
should both work.

After you do this

set password for root = password("passwordhere");

I believe you also need to do 

flush privileges;

for it to take effect

Edit: - the error you described suggests that a password is set and the -p option was not supplied.

---

