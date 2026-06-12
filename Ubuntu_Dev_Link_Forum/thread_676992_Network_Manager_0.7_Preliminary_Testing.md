---
title: "Network Manager 0.7 Preliminary Testing"
date: 2008-01-24
forum: Ubuntu Dev Link Forum
---

### Post by 23meg on 2008-01-24
Alexander Sack, who's working on [the possible integration of NM 0.7 for Hardy]("https://blueprints.launchpad.net/ubuntu/+spec/nm-ifupdown-death-match"), has packaged it for testing, and would like your feedback before pushing it into Hardy. Packages are available in [his PPA]("https://launchpad.net/~asac/+archive").

Please test and report bugs and your experiences **in this thread** (and **not the network-manager source package in Launchpad**). Remember to cite the chipset and driver of your network hardware, and the encryption standard you're using (WEP, WPA or WPA2).[COLOR="White"](No, you shouldn't be using WEP.)[/COLOR]

"*lshw -class network*" will provide info on your hardware. For privacy, you may want to remove the "serial" line it produces, since it's the MAC address of your device.

[SIZE="3"]**Be warned: this will probably break your networking at some point. Make sure you know how to recover before going ahead.**[/SIZE]

---

### Post by mabovo on 2008-01-24
Great news !

I will test it soon at home with Atheros 5418 on wpa-2  :)

---

### Post by PmDematagoda on 2008-01-24
I just installed NM 0.7, it works well with my wired network connection and it seems to be faster than NM 0.6:).

---

### Post by Technoviking on 2008-01-24
No luck with a wpa-2 and iwl3945 driver. nm-applet crashes the first time it launches, then will not show up anytime afterwards. Reverted back to nm 0.65 fine.

Mike

---

### Post by aamukahvi on 2008-01-24
Works here in Virtualbox, but "Edit connections" does nothing.

---

### Post by stephantom on 2008-01-24
```
$ lspci | grep Wireless
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

No dice directly after upgrade (says there are no networking devices), but works smoothly after a reboot. My wireless passphrase was not remembered, I had to enter it again.
I haven't tested any other features, but I connects and stays connected.
Will be back for a more extensive test report soon.

Edit: When I try to configure a VPN nm-applet just tells me that there is no VPN software installed and that I should contact root. This message is less than unhelpful for the average user. Sure, I'm going to poke around and install random vpn packages to see if that does the trick. But the user should be informed that additional software is required and offer to download the packages. Just like the codec installation, or the install service when you first try to share a folder (installs samba/NFS services).

---

### Post by chrisccoulson on 2008-01-24
Network Manager fails to start on my machine. In /var/log/syslog, I see:
```
Jan 24 19:20:10 chris-ubuntuvm NetworkManager: <info>  starting... 
Jan 24 19:20:10 chris-ubuntuvm NetworkManager: <WARN>  nm_hal_manager_new(): Could not initialize connection to the HAL daemon. 
Jan 24 19:20:10 chris-ubuntuvm NetworkManager: <debug> [1201202410.879523] nm_print_open_socks(): Open Sockets List: 
Jan 24 19:20:10 chris-ubuntuvm NetworkManager: <debug> [1201202410.879602] nm_print_open_socks(): Open Sockets List Done.
```

If I do:
```
sudo /etc/init.d/NetworkManager restart
```
...after the machine has booted, then all is well.

Is there a race with HAL?

---

### Post by stephantom on 2008-01-24
Seems that the passphrase it not remembered at all. I have to enter it everytime I establish the connection.

---

### Post by ntetreau on 2008-01-24
NetworkManager also fails on my machine and I also get in syslog:

```
Jan 24 19:30:30 constantines NetworkManager: <info>  starting... 
Jan 24 19:30:30 constantines NetworkManager: <WARN>  nm_hal_manager_new(): Could not initialize connection to the HAL daemon. 
Jan 24 19:30:30 constantines NetworkManager: <debug> [1201203030.904724] nm_print_open_socks(): Open Sockets List: 
Jan 24 19:30:30 constantines NetworkManager: <debug> [1201203030.904749] nm_print_open_socks(): Open Sockets List Done. 
```

Restarting NetworkManager takes care of my wired connection and nm-applet shows up.

It's not showing my intel wifi 4965 but I'm pretty sure this is because of a problem with the latest linux-restricted which updated today. 
EDIT: It was indeed a bug in the new linux-restricted, and now NM-0.7 shows my wireless, I'll update once I get home and connect to my WPA network
```
 sudo mv /lib/firmware/2.6.24-4-generic/iwlwifi-4965.ucode /lib/firmware/2.6.24-4-generic/iwlwifi-4965-1.ucode
```
Here's my output

```
lshw -class network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 61
       serial: <snip>
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 12
       serial: 00:1a:80:58:06:67
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=131.111.76.59 latency=0 module=sky2 multicast=yes
```

EDIT: Also, when i tried to add back my cisco VPN network, something crashed with this in the terminal:

```
(nm-vpn-properties:7168): Gtk-CRITICAL **: gtk_expander_set_expanded: assertion `GTK_IS_EXPANDER (expander)' failed

(nm-vpn-properties:7168): Gtk-CRITICAL **: gtk_container_add: assertion `GTK_IS_WIDGET (widget)' failed
``` 

All-in-all, it's working pretty well actually!

LAST EDIT: In the end, after restarting NetworkManager, my wifi with WPA works fine, and I still can't setup a cisco VPN

---

### Post by pochu on 2008-01-24
I've tried it in real hardware, and right after installing it, the network went down and nm-applet said there was no device detected.

After a reboot, nm-applet wasn't started, and I had this in .xsession-errors:

[CODE]*** glibc detected *** nm-applet: munmap_chunk(): invalid pointer: 0x0807ac8e ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb732850b]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb750ec21]
/usr/lib/libglib-2.0.so.0(g_slist_foreach+0x21)[0xb7525021]
/usr/lib/libnm-util.so.1(nm_utils_slist_free+0x39)[0xb7ec5779]
/usr/lib/libnm-util.so.1[0xb7ec35bd]
/usr/lib/libgobject-2.0.so.0(g_object_unref+0x16b)[0xb758a9db]
/usr/lib/libglib-2.0.so.0[0xb74f9d94]
/usr/lib/libglib-2.0.so.0[0xb74f9ded]
/usr/lib/libglib-2.0.so.0(g_hash_table_remove_all+0x35)[0xb74fa345]
/usr/lib/libglib-2.0.so.0(g_hash_table_destroy+0x33)[0xb74fa3e3]
/usr/lib/libnm-util.so.1[0xb7ebb60d]
/usr/lib/libgobject-2.0.so.0(g_object_unref+0x16b)[0xb758a9db]
nm-applet(nm_gconf_migrate_0_6_connections+0x680)[0x806afd0]
nm-applet(nm_gconf_get_all_connections+0x60)[0x8068200]
nm-applet[0x8059f55]
nm-applet(applet_dbus_settings_list_connections+0x58)[0x805a198]
nm-applet(applet_device_wired_get_class+0x4f)[0x805f42f]
nm-applet[0x80568b7]
/usr/lib/libgobject-2.0.so.0(g_object_newv+0x328)[0xb758e098]
/usr/lib/libgobject-2.0.so.0(g_object_new_valist+0x291)[0xb758ec31]
/usr/lib/libgobject-2.0.so.0(g_object_new+0x40)[0xb758eda0]
nm-applet(nm_applet_new+0x1b)[0x8053cfb]
nm-applet(main+0x60)[0x8053580]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb72cf450]
nm-applet[0x80534b1]
[\CODE]

So I did "nm-applet" in a terminal, and it started and asked me for a password to connect my WPA network (NB: the package from the archive didn't ask me for a password, but took it from the keyring).

But it's working fine now. I have an ipw2200bg

Cheers

---

### Post by Technoviking on 2008-01-24
I did get network manager work, but do have to restart network-manager every time I reboot.

```
sudo /etc/init.d/NetworkManager restart
```

---

### Post by MacUntu on 2008-01-24
> **Mike said:**
> No luck with a wpa-2 and iwl3945 driver. nm-applet crashes the first time it launches, then will not show up anytime afterwards. Reverted back to nm 0.65 fine.

Mike
> **Mike said:**
> I did get network manager work, but do have to restart network-manager every time I reboot.

```
sudo /etc/init.d/NetworkManager restart
```

Confirmed.

---

### Post by Technoviking on 2008-01-24
Also, the menu entry *Edit Connections* does nothing for me.

Mike

---

### Post by mabovo on 2008-01-24
After all upgrades and nm 0.7 installation I am writing this post from my wireless card AR5418 using wpa-2 on MacBook 2.1 amd64 2.6.24-4 R7.

1. Using nm-0.7 I choose wpa-2 and typed my passwphrase. 
2. I checked /etc/networh/interfaces and everything was ok
3. Re-open nm-0.7 and all settings was still there registered. On nm-0.6 all settings didn't get registered after closing it.
4. Testing with dinamically dhcp could not connect to the network.
5. Change to static dhcp typing my IP address, netmask and gateway could finally be connected to the wireless network.

Note.: No crashes noticeable with nm-0.7 on my system.

---

### Post by RAOF on 2008-01-24
> **Mike said:**
> No luck with a wpa-2 and iwl3945 driver. nm-applet crashes the first time it launches, then will not show up anytime afterwards. Reverted back to nm 0.65 fine.

Mike

> **Mike said:**
> I did get network manager work, but do have to restart network-manager every time I reboot.

```
sudo /etc/init.d/NetworkManager restart
```

I don't see this behaviour (iwl3945).  After a reboot, nm-applet found my card, then segfaulted.  After restarting nm-applet it asked for my WPA2 passphrase, and from then on has worked exactly as NM 0.65.

lshw output:
```

  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth2
       version: 02
       serial: <snip>
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.0.150 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

```

---

### Post by PmDematagoda on 2008-01-24
I have the same problems that Mike mentioned.

---

### Post by autocrosser on 2008-01-24
Working without problems with atheros AR5212/AR5213 chipset (D-Link AirPlus DWL-G520)

---

### Post by 23meg on 2008-01-24
Working fine with WPA2 on IPW2200; no crashes or drops so far. lshw output:

```
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:03:05.0
       logical name: eth1
       version: 05
       serial: <snip>
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.10.3 latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g

```

---

### Post by JanDM on 2008-01-25
Working fine here too. Network manager showed up after I did "/etc/init.d/NetworkManager restart". 

I use WPA. lshw output:
```

  *-network:0             
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 4
       bus info: pci@0000:05:04.0
       logical name: wmaster0
       version: 01
       serial: <snip>
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci ip=192.168.1.101 latency=64 module=rt2500pci multicast=yes wireless=IEEE 802.11g

```

---

### Post by ntetreau on 2008-01-25
> **Mike said:**
> Also, the menu entry *Edit Connections* does nothing for me.

Mike

Confirmed

---

### Post by stuart.crouch on 2008-01-25
Does anyone know if the ability for NM to connect before you log in was implemented in this version?
They talked about having allowed networks that dont require the keyring (and hence a log in) to access.

This is the sole reason I switched to WICD - I need my wifi up before I log in!

I hope its there :D the NM gui is better than the WICD one, but WICD meets my needs better at the moment.

---

### Post by MacUntu on 2008-01-25
iwl3945: Still no luck to connect. DHCP doesn't seem to work (no offer found). Manually setting IP etc seems to work, but I can't connect to my WPA2 router:

```
foo@bar:~$ sudo wpa_supplicant -Dwext -iwlan0 -c /etc/wpa_supplicant wpa_supplicant.conf
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 4 value 0x0 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - Trying to associate with SSID 'FooNet'
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - Authentication with 00:00:00:00:00:00 timed out.
Trying to associate with SSID 'FooNet'
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - 
```

---

### Post by Technoviking on 2008-01-25
My lshw
```
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wmaster0
                version: 02
                serial: 00:19:d2:9f:7d:36
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 ip=155.97.97.209 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
```

---

### Post by MacUntu on 2008-01-25
Same as mine (apart from bus info). Here a more detailed log of what happens when running wpa_supplicant (sudo iwlist wlan0 scanning shows the AP):
[http://ubuntuusers.de/paste/31577/](http://ubuntuusers.de/paste/31577/)

---

### Post by VenkateshSrinivas on 2008-01-25
Hi,

I installed it here, had a few problems:
* First, I needed to loosen some dbus settings to get NetworkManager-applet to start; in /etc/dbus-1/system.d/NetworkManager.conf, I needed to allow the console user to own org.freedesktop.NetworkManager, and in nm-applet.conf I needed to allow the console user to own org.freedesktop.NetworkManagerUserSettings.
* Second, nm-applet won't insert entries into /etc/resolv.conf if the resolvconf package is installed. Make sure to remove it.
* Third, if I try to select 'Manual Configuration', I get an error: "The configuration could not be loaded. You are not allowed to access the system configuration."

I'm using an ipw2200. 

Other than that, it feels a lot faster than before.

---

### Post by mabovo on 2008-01-25
I lost the wireless connection when did "lshw" so I need to do "sudo /etc/init.d/networking restart" two times and wait a few seconds to reconnect again.

 *-network
                description: Wireless interface
                product: AR5418 802.11a/b/g/n Wireless PCI Express Adapter
                vendor: Atheros Communications, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wifi0
                version: 01
                serial: 
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci ip=192.168.0.103 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g

---

### Post by High Roller on 2008-01-25
> **stuart.crouch said:**
> Does anyone know if the ability for NM to connect before you log in was implemented in this version?
They talked about having allowed networks that dont require the keyring (and hence a log in) to access.

This is the sole reason I switched to WICD - I need my wifi up before I log in!

I hope its there :D the NM gui is better than the WICD one, but WICD meets my needs better at the moment.

This is the feature that I look forward to the most in NM 0.7
I believe this is under development at the moment.  From what I understand, the logged in user will "publish" this information to the system so that it will be used before login etc.  I'm not sure if the user has a choice to share login credentials with the system or if it is automatically shared.

---

### Post by BurnHead on 2008-01-26
I had the same problem as some people here: the applet didn't start after a reboot. Starting it in the console also worked for me though. "Edit Connections" does not work here, too. Apart from that everything else seems to work fine.
I'm using an Atheros AR5007EG chipset with ndiswrapper 1.51.

---

### Post by mabovo on 2008-01-26
I have installed the new kernel release 2.6.24-5 and had to reinstall madwifi driver again for AR5418 wireless card.
I think this problem to manually connect after reboot depends on some modules in kernel for those kind of wireless cards.
Am I wrong ?

---

### Post by dgf on 2008-01-26
// After a second restart it does work now. Im logged in into my network using Networkmanager 0.7

I have a Asus Wl-500g deluxe as an access point and router with OpenWrt installed and WPA-Encryption.
My chipset: ```
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```
After commenting out everything regarding my wifi-adapter in /etc/network/interfaces Networkmanager starts fine, but I am unable to connect, because it asks every time for the psk and is always unable to connect and times out.

```
Jan 26 13:09:14 Hannibal NetworkManager: <info>  starting... 
Jan 26 13:09:14 Hannibal NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/ipw_wlan_switch 
Jan 26 13:09:14 Hannibal NetworkManager: <WARN>  constructor(): (eth0): Device otherwise managed, ignoring. 
Jan 26 13:09:14 Hannibal NetworkManager: <info>  wlan0_rename: Device is fully-supported using driver 'iwl3945'. 
Jan 26 13:09:14 Hannibal NetworkManager: <info>  wlan0_rename: driver does not support SSID scans (scan_capa 0x00). 
Jan 26 13:09:14 Hannibal NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0_rename'. 
Jan 26 13:09:14 Hannibal NetworkManager: <info>  Bringing up device wlan0_rename 
Jan 26 13:09:14 Hannibal NetworkManager: <info>  Deactivating device wlan0_rename. 
Jan 26 13:09:14 Hannibal NetworkManager: <info>  (wlan0_rename): exported as /org/freedesktop/Hal/devices/net_00_13_02_8e_fc_5c_0 
Jan 26 13:09:14 Hannibal NetworkManager: <info>  (wlan0_rename) supplicant interface is now in state 2 (from 1). 
Jan 26 13:09:16 Hannibal NetworkManager: <info>  SWITCH: no current connection, found better connection 'Auto OpenWrt (wlan0_rename)'. 
Jan 26 13:09:16 Hannibal NetworkManager: <info>  Activating device wlan0_rename 
Jan 26 13:09:16 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 26 13:09:16 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 1 of 5 (Device Prepare) started... 
Jan 26 13:09:16 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 2 of 5 (Device Configure) scheduled... 
Jan 26 13:09:16 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 1 of 5 (Device Prepare) complete. 
Jan 26 13:09:16 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 2 of 5 (Device Configure) starting... 
Jan 26 13:09:16 Hannibal NetworkManager: <info>  Activation (wlan0_rename/wireless): access point 'Auto OpenWrt' has security, but secrets are required. 
Jan 26 13:09:16 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 2 of 5 (Device Configure) complete. 
Jan 26 13:09:34 Hannibal NetworkManager: <info>  (wlan0_rename) Supplicant interface state change: 1 -> 2 
Jan 26 13:09:41 Hannibal NetworkManager: <info>  (wlan0_rename) Supplicant interface state change: 2 -> 1 
Jan 26 13:10:15 Hannibal NetworkManager: <info>  User request for activation of wlan0_rename. 
Jan 26 13:10:15 Hannibal NetworkManager: <info>  Deactivating device wlan0_rename. 
Jan 26 13:10:15 Hannibal NetworkManager: <info>  Activation (wlan0_rename): cancelling... 
Jan 26 13:10:15 Hannibal NetworkManager: <info>  Activation (wlan0_rename): cancelled. 
Jan 26 13:10:15 Hannibal NetworkManager: <info>  Activating device wlan0_rename 
Jan 26 13:10:15 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 26 13:10:15 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 1 of 5 (Device Prepare) started... 
Jan 26 13:10:15 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 2 of 5 (Device Configure) scheduled... 
Jan 26 13:10:15 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 1 of 5 (Device Prepare) complete. 
Jan 26 13:10:15 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 2 of 5 (Device Configure) starting... 
Jan 26 13:10:15 Hannibal NetworkManager: <info>  Activation (wlan0_rename/wireless): access point 'Auto OpenWrt' has security, but secrets are required. 
Jan 26 13:10:15 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 2 of 5 (Device Configure) complete. 
Jan 26 13:10:29 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 26 13:10:29 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 1 of 5 (Device Prepare) started... 
Jan 26 13:10:29 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 2 of 5 (Device Configure) scheduled... 
Jan 26 13:10:29 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 1 of 5 (Device Prepare) complete. 
Jan 26 13:10:29 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 2 of 5 (Device Configure) starting... 
Jan 26 13:10:29 Hannibal NetworkManager: <info>  Activation (wlan0_rename/wireless): connection 'Auto OpenWrt' has security, and secrets exist.  No new secrets needed. 
Jan 26 13:10:29 Hannibal NetworkManager: <info>  Config: added 'ssid' value 'OpenWrt' 
Jan 26 13:10:29 Hannibal NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Jan 26 13:10:29 Hannibal NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Jan 26 13:10:29 Hannibal NetworkManager: <info>  Config: added 'proto' value 'WPA RSN' 
Jan 26 13:10:29 Hannibal NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP' 
Jan 26 13:10:29 Hannibal NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP' 
Jan 26 13:10:29 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 2 of 5 (Device Configure) complete. 
Jan 26 13:10:29 Hannibal NetworkManager: <info>  Config: set interface ap_scan to 1 
Jan 26 13:10:29 Hannibal NetworkManager: <info>  (wlan0_rename) Supplicant interface state change: 1 -> 2 
Jan 26 13:10:54 Hannibal NetworkManager: <info>  Activation (wlan0_rename/wireless): association took too long, asking for new key. 
Jan 26 13:10:54 Hannibal NetworkManager: <info>  (wlan0_rename) Supplicant interface state change: 2 -> 0 
Jan 26 13:11:06 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 26 13:11:06 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 1 of 5 (Device Prepare) started... 
Jan 26 13:11:06 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 2 of 5 (Device Configure) scheduled... 
Jan 26 13:11:06 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 1 of 5 (Device Prepare) complete. 
Jan 26 13:11:06 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 2 of 5 (Device Configure) starting... 
Jan 26 13:11:06 Hannibal NetworkManager: <info>  Activation (wlan0_rename/wireless): connection 'Auto OpenWrt' has security, and secrets exist.  No new secrets needed. 
Jan 26 13:11:06 Hannibal NetworkManager: <info>  Config: added 'ssid' value 'OpenWrt' 
Jan 26 13:11:06 Hannibal NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Jan 26 13:11:06 Hannibal NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Jan 26 13:11:06 Hannibal NetworkManager: <info>  Config: added 'proto' value 'WPA RSN' 
Jan 26 13:11:06 Hannibal NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP' 
Jan 26 13:11:06 Hannibal NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP' 
Jan 26 13:11:06 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 2 of 5 (Device Configure) complete. 
Jan 26 13:11:06 Hannibal NetworkManager: <info>  Config: set interface ap_scan to 1 
Jan 26 13:11:06 Hannibal NetworkManager: <info>  (wlan0_rename) Supplicant interface state change: 0 -> 2 
Jan 26 13:11:31 Hannibal NetworkManager: <info>  Activation (wlan0_rename/wireless): association took too long, asking for new key. 
Jan 26 13:11:31 Hannibal NetworkManager: <info>  (wlan0_rename) Supplicant interface state change: 2 -> 0 
```
After every sequence of trying to connect it asks me for the psk again.

// It does work now, after reboot

---

### Post by dgf on 2008-01-26
After several hours of using I was kicked out and unable to reconnect again using Networkmanager. It asks for my psk but is unable to reconnect. No matter how often it asks and type.
It seems to have some similarities with my first problem posted above:
```

