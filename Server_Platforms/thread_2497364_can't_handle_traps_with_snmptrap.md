---
title: "can't handle traps with snmptrap"
date: 2024-05-02
forum: Server Platforms
---

### Post by davidtuti2 on 2024-05-02
[COLOR=#0C0D0E][FONT=-apple-system]I'm trying to execute a script when traps incoming to my server but I can't see script execution.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]My snmptrapd.conf[/FONT][/COLOR]
```

authcommunity log,execute,net public
traphandle default /tmp/kk.sh
```

My script:

[HTML] more /tmp/kk.shecho "hola hola hola" >> /tmp/log.txtecho "$*" >> /tmp/log.txt[/HTML]

I check with tcpdump if the trap arrives:

[HTML]root@agente:~# tcpdump -i ens33 port 162tcpdump: verbose output suppressed, use -v or -vv for full protocol decodelistening on ens33, link-type EN10MB (Ethernet), capture size 262144 bytes
09:23:39.333678 IP 192.168.1.119.37775 > agente.snmp-trap:  C="Public" Trap(454)  E:1031.9.1 192.168.1.119 enterpriseSpecific s=10 0 E:1031.9.1.1="U" E:1031.9.1.2="77" E:1031.9.1.3="controlm921" E:1031.9.1.4="" E:1031.9.1.5="0008v" E:1031.9.1.6="V" E:1031.9.1.7="Handled" E:1031.9.1.8="20240426174635" E:1031.9.1.9="emuser" E:1031.9.1.10="20240502092339" E:1031.9.1.11="Ended not OK" E:1031.9.1.12="root" E:1031.9.1.13="KK" E:1031.9.1.14="KK" E:1031.9.1.15="JOB_FALLO9" E:1031.9.1.16="controlm921" E:1031.9.1.17="R" E:1031.9.1.18="" E:1031.9.1.19="" E:1031.9.1.20="2"09:23:50.497215 IP 192.168.1.119.46133 > agente.snmp-trap:  C="Public" Trap(454)  E:1031.9.1 192.168.1.119 enterpriseSpecific s=10 0 E:1031.9.1.1="U" E:1031.9.1.2="76" E:1031.9.1.3="controlm921" E:1031.9.1.4="" E:1031.9.1.5="00088" E:1031.9.1.6="V" E:1031.9.1.7="Handled" E:1031.9.1.8="20240426173800" E:1031.9.1.9="emuser" E:1031.9.1.10="20240502092350" E:1031.9.1.11="Ended not OK" E:1031.9.1.12="root" E:1031.9.1.13="KK" E:1031.9.1.14="KK" E:1031.9.1.15="JOB_FALLO6" E:1031.9.1.16="controlm921" E:1031.9.1.17="R" E:1031.9.1.18="" E:1031.9.1.19="" E:1031.9.1.20="1"[/HTML]
[COLOR=#0C0D0E][FONT=-apple-system]When traps are sent from the application , my snmptrapd doesn't process it and does not write anything to /tmp/log.txt[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]I sent few test traps from localhost itself and it is completely working as expected. 
Ahy help please?

[/FONT][/COLOR]

---

### Post by ajgreeny on 2024-05-02
Moved to **Server platforms** which is more appropriate.

---

