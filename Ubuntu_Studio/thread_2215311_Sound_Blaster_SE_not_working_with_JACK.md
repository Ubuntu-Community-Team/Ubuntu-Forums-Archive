---
title: "Sound Blaster SE not working with JACK"
date: 2014-04-06
forum: Ubuntu Studio
---

### Post by tmixshinodarap on 2014-04-06
Hi everyone! I'm tryin to work with FL Studio 11.1 in Ubuntu, so i installed Ubuntu Studio (Inside normal-ubuntu) and everything worked... with the internal soundcard. When i try to switch to my SoundBlaster Audigy SE, JACK refuses to work and throws me this:

```

[COLOR=#FF0000]05:40:56.217 D-BUS: El servidor JACK no puede iniciarse. Disculpa (JACK server can't start, sorry)[/COLOR]Cannot connect to server socket err = No existe el archivo o el directorio (No such file or directory)
Cannot connect to server request channel
jack server is not running or cannot be started
Sun Apr  6 05:40:56 2014: Starting jack server...
Sun Apr  6 05:40:56 2014: JACK server starting in realtime mode with priority 10
Sun Apr  6 05:40:56 2014: self-connect-mode is "Don't restrict self connect requests"
Sun Apr  6 05:40:56 2014: [1m[31mERROR: cannot register object path "/org/freedesktop/ReserveDevice1/Audio1": A handler is already registered for /org/freedesktop/ReserveDevice1/Audio1[0m
Sun Apr  6 05:40:56 2014: [1m[31mERROR: Failed to acquire device name : Audio1 error : A handler is already registered for /org/freedesktop/ReserveDevice1/Audio1[0m
Sun Apr  6 05:40:56 2014: [1m[31mERROR: Audio device hw:1,0 cannot be acquired...[0m
Sun Apr  6 05:40:56 2014: [1m[31mERROR: Cannot initialize driver[0m
Sun Apr  6 05:40:56 2014: [1m[31mERROR: JackServer::Open failed with -1[0m
Sun Apr  6 05:40:56 2014: [1m[31mERROR: Failed to open server[0m
Sun Apr  6 05:40:58 2014: Saving settings to "/home/hybrdangl/.config/jack/conf.xml" ...
(qjackctl.real:2449): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
(qjackctl.real:2449): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
[COLOR=#ff0000]05:44:00.914 No puede conectarse al servidor JACK como cliente. - La operación global falló. - No puede conectarse al servidor. Por favor revise la ventana de mensajes para mas información.[/COLOR]
Cannot connect to server socket err = No existe el archivo o el directorio (No such file or directory)
Cannot connect to server request channel
jack server is not running or cannot be started
```

But with the internal sound card (Realtek) it works flawlessly, so what it can be?

