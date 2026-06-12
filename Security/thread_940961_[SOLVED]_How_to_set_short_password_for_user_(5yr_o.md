---
title: "[SOLVED] How to set short password for user (5yr old son)"
date: 2008-10-07
forum: Security
---

### Post by estevez on 2008-10-07
Hello, after upgrade from drake to hardy and some tweaking its seems that whole family can switch to the new system, but there are still few minor things left... like default password policy. 

I had separate accounts for me (the master and maintainer :), my wife and my kids. I need to set short plain password for my sons, just few chars to teach them good habits. 6+ chars is too much for them. How I can change default hardy behavior?  

Thank you

---

### Post by estevez on 2008-10-07
solved. just better search through this forum revealed that:

edit in file: /etc/pam.d/common-password

line: password required pam_unix.so nullok obscure md5 

to: password required pam_unix.so nullok min=3 md5 

is what i need.

---

### Post by sisco311 on 2008-10-07
you can set a non secure password, as root:
```
sudo passwd *username*
```

changing(system wide) the lenght of the password is not secure.

---

### Post by estevez on 2008-10-07
thank you for advice. any risk, if only my account is in admin group? for my sons is possibility to change their own password  fairly important .-)

---

### Post by sisco311 on 2008-10-07
in your case the risks are negligible.
you can read more about security [here]("http://ubuntuforums.org/showthread.php?t=765421")

EDIT:
Please mark the thread solved by selecting 
**Mark this thread as solved** from the [COLOR="Red"]**Thread Tools**[/COLOR].

---

