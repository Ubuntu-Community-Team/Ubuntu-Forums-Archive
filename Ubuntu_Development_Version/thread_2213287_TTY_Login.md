---
title: "TTY Login"
date: 2014-03-25
forum: Ubuntu Development Version
---

### Post by tad1073 on 2014-03-25
I am unable to login to TTY 3, I get an incorrect password notification but I can login into my desktop with the same password.

---

### Post by james114 on 2014-03-26
Check out your keymap configuration, perhaps it is wrong for the tty.
Try entering your password when you're prompted for your username and see if the characters turn out right


Changing the console font:
```
sudo dpkg-reconfigure console-setup
```


And then choose the right layout there. 
You might have to reboot to take effect.

---

### Post by tad1073 on 2014-03-27
The characters are right.

---

### Post by pqwoerituytrueiwoq on 2014-03-27
using numlock? sometimes when switching to a TTY the led stays on but numlock is off, hit the key a few times to get the lled synced and in the right setting

---

### Post by Iowan on 2014-03-27
Any other TTY's work?
I haven't searched why, but I can't login via TTY1 - although TTY3 works
[http://askubuntu.com/questions/205121/cannot-login-to-any-ttys-wrong-password](http://askubuntu.com/questions/205121/cannot-login-to-any-ttys-wrong-password)

---

### Post by tad1073 on 2014-03-27
None work for me, I'm not using the # pad.

---

### Post by pqwoerituytrueiwoq on 2014-03-28
caps lock?

---

### Post by tad1073 on 2014-03-29
nope, no caps lock

---

### Post by steeldriver on 2014-03-29
What exactly is the "incorrect password notification" that you're getting? is your home directory encrypted?

AFAIK the only message you should get from a failed PAM login attempt is "Login incorrect", at least in my locale (i.e. it isn't specific about whether the password was incorrect, or the login account name). If you are getting a different message maybe that will give us some clues?

---

### Post by pqwoerituytrueiwoq on 2014-03-29
type your password as your username and make sure it look right, maybe it is a keyboard setting issue

---

