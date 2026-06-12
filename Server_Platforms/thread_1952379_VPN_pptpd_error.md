---
title: "VPN pptpd error"
date: 2012-04-04
forum: Server Platforms
---

### Post by JSunny on 2012-04-04
Hey !

i just got into ubuntu a couple of weeks ago. right now i can handle the basics commands like  cd, cp, nano, mv, ifconfig and so on

i tried to set up a VPN Server (pptpd), therefor i just used one of the several tutorials via google.
So simple i installed pptpd with

sudo apt-get install pptpd

and configured the necessary files.

There is no eth0 gateway on my Ubuntu vServer, so i just venet0 instead.

here the abstract from ifconfig


root@h2014422:~# ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5885 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5885 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:682265 (682.2 KB)  TX bytes:682265 (682.2 KB)

venet0    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:127.0.0.1  P-t-P:127.0.0.1  Bcast:0.0.0.0  Mask:255.255.255.255
          inet6 addr: ::1/128 Scope:Host
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
          RX packets:547715 errors:0 dropped:0 overruns:0 frame:0
          TX packets:652893 errors:0 dropped:8 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:224323666 (224.3 MB)  TX bytes:642187033 (642.1 MB)

venet0:0  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:85.214.217.184  P-t-P:85.214.217.184  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1

  when i try to connect with a client now (PC WIN7 or Android) there appears always an Error 807. Something like authentication failed. but i am sure there is no mistake in my chap-secrets configuration file. 

So, could someone please help me to troubleshoot the error.
if i should provide files or information please ask (with dir) and i ll post them .

Thanks for your help!

---

### Post by spynappels on 2012-04-04
I replied to your German post, but I basically said that there could be a problem with venet0 and lo having the same IP address.

Is there a specific reason you used pptp? Would a SSL based VPN like OpenVPN be an option for you?

---

### Post by JSunny on 2012-04-04
thanks spynappels for your answer. 
basically i want to use pptpd, 'cause it works simple and fine also with my android and other devices. OpenVPN is fine too but i am not sure if that runs on my phone as well ;)
therefor i prefer pptpd.

---

### Post by JSunny on 2012-04-04
you said

"It appears that there may be some issues in that venet0 has the same IP address as lo, which could be causing problems for you."

what do you mean with that exactly?
these are the standard configurations which where provided from my provider. so i didnt change them

---

### Post by JSunny on 2012-04-04
so these are my configurations

**root@h2014422:~# cat /etc/pptpd.conf**
    ###############################################
    # $Id: pptpd.conf 4255 2004-10-03 18:44:00Z rene $
    #
    # Sample Poptop configuration file /etc/pptpd.conf
    #
    # Changes are effective when pptpd is restarted.
    ###############################################

    # TAG: ppp
    #    Path to the pppd program, default ./usr/sbin/pppd. on Linux
    #
    ppp /usr/sbin/pppd

    # TAG: option
    #    Specifies the location of the PPP options file.
    #    By default PPP looks in ./etc/ppp/options.
    #
    option /etc/ppp/pptpd-options

    # TAG: debug
    #    Turns on (more) debugging to syslog
    #
    #debug

    # TAG: stimeout
    #    Specifies timeout (in seconds) on starting ctrl connection
    #
    # stimeout 10

    # TAG: noipparam
    #       Suppress the passing of the client.s IP address to PPP, which is
    #       done by default otherwise.
    #
    #noipparam

    # TAG: logwtmp
    #    Use wtmp(5) to record client connections and disconnections.
    #
    logwtmp

    # TAG: bcrelay <if>
    #    Turns on broadcast relay to clients from interface <if>
    #
    bcrelay venet0

    # TAG: localip
    # TAG: remoteip
    #    Specifies the local and remote IP address ranges.
    #
    #       Any addresses work as long as the local machine takes care of the
    #       routing.  But if you want to use MS-Windows networking, you should
    #       use IP addresses out of the LAN address space and use the proxyarp
    #       option in the pppd options file, or run bcrelay.
    #
    #    You can specify single IP addresses seperated by commas or you can
    #    specify ranges, or both. For example:
    #
    #        192.168.0.234,192.168.0.245-249,192.168.0.254
    #
    #    IMPORTANT RESTRICTIONS:
    #
    #    1. No spaces are permitted between commas or within addresses.
    #
    #    2. If you give more IP addresses than MAX_CONNECTIONS, it will
    #       start at the beginning of the list and go until it gets
    #       MAX_CONNECTIONS IPs. Others will be ignored.
    #
    #    3. No shortcuts in ranges! ie. 234-8 does not mean 234 to 238,
    #       you must type 234-238 if you mean this.
    #
    #    4. If you give a single localIP, that.s ok - all local IPs will
    #       be set to the given one. You MUST still give at least one remote
    #       IP for each simultaneous client.
    #
    # (Recommended)
    #localip 192.168.0.1
    #remoteip 192.168.0.234-238,192.168.0.245
    # or
    localip 10.89.64.1
    remoteip 10.89.64.100-150

