---
title: "Unauthorised access to root account"
date: 2005-03-21
forum: Server Platforms
---

### Post by jorgegcab on 2005-03-21
I've had a security thread recently, with an unauthorized access to root account with physical access to the computer. 

Lastlog reports a root session init on TTY2. AFAIK this is not possible, as root sessions are only possible from sudo.

I know, Iknow. You can't tell how that can be done, but is there another reason to have this session reported other than a real one?

Thanks

Jorge Garcia

---

### Post by nemin on 2005-04-02
[QUOTE=jorgegcab]I've had a security thread recently, with an unauthorized access to root account with physical access to the computer. [/QUOTE]
I just want to mention you can't trust any file on your computer (only those on physically read-only devices) after an unauthorized root access, so neither your lastlog...

---

### Post by randy on 2005-04-10
But if someone gained sudo access to your box they could enable root logins.

---

### Post by Xgates on 2005-04-11
[QUOTE=randy]But if someone gained sudo access to your box they could enable root logins.[/QUOTE]


I like that analogy, logic it sounds like trying to be justifed in something:

'If someone gained sudo access'   LOL, having SUDO only means to be a user. If someone gained the user account, user password they'd have SUDO.

Sudo=Bad Security

---

### Post by nocturn on 2005-04-12
Check /etc/shadow to see if there is a root password set.

You can also run rkhunter to check if there are rootkits present, maybe they planted a backdoor to have remote access too.

---

### Post by graigsmith on 2005-04-19
[QUOTE=Xgates]I like that analogy, logic it sounds like trying to be justifed in something:

'If someone gained sudo access'   LOL, having SUDO only means to be a user. If someone gained the user account, user password they'd have SUDO.

Sudo=Bad Security[/QUOTE]
 not especially, i gave my friend a user account and made it so he can't use sudo.  whenever you create a new user from the gnome users and groups thing.  when you add a user, the last tab that comes up, you can disable allowing running of system admin tasks, which makes sudo impossible from that account.  All user accounts are not created equal.

---

### Post by nautilus on 2005-04-22
oi, new users don't just 'get' sudo, the admin (root) must add them to the sudoers file explicitly.

c'mon, *slap*.

but yeah, sudo strikes me as insecure, too.

---

