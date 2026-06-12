---
title: "connetion errors for sudo apt-get update"
date: 2011-03-24
forum: Server Platforms
---

### Post by jwlnewsome on 2011-03-24
[SIZE=2]Hi all,
I have a connection error when i try to use 
sudo apt-get apache2 install[/SIZE]
[FONT=Verdana][SIZE=2]
I'm running a virtual server with ubuntu server installed as the OS. The physical server is windows 2008.

I have configured the interface for a static ip
[/SIZE][/FONT][FONT=Verdana][SIZE=2]auto eth0
iface eth0 inet static
        address 109.108.138.93
        netmask 255.255.255.0
        network [/SIZE][/FONT][FONT=Verdana][SIZE=2]109.108.138[/SIZE][/FONT][FONT=Verdana][SIZE=2].0
        broadcast [/SIZE][/FONT][FONT=Verdana][SIZE=2]109.108.138[/SIZE][/FONT][FONT=Verdana][SIZE=2].255
        gateway [/SIZE][/FONT][FONT=Verdana][SIZE=2]109.108.138[/SIZE][/FONT][FONT=Verdana][SIZE=2].1[/SIZE][/FONT]

[FONT=Verdana][SIZE=2]I have configured my resolv.conf so it points to the correct nameserver ip

When i ping both an ip or a hostname everything is OK

but when i run 

[/SIZE][/FONT][FONT=Verdana][SIZE=2]sudo apt-get update

I just get a load of connection errors and i cannot install any packages 
any help would be great 
Thanks in advance John
[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]

---

### Post by Cheesehead on 2011-03-24
What kind of connection errors?

---

### Post by jwlnewsome on 2011-03-25
sorry problem solved. seems the ip was looping back to another domain, deleted the re-routhing from the windows route table and all is well. chalk this one up to check the basics and dont rely on the word of mouth.

---

