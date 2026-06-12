---
title: "Auto login as root in terminal mode"
date: 2012-05-03
forum: Server Platforms
---

### Post by wkevin on 2012-05-03
Hi,
I have a server running ubuntu. This server is **not** connected to the outside world, so there is no
security issues,
My question is: I work with this server only in terminal mode, not in X windows. 
Is there a way to configure an automatic boot, so when I perform  a restart, it will
automatically login into terminal mode, without any need to enter username and password ? 

regards,
Kevin Wilson

---

### Post by Jonathan L on 2012-05-03
Hi Kevin

> I have a server running ubuntu. This server is **not** connected to the outside world, so there is no
security issues,
My question is: I work with this server only in terminal mode, not in X windows. 
Is there a way to configure an automatic boot, so when I perform  a restart, it will
automatically login into terminal mode, without any need to enter username and password ? 

I wouldn't advise it but ... the login process is started by /etc/init/tty*.conf, and you could run a shell instead of getty.

It is frankly mighty strange! What would you want that for?

If you want to start programs when you reboot, the usual way is /etc/init.d/ or even /etc/rc.local; for running them periodically the usual way is crontab.

Hope that's helpful.

Kind regards,
Jonathan.

---

### Post by wkevin on 2012-05-04
Jonatahan, thanks for your reply.

>I wouldn't advise it but ... the login process is started by /etc/init/tty*.conf, and you could run a shell instead >of getty.

Could you/somebody else be more specific and tell what exactly I should do ? or simply 
show contents of one of the  /etc/init/tty* files which enable automatic login without entering
usename and password?

rgs
Kevin

---

### Post by Jonathan L on 2012-05-04
Hi Kevin

Not knowing what you really want to achieve makes it difficult to be concrete.

I still wouldn't advise it but ...

1.  Use Single User mode.  Either by getting the grub menu (press ESC) or editing /boot/grub/grub.cfg, you add "single" to the line you want to use.  This is easy, but you might not have all of the system running that you wanted (printer daemons, etc).

2.  Remove getty.  You edit /etc/init/tty1.conf so that it doesn't run getty, it runs a shell.  This will be tricky, because getty is responsible for getting the tty in the right mode and so on,  so you have to get the redirections right, but when you do, the whole system will be running properly.

3.  Get the source of getty and modify it so it doesn't need a login.  If you can program in C, this is much easier than 2; if you can't, it's much harder.

I'll repeat I don't think it's a good idea.  What are you doing that means you can't log in as root, once, and stay logged in?

My curiosity is piqued!

Kind regards,
Jonathan.

---

