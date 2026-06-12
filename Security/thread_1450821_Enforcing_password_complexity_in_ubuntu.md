---
title: "Enforcing password complexity in ubuntu"
date: 2010-04-09
forum: Security
---

### Post by computerman on 2010-04-09
I must be losing it because I can't seem to find my answer on the google mechine. I need to enforce password complexity in ubuntu. I need min length, upper case, number and or special characters. I don't want to have to install pam_cracklib on all these boxes. I have looked at he common-password and it's not much help. Thanks for any help you can give.

---

### Post by cdenley on 2010-04-09
The pam_unix.so module can enforce a minimum character length, and the obscure option enforces complexity "based on the length of the password and the number of different types of characters (alpha, numeric, etc.) used".

```

man pam_unix

```

---

### Post by HermanAB on 2010-04-10
The PAM complexity system is more intelligent than the Windows one.  You can trade off complexity for length.  So you can either use say a 9 character password with complexity, or a 12 character password without.

---

### Post by computerman on 2010-04-14
Thanks guys for your response, I did look at the man page for pam_unix and I made changes in common-auth but It didn't work. What is the config file that I need to modify?

Thanks Again

---

### Post by cdenley on 2010-04-14
I believe you have to modify /etc/pam.d/common-password.

---

### Post by computerman on 2010-04-14
I made a change to common-password to include obsure and min=6 which is the default but when i do a passwd it lets me change a password to 1 character and they can all be for example aaaa. Its like the defaults don't work. I built a vmware of ubuntu 9.10 from scratch for this too and I get the same results. Any Ideas? Thanks!

---

### Post by cdenley on 2010-04-14
> **computerman said:**
> I made a change to common-password to include obsure and min=6 which is the default but when i do a passwd it lets me change a password to 1 character and they can all be for example aaaa. Its like the defaults don't work. I built a vmware of ubuntu 9.10 from scratch for this too and I get the same results. Any Ideas? Thanks!

It works fine for me. Are you running the "passwd" command as root? The root user seems to be exempt from those restrictions.

---

### Post by computerman on 2010-04-14
Wow your right, I tried it as a normal user and wham it won't let me change it. I'm not sure I like that though. Root should still have those restrictions applied to it. Thanks for your help again!

---

### Post by LumbeeNDN on 2011-09-08
Hopefully I will save someone else some pain with this. To set the minimum password go into 
/etc/pam.d/common-password and find this line...

password        [success=1 default=ignore]      pam_unix.so obscure sha512

...make it look like this....

password        [success=1 default=ignore]      pam_unix.so obscure sha512 min=6


DO NOT simply add 'min=6' to the end of the this file. I did this and it locked me out of the server!

---

