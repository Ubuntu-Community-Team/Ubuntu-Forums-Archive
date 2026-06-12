---
title: "Open Vpn Server Problem"
date: 2017-12-09
forum: Server Platforms
---

### Post by secoonder on 2017-12-09
i am Using Ubuntu 14.04  . i installed OPen Vpn Server three year ago. it works properly.
Yesterday,Some vpn users connection started  lost.After three minutes ,their connections  was successfuly.This happened for 20 minutes.And then the problem is solved.i could not understand the problem.
My VPN Server log is 
```
"New Connection by client "myclient" will cause previous active,sessions by this client to be dropped.[COLOR=#000000]Remember to use the--duplicate-cn option if you want multiple clients using the same certificate or username to concurrently connect."[/COLOR]
```
[COLOR=#000000]

duplicate-cn is disable in my openvpn.conf for security.

i generated different certificates for all users.

What is the problem ?What can i do ?

Thank you very much for your help


[/COLOR]

---

### Post by secoonder on 2017-12-10
Can you help Me ?

---

### Post by wildmanne39 on 2017-12-10
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

### Post by darkod on 2017-12-10
Do you still have the problem? You say it was solved after 20mins.

If it works OK now I wouldn't worry about it. Looks like problems with the client connection and the client is trying to connect again while the server still hasn't deleted the old connection. So it looks like new client trying to connect with the same certificate and it reports that message in the log.

Do you use the 'persist-key' and 'keepalive' parameters in the client conf file?

---

### Post by secoonder on 2017-12-19
Thank you Darkod.
i dont use Persist-Key and Persist-tun parameters in the all client conf file. 

When these problems occur; Some  clients were properly connected my vpn server.But some clients disconnected it, but these clients have a internet at the same time. :) ?
My server.conf is
```
root@xxxx:/etc/openvpn# uname -a
Linux xxxx 3.13.0-79-generic #123-Ubuntu SMP Fri Feb 19 14:27:58 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```
ifconfig tun0
```

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:10.a.b.c  P-t-P:10.a.b.d  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1400  Metric:1
          RX packets:206295348 errors:0 dropped:0 overruns:0 frame:0
          TX packets:155141003 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:211743522723 (211.7 GB)  TX bytes:55917175516 (55.9 GB)
```
server.conf is 
```
port 1194
tun-mtu 1400
tls-server
proto tcp
dev tun
ca  /etc/openvpn/easy-rsa/keys/ca.crt
cert /etc/openvpn/easy-rsa/keys/firewall.crt
key /etc/openvpn/easy-rsa/keys/firewall.key
dh /etc/openvpn/easy-rsa/keys/dh2048.pem
server 10.2.1.0 255.255.255.0
ifconfig-pool-persist ipp.txt 600
push "route 192.168.x.0 255.255.255.0"
client-config-dir /etc/openvpn/ccd
push "dhcp-option DNS m.n.o.p"
push "dhcp-option DNS d.e.f.g"
client-to-client
keepalive 20 60
comp-lzo
max-clients 100
user nobody
group nogroup
persist-key
persist-tun
status /var/log/openvpn-status.log
log-append  /var/log/openvpn.log
verb 3
```


server.log
```
Tue Dec 19 00:42:46 2017 85.z.x.y:53736 [client1] Peer Connection Initiated with [AF_INET]85.98.x.y:53736
Tue Dec 19 00:42:46 2017 MULTI: new connection by client 'client1' will cause previous active sessions by this client to be dropped.  Remember to use the --duplicate-cn option if you want multiple clients using the same certificate or username to concurrently connect.

```
Client1 Pc is Win 7 pro 64 bit.
Client 1 ovpn file is
**client1**
```
tls-client
client
dev tun
proto tcp
tun-mtu 1400
remote a.b.c.d 1194
resolv-retry infinite
pkcs12 example.p12
askpass con.txt
resolv-retry infinite
ns-cert-type server
comp-lzo
verb 3
status /var/log/openvpn-status.log
route-method exe
route-delay 2
```


And then i noticed something.
My ipp .txt is
```
client4,10.2.1.4
client5,10.2.1.8
client6,10.2.1.12
client7,10.2.1.16
client8,10.2.1.20

```
i deleted client8 in ipp.txt.  
My ipp .txt is
```
client4,10.2.1.4
client5,10.2.1.8
client6,10.2.1.12
client7,10.2.1.16

```






and i restarted "/etc/init.d/openvpn restart".
The client8 is not removed.i can see again.
My ipp .txt is
```
client4,10.2.1.4
client5,10.2.1.8
client6,10.2.1.12
client7,10.2.1.16
client8,10.2.1.20

```


