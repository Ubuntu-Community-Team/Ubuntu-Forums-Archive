---
title: "Configure SNMP traps with your Auth Key as the community string"
date: 2013-11-29
forum: Server Platforms
---

### Post by chaos_efphect on 2013-11-29
Hello all, So I am in need of some help from some of the more skilled members out there. I was toying around with the idea of trying to get ubuntu to send SNMP traps. I just started using [This APP]("http://architects.dzone.com/articles/introducing-coldstartio-%E2%80%93-snmp") in one of my cisco classes and for cisco routers it was rather straight forward. Now I would like to see if i could get my ubuntu server at home to also interface with that app with no luck. I am still a bit of a noob when it comes to SNMP and so far have gotten totally lost. I have done a ton of reading but have yet to find a nice tutorial that would explain how to enable snmp traps to be sent to an external server and use an auth key. 

So would anyone be willing to help me on this? 

```
Quote from coldstar's website
Configure your device to send SNMP traps with your Auth Key as the community string and as soon as alerts are received they are relayed to your phone within 500ms.

Cisco command                                             
snmp-server host trap.coldstart.io version 2c Auth_Key

```

---

### Post by jonobr on 2013-12-02
Hello


I dont think SNMP is enabled by default on Ubuntu server.
To issue traps from ubuntu you may need to install snmpd.

```
sudo apt-get install snmpd
```

Once done, you would then need to go into /etc/snmp/
there should be a config file in there called snmptrap.conf or something like that which you will need to modify to allow traps to be issued

You can check in snmpd is installed by entering 

```
which snmpd
```

---

