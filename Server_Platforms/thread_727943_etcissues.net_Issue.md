---
title: "/etc/issues.net Issue"
date: 2008-03-18
forum: Server Platforms
---

### Post by noahclark on 2008-03-18
Hello,

I'm trying to get my issues.net file working and I've found a [few ]("http://books.google.com/books?id=PyqjvNNltqYC&pg=PA19&lpg=PA19&dq=issue.net+escape+characters&source=web&ots=XChKfz-A6P&sig=KTT7kL0ZoweLLgLJ9A6tCk6EREs&hl=en")   [examples]("http://www.linuxfromscratch.org/blfs/view/svn/postlfs/logon.html") online but they don't seem to help me much.  If I can figure how to get one escape character to work, the rest should be easy.

Thank You!

---

### Post by bigredradio on 2008-03-20
What do you mean working? This is nothing more than a file that is used to display what OS you are on when you log in. In some cases, software installers will use this file to determine your OS when verifying compatibility. You really shouldn't edit it. If you want to make you login behave different, then you need to update your motd file or shell environment. [http://www.understudy.net/custom.html](http://www.understudy.net/custom.html)

---

### Post by koenn on 2008-03-20
> **bigredradio said:**
> This is nothing more than a file that is used to display what OS you are on when you log in. In some cases, software installers will use this file to determine your OS when verifying compatibility. You really shouldn't edit it. If you want to make you login behave different, then you need to update your motd file or shell environment. [http://www.understudy.net/custom.html](http://www.understudy.net/custom.html)

Not exactly :
/etc/motd  is a message displayed to the user **after** login, 
/etc/issue is a message and/or system information displayed **before** login.
(man 5 motd ; man 5 issue; )

software installers shouldn't rely on /etc/issue to determine compatibility, they should call uname. 

> **noahclark said:**
> Hello,

I'm trying to get my issues.net file working and I've found a [few ]("http://books.google.com/books?id=PyqjvNNltqYC&pg=PA19&lpg=PA19&dq=issue.net+escape+characters&source=web&ots=XChKfz-A6P&sig=KTT7kL0ZoweLLgLJ9A6tCk6EREs&hl=en")   [examples]("http://www.linuxfromscratch.org/blfs/view/svn/postlfs/logon.html") online but they don't seem to help me much.  If I can figure how to get one escape character to work, the rest should be easy.

Thank You!
The escape character is a backslash, and apparently you also need to escape end-of-lines if you want multiple lines in issue.

I tried this and it seems to work. \t shows time and \u should show logged-in users
```

Ubuntu 6.06.1 LTS \n \l  \
I get a 2ndl line \
line 3 \
line 4 \
\t \
\u users logged in

```

---

### Post by bigredradio on 2008-03-21
> **koenn said:**
> 
software installers shouldn't rely on /etc/issue to determine compatibility, they should call uname. 


I agree, but it doesn't mean they still do not use it.

---

### Post by koenn on 2008-03-21
and that's where bugs come from.

---

### Post by noahclark on 2008-03-24
Thanks for the help.  I copy and pasted that line into my issues.net file and this is what I get back:

```

Ubuntu 6.06.1 LTS \n \l  \
I get a 2ndl line \
line 3 \
line 4 \
\t \
\u users logged in


```

---

