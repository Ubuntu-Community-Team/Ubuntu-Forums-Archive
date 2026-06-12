---
title: "[Help] Iptables rules"
date: 2010-10-16
forum: Security
---

### Post by adahendra on 2010-10-16
Hello all,
this is my first thread, i need help from all Ubuntu Forum Members. i need help about iptables rules , 

Schema :
Main Server ------------Internet  ---------- Router [eth0] -- LAN [eth1]---------Client
 110.24.88.57 ----------197.180.34.2      199.181.2.10 -- 192.168.10.1/24


[LIST]
[*]LAN can access to Internet all port
[*]Router can access internet
[*]Router can parsing file to Main Server via Internet
[*]Router can give information about b/w to Main Server using  mysql port
[/LIST]

i was create some script 
Script for  connection.sh

```

#!/bin/bash
## ID is number of Server 
ID="S001"

PUB_IP=`wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//'`
#
# curl -s checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//'
# curl -s http://whatismyip.org/
# lynx -dump checkip.dyndns.org
# lynx -dump www.whatismyip.com | grep 'Your IP'
#
IF_IP=`/sbin/ifconfig eth0 | grep 'inet addr:' | cut -d: -f2 | awk '{ print $1}'`
HOST_NAME=`hostname -f`

DIST=`lsb_release -d |awk '{ print $2}'`
DIST_VERSION=`lsb_release -d |awk '{ print $3}'`
DIST_LTS=`lsb_release -d |awk '{ print $4}'`
DISTRO="$DIST $DIST_VERSION $DIST_LTS"

DATE=`date --date='now' +'%A, %r %B %d %Y'`

KERNEL_OS=`uname -s`
KERNEL_VER=`uname -r`
KERNEL_MACHINE=`uname -m`
KERNEL="$KERNEL_OS $KERNEL_VER on $KERNEL_MACHINE"

DISK_USAGE=`df -h | grep /dev/sda3 | cut -b41-44`
DISK_FREE_0=`df -h | grep /dev/sda3 | cut -b41-44 | sed -e 's/\%//g'`
DISK_FREE_1=$(bc << EOF
100 - $DISK_FREE_0
EOF
)
DISK_FREE="$DISK_FREE_1 %"
BW=`/usr/bin/iperf -c** 110.24.88.57 **| grep bit | awk '{ print $7 $8}'`

echo $HOST_NAME--$IF_IP--$BW--$METAID--$DISK_FREE-- > parsing.txt
#echo $HOST_NAME--$IF_IP--$PUB_IP--$BW--$METAID$DISK_FREE-- > parsing.txt
#echo $HOST_NAME;
#echo $IF_IP;
#echo $PUB_IP;
#echo $BW;


]
```and this is code for parsing.php

```
<?php

$hostname = " 110.24.88.57 ";
$database = "monitoring";
$user = "monitoring";
$pass = "monitoring";

mysql_connect(' 110.24.88.57 ', 'monitoring', '110.24.88.57 ') or die ('Error!!');
mysql_select_db('monitoring');

$data = fopen("parsing.txt","r") or exit (" Ga bisa dibuka! ");
$data2 = fread($data,filesize("parsing.txt"));

$expl = explode("--",$data2);
$host = $expl[0];// Host Number
$ip = $expl[1];//IP Address
$bw = $expl[2];//bw\
$metaid = $expl[3];//About ID of Server

echo $expl[3]."<br>";
//echo $expl[1]."<br>";
//echo $expl[2]."<br>";
//echo $expl[3]."<br>";
//echo $expl[4]."<br>";
//echo $expl[5]."<br>==============================================<br>";

$cekmetaid = mysql_query("SELECT id_host FROM t_host WHERE metaid='".$metaid."'");
$row = mysql_fetch_array($cekmetaid);
$id_host = $row['id_host'];
echo $id_host;
if($id_host != ''){
 echo "masuk";
 $sql = mysql_query("insert into t_monitor set id_host='".$row['id_host']."', ip = '$ip',bandwidth ='$bw', dateupdate=NOW()");
}
//$db->Execute($str);

?>

```And this is my rules for iptables :
```
#!/bin/bash

# How TO Use
# ./routing.sh eth0 IP_SERVER eth1 IP_LAN
#


INET_IP="$2"
INET_IFACE="$1"

LAN_IFACE="$3"
LAN_IP="$4"

##
IP_PPP0="ppp0"

##IPTABLES
IPT="/sbin/iptables"

#PORT FORWARDING
echo sh -c "1" > /proc/sys/net/ipv4/ip_forward



$IPT --flush
$IPT --table nat --flush
$IPT --delete-chain
$IPT --table nat --delete-chain
#$IPT -P INPUT DROP
$IPT -P OUTPUT ACCEPT
$IPT -P FORWARD ACCEPT
 

#ADD IP TABLE RULES
#$IPT  -A OUTPUT -p ALL -o lo -j ACCEPT
$IPT --table nat --append POSTROUTING --out-interface $LAN_IP -j MASQUERADE

$IPT --append FORWARD --in-interface $LAN_IFACE -j ACCEPT

$IPT -A FORWARD -i $LAN_FACE -o $INET_IFACE -j FORWARD
$IPT -A INPUT -i $LAN_IFACE -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT 
$IPT -A FORWARD -i $INET_IFACE -o $INET_IFACE -m state --state ESTABLISHED,RELATED  -j ACCEPT
$IPT -A OUTPUT -o $INET_IFACE -j ACCEPT
$IPT -A OUTPUT -p ALL -o $LAN_IFACE -j ACCEPT
#$IPT -A OUTPUT -p ALL -o $IP_PPP0 -j ACCEPT
$IPT -A FORWARD -j LOG
$IPT -P INPUT -j ACCEPT

# if connection to the internet using GSM modem
#$IPT -A FORWARD -i $INET_IFACE -o $IP_PPP0 -j FORWARD
#$IPT -A OUTPUT -o $IP_PPP0 -j ACCEPT
#$IPT -A INPUT -i $INET_IFACE -j ACCEPT


$IPT -S
$IPT -vnL

cat "/root/routing.sh" >> /etc/rc.local
cat "exit 0" >> /etc/rc.local

```When i'm running file /usr/bin/connection.sh 
i got an error message : Connection refuse

when i'm running file /usr/bin/php parsing.php
working without error 

when i'm running file routing.sh
afer running routing.sh , i can't access localhost and internet

:( :(

Need Help 

Thank You

---

