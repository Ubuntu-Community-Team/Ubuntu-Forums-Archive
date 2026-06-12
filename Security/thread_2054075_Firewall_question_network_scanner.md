---
title: "Firewall question network scanner"
date: 2012-09-06
forum: Security
---

### Post by BigCityCat on 2012-09-06
I have a printer scanner that runs on the network and is not plugged in via usb. I set up the firewall to allow ports for the printer. It works but the scanner does not. Here is the out put from the terminal. Once with the firewall off and once with the firewall on.

> pauly@pauly-laptop:~$ sudo scanimage -L
device `epson2:net:192.168.1.67' is a Epson PID 0864 flatbed scanner
pauly@pauly-laptop:~$ sudo scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

Just wondering what port saned works on or if anyone has any ideas.

---

### Post by Ms. Daisy on 2012-09-06
I wrestled with mine for a while, found some docs from HP telling me which ports it used. But in the end the documents weren't right. I found out which ports my scanner used by turning the firewall on, opening the ufw logs, trying to scan, then watching to see what ports get blocked.  My scanner used a range of high ports. So I had to experiment until it worked.

---

### Post by BigCityCat on 2012-09-06
That sounds good. I will give it a try. Just trying to decide if I would rather just turn the firewall off when I need to do a scan.

---

### Post by steeldriver on 2012-09-06
or how about...

```
sudo netstat -lntp | grep saned
```fwiw mine says 6566

Anyhow there should be a predefined application profile for saned, i.e.

```
sudo ufw allow saned
```should open the relevant port(s) - in fact I just tried it and indeed it opens 6566/tcp

Hope this helps

---

### Post by BigCityCat on 2012-09-06
I wonder if anyone can make sense out of this UFW log when I tried to scan.


> Sep  6 22:40:36 pauly-laptop kernel: [14282.890430] [UFW BLOCK] IN= OUT=wlan0 SRC=192.168.1.65 DST=192.168.1.255 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=8610 DPT=8612 LEN=24 
Sep  6 22:40:36 pauly-laptop kernel: [14282.990489] [UFW BLOCK] IN= OUT=wlan0 SRC=192.168.1.65 DST=192.168.1.255 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=8611 DPT=8612 LEN=24 
Sep  6 22:40:36 pauly-laptop kernel: [14283.090598] [UFW BLOCK] IN= OUT=wlan0 SRC=192.168.1.65 DST=192.168.1.255 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=8612 DPT=8612 LEN=24 
Sep  6 22:40:36 pauly-laptop kernel: [14283.190692] [UFW BLOCK] IN= OUT=wlan0 SRC=192.168.1.65 DST=192.168.1.255 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=8613 DPT=8612 LEN=24 
Sep  6 22:40:36 pauly-laptop kernel: [14283.290818] [UFW BLOCK] IN= OUT=wlan0 SRC=192.168.1.65 DST=192.168.1.255 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=8614 DPT=8612 LEN=24 
Sep  6 22:40:37 pauly-laptop kernel: [14283.907642] [UFW BLOCK] IN= OUT=wlan0 SRC=192.168.1.65 DST=255.255.255.255 LEN=43 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=57786 DPT=3289 LEN=23 
Sep  6 22:40:38 pauly-laptop kernel: [14284.910233] [UFW BLOCK] IN= OUT=wlan0 SRC=192.168.1.65 DST=255.255.255.255 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=40596 DPT=1124 LEN=45 

---

### Post by Ms. Daisy on 2012-09-07
Did you try steeldriver's suggestion? I'd do that first if you're using saned. 

But the logs are saying that the port range is 8610-8614 and they're UDP.  So this should work:
```
sudo ufw allow 8610,8611,8612,8613,8614/udp
```

---

### Post by BigCityCat on 2012-09-07
> **Ms. Daisy said:**
> Did you try steeldriver's suggestion? I'd do that first if you're using saned. 

But the logs are saying that the port range is 8610-8614 and they're UDP.  So this should work:
```
sudo ufw allow 8610,8611,8612,8613,8614/udp
```

Yeh I tried sudo ufw allow 8610:8614/udp and it didn't work. Thanks though.

I'm looking at this.

[http://tldp.org/HOWTO/html_single/Scanner-HOWTO/](http://tldp.org/HOWTO/html_single/Scanner-HOWTO/)

> 
4.2.2. Across a Network

If you are interested in making scanner services available across a network from or to a remote machine, you will need to edit the saned.conf file in the configuration directory of the server (the computer with the scanner), whether /etc/sane.d or /usr/local/etc/sane.d. It usually consists of an entry 'scan-client.somedomain.firm' that will need to be replaced with the hostname of the client you want to be able to use the server's scanner. If you prefer an IP address this can be used instead.

The saned daemon will need to be run as well as inetd or xined on the server. See man saned for the exact changes required to inetd.conf or xined.conf. In addition port 6566 will need to be added to the /etc/services file:

sane 6566/tcp 

The client computer (without the scanner) will need net.conf edited to include the server machine name, i.e., 'scan-server.somedomain.firm.'

Also for the client(s), be sure the entry "net" isn't commented out in the dll.conf file.

---

### Post by BigCityCat on 2012-09-07
> **steeldriver said:**
> or how about...

```
sudo netstat -lntp | grep saned
```fwiw mine says 6566

Anyhow there should be a predefined application profile for saned, i.e.

```
sudo ufw allow saned
```should open the relevant port(s) - in fact I just tried it and indeed it opens 6566/tcp

Hope this helps

I did try this. It didn't work. Thanks

I was looking at this thread and this sounds exactly like what I am seeing. The person describes the solution but it's a little vague and beyond my level. Can you guys help me understand this.

[https://www.linuxquestions.org/questions/slackware-14/cannot-scan-with-sane-over-network-local-machine-works-850953/](https://www.linuxquestions.org/questions/slackware-14/cannot-scan-with-sane-over-network-local-machine-works-850953/)

---

### Post by BigCityCat on 2012-09-07
I think there is a lot more to this. It's above my level. I'm just gonna turn the firewall off when I need to scan but for anyone else reading this. Here is some additional information.

> What is Specific Regarding Firewall Setup for Using Scanners

For using scanners via network the SANE network daemon (the saned) is the server process which must run so that remote clients can access scanners which are connected (usually via USB) to the local host.

When you have a network printer scanner copier all-in-one device with a built-in network interface so that the device is directy accessible via network, it is usually used in a different way by "stand-alone scanning to e-mail" where no SANE software (in particular no saned) is involved (see the section "Scanning via Network" in SDB:Configuring Scanners).

The saned is used by the clients via two kind of network connections. In addition to a control connection (via port 6566) saned also uses a separated data connection (for the actual scanning data). The port of the data connection is selected by the operating system and could no be specified so that all ports above 1024 must have been accessible (i.e. open in the firewall) for connections from the clients. The newest saned version provides support to specify a range of ports for the data connection in the saned configuration file /etc/sane.d/saned.conf via an entry like "data_portrange = 30000 - 30100" so that only those ports would have to be open in the firewall. But the latter does not provide real better security because in the end the saned must be accessible for using scanners via network.

See what the saned man page reads:

First and foremost:
saned is not intended to be exposed to the
Internet or other non-trusted networks.
Make sure that access is limited by a firewall.

Additionally remember this section in the SuSEfirewall2 documentation: /usr/share/doc/packages/SuSEfirewall2/README reads

Some words about security:
Run only those services you actually need.
Think twice before opening them to the Internet.
Do not expose services that are designed
for use in a LAN to the Internet.

To protect your host against unwanted access:

Do not open the sane-port 6566 or any other port regarding using scanners for the external zone in the firewall.

On the other hand the firewall lets by default any network traffic pass via network interfaces which belong to the internal zone. Therefore when the network interface for the internal network is assigned to the internal firewall zone, client hosts in the internal network can access the SANE server process to access scanners which are connected to the server machine. Independent of the firewall setup the SANE server must additionally be configured to permit access from those client hosts (by default it does not permit access).

To make your SANE server accessible:

Assign the network interface which belongs to the internal network to the internal zone of the firewall.

Alternatively as a best effort setup when one same network interface is used for the Internet connection and for the internal network, assign the network interface to the external zone and specify the trusted internal network via FW_TRUSTED_NETS in the firewall configuration.

Example for FW_TRUSTED_NETS:

Assuming your trusted subnet is 192.168.0.0/24 the entry reads:

FW_TRUSTED_NETS="192.168.0.0/24,tcp,6566"

Saned needs additional ports besides 6566 for the actual data transfer (see above). It is recommend to use the same ports as ftp 30000 - 30100 for this (see Bug 551282#c39). Therefore the port range setting in /etc/sane.d/saned.conf should read:

data_portrange = 30000 - 30100

Instead of opening these ports in the firewall (cf. above "DO NOT ...") additional entries like the following are required (assuming your trusted subnet is 192.168.0.0/24) in the firewall configuration:

FW_TRUSTED_NETS="... 192.168.0.0/24,tcp,30000:30100"
FW_SERVICES_ACCEPT_RELATED_EXT="192.168.0.0/24,tcp,,30000:30100"

Furthermore the kernel module nf_conntrack_sane must be loaded (see this mail [http://lists.opensuse.org/archive/opensuse/2011-05/msg00000.html](http://lists.opensuse.org/archive/opensuse/2011-05/msg00000.html)) via the following additional entry for FW_LOAD_MODULES in the firewall configuration:

FW_LOAD_MODULES="... nf_conntrack_sane"

---

### Post by cryptotheslow on 2012-09-07
I'm not that familar with saned but just to shed some light on the UFW logs you posted....  those UDP packets appear to be some kind of discovery protocol as they are being sent to the broadcast address for the network *DST=192.168.1.255* which results in the packets being delivered to any active device on the network.

Presumably once the scanner responds then a connection is made to its specific IP address.

---

### Post by Morbius1 on 2012-09-07
If you're talking about this:
> If your firewall is a Linux machine, we strongly recommend using the
Netfilter nf_conntrack_sane connection tracking module instead.                      ** Make a backup copy of the ufw file:
```
sudo cp /etc/default/ufw /etc/default/ufw.bak
```Then edit /etc/default/ufw and change this line:
> IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_netbios_ns"To this:
> IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_netbios_ns [COLOR=Blue]**nf_conntrack_sane**[/COLOR]"Then restart ufw: 
```
sudo service ufw restart
```I should note that I personally have no idea if there is such a module but it is referenced in /etc/sane.d/sane.conf

---

### Post by Ms. Daisy on 2012-09-08
> **cryptotheslow said:**
> I'm not that familar with saned but just to shed some light on the UFW logs you posted....  those UDP packets appear to be some kind of discovery protocol as they are being sent to the broadcast address for the network *DST=192.168.1.255* which results in the packets being delivered to any active device on the network.

Presumably once the scanner responds then a connection is made to its specific IP address.
I noticed that but couldn't find any documentation on how to allow broadcasting in ufw. I could only find docs for iptables.  Do you know how to allow broadcasting in ufw? Is it as simple as adding 192.168.1.255?

---

