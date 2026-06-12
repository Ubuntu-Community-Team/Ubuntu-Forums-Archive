---
title: "VirtualBox 5.0.24 no sound after xenial upgrade"
date: 2016-08-02
forum: Virtualisation
---

### Post by asgard2 on 2016-08-02
Hi,

sound is not working on any of my virtual box machines (Linux and Windows).

Sound on the host is working and activated as before.

VirtualBox guest Linux/lubuntu settings:
- driver: PulseAudio
- controller: ICH AC97

On the guest, audio seems to work, I can see the visual output from pavucontrol.


Maybe it is a problem with VirtualBox Version 5.0.24?

Someone know a solution?

---

### Post by MAFoElffen on 2016-08-02
Sound, USB, Enhanced Video and shared host folders are etxended via Guest Additions and the Extension Pack. Thiose should be the same version at VirtualBox.

After the Version changed to another version, did you uninstall and install those?

---

### Post by asgard2 on 2016-08-02
No I did not uninstall, virtualbox downloaded the guest addons ISO and I installed the new version with the VBoxLinuxAdditions.run file.
After the terminal log, the old version was recognized and successfully replaced.

Now, I purged any virtualbox* package and reinstalled VBox Additions from the iso, still no audio (and acpi) support. USB and Video is working.

---

### Post by MAFoElffen on 2016-08-03
You've said the right things so far, in your setup. Hmm... I guess if we rule out the obvious, i.e. go to settings > sound > ensure the slider is not lid all the way to the left and is not on mute...

---

### Post by asgard2 on 2016-08-04
It is activated, alsamixer settings:
```
state.I82801AAICH {
    control.1 {
        iface MIXER
        name 'Master Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.2 {
        iface MIXER
        name 'Master Playback Volume'
        value.0 31
        value.1 31
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -4650
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.3 {
        iface MIXER
        name 'Master Mono Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.4 {
        iface MIXER
        name 'Master Mono Playback Volume'
        value.0 63
        value.1 63
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 63'
            dbmin -9450
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.5 {
        iface MIXER
        name 'Beep Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.6 {
        iface MIXER
        name 'Beep Playback Volume'
        value 0
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 15'
            dbmin -4500
            dbmax 0
            dbvalue.0 -4500
        }
    }
    control.7 {
        iface MIXER
        name 'Phone Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.8 {
        iface MIXER
        name 'Phone Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 63'
            dbmin -3450
            dbmax 6000
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.9 {
        iface MIXER
        name 'Mic Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.10 {
        iface MIXER
        name 'Mic Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 63'
            dbmin -3450
            dbmax 6000
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.11 {
        iface MIXER
        name 'Mic Boost (+20dB)'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.12 {
        iface MIXER
        name 'Line Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.13 {
        iface MIXER
        name 'Line Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.14 {
        iface MIXER
        name 'CD Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.15 {
        iface MIXER
        name 'CD Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 63'
            dbmin -3450
            dbmax 6000
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.16 {
        iface MIXER
        name 'Video Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.17 {
        iface MIXER
        name 'Video Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 63'
            dbmin -3450
            dbmax 6000
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.18 {
        iface MIXER
        name 'Aux Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.19 {
        iface MIXER
        name 'Aux Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 63'
            dbmin -3450
            dbmax 6000
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.20 {
        iface MIXER
        name 'PCM Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.21 {
        iface MIXER
        name 'PCM Playback Volume'
        value.0 30
        value.1 30
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 1050
            dbvalue.1 1050
        }
    }
    control.22 {
        iface MIXER
        name 'Capture Source'
        value.0 Mic
        value.1 Mic
        comment {
            access 'read write'
            type ENUMERATED
            count 2
            item.0 Mic
            item.1 CD
            item.2 Video
            item.3 Aux
            item.4 Line
            item.5 Mix
            item.6 'Mix Mono'
            item.7 Phone
        }
    }
    control.23 {
        iface MIXER
        name 'Capture Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.24 {
        iface MIXER
        name 'Capture Volume'
        value.0 14
        value.1 14
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 15'
            dbmin 0
            dbmax 2250
            dbvalue.0 2100
            dbvalue.1 2100
        }
    }
    control.25 {
        iface MIXER
        name 'PCM Out Path & Mute'
        value 'pre 3D'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 'pre 3D'
            item.1 'post 3D'
        }
    }
    control.26 {
        iface MIXER
        name '3D Control - Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.27 {
        iface MIXER
        name 'Mono Output Select'
        value Mix
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Mix
            item.1 Mic
        }
    }
    control.28 {
        iface MIXER
        name 'Mic Select'
        value Mic1
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Mic1
            item.1 Mic2
        }
    }
    control.29 {
        iface MIXER
        name '3D Control Sigmatel - Depth'
        value 1
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 3'
        }
    }
    control.30 {
        iface MIXER
        name 'Sigmatel DAC 6dB Attenuate'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.31 {
        iface MIXER
        name 'Sigmatel ADC 6dB Attenuate'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.32 {
        iface MIXER
        name 'Sigmatel 4-Speaker Stereo Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.33 {
        iface MIXER
        name 'Surround Phase Inversion Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.34 {
        iface MIXER
        name 'External Amplifier'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.35 {
        iface PCM
        name 'Playback Channel Map'
        value.0 3
        value.1 4
        comment {
            access read
            type INTEGER
            count 2
            range '0 - 36'
        }
    }
}


```
[ATTACH=CONFIG]270571[/ATTACH][ATTACH=CONFIG]270572[/ATTACH][ATTACH=CONFIG]270573[/ATTACH]

But the speaker icon is kind of odd with "---" ?

---

