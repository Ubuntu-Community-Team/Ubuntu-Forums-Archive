---
title: "User With a Shorter Password Showing Up"
date: 2018-04-30
forum: Security
---

### Post by naturallywired on 2018-04-30
Hello!  I'm new to Linux and Ubuntu.  I've been getting used to the OS and now I'm researching how to better secure my PC.  One of the problems I have encountered is a new user in Settings --> Users that carries a password that is shorter than the one I made for me.  I just did a system install and noticed it before connecting to anything.  I realize that my setup may be bad somehow but I was wondering if there was anyway I could manually remove the user.  I don't know the password (5 digits).  The user I made has more.  Thanks in advance. :)

---

### Post by deadflowr on 2018-04-30
The password field in System Settings User Accounts only shows 5 asterisks by default.
A security measure so you won't know the actual length.
How many users are listed?

---

### Post by naturallywired on 2018-04-30
Thank you!  That cleared that up.

---

### Post by HermanAB on 2018-05-01
You can enforce the minimum password length requirement in /etc/pam.d/common-password.

Edit this line:
password [success=2 default=ignore] pam_unix.so obscure sha512 minlen=12

The military requires 12 characters minimum.

---

