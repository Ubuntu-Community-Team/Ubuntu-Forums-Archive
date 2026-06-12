---
title: "bluetooth headsets: a2dp profile doesn't work without restarting the service"
date: 2021-02-01
forum: Ubuntu/Debian BASED
---

### Post by momkinghacker on 2021-02-01
First time I try to connect, I get the headphones connected, but the "High Fidelity Playback(A2DP Sink)" isn't available, only "Headset Head Unit(HSP/HFP)" which sounds like ****. Then I do `systemctl restart bluetooth` and this time "High Fidelity Playback(A2DP Sink)" appears, but to make sound work, I need to start `pavucontrol` and switch profile to "off" and back to "High Fidelity Playback(A2DP Sink)". If I restart the service again, it would go back to the initial state(headset_head_unit is available, a2dp_sink is not). 

After the service restart I get this in `systemctl status bluetooth`:

```
&#9679; bluetooth.service - Bluetooth service
     Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
     Active: active (running) since Mon 2021-02-01 20:40:36 CET; 6s ago
       Docs: man:bluetoothd(8)
   Main PID: 6250 (bluetoothd)
     Status: "Running"
      Tasks: 1 (limit: 19013)
     Memory: 660.0K
     CGroup: /system.slice/bluetooth.service
             &#9492;&#9472;6250 /usr/lib/bluetooth/bluetoothd

Feb 01 20:40:36 user-tobefilledbyoem bluetoothd[6250]: Bluetooth daemon 5.53
Feb 01 20:40:36 user-tobefilledbyoem systemd[1]: Started Bluetooth service.
Feb 01 20:40:36 user-tobefilledbyoem bluetoothd[6250]: Starting SDP server
Feb 01 20:40:36 user-tobefilledbyoem bluetoothd[6250]: Bluetooth management interface 1.18 initialized
Feb 01 20:40:36 user-tobefilledbyoem bluetoothd[6250]: Endpoint registered: sender=:1.36 path=/MediaEndpoint/A2DPSink/sbc
Feb 01 20:40:36 user-tobefilledbyoem bluetoothd[6250]: Endpoint registered: sender=:1.36 path=/MediaEndpoint/A2DPSource/sbc
Feb 01 20:40:36 user-tobefilledbyoem bluetoothd[6250]: Endpoint registered: sender=:1.46 path=/MediaEndpoint/A2DPSink/sbc
Feb 01 20:40:36 user-tobefilledbyoem bluetoothd[6250]: Endpoint registered: sender=:1.46 path=/MediaEndpoint/A2DPSource/sbc
Feb 01 20:40:36 user-tobefilledbyoem bluetoothd[6250]: RFCOMM server failed for Headset Voice gateway: rfcomm_bind: Address already in use (98)
Feb 01 20:40:36 user-tobefilledbyoem bluetoothd[6250]: RFCOMM server failed for :1.36/Profile/HSPHSProfile/00001108-0000-1000-8000-00805f9b34fb: rfcomm_bind: Address already in use (98)
```

and when I connect the headphones, I get 3 extra lines:

```
 Feb 01 20:40:50 user-tobefilledbyoem bluetoothd[6250]: Unable to connect Headset Voice gateway: connect: Device or resource busy (16)
Feb 01 20:40:50 user-tobefilledbyoem bluetoothd[6250]: Connecting Headset Voice gateway failed: Input/output error
Feb 01 20:40:53 user-tobefilledbyoem bluetoothd[6250]: /org/bluez/hci0/dev_00_1B_66_E9_40_9A/sep1/fd0: fd(44) ready
```

