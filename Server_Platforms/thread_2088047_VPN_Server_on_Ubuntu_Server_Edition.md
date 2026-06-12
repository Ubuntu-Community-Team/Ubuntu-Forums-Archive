---
title: "VPN Server on Ubuntu Server Edition"
date: 2012-11-25
forum: Server Platforms
---

### Post by FCarlo on 2012-11-25
Hi everyone,

I need a method to access a Samba server remotely. I don't want to use FTP. I thought maybe I could use a VPN server to 'become part of the network', but it doesn't work...:( How should I set up the pptpd server and can I run it on the same machine as the Samba server?

I would really appreciate any help,

FCarlo

---

### Post by sandyd on 2012-11-25
> **FCarlo said:**
> Hi everyone,

I need a method to access a Samba server remotely. I don't want to use FTP. I thought maybe I could use a VPN server to 'become part of the network', but it doesn't work...:( How should I set up the pptpd server and can I run it on the same machine as the Samba server?

I would really appreciate any help,

FCarlo
Ive found that openVPN works best in terms of performance, though it is a bit harder to setup

For openvpn, do this
```

#openvpn install
sudo apt-get install openvpn
sudo cp -R  /usr/share/doc/openvpn/easy-rsa/2.0/* /etc/openvpn/easy-rsa
cd /etc/openvpn/easy-rsa
nano vars

```
press Control + V

Fill in your info
```

export KEY_COUNTRY="US" #Country
export KEY_PROVINCE="California" #Province/State
export KEY_CITY="Los Angeles" #City
export KEY_ORG="..." #Organization (can just be your name)
export KEY_EMAIL="..." #Email
export KEY_DEPARTMENT="Web Services" #Department

```

Press control+x to save.

In the next few steps, just press Enter when it asks you for info
```

./source vars
./clean-all
./build-ca
./build-key-server server
./build-dh
cd keys
cp ca.crt ca.key server.crt server.key dh1024.pem /etc/openvpn
cd /etc/openvpn
nano openvpn.conf

```

Fill in the info below (read the comments!)
```

local 198.23.131.130 #ip address
port 1194 #port 
proto udp
dev tun
ca ca-clients.crt
cert server.crt
key server.key
dh dh1024.pem
server 172.17.0.0 255.255.255.0 #ip address pool
ifconfig-pool-persist ipp.txt
keepalive 10 120
comp-lzo
user nobody
group users
persist-key
persist-tun
status openvpn-status.log
verb 3
##The stuff below is ONLY needed if you are browsing the web through openvpn. In that case, you have to enable forwarding with SNAT, and sysctl.conf. You also need to remove the # in front of the lines as well.

#push "redirect-gateway def1"
#push "dhcp-option DNS 8.8.8.8" #dns server1
#push "dhcp-option DNS 8.8.4.4" #dns server2
duplicate-cn #multiple clients, using same certificate

```
press control+x to save

For each client, go to /etc/openvpn/easy-rsa/
run
```

source vars
./build-key *clientname*
```
the keys (with the clientname) will be in the keys folder.

Transfer it (*clientname.crt, clientname.key, ca.crt*

to the client, install openvpn, and place the following file (and the certificate/keys) into either /etc/openvpn, or %PROGRAMFILES%/OpenVPN/config
```

client
remote 198.23.131.130 1194 #server ip and port
dev tun
proto udp
resolv-retry infinite
nobind
persist-key
persist-tun
ca ca.crt
cert sandyd.crt #clientname.crt
key sandyd.key #clientname.key
comp-lzo
verb 5

```

---

### Post by FCarlo on 2012-11-25
Thank you very much! But will this also work on iOS?

---

### Post by sandyd on 2012-11-25
i don't have an iphone/ipod/ipad/, so I haven't tested this (I do have a mbp though).

but there is an app for it [http://www.guizmovpn.com/](http://www.guizmovpn.com/)

---

### Post by FCarlo on 2012-11-25
Thank you, but is there any way to do it without jail breaking my device?
Thank you so much!!! :)

---

### Post by SeijiSensei on 2012-11-26
Looks like there are [Android solutions](https://www.google.com/search?q=openvpn+client+no+root) for an OpenVPN client that does not require root privileges, but the proprietary nature of iOS probably makes that impossible on Apple devices.

---

### Post by spynappels on 2012-11-26
I think SeijiSensei is correct, but it might be worth taking a look at Tunnelblick for Mac OSX (an OpenVPN client which works very well) and seeing if the developers have anything for iOS.

---

