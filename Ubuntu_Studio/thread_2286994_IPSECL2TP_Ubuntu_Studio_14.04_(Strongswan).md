---
title: "IPSEC/L2TP Ubuntu Studio 14.04 (Strongswan)"
date: 2015-07-16
forum: Ubuntu Studio
---

### Post by Jason_West on 2015-07-16
My first question: Does Ubuntu support IPSEC/L2TP/PSK vpn CLIENT?
  My Second Question: Is there a front end "Network Manager" that supports IPSEC/L2TP and PSK?[INDENT]   
**Background:**
 [/INDENT]

In my endeavors I came across this article: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/264691](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/264691)  - which i have attempted to use the suggestions in - but am still not  able to get a working IPSEC/L2TP/PSK tunnel up as it refrences using  openswan.[INDENT]   
**The Situation:**
 [/INDENT]

I was using Werner Jaeger ipsec client and it worked flawlessly -  about 3 or 4 months ago it has stopped working. I have attempted to  reinstall it on my desktop using Ubuntu Studio 14.04 and Debian 8 and I  get the same results. 
  I now understand that openswan was removed from the distro and  superseded by strongswan. I very much would not like to have to move  away from linux as one of the things i do is work from home and need vpn  to monitor / test / configure networks. Can someone point me to a good  tutorial on configuring it as a client? [INDENT]   
**Side note:**
 [/INDENT]

I found this topic [L2TP IPsec VPN client on Ubuntu 14.10]("http://askubuntu.com/questions/569763/l2tp-ipsec-vpn-client-on-ubuntu-14-10")  - tried all the things in there - still nothing - also that article did  not answer the question being that it is for 14.10 and im using 14.04  it is technically different - I have done alot of things thus far to get  it to work and nothing has helped. Any help would be much  appreciated!!!

---

### Post by Jason_West on 2015-07-21
Ok, I have made a little head-way, though it does not answer the  initial question/problem in doing this with strongswan - If my only option is to run openswan as opposed to strongswan then fine....

I rolled back to openswan on my machine and for the first time in months  it gets connected - though after a couple seconds it drops - I figured  I'd run 'ipsec verify' to check statuses - below is my steps and my logs  minus the sensitive details - any thoughts would be much appreciated
  
What I ran with to install - 
  
sudo apt-get install openswan
sudo apt-get install xl2tpd
sudo apt-get install l2tp-ipsec-vpn
  
I then configured the gui applet
  
I then configured the file:
  /etc/ppp/work.options.xl2tpd[INDENT]   
-Logs-

 [/INDENT]
jason@casa-wesella:~$ sudo ipsec verify

Checking your system to see if IPsec got installed and started correctly:

Version check and ipsec on-path                                 [OK]

Linux Openswan U2.6.38/K3.16.0-43-lowlatency (netkey)

Checking for IPsec support in kernel                            [OK]

 SAref kernel support                                           [N/A]

 NETKEY:  Testing XFRM related proc values                      [FAILED]

  Please disable /proc/sys/net/ipv4/conf/*/send_redirects
  or NETKEY will cause the sending of bogus ICMP redirects!     [FAILED]

  Please disable /proc/sys/net/ipv4/conf/*/accept_redirects
  or NETKEY will accept bogus ICMP redirects!                   [OK]

Checking that pluto is running                                  [OK]

 Pluto listening for IKE on udp 500                             [OK]

 Pluto listening for NAT-T on udp 4500                          [OK]

Two or more interfaces found, checking IP forwarding        Checking NAT and MASQUERADEing                                  [OK]

Checking for 'ip' command                                       [OK]

Checking /bin/sh is not /bin/dash                               [WARNING]

Checking for 'iptables' command                                 [OK]

Opportunistic Encryption Support                                [DISABLED][INDENT] 


Logs from applet -
 [/INDENT]

