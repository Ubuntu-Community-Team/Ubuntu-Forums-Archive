---
title: "Internet Sharing Stop working Ubuntu server 10.04"
date: 2011-12-01
forum: Server Platforms
---

### Post by leandro.mat on 2011-12-01
HI all, 

I am trying to configure a server for the first time. I started with Ubuntu Server 10.04.  I first install and configure a dhcp3-server and then 
a ran the the script available in the section Enable IP forwarding and Masquerading in this web page [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

After run this script I got my Internet sharing working. So I replaced my switch for a wireless route connecting it to eth1 card. The wireless router not worked and I got back to the switch again, but now the Internet sharing stops working. 
I mean, I the internal network I have access to the client and server from both of them using ssh. The dhcp3-server still working I ran again the "Enable IP forwarding and Masquerading script"  but the Internet is working only on the server. 

What kind of log file could help me to locate the problem ?

---

### Post by leandro.mat on 2011-12-01
I guess that is a DNS problem, because if I configure the DNS of any client as, for example, 8.8.8.8
the Internet  works well in the client. 

I tried to modify the content of the file  /etc/resolv.conf  on the server   
to   
nameserver 8.8.8.8

and restart the dhcp3-server, but the problem persist. Can you give me some hint ?

---

### Post by collisionystm on 2011-12-02
> **leandro.mat said:**
> I guess that is a DNS problem, because if I configure the DNS of any client as, for example, 8.8.8.8
the Internet  works well in the client. 

I tried to modify the content of the file  /etc/resolv.conf  on the server   
to   
nameserver 8.8.8.8

and restart the dhcp3-server, but the problem persist. Can you give me some hint ?
did you enable routing???

This is a much better guide here.

[http://documents.made-it.com/Debian_Internet_Server/Debian_Internet_Server-13.html](http://documents.made-it.com/Debian_Internet_Server/Debian_Internet_Server-13.html)

Enable the ip forwarding / routing

assign ip address to your nic cards

then enable masquerade ( assuming eth0 is going to the internet )

sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
if you want your server to be a dns and dhcp server, it is pretty easy. 

just install bind9 for dns

sudo apt-get install bind9

sudo nano /etc/bind/named.conf.options
make it look like this. It will use googles dns servers. your box will just forward to them.

         forwarders {
        8.8.8.8;
 };


sudo service bind9 restart

now edit your dhcpd.conf

sudo nano /etc/dhcp3/dhcpd.conf


# Where you see XXX.XXX.XXX.XXX replace with your desired info
#The ones in bold **XXX** should be the IP of this server.
option time-offset 300;
option domain-name-servers **XXX.XXX.XXX.XXX**;
#option domain-name "WORKGROUP";
option netbios-name-servers **XXX.XXX.XXX.XXX**;
option netbios-dd-server **XXX.XXX.XXX.XXX**;
option netbios-node-type 8;

subnet XXX.XXX.XXX.XXX netmask 255.255.255.0 {
        range XXX.XXX.XXX.XXX     XXX.XXX.XXX.XXX;
        option routers **XXX.XXX.XXX.XXX**;
        option broadcast-address XXX.XXX.XXX.255;
        option subnet-mask 255.255.255.0;
        authoritative;
}



Restart Dhcp

sudo service dhcp3-server restart

or

sudo /etc/init.d/dhcp3-server restart

---

