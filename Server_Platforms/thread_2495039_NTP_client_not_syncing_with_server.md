---
title: "NTP client not syncing with server"
date: 2024-02-05
forum: Server Platforms
---

### Post by godatum2 on 2024-02-05
I have a Ubuntu server running NTP. This seems to be working OK

```
[FONT=Arial]sudo ntpq -npcrv[/FONT]
[FONT=Arial]     remote           refid      st t when poll reach   delay   offset [/FONT]
[FONT=Arial]jitter[/FONT]
[FONT=Arial]==============================[/FONT][FONT=Arial]==============================[/FONT][FONT=Arial]==================[/FONT]
[FONT=Arial]*216.239.35.0    .GOOG.           1 u  302 1024  377   16.475    0.523  [/FONT]
[FONT=Arial]0.256[/FONT]
[FONT=Arial]+216.239.35.4    .GOOG.           1 u  793 1024  377   20.461    1.155  [/FONT]
[FONT=Arial]1.203[/FONT]
[FONT=Arial]+216.239.35.8    .GOOG.           1 u  140 1024  377   21.860    1.204  [/FONT]
[FONT=Arial]0.587[/FONT]
[FONT=Arial]-216.239.35.12   .GOOG.           1 u  971 1024  377   19.215   -0.035  [/FONT]
[FONT=Arial]2.464[/FONT]
[FONT=Arial]associd=0 status=0615 leap_none, sync_ntp, 1 event, clock_sync, [/FONT][FONT=Arial]leap=00, stratum=2,[/FONT]
[FONT=Arial]precision=-23, rootdelay=16.475, rootdisp=29.552, refid=216.239.35.0,[/FONT]
[FONT=Arial]reftime=e96b46fd.e6fd1f35  Mon, Feb  5 2024 11:37:33.902,[/FONT]
[FONT=Arial]clock=e96b482c.941f5352  Mon, Feb  5 2024 11:42:36.578, peer=33036,[/FONT]
[FONT=Arial]tc=10, mintc=3, offset=0.834, frequency=22.740, sys_jitter=0.522,[/FONT]
[FONT=Arial]clk_jitter=0.358, clk_wander=0.047[/FONT]
```

On my Ubuntu client the time is not syncing as shown my the leap_alarm state. The time was about 10 mins out, so I manually adjusted it and restarted the ntp service. But it's still showing as leap_alarm.

```
[FONT=Arial]ntpq -npcrv[/FONT]
[FONT=Arial]     remote           refid      st t when poll reach   delay   offset [/FONT]
[FONT=Arial]jitter[/FONT]
[FONT=Arial]==============================[/FONT][FONT=Arial]==============================[/FONT][FONT=Arial]==================[/FONT]
[FONT=Arial] srv1.company.loc .POOL.          16 p    -   64    0    0.000    0.000  [/FONT]
[FONT=Arial]0.000[/FONT]
[FONT=Arial]associd=0 status=c016 leap_alarm, sync_unspec, 1 event, restart, [/FONT][FONT=Arial]leap=11,[/FONT]
[FONT=Arial]stratum=16, precision=-24, rootdelay=0.000, rootdisp=3.795, refid=INIT,[/FONT]
[FONT=Arial]reftime=00000000.00000000  Thu, Feb  7 2036  6:28:16.000,[/FONT]
[FONT=Arial]clock=e96b4843.14967997  Mon, Feb  5 2024 11:42:59.080, peer=0, tc=3,[/FONT]
[FONT=Arial]mintc=3, offset=0.000000, frequency=4.418, sys_jitter=0.000000,[/FONT]
[FONT=Arial]clk_jitter=0.000, clk_wander=0.000[/FONT]
```

```
[FONT=Arial] sudo ntpdate -q srv1.company.local[/FONT]
[FONT=Arial]server 10.1.0.1, stratum 2, offset -0.193649, delay 0.04465[/FONT]
[FONT=Arial] 5 Feb 11:45:17 ntpdate[12231]: adjust time server IP offset[/FONT]
[FONT=Arial]-0.193649 sec[/FONT]
```

Running:
```

sudo service ntp stop
sudo ntpdate srv1.company.local
        5 Feb 12:05:14 ntpdate[13086]: adjust time server IP offset -0.193957 sec
sudo service ntp start

```

---

### Post by MAFoElffen on 2024-02-05
You missed providing some information that would help with this...

Do you have firewall rules to allow the NTP updates through from NTP client to NTP server?
```

sudo ufw allow from any to any port 123 proto udp

```
In the hosts file of the clients, did you specify the IP and hostname of the NTP server in their hosts file? Or do you have verified local DNS resolv?

Did you disable the systemd timesyncd service on the NTP client so that it doesn't fight and conflict with NTP client?

Did you configure the /etc/ntp.conf file to add your NTP server as the new time server by adding a line
```

server <NTP-server-name> prefer iburst

```
Substituting the name with what the NTP host is?

Did you restart the NTP services on the clients and host to pick up any changes?

---

### Post by TheFu on 2024-02-05
Isn't NTP deprecated for security issues?  Not that it is any better, but I switched to Chrony a few years ago.  Don't forget to disable/purse systemd-timed.

[https://www.ntpsec.org/](https://www.ntpsec.org/) has some specific hardware sync clocks available too. Most tie into GPS hardware, since GPS provided very accurate time anywhere on Earth.

---

### Post by godatum2 on 2024-02-06
The firewall is allowing UDP 123.

I can resolve DNS for srv1.company.local using nslookup.

Output of timedatectl:
```
[FONT=Arial]      
Local time: Tue 2024-02-06 10:55:42 GMT[/FONT]
[FONT=Arial]Universal time: Tue 2024-02-06 10:55:42 UTC[/FONT]
[FONT=Arial]RTC time: Tue 2024-02-06 10:55:42[/FONT]
[FONT=Arial]Time zone: Europe/London (GMT, +0000)[/FONT]
[FONT=Arial] Network time on: yes[/FONT]
[FONT=Arial]NTP synchronized: no[/FONT]
[FONT=Arial] RTC in local TZ: no[/FONT]
```


Contents of [COLOR=#000000]/etc/ntp.conf:
[/COLOR]```
[FONT=Arial]driftfile /var/lib/ntp/ntp.drift[/FONT]
[FONT=Arial]
pool srv1.company.local[/FONT]

[FONT=Arial]# by default act only as a basic NTP client[/FONT]
[FONT=Arial]restrict -4 default nomodify nopeer noquery notrap[/FONT]
[FONT=Arial]restrict -6 default nomodify nopeer noquery notrap[/FONT]

[FONT=Arial]# Local users may interrogate the ntp server more closely.[/FONT]
[FONT=Arial]restrict 127.0.0.1[/FONT]
[FONT=Arial]restrict ::1
[/FONT]
```[COLOR=#000000]

I did restart the NTP service on the srv1.company.local host and client.

On the host running [/COLOR]**[COLOR=#000000]sudo ss -lu[/COLOR]**[COLOR=#000000]:
[/COLOR]```
State               Recv-Q              Send-Q                           Local Address:Port                             Peer Address:Port             Process

UNCONN              0                   0                                   IP:NTP                                               *:*
                   

```

On the client:
```

sudo nmap -sU srv1.company.local

PORT       STATE    SERVICE
123/udp  open     ntp

```

---

### Post by SeijiSensei on 2024-02-06
Have you run ntpdate with the -v switch enabled?

---

### Post by godatum2 on 2024-02-07
> **SeijiSensei said:**
> Have you run ntpdate with the -v switch enabled?

I get an error:

```
no servers can be used, exiting
```

---

