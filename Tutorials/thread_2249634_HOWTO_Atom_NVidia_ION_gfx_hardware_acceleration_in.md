---
title: "HOWTO: Atom NVidia ION gfx hardware acceleration in Flash and MPlayer"
date: 2014-10-23
forum: Tutorials
---

### Post by trancephorm on 2014-10-23
Hi!

For the ones that own Asus AT5IONT-I Atom motherboard with NVidia ION graphics or similar hardware, here's what is needed to make it work flawlessly in Lubuntu 14.04.

[LIST]
[*]Install proprietary video drivers
```

sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings

```
[*]Big desktop fonts are solved with DPI parameter in /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf

[*]Install VDPAU support
```

sudo apt-get install libvdpau1 vdpau-va-driver

```

[*]Install Mozilla Flash plugin along with some tweaking so Flash is able to use hardware for decoding
```

sudo apt-get install flashplugin-installer
sudo mkdir /etc/adobe
sudo echo -e "EnableLinuxHWVideoDecode = 1\nOverrideGPUValidation = 1" | sudo tee /etc/adobe/mms.cfg

```
[*]Install Pulseaudio along with Pulseaudio Volume Control
```

sudo apt-get install pulseaudio pulseaudio-utils pavucontrol

```
[*]Setup ALSA to use HDMI audio output (if you're using HDMI for that)
insert "options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2" in "/etc/modprobe.d/alsa-base.conf"

[*]Setup default audio to HDMI in Pulseaudio
```

pacmd list-cards   ## You should get a list of cards you have, and each card will have a list of profiles.  Get the index number of the card you want.
pacmd set-card-profile 1 output:hdmi-stereo

```
edit /etc/pulse/default.pa and at the bottom put:
```

set-card-profile 1 	output:hdmi-stereo
set-default-sink 1

```
[*]Install newest SMPlayer for your video player needs, and also you have a nice Youtube player in it which is stable contrary to occasionally crashing Flash in FF.
```

sudo add-apt-repository ppa:rvm/smplayer 
sudo apt-get update
sudo apt-get install smplayer smtube smplayer-themes smplayer-skins

```
[*] ~/.mplayer/config file should contain these lines at least:
```

ao=pulse
vo=vdpau
vc=ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau,

```
[*]Setup SMPlayer preferences according to parameters in ~/.mplayer/config

[*]Paste these lines to ~/pa-vol.sh and make the file executable, so it can be used in LXDE environment for volume up/down/mute
```

#!/bin/bash
# CHANGES, RE-VIEWS/WRITES, IMPROVEMENTS:
# mhasko: functions; VOL-steps; 
# gashapon: autodectect default sink
# konrad: more reliable way to autodetect default sink
 
# get default sink name
SINK_NAME=$(pacmd dump | perl -a -n -e 'print $F[1] if /set-default-sink/')
# try this line instead of the one above if you got problems with the detection of your default sink.
#SINK_NAME=$(pactl stat | grep "alsa_output" | perl -a -n -e 'print $F[2]')
 
# set max allowed volume; 0x10000 = 100%
VOL_MAX="0x10000"
 
STEPS="16" # 2^n
VOL_STEP=$((VOL_MAX / STEPS))
 
VOL_NOW=`pacmd dump | grep -P "^set-sink-volume $SINK_NAME\s+" | perl -p -n -e 's/.+\s(.x.+)$/$1/'`
MUTE_STATE=`pacmd dump | grep -P "^set-sink-mute $SINK_NAME\s+" | perl -p -n -e 's/.+\s(yes|no)$/$1/'`
 
function plus() {
        VOL_NEW=$((VOL_NOW + VOL_STEP))
        if [ $VOL_NEW -gt $((VOL_MAX)) ]; then
                VOL_NEW=$((VOL_MAX))
        fi
        pactl set-sink-volume $SINK_NAME `printf "0x%X" $VOL_NEW`
}
 
function minus() {
        VOL_NEW=$((VOL_NOW - VOL_STEP))
        if [ $(($VOL_NEW)) -lt $((0x00000)) ]; then
                VOL_NEW=$((0x00000))
        fi
        pactl set-sink-volume $SINK_NAME `printf "0x%X" $VOL_NEW`
}
 
function mute() {
        if [ $MUTE_STATE = no ]; then
                pactl set-sink-mute $SINK_NAME 1
        elif [ $MUTE_STATE = yes ]; then
                pactl set-sink-mute $SINK_NAME 0
        fi
}
 
function get() {
        BAR=""
        if [ $MUTE_STATE = yes ]; then
                BAR="mute"
                ITERATOR=$((STEPS / 2 - 2))
                while [ $ITERATOR -gt 0 ]; do
                        BAR=" ${BAR} "
                        ITERATOR=$((ITERATOR - 1))
                done
        else
                DENOMINATOR=$((VOL_MAX / STEPS))
                LINES=$((VOL_NOW / DENOMINATOR))
                DOTS=$((STEPS - LINES))
                while [ $LINES -gt 0 ]; do
                        BAR="${BAR}|"
                        LINES=$((LINES - 1))
                done
                while [ $DOTS -gt 0 ]; do
                        BAR="${BAR}."
                        DOTS=$((DOTS - 1))
                done
        fi
        echo "$BAR"
}
 
case "$1" in
        plus)
                plus
        ;;
        minus)
                minus
        ;;
        mute)
                mute
        ;;
        get)
                get
esac

```

[*]Paste these lines into <keyboard></keyboard> section of ~/.config/openbox/lubuntu-rc.xml
```

   <keybind key="XF86AudioMute">
      <action name="Execute">
       <command>pa-vol.sh mute</command>
      </action>
    </keybind>
     <keybind key="XF86AudioRaiseVolume">
      <action name="Execute">
       <command>pa-vol.sh plus<command>
      </action>
    </keybind>
     <keybind key="XF86AudioLowerVolume">
      <action name="Execute">
       <command>pa-vol.sh minus</command>
      </action>
    </keybind>

```

[*]Install ssh server so you can connect Android's MPlayerSSH remote control application to mplayer.
```

sudo apt-get install openssh-server

```

[*]Install Unified Remote server so you can use Unified Remote from Android, multimedia keys. [http://www.unifiedremote.com](http://www.unifiedremote.com)
[/LIST]

This was just a quick tutorial, but if something goes wrong, feel free to ask.... Hope it helps.

---

