---
title: "Setting up proftps on 6.06 server"
date: 2006-06-26
forum: Server Platforms
---

### Post by nabberuk on 2006-06-26
I've just done a clean LAMP install of dapper 6.06. just trying to set up proftpd.

I've installed it by using apt-get (running it from the init.d option) 

added a user using the following command;

sudo useradd userftp -p your_password -d /home/FTP-shared -s /bin/false

Now when i try to log in from ws-ftp i get the following;

Connecting to 192.168.68.10:21
Connected to 192.168.68.10:21 in 0.000000 seconds, Waiting for Server Response
Error reading response from server.
Connection closed by remote host.
Host type (1): Automatic Detect

so, could anyone give me any pointers as to why it isnt working, also how can i change the root directory of where it logs into. i'd like to change it to /var/www

many thanks
nath

---

### Post by nabberuk on 2006-06-26
just checked that the iptables is allowing for port 21, which it is.

---

### Post by spifbv on 2006-06-26
[QUOTE=nabberuk]I've just done a clean LAMP install of dapper 6.06. just trying to set up proftpd.

I've installed it by using apt-get (running it from the init.d option) 

added a user using the following command;

sudo useradd userftp -p your_password -d /home/FTP-shared -s /bin/false

Now when i try to log in from ws-ftp i get the following;

Connecting to 192.168.68.10:21
Connected to 192.168.68.10:21 in 0.000000 seconds, Waiting for Server Response
Error reading response from server.
Connection closed by remote host.
Host type (1): Automatic Detect

so, could anyone give me any pointers as to why it isnt working, also how can i change the root directory of where it logs into. i'd like to change it to /var/www

many thanks
nath[/QUOTE]

try editing /etc/vsftpd.conf and set local_enable=YES and local_root=/var/www, then restart vsftpd

---

### Post by nabberuk on 2006-06-27
but im not using vsftpd, im using proftpd, are these the same program?

---

### Post by clparker on 2006-07-12
no, they are separate applications.

---

