---
title: "How to define passwordless user?"
date: 2006-09-04
forum: Server Platforms
---

### Post by yitzhakbg on 2006-09-04
I have a script which creates new users. It worked perfectly well under Mandriva 2006, but It breaks under Ubuntu Dapper Drake.
Following are the two options which don't work:

1. User with no password:

passwd -d $username
Either doesn't work in Ubuntu, or at least will somebody show me what to do.

2. Creating a password like this:

echo $userpass |passwd $username --stdin

Can someone please help?

Thanks,
Yitzhak

---

### Post by catlett on 2006-09-04
I am not a scipt writer nor do I have other users on my system, so I do not have anything to offer there. All I wanted to mention was "Are those two commands supposed to be issueed from a root terminal?"
As you know I am sure, there isn't a root terminal in Ubuntu. Instead of su-ing to a root terminal sudo is put before the command in an x terminal.
Does changing it to ```
sudo passwd -d $username
```work?
Or you could add this to your script before the commands, it is a way to get to a root terminal in ubuntu ```
sudo -s -H
``` Sorry to not be of more help and to only be stating the obvious but I saw no other replies and thought maybe it could be a sudo issue.

---

### Post by skymt on 2006-09-04
The version of passwd in Ubuntu doesn't have the --stdin option. It appears to have -d though, so that part should work.

---

### Post by yitzhakbg on 2006-09-05
> **catlett said:**
> I am not a scipt writer nor do I have other users on my system, so I do not have anything to offer there. All I wanted to mention was "Are those two commands supposed to be issueed from a root terminal?"
As you know I am sure, there isn't a root terminal in Ubuntu. Instead of su-ing to a root terminal sudo is put before the command in an x terminal.
Does changing it to ```
sudo passwd -d $username
```work?
Or you could add this to your script before the commands, it is a way to get to a root terminal in ubuntu ```
sudo -s -H
``` Sorry to not be of more help and to only be stating the obvious but I saw no other replies and thought maybe it could be a sudo issue.

Thanks. It seems to be a PAM issue. I'm going to compare the Ubuntu PAM files with the Mandriva ones.

---

### Post by shaulmm on 2006-09-10
u can use chpasswd command with this way:
echo $username:$userpass |chpasswd

you can use the -p option of useradd too BUT you have to create the  encrypted password before.

and you can use "expect" methods too, see:
[http://bash.cyberciti.biz/security/change-password-script.sh.php](http://bash.cyberciti.biz/security/change-password-script.sh.php)

---

