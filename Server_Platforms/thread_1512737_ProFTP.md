---
title: "ProFTP"
date: 2010-06-18
forum: Server Platforms
---

### Post by Joeasaurus on 2010-06-18
Hi,
I am aware that with ProFTP I can set:
```
DefaultRoot    ~
```
in the config file to lock users to their home directories but I want to  do something slightly different.

I have a structure set up where each user has their own folder within  /var/www/. I want to lock FTP users to their respective /var/www/  directories instead of their home directories. Is this possible?

Thanks!
[COLOR=Black]:qw[/COLOR]

---

### Post by fang0654 on 2010-06-18
Do their home directories need to be in /home?  You can have their home directories the same as the /var/www.

Edit /etc/passwd to change the home directories.

---

### Post by Ryan Dwyer on 2010-06-19
I don't think that's a wise idea. Programs will try to write to something like ~/.config and you'll have all these unnecessary files in your www directory.

You could try using a variable, eg. DefaultRoot /var/www/%u. You'll need to look up what the variable actually is though.

You might also be interested in enabling Apache's userdir module. It takes any request in the format [http://host/~username/](http://host/~username/) and will read it from /home/username/public_html/. That way you don't have to change your FTP chroot, and they can also store files outside public_html if they wish.

---

### Post by Joeasaurus on 2010-06-21
> **Ryan Dwyer said:**
> I don't think that's a wise idea. Programs will try to write to something like ~/.config and you'll have all these unnecessary files in your www directory.

You could try using a variable, eg. DefaultRoot /var/www/%u. You'll need to look up what the variable actually is though.

You might also be interested in enabling Apache's userdir module. It takes any request in the format [http://host/~username/]("http://host/%7Eusername/") and will read it from /home/username/public_html/. That way you don't have to change your FTP chroot, and they can also store files outside public_html if they wish.

Thanks for this, Very helpful :)

---

