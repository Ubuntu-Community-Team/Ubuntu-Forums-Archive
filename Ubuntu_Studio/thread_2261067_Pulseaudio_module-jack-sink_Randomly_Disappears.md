---
title: "Pulseaudio module-jack-sink Randomly Disappears"
date: 2015-01-16
forum: Ubuntu Studio
---

### Post by marseille2 on 2015-01-16
I have UbuntuStudio 14.04, and seem to have a weird problem with pulseaudio's module-jack-sink. Sometimes it appears (in Patchage, Qjacktl, and pulseaudio volume control), sometimes it doesn't. For instance ... when it's gone, I can't use an app like Mixxx with Jackd... but it will work with alsa. There are also times when I can't use the same app with alsa, and can only run it through Jackd.  

Every now and again, I can reboot and things will be fine ... but that seems to have changed. Module-jack-sink has disappeared :(

 Is there a solution to this and/or is it possible to reload the module from the command line instead?

Previously, I tried:

```
$ pactl load-module module-jack-sink module-jack-source
```

But that was no good. (I shut down all the apps, but I don't think I stopped pulse beforehand, but can't remember). The terminal said:

```
Failure: Module initialization failed
```

Here's the output from pacmd's list of sinks which says some app is suspending it:

```
$ pacmd
Welcome to PulseAudio! Use "help" for usage information.
>>> list-sinks
2 sink(s) available.
    index: 0
    name: <alsa_output.pci-0000_00_14.2.analog-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: APPLICATION 
    priority: 9959
    volume: 0:  82% 1:  82%
            0: -5.26 dB 1: -5.26 dB
            balance 0.00
    base volume: 100%
                 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max request: 0 KiB
    max rewind: 0 KiB
    monitor source: 0
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 1
    configured latency: 0.00 ms; range is 0.50 .. 371.52 ms
    card: 0 <alsa_card.pci-0000_00_14.2>
    module: 5
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "ALC888 Analog"
        alsa.id = "ALC888 Analog"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "0"
        alsa.card_name = "HDA ATI SB"
        alsa.long_card_name = "HDA ATI SB at 0xfe024000 irq 16"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:14.2"
        sysfs.path = "/devices/pci0000:00/0000:00:14.2/sound/card0"
        device.bus = "pci"
        device.vendor.id = "1002"
        device.vendor.name = "Advanced Micro Devices, Inc. [AMD/ATI]"
        device.product.id = "4383"
        device.product.name = "SBx00 Azalia (Intel HDA)"
        device.form_factor = "internal"
        device.string = "front:0"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Analog Stereo"
        device.description = "Built-in Audio Analog Stereo"
        alsa.mixer_name = "Realtek ALC888"
        alsa.components = "HDA:10ec0888,1458a002,00100001"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        analog-output: Analog Output (priority 9900, latency offset 0 usec, available: unknown)
            properties:
                
        analog-output-headphones: Headphones (priority 9000, latency offset 0 usec, available: yes)
            properties:
                device.icon_name = "audio-headphones"
    active port: <analog-output-headphones>
  * index: 1
    name: <bluez_sink.0C_A6_94_B4_F9_F9>
    driver: <module-bluetooth-device.c>
    flags: HARDWARE DECIBEL_VOLUME LATENCY 
    state: IDLE
    suspend cause: 
    priority: 9530
    volume: 0:  33% 1:  33%
            0: -29.22 dB 1: -29.22 dB
            balance 0.00
    base volume: 100%
                 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 44.22 ms
    max request: 3 KiB
    max rewind: 0 KiB
    monitor source: 2
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 1
    fixed latency: 45.32 ms
    card: 1 <bluez_card.0C_A6_94_B4_F9_F9>
    module: 25
    properties:
        bluetooth.protocol = "a2dp"
        device.description = "HK Onyx Studio"
        device.string = "0C:A6:94:B4:F9:F9"
        device.api = "bluez"
        device.class = "sound"
        device.bus = "bluetooth"
        device.form_factor = "speaker"
        bluez.path = "/org/bluez/800/hci0/dev_0C_A6_94_B4_F9_F9"
        bluez.class = "0x240414"
        bluez.name = "HK Onyx Studio"
        device.icon_name = "audio-speakers-bluetooth"
    ports:
        speaker-output: Speaker (priority 0, latency offset -10000 usec, available: yes)
            properties:
                
    active port: <speaker-output>


```

This is is the output of pulseaudio modules:

```
$ pulseaudio --dump-modules
module-alsa-card                        ALSA Card
module-alsa-sink                        ALSA Sink
module-alsa-source                      ALSA Source
module-always-sink                      Always keeps at least one sink loaded even if it's a null one
module-augment-properties               Augment the property sets of streams with additional static information
module-bluetooth-device                 Bluetooth audio sink and source
module-bluetooth-discover               Detect available bluetooth audio devices and load bluetooth audio drivers
module-bluetooth-policy                 When a bluetooth sink or source is added, load module-loopback
module-bluetooth-proximity              Bluetooth Proximity Volume Control
module-card-restore                     Automatically restore profile of cards
module-cli                              Command line interface
module-cli-protocol-tcp                 Command line interface protocol (TCP sockets)
module-cli-protocol-unix                Command line interface protocol (UNIX sockets)
module-combine                          Compatibility module (module-combine rename)
module-combine-sink                     Combine multiple sinks to one
module-dbus-protocol                    D-Bus interface
module-default-device-restore           Automatically restore the default sink and source
module-detect                           Detect available audio hardware and load matching drivers
module-device-manager                   Keep track of devices (and their descriptions) both past and present and prioritise by role
module-device-restore                   Automatically restore the volume/mute state of devices
module-echo-cancel                      Echo Cancellation
module-equalizer-sink                   General Purpose Equalizer
module-esound-sink                      ESOUND Sink
module-filter-apply                     Load filter sinks automatically when needed
module-filter-heuristics                Detect when various filters are desirable
module-gconf                            GConf Adapter
module-http-protocol-tcp                HTTP (TCP sockets)
module-http-protocol-unix               HTTP (UNIX sockets)
module-intended-roles                   Automatically set device of streams based of intended roles of devices
module-jack-sink                        JACK Sink
module-jack-source                      JACK Source
module-jackdbus-detect                  Adds JACK sink/source ports when JACK is started
module-ladspa-sink                      Virtual LADSPA sink
module-loopback                         Loopback from source to sink
module-match                            Playback stream expression matching module
module-mmkbd-evdev                      Multimedia keyboard support via Linux evdev
module-native-protocol-fd               Native protocol autospawn helper
module-native-protocol-tcp              Native protocol (TCP sockets)
module-native-protocol-unix             Native protocol (UNIX sockets)
module-null-sink                        Clocked NULL sink
module-null-source                      Clocked NULL source
module-oss                              OSS Sink/Source
module-pipe-sink                        UNIX pipe sink
module-pipe-source                      UNIX pipe source
module-position-event-sounds            Position event sounds between L and R depending on the position on screen of the widget triggering them.
module-remap-sink                       Virtual channel remapping sink
module-remap-source                     Virtual channel remapping source
module-rescue-streams                   When a sink/source is removed, try to move their streams to the default sink/source
module-role-cork                        Mute & cork streams with certain roles while others exist
module-rtp-recv                         Receive data from a network via RTP/SAP/SDP
module-rtp-send                         Read data from source and send it to the network via RTP/SAP/SDP
module-rygel-media-server               UPnP MediaServer Plugin for Rygel
module-simple-protocol-tcp              Simple protocol (TCP sockets)
module-simple-protocol-unix             Simple protocol (UNIX sockets)
module-sine                             Sine wave generator
module-sine-source                      Sine wave generator source
module-stream-restore                   Automatically restore the volume/mute/device state of streams
module-suspend-on-idle                  When a sink/source is idle for too long, suspend it
module-switch-on-connect                When a sink/source is added, switch to it
module-switch-on-port-available         n/a
module-systemd-login                    Create a client for each login session of this user
module-tunnel-sink                      Tunnel module for sinks
module-tunnel-source                    Tunnel module for sources
module-udev-detect                      Detect available audio hardware and load matching drivers
module-virtual-sink                     Virtual sink
module-virtual-source                   Virtual source
module-virtual-surround-sink            Virtual surround sink
module-volume-restore                   Compatibility module
module-x11-bell                         X11 bell interceptor
module-x11-cork-request                 Synthesize X11 media key events when cork/uncork is requested
module-x11-publish                      X11 credential publisher
module-x11-xsmp                         X11 session management
module-zeroconf-discover                mDNS/DNS-SD Service Discovery
module-zeroconf-publish                 mDNS/DNS-SD Service Publisher
```

---

### Post by marseille2 on 2015-01-16
Go figure... I post a question after days of suffering, and just realized the **pactl** command was wrong (thanks to this old [thread]("http://ubuntuforums.org/archive/index.php/t-1470407.html")). So if anyone wants to know, this is how to solve the issue:

```

$ pactl load-module module-jack-sink
$ pactl load-module module-jack-source

```

Similar to the instructions of the old thread, "Jack sink" should show up in Pulseaudio volume control, in the "Output Devices" tab.

I can also confirm that editing **/etc/pulse/default.pa** to [COLOR=#ff0000]add these lines to the end of the file[/COLOR] worked *after* killing then restarting pulseaudio (*see [old thread]("http://ubuntuforums.org/archive/index.php/t-1470407.html")*):

 ```

load-module module-jack-source
load-module module-jack-sink

```

And most importantly, I can now see Jack sink in both Qjacktl and Patchage to connect them with other audio apps.

---

### Post by oscablenet on 2015-01-24
same problem
thanks
i will try

---

