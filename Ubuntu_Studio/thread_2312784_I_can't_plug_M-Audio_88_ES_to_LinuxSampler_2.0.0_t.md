---
title: "I can't plug M-Audio 88 ES to LinuxSampler 2.0.0 through JSampler Fantasia 0.9"
date: 2016-02-07
forum: Ubuntu Studio
---

### Post by astroclubzp on 2016-02-07
Hello!
I can't plug M-Audio 88 ES to LinuxSampler 2.0.0 through JSampler Fantasia 0.9.
However, I plug the keyboard to ZynAddSubFX through QjackCtl 0.4.1 and it works well.

On the other hand, LinuxSampler works well through internal Fantasia MIDI keyboard!

---

### Post by jejeman on 2016-02-07
I think it was never a possibility to do so - connect MIDI keyboard to Fantasia.
You connect MIDI keyboard directly to linuxsampler.
In order to do so you have to make a MIDI port in linuxsamper.

---

### Post by astroclubzp on 2016-02-07
> **jejeman said:**
> I think it was never a possibility to do so - connect MIDI keyboard to Fantasia.
Yes, of course.

> **jejeman said:**
> You connect MIDI keyboard directly to linuxsampler.
In order to do so you have to make a MIDI port in linuxsamper.
How? :confused:
 I can't do it.

---

### Post by jejeman on 2016-02-07
Linuxsampler is acting as a server program. You communicate with it thru port 8888 on localhost.
This will create ALSA MIDI device and one port
```
CREATE MIDI_INPUT_DEVICE ALSA NAME='LinuxSampler'
SET MIDI_INPUT_PORT_PARAMETER 0 0 NAME='Port 0'
SET MIDI_INPUT_PORT_PARAMETER 0 0 ALSA_SEQ_BINDINGS=NONE
```You can put this in one script file. Usually "something.lscp". And feed to linuxsampler via cat command
```
cat something.lscp | netcat localhost 8888
```Of course, you can do all this in Fantasia via GUI. On the right side you add audio and MIDI devices.

---

### Post by astroclubzp on 2016-02-07
So...
1. I created the file "something.lscp" in my home directory. It contains your code:
```
CREATE MIDI_INPUT_DEVICE ALSA NAME='LinuxSampler' 
SET MIDI_INPUT_PORT_PARAMETER 0 0 NAME='Port 0'
SET MIDI_INPUT_PORT_PARAMETER 0 0 ALSA_SEQ_BINDINGS=NONE

```

2. I ran the linuxsampler in **firts** terminal:
```
oleh@oleh:~$ linuxsampler
LinuxSampler 2.0.0
Copyright (C) 2003,2004 by Benno Senoner and Christian Schoenebeck
Copyright (C) 2005-2015 Christian Schoenebeck
Detected features: MMX SSE SSE2
Automatic Stacktrace: Off
Creating Sampler...OK
Registered sampler engines: 'GIG','SF2','SFZ'
Registered MIDI input drivers: JACK
Registered audio output drivers: JACK
Loading instrument editor plugins...OK
Registered instrument editors: 
Registered internal effect systems: LADSPA
Registered internal effects: 11
Starting LSCP network server (0.0.0.0:8888)...OK
LinuxSampler initialization completed. :-)

```

3. After I ran the script in **second** terminal:
```
oleh@oleh:~$ cat something.lscp | netcat localhost 8888 &
[1] 4479
oleh@oleh:~$ ERR:0:There is no midi input driver 'ALSA'.
ERR:0:There is no MIDI input device with index 0.
ERR:0:There is no MIDI input device with index 0.

```

---

### Post by jejeman on 2016-02-07
Your linuxsampler is preconfigured to load JACK MIDI input driver, no ALSA. So you need to make JACK MIDI input device. Just change device type.
```
CREATE MIDI_INPUT_DEVICE JACK NAME='LinuxSampler' 
SET MIDI_INPUT_PORT_PARAMETER 0 0 NAME='Port 0'
```
On my system linuxsampler loads both drivers
```
linuxsampler 
LinuxSampler 2.0.0
Copyright (C) 2003,2004 by Benno Senoner and Christian Schoenebeck
Copyright (C) 2005-2015 Christian Schoenebeck
Detected features: MMX SSE SSE2
Automatic Stacktrace: Off
Creating Sampler...OK
Registered sampler engines: 'GIG','SF2','SFZ'
Registered MIDI input drivers: ALSA,JACK
Registered audio output drivers: ALSA,JACK
Loading instrument editor plugins...OK
Registered instrument editors: 'gigedit'
Registered internal effect systems: LADSPA
no more csLADSPA plugins
Registered internal effects: 379
Starting LSCP network server (0.0.0.0:8888)...OK
LinuxSampler initialization completed. :-)
```

