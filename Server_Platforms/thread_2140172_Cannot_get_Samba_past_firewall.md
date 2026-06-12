---
title: "Cannot get Samba past firewall"
date: 2013-04-28
forum: Server Platforms
---

### Post by ramicio on 2013-04-28
I have two NICS, two separate networks.  Eth0 (192.168.1.x) can do all traffic, so I don't need any firewall for that.  Eth1 (192.168.0.x) may only do Samba traffic.  Eth0 is on my own business internet connection, and the one on eth1 is not mine, so I absolutely cannot have any traffic other than Samba going through there.  I just cannot get anything on the eth1 side of the network to work when a firewall is on (iptables).  I don't have a computer on the other network (eth1), and never will be able to, so all I have to go by is smbtree.  I will either get "NT_STATUS_BAD_NETWORK_NAME" or "NT_STATUS_UNSUCCESSFUL" on those machines on the other network.  Below are the rules I am trying.

```
-A INPUT -d 192.168.0.0/24 -p icmp --icmp-type 8 -j ACCEPT
-A INPUT -d 192.168.0.0/24 -p icmp --icmp-type 0 -j ACCEPT
-A INPUT -d 192.168.0.0/24 -p udp -m multiport --dports 137,138 -j ACCEPT
-A INPUT -d 192.168.0.0/24 -p tcp -m multiport --dports 139,445 -j ACCEPT
-A INPUT -d 192.168.0.0/24 -j REJECT
-A OUTPUT -s 192.168.0.0/24 -p icmp --icmp-type 0 -j ACCEPT
-A OUTPUT -s 192.168.0.0/24 -p icmp --icmp-type 8 -j ACCEPT
-A OUTPUT -s 192.168.0.0/24 -p udp -m multiport --dports 137,138 -j ACCEPT
-A OUTPUT -s 192.168.0.0/24 -p tcp -m multiport --dports 139,445 -j ACCEPT
-A OUTPUT -s 192.168.0.0/24 -j REJECT
```

Please help me.  I am at my wit's end with this crap and am ready to throw this thing out of the window.

---

### Post by ramicio on 2013-04-29
I had to add "-i lo" to the inputs for some reason.

---

### Post by ramicio on 2013-04-29
I spoke too soon.  It merely resolves the issue of seeing other computers in smbtree.  It does not work.  Other machines do not see it.  Please help.

---

### Post by ramicio on 2013-05-03
Seriously, no one can/will help me?

---

### Post by matt_symes on 2013-05-03
Thread moved to **server platforms**.

You may get better support in this sub forum.

---

### Post by ramicio on 2013-05-03
Thank you :-D

---

### Post by matt_symes on 2013-05-03
Hi

According to this...

