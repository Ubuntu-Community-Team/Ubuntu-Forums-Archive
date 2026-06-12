---
title: "Issues after the  upgrade Ubuntu from 17.10 to 18.04"
date: 2018-04-29
forum: Server Platforms
---

### Post by bern1 on 2018-04-29
Hi, 
My home router based on Ubuntu server stops working after upgrade to 18.04. 
I indentified two issues:
1. unbound
Unbound service doesn't work after upgrade (worked fine with 17.10).
```

ela@akacja:~$ sudo systemctl status unbound
&#9679; unbound.service - Unbound DNS server
   Loaded: loaded (/lib/systemd/system/unbound.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sun 2018-04-29 16:04:16 CEST; 3min 33s ago
     Docs: man:unbound(8)
  Process: 2275 ExecStart=/usr/sbin/unbound -d $DAEMON_OPTS (code=exited, status=1/FAILURE)
  Process: 2200 ExecStartPre=/usr/lib/unbound/package-helper root_trust_anchor_update (code=exited,
  Process: 2188 ExecStartPre=/usr/lib/unbound/package-helper chroot_setup (code=exited, status=0/SUC
 Main PID: 2275 (code=exited, status=1/FAILURE)

Apr 29 16:04:16 akacja systemd[1]: unbound.service: Service hold-off time over, scheduling restart.
Apr 29 16:04:16 akacja systemd[1]: unbound.service: Scheduled restart job, restart counter is at 5.
Apr 29 16:04:16 akacja systemd[1]: Stopped Unbound DNS server.
Apr 29 16:04:16 akacja systemd[1]: unbound.service: Start request repeated too quickly.
Apr 29 16:04:16 akacja systemd[1]: unbound.service: Failed with result 'exit-code'.
Apr 29 16:04:16 akacja systemd[1]: Failed to start Unbound DNS server.
lines 1-15/15 (END)
```
unbound.conf:
```
#
# The full documentation is available at:
# https://www.unbound.net/documentation/unbound.conf.html
#

server:
     # Common Server Options
     chroot: ""
     directory: "/etc/unbound"
    # username: "nobody"
     port: 53
     do-ip4: yes
     do-ip6: no
     do-udp: yes
     do-tcp: yes
     so-reuseport: yes
     do-not-query-localhost: yes

     # System Tuning
     num-threads: 1
    so-reuseport: yes
    infra-cache-slabs: 1
    key-cache-slabs: 1
    msg-cache-slabs: 1
    rrset-cache-slabs: 1
    rrset-cache-size: 64m
    msg-cache-size: 32m
    key-cache-size: 32m
    outgoing-range: 8192
    num-queries-per-thread: 4096
    so-sndbuf: 4m
    so-rcvbuf: 4m

     # Logging Options
     verbosity: 1
     use-syslog: yes
     log-time-ascii: yes
     log-queries: no

     # Unbound Statistics
     statistics-interval: 0
     statistics-cumulative: yes
     extended-statistics: yes

     # Prefetching
     prefetch: yes
     prefetch-key: yes

     # Randomise any cached responses
     rrset-roundrobin: yes

     # Privacy Options
     hide-identity: yes
     hide-version: yes
     qname-minimisation: yes
     minimal-responses: yes

     # DNSSEC
     auto-trust-anchor-file: "/var/lib/unbound/root.key"
     val-permissive-mode: no
     val-clean-additional: yes
     val-log-level: 1

     # Hardening Options
     harden-glue: yes
     harden-short-bufsize: no
     harden-large-queries: yes
     harden-dnssec-stripped: yes
     harden-below-nxdomain: yes
     harden-referral-path: yes
     harden-algo-downgrade: no
     use-caps-for-id: no

     # Listen on all interfaces
     interface-automatic: yes
     interface: 0.0.0.0

     # Allow access from everywhere
     access-control: 0.0.0.0/0 allow

     # Bootstrap root servers
     root-hints: "/usr/share/dns/root.hints"

     # Include DHCP leases
     #include: "/etc/unbound/dhcp-leases.conf"

     # Include any forward zones
     #include: "/etc/unbound/forward.conf"

remote-control:
     control-enable: yes
     control-use-cert: yes
     control-interface: 127.0.0.1
     server-key-file: "/etc/unbound/unbound_server.key"
     server-cert-file: "/etc/unbound/unbound_server.pem"
     control-key-file: "/etc/unbound/unbound_control.key"
     control-cert-file: "/etc/unbound/unbound_control.pem"

# Import any local configurations
#include: "/etc/unbound/local.d/*.conf"
```

