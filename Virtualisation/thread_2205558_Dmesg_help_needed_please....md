---
title: "Dmesg help needed please..."
date: 2014-02-14
forum: Virtualisation
---

### Post by Samuel_Matthews on 2014-02-14
This is my first time posting on here, i had a quick look around and couldn't work out with sub-forum i should put this in, sorry if i have chosen incorrectly...

I had a ubuntu 12.04.3LTS server running TVHeadEnd, with a RPi as the frontend. Everything was working fine, i then went and brought myself a little Dell Poweredge 1950. I have created a VM of the working server that was running TVHeadEnd, added the USB to the config settings, it gets everything, all the MUX's are there, perfect signal and quality. So i go to set the Pi up, reset all the DVB and PVR databases and its coming up with "TVHeadEnd HTSP: No input detected". So after a while of looking around in the server, i came to the Dmesg log, i have added just the end part (everything from the start of the DVB config):

[ 13.531334] dvb-usb: found a 'Hauppauge Nova-TD Stick (52009)' in cold state, will try to load a firmware
[ 13.548551] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[ 13.821865] e1000: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[ 14.646128] init: failsafe main process (584) killed by TERM signal
[ 15.130773] type=1400 audit(1391719987.659:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=753 comm="apparmor_parser"
[ 15.131423] type=1400 audit(1391719987.663:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=753 comm="apparmor_parser"
[ 15.131645] type=1400 audit(1391719987.663:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=753 comm="apparmor_parser"
[ 15.149650] type=1400 audit(1391719987.679:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=755 comm="apparmor_parser"
[ 18.490533] dib0700: firmware started successfully.
[ 18.993964] dvb-usb: found a 'Hauppauge Nova-TD Stick (52009)' in warm state.
[ 18.994473] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 18.995615] DVB: registering new adapter (Hauppauge Nova-TD Stick (52009))
[ 19.939357] usb 1-1: DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[ 20.524680] DiB0070: successfully identified
[ 20.524690] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 20.527972] DVB: registering new adapter (Hauppauge Nova-TD Stick (52009))
[ 20.999385] usb 1-1: DVB: registering adapter 1 frontend 0 (DiBcom 7000PC)...
[ 21.589969] DiB0070: successfully identified
[ 21.626593] Registered IR keymap rc-dib0700-rc5
[ 21.627205] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:11.0/0000:02:03.0/usb1/1-1/rc/rc0/input5
[ 21.627360] rc0: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:11.0/0000:02:03.0/usb1/1-1/rc/rc0
[ 21.627872] dvb-usb: schedule remote query interval to 50 msecs.
[ 21.627880] dvb-usb: Hauppauge Nova-TD Stick (52009) successfully initialized and connected.
[ 21.631543] usbcore: registered new interface driver dvb_usb_dib0700
[ 21.715817] init: udev-fallback-graphics main process (1029) terminated with status 1 
[/COLOR][/FONT][/COLOR][COLOR=#000000][FONT=UbuntuRegular][COLOR=#333333][COLOR=#405A04][FONT=Ubuntu Mono][FONT=times new roman][ 21.780130] init: plymouth-splash main process (1038) terminated with status 1[/FONT]
[/FONT][/COLOR][/COLOR][/FONT][/COLOR][COLOR=#000000][FONT=UbuntuRegular][COLOR=#333333]

My initial guess would be it has something to do with the IR Key-map, since i never got any the dmesg showing the IR Key-map on the previous server. But I'm completely lost with the last two logs, not sure what either of those are but whatever they are they have been terminated...

---

### Post by howefield on 2014-02-14
Thread closed, duplicate here : [http://ubuntuforums.org/showthread.php?t=2205559](http://ubuntuforums.org/showthread.php?t=2205559)

---

