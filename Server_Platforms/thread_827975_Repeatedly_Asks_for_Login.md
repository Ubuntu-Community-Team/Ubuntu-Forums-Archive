---
title: "Repeatedly Asks for Login"
date: 2008-06-13
forum: Server Platforms
---

### Post by Jerim on 2008-06-13
I am running Ubuntu Server 7.10. When it asks for the login name at the CLI, I type it in and hit enter. Then it comes back up and asks for login name. It never asks for the password.

I have ssh enabled and can log in from there. But the same un/pw I use on ssh won't work on machine. I tried booting from the install CD and getting to a CLI so I could do passwd to reset the password. I still can't seem to login. I don't know why it won't get past login name.

---

### Post by molotov00 on 2008-06-13
Could your keyboard be broken? Maybe a key is stuck.

---

### Post by heebus on 2008-06-13
I have this same exact issue.  It's really annoying.  Especially when I was trying to configure my X11 server.  

Error:
Jun 13 09:58:03 mct060d09 login[4654]: PAM (login) illegal module type: cat
Jun 13 09:58:03 mct060d09 login[4654]: PAM pam_parse: expecting return value; [...>>]
Jun 13 09:58:03 mct060d09 login[4654]: PAM unable to dlopen(/etc/pam.d/login)
Jun 13 09:58:03 mct060d09 login[4654]: PAM [error: /etc/pam.d/login: invalid ELF header]
Jun 13 09:58:03 mct060d09 login[4654]: PAM adding faulty module: /etc/pam.d/login
Jun 13 09:58:07 mct060d09 login[4654]: FAILED LOGIN (1) on 'tty1' FOR `username', Module is unknown

---