Jan 26 20:06:50 Hannibal NetworkManager: <info>  wlan0_rename: link timed out. 
Jan 26 20:06:50 Hannibal NetworkManager: <info>  SWITCH: found better connection 'wlan0_rename/Auto OpenWrt' than current connection 'wlan0_rename/Auto OpenWrt'.  have_link=0 
Jan 26 20:06:50 Hannibal NetworkManager: <info>  Deactivating device wlan0_rename. 
Jan 26 20:06:50 Hannibal NetworkManager: <info>  wlan0_rename: canceled DHCP transaction, dhclient pid 5614 
Jan 26 20:06:50 Hannibal avahi-daemon[5025]: Withdrawing address record for 192.168.50.151 on wlan0_rename.
Jan 26 20:06:50 Hannibal avahi-daemon[5025]: Leaving mDNS multicast group on interface wlan0_rename.IPv4 with address 192.168.50.151.
Jan 26 20:06:50 Hannibal avahi-daemon[5025]: Interface wlan0_rename.IPv4 no longer relevant for mDNS.
Jan 26 20:06:50 Hannibal NetworkManager: <info>  Activating device wlan0_rename 
Jan 26 20:06:50 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 26 20:06:50 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 1 of 5 (Device Prepare) started... 
Jan 26 20:06:50 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 2 of 5 (Device Configure) scheduled... 
Jan 26 20:06:50 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 1 of 5 (Device Prepare) complete. 
Jan 26 20:06:50 Hannibal NetworkManager: <info>  (wlan0_rename) Supplicant interface state change: 2 -> 0 
Jan 26 20:06:50 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 2 of 5 (Device Configure) starting... 
Jan 26 20:06:50 Hannibal NetworkManager: <info>  Activation (wlan0_rename/wireless): access point 'Auto OpenWrt' has security, but secrets are required. 
Jan 26 20:06:50 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 2 of 5 (Device Configure) complete. 
Jan 26 20:06:50 Hannibal NetworkManager: Missing or invalid key management
Jan 26 20:06:50 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 26 20:06:50 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 1 of 5 (Device Prepare) started... 
Jan 26 20:06:50 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 2 of 5 (Device Configure) scheduled... 
Jan 26 20:06:50 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 1 of 5 (Device Prepare) complete. 
Jan 26 20:06:50 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 2 of 5 (Device Configure) starting... 
Jan 26 20:06:50 Hannibal NetworkManager: <info>  Activation (wlan0_rename/wireless): connection 'Auto OpenWrt' has security, and secrets exist.  No new secrets needed. 
Jan 26 20:06:50 Hannibal NetworkManager: <info>  Config: added 'ssid' value 'OpenWrt' 
Jan 26 20:06:50 Hannibal NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Jan 26 20:06:50 Hannibal NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Jan 26 20:06:50 Hannibal NetworkManager: <info>  Config: added 'proto' value 'WPA RSN' 
Jan 26 20:06:50 Hannibal NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP' 
Jan 26 20:06:50 Hannibal NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP' 
Jan 26 20:06:50 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 2 of 5 (Device Configure) complete. 
Jan 26 20:06:50 Hannibal NetworkManager: <info>  Config: set interface ap_scan to 1 
Jan 26 20:06:50 Hannibal NetworkManager: <info>  (wlan0_rename) Supplicant interface state change: 0 -> 2 
Jan 26 20:07:15 Hannibal NetworkManager: <info>  Activation (wlan0_rename/wireless): association took too long, asking for new key. 
Jan 26 20:07:15 Hannibal NetworkManager: <info>  (wlan0_rename) Supplicant interface state change: 2 -> 0 
Jan 26 20:17:54 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 26 20:17:54 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 1 of 5 (Device Prepare) started... 
Jan 26 20:17:54 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 2 of 5 (Device Configure) scheduled... 
Jan 26 20:17:54 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 1 of 5 (Device Prepare) complete. 
Jan 26 20:17:54 Hannibal NetworkManager: <info>  Activation (wlan0_rename) Stage 2 of 5 (Device Configure) starting... 
Jan 26 20:17:54 Hannibal NetworkManager: <info>  Activation (wlan0_rename/wireless): connection 'Auto OpenWrt' has security, and secrets exist.  No new secrets needed. 
```

---

### Post by pochu on 2008-01-26
I have some problems with the wireless since I upgraded these packages. The network stops working randomly, although the connection is good (> 60%). It usually comes back after a few seconds (10 or 20)...

Perhaps this is related:

emilio@pochu:~$ tail /var/log/syslog
Jan 26 20:41:58 pochu NetworkManager: <info>  (eth0) Supplicant interface state change: 7 -> 6 
Jan 26 20:41:58 pochu NetworkManager: <info>  (eth0) Supplicant interface state change: 6 -> 7 
Jan 26 20:42:08 pochu NetworkManager: <info>  (eth0) Supplicant interface state change: 7 -> 6 
Jan 26 20:42:08 pochu NetworkManager: <info>  (eth0) Supplicant interface state change: 6 -> 7 
Jan 26 20:42:18 pochu NetworkManager: <info>  (eth0) Supplicant interface state change: 7 -> 6 
Jan 26 20:42:18 pochu NetworkManager: <info>  (eth0) Supplicant interface state change: 6 -> 7 
Jan 26 20:42:28 pochu NetworkManager: <info>  (eth0) Supplicant interface state change: 7 -> 6 
Jan 26 20:42:28 pochu NetworkManager: <info>  (eth0) Supplicant interface state change: 6 -> 7 
Jan 26 20:42:38 pochu NetworkManager: <info>  (eth0) Supplicant interface state change: 7 -> 6 
Jan 26 20:42:38 pochu NetworkManager: <info>  (eth0) Supplicant interface state change: 6 -> 7 
emilio@pochu:~$

---

### Post by jbrnd on 2008-01-26
Works well for me (amd64, bcm43xx wireless, tg3 wired). Except one thing: nm-vpn-properties segfaults when I try to configure a vpnc connection. The segfault happens when I click the Forward button after choosing vpnc connection type. Maybe this is related to the fact that the network-manager-vpnc package is still at 0.6.4svn2422-0ubuntu4 ?

Running nm-vpn-properties under gdb gives me

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 47571492818208 (LWP 16103)]
0x00002b4417d11888 in g_type_check_instance_is_a ()
   from /usr/lib/libgobject-2.0.so.0

---

### Post by lsmobrian on 2008-01-26
Works great for me under wpa

- nm-vpnc breaks when adding a connection
nm-vpn-properti[7301]: segfault at 00000000 eip b5eff2dc esp bfed67c0 error 6

- edit connections(right click) appears to do nothing 
          is this the same as manual config? (left click)

  *-network
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:c0:49:fc:59:02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.24-5-generic ip=192.168.10.10 latency=64 link=yes module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

---

### Post by MacUntu on 2008-01-27
After yesterdays updates (too bad I can't remember details) it finally works (WPA2, iwl3945). 

Storing the password seems to work fine:
* Not asked for a password after login.
* Not asked for a password after resuming from suspend.
* Asked to unlock the keyring after resuming from hibernate. - Don't know if that's necessary. EDIT: But not every time? Just tried that again and it worked, next time I had to unlock the keyring again. Strange.

---

### Post by tormod on 2008-01-27
I rebuilt the packages for Gutsy. They didn't work for me, but if somebody wants to try them, they are at [http://tormod.webhop.org/linux/network-manager/](http://tormod.webhop.org/linux/network-manager/)

---

### Post by RAOF on 2008-01-27
VPN setup is broken - both OpenVPN and vpnc crash once you press "next" in the VPN setup dialog.

Apport crash files available on request.

---

### Post by mabovo on 2008-01-28
Sorry to post a silly question here but ...

I removed the netmon applet from gnome panel and don't know how to restore to its original place on top panel.

To check wireless connection I installed netmon-applet and netspeed-applet but I am missing  the non workable functions of nm-0.7 applet in gnome-panel. :)

Thanks.

---

### Post by asac on 2008-01-28
> **RAOF said:**
> VPN setup is broken - both OpenVPN and vpnc crash once you press "next" in the VPN setup dialog.

Apport crash files available on request.

vpn needs to be upgraded. the current packages won't work. stay tuned.

---

### Post by asac on 2008-01-28
> **Mike said:**
> I did get network manager work, but do have to restart network-manager every time I reboot.

```
sudo /etc/init.d/NetworkManager restart
```

This should be fixed in 0.7~~svn20080121t191418+eni1-0ubuntu0~pre7, which should be in my ppa in about an hour or so.

Thanks for testing this,

 - Alexander

---

### Post by asac on 2008-01-28
> **VenkateshSrinivas said:**
> Hi,

I installed it here, had a few problems:
* First, I needed to loosen some dbus settings to get NetworkManager-applet to start; in /etc/dbus-1/system.d/NetworkManager.conf, I needed to allow the console user to own org.freedesktop.NetworkManager, and in nm-applet.conf I needed to allow the console user to own org.freedesktop.NetworkManagerUserSettings.


maybe you denied dpkg to overwrite your previous configuration? for instance, nm-applet.conf shipped by network-manager-gnome allows console to own the NetworkManagerUserSettings.

anyway, maybe try to run apt-get install --reinstall network-manager network-manager-gnome and use the maintainers configuration when being asked on what to do.

Thanks,
  - Alexander

---

### Post by ntetreau on 2008-01-28
I can confirm that NM-0.7 autostart on my system, other the VPN, it now works as well if not better than 0.65

---

### Post by tribaal on 2008-01-28
Silly question - Is this available for Gutsy x64 or is it really only for Hardy alpha?

TLS/TKIP encryption support was not good with 0.65, I wonder if there is any improvement on this side of things (used to segfault when roaming).

I'll wait until this weekend if I have to upgrade to Hardy to test this package.

Cheers

- Trib'

---

### Post by autocrosser on 2008-01-28
If you look at his site, he has a updated .65 for download also--you might give it a try......

---

### Post by cantas on 2008-01-28
Where do I find the configuration of the networks with the saved passwords? I was looking in gconf-editor and I couldn't find anything but previous configurations related to nm 0.6.5, that do not affect nm 0.7.
I have a network that has two saved values and I'd like to remove one (there are two "auto SSID" in my choice of networks)

---

### Post by Technoviking on 2008-01-28
nm 0.7 is working great now. I have not tested vpn yet.

---

### Post by F-3582 on 2008-01-28
Same here. I use an IPW2200 WLAN card and it looks like everything works perfectly. The time it takes to establish a wireless network has greatly reduced, too.

---

### Post by cantas on 2008-01-28
Where do I find the configuration of the networks with the saved passwords? I was looking in gconf-editor and I couldn't find anything but previous configurations related to nm 0.6.5, that do not affect nm 0.7.
I have a network that has two saved values and I'd like to remove one (there are two "auto SSID" in my choice of networks)

EAP-TTLS does not work at University of Illinois at Chicago. The network is disconnected immediately, it doesn't even start the authentication process. Same parameters as my custom wpa_supplicant script

---

### Post by F-3582 on 2008-01-28
You find it in the Seahorse application (a nice gui for editing GPG keys and keyring passwords) or directly in the Keyring Manager (somewhere at System->Preferences or Aministration).

Seahorse is a lot more comfortable, by the way.

By the way, there is one thing that bothers me. Whenever I try to make NetworkManager store a password in the keyring, I have to open the Keyring Manager in order to make the "Grant NetworkManager access to the keyring" dialog appear. Any suggestions? I've been having this issue since Gutsy at some point.

---

### Post by cantas on 2008-01-28
Good! I already had it but I never thought it could be there. For NM 0.6.5 it was sufficient to use gconf-editor.

Now I have to solve the connection problem with EAP-TTLS.

---

### Post by cantas on 2008-01-28
That eliminated the saved secrets, but did not remove the networks tagged as "auto" from the list in network manager

---

### Post by mabovo on 2008-01-28
No wireless connection after recent upgrades. 
NM-0.7 doesn't work anymore only wired now.
Wireless card Atheros 5418 with D-Link DI-624 router using WPA-2 or WPA don't connect.

---

### Post by MacUntu on 2008-01-28
Still working fine for me (iwl3945/WPA2).

---

### Post by mabovo on 2008-01-28
I am wired and the applet is showing "no connection" or "network disabled" something ?

---

### Post by mauddib on 2008-01-29
Hi,

does this yet work with ppp?

has anyone tried it with cdma/gsm devices? I think that is part of this build..

only "VPN Connections" is showing up in nm applet..?

---

### Post by BurnHead on 2008-01-29
I can confirm  the problems connecting to WPA/WPA2 protected networks. NM tries to connect to my router (Fritz!Box Fon WLAN 7140), but after a few seconds it just says that it couldn't connect (and as far as I can see, it's because it didn't get an IP adress). Wired network is working fine though.

Still using an Atheros AR5007EG based card with ndiswrapper 1.51.

Cheers.

---

### Post by MacUntu on 2008-01-29
> **mabovo said:**
> I am wired and the applet is showing "no connection" or "network disabled" something ?

Although wired networking works, I'm getting the same symbol (the monitor with "x").

---

### Post by mabovo on 2008-01-29
I also tried to configure through the applet but system display a message that I don't have permission to change the network configuration and still no wireless connection in AR5418.

---

### Post by donspaulding on 2008-01-29
I just installed NM 0.7 today (the 1/28 build) with all the dependencies and it works like a charm (well, nm-applet core dumped on me the first time I ran it, but worked fine two seconds later)!  It detects the networks I use as "auto" and is blazing fast compared to 0.6.  Wifi and wired connections both work.

Lenovo T61
iwl4965 a/b/g/n
wpa2 wifi

I'll try it out again on a WEP network tonight, just to see how it goes.

Also, I love the cleaner look of the wifi browser.  Looks great! :)

EDIT:  NM 0.7 works seamlessly for me across WPA2, WEP, and wired connections. I haven't had to think about connecting any of my networks over the past 2 days, they all Just Work (tm). This is how ubuntu+NM was meant to be.

---

### Post by nicweb on 2008-01-30
No problems at all with ipw2200 / wpa and open wifis and wired connection...

---

### Post by mabovo on 2008-01-31
NM0.7 shows ssid but when I try to connect it keeps asking for my passphrase indefinitely.

```

