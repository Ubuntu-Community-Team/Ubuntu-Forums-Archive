---
title: "QjackCtl and IDJC problem"
date: 2014-12-30
forum: Ubuntu Studio
---

### Post by tomas24 on 2014-12-30
Hi all,

I saw the kickass new features in ubuntu studio to make internet radio with IDJC en QjackCtl..

I have read many tutorials and forum posts of ppl with the same issue.. but still not running

We have Beringher USB mixer and a Onboard Sound card (Digitial and analog)

We  want to get the music input manually in the mixer... so we can fade it/out manual.


The problem weve got after a **** load of tutorials after starting QjackCtl is:

```

 [COLOR=#999999]16:17:07.394 Patchbay uitgeschakeld.[/COLOR]
 [COLOR=#999999]16:17:07.396 Initialisatie van statistieken.[/COLOR]
 [COLOR=#cccc99]16:17:07.400 ALSA verbindingen aangepast.[/COLOR]
 [COLOR=#999999]16:17:07.405 DBUS : Service is beschikbaar (org.jackaudio.service ook gekend als jackdbus).[/COLOR]
 [COLOR=#999999]16:17:07.412 Opstart script...[/COLOR]
 [COLOR=#990099]16:17:07.413 artsshell -q terminate[/COLOR]
 Cannot connect to server socket err = File does not exist

 Cannot connect to server request channel
 jack server is not running or cannot be started
 Cannot connect to server socket err = File does not exist

 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#66cc99]16:17:07.414 ALSA verbindingen aangepast.[/COLOR]
 sh: 1: artsshell: not found
 [COLOR=#999999]16:17:07.814 Opstart script beëindigd met exit status=32512.[/COLOR]
 [COLOR=#ff0000]16:17:07.896 DBUS : JACK server could not be started / kon niet worden gestart. Sorry[/COLOR]
 Tue Dec 30 16:17:07 2014: Starting jack server...
 Tue Dec 30 16:17:07 2014: JACK server starting in non-realtime mode
 Tue Dec 30 16:17:07 2014: ERROR: control open "/dev/dsp" (No such file or directory)
 Tue Dec 30 16:17:07 2014: ERROR: control open "/dev/dsp" (No such file or directory)
 Tue Dec 30 16:17:07 2014: creating alsa driver ... /dev/dsp|/dev/dsp|2048|3|192000|0|0|nomon|swmeter|-|32bit
 Tue Dec 30 16:17:07 2014: ERROR: control open "/dev/dsp" (No such file or directory)
 Tue Dec 30 16:17:07 2014: ERROR: ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
 Tue Dec 30 16:17:07 2014: ERROR: Cannot initialize driver
 Tue Dec 30 16:17:07 2014: ERROR: JackServer::Open failed with -1
 Tue Dec 30 16:17:07 2014: ERROR: Failed to open server
 Tue Dec 30 16:17:09 2014: Saving settings to "/home/meine/.config/jack/conf.xml" ...
 [COLOR=#ff0000]16:17:11.372 Could not connect to the JACK server[/COLOR]

 Cannot connect to server socket err = fiel does not exist

 Cannot connect to server request channel
 jack server is not running or cannot be started



```


we hope we can get it working
thx in advance

---