`pacmd list-cards` when there's no a2dp:

    ```
index: 6
        name: <bluez_card.00_1B_66_E9_40_9A>
        driver: <module-bluez5-device.c>
        owner module: 32
        properties:
                device.description = "MOMENTUM 3"
                device.string = "00:1B:66:E9:40:9A"
                device.api = "bluez"
                device.class = "sound"
                device.bus = "bluetooth"
                device.form_factor = "headset"
                bluez.path = "/org/bluez/hci0/dev_00_1B_66_E9_40_9A"
                bluez.class = "0x240404"
                bluez.alias = "MOMENTUM 3"
                device.icon_name = "audio-headset-bluetooth"
                device.intended_roles = "phone"
        profiles:
                headset_head_unit: Headset Head Unit (HSP/HFP) (priority 30, available: yes)
                a2dp_sink: High Fidelity Playback (A2DP Sink) (priority 40, available: no)
                off: Off (priority 0, available: yes)
        active profile: <headset_head_unit>
        sinks:
                bluez_sink.00_1B_66_E9_40_9A.headset_head_unit/#4: MOMENTUM 3
        sources:
                bluez_sink.00_1B_66_E9_40_9A.headset_head_unit.monitor/#7: Monitor of MOMENTUM 3
                bluez_source.00_1B_66_E9_40_9A.headset_head_unit/#8: MOMENTUM 3
        ports:
                headset-output: Headset (priority 0, latency offset 0 usec, available: yes)
                        properties:

                headset-input: Headset (priority 0, latency offset 0 usec, available: yes)
                        properties:
```

`pacmd list-cards` when there is a2dp:

```
     index: 7
        name: <bluez_card.00_1B_66_E9_40_9A>
        driver: <module-bluez5-device.c>
        owner module: 33
        properties:
                device.description = "MOMENTUM 3"
                device.string = "00:1B:66:E9:40:9A"
                device.api = "bluez"
                device.class = "sound"
                device.bus = "bluetooth"
                device.form_factor = "headset"
                bluez.path = "/org/bluez/hci0/dev_00_1B_66_E9_40_9A"
                bluez.class = "0x240404"
                bluez.alias = "MOMENTUM 3"
                device.icon_name = "audio-headset-bluetooth"
                device.intended_roles = "phone"
        profiles:
                headset_head_unit: Headset Head Unit (HSP/HFP) (priority 30, available: no)
                a2dp_sink: High Fidelity Playback (A2DP Sink) (priority 40, available: unknown)
                off: Off (priority 0, available: yes)
        active profile: <a2dp_sink>
        sinks:
                bluez_sink.00_1B_66_E9_40_9A.a2dp_sink/#5: MOMENTUM 3
        sources:
                bluez_sink.00_1B_66_E9_40_9A.a2dp_sink.monitor/#9: Monitor of MOMENTUM 3
        ports:
                headset-output: Headset (priority 0, latency offset 0 usec, available: unknown)
                        properties:

                headset-input: Headset (priority 0, latency offset 0 usec, available: no)
                        properties:
```

OS - KDE neon 5.20 aka Ubuntu 20.04

Kernel - 5.10.0-1011-oem, but same thing on linux-image-5.4.0

What could be the issue? What other information can I provide?

---

### Post by howefield on 2021-02-01
Thread moved to the "*Ubuntu/Debian BASED*" forum.

PS. Pease change your quote tags to code tags.

---

### Post by momkinghacker on 2021-02-02
I figured out that there were 2 instances of pulseaudio, one was started by user `user`, second by user `sddm` and it seems that both were started by systemd(at least it's what I saw in pstree), so I temporarily removed `/usr/lib/systemd/user/pulseaudio.{service,socket}`, added `pulseaudio --start` to plasma's autostart and it works like a charm, I don't even need to switch profiles back and forth to get sound. The real solution would be to figure out why there's a second instance and deal with it. 

These links may be helpful(but not for me, I'm too dumb): 

[https://bbs.archlinux.org/viewtopic.php?id=175241](https://bbs.archlinux.org/viewtopic.php?id=175241) 
[https://unix.stackexchange.com/questions/204522/how-does-pulseaudio-start](https://unix.stackexchange.com/questions/204522/how-does-pulseaudio-start)

---