mabovo@macbook:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:15:E9:79:52:9E
                    ESSID:"mabovo"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-60 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:ath_ie=dd0900037f01010006ff7f
mabovo@macbook:~$ sudo lshw -class network
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 22
       serial: 
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=half firmware=N/A ip=192.168.0.4 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=10MB/s
  *-network
       description: Wireless interface
       product: AR5418 802.11a/b/g/n Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wifi0
       version: 01
       serial: 00:1b:63:05:81:11
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g

```

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/122703](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/122703)

---

### Post by MadMan2k on 2008-01-31
no problems with nm0.7 here. on contrary, since I use it connection speed with b43 went up from 1-5Mbit to 23-54Mbit.
But this might also be the new wpa_supplicant.

---

### Post by yelo3 on 2008-01-31
All right with ipw2200 works great!

---

### Post by mabovo on 2008-01-31
I am posting here my dmesg.
It seems that there are some misundertood between wifi0 and ath0 and possible conflict with madwifi and ndiswrapper installed together.

---

### Post by pochu on 2008-01-31
Every time I reboot my /etc/resolv.conf (where my DNS are) is cleaned out, so I need to enter it again (I do it through network-admin).

This wasn't happening with network-manager 0.6.

```

           *-network:0
                description: Wireless interface
                product: PRO/Wireless 2200BG Network Connection
                vendor: Intel Corporation
                physical id: 4
                bus info: pci@0000:06:04.0
                logical name: eth0
                version: 05
                serial: 00:16:6f:a3:c2:37
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=32 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated
           *-network:1
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 8
                bus info: pci@0000:06:08.0
                logical name: eth1
                version: 10
                serial: 00:16:36:5f:67:53
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.34 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
```

---

### Post by donspaulding on 2008-01-31
> **donspaulding said:**
> 
Lenovo T61
iwl4965 a/b/g/n
wpa2 wifi

I'll try it out again on a WEP network tonight, just to see how it goes.


NM 0.7 works seamlessly for me across WPA2, WEP, and wired connections.  I haven't had to think about connecting any of my networks over the past 2 days, they all Just Work (tm).  This is how ubuntu+NM was meant to be.

---

### Post by lime4x4 on 2008-01-31
well it shouldn't be working on my machine but i do have internet connection. the applet at the top says no connection. Plus it only uses one of my nic cards cause hardy doesn't seem to like my nvdia ethernet cards.hardy didn't use the nvidia ethernet cards before updating network-manager that is why i have a linksys card installed (old reliable...lol)

00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
04:06.0 Ethernet controller: Lite-On Communications Inc LNE100TX (rev 20)

john@john-hardy:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: LNE100TX
       vendor: Lite-On Communications Inc
       physical id: 6
       bus info: pci@0000:04:06.0
       logical name: eth2
       version: 20
       serial: 
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 latency=32 module=tulip multicast=yes
  *-network:0
       description: Ethernet interface
       physical id: 2
       logical name: br0
       serial: 
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=192.168.1.102 multicast=yes
  *-network:1
       description: Ethernet interface
       physical id: 3
       logical name: vbox0
       serial: 
       capabilities: ethernet physical
       configuration: broadcast=yes driver=tun driverversion=1.6 firmware=N/A multicast=yes
  *-network:2
       description: Ethernet interface
       physical id: 4
       logical name: vbox1
       serial:
       capabilities: ethernet physical
       configuration: broadcast=yes driver=tun driverversion=1.6 firmware=N/A multicast=yes
john@john-hardy:~$ x


john@john-hardy:~$ ifconfig
br0       Link encap:Ethernet  HWaddr   
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:ccff:fed9:2b24/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1699 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1313 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1293977 (1.2 MB)  TX bytes:279166 (272.6 KB)

eth0      Link encap:Ethernet  HWaddr   
          inet addr:192.168.1.108  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:213 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr   
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe7d:6b99/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:27313 (26.6 KB)
          Interrupt:214 Base address:0x8000 

eth2      Link encap:Ethernet  HWaddr  
          inet6 addr: fe80::2a0:ccff:fed9:2b24/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1706 errors:1 dropped:0 overruns:0 frame:0
          TX packets:1333 errors:3 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:1318820 (1.2 MB)  TX bytes:282655 (276.0 KB)
          Interrupt:20 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1316 (1.2 KB)  TX bytes:1316 (1.2 KB)

vbox0     Link encap:Ethernet  HWaddr   
          inet6 addr: fe80::2ff:71ff:feed:1a7b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:298 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vbox1     Link encap:Ethernet  HWaddr   
          inet6 addr: fe80::2ff:50ff:fe2e:7f6a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:298 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

john@john-hardy:~$

---

### Post by omha on 2008-01-31
just installed it and after a reboot my network worked PERFECT!!! i have never been so fast connected, i used to need to manually turn wifi on and off, not any more thanks nm-0.7!

eveythings seem stable, vpn does not work because the packages are built against 0.6



Edit, this should actually be in the other topic, sorry.

---

### Post by lewmnik on 2008-02-03
:) This is really great news, I hope you'll get stable enough. Is there a chance to get version that works with knetworkmanager also? That would be really great!

---

### Post by lewmnik on 2008-02-03
On an edubuntu hardy Dell latitude d510
```
  
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth1
       version: 05
   
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=10.11.2.82 latency=64 link=yes maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g

```

Edubuntu on Compaq desktop: both wireless and ethernet work well!
```
  *-network:0             
       description: Wireless interface
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: b
       bus info: pci@0000:02:0b.0
       logical name: wmaster0
       version: 01
       serial: 
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=prism54pci ip=10.11.2.83 latency=64 maxlatency=28 mingnt=10 module=p54pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: d
       bus info: pci@0000:02:0d.0
       logical name: eth0
       version: 74
       serial: 
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full latency=64 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=100MB/s
 
```

It Just Works™!

---

### Post by _tom_ on 2008-02-04
nm 0.7 works great on a HP nx7400 notebook (iwl3945 driver) and a workstation with a 3Com USB OfficeConnect Adapter (zd1211rw driver). The connection to a WPA encrypted is established very fast and the connection is very stable.

So +1 for inclusion in hardy

---

### Post by lonniehenry on 2008-02-04
nm 0.7 works after a reboot with WEP on my hardy test laptop.  Faster connection and stable.  Edit connections doesn't do anything. Haven't tryed VPN

---

### Post by djspirit on 2008-02-05
works fine for me on a dell laptop d820, iwl3945 driver

anyway to setup 802.1.x on  wired devices ?

---

### Post by Vadi on 2008-02-05
Worked perfect on ndiswrapper, net8185 driver

---

### Post by omha on 2008-02-06
I have problems with nm-0.7 remembering my schools WPA/PEAP config, my home WEP works great

okay, its official, im a forum n00b.

---

### Post by mabovo on 2008-02-06
NM-0.7 works great on wired network but can't do the same job on wireless. 
It detects the AP (D-Link DI-624 with WPA2) asks for the wireless network security password with WPA & WPA2 Personal enabled in the first box and tries to connect.
After a few seconds it returns asking to type the password again and again.
  *-network
       description: Wireless interface
       product: AR5418 802.11a/b/g/n Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wifi0
       version: 01
       serial:
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g

---

### Post by der_vegi on 2008-02-06
NM 0.7 works so far fine for me. I am using an unencrypted network with vpnc connection. Okay, obviously network-manager-vpnc does not work with 0.7, but vpnc from terminal does.
My system: Hardy amd64 with all updates applied until today, Dell Inspiron 1501.  Here the output of
```
lshw -class network
```
```
  *-network               
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0_rename
       serial: 
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=10.9.26.24 multicast=yes wireless=IEEE 802.11g

```
There is another unencrypted network though, where I can hardly connect and it disconnects after a few seconds. I'll try to track this further in a couple of days.

Edit: I am using the b43 driver.

---

### Post by tensop on 2008-02-06
Fails connecting to eduPaSS 801.x dynamic WEP after first successful connection

---

### Post by mabovo on 2008-02-06
After modifying wpa_supplicant.conf I could finally connect to the wireless network but still network-manager icon indicates that none networking devices were found on system. ???
  *-network
       description: Wireless interface
       product: AR5418 802.11a/b/g/n Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wifi0
       version: 01
       serial: 
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.10.131 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
mabovo@macbook:~$

---

### Post by decoherence on 2008-02-06
Upgraded to hardy from gutsy with an Averatec 2370 initially set up (a while ago) with the directions at [http://ubuntuforums.org/showthread.php?t=308152&highlight=averatec](http://ubuntuforums.org/showthread.php?t=308152&highlight=averatec)

In gutsy the wireless worked only some of the time. Sometimes it would drop the connection after a few minutes, sometimes it would refuse to connect at all. This is with no encryption.

After upgrading to the 8.04 branch I was pleasantly surprised with solid wireless. Uptime of three days so far -- unheard of before.

Don't really know if it has anything to do with nm or if it's new drivers for the ralink wireless, but in any case nm is doing its job properly and the strangeness has stopped.

```
decoherence@averatec:~$ lsmod | grep rt

...
rt73usb                27136  0 
rt2x00usb              12800  1 rt73usb
rt2x00lib              22528  2 rt73usb,rt2x00usb
rfkill                  8208  1 rt2x00lib
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
mac80211              163480  2 rt2x00usb,rt2x00lib
agpgart                34760  1 nvidia
usbcore               145516  5 rt73usb,rt2x00usb,ohci_hcd,ehci_hcd

```

The network has no (visible) security... all unencrypted. I'll be setting up WPA/AES soon and will post if there's anything interesting.

:guitar:

---

### Post by oponek on 2008-02-07
The new version works for me (rt2400 card) in Hardy! :-)

---

### Post by tribaal on 2008-02-07
NetworkManager works fine, but unfortunately nm-applet won't autostart.

It works fine once I launch it by hand and keep a terminal open.
Somehow, launching the applet with & makes it work, until I close the terminal (which is weird).

- Trib'

---

### Post by MacUntu on 2008-02-07
A little feedback would be nice. :)

---

### Post by tribaal on 2008-02-07
> **MacUntu said:**
> A little feedback would be nice. :)

Isn't that what this post is all about?

- trib'

---

### Post by mabovo on 2008-02-07
AR5418 Atheros with Madwifi is very unstable with NM-0.7.
It disconnects after an interval of use (maybe two or three hours after made connection).
I guess it depends on having the driver attached inside the kernel ?

Hope that it comes available on time for Hardy :(

---

### Post by MacUntu on 2008-02-07
> **tribaal said:**
> Isn't that what this post is all about?

- trib'

I ment feedback from the ones we're giving feedback. :)

---

### Post by henrique on 2008-02-07
mabovo: Can you post the configuration changes, please?

---

### Post by VenkateshSrinivas on 2008-02-07
For what its worth, this also works great on Debian Testing. =)

I still have problems with 'Manual Configuration'; has anyone been able to get that working?

---

### Post by mabovo on 2008-02-07
In fact I removed all supplicant configuration files from /etc and /etc/wpa_supplicant also eliminated all entries from interfaces and renewed the wireless networking.
Every day I update madwifi driver from snapshots.madwifi.org and expect that a new version of nm-0.7 could be released to solve this pigtail.

[   34.669583] ath_hal: module license 'Proprietary' taints kernel.
[   34.671696] ath_hal: 0.9.30.13 (AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133)
[   34.898507] wlan: svn r3344
[   34.926679] usb 1-4: USB disconnect, address 3
[   34.969975] ath_pci: svn r3344
[   34.970040] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   34.970053] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   35.135343] MadWifi: ath_attach: Switching rfkill capability off
[   35.225755] appletouch: Geyser mode initialized.
[   35.225816] input: appletouch as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/input/input11
[   35.276754] usbcore: registered new interface driver appletouch
[   35.278351] ath_rate_sample: 1.2 (svn r3344)
[   35.278490] MadWifi: ath_attach: Switching per-packet transmit power control off
[   35.278787] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   35.278794] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   35.278798] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   35.278805] wifi0: turboG rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   35.278811] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   35.278817] wifi0: ath_announce: Use hw queue 1 for WME_AC_BE traffic
[   35.278819] wifi0: ath_announce: Use hw queue 0 for WME_AC_BK traffic
[   35.278821] wifi0: ath_announce: Use hw queue 2 for WME_AC_VI traffic
[   35.278823] wifi0: ath_announce: Use hw queue 3 for WME_AC_VO traffic
[   35.278825] wifi0: ath_announce: Use hw queue 8 for CAB traffic
[   35.278827] wifi0: ath_announce: Use hw queue 9 for beacons
[   35.416922] ath_pci: wifi0: Atheros 5418: mem=0x50100000, irq=17
[   35.417025] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   35.417039] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   35.418053] sky2 0000:01:00.0: v1.20 addr 0x50200000 irq 16 Yukon-EC (0xb6) rev 2
[   35.418503] sky2 eth0: addr 00:17:f2:df:89:b5

---

### Post by mabovo on 2008-02-07
interfaces
> 
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

auto ath0
iface ath0 inet dhcp

Auto eth0
iface eth0 inet dhcp


wpa_supplicant.conf
> 
ctrl_interface=/var/run/wpa_supplicant
network={
        ssid="mabovo"
	scan_ssid=1
	proto=WPA RSN
	pairwise=CCMP TKIP
	key_mgmt=WPA-PSK
	group=CCMP TKIP
        psk=<snip>
}


---

### Post by Moop on 2008-02-07
Network Manager 0.7 works great for me on Hardy 64bit. 
WPA2
```
*-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 8
       bus info: pci@0000:07:08.0
       logical name: wmaster0
       version: 00
       serial: 
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g
```

---

### Post by MacUntu on 2008-02-07
@mabovo:

I always thought nm needs interfaces to only contain 

> auto lo
iface lo inet loopback

?

---

### Post by mabovo on 2008-02-07
I just followed the tips on here:
[http://ubuntuforums.org/showthread.php?t=263136&page=12](http://ubuntuforums.org/showthread.php?t=263136&page=12)

Should D-Bus be upgraded to 1.2.0 in order to nm-0.7 recognizes my AP D-Link DI-624 ?
Why it keeps asking for my password without connect to wireless ?

---

### Post by ntetreau on 2008-02-08
I had to go back to NM 0.6.5 for lack of VPN in 0.7.  Could you please package the VPN plugins as well?

---

### Post by luksmann on 2008-02-09
After upgrading I still experience the same problem as before...

Although my Belkin router is detected I can't connect to it. As soon as I move one room further towards the AP connections works fine. Even when I walk back to my room. 

I am using a Intel Corporation PRO/Wireless 3945ABG Network Connection.

Also my W-Lan connection is namend wlan0_rename, and NM Config always shows 3 cabel connections and no Wlan interface.

```

 *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: XX:XX:XX:XX:XX:XX
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.2.3 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

