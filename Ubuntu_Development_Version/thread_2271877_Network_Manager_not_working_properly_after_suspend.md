---
title: "Network Manager not working properly after suspend"
date: 2015-04-02
forum: Ubuntu Development Version
---

### Post by enricobe on 2015-04-02
Hello,
I try to explain the problem in the easiest way I can because my english is not so perfect :) Xubuntu 15.04 kernel 4.0 RC5.

1- The wifi network works properly when I boot the PC
2- The PC goes in suspend mode after 30 mins or when I put it in suspend.
3- When I press a key the PC wakes up
4- The network doesn't work. 

There are 2 situation possibile at this time: 

case A) 
 5a- The indicator at the top-right of the screen has 2 grey arrows and don't even tries to connect to the wifi
6a- If I click on the network indicator it doesn't show my wifi network but only other wifi networks are showed.
7a- The "Enable Wifi" and "Enable Network" options are not active (grey) and can't be clicked
8a- the list of available network refreshes When I try to connect to another wifi network  and I can find my network and connect to.

case B)
5b- The indicator at the top-right of the screen has a blinking circle (it tries to connect to my network) but it never connects
6b- I click on my WiFi network from the list and it still doesn't connect
7b- I click on another Wifi network 
8b- I click again on my network and it connects

someone has the same bug? Is it a bug?

---

### Post by dino99 on 2015-04-02
looks like the xubuntu team still have some bugs around ;) is it reported ?
it could be a systemd issue, not scanning it back after a lost (or else)
is there something usefull logged after the 'suspend' mode been awaken back ?

---

### Post by enricobe on 2015-04-02
> **9d9 said:**
> looks like the xubuntu team still have some bugs around [IMG]http://ubuntuforums.org/images/smilies/icon_wink.gif[/IMG] is it reported ?
it could be a systemd issue, not scanning it back after a lost (or else)
is there something usefull logged after the 'suspend' mode been awaken back ?

Thanks 9d9 for your quick reply.

Where should I check if it's reported? On Launchpad? Can you please remember me which are the useful logs? I am lost in the hundreds of Linux's logs :)

---

### Post by Elfy on 2015-04-02
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1270257](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1270257)

looks likely as a candidate for what you're seeing

do you see the same thing with kernels that vivid has?

---

### Post by enricobe on 2015-04-02
> **Elfy said:**
> [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1270257](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1270257)

looks likely as a candidate for what you're seeing

do you see the same thing with kernels that vivid has?

Thank you, this bug looks like the one I am reporting here.

I can't check the bug on Vivid's kernels because I have [other problems]("http://ubuntuforums.org/showthread.php?t=2267816") with these kernels. I need to use the v4

---

### Post by dino99 on 2015-04-02
'sudo journalctl' will list all the booting processes; pay attention on the red lines (if any) and the white brighten lines can be of some interest too (but not critical)
the other logs are inside /var/log/ mainly syslog/dmesg (if it still exist & updated, mine is removed)

---

### Post by enricobe on 2015-04-02
I have saved some interesting lines of Journalctl. After the wake up:

