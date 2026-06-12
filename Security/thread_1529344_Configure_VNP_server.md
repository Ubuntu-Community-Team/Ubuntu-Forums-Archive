---
title: "Configure VNP server"
date: 2010-07-12
forum: Security
---

### Post by Xi0N on 2010-07-12
I have a dedicated server inside of my company with ubuntu installed on it.
I have been trying to configure a vpn server on it, for connecting remotely in a secure fashion.....

I was wondering if anyone can provide me with a how-to for doing this.

Thanks!

---

### Post by Sanjeevtrip on 2010-07-12
Checkout this
```

http://www.linux.com/learn/docs/ldp/805-VPN-HOWTO

```

---

### Post by Xi0N on 2010-07-12
Thanks!

I also found this:

[https://help.ubuntu.com/9.10/serverguide/C/openvpn.html](https://help.ubuntu.com/9.10/serverguide/C/openvpn.html)

It is more up to date and is ubuntu-made so, i should not have much problems.

One question i have is, if i get to connect to the vpn, my machine would have an ip like 10.1.0.8 or sth similar..... how to make this ip able to see all the ips in the main subnet? 192.168.1.x?

---

### Post by Sanjeevtrip on 2010-07-12
once you get connected, you will be assigned the ip listed the conf file.
if you have internal dns server you can add that entry and access the machines.

---

### Post by spynappels on 2010-07-12
You can edit the server.conf file to push a route to the clients, telling it to use the OpenVPN server as the gateway for LAN IPs. There is one issue that I can see with this, and this is that your LAN uses the 192.168.1.x subnet which is very common. For this setup to work, your LAN subnet needs to be a less common one such as 192.168.68.x.

The problem occurs when you are on a 192.168.1.x remote LAN and you want to access the VPN and some node inside your Office LAN. If a route is pushed saying that all 192.168.1.x traffic is to go through the VPN, you get a conflict with the local 192.168.1.x addresses and you will have all sorts of problems.

---

### Post by Xi0N on 2010-07-12
What i dont see really clear is the thing on the server conf file.

See: My company's local subnet is 192.168.1.x
The DNS Server is 192.168.1.2
The gateway (the router) is in 192.168.1.155

The openvpn server is in 192.168.1.250

The idea would be that the openvpn clients get connected with some ip like

192.168.2.x and then, be able to see the whole net.....

Im "playing" with the configuration file, and i have something like this:



```
server-bridge 192.168.2.2 255.255.255.0 192.168.2.70 192.168.2.79

(...)
push "redirect-gateway"
push "dhcp-option DNS 192.168.1.2"
push "dhcp-option DOMAIN mycompanydomain.lan"
push "route 192.168.1.2 255.255.255.0"
```


I dont know if its correct since im inside the company just now and i suppose i cannot perform a proper test...

Do this options seem ok to you?

---

### Post by spynappels on 2010-07-12
To get that, you will need to use bridged mode rather than routed mode. I tend to use routed mode because of several different reasons, but if you use bridged mode, your LAN DHCP can give IPs to connected clients, and broadcasts will also reach your clients. You can also tell the clients to route all traffic through the VPN, and then if your DHCP tells connecting clients which DNS server to use, you're all set.

---

### Post by Xi0N on 2010-07-12
OK, that was the problem. I am getting chunks of information from different posts, and i think, finally, im mixing up routing mode and bridging mode....

I should see it like when you use virtual networking in virtual machines and you select either nat or bridged networking....
My point is exactly that: Be able to see the connected client as if he were one more machine in the network... and that cna only be achieved using the bridged setup, as i can see....

I think i will start all over again and go step by step... but it's really confusing to set all the ips correctly in the server configuration file.

If you dont mind, i will go on with this thread until im done with it....

Thanks!!!

---

### Post by spynappels on 2010-07-12
No problem, if you have any more questions, ask. I've more experience with routed mode, but you definitely need bridged mode.

---

### Post by Xi0N on 2010-07-12
```
Mon Jul 12 22:28:09 2010 /sbin/route del -net 0.0.0.0 netmask 0.0.0.0
Mon Jul 12 22:28:09 2010 /sbin/route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.2.2
Mon Jul 12 22:28:09 2010 /sbin/route add -net 192.168.1.2 netmask 255.255.255.0 gw 192.168.2.2
route: netmask doesn't match route address
Usage: route [-nNvee] [-FC] [<AF>]           List kernel routing tables
       route [-v] [-FC] {add|del|flush} ...  Modify routing table for AF.

       route {-h|--help} [<AF>]              Detailed usage syntax for specified AF.
       route {-V|--version}                  Display version/author and exit.

        -v, --verbose            be verbose
        -n, --numeric            don't resolve names
        -e, --extend             display other/more information
        -F, --fib                display Forwarding Information Base (default)
        -C, --cache              display routing cache instead of FIB

  <AF>=Use '-A <af>' or '--<af>'; default: inet
  List of possible address families (which support routing):
    inet (DARPA Internet) inet6 (IPv6) ax25 (AMPR AX.25) 
    netrom (AMPR NET/ROM) ipx (Novell IPX) ddp (Appletalk DDP) 
    x25 (CCITT X.25) 
Mon Jul 12 22:28:09 2010 ERROR: Linux route add command failed: external program exited with error status: 4
Mon Jul 12 22:28:09 2010 Initialization Sequence Completed
Mon Jul 12 22:28:19 2010 Authenticate/Decrypt packet error: cipher final failed
Mon Jul 12 22:28:29 2010 Authenticate/Decrypt packet error: cipher final failed
Mon Jul 12 22:28:39 2010 Authenticate/Decrypt packet error: cipher final failed
Mon Jul 12 22:28:49 2010 Authenticate/Decrypt packet error: cipher final failed
Mon Jul 12 22:28:59 2010 Authenticate/Decrypt packet error: cipher final failed


```

I came this far..... i seem to get connected but there's something wrong with the configuration.....:o

---

### Post by Xi0N on 2010-07-13
OK.

I finally seem to be able to connect.... via the command line, i tryed to do so and all the outputs seem ok: Mi network interface in the client also changes and all seems perfect.

The only thing is that i stilll cannot see anyone.
How can i verify that i am successfully connected to the vpn?

Which config files do i need to paste here for you guys to check what i have done?

Thanks!

---

### Post by spynappels on 2010-07-13
Ok, so you can ping the VPN server.
Can you ping any other hosts?
If not, do a quick search for "Enable IP forwarding" on these forums.

All this tinkering is fun, isn't it?

---

### Post by Xi0N on 2010-07-13
Ok, now i seem to be able to reach the internet, im just not 100% sure, though----

The connection seems to be ok, and a ping to [www.google.es](www.google.es) returns data..... but i ping the server, which should be in 10.8.0.1, and i receive no answer: None of the local network addressess seem reachable neither.

This is part of the server.conf file, maybe it helps:

```
ifconfig-pool-persist ipp.txt
server-bridge 10.8.0.1 255.255.255.0 10.8.0.10 10.8.0.20

keepalive 10 120
#push "redirect-gateway"
push "dhcp-option DNS 192.168.1.2"
#push "dhcp-option DOMAIN mydomain.LAN"
#push "route 192.168.0.0 255.255.255.0"

```

Also, this appears in console upon the connection

```
Tue Jul 13 19:27:53 2010 PUSH: Received control message: 'PUSH_REPLY,redirect-gateway,dhcp-option DNS 192.168.1.2,route-gateway 10.8.0.1,ping 10,ping-restart 120,ifconfig 10.8.0.10 255.255.255.0'
Tue Jul 13 19:27:53 2010 OPTIONS IMPORT: timers and/or timeouts modified
Tue Jul 13 19:27:53 2010 OPTIONS IMPORT: --ifconfig/up options modified
Tue Jul 13 19:27:53 2010 OPTIONS IMPORT: route options modified
Tue Jul 13 19:27:53 2010 OPTIONS IMPORT: route-related options modified
Tue Jul 13 19:27:53 2010 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Tue Jul 13 19:27:53 2010 ROUTE default_gateway=192.168.1.1
Tue Jul 13 19:27:53 2010 TUN/TAP device tap0 opened
Tue Jul 13 19:27:53 2010 TUN/TAP TX queue length set to 100
Tue Jul 13 19:27:53 2010 /sbin/ifconfig tap0 10.8.0.10 netmask 255.255.255.0 mtu 1500 broadcast 10.8.0.255
Tue Jul 13 19:27:53 2010 /sbin/route add -net 212.81.223.226 netmask 255.255.255.255 gw 192.168.1.1
Tue Jul 13 19:27:53 2010 /sbin/route del -net 0.0.0.0 netmask 0.0.0.0
Tue Jul 13 19:27:53 2010 /sbin/route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.8.0.1

```

---

### Post by spynappels on 2010-07-13
> **Xi0N said:**
> 
```
ifconfig-pool-persist ipp.txt
server-bridge 10.8.0.1 255.255.255.0 10.8.0.10 10.8.0.20

keepalive 10 120
#push "redirect-gateway"
push "dhcp-option DNS 192.168.1.2"
#push "dhcp-option DOMAIN mydomain.LAN"
#push "route 192.168.0.0 255.255.255.0"

```



the route you are pushing is on a different subnet, you are pushing a route to 192.168.0.0 instead of 192.168.1.0

---

### Post by Xi0N on 2010-07-13
I changed that... no luck still....

I hope correcting the errors little by little will lead to the solution..

Thanks!

Ill inform if i make any progress....

---

### Post by Sanjeevtrip on 2010-07-14
check the route netmask and gw

---

### Post by Xi0N on 2010-07-14
> **Sanjeevtrip said:**
> check the route netmask and gw

What exactly do you mean? how should they look like?

---

### Post by Xi0N on 2010-07-15
I FINALLY MADE IT

I followed this tuto: [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)


The proper way to set aa vpn, as i understood, is having th vpn clients in another subnet, however, this tuto makes you have the clients in a 192.168.1.x subnet, which is a common one....

The problem is, if i change the options in the server config file, to have the vpn clients inside another subnet (10.8.0.x) i cannot make them see the computers in 192.168.1.x....... how to solve this?

---