---

### Post by astroclubzp on 2016-02-07
> **jejeman said:**
> Of course, you can do all this in Fantasia via GUI. On the right side you add audio and MIDI devices.
No, I can't do it, because Fantasia right side menu driver selector proposes me *only* JACK driver.

[IMG]https://lh3.googleusercontent.com/_Tpv-2SdGINVbOWIS04t8hdaoQGim72O9OQIsiv-MntDqG_c8_btyJayX2VLuMtaTLwzzdEXqFmzOG5RGo2vIIohTN98SLVnHtNqVjPxUhwwTO8hJgM16NQWZ5GApUOoKQVtyaCu5Za_B7jvzKL9UpVDGmgJzDX3YIqv-wViUN0aqJ7IKme1vTUGM2-ELl85ppcOndHVG3Qf2qSbsXPqA-FFr0vAMmKoSxhtiZJppsR-Nm8ELdZ7hqK3nkW75TcBfRpe9BaWQF_R2TqPtLJHUodOQSGKASanI3Dszidv22fRMbDNyOlKNj3NpaBQKi1jtdnCRFz3tGD-kf1A-EOLaK0anybMIyC7Ijmthee6UlAk37UUNuOBcHbJbzOFEk_No_gVniO11sUTa5p7cOXavRc_dIWws-OJEepdHqEF757UQ-LEzNbde6O42PuhoWLkKg4EXmygsLaATvy5T1z5EHSRZ6PibbGUXvpmyiPj2OKplrnoiGfTD9c_sRqH4xoP6JSPygfXE2CMUL5VMQ9fPSOi4lcE4oW5QM-_tHX9s_6Rz-8moGdgGbrFH2UVDMdCd9Bv=w263-h99-no[/IMG]

---

### Post by jejeman on 2016-02-07
So, create JACK device then.

---

### Post by astroclubzp on 2016-02-07
> **jejeman said:**
> So, create JACK device then.

IMHO, I created it, but M-Audio 88ES doesn't work...

[IMG]https://lh3.googleusercontent.com/hm-WUJgYdRJXBhLXwUEdu9jIAy-RLsAycAuE1aKZBhsih64yZHvsqYFF6bEMr-dVHvWCoRNrTkgSOHBgCvGt9v5KycBZZIYDMK6nRg9aZiPRNxbBqVTZJHEeqvQnt6Ie6qzcQaQdN1XNNlTLerfJnvq5eqEPncf_-OBHjC-yrBNLfD5ziRiuGSu20OHhh7X03giOIP4IxL7YNo8e0PibGqhauf5Wtf_-8jZERuabWGwbu1pUDspksxTELanFMbln3f8LxlzLmBzOkDSf180REx5cMZ4ih94rkBX20DUIp1ZRaqCOWOKPuNkNPpgltL49tloIleR03c0wn3j7wyX9rvPXPIG1XYnx1FE6Wn0-9gVk3BRsiRALQ5aTYVleipx5KQzKw6g9eLpFW1F0W43fdDcTeXT8eQN5cOcqaihKcVHLvlMVjJKkfX9g3vMtsRY9wCEhmEbWftq8l6GWggN48waWQ0H-lK4PgrgRWdAlzswL0UsMB-eC15De_bWPqzCiItPmmetBauLk2k0TNKf24jErf0ktfkPx6NiJwYvkERt4KiVJHkLqGGVRii7P1ap-c6Fw=w1305-h734-no[/IMG]

---

### Post by jejeman on 2016-02-07
You need to connet now the Keystation port to linuxsampler MIDI port in order to recive MIDI messages.
Since keystation is in ALSA "realm", and linuxsampler in JACK "relam" you need to bind these two "realms". There are two ways to do this:
1. a2jmidid
2. adding MIDI driver in JACK server settings
After binding, you will see ports from ALSA MIDI in JACK MIDI. Then just connect.

---

### Post by astroclubzp on 2016-02-07
> **jejeman said:**
> You need to connet now the Keystation port to linuxsampler MIDI port in order to recive MIDI messages.
Since keystation is in ALSA "realm", and linuxsampler in JACK "relam" you need to bind these two "realms". There are two ways to do this:
1. a2jmidid
2. adding MIDI driver in JACK server settings
After binding, you will see ports from ALSA MIDI in JACK MIDI. Then just connect.
Hurra!

**a2jmidid** solved my problem! :D

Many thanks!

---

