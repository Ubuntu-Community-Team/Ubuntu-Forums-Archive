---
title: "root@(none) WTF?"
date: 2006-04-10
forum: Server Platforms
---

### Post by stabface on 2006-04-10
I am setting up a file sharing server for an office and ran into a weird problem when i am trying to set the hostname i am getting this

i edited /etc/hosts then

echo server2 > /etc/hostname

/bin/hostname -F /etc/hostname

and then i get this error, 

/bin/hostname: line 1: server2: command not found

please help

---

### Post by MJN on 2006-04-10
What happens if you merely enter **/bin/hostname server2**     ?

Mathew

---

### Post by stabface on 2006-04-10
if i just enter that i get 

/bin/hostname: line 1: server2: command not found

---

### Post by stabface on 2006-04-10
i am trying t set up samba and i need a hostname of the netbios this is strange

---

### Post by stabface on 2006-04-11
bump

---

### Post by Iowan on 2006-04-12
Doubt this helps:[http://linuxhelp.blogspot.com/2005/01/changing-hostname-on-your-machine.html]("http://linuxhelp.blogspot.com/2005/01/changing-hostname-on-your-machine.html")

---

### Post by fdoving on 2006-04-14
You can try to re-install hostname.

[CODE]
apt-get install --reinstall hostname
[/CODE

And try again.


- Frode

---

### Post by stabface on 2006-04-19
thanks that did the trick

---

