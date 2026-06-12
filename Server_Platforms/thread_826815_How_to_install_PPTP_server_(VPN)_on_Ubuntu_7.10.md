---
title: "How to install PPTP server (VPN) on Ubuntu 7.10"
date: 2008-06-12
forum: Server Platforms
---

### Post by csurlee on 2008-06-12
Poptop is the PPTP server solution for Linux.
What is PPTP?

PPTP stands for Point to Point Tunneling Protocol. It was developed by a consortium including Microsoft and is used for establishing VPN (Virtual Private Network) tunnels across the Internet. This allows remote users to securely and inexpensively access their corporate network from anywhere on the Internet.

PPTP uses a client-server model for establishing VPN connections. Most Microsoft operating systems ship with a PPTP client, so there is no need to purchase third-party client software. PPTP has the additional advantage over other VPN technologies of being easy to setup.
What is Poptop?

Before Poptop, no solution existed if you wish to connect PPTP clients to Linux servers. Using Poptop, Linux servers can now function seamlessly in a PPTP VPN environment. This enables administrators to leverage the considerable benefits of both Microsoft and Linux operating systems.

The current release version supports Windows 95/98/Me/NT/2000/XP PPTP clients and Linux PPTP clients.

Poptop is free software, licensed under the terms of the GNU GPL.

Features of Poptop include:

    * Microsoft compatible authentication and encryption (MSCHAPv2, MPPE 40 - 128 bit RC4 encryption)
    * Support for multiple client connections
    * Seamless integration into a Microsoft network environment (LDAP, SAMBA) using RADIUS plugin
    * Works with Windows 95/98/Me/NT/2000/XP PPTP clients
    * Works with Linux PPTP client
    * Poptop is, and will remain, totally free under the GNU General Public License

How to install Poptop (PPTPD)?

    * Use this command:

apt-get install pptpd -y

    * Edit the /etc/pptpd.conf file like this

nano /etc/pptpd.conf

The file looks like this:
```
    ###############################################
    # $Id: pptpd.conf 4255 2004-10-03 18:44:00Z rene $
    #
    # Sample Poptop configuration file /etc/pptpd.conf
    #
    # Changes are effective when pptpd is restarted.
    ###############################################

    # TAG: ppp
    #    Path to the pppd program, default ‘/usr/sbin/pppd’ on Linux
    #
    #ppp /usr/sbin/pppd

    # TAG: option
    #    Specifies the location of the PPP options file.
    #    By default PPP looks in ‘/etc/ppp/options’
    #
    option /etc/ppp/pptpd-options

    # TAG: debug
    #    Turns on (more) debugging to syslog
    #
    #debug

    # TAG: stimeout
    #    Specifies timeout (in seconds) on starting ctrl connection
    #
    # stimeout 10

    # TAG: noipparam
    #       Suppress the passing of the client’s IP address to PPP, which is
    #       done by default otherwise.
    #
    #noipparam

    # TAG: logwtmp
    #    Use wtmp(5) to record client connections and disconnections.
    #
    logwtmp

    # TAG: bcrelay <if>
    #    Turns on broadcast relay to clients from interface <if>
    #
    #bcrelay eth1

    # TAG: localip
    # TAG: remoteip
    #    Specifies the local and remote IP address ranges.
    #
    #       Any addresses work as long as the local machine takes care of the
    #       routing.  But if you want to use MS-Windows networking, you should
    #       use IP addresses out of the LAN address space and use the proxyarp
    #       option in the pppd options file, or run bcrelay.
    #
    #    You can specify single IP addresses seperated by commas or you can
    #    specify ranges, or both. For example:
    #
    #        192.168.0.234,192.168.0.245-249,192.168.0.254
    #
    #    IMPORTANT RESTRICTIONS:
    #
    #    1. No spaces are permitted between commas or within addresses.
    #
    #    2. If you give more IP addresses than MAX_CONNECTIONS, it will
    #       start at the beginning of the list and go until it gets
    #       MAX_CONNECTIONS IPs. Others will be ignored.
    #
    #    3. No shortcuts in ranges! ie. 234-8 does not mean 234 to 238,
    #       you must type 234-238 if you mean this.
    #
    #    4. If you give a single localIP, that’s ok - all local IPs will
    #       be set to the given one. You MUST still give at least one remote
    #       IP for each simultaneous client.
    #
    # (Recommended)
    #localip 192.168.0.1
    #remoteip 192.168.0.234-238,192.168.0.245
    # or
    localip 192.168.101.1      <— THIS IS YOUR SERVER IP
    remoteip 192.168.101.200-245  <—- THIS WILL BE THE IP’S FOR THE CLIENTS 
```

    * Now you will need to add a user and password in the /etc/ppp/chap-secrets file. The user will login with this user and password

