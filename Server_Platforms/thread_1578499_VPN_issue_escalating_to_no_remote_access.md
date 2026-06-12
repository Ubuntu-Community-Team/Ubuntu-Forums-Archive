---
title: "VPN issue escalating to no remote access"
date: 2010-09-20
forum: Server Platforms
---

### Post by hamilton.jason on 2010-09-20
Hello,
I am a novice ubuntu user. I used the GUI desktop version before I bought a mac so I have gotten a little rusty. This past weekend i gutted an old Dell Dimension 4400 and put some RAM (512) and a Hard drive (128 gb) into it. I installed ubuntu server 10.04.1 32 bit and got it up and running. No problems there are 5 failed attempts at burning a CD. 

After i got the server up, first thing i did was enable telnet. I created a user that doesnt have all the rights as my initial admin user. Next i set up a Samba Share drive and was able to access that from all my LAN computers. Then i enabled FTP to a designated directory. 

The last step was to set up VPN. This has been a bloody nightmare. I wont go into detail about all the steps i took to try to get it to work, that would be a different thread all together.

The issue i am currently having is that in an effort to trouble shoot my vpn connection, i did a ufw disable to turn off the ubuntu built in firewall. then i did a remote reboot (since i am at work).

The server never came backup. I try to do a telnet to my host name (using dyndns) and it just came up blank. Went home on my lunch break to check the server and it was stuck at the push F1 to continue screen before it boots. It keeps trying to boot from floopy. Changed the BOOT order to check HD first and totally disregard floopy (it doesnt even have the drive). Keeps trying to boot from floppy anyways but ill fix that later. 

So i can Console into it by using keyboard and monitor but i cannot telnet into. I rebooted router and verified that the port forwarding was still enabled. I rebooted server after changed ufw to enable. but i still cannot access the server remotely. Didnt have too much time to troubleshoot. Was wondering if anyone had any similar issues and how to fix it. 

Sorry about the long winded post.

---

### Post by hamilton.jason on 2010-09-20
ok i am back home and in the server.

First thing i did was go to the ufw and look at status. It says block all incoming accept all outgoing.
Made rules to accept the incoming ports. Still no success. 

Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
1723                       ALLOW IN    Anywhere
23                         ALLOW IN    Anywhere
21                         ALLOW IN    Anywhere

# 

Tried to do a ping to 4.2.2.2 and it failed so no route to network. Went and changed the default gateway to my routers eth ip address. Then i was able to ping out. At this point i am able to telnet in from computers in the LAN but not from the internet. I am still unable to ftp into the server. Out of precaution i decided to restart the eth interface...

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.105
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.l68.1.1

# /etc/init.d/networking restart
 * Reconfiguring network interfaces...
192.l68.1.1: Unknown host
Failed to bring up eth0.
   ...done.
# 

eth0      Link encap:Ethernet  HWaddr 00:13:20:59:8a:b3  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:20ff:fe59:8ab3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:925 errors:0 dropped:0 overruns:0 frame:0
          TX packets:268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:98840 (98.8 KB)  TX bytes:24016 (24.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)


# arp
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.1.1              ether   00:14:a5:35:6e:3c   C                     eth0
192.168.1.101            ether   f8:1e:df:dd:fc:da   C                     eth0
# 

Status:	Connection attempt failed with "ECONNREFUSED - Connection refused by server".
Error:	Could not connect to server


Above is the message i get when trying to FTP into the server from LAN. Its the same thing i get when i try to FTP or Telnet from out of network. Looks like UFW is messing with it. Router is configured correctly. Any assistance?

---

### Post by hamilton.jason on 2010-09-20
ill keep updating this post as i troubleshoot so that maybe somebody will be able to see something that i am missing.

Looks like UFW was blocking my telnet attempts. Checked the/var/log/kern.log and found blocking of port 23 (telnet). However there are no indications of it blocking any FTP sessions or the remote sessions. Those are only current home sessions. When i try to telnet remotely, it does not show on this log. 

Sep 20 17:18:12 homeserver kernel: [18808.959571] [UFW BLOCK] IN=eth0 OUT= MAC=00:13:20:59:8a:b3:f8:1e:df:dd:fc:da:08:00 SRC=192.168.1.101 DST=192.168.1.105 LEN=64 TOS=0x10 PREC=0x00 TTL=64 ID=56714 DF PROTO=TCP SPT=49295 DPT=23 WINDOW=65535 RES=0x00 SYN URGP=0

