---
title: "Setting vnc over ssh tunneling"
date: 2007-04-05
forum: Server Platforms
---

### Post by Nevermore on 2007-04-05
Hi everyone
i installed vnc4server 
then i added to xorg.conf the following options:

```

in the section Modules
Load "vnc"

in the section Screen
Option "PasswordFile" "/home/foo/.vnc/passwd"
Option "IdleTimeout" "10"
Option "localhost"

```

i also installed SSHD for authentication with rsa key only
tested it a couple times to be sure it worked, tested vnc as well, from localhost, and not (removing localhost from xorg.conf)
then i issued:
ssh -C -L 5901:target:5900 foo@target
put the phrassphrase
then on another terminal:
xvnc4viewer localhost:1
but i keep getting erros and it doesn't work..
in particular i keep getting this error in the ssh window:

channel3:open failed:connection failed:connection refused

is i send xvnc4viewer localhost instead i get a configuration vnc page (clipboards and so)
what can i do?

---

### Post by elst on 2007-04-07
What happens if you try to start a VNC server with SSH?

> ssh -f -L -N localhost:10901:server.example.com:5901 [email]username@server.example.com[/email] vncserver :1

---

### Post by r00tintheb0x on 2007-04-08
No  no no, bad admin. "ssh -X username@hostnanme" will forward and X apps to your local desktop granted its running an X server.

---

### Post by elst on 2007-04-08
SSH protects the connection in both cases.

EDIT: If this a public server then it should be firewalled, so that there is no direct remote access to any port used by VNC.

---

### Post by Nevermore on 2007-04-11
the true problem is that i can't firewall it
or better i had to leave a port open for vncserver..
since i was totally unable to have the ssh redirection working!

ssh -X is not suitable for me, since sometime i have to leave an X app running even if i go offline with the "controlling" machine.

i didn't try to start the ssh server, however i would prefer it to be always online so that i can just log in (i am afraid that closing the server closes also the X session i am using)

---

### Post by Nevermore on 2007-04-11
elst your idea seems the only feasible
the thing i want to know is this:
if i start a server and spawn some x apps, when i close the ssh connectiong, will they survive?
like if i start xchat on the server by vnc, will it be visible for other ppl there?

---

### Post by elst on 2007-04-12
The command that I posted does two things:

i) It creates an SSH tunnel that persists as long as the SSH process runs on the client.
ii) It runs the "vncserver" command on the server, to create a new desktop as display 1.

These two things are separate, and can be done independently. For example, you can use vncserver in /etc/rc.local to create a remote-accessible desktop for a user when the system boots up. 

Once created the desktop runs until terminated, and you can disconnect and reconnect at will. Access to this desktop is protected by a password that you set with the vncpasswd command. Again, if the server is accessible from outside a controlled network you must use an SSH tunnel for your VNC connection, as VNC only provides very weak password security, and uses unencrypted connections.

---

### Post by Nevermore on 2007-04-12
thanks elst
so i added tightvncserver :0 to my rc.local 
hoping that it will spawn a server ON the same X session that i see on the server (because is i open a xchat client there, i want the user actually sitting in front to see it)
is that correct?
how do i restrict the connection to vnc to ssh only now?

---

### Post by Nevermore on 2007-05-10
i tried with tightvncserver but it doesnt work
what i did is closing 5900 port on my firewall
then running vnc from xorg.conf
adding localhost option
and ssh it like that:
ssh -L 5900:localhost:5900 user@remote
then i can open xvnc4viewer localhost
and i am on the remote host.

---

