---
title: "ssh server and automatic gnome logins"
date: 2007-06-10
forum: Server Platforms
---

### Post by mopi on 2007-06-10
Hi all.

I have enabled automatic login on my desktop pc using:
System -> Administration -> Login Window.
Security Tab -> Enable Automatic Login (Checked)

This is described in [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_automatic_login_into_GNOME_.28not_secure.29]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_automatic_login_into_GNOME_.28not_secure.29") as not secure. I understand that it's not secure if you have local access to the computer but what about running an ssh server on the same machine? I assume gnome must store the password somewhere to be able to log in. Is this password in any way readable by ssh users?

Thanks in advance.

---

### Post by Ek0nomik on 2007-06-10
The password is encrypted.  Also, if a user did have your personal user name and password, they would need the administrator (sudo) password to be able to harm any system files, and this is also encrypted (but I can't seem to find where these files are stored, but maybe that's a good thing.  ;))

---

