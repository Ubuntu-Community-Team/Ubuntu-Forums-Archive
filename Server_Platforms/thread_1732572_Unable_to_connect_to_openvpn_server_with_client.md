---
title: "Unable to connect to openvpn server with client"
date: 2011-04-18
forum: Server Platforms
---

### Post by corkscrew on 2011-04-18
I'm a newbie to working with server.
System
Ubuntu Lucid Server (10.04.1)
Kernel Linux 2.6.32-30-server

NoMachine NX set up
Webmin 1.53

Netgear DGN2000 ADSL Router

Mixed LAN behind router including the Server , a NAS, IP Camera, win 7 box and 2 linux Ubuntu Lucid Lynx boxes one wired one wirless.

I would like to set up a VPN on my server machine so I can access my LAN and if possible use NOMachine NX over the connection.

I started out by following this how to set up vpn using webmin [http://www.frontiernet.net/~beakmyn/vpn%20howto/Complete%20Home%20VPN%20Howto%20Guide.html](http://www.frontiernet.net/~beakmyn/vpn%20howto/Complete%20Home%20VPN%20Howto%20Guide.html)

Completed everything and exported client files.

I am now trying to connect to server machine from my laptop, my first question is can I do this since both machines are on the same LAN behind the router?

I have tried to set up a vpn connection via the network manager it successfully imports the client config files which i exported.

When I try to start the vpn connection nothing appears to happen?

I open up daemon log and see the following message

```
u300 NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.openvpn'...
Apr 18 10:58:52 u300 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 2072
Apr 18 10:58:52 u300 NetworkManager: <WARN>  vpn_service_watch_cb(): VPN service 'org.freedesktop.NetworkManager.openvpn' exited with error: 1
Apr 18 10:58:52 u300 NetworkManager: <info>  Policy set 'Auto homewifi' (wlan0) as default for routing and DNS.
Apr 18 10:58:57 u300 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' did not start in time, cancelling connections
Apr 18 10:59:16 u300 kernel: [  252.053309] CE: hpet increasing min_delta_ns to 15000 nsec

```

What am I missing or doing wrong?

---

### Post by Shwick2 on 2011-04-18
The link to the manual you read doesn't work.

Yes you can connect to your vpn from the same lan that your server is on.

Is the vpn port open on your server?

Edit: also try using the openvpn client instead of ubuntu's network manager to make the connection, unless that is  waht you are doing

---

### Post by corkscrew on 2011-04-19
> **Shwick2 said:**
> The link to the manual you read doesn't work.

Yes you can connect to your vpn from the same lan that your server is on.

Is the vpn port open on your server?

Edit: also try using the openvpn client instead of ubuntu's network manager to make the connection, unless that is  waht you are doing

Sorry about the link here it is again 
[http://www.frontiernet.net/~beakmyn/vpn%20howto/Complete%20Home%20VPN%20Howto%20Guide.html](http://www.frontiernet.net/~beakmyn/vpn%20howto/Complete%20Home%20VPN%20Howto%20Guide.html)

The how to on this page is relevant since it will show you all the settings I have in my server, the only thing I didn't do on advisement was the firewall stuff since my server is behind a router.

In my vpn configuration viewed with webmin it is set for port 1194 and I have this port opened in my router.

How would I go about using the openvpn client instead of network manager?

---

### Post by Shwick2 on 2011-04-19
I am only recommending you try something else if you can't find a solution.

I googled your error and found back in 2008 people had the same problem, [http://ubuntuforums.org/archive/index.php/t-979085.html](http://ubuntuforums.org/archive/index.php/t-979085.html)
Resulting bug report, [http://ubuntuforums.org/archive/index.php/t-979085.html](http://ubuntuforums.org/archive/index.php/t-979085.html)

Try checking /var/log/daemon.log and see what openvpn is reporting.

Maybe you didn't configure tun0.

This guide is saying network manager is not good for openvpn, [http://ubuntuforums.org/showthread.php?t=1021592](http://ubuntuforums.org/showthread.php?t=1021592)

So I hope you find the solution but if not try something else, such as setting up openvpn using the official openvpn guide, [http://openvpn.net/index.php/open-source/documentation/howto.html](http://openvpn.net/index.php/open-source/documentation/howto.html)

---

### Post by corkscrew on 2011-04-19
Thanks for trying to help but tried all these, my 1st post displays error from daemon.log trouble is I dont know what it means

---

### Post by corkscrew on 2011-04-20
I'm a newbie to working with server. I tried posting under networks but didn't get a response which would fix.
System
Ubuntu Lucid Server (10.04.1)
Kernel Linux 2.6.32-30-server

NoMachine NX set up
Webmin 1.54

Netgear DGN2000 ADSL Router

Mixed LAN behind router including the Server , a NAS, IP Camera, win 7 box and 2 linux Ubuntu Lucid Lynx boxes one wired one wirless.

I would like to set up a VPN on my server machine so I can access my LAN and if possible use NOMachine NX over the connection.

I started out by following this how to set up vpn using webmin [http://www.frontiernet.net/~beakmyn/vpn%20howto/Complete%20Home%20VPN%20Howto%20Guide.html](http://www.frontiernet.net/~beakmyn/vpn%20howto/Complete%20Home%20VPN%20Howto%20Guide.html)

Completed everything and exported client files.

I am now trying to connect to server machine from my laptop, my first question is can I do this since both machines are on the same LAN behind the router?

I have tried to set up a vpn connection via the network manager it successfully imports the client config files which i exported.

When I try to start the vpn connection nothing appears to happen?

I open up daemon log and see the following message

```
u300 NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.openvpn'...
Apr 18 10:58:52 u300 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 2072
Apr 18 10:58:52 u300 NetworkManager: <WARN>  vpn_service_watch_cb(): VPN service 'org.freedesktop.NetworkManager.openvpn' exited with error: 1
Apr 18 10:58:52 u300 NetworkManager: <info>  Policy set 'Auto homewifi' (wlan0) as default for routing and DNS.
Apr 18 10:58:57 u300 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' did not start in time, cancelling connections
Apr 18 10:59:16 u300 kernel: [  252.053309] CE: hpet increasing min_delta_ns to 15000 nsec

```

What am I missing or doing wrong?

---

### Post by byStanderone on 2011-04-20
hi, 
would assume that you're connected to the internet while doing your experiment...am not sure if a vpn connection could be done, since all your box behind the router will have the same external ip addresses, server or client likewise.

---

### Post by spynappels on 2011-04-20
That's actually quite a good how-to. It does leave out one or two small issues though, which probably don't have a bearing on your present issues but will probably cause problems down the line.

For your issue now, you can start the daemon in such a way as to see exactly see what is happening:

```
sudo openvpn --config /path/to/config.conf | tee openvpn_start.txt
```

EDIT: You may have to do this on the client from outside the LAN, using a USB Modem. Doing this on the server will also give us some background info /EDIT

Make sure the service is stopped before you do this, but this will give a verbose step-by-step of the service starting. The txt file created can be uploaded here so we can have a look at the output of the command to determine where the problems occur.

What is the subnet of your home LAN? Even just giving us the LAN IP address of the VPN server would do, it will let us see what your LAN subnet is and whether you may experience routing issues when accessing your home LAN from a remote location.

---

### Post by cariboo on 2011-04-20
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by corkscrew on 2011-04-20
> **spynappels said:**
> That's actually quite a good how-to. It does leave out one or two small issues though, which probably don't have a bearing on your present issues but will probably cause problems down the line.

For your issue now, you can start the daemon in such a way as to see exactly see what is happening:

```
sudo openvpn --config /path/to/config.conf | tee openvpn_start.txt
```

EDIT: You may have to do this on the client from outside the LAN, using a USB Modem. Doing this on the server will also give us some background info /EDIT

Make sure the service is stopped before you do this, but this will give a verbose step-by-step of the service starting. The txt file created can be uploaded here so we can have a look at the output of the command to determine where the problems occur.

What is the subnet of your home LAN? Even just giving us the LAN IP address of the VPN server would do, it will let us see what your LAN subnet is and whether you may experience routing issues when accessing your home LAN from a remote location.

Ok here's the output from the client but it is from inside the LAN
```
sudo openvpn --config /etc/openvpn/u300clientkey.conf | tee openvpn_start.txt
Wed Apr 20 17:27:15 2011 OpenVPN 2.1.0 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [MH] [PF_INET6] [eurephia] built on Jul 20 2010
Wed Apr 20 17:27:15 2011 WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Wed Apr 20 17:27:15 2011 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Wed Apr 20 17:27:15 2011 Cannot load certificate file u300clientkey.crt: error:02001002:system library:fopen:No such file or directory: error:20074002:BIO routines:FILE_CTRL:system lib: error:140AD002:SSL routines:SSL_CTX_use_certificate_file:system lib
Wed Apr 20 17:27:15 2011 Exiting
```

The same command run on the server
```
sudo openvpn --config /etc/openvpn/Arbirlot-VPN-Server.conf | tee openvpn_start.txt
Wed Apr 20 16:27:44 2011 Warning: Error redirecting stdout/stderr to --log file: servers/Arbirlot-VPN-Server/logs/openvpn.log: No such file or directory (errno=2)
Wed Apr 20 16:27:44 2011 OpenVPN 2.1.0 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [MH] [PF_INET6] [eurephia] built on Jul 20 2010
Wed Apr 20 16:27:44 2011 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Wed Apr 20 16:27:44 2011 Note: cannot open servers/Arbirlot-VPN-Server/logs/openvpn-status.log for WRITE
Wed Apr 20 16:27:44 2011 Note: cannot open servers/Arbirlot-VPN-Server/logs/ipp.txt for READ/WRITE
Wed Apr 20 16:27:44 2011 Cannot open keys/arbirlot/dh2048.pem for DH parameters: error:02001002:system library:fopen:No such file or directory: error:2006D080:BIO routines:BIO_new_file:no such file
Wed Apr 20 16:27:44 2011 Exiting
```

Subnet of my home LAN is 198.168.25.*

Nothing to do with this I know but using various how to's I managed set up NXNoMachine on the same server and can access it remotely with my laptop via my dynamic Domain name I have set up.

---

### Post by spynappels on 2011-04-21
Could you try using absolute paths for your keys and certs in your conf files?

/etc/openvpn/keys/keyfile.key  or whatever the full path is on your system?

---

### Post by corkscrew on 2011-04-21
> **spynappels said:**
> Could you try using absolute paths for your keys and certs in your conf files?

/etc/openvpn/keys/keyfile.key  or whatever the full path is on your system?

Ok I edited conf as you suggested here is the modified file

```
port 1194
proto udp
dev tun0
ca keys/etc/openvpn/keys/arbirlot/ca.crt
cert keys/etc/openvpn/keys/arbirlot/serverkey.crt
key keys/etc/openvpn/keys/arbirlot/serverkey.key
dh keys/etc/openvpn/keys/arbirlot/dh2048.pem
server 10.8.0.0 255.255.255.0
crl-verify keys/etc/openvpn/keys/arbirlot/crl.pem
ifconfig-pool-persist servers/Arbirlot-VPN-Server/logs/ipp.txt
tls-auth servers/etc/openvpn/servers/Arbirlot-VPN-Server/ta.key 0
cipher DES-CFB
user nobody
group nogroup
status servers/etc/openvpn/servers/Arbirlot-VPN-Server/logs/openvpn-status.log
log-append servers/etc/openservers/Arbirlot-VPN-Server/logs/openvpn.log
verb 2
mute 20
max-clients 3
keepalive 10 120
client-config-dir /etc/openvpn/servers/Arbirlot-VPN-Server/ccd
tls-server
comp-lzo
persist-key
persist-tun
ccd-exclusive
push "route 198.168.25.52 255.255.255.0"
push "redirect-gateway"
```

I also edited absolute path to log files. The result is that now the server wont start.
```
sudo /etc/init.d/openvpn restart
 * Stopping virtual private network daemon(s)...
 *   No VPN is running.
 * Starting virtual private network daemon(s)...
 *   Autostarting VPN 'Arbirlot-VPN-Server'
   ...fail!
```

I then re ran the command from your last post, looking at the output could all these problems be related to file permissions?

```
sudo openvpn --config /etc/openvpn/Arbirlot-VPN-Server.conf | tee openvpn_start.txt
Thu Apr 21 12:26:26 2011 Warning: Error redirecting stdout/stderr to --log file: servers/etc/openservers/Arbirlot-VPN-Server/logs/openvpn.log: No such file or directory (errno=2)
Thu Apr 21 12:26:26 2011 OpenVPN 2.1.0 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [MH] [PF_INET6] [eurephia] built on Jul 20 2010
Thu Apr 21 12:26:26 2011 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Thu Apr 21 12:26:26 2011 Note: cannot open servers/etc/openvpn/servers/Arbirlot-VPN-Server/logs/openvpn-status.log for WRITE
Thu Apr 21 12:26:26 2011 Note: cannot open servers/Arbirlot-VPN-Server/logs/ipp.txt for READ/WRITE
Thu Apr 21 12:26:26 2011 Cannot open keys/etc/openvpn/keys/arbirlot/dh2048.pem for DH parameters: error:02001002:system library:fopen:No such file or directory: error:2006D080:BIO routines:BIO_new_file:no such file
Thu Apr 21 12:26:26 2011 Exiting

```

I find the line in this output regarding the dh2048.pem a bit strange as you can see I from the config file i have altered the path to this file as well

---

### Post by spynappels on 2011-04-21
> **corkscrew said:**
> 
ca keys/etc/openvpn/keys/arbirlot/ca.crt
cert keys/etc/openvpn/keys/arbirlot/serverkey.crt
key keys/etc/openvpn/keys/arbirlot/serverkey.key
dh keys/etc/openvpn/keys/arbirlot/dh2048.pem
.....
crl-verify keys/etc/openvpn/keys/arbirlot/crl.pem
ifconfig-pool-persist servers/Arbirlot-VPN-Server/logs/ipp.txt
tls-auth servers/etc/openvpn/servers/Arbirlot-VPN-Server/ta.key 0
.....
status servers/etc/openvpn/servers/Arbirlot-VPN-Server/logs/openvpn-status.log
log-append servers/etc/openservers/Arbirlot-VPN-Server/logs/openvpn.log
...
client-config-dir /etc/openvpn/servers/Arbirlot-VPN-Server/ccd


If you look at the last quoted line and compare it to all the others, you will see that in all the others the path is still incorrect. Your system will not recognise keys/etc....... the correct path would be /etc/.....

Just double check the paths in the conf files again, and then try to start the service using the commands you used earlier with the --config switch to get a verbose listing of what is happening and where the issues are.

---

### Post by corkscrew on 2011-04-21
> **spynappels said:**
> If you look at the last quoted line and compare it to all the others, you will see that in all the others the path is still incorrect. Your system will not recognise keys/etc....... the correct path would be /etc/.....

Just double check the paths in the conf files again, and then try to start the service using the commands you used earlier with the --config switch to get a verbose listing of what is happening and where the issues are.

ok edited file to this
```
port 1194
proto udp
dev tun0
/etc/openvpn/keys/arbirlot/ca.crt
/etc/openvpn/keys/arbirlot/serverkey.crt
/etc/openvpn/keys/arbirlot/serverkey.key
/etc/openvpn/keys/arbirlot/dh2048.pem
server 10.8.0.0 255.255.255.0
/etc/openvpn/keys/arbirlot/crl.pem
ifconfig-pool-persist servers/Arbirlot-VPN-Server/logs/ipp.txt
tls-auth servers/etc/openvpn/servers/Arbirlot-VPN-Server/ta.key 0
cipher DES-CFB
user nobody
group nogroup
/etc/openvpn/servers/Arbirlot-VPN-Server/logs/openvpn-status.log
/etc/openservers/Arbirlot-VPN-Server/logs/openvpn.log
verb 2
mute 20
max-clients 3
keepalive 10 120
client-config-dir /etc/openvpn/servers/Arbirlot-VPN-Server/ccd
tls-server
comp-lzo
persist-key
persist-tun
ccd-exclusive
push "route 198.168.25.52 255.255.255.0"
push "redirect-gateway"
```

Ran both commands again...

```
sudo openvpn --config /etc/openvpn/Arbirlot-VPN-Server.conf | tee openvpn_start.txt
Options error: Unrecognized option or missing parameter(s) in /etc/openvpn/Arbirlot-VPN-Server.conf:4: /etc/openvpn/keys/arbirlot/ca.crt (2.1.0)
Use --help for more information.
```


```
> sudo /etc/init.d/openvpn restart 
 * Stopping virtual private network daemon(s)...
 *   No VPN is running.
 * Starting virtual private network daemon(s)...
 *   Autostarting VPN 'Arbirlot-VPN-Server'
   ...fail!
```

Sorry for my ignorance but whats the command to run to start openvpn and see whats happening?

---

### Post by spynappels on 2011-04-21
You need to change some items in the conf to the following, I may not have been clear enough:

```

port 1194
proto udp
dev tun0
ca /etc/openvpn/keys/arbirlot/ca.crt 
cert /etc/openvpn/keys/arbirlot/serverkey.crt
key /etc/openvpn/keys/arbirlot/serverkey.key
dh /etc/openvpn/keys/arbirlot/dh2048.pem
server 10.8.0.0 255.255.255.0
#/etc/openvpn/keys/arbirlot/crl.pem
ifconfig-pool-persist /etc/openvpn/servers/Arbirlot-VPN-Server/logs/ipp.txt
tls-auth /etc/openvpn/servers/Arbirlot-VPN-Server/ta.key 0
cipher DES-CFB
user nobody
group nogroup
status /etc/openvpn/servers/Arbirlot-VPN-Server/logs/openvpn-status.log
log /etc/openvpn/servers/Arbirlot-VPN-Server/logs/openvpn.log
verb 2
mute 20
max-clients 3
keepalive 10 120
client-config-dir /etc/openvpn/servers/Arbirlot-VPN-Server/ccd
tls-server
comp-lzo
persist-key
persist-tun
ccd-exclusive
push "route 198.168.25.52 255.255.255.0"
push "redirect-gateway"
```

Save the above config in the same place as the original config but with a different name such as test.conf

while in the directory where you saved it run the following command and paste back the output.

```
sudo openvpn --config test.conf
```

---

### Post by corkscrew on 2011-04-21
> **spynappels said:**
> You need to change some items in the conf to the following, I may not have been clear enough:

```

port 1194
proto udp
dev tun0
ca /etc/openvpn/keys/arbirlot/ca.crt 
cert /etc/openvpn/keys/arbirlot/serverkey.crt
key /etc/openvpn/keys/arbirlot/serverkey.key
dh/etc/openvpn/keys/arbirlot/dh2048.pem
server 10.8.0.0 255.255.255.0
#/etc/openvpn/keys/arbirlot/crl.pem
ifconfig-pool-persist /etc/openvpn/servers/Arbirlot-VPN-Server/logs/ipp.txt
tls-auth /etc/openvpn/servers/Arbirlot-VPN-Server/ta.key 0
cipher DES-CFB
user nobody
group nogroup
status /etc/openvpn/servers/Arbirlot-VPN-Server/logs/openvpn-status.log
log /etc/openvpn/servers/Arbirlot-VPN-Server/logs/openvpn.log
verb 2
mute 20
max-clients 3
keepalive 10 120
client-config-dir /etc/openvpn/servers/Arbirlot-VPN-Server/ccd
tls-server
comp-lzo
persist-key
persist-tun
ccd-exclusive
push "route 198.168.25.52 255.255.255.0"
push "redirect-gateway"
```

Save the above config in the same place as the original config but with a different name such as test.conf

while in the directory where you saved it run the following command and paste back the output.

```
sudo openvpn --config test.conf
```

ok done that here's the output 
```
sudo openvpn --config test.conf
Options error: Unrecognized option or missing parameter(s) in test.conf:4: /etc/openvpn/keys/arbirlot/ca.crt (2.1.0)
Use --help for more information.
```

seems to be the same file causing the problem?

---

### Post by spynappels on 2011-04-28
Hi, sorry for the delay in getting back to you. Can you paste the entire test.conf file exactly as it appears on your system please? I want to just check for extra or missing spaces, typos etc.

---

### Post by corkscrew on 2011-04-28
> **spynappels said:**
> Hi, sorry for the delay in getting back to you. Can you paste the entire test.conf file exactly as it appears on your system please? I want to just check for extra or missing spaces, typos etc.

Hey thanks very much for taking the time to help me, here's the contents of the test.conf file
```
port 1194
proto udp
dev tun0
/etc/openvpn/keys/arbirlot/ca.crt
/etc/openvpn/keys/arbirlot/serverkey.crt
/etc/openvpn/keys/arbirlot/serverkey.key
/etc/openvpn/keys/arbirlot/dh2048.pem
server 10.8.0.0 255.255.255.0
/etc/openvpn/keys/arbirlot/crl.pem
ifconfig-pool-persist servers/Arbirlot-VPN-Server/logs/ipp.txt
tls-auth servers/etc/openvpn/servers/Arbirlot-VPN-Server/ta.key 0
cipher DES-CFB
user nobody
group nogroup
/etc/openvpn/servers/Arbirlot-VPN-Server/logs/openvpn-status.log
/etc/openservers/Arbirlot-VPN-Server/logs/openvpn.log
verb 2
mute 20
max-clients 3
keepalive 10 120
client-config-dir /etc/openvpn/servers/Arbirlot-VPN-Server/ccd
tls-server
comp-lzo
persist-key
persist-tun
ccd-exclusive
push "route 198.168.25.52 255.255.255.0"
push "redirect-gateway"
```

---

### Post by spynappels on 2011-05-02
Hi Corkscrew,

Can you please compare your output to what I posted in post no. 15, there are still some differences which you will need to correct before it can work. Can you correct the conf file and try again please?

---

### Post by corkscrew on 2011-05-02
> **spynappels said:**
> Hi Corkscrew,

Can you please compare your output to what I posted in post no. 15, there are still some differences which you will need to correct before it can work. Can you correct the conf file and try again please?

Hi spynappels

Done it I just copied and pasted from your post #15 re ran command here's output
 ```
sudo openvpn --config test.conf
Options error: In [CMD-LINE]:1: Error opening configuration file: test.conf
Use --help for more information.
```
 
Here's test.conf file
```
port 1194
proto udp
dev tun0
ca /etc/openvpn/keys/arbirlot/ca.crt 
cert /etc/openvpn/keys/arbirlot/serverkey.crt
key /etc/openvpn/keys/arbirlot/serverkey.key
dh /etc/openvpn/keys/arbirlot/dh2048.pem
server 10.8.0.0 255.255.255.0
#/etc/openvpn/keys/arbirlot/crl.pem
ifconfig-pool-persist /etc/openvpn/servers/Arbirlot-VPN-Server/logs/ipp.txt
tls-auth /etc/openvpn/servers/Arbirlot-VPN-Server/ta.key 0
cipher DES-CFB
user nobody
group nogroup
status /etc/openvpn/servers/Arbirlot-VPN-Server/logs/openvpn-status.log
log /etc/openvpn/servers/Arbirlot-VPN-Server/logs/openvpn.log
verb 2
mute 20
max-clients 3
keepalive 10 120
client-config-dir /etc/openvpn/servers/Arbirlot-VPN-Server/ccd
tls-server
comp-lzo
persist-key
persist-tun
ccd-exclusive
push "route 198.168.25.52 255.255.255.0"
push "redirect-gateway"


```

---

