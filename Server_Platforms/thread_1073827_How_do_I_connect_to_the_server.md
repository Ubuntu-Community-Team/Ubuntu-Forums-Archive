---
title: "How do I connect to the server?"
date: 2009-02-18
forum: Server Platforms
---

### Post by wordmaster on 2009-02-18
Hello,

I have the server up and running with Ubuntu 10. I have installed Samba, I have put the stuff in the config file so that it will work with older windoze versions.

Now, how do I connect to the server from my 98SE desktop? Do I have to FTP? If so, how do I find the IP address for the server?

I assume there is another way to get in so that programs on the server can be run from the desktop, but how? Is there some program I have to install on the 98SE?

Any and all help greatly appreciated.

---

### Post by theDaveTheRave on 2009-02-18
On your server you need to get the IP address.

```

ifconfig

```

Then on the win98 terminal you need to put the full name of the samba share

eg if you called the shared drive "myShare", and IP address from ifconfig told you the server IP was 192.168.1.120 you would access by typing in the folowing into the file manager / explorer bar in win98

```

//192.168.1.120/myShare

```

If you can't ping the server's IP however, you have different issues.

Also, if you are connecting via a router, you may need to make sure that the router isn't acting as a name server, or you may get a conflict (routers IP addresses are normally something like 192.168.0.1 or similar), it should come up as the netmask or default gateway in the report from ifconfig.

Hope that helps.

David

---

### Post by mozkill on 2009-02-18
Please let us know if anything on these two sites helps you:

[http://www.ubuntuhq.com/wiki/index.php/Ubuntu_Howtos](http://www.ubuntuhq.com/wiki/index.php/Ubuntu_Howtos)
[http://www.howtoforge.com/howtos/linux/ubuntu](http://www.howtoforge.com/howtos/linux/ubuntu)

---

### Post by wordmaster on 2009-02-27
> **theDaveTheRave said:**
> On your server you need to get the IP address.

```

ifconfig

```

Then on the win98 terminal you need to put the full name of the samba share

eg if you called the shared drive "myShare", and IP address from ifconfig told you the server IP was 192.168.1.120 you would access by typing in the folowing into the file manager / explorer bar in win98

```

//192.168.1.120/myShare

```

If you can't ping the server's IP however, you have different issues.

Also, if you are connecting via a router, you may need to make sure that the router isn't acting as a name server, or you may get a conflict (routers IP addresses are normally something like 192.168.0.1 or similar), it should come up as the netmask or default gateway in the report from ifconfig.

Hope that helps.

David


Thank you, but I am still a bit lost. Here is what I got when I typed ifconfig:

me@user:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:d4:ba:1c  
          inet addr:10.2.8.195  Bcast:10.2.63.255  Mask:255.255.192.0
          inet6 addr: fe80::222:15ff:fed4:ba1c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:268411 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57965 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:70083772 (70.0 MB)  TX bytes:6528274 (6.5 MB)
          Interrupt:216 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96705 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96705 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:44643579 (44.6 MB)  TX bytes:44643579 (44.6 MB)

vnet0     Link encap:Ethernet  HWaddr fa:27:32:9e:83:36  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::f827:32ff:fe9e:8336/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4410 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:1070704 (1.0 MB)


Which of these IP addreses is the one I need to be trying to connect to? Also, how can I know what the shared drive is? Is that something Samba set up while it was loading? Any and all help appreciated

---

### Post by wirelessmonkey on 2009-02-27
Your server IP is 10.2.8.195
Your share is something you should have set up in your smb.conf.

---

### Post by cariboo on 2009-02-27
You don't need any thing special to connect to the server with a computer running Win98, just make sure you are in the same workgroup. I used to add an alias  for the server in the hosts file, but that was the only thing different.

Jim

---

### Post by TwiceOver on 2009-02-28
Just wondering what your setup is.  Looking at you ifconfig is kinda wacky for a router.

Do you have cable modem -> Router -> Internal network, or is your server box connected directly to the modem?

What else is on the box?  I see a vnet0 which is the confusing part.  Are you running some sort of vmware session?

---