But " my server.conf is "client-config-dir /etc/openvpn/ccd"
and ccd folder is
```
more client4 
ifconfig-push 10.2.1.93 10.2.1.94

```
```
more client5 
ifconfig-push 10.2.1.97 10.2.1.98



```
```
more client6 
client6: No such file or directory



```
```
more client7 
ifconfig-push 10.2.1.101 10.2.1.102

```
```
more client8
client8: No such file or directory

```


"Note:Client6 and client 8 left a work.Thus i deleted its file,but i can not deleted in ipp.txt"


Could it be an interesting thing with that? 

Am i changing keep alive 20 60 value in my server.conf ?

if they are not enough ,am &#305; make verb 4 in server.conf ?

What can i do ?

---

### Post by darkod on 2017-12-19
I wouldn't worry about the ipp.txt file. I have seen something similar, that openvpn can add a client again if you delete it manually. I only don't remember what was the exact situation. Or maybe the openvpn service had to be stopped first, then the line deleted from ipp.txt and then the service started.

Did you try adding the 'persist-key' and 'keepalive' parameters in the client.conf to see if it helps solve those errors? I suggest to do that first.

---

### Post by secoonder on 2018-01-10
darkod
thank you very much for your help
i added persist key and keep alive. bu the problem is not solved.my output log is
> Wed Jan 10 09:23:48 2018 us=635372 xzbd/1.2.3.4MULTI: packet dropped due to output saturation (multi_process_incoming_tun)
Wed Jan 10 09:23:48 2018 us=635410 xzbd/1.2.3.4MULTI: packet dropped due to output saturation (multi_process_incoming_tun)
Wed Jan 10 09:23:48 2018 us=635423 xzbd/1.2.3.4 MULTI: packet dropped due to output saturation (multi_process_incoming_tun)
Wed Jan 10 09:23:48 2018 us=635572 xzbd/1.2.3.4 MULTI: packet dropped due to output saturation (multi_process_incoming_tun)
Wed Jan 10 09:23:48 2018 us=635698 xzbd/1.2.3.4 MULTI: packet dropped due to output saturation (multi_process_incoming_tun)
Wed Jan 10 09:23:48 2018 us=635708 xzbd/1.2.3.4 MULTI: packet dropped due to output saturation (multi_process_incoming_tun)
Wed Jan 10 09:23:48 2018 us=635935 xzbd/1.2.3.4 MULTI: packet dropped due to output saturation (multi_process_incoming_tun)
Wed Jan 10 09:23:48 2018 us=635947 xzbd/1.2.3.4 MULTI: packet dropped due to output saturation (multi_process_incoming_tun)
Wed Jan 10 09:23:48 2018 us=636150 xzbd/1.2.3.4 MULTI: packet dropped due to output saturation (multi_process_incoming_tun)
Wed Jan 10 09:23:48 2018 us=636183 xzbd/1.2.3.4 MULTI: packet dropped due to output saturation (multi_process_incoming_tun)
Wed Jan 10 09:23:48 2018 us=636194 xzbd/1.2.3.4 MULTI: packet dropped due to output saturation (multi_process_incoming_tun)
Wed Jan 10 09:23:48 2018 us=636204 xzbd/1.2.3.4 MULTI: packet dropped due to output saturation (multi_process_incoming_tun)
Wed Jan 10 09:23:48 2018 us=636213 xzbd/1.2.3.4MULTI: packet dropped due to output saturation (multi_process_incoming_tun)
Wed Jan 10 09:23:48 2018 us=636221 xzbd/1.2.3.4 MULTI: packet dropped due to output saturation (multi_process_incoming_tun)
Wed Jan 10 09:23:48 2018 us=636230 xzbd/1.2.3.4 MULTI: packet dropped due to output saturation (multi_process_incoming_tun)
Wed Jan 10 09:23:48 2018 us=636239 xzbd/1.2.3.4MULTI: packet dropped due to output saturation (multi_process_incoming_tun)
Wed Jan 10 09:23:48 2018 us=636249 xzbd/1.2.3.4 MULTI: packet dropped due to output saturation (multi_process_incoming_tun)
Wed Jan 10 09:23:48 2018 us=726682 xzbd/1.2.3.4MULTI: packet dropped due to output saturation (multi_process_incoming_tun)
Wed Jan 10 09:23:48 2018 us=845551 xzbd/1.2.3.4 MULTI: packet dropped due to output saturation (multi_process_incoming_tun)




---

### Post by darkod on 2018-01-10
Have you tried using udp instead of tcp? I have always used only udp for openvpn, like it uses by default.

Also, try without setting your own tun-mtu unless that parameter is really needed.

I would strip the server.conf anf client.conf files of any additional parameters. First start with basic necessary parameters and see if that is stable. After that you can start adding more parameters and it would also show you which parameter has issues (when problems start showing up).

---

