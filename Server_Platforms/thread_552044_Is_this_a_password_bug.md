---
title: "Is this a password bug?"
date: 2007-09-16
forum: Server Platforms
---

### Post by cbozic on 2007-09-16
I have made some changes in /etc/pam.d/common-password but they don't seem to be reflected in the User Manager GUI, useradd, or passwd.  Is this a bug or am I missing something?  I'm very new to PAM so this is probably just something I'm doing wrong.  However, I've spent days in the documentation for PAM and I still can't figure out why my changes don't seem to appear.  Can anyone help here?

Thanks,
Chris Bozic

---

### Post by Koybe on 2007-09-16
Maybe you should post your conf there so we can have a look. Anyway pam does not require any service restart or something. Everything should be enable once the file has been save. In that way you should always manage to have a root console open somewhere when you're changing your pam... just in case ;-)

Don't forget that the ordrer of the lines in the pam files are important.

---

### Post by cbozic on 2007-09-16
Thanks for the reply.  Here is my /etc/pam.d/common-password

```
#
# /etc/pam.d/common-password - password-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define  the services to be
#used to change user passwords.  The default is pam_unix

# The "nullok" option allows users to change an empty password, else
# empty passwords are treated as locked accounts.
#
# (Add `md5' after the module name to enable MD5 passwords)
#
# The "obscure" option replaces the old `OBSCURE_CHECKS_ENAB' option in
# login.defs. Also the "min" and "max" options enforce the length of the
# new password.

#password   required   pam_unix.so nullok obscure min=8 max=8 md5

# Alternate strength checking for password. Note that this
# requires the libpam-cracklib package to be installed.
# You will need to comment out the password line above and
# uncomment the next two in order to use this.
# (Replaces the `OBSCURE_CHECKS_ENAB', `CRACKLIB_DICTPATH')
#
password requisite	  pam_cracklib.so retry=3 minlen=8 difok=3
password required	  pam_unix.so use_authtok nullok md5

```

As you can see, I simply followed the directions in this file and uncommented the two cracklib lines and commented out the previous configuration without cracklib.  The cracklib pam package is also installed.  All I am trying to do at this time is force a password to be 8 characters long.  Once that is working with cracklib, I would like to use some more of the cracklib features to improve password complexity.

Is my configuration valid or should I post a bug?

Thanks,
Chris Bozic

---

### Post by HermanAB on 2007-09-16
Hmm, did you restart everything?

Cheers,

H.

---

### Post by cbozic on 2007-09-16
Yes, I did reboot and still my changes still aren't in place. This seems like it may be a bug to me but I am so new to PAM and cracklib that I can't be totally certain until I get some more feedback.  

BTW...  I've tried this on both Feisty and Dapper with no success.

---

### Post by cbozic on 2007-09-16
I posted this as a bug just to be safe.  

[https://bugs.launchpad.net/ubuntu/+source/pam/+bug/139999](https://bugs.launchpad.net/ubuntu/+source/pam/+bug/139999)

---

### Post by Koybe on 2007-09-16
Yes I can't help. 
Do you have anything in your log that can give us some more information? And I can't get to your launchpad entry.

I have no idea as I'm not using cracklib. But maybe there is a default file to enable. You can have a look in /etc/default and be sure there is nothing related to this.

[Maybe a way to help]("http://www.2sheds.ru/blog/2007/03/generate-cracklib-word-library-on-ubuntu-linux/")

---

