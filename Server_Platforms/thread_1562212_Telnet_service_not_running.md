---
title: "Telnet service not running"
date: 2010-08-27
forum: Server Platforms
---

### Post by Thyagaraj on 2010-08-27
I have telnet service intalled(apt-get install telnetd), but when I type telnet, I'm getting the following error:

bash: /usr/bin/telnet: No such file or directory

please any one help me...

---

### Post by Bachstelze on 2010-08-27
You also need to install a Telnet client, but why would you want to do that?

---

### Post by Thyagaraj on 2010-08-28
I'm using zabbix monitoring tool. It has email notification configured with postfix to notify to my gmail account.
The same settings working on my local machines and I could see mails from zabbix but it is not working on real servers.

In a forum it is said something like we can check if we could connect or if smtp working or not with the command  "telnet localhost 25". This command is working fine on local machines and if I type only telnet, I could see the telnet prompt(telnet>). If I use this command on servers I'm getting above posted error.

Thank you!

---

### Post by BkkBonanza on 2010-08-28
To do the checks you want you need the telnet client not the server. 
So you should install telnet not telnetd.

Telnet is for connecting to something.

Telnetd is a daemon that listens for connections, which is not what you want.

sudo apt-get remove telnetd
sudo apt-get install telnet

---

### Post by Thyagaraj on 2010-08-30
I removed telnetd and installed telnet, but no change:(

---

### Post by BkkBonanza on 2010-08-30
No change, how? Indicate what you typed and what message you got back.
Try **whereis telnet** it should indicate where the program is installed. Maybe it is not in /usr/bin.

---

### Post by Thyagaraj on 2010-08-30
It is under /usr/bin directory. I typed telnet. I'm getting the same error like this below

bash: /usr/bin/telnet: No such file or directory

---

### Post by BkkBonanza on 2010-08-30
That message is telling you it isn't under /usr/bin - so which is it?
It's either there or it isn't there.

What do you get back from **ls -lsa /usr/bin/telnet**
And then what from **echo $PATH**

---

### Post by Thyagaraj on 2010-08-30
The output of ls -lsa /usr/bin/telnet is:

88 -rwxr-xr-x 1 root root 84096 2010-08-27 07:02 /usr/bin/telnet
but this is differenet on my local machine(with link to /etc/alternatives/telnet)

The output of echo $PATH is:

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin

---

### Post by BkkBonanza on 2010-08-30
That makes no sense then. The program is there and has correct permissions and the directory is in the path. It should work. 

On my machine with 10.04 it has the link to /etc/alternatives, which in turn links back to /usr/bin/telnet.netkit. I guess this is some recent change but it works fine for me. I don't think that is wrong but I don't know when it was changed. I very rarely ever use telnet so wouldn't have noticed.

---

### Post by Thyagaraj on 2010-09-03
Thanks Bonanza, some how I made telnet to work.

---