(I have removed the first lines about linux-kernel and systemd and removed some digits from the Mac Address)
```

apr 02 16:47:51 enrico-linux NetworkManager[757]: <info> wake requested (sleeping: yes  enabled: yes)
apr 02 16:47:51 enrico-linux NetworkManager[757]: <info> waking up...
apr 02 16:47:51 enrico-linux NetworkManager[757]: <info> (eth0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
apr 02 16:47:51 enrico-linux NetworkManager[757]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
apr 02 16:47:51 enrico-linux NetworkManager[757]: <info> (eth0): preparing device
apr 02 16:47:51 enrico-linux NetworkManager[757]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
apr 02 16:47:51 enrico-linux kernel: r8169 0000:09:00.0 eth0: link down
apr 02 16:47:51 enrico-linux NetworkManager[757]: <info> (wlan0): preparing device
apr 02 16:47:51 enrico-linux NetworkManager[757]: <info> NetworkManager state is now DISCONNECTED
apr 02 16:47:51 enrico-linux wpa_supplicant[874]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
apr 02 16:47:51 enrico-linux wpa_supplicant[874]: dbus: Failed to construct signal
apr 02 16:47:51 enrico-linux NetworkManager[757]: <warn> could not get interface properties: No readable properties in this interface.
apr 02 16:47:51 enrico-linux NetworkManager[757]: <info> (wlan0): supplicant interface state: starting -> ready
apr 02 16:47:51 enrico-linux NetworkManager[757]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
apr 02 16:47:51 enrico-linux NetworkManager[757]: <warn> could not get interface properties: No readable properties in this interface.
apr 02 16:47:51 enrico-linux wpa_supplicant[874]: wlan0: CTRL-EVENT-SCAN-STARTED
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Auto-activating connection 'NETGEAR-06'.
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) starting connection 'NETGEAR-06'
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> NetworkManager state is now CONNECTING
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0/wireless): access point 'NETGEAR-06' has security, but secrets are required.
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> (wlan0): supplicant interface state: ready -> inactive
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0/wireless): connection 'NETGEAR-06' has security, and secrets exist.  No new secrets needed.
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Config: added 'ssid' value 'NETGEAR-06'
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Config: added 'scan_ssid' value '1'
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Config: added 'auth_alg' value 'OPEN'
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Config: added 'psk' value '<omitted>'
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Config: set interface ap_scan to 1
apr 02 16:47:52 enrico-linux systemd-journal[235]: Forwarding to syslog missed 2 messages.
apr 02 16:47:52 enrico-linux wpa_supplicant[874]: wlan0: SME: Trying to authenticate with 28:xx:xx:xx:xx:22 (SSID='NETGEAR-06' freq=2437 MHz)
apr 02 16:47:52 enrico-linux kernel: wlan0: authenticate with 28:xx:xx:xx:xx:22
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> (wlan0): supplicant interface state: inactive -> authenticating
apr 02 16:47:52 enrico-linux wpa_supplicant[874]: wlan0: Trying to associate with 28:xx:xx:xx:xx:222 (SSID='NETGEAR-06' freq=2437 MHz)
apr 02 16:47:52 enrico-linux kernel: wlan0: send auth to 28:xx:xx:xx:xx:22 (try 1/3)
apr 02 16:47:52 enrico-linux kernel: wlan0: authenticated
apr 02 16:47:52 enrico-linux kernel: rtl8723ae 0000:08:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
apr 02 16:47:52 enrico-linux kernel: rtl8723ae 0000:08:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
apr 02 16:47:52 enrico-linux kernel: wlan0: associate with 28:xx:xx:xx:xx:22 (try 1/3)
apr 02 16:47:52 enrico-linux wpa_supplicant[874]: wlan0: Associated with 28:xx:xx:xx:xx:22
apr 02 16:47:52 enrico-linux kernel: wlan0: RX AssocResp from 28:xx:xx:xx:xx:22 (capab=0x411 status=0 aid=6)
apr 02 16:47:52 enrico-linux kernel: wlan0: associated
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> (wlan0): supplicant interface state: authenticating -> associated
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
apr 02 16:47:52 enrico-linux wpa_supplicant[874]: wlan0: WPA: Key negotiation completed with 28:xx:xx:xx:xx:22 [PTK=CCMP GTK=CCMP]
apr 02 16:47:52 enrico-linux wpa_supplicant[874]: wlan0: CTRL-EVENT-CONNECTED - Connection to 28:xx:xx:xx:xx:22 completed [id=0 id_str=]
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'NETGEAR-06'.
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> dhclient started with pid 5222
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
apr 02 16:47:53 enrico-linux NetworkManager[757]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
apr 02 16:47:53 enrico-linux dhclient[5222]: DHCPREQUEST of 192.168.0.5 on wlan0 to 255.255.255.255 port 67 (xid=0x7ec96eb8)
apr 02 16:47:53 enrico-linux lightdm[834]: initctl: Impossibile connettersi a Upstart: Failed to connect to socket /com/ubuntu/upstart: Connessione rifiutata
apr 02 16:47:53 enrico-linux lightdm[5227]: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
apr 02 16:47:53 enrico-linux lightdm[5227]: PAM adding faulty module: pam_kwallet.so
apr 02 16:47:53 enrico-linux lightdm[5227]: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
apr 02 16:47:53 enrico-linux systemd[1]: Started Session c5 of user lightdm.
apr 02 16:47:53 enrico-linux systemd-logind[769]: New session c5 of user lightdm.
apr 02 16:47:53 enrico-linux systemd[1]: Starting Session c5 of user lightdm.
apr 02 16:47:53 enrico-linux lightdm[5326]: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
apr 02 16:47:53 enrico-linux lightdm[5326]: PAM adding faulty module: pam_kwallet.so
apr 02 16:47:53 enrico-linux lightdm[5326]: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "enrico"
apr 02 16:47:54 enrico-linux avahi-daemon[785]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::26fd:52ff:fe29:9c4e.
apr 02 16:47:54 enrico-linux avahi-daemon[785]: New relevant interface wlan0.IPv6 for mDNS.
apr 02 16:47:54 enrico-linux avahi-daemon[785]: Registering new address record for fe80::xxxx:xxxx:xxxx:9c4e on wlan0.*.
apr 02 16:47:56 enrico-linux kernel: radeon 0000:01:00.0: evergreen_surface_check_2d:278 texture pitch 1408 invalid must be aligned with 256
apr 02 16:47:56 enrico-linux kernel: radeon 0000:01:00.0: evergreen_cs_track_validate_texture:827 texture invalid 0x15542bc1 0x400002ff 0x060a0000 0x00000000 0x80000000 0x800204da
apr 02 16:47:56 enrico-linux kernel: [drm:radeon_cs_ib_chunk [radeon]] *ERROR* Invalid command stream !
apr 02 16:47:56 enrico-linux org.gtk.vfs.Daemon[5243]: A connection to the bus can't be made
apr 02 16:47:56 enrico-linux org.gtk.vfs.Daemon[5243]: g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
apr 02 16:47:56 enrico-linux dhclient[5222]: DHCPREQUEST of 192.168.0.5 on wlan0 to 255.255.255.255 port 67 (xid=0x7ec96eb8)
apr 02 16:47:56 enrico-linux lightdm[5227]: pam_unix(lightdm-greeter:session): session closed for user lightdm
apr 02 16:48:02 enrico-linux dhclient[5222]: DHCPREQUEST of 192.168.0.5 on wlan0 to 255.255.255.255 port 67 (xid=0x7ec96eb8)
apr 02 16:48:11 enrico-linux dhclient[5222]: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x5563f5a3)
apr 02 16:48:11 enrico-linux sudo[5347]: enrico : TTY=pts/1 ; PWD=/home/enrico ; USER=root ; COMMAND=/bin/journalctl
apr 02 16:48:11 enrico-linux sudo[5347]: pam_unix(sudo:session): session opened for user root by enrico(uid=0)

```

