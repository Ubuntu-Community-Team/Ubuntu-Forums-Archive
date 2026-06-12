---
title: "Howto remove unwanted sounddevices modules/drivers?"
date: 2016-08-12
forum: Ubuntu/Debian BASED
---

### Post by jonas-thornvall on 2016-08-12
I have a special fork of 14.04 installed called Linuxium for Intel Compute Stick, i was stupid enough to try install lowlatency drivers and packages from KX studio. 
First of all it lacked support for the sounddevice drivers, wifi, bluetooth but what was worse it also installed a sound device called loopback and set it to default.

It do seem that the loopback drivers is part of the alsa package, but not installed normally?

Fortunately there was a script that let me reinstall my sounddevice drivers "kernel", but after reinstallation they still were not working, and in alsamixer there is still the sndaloop/loopback s as default. And i got pulseaudio unable to connect, i really do not need pulseaudio as long as the alsadrivers working for multimedia,gaming and surf->flashbplayer.

So i tried change the default card to Alsa in /usr/share/alsa/alsa.conf it worked but pulse audio was till unable to connect i took it so far to make an installation on another partition and copy the files in /usr/share/alsa/alsa.conf.

But then it still showed loopback device and it was sent to default once again.

Now i am confused because it seem like the module is default both to configuration filed and part of the "kernel modules?" but *normally* it will not be installed although apparently part of the original configuration files and kernel.

But once there it seem impossible to remove?

MY QUESTION how to remove or stop loopback/sndaloop from being loaded at all, i frankly never want to see that module again because it cause trouble.
I think it even breakes the route when i run in jackd mode instead of sound all that comes out is infinite hiss.

In my attempt i changed these lines to device 1 ->"intelHDMI", although it set device to default in alsamixer it did not work out because pulseaudio still refused connection.

defaults.ctl.card 0
defaults.pcm.card 0
defaults.pcm.device 0


My alsa.conf below

