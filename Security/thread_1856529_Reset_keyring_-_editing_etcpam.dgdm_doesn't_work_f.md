---
title: "Reset keyring - editing /etc/pam.d/gdm doesn't work for me!"
date: 2011-10-08
forum: Security
---

### Post by MonocleMike2 on 2011-10-08
Description:    Ubuntu 11.04
Release:    11.04
Codename:    natty

I have read the article about including the line
@include common-pamkeyring
at the end of /etc/pam.d/gdm and if I do then I can't login at all! The login screen just loops asking me to select the user!  I then have to reboot into recovery mode without the graphical screen and take the line out again.  I don't want or need the security.  I want to just turn it off.  I've tried system/preferences/passwords and system keys but cannot see which one to delete.
Help please :)

---

### Post by FuturePilot on 2011-10-08
What are you trying to do? Auto login? You can do that by opening the unity panel and typing in "login" and setting autologin from there.

---

### Post by MonocleMike2 on 2011-10-09
I am trying to suppress the frequent messages asking for my key ring password.  I am not trying to autologin.  I can't use Unity as my hardware is too old.  I have avoided the keyring problem on new users by entering a blank password when first asked to set it up and accepting the option to use unsafe passwords.  I would like to do the same for an existing user but don't know how either within the graphical interface nor from the command line.

---

### Post by matt_symes on 2011-10-09
Hi

Is the password for the keyring the same as the login password ?

Kind regards

---

### Post by MonocleMike2 on 2011-10-09
Hi,

Yes.

Regards

---

### Post by matt_symes on 2011-10-09
Hi

Can't you change it to a blank password using seahorse ?

Open a terminal and type

```
seahorse
```Right click on the password placeholder and select 'change password' and change it to a blank password.

Will that not work for you ?

What is the name of the password placeholder ? default ? login ?

Kind regards

---

### Post by MonocleMike2 on 2011-10-09
Thank you.  That appears to have solved it.  I had got to that dialogue screen via System/Preferences/Passwords and Encryption Keys but I didn't know about the functionality of the right click.  Simple when you know how but I'm still a newbie
Thank you again.

---

