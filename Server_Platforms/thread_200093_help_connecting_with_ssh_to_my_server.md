---
title: "help connecting with ssh to my server"
date: 2006-06-19
forum: Server Platforms
---

### Post by cobbweb on 2006-06-19
Hello, 
 
 I just installed a LAMP server on one of my computers down stairs to use as a sever would like to be able to connect to it via ssh so I can edit it from my computer upstairs.(by the way would vncviewer be a better choice for this?) I have done the following. 

 when to /etc/network/interfaces    
  and edited with 

auto eth0
        iface eth0 inet static
	address 192.168.2.5
	netmask 255.255.255.0
	gateway 192.168.2.1


My router is a Belkin and it's address or whatever to get to it so i can configure it is 192.168.2.1 

 I wish to now,however connect to my server down stairs, but am for some reason unable to or am doing somthing wrong. I need help on how I connect to my server. Thanks,
 
 Cobbweb

---

### Post by simonn on 2006-06-19
Can you ping it?

Is port 22 open?

Is sshd running on the server?

$ ps -A | grep sshd

---

### Post by coach-x on 2006-06-19
I dont know if the default lamp installs openssh-server, you might need to apt-get install ssh openssh-server

---

### Post by cobbweb on 2006-06-19
yup that was it i needed to install ssh. Though it had it all ready installed.. Ok thanks , 

 Cobbweb

---

