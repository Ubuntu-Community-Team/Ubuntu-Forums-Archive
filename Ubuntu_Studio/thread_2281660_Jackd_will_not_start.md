---
title: "Jackd will not start"
date: 2015-06-08
forum: Ubuntu Studio
---

### Post by fould12 on 2015-06-08
I am completely new to Ubuntu and Linux in general, so I have no idea what many of the commands are, such as 'sudo' and 'kill'. I also do not understand what Jackd does, or how to set it up, since there are pretty much no tutorials on how to set it up, only what you can do with it after you know everything about it.

The only reason I want to use Jackd is to have MIDI input and output through Wine, and I heard you need Jack to do that. If there is an easier way, PLEASE tell me.

Anyway, whenever I try to start the application, it reports the error:
 [COLOR=#ff0000]Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

 
Mon Jun  8 14:03:19 2015: Starting jack server...
 Mon Jun  8 14:03:19 2015: JACK server starting in realtime mode with priority 10
 Mon Jun  8 14:03:19 2015: ERROR: cannot register object path "/org/freedesktop/ReserveDevice1/Audio0": A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0
 Mon Jun  8 14:03:19 2015: ERROR: Failed to acquire device name : Audio0 error : A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0
 Mon Jun  8 14:03:19 2015: ERROR: Audio device hw:0 cannot be acquired...
 Mon Jun  8 14:03:19 2015: ERROR: Cannot initialize driver
 Mon Jun  8 14:03:19 2015: ERROR: JackServer::Open failed with -1
 Mon Jun  8 14:03:19 2015: ERROR: Failed to open server
 [COLOR=#ff0000]14:03:22.120 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 Mon Jun  8 14:03:21 2015: Saving settings to "/home/kuin/.config/jack/conf.xml" ...



I think it is a problem with pulseaudio, something about pulseaudio needing to release control to Jack, by using something called pulseaudio-module-jack, and the module jackdbus-detect. But I have no idea what a module is, how to get it working, or what it does. I am completely lost because there are pretty much no tutorials on the programs, and it is like everything involved with Linux just expects you to already magically know everything without studying or any guidelines.

Basically, if there is an easy fix to this problem, please tell me. But if I need to know how this works, how to use these programs, and what the problem is in the first place, then PLEASE give me some links to tutorials for people who know pretty much nothing about Linux or Ubuntu.

---

### Post by sandyd on 2015-06-08
If pulseaudio is running, jack cannot run. However you can redirect pulseaudio to jack if you want. See [here]("https://github.com/jackaudio/jackaudio.github.com/wiki/WalkThrough_User_PulseOnJack") for generic instructions on how to do that.
You can disable pulseaudio by running
```

mkdir -p ~/.pulse
echo "autospawn = no" ~/.pulse/client.conf
```

Then, set apps to use jack ports instead of pulseaudio
```

cat << EOF > ~/.asoundrc
pcm.rawjack {
    type jack
    playback_ports {
        0 system:playback_1
        1 system:playback_2
    }
    capture_ports {
        0 system:capture_1
        1 system:capture_2
    }
}

pcm.jack {
    type plug
    slave { pcm "rawjack" }
    hint {
    description "JACK Audio Connection Kit"
    }
}
pcm.!default {
    type plug
    slave { pcm "rawjack" }
}
EOF
```

Then reboot and install qjackctl. Fiddle around with it until your sound settings are right.

---

### Post by jejeman on 2015-06-09
As far as I remember you don't need JACK to utilize MIDI via WINE. It all goes through ALSA. You can use 
```
aconnect
```
to connect MIDI devices

---