---

### Post by Elfy on 2015-04-02
if this gets nowhere in here, I'll do a less than common thing and move it to Networking.

---

### Post by dino99 on 2015-04-02
> **enricobe said:**
> I have saved some interesting lines of Journalctl. After the wake up:

(I have removed the first lines about linux-kernel and systemd and removed some digits from the Mac Address)
```

apr 02 16:47:51 enrico-linux NetworkManager[757]: <info> wake requested (sleeping: yes  enabled: yes)
apr 02 16:47:51 enrico-linux NetworkManager[757]: <info> waking up...
apr 02 16:47:51 enrico-linux NetworkManager[757]: <info> (eth0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
apr 02 16:47:51 enrico-linux NetworkManager[757]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
apr 02 16:47:51 enrico-linux NetworkManager[757]: <info> (eth0): preparing device
apr 02 16:47:51 enrico-linux NetworkManager[757]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
apr 02 16:47:51 enrico-linux kernel: r8169 0000:09:00.0 eth0: link down
apr 02 16:47:51 enrico-linux NetworkManager[757]: <info> (wlan0): preparing device
apr 02 16:47:51 enrico-linux NetworkManager[757]: <info> NetworkManager state is now DISCONNECTED
apr 02 16:47:51 enrico-linux wpa_supplicant[874]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
apr 02 16:47:51 enrico-linux wpa_supplicant[874]: dbus: Failed to construct signal
apr 02 16:47:51 enrico-linux NetworkManager[757]: <warn> could not get interface properties: No readable properties in this interface.
apr 02 16:47:51 enrico-linux NetworkManager[757]: <info> (wlan0): supplicant interface state: starting -> ready
apr 02 16:47:51 enrico-linux NetworkManager[757]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
apr 02 16:47:51 enrico-linux NetworkManager[757]: <warn> could not get interface properties: No readable properties in this interface.
apr 02 16:47:51 enrico-linux wpa_supplicant[874]: wlan0: CTRL-EVENT-SCAN-STARTED
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Auto-activating connection 'NETGEAR-06'.
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) starting connection 'NETGEAR-06'
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> NetworkManager state is now CONNECTING
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0/wireless): access point 'NETGEAR-06' has security, but secrets are required.
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> (wlan0): supplicant interface state: ready -> inactive
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0/wireless): connection 'NETGEAR-06' has security, and secrets exist.  No new secrets needed.
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Config: added 'ssid' value 'NETGEAR-06'
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Config: added 'scan_ssid' value '1'
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Config: added 'auth_alg' value 'OPEN'
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Config: added 'psk' value '<omitted>'
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Config: set interface ap_scan to 1
apr 02 16:47:52 enrico-linux systemd-journal[235]: Forwarding to syslog missed 2 messages.
apr 02 16:47:52 enrico-linux wpa_supplicant[874]: wlan0: SME: Trying to authenticate with 28:xx:xx:xx:xx:22 (SSID='NETGEAR-06' freq=2437 MHz)
apr 02 16:47:52 enrico-linux kernel: wlan0: authenticate with 28:xx:xx:xx:xx:22
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> (wlan0): supplicant interface state: inactive -> authenticating
apr 02 16:47:52 enrico-linux wpa_supplicant[874]: wlan0: Trying to associate with 28:xx:xx:xx:xx:222 (SSID='NETGEAR-06' freq=2437 MHz)
apr 02 16:47:52 enrico-linux kernel: wlan0: send auth to 28:xx:xx:xx:xx:22 (try 1/3)
apr 02 16:47:52 enrico-linux kernel: wlan0: authenticated
apr 02 16:47:52 enrico-linux kernel: rtl8723ae 0000:08:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
apr 02 16:47:52 enrico-linux kernel: rtl8723ae 0000:08:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
apr 02 16:47:52 enrico-linux kernel: wlan0: associate with 28:xx:xx:xx:xx:22 (try 1/3)
apr 02 16:47:52 enrico-linux wpa_supplicant[874]: wlan0: Associated with 28:xx:xx:xx:xx:22
apr 02 16:47:52 enrico-linux kernel: wlan0: RX AssocResp from 28:xx:xx:xx:xx:22 (capab=0x411 status=0 aid=6)
apr 02 16:47:52 enrico-linux kernel: wlan0: associated
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> (wlan0): supplicant interface state: authenticating -> associated
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
apr 02 16:47:52 enrico-linux wpa_supplicant[874]: wlan0: WPA: Key negotiation completed with 28:xx:xx:xx:xx:22 [PTK=CCMP GTK=CCMP]
apr 02 16:47:52 enrico-linux wpa_supplicant[874]: wlan0: CTRL-EVENT-CONNECTED - Connection to 28:xx:xx:xx:xx:22 completed [id=0 id_str=]
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'NETGEAR-06'.
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> dhclient started with pid 5222
apr 02 16:47:52 enrico-linux NetworkManager[757]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
apr 02 16:47:53 enrico-linux NetworkManager[757]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
apr 02 16:47:53 enrico-linux dhclient[5222]: DHCPREQUEST of 192.168.0.5 on wlan0 to 255.255.255.255 port 67 (xid=0x7ec96eb8)
apr 02 16:47:53 enrico-linux lightdm[834]: initctl: Impossibile connettersi a Upstart: Failed to connect to socket /com/ubuntu/upstart: Connessione rifiutata
apr 02 16:47:53 enrico-linux lightdm[5227]: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
apr 02 16:47:53 enrico-linux lightdm[5227]: PAM adding faulty module: pam_kwallet.so
apr 02 16:47:53 enrico-linux lightdm[5227]: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
apr 02 16:47:53 enrico-linux systemd[1]: Started Session c5 of user lightdm.
apr 02 16:47:53 enrico-linux systemd-logind[769]: New session c5 of user lightdm.
apr 02 16:47:53 enrico-linux systemd[1]: Starting Session c5 of user lightdm.
apr 02 16:47:53 enrico-linux lightdm[5326]: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
apr 02 16:47:53 enrico-linux lightdm[5326]: PAM adding faulty module: pam_kwallet.so
apr 02 16:47:53 enrico-linux lightdm[5326]: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "enrico"
apr 02 16:47:54 enrico-linux avahi-daemon[785]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::26fd:52ff:fe29:9c4e.
apr 02 16:47:54 enrico-linux avahi-daemon[785]: New relevant interface wlan0.IPv6 for mDNS.
apr 02 16:47:54 enrico-linux avahi-daemon[785]: Registering new address record for fe80::xxxx:xxxx:xxxx:9c4e on wlan0.*.
apr 02 16:47:56 enrico-linux kernel: radeon 0000:01:00.0: evergreen_surface_check_2d:278 texture pitch 1408 invalid must be aligned with 256
apr 02 16:47:56 enrico-linux kernel: radeon 0000:01:00.0: evergreen_cs_track_validate_texture:827 texture invalid 0x15542bc1 0x400002ff 0x060a0000 0x00000000 0x80000000 0x800204da
apr 02 16:47:56 enrico-linux kernel: [drm:radeon_cs_ib_chunk [radeon]] *ERROR* Invalid command stream !
apr 02 16:47:56 enrico-linux org.gtk.vfs.Daemon[5243]: A connection to the bus can't be made
apr 02 16:47:56 enrico-linux org.gtk.vfs.Daemon[5243]: g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
apr 02 16:47:56 enrico-linux dhclient[5222]: DHCPREQUEST of 192.168.0.5 on wlan0 to 255.255.255.255 port 67 (xid=0x7ec96eb8)
apr 02 16:47:56 enrico-linux lightdm[5227]: pam_unix(lightdm-greeter:session): session closed for user lightdm
apr 02 16:48:02 enrico-linux dhclient[5222]: DHCPREQUEST of 192.168.0.5 on wlan0 to 255.255.255.255 port 67 (xid=0x7ec96eb8)
apr 02 16:48:11 enrico-linux dhclient[5222]: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x5563f5a3)
apr 02 16:48:11 enrico-linux sudo[5347]: enrico : TTY=pts/1 ; PWD=/home/enrico ; USER=root ; COMMAND=/bin/journalctl
apr 02 16:48:11 enrico-linux sudo[5347]: pam_unix(sudo:session): session opened for user root by enrico(uid=0)

```

