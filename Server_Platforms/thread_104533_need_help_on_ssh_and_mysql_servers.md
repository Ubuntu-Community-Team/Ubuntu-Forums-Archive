---
title: "need help on ssh and mysql servers"
date: 2005-12-16
forum: Server Platforms
---

### Post by pedrotuga on 2005-12-16
Hey all!

I am trying to setup a server, so far the webserver is the only one working fine.
I am kind of new to the servers administration thing.

I installed openssh the as described in the ubuntu wiki

[https://wiki.ubuntu.com/SSHHowto?highlight=%28ssh%29](https://wiki.ubuntu.com/SSHHowto?highlight=%28ssh%29)

and apache'php'mysql as well

[https://wiki.ubuntu.com/ApacheMySQLPHP?highlight=%28apache%29%7C%28php%29%7C%28sql%29](https://wiki.ubuntu.com/ApacheMySQLPHP?highlight=%28apache%29%7C%28php%29%7C%28sql%29)

the thing is... from the outside i can only have access to http

I tryed to connect the database with mysql-administrator in a remote computer and also access throgh ssh in a windows computer using putty.
noone worked :(

why da heck dont they work :(

help plz

---

### Post by omegamike on 2005-12-26
Hi,

I actually set up a server about a week ago and had similar problems. I had to check the settings on my router because I was behind a NAT firewall. I logged into the router and enabled port forwarding to the computer at the ports I needed (I used ftp and html). In addition to that, I had to enable Passive port access in my ftp configuration. You might need to do the same, but I am not sure whether it is the same for ftp/sftp servers. Basically I added a line in the configuration as follows:

PassivePorts 50000 50019

I then logged back into the router and enabled the port forwarding feature accordingly. Like I said, I am not sure if it works the same way for sftp servers, but you might try adding that line to your: /etc/ssh/sshd_config and changing your port forwarding.

It worked for me

---

### Post by pedrotuga on 2005-12-27
Thx!

A NAT firewall was the problem. I can only access the computer witin the local network. I already talked with the network administrator in order to open my sftp and ssh ports to the outside.

---

