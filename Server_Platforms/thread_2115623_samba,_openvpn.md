---
title: "samba, openvpn"
date: 2013-02-13
forum: Server Platforms
---

### Post by Peter1981 on 2013-02-13
Hi,

I'm a very new ubuntu user and I need your help.
I have ubuntu 12.04 LTS with samba file server and openvpn program. It's a home server.
I use securepoint OpenVPN v1 program to connect to my server.
I use tun0 device.
I can connect to my server but I don't know how to browse the samba server.
Do I have to use my web browser or any special program?
This is my smb.conf file:
 [FONT=&quot] [global][/FONT]
  [FONT=&quot]    workgroup = WORKGROUP[/FONT]
  [FONT=&quot]   netbios name = FTP server[/FONT]
  [FONT=&quot]   lm announce = no[/FONT]
  [FONT=&quot]   preferred master = yes[/FONT]
  [FONT=&quot]   enhanced browsing = yes[/FONT]
  [FONT=&quot]      server string = %h FTP server (Samba, Ubuntu)[/FONT]
  [FONT=&quot]    wins support = yes[/FONT]
  [FONT=&quot]    dns proxy = no[/FONT]
  [FONT=&quot]    interfaces = 127.0.0.1/8 192.168.0.0/24 10.8.0.0/24[/FONT]
  [FONT=&quot]   hosts allow = 10.8.0. 192.168.0. 127.0.0.[/FONT]
  [FONT=&quot]   hosts deny = 0.0.0.0/0[/FONT]
  [FONT=&quot]   interfaces = tun0 eth0[/FONT]
  [FONT=&quot]    bind interfaces only = yes[/FONT]
  [FONT=&quot]    log file = /var/log/samba/log.%m[/FONT]
  [FONT=&quot]    max log size = 1000[/FONT]
  [FONT=&quot]   syslog = 0[/FONT]
  [FONT=&quot]    panic action = /usr/share/samba/panic-action %d[/FONT]
  [FONT=&quot] 
[/FONT]
    [FONT=&quot]   security = user[/FONT]
  [FONT=&quot]    encrypt passwords = true[/FONT]
  [FONT=&quot]   passdb backend = tdbsam[/FONT]
  [FONT=&quot]    obey pam restrictions = yes[/FONT]
  [FONT=&quot]   unix password sync = yes[/FONT]
  [FONT=&quot]    pam password change = yes[/FONT]
  [FONT=&quot]   map to guest = bad user[/FONT]
  [FONT=&quot]    domain logons = yes[/FONT]
  [FONT=&quot]   logon drive = H:[/FONT]
  [FONT=&quot]   logon home = \\%N\%U[/FONT]
  [FONT=&quot]   create mask = 0700[/FONT]
  [FONT=&quot]  
[/FONT]
[FONT=&quot][profiles][/FONT]
  [FONT=&quot]   comment = Users profiles[/FONT]
  [FONT=&quot]   path = %H[/FONT]
  [FONT=&quot]   guest ok = no[/FONT]
  [FONT=&quot]   browseable = no[/FONT]
  [FONT=&quot]   create mask = 0600[/FONT]
  [FONT=&quot]   directory mask = 0700[/FONT]
  [FONT=&quot]   read only = no[/FONT]
  [FONT=&quot]   hide unreadable = yes[/FONT]
  [FONT=&quot]   hide dot files = yes[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot][printers][/FONT]
  [FONT=&quot]   comment = All Printers[/FONT]
  [FONT=&quot]   browseable = no[/FONT]
  [FONT=&quot]   path = /var/spool/samba[/FONT]
  [FONT=&quot]   printable = yes[/FONT]
  [FONT=&quot]   guest ok = no[/FONT]
  [FONT=&quot]   read only = yes[/FONT]
  [FONT=&quot]   create mask = 0700[/FONT]
  [FONT=&quot] [/FONT]
[FONT=&quot][/FONT][FONT=&quot][kozos] [/FONT]  
[FONT=&quot]   comment = Samba server[/FONT]
  [FONT=&quot]   path = /home/io[/FONT]
  [FONT=&quot]   read only = no[/FONT]
  [FONT=&quot]   browsable = yes[/FONT]
  [FONT=&quot]   guest ok = no[/FONT]
  [FONT=&quot]   writable = yes[/FONT]
  [FONT=&quot]   read only = no[/FONT]

[FONT=&quot][/FONT]
[FONT=&quot]And this is my server.conf file:[/FONT]


  [FONT=&quot]port 1194[/FONT]
  [FONT=&quot]proto udp[/FONT]
  [FONT=&quot]dev tun[/FONT]
  [FONT=&quot]ca ca.crt[/FONT]
  [FONT=&quot]cert server.crt[/FONT]
  [FONT=&quot]key server.key  # This file should be kept secret[/FONT]
  [FONT=&quot]dh dh1024.pem[/FONT]
  [FONT=&quot]server 10.8.0.0 255.255.255.0[/FONT]
  [FONT=&quot]ifconfig-pool-persist ipp.txt[/FONT]
  [FONT=&quot]keepalive 10 120[/FONT]
  [FONT=&quot]max-clients 10[/FONT]
  [FONT=&quot]persist-key[/FONT]
  [FONT=&quot]persist-tun[/FONT]
  [FONT=&quot]verb 3[/FONT]
  [FONT=&quot]mute 20[/FONT]
  
[FONT=&quot][/FONT]
[FONT=&quot]Are these conf file right or I have to change something?[/FONT]
[FONT=&quot]Let me know what to change if I need.[/FONT]

[FONT=&quot][/FONT]
[FONT=&quot]Thank you[/FONT]

[FONT=&quot][/FONT]
[FONT=&quot]Peter
[/FONT]
  
  [FONT=&quot] [/FONT]

---

### Post by Peter1981 on 2013-02-14
I changed something in the server.conf file.
push "route 192.168.0.8 255.255.255.0"
If I apply this command I always get a message
[B]The route addition failed: The parameter is incorrect.
[/B]What is wrong? I still can connect to the openvpn server but still can not browse the samba.
I have the following devices
eth0 inet addr 192.168.0.8 bcast 192.168.0.255 mask 255.255.255.0
tun0 inet addr 10.8.0.1 P-t-P 10.8.0.2 mask 255.255.255.255
I get the eth0 IP address by dhcp from my router and the samba and openvpn server are on the same PC.

Thanks

Peter

---

### Post by volkswagner on 2013-02-14
I'm not sure if this applies, but when setting up OpenVPN on my router I followed [this how to]("http://wiki.openwrt.org/doc/howto/vpn.openvpn").  I am able to browse SAMBA shares.  Check out the two edits for "Join your clients to a windows domain".

---

### Post by Peter1981 on 2013-02-14
1

---

