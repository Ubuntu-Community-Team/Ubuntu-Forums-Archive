---
title: "need bandwith monitor"
date: 2006-06-12
forum: Server Platforms
---

### Post by mrweirdo on 2006-06-12
not sure if this is the best place but since I'm runing ubuntu server with just the base install an no gui I'm posting it here. Does anyone know of a good bandwith monitor? basicaly what I want to be able to do is monitor my montly bandwith usage in gigabytes on the external nic eth0. preferably in a shell or a nice webpage printout runing on the apache server.

---

### Post by MonkeyNet on 2006-06-12
[QUOTE=mrweirdo]not sure if this is the best place but since I'm runing ubuntu server with just the base install an no gui I'm posting it here. Does anyone know of a good bandwith monitor? basicaly what I want to be able to do is monitor my montly bandwith usage in gigabytes on the external nic eth0. preferably in a shell or a nice webpage printout runing on the apache server.[/QUOTE]

MRTG would be a good bet for you. You can configure it to watch traffic on the Ethernet Interface. You can also set it up to graph CPU, Memory Usage, etc.

You may need to enable multiverse and universe repositories in order to d/l it using Syanptics but someone else might be able to better confirm this.

If you are not new to linux and apache you can d/l and compile it yourself from the mrtg site, [http://oss.oetiker.ch/mrtg/](http://oss.oetiker.ch/mrtg/)

It's fairly well documented with examples for configuration.

Cheers

---

### Post by mrweirdo on 2006-06-12
thanks i will look into it. I allready found something called cactus however it seems the documentation is lacking and I cant seem to figure out to get it how to monitor my device. So hopefully MRTG will work beter :)

---

### Post by mrcowcow on 2006-06-12
It looks like munin will do what you want. There is a tutorial on how to set it up [here.]("http://www.howtoforge.com/server_monitoring_monit_munin")

---

### Post by MonkeyNet on 2006-06-12
[QUOTE=mrcowcow]It looks like munin will do what you want. There is a tutorial on how to set it up [here.]("http://www.howtoforge.com/server_monitoring_monit_munin")[/QUOTE]

Munin looks to be heavily derived from MRTG. Although it does look a little easier to setup. When i've got a chance, might do a howto on setting up MRTG with ubuntu for anyone who is interested

---

### Post by mrcowcow on 2006-06-13
[QUOTE=MonkeyNet]Munin looks to be heavily derived from MRTG. Although it does look a little easier to setup. When i've got a chance, might do a howto on setting up MRTG with ubuntu for anyone who is interested[/QUOTE]
I would be interested in that. Munin is not avaible from packages.ubuntu.com, so it will be a bit harder to set up then the tutorial I posted suggests. But MRTG may be better for doing this anyway.

---

### Post by mrweirdo on 2006-06-14
to be truthfull I was looking for something more along the lines of something that uses iptables loging. I used to use ipcop and it has an addon called Net Traffic that did that.

---

### Post by DanielArdelian on 2006-06-14
ipac-ng works smoothly for me and is also available in the repositories (probably Universe, don't remember for sure). Its based on iptables and can give you a lot of traffic / time statistics

---

### Post by mrweirdo on 2006-06-14
[QUOTE=DanielArdelian]ipac-ng works smoothly for me and is also available in the repositories (probably Universe, don't remember for sure). Its based on iptables and can give you a lot of traffic / time statistics[/QUOTE]

ah that makes since then what the ipac rules are for in ipcops iptables listings when i viewed them :D weird.

now to integrate this into my iptables. I have a shell script that runs whenever ubuntu boots  that inputs the rules into the firewall. My guess this is not the best method and I should make them perminent. Anyone know how I might go about doing that via the shell prompt?

---

### Post by DanielArdelian on 2006-06-14
Run the shell script from /etc/rc.local
There is no way to make the rules "persistent", iptables always start with a clean set of rules on boot, they have no memory.

The best way would be to create your own /etc/init.d/iptables script and activate that with update-rc.d to be executed at specific runlevels with a specific priority, but that would probably be overkill. You could take a look at /etc/init.d/skeleton to see how this could be done.

---

### Post by mrweirdo on 2006-06-14
ok well I put it in /etc/init.d/iptables so it looks like Im good :) thnx :)

---