Sorry for my bad english and thanks in advance (:

---

### Post by jejeman on 2014-04-06
Does Audigy card work normaly?
Did you disabled onboard card in BIOS?

---

### Post by tmixshinodarap on 2014-04-06
The Audigy card works totally normaly, i use it as my primary sound card and no, i didn't disabled the onboard card, i will do this now and post an update.

---

### Post by tmixshinodarap on 2014-04-06
```

Sun Apr  6 05:56:50 2014: Starting jack server...
Sun Apr  6 05:56:50 2014: JACK server starting in realtime mode with priority 10
Sun Apr  6 05:56:50 2014: self-connect-mode is "Don't restrict self connect requests"
Sun Apr  6 05:56:50 2014: Acquired audio card Audio1
Sun Apr  6 05:56:50 2014: creating alsa driver ... hw:1,0|hw:1,0|256|3|44100|0|0|nomon|swmeter|-|32bit
Sun Apr  6 05:56:50 2014: configuring for 44100Hz, period = 256 frames (5.8 ms), buffer = 3 periods
Sun Apr  6 05:56:50 2014: ALSA: final selected sample format for capture: 32bit integer little-endian
Sun Apr  6 05:56:50 2014: [1m[31mERROR: ALSA: got smaller periods 2 than 3 for capture[0m
Sun Apr  6 05:56:50 2014: [1m[31mERROR: ALSA: cannot configure capture channel[0m
Sun Apr  6 05:56:50 2014: [1m[31mERROR: Cannot initialize driver[0m
Sun Apr  6 05:56:50 2014: [1m[31mERROR: JackServer::Open failed with -1[0m
Sun Apr  6 05:56:50 2014: [1m[31mERROR: Failed to open server[0m
Sun Apr  6 05:56:51 2014: Saving settings to "/home/hybrdangl/.config/jack/conf.xml" ...
(qjackctl.real:2375): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
(qjackctl.real:2375): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
[COLOR=#ff0000]05:56:53.902 No puede conectarse al servidor JACK como cliente. - La operación global falló. - No puede conectarse al servidor. Por favor revise la ventana de mensajes para mas información.[/COLOR]
Cannot connect to server socket err = No existe el archivo o el directorio
Cannot connect to server request channel
jack server is not running or cannot be started

```

That's what i got now...

---

### Post by jejeman on 2014-04-06
First, set periods to be 2. For PCI cards always use 2 periods.
Now, since you disabled onboard card, check the number of the Audigy card, it should be hw0 now.

---

### Post by su:bhatta on 2014-04-06
> **tmixshinodarap said:**
> Hi everyone! I'm tryin to work with FL Studio 11.1 in Ubuntu, _*so i installed Ubuntu Studio (Inside normal-ubuntu)*_ :

What does this mean?
You installed Ubuntu Studio packages in a Ubuntu installation?

---

### Post by tmixshinodarap on 2014-04-06
Yes, it shows as hw0 now but it keeps doing the same thing

---

### Post by jejeman on 2014-04-07
Give
```
cat .jackdrc
```

---

### Post by tmixshinodarap on 2014-04-08
```
/usr/bin/jackd -r -dalsa -dhw:0 -r44100 -p512 -n4 -s -S
```

That's the result

*PD: I've deactivated the on-board soundcard just in case.*

---

### Post by tmixshinodarap on 2014-04-08
I've reinstalled Ubuntu 13.10 to see if that will be an answer but no, it's the same thing, but the qjackctl output is different now:

```


[COLOR=#ff0000]23:02:39.251 D-BUS: El servidor JACK no puede iniciarse. Disculpa[/COLOR]
Cannot connect to server socket err = No existe el archivo o el directorio
Cannot connect to server request channel
jack server is not running or cannot be started
Tue Apr  8 23:02:39 2014: Starting jack server...
Tue Apr  8 23:02:39 2014: JACK server starting in non-realtime mode
Tue Apr  8 23:02:39 2014: ERROR: cannot register object path "/org/freedesktop/ReserveDevice1/Audio0": A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0
Tue Apr  8 23:02:39 2014: ERROR: Failed to acquire device name : Audio0 error : A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0
Tue Apr  8 23:02:39 2014: ERROR: Audio device hw:0 cannot be acquired...
Tue Apr  8 23:02:39 2014: ERROR: Cannot initialize driver
Tue Apr  8 23:02:39 2014: ERROR: JackServer::Open failed with -1
Tue Apr  8 23:02:39 2014: ERROR: Failed to open server
Tue Apr  8 23:02:41 2014: Saving settings to "/home/hyan/.config/jack/conf.xml" ...
[COLOR=#ff0000]23:02:44.900 No puede conectarse al servidor JACK como cliente. - La operación global falló. - No puede conectarse al servidor. Por favor revise la ventana de mensajes para mas información.[/COLOR]
Cannot connect to server socket err = No existe el archivo o el directorio
Cannot connect to server request channel
jack server is not running or cannot be started


```

---

### Post by jejeman on 2014-04-09
> **tmixshinodarap said:**
> ```
/usr/bin/jackd -r -dalsa -dhw:0 -r44100 -p512 -n4 -s -S
```
That's the result
-n should always be 2 for PCI card.

Did you install Ubuntu or Ubuntu Studio?

---

### Post by tmixshinodarap on 2014-04-09
Ubuntu 13.10

---

### Post by jejeman on 2014-04-09
Did you, then, enabled the RT priority? Are you in audio group?

---

### Post by tmixshinodarap on 2014-04-09
I'm in the audio group, and yes i've enabled it and disabled it, didn't worked, here are my configs on qjackctl

[IMG]http://i.imgur.com/hXfh3pC.jpg[/IMG]

---

### Post by jejeman on 2014-04-09
When I said enable RT priority I ment did you set up limits.conf?

---

### Post by tmixshinodarap on 2014-04-09
No, i didn't... how i do that?

---

### Post by jejeman on 2014-04-09
JACK when installed should ask user if he wants limits to be set. It looks like this.
```
$ cat /etc/security/limits.d/audio.conf 
# Provided by the jackd package.
#
# Changes to this file will be preserved.
#

@audio   -  rtprio     95
@audio   -  memlock    unlimited
#@audio   -  nice      -19

```
Since you didn't installed Ubuntu Studio you should read this
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

---

### Post by tmixshinodarap on 2014-04-09
My audio.conf looks exactly as yours and the Ubuntu Studio Preparation didn't solve the thing. I thought it was a PulseAudio problem since i watched that many users were having problems with it, i've uninstalled it and nothing happened

This is really frustrating

---

### Post by jejeman on 2014-04-09
Unistalling pulseaudio is bad thing to do, Ubuntu needs it. You can just turn it off.

---

### Post by Clockmender on 2014-04-19
My setup with an E-MU 0404 PCI card needs 48000 sample rate , hw:1,2 as input device, hw:1,0 as playback 256 or 512 Frames/Period, 2 Buffers/Period, Realtime box checked (yours seems to be "non-realtime") and you will need the alsa firmware, libs, drivers and utils loaded. My Audigy card is card1, the internal card is still active and causes no problems. If you are still having trouble, consult my webpages at [www.lafavinie.com/Music](www.lafavinie.com/Music) and look at the Setup, Audio and Studio pages in particular. Have you loaded some elements of Ubuntu Studio on top of a vanilla Ubuntu install? - if yes, have you followed all the required steps, like getting the realtime kernal as your boot option? If in doubt consult my pages or [https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu](https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu) Next, how are you trying to start Jack - with QjackCtl or some other means. Gladish or Claudia are better options than QjackCtl, command line start is very difficult to get exactly right and the various GUI options represent a much lower risk factor. You may also need to set the capture and playback enumerators in your Audigy card - use QasHctl as per my web pages.

You must set Input Device and Output Device seperately in the Jack Setup window - not the overall device as you have done, use the > button next to them to achieve this.

It is entirely possible that you have tinkered too much without getting the basics right, sorry if that sounds harsh, but I have been there too! If this is the case starting from scratch might be a better option.

Aswers to my questions would be appreciated and I may be able to help further.

Good luck.

---

### Post by Clockmender on 2014-04-24
Hmmmm no reply, - he must have sorted it.

---

### Post by SonicPrince on 2014-04-28
If he did sort it, be nice for the 'sort' to be added here to finish the thread as well as for future reference.

Clockmender, that link of yours  is neat, I've bookmarked it for later.
I gotta say, that would have to be the cleanest, neatest studio I've ever seen !

---