good catch :p

you need to report against dbus (ubuntu-bug dbus) and set the bug title to 'wpa_supplicant[874]: dbus: Failed to construct signal after 'suspend' ' with the all posted above  as bug comments

---

### Post by enricobe on 2015-04-02
> **Elfy said:**
> if this gets nowhere in here, I'll do a less than common thing and move it to Networking.

I have posted here because I use the Vivid version of Xubuntu :)

> **9d9 said:**
> good catch :p

you need to report against dbus (ubuntu-bug dbus) and set the bug title to 'wpa_supplicant[874]: dbus: Failed to construct signal' with the all posted above  as bug comments

I'm glad to help in bug searching :) 
I must use the "ubuntu-bug dbus" command after the wake up to report the bug on launchpad? Am I right? 
I ask to you because I'm not sure what is the best way to report the bug

---

### Post by dino99 on 2015-04-02
> **enricobe said:**
> I have posted here because I use the Vivid version of Xubuntu :)



I'm glad to help in bug searching :) 
I must use the "ubuntu-bug dbus" command after the wake up to report the bug on launchpad? Am I right? 
I ask to you because I'm not sure what is the best way to report the bug

no need to test again the 'suspend' issue as you have posted the related part of journalctl; so report when you like using copy/paste  (you can remove lines about 'lightdm' they are harmless)  ):P

