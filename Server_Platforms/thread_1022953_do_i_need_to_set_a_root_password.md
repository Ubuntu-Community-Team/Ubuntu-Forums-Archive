---
title: "do i need to set a root password"
date: 2008-12-27
forum: Server Platforms
---

### Post by enzo12345 on 2008-12-27
I am setting up a web server, and want to make it as secure as possible.

As no root password is set up, do i need to set up a password, or is it more secure having no root account/password?

Thanks.

---

### Post by albinootje on 2008-12-27
> **enzo12345 said:**
> I am setting up a web server, and want to make it as secure as possible.

As no root password is set up, do i need to set up a password, or is it more secure having no root account/password?


By default the root account is disabled in Ubuntu.
Read :  [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by enzo12345 on 2008-12-27
ok thanks

---

### Post by pdtpatrick on 2008-12-27
when you first build upon .. root account is disabled which you can enable by using sudo passwd root from the user account u created while installing the system. However i would recommend you use sudo whenever you want to become a privileged user .. it's more secure especially since you are building a webserver :)

---

### Post by cariboo on 2008-12-27
Just a note, it is against forum policy to tell someone how to enable the root account. If a users knows enough that they need a root password, they also know how to find out how to enable it. Personally I am comfortable with sudo, and when I do work on one of my systems that has the root acount enabled, I keep forgetting about su and try to use sudo instead.

Jim

---