2. Not assign IP addresses to wifi network interface 'wlp4s0'. 
Netplan configuration as below worked fine with 17.10 (but not 18.04)
```
network:
  version: 2
  renderer: networkd
  ethernets:
    wlp4s0:
      addresses:
       - 10.10.11.1/24
      dhcp4: no
```
Not assigning wifi IP address block my firerwall - Shorewall:
```
ela@akacja:~$ sudo systemctl status shorewall
&#9679; shorewall.service - Shorewall IPv4 firewall
   Loaded: loaded (/lib/systemd/system/shorewall.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sun 2018-04-29 16:04:15 CEST; 36min ago
  Process: 1152 ExecStart=/sbin/shorewall $OPTIONS start $STARTOPTIONS (code=exited, status=143)
 Main PID: 1152 (code=exited, status=143)

Apr 29 16:04:15 akacja shorewall[1152]: Generating Rule Matrix...
Apr 29 16:04:15 akacja shorewall[1152]: Creating iptables-restore input...
Apr 29 16:04:15 akacja shorewall[1152]: Shorewall configuration compiled to /var/lib/shorewall/.star
Apr 29 16:04:15 akacja shorewall[1152]: Starting Shorewall....
Apr 29 16:04:15 akacja shorewall[1152]:    ERROR: Unable to determine the IP address(es) of wlp4s0:
Apr 29 16:04:15 akacja root[2148]: ERROR:Shorewall start failed:Firewall state not changed
Apr 29 16:04:15 akacja shorewall[1152]: Terminated
Apr 29 16:04:15 akacja systemd[1]: shorewall.service: Main process exited, code=exited, status=143/n
Apr 29 16:04:15 akacja systemd[1]: shorewall.service: Failed with result 'exit-code'.
Apr 29 16:04:15 akacja systemd[1]: Failed to start Shorewall IPv4 firewall.


```
Maybe launching service order need to be changed?

See networks configuration report :
[URL="http://paste.ubuntu.com/p/pYgDZ3MSgy/"]http://paste.ubuntu.com/p/pYgDZ3MSgy/
[/URL]
How could I fix these issues. 
TIA,

---

### Post by bern1 on 2018-05-02
Issue no1 - Unbound hopefully resolved. 
The cause of the Unbound issue was systemd-resolved service wchich was activated after upgrade and block Unbound. 
Stop and disable systemd-resolved service back Unbound into the life. 

So issue no2 'not assigned wifi IP addreses' (mentioned in the first post) still remains. 
I use Atheros WIFI mpcie card in the ACCESS Point Mode. So I use hostapd.
I've checked that after Ubuntu apgrade hostapd doesn't start
```
ela@akacja:~$ sudo systemctl status hostapd
â hostapd.service
   Loaded: masked (/dev/null; bad)
   Active: inactive (dead)
```

I have wifi network interface defined in  /etc/netplan/03-netcfg.yaml as:
```
network:
  version: 2
  renderer: networkd
  ethernets:
    wlp4s0:
      addresses:
       - 10.10.11.1/24
      dhcp4: no
```
and isc-dhcp-serwer in /etc/dhcp/dhcpd.conf (the fragment):
```
# WLAN
subnet 10.10.11.0 netmask 255.255.255.0 {
    range 10.10.11.10 10.10.11.50;
    option routers 10.10.11.1;
    option broadcast-address 10.10.11.255;
    option domain-name-servers 10.10.11.1;
    option ntp-servers 10.10.11.1;
    option netbios-name-servers 10.10.11.1;
    option netbios-node-type 2;
    default-lease-time 600;
    max-lease-time 7200;
    }

```

