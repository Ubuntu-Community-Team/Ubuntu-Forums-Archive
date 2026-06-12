---
title: "[SOLVED] Yet another mysql root password problem"
date: 2007-10-07
forum: Server Platforms
---

### Post by volkswagner on 2007-10-07
Please help, I am still configuring a new LAMP install Ubuntu 6.06.

I am pretty sure I set up my standard password during the Mysql install.  

I do get the dreaded 1045 error when trying to log into Mysql using root user.

Strangely when following other posts refer to reset password, I have issues..

Following these instructions [https://help.ubuntu.com/community/MysqlPasswordReset]("https://help.ubuntu.com/community/MysqlPasswordReset")

when i get to 
```

   /usr/bin/mysqld --skip-grant-tables --user=root
```

no file so i use

```
mysqld --skip-grant-tables
```

after this entry I do not get a return prompt.  I have seen in another post where they had the same problem and solved by stopping the command.

How do I stop the command.  

Note;  This happens both at the server and when remote through ssh.

Also after the command was entered I was able to log into Mysql via webmin.
While logged in I could see the list of users and the encrypted passwords.

I tried to add another user with all privledges and was "kicked" off.  The next time I was able to log in with the new user and password but not a superuser.

I am a complete newbie so be gentle.

If i can replicate the condition with webmin, can I make more use of the information.
Such as the encrypted password.  
I will try to add another user with the same password I used in the root account during setup, then compare the encrypted code to see if they match?

Thanks in advance.   

I have been reading and trying to implement what I have found to no avail.  Hence this new post.

---

### Post by volkswagner on 2007-10-07
Update:  I created a new user with all permissions (via method described earlier). I then logged back in to mysql via new user to check the encrypted passwords.  The passwords do not match so I do not know the root password. 

Can I delete both root users then recreate them via webmin?  

Will this cause more problems?

---

### Post by volkswagner on 2007-10-07
Newbie figured the error of his ways.

While staying up way too late to intall server....one too many copy and paste commands.

I did not edit or creat my own password when pasting
```

mysqladmin -u root password yourrootsqlpassword
```

```
mysqladmin -h server1.example.com -u root password yourrootsqlpassword
```

Dope!

---

### Post by koenn on 2007-10-08
> **volkswagner said:**
> Newbie figured the error of his ways.
...
Dope!

Good one !

---