---

### Post by Elfy on 2015-04-02
I understand why you posted here. If necessary I'll move it elsewhere - I can do that ;)

For the moment I'd do as 9d9 says and do a new bug

---

### Post by enricobe on 2015-04-02
Ok, I have reported the bug [https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/1439771](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/1439771)
I hope to have done the report in the right way

---

### Post by dino99 on 2015-04-02
> **enricobe said:**
> Ok, I have reported the bug [https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/1439771](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/1439771)
I hope to have done the report in the right way

well done Enrico :p  now you can send a message to the Italian Loco team, they have one more 'pro' with them :guitar:

---

### Post by enricobe on 2015-04-02
> **9d9 said:**
> well done Enrico :p  now you can send a message to the Italian Loco team, they have one more 'pro' with them :guitar:

Thank you :lolflag:
I'm already trying to enter in the Translation Team :D (I need to say that my "eng2ita" is so much better than my "ita2eng" :p )

---

### Post by clafab on 2015-04-06
I have the same problem with my MacBook Pro 11,3 running Xubuntu 15.04 beta 2.
However Wifi only doesn't work, if I disable the "Lock screen after suspend" option
(I always disable locking after suspend, because you can instantly start working again after resume).
When I leave this option enabled, I have to login after resume and Wifi works.

In earlier versions of Xubuntu (I used both Xubuntu 14.04 and 14.10 and had the same problem)
you can fix this by creating a pm-utils hook in /etc/pm/sleep.d, which is restarting the network-manager.
I tried to get this wifi-fix pm-hook working, then I noticed Xubuntu 15.04 uses systemd :)


