---
title: "VPN Confiuration"
date: 2012-03-20
forum: Server Platforms
---

### Post by weiinc on 2012-03-20
I am trying to configure OPENVPN and carefully followed the procedure shown here:

[https://help.ubuntu.com/10.10/serverguide/C/openvpn.html](https://help.ubuntu.com/10.10/serverguide/C/openvpn.html)

When I try to start the server it fails.

syslog shows:

Mar 20 14:33:25 ubuntu-server ovpn-server[9046]: Options error: You must define DH file (--dh)

I am neither a newbie nor an expert in all things Linux. This is one of those not so smart me things.

Any direction will be appreciated.

Mike

---

### Post by RyanRahl on 2012-03-20
It looks like your config file is not pointed to your Diffie Hellman parameters that you created with ./build-dh from the tutorial you linked. Assuming you used the easy-rsa scripts included with OpenVPN, the file will be called something like dh1024.pem and will be located where you ran the script (usually /etc/openvpn/easy-rsa/2.0). In your config file you should have a line that says

```
dh dh1024.pem
```

So if your dh1024.pem file is still in the easy-rsa script directory you just need to move it to the same directory that contains your config file (usually /etc/openvpn).

If this is not the case you should post your config file and the output of:

```
sudo ls -lhR /etc/openvpn
```
and
```
sudo cat /var/log/syslog | grep -i openvpn
```

So everyone can have a closer look

I would suggest using this tutorial in the future:

[http://openvpn.net/index.php/open-source/documentation/howto.html#pki](http://openvpn.net/index.php/open-source/documentation/howto.html#pki)

---

### Post by SeijiSensei on 2012-03-20
If you're simply trying to set up a point-to-point tunnel between two machines, then using a [shared static key]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html") is much much easier.

I've run dozens of OpenVPN tunnels this way.  Here's an example of the config file for one of them:

```

dev tun
remote openvpn.example.com
ifconfig 10.1.1.10 10.1.1.1
up /etc/openvpn/add_routes.thistunnel
secret /etc/openvpn/keys/thistunnel.key
port 51000
user nobody
group nogroup
comp-lzo
ping 15
ping-restart 45
ping-timer-rem
persist-tun
persist-key
verb 3

```

This is the file for the client.  It can be behind a firewall or on a roaming machine.  When OpenVPN starts, it attempts to connect with openvpn.example.com and set up the tunnel.

The configuration file on the other end is essentially identical to this one except there is no "remote" directive, and the order of addresses in the "ifconfig" directive is reversed.

You create the key file by running the command "openvpn --genkey --secret /etc/openvpn/keys/thistunnel.key"

---

### Post by collisionystm on 2012-03-20
I do a PTP vpn between 7 sites.

I keep it relatively simple.

Install openvpn

use my static.key i generated

openvpn --genkey --secret static.key

keep the static.key in the /etc/openvpn folder

On server side, I make a .conf file for the site in /etc/openvpn

client.conf

remote IP.ADDRESS.OF.CLIENT
dev tun
port 83*
secret static.key
ifconfig 10.6.0.* 10.7.0.*
daemon
route subnet.of.client subnet.mask


On Client side use the same static.key

server.conf

local IP.OF.LISTENING.ADAPTER
dev tun
port 83*
secret secret.key
daemon
ifconfig 10.7.0.* 10.6.0.*
route subnet.of.server subnet.mask


You can start the VPN using 

sudo openvpn client.conf on the server
sudo openvpn server.conf on the client

or just sudo service openvpn restart on both machines


test with a ping.

Replace the * with the number of your choice. Needs to match on both ends.

Each client needs a different port to the server.

---

### Post by collisionystm on 2012-03-21
I also made a short script that will notify you if the client is down.

#!/bin/bash
HOSTS="IP OF CLIENT"
COUNT=4
for myHost in $HOSTS
do
  count=$(ping -c $COUNT $myHost | grep 'received' | awk -F',' '{ print $2 }' | awk '{ print $1 }')
  if [ $count -eq 0 ]; then
    # 100% failed
        echo "An attempt to reach the VPN Client $HOSTS failed at $(date). Please check the internet connection and if needed reboot the server." | mail -s "VPN Client unreachable" myemail@address
  fi
done

I have it run in cron every 5 minutes.

---

### Post by weiinc on 2012-03-21
thanks ever so much.

i believe i got the system muddled and i am re-generating the server.

i will try the suggested method and report success or failure

mike

---

