---
title: "can't login into my account done everything possible"
date: 2015-01-16
forum: System76 Support
---

### Post by Rudwan on 2015-01-16
Cant seem to login into my admin account  on my Ubuntu 14.04 and can only login into my guest account, I have went through all of the posts on the forum and tried everything but still it has been unsuccessful. What should I do ?

---

### Post by kerry_s on 2015-01-16
reboot the computer, after your bios loads, hold shift, it should get you into grub. select rescue-> root

type:
mount -rw -o remount /
passwd your-user-name

put in a new password & you should be good to go.

---

### Post by Rudwan on 2015-01-17
I have changed my password already but still cant login. Whenever I type my old password the screen goes black and for second and still does not login.

---

### Post by steeldriver on 2015-01-17
Can you log in to one of the non-GUI graphical terminals (using Ctrl-Alt-F1 or Ctrl-Alt-F2 etc.)?

If so please do and then let's look at some of your file and directory permissions:
```

ls -ld ~/{,{.X,.ICE}authority}

```

We could also maybe learn something from your .xsession-errors file:

```

tail ~/.xsession-errors

```

---

### Post by Rudwan on 2015-01-17
thank you for the help but sorted out myself by ```
mv ~/.config/xfce4{,.bak}
```
it was a problem with my files in home directory

---

