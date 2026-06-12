---
title: "Help analyze my open ports please"
date: 2009-11-10
forum: Security
---

### Post by ssc351 on 2009-11-10
Hey everyone,

The past week or so I have been learning about linux security/firewalls/etc and learning about how to be paranoid :)  I am a newbie with all this stuff so bear with me if I get something wrong.  So I did a couple of different port scans and it appears I have some ports open that I have no idea what they do and I am wondering how to close them or if I even need to close them.  
The ports I know I use are 22 for SSH (for my iphone) and port 45454 for Vuze or torrents. I also have i2p set-up on my computer so I would have expected to see port 8887 open, but its not there...interesting.  I don't really know what the rest of the ports are...some look like a printer port and maybe a networking port but Im not sure.  

Lastly, when i set-up i2p I forwarded port 8887 on my router, but this got me thinking, is it better to just forward all the ports I need or to use UPnP?  It would seem more user friendly to just use UPnP but does that impose some security risks?

Thanks for the help!

lsof -i -n -P
COMMAND  PID   USER   FD   TYPE DEVICE SIZE NODE NAME
firefox 4093 travis   22u  IPv4  39093       TCP 188.126.86.183:56562->91.189.94.12:80 (CLOSE_WAIT)
firefox 4093 travis   48u  IPv4  39143       TCP 188.126.86.183:56563->91.189.94.12:80 (CLOSE_WAIT)
firefox 4093 travis   60u  IPv4  39180       TCP 188.126.86.183:56564->91.189.94.12:80 (CLOSE_WAIT)
firefox 4093 travis   61u  IPv4  39183       TCP 188.126.86.183:56565->91.189.94.12:80 (CLOSE_WAIT)
firefox 4093 travis   62u  IPv4  39186       TCP 188.126.86.183:56566->91.189.94.12:80 (CLOSE_WAIT)
firefox 4093 travis   63u  IPv4  39203       TCP 188.126.86.183:56567->91.189.94.12:80 (CLOSE_WAIT)
firefox 4093 travis   64u  IPv4  39218       TCP 188.126.86.183:56568->91.189.94.12:80 (CLOSE_WAIT)
firefox 4093 travis   65u  IPv4  36175       TCP 188.126.86.183:41836->64.152.208.152:80 (ESTABLISHED)
firefox 4093 travis   67u  IPv4  39224       TCP 188.126.86.183:56569->91.189.94.12:80 (CLOSE_WAIT)
firefox 4093 travis   71u  IPv4  36257       TCP 188.126.86.183:42487->75.126.76.147:80 (ESTABLISHED)
firefox 4093 travis   72u  IPv4  36286       TCP 188.126.86.183:34067->87.248.207.79:1935 (ESTABLISHED)
firefox 4093 travis   74u  IPv4  30336       TCP 154.32.1.2:50734->68.142.121.224:443 (ESTABLISHED)
firefox 4093 travis   77u  IPv4  17111       TCP 188.126.89.131:51700->74.125.163.20:80 (ESTABLISHED)
firefox 4093 travis   78u  IPv4  36305       TCP 188.126.86.183:47668->74.125.79.102:80 (ESTABLISHED)
java    6892 travis   10u  IPv6  33801       TCP 127.0.0.1:6880 (LISTEN)
java    6892 travis   27u  IPv6  33822       TCP *:45454 (LISTEN)
java    6892 travis   31u  IPv6  33946       TCP 127.0.0.1:45100 (LISTEN)
java    6892 travis   77u  IPv6  33954       TCP *:6886 (LISTEN)
java    6892 travis   78u  IPv6  33958       TCP *:43603 (LISTEN)
java    6892 travis   80u  IPv6  34071       UDP *:45454 
java    6892 travis   84u  IPv6  34003       UDP *:1900 
java    6892 travis   94u  IPv6  33984       UDP *:16680 
java    6892 travis   95u  IPv6  33985       UDP 188.126.86.183:33683 
java    6892 travis   96u  IPv6  33986       UDP *:16680 
java    6892 travis   97u  IPv6  33987       UDP 154.32.1.2:33683 
java    6892 travis   98u  IPv6  37778       TCP 188.126.86.183:33095->173.88.146.106:36297 (ESTABLISHED)
java    6892 travis  100u  IPv6  34031       TCP *:51909 (LISTEN)
java    6892 travis  104u  IPv6  34005       UDP 188.126.86.183:51909 
java    6892 travis  105u  IPv6  34006       UDP *:1900 
java    6892 travis  106u  IPv6  34007       UDP 154.32.1.2:51909 
java    6892 travis  138u  IPv6  35837       TCP 188.126.86.183:57162->64.229.176.29:21770 (ESTABLISHED)
java    6892 travis  143u  IPv6  34299       TCP 188.126.86.183:34342->123.243.120.160:42260 (ESTABLISHED)
java    6892 travis  162u  IPv6  34332       TCP 188.126.86.183:53338->68.238.241.53:36463 (CLOSE_WAIT)
java    6892 travis  169u  IPv6  34501       TCP 188.126.86.183:33308->189.77.138.116:17933 (ESTABLISHED)


