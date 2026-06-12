---
title: "TFTP-Server on Ubuntu 12.04"
date: 2013-09-26
forum: Server Platforms
---

### Post by thomas14 on 2013-09-26
Hello Community,

i´m trying to install a TFTP-Server on Ubuntu Versin 12.04.
Maybe you want to know why i need an TFTP-Server. I need this TFTP-Server for backup Configuration- and OS-Files from our Cisco Devices. So i need to put this files to my server and get them if i need to restore some OS or config.
First i want to share a link of a tutorial i used to install my server system: [http://mohammadthalif.wordpress.com/2010/03/05/installing-and-testing-tftpd-in-ubuntudebian/](http://mohammadthalif.wordpress.com/2010/03/05/installing-and-testing-tftpd-in-ubuntudebian/)
Before i install tftp i did my network settings. After i installed tftp i tried to test get and put but i allways get an connection timed out from my cisco device as well my tftp-server himself. 
If anyone have some idea how to solve my problem, please let me know.

kind regards,
Thomas

---

### Post by Kirboosy on 2013-09-26
Welcome to the forums! :D

Are you sure the service is running? We can restart the service just for safety.
```
sudo service xinetd restart
```
Do you have a firewall running on the TFTP server or cisco device? 


Hope that helps!
~Caboose

---

### Post by thomas14 on 2013-09-26
> **Caboose885 said:**
> Welcome to the forums! :D

Are you sure the service is running? We can restart the service just for safety.
```
sudo service xinetd restart
```
Do you have a firewall running on the TFTP server or cisco device? 

Hope that helps!
~Caboose


hey Caboose,

i restart the service:
```
srvtftp01:sudo service xinetd restart
xinetd stop/waiting
xinetd start/running, process 9778
```

I dont know if ubuntu is running a firewall, but my cisco device i try is not having one.

kind regards,
Thomas

---

### Post by Kirboosy on 2013-09-26
Did restarting the service change anything?

---

### Post by thomas14 on 2013-09-27
All i get on my cisco devices is:
```

sw-01#copy running-config tftp
Address or name of remote host []? 192.168.1.100
Destination filename [sw01-confg]?
.....
%Error opening tftp://192.168.0.100/sw01-confg (Timed out)
```

But i still can login with ssh and ping. So there is no network problem. There have to be a problem with my tftp-service because i can not get my test file:

```
administrator@srvtftp01:~$ cd /home/administrator/
administrator@srvtftp01:~$ tftp 192.168.1.100
tftp> get test
Transfer timed out.
```

---

### Post by atux on 2013-09-27
Hi. what do you mean by saying [COLOR=#000000]Before i install tftp i did my network settings.[/COLOR]. best thing is to try from a different machine to do a telnet on the tftp server at port 69 to check if it working. it seems that you have rights issue. try these things and let us know the results.[COLOR=#000000]

[/COLOR]

---

### Post by Kirboosy on 2013-09-27
You might be in the wrong directory by default when you connect on TFTP. Did you follow the guide you linked to step by step?

Something isn't quite right with your settings. Paste the output of the following command.

```
cat /etc/xinetd.d/tftp
```

You are opening a connection but its just unable to find the file.

~Caboose

---

