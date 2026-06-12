---
title: "WiFi Success - Lubuntu 18.04 - rtl8811au - Old Dell Laptop"
date: 2018-09-12
forum: Ubuntu, Linux and OS Chat
---

### Post by electrosteam on 2018-09-12
This is just my story of how I got my WiFi running, hope it helps someone.

Lubuntu 18.04 LTS.
Dell Inspiron 5150, build 2003, 2 GB RAM, Linux 4.15.0-33-generic #36.

Operating via ethernet cable through a TP-link modem/router as no WiFi facility in this laptop.
Original Modem/Router set-up was accomplished separately with a Windows 10 machine and included name and password for each of the 2.4 GHz and 5 GHz channels.

Search web, find EDUP USB dongle, dual band, listed as Linux compatible, cheap.
Purchase, find no written instructions for Linux, CD will not open on Linux machine.
Visit Realtek website, shows chip as Realtek rtl8811au.
Get instructions for Linux, must do a Make on the Kernel - groan !

Search forums, posts indicate rtl8812au driver should match.
Synaptic Package Manager lists rtl8812au-dkms as an acceptable install.
Install rtl8812au-dkms.

Try to operate dongle, frustrated, more searching, find Package nm-applet.
Install nm-applet, no success, mind confused with SSID, ESSID, BSSID MAC, Cloned MAC, Band, Channel, IPv4, IPv6 etc etc
Eventually decided "Cloned MAC Address" not needed for a personal home installation.

Search forums, get all the good Command-line instructions from the contributors here.
Build a text file with the results of all the commands on my system - over 500 lines.
Notable commands:
  ~$ nmcli dev wifi list:
  - shows SSID name, Channel No., Signal strength, Signal Rate, Security type(s) for 2.4 GHz,
  - equivalent data for the 5 GHZ,
  - all the equivalent data for my neighbours (must chat to those running No Security).
  ~$ nmcli -f ssid,bssid:
  - shows brand name of adapter and radio link standard,
  - shows a version of the adapter name, adapter MAC Address, and MTU setting.

One confusing aspect of all this is the use of alternate names for the same thing.
Also that most of the easy help is based on Ubuntu GUI, not the cut-down GUI on Lubuntu.
Perseverence finally pays off and it all starts to make sense.

Examine the nameplate on my TP-Link modem/router and get applicable data:
 - Model No. and Serial No.
 - Default IP Address,
 - MAC Address,
 - Password No. (never used).

Use browser with router nameplate Default IP Address to enquire status at router.
Change User and Password for future web access (from Admin/Admin).
Note MAC for 2.4 GHz same as router nameplate, 5 GHz MAC increment 2 in last digit.
IPv6 Address shown as N/A.
Lots of other details which I inspected with interest, and passed over.

Along the way discover need to re-boot to make settings permanent, and recommendation that the ethernet cable be removed when WiFi in use.

On Lubuntu, select > Preferences > Network Connections > Add New Connection (+) >
    > shows editing dialogue box with name allocated "WiFi connection 1".
Select tab "General":
    - tick box "Automatically connect to this network when available" cleared (Not Tick),
    - text box "Connection priority for auto-activation" default (0),
    - tick box "All users may connect to this network" default (Tick),
    - tick box "Automatically connect to VPN when using this connection" default (Not Tick),
    - text entry box had no default and nothing entered (something with VPN ?).

Select tab "Wi-Fi":
    - text box SSID: enter SSID name from ~$ nmcli dev wifi list,
    - text box Mode: select "Client",
    - text box Band:  select "B/G (2.4 GHz)",
    - text box Channel: enter Channel number from ~$ nmcli dev wifi list,
        - frequency is automatically entered for the selected channel,
    - text box BSSID: enter MAC Address from Router nameplate,
    - text box Device: enter dongle MAC address number from ~$ nmcli -f ssid,bssid,
    - text box "Cloned MAC address": select "Preserve",
    - text box "MTU": enter number from ~$ nmcli -f ssid,bssid.

Select tab "Wi-Fi Security":
    - text box "Security": enter levels from ~$ nmcli dev wifi (may also be Personal etc),
    - text box "Password": enter password previously setup for that channel on the router,
    - tick box "Show Password" left at default (Not Tick).

Select tab "Proxy":
    - left at defaults,
    - text box "Method": default None,
    - otherwise all default Blank.

Select tab "IPv4 Settings":
    - left at defaults,
    - text box "Method": default "Automatic (DHCP)",
    - otherwise all default Blank.

Select tab "IPv6 Settings":
    - left at defaults,
    - text box "Method": default "Automatic",
    - text box "IPv6 privacy extensions:": default "Disabled",
    - text box "IPv6" address generation mode:": default "Stable privacy",
    - otherwise all Blank,
    - selecting box "Routes" > text box all default Blank.

When running, discovered that both the ethernet and WiFi were operating in parallel on my system monitor, GKrellMan.
So my setup has the tick box on the GUI General tab to not automatically connect when available (No Tick).
But, I could not discover the command line entry to start the WiFi, relying on the task bar Network Icon menu selection instead.

Then, the system was updated to Linux 4.15.0-34, and the WiFi no longer worked !
Various command line tests showed the rtl8812 driver no longer operating, and a hint that the kernel version was inconsistent.
So, did a re-install of rtl8812au-dkms to re-establish operation.

Now I cannot find any reference to nm-applet in my package list, but it does show as running with htop.
Also shown as installed is network-manager, which appears to be  the GUI interface containing nm-applet.

John.

---

### Post by slickymaster on 2018-09-13
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

