---
title: "Password policy for all users"
date: 2009-10-30
forum: Security
---

### Post by yeleek on 2009-10-30
Hi,

Tried searching for this - can't find it.  How can I set a password policy that effects not just all local accounts, but all new accounts which maybe created?

Thank you

---

### Post by cariboo on 2009-10-30
Have a look at this [document]("https://help.ubuntu.com/8.04/serverguide/C/user-management.html"), it should answer your questions.

---

### Post by yeleek on 2009-10-31
Thanks - I guess what I'm looking for (perhaps doesn't exist) is the ability to specify:

Max age of password
Min age of password
Min length of password
Max number of incorrect logins before lockout
How long lockout lasts
Interval for counting tries between attempts for lockout.

I hate to say it - but very similar to the password policy that can be specified in a Windows GPO or LGPO...

Any ideas?

Thank you

---

### Post by cariboo on 2009-10-31
Check the section Called Password Policy, you can do everything you just asked about.

---

### Post by yeleek on 2009-11-01
Hi,

Err...  That page doesn't cover the same functionality as a windows password/lockout policy.  I'm looking for this

[IMG]http://www.windowsecurity.com/img/upl/image0021239706222782.jpg[/IMG]

and

[IMG]http://www.windowsnetworking.com/img/upl/image0021093937291603.jpg[/IMG]


Is this functionality (lockouts etc) documented elsewhere then?

Thanks

---

### Post by yeleek on 2009-11-02
Anyone?  thx.

---

### Post by yeleek on 2009-11-03
bump

---

### Post by cariboo on 2009-11-03
Have a look at:

```
man passwd
```

It will show the commands needed to do most of what you want. There is no gui to accomplish it though

---

### Post by cashbank on 2009-12-10
My password has locked me out when I try to logon to ubuntu. Should I change the settings in Windows. I have a Vista os, and I can not find this directory.  Is there a way to by pass the password?:(

---

### Post by oldos2er on 2009-12-10
You can reset it: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

