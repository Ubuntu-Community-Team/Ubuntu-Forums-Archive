---
title: "NO DNS after connecting to OpenVPN ubuntu 16.10"
date: 2017-02-15
forum: Server Platforms
---

### Post by amrasurion on 2017-02-15
SOLUTION:
> **SeijiSensei said:**
> Try editing /etc/resolvconf/resolv.conf.d/head and adding the line
```

nameserver 8.8.8.8

```
to the bottom of that file.  Then restart resolvconf or reboot.  Any better?  If so, and you prefer to use OpenDNS, replace 8.8.8.8 with the appropriate OpenDNS server address.




OriginalPost : 

Added cert and key file to network manager and was able to connect but no pages would load and wasnt able to ping.  I can connect via windows 10 no problem.

Had to physically disconnect vpn from network manager. The only way i was able to connect, get IP to change and pages to load was select the .ovpn file

sudo openvpn ~/ovpnfiles/client1.ovpn

this also stopped working after checking ipleak and a couple other pages. and the only way for me to access the internet again was to
 sudo ifconfig tun0 
down and now I'm here to see what my options are. I'll be checking here frequently to see what some of your ideas may be.

now when run the .ovpn i cannot load anything and i dont understand why it would work before but not now.


edit : i edited the VPN connection and changed DNS to opendns servers. Now im currently connected as i type this ipleak.net shows the dns is correct but ip remains the same.


edit :i removed the VPNs certs from edit connections and added them back in. The following reconnect was successfull and IP change but by the next page load it had stalled

---

### Post by amrasurion on 2017-02-16
Quick bump.

---

### Post by wildmanne39 on 2017-02-17
*Thread moved to **Server Platforms**.*

---

### Post by amrasurion on 2017-02-20
bump

---

### Post by darkod on 2017-02-20
Try using a .conf file in /etc/openvpn instead of NetworkManager. I always prefer that... If you need the connection to be established on boot, a .conf file should do it.

If you want it manually, put another extension except .conf and use the openvpn command to open the tunnel.

---

### Post by amrasurion on 2017-02-20
My apologies, linux noob here, i havent booted windows in a few days as im trying to learn more. 

by .conf im assuming that you mean the .ovpn configure file if not then im not sure which file your referring to or how to write it.

i moved host.ovpn to /etc/openvpn
then sudo /etc/openvpn/host.ovpn

the connection is established, i see tun0 but all pages time out.
i have to ifconfig tun0 down to come back and post. Same issue as network network manager just through terminal

My configuration is as follows :

host.ovpn
clien
dev tun
proto udp
remote serverip 1194
resolv-retry infinite
no bing
user nobody
group nogroup
persist-key
persist-tun
remote-cert-tls server
cipher AES-128-CBC
auth SHA256
comp-lzo
verb 3
key-direction 1

# script-security 2
# up /etc/openvpn/update-resolv-conf
# down /etc/openvpn/update-resolv-conf

---

### Post by darkod on 2017-02-20
ovpn is the windows extension. For linux use client.conf or basically you can call it whatever you want. If it ends in .conf it will start the connection automatically on boot and on openvpn service restart, otherwise you have to start it manually.

Do you want the vpn tunnel to be on 24x7? If yes, I would suggest to start like this:
1. Create new blank file /etc/openvpn/client.conf and type the settings you need from the ovpn file (by hand). I'm saying this because you might have issues with how the text file is handled in windows and linux. They don't handle it in the same way so try avoiding to create/modify text files for linux on windows. Creating a new text file in linux from scratch will make sure you avoid this issue...
2. Restart the openvpn service:
```
sudo systemctl restart openvpn.service
```
3. Check if tun interface was created:
```
ifconfig
```
4. Check your routing after the vpn is on and your public IP (is it meant to go through the vpn?):
```
route -n
curl icanhazip.com
```

---

### Post by amrasurion on 2017-02-20
by renaming host.ovpn - host.conf 
and
```
bobafett@deathstar:~$ curl icanhazip.com
curl: (6) Could not resolve host: icanhazip.com
```

wanted to post this so you could have a look. I'll be retyping the .conf file myself later. and thank you for the timely responses.

i also did 
scp /var/log/syslog [email]me@server:~/syslog.copy[/email]

---

### Post by darkod on 2017-02-20
From the last message it looks like you have no dns, which might be why you are not loading any pages... It doesn't necessarily mean you are not on the internet.

Try this while the vpn is ON:
```
ping -c 4 8.8.8.8
sudo apt-get install traceroute
traceroute 8.8.8.8
```

Try this with both vpn ON and OFF (separate results):
```
cat /etc/resolv.conf
dig google.com
```

PS. What might be hapenning is the dns servers that need to be used when the vpn is on do not get configured somehow. It could be an issue on the server side but you say windows client works correctly, right? So far it looks like your linux client is not configured with dns correctly after you connect the vpn.

---

### Post by amrasurion on 2017-02-20
vpn connected 
```
ping -c 4 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=60 time=272 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=60 time=273 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=60 time=272 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=60 time=335 ms
```


traceroute times out


```
bobafett@deathstar:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
```


```
bobafett@deathstar:~$ dig google.com

; <<>> DiG 9.10.3-P4-Ubuntu <<>> google.com
;; global options: +cmd
;; connection timed out; no servers could be reached
```


so that narrows it down. The server is already configured to OpenDNS.

the original post of client1.ovpn was the first server.
 host.conf directs to a different server but this is the exact same issue i ran into with the last one. Windows worked fine but ubuntu did not.

---

### Post by darkod on 2017-02-20
So, you have route to the internet but no dns. In resolv.conf you have only the localhost which can't help you because there is no dns server on the localhost.

I don't know if the server is configured for OpenDNS but according to resolv.conf and dig there is no working dns (after the vpn is connected). Again, this might also be result of what the openvpn server is telling the client to do after it connects, but I am confused why would it work for windows clients and not for linux.

Do you have control of the server side?

---

### Post by SeijiSensei on 2017-02-20
Try editing /etc/resolvconf/resolv.conf.d/head and adding the line
```

nameserver 8.8.8.8

```
to the bottom of that file.  Then restart resolvconf or reboot.  Any better?  If so, and you prefer to use OpenDNS, replace 8.8.8.8 with the appropriate OpenDNS server address.

---

### Post by amrasurion on 2017-02-20
bobafett@deathstar:~$ nmcli device show tun0 | grep IP4.DNS
bobafett@deathstar:~$ nmcli device show wlo1 | grep IP4.DNS
IP4.DNS[1]:                             208.67.222.222
IP4.DNS[2]:                             208.67.220.220

---

### Post by amrasurion on 2017-02-20
Excellent. 

Issue has been resolved. I have learned a lot and am very grateful for your help. this is a great welcoming to the ubuntu community.


> **SeijiSensei said:**
> Try editing /etc/resolvconf/resolv.conf.d/head and adding the line
```

nameserver 8.8.8.8

```
to the bottom of that file.  Then restart resolvconf or reboot.  Any better?  If so, and you prefer to use OpenDNS, replace 8.8.8.8 with the appropriate OpenDNS server address.

I would like to personally thank both of you. Darkod for helping me troubleshoot and SeijiSensei for the solution

---

