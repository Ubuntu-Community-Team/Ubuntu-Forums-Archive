---
title: "PulseAudio Jack not loaded after a logout/login or a QjackCtl restart"
date: 2016-05-22
forum: Ubuntu Studio
---

### Post by oscalypso on 2016-05-22
Hi 

At boot, when i start **QjackCtl**, **PulseAudio Jack** is automatically loaded and connected to system 
like this :

[https://drive.google.com/file/d/0B73lh-1di29vRlk1ZTdPUUUwTWM/view?usp=sharing](https://drive.google.com/file/d/0B73lh-1di29vRlk1ZTdPUUUwTWM/view?usp=sharing)

After a logout and login of the session, **PulseAudio Jack** is not here anymore and I can't get sound from Firefox etc...

[https://drive.google.com/file/d/0B73lh-1di29vbmQ5UWQ1YjExdXc/view?usp=sharing](https://drive.google.com/file/d/0B73lh-1di29vbmQ5UWQ1YjExdXc/view?usp=sharing)

So
I have put this script  that is loaded on each Jack startup (under Options tab in Qjackctl)

```
[I]#load pulseaudio jack modules
#!/bin/bash

pactl load-module module-jack-sink 
pactl load-module module-jack-source

echo "set-default-sink jack_out" | pacmd
echo "set-default-source jack_in" | pacmd

[/I]
```It works fine when I logout/login or stop/restart[B] QjackCtl

[/B]The problem is on Boot or Restart: I have 2 **PulseAudio Jack** :

[https://drive.google.com/file/d/0B73lh-1di29vSjUweGpPQi0zU0U/view?usp=sharing](https://drive.google.com/file/d/0B73lh-1di29vSjUweGpPQi0zU0U/view?usp=sharing)


The solution would be a condition in the script to test if PulseAudio Jack is already there
or to remove the command that load PulseAudio Jack on boot and let the script do the job

I can't find a way for one solution or the other 

Any help is much appeciated

Thanks guys 

Fred

---

### Post by oscalypso on 2016-05-24
I solved it

in the file **/etc/pulse/default.pa**

i've put in comments the lines under [B]"Automatically connect sink and source if JACK server is present"

[/B]like this :
```
[B]#.ifexists module-jackdbus-detect.so
#.nofail
#load-module module-jackdbus-detect channels=2
#.fail
#.endif[/B]
```

then under Options tab in QjackCtl
i 've ticked the line[B]run script after startup
[/B]and wrote the path to the script on the right field
the script is
```
[B]pactl load-module module-jack-sink channels=2
pactl load-module module-jack-source channels=2
[/B]
```
this way pulseAudio is connected each time jack is started even after logout

---

