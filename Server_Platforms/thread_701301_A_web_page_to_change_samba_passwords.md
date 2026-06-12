---
title: "A web page to change samba passwords?"
date: 2008-02-19
forum: Server Platforms
---

### Post by Rich99 on 2008-02-19
I use dapper drake as a fileserver for windows clients using samba.  Security is through username/password.  I would like a way for users to be able to change their own samba passwords through a web interface. Is there a way to do this?  Users don't need access to anything (shell etc) other than samba, so I don't want them to know or be able to change their unix password.  SWAT allows you to change your samba password, but you have to authenticate with your unix password first. I don't want users knowing their unix password.

Any ideas?

---

### Post by kidders on 2008-02-20
Hi there,

I suppose you could throw together a quick perl/PHP/etc script that called smbpasswd, as you would if you were going to change someone's password manually. I would suggest running Apache (out of convention) or lighttpd (for efficiency) over SSL, to keep your users' passwords reasonably safe.

---

### Post by aknight_sa on 2008-03-10
> **Rich99 said:**
> I use dapper drake as a fileserver for windows clients using samba.  Security is through username/password.  I would like a way for users to be able to change their own samba passwords through a web interface. Is there a way to do this?  Users don't need access to anything (shell etc) other than samba, so I don't want them to know or be able to change their unix password.  SWAT allows you to change your samba password, but you have to authenticate with your unix password first. I don't want users knowing their unix password.

Any ideas?

i am having the same situation as you have here..i just wanted to know if you have been able to work this out or not? and if you did what did you do?

thanks

---

### Post by netlogic on 2008-03-10
You can try usermin.

---

