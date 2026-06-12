---
title: "VNC via SSH password authentication"
date: 2008-03-30
forum: Server Platforms
---

### Post by Jeztastic on 2008-03-30
Hi

I am trying to get a VNC connection going over SSH. My server is an Xubuntu machine, and client is Vista SP1.

My SSH connection is working fine, but I cannot connect over VNC, as my password is not authenticating. I have been using this guide.

[http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/6](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/6)

Any help much appreciated, as I am nearly there!

Thanks,

Jez

---

### Post by eldragon on 2008-03-30
first off? how are you starting the tunnel?

since you are using vista, i'll asume you are using putty

start putty with: putty -L 5900:localhost:5900 username@password

check that after connecting, there is no error while creating the tunnel.

then just try to connect the vncviewer @ localhost

if this is what you are doing, and still have problems.

try disabling from the vista's network connection, the topology and discovery services it comes. you could also disable ipv6 which is useless right now.

another thing to test: try to connect to the server, from the server, and make sure the vnc server is actually working 

EDIT


this is how i did it here: [http://ubuntuforums.org/showthread.php?p=3554778#post3554778](http://ubuntuforums.org/showthread.php?p=3554778#post3554778)

its a small step by step with same server. 

one las question: why do you want vnc authentication, if you will be tunneling into your server? you could block all ports at the router / firewall except for 22 and still connect, withouth the need to enter a second password to vnc into the server

---

### Post by croto on 2008-03-30
Ok, let's see if you can connect *without* a password. Instead of
```

#!/bin/sh
x11vnc -nap -bg -many -rfbauth ~/.vnc/passwd -desktop "VNC ${USER}@${HOSTNAME}" \
|grep -Eo "[0-9]{4}">~/.vnc/port

```

try this:
```

#!/bin/sh
x11vnc -nap -bg -many  -desktop "VNC ${USER}@${HOSTNAME}" \
|grep -Eo "[0-9]{4}">~/.vnc/port

```
 
and try to connect. If this works, maybe something went wrong when you created the password with "vncpasswd ~/.vnc/passwd". Make sure that file exists after you issue the command.

---

### Post by krunge on 2008-03-30
> **Jeztastic said:**
> Hi

I am trying to get a VNC connection going over SSH. My server is an Xubuntu machine, and client is Vista SP1.


If you want to, you can give SSVNC a try:  [http://www.karlrunge.com/x11vnc/ssvnc.html]("http://www.karlrunge.com/x11vnc/ssvnc.html")

It will start up the Putty link automatically and then start the VNC viewer going through the SSH tunnel.  It is a little klunky, but it works.

Just click on 'Use SSH' and enter  username@hostname:0 (or similar) and then click 'Connect'.  You can even have it start x11vnc, if that is your VNC server. Let me know if you have any questions or problems.

---

### Post by Jeztastic on 2008-03-31
Thanks for jumping in everybody.

Removing the password login from share11vnc made no difference - I was still asked for the password :confused: I don't need to reboot after changing a script do I? 

Running tightvnc veiwer on loopback, I was still asked for a password and refused authentication.

Anyway, I deleted .vnc, uninstalled x11vnc and started again. When I reinstalled x11vnc, and ran ```
vncpasswd ~/.vnc/passwd
``` I was told I did not have .vnc, and that I needed to install vnc4-common. This I did, and ran  ```
vncpasswd ~/.vnc/passwd
``` sucessfully (the terminal asked me to enter and confirm password). However, I still do not have a .vnc directory. :confused:

Please help!

---

### Post by croto on 2008-03-31
Hey,

.vnc is a hidden directory. I don't remember how to tell the file manager to show hidden files (there must be a hotkey, or the menus...). On the terminal, type 
```

ls -a ~

```
to show all files, including hidden files and directories. Yoy should see it there. To see the contents of that directory, try:
```

cd .vnc
ls

```

After you removed the password login from share11vnc you don't have to reboot, you just have to restart the x11vnc service. Of course, restarting the computer would work too.

---