I fixed the no-Wifi after resume issue by creating a systemd service ("hook").
This is no fix for the problem, but a good workaround:

1. Create a new systemd service file in /etc/systemd/system:
```
sudo nano /etc/systemd/system/wififix.service
```

And the following content:

```
[Unit]
Description=Fix Wifi after resume by restarting networking
After=suspend.target

[Service]
Type=oneshot
ExecStart=/usr/bin/nmcli networking off ; /usr/bin/nmcli networking on

[Install]
WantedBy=suspend.target
```


Setting the Execute bit is not required.

2. Enable the service:
```
sudo systemctl enable wififix.service
```

3. Check the status:
```
sudo systemctl status wififix.service
```

You should see no errors and the following output:
```
wififix.service - Fix Wifi after resume by restarting networking
Loaded: loaded (/etc/systemd/system/wififix.service; enabled; vendor preset: enabled)
Active: inactive (dead)
```

Reboot is not required, but I always do one to be sure.

4. Try going to sleep and be happy with Xubuntu 15.04 and Wifi after resume ;)

Never had such a good suspend/resume experience with Xubuntu, I always had problems with no backlight after resume and slow suspend.
It suspends within seconds and also resumes within seconds, Wifi needs some extra seconds to work again (everything is restarted).

Greetings,
Fabian

---

### Post by enricobe on 2015-04-07
> **clafab said:**
> I have the same problem with my MacBook Pro 11,3 running Xubuntu 15.04 beta 2.
However Wifi only doesn't work, if I disable the "Lock screen after suspend" option
(I always disable locking after suspend, because you can instantly start working again after resume).
When I leave this option enabled, I have to login after resume and Wifi works.

