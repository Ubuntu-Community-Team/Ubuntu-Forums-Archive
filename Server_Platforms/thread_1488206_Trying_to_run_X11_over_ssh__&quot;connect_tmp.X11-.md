---
title: "Trying to run X11 over ssh:  &quot;connect /tmp/.X11-unix/X0: No such file or directory&quot;"
date: 2010-05-19
forum: Server Platforms
---

### Post by u-slayer on 2010-05-19
I'm trying to run X11 windows over ssh but I get this error:

```

ssh -X -C server@192.168.1.103
Warning: No xauth data; using fake authentication data for X11 forwarding.
server@server:~$ xclock
connect /tmp/.X11-unix/X0: No such file or directory
Error: Can't open display: localhost:10.0

```

I managed to connect with another computer. That computer has a /tmp/.X11-unix/X0 socket. Is there a way to create a socket on this computer?

---

### Post by u-slayer on 2010-05-20
:o

---

### Post by tgalati4 on 2010-05-20
ssh -Y -2 server@192.168.1.103

---

### Post by u-slayer on 2010-05-21
> **tgalati4 said:**
> ssh -Y -2 server@192.168.1.103

I get the same error.

---

### Post by u-slayer on 2010-05-21
:)

---

### Post by tgalati4 on 2010-05-21
Well you should have a system file called X0 that is owned by root:

tgalati4@tubuntu2:/tmp/.X11-unix$ ls -la
total 8
drwxrwxrwt  2 root root 4096 2010-05-07 08:50 .
drwxrwxrwt 10 root root 4096 2010-05-21 07:35 ..
srwxrwxrwx  1 root root    0 2010-05-07 08:50 X0

tgalati4@tubuntu2:~$ env | grep DISPLAY
DISPLAY=localhost:10.0


Your DISPLAY environment variable is correct.

Does your server machine have a valid xorg install?

What is the output of:

ps -ef | grep X

---

### Post by u-slayer on 2010-05-21
> **tgalati4 said:**
> 

Does your server machine have a valid xorg install?

What is the output of:

ps -ef | grep X

```
root      1420  1419  3 12:58 tty7     00:05:58 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-tWW68n/database -nolisten tcp vt7
user      2074     1  0 13:05 ?        00:00:00 python /usr/bin/x-tile --oaf-activate-iid=OAFIID:GNOME_X_Tile_Applet_Factory --oaf-ior-fd=18
root      4349  4331  0 16:11 pts/2    00:00:00 grep X

```

My display seems wrong:
```

#env | grep DISPLAY
DISPLAY=:0.0

```

Also I don't have an /tmp/.X11-unix folder.

---

### Post by u-slayer on 2010-05-21
I tried exporting your DISPLAY value. Now I get this:

```
Warning: No xauth data; using fake authentication data for X11 forwarding.
server@server:~$ xclock
connect localhost port 6010: Connection refused
Error: Can't open display: localhost:10.0

```

---

### Post by tgalati4 on 2010-05-21
The DISPLAY variable gets set when you ssh -2 -Y into your remote machine.  That instructs the xserver to send graphics to display 10.  That leaves 9 displays for the local machine.

You will have a /tmp/.X11-unix/X0 file on both machines.  It gets written at boot time.  I presume it's a scratch pad for the xserver.  So which machine is missing this directory?  On that machine, either reboot, or perform a reconfigure:

sudo dpkg-reconfigure -phigh xserver-xorg

Then reboot.

Do you have a firewall blocking port 6010 per chance?  Check both computers and the router that connects them.

---

