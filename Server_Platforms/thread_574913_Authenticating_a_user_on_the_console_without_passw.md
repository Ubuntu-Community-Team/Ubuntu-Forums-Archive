---
title: "Authenticating a user on the console without password"
date: 2007-10-13
forum: Server Platforms
---

### Post by Sodki on 2007-10-13
Hello,

I can configure GDM to allow graphical logins without password to certain users, using PAM. Is there a way to allow those users to do the same in the console? I want to be able to insert my username and sucessfully login without having to enter a password and I don't want to use an empty password.

Thank you.

---

### Post by zekica on 2007-10-13
You can change user's password using passwd, and using -d switch, you can make it passwordless - it won't even ask for it. This is almost exactly what you want.

---

### Post by John Bennett on 2007-10-20
I used...

```
sudo passwd -d username
```

for each of my users, but the gdm graphical login still requires a password for each user.

This may be a solution, but I've not tried it yet...

[http://www.nabble.com/forum/ViewPost.jtp?post=11023778&framed=y](http://www.nabble.com/forum/ViewPost.jtp?post=11023778&framed=y)

---