nano /etc/ppp/chap-secrets

    * add a user like this:
```
    # Secrets for authentication using CHAP
    # client    server    secret            IP addresses

    user      pptpd     password               “*”
```

  > The "*" can be a IP address (Ex. 222.222.222.222) and the client will be able to connect only from this IP address or you can put * and the client will be able to connect from anyware

    * Kill the pptpd service and start it

killall pptpd

pptpd

DONE.
I hope this is a usefull howto for everyone

---

### Post by gtdaqua on 2008-06-12
good one. but the post is more like asking a question. modify the title to reflect "HOW TO:" - this will specifically mean that this is a guide to install PPTP server.

---

### Post by [vu] on 2008-06-12
Nice How-to

I used poptop in fedora and ubuntu and work very well.

Also, to use more features, you can edit the file /etc/ppp/options.pptpd (i dont remember the correct name, but its something like that)
There you can activate encriptation, compression, radius plugin..

Sorry for my english, im a Spanish speaker

---

### Post by csurlee on 2008-06-13
Thanks, i changed the title :)

---

### Post by csurlee on 2008-06-13
> **'[vu] said:**
> Nice How-to
I used poptop in fedora and ubuntu and work very well.

Also, to use more features, you can edit the file /etc/ppp/options.pptpd (i dont remember the correct name, but its something like that)
There you can activate encriptation, compression, radius plugin..

Sorry for my english, im a Spanish speaker

The file you specify /etc/ppp/pptpd-options , there you can modify encription, etc. Good observation, thanks :)

---

### Post by orangey on 2008-06-27
Hi, I'm a little confused as to the ips.  Localip is the ip of the server, so if my ubuntu box is 192.168.1.100, then that's what I should set it to?  Or should I set it to some free address on the subnet?  Remoteip range is also on the same subnet?  Or external?  Also, I have a DHCP server on the network, can I get the clients to get DHCP addrs and DNS, WINS, DefaultRouter, etc?

Ty.

Edit: Also do I need to touch iptables to allow GRE and port 1723?  What about enableing ip packet forwarding in the sysctl?

---

### Post by csurlee on 2008-06-27
> **orangey said:**
> Hi, I'm a little confused as to the ips.  Localip is the ip of the server, so if my ubuntu box is 192.168.1.100, then that's what I should set it to?  Or should I set it to some free address on the subnet?  Remoteip range is also on the same subnet?  Or external?  Also, I have a DHCP server on the network, can I get the clients to get DHCP addrs and DNS, WINS, DefaultRouter, etc?

Ty.

Edit: Also do I need to touch iptables to allow GRE and port 1723?  What about enableing ip packet forwarding in the sysctl?
@orangey: 
     Hello, 
So if your server Ip address is 192.168.1.100 on the **/etc/pptpd.conf**
 file in this line: **localip 192.168.101.1** you will put your server IP in your case 192.168.1.100. On this line: **remoteip 192.168.101.200-245  **you can put you remote IP's or IP range in my case for you for EX.  **remoteip 192.168.1.200-245  **. The PPTPD service will get for your clients the IP-s DNS WINS GW etc. On my servers i use DHCP and PPTPD and i have no problems when i want to connect the PPTPD service will give me the IP DNS etc. So you can use DHCP and PPTPD withe no problems.

      Have a good day! If you have other questions dont hesitate to write it. ;)

---

