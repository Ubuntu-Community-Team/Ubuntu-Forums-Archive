---
title: "using sudo without password?"
date: 2009-07-12
forum: Security
---

### Post by MrUmunhum on 2009-07-12
Hi group,

  I have just installed 9.04 and I have a security question.

  In my Fedora system I can remove the 'X' in the /etc/passwd file to bypass the annonying 'enter password' prompt for the sudo command. This does not work with Ubuntu. Is there a way to by pass the password prompt??

---

### Post by kerry_s on 2009-07-12
you use the sudoers file, edit it with "sudo visudo".

i use a few, see pic:

---

### Post by T-Train on 2009-07-12
Edit your /etc/sudoers file.  Below is the line that will allow group YOUR_GROUP sudo privledges with out a password.

%YOUR_GROUP ALL=NOPASSWD: ALL

---

### Post by lovinglinux on 2009-07-12
I suggest you increase the timeout instead of removing the password.

---

### Post by abaden on 2009-07-13
> **lovinglinux said:**
> I suggest you increase the timeout instead of removing the password.

I'll second that. You can accomplish this by simply typing 
```
sudo visudo
```

and then add 
```
passwd_timeout=x
```

to the end of your "Defaults" line (normally something like "Defaults env_reset"). "X" is the number of minutes before your sudo authentication times out. I normally use around 15 minutes on my servers, and 30 minutes on my desktop machines - it all depends on how comfortable you are with your environment.


Alex

---

### Post by Warren Watts on 2009-07-13
The whole purpose of "sudo" is to help prevent accidentally borking your system by entering commands that can wreak havoc on your OS.  

Having to enter a password gives you the opportunity to "think twice" before entering commands with the potential to damage your installation.

Are you SURE you really want to eliminate that opportunity to think a command through by doing away with having to enter a password?

---

### Post by kerry_s on 2009-07-13
certain programs is fine, system wide is just stupid, you might as well be root.

longer timeout ? god forbid your not surfing on line and hit a hidden sudo js while your sudo is still wide open. :lolflag:

i only use no password on gui programs, i try not to for cli commands.

---

### Post by lovinglinux on 2009-07-13
> **kerry_s said:**
> 
longer timeout ? god forbid your not surfing on line and hit a hidden sudo js while your sudo is still wide open. :lolflag:

[NoScript](https://addons.mozilla.org/en-US/firefox/addon/722) ;)

---

### Post by aysiu on 2009-07-13
I'm closing this thread, in accordance with forum policy:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

