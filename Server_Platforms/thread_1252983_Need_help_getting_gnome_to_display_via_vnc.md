---
title: "Need help getting gnome to display via vnc"
date: 2009-08-29
forum: Server Platforms
---

### Post by mastermike14 on 2009-08-29
So i ubuntu desktop 8.04 running on a server that i ONLY have SSH access to. I want to set it up so i can access my server via vnc and have the gnome desktop enviroment come up. Ive installed vnc server so far but when i connect to my server via vnc i get a command line and now gui. Ive got gnome installed already. Can someone please help. Ive searched google but couldnt find anything to get gnome to display via vnc.

---

### Post by braiamp on 2009-08-29
Maybe this article help [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by mastermike14 on 2009-08-29
i found it. I just need to add gnome-session to the xstartup script

---

### Post by phantasmik on 2009-08-29
Just a little suggestion if you are connecting to your server's vnc server outside of your local network, I recommend using SSH tunneling, depending on what port you use run this command on the Client computer:

```
ssh -f -N -L 5901:localhost:5901 youruser@yourdomain
```

if its VNC server 1 default port 5901 so after you run this command when you connect to the server just type in localhost:1

this method is more secure than connecting directly, it helps to keep your password protected over the internet

---

