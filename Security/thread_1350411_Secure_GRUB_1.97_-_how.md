---
title: "Secure GRUB 1.97 - how?"
date: 2009-12-09
forum: Security
---

### Post by jacekadm on 2009-12-09
Hello
I need to secure GRUB v. 1.97 with password
I found info that i must create a file in /etc/grub.d/  called 02_password which contains

 ### BEGIN /etc/grub.d/02_password ###
 set superusers="myuser"
 password myuser mypassword
 ### END /etc/grub.d/02_password ###

 after editing it I must use grub-mkconfig
TO ACTUALIZE CONFIGURATION GRUB FILES 

 unfortunately when I'm trying to use grub-mkconfig I receive an error message
 ### BEGIN /etc/grub.d/02_password ###
 /etc/grub.d/02_password: 3: password: not found

 What am I doing wrong?
I use Xubuntu 9.10

---

### Post by ayenack on 2009-12-09
Take a look at this.

[http://shibuvarkala.blogspot.com/2008/11/howto-password-protect-grub-in-ubuntu.html](http://shibuvarkala.blogspot.com/2008/11/howto-password-protect-grub-in-ubuntu.html)

Be careful though as it's completely possible to bugger your system if you get it wrong.

---

### Post by cariboo on 2009-12-09
I found [this]("http://grub.enbug.org/Authentication?highlight=(password)"), on the grub2 wiki, it may help.

---

### Post by Dr Small on 2009-12-10
Always make a backup of your original files first, elsewhere, incase you ruin your configuration, you then can have something to default to.

---

### Post by bodhi.zazen on 2009-12-10
And understand grub passwords are easily circumvented by someone with physical access.

---

### Post by vahtenberg on 2011-07-28
Have the same problem with grub 1-99-rc1 on ubuntu natty. Any suggestions?

---

