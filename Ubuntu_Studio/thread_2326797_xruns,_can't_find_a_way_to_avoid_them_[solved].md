---
title: "xruns, can't find a way to avoid them [solved]"
date: 2016-06-04
forum: Ubuntu Studio
---

### Post by Carlosll on 2016-06-04
Hi


I have lots of xruns with and Ua-25ex, toshiba satellite l-655 with an intel i5. Ubuntu Studio 16.04.

I want to use the Studio for audio production.  

I Have almost past the realtimeconfigquickscan without some options that seems to be deprecated: 

for example: tmpfs on tmp: [http://wiki.linuxaudio.org/wiki/system_configuration#tmpfs](http://wiki.linuxaudio.org/wiki/system_configuration#tmpfs)

How do I configure the jack? 

thank you and sorry for the previous version of this question, I was in a bad moment.

---

### Post by Carlosll on 2016-06-06
the first thing is that I boot the studio with the lowlatency kernel:

```
uname -a

 4.4.0-21-lowlatency #37-Ubuntu SMP PREEMPT Mon Apr 18 20:20:26 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```

and when I run the realtimeconfigquickscan downloaded from [URL="https://github.com/raboof/realtimeconfigquickscan"]https://github.com/raboof/realtimeconfigquickscan 
[/URL]
it says:

```
~/realtimeconfigquickscan$ perl ./realTimeConfigQuickScan.pl
== GUI-enabled checks ==
Checking if you are root... no - good
Checking filesystem 'noatime' parameter... 4.4.0 kernel - good
(relatime is default since 2.6.30)
Checking CPU Governors... CPU 0: 'ondemand' CPU 1: 'ondemand' CPU 2: 'ondemand' CPU 3: 'ondemand'  - not good
Set CPU Governors to 'performance' with 'cpufreq-set -c <cpunr> -g performance'
See also: [http://linuxmusicians.com/viewtopic.php?f=27&t=844](http://linuxmusicians.com/viewtopic.php?f=27&t=844)
Checking swappiness... 10 - good
Checking for resource-intensive background processes... none found - good
Checking checking sysctl inotify max_user_watches... >= 524288 - good
Checking access to the high precision event timer... readable - good
Checking access to the real-time clock... readable - good
Checking whether you're in the 'audio' group... yes - good
Checking for multiple 'audio' groups... no - good
Checking the ability to prioritize processes with chrt... yes - good
Checking kernel support for high resolution timers... found - good
**Kernel with Real-Time Preemption... not found - not good**
Kernel without real-time capabilities found
For more information, see [http://wiki.linuxaudio.org/wiki/system_configuration#installing_a_real-time_kernel](http://wiki.linuxaudio.org/wiki/system_configuration#installing_a_real-time_kernel)
Checking if kernel system timer is high-resolution... found - good
Checking kernel support for tickless timer... found - good
== Other checks ==
Checking filesystem types... ok.
not found.
** Warning: no tmpfs partition mounted on /tmp
   For more information, see:
   - [http://wiki.linuxaudio.org/wiki/system_configuration#tmpfs](http://wiki.linuxaudio.org/wiki/system_configuration#tmpfs)
   - [http://lowlatency.linuxaudio.org](http://lowlatency.linuxaudio.org)
** Set $SOUND_CARD_IRQ to the IRQ of your soundcard to enable more checks.
   Find your sound card's IRQ by looking at '/proc/interrupts' and lspci.
```

So I don't know if the PREEMPT kernel is PREEMPT or not. I'm searching what's about:

---

### Post by Carlosll on 2016-06-06
Found in:

[http://www.webhostingtalk.com/showthread.php?t=914631](http://www.webhostingtalk.com/showthread.php?t=914631)

SMP = Symmetric Multi-Processors.
PREEMP = PREEMPtable.
RT = Real Time.

all right. but is the SMP kernel good for music?  

I'm trynig to boot wiht the other kernel that are include in the studio.

---

### Post by Carlosll on 2016-06-06
The only kernel included in Ubuntu Studio it's the SMP one. 

so the question is, it's ok to music production the SMP PREEMT kernel and it is thought and working for the music production?
or should I Install the RT one?

Searching

---

### Post by Carlosll on 2016-06-06
from:
[http://wiki.linuxaudio.org/wiki/system_configuration#the_kernel](http://wiki.linuxaudio.org/wiki/system_configuration#the_kernel)

"Although the best results are still expected when using a real-time kernel. Try it, test it and decide for yourself.  [..]
In the pre-2.6.39 kernel era rt kernels were indeed necessary in some  cases where sound devices were sharing IRQ's with other peripherals.  With the rt kernel and the rtirq script you could prioritize IRQ threads  but since 2.6.39 it is possible to use the rtirq kernel with a generic  kernel and the threadirqs kernel option."

"The most reliable way to detect relevant status of a running kernel, is probably thus:"

CONFIG_HZ_1000=y
CONFIG_HZ=1000
CONFIG_PREEMPT_RT_FULL=y
CONFIG_PREEMPT=y

so, searching in the config

mousepad config-4.4.0-21-lowlatency

it shows that

CONFIG_PREEMPT_RT_FULL it is not wrote in the file.so do I have to install a RT Kernel?

It says:

"
   Ubuntu Studio 12.04 comes with a 1000 Hz non-real-time low-latency  kernel. Unfortunately there are no packaged real-time kernels available  but using [the kernel build method described in this Wiki]("http://wiki.linuxaudio.org/wiki/system_configuration#build_your_own_real-time_kernel") it should be fairly easy to build your own real-time kernel"

But I'm using a 16.04 so I have to search for something new.

---

### Post by Carlosll on 2016-06-06
I have found a website:

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

posted on 01/jan/2016

And I have found that the 16.04 studio was released on April 21, 2016.

so, it could be deprecated. anyway, I'm going to try the tips of ubuntu Studio preparation

---

### Post by Carlosll on 2016-06-06
"PulseAudio and Jack working separately  It  is possible to use jack without communicating with Pulse Audio : not  use Dbus. In Qjackctl (Jack Control), go to the settings and uncheck the  Dbus option. Restart the computer or your session. And then, when you  start jackd, Pulse Audio and Jack works separately. 
It  is very interesting when you have an integrated sound card and a sound  card for audio. This way, the system continue to use the default sound  card as if nothing changed. And audio application will only see the  dedicated sound card using Jack. 
Indeed, it is not very usefull if you have only one sound card."

so I uncheck the D-bus option in Jack

---

### Post by Carlosll on 2016-06-06
nop

```

 18:07:32.888 Reiniciar estadísticas.
 18:07:32.935 Cambios en las conexiones ALSA.
 18:07:32.939 D-BUS: Disponible (org.jackaudio.service aka jackdbus).
 Cannot connect to server socket err = No existe el archivo o el directorio
 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
 18:07:33.152 Cambió el gráfico de conexiones ALSA.
 18:07:39.901 Cambió el gráfico de conexiones ALSA.
 18:07:39.991 Cambios en las conexiones ALSA.
 18:08:37.563 Cambios en las conexiones JACK.
 18:08:37.567 Cliente activado.
 18:08:37.568 Patchbay desactivada.
 ]18:09:11.633 XRUN callback (1).
 18:09:13.600 XRUN callback (95 omitidos).
 18:09:15.611 XRUN callback (125 omitidos).
 18:09:17.617 XRUN callback (2 omitidos).
 ]18:09:23.100 XRUN callback (226).
 18:09:23.637 XRUN callback (31 omitidos).
 18:09:25.648 XRUN callback (125 omitidos).
 18:09:25.860 Cambió el gráfico de conexiones ALSA.
 18:09:25.864 Cambió el gráfico de conexiones de JACK.
 18:09:26.059 Cambios en las conexiones JACK.
 18:09:26.060 Cambios en las conexiones ALSA.
 18:09:27.676 XRUN callback (126 omitidos).
 18:09:29.685 XRUN callback (124 omitidos).
 18:09:31.695 XRUN callback (125 omitidos).
 18:09:33.704 XRUN callback (124 omitidos).
 18:09:35.716 XRUN callback (125 omitidos).
 18:09:37.726 XRUN callback (125 omitidos).
 18:09:39.737 XRUN callback (124 omitidos).
 18:09:41.747 XRUN callback (125 omitidos).
 18:09:43.757 XRUN callback (125 omitidos).
 18:09:45.767 XRUN callback (124 omitidos).
 18:09:46.558 Cliente desactivado.

```
only triyng the hydrogen to play a song

---

### Post by QIII on 2016-06-06
Hello!

Would you please succinctly state your support request now?

Continuosly piling new posts on to your thread as you are makes it confusing for anyone who might offer help.  Please state your question and wait for someone to respond.

Also:  Please use standard colors and enclose all commands and results in code tags.

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by Carlosll on 2016-06-06
Problably I need to kill pulse audio, or not...

---

### Post by QIII on 2016-06-06
Or:  State your question and wait for a response.

---

### Post by QDR06VV9 on 2016-06-06
I am not sure what is going on...but have you tried this yet?

```
jackctl_server_start
```
More here: [http://jackaudio.org/files/docs/html/group__ControlAPI.html](http://jackaudio.org/files/docs/html/group__ControlAPI.html)

---

### Post by Carlosll on 2016-06-06
Hello

thank you, I will do it.

the thing is that I want to  use The Ubuntu Studio for audio production, recording guitar, bass,  hydrogen, voice, etc. but I can hardly get it to work. I get a lot of  xruns when only I'm triyng to start to play a simple drums song on hydrogen and most of the times qjack it gets freeze.

I have blacked list the integrated soundcard that always have made conflicts whit the external one, that I want to use. And also, I have Disabled the pulse audio in the qjacktl, because it's said that doesn't not work for low latencies. That's what I have done. 

what can I do to achieve an audio production studio? 

Thank you

---

### Post by Carlosll on 2016-06-06
HI

```

carlitos@carlitos-Satellite-L655:~$ jackctl_server_start
jackctl_server_start: no se encontró la orden

```

It say that the command it is not found. But, when I start the qjackctl in gui>start button doesn't have the same effect?

---

### Post by yoshii on 2016-06-06
This will hopefully be helpful for you:  [http://ubuntuforums.org/showthread.php?t=2309922&highlight=ubuntu+studio+daw](http://ubuntuforums.org/showthread.php?t=2309922&highlight=ubuntu+studio+daw)

It includes tips like disabling file access time logging in fstab, setting CPU power management to Performance, disabling unneeded linux services with .override files, and I have available screenshots of how to configure PulseAudio's settings files for low-latency.  I can email the archive of info to you if you like since I can't yet find a file hosting site for it.  

Personally, I gave up on using JACK for some things.  Although the AV Linux distro seems to have it all worked out for JACK (but not for Wine/PulseAudio).  
But the thing is, I use 32-bit Windows Reaper for audio use instead of the native Linux programs.   So that's the main difference.

---

### Post by Carlosll on 2016-06-07
Hi everybody

I have found what was happening!! 

I had old songs from another distro and a previous version of hydrogen and the references to the instruments into the files of that songs are mistaken.

Probably the instruments libraries are named different or whatever, so when I started that songs the system broke into 
xruns.

I didn't believe it so I have been doing bad things to the system such open ardour, hydrogen, blender, and firefox and trying to play a youtube video, recording both inputs of sound card as recording hydrogen everything at same time and:

NO XRUNS!!!!!!!

Great, thank all of you, and sorry for the first version of this thread, I was discovering that all my songs were gone.

So thank you again and I'm going to change the thread as solved

---

### Post by yoshii on 2017-01-30
Hey, I'm really glad it worked out for you!  Nice.  :D

---

