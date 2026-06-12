---
title: "Starting JACK from script"
date: 2011-02-15
forum: Ubuntu Studio
---

### Post by Cerapter on 2011-02-15
I'm using my MIDI keyboard in Ubuntu using JACK, (qjackctl,) Linuxsampler and Rosegarden. My problem is, this all takes a long while to boot up, and every time, I have to add some connections in qjackctl to make it all run smoothly.

Is there any way I can either replace qjackctl in this specific instance by running a script, or give qjackctl commands through the script? If I could boot up this whole gizmajig of software by pressing just one button, I would be very happy.

---

### Post by RaumTrug on 2011-02-15
```
ls /usr/bin/jack*
```

lots of command-line tools there that mess with jack. qjackctl is just a gui, so things like "jack_connect" will also show up in qjack immediately. remember to put some "sleep" lines between the commands (i.e. launching a prog, then sleep a few seconds, then connect), to make sure the program is done loading & ready before messing with connections and such, also after launching jackd & before starting the progs.

---

### Post by _oscar_ on 2011-02-16
Or you might consider defining (and activating) a patchbay, available in qjackctl

---

### Post by Pablo_F on 2011-02-16
Hi, 

This can help:

[http://digitaldub.wordpress.com/2009/12/16/linux-audio-session-scripting/](http://digitaldub.wordpress.com/2009/12/16/linux-audio-session-scripting/)

[http://wiki.linuxaudio.org/apps/all/jack_snapshot](http://wiki.linuxaudio.org/apps/all/jack_snapshot)

However, it seems that tapas.affenbade.org is down. Instead, you can use aj-snapshot: 

[http://sourceforge.net/projects/aj-snapshot/](http://sourceforge.net/projects/aj-snapshot/)

Also, you could try ladish:

[http://ladish.org/](http://ladish.org/)


Another option, as oscar pointed out, is the qjacktl patchbay:

[http://www.rncbc.org/drupal/node/76](http://www.rncbc.org/drupal/node/76)

but you can't start programs with this.


In linuxmusicians.com there is an interesting thread on linux audio sessions.

Cheers, Pablo

---

### Post by AutoStatic on 2011-02-16
> **Cerapter said:**
> Is there any way I can either replace qjackctl in this specific instance by running a script, or give qjackctl commands through the script? If I could boot up this whole gizmajig of software by pressing just one button, I would be very happy.There is also Ladish, and Jack Session. But if you'd really like to script it **jack_connect** and **aconnect** are your friends. Some examples: [http://ubuntuforums.org/showthread.php?t=1663228](http://ubuntuforums.org/showthread.php?t=1663228)

Best,

Jeremy

---

### Post by Cerapter on 2011-02-17
Thanks for a lot of great resources! Ladish seems neat, and I'll try it if I find it too hard to make a script.

I only wish I could make Qjackctl output what it does, so I can add only the missing details. I guess aj-snapshot would do something similar, so I'll try that.

EDIT: when I tried building or configuring aj-snapshot, it gave me this:
```
checking alsa/asoundlib.h usability... no
checking alsa/asoundlib.h presence... no
checking for alsa/asoundlib.h... no
checking jack/jack.h usability... no
checking jack/jack.h presence... no
checking for jack/jack.h... no
checking mxml.h usability... no
checking mxml.h presence... no
checking for mxml.h... no
checking for main in -lasound... no
configure: error: ALSA library (asound) is required
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
```I have never lacked anything JACK and ALSA related, so I find this quite strange. Any ideas?

---

### Post by AutoStatic on 2011-02-17
> **Cerapter said:**
> I only wish I could make Qjackctl output what it does, so I can add only the missing details.What do you mean exactly? You can list all ports known to JACK with **jack_lsp**

> **Cerapter said:**
> EDIT: when I tried building or configuring aj-snapshot, it gave me this:
[code]checking alsa/asoundlib.h usability... no
checking alsa/asoundlib.h presence... no
checking for alsa/asoundlib.h... nolibasound2-dev: /usr/include/alsa/asoundlib.h

> **Cerapter said:**
> checking jack/jack.h usability... no
checking jack/jack.h presence... no
checking for jack/jack.h... nolibjack-dev: /usr/include/jack/jack.h

> **Cerapter said:**
> checking mxml.h usability... no
checking mxml.h presence... no
checking for mxml.h... nolibmxml-dev: /usr/include/mxml.h

> **Cerapter said:**
> I have never lacked anything JACK and ALSA related, so I find this quite strange. Any ideas?Yes, you're lacking the aforementioned -dev packages, so install those and you should be good to go.

Best,

Jeremy

---

### Post by Cerapter on 2011-02-18
Thanks, dev files didn't occur to me. I installed them and installed aj-snapshot, and it seems to do its job. :D

> **AutoStatic said:**
> What do you mean exactly? You can list all ports known to JACK with **jack_lsp**

I wish I could write to file all of the jack commands that qjackctl performs in the background as I press the buttons. Perhaps there's some secret and important command that I now omit! But after an initial moment of frustration, I seem to have a script that works like I wished.

One thing that's bugging me, though, is this message that I get when starting up jack:
```
cerapter@Ancalagon:~$ pasuspender -- jackd -d alsa -d "hw:1" &

(...)

Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    1536492
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
SSE2 detected
creating alsa driver ... hw:1|hw:1|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:1
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 24bit big-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 24bit big-endian
ALSA: use 2 periods for playback
gave up!
gave up!
```
Should I listen to the memory warning? I opened the file and added the line, but I still get this. It also hangs for an awful long time until it gives up, do you know if any of that is normal?

---

### Post by AutoStatic on 2011-02-19
> **Cerapter said:**
> I wish I could write to file all of the jack commands that qjackctl performs in the background as I press the buttons.Which buttons? You mean the transport buttons? You can control those with the **jack_transport** utility:
```
jeremy@piertje:~$ jack_transport
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    2297862
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:Intel|hw:Intel|1024|2|48000|0|0|nomon|swmeter|-|32bit
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
jack_transport> help
activate		Call jack_activate().
avr		Set audio/video frame ratio <audio frames per video frame>.
exit		Exit transport program.
deactivate		Call jack_deactivate().
help		Display help text [<command>].
locate		Locate to frame <position>.
master		Become timebase master [<conditionally>].
play		Start transport rolling.
quit		Synonym for `exit'.
release		Release timebase.
stop		Stop transport.
tempo		Set beat tempo <beats_per_min>.
timeout		Set sync timeout in <seconds>.
?		Synonym for `help'.
```


> **Cerapter said:**
> Perhaps there's some secret and important command that I now omit! But after an initial moment of frustration, I seem to have a script that works like I wished.

One thing that's bugging me, though, is this message that I get when starting up jack:
```
cerapter@Ancalagon:~$ pasuspender -- jackd -d alsa -d "hw:1" &
```JACK probably gives up because of the ampersand you've used at the end of your command. I'm not sure namely how pasuspender responds to such a command. I think it is best not use pasuspender but to create a *client.conf* file in your */home/yourusername/.pulse* directory with the line *autospawn = no* in it and run **pulseaudio -k** before running JACK. I think this is also the cause why JACK hangs so long before giving up.

> **Cerapter said:**
> Should I listen to the memory warning?No, it's ok. This issue is being discussed atm. While JACK gives a warning Ardour doesn't run properly without unlimited memlocking while both apps have the same original author.

Best,

Jeremy

---

### Post by Cerapter on 2011-02-21
Pardon my lack of specificity. I do not know what you mean by transport buttons, but I meant "everything I do with qjackctl, and also everything it does when it starts up". With Fantasia, I can export an LDCP script that does what Fantasia did last time, and I wanted to do the same with qjackctl.

> **AutoStatic said:**
> 
JACK probably gives up because of the ampersand you've used at the end  of your command. I'm not sure namely how pasuspender responds to such a  command. I think it is best not use pasuspender but to create a *client.conf* file in your */home/yourusername/.pulse* directory with the line *autospawn = no* in it and run **pulseaudio -k** before running JACK. I think this is also the cause why JACK hangs so long before giving up.

I did this, but as I feared, pulseaudio no longer resumes operation after I kill jack. In fact, I cannot seem to connect it even manually. I suppose this problem could be unrelated, but if I don't figure it out, is there a command I should run, upon quitting my audio session, that brings pulseaudio back to normal?

---

### Post by Pablo_F on 2011-02-21
> I did this, but as I feared, pulseaudio no longer resumes operation after I kill jack. In fact, I cannot seem to connect it even manually. I suppose this problem could be unrelated, but if I don't figure it out, is there a command I should run, upon quitting my audio session, that brings pulseaudio back to normal? 

You can use scripts around jackd in qjackctl (Setup, Options, scripting). For example, this is my startup script (the first one, executed just before the jack server):


#!/bin/bash
#autospawn no, kill pulseaudio and wait a sec
sed -i 's/yes/no/g' ~/.pulse/client.conf 
pulseaudio -k 
sleep 1
#Clean up /dev/shm by deleting the files left over by Pulseaudio.
#Just in case
#See [https://bugs.launchpad.net/ubuntu/+source/jack-audio-connection-kit/+bug/491329](https://bugs.launchpad.net/ubuntu/+source/jack-audio-connection-kit/+bug/491329)
rm -f /dev/shm/pulse*

Now, the post shutdown script (the 4th one):

#!/bin/bash
#Not sure if this is needed but it does not hurt
killall jackd
sleep 1
# Autospawn yes and start pulseaudio
sed -i 's/no/yes/g' ~/.pulse/client.conf
pulseaudio --start


This way, when I kill jackd, I have pulseaudio up and running again. 


You can apply the idea to your script even if you don't use qjackctl. 

Or you can also execute a poststart script (second one in qjackctl' scripts) which launches the apps, restore connections, etc.

And the third one, the shutdown script, where you can take a snaphot of the jackd connections and then kill the jack clients you use. Or something like that. 

This way, you use qjackctl as the main program of your studio, with the start and stop buttons (the main ones, not the transport ones of course).

Just an idea. 

Cheers, Pablo

---

### Post by Cerapter on 2011-02-22
Thanks, that did the trick for pulseaudio! Jack also seems to be more happy now that I don't use pasuspender.

I wrote a long and sloppy bash script to accomodate all of my session options. I bet it's unorthodox, but it does the trick and pleases my peculiar way of doing things. I'll post it here in case it's of interest. Otherwise, I'm marking this as solved. Thanks for all your help, AutoStatic especially!

```
#!/bin/bash

if [ "$1" = "start" ]; then
    # audio session start

    # pause pulseaudio
    sed -i 's/yes/no/g' ~/.pulse/client.conf
    pulseaudio -k 
    # start jack on guitar rig (could sometimes be hw:2!!)
    jackd -d alsa -d "hw:1" &
    sleep 3

    if [ "$2" = "piano" ]; then
        # don't play the pipe organ!
        killall -w aeolus

        # play the grand maestro!
        linuxsampler &
        sleep 5
        # make jsampler/qsampler redundant!
        cat ~/jsampler_jack.lscp | netcat localhost 8888 &
        sleep 2
        # load the linuxsampler jack connections
        aj-snapshot -r ~/lsampler.xml &

        if [ "$3" = "rosep" ]; then
            # start rosegarden and pianobooster
            sleep 2
            rosegarden &
            sleep 3
            pianobooster &
            sleep 5
            # load these connections
            aj-snapshot -r ~/alt_pbooster.xml &
        fi
    fi
    if [ "$2" = "organ" ]; then
        # don't play the grand maestro!
        killall -w linuxsampler
        killall -w rosegarden
        killall -w pianobooster

        # play the pipe organ!
        aeolus &
        sleep 2
        # load the aeolus jack connections
        aj-snapshot -r ~/porgan.xml &
    fi
else
    # audio session quit
    killall -w linuxsampler
    killall -w rosegarden
    killall -w pianobooster
    killall -w jackd
    killall -w aeolus

    # resume pulseaudio
    sed -i 's/no/yes/g' ~/.pulse/client.conf
    pulseaudio --start
fi
```

---

### Post by Pablo_F on 2011-02-22
Nice script, thanks for sharing!

>  # start jack on guitar rig (could sometimes be hw:2!!)
    jackd -d alsa -d "hw:1" &

If we use card names instead of numbers, we won't have to worry about jack using the wrong interface. 

Call it *hw:Name* where Name is the name of the card that you want Jack to use. You can see it in the terminal output of *cat /proc/asound/cards*, between square brackets. 

Cheers, Pablo

---

### Post by Cerapter on 2011-03-09
I cleaned up the script and made it easier to expand. In the process, I learned how to use **jack_connect** and **aconnect**, and I also came to learn the -c option for jack_lsp, which made it so much more useful. With this, I could live without aj-snapshot/jack-snapshot. (I did not find a jack_lsp equivalent for ALSA, so I had to use qjackctl's connections dock for that part).

The result: all of my audio sessions in one file (plus any lscp files for linuxsampler).

```
#!/bin/bash

# PART 1: software starters
function start_grandmaestro {
    if [ ! "$(pidof linuxsampler)" ]; then
        linuxsampler &
        sleep 3
        # run the lscp script I made in Fantasia
        cat ~/scripts/jsampler_jack.lscp | netcat localhost 8888 &
        sleep 2
        
        # basic JACK and ALSA connections
        aconnect 'Hua Xing':0 LinuxSampler:0
        jack_connect system:playback_1 LinuxSampler:0
        jack_connect system:playback_2 LinuxSampler:1
    fi
}
function start_aeolus {
    if [ ! "$(pidof aeolus)" ]; then
        aeolus &
        sleep 2
        
        # basic JACK and ALSA connections
        aconnect 'Hua Xing':0 aeolus:0
        jack_connect system:playback_1 aeolus:out.L
        jack_connect system:playback_2 aeolus:out.R
    fi
}
function start_rosegarden {
    if [ ! "$(pidof rosegarden)" ]; then
        rosegarden &
        sleep 2

        # basic JACK and ALSA connections
        # (Rosegarden does this automatically too)
        aconnect System:1 rosegarden:0
        jack_connect system:capture_1 "rosegarden:record in 1 L"
        jack_connect system:capture_2 "rosegarden:record in 1 R"
        jack_connect system:playback_1 "rosegarden:master out L"
        jack_connect system:playback_2 "rosegarden:master out R"
    fi
}
function start_pianobooster {
    if [ ! "$(pidof pianobooster)" ]; then
        pianobooster &
        sleep 1

        # basic JACK and ALSA connections
        aconnect "Hua Xing":0 "RTMidi Input Client":0
    fi
}

# PART 2: basic functions
function start_jackd {
    if [ ! "$(pidof jackd)" ]; then
        # pause pulseaudio
        sed -i 's/yes/no/g' ~/.pulse/client.conf
        pulseaudio -k 
        # start jack on guitar rig
        jackd -d alsa -d "hw:GuitarRigMobile" &
        sleep 1
        rm -f /dev/shm/pulse*
    fi
}
function quit_session {
    # quit all audio software
    killall -w linuxsampler &
    killall -w rosegarden &
    killall -w pianobooster &
    killall -w jackd &
    killall -w aeolus &
    killall -w aj-snapshot &
    sleep 1

    # resume pulseaudio
    sed -i 's/no/yes/g' ~/.pulse/client.conf
    pulseaudio --start
}
function check_connections {
    if [ "$(pidof linuxsampler)" -o "$(pidof rosegarden)" ]; then
        aconnect rosegarden:3 LinuxSampler:1
    fi

    if [ "$(pidof aeolus)" -o "$(pidof rosegarden)" ]; then
        aconnect rosegarden:3 aeolus:1
    fi

    if [ "$(pidof pianobooster)" -o "$(pidof rosegarden)" ]; then
        aconnect "RtMidi Output Client":0 rosegarden:0
    fi
}

# PART 3: communicating with the script
if [ "$1" = "start" ]; then
    # audio session start
    start_jackd

    # play the grand maestro!
    if [ "$2" = "piano" ]; then
        killall -w aeolus
        start_grandmaestro
    fi

    # play the pipe organ!
    if [ "$2" = "organ" ]; then
        killall -w linuxsampler
        start_aeolus
    fi

    # open rosegarden
    if [ "$3" = "rose" ]; then
        start_rosegarden
    else
        killall -w rosegarden
    fi

    # open piano booster
    if [ "$4" = "pboost" ]; then
        start_pianobooster
    else
        killall -w pianobooster
    fi

    # apply cross-software connections
    check_connections
else
    quit_session
fi
```Run examples include:
*./audio.sh start piano rose* - sets up the grand maestro gigasampler file and opens rosegarden, all connections are taken care of
*./audio.sh start whatev rose pboost* - just starts rosegarden and piano booster, and connect whatever instrument is found (useless if none)
*./audio.sh* - exits the audio session

---

