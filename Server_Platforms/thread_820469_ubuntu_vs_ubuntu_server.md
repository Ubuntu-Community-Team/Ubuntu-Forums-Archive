---
title: "ubuntu vs ubuntu server"
date: 2008-06-06
forum: Server Platforms
---

### Post by kripz on 2008-06-06
Are there any differences in the underlying services/kernels etc?

If i install the desktop and remove all programs and the desktop, will i have ubuntu server?

Is it possible to turn off the desktop in the desktop version to save some memory?

If so, can i still connect remotely using vnc (to manage vm software)?

---

### Post by gtdaqua on 2008-06-06
what do u want to achieve? thats important. You dont want to have a server just because you can. What you gonna do with it or simply WHAT DO YOU WANT?

---

### Post by cdenley on 2008-06-06
The difference is that ubuntu server's install cd installs the server kernel by default, and allows you to select different server configurations during the install. It will not install a desktop environment, so when it boots the first time, you will only have a command terminal.

You can always switch kernels, install a desktop environment, or change your server configurations. You can make the desktop version into a server and the server version into a desktop. If you are new to linux or unfamiliar with terminal commands, I would start with a desktop install.

You can disable the desktop environment, but I don't think it uses much memory while you're not logged in. You can't use a vnc client if you don't have an existing X session to connect to.

to configure common server setups
```

sudo tasksel

```

to install the server kernel (probably not needed)
```

sudo apt-get install linux-server

```

to install the ubuntu desktop environment
```

sudo apt-get install ubuntu-desktop

```

to disable your desktop environment from starting automatically
```

sudo update-rc.d -f gdm remove

```

to start your desktop environment
```

sudo /etc/init.d/gdm start

```

to stop your desktop environment
```

sudo /etc/init.d/gdm stop

```

---

### Post by Titan8990 on 2008-06-06
The server kernel is different then the desktop kernal.

Yes, you can remove the desktop from the desktop version with #apt-get purge ubuntu-desktop.

I'm not an expert on VNC but I believe that is used to see graphics on the host computer, not what you want.

SSH would be the best choice. It is also much more secure than VNC (which is known for security flaws).


Edit: Someone beat me to it...

---

### Post by rock lobster on 2008-06-06
> **gtdaqua said:**
> what do u want to achieve? thats important. You dont want to have a server just because you can. What you gonna do with it or simply WHAT DO YOU WANT?

Honestly that is prob the best answer. I like using server with xming and ssh its a little slow over a WAN but its really nice and secure (also gets the job done with little over head and you still get X11, i also have the GUI installed just in case)

---

### Post by kripz on 2008-06-07
I want to run a file/web server. On that server i want to run vm software for some sort of firewall/proxy and also windows XP.

I want to vnc into the windows XP vm or better yet, vnc into the server to control everything.

---

