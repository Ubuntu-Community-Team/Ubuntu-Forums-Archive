---
title: "[SOLVED] ssh won't work"
date: 2007-12-23
forum: Server Platforms
---

### Post by gishaust on 2007-12-23
i have been using ssh with my windows laptop to access the server on the internal  network. Now i have an ubuntu machine and i tried to ssh using the terminal but it won't work

ssh <username>@<computer name or ip_address>:22

I have been using this example but it will not work. so i tried putty on the windows machine and into the server  first go. the error i am getting from the terminal is the following

ubuntu:~$ ssh gishaust@192.100.1.1:22
ssh: 192.100.1.1:22: Name or service not known

has anyone got any ideas

gishaust

---

### Post by PreviousN on 2007-12-23
Hey there,

I edited this because I misread you. 

Ok, here's how you ssh. First, "sudo apt-get install ssh sshfs". Second, type this "sshgishaust@192.100.1.1" You don't need 22 because thats the default port. Also...if you want to use a different port in the future, ssh uses a "switch". The syntax is like this. "ssh -p [port] [username]@[server]"

Cheers!

---

### Post by gishaust on 2007-12-23
thanks that was exactly what I was looking for this is solved. i did not have the package installed

---

