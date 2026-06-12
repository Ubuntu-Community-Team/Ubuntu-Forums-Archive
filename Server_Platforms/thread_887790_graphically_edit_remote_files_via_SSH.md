---
title: "graphically edit remote files via SSH"
date: 2008-08-12
forum: Server Platforms
---

### Post by eggdeng on 2008-08-12
On Dapper, (Edgy, Feisty, Gutsy too AFAIK) it was possible to use the Connect to Server applet to edit remote files over SSH using a text editor like gedit.
All you had to do, once the remote folder was mounted, was click on the remote file, supply the password again and then edit and save directly. However, this invaluable functionality sems to be lost in Hardy. On the last step, the password prompt simply comes back up again.
A couple of bug reports are quietly gathering dust on launchpad but there seem to be no solutions. Any ideas, workarounds, alternatives?

---

### Post by FakeOutdoorsman on 2008-08-12
I use sshfs to connect to a headless development server.  It basically allows me to mount the remote folder and then work on it like it is a local folder.  I can then edit the mounted files with any program on the client machine:
```
sshfs frink@192.168.1.175:/var/www/htdocs ~/tarkin
```

---

### Post by HermanAB on 2008-08-12
ssh -X -C -c blowfish root@server "gedit /etc/fstab"

Cheers,

Herman

---

### Post by tagra123 on 2008-08-12
I use something similar to HermanAB

ssh -X -C -c blowfish username@server

once connection is established you can use nautilus to browse, edit files etc...

just type in nautilus  or another application once the connection is made.

---

### Post by FakeOutdoorsman on 2008-08-12
> **HermanAB said:**
> ssh -X -C -c blowfish root@server "gedit /etc/fstab"

Cheers,

Herman
Doesn't this work only if the remote server has an X server and whatever program you want to run installed on that remote server?

---

### Post by eggdeng on 2008-08-12
Many thanks for the suggestions & sorry for not being more specific. I haven't looked at blowfish as the server in question isn't running a GUI & the only text editor available is vi. So I followed FakeOutdoorsman's suggestion to use sshfs & bang! Fixed! :)

---

### Post by HermanAB on 2008-08-12
Note that you don't need an X server on the remote system.  SSH uses the X server of the local system.  The X server is the thing that handles the screen keyboard and mouse, so it has to run on the local machine and doesn't have to run on the remote machine.  

My example requires that gedit for example is installed on the remote machine, which is interesting, because gedit is an X application.  Even though the remote machine has no X server it will run through SSH, since it uses the local X server - Magic!

Cheers,

Herman

---

