---
title: "Jack, alsa"
date: 2013-02-05
forum: Ubuntu Studio
---

### Post by DjRadu on 2013-02-05
I am a complete beginer in ubuntu studio for music making , i was making music on windows but i flushed windows and never will return ! Now their are allot of audio/music software i knew from windows and found in Ubuntu Studio.Problem is many times i get messages like the jack could not be started,error in jack, alsa vs jack , etc,etc. What i want to you to ask is that you kindly instruct me in how to corect configure JACK,ALSA etc so this kind of problems do not apear anymore....but especialy jack.I now im maybe anoyng but i want to learn and where is the best place than here,sorry if its offtopic,i did not knew where to start ! Sorry my english im from Romania.
_[COLOR=Blue]**Off Topic **[/COLOR]_: Is their any way to get the elegant dvd with case cover of UBUNTU STUDIO latest version like the time when i wass receiving ubuntu,kubuntu,edubuntu just to try them,i know this does not happen anymore il pay but i dont have a credit card just bank transfer,western union,money gram SORRY FOR OFFTOPIC !
THANK YOU VERRY MUCH !
DJ RADU !

---

### Post by jejeman on 2013-02-05
```
jack could not be started
```One of the most common reason is that something is already using the soundcard. Kill all programs that use audio and try again.
Make sure that you selected the right sound card, if you have more than one.

---

### Post by ttoine on 2013-02-07
Are you using the integrated sound card of your PC ? Or do you have a second sound card, and if yes, wich brand and model ?

---

### Post by DjRadu on 2013-02-07
> **ttoine said:**
> Are you using the integrated sound card of your PC ? Or do you have a second sound card, and if yes, wich brand and model ?
My inegrated card !

---

### Post by DjRadu on 2013-02-08
My problem shows like this :

[COLOR=Red][B]D-BUS: JACK could not not be started 

Sorry[/B][/COLOR]

The next one :
  
-**[COLOR=Red]Could not connect to JACK server as client.[/COLOR]**
**[COLOR=Red]- Overall operation failed.[/COLOR]**
**[COLOR=Red]- Unable to connect to server.[/COLOR]**
**[COLOR=Red]Please check the messages window for more info.[/COLOR]**



And the code !
   
```

09:24:43.135 Patchbay deactivated.
 09:24:43.135 Statistics reset.
 09:24:43.147 ALSA connection change.
 09:24:43.157 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 09:24:43.165 ALSA connection graph change.
 (qjackctl.real:3178): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl.real:3178): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 09:24:44.264 D-BUS: JACK server could not be started. Sorry
 Fri Feb  8 09:24:44 2013: Starting jack server...
 Fri Feb  8 09:24:44 2013: JACK server starting in realtime mode with priority 10
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 (qjackctl.real:3178): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl.real:3178): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 Fri Feb  8 09:24:44 2013: control device hw:0
 Fri Feb  8 09:24:44 2013: control device hw:0
 Fri Feb  8 09:24:44 2013: [1m[31mERROR: Failed to acquire device name : Audio0 error : Method "RequestRelease" with signature "i" on interface "org.freedesktop.ReserveDevice1" doesn't exist
 [0m
 Fri Feb  8 09:24:44 2013: [1m[31mERROR: Audio device hw:0 cannot be acquired...[0m
 Fri Feb  8 09:24:44 2013: [1m[31mERROR: Cannot initialize driver[0m
 Fri Feb  8 09:24:44 2013: [1m[31mERROR: JackServer::Open failed with -1[0m
 Fri Feb  8 09:24:44 2013: [1m[31mERROR: Failed to open server[0m
 Fri Feb  8 09:24:45 2013: Saving settings to "/home/djradu/.config/jack/conf.xml" ...
 (qjackctl.real:3178): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl.real:3178): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 09:28:00.393 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started

```PLEASE HELP !

---

### Post by Sylos on 2013-02-08
Hello.

If you are using a version of Ubuntu/Ubuntu studio that has Pulseaudio installed try the following:

```
sudo killall pulseaudio
```

then try starting jack and set what the message window says. You'll need to start Jack within a few seconds of issuing that command because the little devil respawns fairly rapidly.

Cheers

---

### Post by ttoine on 2013-02-08
Don't kill Pulse Audio, install the package "pulseaudio-module-jack".

Also, can you try to start jack without the real time option, to see if it a matter of real time access right ?

---

### Post by DjRadu on 2013-02-09
In UBUNTU SOFTWARE CENER iinstalled ome stuff like ALSA to JACK bridge and a few things more an it works ow,problem solved,tahnk you :KS

---

