---
title: "[HowTo] Set static ip on server"
date: 2008-06-21
forum: Server Platforms
---

### Post by undertakingyou on 2008-06-21
This is my first howto so please bear with me.  

The reason that I am writing this:
I was migrating servers to a new setup.  Before I just had a desktop and I installed a LAMP and ran with it.  Later I got actual server hardware and installed the server edition of ubuntu.  I had the new server set on DHCP for the migration and after the migration I needed to change the IP from DHCP to STATIC and that way all my DNS stuff would just be done.  The thing is I didn't have a GUI and I had to do it via command line.

So here it goes.

First, edit /etc/network/interfaces.
Change the entry for your ethernet device (eth0 in my case) so line that instead of this:
```
 auto eth0
iface eth0 inet dhcp
```
change it so that it says this:
```
auto eth0
iface eth0 inet static
     address <ip address of your choice>
     netmask <netmask, usually 255.255.255.0>
     broadcast <broadcast ip>
     gateway <ip of gateway>

```

Then just restart the networking daemon
```
sudo /etc/init.d/networking restart
```
After the restart it should have the static IP that you set.

This will of course work for any machine.  But is particularly convenient for a server where you are ssh'd in.

If you are having DNS issues after that edit your /etc/resolv.conf and add the line
```
nameserver <ip>
```
The order of the nameservers entered are the order that the system will use to try a DNS lookup.  Usually two are sufficient.  I do mine as first nameserver the internal DNS, second I do a public DNS and I use 4.2.2.2 .  You could also use openDNS which is 208.67.222.222 and 208.67.220.220 .  Either one should do it for you.
Have fun!!!

---

### Post by sp0nge on 2008-06-21
Great timing on this post!

I have just installed Ubuntu Server on an old desktop that will become a test server as I experiment with hosting my own web server. This is my first experience with configuring and/or running my own server, so thanks in advance for your help and understanding. 

In a [guide]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p3") I am following, the author advises the following:

```
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
```

As you see, your post varies slightly and I have some questions.

1) Are both netmask and network necessary? The guide advises both but does not define them clearly, and your post suggests they are the same. 

2) Is the broadcast IP the external address that my router displays? 

Again, thanks for the help.

---

### Post by undertakingyou on 2008-06-22
In my setup I just did netmask.  The network should be implied and everything work.  The broadcast is not the external IP.  It is the last IP in a block.  So, it a 192.168.0.0 network, the gateway would normally be 192.168.0.1 and the broadcast 192.168.0.255.  Broadcast is always the last IP in your range set.

---

### Post by magicplayr2000 on 2008-06-22
I just had to do this the other day.  I was getting all kinds of weird problems from not properly setting my static IP.  This would've been very useful.

---

### Post by gtdaqua on 2008-06-22
> **undertakingyou said:**
> This is my first howto so please bear with me.  

The reason that I am writing this:
I was migrating servers to a new setup.  Before I just had a desktop and I installed a LAMP and ran with it.  Later I got actual server hardware and installed the server edition of ubuntu.  I had the new server set on DHCP for the migration and after the migration I needed to change the IP from DHCP to STATIC and that way all my DNS stuff would just be done.  The thing is I didn't have a GUI and I had to do it via command line.

So here it goes.

First, edit /etc/network/interfaces.
Change the entry for your ethernet device (eth0 in my case) so line that instead of this:
```
 auto eth0
iface eth0 inet dhcp
```
change it so that it says this:
```
auto eth0
iface eth0 inet static
     address <ip address of your choice>
     netmask <netmask, usually 255.255.255.0>
     broadcast <broadcast ip>
     gateway <ip of gateway>

```

Then just restart the server
```
sudo shutdown -r now
```
After the restart it should have the static IP that you set.

.....



You dont have to restart the server. 

```

sudo /etc/init.d/networking restart

```

This is enough. Restarting the whole server is not a good idea. Most of the stuff in linux can be done without having to restart.

---

### Post by undertakingyou on 2008-06-22
> **gtdaqua said:**
> You dont have to restart the server. 

```

sudo /etc/init.d/networking restart

```

This is enough. Restarting the whole server is not a good idea. Most of the stuff in linux can be done without having to restart.

Super point and thanks for the info.  I'll update the howto.

---