```

---

### Post by mabovo on 2008-02-09
Downgrading to NM 0.6.5 for lack of feedback.

If testing is required please give a few more tips.

I think it is a wasting of time considering [https://wiki.ubuntu.com/HardyReleaseSchedule](https://wiki.ubuntu.com/HardyReleaseSchedule) 

Thanks.

---

### Post by drobvice on 2008-02-09
After upgrade to Hardy from a relatively fresh, clean install and up-to-date Gutsy on my Toshiba laptop, Network Manager does not show my wireless connection at all.  Only wired and modem (I think).  This worked perfectly in Gutsy.

Edit - Sorry, I misunderstood.  I thought this was part of the Hardy packages applied during upgrade.  I still have 0.6~

---

### Post by kjbuente on 2008-02-09
Just reporting in saying that I am not able to connect to a WPA or WPA2 with my wireless card. Just always asks for the key. Perhaps a problem with wpasupplicant? I'm Using latest madwifi driver, have not tried the new ath5k drivers. Have not tried Open or WEP yet. 

Hardware info:

```
  *-network:0             
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications, Inc.
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: wifi0
       version: 01
       serial: [REMOVED]
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=96 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

```

---

### Post by mabovo on 2008-02-09
Amazingly downgrading to nm-0.6.5 could finally connect to wireless network. 
  *-network
       description: Wireless interface
       product: AR5418 802.11a/b/g/n Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wifi0
       version: 01
       serial:
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.10.131 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
mabovo@macbook:~$

---

### Post by napsy on 2008-02-11
Besides that "Edit connections" option NM 0.7 works for me perfectly. The only thing I miss is a refresh option to manually refresh the network list.

---

### Post by hardawayd on 2008-02-12
I finally got the nm 0.7 installed on my Macbook Pro with the lates Hardy files updated and still when i click to configure the network it only shows my wired and modem entries.  How do you add wireless???

---

### Post by Technoviking on 2008-02-12
> **napsy said:**
> Besides that "Edit connections" option NM 0.7 works for me perfectly. The only thing I miss is a refresh option to manually refresh the network list.
Same here, I'm guessing that is a problem with PolicyKit rather than nm 0.7.

---

### Post by kjbuente on 2008-02-12
Reporting Back, Finally had some time to test on an open wifi.

It seems that all wireless is out. I can not connect with my AP being Open,WEP,WPA, or WPA2. Nothing works, it worked nicely with 0.6.5. (Not complaining, I'm just stating). Also when I tried to connect though terminal, I get authorization time outs with my MAC. After a while the MAC goes to all zeros. (Atheros mPCI card, using latest SVN snapshot).

I also seem to have problems with PPP. I Use a connection though my phone normally though GnomePPP. I tried to configure it in nm-applet, and did it wrong. Now when I go and try to change the settings. It says that I am not allowed to do so. Perhaps this is not an issue with NM, but actually PolicyKit not unlocking the need file?

---

### Post by mabovo on 2008-02-12
On my MacBook with Atheros ar5418, NM0.7 detects the network, request the password and proceed with temptative to connect but after a while it return back asking for the password again.
Attached a figure with the router D-Link DI-624 configuration linked with a cable modem Motorola SBV5120 Surfboard.

---

### Post by mabovo on 2008-02-12
> **Mike said:**
> Same here, I'm guessing that is a problem with PolicyKit rather than nm 0.7.
I would go further suggesting this could be a lack of integration between dbus and hal with network-manager !

---

### Post by kjbuente on 2008-02-12
I wanted to add to the supported working wireless devices. I have a USB wireless stick that I use to go war driving. This works well in NM.7. It is a Zydas chipset, but lshw does not show any useful info about it.

I want to say that NM.7 works great with it so far, could not believe how fast it authenticated! Just wish the Atheros chips worked. (Also wish I could code, and knew tomorrow lottery number :)) If I find another chipset to test, I'll post back...

Update:
I just noticed that nm-applet had crashed. I can replicate it when I use GNOMEPPP to surf the web and I plug in my USB Zydas stick. Got to love fresh code, eh? :)

---

### Post by mabovo on 2008-02-13
Atheros chipsets will be integrated only in Itch Iguana.

---

### Post by mabovo on 2008-02-13
After today upgrades nm-0.7 display  duplicated information.

---

### Post by kjbuente on 2008-02-13
Mabovo, have you tried to recompile the kernel with the Atheros driver built-in instead of as a module? I have yet to try since I'm always low on time. After you compile the driver for your machine, there should be a folder that has a script that will allow you to do this. I do not know if you have to remove the module or if it would do it for us. Another reason that I have not done this is since we are most likly to recive some kernel updates still, I'd have to do this every time we get an update.

---

### Post by mabovo on 2008-02-13
I  patched  madwifi driver i kernel 2.6.24-7 cause I prefer not to recompile it and wait for the modules being released as standard.
Atheros madwifi driver has a bug filled to eliminate this patch for Hardy and insert it direct into kernel.

---

### Post by nicweb on 2008-02-14
Now that feature freeze is active, does that mean there's no chance that 0.7 will hit hardy repos?

---

### Post by mabovo on 2008-02-14
Yeahp !

---

### Post by F-3582 on 2008-02-14
There are Freeze Exceptions for such cases.

---

### Post by mabovo on 2008-02-14
I like that :)

Maybe ath5k could be on time too ?

---

### Post by quackking on 2008-02-14
Hi, Hardy Alpha 4 on Thinkpad T40-2373 - the WiFi card is Atheros 5212. NM doesn't detect the card, and in fact all the interfaces come up grayed out. I am having no luck with Ubuntu and WiFi on this laptop. WiFi Radar does seem to see networks in the area, but I can't connect (this is using a 13-character WPA key.)

I  hope this gets fixed!

---

### Post by mabovo on 2008-02-14
Install the latest driver from Madwifi org at [http://downloads.sourceforge.net/madwifi/madwifi-0.9.4.tar.gz](http://downloads.sourceforge.net/madwifi/madwifi-0.9.4.tar.gz) or follow this howto on [http://ubuntuforums.org/showpost.php?p=2731459&postcount=25](http://ubuntuforums.org/showpost.php?p=2731459&postcount=25)

---

### Post by pochu on 2008-02-14
> **nicweb said:**
> Now that feature freeze is active, does that mean there's no chance that 0.7 will hit hardy repos?
14:37 <     pochu> asac: will we see NM 0.7 in Hardy?
14:37 <      asac> pochu: we decided to not do it.
14:38 <      asac> we kept the option to reconsider if upstream does a final release soon
14:38 <      asac> (but unlikely)


Hope that clarifies.

---

### Post by ThomasNovin on 2008-02-15
Hello.

I have bug 159064 on Launchpad. I have moved it affect linux-ubuntu-modules-2.6.24 but after reading [https://bugzilla.novell.com/show_bug.cgi?id=269747](https://bugzilla.novell.com/show_bug.cgi?id=269747) maybe it is NetworkManager related after all? What do you think?

Sometimes it works for me but mostly it doesn't.

---

### Post by mabovo on 2008-02-15
I would say that network-manager 0.7  is causing all this instability on my system...

After every line with gdm, Compiz or npviewer "segfault" is followed by a line with Sky2 eth0: disabling interface.

---

### Post by ThomasNovin on 2008-02-15
> **mabovo said:**
> I would say that network-manager 0.7  is causing all this instability on my system...

What makes you say that?

---

### Post by mabovo on 2008-02-15
> **23meg said:**
> Please test and report bugs and your experiences **in this thread** (and **not the network-manager source package in Launchpad**). Remember to cite the chipset and driver of your network hardware, and the encryption standard you're using (WEP, WPA or WPA2).[COLOR="White"](No, you shouldn't be using WEP.)[/COLOR]
[SIZE="3"]**Be warned: this will probably break your networking at some point. Make sure you know how to recover before going ahead.**[/SIZE]

It is not a complain and I also expect some crashes too.

---

### Post by mattismyname on 2008-02-17
Any benefit testing w/ the following config?  (I don't want to risk the breakage if it's not going to be any benefit to you.)

thanks

```
  *-network               
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: a
       bus info: pci@0000:02:0a.0
       logical name: eth0
       version: 10
       serial: 00:40:05:xx:xx:xx
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.101 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
```

---

### Post by mabovo on 2008-02-18
If it's working with nm-0.6.5 so has nothing to be fixed ! :)

---

### Post by ^Albe^ on 2008-02-18
does this nm7 avoid the insertion of the master keyring key for connect to a wpa lan?
i think that it is secure, but is really annoing

regards, and thx for ubuntu

---

### Post by Nicks Spleen on 2008-02-18
Just upgraded today, everything working fine after reboot.

```
$ lshw -class network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: <removed>
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: <removed>
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.102 multicast=yes wireless=IEEE 802.11g

```

---

### Post by ThomasNovin on 2008-02-19
> **^Albe^ said:**
> does this nm7 avoid the insertion of the master keyring key for connect to a wpa lan?
i think that it is secure, but is really annoing

regards, and thx for ubuntu

That is no longer an issue in Hardy.

---

### Post by ^Albe^ on 2008-02-19
> **ThomasNovin said:**
> That is no longer an issue in Hardy.

sorry the ot
but i have always the keyring password request switching from wired to wireless
any trick for remove that question?
(this pc running hardy)
regards

---

### Post by mabovo on 2008-02-20
> **^Albe^ said:**
> sorry the ot
but i have always the keyring password request switching from wired to wireless
any trick for remove that question?
(this pc running hardy)
regards

Same here, and I still have to restart /etc/init.d/networking every reboot and sudo dhclient eth0 to get ip address.

I think something has broken in network-manager after yesterday updates causing breakage in packages like bzrtools, python-central and jockey-common.

---

### Post by MadMan2k on 2008-02-20
at least for me the new network-manager gave a great speed increase (1Mbit <> 54Mbit) is there a possibilty that those packages will be kept up to date?

---

### Post by Laervian on 2008-02-21
Just installed here in Gutsy (I made a swift upgrade of some packages and then used the ppa). I have still to test it - right now I am using Internet through a 3g (Vodafone) connection. And here comes in the request: in Windows Vista, whatever means one uses to connect to internet, settings and connection can be accessed always through the same program. This means that, for example, the tray icon does signal connection enabled whatever kind of connection I am using.

On the other hand, nm-applet does signal connection only if i connect THROUGH that program.

Simple question then: would it be possible to render it more Vista-like? I find that feature quite good. :)

---

### Post by mabovo on 2008-02-21
After 4 weeks , new kernel released and 130 posts since we started testing nm-0.7, there is no updates on network-manager or wpasupplicant packages.

I don't know if I stick with nm-0.7 expecting some kind of support to my wireless card AR5418 or focus my attention to more interesting issues to solve/test in Hardy.

Any chance to go ahead with nm-0.7 ?

---

### Post by JamesUser on 2008-02-22
For me, WPA2 works fine out of the box. Am writing this from a live cd session. :-) It's all so painless. Thanks.

I am running Hardy Alpha 4 on a Dell Inspiron 6400 with ipw3945 wireless card. The only glitch is that the wi-fi LED does not glow. I found that a bug has already been logged for that and even a patch is available for testing.

---

### Post by fransex on 2008-02-23
> **kjbuente said:**
> I tried to configure it in nm-applet, and did it wrong. Now when I go and try to change the settings. It says that I am not allowed to do so. Perhaps this is not an issue with NM, but actually PolicyKit not unlocking the need file?

> **mabovo said:**
> I would go further suggesting this could be a lack of integration between dbus and hal with network-manager !

My old computer (kubuntu hardy 8.04 i386 - Athlon), which has a working custom kernel, seems to agree with you two:

```
me@computer$ LC_ALL=EN sudo dpkg --configure -a
Setting up hal (0.5.10-5ubuntu7) ...
 * Reloading system message bus config...
   ...done.