### Post by DanielArdelian on 2006-06-14
You do know you have to add SNNiptables and KNNiptables symlinks to /etc/init.d/iptables from the appropriate /etc/rc.XX directories, and the script MUST know how to handle the "start" / "stop" / "restart" command line parameters, don't you ? :D

Personally I don't know what values to suggest for NN and XX, not at my computer right now, but IMHO the script should be started after networking has been brought up by init...

For starters, you could try:
```

  update-rc.d  iptables  defaults

```

to create the symlinks.

For details, see the man page of update-rc.d

---

### Post by LordMerlin on 2006-07-09
Hi

I'm also looking for a simple way of see what goes through my router, both in and out. I have had a look @ MRTG and Cacti, but can't seem to grasp the technical documentations written for the more technically challenged.

I installed mrtg, mrtg-utils and SNMP from aptitude (This is on Ubuntu 5.10), and tried to setup the config file, but it seems I'd need to learn SNMP as well just to use it. Unfortunattely I don't have the time now to learn both MRTG & SNMP. What can I do to see who's using so much bandwidth on our LAN?

I have an ADSL router, with one end connected to the ADSL line, getting an IP from my ISP. The other port (which is 192.168.0.1) connects to my Ubuntu server, on 192.168.0.2. Then I have another NIC 192.168.10.1, which connects to the internet LAN via a 24 port hub.

This is the output from cfgmaker:

```
cfgmaker public@192.168.0.2 --global "WorkDir: /var/www/mrtg/" --output server.cfg
--base: Get Device Info on public@192.168.0.2:
SNMP Error:
Received SNMP response with error code
  error status: noSuchName
  index 1 (OID: 1.3.6.1.2.1.1.9.1.4.9)
SNMPv1_Session (remote host: "192.168.0.2" [192.168.0.2].161)
                  community: "public"
                 request ID: 1189127895
                PDU bufsize: 8000 bytes
                    timeout: 2s
                    retries: 5
                    backoff: 1)
 at /usr/share/perl5/SNMP_util.pm line 733
--base: Vendor Id:
--base: Populating confcache
--coca: populate confcache public@192.168.0.2:
--coca: Skipping ifName scanning because public@192.168.0.2: does not seem to support it
--coca: Skipping ifDescr scanning because public@192.168.0.2: does not seem to support it
--coca: Skipping ifType scanning because public@192.168.0.2: does not seem to support it
--coca: Skipping ipAdEntIfIndex scanning because public@192.168.0.2: does not seem to support it
--coca: Skipping ifPhysAddress scanning because public@192.168.0.2: does not seem to support it
--base: Get Interface Info
--base: Walking ifIndex
SNMP Error:
Received SNMP response with error code
  error status: noSuchName
  index 1 (OID: 1.3.6.1.2.1.2.2.1.1)
SNMPv1_Session (remote host: "192.168.0.2" [192.168.0.2].161)
                  community: "public"
                 request ID: 1189127901
                PDU bufsize: 8000 bytes
                    timeout: 2s
                    retries: 5
                    backoff: 1)
 at /usr/share/perl5/SNMP_util.pm line 627
SNMPWALK Problem for 1.3.6.1.2.1.2.2.1.1 on public@192.168.0.2::::::v4only
 at /usr/bin/cfgmaker line 144
--base: Walking ifType
SNMP Error:
Received SNMP response with error code
  error status: noSuchName
  index 1 (OID: 1.3.6.1.2.1.2.2.1.3)
SNMPv1_Session (remote host: "192.168.0.2" [192.168.0.2].161)
                  community: "public"
                 request ID: 1189127902
                PDU bufsize: 8000 bytes
                    timeout: 2s
                    retries: 5
                    backoff: 1)
 at /usr/share/perl5/SNMP_util.pm line 627
SNMPWALK Problem for 1.3.6.1.2.1.2.2.1.3 on public@192.168.0.2::::::v4only
 at /usr/bin/cfgmaker line 144
--base: Walking ifAdminStatus
SNMP Error:
Received SNMP response with error code
  error status: noSuchName
  index 1 (OID: 1.3.6.1.2.1.2.2.1.7)
SNMPv1_Session (remote host: "192.168.0.2" [192.168.0.2].161)
                  community: "public"
                 request ID: 1189127903
                PDU bufsize: 8000 bytes
                    timeout: 2s
                    retries: 5
                    backoff: 1)
 at /usr/share/perl5/SNMP_util.pm line 627
SNMPWALK Problem for 1.3.6.1.2.1.2.2.1.7 on public@192.168.0.2::::::v4only
 at /usr/bin/cfgmaker line 144
--base: Walking ifOperStatus
SNMP Error:
Received SNMP response with error code
  error status: noSuchName
  index 1 (OID: 1.3.6.1.2.1.2.2.1.8)
SNMPv1_Session (remote host: "192.168.0.2" [192.168.0.2].161)
                  community: "public"
                 request ID: 1189127904
                PDU bufsize: 8000 bytes
                    timeout: 2s
                    retries: 5
                    backoff: 1)
 at /usr/share/perl5/SNMP_util.pm line 627
SNMPWALK Problem for 1.3.6.1.2.1.2.2.1.8 on public@192.168.0.2::::::v4only
 at /usr/bin/cfgmaker line 144
--base: Walking ifMtu
SNMP Error:
Received SNMP response with error code
  error status: noSuchName
  index 1 (OID: 1.3.6.1.2.1.2.2.1.4)
SNMPv1_Session (remote host: "192.168.0.2" [192.168.0.2].161)
                  community: "public"
                 request ID: 1189127905
                PDU bufsize: 8000 bytes
                    timeout: 2s
                    retries: 5
                    backoff: 1)
 at /usr/share/perl5/SNMP_util.pm line 627
SNMPWALK Problem for 1.3.6.1.2.1.2.2.1.4 on public@192.168.0.2::::::v4only
 at /usr/bin/cfgmaker line 144
--base: Walking ifSpeed
SNMP Error:
Received SNMP response with error code
  error status: noSuchName
  index 1 (OID: 1.3.6.1.2.1.2.2.1.5)
SNMPv1_Session (remote host: "192.168.0.2" [192.168.0.2].161)
                  community: "public"
                 request ID: 1189127906
                PDU bufsize: 8000 bytes
                    timeout: 2s
                    retries: 5
                    backoff: 1)
 at /usr/share/perl5/SNMP_util.pm line 627
SNMPWALK Problem for 1.3.6.1.2.1.2.2.1.5 on public@192.168.0.2::::::v4only
 at /usr/bin/cfgmaker line 183
--base: Writing server.cfg
root@Gimbli:~#

```