In earlier versions of Xubuntu (I used both Xubuntu 14.04 and 14.10 and had the same problem)
you can fix this by creating a pm-utils hook in /etc/pm/sleep.d, which is restarting the network-manager.
I tried to get this wifi-fix pm-hook working, then I noticed Xubuntu 15.04 uses systemd :)


I fixed the no-Wifi after resume issue by creating a systemd service ("hook").
This is no fix for the problem, but a good workaround:

1. Create a new systemd service file in /etc/systemd/system:
```
sudo nano /etc/systemd/system/wififix.service
```

And the following content:

```
[Unit]
Description=Fix Wifi after resume by restarting networking
After=suspend.target

[Service]
Type=oneshot
ExecStart=/usr/bin/nmcli networking off ; /usr/bin/nmcli networking on

[Install]
WantedBy=suspend.target
```


Setting the Execute bit is not required.

2. Enable the service:
```
sudo systemctl enable wififix.service
```

3. Check the status:
```
sudo systemctl status wififix.service
```

You should see no errors and the following output:
```
wififix.service - Fix Wifi after resume by restarting networking
Loaded: loaded (/etc/systemd/system/wififix.service; enabled; vendor preset: enabled)
Active: inactive (dead)
```

Reboot is not required, but I always do one to be sure.

4. Try going to sleep and be happy with Xubuntu 15.04 and Wifi after resume ;)

Never had such a good suspend/resume experience with Xubuntu, I always had problems with no backlight after resume and slow suspend.
It suspends within seconds and also resumes within seconds, Wifi needs some extra seconds to work again (everything is restarted).

Greetings,
Fabian

Thank for you detailed answer Fabian :)
I have understand that in your case the Wifi works if you have the password request at the wake up. Am I right? I have this option enabled but the WiFi doesn't work.

---

### Post by clafab on 2015-04-07
> **enricobe said:**
> Thank for you detailed answer Fabian :)
I have understand that in your case the Wifi works if you have the password request at the wake up. Am I right? I have this option enabled but the WiFi doesn't work.

Yes, that's right. If I have to enter my password after resume, Wifi works. If I enable "auto-login" ("lock screen when system is going for sleep"- option unchecked), Wifi doesn't work.

You can also try restarting the network manager manually after suspend, before creating a systemd service to check if it really works for you:
```
sudo service network-manager restart
```
This will do the same as my wififix systemd-service.

---

### Post by zika on 2015-04-07
> **clafab said:**
> Reboot is not required, but I always do one to be sure.What is the purpose of suspend if You do reboot? Why not power-off then?
Click on nm-applet ro wake connection up does not do the trick after suspend?

---

### Post by clafab on 2015-04-07
> **zika said:**
> What is the purpose of suspend if You do reboot? Why not power-off then?
Click on nm-applet ro wake connection up does not do the trick after suspend?

Oh, the reboot was related to changes of system config (enabling systemd service in this case).
I never shutdown my Laptop, just suspend it all the time.

Clicking on the nm-applet doesn't help, i have to restart the nm. I can also do this by enabling and disabling
the network with the nm-applet.
As I wrote in my first post, I always had problems with network after resume on my MacBook.
Other people with other Laptop models also have the same problem with earlier Ubuntu versions,
restarting nm works in most cases.

@enricobe: Did restarting network-manager work for you?

---

### Post by enricobe on 2015-04-07
> **clafab said:**
> Yes, that's right. If I have to enter my password after resume, Wifi works. If I enable "auto-login" ("lock screen when system is going for sleep"- option unchecked), Wifi doesn't work.

You can also try restarting the network manager manually after suspend, before creating a systemd service to check if it really works for you:
```
sudo service network-manager restart
```
This will do the same as my wififix systemd-service.

My wifi doesn't work with the password request after resume. It seems that the bug is different on different hardware.

---