[http://www.cyberciti.biz/faq/what-ports-need-to-be-open-for-samba-to-communicate-with-other-windowslinux-systems/](http://www.cyberciti.biz/faq/what-ports-need-to-be-open-for-samba-to-communicate-with-other-windowslinux-systems/)

You need TCP as well as UDP ports open. From that sites as well...

```

matthew-S206:/home/matthew/server_firewall_rules % grep -i NETBIOS /etc/services
netbios-ns      137/tcp                         # NETBIOS Name Service
netbios-ns      137/udp
netbios-dgm     138/tcp                         # NETBIOS Datagram Service
netbios-dgm     138/udp
netbios-ssn     139/tcp                         # NETBIOS session service
netbios-ssn     139/udp
matthew-S206:/home/matthew/server_firewall_rules % 

```

Kind regards

---

### Post by ramicio on 2013-05-03
I toyed with that.  I tried doing both TCP and UDP for 137-139 and 445.

---

### Post by matt_symes on 2013-05-03
Hi

Both your input and output rules are using dports only. Are you sure this is correct ?

I have to be honest and say that i have never set up the specific rules you are trying to set up so i'm just throwing ideas into the pot.

Some on in this subforum will have done so i expect though so be patient.

Kind regards

---

### Post by prodigy_ on 2013-05-03
Well, I'm not an adept at iptables but your rules look wrong since you allow only 137, 138, 139 and 445 as **destination** ports on both chains. IIRC this means you break Samba connections both ways dropping any reply packets from Samba servers on either side.

Also it's not a good idea to expose Samba to untrusted network. You should set up an FTP or SFTP server instead.

---

### Post by ramicio on 2013-05-03
I will try just --ports and do 137,138,139,445 in both TCP and UDP.  Unfortunately I am not home to test this right now.  I will have to wait until this evening.

---

### Post by darkod on 2013-05-03
Are the rules you posted the only rules in the firewall? I assume not. You need to have a INPUT accept rule for all established and related traffic, so that the communication can go on.

But I agree with not being a good idea using samba for this. You really need to look into sftp or similar.

As you said, try allowing 137,138,139,445 both tcp and udp in the INPUT chain.
The OUTPUT rules you don't need since the reply is not sent to the same ports. The client will open the connection from a random high port, not from 139 also. Besides, are you controlling OUTPUT traffic too? Don't you have ACCEPT for all OUTPUT traffic? I don't see much sense blocking traffic originating from your machines. If the OUTPUT policy is DROP you will need something accepting the established and related traffic, but not the --dports 137,138,139,445 since the reply from the server is not sent to those ports.

Also, are you sure this is a firewall issue? Could it be samba config issue? Can you disable all firewall temporarily and see if samba works like that?

PS. Also in your INPUT rules you are using -d 192.168.0.0/24 which makes no sense really. The firewall is about the server machine, not the whole subnet. Further more, you can easily limit it to the incoming traffic on eth1 because that's what you want (samba only on eth1):
```
-A INPUT -i lo -j ACCEPT
-A INPUT -i eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i eth1 -p tcp -m multiport --dports 137:139,445 -j ACCEPT
-A INPUT -i eth1 -p udp -m multiport --dports 137:139,445 -j ACCEPT
```

Something like that for example. Please note that I assume ACCEPT policy for the OUTPUT chain, otherwise you need rules for OUTPUT too.

---

### Post by ramicio on 2013-05-03
Samba indeed works flawlessly without the firewall on.  I've just removed all firewall rules in the time being.  There are other things in the firewall, but I don't believe they are rules.

```
# Generated by iptables-save v1.4.12 on Fri Apr 26 19:59:22 2013
*filter
:INPUT ACCEPT [140825:40502804]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [77581:228255896]
:fail2ban-apache-multiport - [0:0]
:fail2ban-ssh - [0:0]
-A INPUT -i lo -s 192.168.0.0/24 -p icmp --icmp-type 8 -j ACCEPT
-A INPUT -i lo -s 192.168.0.0/24 -p icmp --icmp-type 0 -j ACCEPT
-A INPUT -i lo -s 192.168.0.0/24 -p tcp -m multiport --ports 137,138,139,445 -j ACCEPT
-A INPUT -i lo -s 192.168.0.0/24 -p udp -m multiport --ports 137,138,139,445 -j ACCEPT
-A INPUT -i lo -s 192.168.0.0/24 -j REJECT
-A OUTPUT -d 192.168.0.0/24 -p icmp --icmp-type 8 -j ACCEPT
-A OUTPUT -d 192.168.0.0/24 -p icmp --icmp-type 0 -j ACCEPT
-A OUTPUT -d 192.168.0.0/24 -p tcp -m multiport --ports 137,138,139,445 -j ACCEPT
-A OUTPUT -d 192.168.0.0/24 -p udp -m multiport --ports 137,138,139,445 -j ACCEPT
-A OUTPUT -d 192.168.0.0/24 -j REJECT
COMMIT
# Completed on Fri Apr 26 19:59:22 2013
```

That's what I have in there already.  I work with a text file and iptables-restore because it's easier to do in a text editor than in the shell with individual commands.

Here is what I will change the input to:

```
-A INPUT -i lo -j ACCEPT
-A INPUT -i eth1 -p icmp --icmp-type 8 -j ACCEPT
-A INPUT -i eth1 -p icmp --icmp-type 0 -j ACCEPT
-A INPUT -i eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i eth1 -p tcp -m multiport --ports 137:139,445 -j ACCEPT
-A INPUT -i eth1 -p udp -m multiport --ports 137:139,445 -j ACCEPT
-A INPUT -i eth1 -j REJECT
```

Is that more sane? It still doesn't work in smbtree.  I have nothing in the output chain and I get NT_STATUS errors from smbree for the computers on eth1's LAN.  In the event I lose my internet connection (on eth0), I still don't want it outbounding traffic to eth1's internet connection.  Will attempted outbound traffic fail if eth0's connection is down, or will retry but on eth1?  Will it only try another connection if the actual ethernet link of eth0 fails?

---

### Post by ramicio on 2013-05-03
The computer on there wasn't turned on but it was still appearing.

---

### Post by darkod on 2013-05-03
Is samba listening to all IPs? Make sure it's not listening only on eth0 or lo since if you don't have forwarding enabled, no packets are forwarded between eth1 and other interfaces.

The forwarding option is in /etc/sysctl.conf, something like:
net.ipv4.ip_forward=1

You need to uncomment it (it's commented by default).

Since you are limiting samba to eth1 only, it's best to make sure it listens to that interface first. You can also make it listen only on that interface, in which case you don't need the forwarding enabled I guess.

PS. Also, what kind of test are you doing? Try opening the server by IP and see if you can open the share. Don't test only by looking in network whether you see the server. Whether the server shows there or not it depends on other things, not only samba and the firewall. You might be looking at the problem in a wrong way.
To test connectivity with samba and the shares, do it always by IP. Once that is working with the firewall in place, you can work on why it doesn't show in Network.

Most often the reason it doesn't show in Network is not having the same workgroup with the client machine, and not having the same dns server. The dns server needs to be the same.

---

### Post by ramicio on 2013-05-03
Do I need to restart any service after uncommenting that line?

I am not attempting to limit samba to eth1 only, I need it on both eth0 and eth1.  There is nothing in my samba config that is limiting the interfaces it's listening on.

The only way I have of testing it is by using an app on my iPhone to look at samba shares.  I will test it later by IP.

The server shows up on both networks when I have the firewall disabled.

---

### Post by darkod on 2013-05-03
You need to restart only networking as far as I know.
sudo service networking restart

---

### Post by ramicio on 2013-05-03
Thank you.  That's all to do for now I suppose.  I will get back to this thread when I get home from work and test it out.

---

### Post by ramicio on 2013-05-03
It appears to be working.  I have just one problem.  I have the address set to be static (192.168.0.2) but it's showing in ifconfig as a machine in the DHCP range for that router, 192.168.0.104.  On the router it shows up as 192.168.0.2.  Apache will respond to both addresses and the samba browser on my phone will show each address as a machine, though it will only connect to 192.168.0.2.  I tried taking down the connection and bringing it back up, but no luck.

---

### Post by darkod on 2013-05-03
Are you sure your /etc/network/interfaces file is correct? If it's set to 192.168.0.2 static then it should be static. Also, I believe static IP outside the dhcp range do not show on the router. How can it show up on the router as 192.168.0.2?

---

### Post by ramicio on 2013-05-03
The router just lists clients connected to it, not specifically DHCP clients.

```
auto eth1
iface eth1 inet static
address 192.168.0.2
```

I had netmask and gateway in there before.  I don't think they're needed, are they?

---

### Post by darkod on 2013-05-04
Of course they are. You also have to specify dns nameservers. When it's static, you put everything by hand, not only the IP. I guess because there is info missing, the router also assigns another dynamic IP so you get into this situation.

```
auto eth1
iface eth1 inet static
   address 192.168.0.2
   netmask 255.255.255.0 (if that's the one you are using)
   gateway 192.168.0.1 (if that's the correct one)
   dns-nameservers x.x.x.x y.y.y.y
```

Now, if this machine goes out to the internet/the main network through eth0, in that case you can use eth1 only with address and netmask options. The gateway is not needed but in that case the only gateway and route will be the gateway on the eth0 interface. If you want a gateway and route used on eth1 you have to specify the option. Also the dns-nameservers are not needed if you already have some set on eth0 and want to use only those.

---

### Post by SeijiSensei on 2013-05-04
I don't see the required rule for reply traffic in that snippet.  Is is somewhere else in the ruleset? 

```
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
```

This tells the firewall to track all requests and automatically accept any packets sent in response.  This is pretty much a mandatory rule in any firewall chain.  It should be near the top of the ruleset along with the rule for interface lo.

---

### Post by ramicio on 2013-05-04
> **darkod said:**
> Of course they are. You also have to specify dns nameservers. When it's static, you put everything by hand, not only the IP. I guess because there is info missing, the router also assigns another dynamic IP so you get into this situation.

```
auto eth1
iface eth1 inet static
   address 192.168.0.2
   netmask 255.255.255.0 (if that's the one you are using)
   gateway 192.168.0.1 (if that's the correct one)
   dns-nameservers x.x.x.x y.y.y.y
```

Now, if this machine goes out to the internet/the main network through eth0, in that case you can use eth1 only with address and netmask options. The gateway is not needed but in that case the only gateway and route will be the gateway on the eth0 interface. If you want a gateway and route used on eth1 you have to specify the option. Also the dns-nameservers are not needed if you already have some set on eth0 and want to use only those.

Very good.

> **SeijiSensei said:**
> I don't see the required rule for reply traffic in that snippet.  Is is somewhere else in the ruleset? 

```
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
```

This tells the firewall to track all requests and automatically accept any packets sent in response.  This is pretty much a mandatory rule in any firewall chain.  It should be near the top of the ruleset along with the rule for interface lo.

That is indeed in my rules.

I think it's all set.  I restarted the machine and it started up with the proper address for eth1 and the firewall rules loaded.  All is working.  Thanks much everyone!

---

