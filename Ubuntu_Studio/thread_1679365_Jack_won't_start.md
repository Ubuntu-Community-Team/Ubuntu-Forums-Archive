---
title: "Jack won't start"
date: 2011-01-31
forum: Ubuntu Studio
---

### Post by piovezan on 2011-01-31
Hi all,

This is what I get when I try to start the Jack server via its GUI (JACK Control). It first fails to connect to the server, which is expected since jackd is not configured to run at startup:

[COLOR=#999999]23:50:07.958 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]23:50:07.981 Statistics reset.[/COLOR]
 Cannot connect to server socket err = Arquivo ou diretÃ³rio nÃ£o encontrado
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]23:50:08.013 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]23:50:08.208 ALSA connection change.[/COLOR]
 [COLOR=#999999]
[/COLOR]
Then the real trouble begins, when it starts the server and throws a succession of read errors:
[COLOR=#999999]
[/COLOR]
[COLOR=#999999]23:55:46.686 Startup script...[/COLOR]
 [COLOR=#990099]23:55:46.686 artsshell -q terminate[/COLOR]
 Cannot connect to server socket err = Arquivo ou diretÃ³rio nÃ£o encontrado
 Cannot connect to server socket
 jack server is not running or cannot be started
 sh: artsshell: not found
 [COLOR=#999999]23:55:47.088 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]23:55:47.088 JACK is starting...[/COLOR]
 [COLOR=#990099]23:55:47.089 /usr/bin/jackd -dalsa -dhw:0 -r192000 -p1024 -n3[/COLOR]
 [COLOR=#999999]23:55:47.099 JACK was started with PID=3703.[/COLOR]
 no message buffer overruns
 no message buffer overruns
 jackdmp 1.9.6
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2010 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK server starting in realtime mode with priority 10
 audio_reservation_init
 Acquire audio card Audio0
 creating alsa driver ... hw:0|hw:0|1024|3|192000|0|0|nomon|swmeter|-|32bit
 Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xfe978000 irq 43
 configuring for 192000Hz, period = 1024 frames (5.3 ms), buffer = 3 periods
 ALSA: final selected sample format for capture: 32bit integer little-endian
 ALSA: use 3 periods for capture
 ALSA: final selected sample format for playback: 32bit integer little-endian
 ALSA: use 3 periods for playback
 playback and capture sample rates do not match (96000 vs. 192000)
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 [COLOR=#ff0000]23:55:54.112 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.[/COLOR]
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
 Driver is not running
 JackSocketClientChannel read fail
 Cannot create new client
 Cannot open qjackctl client
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 [COLOR=#999999]23:55:57.196 JACK is stopping...[/COLOR]
 jack main caught signal 15
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 Released audio card Audio0
 audio_reservation_finish
 [COLOR=#999999]23:55:57.383 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]23:55:57.384 Post-shutdown script...[/COLOR]
 [COLOR=#990099]23:55:57.384 killall jackd[/COLOR]
 jackd: processo nÃ£o achado
 [COLOR=#999999]23:55:57.789 Post-shutdown script terminated with exit status=256.[/COLOR]


I'm using UbuntuStudio  10.10. Tried first the stock kernel (2.6.35-22), then installed all the required Synaptic updates, and finally tried the latest kernel (2.6.35-25). I'm now considering downgrading it to 32 after [another forum topic]("http://ubuntuforums.org/showthread.php?t=1593095&page=3").

I believe the "playback and capture sample rates do not match (96000 vs. 192000)" message is not an issue, since the read errors still occur even if I eliminate the message by changing the capture sample rate to 96000. BTW, tweaking the parameters around didn't make it work either.

I suspect it may be related to some other issue in my basic sound setup. In System > Preferences > Sound, I'm using the Analog Stereo Duplex profile but the speaker test fails as I'm not able to hear anything in my analog phones. Does it make sense to guess that all the sound is being directed to digital output even under that profile? (I lack hardware to test it anyway). The Synaptic updates did improve things for Audacious, which now outputs to the default PCM device (with the stock installation it wouldn't,  using either ALSA or PulseAudio, and I had to set it to the a specific PCM device from the list).

Any clues?

Thanks![FONT=Courier New]
[/FONT]

---

### Post by AutoStatic on 2011-02-01
Your onboard card can handle it but not at such low latencies. Try doubling your Frames/Period setting to 2048 or even higher.
Or lower your sample rate and set 2 for Periods/Buffer instead of 3. You only use 3 for bus driven devices like USB or FireWire.

Best,

Jeremy

---

### Post by Pablo_F on 2011-02-01
Yes, optimal jack settings depend on your hardware to a great extent.

In addition, System > Preferences > Sound is not basic sound setup, it is pulseaudio setup. Jack ignores System > Preferences > Sound, but not lower level alsa tools like alsamixer.

You can see your basic hardware-software sound setup by running the alsa-info.sh script. This command will do it:

wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

Feel free to upload the result and give the URL so we can try to help you better.

Cheers, Pablo

---

### Post by piovezan on 2011-02-01
Hi people, thanks a lot for the quick feedback.

I went for the high sample rate settings because they were giving me the lowest latencies according to JACK Control and I thought the sound card could handle it no matter how low the latency was. Anyway sample rates of 44100 or 48000 were the first ones I tried and didn't provide better results. I changed the Frames/Period and Periods/Buffer settings as recommended by AutoStatic but the read errors still take place, so I think I'm missing something else.

This is the result of alsa-info.sh: [http://www.alsa-project.org/db/?f=50c01c3d4001a3790eb164ea2a7dc1f8ec4a41db](http://www.alsa-project.org/db/?f=50c01c3d4001a3790eb164ea2a7dc1f8ec4a41db) . Hope it gives a clue about the sound test issue as well.

Thanks!

---

### Post by piovezan on 2011-02-01
Good news! Jackd started with Audio set to "Playback Only". No idea why, though. Perhaps it is worthwhile to get this clarified before the topic is closed.
[COLOR=#cccc99][/COLOR]

---

### Post by AutoStatic on 2011-02-02
> **piovezan said:**
> Good news! Jackd started with Audio set to "Playback Only".That's because your soundcard probably cannot handle full duplex at such high sample rates. I'd suggest to set the sample rate to 48000 and try getting the Frames size as low as possible. @ 48Khz you can go as low as 2ms (system) latency, that should suffice I guess ;)
For more info on attaining such low latencies: [http://wiki.linuxmusicians.com/doku.php?id=system_configuration](http://wiki.linuxmusicians.com/doku.php?id=system_configuration)

Best,

Jeremy

---

### Post by piovezan on 2011-02-02
Thanks for your reply AutoStatic! Actually I had given up high sample rates since you first recommended against them. With 48000 or even lower the Duplex and Capture Only modes are still not possible, whatever the Frames/Period size is. Strangely enough, if I downgrade to Jackd1 (0.118) the Duplex mode 'works' (throwing XRUNs for every configuration I try) and Capture Only mode fails due to an "impossible sample width (1) discovered!" error.

I have checked your link and run Quickscan and found a few potential system limitations (highlighted). I'd like to understand how much they can interfere in this case, and also whether they are expected to exist in my UbuntuStudio installation (10.10 + Synaptic updates) or are the result of some installation/update mistake. SOUND_CARD_IRQ is set as requested by the script in a previous run for better diagnosis.


[FONT=Courier New][COLOR=black]$ export SOUND_CARD_IRQ=44
$ ./realTimeConfigQuickScan.pl[/COLOR][/FONT][FONT=Courier New]
== GUI-enabled checks ==
Checking if you are root... no - good
Checking filesystem 'noatime' parameter... 2.6.35 kernel - good
(relatime is default since 2.6.30)
[/FONT]  [FONT=Courier New][COLOR=Red]Checking CPU Governors... CPU 0: 'ondemand' CPU 1: 'ondemand'  - not good[/COLOR][/FONT] [FONT=Courier New]
Set CPU Governors to 'performance' with 'cpufreq-set -c <cpunr> -g performance'
See also: [http://linuxmusicians.com/viewtopic.php?f=27&t=844](http://linuxmusicians.com/viewtopic.php?f=27&t=844)
[/FONT] [FONT=Courier New][COLOR=Red]Checking swappiness... 60 - not good[/COLOR][/FONT] [FONT=Courier New]
** vm.swappiness is larger than 10
set it with '/sbin/sysctl -w vm.swappiness=10'
See also: [http://linuxmusicians.com/viewtopic.php?f=27&t=452&start=30#p8916](http://linuxmusicians.com/viewtopic.php?f=27&t=452&start=30#p8916)
Checking for resource-intensive background processes... none found - good
[/FONT] [FONT=Courier New][COLOR=Red]Checking checking sysctl inotify max_user_watches... < 524288 - not good[/COLOR][/FONT] [FONT=Courier New]
increase max_user_watches by adding 'fs.inotify.max_user_watches = 524288' to /etc/sysctl.conf and rebooting
For more information, see [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#sysctl.conf](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#sysctl.conf)
[/FONT] [FONT=Courier New][COLOR=Red]Checking access to the high precision event timer... not readable - not good[/COLOR][/FONT] [FONT=Courier New]
/dev/hpet found, but not readable.
make /dev/hpet readable by the 'audio' group
For more information, see [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#hpet](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#hpet)
[/FONT] [FONT=Courier New][COLOR=Red]Checking access to the real-time clock... not readable - not good[/COLOR][/FONT] [FONT=Courier New]
/dev/rtc found, but not readable.
make /dev/rtc readable by the 'audio' group
For more information, see [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#real-time_clock](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#real-time_clock)
Checking whether you're in the 'audio' group... yes - good
Checking for multiple 'audio' groups... no - good
yes - good.
Checking the ability to prioritize processes with chrt... yes - good
== Other checks ==
Finding current kernel config... found /boot/config-2.6.35-25-generic
[/FONT] [FONT=Courier New][COLOR=Red]Checking for Ingo Molnar's Real-Time Preemption... not found.[/COLOR][/FONT] [FONT=Courier New]
** Kernel without real-time capabilities found
   For more information, see [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#installing_a_real-time_kernel](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#installing_a_real-time_kernel)
Checking for high-resolution timers... found - good.
[/FONT] [FONT=Courier New][COLOR=Red]Checking for 1000hz clock... not found.[/COLOR][/FONT] [FONT=Courier New]
** Try setting your clock to 1000hz
   For more information, see:
   * [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#installing_a_real-time_kernel](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#installing_a_real-time_kernel)
   * [http://www.rosegardenmusic.com/wiki/frequently_asked_questions#what_does_system_timer_resolution_is_too_low_mean](http://www.rosegardenmusic.com/wiki/frequently_asked_questions#what_does_system_timer_resolution_is_too_low_mean)
Checking for High Resolution Timers... found - good.
Checking filesystem types... ok.
not found.
[/FONT] [FONT=Courier New][COLOR=Red]** Warning: no tmpfs partition mounted on /tmp[/COLOR][/FONT] [FONT=Courier New]
   For more information, see:
   - [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#tmpfs](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#tmpfs)
   - [http://lowlatency.linuxaudio.org](http://lowlatency.linuxaudio.org)[/FONT]

---

### Post by genmi on 2011-02-03
I have recently reinstalled, am now running 10.10 studio with jackdmp version 1.9.6 and am getting the same error messages as this other gentleman. I will provide it in any case:

```
[COLOR=#999999]12:20:22.227 JACK is starting...[/COLOR] [COLOR=#990099]12:20:22.228 /usr/bin/jackd -dalsa -dhw:0 -r48000 -p2048 -n2[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 Cannot create thread 1 Operation not permitted
 [COLOR=#999999]12:20:22.351 JACK was started with PID=9786.[/COLOR]
 Cannot create thread 1 Operation not permitted
 jackdmp 1.9.6
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2010 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK server starting in realtime mode with priority 10
 Cannot lock down memory area (Cannot allocate memory)
 audio_reservation_init
 Acquire audio card Audio0
 creating alsa driver ... hw:0|hw:0|2048|2|48000|0|0|nomon|swmeter|-|32bit
 Using ALSA driver HDA-Intel running on card 0 - HDA ATI SB at 0xc0000000 irq 16
 configuring for 48000Hz, period = 2048 frames (42.7 ms), buffer = 2 periods
 ALSA: final selected sample format for capture: 32bit integer little-endian
 ALSA: use 2 periods for capture
 ALSA: final selected sample format for playback: 32bit integer little-endian
 ALSA: use 2 periods for playback
 Cannot use real-time scheduling (RR/10)(1: Operation not permitted)
 AcquireSelfRealTime error
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 [COLOR=#FF0000]12:20:29.573 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.[/COLOR]
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
 Driver is not running
 Cannot create new client
 JackSocketClientChannel read fail
 Cannot open qjackctl client
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 alsa_driver_xrun_recovery
 JackAudioDriver::ProcessAsync: read error, skip cycle
 [COLOR=#999999]12:20:30.986 JACK is stopping...[/COLOR]
 alsa_driver_xrun_recovery
 jack main caught signal 15
 JackAudioDriver::ProcessAsync: read error, skip cycle
 Released audio card Audio0
 audio_reservation_finish
 [COLOR=#999999]12:20:31.072 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]12:20:31.074 Post-shutdown script...[/COLOR]
 [COLOR=#990099]12:20:31.076 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]12:20:31.509 Post-shutdown script terminated with exit status=256.[/COLOR]
```


I have followed the advice on this: Turned sample rate up to 4800. Turned frames/period to 2048. Still this error persists.

---

### Post by piovezan on 2011-02-03
Hey genmi, I'm new to this but I think your issue is not the same as mine, despite the similar read errors. I've seen these errors being caused by various reasons. In your log there is a particular message which I remember being reported by other users in (solved) topics here and there:

"**Cannot lock down memory area (Cannot allocate memory)**"

It is discussed for example in [this forum topic]("http://ubuntuforums.org/showthread.php?t=1637399"). It may have something to do with your system configuration, access permissions, etc. Give it a look and also try a Google search for this message, I'm sure this is a fairly common issue.

Best regards!

---

### Post by AutoStatic on 2011-02-04
> **piovezan said:**
> Strangely enough, if I downgrade to Jackd1 (0.118) the Duplex mode 'works' (throwing XRUNs for every configuration I try) and Capture Only mode fails due to an "impossible sample width (1) discovered!" error.That's a known issue iirc. Not sure what the cause was, something with soundcards not liking to be run in non-duplex mode.

> **piovezan said:**
> I have checked your link and run Quickscan and found a few potential system limitations (highlighted). I'd like to understand how much they can interfere in this case, and also whether they are expected to exist in my UbuntuStudio installation (10.10 + Synaptic updates) or are the result of some installation/update mistake.The limitations are expected to exist. Ubuntu Studio is poorly optimized. There are few distro's who get this right, I think atm only AV Linux and Tango Studio, maybe KX Studio.

When it comes to the output of the Quickscan script, please use code blocks ;) Performance-wise it is always better to disable CPU frequency scaling or set the governor to performance (even though recent versions of JACK cope better with CPU scaling). Lowering swappiness prevents your system from swapping too soon and too much. Not sure if raising inotify_max_user_watches boosts performance significantly. I don't think so, but the less overhead, the better. I've done some research on what inotify does exactly and it's still unclear to me how much overhead this stuff is causing. When it comes to the hardware timers and the clock frequency, this only matters when you do a lot of MIDI stuff. Adjusting these settings doesn't yield better performance. And don't worry about the tmpfs warning, recent JACK versions use a different temporary filesystem so this warning is a bit deprecated.

Best,

Jeremy

---

### Post by piovezan on 2011-02-04
> **AutoStatic said:**
> The limitations are expected to exist. Ubuntu Studio is poorly optimized. . There are few distro's who get this right, I think atm only AV Linux and Tango Studio, maybe KX Studio.

How 'poorly' do you mean? In the case of 10.10 I agree to an extent due to all those problems Quickscan reported, what about 10.04 with the linux-rt package? I ask that after inferring from the [UbuntuStudioRealTimeKernel]("https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel") page that most audio users don't need extremely low latency except in a few cases, thus only a few audio-oriented distros resort to optimizing everything. So perhaps Ubuntu Studio can be considered only another 'moderately' optimized distro?


> **AutoStatic said:**
> Performance-wise it is always better to disable CPU frequency scaling or set the governor to performance (even though recent versions of JACK cope better with CPU scaling). Lowering swappiness prevents your system from swapping too soon and too much. Not sure if raising inotify_max_user_watches boosts performance significantly. I don't think so, but the less overhead, the better. I've done some research on what inotify does exactly and it's still unclear to me how much overhead this stuff is causing. When it comes to the hardware timers and the clock frequency, this only matters when you do a lot of MIDI stuff. Adjusting these settings doesn't yield better performance. And don't worry about the tmpfs warning, recent JACK versions use a different temporary filesystem so this warning is a bit deprecated.

I'm trying everything except for the kernel recompiling + setting clock to 1000Hz and will comment soon.
BTW since the tmpfs warning is deprecated, shouldn't the script be doing something about this? Like checking the JACK version or something?

---

### Post by AutoStatic on 2011-02-04
> **piovezan said:**
> How 'poorly' do you mean? In the case of 10.10 I agree to an extent due to all those problems Quickscan reported, what about 10.04 with the linux-rt package? I ask that after inferring from the [UbuntuStudioRealTimeKernel]("https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel") page that most audio users don't need extremely low latency except in a few cases, thus only a few audio-oriented distros resort to optimizing everything. So perhaps Ubuntu Studio can be considered only another 'moderately' optimized distro?I wasn't referring to latency, even though the lower the latency the more this demands from your system. With poorly optimized I mean that I personally think a default Ubuntu Studio installation is not optimized for serious music production. With or without -rt kernel. Besides, the 2.6.31-11-rt kernel for 10.04 is not the best -rt kernel ever either. If you just want to try out some music software or occasionally record something it's ok. But I wouldn't record/mix a 20+ track project on it.

> **piovezan said:**
> I'm trying everything except for the kernel recompiling + setting clock to 1000Hz and will comment soon.If you're using 10.04 grab the real-time kernel from Tango Studio and then there shouldn't be any need to recompile.

> **piovezan said:**
> BTW since the tmpfs warning is deprecated, shouldn't the script be doing something about this? Like checking the JACK version or something?Well, you could try contacting the author of the script. Haven't seen him (raboof) here in a while though ;) He's on IRC, #opensourcemusicians on Freenode.

Best,

Jeremy

---

### Post by piovezan on 2011-02-04
> **AutoStatic said:**
> I wasn't referring to latency, even though the lower the latency the more this demands from your system. With poorly optimized I mean that I personally think a default Ubuntu Studio installation is not optimized for serious music production. With or without -rt kernel. Besides, the 2.6.31-11-rt kernel for 10.04 is not the best -rt kernel ever either. If you just want to try out some music software or occasionally record something it's ok. But I wouldn't record/mix a 20+ track project on it.

I see. And why in your opinion is so difficult for most audio-oriented distros to come up with the lowest latencies for both hobbyist and pro usage at once?

You see, I'm still unsure that Ubuntu Studio isn't suited for 20+ track projects because I'm a novice computer audio user. So perhaps I simply have a wrong idea of what the limitations of computer-aided composition are. I do have previous composing experience with different approaches on Windows (MIDI sequencing + soundfonts, MOD tracking, wave editing), and I believe I can use either Rosegarden or a DAW such as Ardour to integrate MIDI and audio recording, along with extra stuff like a software drum machine and some kind of real-time effect software, both of which can be pipelined into the whole process (though the integration details are not quite clear to me yet). I have a notion that certain steps are stronger candidates to cause bottlenecks than others, such as processing real-time effects and software synthesis, besides the track mixing itself. For now I don't have equipment that could reduce the system load (e.g. a  dedicated soundcard or external synthesizer), and, since the paradigm  is computer-centered, I doubt external hardware can play a huge role in  reducing the system load (but I might be assuming wrong). I don't think 20+ track compositions will be too uncommon, based both on MIDI and audio recording. And I think  it's only natural for a novice like me to expect that any audio-oriented  low latency distro flavor will do, and that for such systems a 'heavy' project would have a far bigger track count than 20+, perhaps 40+ or 50+.


> **AutoStatic said:**
> Well, you could try contacting the author of the script. Haven't seen him (raboof) here in a while though ;) He's on IRC, #opensourcemusicians on Freenode.

Great, I'll be glad to get involved! :D

---

### Post by AutoStatic on 2011-02-05
> **piovezan said:**
> And why in your opinion is so difficult for most audio-oriented distros to come up with the lowest latencies for both hobbyist and pro usage at once?Because you can't focus on both groups at once, they have totally different demands. And add to this that some simply are less knowledgeable about optimizing the system for real-time low latency work. 

> **piovezan said:**
> You see, I'm still unsure that Ubuntu Studio isn't suited for 20+ track projects because I'm a novice computer audio user. So perhaps I simply have a wrong idea of what the limitations of computer-aided composition are.No you don't. I've been there too. I've come to realize that the computer, the OS and the software are all tools for a musician, just like instruments. If you get to know these tools better you will get better results. With GNU/Linux the learning is indeed steeper than with a Macbook and ProTools (but even then it really helps if you know what you're doing) but I've decided to choose GNU/Linux as my OS of choice so I had to deal with its drawbacks and hop on the rollercoaster ride. I'm almost at the end of the ride. And I didn't get sick yet, I really enjoyed it so far actually.

> **piovezan said:**
> I have a notion that certain steps are stronger candidates to cause bottlenecks than others, such as processing real-time effects and software synthesis, besides the track mixing itself.Well, you're actually spot on ;)

> **piovezan said:**
> For now I don't have equipment that could reduce the system load (e.g. a  dedicated soundcard or external synthesizer), and, since the paradigm  is computer-centered, I doubt external hardware can play a huge role in  reducing the system load (but I might be assuming wrong).You're spot on again ;) For me, it's all about a clean and well configured system. With such a system you can even do what you just described by using your onboard card.

> **piovezan said:**
> I don't think 20+ track compositions will be too uncommon, based both on MIDI and audio recording.No, you'll easily get there. And I should differentiate a bit here, 20+ audio and MIDI tracks shouldn't be an issue, but as soon as you'll start adding plug-ins to those tracks and maybe hook up some softsynths via inserts then you will most certainly run into problems.

> **piovezan said:**
> And I think  it's only natural for a novice like me to expect that any audio-oriented  low latency distro flavor will do, and that for such systems a 'heavy' project would have a far bigger track count than 20+, perhaps 40+ or 50+.True. And this is where Ubuntu Studio should work on, to come up to that expectation. At the moment I really doubt that. As a novice with such an expectation you're better off with Tango Studio or a bit more hardcore, AV Linux or 64 Studio (when the new version will be released). Mind you though that I've never used those distro's myself, I only use plain Ubuntu and modify it to my likings. So if I make any false assumptions here I stand corrected beforehand.       

Best,

Jeremy

---

### Post by dawiba on 2011-02-05
> **AutoStatic said:**
> Because you can't focus on both groups at once, they have totally different demands.

I don't follow why you can't do this. How are the demands totally different?

> **Autostatic said:**
> And add to this that some simply are less knowledgeable about optimizing the system for real-time low latency work.

All the more reason a system (particularly one which calls itself a Studio distro) should be properly configured OOTB, surely?

---

### Post by raboofje on 2011-02-05
> **AutoStatic said:**
> don't worry about the tmpfs warning, recent JACK versions use a different temporary filesystem so this warning is a bit deprecated.

Yeah, jack moved to /dev/shm. Are there still other applications that use /tmp for storing realtime temporary data? if not that check should be removed i guess.

---

### Post by AutoStatic on 2011-02-05
> **dawiba said:**
> I don't follow why you can't do this. How are the demands totally different?What do you consider a hobbyist and what a pro user? I don't think a hobbyist has two daisy-chained FireWire cards, a decent collection of microphones, studio monitors, a DAW controller and a good pair of headphones.

> **dawiba said:**
> All the more reason a system (particularly one which calls itself a Studio distro) should be properly configured OOTB, surely?Yes, and they're working on it if I look at the IRC channels and the mailing lists. But it's hard for such an official project to exceed the boundaries. Stuff like adding lines to /etc/sysctl.conf, adding options to /etc/fstab, not shipping packages like apt-xapian-index, adding udev rules for hardware timers, adding/removing init.d scripts, maintaining real-time kernel packages etc. If you're running your own project you don't have to go through all the Ubuntu bureaucracy to get things done, you just do it and release a new version. So maybe in the case of Ubuntu Studio it's not about being knowledgeable actually even though I do think there's room for improvement. But then some people are good at running a project and others are better at tweaking their systems. You have to find ways to get those people to communicate and find them willing to cooperate on a joined project.

Best,

Jeremy

---

### Post by piovezan on 2011-02-05
There he comes, thanks raboof for reading :)

> **raboofje said:**
> Yeah, jack moved to /dev/shm. Are there still other applications that use /tmp for storing realtime temporary data? if not that check should be removed i guess.

Perhaps this check is not as obsolete as I first thought :( The /tmp dir is a [global temporary folder]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") used by a lot of Linux applications. I suppose almost any system or non-system application uses it to keep temporary data that is not expected to be preserved between reboots.

After reading this piece of documentation regarding [Linux tmpfs 2.6.37]("http://lxr.linux.no/#linux+v2.6.37/Documentation/filesystems/tmpfs.txt") I understand that, benefits to jack aside, pointing /tmp to a tmpfs such as /dev/shm can in most cases represent a general improvement to system performance, since temporary data can be handled faster by a primarily memory-based file system such as tmpfs (the same principle could be applied to virtualize /var or any other temporary data storage, although /tmp is probably the only 'safe' place to virtualize, due to the completely transient nature of its contents). The Linux system itself takes some advantage of tmpfs with /dev/shm and also its own internal tmpfs mount, which is invisible to users.

It would require further investigation before guaranteeing that a user-mounted tmpfs improves performance in every single case. First, the /tmp check [must include an upper bound check]("http://www.ibm.com/developerworks/library/l-fs3.html") in the tmpfs mount, otherwise the tmpfs may eat all the memory and cause a sudden kill of whichever the most memory-demanding application is. And considering the low latency requirement, I suspect that depending on a number of conditions, including RAM size and how much of it the loaded audio applications demand, sharing the available memory with one or more additional tmpfs mounts may actually lead to a performance decrease somewhere.

So I believe that asking the user to mount /tmp on a tmpfs could lead in some cases to an eventual problem, while for most cases it will be a useful check resulting in a system performance boost. This probably has been extensively discussed before; perhaps one should consider how those tmpfs optimizations are handled in one or more reference implementations of a safe low latency distro (not only  Ubuntu Studio) before deciding what to do about this check. [http://lowlatency.linuxaudio.org]("http://lowlatency.linuxaudio.org/#config") recommends it.

BTW, has the /tmp check been created for jack in the first place?

---

### Post by dawiba on 2011-02-05
[QUOTE=AUTOSTATIC]What do you consider a hobbyist and what a pro user? I don't think a hobbyist has two daisy-chained FireWire cards, a decent collection of microphones, studio monitors, a DAW controller and a good pair of headphones.
[/QUOTE]

Some might. Some might not. That wasn't the point of my question. Different people have different gear. This is largely irrelevant. What I consider a hobbyist and a professional in this context is totally irrelevant. You haven't described how their needs are different, specifically, in the context of this thread. In this context, all users need their computer to accept audio and/or midi signals, process this and then produce a finished product to their satisfaction. All in a way that they understand and are comfortable using and which makes them productive. How many mics someone has is irrelelvant to this.

For the record, I wasn't looking to start an argument.

I am not looking to run down Linux audio or any particular distro . Thus far, I haven't. It is perfectly possible to produce a single working environment that will meet the needs of all users wishing to record and process audio/midi in their computers, whether they are hobbyists or professionals. Undoubtedly, there are developers working towards this end right now, even as I type. Good for them. Falling out with me for asking questions and suggesting (indirectly) that a 'Studio' distro should be allowing all users to do that right now, won't achieve that goal.

This is now, of course, very much OT. I apologize for that. If you like, I'd be happy to carry on the discussion in a separate thread (to allow this thread to stay on topic).

In the meantime, I shall stop posting and go back to lurking instead. Who knows, I may even go back to Windows ;)

---

### Post by piovezan on 2011-02-05
I find this discussion very enlightening, and I'm sure we can benefit from continuing it, either here or in a new topic. I too have an expectation that a single distro tuning could work for both moderately and strongly demanding audio projects, and that any possible impediments to achieving this would fall mostly into "short blanket" technical choices (e.g. favoring an optimization that is too restrictive to other parts of the system).

Although I'm not familiar to open source projects I believe AutoStatic has been in the front-line long enough to have a sharper sense of how the ([limited]("http://dullass.blogspot.com/2010/08/state-of-ubuntu-studio-2010.html")) development resources are distributed, in practice, to cover the roadmap of an official distro, as well as drained to make up for other forces involved, which of course contributes to drive priorities off the path. I think it makes a lot of sense -- although hardware compatibility for the video and graphics fronts of the 'Studio' is achieved more easily, being a different flavor of an official distro (which comes from another distro) has a cost to audio support, which is to deal with stuff such as unwelcome package updates that constantly threaten system responsiveness, additional bug tracking, etc. Yet considering Ubuntu Studio's current status as a whole and also the feedback from the forums I think the team has been doing pretty well and all these expectations can be achieved in due time. The only picky people are us audio users anyway. ;)

In my personal opinion, if the technical limitations can be surpassed, the job of providing a real low latency kernel specific to audio production demands (and shared by as many audio-oriented distros as possible) should be left to a higher-level, separate group. I'm not familiar to the linux audio development community but I think such group exists.

BTW AutoStatic, how responsive to audio production you consider the Ubuntu kernel you are currently using? (I intend to compare it to the most responsive Ubuntu Studio kernel you mentioned).

---

### Post by dawiba on 2011-02-06
Piovesan - You and I are in broad agreement.

I've come back to using Ubuntu after a period of almost a year using Windows. I find that while things are better than they were, they haven't improved as much as I'd hoped.

Once I understood the changes, Jack and Firewire were easier to set up (for me). For many users, Jack is still a headache, as a cursory glance through this forum will show. Another glance will show that criticism of Jack is unacceptable for some reason.
Ardour, which is the program I like to use, doesn't do midi yet. Nor does it use multiple processor cores. These things are coming but aren't here yet.
I still can't see how to advance my midi timing so that audio from external sources, triggered by midi from QTractor, will be in time with other audio when recorded into Ardour.
I'm forced to use a2jmidi to use Qtractor's midi with Jack while using my Firewire interface. There is a need for more programs to use Jack Midi for us Firewire users, given that Jack is so pivotal to Linux audio.
As someone who tries to use Ubuntu using only software from the repositories as much as possible (Ubuntu 10.10), I've lost my realtime kernel. Some Linux users like to point to the realtime kernel as a great way to achieve low latency and as something that is unique to Linux and gives Linux users an advantage for manipulating audio and midi. If this is true, it should be practically the first inclusion in a Studio distro.
Jack and Pulseaudio still aren't the best of friends.

None of these things has stopped me using Ubuntu so far and I intend to continue using it.

Incidentally, my main reason for sticking to software from the repositories as far as possible, is so that when I'm talking to others about using Ubuntu, I can show them how it works without resorting to the terminal too much. Like it or not, lots of Windows and Mac users don't or won't use a terminal. In fact, I'm not very fond of it myself :). I've found that showing them a working, dual-booting Ubuntu system that echoes their current experiences while allowing them to fallback to their original OS, is more likely to encourage them to try Linux than showing them how to use the terminal.

Saying to them:
> Stuff like adding lines to /etc/sysctl.conf, adding options to /etc/fstab, not shipping packages like apt-xapian-index, adding udev rules for hardware timers, adding/removing init.d scripts, maintaining real-time kernel packages etc.
leaves them feeling browbeaten and unlikely to join the Linux ranks.

I happily concede to Autostatic's superior knowledge of Linux, the processes and people involved in producing a distro of any flavour. In fact, I'm happy to concede that to everyone on this forum :)

I'm still entitled to express my opinions.

Arbitrarily dividing users into pro and hobbyist beforehand is pointless. People and their needs come in all shapes and sizes. Talking down to people using jargon is just about the quickest way to lose friends and influence people.

Of course, there might well be political issues as well. As far as I can tell, at it's simplest, most of this revolves around who is setting the agenda for the various distros. Vested interests operate in similar ways, whatever the field. None of it should be used to justify perceived under-performance of a distro. Outside of those directly or closely involved, I don't suppose too many people give a damn.

Anyway, just giving my opinion as someone coming back to Ubuntu with a fresh pair of eyes :)

---

### Post by cchhrriiss121212 on 2011-02-06
Dawiba, I think everyone on this forum is already aware of the faults you mentioned, and areas for improvement within Linux audio. Unfortunately, mentioning these issues does not help them improve. 

> I find that while things are better than they were, they haven't improved as much as I'd hoped.Open source does not improve unless people like you and me actively help out, which you can do by donating your time, money or skills. Good software costs time and money, not for the user, but for the developer. If you want improvements you will have to get involved.
Ubuntu is designed with user friendliness and aims for a higher market  share, but the developers of Linux audio software may not share this  principle. In practice they just write the software they like and if  others want to join in, they are free to do so.
> 
Another glance will show that criticism of Jack is unacceptable for some reason... I'm still entitled to express my opinions.There is no need to feel so defensive about what you post, AFAIK, no-one is censoring your opinions and no-one has requested you stop posting. 

> Saying to them:
     Quote:*snip*

leaves them feeling browbeaten and unlikely to join the Linux ranks.
Talking down to people using jargon is just about the quickest way to lose friends and influence people.I don't understand the hostility here, Autostatic is possibly the friendliest poster on this forum and if you want these tips further explained I'm sure he would do so. In addition he was giving you a specific answer to a specific question you asked, and not quoting jargon just to prove he knows more than you.
> I still can't see how to advance my midi timing so that audio from  external sources, triggered by midi from QTractor, will be in time with  other audio when recorded into Ardour.Why not use Qtractor for MIDI and audio? Then timing will not be an issue.

---

### Post by piovezan on 2011-02-06
These are my remarks:

> **dawiba said:**
> Jack is still a headache, as a cursory glance through this forum will show. Another glance will show that criticism of Jack is unacceptable for some reason.

I don't think that the Jack headache is exclusive to Ubuntu. Jack is  pivotal to Linux audio as you mentioned, and support for Jack is widely  marketed by most audio-oriented distros. It is 3rd party software and dealing with 3rd party software is never as straightforward as people tend to think. Slower communication (they are different teams, managed differently), a fix for a given distro not being prioritized as it should be (as they support many distros with competing release dates, besides running their own roadmap), the issues of addressing problems in the distro itself instead of fixing them at their origin (which is always better and less prone to side effects, despite being the most difficult way). It is very different from supporting a single system. This is how I see it as a developer.

Same thing to Ardour, Jack Midi, and compatibility to Pulseaudio. They are not Ubuntu or Ubuntu Studio exclusive. I think these limitations are expected to come to any Linux distro adopting them.

> **dawiba said:**
> Saying to them (...) leaves them feeling browbeaten and unlikely to join the Linux ranks.

No matter how user-friendly Ubuntu is, it still cannot stop being Linux. It aims to be simple for everyone, yet in some cases it cannot afford not suffering from the "competing support demands" syndrome. In the cause of audio production, I understand it is a consequence of having to integrate many subsystems instead of using a monolithic solution.

> **dawiba said:**
> Of course, there might well be political issues as well. As far as I can tell, at it's simplest, most of this revolves around who is setting the agenda for the various distros. Vested interests operate in similar ways, whatever the field. None of it should be used to justify perceived under-performance of a distro.

As you can see, there are competing interests (not even political -- I would say logistical) that I believe to justify it.

---

### Post by dawiba on 2011-02-06
Hi cchhrriiss121212

> **cchhrriiss121212]I think everyone on this forum is already aware of the faults you mentioned, and areas for improvement within Linux audio. Unfortunately, mentioning these issues does not help them improve.[/QUOTE]

Unfortunately, not talking about them doesn't help either  said:**
> Open source does not improve unless people like you and me actively help out, which you can do by donating your time, money or skills.

I know this. I have done so and will continue to do so :)

[QUOTE=cchhrriiss121212]AFAIK, no-one is censoring your opinions and no-one has requested you stop posting.[/QUOTE]

I know this also. You didn't need to explain it, but thank you :)

[QUOTE=cchhrriiss121212]I don't understand the hostility here, Autostatic is possibly the friendliest poster on this forum[/QUOTE]

Perhaps you're reading my replies as over-sensitive (I'm not usually). I wasn't being hostile (honest, guv), but I ***was*** sticking to my guns. I'm not interested in denting anyone's popularity or upsetting anyone. I've already said I'm not looking to argue. I am up for a discussion though ;).

Thanks for the advice about using QTractor for audio and midi. I have tried but the timing issue still exists. It exists because midi has to leave my computer, be converted to audio which then has to return to my computer. The delay is very slight and is easily fixed by manually aligning the recorded audio. I'd still like a way to advance my midi timing though :)

Please note, lots of smileys :)

---

### Post by dawiba on 2011-02-06
[QUOTE=piovezan]Is the Jack headache exclusive to Ubuntu? I'm afraid not.[/QUOTE]

Agreed. I never claimed otherwise. I do use Ubuntu though ;)

In summary for the rest of your post, in broad terms I pretty much agree. I don't think this is Ubuntu Studio specific.

---

### Post by piovezan on 2011-02-06
Scrappy user digivolves to Smiley guy. Good! ;)

So now that you get the big picture, let's finish our OT discussion. My soundcard is aching to talk Duplex to Jack. :P If someone sees technical restrictions to make a Linux distro work for both pro and hobbyist users, I'd be glad to hear them. The challenge posed by supporting multiple OS's is well clear, however I'd like to come to a conclusion whether improving a distro to suit the different latency demands from pro and hobbyist users would be technically feasible or not. Saying "Distro X or Y doesn't do the low latency stuff well, but then again which audio distro does?" is just not enough for me. ;)

Regarding the Jack issue, I have improved my Quickscan reports; the latest is quite smooth now. I have even dropped overclocking in my machine so that the only complaint coming from the report is about kernel optimizations (no real-time capabilities and no 1000hz clock), everything else is status green now.

Yet Jack won't run in Duplex or Capture Only mode :(

```

== GUI-enabled checks ==
Checking if you are root... no - good
Checking filesystem 'noatime' parameter... 2.6.35 kernel - good
(relatime is default since 2.6.30)
Checking CPU Governors... CPU 0: 'performance' CPU 1: 'performance'  - good
Checking swappiness... 10 - good
Checking for resource-intensive background processes... none found - good
Checking checking sysctl inotify max_user_watches... >= 524288 - good
Checking access to the high precision event timer... readable - good
Checking access to the real-time clock... readable - good
Checking whether you're in the 'audio' group... yes - good
Checking for multiple 'audio' groups... no - good
yes - good.
Checking the ability to prioritize processes with chrt... yes - good
== Other checks ==
Finding current kernel config... found /boot/config-2.6.35-25-generic
Checking for Ingo Molnar's Real-Time Preemption... not found.
** Kernel without real-time capabilities found
   For more information, see http://wiki.linuxmusicians.com/doku.php?id=system_configuration#installing_a_real-time_kernel
Checking for high-resolution timers... found - good.
Checking for 1000hz clock... not found.
** Try setting your clock to 1000hz
   For more information, see:
   * http://wiki.linuxmusicians.com/doku.php?id=system_configuration#installing_a_real-time_kernel
   * http://www.rosegardenmusic.com/wiki/frequently_asked_questions#what_does_system_timer_resolution_is_too_low_mean
Checking for High Resolution Timers... found - good.
Checking filesystem types... ok.
not found.
** Warning: no tmpfs partition mounted on /tmp
   For more information, see:
   - http://wiki.linuxmusicians.com/doku.php?id=system_configuration#tmpfs
   - http://lowlatency.linuxaudio.org

```

---

### Post by Pablo_F on 2011-02-06
Hi, 

What audio card are you using? Is it an onboard? What are the terminal outputs of *arecord -l* and *aplay -l*?

Have you tried with jackd1 instead of jackd2? (sudo apt-get install jackd1)

I second Autostatic that you should give tango studio a try. It is a wonderful distro, based on and fully compatible with ubuntu/ubuntustudio 10.04, but better suited for audio work, imho.

EDIT: The terminal is fine. It is not intuitive but it gives you flexibility and it is faster for some purposes. For example (a biased example because vlc is a three-letter word and it is in the repos :) ) it is faster to type sudo apt-get install vlc, than open the sotware center, search vlc and click to install it. And both methods are way faster than most windows users would do: open a web browser and so on. 

Another example, for helping through the forums, the info in plain text is more accurate and extensive than what you can see in screenshots, and it is a matter of copy-paste text. 

Cheers, Pablo

---

### Post by dawiba on 2011-02-06
The terminal is fine. I prefer not to use it. Speed is not an issue for users used to the terminal. It takes me ages to do anything in the terminal :) 

I'm not bothered how quickly I download or install a program. I concede that for some, this will be important. I try to encourage users to Linux by showing them just how much they can actually do without opening a terminal window. They seem to like that ;)

---

### Post by piovezan on 2011-02-06
> **Pablo_F said:**
> What audio card are you using? Is it an onboard? What are the terminal outputs of *arecord -l* and *aplay -l*?

Yes, it is an onboard card. 'HDA Intel' according to the terminal. The [mobo spec]("http://www.asus.com/product.aspx?P_ID=6nnVb6RBxd7PhGmt") mentions an ICH7 chipset, which is [supported]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel") by ALSA/Jack through the snd-hda-intel driver, despite also mentioning an 8-channel VIA VT1708B HDA Codec (which may be trouble, but it seems to be already [supported]("http://www.murga-linux.com/puppy/viewtopic.php?p=322567") as well).

```

piovezan@ubuntu:~$ arecord -l
**** Lista de Dispositivos CAPTURE Hardware ****
placa 0: Intel [HDA Intel], dispositivo 0: VT1708B Analog [VT1708B Analog]
  Dispositivo secundário: 2/2
  Dispositivo secundário #0: subdevice #0
  Dispositivo secundário #1: subdevice #1
piovezan@ubuntu:~$ aplay -l
**** Lista de Dispositivos PLAYBACK Hardware ****
placa 0: Intel [HDA Intel], dispositivo 0: VT1708B Analog [VT1708B Analog]
  Dispositivo secundário: 2/2
  Dispositivo secundário #0: subdevice #0
  Dispositivo secundário #1: subdevice #1
placa 0: Intel [HDA Intel], dispositivo 1: VT1708B Digital [VT1708B Digital]
  Dispositivo secundário: 1/1
  Dispositivo secundário #0: subdevice #0

```> **Pablo_F said:**
>  Have you tried with jackd1 instead of jackd2? (sudo apt-get install jackd1) 

Yes [I have]("http://art.ubuntuforums.org/showpost.php?p=10426740&postcount=10"). And just tried once more via terminal. No issues during installation apparently, yet same results as before.

> **Pablo_F said:**
>  I second Autostatic that you should give tango studio a try. It is a wonderful distro, based on and fully compatible with ubuntu/ubuntustudio 10.04, but better suited for audio work, imho. 

Yes it's plan B. :) I'll be sure to try it and I really appreciate the recommendation.

Thanks!

---

### Post by AutoStatic on 2011-02-07
> **dawiba said:**
> Some might. Some might not. That wasn't the point of my question. Different people have different gear. This is largely irrelevant. What I consider a hobbyist and a professional in this context is totally irrelevant. You haven't described how their needs are different, specifically, in the context of this thread. In this context, all users need their computer to accept audio and/or midi signals, process this and then produce a finished product to their satisfaction. All in a way that they understand and are comfortable using and which makes them productive. How many mics someone has is irrelelvant to this.Hello dawiba. True. I should have phrased it differently. What I wanted to say is that for me the difference between a hobbyist and a pro user is that a pro user is willing to invest time, money and effort into getting everything set up so he can create the things he wants. Gear can be one of those investments. But it could also relate to investing time and energy to get to know the platform you're using and the software that is available for that platform.

> **dawiba said:**
> For the record, I wasn't looking to start an argument.Me neither. It was not my intention to raise an argument. I do understand though my previous post could be interpreted as such so therefor I apologize.

> **dawiba said:**
> It is perfectly possible to produce a single working environment that will meet the needs of all users wishing to record and process audio/midi in their computers, whether they are hobbyists or professionals.This is imho not possible. A hobbyist probably prefers a system that works right away and that might clash with the demands from pro users.

> **dawiba said:**
> Undoubtedly, there are developers working towards this end right now, even as I type. Good for them.Unfortunately they're not. Ubuntu Studio has no or very few developers, they rely on the developers from the [MOTU]("https://wiki.kubuntu.org/MOTU") team. And they're focusing on things that I find of lesser importance for a pro user, like getting NetworkManager to behave well in a real-time low latency environment. Afaik there are very few Linux audio pro users that use this tool. They either disable it right away and use something else or use a completely different Desktop Environment that doesn't use NetworkManager as a WiFi networks manager.

Best,

Jeremy

---

### Post by dawiba on 2011-02-07
Autostatic - First of all thanks for taking the time to reply.

We appear to have got off to a bad start here :oops:. I would also like to apologise if anything I have said is taken out of context. It was not my intention to upset anyone.

Piovezan - sorry for hijacking the thread.

---

### Post by AutoStatic on 2011-02-07
Hello dawiba, all well :)

piovezan: [http://ubuntuforums.org/showthread.php?t=1336078](http://ubuntuforums.org/showthread.php?t=1336078)
And what are your current JACK settings?

Best,

Jeremy

---

### Post by piovezan on 2011-02-08
Hi AutoStatic,

I'm about to try out Tango Studio, but let's give this a last try.

The link suggests to make sure that the card, device, and input/output channels are correctly set. The user seemed to have wrong card and channel offset values.

So let's check all these values. The aplay -l and arecord -l outputs can be found in a previous post (please let me know if you need it translated). I have a single soundcard, with one device (device 0) for analog capture and two for playback (device 0 for analog and device 1 for digital, which I'm not interested at). It seems that the same device is listed for both capture and playback, but I think this is not an issue based on other topics providing those command outputs. Or is it?

Anyway I tried to set these values on Jackd1 manually, although I believe it to be unnecessary since Jack control seems to find them correctly when they're set to default (i.e. autodetected). Nothing changed. Tried various configurations, changing card to hw:0,0 instead of hw:0, changing channel offsets, etc. to no avail. I have set them back to "(default)" now. This is the messages log so you can see my Jack configuration:

```

16:11:41.807 Startup script...
16:11:41.807 artsshell -q terminate
sh: artsshell: not found
16:11:42.210 Startup script terminated with exit status=32512.
16:11:42.210 JACK is starting...
16:11:42.210 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p256 -n2
16:11:42.213 JACK was started with PID=4942.
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    1538451
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|256|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 256 frames (5.8 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
16:11:44.417 Server configuration saved to "/home/piovezan/.jackdrc".
16:11:44.418 Statistics reset.
16:11:44.419 Client activated.
16:11:44.420 JACK connection change.
16:11:44.423 JACK connection graph change.
16:11:44.431 XRUN callback (1).
16:11:44.715 Client deactivated.
16:11:44.716 JACK is stopping...
jack main caught signal 15
16:11:44.855 JACK was stopped successfully.
16:11:44.856 Post-shutdown script...
16:11:44.856 killall jackd
jackd: processo nÃ£o achado
16:11:45.263 Post-shutdown script terminated with exit status=256.

```

---

### Post by AutoStatic on 2011-02-08
> **piovezan said:**
> The link suggests to make sure that the card, device, and input/output channels are correctly set. The user seemed to have wrong card and channel offset values.Yeah I now see that too.

> **piovezan said:**
> It seems that the same device is listed for both capture and playback, but I think this is not an issue based on other topics providing those command outputs. Or is it?No.

> **piovezan said:**
> Anyway I tried to set these values on Jackd1 manually, although I believe it to be unnecessary since Jack control seems to find them correctly when they're set to default (i.e. autodetected).You're right, it shouldn't make a difference.

You could try installing the **linux-backports-modules-alsa-maverick-generic** package. On my notebook with 10.04 I always have to do that otherwise my onboard card won't play nicely with JACK.

Best,

Jeremy

---

### Post by AutoStatic on 2011-02-08
> **piovezan said:**
> Perhaps this check is not as obsolete as I first thought :( The /tmp dir is a [global temporary folder]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") used by a lot of Linux applications. I suppose almost any system or non-system application uses it to keep temporary data that is not expected to be preserved between reboots.

After reading this piece of documentation regarding [Linux tmpfs 2.6.37]("http://lxr.linux.no/#linux+v2.6.37/Documentation/filesystems/tmpfs.txt") I understand that, benefits to jack aside, pointing /tmp to a tmpfs such as /dev/shm can in most cases represent a general improvement to system performance, since temporary data can be handled faster by a primarily memory-based file system such as tmpfs (the same principle could be applied to virtualize /var or any other temporary data storage, although /tmp is probably the only 'safe' place to virtualize, due to the completely transient nature of its contents). The Linux system itself takes some advantage of tmpfs with /dev/shm and also its own internal tmpfs mount, which is invisible to users.

It would require further investigation before guaranteeing that a user-mounted tmpfs improves performance in every single case. First, the /tmp check [must include an upper bound check]("http://www.ibm.com/developerworks/library/l-fs3.html") in the tmpfs mount, otherwise the tmpfs may eat all the memory and cause a sudden kill of whichever the most memory-demanding application is. And considering the low latency requirement, I suspect that depending on a number of conditions, including RAM size and how much of it the loaded audio applications demand, sharing the available memory with one or more additional tmpfs mounts may actually lead to a performance decrease somewhere.

So I believe that asking the user to mount /tmp on a tmpfs could lead in some cases to an eventual problem, while for most cases it will be a useful check resulting in a system performance boost. This probably has been extensively discussed before; perhaps one should consider how those tmpfs optimizations are handled in one or more reference implementations of a safe low latency distro (not only  Ubuntu Studio) before deciding what to do about this check. [http://lowlatency.linuxaudio.org]("http://lowlatency.linuxaudio.org/#config") recommends it.

BTW, has the /tmp check been created for jack in the first place?

It definitely needs some testing. And it is indeed not as obsolete as I thought before, any application using /tmp can save temporary data faster if /tmp is mounted on a temporary filesystem residing in memory. I never really thought about this that well so thanks for digging this up! tmpfs relies (heavily?) with swap so doesn't this conflict a bit with lowering swappiness?

Best,

Jeremy

---

### Post by piovezan on 2011-02-08
> **AutoStatic said:**
> tmpfs relies (heavily?) with swap so doesn't this conflict a bit with lowering swappiness?

Coming to a reasonable conclusion about this requires a few things to be confirmed first. I'll do some research. Back to the OS class :P And as you said, testing will be definitely necessary.

I've seen debates about whether swapping is necessary or not. Checking this will also help to understand the Linux VM (virtual memory) & paging mechanism and make sure that a low swappiness value is really an improvement (I'm afraid that the [remark]("http://linuxmusicians.com/viewtopic.php?f=27&t=452&start=30#p8916") about memory-intensive operations from the user that originally suggested the swappiness reduction might be the most common case and thus a bad scenario for the low swappiness value).

Telling how much tmpfs relies on swap is not easy. The decision to swap a given memory page to disk depends on how often that page is accessed. Parts of the tmpfs may be frequently accessed (and thus bad candidates to swapping) and parts may be accessed less often. It depends on who is using the /tmp directory and for what.

---

### Post by AutoStatic on 2011-02-09
> **piovezan said:**
> I've seen debates about whether swapping is necessary or not.It sure isn't desirable in a real-time low latency environment

> **piovezan said:**
> Checking this will also help to understand the Linux VM (virtual memory) & paging mechanism and make sure that a low swappiness value is really an improvement (I'm afraid that the [remark]("http://linuxmusicians.com/viewtopic.php?f=27&t=452&start=30#p8916") about memory-intensive operations from the user that originally suggested the swappiness reduction might be the most common case and thus a bad scenario for the low swappiness value).If you got a lot of RAM I don't think you will run into issues quickly. But then you do have to limit tmpfs in what it can address in memory space.

> **piovezan said:**
> Telling how much tmpfs relies on swap is not easy. The decision to swap a given memory page to disk depends on how often that page is accessed. Parts of the tmpfs may be frequently accessed (and thus bad candidates to swapping) and parts may be accessed less often. It depends on who is using the /tmp directory and for what.With lesser RAM you will have to find the right balance regarding swappiness.

I've started a thread about this on LAU: [http://lists.linuxaudio.org/pipermail/linux-audio-user/2011-February/076366.html](http://lists.linuxaudio.org/pipermail/linux-audio-user/2011-February/076366.html)

Best,

Jeremy

---

### Post by piovezan on 2011-02-09
> **AutoStatic said:**
> It sure isn't desirable in a real-time low latency environment

That seems to be right at first thought, but still I'd like to make sure that swapping doesn't bring any benefits to memory accessing by reducing VM fragmentation. In a similar way to disk fragmentation, it is noticeable when the disk space is low, but performance starts to degrade before that.

> **AutoStatic said:**
>  I've started a thread about this on LAU: [http://lists.linuxaudio.org/pipermail/linux-audio-user/2011-February/076366.html](http://lists.linuxaudio.org/pipermail/linux-audio-user/2011-February/076366.html)

I'm following it. Despite the design of an audio application, I think memory-disk i/o to be a key point. Will post about it soon.
[]("http://www.alsa-project.org/db/?f=5eee15c0c4e09ffbaa083bcc9135c4d6034eabd1")

---

### Post by piovezan on 2011-02-10
Whoa, Tango Studio runs Jackd1 with no xruns right out of the box! What a great recommendation :D

These are the alsa-info reports for [Ubuntu Studio 10.10]("http://www.alsa-project.org/db/?f=5eee15c0c4e09ffbaa083bcc9135c4d6034eabd1") and [Tango Studio 1.1]("http://www.alsa-project.org/db/?f=cc9894c595f194832dadb52c30a6595730efa31d") (based on Ubuntu Lucid 10.04.1) just in case someone wants to diff them and try to figure out what the issue possibly was.

AutoStatic, I had installed the package you suggested, but it seemed to depend on a kernel update to provide results, and I was too hyped about TS so I couldn't help going and reinstalling the whole thing :P

---

### Post by IceRoadTrucker on 2011-02-10
Hello.  I agree that my Ubuntu Studio partition runs like @$$ when I enable networkmanager. However, my Puredyne partition (with XFCE, not the usual interface) had it installed by default (unlike Ubuntu Studio) and can networkmanager/Nvidia/realtime really well on a computer from about 2004.

---

### Post by AutoStatic on 2011-02-11
> **piovezan said:**
> Whoa, Tango Studio runs Jackd1 with no xruns right out of the box! What a great recommendation :DCool! Another proof that TS is at present one of the best alternatives (together with AV Linux) for making music with Linux. Based on a LTS release, very active repositories, project owner who knows what he's doing and they even got a little forum recently. French only though.

Best,

Jeremy

---

### Post by Cdn~innu on 2011-02-11
I found all sorts of strange goings-on using pulse audio. Once pulse was disabled and run with alsa only
JACK worked fine in RT mode. select qjackctrl, and then click start button if all is OK window should run updating with minimum of messages, and RT should be evident in the jack window.

Check Rivendell Audio Automation Wiki for details on disabling pulse audio. If you go too far by just deleting installed components it will also kill access to X server access at login.

---

### Post by Pablo_F on 2011-02-11
I have never tried TS but according to the comments I hear and read, it sounds like "Linux audio for human beings" :cool:

---

### Post by piovezan on 2011-02-13
> **piovezan said:**
> That seems to be right at first thought, but still I'd like to make sure that swapping doesn't bring any benefits to memory accessing by reducing VM fragmentation. In a similar way to disk fragmentation, it is noticeable when the disk space is low, but performance starts to degrade before that.

Well I haven't found a good reason to think that VM fragmentation plays a significant role in memory management. It is not even an issue in page replacement algorithms. The frequency of page swapping plays a much bigger role in degrading system responsiveness, although this only happens when the current processes are too memory demanding. On the other side modern memory management approaches always consider swapping a fundamental part exactly for the "graceful degradation" it provides (this is mentioned for example [here]("http://kerneltrap.org/node/3202")).


> **piovezan said:**
> I'm following it. Despite the design of an audio application, I think memory-disk i/o to be a key point. Will post about it soon.


What I was trying to say is, I was reluctant to believe that a well designed audio application behaves as mentioned in the LAU thread, so I thought memory-disk i/o would always happen (and also the design I imagined would make the same data occupying the memory twice, both as process data and tmpfs data, which would reduce memory availability). But now I think that remark about application design to be correct.

---

### Post by danielsun23 on 2011-06-30
Sorry to revive this chain, but I am also having problems starting Jack in qjackctl 

I ran the ALSA scripts which gave me the following

[http://www.alsa-project.org/db/?f=bf51e83db7123e27fe0e34bff0071d3c667e4691](http://www.alsa-project.org/db/?f=bf51e83db7123e27fe0e34bff0071d3c667e4691)

Trying to start a jack server with qjackctl gives me the following

```
19:23:14.322 Patchbay deactivated.
19:23:14.338 Statistics reset.
19:23:14.360 ALSA connection change.
Cannot open qjackctl client
19:23:19.421 ALSA connection graph change.
19:23:27.196 JACK is starting...
19:23:27.197 /usr/bin/jackd -v -t5000 -u -dalsa -dhw:0 -r48000 -p2048 -n2 -P
JackSocketClientChannel read fail
Cannot open qjackctl client
19:23:27.230 JACK was started with PID=21762.
19:23:32.236 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.
no message buffer overruns
no message buffer overruns
`default' server already active
Failed to start server
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Cannot read socket fd = 25 err = Interrupted system call
JackSocketClientChannel read fail
Cannot open qjackctl client
19:23:32.492 JACK was stopped with exit status=255.
19:23:32.493 Post-shutdown script...
19:23:32.493 killall jackd
19:23:32.916 Post-shutdown script terminated successfully.
```

I am new to ubuntu, and my friend recommended ubuntu studio (I am running 11.04), and I would really like some help using some of the cool music software. 

Trying to run jackd -d alsa -d hw:0 in terminal gives me the following.
```

jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
control device hw:0
control device hw:0
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xda080000 irq 45
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
Cannot initialize driver
JackServer::Open() failed with -1
Failed to start server

```

---

### Post by danielsun23 on 2011-06-30
After a restart, I try running jack -d alsa -d hw:0 and get the following

```
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
control device hw:0
control device hw:0
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xda080000 irq 45
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
Cannot initialize driver
JackServer::Open() failed with -1
Failed to start server
daniel@owner-laptop:~$ alsa
Usage: /sbin/alsa {unload|reload|force-unload|force-reload|suspend|resume}
daniel@owner-laptop:~$ /sbin/alsa force-reload
Terminating processes: 1623 18541 21392 21392 21392 21392 (with SIGKILL:) 21392 (failed: processes still using sound devices: 30265(pulseaudio)).
/sbin/alsa: Warning: Processes using sound devices: 30265(pulseaudio). 
mkdir: cannot create directory `/var/run/alsa': Permission denied
/sbin/alsa: Warning: Failed to create /var/run/alsa/. 
/sbin/alsa: Warning: Not keeping list of removed modules because /var/run/alsa is absent.
It will not be possible automatically to reload these modules. 
Unloading ALSA sound driver modules:/sbin/alsa: 219: cannot create /var/run/alsa/modules-removed: Directory nonexistent
 snd-seq-dummy snd-hda-codec-si3054 snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
mkdir: cannot create directory `/var/run/alsa': Permission denied
Loading ALSA sound driver modules: (none to reload).
[2]+  Killed                  qjackctl
daniel@owner-laptop:~$ jackd -d alsa -d hw:0
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
control device hw:0
control device hw:0
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xda080000 irq 45
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
Driver is not running
Cannot create new client
JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
Driver is not running
Cannot create new client


```

Any help is extremely appreciated.

---

### Post by Pablo_F on 2011-07-01
When you see this message:

> the playback device "hw:0" is already in use. Please stop the application using it and run JACK again

or this one:

> `default' server already active

you need to stop the application that is using the alsa device.

Run in a terminal:
[B]
lsof | grep pcm[/B]

which will give the process that is using /dev/snd/pcmC0D0p 
(Card 0, Device 0, playback) 

Kill it:

**kill PID**

where PID is the process ID number (second column)

Cheers, Pablo

---

### Post by danielsun23 on 2011-07-01
Thank you for that. I realized jack is actually working, even though qjackctl tells me it cannot create server. 

```
08:03:36.601 JACK is starting...
08:03:36.602 /usr/bin/jackd -v -t5000 -u -dalsa -dhw:0 -r48000 -p2048 -n2 -P
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
08:03:36.637 JACK was started with PID=8598.
08:03:36.693 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
no message buffer overruns
no message buffer overruns
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
Jack: Create non RT thread
Jack: ThreadHandler: start
Jack: playback device hw:0
Jack: capture device hw:0
Jack: apparent rate = 48000
Jack: frames per period = 2048
Jack: JackDriver::Open capture_driver_name = hw:0
Jack: JackDriver::Open playback_driver_name = hw:0
Jack: JackEngine::ClientInternalOpen: name = system
Jack: JackEngine::AllocateRefNum ref = 0
Jack: JackPosixSemaphore::Allocate name = jack_sem.1001_default_system val = 0
Jack: JackEngine::NotifyAddClient: name = system
Jack: JackGraphManager::SetBufferSize size = 2048
Jack: JackConnectionManager::DirectConnect first: ref1 = 0 ref2 = 0
Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
Jack: JackDriver::SetupDriverSync driver sem in flush mode
control device hw:0
control device hw:0
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|-|2048|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xda080000 irq 45
configuring for 48000Hz, period = 2048 frames (42.7 ms), buffer = 2 periods
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
Jack: JackSocketServerChannel::Open
Jack: Bind: addr.sun_path /dev/shm/jack_default_1001_0
Jack: JackSocketServerChannel::BuildPoolTable size = 1
Jack: JackEngine::Open
Jack: Connect: addr.sun_path /dev/shm/jack_default_1001_0
Jack: JackEngine::ClientInternalOpen: name = freewheel
Jack: JackEngine::AllocateRefNum ref = 1
Jack: JackPosixSemaphore::Allocate name = jack_sem.1001_default_freewheel val = 0
Jack: JackEngine::NotifyAddClient: name = freewheel
Jack: JackConnectionManager::DirectConnect first: ref1 = 1 ref2 = 1
Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 1 ref2 = 1
Jack: JackDriver::SetupDriverSync driver sem in flush mode
Jack: JackGraphManager::SetBufferSize size = 2048
Jack: JackAudioDriver::Attach fBufferSize 2048 fSampleRate 48000
Jack: JackGraphManager::AllocatePortAux port_index = 1 name = system:playback_1 type = 32 bit float mono audio
Jack: JackConnectionManager::AddInputPort ref = 0 port = 1
Jack: JackAudioDriver::Attach fPlaybackPortList[i] 1 
Jack: JackGraphManager::AllocatePortAux port_index = 2 name = system:playback_2 type = 32 bit float mono audio
Jack: JackConnectionManager::AddInputPort ref = 0 port = 2
Jack: JackAudioDriver::Attach fPlaybackPortList[i] 2 
Jack: Clock source : system clock via clock_gettime
Jack: JackServer::Start
Jack: JackThreadedDriver::Start
Jack: Create non RT thread
Jack: ThreadHandler: start
Jack: JackThreadedDriver::Init IsRealTime
Jack: Create non RT thread
Jack: ThreadHandler: start
Jack: JackSocketServerChannel::ClientCreate socket
Jack: JackSocketServerChannel::BuildPoolTable size = 2
Jack: fSocketTable i = 1 fd = 8
Jack: fPollTable i = 1 fd = 8
Jack: JackRequest::Notification
Jack: JackEngine::NotifyClient: no callback for event = 4
Jack: JackEngine::NotifyClient: no callback for event = 4
```

I don't know if it's important that it's causing an error, because I still have a working jack.

---

### Post by Pablo_F on 2011-07-01
Well, yes, some messages can be a bit confusing sometimes. Anyway... you have a working jack :)

---

### Post by danielsun23 on 2011-07-01
Thank you so much!

---

### Post by Flaggmann on 2011-07-02
after you get the jack window open and the message pops up unable to connect, click on setup and find misc tab, put a check mark in launch jack on application startup. Then close all jack windows and restart using qjackctl.

to autostart on login, add qjackctl to the startup folder/list. Access that from the System -->Preferences --> Startup  menu.

Realtime operation will give great response but will take priority on memory resources...

---

### Post by TSTR on 2012-01-23
Hey, guys I'm new here any direction would be appreciated...I just want to add that if I ever cause a crash while using JACK. What i would do is first remember what programs were running with Jack at the time of the crash. Without starting JACK start those programs.(remember might be 3 programs but I am just using AUDACITY as an example) . For example, If JACK crashed while using AUDACITY...Then run AUDACITY without JACK. In the AUDACITY menu got to EDIT >>> PREFERENCES >>> DEVICES There make sure that The host is not set to JACK. Then close AUDACITY. The proper shutdown of the programs will fix the errors. Jack starts after this. basically just make sure whatever programs crashed with JACK are one at a time started with their default host (obviously not JACK). Problem fixed. This is of course if you had a working Jack configuration that stopped working after a crash. If you try this before you start editing stuff I think It would save some not so buggy bug posts. I'm a NOOB who pays attention to what my computer is saying LOL...


On a UBUNTU9.10 usb install upgraded to the 10.04LTS upgraded to UBUNTUSTUDIO on a Motion Computing LE1600 dual screen RT KERNEL...So far so good...

---

### Post by TSTR on 2012-02-03
**Re: Jack won't start** 			
 			 			 		   		 		 		Good news!  Jackd started with Audio set to "Playback Only". No idea why, though.  Perhaps it is worthwhile to get this clarified before the topic is  closed.

do you get sound without jack running??? also have you dabbled with the alsamixer in terminal...there are more settings for you inputs outputs and speakers etc...

---

### Post by TSTR on 2012-02-03
yea, danielsun23 I was going to mention to check and see if Jack is running. I have the same bug...Basically error message pops up and  says unable to start JACK but it is actually running. The error message doesn't pop up after you save your alsamixer settings, Unfortunately after a reboot the JACK error message pops up again. I figured I'd mention it so someone who is linux savvy may find out how to get that error message from popping up at all considering Jack is functioning (how to save alsamixer settings>>> [http://ubuntuforums.org/showthread.php?t=1652691](http://ubuntuforums.org/showthread.php?t=1652691) )Since I'm new can anyone advise me on whether it is worth posting this as a bug. I've never posted one before. Thank You...

---

### Post by mjhouska on 2012-02-05
this thread should be stickied.

---