---

### Post by spynappels on 2010-09-21
Can I just ask a couple of questions?

Is there a specific reason you are using Telnet rather than SSH?

What VPN are you using? OpenVPN? In what configuration, routed or bridged?

What are you trying to accomplish? Remote access into your home LAN or using the VPN for "secure" browsing?

---

### Post by hamilton.jason on 2010-09-21
Ok so last night while barely awake i enabled SSH and i am able to log in with that now remotely. So it has to be something local w/ telnet. I was using telnet just for simplicity purposes. Its an empty server at the moment so not too worried about security. 

I will disable telnet features when i get this other stuff figured out.

Current Issue:
FTP still not working
Samba Still not working
VPN still not working (never worked)

UFW has been disabled, not sure about apparmor though. Not very familiar w/ app armor.
This is all after i rebooted server. Apparently it messed something up. 

For VPN is am using simple pptpd. I following the instructions but it isnt working still. 

End goal is to be able to VPN using my phone or mac and watch streaming videos via share drive. Also being able to print remotely would be pretty sweet. In order for this to work i need vpn working and samba working. but FTP is a must for other purposes. 

Any data read outs you need to assist, just let me know. Ill be monitoring thread all day. 

Thank you.

---

### Post by hamilton.jason on 2010-09-21
Success!

I feel kind of stupid. I am new to Ubuntu server so dont laugh to hard. Fix to this issue:

service vsftpd start (fpt service started)
service nmbd start   (samba service started)

I am sure service telnetd start would also start my telnet sessions again. I was under the impression that a reboot would automatically bring those back up. 

Current issue now:
VPN still not working, using pptpd. 
making these services auto start on reboot.

What read-outs would help isolate the issue w/ my pptpd vpn connection?

---

### Post by hamilton.jason on 2010-09-22
Current messages that i am getting (think they are relevant). Any assistance?

Sep 22 07:38:38 homeserver pptpd[7222]: CTRL: Starting call (launching pppd, opening GRE)
Sep 22 07:38:38 homeserver pptpd[7222]: CTRL: pty_fd = 6
Sep 22 07:38:38 homeserver pptpd[7222]: CTRL: tty_fd = 7
Sep 22 07:38:38 homeserver pptpd[7222]: CTRL: I wrote 32 bytes to the client.
Sep 22 07:38:38 homeserver pptpd[7222]: CTRL: Sent packet to client
Sep 22 07:38:38 homeserver pptpd[7223]: CTRL (PPPD Launcher): program binary = /usr/sbin/pppd
Sep 22 07:38:38 homeserver pptpd[7223]: CTRL (PPPD Launcher): local address = 192.168.1.105
Sep 22 07:38:38 homeserver pptpd[7223]: CTRL (PPPD Launcher): remote address = 192.168.1.110
Sep 22 07:38:38 homeserver pptpd[7222]: GRE: Bad checksum from pppd.
Sep 22 07:38:59 homeserver bcrelay[7221]: UDP_BroadCast(sp=138,dp=138) from: eth0 relayed to:
Sep 22 07:39:08 homeserver pptpd[7222]: GRE: read(fd=6,buffer=805a540,len=8196) from PTY failed: status = -1 error = Input/output error, usual$
Sep 22 07:39:08 homeserver pptpd[7222]: CTRL: PTY read or GRE write failed (pty,gre)=(6,7)
Sep 22 07:39:08 homeserver pptpd[7222]: CTRL: Reaping child PPP[7223]
Sep 22 07:39:08 homeserver pptpd[7222]: CTRL: Client 166.188.19.121 control connection finished
Sep 22 07:39:08 homeserver pptpd[7222]: CTRL: Exiting now
Sep 22 07:39:08 homeserver pptpd[7220]: MGR: Reaped child 7222
Sep 22 07:39:09 homeserver bcrelay[7221]: UDP_BroadCast(sp=138,dp=138) from: eth0 relayed to:
Sep 22 07:40:49 homeserver bcrelay[7221]: UDP_BroadCast(sp=137,dp=137) from: eth0 relayed to:
Sep 22 07:41:09 homeserver bcrelay[7221]: UDP_BroadCast(sp=138,dp=138) from: eth0 relayed to:

---

### Post by spynappels on 2010-09-22
Hi Jason,

I'm sorry, I don't know enough about pptp VPNs, I have only worked with OpenVPN systems.

Check your init script to see if the services should be started on boot, you can add them there if not.

---

