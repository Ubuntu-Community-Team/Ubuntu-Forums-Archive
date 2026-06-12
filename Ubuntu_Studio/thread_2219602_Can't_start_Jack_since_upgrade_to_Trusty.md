---
title: "Can't start Jack since upgrade to Trusty"
date: 2014-04-24
forum: Ubuntu Studio
---

### Post by halfbeing on 2014-04-24
I wonder if someone could help me. Since upgrading to Trusty a couple of days ago I can no longer start jack. I've tried a few times and each time I get different error messages. The qjackctl log below covers a few attempts and I'm a bit confused by it. One thing to know is that process 10823, which is mentioned at one point, turned out to be pulseaudio.

Can anyone tell me how I can get jack working again and playing nicely with pulseaudio?

Thanks.

EDIT: Sorry, I was tired and forget to include the output of qjackctl. Here it is:

[COLOR=#999999]23:28:30.043 Patchbay deactivated.[/COLOR]
[COLOR=#999999]23:28:30.226 Statistics reset.[/COLOR]
[COLOR=#cccc99]23:28:30.765 ALSA connection change.[/COLOR]
[COLOR=#999999]23:28:31.522 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
[COLOR=#66cc99]23:28:31.559 ALSA connection graph change.[/COLOR]
[COLOR=#ff0000]23:28:36.271 D-BUS: JACK server could not be started. Sorry[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Thu Apr 24 23:28:35 2014: Starting jack server...
Thu Apr 24 23:28:35 2014: JACK server starting in realtime mode with priority 10
Thu Apr 24 23:28:35 2014: Acquired audio card Audio2
Thu Apr 24 23:28:35 2014: creating alsa driver ... hw:USB,0|hw:USB,0|256|2|48000|0|0|nomon|swmeter|-|32bit
Thu Apr 24 23:28:36 2014: ERROR: 
ATTENTION: The playback device "hw:USB,0" is already in use. The following applications  are using your soundcard(s) so you should  check them and stop them as necessary before  trying to start JACK again:
pulseaudio (process ID 10823)
Thu Apr 24 23:28:36 2014: ERROR: Cannot initialize driver
Thu Apr 24 23:28:36 2014: ERROR: JackServer::Open failed with -1
Thu Apr 24 23:28:36 2014: ERROR: Failed to open server
Thu Apr 24 23:28:36 2014: Saving settings to "/home/robert/.config/jack/conf.xml" ...
[COLOR=#ff0000]23:28:38.352 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
[COLOR=#ff0000]23:29:27.357 D-BUS: JACK server could not be started. Sorry[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Thu Apr 24 23:29:27 2014: Starting jack server...
Thu Apr 24 23:29:27 2014: JACK server starting in realtime mode with priority 10
Thu Apr 24 23:29:27 2014: ERROR: cannot register object path "/org/freedesktop/ReserveDevice1/Audio2": A handler is already registered for /org/freedesktop/ReserveDevice1/Audio2
Thu Apr 24 23:29:27 2014: ERROR: Failed to acquire device name : Audio2 error : A handler is already registered for /org/freedesktop/ReserveDevice1/Audio2
Thu Apr 24 23:29:27 2014: ERROR: Audio device hw:USB,0 cannot be acquired...
Thu Apr 24 23:29:27 2014: ERROR: Cannot initialize driver
Thu Apr 24 23:29:27 2014: ERROR: JackServer::Open failed with -1
Thu Apr 24 23:29:27 2014: ERROR: Failed to open server
[COLOR=#ff0000]23:29:29.426 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Thu Apr 24 23:29:28 2014: Saving settings to "/home/robert/.config/jack/conf.xml" ...
[COLOR=#ff0000]23:33:28.958 D-BUS: JACK server could not be started. Sorry[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Thu Apr 24 23:33:28 2014: Starting jack server...
Thu Apr 24 23:33:28 2014: JACK server starting in realtime mode with priority 10
Thu Apr 24 23:33:28 2014: ERROR: cannot register object path "/org/freedesktop/ReserveDevice1/Audio2": A handler is already registered for /org/freedesktop/ReserveDevice1/Audio2
Thu Apr 24 23:33:28 2014: ERROR: Failed to acquire device name : Audio2 error : A handler is already registered for /org/freedesktop/ReserveDevice1/Audio2
Thu Apr 24 23:33:28 2014: ERROR: Audio device hw:USB,0 cannot be acquired...
Thu Apr 24 23:33:28 2014: ERROR: Cannot initialize driver
Thu Apr 24 23:33:28 2014: ERROR: JackServer::Open failed with -1
Thu Apr 24 23:33:28 2014: ERROR: Failed to open server
Thu Apr 24 23:33:29 2014: Saving settings to "/home/robert/.config/jack/conf.xml" ...
[COLOR=#ff0000]23:33:30.994 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
[COLOR=#ff0000]00:23:13.887 D-BUS: JACK server could not be started. Sorry[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Fri Apr 25 00:23:13 2014: Starting jack server...
Fri Apr 25 00:23:13 2014: JACK server starting in realtime mode with priority 10
Fri Apr 25 00:23:13 2014: ERROR: cannot register object path "/org/freedesktop/ReserveDevice1/Audio2": A handler is already registered for /org/freedesktop/ReserveDevice1/Audio2
Fri Apr 25 00:23:13 2014: ERROR: Failed to acquire device name : Audio2 error : A handler is already registered for /org/freedesktop/ReserveDevice1/Audio2
Fri Apr 25 00:23:13 2014: ERROR: Audio device hw:USB,0 cannot be acquired...
Fri Apr 25 00:23:13 2014: ERROR: Cannot initialize driver
Fri Apr 25 00:23:13 2014: ERROR: JackServer::Open failed with -1
Fri Apr 25 00:23:13 2014: ERROR: Failed to open server
Fri Apr 25 00:23:14 2014: Saving settings to "/home/robert/.config/jack/conf.xml" ...
[COLOR=#ff0000]00:23:16.146 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started

---

### Post by SonicPrince on 2014-04-28
Hi,

> ATTENTION: The playback device "hw:USB,0" is already in use. The  following applications  are using your soundcard(s) so you should  check  them and stop them as necessary before  trying to start JACK again: pulseaudio (process ID 10823)

Have a look at [https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro](https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro) for whatever reason the same thing happened with me after installing Trusty Beta 1.

Cheers
(edited for grammer..)

---

### Post by halfbeing on 2014-04-28
> **SonicPrince said:**
> Hi,



Have a look at [https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro](https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro) for whatever reason the same thing happened with me after installing Trusty Beta 1.

Cheers
(edited for grammer..)

Thanks for taking the trouble to reply. In the end the problem resolved itself with a reboot, but unfortunately I forgot to update this thread afterwards.

---