MY /etc/hostapd/hostapd.conf is as follow:
```
driver=nl80211
######################### basic hostapd configuration ##########################
#
interface=wlp4s0
country_code=PL
ieee80211d=1
ieee80211h=1
channel=2
hw_mode=g
ieee80211n=1
wmm_enabled=1
ht_capab=[LDPC][HT40+][SHORT-GI-20][SHORT-GI-40][TX-STBC][RX-STBC1][DSSS_CCK-40]
logger_syslog=-1
logger_syslog_level=0
logger_stdout=-1
logger_stdout_level=4
#dump_file=/tmp/hostapd.dump
auth_algs=1
ctrl_interface=/var/run/hostapd
ctrl_interface_group=0
ssid=Fire
ignore_broadcast_ssid=0
######################### wpa hostapd configuration ############################
#
wpa=3
wpa_passphrase=******
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP

```

Before the upgreade it worked. Currently when I mannually run hostapd I have:
```
ela@akacja:~$ sudo hostapd  /etc/hostapd/hostapd.conf
Configuration file: /etc/hostapd/hostapd.conf
wlp4s0: interface state UNINITIALIZED->COUNTRY_UPDATE
wlp4s0: interface state COUNTRY_UPDATE->HT_SCAN
20/40 MHz operation not permitted on channel pri=2 sec=9 based on overlapping BSSes
Using interface wlp4s0 with hwaddr 18:f4:6a:30:ae:50 and ssid "Fire"
wlp4s0: interface state HT_SCAN->ENABLED
wlp4s0: AP-ENABLED
wlp4s0: AP-STA-CONNECTED 24:92:0e:cc:d8:cc
wlp4s0: AP-STA-DISCONNECTED 24:92:0e:cc:d8:cc
wlp4s0: AP-STA-CONNECTED 34:23:ba:c4:3c:78
wlp4s0: AP-STA-DISCONNECTED 34:23:ba:c4:3c:78
wlp4s0: AP-STA-CONNECTED 34:23:ba:c4:3c:78
wlp4s0: AP-STA-DISCONNECTED 34:23:ba:c4:3c:78
^Cwlp4s0: interface state ENABLED->DISABLED
wlp4s0: AP-DISABLED
nl80211: deinit ifname=wlp4s0 disabled_11b_rates=0
```
But none client can connect to WIFI network
How could I diagnose what is wrong with my WIFI AP after Ubuntu upgrade?
TIA, 
B

---

### Post by bern1 on 2018-05-03
Hi, 
I'm still fighting over the restoration of WIFI Access Point. ;-)
I completely removed hostapd and installed from the beginning and start hostapd service.
Strange: testing wifi client (win7 x64 Laptop) shows me connection established an excellent signal quality but serer not assigned IP address to the client. I expected for example: 10.10.11.12 but ip address is empty..
 The syslog shows me:
```
ela@akacja:~$ sudo grep -i hostapd /var/log/syslog
May  3 15:37:14 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 MLME: MLME-DEAUTHENTICATE.indication(e0:b9:a5:34:57:83, 1)
May  3 15:37:14 akacja kernel: [25125.820702] netlink: 'hostapd': attribute type 213 has an invalid length.
May  3 15:37:15 akacja hostapd[4967]: Configuration file: /etc/hostapd/hostapd.conf
May  3 15:37:15 akacja hostapd[4967]: wlp4s0: interface state UNINITIALIZED->COUNTRY_UPDATE
May  3 15:37:15 akacja hostapd[4967]: wlp4s0: interface state COUNTRY_UPDATE->HT_SCAN
May  3 15:37:16 akacja kernel: [25127.141236] netlink: 'hostapd': attribute type 213 has an invalid length.
May  3 15:37:17 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 IEEE 802.11: authentication OK (open system)
May  3 15:37:17 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 MLME: MLME-AUTHENTICATE.indication(e0:b9:a5:34:57:83, OPEN_SYSTEM)
May  3 15:37:17 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 MLME: MLME-DELETEKEYS.request(e0:b9:a5:34:57:83)
May  3 15:37:17 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 IEEE 802.11: authenticated
May  3 15:37:17 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 IEEE 802.11: association OK (aid 1)
May  3 15:37:17 akacja kernel: [25127.854345] netlink: 'hostapd': attribute type 213 has an invalid length.
May  3 15:37:17 akacja kernel: [25127.854484] netlink: 'hostapd': attribute type 213 has an invalid length.
May  3 15:37:17 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 IEEE 802.11: associated (aid 1)
May  3 15:37:17 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 MLME: MLME-REASSOCIATE.indication(e0:b9:a5:34:57:83)
May  3 15:37:17 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 MLME: MLME-DELETEKEYS.request(e0:b9:a5:34:57:83)
May  3 15:37:17 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 IEEE 802.11: binding station to interface 'wlp4s0'
May  3 15:37:17 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 WPA: event 1 notification
May  3 15:37:17 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 WPA: start authentication
May  3 15:37:17 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 IEEE 802.1X: unauthorizing port
May  3 15:37:17 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 WPA: sending 1/4 msg of 4-Way Handshake
May  3 15:37:17 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 WPA: received EAPOL-Key frame (2/4 Pairwise)
May  3 15:37:17 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 WPA: sending 3/4 msg of 4-Way Handshake
May  3 15:37:17 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 WPA: received EAPOL-Key frame (4/4 Pairwise)
May  3 15:37:17 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 IEEE 802.1X: authorizing port
May  3 15:37:17 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 RADIUS: starting accounting session 6C790EA035AA9B1A
May  3 15:37:17 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 WPA: pairwise key handshake completed (RSN)
May  3 15:47:16 akacja hostapd: wlp4s0: WPA rekeying GTK
May  3 15:47:16 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 WPA: sending 1/2 msg of Group Key Handshake
May  3 15:47:16 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 WPA: received EAPOL-Key frame (2/2 Group)
May  3 15:47:16 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 WPA: group key handshake completed (RSN)
May  3 15:57:16 akacja hostapd: wlp4s0: WPA rekeying GTK
May  3 15:57:16 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 WPA: sending 1/2 msg of Group Key Handshake
May  3 15:57:16 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 WPA: EAPOL-Key timeout
May  3 15:57:16 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 WPA: sending 1/2 msg of Group Key Handshake
May  3 15:57:17 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 WPA: received EAPOL-Key frame (2/2 Group)
May  3 15:57:17 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 WPA: group key handshake completed (RSN)
May  3 15:57:17 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 WPA: received EAPOL-Key 2/2 Group with unexpected replay counter
May  3 16:07:16 akacja hostapd: wlp4s0: WPA rekeying GTK
May  3 16:07:16 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 WPA: sending 1/2 msg of Group Key Handshake
May  3 16:07:16 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 WPA: EAPOL-Key timeout
May  3 16:07:16 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 WPA: sending 1/2 msg of Group Key Handshake
May  3 16:07:17 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 WPA: received EAPOL-Key frame (2/2 Group)
May  3 16:07:17 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 WPA: group key handshake completed (RSN)
May  3 16:07:17 akacja hostapd: wlp4s0: STA e0:b9:a5:34:57:83 WPA: received EAPOL-Key 2/2 Group with unexpected replay counter
```
What does ```
netlink: 'hostapd': attribute type 213 has an invalid length.
```mean?
Maybe this block wifi AP?
Regards, 
B

---

### Post by 1toulibre on 2018-12-28
Hello , found nothing to make it work with hostapd but only installed dnsmasq without any adjustments then was able to create normally a hotspot working good without staying stucked by seeking ip adress

Hope it'll help

Still getting nearly the same message 

netlink: 'wpa_supplicant': attribute type 213 has an invalid length 

but no worry at all

Best regards from Ubuntu Forums France

---