```
#
#  ALSA library configuration file
#

# pre-load the configuration files

@hooks [
    {
        func load
        files [
            {
                @func concat
                strings [
                    { @func datadir }
                    "/alsa.conf.d/"
                ]
            }
            "/etc/asound.conf"
            "~/.asoundrc"
        ]
        errors false
    }
]

# load card-specific configuration files (on request)

cards.@hooks [
    {
        func load
        files [
            {
                @func concat
                strings [
                    { @func datadir }
                    "/cards/aliases.conf"
                ]
            }
        ]
    }
    {
        func load_for_all_cards
        files [
            {
                @func concat
                strings [
                    { @func datadir }
                    "/cards/"
                    { @func private_string }
                    ".conf"
                ]
            }
        ]
        errors false
    }
]

#
# defaults
#

# show all name hints also for definitions without hint {} section
defaults.namehint.showall on
# show just basic name hints
defaults.namehint.basic on
# show extended name hints
defaults.namehint.extended on
#
defaults.ctl.card 0
defaults.pcm.card 0
defaults.pcm.device 0
defaults.pcm.subdevice -1
defaults.pcm.nonblock 1
defaults.pcm.compat 0
defaults.pcm.minperiodtime 5000        # in us
defaults.pcm.ipc_key 5678293
defaults.pcm.ipc_gid audio
defaults.pcm.ipc_perm 0660
defaults.pcm.dmix.max_periods 0
defaults.pcm.dmix.rate 48000
defaults.pcm.dmix.format "unchanged"
defaults.pcm.dmix.card defaults.pcm.card
defaults.pcm.dmix.device defaults.pcm.device
defaults.pcm.dsnoop.card defaults.pcm.card
defaults.pcm.dsnoop.device defaults.pcm.device
defaults.pcm.front.card defaults.pcm.card
defaults.pcm.front.device defaults.pcm.device
defaults.pcm.rear.card defaults.pcm.card
defaults.pcm.rear.device defaults.pcm.device
defaults.pcm.center_lfe.card defaults.pcm.card
defaults.pcm.center_lfe.device defaults.pcm.device
defaults.pcm.side.card defaults.pcm.card
defaults.pcm.side.device defaults.pcm.device
defaults.pcm.surround21.card defaults.pcm.card
defaults.pcm.surround21.device defaults.pcm.device
defaults.pcm.surround40.card defaults.pcm.card
defaults.pcm.surround40.device defaults.pcm.device
defaults.pcm.surround41.card defaults.pcm.card
defaults.pcm.surround41.device defaults.pcm.device
defaults.pcm.surround50.card defaults.pcm.card
defaults.pcm.surround50.device defaults.pcm.device
defaults.pcm.surround51.card defaults.pcm.card
defaults.pcm.surround51.device defaults.pcm.device
defaults.pcm.surround71.card defaults.pcm.card
defaults.pcm.surround71.device defaults.pcm.device
defaults.pcm.iec958.card defaults.pcm.card
defaults.pcm.iec958.device defaults.pcm.device
defaults.pcm.modem.card defaults.pcm.card
defaults.pcm.modem.device defaults.pcm.device
# truncate files via file or tee PCM
defaults.pcm.file_format    "raw"
defaults.pcm.file_truncate    true
defaults.rawmidi.card 0
defaults.rawmidi.device 0
defaults.rawmidi.subdevice -1
defaults.hwdep.card 0
defaults.hwdep.device 0
defaults.timer.class 2
defaults.timer.sclass 0
defaults.timer.card 0
defaults.timer.device 0
defaults.timer.subdevice 0

#
#  PCM interface
#

# redirect to load-on-demand extended pcm definitions
pcm.cards cards.pcm

pcm.default cards.pcm.default
pcm.sysdefault cards.pcm.default
pcm.front cards.pcm.front
pcm.rear cards.pcm.rear
pcm.center_lfe cards.pcm.center_lfe
pcm.side cards.pcm.side
pcm.surround21 cards.pcm.surround21
pcm.surround40 cards.pcm.surround40
pcm.surround41 cards.pcm.surround41
pcm.surround50 cards.pcm.surround50
pcm.surround51 cards.pcm.surround51
pcm.surround71 cards.pcm.surround71
pcm.iec958 cards.pcm.iec958
pcm.spdif iec958
pcm.hdmi cards.pcm.hdmi
pcm.dmix cards.pcm.dmix
pcm.dsnoop cards.pcm.dsnoop
pcm.modem cards.pcm.modem
pcm.phoneline cards.pcm.phoneline

pcm.hw {
    @args [ CARD DEV SUBDEV ]
    @args.CARD {
        type string
        default {
            @func getenv
            vars [
                ALSA_PCM_CARD
                ALSA_CARD
            ]
            default {
                @func refer
                name defaults.pcm.card
            }
        }
    }
    @args.DEV {
        type integer
        default {
            @func igetenv
            vars [
                ALSA_PCM_DEVICE
            ]
            default {
                @func refer
                name defaults.pcm.device
            }
        }
    }
    @args.SUBDEV {
        type integer
        default {
            @func refer
            name defaults.pcm.subdevice
        }
    }        
    type hw
    card $CARD
    device $DEV
    subdevice $SUBDEV
    hint {
        show {
            @func refer
            name defaults.namehint.extended
        }
        description "Direct hardware device without any conversions"
    }
}

pcm.plughw {
    @args [ CARD DEV SUBDEV ]
    @args.CARD {
        type string
        default {
            @func getenv
            vars [
                ALSA_PCM_CARD
                ALSA_CARD
            ]
            default {
                @func refer
                name defaults.pcm.card
            }
        }
    }
    @args.DEV {
        type integer
        default {
            @func igetenv
            vars [
                ALSA_PCM_DEVICE
            ]
            default {
                @func refer
                name defaults.pcm.device
            }
        }
    }
    @args.SUBDEV {
        type integer
        default {
            @func refer
            name defaults.pcm.subdevice
        }
    }        
    type plug
    slave.pcm {
        type hw
        card $CARD
        device $DEV
        subdevice $SUBDEV
    }
    hint {
        show {
            @func refer
            name defaults.namehint.extended
        }
        description "Hardware device with all software conversions"
    }
}

pcm.plug {
    @args [ SLAVE ]
    @args.SLAVE {
        type string
    }
    type plug
    slave.pcm $SLAVE
}

pcm.shm {
    @args [ SOCKET PCM ]
    @args.SOCKET {
        type string
    }
    @args.PCM {
        type string
    }
    type shm
    server $SOCKET
    pcm $PCM
}

pcm.tee {
    @args [ SLAVE FILE FORMAT ]
    @args.SLAVE {
        type string
    }
    @args.FILE {
        type string
    }
    @args.FORMAT {
        type string
        default {
            @func refer
            name defaults.pcm.file_format
        }
    }
    type file
    slave.pcm $SLAVE
    file $FILE
    format $FORMAT
    truncate {
        @func refer
        name defaults.pcm.file_truncate
    }
}

pcm.file {
    @args [ FILE FORMAT ]
    @args.FILE {
        type string
    }
    @args.FORMAT {
        type string
        default {
            @func refer
            name defaults.pcm.file_format
        }
    }
    type file
    slave.pcm null
    file $FILE
    format $FORMAT
    truncate {
        @func refer
        name defaults.pcm.file_truncate
    }
}

pcm.null {
    type null
    hint {
        show {
            @func refer
            name defaults.namehint.basic
        }
        description "Discard all samples (playback) or generate zero samples (capture)"
    }
}

#
#  Control interface
#
    
ctl.sysdefault {
    type hw
    card {
        @func getenv
        vars [
            ALSA_CTL_CARD
            ALSA_CARD
        ]
        default {
            @func refer
            name defaults.ctl.card
        }
    }
    hint.description "Default control device"
}
ctl.default ctl.sysdefault

ctl.hw {
    @args [ CARD ]
    @args.CARD {
        type string
        default {
            @func getenv
            vars [
                ALSA_CTL_CARD
                ALSA_CARD
            ]
            default {
                @func refer
                name defaults.ctl.card
            }
        }
    }
    type hw
    card $CARD
    hint.description "Direct control device"
}

ctl.shm {
    @args [ SOCKET CTL ]
    @args.SOCKET {
        type string
    }
    @args.CTL {
        type string
    }
    type shm
    server $SOCKET
    ctl $CTL
}

#
#  RawMidi interface
#

rawmidi.default {
    type hw
    card {
        @func getenv
        vars [
            ALSA_RAWMIDI_CARD
            ALSA_CARD
        ]
        default {
            @func refer
            name defaults.rawmidi.card
        }
    }
    device {
        @func igetenv
        vars [
            ALSA_RAWMIDI_DEVICE
        ]
        default {
            @func refer
            name defaults.rawmidi.device
        }
    }
    hint.description "Default raw MIDI device"
}

rawmidi.hw {
    @args [ CARD DEV SUBDEV ]
    @args.CARD {
        type string
        default {
            @func getenv
            vars [
                ALSA_RAWMIDI_CARD
                ALSA_CARD
            ]
            default {
                @func refer
                name defaults.rawmidi.card
            }
        }
    }
    @args.DEV {
        type integer
        default {
            @func igetenv
            vars [
                ALSA_RAWMIDI_DEVICE
            ]
            default {
                @func refer
                name defaults.rawmidi.device
            }
        }
    }
    @args.SUBDEV {
        type integer
        default -1
    }
    type hw
    card $CARD
    device $DEV
    subdevice $SUBDEV
    hint {
        description "Direct rawmidi driver device"
        device $DEV
    }
}

rawmidi.virtual {
    @args [ MERGE ]
    @args.MERGE {
        type string
        default 1
    }
    type virtual
    merge $MERGE
}

#
#  Sequencer interface
#

seq.default {
    type hw
    hint.description "Default sequencer device"
}

seq.hw {
    type hw
}

#
#  HwDep interface
#

hwdep.default {
    type hw
    card {
        @func getenv
        vars [
            ALSA_HWDEP_CARD
            ALSA_CARD
        ]
        default {
            @func refer
            name defaults.hwdep.card
        }
    }
    device {
        @func igetenv
        vars [
            ALSA_HWDEP_DEVICE
        ]
        default {
            @func refer
            name defaults.hwdep.device
        }
    }
    hint.description "Default hardware dependent device"
}

hwdep.hw {
    @args [ CARD DEV ]
    @args.CARD {
        type string
        default {
            @func getenv
            vars [
                ALSA_HWDEP_CARD
                ALSA_CARD
            ]
            default {
                @func refer
                name defaults.hwdep.card
            }
        }
    }
    @args.DEV {
        type integer
        default {
            @func igetenv
            vars [
                ALSA_HWDEP_DEVICE
            ]
            default {
                @func refer
                name defaults.hwdep.device
            }
        }
    }
    type hw
    card $CARD
    device $DEV
    hint {
        description "Direct hardware dependent device"
        device $DEV
    }
}

#
#  Timer interface
#

timer_query.default {
    type hw
}

timer_query.hw {
    type hw
}

timer.default {
    type hw
    class {
        @func refer
        name defaults.timer.class
    }
    sclass {
        @func refer
        name defaults.timer.sclass
    }
    card {
        @func refer
        name defaults.timer.card
    }
    device {
        @func refer
        name defaults.timer.device
    }
    subdevice {
        @func refer
        name defaults.timer.subdevice
    }
    hint.description "Default timer device"
}

timer.hw {
    @args [ CLASS SCLASS CARD DEV SUBDEV ]
    @args.CLASS {
        type integer
        default {
            @func refer
            name defaults.timer.class
        }
    }
    @args.SCLASS {
        type integer
        default {
            @func refer
            name defaults.timer.sclass
        }
    }
    @args.CARD {
        type string
        default {
            @func refer
            name defaults.timer.card
        }
    }
    @args.DEV {
        type integer
        default {
            @func refer
            name defaults.timer.device
        }
    }
    @args.SUBDEV {
        type integer
        default {
            @func refer
            name defaults.timer.subdevice
        }
    }
    type hw
    class $CLASS
    sclass $SCLASS
    card $CARD
    device $DEV
    subdevice $SUBDEV
    hint {
        description "Direct timer device"
        device $DEV
    }
}
```

---

### Post by howefield on 2016-08-12
Thread moved to the "*Ubuntu/Debian BASED*" forum and .conf file contents enclosed in code tags.

---

### Post by ajgreeny on 2016-08-12
Please use **Code-Tags** for terminal output and any code or configuration files copied to your posts. See my signature below for a **How-to**

---