Segmentation fault
Segmentation fault
dpkg: error processing hal (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of kubuntu-desktop:
 kubuntu-desktop depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing kubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 hal
 kubuntu-desktop
me@computer$

```

and the segfault messages produced are, as usual for this ind of bugs, slightly different each time::

```
me@computer$ sudo tail /var/log/messages
Feb 23 05:28:14 localhost kernel: [18366.600414] polkit-auth[11920]: segfault at 00000000 eip 00000000 esp bfb11384 error 4
Feb 23 05:28:14 localhost kernel: [18366.608045] polkit-auth[11922]: segfault at 00000000 eip 00000000 esp bf8ce114 error 4
Feb 23 05:28:22 localhost kernel: [18374.659156] polkit-auth[12549]: segfault at 00000000 eip 00000000 esp bfd4ddc4 error 4
Feb 23 05:28:23 localhost kernel: [18374.694278] polkit-auth[12551]: segfault at 00000000 eip 00000000 esp bfa6eab4 error 4
Feb 23 05:37:31 localhost kernel: [18922.831936] polkit-auth[13004]: segfault at 00000000 eip 00000000 esp bf8410b4 error 4
Feb 23 05:37:31 localhost kernel: [18922.859769] polkit-auth[13006]: segfault at 00000000 eip 00000000 esp bfb743c4 error 4
Feb 23 05:37:40 localhost kernel: [18931.886573] polkit-auth[13672]: segfault at 00000000 eip 00000000 esp bff23794 error 4
Feb 23 05:37:40 localhost kernel: [18931.915071] polkit-auth[13674]: segfault at 00000000 eip 00000000 esp bfd7c5c4 error 4
Feb 23 05:55:07 localhost kernel: [19978.881239] polkit-auth[13754]: segfault at 00000000 eip 00000000 esp bfbf5c74 error 4
Feb 23 05:55:07 localhost kernel: [19978.907253] polkit-auth[13756]: segfault at 00000000 eip 00000000 esp bfa6e204 error 4
me@computer$

```

Did anyone face rhis issue? :confused:

TIA

---

### Post by mabovo on 2008-02-23
This message handler errors evoke problems with dbus too.```

mabovo@macbook:~$ sudo tail /var/log/messages
[sudo] password for mabovo: 
Feb 23 17:41:38 macbook kernel: [  360.993253] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
Feb 23 17:45:33 macbook kernel: [  412.143040] ADDRCONF(NETDEV_UP): ath0: link is not ready
Feb 23 17:45:33 macbook kernel: [  412.146319] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
Feb 23 17:45:38 macbook kernel: [  414.136543] sky2 eth0: Link is down.
Feb 23 17:45:40 macbook kernel: [  415.434258] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
Feb 23 17:45:40 macbook kernel: [  415.436908] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Feb 23 17:45:40 macbook dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Feb 23 17:45:46 macbook dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Feb 23 17:45:46 macbook dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Feb 23 17:45:46 macbook dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
mabovo@macbook:~$ 





```

---

### Post by tekoholix on 2008-02-23
0.6.5 was fine for me under Hardy (Updated 2-4 times a day), until 2 days ago, when some update broke it, making it suddenly show my ham0 and pan0 interfaces, and broke Hamachi VPN.  In fact, the system automatically attempts connection to the ham0 or pan0 on login, will not default to wireless or permit data thru on ham0, no matter what I tried.

Tonight, I decided to take the drastic measure of trying out 0.7, thinking for sure I was screwing the pooch (my bcm94311mcg wifi has been trouble from day one, with Hardy, finally working with ndiswrapper)...

After reboot (as expected), EVERYTHING WORX!!  Hamachi's back, WiFi's up by default, speeds are 3-4Mb faster, etc.  I've not tried any WPA, WEP, anything else yet, but I surely will, in the next few days!!

Thanx a million!!

p.s.:  Unfortunately, seconds after I posted this, I found that the "Edit Connections..." menu entry, for me also, apparently does nothing.  Guess I'll have to wait to see what that does...

New problem:  It seems, unfortunately, that the DNS Servers are not passed by DHCP.  Upon each reboot, I've got to manually add my router's address as DNS, before the connection becomes valid.

---

### Post by Bert Mariën on 2008-02-25
For me the network-manager has never worked for my wireless connection (acx) since I first tried Ubuntu (6.10).
I installed the alpha 5 yesterday, and it still didn't work for me. I always uninstall the network-manager, otherwise I cannot get any wireless connection.

---

### Post by wieman01 on 2008-02-25
> **Bert Mariën said:**
> For me the network-manager has never worked for my wireless connection (acx) since I first tried Ubuntu (6.10).
I installed the alpha 5 yesterday, and it still didn't work for me. I always uninstall the network-manager, otherwise I cannot get any wireless connection.
May I ask what chipset / wireless adapter you have got?

---

### Post by Bert Mariën on 2008-02-26
> **wieman01 said:**
> May I ask what chipset / wireless adapter you have got?

D-Link G520+ (acx driver).

On my other computer the network manager did okay (Belkin adapter).

---

### Post by Bert Mariën on 2008-02-26
One of these weeks I'd like to buy another wireless card, because the G520+ is not recognized by most other distro's. Ubuntu and Ubuntu based distro's normally do recognize the card, but I always need to uninstall the network manager before I can get a connection.

Don't know yet which card I should buy, but it should be a card that is recognized by ALL Linux distro's.

---

### Post by wieman01 on 2008-02-26
> **Bert Mariën said:**
> One of these weeks I'd like to buy another wireless card, because the G520+ is not recognized by most other distro's. Ubuntu and Ubuntu based distro's normally do recognize the card, but I always need to uninstall the network manager before I can get a connection.

Don't know yet which card I should buy, but it should be a card that is recognized by ALL Linux distro's.
Please read this sticky:

[http://ubuntuforums.org/showthread.php?t=370108]("http://ubuntuforums.org/showthread.php?t=370108")

---

### Post by Bert Mariën on 2008-02-26
> **wieman01 said:**
> Please read this sticky:

[http://ubuntuforums.org/showthread.php?t=370108]("http://ubuntuforums.org/showthread.php?t=370108")

Thank You. This will be VERY useful.

---

### Post by mabovo on 2008-02-26
Atheros AR5418 is not in the list, so I have to dual boot with OSX in order to use my wireless card ?

---

### Post by Sammi on 2008-02-26
One question:

Is this the same version and same updates, as discussed here for Fedora 9: [http://fedoraproject.org/wiki/Interviews/DanWilliams](http://fedoraproject.org/wiki/Interviews/DanWilliams) ?

---

### Post by mabovo on 2008-02-26
This article doesn't explain about dhcp and routers.

---

### Post by High Roller on 2008-02-27
> **Sammi said:**
> One question:

Is this the same version and same updates, as discussed here for Fedora 9: [http://fedoraproject.org/wiki/Interviews/DanWilliams](http://fedoraproject.org/wiki/Interviews/DanWilliams) ?

It's a snapshot of NM 0.7 in its semi-current form.  A lot of the features are still in the process of being implemented.

Notice that there's no mention of a "NM 0.7 Final" even after the release of FC 9 at the end of April?

I think it'll be a good call though if they hold off implementing such an unfinished product until it at least has a stable release out the door.  It has been many years in the making...  What's a few more!?  :)

---

### Post by Sammi on 2008-02-27
Thanks for the reply and info.

But I'd like to know more about the upcomming 0.7 milestone. Does anyone know of an article that discusses it in length? (other than reading this tread of course)

---

### Post by anders.ostling on 2008-02-27
vpnc can not be configured with nm 0.7 and the vpn helper program. After selecting vpnc (Cisco compatible) as vpn subsystem in the gui, the program dumps core. 

anders@anders-laptop:~$ /usr/bin/nm-vpn-properties 

(nm-vpn-properties:19946): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(nm-vpn-properties:19946): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(nm-vpn-properties:19946): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(nm-vpn-properties:19946): Gtk-CRITICAL **: gtk_expander_set_expanded: assertion `GTK_IS_EXPANDER (expander)' failed

(nm-vpn-properties:19946): Gtk-CRITICAL **: gtk_container_add: assertion `GTK_IS_WIDGET (widget)' failed
Segmentation fault (core dumped)

Besides from this problem, NM works fine with both wired and wireless (Interl 3945BG) card on my Dell Latitude D620. Have only tested WPA/PSK and WEP

---

### Post by Starks on 2008-02-28
NM 0.7 prevents connections to 802.11a networks

b/g networks are fine

---

### Post by wieman01 on 2008-02-28
> **Starks said:**
> NM 0.7 prevents connections to 802.11a networks

b/g networks are fine
That's most likely not NM but your wireless driver...

---

### Post by Starks on 2008-02-28
Why would that be the case? 802.11a works fine with NM 0.6.5

---

### Post by Darrena on 2008-02-28
Since we are in Freeze now and it doesn't look like .7 will make it is there any chance that 0.6.6 can be considered?  It is in rc2 right now and includes most of the features people care about in 0.7 except static addresses.   It includes wired 802.1x, profiles, and a number of bug fixes.

---

### Post by wieman01 on 2008-02-28
> **Starks said:**
> Why would that be the case? 802.11a works fine with NM 0.6.5
OK, you got a point. I thought 802.11a is in a very early development stage, but I must have been wrong. I'll shut up. :-)

---

### Post by Starks on 2008-02-29
> **wieman01 said:**
> OK, you got a point. I thought 802.11a is in a very early development stage, but I must have been wrong. I'll shut up. :-)

Huh? Wireless-A has been around for years. Are you talking about Wireless-N and its drafts?

---

### Post by autocrosser on 2008-03-02
Any thoughts on furthering NM 0.7?? As it is, it works well for me, but I have not seen any changes to it from when I started testing back in January.....Would be nice to see a update or two....

---

### Post by High Roller on 2008-03-02
> **autocrosser said:**
> Any thoughts on furthering NM 0.7?? As it is, it works well for me, but I have not seen any changes to it from when I started testing back in January.....Would be nice to see a update or two....

At this point I think it's being abandoned in terms of Hardy.  You may see it come back for Hardy +1 (or +2).  I would predict that NM 0.6.6 will be making its way into Hardy.

NM 0.7 will be nice.  If not for me then for my great grand children.   j/k :)

---

### Post by Hobnobb on 2008-03-03
Just wanted to bump that static address setting really does not work in nm 0.7. Even if I help it by editing the /etc/network/interfases file correctly  myself it still manages to not read this info.
How could they forget something so basic ?  I understand that they are focussed on getting the wireless thing working, but they should allways check the code if the basic things still are working.
There will be many future hardy users who can't be bothered with the wireless stuff, for whatever reason, one being a higher troughput locally if one has a GB-hub.
Hope someone checks the static settings possibility in the .66 NM, if that will be the  Betahardy version,
Tjau

---

### Post by sofamensch on 2008-03-03
As far as i tested it, the Static IP setting is partially working.

On my Hardy 8.04 with Atheros Chipset, the Roaming Mode with an WEP Network works just about perfect. 
When doing a manual configuration, with a Static IP Address, the iwconfig tells me that everything is allright, ifconfig shows me the right IP adress. 
I even can ping google.de (so DNS is working) and download updates for ubuntu. But the fork: somehow FireFox doesn't connect to the internet ! (Same with Epiphany)

---

### Post by sofamensch on 2008-03-03
1) (I shortened this to keep it KISS)
 Firefox 3 does NOT work using a static IP Addressor DHCP and the Manual Configuration. But Ping and everything works.I just checked, the internet connection is very good. A random browser (Amaya) works fine, and after a downgrade to FireFox 2 i am able to edit this post :-)
I assume it got to do with this effect: When setting up a manual connection, shortly after connecting it gives me a message "Network Disconnected".

My first idea was IPv6 so i disabled it in firefox, but thats not it.

2) Please make the Network Manager open only ONCE. Everytime i open a second one unnoticed i get this "Configuration File could not be saved.." Error

3) After a while, i cannot set anything anymore, because of the just mentioned "Configuration File could not be saved.." message, even if there is only one network-admin process.

---

### Post by mabovo on 2008-03-03
I am in the following situation:

1. After testing NM0.7 for a while and couldn't get connected wireless card I decided to downgrade to NM0.6.5. The process was very painfully boring.
2. Finally could connect wireless atheros ar5418 using NM-0.6.5 but it is impossible to stay connected for more than an hour so I decided to return testing NM0.7.
3. I prefer NM0.7 to be used on wired networks using DHCP but miss a lot the wireless life. 

What to do next ?

---

### Post by oponek on 2008-03-04
New version of Network Manager does not detect my ralink rt2400 card in Ubuntu Hardy!

---

### Post by Hobnobb on 2008-03-04
Hi all
I have to come back on my previous post and confess some lies I made therein.
I was intrigued that static adresses  in NM0.7 worked for some and not for others, like me. So I decided to test the differrent configs in NM 0.65 and NM 0.7. Turned out that NM 0.65 has the same flaw as NM0.7 being that one cannot edit static adresses AFTER roaming adresses once is used.:frown:

OK, this is the situation
NIC: Intel Corp 82573L Gigabit Ethernet Controller onboard on a MSI 975X motherboard.
Hardy Alpha 4 freshly installed on new partition.
Disabled IPv6
All other drivers work fine as far as I can see.

Now I can edit the static adresses in NetworkManager and in his turn NM edits the /etc/network/interfasces file nicely.
If I switch to roaming mode then this works too if there is a dhcp server in sight. BUT then already something has gone wrong I think. The roaming mode has destroyed the eth0 part in the  /etc/net../interfaces file and has as far as I know not made a backup! If I then try in NM to revert to static the old address has gone, probably because it cannot find a entry in the interfaces file which NM had destoyed itself  in the first place.
If I then enter static address info in NM it does not want to safe it anymore, coming with some bogus warning that I do not have admin rights allthough I just entered the password to use the editing mode.
I had to replace my own backup off the interfaces file and issue  sudo ifup eth0  to get thing working again.

Bottomline: Entering roaming mode once, destroys the interfaces file and thereafter the static addr.editing possibility in NM. This is on my machine in BOTH NM0.65 and NM0.7.
hope this helps.

@sofamensch  The situation u discribe is on my machine when I disable networking in the panel-Applet. Then Firefor and Evolution don't work anymore on the internet but I can still surf locally and issue all kinds of other networktraffic.
So the statement  'deactivate network' in the applet is gravely misleading, I think.
Tjau

btw why is this not sticky anymore ?

---

### Post by olskar on 2008-03-08
Works good with ipw2200

---

### Post by ripperzane on 2008-03-27
EDITED:
You got hamachi working in 8.04 x64? I get to the point where I unpack it, then attempt to install after upx-d to the hamachi executable, then I try to do the tunecfg/./tunecfg and it errors every time.
**I got it fixed. Forgot that installing ia32-libs seems to fix the issue. ($sudo apt-get install ia32-libs)**

> **tekoholix said:**
> 0.6.5 was fine for me under Hardy (Updated 2-4 times a day), until 2 days ago, when some update broke it, making it suddenly show my ham0 and pan0 interfaces, and broke Hamachi VPN.  In fact, the system automatically attempts connection to the ham0 or pan0 on login, will not default to wireless or permit data thru on ham0, no matter what I tried.

Tonight, I decided to take the drastic measure of trying out 0.7, thinking for sure I was screwing the pooch (my bcm94311mcg wifi has been trouble from day one, with Hardy, finally working with ndiswrapper)...

After reboot (as expected), EVERYTHING WORX!!  Hamachi's back, WiFi's up by default, speeds are 3-4Mb faster, etc.  I've not tried any WPA, WEP, anything else yet, but I surely will, in the next few days!!

Thanx a million!!

p.s.:  Unfortunately, seconds after I posted this, I found that the "Edit Connections..." menu entry, for me also, apparently does nothing.  Guess I'll have to wait to see what that does...

New problem:  It seems, unfortunately, that the DNS Servers are not passed by DHCP.  Upon each reboot, I've got to manually add my router's address as DNS, before the connection becomes valid.

---

### Post by tekoholix on 2008-03-27
> **ripperzane said:**
> EDITED:
You got hamachi working in 8.04 x64? I get to the point where I unpack it, then attempt to install after upx-d to the hamachi executable, then I try to do the tunecfg/./tunecfg and it errors every time.
**I got it fixed. Forgot that installing ia32-libs seems to fix the issue. ($sudo apt-get install ia32-libs)**

Hmmm...  I cannot be sure, at this point, but I believe that I had Hamachi running on Gutsy, and when upgraded, it simply continued to work, save for the update that broke it temporarily.  At this point, though, I'm on a fresh, clean Hardy (5 days old), and don't believe I needed the ia32-libs to get Hamachi running again...  I do have them installed now, for Skype, but that was one of the last installed...

Anyhow, glad it worked for ya'!!

---

### Post by jjbarrows on 2008-05-18
Hi and Thanks for making network-manager 0.7 available for testing - it fixed my lack of wifi;

hardy heron
tried all sorts of things (wicd, wifi-radar, compiling drivers from source, ndiswrapper, iwconfig)

install n-m 0.7, and it works!
I had to manually modprobe iwl3945 first; but thats probably due to something getting broken in all the stuffing around i did before

hardware info:
 *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 02
       serial: xxx
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.0.111 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

---

### Post by robtaylor on 2008-05-22
Its working great for me with iwl4965 and a custom 2.6.25-rc6 kernel, one problem though, 'edit connections' fails to launch nm-connection-editor. Launching nm-connection-editor manually works fine, though the 'Add' button crashes it, but this is known upstream problem - Fc9 is shipping with a patch that removes the button.

---

### Post by boobytrapped on 2008-05-23
I am trying to use these packages on hardy to connect to a LEAP network and having no luck.  I didn't get any success with the original hardy network-manager packages either.  I have a iwl3945 network adapter (on a T60p thinkpad).

Using wpa_supplicant directly works so the bug is in network-manager.

Network-manager used to work on gutsy.

---

### Post by mrMango on 2008-06-05
Apparently the new nm can't find my wireless. The wireless is working correctly using iwconfig, so I know the problem must be related to nm.

```
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: eth0
       version: 10
       serial: de:ad:be:ef:00:00
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=xxx.xxx.xxx.xxx latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:00:de:ad:be:ef
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

Getting the wired interface to work required me deleting everything but loopback in /etc/network/interfaces, otherwise NetworkManager spat out "device otherwise managed" in syslog.

Now that that's fixed, I still can't get the wireless. Here's some relevant info from syslog about N-M startup

```
Jun  5 00:06:30 tom-laptop NetworkManager: <info>  starting... 
Jun  5 00:06:30 tom-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver '8139too'. 
Jun  5 00:06:30 tom-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Jun  5 00:06:30 tom-laptop NetworkManager: <info>  Bringing up device eth0 
Jun  5 00:06:30 tom-laptop kernel: [  260.035785] eth0: link up, 100Mbps, full-duplex, lpa 0xC1E1
Jun  5 00:06:30 tom-laptop NetworkManager: <info>  Deactivating device eth0. 
Jun  5 00:06:30 tom-laptop NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_de_ad_be_ef_00_00
Jun  5 00:06:30 tom-laptop NetworkManager: nm_device_802_11_wireless_new: assertion `driver != NULL' failed
Jun  5 00:06:30 tom-laptop NetworkManager: <info>  (eth0) supplicant interface is now in state 2 (from 1). 
Jun  5 00:06:30 tom-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'Auto Ethernet (eth0)'. 
Jun  5 00:06:30 tom-laptop NetworkManager: <info>  Activating device eth0 
Jun  5 00:06:30 tom-laptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 

```

```
nm_device_802_11_wireless_new: assertion `driver != NULL' failed
```
Probabaly the most important item.

Also receiving the bug where edit connections doesn't do anything, and the add button in nm-connection-editor crashes the application.

---

### Post by asac on 2008-06-10
Hi,

I didnt have time to update the available packages for some time. However, I keep my branches updated again. Anyone who wants to be brave and build the latest available from bzr, can build both from my branches again. Anyway, no guarantees that this wont break your network :).

This involves a few steps:
 1. get the sources
 2. build the server
 3. install the server packages
 4. build the applet
 5. install the applet
 6. restart/relogin

Steps:
=======

1. get the sources
 bzr branch lp:~ubuntu-core-dev/network-manager/ubuntu.0.7 network-manager.ubuntu.07
 bzr branch lp:~asac/network-manager-applet/ubuntu.0.7 network-manager-applet.ubuntu.07

2. To build the server you run:
 cd network-manager.ubuntu.07
 dpkg-buildpackage -rfakeroot

(in case this complains about missing build dependencies, just install them.)

3. install the network manager build in step 2. You need network-manager-dev, libnm-util-dev and libnm-glib-dev as well as network-manager, libnm-util1 and libnm-glib0.

4. To build the applet run:
 cd network-manager-applet.ubuntu.07
 dpkg-buildpackage -rfakeroot

(again: in case this complains about missing build dependencies, just install them.)

5. install the applet: just install network-manager-gnome package

6. restart/relogin

---

### Post by plun on 2008-06-10
> **asac said:**
> Hi,

I didnt have time to update the available packages for some time. 

Well, thanks anyway...:)

Just a proposal..  please take a look at this thread.

[http://ubuntuforums.org/showthread.php?t=797059](http://ubuntuforums.org/showthread.php?t=797059)

Maybe you and Darrena can coordinate this....you
can develop and Darrena runs the testing  ?

Darrenas packages runs just fine for me on Intrepid...:)

---

### Post by asac on 2008-06-11
> **plun said:**
> Well, thanks anyway...:)

Just a proposal..  please take a look at this thread.

[http://ubuntuforums.org/showthread.php?t=797059](http://ubuntuforums.org/showthread.php?t=797059)

Maybe you and Darrena can coordinate this....you
can develop and Darrena runs the testing  ?

Darrenas packages runs just fine for me on Intrepid...:)

