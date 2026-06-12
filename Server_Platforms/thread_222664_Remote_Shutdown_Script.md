---
title: "Remote Shutdown Script"
date: 2006-07-25
forum: Server Platforms
---

### Post by bricktop on 2006-07-25
Hello,

Ok i need some help. I have two Ubuntu Servers running mutiple VM's. Both servers are connected to a UPS. The ups supports shutdown of 1 server via the rs232 interface, this works fine. It uses a local script to shutdown the server. Is there a way i can utilise the existing script to remote shutdown the other ubuntu server before it shuts down the local machine? I am sure there is a way to d this as i can log into the remote box via ssh.

Anybody?](*,)

---

### Post by philippe_carlo on 2006-07-25
You need to set up ssh for logging in using keys: [http://the.earth.li/~sgtatham/putty/0.55/htmldoc/Chapter8.html]("http://the.earth.li/~sgtatham/putty/0.55/htmldoc/Chapter8.html")

After that, you can write a script that does not need to provide a password to log on and which executes a command on the remote server. You may need to adjust sudo for calling shutdown as a common user without a password prompt (see 'man sudoers').

---

### Post by bricktop on 2006-07-25
Thanks a million, will check it out...

---

