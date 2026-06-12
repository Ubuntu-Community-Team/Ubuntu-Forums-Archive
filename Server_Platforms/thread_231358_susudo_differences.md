---
title: "su/sudo differences?"
date: 2006-08-07
forum: Server Platforms
---

### Post by jkh107 on 2006-08-07
This may sound like a stupid question, but what is the big difference between Ubuntu-style sudo and the use of su in other distributions? I understand which users and passwords get used when in both set-ups, but I don't understand how one is of any benefit over the other. The Ubuntu wiki says that the sudo account should be protected in the same way as the root account, which I take to mean that you shouldn't log on as a member of the admin group on a regular basis. So what is the real difference between having a root password and a regular user (for example, Fedora's default) and having a sudo/admin group user and a regular user (like in Ubuntu)?

---

### Post by MrHorus on 2006-08-07
> **jkh107 said:**
> This may sound like a stupid question, but what is the big difference between Ubuntu-style sudo and the use of su in other distributions?

su allows you so Switch User if you pass a username as an arguement or switch to root if you run it by itself and you will hold those privilages until you type `exit`.

sudo will allow you to run a programme AS root but you will lose those shell privs after a period of time and/or once the programme terminates.

---

### Post by aysiu on 2006-08-07
You can log in as a sudo user as many times as you want. The sudo user doesn't have administrative privileges unless she uses the command *sudo* or *gksudo* or *kdesu*--which is authenticated with a password. Otherwise, she's a user just like any other user.

---

### Post by jkh107 on 2006-08-08
Thank you, that was very helpful.

---

### Post by underthehour2000 on 2007-03-16
:popcorn: pop quiz....

Could some 1 be so kind to explain the difference between....

gksudo & sudo then?

Cheers

---

### Post by aysiu on 2007-03-16
> **underthehour2000 said:**
> :popcorn: pop quiz....

Could some 1 be so kind to explain the difference between....

gksudo & sudo then?

Cheers
Yes.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by SjRaptor on 2007-03-16
'sudo' provides accountability for users who would otherwise require root privileges. When a user has sudo access, it doesn't automatically give them privileges to do everything or anything root can do.

For example, you want to give a user privilege to change the IP addresses of the system. To do so, they require root privileges. Instead of giving them a root account, with sudo, you can give the user privilege to change the IP address using 'ifconfig' but nothing else. When a user executes a sudo command, the action is logged, timestamped, and whether they were successful or denied privilege.


Oh, and btw.. su is the command to switch user. Without invoking a username, it defaults to super-user.

See the [sudo man page](http://sudo.ws/sudo/man/sudo.html) for more information

---

### Post by Geffers on 2007-09-08
Thanks for info.

Geffers

---

### Post by azurepalm on 2007-12-20
what is the default su password?

i tried entering my sudo password and it fails.

---

### Post by aysiu on 2007-12-20
> **azurepalm said:**
> what is the default su password?

i tried entering my sudo password and it fails.
There is no default *su* password. The root account is disabled for logins.

If you have several commands you want to run as root, try ```
sudo -i
```

---

### Post by goliar on 2008-01-10
Well, I would think that one of the**[COLOR="Red"] biggest security-related advantages[/COLOR]** of **sudo** is that the given (non-privileged) user can execute a high-privilege operation WITHOUT knowing the root password and WITHOUT ever having a need to type it somewhere. _What you don't know you can't expose_.
That's also a big difference to Windows which has, natively, only **runas **(a rough equivalent of **su**) - which forces the user to expose the password for the privileged account everytime it is used.

Peter

---