### Post by orangey on 2008-06-27
Thanks for the prompt response.  Tried that and it didn't seem to help.  I keep getting error 619.  In the logs, it stops and says "LCP: timeout sending Config-Requests".  I suspect GRE or IPsec might not be allowed properly on my client side.  I'll ahve to try again later.  Thanks though.

---

### Post by Kolipoki on 2008-06-27
Would with this work in 8.04 too?

---

### Post by csurlee on 2008-07-01
> **Kolipoki said:**
> Would with this work in 8.04 too?
Hello,
  this days i will try it but i think will work on 8.04 to

---

### Post by laos on 2008-07-12
i made exactly you tell, but in the client(windows xp sp2) i got error:619 after user and password checks, my server is 8.04 and i redirect only the port 1723 in the router to the server. some idea? thanks

---

### Post by Usta_AsH on 2008-08-30
Hi, I did everything nicely.
Client can connect to VPN server. Connection accepts. But the problem is, client cannot connect to internet but client can ping  to client's ip address and server ip adress not another ip address else. my ifconfig is:

eth0 Link encap:Ethernet HWaddr 00:06:5B:5E:10:8D
inet addr:207.10.234.175 Bcast:207.10.239.255 Mask:255.255.248.0
inet6 addr: fe80::206:5bff:fe5e:108d/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:394300 errors:0 dropped:0 overruns:1 frame:0
TX packets:3139 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:27426894 (26.1 MiB) TX bytes:547112 (534.2 KiB)
Interrupt:11 Base address:0x4c00

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:340 errors:0 dropped:0 overruns:0 frame:0
TX packets:340 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:193256 (188.7 KiB) TX bytes:193256 (188.7 KiB)

I also another real wan ip address(it is dedicated server) which is 207.10.234.176.

What should I write to localip and remoteip?

---

### Post by CXT on 2008-12-11
please guide me to install PPDPD with FREERADIUS Authentication. thanks,

---

### Post by RayVad on 2008-12-24
Installed PPTPD in Hardy Heron (8.04) with Shorewall.

But have some issues left:

- When stopping the server by /etc/init.d/pptpd stop the server stops but the client still has it's connection open.
Should think that his client will disconnect also.

- Strange behaviour like pinging is possible from LAN to client and later on it isn't possible anymore. While from client it is still possible to ping the LAN. Routing problem?!?

- In webmin i can see the active connection, but no PPP interface and Username is displayed. Both says "Unknown"

Any help/advice would be appreciated.
Thanks in advance.
Ray

---

### Post by xodonnell on 2009-03-25
I have been having the same problem.  In Active connections the PPP Interface and Username fields are unknown.  

I am also curious if there is a log file that records which user is logging in, at what time and for how long.


Has no one else noticed this as a problem or are we the only ones who cannot see the username of the user connected?

---

### Post by taewoo on 2009-09-22
Hi all.
@[csurlee]("http://ubuntuforums.org/member.php?u=476097"): Thanks for posting this. Linux noobs like me will appreciate this.

I've followed the steps... i can connect to my VPN server from Windows XP via VPN manager and do auth... The machine gets the right IP, but i can't seem to send or receive any data from it.

Are there some other steps that I need to do? I've read in other foums about changing IP forwarding and iptable entries...?

---

### Post by csurlee on 2009-09-24
> **taewoo said:**
> Hi all.
@[csurlee]("http://ubuntuforums.org/member.php?u=476097"): Thanks for posting this. Linux noobs like me will appreciate this.

I've followed the steps... i can connect to my VPN server from Windows XP via VPN manager and do auth... The machine gets the right IP, but i can't seem to send or receive any data from it.

Are there some other steps that I need to do? I've read in other foums about changing IP forwarding and iptable entries...?


Normaly its working, you will need to look at the log files.


NOTE.: this howto wasmade for 7.10, for other versions its posibile to crash

---

### Post by xcitchx on 2012-08-23
This is working for ubuntu 12.04 on xen vps?. And how to set remoteip if i use dynamic ip dialup connection?. Thanks

---

### Post by cybercity@localhost on 2012-09-23
nice post! but there is a question i would like to ask that how can we apply bandwidth limitations on the user connecting to this server?

---

