---
title: "FIRST_SPACES [      ] unable to start strongSwan -- fatal errors in config"
date: 2012-02-12
forum: Server Platforms
---

### Post by danny620 on 2012-02-12
When try to restart ipsec to load new configuration i get


danny@Northplanet:~$ sudo /etc/init.d/ipsec restart
 * Restarting strongswan IPsec services ipsec                                                                                                              Stopping strongSwan IPsec failed: starter is not running
Starting strongSwan 4.5.2 IPsec [starter]...
/etc/ipsec.conf:6: syntax error, unexpected FIRST_SPACES [      ]
unable to start strongSwan -- fatal errors in config

any ideas (below is my config file)


# ipsec.conf - strongSwan IPsec configuration file

# basic configuration

#  config setup
        # plutodebug=all
        # crlcheckinterval=600
        # strictcrlpolicy=yes
        # cachecrls=yes
        # nat_traversal=yes
#       charonstart=yes
#       plutostart=yes

# Add connections here.
config setup
virtual_private=%v4:10.0.0.0/8,%v4:192.168.0.0/16,%v4:172.16.0.0/12
nat_traversal=yes
protostack=netkey
oe=no
plutoopts="--interface=eth1" conn L2TP-PSK
authby=secret
pfs=no
auto=add
keyingtries=3
dpddelay=30
dpdtimeout=120
dpdaction=clear
rekey=yes
ikelifetime=8h
keylife=1h
type=transport
left=10.0.0.100
leftnexthop=%defaultroute
leftprotoport=17/1701
right=109.111.208.44
rightprotoport=17/1701

# Sample VPN connections

#conn sample-self-signed
#      left=%defaultroute
#      leftsubnet=10.1.0.0/16
#      leftcert=selfCert.der
#      leftsendcert=never
#      right=192.168.0.2
#      rightsubnet=10.2.0.0/16
#      rightcert=peerCert.der
#      auto=start

#conn sample-with-ca-cert
#      left=%defaultroute
#      leftsubnet=10.1.0.0/16
#      leftcert=myCert.pem
#      right=192.168.0.2
#      rightsubnet=10.2.0.0/16
#      rightid="C=CH, O=Linux strongSwan CN=peer name"
#      keyexchange=ikev2
#      auto=start

include /var/lib/strongswan/ipsec.conf.inc

---

### Post by danny620 on 2012-02-12
any help??

---

### Post by ecdsa on 2012-02-13
Hi Danny,

> Starting strongSwan 4.5.2 IPsec [starter]...
/etc/ipsec.conf:6: syntax error, unexpected FIRST_SPACES [      ]

any ideas (below is my config file)Unfortunately, the config file got seriously butchered when you posted it here. So I can't exactly pinpoint the problem. But in general the error you see above means that you didn't properly indent some of the options or comments in ipsec.conf.

For example, the following would trigger this problem:

```

conn L2TP-PSK
    authby=secret
#pfs=no
    auto=add

```Just make sure all options that belong to a *conn* or *config setup* section (including commented ones) are properly indented.

---

### Post by danny620 on 2012-02-13
Please see [http://www.northplanet.co.uk/screenshoot.jpg](http://www.northplanet.co.uk/screenshoot.jpg) still tryied but no luck.

Thanks for replying

---

### Post by ecdsa on 2012-02-13
Please have a look at the beginning of your file:

```

# config setup
    # plutodebug=all
    # crlcheckinterval=600
    # strictcrlpolicy=yes
    # cachecrls=yes
    nat_traversal=yes
    charonstart=yes
    plutostart=yes

```There are two problems with these lines:

[LIST=1]
[*]You have three options not within any config section and not commented out.
[*]You have indented comments, which are not part of a config section (there shouldn't be any white-space before the # character on these lines).
[/LIST]
 Both of these issues cause the error seen here. The second issue might seem a bit strange but the parser for ipsec.conf was written a long time ago and is rather picky.

---

