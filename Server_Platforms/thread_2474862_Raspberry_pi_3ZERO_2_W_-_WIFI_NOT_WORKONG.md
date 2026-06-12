---
title: "Raspberry pi 3/ZERO 2 W - WIFI NOT WORKONG"
date: 2022-05-10
forum: Server Platforms
---

### Post by elsabz on 2022-05-10
[h=2]Raspberry pi 3/ZERO 2 W - WIFI NOT WORKING[/h]
Hello, I tried to install the special ubuntu IOT image (ubuntu-22.04-preinstalled-server-arm64+raspi) for raspberry, version 22.04 and also Ubuntu 20.04.4 LTS (GNU / Linux 5.4.0-1060-raspi aarch64). The installation was successful on Raspberrypi 3 and raspberry pi ZERO 2 W, but unfortunately I can't get WiFi wlan0 to work. I modify the YAML file in the / etc / netplan directory, then I execute the command "netplan generate" and then "netplan apply", no error from the command line, only the wifi is always DOWN and in DORMIENT state.

I tried to install Network-Manager and used it as a renderer in Netplan configuration, so if I switch from one WiFi to another I can get the WiFi to work, it goes to UP and DEFAULT status, unfortunately after the reboot it returns DOWN and in DORMIENT status. I tried other cards like odroid C4 with ubuntu 20.04 mate, with this netplan it works great and the WiFi wlan0 (dongle) is fine.

Can anyone help me?

---

### Post by elsabz on 2022-05-10
I managed to get it to work by installing an old version ubuntu-20.04.3-preinstalled-server-arm64 + raspi.img
I'm not sure if this version change is the solution, maybe I'll try to reinstall version 22.04.[COLOR=#005400][FONT=Monaco]
[/FONT][/COLOR]However after installing this version 20.04 the situation seemed not to change.[COLOR=#005400][FONT=Monaco]
[/FONT][/COLOR]Instead I then tried running the following commands[COLOR=#005400][FONT=Monaco]

sudo ip link set wlan0 up
[/FONT][/COLOR][COLOR=#005400][FONT=Monaco]sudo iw dev wlan0 scan | grep -i ssid

[/FONT][/COLOR]when I launched the second one, the SSID of another AccessPoint appeared but it appears to be in the same subnet[COLOR=#005400][FONT=Monaco]
[/FONT][/COLOR]I then edited the netplan configuration file with this SSID and ran the related commands (generate, apply)[COLOR=#005400][FONT=Monaco]
[/FONT][/COLOR]After this the wlan0 connected even after a reboot.[COLOR=#005400][FONT=Monaco]
[/FONT][/COLOR]I do not understand why this behavior, surely something escapes me that I probably do not know, however I will try to install version 22.04.

---

### Post by MAFoElffen on 2022-06-02
Found this: [https://askubuntu.com/questions/1143287/how-to-setup-of-raspberry-pi-3-onboard-wifi-for-ubuntu-server-with-netplan/1143594#1143594](https://askubuntu.com/questions/1143287/how-to-setup-of-raspberry-pi-3-onboard-wifi-for-ubuntu-server-with-netplan/1143594#1143594)

Answer 26 (Top Answer) explains it fairly well...

---

