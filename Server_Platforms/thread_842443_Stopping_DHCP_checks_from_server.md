---
title: "Stopping DHCP checks from server"
date: 2008-06-27
forum: Server Platforms
---

### Post by wxman on 2008-06-27
My version 8.04 keeps checking the DHCP from the router/firewall, but I have it set to static IP address. The server logs repeatedly show:
```

Jun 27 10:33:46 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Jun 27 10:34:01 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Jun 27 10:34:08 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jun 27 10:34:11 server1 dhclient: No DHCPOFFERS received.
Jun 27 10:34:11 server1 dhclient: No working leases in persistent database - sleeping.
Jun 27 10:34:11 server1 dhclient: execve (/lib/dhcp3-client/call-dhclient-script, ...): No such file or directory

```

I have my /etc/network/interfaces set like:

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
      address 192.168.31.200
      netmask 255.255.255.0
      network 192.168.31.0
      broadcast 192.168.31.255
      gateway 192.168.31.1

```

DHCP is disabled on my router(monowall), and I removed DHCP from the server by doing: apt-get remove dhcp3-client.
Why would the server still be looking to the DHCP server when I thought I told it to use a static IP?

---

### Post by MJN on 2008-06-27
The DHCP client may still be running - find out with ps aux |grep dhclient

Also, you may have some existing leases that are requiring renewal - you can safely clear out /var/lib/dhcp3/dhclient*.leases

Mathew

---

### Post by wxman on 2008-06-27
I ran ps aux |grep dhclient as you said, and got:
```

root@server1:~# ps aux |grep dhclient
root      6036  0.0  0.0   3004   768 pts/0    S+   19:13   0:00 grep dhclient
dhcp     11034  0.0  0.0   2440   800 ?        Ss   Jun24   0:00 dhclient3 -e IF                                     _METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leas                                     es eth0

```

I've never read that before, and I can't find anywhere what's it's telling me. Does this tell me anything?
I also emptied out the /var/lib/dhcp3/dhclient*.leases. I'll check the logs again tonight to see if there's any change.
Thanks.

---

### Post by mrpeenut24 on 2008-06-28
This tells you there is a dhcp process running under pid 11034.  If you've deleted everything and you want to stop the process you can run 'kill -9 11034'.

---

### Post by wxman on 2008-06-28
Thanks. That's good to learn for the future.
The last step seemed to work. It's been 30 minutes and so far no new log entries.

Thanks again.

---

### Post by mrpeenut24 on 2008-06-28
No problem.  However, kill -9 is very powerful and can sometimes screw things up if a process is writing to a file (among other things).  Often kill -15 will suffice, as this sends it a TERMinate signal, but this can sometimes be ignored.  kill -9 cannot be ignored.

---

### Post by wxman on 2008-06-28
That's good to know too. Just when I think I've got the hang of Linux, I find I'm still learning. Now I need to find if anything in the start-up will cause the same problem to occur if I need to reboot the server. So far I can't find anything, but I also missed the process you pointed out.

---

### Post by MJN on 2008-06-28
You've removed the DHCP client so it's not going to happen again. The only bit you missed was that removing a package doesn't necessarily stop the current process running in memory.

Mathew

---

### Post by cariboo on 2008-06-28
Just as a point of interest you don't have to retsart your server every time you make a change to running services, most of the services are located in /etc/init.d. To stop or start a service, in a terminal type:

```
sudo /etc/init.d/service stop/start
```

where service is the service you want to stop or start. There are a lot more options, if you just enter the service name with out any options, it will tell you the available options.

Remember Linux is not Windows

Jim

---

### Post by wxman on 2008-06-28
> **cariboo907 said:**
> Just as a point of interest you don't have to retsart your server every time you make a change to running services, most of the services are located in /etc/init.d. To stop or start a service, in a terminal type:

```
sudo /etc/init.d/service stop/start
```

where service is the service you want to stop or start. There are a lot more options, if you just enter the service name with out any options, it will tell you the available options.

Remember Linux is not Windows

Jim


I did know that. I just wasn't sure if something in a start up script that will get it all going again if I had to do a reboot for some reason.

---