**root@h2014422:~# cat /etc/ppp/chap-secrets**
# Secrets for authentication using CHAP
# client        server  secret                  IP addresses
jani            pptpd   jani                    *


**root@h2014422:~# cat /etc/sysctl.conf**
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables.
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# Uncomment the following to stop low-level messages on console
#kernel.printk = 4 4 1 7

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.all.forwarding=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Ignore ICMP broadcasts
#net.ipv4.icmp_echo_ignore_broadcasts = 1
#
# Ignore bogus ICMP errors
#net.ipv4.icmp_ignore_bogus_error_responses = 1
#
# Do not accept ICMP redirects (prevent MITM attacks)
#net.ipv4.conf.all.accept_redirects = 0
#net.ipv6.conf.all.accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net.ipv4.conf.all.secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net.ipv4.conf.all.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net.ipv4.conf.all.accept_source_route = 0
#net.ipv6.conf.all.accept_source_route = 0
#
# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1

---

### Post by spynappels on 2012-04-04
> **JSunny said:**
> There is no eth0 gateway on my Ubuntu vServer, so i just venet0 instead.

here the abstract from ifconfig


root@h2014422:~# ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5885 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5885 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:682265 (682.2 KB)  TX bytes:682265 (682.2 KB)

venet0    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:127.0.0.1  P-t-P:127.0.0.1  Bcast:0.0.0.0  Mask:255.255.255.255
          inet6 addr: ::1/128 Scope:Host
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
          RX packets:547715 errors:0 dropped:0 overruns:0 frame:0
          TX packets:652893 errors:0 dropped:8 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:224323666 (224.3 MB)  TX bytes:642187033 (642.1 MB)

venet0:0  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:85.214.217.184  P-t-P:85.214.217.184  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1


Ok, lets start at the beginning.
This is a virtual server, right?  Is it running on OpenVZ? Is it a server in the cloud (VPS) or do you have an OpenVZ host running locally somewhere?

I think the issue lies with the networking on the Server rather than with pptp. Looking at venet0 in the ifconfig output, it has 127.0.0.1 as it's IP address. That cannot be correct, as this IP address is reserved for the loopback interface (lo). There is a logical interface configured in venet0:0, but it is a point-to-point link, which does not look right.

Could you post the output of the following to see what the situation is regarding networking?
```
cat /etc/network/interfaces
```
Can you access the internet from the server?

---

### Post by JSunny on 2012-04-04
thanks spynappels for your help.

**root@h2014422:~# cat /etc/network/interfaces**
# This configuration file is auto-generated.
# WARNING: Do not edit this file, otherwise your changes will be lost.
# Please edit template /etc/network/interfaces.template instead.


auto lo
iface lo inet loopback
        address 127.0.0.1
        netmask 255.0.0.0
        broadcast 127.255.255.255
        up ip route replace 127.0.0.0/8 dev lo


# Auto generated venet0 interfaces
auto venet0
iface venet0 inet static
        address 127.0.0.1
        netmask 255.255.255.255
        broadcast 0.0.0.0

        up route add default dev venet0


iface venet0 inet6 static
        address ::1
        netmask 128

        up ip -6 r a default dev venet0

auto venet0:0
iface venet0:0 inet static
        address 85.214.217.184
        netmask 255.255.255.255

