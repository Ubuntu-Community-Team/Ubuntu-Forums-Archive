---
title: "Cant connect to my server, from any pc on my local network"
date: 2016-01-05
forum: Ubuntu/Debian BASED
---

### Post by FabianPena on 2016-01-05
Hi, im new in ubuntu forums.

I'm trying to connect to my server in digital ocean, initially from only one pc, mi OS is Elementary OS Freya,  i searched a lot of forums with this issue : 
```

ssh: connect to host xx.xx.xx.xx port 22: Connection timed out

```

But when i try to connect from other pc with windows using putty, get the same error.
So i tried from my phone, the same,


So I decided to change the Internet network connection on my phone , I removed the wifi, and used the satellite internet . and it worked. But i need to connect to the server from mi Elementary, what can i do? 

Thank's a lot guys.

---

### Post by MAFoElffen on 2016-01-06
Elementary OS is based on the Ubuntu core, but is it's own distribution. 

 - For OpenSSH to work, there is a Server and a Client. 
 - The server has to have port 22 open through it's firewall.
 - There needs to be a physical and logical network path between point A and point B.
 - There user on the client needs to have permissions to use ssh on the client.
 - The user on the client needs to have valid credientials that they will use on the server.

To diagnose:
```

# confirm the ip address of the server (execute on server)
ifconfig -a
# confirm that ssh is running on server
sudo journalctl | grep ssh 
sudo systemctl status ssh.service
# confirm there is a listener open on port 22 of server 
netstat -anp | grep 22

```
If ssh server is running on the server -and- is listening, then go to the client and ensure there is a path from the client to the server
```

ping -n 3 192.168.0.100
# subsitute the ip address here, with that found from the above ifconfig results...

```
A network path needs to be on the same network segment (same network ID), or have a router(s) enabling a connection between networks.

If a good ping results, then look at the format of your ssh command...
```

ssh userName@192.168.0.100
# substitute userName for a valid user on the server, and the IP address of the server

```
If from Win, ping from a cmd.exe window, Then from putty, fill in the IP address, port 22, connect ... once it hits the listener of the ssh server, it should prompt for  user name and password.
I can tell you that most the the time if you get that error message, it means there is not a physical network path. @d most command reason would be that the listener is not on (firewall rule)

---

### Post by howefield on 2016-01-06
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by FabianPena on 2016-01-09
I confirmed ssh is running in server.
ping is working too.

If i use any pc from mi local network, i cant connect to ssh outside (i tried from win with putty, mi phone with juice ssh, and obviusly, mi linux)

If i use mi phone with satelital connection, (not on my local network), with juicessh, i can connect to my server.

So... what's going on?

---

