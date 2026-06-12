---
title: "problem with Wireless card in kali"
date: 2015-11-02
forum: Ubuntu/Debian BASED
---

### Post by mohammad14 on 2015-11-02
Hi please help me for install driver my wirrles card in kali

lsusb:

```
Bus 002 Device 007: ID 1740:9603 Senao RTL8188S WLAN Adapter
Bus 002 Device 004: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 001 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

iwconfig:

```
[COLOR=#000000][COLOR=#0000BB]          
lo        no wireless extensions[/COLOR][COLOR=#007700].

[/COLOR][COLOR=#0000BB]eth0      no wireless extensions[/COLOR][COLOR=#007700].

[/COLOR][COLOR=#0000BB]wlan1     unassociated  Nickname[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#DD0000]"rtl_wifi"
          [/COLOR][COLOR=#0000BB]Mode[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]Managed  Access Point[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000BB]Not[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]Associated   Sensitivity[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]0[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]0  
          Retry[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]off   RTS thr[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]off   Fragment thr[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]off
          Encryption key[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]off
          Power Management[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]off
          Link Quality[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]0  Signal level[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]0  Noise level[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]0
          Rx invalid nwid[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]0  Rx invalid crypt[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]0  Rx invalid frag[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]0
          Tx excessive retries[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]0  Invalid misc[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]0   Missed beacon[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]0  [/COLOR][/COLOR]
```

airmon-ng start wlan1:

```
[COLOR=#000000][COLOR=#0000BB]No interfering processes found
PHY    [/COLOR][COLOR=#007700]Interface    [/COLOR][COLOR=#0000BB]Driver        Chipset

null    wlan1        r8712u        Senao RTL8188S WLAN Adapterphy1    wlan2        rt2800usb    Ralink Technology[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000BB]Corp[/COLOR][COLOR=#007700]. [/COLOR][COLOR=#0000BB]RT5370  [/COLOR][/COLOR]
```

---

### Post by howefield on 2015-11-02
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

