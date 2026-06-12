---
title: "Help! I removed myself from the sudo group!!"
date: 2007-06-02
forum: Server Platforms
---

### Post by Luft on 2007-06-02
I wanted to create a webmaster group and add myself to it so I issued the following command after creating the group:

usermod -G webmaster eric

I though that it would just add the webmaster group to the list of groups I'm in but instead it replaced my groups with this one.  Now I'm out of the sudo group and can't get back in.  ](*,)

---

### Post by dfreer on 2007-06-02
Try rebooting and selecting the rescue mode in GRUB. This will give you a root prompt and from there you can add yourself to the sudo list.

---

### Post by Luft on 2007-06-02
The install is Ubuntu 7.04 server.  I doesn't  gives me an option of rescue mode.

---

### Post by Luft on 2007-06-02
Wait!  There is a recovery mode!  I'm saved!  Thank you!

:D

---

### Post by dfreer on 2007-06-02
Do you know how to give yourself sudo powers?

---

### Post by Luft on 2007-06-02
Yes, I had a test server so I queried it to see what groups I belonged to and issued the command:
usermod -G adm,dialout,cdrom,floppy,audio,dip,video,plugdev,scanner,lpadmin,admin,webmaster eric

Actually I made a script and testing it so I wouldn't screw things up worse than I already had.  ;)

---

