---
title: "Hostname Not Known on a Connect to Server"
date: 2008-07-08
forum: Server Platforms
---

### Post by sjrlaw on 2008-07-08
I set up a server with the Ubuntu server distro.  I used the Connect to Server app in Gnome and selected SSH to connect a workstation to the server.  When I put in the IP address, I am fine.  However, if I put in the hostname for the server, I get a Hostname Not Known error.  Do I have to configure DNS on the server to resolve the Hostname to IP address problem?  If so, how?

---

### Post by windependence on 2008-07-08
No, you need to put a DNS entry in the hosts file of the computer you are using to access the server. On Linuxm the file is in /etc/hosts.

Put an entry in like so:

```
xxx.xxx.xxx.xxx  yourservername
```

Where the xx are your internal IP address of the server.

-Tim

---

### Post by sjrlaw on 2008-07-08
Thanks, Win.  Tried it.  However, I can't save the changes, as I don't have the permissions.  It doesn't ask me for my root password.  How do I do it without using sudo on the command line?  I would prefer to use the GUI to launch the text editor.

---

### Post by windependence on 2008-07-08
Just fire up a terminal and do:

```
sudo nano /etc/hosts
```

Make your changes and do control o to save, then control x to exit.

-Tim

---

### Post by sjrlaw on 2008-07-09
Tim:

Did that, but it still doesn't work.

Steve

---

