---
title: "probleme in server ssh"
date: 2008-11-21
forum: Server Platforms
---

### Post by poggie on 2008-11-21
Hey All,
I need some help setting up openssh on Ubuntu server 8.10
So far I have - Installed the server and client on my machine
                Changed my IP to a static one
                Port forwarding(i'm behind a router)


Now I have two questions
When I connect to my server from the machine itself using 
~ssh localhost 
its fine, but when from another machine it does not work


Will I be able to connect to it anywhere without typing in my ip but instead using a name like poggie.eastlink.ca?

---

### Post by hictio on 2008-11-21
> **poggie said:**
> Hey All,
Now I have two questions
When I connect to my server from the machine itself using 
~ssh localhost 
its fine, but when from another machine it does not work

This is worrisome, if you can't connect to your server form inside the LAN, for the moment forget about connecting to it from the internet.
Try this, from another box inside your LAN:

```

telnet ip.of.ubuntu.server 22 (ENTER)

```

You'll have to see something like this:
```

Connected to ip.of.ubuntu.server
Escape character is '^]'.
SSH-2.0-OpenSSH_5.1p1 Debian-3ubuntu1

```

Type a few ENTERs to get out of that.

> **poggie said:**
> 
Will I be able to connect to it anywhere without typing in my ip but instead using a name like poggie.eastlink.ca?

(Assuming you have a home connection, non fixed IP address) For this to work no need to setup a way that your router informs a service, like DynDNS, that the IP address has changed.
Many routers have that ability, you'll have to register an account, and fill the data on the router it self.
If your router does not support it, you have to install a client on the Ubuntu server itself that will do just that, keep tabs of your current IP address.

---

### Post by Dr Small on 2008-11-21
If on a different machine on the LAN, you can access the SSH server by running:
```
ssh user@*ipaddress*
```

If you want to be able to use a hostname from outside of the network, you will need to have a DNS entry pointing to your static external IP address, or simply register an account at DnyDNS.org and use one of their subdomains. If you have a dynamic external IP address, there is applications to solve that problem also.

Dr Small

---

### Post by poggie on 2008-11-21
Well, I typed it in and it returned

Could not open connection to host, on port 22
Connect Failed

And by server ip you meant the 192.168.blah.blah ip right, the one I set.

---

### Post by Dr Small on 2008-11-21
> **poggie said:**
> And by server ip you meant the 192.168.blah.blah ip right, the one I set.

That IP address is vitally important.
A further question as pressed from your latest results; Do you have Firestarter installed on this system? Sounds like you are denying all inbound traffic on your LAN (not such a wise idea, unless you are on a corporate LAN).

---

### Post by poggie on 2008-11-21
yes firestarter is installed, advise me as to what i should do now.

---

### Post by Dr Small on 2008-11-21
> **poggie said:**
> yes firestarter is installed, advise me as to what i should do now.
Open Firestarter:
```
gksudo firestarter
```

Browse to "Policy" tab.
Click in the "Allow Service" white area.
Go to the top and click "Add Rule"
Select SSH as the "Name"
"When the source is..." -- Anyone
+Add
Apply Policy

Go back and try again with SSH.

---

### Post by poggie on 2008-11-21
ok really embarassing 
my ip was actually 192.168.1.105 not what i had set it as so now I need to know how to change my ip to a static one...

---

### Post by Dr Small on 2008-11-21
> **poggie said:**
> ok really embarassing 
my ip was actually 192.168.1.105 not what i had set it as so now I need to know how to change my ip to a static one...
Open /etc/network/interfaces with your favorite editor.
Example:
```
gksudo gedit /etc/network/interfaces
```
or
```
sudo vim /etc/network/interfaces
```

Below the lines that look like this:
```
auto lo
iface lo inet loopback
```

Comment them out with the hash symbol (#).

If you are on ethernet use:
```

auto eth0
iface eth0 inet static
address 192.168.0.105
netmask 255.255.255.0
gateway 192.168.1.1
```

If Wireless:
```
auto ath0
iface ath0 inet static
address 192.168.0.105
netmask 255.255.255.0
gateway 192.168.1.1
```

Change the gateway to match your network (router's IP address) and set the static IP address to what you want in "address ".
Restart Networking:
```
sudo /etc/init.d/networking restart
```

---

### Post by poggie on 2008-11-21
Wow thanks very much Dr Small,
You have been a big help, one more thing though before I move along. I would like to be able to access this from places outside my network say at my University or maybe at a friends place. How would I go about getting that setup?

---

### Post by hictio on 2008-11-21
> **poggie said:**
> Wow thanks very much Dr Small,
You have been a big help, one more thing though before I move along. I would like to be able to access this from places outside my network say at my University or maybe at a friends place. How would I go about getting that setup?

You'll have to:

- Port forward the SSH port, by default 22, from your router to the IP that the Ubuntu server is using in your LAN.

- Make sure you have a way of accessing thru your router your Ubuntu's server SSH.
The easiest way is registering a hostname on a place dyndns.org, so it's client will keep tabs on the IP that your ISP assigns to your router; not to mention that it will be easier for you to type:

```

ssh user@somehostnane.dyndns.org

```

Than:

```

ssh user@public.isps.ip.address

```

Like I said in the post above, many SOHO routers allow you to register them to places like DynDNS.org, that is, they have a way of informing them of your current IP address, if yours don't, at the site, you can download a client for your Ubuntu server, that will do just that (run all the time, keeping track of your current public IP address, and then inform dyndns.org if it changes).

The first thing that you should do, is port forwarding, and check that your ISP is not blocking SSH traffic.
Do the port forwarding thing, and then access a place like [http://checkip.dyndns.org/](http://checkip.dyndns.org/) to get your external/ public IP address, and then on the linux box, or any other box in your LAN, type:

```

ssh user@public.isps.ip.address

```

To see if you can get to your Ubuntu server's SSH, perhaps ask a friend, or someone outside your LAN to test that as well.

---

### Post by poggie on 2008-11-22
and if I didnt want to do it like that? as in not use hostname.dyndns.org but rather my.own.com.

---

### Post by Dr Small on 2008-11-22
> **poggie said:**
> and if I didnt want to do it like that? as in not use hostname.dyndns.org but rather my.own.com.
You would have to register a domain, and have it's IP record point to your's.

---

### Post by hictio on 2008-11-22
> **Dr Small said:**
> You would have to register a domain, and have it's IP record point to your's.

Indeed.

Out of curiosity, can you register a domain to point to an IP that is on a DSL allocation? Not sure if this is the case of OP, just curious.

---

### Post by bnejoker on 2009-04-14
helooo !!!
i have a probleme in my server ssh when i write this cammand in terminal :
ssh 192.168.0.1 -p 22
its comming this message :
ssh: connect to host 192.168.0.1 port 22: Connection refused.
please help me i'am beginer.
thanks......

---

### Post by wirelessmonkey on 2009-04-14
Is there an ssh server listening on 192.168.0.1?

---

### Post by bnejoker on 2009-04-14
thakns for you repond for my question 
yes the adress ip is listening on ssh server ....

nedjemeddine@nedjemeddine-desktop:~$ ssh 192.168.0.1 -p 22
ssh: connect to host 192.168.0.1 port 22: Connection refused

---

### Post by cdenley on 2009-04-14
Verify that the server is listening on that port. Run this command on the server and post the output.
```

sudo netstat -tlnp

```
If there is a server listening for external connection, then you have some firewall or networking device blocking the connection. Post your iptables rules from the server.
```

sudo iptables -L -n

```
Also, verify you are using the correct IP address by running this command on your server and posting the output.
```

ifconfig

```

---

### Post by bnejoker on 2009-04-14
thanks my friend but i c'ant know if the  server is listening on that port
please please talk me you and i'am sorry .....
1-
```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:1235            0.0.0.0:*               LISTEN      5430/sshd       
tcp        0      0 10.102.4.64:53          0.0.0.0:*               LISTEN      5406/named      
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      5406/named      
tcp        0      0 0.0.0.0:26006           0.0.0.0:*               LISTEN      7608/skype      
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      5467/cupsd      
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      5406/named      
tcp6       0      0 ::1:5900                :::*                    LISTEN      6210/vino-server
tcp6       0      0 :::1235                 :::*                    LISTEN      5430/sshd       
tcp6       0      0 :::53                   :::*                    LISTEN      5406/named      
tcp6       0      0 ::1:953                 :::*                    LISTEN      5406/named      

```
the 2- command :
sudo iptables -L -n
```

 level 4 prefix `''IN-internet':'' 
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain in_internet_dns_c15 (1 references)
target     prot opt source               destination         
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spt:53 state ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:53 state ESTABLISHED 

Chain in_internet_dns_s7 (1 references)
target     prot opt source               destination         
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:53 state NEW,ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:53 state NEW,ESTABLISHED 

Chain in_internet_ftp_c11 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:21 dpts:32768:61000 state ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:20 dpts:32768:61000 state RELATED,ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:65535 dpts:32768:61000 state ESTABLISHED 

Chain in_internet_ftp_s5 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:65535 dpt:21 state NEW,ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:65535 dpt:20 state ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:65535 dpts:32768:61000 state RELATED,ESTABLISHED 

Chain in_internet_http_c9 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:80 dpts:32768:61000 state ESTABLISHED 

Chain in_internet_http_s4 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:65535 dpt:80 state NEW,ESTABLISHED 

Chain in_internet_https_c10 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:443 dpts:32768:61000 state ESTABLISHED 

Chain in_internet_imap_s1 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:65535 dpt:143 state NEW,ESTABLISHED 

Chain in_internet_imaps_s2 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:65535 dpt:993 state NEW,ESTABLISHED 

Chain in_internet_ntp_c18 (1 references)
target     prot opt source               destination         
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spt:123 dpt:123 state ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spt:123 dpts:32768:61000 state ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:123 dpt:123 state ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:123 dpts:32768:61000 state ESTABLISHED 

Chain in_internet_ping_c16 (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           state ESTABLISHED icmp type 0 

Chain in_internet_rsync_c17 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:873 dpts:32768:61000 state ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spt:873 dpts:32768:61000 state ESTABLISHED 

Chain in_internet_smtp_c12 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:25 dpts:32768:61000 state ESTABLISHED 

Chain in_internet_smtp_s3 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:65535 dpt:25 state NEW,ESTABLISHED 

Chain in_internet_smtps_c13 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:465 dpts:32768:61000 state ESTABLISHED 

Chain in_internet_squid_c8 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:3128 dpts:32768:61000 state ESTABLISHED 

Chain in_internet_ssh1_s6 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:65535 dpt:1235 state NEW,ESTABLISHED 

Chain in_internet_ssh_c14 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:22 dpts:32768:61000 state ESTABLISHED 

Chain in_world (1 references)
target     prot opt source               destination         
in_world_all_c1  all  --  0.0.0.0/0            0.0.0.0/0           
in_world_irc_c2  all  --  0.0.0.0/0            0.0.0.0/0           
in_world_ftp_c3  all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED 
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 5 LOG flags 0 level 4 prefix `''IN-world':'' 
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain in_world_all_c1 (1 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state ESTABLISHED 

Chain in_world_ftp_c3 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:21 dpts:32768:61000 state ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:20 dpts:32768:61000 state RELATED,ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:65535 dpts:32768:61000 state ESTABLISHED 

Chain in_world_irc_c2 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:6667 dpts:32768:61000 state ESTABLISHED 

Chain out_home (1 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED 
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           

Chain out_home2internet (1 references)
target     prot opt source               destination         
out_home2internet_ftp_s1  all  --  0.0.0.0/0            0.0.0.0/0           
out_home2internet_jabber_s2  all  --  0.0.0.0/0            0.0.0.0/0           
out_home2internet_telnet_s3  all  --  0.0.0.0/0            0.0.0.0/0           
out_home2internet_time_s4  all  --  0.0.0.0/0            0.0.0.0/0           
out_home2internet_cups_s5  all  --  0.0.0.0/0            0.0.0.0/0           
out_home2internet_ping_s6  all  --  0.0.0.0/0            0.0.0.0/0           
out_home2internet_pop3_s7  all  --  0.0.0.0/0            0.0.0.0/0           
out_home2internet_pop3s_s8  all  --  0.0.0.0/0            0.0.0.0/0           
out_home2internet_dhcp_s9  all  --  0.0.0.0/0            0.0.0.0/0           
out_home2internet_dns_s10  all  --  0.0.0.0/0            0.0.0.0/0           
out_home2internet_http_s11  all  --  0.0.0.0/0            0.0.0.0/0           
out_home2internet_https_s12  all  --  0.0.0.0/0            0.0.0.0/0           
out_home2internet_rsync_s13  all  --  0.0.0.0/0            0.0.0.0/0           
out_home2internet_rtp_s14  all  --  0.0.0.0/0            0.0.0.0/0           
out_home2internet_icmp_s15  all  --  0.0.0.0/0            0.0.0.0/0           
out_home2internet_imap_s16  all  --  0.0.0.0/0            0.0.0.0/0           
out_home2internet_imaps_s17  all  --  0.0.0.0/0            0.0.0.0/0           
out_home2internet_nntp_s18  all  --  0.0.0.0/0            0.0.0.0/0           
out_home2internet_ntp_s19  all  --  0.0.0.0/0            0.0.0.0/0           
out_home2internet_smtp_s20  all  --  0.0.0.0/0            0.0.0.0/0           
out_home2internet_smtps_s21  all  --  0.0.0.0/0            0.0.0.0/0           
out_home2internet_ssh_s22  all  --  0.0.0.0/0            0.0.0.0/0           
out_home2internet_squid_s23  all  --  0.0.0.0/0            0.0.0.0/0           
out_home2internet_sip_s24  all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED 

Chain out_home2internet_cups_s5 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:631 dpts:1024:65535 state ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:631 dpt:631 state ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spt:631 dpts:1024:65535 state ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spt:631 dpt:631 state ESTABLISHED 

Chain out_home2internet_dhcp_s9 (1 references)
target     prot opt source               destination         
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spt:67 dpt:68 

Chain out_home2internet_dns_s10 (1 references)
target     prot opt source               destination         
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spt:53 state ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:53 state ESTABLISHED 

Chain out_home2internet_ftp_s1 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:21 dpts:1024:65535 state ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:20 dpts:1024:65535 state RELATED,ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:65535 dpts:1024:65535 state ESTABLISHED 

Chain out_home2internet_http_s11 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:80 dpts:1024:65535 state ESTABLISHED 

Chain out_home2internet_https_s12 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:443 dpts:1024:65535 state ESTABLISHED 

Chain out_home2internet_icmp_s15 (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           state ESTABLISHED 

Chain out_home2internet_imap_s16 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:143 dpts:1024:65535 state ESTABLISHED 

Chain out_home2internet_imaps_s17 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:993 dpts:1024:65535 state ESTABLISHED 

Chain out_home2internet_jabber_s2 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:5222 dpts:1024:65535 state ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:5223 dpts:1024:65535 state ESTABLISHED 

Chain out_home2internet_nntp_s18 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:119 dpts:1024:65535 state ESTABLISHED 

Chain out_home2internet_ntp_s19 (1 references)
target     prot opt source               destination         
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spt:123 dpt:123 state ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spt:123 dpts:1024:65535 state ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:123 dpt:123 state ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:123 dpts:1024:65535 state ESTABLISHED 

Chain out_home2internet_ping_s6 (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           state ESTABLISHED icmp type 0 

Chain out_home2internet_pop3_s7 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:110 dpts:1024:65535 state ESTABLISHED 

Chain out_home2internet_pop3s_s8 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:995 dpts:1024:65535 state ESTABLISHED 

Chain out_home2internet_rsync_s13 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:873 dpts:1024:65535 state ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spt:873 dpts:1024:65535 state ESTABLISHED 

Chain out_home2internet_rtp_s14 (1 references)
target     prot opt source               destination         
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spts:10000:20000 state ESTABLISHED 

Chain out_home2internet_sip_s24 (1 references)
target     prot opt source               destination         
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spt:5060 dpt:5060 state ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spt:5060 dpts:1024:65535 state ESTABLISHED 

Chain out_home2internet_smtp_s20 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:25 dpts:1024:65535 state ESTABLISHED 

Chain out_home2internet_smtps_s21 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:465 dpts:1024:65535 state ESTABLISHED 

Chain out_home2internet_squid_s23 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:3128 dpts:1024:65535 state ESTABLISHED 

Chain out_home2internet_ssh_s22 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:22 dpts:1024:65535 state ESTABLISHED 

Chain out_home2internet_telnet_s3 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:23 dpts:1024:65535 state ESTABLISHED 

Chain out_home2internet_time_s4 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:37 dpts:1024:65535 state ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spt:37 dpts:1024:65535 state ESTABLISHED 

Chain out_internet (1 references)
target     prot opt source               destination         
out_internet_imap_s1  all  --  0.0.0.0/0            0.0.0.0/0           
out_internet_imaps_s2  all  --  0.0.0.0/0            0.0.0.0/0           
out_internet_smtp_s3  all  --  0.0.0.0/0            0.0.0.0/0           
out_internet_http_s4  all  --  0.0.0.0/0            0.0.0.0/0           
out_internet_ftp_s5  all  --  0.0.0.0/0            0.0.0.0/0           
out_internet_ssh1_s6  all  --  0.0.0.0/0            0.0.0.0/0           
out_internet_dns_s7  all  --  0.0.0.0/0            0.0.0.0/0           
out_internet_squid_c8  all  --  0.0.0.0/0            0.0.0.0/0           
out_internet_http_c9  all  --  0.0.0.0/0            0.0.0.0/0           
out_internet_https_c10  all  --  0.0.0.0/0            0.0.0.0/0           
out_internet_ftp_c11  all  --  0.0.0.0/0            0.0.0.0/0           
out_internet_smtp_c12  all  --  0.0.0.0/0            0.0.0.0/0           
out_internet_smtps_c13  all  --  0.0.0.0/0            0.0.0.0/0           
out_internet_ssh_c14  all  --  0.0.0.0/0            0.0.0.0/0           
out_internet_dns_c15  all  --  0.0.0.0/0            0.0.0.0/0           
out_internet_ping_c16  all  --  0.0.0.0/0            0.0.0.0/0           
out_internet_rsync_c17  all  --  0.0.0.0/0            0.0.0.0/0           
out_internet_ntp_c18  all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED 
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 5 LOG flags 0 level 4 prefix `''OUT-internet':'' 
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain out_internet_dns_c15 (1 references)
target     prot opt source               destination         
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:53 state NEW,ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:53 state NEW,ESTABLISHED 

Chain out_internet_dns_s7 (1 references)
target     prot opt source               destination         
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spt:53 state ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:53 state ESTABLISHED 

Chain out_internet_ftp_c11 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:32768:61000 dpt:21 state NEW,ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:32768:61000 dpt:20 state ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:32768:61000 dpts:1024:65535 state RELATED,ESTABLISHED 

Chain out_internet_ftp_s5 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:21 dpts:1024:65535 state ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:20 dpts:1024:65535 state RELATED,ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:32768:61000 dpts:1024:65535 state ESTABLISHED 

Chain out_internet_http_c9 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:32768:61000 dpt:80 state NEW,ESTABLISHED 

Chain out_internet_http_s4 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:80 dpts:1024:65535 state ESTABLISHED 

Chain out_internet_https_c10 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:32768:61000 dpt:443 state NEW,ESTABLISHED 

Chain out_internet_imap_s1 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:143 dpts:1024:65535 state ESTABLISHED 

Chain out_internet_imaps_s2 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:993 dpts:1024:65535 state ESTABLISHED 

Chain out_internet_ntp_c18 (1 references)
target     prot opt source               destination         
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spt:123 dpt:123 state NEW,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spts:32768:61000 dpt:123 state NEW,ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:123 dpt:123 state NEW,ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:32768:61000 dpt:123 state NEW,ESTABLISHED 

Chain out_internet_ping_c16 (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           state NEW,ESTABLISHED icmp type 8 

Chain out_internet_rsync_c17 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:32768:61000 dpt:873 state NEW,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spts:32768:61000 dpt:873 state NEW,ESTABLISHED 

Chain out_internet_smtp_c12 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:32768:61000 dpt:25 state NEW,ESTABLISHED 

Chain out_internet_smtp_s3 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:25 dpts:1024:65535 state ESTABLISHED 

Chain out_internet_smtps_c13 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:32768:61000 dpt:465 state NEW,ESTABLISHED 

Chain out_internet_squid_c8 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:32768:61000 dpt:3128 state NEW,ESTABLISHED 

Chain out_internet_ssh1_s6 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:1235 dpts:1024:65535 state ESTABLISHED 

Chain out_internet_ssh_c14 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:32768:61000 dpt:22 state NEW,ESTABLISHED 

Chain out_world (1 references)
target     prot opt source               destination         
out_world_all_c1  all  --  0.0.0.0/0            0.0.0.0/0           
out_world_irc_c2  all  --  0.0.0.0/0            0.0.0.0/0           
out_world_ftp_c3  all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED 
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 5 LOG flags 0 level 4 prefix `''OUT-world':'' 
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain out_world_all_c1 (1 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state NEW,ESTABLISHED 

Chain out_world_ftp_c3 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:32768:61000 dpt:21 state NEW,ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:32768:61000 dpt:20 state ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:32768:61000 dpts:1024:65535 state RELATED,ESTABLISHED 

Chain out_world_irc_c2 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:32768:61000 dpt:6667 state NEW,ESTABLISHED 

Chain pr_internet_fragments (1 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 5 LOG flags 0 level 4 prefix `'PACKET FRAGMENTS:'' 
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain pr_internet_icmpflood (1 references)
target     prot opt source               destination         
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 100/sec burst 50 
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 5 LOG flags 0 level 4 prefix `'ICMP FLOOD:'' 
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain pr_internet_malbad (4 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 5 LOG flags 0 level 4 prefix `'MALFORMED BAD:'' 
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain pr_internet_malnull (1 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 5 LOG flags 0 level 4 prefix `'MALFORMED NULL:'' 
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain pr_internet_malxmas (1 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 5 LOG flags 0 level 4 prefix `'MALFORMED XMAS:'' 
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain pr_internet_nosyn (1 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 5 LOG flags 0 level 4 prefix `'NEW TCP w/o SYN:'' 
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain pr_internet_synflood (1 references)
target     prot opt source               destination         
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 100/sec burst 50 
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 5 LOG flags 0 level 4 prefix `'SYN FLOOD:'' 
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

```
the 3th command 
ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:50:fc:26:7a:3a  
          inet6 addr: fe80::250:fcff:fe26:7a3a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7569 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5345318 (5.3 MB)  TX bytes:1744703 (1.7 MB)
          Interrupt:16 Base address:0x9400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6841 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6841 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:198599 (198.5 KB)  TX bytes:198599 (198.5 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.102.4.64  P-t-P:10.102.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:6823 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8427 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:5147010 (5.1 MB)  TX bytes:1517557 (1.5 MB)

```
please my friend where is the wrong in my configuration 
and thank's again ..... ):P

---

### Post by cdenley on 2009-04-14
Your server is running ssh on port 1235, and it does not appear to have the IP address 192.168.0.1 currently configured.

```

ssh -p 1235 10.102.4.64

```

---

### Post by bnejoker on 2009-04-14
Your server is running ssh on port 1235, and it does not appear to have the IP address 192.168.0.1 currently configured.
hi .
when i write ssh -p 1235 10.102.4.64 in terminal it comming that message
```

ssh -p 1235 10.102.4.64
ssh_exchange_identification: Connection closed by remote host

```
:)
and how i appear to have the IP address 192.168.0.1 currently configured.
verry thank's for you .....

---

### Post by spynappels on 2009-04-15
Your eth0 interface does not appear to have an IPv4 address. Can you post your /etc/network/interfaces file to see if you are using static or dhcp addressing. Then we can get you IP address sorted out.

Stefan.

---

### Post by bnejoker on 2009-04-15
hi,again......

1-this is my network interfaces file

```
                
auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual
	name LAN
	address 192.168.0.1
	netmask 255.255.255.0
	broadcast 192.168.0.255
	network 192.168.0.0
        gateway 192.168.0.1

```
2-and when i put these command in terminal
```
nedjemeddine@nedjemeddine-desktop:~$ ssh 10.102.0.87 -p 22
The authenticity of host '10.102.0.87 (10.102.0.87)' can't be established.
RSA key fingerprint is d6:49:5b:03:a4:3d:7e:a6:2e:6e:7b:c2:8c:2a:a6:bf.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '10.102.0.87' (RSA) to the list of known hosts.
nedjemeddine@10.102.0.87's password: 
Linux nedjemeddine-desktop 2.6.27-11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
Last login: Wed Jan  5 07:55:44 2000 from 10.102.3.84
nedjemeddine@nedjemeddine-desktop:~$ 

```
thnaks ...... ):P

---