yes, the server runs fine. There is already webspace & cloud on it without any problems and i tried also to install Voip. So that cant be a problem. 
Thats correct, its an virtual server from strato
original website [http://www.strato.de/server/virtual-linux-server/](http://www.strato.de/server/virtual-linux-server/)
english equivalence [http://www.strato-hosting.co.uk/server/virtual/](http://www.strato-hosting.co.uk/server/virtual/)

as far as i can see that, TUN / TAP is available "(TUN and TAP are virtual network devices. They facilitate the configuration of VPNs)"

---

### Post by spynappels on 2012-04-04
Ok, I think I see what way this works, but I'm a little shaky as I've not worked with OpenVZ before and I'm not sure how the networking is set up.

Let's have a look at the pptp side then.

Is the pptpd service running? ```
ps -ef | grep pptpd
```

Is it listening on the correct port? ```
lsof | grep pptpd
```

If the answer to both of those is yes, we can take a packet capture on some traffic to that port on interface venet0:0 and see if thraffic is getting there and what the response is.

---

### Post by JSunny on 2012-04-04
just rebooted

**root@h2014422:~# ps -ef | grep pptpd**
root      1463     1  0 16:44 ?        00:00:00 /usr/sbin/pptpd
root      3272  3260  0 16:45 pts/0    00:00:00 grep --color=auto pptpd

**root@h2014422:~# lsof | grep pptpd**
pptpd     1463         root  cwd    DIR              0,121     4096  12714619 /
pptpd     1463         root  rtd    DIR              0,121     4096  12714619 /
pptpd     1463         root  txt    REG              0,121    26572  12814400 /usr/sbin/pptpd
pptpd     1463         root  mem    REG              0,121    42572  12716935 /lib/libnss_files-2.11.1.so
pptpd     1463         root  mem    REG              0,121    79676  12716929 /lib/libnsl-2.11.1.so
pptpd     1463         root  mem    REG              0,121  1335560  12716864 /lib/libc-2.11.1.so
pptpd     1463         root  mem    REG              0,121    31020  12716997 /lib/libwrap.so.0.7.6
pptpd     1463         root  mem    REG              0,121   113964  12716846 /lib/ld-2.11.1.so
pptpd     1463         root    0u   CHR                1,3      0t0  12715221 /dev/null
pptpd     1463         root    1u   CHR                1,3      0t0  12715221 /dev/null
pptpd     1463         root    2u   CHR                1,3      0t0  12715221 /dev/null
pptpd     1463         root    3r  FIFO                0,6      0t0   4612021 pipe
pptpd     1463         root    4w  FIFO                0,6      0t0   4612021 pipe
pptpd     1463         root    5u  unix 0xffff8102c1e603c0      0t0   4612022 socket
pptpd     1463         root    6u  IPv4            4612023      0t0       TCP *:1723 (LISTEN)

"If the answer to both of those is yes, we can take a packet capture on  some traffic to that port on interface venet0:0 and see if thraffic is  getting there and what the response is. 	"

how can i do that?
oh and btw, someone told me to use veth0 isntead of eth0 because of the virtual machine, could that be correct?

---

### Post by JSunny on 2012-04-04
now i changed in /etc/pptpd.conf the venet0 to veth0 and it says:


**root@h2014422:~# ps -ef | grep pptpd**
root      3283     1  0 16:48 ?        00:00:00 pptpd [87.123.100.167:3334 - 0000]
root      3317  3260  0 16:51 pts/0    00:00:00 grep --color=auto pptpd
**root@h2014422:~# lsof | grep pptpd**

(nothing)

---

### Post by spynappels on 2012-04-04
> **JSunny said:**
> just rebooted

**root@h2014422:~# ps -ef | grep pptpd**
root      1463     1  0 16:44 ?        00:00:00 /usr/sbin/pptpd
root      3272  3260  0 16:45 pts/0    00:00:00 grep --color=auto pptpd

**root@h2014422:~# lsof | grep pptpd**
pptpd     1463         root  cwd    DIR              0,121     4096  12714619 /
pptpd     1463         root  rtd    DIR              0,121     4096  12714619 /
pptpd     1463         root  txt    REG              0,121    26572  12814400 /usr/sbin/pptpd
pptpd     1463         root  mem    REG              0,121    42572  12716935 /lib/libnss_files-2.11.1.so
pptpd     1463         root  mem    REG              0,121    79676  12716929 /lib/libnsl-2.11.1.so
pptpd     1463         root  mem    REG              0,121  1335560  12716864 /lib/libc-2.11.1.so
pptpd     1463         root  mem    REG              0,121    31020  12716997 /lib/libwrap.so.0.7.6
pptpd     1463         root  mem    REG              0,121   113964  12716846 /lib/ld-2.11.1.so
pptpd     1463         root    0u   CHR                1,3      0t0  12715221 /dev/null
pptpd     1463         root    1u   CHR                1,3      0t0  12715221 /dev/null
pptpd     1463         root    2u   CHR                1,3      0t0  12715221 /dev/null
pptpd     1463         root    3r  FIFO                0,6      0t0   4612021 pipe
pptpd     1463         root    4w  FIFO                0,6      0t0   4612021 pipe
pptpd     1463         root    5u  unix 0xffff8102c1e603c0      0t0   4612022 socket
pptpd     1463         root    6u  IPv4            4612023      0t0       TCP *:1723 (LISTEN)


Ok, lets stick with venet0 for the moment, as at least you have connection with that, and the daemon is running and listening on port 1723 which is correct.

To take a network capture you will need to use tcpdump
```
tcpdump -i venet0:0 -c 1000 -w /var/tmp/pptp_diag1.pcap port 1723
``` while attempting to connect a pptp session from a device. The idea is to capture what is happening when a client tries to connect. The -i flag tells tcpdump to capture from the venet0:0 interface, the -c flag tells it to only capture 1000 packets (to begin with) and the -w flag tells it to write the packets to a file.

You should transfer the resulting file to your local computer and open it in Wireshark to see what traffic is sent between the client and the pptp server.

---

### Post by JSunny on 2012-04-04
there you go :)

[I][http://h2014422.stratoserver.net/log/pptp_diag1.pcap](http://h2014422.stratoserver.net/log/pptp_diag1.pcap)

----

maybe i understand that wrong but could it be that my client actually connect but then disconnect again?
[/I][B]
root@h2014422:/var/tmp# ps -ef | grep pptpd[/B][I]
root      3358     1  0 16:55 ?        00:00:00 /usr/sbin/pptpd
root      3529  3358  0 17:51 ?        00:00:00 pptpd [87.123.100.167:0A11 - 008    0]
root      3533  3358  0 17:53 ?        00:00:00 pptpd [87.123.100.167:9DD6 - 010    0]
root      3575  3358  0 17:54 ?        00:00:00 pptpd [87.123.100.167:8D78 - 018    0]
root      3579  3358  0 17:55 ?        00:00:00 pptpd [87.123.100.167:5414 - 020    0]
root      3642  3358  0 17:56 ?        00:00:00 pptpd [87.123.100.167:1A60 - 028    0]
root      3791  3548  0 18:12 pts/2    00:00:00 grep --color=auto pptpd

[/I]

---

### Post by spynappels on 2012-04-04
Hi,

I've had a look at the packet capture and I can see that there were 3 connection attempts made.

In each case the TCP Control Connection is set up correctly, and the Start-Control-Connection-Request and Start-Control-Connection-Reply messages are exchanged correctly.

What I don't understand is why the client sends a FIN message to close the TCP connection, but it means that the client closes the connection, not the server.

Unfortunately, I don't know enough about the pptp protocol to be able to troubleshoot any further. I hope someone else who is more knowledgeable on the protocol can help you further, at least we were able to see that networking appears to work correctly.

I wish you all the best with it and hope you get it sorted out:wink:

---

### Post by JSunny on 2012-04-05
thanks spynappels for your help. i hope someone else is able to help me.

but still, is there any way to avoid that problem? i tried to reinstall pptpd a couple of times, but still it doesnt help. any other ideas?

thanks all

---

### Post by JSunny on 2012-04-12
no one got an idea?

---