Jul 21 15:23:45.505 ipsec_setup: Starting Openswan IPsec U2.6.38/K3.16.0-43-lowlatency...
  Jul 21 15:23:46.412 ipsec__plutorun: Starting Pluto subsystem...
  Jul 21 15:23:46.659 ipsec__plutorun: adjusting ipsec.d to /etc/ipsec.d
  Jul 21 15:23:46.749 recvref[30]: Protocol not available
  Jul 21 15:23:46.749 xl2tpd[2313]: This binary does not support kernel L2TP.
  Jul 21 15:23:46.749 xl2tpd[2316]: xl2tpd version xl2tpd-1.3.6 started on casa-wesella PID:2316
  Jul 21 15:23:46.750 xl2tpd[2316]: Written by Mark Spencer, Copyright (C)  1998, Adtran, Inc.
  Jul 21 15:23:46.750 xl2tpd[2316]: Forked by Scott Balmos and David Stipp, (C) 2001
  Jul 21 15:23:46.750 xl2tpd[2316]: Inherited by Jeff McAdams, (C) 2002
  Jul 21 15:23:46.750 xl2tpd[2316]: Forked again by Xelerance ([www.xelerance.com]("http://www.xelerance.com")) (C) 2006
  Jul 21 15:23:46.751 xl2tpd[2316]: Listening on IP address 0.0.0.0, port 1701
  Jul 21 15:23:46.752 Starting xl2tpd: xl2tpd.
  Jul 21 15:23:46.891 ipsec__plutorun: 027 bad right --id: does not look numeric and name lookup failed (ignored)
  Jul 21 15:23:46.892 ipsec__plutorun: 002 added connection description "Work"
  Jul 21 15:23:47.123 104 "Work" #1: STATE_MAIN_I1: initiate
  Jul 21 15:23:47.124 003 "Work" #1: received Vendor ID payload [RFC 3947] method set to=115 
  Jul 21 15:23:47.124 003 "Work" #1: received Vendor ID payload [Dead Peer Detection]
  Jul 21 15:23:47.124 003 "Work" #1: ignoring unknown Vendor ID payload [8299031757a36082c6a621de00050282]
  Jul 21 15:23:47.124 106 "Work" #1: STATE_MAIN_I2: sent MI2, expecting MR2
  Jul 21 15:23:47.124 003 "Work" #1: NAT-Traversal: Result using draft-ietf-ipsec-nat-t-ike (MacOS X): i am NATed
  Jul 21 15:23:47.124 108 "Work" #1: STATE_MAIN_I3: sent MI3, expecting MR3
  Jul 21 15:23:47.124 004 "Work" #1: STATE_MAIN_I4: ISAKMP SA  established {auth=OAKLEY_PRESHARED_KEY cipher=oakley_3des_cbc_192  prf=oakley_sha group=modp1024}
  Jul 21 15:23:47.125 117 "Work" #2: STATE_QUICK_I1: initiate
  Jul 21 15:23:47.125 003 "Work" #2: ignoring informational payload, type IPSEC_RESPONDER_LIFETIME msgid=8e08921c
  Jul 21 15:23:47.125 003 "Work" #2: NAT-Traversal: received 2 NAT-OA. ignored because peer is not NATed
  Jul 21 15:23:47.125 004 "Work" #2: STATE_QUICK_I2: sent QI2, IPsec SA  established transport mode {ESP=>0x37742a26 <0x478d0d00  xfrm=AES_128-HMAC_SHA1 NATOA=none NATD=none DPD=none}
  Jul 21 15:23:48.129 xl2tpd[2316]: Connecting to host Public IP, port 1701
  Jul 21 15:23:48.168 xl2tpd[2316]: Connection established to Public IP, 1701.  Local: 57627, Remote: 14608 (ref=0/0).
  Jul 21 15:23:48.194 xl2tpd[2316]: Calling on tunnel 57627
  Jul 21 15:23:48.212 xl2tpd[2316]: Call established with Public IP, Local: 14783, Remote: 14609, Serial: 1 (ref=0/0)
  Jul 21 15:23:48.212 xl2tpd[2316]: start_pppd: I'm running: 
  Jul 21 15:23:48.213 xl2tpd[2316]: "/usr/sbin/pppd" 
  Jul 21 15:23:48.213 xl2tpd[2316]: "passive" 
  Jul 21 15:23:48.213 xl2tpd[2316]: "nodetach" 
  Jul 21 15:23:48.214 xl2tpd[2316]: ":" 
  Jul 21 15:23:48.214 xl2tpd[2316]: "file" 
  Jul 21 15:23:48.214 xl2tpd[2316]: "/etc/ppp/Work.options.xl2tpd" 
  Jul 21 15:23:48.215 xl2tpd[2316]: "/dev/pts/6" 
  Jul 21 15:23:48.331 pppd[2427]: Plugin passprompt.so loaded.
  Jul 21 15:23:48.332 pppd[2427]: pppd 2.4.5 started by root, uid 0
  Jul 21 15:23:48.333 pppd[2427]: Using interface ppp0
  Jul 21 15:23:48.333 pppd[2427]: Connect: ppp0 <--> /dev/pts/6
  Jul 21 15:23:52.345 pppd[2427]: Remote message: Login ok
  Jul 21 15:23:52.346 pppd[2427]: PAP authentication succeeded
  Jul 21 15:23:52.390 pppd[2427]: Deflate (15) compression enabled
  Jul 21 15:23:52.429 pppd[2427]: local  IP address Private IP
  Jul 21 15:23:52.429 pppd[2427]: remote IP address Private IP
  Jul 21 15:24:31.977 Stopping xl2tpd: xl2tpd.
  Jul 21 15:24:31.977 xl2tpd[2316]: death_handler: Fatal signal 15 received
  Jul 21 15:24:31.979 pppd[2427]: Modem hangup
  Jul 21 15:24:31.979 pppd[2427]: Connect time 0.7 minutes.
  Jul 21 15:24:31.980 pppd[2427]: Sent 10334 bytes, received 13370 bytes.
  Jul 21 15:24:31.980 pppd[2427]: Connection terminated.
  Jul 21 15:24:31.993 ipsec_setup: Stopping Openswan IPsec...
  Jul 21 15:24:32.089 pppd[2427]: Exit.