Another from nmap:
 nmap -sT localhost -p 20-65535

Starting Nmap 4.76 ( [http://nmap.org](http://nmap.org) ) at 2009-11-10 18:18 PST
Interesting ports on localhost (127.0.0.1):
Not shown: 65506 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
631/tcp   open  ipp
6880/tcp  open  unknown
6886/tcp  open  unknown
43603/tcp open  unknown
45100/tcp open  unknown
45454/tcp open  unknown
51909/tcp open  unknown

sudo netstat -plntu 
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      2473/sshd       
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      5863/cupsd      
tcp6       0      0 127.0.0.1:6880          :::*                    LISTEN      6892/java       
tcp6       0      0 :::51909                :::*                    LISTEN      6892/java       
tcp6       0      0 :::6886                 :::*                    LISTEN      6892/java       
tcp6       0      0 :::139                  :::*                    LISTEN      2762/smbd       
tcp6       0      0 127.0.0.1:45100         :::*                    LISTEN      6892/java       
tcp6       0      0 :::45454                :::*                    LISTEN      6892/java       
tcp6       0      0 :::43603                :::*                    LISTEN      6892/java       
tcp6       0      0 :::22                   :::*                    LISTEN      2473/sshd       
tcp6       0      0 :::445                  :::*                    LISTEN      2762/smbd       
udp        0      0 0.0.0.0:49154           0.0.0.0:*                           3044/avahi-daemon: 
udp        0      0 154.32.1.2:137          0.0.0.0:*                           2758/nmbd       
udp        0      0 0.0.0.0:137             0.0.0.0:*                           2758/nmbd       
udp        0      0 154.32.1.2:138          0.0.0.0:*                           2758/nmbd       
udp        0      0 0.0.0.0:138             0.0.0.0:*                           2758/nmbd       
udp        0      0 0.0.0.0:68              0.0.0.0:*                           3913/dhclient   
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           3044/avahi-daemon: 
udp6       0      0 :::45454                :::*                                6892/java       
udp6       0      0 154.32.1.2:33683        :::*                                6892/java       
udp6       0      0 188.126.86.183:33683    :::*                                6892/java       
udp6       0      0 :::16680                :::*                                6892/java       
udp6       0      0 :::16680                :::*                                6892/java       
udp6       0      0 154.32.1.2:51909        :::*                                6892/java       
udp6       0      0 188.126.86.183:51909    :::*                                6892/java       
udp6       0      0 :::1900                 :::*                                6892/java       
udp6       0      0 :::1900                 :::*   

Also, here is my firewall script for my iptables...I took it off of the beginners tutorial:
#!/bin/bash

# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 
modprobe ip_conntrack_irc
modprobe ip_conntrack_ftp

# Remove all rules and chains
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow loopback traffic
iptables -A FIREWALL -i lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
iptables -A FIREWALL -j DROP

# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL
# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP

# Allow i2p
iptables -A TRUSTED -p udp -m udp --dport 8887 -j ACCEPT
iptables -A TRUSTED -p udp -m udp --dport 123 -j ACCEPT
#iptables -A TRUSTED -p udp -m tcp --dport 7657 -j ACCEPT

# Allow bittorrent
iptables -A TRUSTED -p tcp -m tcp --dport 45454-j ACCEPT

# End message
echo " [End iptables rules setting]"

---

