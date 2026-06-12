---
title: "Ofono/Pulseaudio A2DP vs. HFP (HFGW)"
date: 2012-02-07
forum: Ubuntu Dev Link Forum
---

### Post by tol007 on 2012-02-07
Hi.
I have trouble with pulseaudio/ofono/bluez configuration. I would like to configure my PC as headset (two-way audio routing HFP). I tried to configure pulseaudio according to [http://padovan.org/blog/2010/02/handsfree-profile-into-bluez-and-ofono/](http://padovan.org/blog/2010/02/handsfree-profile-into-bluez-and-ofono/) but it doesn't work. Bluetooth card is not visible after pairing my smartphone ( /etc/bluetooth/audio.conf  with option “Enable=Gateway” ). I have enabled all interfaces in bluez/audio/manager.c such as GATEWAY TRUE, HFP TRUE, SOCKET TRUE. After that my bt sound card is visible in pulseaudio (pactl list). After establishing of modem connection (ofono/test/enable-modem) I can see only A2DP audio connection. There is no way to change this option to Handsfree Gateway although hfgw profile is visible in bt sound card:
```
    
Profile:
        a2dp_source:   (A2DP) (sinks: 0, sources: 1, priority. 10)
        hfgw: Handsfree Gateway (sinks: 1, sources: 1, priority. 20)
        off:  (sinks: 0, sources: 0, priority. 0)

```When I'm trying to switch profile to hfgw (pactl set-card-profile <soundcard.name> <profile>) then pulseaudio shows that hfgw is not connected according to attached logs:
```

D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Client added for object /org/pulseaudio/core1/client11
D: [pulseaudio] protocol-native.c: Protocol version: remote 23, local 23
I: [pulseaudio] protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
D: [pulseaudio] protocol-native.c: SHM possible: yes
D: [pulseaudio] protocol-native.c: Negotiated SHM: yes
D: [pulseaudio] module-augment-properties.c: Looking for .desktop file for pactl
**W: [pulseaudio] module-bluetooth-device.c: HandsfreeGateway is not connected, refused to switch profile**
I: [pulseaudio] client.c: Freed 11 "pactl"
I: [pulseaudio] protocol-native.c: Connection died.
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Client removed from object /org/pulseaudio/core1/client11

```After pairing everything seems to be fine. I can enable modem by ofono and SCO is opened when I try to make a call. Anyone know what's wrong? (ubuntu 10.10, bluez 4.98, pulseaudio 1.1. Ofono 1.3)

---

### Post by heuristicist on 2012-05-17
I recently ran into the same issue. After *much* experimentation, it looks like the HFGW profile only becomes available when the phone is actually in a call. I had the commands to set up change the profile and set up the loopback ready to go, then I initiated a call, and then quickly ran the commands and got the speaker sound coming out of my computer's speakers, which was my objective. Unfortunately, the quality was quite poor. I don't know which part of the stack is the problem in this case (ofono, pulse, or bluez) but it seems that the demo video that is out there of this same process has the same quality issue. :\

---

### Post by swatijoshi on 2012-06-15
Hi Please help me regarding this,

before heading to ofono pulse audio routing ( which is working fine on other system but not our target system) please help me in 
**connecting the bluetooth mobile to ubuntu system using bluez**

currently we are working on bluetooth hands free profile (HFP).
  
[LIST]
[*]we are using bluez 4.96
[*]the following changes are made in the audio.conf file in  /etc/bluetooth/audio             HandsFreeGatweway = Enabled              HFP = true
[*]Ubuntu version tried on 11.04 and 11.10
[*]x86 processor.
[/LIST]
  we are able to connect the device. However the connection is not  stable and within few seconds of connection it gets disconnected  automatically.
  Please help us to establish a stable connection.

---