Well, he should have pinged me :).

---

### Post by xlizard on 2008-06-12
hmmm ... compilation faild :(

network-manager.ubuntu.07 says

cc1: warnings being treated as errors
interface_parser.c: In function ‘ifparser_init’:
interface_parser.c:105: error: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
make[4]: *** [libnmbackend_la-interface_parser.lo] Error 1
make[4]: Leaving directory `/usr/src/network-manager.ubuntu.07/src/backends'


and the applett:

cc1: warnings being treated as errors
nma-gconf-settings.c: In function ‘nma_gconf_settings_add_connection’:
nma-gconf-settings.c:97: error: format not a string literal and no format arguments
make[4]: *** [libgconf_helpers_la-nma-gconf-settings.lo] Error 1
make[4]: Leaving directory `/usr/src/network-manager-applet.ubuntu.07/src/gconf-helpers'

what i have to do?

---

### Post by asac on 2008-07-02
Update:

New 0.7 snapshot packages available in network-manager PPA. Read:

[http://www.asoftsite.org/s9y/archives/145-NetworkManager-0.7-is-back-New-PPA.html](http://www.asoftsite.org/s9y/archives/145-NetworkManager-0.7-is-back-New-PPA.html)

Happy testing!

---

### Post by asac on 2008-07-02
> **xlizard said:**
> hmmm ... compilation faild :(

network-manager.ubuntu.07 says

cc1: warnings being treated as errors
interface_parser.c: In function ‘ifparser_init’:
interface_parser.c:105: error: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
make[4]: *** [libnmbackend_la-interface_parser.lo] Error 1
make[4]: Leaving directory `/usr/src/network-manager.ubuntu.07/src/backends'


Yeah, the code is not yet ready for intrepid. Thus, the PPA I just announced currently contain hardy packages only. Of course, intrepid will follow soon.

---

### Post by xlizard on 2008-07-05
erf ... yes, i upgraded to expreimental, forgot this, sorry.
in your new snapshot-package is missing one file (if i am correct) - libnm-util.so.1
because:
lizard@lizard-laptop:~$ nm-tool 
/usr/bin/.libs/lt-nm-tool: error while loading shared libraries: libnm-util.so.1: cannot open shared object file: No such file or directory

and one new bug:
in connection-manager > mobile broadband it is not possible to store pin/puc/password anymore ... no error, they just not saved

---

### Post by gonfreecs on 2008-07-08
Hi!

I have tested the new packages of NM 0.7 from PPA and I have bad news. After having rebooted my computer, nothing was working... My wired network was unable to start with NetworkManager (but worked perfectly using ifconfig and dhcp), and NM was not able to show the list of wired networks. The wifi LED of my computer was off. A ifconfig eth1 up was able to turn the light on but NM was still unable to show a list of wireless networks.

Here is the result of  lshw -class network:

```

  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5755m-v3.29 ip=193.49.107.247 latency=0 module=tg3 multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: eth1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

After sudo ifconfig eth1 up, the wireless interface is not disabled:

```

  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:1c:26:cb:3b:10
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

Here is an extract of /var/log/syslog

```

Jul  8 10:21:12 jungle NetworkManager: <info>  starting... 
Jul  8 10:21:12 jungle NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch 
Jul  8 10:21:12 jungle NetworkManager: <info>  eth0: Device is fully-supported using driver 'tg3'. 
Jul  8 10:21:12 jungle NetworkManager: <info>  Found new Ethernet device 'eth0'. 
Jul  8 10:21:12 jungle NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_1c_23_a9_94_8c 
Jul  8 10:21:12 jungle NetworkManager: nm_device_wifi_new: assertion `driver != NULL' failed
Jul  8 10:21:12 jungle NetworkManager: <info>  Trying to start the supplicant... 
Jul  8 10:21:12 jungle NetworkManager: <info>  Trying to start the system settings daemon... 
Jul  8 10:21:12 jungle NetworkManager: <WARN>  killswitch_getpower_reply(): Error getting killswitch power: Access type not supported. 
Jul  8 10:21:12 jungle nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jul  8 10:21:12 jungle nm-system-settings: Can not read directory '/etc/NetworkManager/system-connections': Error opening directory '/etc/NetworkManager/system-connections': No such file or directory
Jul  8 10:21:16 jungle NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Jul  8 10:21:16 jungle NetworkManager: <info>  (eth0): bringing up device. 
Jul  8 10:21:16 jungle kernel: [   40.780938] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul  8 10:21:16 jungle nm-system-settings: Adding default connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_1c_23_a9_94_8c
Jul  8 10:21:16 jungle NetworkManager: <info>  (eth0): preparing device. 
Jul  8 10:21:16 jungle NetworkManager: <info>  (eth0): deactivating device. 
Jul  8 10:21:16 jungle NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
Jul  8 10:21:16 jungle NetworkManager: <info>  (eth0): device state change: 2 -> 3 
Jul  8 10:21:16 jungle NetworkManager: <info>  (eth0): carrier now OFF (device state 3) 
Jul  8 10:21:16 jungle NetworkManager: <info>  (eth0): device state change: 3 -> 2 
Jul  8 10:21:16 jungle NetworkManager: <info>  (eth0): deactivating device. 
Jul  8 10:21:16 jungle NetworkManager: <WARN>  auto_activate_device(): Connection 'Auto eth0' auto-activation failed: (2) Device not managed by NetworkManager 
Jul  8 10:21:17 jungle kernel: [   42.027272] tg3: eth0: Link is up at 100 Mbps, full duplex.
Jul  8 10:21:17 jungle kernel: [   42.027283] tg3: eth0: Flow control is off for TX and off for RX.
Jul  8 10:21:17 jungle kernel: [   42.031625] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jul  8 10:21:17 jungle NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
Jul  8 10:21:17 jungle NetworkManager: <info>  (eth0): device state change: 2 -> 3 
Jul  8 10:21:17 jungle NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
Jul  8 10:21:17 jungle NetworkManager: <info>  (eth0): device state change: 3 -> 4 
Jul  8 10:21:17 jungle NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Jul  8 10:21:17 jungle NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Jul  8 10:21:17 jungle NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Jul  8 10:21:17 jungle NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Jul  8 10:21:17 jungle NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Jul  8 10:21:17 jungle NetworkManager: <info>  (eth0): device state change: 4 -> 5 
Jul  8 10:21:17 jungle NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Jul  8 10:21:17 jungle NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Jul  8 10:21:17 jungle NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Jul  8 10:21:17 jungle NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Jul  8 10:21:17 jungle NetworkManager: <info>  (eth0): device state change: 5 -> 7 
Jul  8 10:21:17 jungle NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Jul  8 10:21:17 jungle NetworkManager: <info>  dhclient started with pid 6217 
Jul  8 10:21:17 jungle NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Jul  8 10:21:17 jungle dhclient: Internet Systems Consortium DHCP Client V3.0.6
Jul  8 10:21:17 jungle dhclient: Copyright 2004-2007 Internet Systems Consortium.
Jul  8 10:21:17 jungle dhclient: All rights reserved.
Jul  8 10:21:17 jungle dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jul  8 10:21:17 jungle dhclient: 
Jul  8 10:21:17 jungle dhclient: wmaster0: unknown hardware address type 801
Jul  8 10:21:17 jungle dhclient: wmaster0: unknown hardware address type 801
Jul  8 10:21:17 jungle NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit 
Jul  8 10:21:17 jungle kernel: [   42.094260] NET: Registered protocol family 17
Jul  8 10:21:17 jungle dhclient: Listening on LPF/eth0/00:1c:23:a9:94:8c
Jul  8 10:21:17 jungle dhclient: Sending on   LPF/eth0/00:1c:23:a9:94:8c
Jul  8 10:21:17 jungle dhclient: Sending on   Socket/fallback
Jul  8 10:21:17 jungle dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Jul  8 10:21:19 jungle avahi-daemon[5383]: Registering new address record for fe80::21c:23ff:fea9:948c on eth0.*.
Jul  8 10:21:22 jungle dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Jul  8 10:21:28 jungle kernel: [   45.681383] eth0: no IPv6 routers present
Jul  8 10:21:30 jungle dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Jul  8 10:21:43 jungle dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Jul  8 10:21:48 jungle hcid[5958]: Default passkey agent (:1.23, /org/bluez/passkey) registered
Jul  8 10:21:48 jungle hcid[5958]: Default authorization agent (:1.23, /org/bluez/auth) registered
Jul  8 10:21:49 jungle dhclient: No DHCPOFFERS received.
Jul  8 10:21:49 jungle dhclient: No working leases in persistent database - sleeping.

```

Tell me if you want additional information, I would be glad to help you debug this wonderful software.

Best regards!

---

### Post by xlizard on 2008-07-10
that is strange ... here everything is working fine, well the missing lib-file, the password/pin problem for wwan and some wireless issues which are no 0.7 problem (iwl4965 card)

---

### Post by asac on 2008-07-26
I uploaded a new trunk snapshot to [http://launchpad.net/~network-manager/+archive](http://launchpad.net/~network-manager/+archive) ... builds are available for intrepid and hardy.

To install add the archive to your sources.list and run a full upgrade.

Let me know how it works for you. If you provide negative or positive feedback please give me your chipset/driver (for wifi and wired) and your modem model (for 3g).

---

### Post by MadMan2k on 2008-07-30
on hardy libpcslite is too old, so the install fails. please adapt your build-depends.

---

### Post by bodly on 2008-07-31
asac,

Thanks for building these packages.  I tested them on intrepid and for the most part they're working great.  The one thing I've noticed so far is that nm-tool does not work.  I get these errors:

/usr/bin/nm-tool: line 117: cd: /build/buildd/network-manager-0.7~~svn20080720t224551+eni1/test: No such file or directory
cc: nm-tool.o: No such file or directory
cc: ../libnm-glib/.libs/libnm_glib.so: No such file or directory
cc: /build/buildd/network-manager-0.7~~svn20080720t224551+eni1/libnm-util/.libs/libnm-util.so: No such file or directory
cc: ../libnm-util/.libs/libnm-util.so: No such file or directory


This is not a big problem for me, but I thought I'd mention it.  Again, thanks for the packages.

---

### Post by xlizard on 2008-08-03
strage  problem: after sleep i have to kill wpa_supplicant to connect to an wpa wlan.

another think is, is it possible to enter custom init-commands for mobile broadband connection? background: vodafone de sends dns-server 10.11.12.13 and 10.11.12.14. a nice workaround is to set the default nameserver with the command AT!SCDNS=1,"139.7.30.125","139.7.30.126"

another thing with mobile is, folloing the documentation of sierra and use ttyUSB0 for at-commands and ttyUSB2 for the ppp connection (shift it, if ttyUSB0 is not the modem of cause ;) ) this gives you the possibility to get information like signal with the at command at ttyUSB0 even while connection is up

and the last, executing a custom command after connected, based ob the connection-setting, for example to execute bmctl.pl to disable image-recompression in mobile connections

---

### Post by TomvE on 2008-08-05
Does the mobile broadband bit also work with a Nokia phone connected via USB? At the moment I'm using wvdial, but it would be nice if the network manager can handle that connection as well.

---

### Post by asac on 2008-08-07
> **TomvE said:**
> Does the mobile broadband bit also work with a Nokia phone connected via USB? At the moment I'm using wvdial, but it would be nice if the network manager can handle that connection as well.

Network Manager 0.7 entered intrepid today. Please test your nokia thing with it. I would be curious to know if its properly detected.

---

### Post by asac on 2008-08-10
I uploaded a new snapshot to network-manager PPA ([http://launchpad.net/~network-manager/+archive](http://launchpad.net/~network-manager/+archive)). also i updated the openvpn package for preliminary testing there. Please test.

---

### Post by Slug71 on 2008-08-12
this version of Network Manager sucks! Cant connect to my Wireless Connection. Using Ubuntu Intrepid Ibex Alpha 3 with all current updates.
Filed a bug(#257393) for this issue.

---

### Post by Slug71 on 2008-08-12
My bad, for some reason my Wireless card is disabled.

---

### Post by Rotarychainsaw on 2008-08-13
Using the PPA, saw that the cisco vpn plugin was updated today. Can't get it to connect to my schools VPN, says 'There was a problem launching the authentication dialog for VPN connection type 'org.freedesktop.NetworkManager.vpnc'. Contact your system administrator.'

---

### Post by asac on 2008-08-14
uploaded a new snapshot for the network-manager, the libs, the applet and the vpn plugins taken on 12th aug to network-manager PPA.

Further, I think that the vpn password dialog issues are fixed.

Please test.

---

### Post by dupondje on 2008-08-15
It still seems to forget Static IP configuration :(

---

### Post by asac on 2008-08-18
> **Rotarychainsaw said:**
> Using the PPA, saw that the cisco vpn plugin was updated today. Can't get it to connect to my schools VPN, says 'There was a problem launching the authentication dialog for VPN connection type 'org.freedesktop.NetworkManager.vpnc'. Contact your system administrator.'

Does the todays upload in PPA work for you?

---

### Post by asac on 2008-08-18
> **dupondje said:**
> It still seems to forget Static IP configuration :(

this is fixed in latest PPA version ([https://edge.launchpad.net/~network-manager/+archive](https://edge.launchpad.net/~network-manager/+archive))

---

### Post by dupondje on 2008-08-18
> **asac said:**
> this is fixed in latest PPA version ([https://edge.launchpad.net/~network-manager/+archive](https://edge.launchpad.net/~network-manager/+archive))

Still forgets settings @ reboot :(

Every setting gets lost (name, ip's, etc) and gets back to default DHCP auto config :(

If u set a static IP, it even doesn't change to the static ip by pressing OK, u need to manually restart the Network Manager!

---

### Post by jfxberns on 2008-08-28
I am also experiencing that the settings for my wired network revert from manual to automatic on reboot.  Not good.

Any fix yet?

---

### Post by Polygon on 2008-08-28
i was googling for a solution to my problem and i came across this post

i recently put ubuntu back on my laptop after having vista on it for about a month. A month before, i was able to connect to my campus WPA network using network manager 7.0, but now after installing the latest ppa, network manager segfaults whenever i try and enter my authentication information

here is my wireless card in my laptop:

> 
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:1f:3a:4b:39:71
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=10.198.131.187 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g


I am using a special self-compiled branch of madwifi or else i would get no wifi connectivity at all ([http://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6/](http://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6/))

and when i try to connect to said network:

[[IMG]http://img154.imageshack.us/img154/975/screenshotwirelessnetwooa5.th.png[/IMG]](http://img154.imageshack.us/my.php?image=screenshotwirelessnetwooa5.png)

i get this in terminal:

[[IMG]http://img361.imageshack.us/img361/8882/screenshotmi5.th.png[/IMG]](http://img361.imageshack.us/my.php?image=screenshotmi5.png)

---

### Post by cszikszoy on 2008-09-01
Network manager 0.7 working very well for me on Hardy.  I'm only using it with a wired connection, though.

I have yet to try to use any of the VPN plugins either.

---

### Post by olskar on 2008-09-02
Whats the easiest way to try this on hardy?

---

### Post by cszikszoy on 2008-09-02
> **olskar said:**
> Whats the easiest way to try this on hardy?

[https://launchpad.net/~network-manager/+archive](https://launchpad.net/~network-manager/+archive)

Go there and add those to your software sources.  Then just do
```
sudo apt-get update
```

And it should prompt you to download and install all of the parts for NM 0.7

---

### Post by jfxberns on 2008-09-02
> **dupondje said:**
> Still forgets settings @ reboot :(

Every setting gets lost (name, ip's, etc) and gets back to default DHCP auto config :(

If u set a static IP, it even doesn't change to the static ip by pressing OK, u need to manually restart the Network Manager!

The problem seems to arise from Network Manager not asking for (and getting) root permission to update the /etc/network/interface config file.

A simple fix: delete the interface in network manager and add a new interface.  When you add a new interface, Network Manager asks for your root password and then writes the new configuration file properly.

It worked for me.

---

### Post by Noble Neil on 2008-09-03
I upgraded to 0.7 to get my huawei e270 working. And it did!
But now internet sharing doesn't work :-(

I never managed to get the ip-table script solutions to work, so I just used firestarter. Now whenever I plug in my LAN cable I loose wireless internet connection.

Could someone help me? I guess I need to use the button "routes" in the network-manager GUI?

My setup is this:
internet -> wireless adsl router -> dhcp to wireless clients 192.168.2.x including ubuntu box
Ubuntubox -> LAN to windows box. I have set the ubuntu LAN to 192.168.0.1 static.
Windows box is set to dhcp, but falls back to alternative static IP if DHCP fails. Connection between ubuntubox and windows box is OK, but I loose internetconnectivity when I plug in LAN cable.

---

### Post by dupondje on 2008-09-05
> **jfxberns said:**
> The problem seems to arise from Network Manager not asking for (and getting) root permission to update the /etc/network/interface config file.

A simple fix: delete the interface in network manager and add a new interface.  When you add a new interface, Network Manager asks for your root password and then writes the new configuration file properly.

It worked for me.

It doesn't save anything for me :( Crappy thing

---

### Post by KDB9000 on 2008-09-09
I tried to install this on my Hardy system, but I was met with incompatible versions of dependences and broken dependences.

---

### Post by Tankalot on 2008-09-09
Latest build ruined pretty much everything- still wasn't able to save settings, and couldn't connect either- including my 3G dongle-thingermagig (Huaweii E220). Was forced to revert to standard 0.6xx from Ubuntu to be able to even go online :/

---

### Post by asac on 2008-09-10
> **Tankalot said:**
> Latest build ruined pretty much everything- still wasn't able to save settings, and couldn't connect either- including my 3G dongle-thingermagig (Huaweii E220). Was forced to revert to standard 0.6xx from Ubuntu to be able to even go online :/

did you properly reboot after getting the latest updates? are you sure that everything updated properly? There was a build error that might have prevented some packages to be available in sync-with the others.

---

### Post by asac on 2008-09-12
ok. a new gem has landed in the network-manager PPA: the mobile broadband wizard which is ment to ease the setup of 3g connections.

the packages that have this are:

network-manager-gnome 0.7~~svn20080907t033843-0ubuntu3~mbca1 (intrepid)
network-manager-gnome 0.7~~svn20080907t033843-0ubuntu3~mbca1~nm1 (hardy)

once you have installed them ensure that you also have libmbca0 installed.

next time you plug in a 3g card or phone which is recognized and you dont have a suitable connection setup you should see the wizard pop up.

alternatively it should show up when you go create "New" connection in the connection-editor "Mobile Broadband" tab.

Please test and report back.

(fwiw, the network-manager PPA is: [https://edge.launchpad.net/~network-manager/+archive](https://edge.launchpad.net/~network-manager/+archive))

---

### Post by Rotarychainsaw on 2008-09-15
Just alerting you of a potential bug regarding the print dialog. I am running the PPA and ran into this problem. I would assume that network-manager takes care of upping the loopback interface. 

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/223776](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/223776)

---

### Post by asac on 2008-09-16
for all that saw Networkmanager crashes (or more visually the applet disappearing) after resume, I uploaded a proposed fix to the network-manager ppa. Please test. The versions uploaded are:

Uploading to ppa-nm (via ftp to ppa.launchpad.net):
network-manager_0.7~~svn20080908t183521+eni0-0ubuntu3~nm2~hardy1.dsc: done. network-manager_0.7~~svn20080908t183521+eni0-0ubuntu3~nm2~hardy1.diff.gz: done. network-manager_0.7~~svn20080908t183521+eni0-0ubuntu3~nm2~hardy1_source.changes: done.
Successfully uploaded packages.

Uploading to ppa-nm (via ftp to ppa.launchpad.net):
network-manager_0.7~~svn20080908t183521+eni0-0ubuntu3~nm2.dsc: done. network-manager_0.7~~svn20080908t183521+eni0-0ubuntu3~nm2.diff.gz: done. network-manager_0.7~~svn20080908t183521+eni0-0ubuntu3~nm2_source.changes: done.

---

### Post by Carlos Santiago on 2008-09-17
I have two 3G modems and I would be glad to test them with Network Manager 0.7 over Ubuntu 8.04 (Hardy).
Both of them work via command line.

My modems are:
 - Novatel Merlin U630
 - Huawei U620

However, my provider is not listed on the wizard.
(I already supply the provider data to [http://svn.gnome.org/viewvc/mobile-broadband-provider-info/](http://svn.gnome.org/viewvc/mobile-broadband-provider-info/))

While the provider is not shown in the wizard I am trying to test both of the modems inserting the provider data myself. 
But I don't know where I should place the OPERATOR string, as it is used on the chatscript: AT+COPS=0,0,"P OPTIMUS"

Follows the providers info:
Name: Kanguru
Country: PT (Portugal)
Operator: P OPTIMUS
APN: myconnection
DNS: 62.169.67.172, 62.169.67.171
user: anything
password: anything

And other subscription of the same provider:
Name: Kanguru (fixo)
Country: PT (Portugal)
Operator: P OPTIMUS
APN: kangurufixo
DNS: 62.169.67.172, 62.169.67.171
user: anything
password: anything

---

### Post by [Psyduck] on 2008-09-17
> **asac said:**
> for all that saw Networkmanager crashes (or more visually the applet disappearing) after resume, I uploaded a proposed fix to the network-manager ppa. Please test. The versions uploaded are:

Uploading to ppa-nm (via ftp to ppa.launchpad.net):
network-manager_0.7~~svn20080908t183521+eni0-0ubuntu3~nm2~hardy1.dsc: done. network-manager_0.7~~svn20080908t183521+eni0-0ubuntu3~nm2~hardy1.diff.gz: done. network-manager_0.7~~svn20080908t183521+eni0-0ubuntu3~nm2~hardy1_source.changes: done.
Successfully uploaded packages.

Uploading to ppa-nm (via ftp to ppa.launchpad.net):
network-manager_0.7~~svn20080908t183521+eni0-0ubuntu3~nm2.dsc: done. network-manager_0.7~~svn20080908t183521+eni0-0ubuntu3~nm2.diff.gz: done. network-manager_0.7~~svn20080908t183521+eni0-0ubuntu3~nm2_source.changes: done.
This update fixed the problem with the nm-applet "crashing".

Now if someone could assist me in getting my wireless connection to work flawless I would be grateful. I have a WPA2 network and it can take several minutes and multiple password inputs to get a working wireless connection.

---

### Post by KDB9000 on 2008-09-17
NM 0.7 is running fine for me and seems to be better then 0.6. I am having trouble with OpenVPN in NM 0.7 now. I am on Hardy, and I also did the upgrade for NM 0.7 OpenVPN. I redid my profile, but when I try to connect it says that "VPN service stop unexpectedly." I am not sure what is wrong or were to start to troubleshoot the problem. Any thoughts?

---

### Post by asac on 2008-09-18
> **'[Psyduck] said:**
> This update fixed the problem with the nm-applet "crashing".

Now if someone could assist me in getting my wireless connection to work flawless I would be grateful. I have a WPA2 network and it can take several minutes and multiple password inputs to get a working wireless connection.

Which driver/chipset are you using? Could you please attach your complete syslog taken _after_ reproducing the flakiness? Also ensure that you have nothing configured in /etc/network/interfaces (except "lo" which must stay in there).

---

### Post by asac on 2008-09-18
> **Carlos Santiago said:**
> I have two 3G modems and I would be glad to test them with Network Manager 0.7 over Ubuntu 8.04 (Hardy).
Both of them work via command line.

My modems are:
 - Novatel Merlin U630
 - Huawei U620

However, my provider is not listed on the wizard.
(I already supply the provider data to [http://svn.gnome.org/viewvc/mobile-broadband-provider-info/](http://svn.gnome.org/viewvc/mobile-broadband-provider-info/))

While the provider is not shown in the wizard I am trying to test both of the modems inserting the provider data myself. 
But I don't know where I should place the OPERATOR string, as it is used on the chatscript: AT+COPS=0,0,"P OPTIMUS"

Follows the providers info:
Name: Kanguru
Country: PT (Portugal)
Operator: P OPTIMUS
APN: myconnection
DNS: 62.169.67.172, 62.169.67.171
user: anything
password: anything

And other subscription of the same provider:
Name: Kanguru (fixo)
Country: PT (Portugal)
Operator: P OPTIMUS
APN: kangurufixo
DNS: 62.169.67.172, 62.169.67.171
user: anything
password: anything

Can you file a bug with this provider info against mobile-broadband-provider-info in launchpad so we can add that to the database?

Also the AT+COPS=0,0 operator should happen automatically. Maybe try to update to latest NM packages i uploaded to PPA today. The last bits had some issues with modem probe code.

---

### Post by [Psyduck] on 2008-09-18
Here's my syslog that shows several attempts to connect and finally it works.

I'm using the patched kernel from [www.array.org](www.array.org) for my eee pc 1000H. It is possible that this is an issue with the driver/kernel. 

One annoying thing is that it keeps asking for my WPA-password. Is there a way to make it remember the password?

---

### Post by Shihan74 on 2008-09-23
Hi guys, im on the aa1 and its been a bit of a mixed bag for me with 0.7. Mostly tried it because of 3g support, and the default configs are a little screwy. (its a huawei e220 hdspa usb modem - has a strange problem when its first plugged in, but when unplugged and re-plugged in fixes itself)

On the three network (AU), nm (for some reason) sets the dialin code to *99***1# (or something like that) a username of "a" (?) and an APN of 3netaccess. But, none of that is correct, the dial in number is just *99#, and no apn or username need be set (though neither actually matter).

Wireless has been a bit of a nightmare, doesn't remember any settings and having trouble connecting to most AP's... my home ap (billion router) runs wpa with tkip and its the only one that connects with any consistency. The one at work (which connects maybe 1 in 20 attempts) runs wpa and aes (netscreen ssg5 iirc). Haven't been able so far to get it to connect to a wpa2 ap at all - but that may just be because i've only attempted to a couple of times (the aa1 uses the madwifi drivers).

Once I can get together a bunch of logs i'll attach them here, but its nice to see 0.7 and the 3g working!


lshw -class network:
```

# lshw -class network

  *-network               

       description: Ethernet interface

       product: RTL8101E PCI Express Fast Ethernet controller

       vendor: Realtek Semiconductor Co., Ltd.

       physical id: 0

       bus info: pci@0000:02:00.0

       logical name: eth0

       version: 02

       serial: 00:1e:68:88:a2:fc

       capacity: 1GB/s

       width: 64 bits

       clock: 33MHz

       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair

  *-network

       description: Wireless interface

       product: AR242x 802.11abg Wireless PCI Express Adapter

       vendor: Atheros Communications Inc.

       physical id: 0

       bus info: pci@0000:03:00.0

       logical name: wifi0

       version: 01

       serial: 00:1f:e2:bc:8a:06

       width: 64 bits

       clock: 33MHz

       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless

       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g



```

Syslog (first time it was switched on, it connected on the second attempt, which is a rarity), second time it gave up (eventually i rebooted and im on about the 20th attempt by now).
```

Sep 24 10:19:22 helium NetworkManager: <info>  Config: set interface ap_scan to 2
Sep 24 10:19:22 helium NetworkManager: <info>  (ath0): supplicant connection state change: 1 -> 2
Sep 24 10:19:22 helium NetworkManager: <info>  (ath0): supplicant connection state change: 2 -> 3
Sep 24 10:19:24 helium NetworkManager: <info>  (ath0): supplicant connection state change: 3 -> 4
Sep 24 10:19:34 helium NetworkManager: <info>  (ath0): supplicant connection state change: 4 -> 0
Sep 24 10:19:34 helium NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 2
Sep 24 10:19:34 helium NetworkManager: <info>  (ath0): supplicant connection state change: 2 -> 3
Sep 24 10:19:34 helium NetworkManager: <info>  (ath0): supplicant connection state change: 3 -> 0
Sep 24 10:19:34 helium NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 4
Sep 24 10:19:44 helium NetworkManager: <info>  (ath0): supplicant connection state change: 4 -> 0
Sep 24 10:19:44 helium NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 2
Sep 24 10:19:44 helium NetworkManager: <info>  (ath0): supplicant connection state change: 2 -> 3
Sep 24 10:19:44 helium NetworkManager: <info>  (ath0): supplicant connection state change: 3 -> 0
Sep 24 10:19:44 helium NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 4
Sep 24 10:19:47 helium NetworkManager: <info>  Activation (ath0/wireless): association took too long.
Sep 24 10:19:47 helium NetworkManager: <info>  (ath0): device state change: 5 -> 6
Sep 24 10:19:47 helium NetworkManager: <info>  Activation (ath0/wireless): asking for new secrets
Sep 24 10:19:47 helium NetworkManager: <info>  (ath0): supplicant connection state change: 4 -> 0
Sep 24 10:19:52 helium NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 24 10:19:52 helium NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started...
Sep 24 10:19:52 helium NetworkManager: <info>  (ath0): device state change: 6 -> 4
Sep 24 10:19:52 helium NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled...
Sep 24 10:19:52 helium NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete.
Sep 24 10:19:52 helium NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting...
Sep 24 10:19:52 helium NetworkManager: <info>  (ath0): device state change: 4 -> 5
Sep 24 10:19:52 helium NetworkManager: <info>  Activation (ath0/wireless): connection 'Auto mysid' has security, and secrets exist.  No new secrets needed.
Sep 24 10:19:52 helium NetworkManager: <info>  Config: added 'ssid' value 'mysid'
Sep 24 10:19:52 helium NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Sep 24 10:19:52 helium NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Sep 24 10:19:52 helium NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Sep 24 10:19:52 helium NetworkManager: <info>  Config: added 'proto' value 'WPA RSN'
Sep 24 10:19:52 helium NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP'
Sep 24 10:19:52 helium NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP'
Sep 24 10:19:52 helium NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete.
Sep 24 10:19:52 helium NetworkManager: <info>  Config: set interface ap_scan to 1
Sep 24 10:19:52 helium NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 2
Sep 24 10:19:54 helium NetworkManager: <info>  (ath0): supplicant connection state change: 2 -> 0
Sep 24 10:19:54 helium NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 2
Sep 24 10:19:56 helium NetworkManager: <info>  (ath0): supplicant connection state change: 2 -> 3
Sep 24 10:19:56 helium NetworkManager: <info>  (ath0): supplicant connection state change: 3 -> 4
Sep 24 10:19:56 helium NetworkManager: <info>  (ath0): supplicant connection state change: 4 -> 5
Sep 24 10:19:56 helium NetworkManager: <info>  (ath0): supplicant connection state change: 5 -> 6
Sep 24 10:19:57 helium NetworkManager: <info>  (ath0): supplicant connection state change: 6 -> 7
Sep 24 10:19:57 helium NetworkManager: <info>  Activation (ath0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'mysid'.
Sep 24 10:19:57 helium NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep 24 10:19:57 helium NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) started...
Sep 24 10:19:57 helium NetworkManager: <info>  (ath0): device state change: 5 -> 7
Sep 24 10:19:57 helium NetworkManager: <info>  Activation (ath0) Beginning DHCP transaction.
Sep 24 10:19:57 helium NetworkManager: <info>  dhclient started with pid 6469
Sep 24 10:19:57 helium NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) complete.
Sep 24 10:19:57 helium dhclient: Internet Systems Consortium DHCP Client V3.0.6
Sep 24 10:19:57 helium dhclient: Copyright 2004-2007 Internet Systems Consortium.
Sep 24 10:19:57 helium dhclient: All rights reserved.
Sep 24 10:19:57 helium dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Sep 24 10:19:57 helium dhclient:
Sep 24 10:19:57 helium dhclient: wifi0: unknown hardware address type 801
Sep 24 10:19:57 helium dhclient: wifi0: unknown hardware address type 801
Sep 24 10:19:57 helium NetworkManager: <info>  DHCP: device ath0 state changed (null) -> preinit
Sep 24 10:19:57 helium dhclient: Listening on LPF/ath0/00:1f:e2:bc:8a:06
Sep 24 10:19:57 helium dhclient: Sending on   LPF/ath0/00:1f:e2:bc:8a:06
Sep 24 10:19:57 helium dhclient: Sending on   Socket/fallback

--- snip ---

Sep 24 10:24:55 helium NetworkManager: <info>  (eth0): device state change: 1 -> 2
Sep 24 10:24:55 helium NetworkManager: <info>  (eth0): bringing up device.
Sep 24 10:24:55 helium kernel: [   48.854140] r8169: eth0: link down
Sep 24 10:24:55 helium kernel: [   48.855765] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 24 10:24:55 helium NetworkManager: <info>  (eth0): preparing device.
Sep 24 10:24:55 helium NetworkManager: <info>  (eth0): deactivating device.
Sep 24 10:24:55 helium NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Sep 24 10:24:55 helium NetworkManager: <info>  (eth0): device state change: 2 -> 3
Sep 24 10:24:55 helium NetworkManager: <info>  (ath0): device state change: 1 -> 2
Sep 24 10:24:55 helium NetworkManager: <info>  (ath0): bringing up device.
Sep 24 10:24:55 helium NetworkManager: <info>  (ath0): preparing device.
Sep 24 10:24:55 helium NetworkManager: <info>  (ath0): deactivating device.
Sep 24 10:24:55 helium NetworkManager: <info>  (eth0): carrier now OFF (device state 3)
Sep 24 10:24:55 helium NetworkManager: <info>  (eth0): device state change: 3 -> 2
Sep 24 10:24:55 helium NetworkManager: <info>  (eth0): deactivating device.
Sep 24 10:24:55 helium NetworkManager: <info>  (ath0): device state change: 2 -> 3
Sep 24 10:24:55 helium nm-system-settings: Adding default connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_1e_68_88_a2_fc
Sep 24 10:24:55 helium kernel: [   48.965098] NET: Registered protocol family 17
Sep 24 10:24:55 helium NetworkManager: <info>  (ath0): supplicant interface state change: 1 -> 2.
Sep 24 10:24:56 helium avahi-daemon[4982]: Registering new address record for fe80::21f:e2ff:febc:8a06 on ath0.*.
Sep 24 10:25:51 helium NetworkManager: <info>  Activation (ath0) starting connection 'Auto mysid'
Sep 24 10:25:51 helium NetworkManager: <info>  (ath0): device state change: 3 -> 4
Sep 24 10:25:51 helium NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 24 10:25:51 helium NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started...
Sep 24 10:25:51 helium NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled...
Sep 24 10:25:51 helium NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete.
Sep 24 10:25:51 helium NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting...
Sep 24 10:25:51 helium NetworkManager: <info>  (ath0): device state change: 4 -> 5
Sep 24 10:25:51 helium NetworkManager: <info>  Activation (ath0/wireless): access point 'Auto mysid' has security, but secrets are required.
Sep 24 10:25:51 helium NetworkManager: <info>  (ath0): device state change: 5 -> 6
Sep 24 10:25:51 helium NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete.
Sep 24 10:25:52 helium NetworkManager: <info>  (ath0): supplicant connection state change: 2 -> 1
Sep 24 10:26:23 helium NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 24 10:26:23 helium NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started...
Sep 24 10:26:23 helium NetworkManager: <info>  (ath0): device state change: 6 -> 4
Sep 24 10:26:23 helium NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled...
Sep 24 10:26:23 helium NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete.
Sep 24 10:26:23 helium NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting...
Sep 24 10:26:23 helium NetworkManager: <info>  (ath0): device state change: 4 -> 5
Sep 24 10:26:23 helium NetworkManager: <info>  Activation (ath0/wireless): connection 'Auto mysid' has security, and secrets exist.  No new secrets needed.
Sep 24 10:26:23 helium NetworkManager: <info>  Config: added 'ssid' value 'mysid'
Sep 24 10:26:23 helium NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Sep 24 10:26:23 helium NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Sep 24 10:26:23 helium NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Sep 24 10:26:23 helium NetworkManager: <info>  Config: added 'proto' value 'WPA RSN'
Sep 24 10:26:23 helium NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP'
Sep 24 10:26:23 helium NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP'
Sep 24 10:26:23 helium NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete.
Sep 24 10:26:23 helium NetworkManager: <info>  Config: set interface ap_scan to 2
Sep 24 10:26:23 helium NetworkManager: <info>  (ath0): supplicant connection state change: 1 -> 2
Sep 24 10:26:23 helium NetworkManager: <info>  (ath0): supplicant connection state change: 2 -> 3
Sep 24 10:26:25 helium NetworkManager: <info>  (ath0): supplicant connection state change: 3 -> 4
Sep 24 10:26:35 helium NetworkManager: <info>  (ath0): supplicant connection state change: 4 -> 0
Sep 24 10:26:35 helium NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 2
Sep 24 10:26:35 helium NetworkManager: <info>  (ath0): supplicant connection state change: 2 -> 3
Sep 24 10:26:35 helium NetworkManager: <info>  (ath0): supplicant connection state change: 3 -> 0
Sep 24 10:26:35 helium NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 4
Sep 24 10:26:45 helium NetworkManager: <info>  (ath0): supplicant connection state change: 4 -> 0
Sep 24 10:26:45 helium NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 2
Sep 24 10:26:45 helium NetworkManager: <info>  (ath0): supplicant connection state change: 2 -> 3
Sep 24 10:26:45 helium NetworkManager: <info>  (ath0): supplicant connection state change: 3 -> 0
Sep 24 10:26:45 helium NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 4
Sep 24 10:26:48 helium NetworkManager: <info>  Activation (ath0/wireless): association took too long.
Sep 24 10:26:48 helium NetworkManager: <info>  (ath0): device state change: 5 -> 6
Sep 24 10:26:48 helium NetworkManager: <info>  Activation (ath0/wireless): asking for new secrets
Sep 24 10:26:48 helium NetworkManager: <info>  (ath0): supplicant connection state change: 4 -> 0
Sep 24 10:26:53 helium NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 24 10:26:53 helium NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started...
Sep 24 10:26:53 helium NetworkManager: <info>  (ath0): device state change: 6 -> 4
Sep 24 10:26:53 helium NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled...
Sep 24 10:26:53 helium NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete.
Sep 24 10:26:53 helium NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting...
Sep 24 10:26:53 helium NetworkManager: <info>  (ath0): device state change: 4 -> 5
Sep 24 10:26:53 helium NetworkManager: <info>  Activation (ath0/wireless): connection 'Auto mysid' has security, and secrets exist.  No new secrets needed.
Sep 24 10:26:53 helium NetworkManager: <info>  Config: added 'ssid' value 'mysid'
Sep 24 10:26:53 helium NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Sep 24 10:26:53 helium NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Sep 24 10:26:53 helium NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Sep 24 10:26:53 helium NetworkManager: <info>  Config: added 'proto' value 'WPA RSN'
Sep 24 10:26:53 helium NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP'
Sep 24 10:26:53 helium NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP'
Sep 24 10:26:53 helium NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete.
Sep 24 10:26:53 helium NetworkManager: <info>  Config: set interface ap_scan to 2
Sep 24 10:26:53 helium NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 2
Sep 24 10:26:53 helium NetworkManager: <info>  (ath0): supplicant connection state change: 2 -> 3
Sep 24 10:26:53 helium NetworkManager: <info>  (ath0): supplicant connection state change: 3 -> 4
Sep 24 10:27:03 helium NetworkManager: <info>  (ath0): supplicant connection state change: 4 -> 0
Sep 24 10:27:03 helium NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 2
Sep 24 10:27:03 helium NetworkManager: <info>  (ath0): supplicant connection state change: 2 -> 3
Sep 24 10:27:03 helium NetworkManager: <info>  (ath0): supplicant connection state change: 3 -> 0
Sep 24 10:27:03 helium NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 4
Sep 24 10:27:13 helium NetworkManager: <info>  (ath0): supplicant connection state change: 4 -> 0
Sep 24 10:27:13 helium NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 2
Sep 24 10:27:13 helium NetworkManager: <info>  (ath0): supplicant connection state change: 2 -> 3
Sep 24 10:27:13 helium NetworkManager: <info>  (ath0): supplicant connection state change: 3 -> 0
Sep 24 10:27:13 helium NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 4
Sep 24 10:27:18 helium NetworkManager: <info>  Activation (ath0/wireless): association took too long.
Sep 24 10:27:18 helium NetworkManager: <info>  (ath0): device state change: 5 -> 6
Sep 24 10:27:18 helium NetworkManager: <info>  Activation (ath0/wireless): asking for new secrets
Sep 24 10:27:18 helium NetworkManager: <info>  (ath0): supplicant connection state change: 4 -> 0
Sep 24 10:27:24 helium NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 24 10:27:24 helium NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started...
Sep 24 10:27:24 helium NetworkManager: <info>  (ath0): device state change: 6 -> 4
Sep 24 10:27:24 helium NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled...
Sep 24 10:27:24 helium NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete.
Sep 24 10:27:24 helium NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting...
Sep 24 10:27:24 helium NetworkManager: <info>  (ath0): device state change: 4 -> 5
Sep 24 10:27:24 helium NetworkManager: <info>  Activation (ath0/wireless): connection 'Auto mysid' has security, and secrets exist.  No new secrets needed.
Sep 24 10:27:24 helium NetworkManager: <info>  Config: added 'ssid' value 'mysid'
Sep 24 10:27:24 helium NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Sep 24 10:27:24 helium NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Sep 24 10:27:24 helium NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Sep 24 10:27:24 helium NetworkManager: <info>  Config: added 'proto' value 'WPA RSN'
Sep 24 10:27:24 helium NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP'
Sep 24 10:27:24 helium NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP'
Sep 24 10:27:24 helium NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete.
Sep 24 10:27:24 helium NetworkManager: <info>  Config: set interface ap_scan to 2
Sep 24 10:27:24 helium NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 2
Sep 24 10:27:24 helium NetworkManager: <info>  (ath0): supplicant connection state change: 2 -> 3
Sep 24 10:27:24 helium NetworkManager: <info>  (ath0): supplicant connection state change: 3 -> 4
Sep 24 10:27:34 helium NetworkManager: <info>  (ath0): supplicant connection state change: 4 -> 0
Sep 24 10:27:34 helium NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 2
Sep 24 10:27:34 helium NetworkManager: <info>  (ath0): supplicant connection state change: 2 -> 3
Sep 24 10:27:34 helium NetworkManager: <info>  (ath0): supplicant connection state change: 3 -> 0
Sep 24 10:27:36 helium NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 4
Sep 24 10:27:46 helium NetworkManager: <info>  (ath0): supplicant connection state change: 4 -> 0
Sep 24 10:27:46 helium NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 2
Sep 24 10:27:46 helium NetworkManager: <info>  (ath0): supplicant connection state change: 2 -> 3
Sep 24 10:27:46 helium NetworkManager: <info>  (ath0): supplicant connection state change: 3 -> 0
Sep 24 10:27:46 helium NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 4
Sep 24 10:27:49 helium NetworkManager: <info>  Activation (ath0/wireless): association took too long.
Sep 24 10:27:49 helium NetworkManager: <info>  (ath0): device state change: 5 -> 6
Sep 24 10:27:49 helium NetworkManager: <info>  Activation (ath0/wireless): asking for new secrets
Sep 24 10:27:49 helium NetworkManager: <info>  (ath0): supplicant connection state change: 4 -> 0
Sep 24 10:27:54 helium NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 24 10:27:54 helium NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started...
Sep 24 10:27:54 helium NetworkManager: <info>  (ath0): device state change: 6 -> 4
Sep 24 10:27:54 helium NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled...
Sep 24 10:27:54 helium NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete.
Sep 24 10:27:54 helium NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting...
Sep 24 10:27:54 helium NetworkManager: <info>  (ath0): device state change: 4 -> 5
Sep 24 10:27:54 helium NetworkManager: <info>  Activation (ath0/wireless): connection 'Auto mysid' has security, and secrets exist.  No new secrets needed.
Sep 24 10:27:54 helium NetworkManager: <info>  Config: added 'ssid' value 'mysid'
Sep 24 10:27:54 helium NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Sep 24 10:27:54 helium NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Sep 24 10:27:54 helium NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Sep 24 10:27:54 helium NetworkManager: <info>  Config: added 'proto' value 'WPA RSN'
Sep 24 10:27:54 helium NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP'
Sep 24 10:27:54 helium NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP'
Sep 24 10:27:54 helium NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete.
Sep 24 10:27:54 helium NetworkManager: <info>  Config: set interface ap_scan to 2
Sep 24 10:27:54 helium NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 2
Sep 24 10:27:54 helium NetworkManager: <info>  (ath0): supplicant connection state change: 2 -> 3
Sep 24 10:27:54 helium NetworkManager: <info>  (ath0): supplicant connection state change: 3 -> 4
Sep 24 10:28:04 helium NetworkManager: <info>  (ath0): supplicant connection state change: 4 -> 0
Sep 24 10:28:04 helium NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 2
Sep 24 10:28:04 helium NetworkManager: <info>  (ath0): supplicant connection state change: 2 -> 3
Sep 24 10:28:04 helium NetworkManager: <info>  (ath0): supplicant connection state change: 3 -> 0
Sep 24 10:28:04 helium NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 4
Sep 24 10:28:14 helium NetworkManager: <info>  (ath0): supplicant connection state change: 4 -> 0
Sep 24 10:28:14 helium NetworkManager: <info>  (ath0): supplicant connection state change: 2 -> 3
Sep 24 10:28:14 helium NetworkManager: <info>  (ath0): supplicant connection state change: 3 -> 0
Sep 24 10:28:14 helium NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 4
Sep 24 10:28:19 helium NetworkManager: <info>  Activation (ath0/wireless): association took too long.
Sep 24 10:28:19 helium NetworkManager: <info>  (ath0): device state change: 5 -> 9
Sep 24 10:28:19 helium NetworkManager: <info>  Activation (ath0) failed for access point (mysid)
Sep 24 10:28:19 helium NetworkManager: <info>  Marking connection 'Auto mysid' invalid.
Sep 24 10:28:19 helium NetworkManager: <info>  Activation (ath0) failed.
Sep 24 10:28:19 helium NetworkManager: <info>  (ath0): device state change: 9 -> 3
Sep 24 10:28:19 helium NetworkManager: <info>  (ath0): deactivating device.
Sep 24 10:28:19 helium NetworkManager: <info>  Activation (ath0) starting connection 'mysid'
Sep 24 10:28:19 helium NetworkManager: <info>  (ath0): device state change: 3 -> 4
Sep 24 10:28:19 helium NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 24 10:28:19 helium NetworkManager: <info>  (ath0): supplicant connection state change: 4 -> 0

etc...

```

---

### Post by Ingenium on 2008-09-26
> **KDB9000 said:**
> NM 0.7 is running fine for me and seems to be better then 0.6. I am having trouble with OpenVPN in NM 0.7 now. I am on Hardy, and I also did the upgrade for NM 0.7 OpenVPN. I redid my profile, but when I try to connect it says that "VPN service stop unexpectedly." I am not sure what is wrong or were to start to troubleshoot the problem. Any thoughts?

I'm having the same problem with OpenVPN. Is this a known issue? Anyone have an idea of what the problem actually is?

---

### Post by KDB9000 on 2008-09-30
> **Ingenium said:**
> I'm having the same problem with OpenVPN. Is this a known issue? Anyone have an idea of what the problem actually is?

You need to update to a newer version of OpenVPN. I forget what version number.

Big problem, I did an updated for NM 0.7 today (9/30/08 around 10 PM) and did a restart (well the window manger messed up and I had to restart to fix it), when it came back up it said that there was a problem with some of my applets and asked if I wanted to delete them or not. I did to try and fix the problem but I can't add them back and now I can't run any applications on my system. I am using another computer to write this post. I am going to try and install the old version over it so I can try and get my system back.

---

### Post by Rotarychainsaw on 2008-09-30
I ran into that too, I couldnt run any apps at all, it was really odd. Went to tty4 and did a dist upgrade, pulled down another new nm package and all was well.

---

### Post by Ingenium on 2008-10-01
Upgraded just now and wireless stopped working. iwlist scan shows networks, but network manager shows no wireless networks. Using ethernet for now while I try to fix it. Anyone know how to revert to the previous release? It's not showing up in the package manager.

---

### Post by stereo_steve on 2008-10-01
wifi stopped working for me yesterday as well :-( I use intel 3945 drivers. 

I see an update came though today though via my ethernet connection. I'll check it out later this evening when I get home.

---

### Post by Ingenium on 2008-10-01
I also use the intel 3925 drivers. I just forced an update (apt-get update, apt-get dist-upgrade) and there were no new updates available. 

Is your repository [http://ppa.launchpad.net/network-manager/ubuntu?](http://ppa.launchpad.net/network-manager/ubuntu?)

---

### Post by Ingenium on 2008-10-01
Manually ran wpa_supplicant to try connect to my wireless network. It gave me a few errors and wouldn't connect, but network manager started working after that...weird. No idea if this is reproducible.

---

### Post by Sypher|NL on 2008-10-02
My old NM-applet had the (well known) "always spinning on wired" issue. I was hoping 0.7 would fix it.

It indeed fixed it, but now I cannot use my wireless anymore. It keeps on asking for my WPA2 keys. I've tried multiple accesspoints with all different keys, but it just won't work.

Also, if i tick the 'show passwords' box, the password i see looks encrypted.

Edit: Seems like it doesnt like AES encryption. When I set it to TKIP on my accesspoints (or TKIP+AES) it works.

---

### Post by zenkaon on 2008-10-03
nm-applet 0.7 works great for me. I run ubuntu 8.04 on 2 laptops and 1 PC. 

The wired connection works fine.
The wireless works with WPA2-PSK encryption on intel 2200 and 3800 wireless cards.
I can connect my 3G GSM Huewai E220 modem to the outside world.

Feature request: Would be great if I could connect to the internet using my E220 modem and share this connection with my internal LAN (all connected up with a router with no access to a regular broadband connection)

---

### Post by hackerseraph on 2008-10-18
Bump

Having this same issue; I need to be able to select tkip; anyone come up with any fixes?

---

### Post by tribaal on 2008-10-18
> **hackerseraph said:**
> Bump

Having this same issue; I need to be able to select tkip; anyone come up with any fixes?

That's the only think keeping we from installing Intrepid right now - I need to be able to select TKIP for my university's network...

- Trib'

---

