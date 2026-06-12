---
title: "SSH Command?"
date: 2006-06-17
forum: Server Platforms
---

### Post by Isoss on 2006-06-17
I have a connection between two ubutnu michines and everything is OK. I can SSH, FTP and everything.
Now I have openssh-server and ssh installed on both and I can create SSH folders ... So I need to know what commands can I use in terminal for 1. Creating SSH folders specifying the server IP, port, user name, name to use for the connection! 2. SSHing with Terminal ... I mean something like nautilus, a SSH command that would connect me to an existing SSH connection and opens the folder as if I have double-clicked on the SSH folder which is by default created on the Desktop.

Hope I made myself clear and hope somebody has an answer and I'll appriciate your help cuz this is very important since I use PuTTy.

---

### Post by denni on 2006-06-17
hope i understand you correctly
use sshfs 
on server do;
> - apt-get install sshfs fuse-utils
- modprobe fuse
- pico /etc/modules and add fuse to it
- mkdir /mnt/sshfs
on client do;
> - sshfs server:/ /mnt/sshfs
- use what ever filemanager you whant and what ever program to get access to your servers documents

---

### Post by Isoss on 2006-06-17
Can u explain more? I did exactly what you did and installed sshfs on the server, not from the cleint machine I ran sshfs server://mnt/sshfs (I put the server's IP instead of server) and it's telling me ```
isos@isos-laptop:~$ sshfs 192.168.0.1://mnt/sshs
remote host has disconnected

```
I don't think I fully understood. The reason why I want to do it is that one of the PCs has ubuntu-server so I want to access for example the Desktop of another ubuntu machine which has ubuntu-desktop so I can ls the content and copy or paste or create folders.

Let me explain more what I need to do that made me ask such a quesiotn. Using terminal or the shell of ubuntu-server, how can I copy the content of /var/www of the ubuntu michine which has a desktop to the /var/www of ubuntu-server "which doesn't has desktop"?

Thanks.

---

### Post by denni on 2006-06-18
> in stead of 
isos@isos-laptop:~$ sshfs 192.168.0.1://mnt/sshs
do 
isos@isos-laptop:~$ sshfs 192.168.0.1:/ /mnt/sshs

with space between the server and the client mount point

you can also shose the user you whant to connect as on the server
> sshfs root@192.168.0.1:/ /mnt/sshfs 

then you can just copy to and from that mount point like eny another folder on your client sistem

---

### Post by imagine on 2006-06-19
> **denni]on server do said:**
> - apt-get install sshfs fuse-utils
- modprobe fuse
- pico /etc/modules and add fuse to it
- mkdir /mnt/sshfs

on client do;
> - sshfs server:/ /mnt/sshfs
[/QUOTE]
No, you do that all on the client, not on the server.

---

