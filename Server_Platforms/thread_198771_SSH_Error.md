---
title: "SSH Error"
date: 2006-06-17
forum: Server Platforms
---

### Post by Isoss on 2006-06-17
I have a ssh connection between two PCs. One has ubuntu-server and the other has ubuntu-desktop. I have installed ssh and openssh-server on both and so now I am trying to ssh to /var/www at the ubuntu-server to no avail. I know how to work with SSH cuz I've done it before. I have filled the server's IP, the port (22), the username, the folder path and the connection name. Now when I click on the ssh folder that was created on my desktop it prompts this error: Could not open location 'ssh://admin@192.168.0.1:22/var/www'

Details: Unknown error code: 38

Why is that? somebody help this is eating my time. And thanks in advance.

---

### Post by Randomskk on 2006-06-17
If you connect in a terminal does it work?
```

ssh -ladmin 192.168.0.1
```

---

### Post by bluenova on 2006-10-28
The keys have probably changed.

Goto:

/home/yourusername/.ssh/ and delete the contents of known_hosts

Next time you try to connect it will ask you to accept the new key, this should sort it out.

---

### Post by Endolith on 2007-10-11
I just had this error through the Place menu, but not through the command line.  I killed gnome-panel (after which it restarted) and ssh folders started working again.

---

### Post by dmizer on 2007-10-12
just do this command:
```
ssh admin@192.168.0.1
```
enter your password.  then:
```
cd /var/www
```

---

