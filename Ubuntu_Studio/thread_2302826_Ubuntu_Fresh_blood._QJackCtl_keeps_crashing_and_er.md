---
title: "Ubuntu Fresh blood. QJackCtl keeps crashing and error-ing."
date: 2015-11-13
forum: Ubuntu Studio
---

### Post by serge17 on 2015-11-13
Hi community, Serge here

I'm recently new to Linux. I've installed UbuntuStudio on an Eeepc.
Runs great, got Qjack working with my Trust Usb Card and Rakarrack...
Until yesterday i start having issues with Ubuntu Software Center so i updated my system manually. All went fine, no more Soft Center errors,
unfortunately, now QJack keeps crashing and giving me an error:
 (this one when i iniciate it)

 [B][COLOR=#999999]21:31:30.068 Patchbay deactivated.[/COLOR]
[/B]
**[COLOR=#999999]21:31:30.114 Statistics reset.[/COLOR]**
**[COLOR=#cccc99]21:31:30.334 ALSA connection change.[/COLOR]**
**[COLOR=#999999]21:31:30.405 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]**
**Cannot connect to server socket err = Ficheiro ou directoria inexistente**
**Cannot connect to server request channel**
**jack server is not running or cannot be started**
**[COLOR=#66cc99]21:31:30.429 ALSA connection graph change.[/COLOR]**
**(qjackctl:4449): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed**
[B](qjackctl:4449): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed


[/B](and after when i hit Start)

 
[B][COLOR=#ff0000]21:33:18.484 D-BUS: JACK server could not be started. Sorry[/COLOR]
[/B]
**[COLOR=#999999]Fri Nov 13 21:33:17 2015: Starting jack server...[/COLOR]**
**[COLOR=#999999]Fri Nov 13 21:33:17 2015: JACK server starting in realtime mode with priority 10[/COLOR]**
**[COLOR=#999999]Fri Nov 13 21:33:18 2015: ERROR: cannot register object path "/org/freedesktop/ReserveDevice1/Audio0": A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0[/COLOR]**
**[COLOR=#999999]Fri Nov 13 21:33:18 2015: ERROR: Failed to acquire device name : Audio0 error : A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0[/COLOR]**
**[COLOR=#999999]Fri Nov 13 21:33:18 2015: ERROR: Audio device hw:Intel cannot be acquired...[/COLOR]**
**[COLOR=#999999]Fri Nov 13 21:33:18 2015: ERROR: Cannot initialize driver[/COLOR]**
**[COLOR=#999999]Fri Nov 13 21:33:18 2015: ERROR: JackServer::Open failed with -1[/COLOR]**
**[COLOR=#999999]Cannot connect to server socket err = Ficheiro ou directoria inexistente[/COLOR]**
**[COLOR=#999999]Cannot connect to server request channel[/COLOR]**
**[COLOR=#999999]jack server is not running or cannot be started[/COLOR]**
**[COLOR=#999999](qjackctl:4449): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed[/COLOR]**
**[COLOR=#999999](qjackctl:4449): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed[/COLOR]**
**[COLOR=#999999]Fri Nov 13 21:33:18 2015: ERROR: Failed to open server[/COLOR]**
**[COLOR=#999999]Fri Nov 13 21:33:19 2015: Saving settings to "/home/serge/.config/jack/conf.xml" ...[/COLOR]**
**[COLOR=#ff0000]21:33:21.130 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]**
**[COLOR=#999999]Cannot connect to server socket err = Ficheiro ou directoria inexistente[/COLOR]**
**[COLOR=#999999]Cannot connect to server request channel[/COLOR]**
[B][COLOR=#999999]jack server is not running or cannot be started
[/COLOR][/B][COLOR=#999999]

[/COLOR]I've tried lots of advices from around here and the internets but it keeps failing. At first i thought it could be the sound card but the weird thing is that it works in Audacity. I got a bented electronic keyboard plugged through jack to the mic socket of the usb card. In audacity i select the usb card as mic input and it records like a charm.
I've tried unninstaling Qjack and reinstalling it. Try force reloading Alsa. Uninstalled pulseaudio after reading that it could affect the process. I've been trying with different tweaks but with no sucess.
The setup in Qjack used to be hw:0,0 for the output device and hw:1,0 for the input. (don't know if that helps)
The currently version Ubuntu is 14.04.3 LTS 

If someone could help me with this it would be really nice.
Thanks in advance**[COLOR=#999999][/COLOR]**

---

### Post by marseille2 on 2015-11-13
[COLOR=#000000]You could try this:



1. Go the terminal and make sure jack is killed:

```
$ killall jackd jackdbus
```[/COLOR]
[COLOR=#000000]
2. delete these files:

  
[LIST]
[*]~/.jackdrc
[*]~/.config/jack/conf.xml
[*]~/.config/rncbc.org/QjackCtl.conf
[*](also delete the 'pulse' *directory* if it's still in .config)
[/LIST]

[/COLOR]
3. Reboot


4. Fire up qjackctl and see if it works. You might need to check if dbus is checked or not (in settings), and choose the appropriate input/output for your card. You can find your sound card(s) with:

```
$ cat /proc/asound/cards
```

Alternatively, you can just [fire up jack from the command line]("http://linuxmusicians.com/viewtopic.php?f=1&t=10893"), or use another package. I think there's been some problems with getting Qjackctl to suspend pulseaudio (commonly seen to be causing your [error]("http://askubuntu.com/questions/224151/jack-server-could-not-be-started-when-using-qjackctl")). So I think some people use a program named [Catia]("http://kxstudio.linuxaudio.org/Applications:Catia") (probably the KX studio repos has it).

Also see this [thread]("http://ubuntuforums.org/showthread.php?t=2270247") for more... 

And last, but not least... if this fix doesn't work for you... post the output of:

```
$ cat /proc/asound/cards

```
so that someone can come along, and add some advice:)

---

### Post by serge17 on 2015-11-13
bonjour :)

thanks, gonna try it and reply as soon as i got sum news.

---

### Post by serge17 on 2015-11-13
Hey again,
i tried to remove the files you listed but it said the directory didn't exist.

here's the output of sound cards

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdff00000 irq 29
 1 [Device         ]: USB-Audio - USB Sound Device
                      USB Sound Device at usb-0000:00:1d.0-1, full speed

Jack still doesn't work. Thanks thought.
Gonna keep looking. It worked before so it's gotta work again somehow. ;)

---