---

### Post by gene475001 on 2015-08-27
You may have already tried this, but I'll throw it out. I managed to get the client working in Mint 17.2 (based on Ubuntu 14.04) as well as Xubuntu 14.04 using Openswan 1:2.6.38-1 and the l2tp-ipsec-vpn-daemon 0.9.0-1 on a relatively fresh installation. I had tried Strongswan, but backed it out and uninstalled it just before trying Openswan again. I'm pretty sure I cleaned out StrongSwan entirely. The  l2tp-ipsec-vpn-daemon 0.9.0-1 is not a network manager plugin. Basically it adds an applet to your systray that allows you to deal with L2TP/IPSEC connections. It takes the info you enter and puts it in all the configuration files (ipsec.secrets, xl2tpd.options, etc). One of the files it creates is supposed to contain your connection information for each VPN. I discovered when you use the L2TP IPSEC Applet GUI it doesn't add the password in the VPN profile /etc/ppp directory. In fact, every time you add or edit a VPN using the GUI it deletes your password from each VPN configuration file. When  I added it back to each VPN config file ("ConnectionName.xl2tpd" under /etc/ppp) it connected. 

I'm still seeing strange errors in my log file like these.

[COLOR=#000000]Aug 27 11:23:03.821 ipsec__plutorun: adjusting ipsec.d to /etc/ipsec.d[/COLOR]
[COLOR=#000000]Aug 27 11:23:03.828 recvref[30]: Protocol not available[/COLOR]
[COLOR=#000000]Aug 27 11:23:03.828 xl2tpd[13457]: This binary does not support kernel L2TP.
[/COLOR]
[COLOR=#000000]Aug 27 11:43:08.358 xl2tpd[13460]: handle_packet: bad control packet![/COLOR]

[COLOR=#000000]Aug 27 11:50:08.406 xl2tpd[13460]: check_control: Received out of order control packet on tunnel 63223 (got 29, expected 28)

At least it connects and I can use my vpn.[/COLOR]

---