Can someone please help me?

---

### Post by LordMerlin on 2006-07-09
> **MonkeyNet said:**
> Munin looks to be heavily derived from MRTG. Although it does look a little easier to setup. When i've got a chance, might do a howto on setting up MRTG with ubuntu for anyone who is interested

Hi 

Have you made a Munin HOWTO yet? Or can you give me some pointers on how to get it to work on Ubuntu 5.10 with two NIC's - 192.168.0.2 connected to the ADSL router, and 192.168.10.1 connected to a 24 port HUB for the internal LAN

I tried MRTG, but fail when I need to write the config script:


 I'm also looking for a simple way of see what goes through my router, both in and out. I have had a look @ MRTG and Cacti, but can't seem to grasp the technical documentations written for the more technically challenged.
 
 I installed mrtg, mrtg-utils and SNMP from aptitude 
 
 This is the output from cfgmaker:
 
 ```
cfgmaker public@192.168.0.2 --global "WorkDir: /var/www/mrtg/" --output server.cfg
 --base: Get Device Info on public@192.168.0.2:
 SNMP Error:
 Received SNMP response with error code
   error status: noSuchName
   index 1 (OID: 1.3.6.1.2.1.1.9.1.4.9)
 SNMPv1_Session (remote host: "192.168.0.2" [192.168.0.2].161)
                   community: "public"
                  request ID: 1189127895
                 PDU bufsize: 8000 bytes
                     timeout: 2s
                     retries: 5
                     backoff: 1)
  at /usr/share/perl5/SNMP_util.pm line 733
 --base: Vendor Id:
 --base: Populating confcache
 --coca: populate confcache public@192.168.0.2:
 --coca: Skipping ifName scanning because public@192.168.0.2: does not seem to support it
 --coca: Skipping ifDescr scanning because public@192.168.0.2: does not seem to support it
 --coca: Skipping ifType scanning because public@192.168.0.2: does not seem to support it
 --coca: Skipping ipAdEntIfIndex scanning because public@192.168.0.2: does not seem to support it
 --coca: Skipping ifPhysAddress scanning because public@192.168.0.2: does not seem to support it
 --base: Get Interface Info
 --base: Walking ifIndex
 SNMP Error:
 Received SNMP response with error code
   error status: noSuchName
   index 1 (OID: 1.3.6.1.2.1.2.2.1.1)
 SNMPv1_Session (remote host: "192.168.0.2" [192.168.0.2].161)
                   community: "public"
                  request ID: 1189127901
                 PDU bufsize: 8000 bytes
                     timeout: 2s
                     retries: 5
                     backoff: 1)
  at /usr/share/perl5/SNMP_util.pm line 627
 SNMPWALK Problem for 1.3.6.1.2.1.2.2.1.1 on public@192.168.0.2::::::v4only
  at /usr/bin/cfgmaker line 144
 --base: Walking ifType
 SNMP Error:
 Received SNMP response with error code
   error status: noSuchName
   index 1 (OID: 1.3.6.1.2.1.2.2.1.3)
 SNMPv1_Session (remote host: "192.168.0.2" [192.168.0.2].161)
                   community: "public"
                  request ID: 1189127902
                 PDU bufsize: 8000 bytes
                     timeout: 2s
                     retries: 5
                     backoff: 1)
  at /usr/share/perl5/SNMP_util.pm line 627
 SNMPWALK Problem for 1.3.6.1.2.1.2.2.1.3 on public@192.168.0.2::::::v4only
  at /usr/bin/cfgmaker line 144
 --base: Walking ifAdminStatus
 SNMP Error:
 Received SNMP response with error code
   error status: noSuchName
   index 1 (OID: 1.3.6.1.2.1.2.2.1.7)
 SNMPv1_Session (remote host: "192.168.0.2" [192.168.0.2].161)
                   community: "public"
                  request ID: 1189127903
                 PDU bufsize: 8000 bytes
                     timeout: 2s
                     retries: 5
                     backoff: 1)
  at /usr/share/perl5/SNMP_util.pm line 627
 SNMPWALK Problem for 1.3.6.1.2.1.2.2.1.7 on public@192.168.0.2::::::v4only
  at /usr/bin/cfgmaker line 144
 --base: Walking ifOperStatus
 SNMP Error:
 Received SNMP response with error code
   error status: noSuchName
   index 1 (OID: 1.3.6.1.2.1.2.2.1.8)
 SNMPv1_Session (remote host: "192.168.0.2" [192.168.0.2].161)
                   community: "public"
                  request ID: 1189127904
                 PDU bufsize: 8000 bytes
                     timeout: 2s
                     retries: 5
                     backoff: 1)
  at /usr/share/perl5/SNMP_util.pm line 627
 SNMPWALK Problem for 1.3.6.1.2.1.2.2.1.8 on public@192.168.0.2::::::v4only
  at /usr/bin/cfgmaker line 144
 --base: Walking ifMtu
 SNMP Error:
 Received SNMP response with error code
   error status: noSuchName
   index 1 (OID: 1.3.6.1.2.1.2.2.1.4)
 SNMPv1_Session (remote host: "192.168.0.2" [192.168.0.2].161)
                   community: "public"
                  request ID: 1189127905
                 PDU bufsize: 8000 bytes
                     timeout: 2s
                     retries: 5
                     backoff: 1)
  at /usr/share/perl5/SNMP_util.pm line 627
 SNMPWALK Problem for 1.3.6.1.2.1.2.2.1.4 on public@192.168.0.2::::::v4only
  at /usr/bin/cfgmaker line 144
 --base: Walking ifSpeed
 SNMP Error:
 Received SNMP response with error code
   error status: noSuchName
   index 1 (OID: 1.3.6.1.2.1.2.2.1.5)
 SNMPv1_Session (remote host: "192.168.0.2" [192.168.0.2].161)
                   community: "public"
                  request ID: 1189127906
                 PDU bufsize: 8000 bytes
                     timeout: 2s
                     retries: 5
                     backoff: 1)
  at /usr/share/perl5/SNMP_util.pm line 627
 SNMPWALK Problem for 1.3.6.1.2.1.2.2.1.5 on public@192.168.0.2::::::v4only
  at /usr/bin/cfgmaker line 183
 --base: Writing server.cfg
 root@Gimbli:~#
 
```
 
 Can someone please help me?

---

