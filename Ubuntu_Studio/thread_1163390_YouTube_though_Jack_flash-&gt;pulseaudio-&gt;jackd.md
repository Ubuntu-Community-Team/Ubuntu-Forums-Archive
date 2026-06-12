---
title: "YouTube though Jack: flash-&gt;pulseaudio-&gt;jackd-&gt;alsa"
date: 2009-05-18
forum: Ubuntu Studio
---

### Post by raboofje on 2009-05-18
I got YouTube working though Jack, and wanted to share my approach.

First I tried libflashsupport-jack (details [here](http://arnout.engelen.eu/index.php/Jack#libflashsupport-jack)), but that resulted in  audio with small hickups and a very unstable firefox.

Second try was using the flash->pulseaudio->jackd->alsa path. To have pulseaudio output to jack, you need pulseaudio-module-jack which unfortunately [isn't in ubuntu anymore](https://bugs.launchpad.net/ubuntu/+bug/198048). Some googling [suggested](http://ubuntuforums.org/showthread.php?t=548178) downloading packages for other distributions and dropping them into my ubuntu installation, but those are terrible hacks which indeed didn't work. 

Then I realized that I could just build from the ubuntu source package:
[LIST]
[*]apt-get build-dep pulseaudio
[*]apt-get install libjack-dev
[*]apt-get source pulseaudio
[*]cd pulseaudio_<tab>
[*]./configure --with-jack
[*]cd src
[*]make module-jack-sink.la
[*]cp .libs/module-jack-sink.so /usr/lib/pulse-0.9/modules
[/LIST]

This produced a usable module-jack-sink.so, so I could:

[LIST]
[*]create a jackd.pa with pretty much only module-jack-sink
[*]start jack
[*]start pulseaudio
[*]start firefox
[*]open youtube
[*]enjoy :)
[/LIST]

Hope this helps some of you trying to achieve the same.

---

### Post by bxcrx on 2009-05-18
Did you just want to try out Jack?

---

### Post by raboofje on 2009-05-19
> **bxcrx said:**
> Did you just want to try out Jack?

No, I wanted to use some applications that require Jack to work (well) and some that don't (Flash) simultaneously. 

Another option would be using dmix, but in my experience that introduces too much of a performance hit.

---

### Post by thorgal on 2009-05-19
this is working quite well with my patch set (oss2jack). See howto at
[http://linuxmusicians.com/viewtopic.php?p=5862#p5862](http://linuxmusicians.com/viewtopic.php?p=5862#p5862)

---

### Post by raboofje on 2009-05-19
Hmm, while much much more stable than libflashsupport-jack, this is still not as solid as I'd hoped. I should look into oss2jack soon :).

---

### Post by markbuntu on 2009-05-22
The module-pulse-jack from the Debian repos work. Ubuntu is built on Debian.

There is no longer any pulse 0.9.14 modules at Debian since all development has moved to pulse0.9.15 but the module-pulse-jack for 0.9.15 works just fine with pulse0.9.15 from themuso's PPA which originally included the pulse-jack module but that was stripped out when 0.9.15 was accepted into Koala. Also stripped out were the libasound2 modules for oss-jack and alsa-jack to allow oss and alsa apps to use jack natively.

There is also more on getting pulse and jack to work together here. I find that they behave better when pulse is started first and the modules are loaded via a small script at jack start. This lets jack take control of the hardware and the modules are unloaded automatically when jack is closed.

The pulse and jack devs are both working to make jack and pulse behave better together through dbus. There is a discussion going on at the pulse mailing list about jack and dbus now. 

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

The only issues are that pulse will crash if not disconnected before closing jack and if you have only one audio device pulse may crash anyway when jack is closed but turning on a rtp device seems to fix that.

Someday jack will return to /main and these issues will be gone...

---

### Post by raboofje on 2009-05-23
> **markbuntu said:**
> The module-pulse-jack from the Debian repos work.

Um, no they don't: as you document yourself [here](http://ubuntuforums.org/showthread.php?t=843012), sid currently has 0.9.15, jaunty still carries 0.9.14, and they're not binary compatible.

> the module-pulse-jack for 0.9.15 works just fine with pulse0.9.15 from themuso's PPA

I didn't know about that PPA - I might try it, but this is getting a bit messy: soon we'll find ourselves mix-and-matching packages from Ubuntu proper, the backports, themuso's PPA, khashayar's PPA, 64studio, ...

> The pulse and jack devs are both working to make jack and pulse behave better together through dbus. There is a discussion going on at the pulse mailing list about jack and dbus now. 

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Did you mean to link to the pulse mailinglist?

> The only issues are that pulse will crash if not disconnected before closing jack and if you have only one audio device pulse may crash anyway when jack is closed but turning on a rtp device seems to fix that.

I'm getting crashes after a while during use - perhaps i should try upgrading to 0.9.15 though.

---

### Post by mocha on 2009-05-31
> **raboofje said:**
> 
Then I realized that I could just build from the ubuntu source package:
[LIST]
[*]apt-get build-dep pulseaudio
[*]apt-get source pulseaudio
[*]cd pulseaudio_<tab>
[*]./configure --with-jack
[*]cd src
[*]make module-jack-sink.la
[*]cp .libs/module-jack-sink.so /usr/lib/pulse-0.9/modules
[/LIST]

This produced a usable module-jack-sink.so, so I could:

[LIST]
[*]create a jackd.pa with pretty much only module-jack-sink
[*]start jack
[*]start pulseaudio
[*]start firefox
[*]open youtube
[*]enjoy :)
[/LIST]

Hope this helps some of you trying to achieve the same.

Thank you!!  I use Jack with Pulseaudio to make screen captures with recordmydesktop and needed this module to get audio cap.

---

### Post by mocha on 2009-06-01
Markbuntu,

May I suggest you make a link to post 1 of this thread in your guide [http://ubuntuforums.org/showthread.php?t=843012]("http://ubuntuforums.org/showthread.php?t=843012") under the heading "Pulse Audio through jack".  I think a lot of us coming from Intrepid will need to know this.

---

### Post by crazybuntu on 2009-06-01
as usual nothing works on first try.. i got this error when doing  make module-jack-sink.la:

```

/bin/bash ../libtool --tag=CC   --mode=compile gcc -std=gnu99 -DHAVE_CONFIG_H -I. -I..    -I../src -I../src/modules -I../src/modules/rtp -I../src/modules/gconf -I../src/modules/bluetooth -pthread -D_POSIX_PTHREAD_SEMANTICS     -DPA_DLSEARCHPATH=\"/usr/local/lib/pulse-0.9/modules/\" -DPA_DEFAULT_CONFIG_DIR=\"/usr/local/etc/pulse\" -DPA_BINARY=\"/usr/local/bin/pulseaudio\" -DPA_SYSTEM_RUNTIME_PATH=\"/usr/local/var/run/pulse\" -DPA_SYSTEM_CONFIG_PATH=\"/usr/local/var/lib/pulse\" -DPA_SYSTEM_STATE_PATH=\"/usr/local/var/lib/pulse\" -DAO_REQUIRE_CAS -DPULSE_LOCALEDIR=\"/usr/local/share/locale\" -DPA_MACHINE_ID=\"/usr/local/var/lib/dbus/machine-id\" '-DDEBUG_TRAP=__asm__("int $3")'  -g -O2 -Wall -W -Wextra -pedantic -pipe -Wno-long-long -Wvla -Wno-overlength-strings -Wconversion -Wundef -Wformat -Wlogical-op -Wpacked -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wdeclaration-after-statement -Wfloat-equal -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-noreturn -Wshadow -Wendif-labels -Wpointer-arith -Wcast-align -Wwrite-strings -Wno-unused-parameter -ffast-math -MT module_jack_sink_la-module-jack-sink.lo -MD -MP -MF .deps/module_jack_sink_la-module-jack-sink.Tpo -c -o module_jack_sink_la-module-jack-sink.lo `test -f 'modules/module-jack-sink.c' || echo './'`modules/module-jack-sink.c
mkdir .libs
 gcc -std=gnu99 -DHAVE_CONFIG_H -I. -I.. -I../src -I../src/modules -I../src/modules/rtp -I../src/modules/gconf -I../src/modules/bluetooth -pthread -D_POSIX_PTHREAD_SEMANTICS -DPA_DLSEARCHPATH=\"/usr/local/lib/pulse-0.9/modules/\" -DPA_DEFAULT_CONFIG_DIR=\"/usr/local/etc/pulse\" -DPA_BINARY=\"/usr/local/bin/pulseaudio\" -DPA_SYSTEM_RUNTIME_PATH=\"/usr/local/var/run/pulse\" -DPA_SYSTEM_CONFIG_PATH=\"/usr/local/var/lib/pulse\" -DPA_SYSTEM_STATE_PATH=\"/usr/local/var/lib/pulse\" -DAO_REQUIRE_CAS -DPULSE_LOCALEDIR=\"/usr/local/share/locale\" -DPA_MACHINE_ID=\"/usr/local/var/lib/dbus/machine-id\" "-DDEBUG_TRAP=__asm__(\"int \$3\")" -g -O2 -Wall -W -Wextra -pedantic -pipe -Wno-long-long -Wvla -Wno-overlength-strings -Wconversion -Wundef -Wformat -Wlogical-op -Wpacked -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wdeclaration-after-statement -Wfloat-equal -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-noreturn -Wshadow -Wendif-labels -Wpointer-arith -Wcast-align -Wwrite-strings -Wno-unused-parameter -ffast-math -MT module_jack_sink_la-module-jack-sink.lo -MD -MP -MF .deps/module_jack_sink_la-module-jack-sink.Tpo -c modules/module-jack-sink.c  -fPIC -DPIC -o .libs/module_jack_sink_la-module-jack-sink.o
modules/module-jack-sink.c:35:23: error: jack/jack.h: No such file or directory
modules/module-jack-sink.c:86: error: expected specifier-qualifier-list before &#8216;jack_port_t&#8217;
modules/module-jack-sink.c: In function &#8216;sink_process_msg&#8217;:
modules/module-jack-sink.c:138: error: &#8216;struct userdata&#8217; has no member named &#8216;buffer&#8217;
modules/module-jack-sink.c:152: error: &#8216;struct userdata&#8217; has no member named &#8216;buffer&#8217;
modules/module-jack-sink.c:155: error: &#8216;struct userdata&#8217; has no member named &#8216;frames_in_buffer&#8217;
modules/module-jack-sink.c:155: error: &#8216;jack_nframes_t&#8217; undeclared (first use in this function)
modules/module-jack-sink.c:155: error: (Each undeclared identifier is reported only once
modules/module-jack-sink.c:155: error: for each function it appears in.)
modules/module-jack-sink.c:155: error: expected &#8216;;&#8217; before &#8216;offset&#8217;
modules/module-jack-sink.c:156: error: &#8216;struct userdata&#8217; has no member named &#8216;saved_frame_time&#8217;
modules/module-jack-sink.c:156: error: expected expression before &#8216;)&#8217; token
modules/module-jack-sink.c:157: error: &#8216;struct userdata&#8217; has no member named &#8216;saved_frame_time_valid&#8217;
modules/module-jack-sink.c:162: error: &#8216;struct userdata&#8217; has no member named &#8216;thread_mq&#8217;
modules/module-jack-sink.c:166: error: expected &#8216;;&#8217; before &#8216;l&#8217;
modules/module-jack-sink.c:167: warning: ISO C90 forbids mixed declarations and code
modules/module-jack-sink.c:170: error: &#8216;l&#8217; undeclared (first use in this function)
modules/module-jack-sink.c:170: warning: implicit declaration of function &#8216;jack_port_get_total_latency&#8217;
modules/module-jack-sink.c:170: error: &#8216;struct userdata&#8217; has no member named &#8216;client&#8217;
modules/module-jack-sink.c:170: error: &#8216;struct userdata&#8217; has no member named &#8216;port&#8217;
modules/module-jack-sink.c:170: error: &#8216;struct userdata&#8217; has no member named &#8216;frames_in_buffer&#8217;
modules/module-jack-sink.c:172: error: &#8216;struct userdata&#8217; has no member named &#8216;saved_frame_time_valid&#8217;
modules/module-jack-sink.c:176: error: &#8216;ft&#8217; undeclared (first use in this function)
modules/module-jack-sink.c:176: warning: implicit declaration of function &#8216;jack_frame_time&#8217;
modules/module-jack-sink.c:176: error: &#8216;struct userdata&#8217; has no member named &#8216;client&#8217;
modules/module-jack-sink.c:177: error: &#8216;d&#8217; undeclared (first use in this function)
modules/module-jack-sink.c:177: error: &#8216;struct userdata&#8217; has no member named &#8216;saved_frame_time&#8217;
modules/module-jack-sink.c:177: error: &#8216;struct userdata&#8217; has no member named &#8216;saved_frame_time&#8217;
modules/module-jack-sink.c: At top level:
modules/module-jack-sink.c:192: error: expected &#8216;)&#8217; before &#8216;nframes&#8217;
modules/module-jack-sink.c: In function &#8216;thread_func&#8217;:
modules/module-jack-sink.c:219: error: &#8216;struct userdata&#8217; has no member named &#8216;thread_mq&#8217;
modules/module-jack-sink.c:220: error: &#8216;struct userdata&#8217; has no member named &#8216;rtpoll&#8217;
modules/module-jack-sink.c:229: error: &#8216;struct userdata&#8217; has no member named &#8216;rtpoll&#8217;
modules/module-jack-sink.c:239: error: &#8216;struct userdata&#8217; has no member named &#8216;thread_mq&#8217;
modules/module-jack-sink.c:240: error: &#8216;struct userdata&#8217; has no member named &#8216;thread_mq&#8217;
modules/module-jack-sink.c: In function &#8216;jack_shutdown&#8217;:
modules/module-jack-sink.c:267: error: &#8216;struct userdata&#8217; has no member named &#8216;jack_msgq&#8217;
modules/module-jack-sink.c: In function &#8216;module_jack_sink_LTX_pa__init&#8217;:
modules/module-jack-sink.c:275: error: &#8216;jack_status_t&#8217; undeclared (first use in this function)
modules/module-jack-sink.c:275: error: expected &#8216;;&#8217; before &#8216;status&#8217;
modules/module-jack-sink.c:276: warning: ISO C90 forbids mixed declarations and code
modules/module-jack-sink.c:285: warning: implicit declaration of function &#8216;jack_set_error_function&#8217;
modules/module-jack-sink.c:304: error: &#8216;struct userdata&#8217; has no member named &#8216;saved_frame_time_valid&#8217;
modules/module-jack-sink.c:305: error: &#8216;struct userdata&#8217; has no member named &#8216;rtpoll&#8217;
modules/module-jack-sink.c:306: error: &#8216;struct userdata&#8217; has no member named &#8216;thread_mq&#8217;
modules/module-jack-sink.c:306: error: &#8216;struct userdata&#8217; has no member named &#8216;rtpoll&#8217;
modules/module-jack-sink.c:309: error: &#8216;struct userdata&#8217; has no member named &#8216;jack_msgq&#8217;
modules/module-jack-sink.c:316: error: &#8216;struct userdata&#8217; has no member named &#8216;rtpoll_item&#8217;
modules/module-jack-sink.c:316: error: &#8216;struct userdata&#8217; has no member named &#8216;rtpoll&#8217;
modules/module-jack-sink.c:316: error: &#8216;struct userdata&#8217; has no member named &#8216;jack_msgq&#8217;
modules/module-jack-sink.c:318: error: &#8216;struct userdata&#8217; has no member named &#8216;client&#8217;
modules/module-jack-sink.c:318: warning: implicit declaration of function &#8216;jack_client_open&#8217;
modules/module-jack-sink.c:318: error: &#8216;JackServerName&#8217; undeclared (first use in this function)
modules/module-jack-sink.c:318: error: &#8216;JackNullOption&#8217; undeclared (first use in this function)
modules/module-jack-sink.c:318: error: &#8216;status&#8217; undeclared (first use in this function)
modules/module-jack-sink.c:323: warning: implicit declaration of function &#8216;jack_get_ports&#8217;
modules/module-jack-sink.c:323: error: &#8216;struct userdata&#8217; has no member named &#8216;client&#8217;
modules/module-jack-sink.c:323: error: &#8216;JackPortIsPhysical&#8217; undeclared (first use in this function)
modules/module-jack-sink.c:323: error: &#8216;JackPortIsInput&#8217; undeclared (first use in this function)
modules/module-jack-sink.c:323: warning: assignment makes pointer from integer without a cast
modules/module-jack-sink.c:343: warning: implicit declaration of function &#8216;jack_get_client_name&#8217;
modules/module-jack-sink.c:343: error: &#8216;struct userdata&#8217; has no member named &#8216;client&#8217;
modules/module-jack-sink.c:343: warning: format &#8216;%s&#8217; expects type &#8216;char *&#8217;, but argument 6 has type &#8216;int&#8217;
modules/module-jack-sink.c:346: warning: implicit declaration of function &#8216;jack_get_sample_rate&#8217;
modules/module-jack-sink.c:346: error: &#8216;struct userdata&#8217; has no member named &#8216;client&#8217;
modules/module-jack-sink.c:346: warning: conversion to &#8216;uint32_t&#8217; from &#8216;int&#8217; may change the sign of the result
modules/module-jack-sink.c:352: error: &#8216;struct userdata&#8217; has no member named &#8216;port&#8217;
modules/module-jack-sink.c:352: warning: implicit declaration of function &#8216;jack_port_register&#8217;
modules/module-jack-sink.c:352: error: &#8216;struct userdata&#8217; has no member named &#8216;client&#8217;
modules/module-jack-sink.c:352: error: &#8216;JACK_DEFAULT_AUDIO_TYPE&#8217; undeclared (first use in this function)
modules/module-jack-sink.c:352: error: &#8216;JackPortIsOutput&#8217; undeclared (first use in this function)
modules/module-jack-sink.c:352: error: &#8216;JackPortIsTerminal&#8217; undeclared (first use in this function)
modules/module-jack-sink.c:367: error: &#8216;struct userdata&#8217; has no member named &#8216;client&#8217;
modules/module-jack-sink.c:367: warning: format &#8216;%s&#8217; expects type &#8216;char *&#8217;, but argument 4 has type &#8216;int&#8217;
modules/module-jack-sink.c:368: error: &#8216;struct userdata&#8217; has no member named &#8216;client&#8217;
modules/module-jack-sink.c:368: warning: passing argument 3 of &#8216;pa_proplist_sets&#8217; makes pointer from integer without a cast
modules/module-jack-sink.c:381: error: &#8216;struct userdata&#8217; has no member named &#8216;thread_mq&#8217;
modules/module-jack-sink.c:382: error: &#8216;struct userdata&#8217; has no member named &#8216;rtpoll&#8217;
modules/module-jack-sink.c:384: warning: implicit declaration of function &#8216;jack_set_process_callback&#8217;
modules/module-jack-sink.c:384: error: &#8216;struct userdata&#8217; has no member named &#8216;client&#8217;
modules/module-jack-sink.c:384: error: &#8216;jack_process&#8217; undeclared (first use in this function)
modules/module-jack-sink.c:385: warning: implicit declaration of function &#8216;jack_on_shutdown&#8217;
modules/module-jack-sink.c:385: error: &#8216;struct userdata&#8217; has no member named &#8216;client&#8217;
modules/module-jack-sink.c:386: warning: implicit declaration of function &#8216;jack_set_thread_init_callback&#8217;
modules/module-jack-sink.c:386: error: &#8216;struct userdata&#8217; has no member named &#8216;client&#8217;
modules/module-jack-sink.c:388: error: &#8216;struct userdata&#8217; has no member named &#8216;thread&#8217;
modules/module-jack-sink.c:393: warning: implicit declaration of function &#8216;jack_activate&#8217;
modules/module-jack-sink.c:393: error: &#8216;struct userdata&#8217; has no member named &#8216;client&#8217;
modules/module-jack-sink.c:406: warning: implicit declaration of function &#8216;jack_port_name&#8217;
modules/module-jack-sink.c:406: error: &#8216;struct userdata&#8217; has no member named &#8216;port&#8217;
modules/module-jack-sink.c:406: warning: format &#8216;%s&#8217; expects type &#8216;char *&#8217;, but argument 6 has type &#8216;int&#8217;
modules/module-jack-sink.c:408: warning: implicit declaration of function &#8216;jack_connect&#8217;
modules/module-jack-sink.c:408: error: &#8216;struct userdata&#8217; has no member named &#8216;client&#8217;
modules/module-jack-sink.c:408: error: &#8216;struct userdata&#8217; has no member named &#8216;port&#8217;
modules/module-jack-sink.c:409: error: &#8216;struct userdata&#8217; has no member named &#8216;port&#8217;
modules/module-jack-sink.c:409: warning: format &#8216;%s&#8217; expects type &#8216;char *&#8217;, but argument 6 has type &#8216;int&#8217;
modules/module-jack-sink.c: In function &#8216;module_jack_sink_LTX_pa__done&#8217;:
modules/module-jack-sink.c:441: error: &#8216;struct userdata&#8217; has no member named &#8216;client&#8217;
modules/module-jack-sink.c:442: warning: implicit declaration of function &#8216;jack_client_close&#8217;
modules/module-jack-sink.c:442: error: &#8216;struct userdata&#8217; has no member named &#8216;client&#8217;
modules/module-jack-sink.c:447: error: &#8216;struct userdata&#8217; has no member named &#8216;thread&#8217;
modules/module-jack-sink.c:448: error: &#8216;struct userdata&#8217; has no member named &#8216;thread_mq&#8217;
modules/module-jack-sink.c:449: error: &#8216;struct userdata&#8217; has no member named &#8216;thread&#8217;
modules/module-jack-sink.c:452: error: &#8216;struct userdata&#8217; has no member named &#8216;thread_mq&#8217;
modules/module-jack-sink.c:457: error: &#8216;struct userdata&#8217; has no member named &#8216;rtpoll_item&#8217;
modules/module-jack-sink.c:458: error: &#8216;struct userdata&#8217; has no member named &#8216;rtpoll_item&#8217;
modules/module-jack-sink.c:460: error: &#8216;struct userdata&#8217; has no member named &#8216;jack_msgq&#8217;
modules/module-jack-sink.c:461: error: &#8216;struct userdata&#8217; has no member named &#8216;jack_msgq&#8217;
modules/module-jack-sink.c:463: error: &#8216;struct userdata&#8217; has no member named &#8216;rtpoll&#8217;
modules/module-jack-sink.c:464: error: &#8216;struct userdata&#8217; has no member named &#8216;rtpoll&#8217;
make: *** [module_jack_sink_la-module-jack-sink.lo] Error 1


```and its 9.14 pulseaudio source

cant run pavucontrol : showing error

```
 error while loading shared libraries: libpulsecommon-0.9.15.so: cannot open shared object file: No such file or directory 
```

help pls

---

### Post by mocha on 2009-06-01
Looks like you're missing some jack dev libraries.  Did you do the apt-get install build-dep pulseaudio?  Look in synaptic for "jack dev", try intalling some of the dev libraries and run make again.

In general, when you see a message like "modules/module-jack-sink.c:35:23: error: jack/jack.h: No such file or directory" it means you are missing some dev libs.  There is a nice program called "apt-file" which you can use to find out what package the libs are located in.  You run it like "apt-file search jack.h"  When you first install apt-file you have to do "apt-file update" to download the metadata.

---

### Post by raboofje on 2009-06-01
> **mocha said:**
> Looks like you're missing some jack dev libraries.  Did you do the apt-get install build-dep pulseaudio?  Look in synaptic for "jack dev", try intalling some of the dev libraries and run make again

Yeah - normally 'apt-get build-dep pulseaudio' would fetch the needed dev packages, but since jack is normally disabled in ubuntu it doesn't fetch libjack-dev. I added it to the instructions.

---

### Post by crazybuntu on 2009-06-01
ok i can make the module-jack-sink.so now i copied it to the usr/lib/pulse folder

but when i start jack server, it says suspending pulse audio and sound doesnt work .. 

pavucontrol doesnt work too, says connection failed ??

---

### Post by mocha on 2009-06-02
> **crazybuntu said:**
> ok i can make the module-jack-sink.so now i copied it to the usr/lib/pulse folder

but when i start jack server, it says suspending pulse audio and sound doesnt work .. 

pavucontrol doesnt work too, says connection failed ??

Did you setup Jack properly?  Did you make a script to load the jack-pulse module and then call the script in the Jack startup command box?

---

### Post by crazybuntu on 2009-06-02
hmm i reinstalled pulseaudio 9.15 from [http://ppa.launchpad.net/themuso/ppa/ubuntu](http://ppa.launchpad.net/themuso/ppa/ubuntu) , it works , pavucontrol also works 

now when i start jack server , i cannot play audio from rhythmbox, before i installed pulseaudio it works fine.

and how do i setup jack with pulseaudio properly ??? 

Lets get couple things straight here :

1. after doing 

[LIST]
[*]apt-get build-dep pulseaudio
[*]apt-get install libjack-dev
[*]apt-get source pulseaudio
[*]cd pulseaudio_<tab>
[*]./configure --with-jack
[*]cd src
[*]make module-jack-sink.la
[*]cp .libs/module-jack-sink.so /usr/lib/pulse-0.9/modules
[/LIST]
Do i have to install pulseaudio ? sudo apt-get pulseaudio   ?

2. so i have done the above and got module-jack-sink.so , but there is no  /usr/lib/pulse-0.9/modules folder, so i created one . Is this ok?

3. do i need to install pulseaudio dev chooser ?? well i did and the pulsaudio manger says  server versio 0.9.15 but client linked to library 9.15, compiled with library 9.14

4. create a jackd.pa with pretty much only module-jack-sink = ??? how ???

---

### Post by mocha on 2009-06-05
You need to have pulseaudio installed already before you begin.  I would also install all the GUI apps for it, just search synaptic for pulseaudio.  Don't bother with 0.9.15, the 0.9.14 version works just fine.

It kind of sounds like you've done a lot of stuff that you might not recover from now.  The basic procedure is install pulseaudio, install the GUI apps, install the build dependancies for pulse and jack, get the repo version of the pulse source, configure it to make the jack module, make it, copy the jack module to the pulse lib directory.

I think you might have different versions of stuff floating around now.  If you installed 0.9.15 pulse then you need the 0.9.15 source to build the jack module.

I played with 0.9.15 for awhile from that same repo and went back to 0.9.14, so it's possible to fix this, just remove the PPA source line, then go into synaptic and downgrade all the stuff it upgraded.

---

### Post by crazybuntu on 2009-06-13
i removed pulseaudio and libpulse , now its back nto 9.14

---

### Post by crazybuntu on 2009-06-13
> **mocha said:**
> Did you setup Jack properly?  Did you make a script to load the jack-pulse module and then call the script in the Jack startup command box?

how do i make this script i am totally blind ? theres no mentioning of this in the first post ??

what i did was i edited the default.pa like this 
[http://wiki.archlinux.org/index.php/PulseAudio#Pulseaudio_through_JACK](http://wiki.archlinux.org/index.php/PulseAudio#Pulseaudio_through_JACK)

and when i start pulse audio volume control = says connection refused 
via terminal :
E: socket-client.c: socket(): Address family not supported by protocol
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.

in pulse audio manager, i cant connect to pulse audio server

that didnt work... so i am back To the beginning now with pulseaudio 9.14 and JACK with DEFAULT settings, and the module-jack-sink.so in the /usr/lib/pulse-0.9/modules folder

---

### Post by lgnokia on 2009-06-13
i have alreay ubuntu cd from uk.

---

### Post by crazybuntu on 2009-06-13
i followed this tutorial [http://kishalmi.net/cms/node/53](http://kishalmi.net/cms/node/53)

and downloaded the [http://ftp.au.debian.org/debian/pool/main/p/pulseaudio/pulseaudio-module-jack_0.9.10-3_i386.deb](http://ftp.au.debian.org/debian/pool/main/p/pulseaudio/pulseaudio-module-jack_0.9.10-3_i386.deb) debian package of module jack

then i extract and copide module-jack-sink and source to /usr/lib/pulse-0.9/modules

when i try to run pulsaudio volume control / connect to server its says CONNECTION REFUSED ?????

---

### Post by crazybuntu on 2009-06-13
WOHOO IT WORKS !! 

The problem was probably there was no module-jack-source, so i make the module from source like the sink module

```
make module-jack-sink.la
cp .libs/module-jack-sink.so /usr/lib/pulse-0.9/modules

```
and 

```
make module-jack-source.la
cp .libs/module-jack-source.so /usr/lib/pulse-0.9/modules
```

edited /etc/pulse/default.pa :
```

# Jack modules
load-module module-jack-sink channels=2
load-module module-jack-source channels=2

### comment this one out, so it doesn't load alsa/oss modules
#.ifexists module-hal-detect.so
#load-module module-hal-detect
#.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
#load-module module-detect
#.endif

### Make some devices default
set-default-sink jack_out
set-default-source jack_in


```

THATS IT

now kill pulseaudio if it is running, and start qtjackctl from menu , and it will show connection of pulseaudio sink and source,
start any program including firefox / rhythm box it will streamed into jack from pulseaudio 

too bad, using gtkrecordmydesktop, i got choppy recording when in fullscreen under my core duo 1.7 , 1 GB laptop, probably because of Onboard Intel GMA 945 Video card. 

But its quite decent if i record only a part of the screen.

---

### Post by mocha on 2009-06-14
I'm glad it's working for you, however you don't need the jack source module, but hey, if it works for you then just leave it alone.  The "script" I keep talking about loads the jack modules "on demand" when the Jack server is started, instead of always loaded as in the default.pa method.

The script for your case would be:

```
#!/bin/bash

pactl load-module module-jack-sink
pactl load-module module-jack-source

```

In the JACK control options just point to this script as the "Execute script after startup" and comment out the lines in default.pa.  I'm sure you understand now with all the experimenting you've been doing, the script loads the pulse-jack modules after the Jack server is started instead of loading them though the default.pa file which will most likely lead to other annoying problems.  However, my number one rule in linux is if it's working for you then just leave it alone.

---

### Post by crazybuntu on 2009-06-16
Script didnt work , resulting in
connection refused when opening pulseaudio volume control
and pusleaudio not showing in jack ?

Anyways, i got another error without using the script above, when i am using pulseaudio with jack, after around 10 minutes, the audio server crashes, showing connection refused and jack is stops, if i run it in terminal, it shows this error :

```

ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 3 periods for playback
W: module-jack-sink.c: JACK error >cannot read server event (Success)<
W: module-jack-sink.c: JACK error >cannot continue execution of the processing graph (Broken pipe)<
W: module-jack-sink.c: JACK error >zombified - calling shutdown handler<
W: module-jack-sink.c: JACK error >cannot send request type 7 to server<
W: module-jack-sink.c: JACK error >cannot read result for request type 7 from server (Broken pipe)<
W: module-jack-sink.c: JACK error >cannot continue execution of the processing graph (Broken pipe)<
W: module-jack-sink.c: JACK error >zombified - calling shutdown handler<

``` 
and the audio in firefox is turned off after it crashes

i have to restart pulseaudio and firefox again in terminal and it will work again..

---

### Post by crazybuntu on 2009-06-18
turned out the script missed the first line , it should be like this : 
```

#load pulseaudio jack modules
#!/bin/bash

pactl load-module module-jack-sink
pactl load-module module-jack-source

```

To avoid crashing of pulseaudio when stopping jack,do this :

**Closing jack**
If you close jack before you stop or close any application playing through the Pulse Audio jack sink, Pulse Audio may crash and need to be restarted if you do not disconnect the pulseaudio sink and source before closing jack. You can go to connections and choose disconnect all before stopping jack and your applications should not crash when you stop jack.

---

### Post by mocha on 2009-06-18
Sounds like you got it figured out.  You should also add the "channels=2" bit to the script when you load the modules via script.

---

### Post by ecullerton on 2009-06-25
It looks like you guys have some good experience with routing pulseaudio through jack, so I'd like to ask for some help!

I'm running Ubuntu Studio Hardy.  I used the guide posted here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)
(its the 10,000 page guide)


My exact steps were:

1. Download and install the amd64 version pulseaudio-module-jack from the lenny package site here:

[http://packages.debian.org/lenny/sound/pulseaudio-module-jack](http://packages.debian.org/lenny/sound/pulseaudio-module-jack)

2. Create the script to execute after startup to load the module.

3. Make the script executable.


When I start jack, the module does not load.

I tried running the code:
$ pactl load-module module-jack-sink

in a terminal after jack was started and I get the error message that the module initialization failed

I don't want to push any further without help because I know I can do big damage if I'm not careful.


A bit more info about my system:

64 bit version
using the latest svn of jackmp
using the latest svn of ffado
focusrite pro10 audio interface


Thanks!

---

### Post by raboofje on 2009-06-25
> **ecullerton said:**
> 1. Download and install the amd64 version pulseaudio-module-jack from the lenny package site here:

[http://packages.debian.org/lenny/sound/pulseaudio-module-jack](http://packages.debian.org/lenny/sound/pulseaudio-module-jack)


Opinions differ, but I think this is a bad idea and you'd be better off 
getting the sources of your pulseaudio version with 'apt-get source' and compile the modules from those.

> I tried running the code:
$ pactl load-module module-jack-sink

in a terminal after jack was started and I get the error message that the module initialization failed

Is that the exact error message?

Which version of the pulseaudio modules do you have installed?

Which version of pulseaudio-module-jack from Debian did you install?

---

### Post by markbuntu on 2009-06-25
> **ecullerton said:**
> It looks like you guys have some good experience with routing pulseaudio through jack, so I'd like to ask for some help!

I'm running Ubuntu Studio Hardy.  I used the guide posted here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)
(its the 10,000 page guide)


My exact steps were:

1. Download and install the amd64 version pulseaudio-module-jack from the lenny package site here:

[http://packages.debian.org/lenny/sound/pulseaudio-module-jack](http://packages.debian.org/lenny/sound/pulseaudio-module-jack)

2. Create the script to execute after startup to load the module.

3. Make the script executable.


When I start jack, the module does not load.

I tried running the code:
$ pactl load-module module-jack-sink

in a terminal after jack was started and I get the error message that the module initialization failed

I don't want to push any further without help because I know I can do big damage if I'm not careful.


A bit more info about my system:

64 bit version
using the latest svn of jackmp
using the latest svn of ffado
focusrite pro10 audio interface


Thanks!

You should check that jack is not starting with pasuspender which will suspend pulseaudio causing the modules to not get loaded. I saw this somewhere a long time ago and it might have been in hardy.

It is also possible that the modules in pa 0.9,.10 are not compatible with the latest jack but I have heard nothing either way about that. Not a lot of people try this.

---

### Post by ecullerton on 2009-06-25
Thanks for the replies...

running jack with verbos messages I get this error:

Jack: JackRequest::ClientOpen
Jack: JackSocketServerChannel::ClientAdd
22:18:57.050 JACK connection graph change.
Jack: JackEngine::ClientOpen: name = PulseAudio JACK Sink 
Jack: JackEngine::AllocateRefNum ref = 3
Jack: JackFifo::Allocate name = /dev/shm/jack_fifo.1000_default_PulseAudio JACK Sink
Jack: JackSocketNotifyChannel::Open name = PulseAudio JACK Sink
Jack: Connect: addr.sun_path /dev/shm/jack_PulseAudio JACK Sink_1000_0
Jack: JackShmMem::new index = 3 attached = 9cd07000 size = 120 
Jack: JackExternalClient::Open name = PulseAudio JACK Sink index = 3 base = 9cd07000
Jack: JackProcessSync::TimedWait time out = 5000000
Jack: JackProcessSync::TimedWait finished delta = 1783.0
Jack: JackEngine::NotifyAddClient: name = PulseAudio JACK Sink
Jack: JackExternalClient::ClientNotify ref = 0 name = system notify = 0
Jack: JackExternalClient::ClientNotify ref = 1 name = freewheel notify = 0
Jack: JackExternalClient::ClientNotify ref = 3 name = PulseAudio JACK Sink notify = 0
Jack: JackClient::AddClient name = PulseAudio JACK Sink, ref = 3 
Jack: JackFifo::ConnectAux name = /dev/shm/jack_fifo.1000_default_PulseAudio JACK Sink
Jack: JackClient::kAddClient fName = qjackctl name = PulseAudio JACK Sink
Jack: JackExternalClient::ClientNotify ref = 2 name = qjackctl notify = 0
Jack: JackExternalClient::ClientNotify ref = 3 name = PulseAudio JACK Sink notify = 0
Jack: JackExternalClient::ClientNotify ref = 3 name = PulseAudio JACK Sink notify = 0
Jack: JackSocketServerChannel::BuildPoolTable size = 4
Jack: fSocketTable i = 1 fd = 5
Jack: fSocketTable i = 2 fd = 18
Jack: fSocketTable i = 3 fd = 21
Jack: fPollTable i = 1 fd = 5
Jack: fPollTable i = 2 fd = 18
Jack: fPollTable i = 3 fd = 21
Jack: JackRequest::ClientClose
Jack: JackEngine::ClientCloseAux ref = 3
Jack: JackGraphManager::RemoveAllPorts ref = 3
Jack: JackProcessSync::TimedWait time out = 10000000
Jack: JackProcessSync::TimedWait finished delta = 403.0
Jack: JackExternalClient::ClientNotify ref = 3 name = PulseAudio JACK Sink notify = 1
Jack: JackClient::RemoveClient name = PulseAudio JACK Sink, ref = 3 
Jack: JackFifo::Disconnect /dev/shm/jack_fifo.1000_default_PulseAudio JACK Sink
Jack: JackClient::kRemoveClient fName = qjackctl name = PulseAudio JACK Sink
Jack: JackFifo::Destroy name = /dev/shm/jack_fifo.1000_default_PulseAudio JACK Sink
Jack: JackSocketNotifyChannel::Close
Jack: JackClientSocket::Close
Jack: JackShmMem::delete size = 0 index = 3
Jack: JackSocketServerChannel::ClientRemove ref = 3
Jack: JackClientSocket::Close
Jack: JackSocketServerChannel::BuildPoolTable size = 3
Jack: fSocketTable i = 1 fd = 5
Jack: fSocketTable i = 2 fd = 18
Jack: fPollTable i = 1 fd = 5
Jack: JackRequest::Notification
Jack: JackEngine::NotifyClients: no callback for event = 4
Jack: JackEngine::NotifyClients: no callback for event = 4
Jack: JackExternalClient::ClientNotify ref = 2 name = qjackctl notify = 4
Jack: fPollTable i = 2 fd = 18
Jack: JackClient::kGraphOrderCallback


Pulseaudio is still running in the background after I start jack, so pasuspender is not invoked.


I checked the versions in the synamtic package manager:

pulseaudio             0.9.10-1ubuntu
pulseaudio-module-jack 0.9.10-3

Does it matter that the versions are different?

Thanks

---

### Post by markbuntu on 2009-06-26
It looks like the connection is timing out. Do you have anything using pulse. if not pulse may go to sleep. I usually have an app playing in pulseaudio when I start jack and move it to the jack sink after I start jack. You need to make sure the app is not using the hardware that jack wants.

Did you adjust the timeout in the jack control setup to 1000 or more? 
The default 500 causes jack to timeout the pulse connection.

---

### Post by ecullerton on 2009-06-27
I had the timeout setting to 5000, and I tried 10000 too with no luck.

I also added the lenny repository to my sources list and upgraded all my pulseaudio to the lenny version 0.9.10-3.  Still get the same errors.

To test your procedure, I started some music in rhythmbox, then started jack.  Again, same error.  I know they are not competing for the same hardware because I'm using a firewire driver in jack.

---

### Post by Capoeira on 2009-06-27
hi guys, there is another way wich is easyer. with alsa-jack. see here: [http://linuxmusicians.com/viewtopic.php?f=4&t=1022&p=6882&hilit=alsa+jack#p6882](http://linuxmusicians.com/viewtopic.php?f=4&t=1022&p=6882&hilit=alsa+jack#p6882)

---

### Post by raboofje on 2009-06-28
> **Capoeira said:**
> hi guys, there is another way wich is easyer. with alsa-jack. see here: [http://linuxmusicians.com/viewtopic.php?f=4&t=1022&p=6882&hilit=alsa+jack#p6882](http://linuxmusicians.com/viewtopic.php?f=4&t=1022&p=6882&hilit=alsa+jack#p6882)

Unfortunately, Ubuntu doesn't include the alsa-jack module for the same reason it doesn't include the pulseaudio-jack modules: alsa is in main, while jack is no longer there.

See [https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/197957](https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/197957)

---

### Post by Capoeira on 2009-06-28
> **raboofje said:**
> Unfortunately, Ubuntu doesn't include the alsa-jack module for the same reason it doesn't include the pulseaudio-jack modules: alsa is in main, while jack is no longer there.

See [https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/197957](https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/197957)

ahh ok, it is in 64-studio 3.0 beta repros though (hardy)

---

### Post by myquidproquo on 2009-10-26
Hi everyone!
This topic has been very helpful for me but I am still having a problem.

When I start my pc I don't have jack running and sound is working fine.
Then I start jack and I have the "PulseAudio jack sink" connected to "system" in jack. I start Rhythmbox and it can't play sound. It just stays there at 0m00s of any song and jack gives me some xruns errors...

I feel that I'm almost there, but there's something missing :)
Any suggestion? 

Thanks in advance.

---

### Post by Cavsfan on 2009-11-30
I give up! ](*,)I have tried and tried for (more than) several days and still jack gets an error and gtk-recordmydesktop gets an error. I am just tired of trying! 
Something should not be this freaking difficult! But, seeing the Youtube videos of it being done aggravates me to no end! I know I am not that dumb, 
but apparently I am not smart enough to figure out how to make a simple video showing off my desktop with some music playing all at the same time.
My head hurts from trying and trying this and then that....
  Every timeI thought I was getting closer to solving this puzzle, I was disappointed again!
I will record my desktop without sound and use ffmpeg to put that and an MP3 together I guess. I will give credits for the MP3 though overstream.net.
](*,)

This linux/ubuntu etc. is definitely not for just anyone...
I upgraded to 9.10, but thought that 9.04 had a better chance of producing a video with sound for youtube. So, I went back.

I am sorry if I sound really frustrated, but frustrated does not quite communicate the sheer feeling of total ignorance I am feeling right now.
I feel dumber than a rock!
I know that my sig. says it doesn't last forever, but maybe in this case it does... ](*,)

---

### Post by mocha on 2009-12-01
> **Cavsfan said:**
> I give up! ](*,)I have tried and tried for (more than) several days and still jack gets an error and gtk-recordmydesktop gets an error. I am just tired of trying!

Since I upgraded to Karmic recently and now I saw your post I wanted to verify the problem, and you are correct the Jaunty procedure no longer works.  There are some new issues in Karmic which cause us to make workarounds.

First, download this [https://launchpad.net/~motin/+archive/until-jack-is-included-in-main/+build/1316208/+files/pulseaudio-module-jack_0.9.19-0ubuntu4+withjack0_i386.deb]("https://launchpad.net/~motin/+archive/until-jack-is-included-in-main/+build/1316208/+files/pulseaudio-module-jack_0.9.19-0ubuntu4+withjack0_i386.deb").  That package contains a precompiled module-jack-sink.so for Karmic.  To prevent having to install a bunch of packages from that PPA and munging your system, open the deb in the archive manager and find and extract the module-jack-sink.so file, as root copy it to /usr/lib/pulse-0.9.19/modules then run "sudo ldconfig".  That should take care of installing the module and registering it.

Second, unfortunately it appears that Ubuntu built the Karmic version of recordmydesktop without JACK support.  You can confirm this suspicion by running "recordmydesktop --print-config" and you'll see it says Jack Disabled.  So you're going to have to grab the source (apt-get source recordmydesktop), extract and move the directory into /usr/src, make sure you have all the jack dev packages installed in synaptic, then as root execute:

```
./configure --prefix=/usr --enable-jack=yes LIBS=-ljack CFLAGS=-DHAVE_LIBJACK
make
make install
```

Run "recordmydesktop --print-config" again and it should say enabled.  

After you perform these workarounds the existing functional procedures with gtk-recordmydesktop, JACK, etc, is the same as before.

I dedicated a proof-of-concept video to you!  [http://www.youtube.com/watch?v=_2ij3Gm7bgA]("http://www.youtube.com/watch?v=_2ij3Gm7bgA")

---

### Post by VertexPusher on 2009-12-01
Why don't you guys use the ALSA loopback device?

Just load the module, make "Loopback" the default soundcard, launch Jack and start routing.

:popcorn:

---

### Post by mocha on 2009-12-01
> **VertexPusher said:**
> Why don't you guys use the ALSA loopback device?

Just load the module, make "Loopback" the default soundcard, launch Jack and start routing.

:popcorn:

Does that allow you to hear what's playing while you're recording?  Jack is far superior to every other solution I've tried.  I've seen people say to use pulseaudio with recordmydesktop, but that's a bunch of BS because if you're doing a capture of video the audio will always go out of sync.  Using Jack is the only way to keep audio in sync, plus it plays nice with pulseaudio, and you can hear what is playing during the capture.  In essence, it allows you to compute with a linux desktop as you would expect in 2009, not 1999.

---

### Post by Cavsfan on 2009-12-01
> **mocha said:**
> Since I upgraded to Karmic recently and now I saw your post I wanted to verify the problem, and you are correct the Jaunty procedure no longer works.  There are some new issues in Karmic which cause us to make workarounds.

First, download this [https://launchpad.net/~motin/+archive/until-jack-is-included-in-main/+build/1316208/+files/pulseaudio-module-jack_0.9.19-0ubuntu4+withjack0_i386.deb]("https://launchpad.net/%7Emotin/+archive/until-jack-is-included-in-main/+build/1316208/+files/pulseaudio-module-jack_0.9.19-0ubuntu4+withjack0_i386.deb").  That package contains a precompiled module-jack-sink.so for Karmic.  To prevent having to install a bunch of packages from that PPA and munging your system, open the deb in the archive manager and find and extract the module-jack-sink.so file, as root copy it to /usr/lib/pulse-0.9.19/modules then run "sudo ldconfig".  That should take care of installing the module and registering it.

Second, unfortunately it appears that Ubuntu built the Karmic version of recordmydesktop without JACK support.  You can confirm this suspicion by running "recordmydesktop --print-config" and you'll see it says Jack Disabled.  So you're going to have to grab the source (apt-get source recordmydesktop), extract and move the directory into /usr/src, make sure you have all the jack dev packages installed in synaptic, then as root execute:

```
./configure --prefix=/usr --enable-jack=yes LIBS=-ljack CFLAGS=-DHAVE_LIBJACK
make
make install
```Run "recordmydesktop --print-config" again and it should say enabled.  

After you perform these workarounds the existing functional procedures with gtk-recordmydesktop, JACK, etc, is the same as before.

I dedicated a proof-of-concept video to you!  [http://www.youtube.com/watch?v=_2ij3Gm7bgA](http://www.youtube.com/watch?v=_2ij3Gm7bgA)

Thanks mocha! I was so aggravated I had given up! :frown: And I never give up!
I almost immediately downloaded and installed Karmic Koala 64 bit.
I forgot to mention that I have 64 bit, so I believe that link to download the jack 
program won't work. I think that is what it said when I clicked on it.
Could you please give me the 64 bit link (I hope it doesn't make a 
difference!).
Thank you very much for taking the time and explaining it in a way I can understand!
I am learning and taking notes from all of this, so don't think you are wasting your time!
I am going to check out your video.
Thanks! :D

PS 
recordMyDesktop was compiled with the following options:

Jack Disabled
Default Audio Backend    :ALSA)

---

### Post by VertexPusher on 2009-12-01
> **mocha said:**
> Does that allow you to hear what's playing while you're recording?  Jack is far superior to every other solution I've tried.
Jack is great, but PulseAudio is crap. If you do the same things with ALSA, it will be more stable, latency will be lower, CPU load will be lower, and it will work with all applications that PulseAudio fails to support.

Here's a step-by-step example:

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
$
```

That's my soundcard, an off-the-shelf Intel HDA interface. Now see what happens:

```
$ sudo modprobe snd-aloop
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: Loopback [Loopback], device 0: Loopback PCM [Loopback PCM]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 3: Loopback [Loopback], device 1: Loopback PCM [Loopback PCM]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
$
```

There you can see the loopback soundcard which I'll make the default card for playback using this .asoundrc file in my home folder:

```
pcm.!default {
        type plug
        slave.pcm dmix:Loopback
}
```

Normally you would do this with a GUI such as asoundconf-gtk, but oh well, the Ubuntu devs failed to package that tool.

Next I'm gonna launch Jack with a config like this:

[[IMG]http://img214.imageshack.us/img214/1879/screenshotsetupjackaudi.png[/IMG]](http://img214.imageshack.us/i/screenshotsetupjackaudi.png/)
(Input device is "plughw:Loopback,1", output device is "plughw:Intel,0".)

Now I can start up Jack and set up connections. All the sounds from applications (media players, Flash plugin etc.) will be mixed and fed into Jack through the system capture ports. The system playback ports will be connected to my real soundcard, so I can monitor everything. If I want to, I can start up another instance of Jack and do the same thing in reverse. For example, I can route audio from my microphone through a pitch shifter into Skype or Second Life and then talk like Darth Vader or Mickey Mouse. That sort of stuff. On the application side, Jack is invisible because it's hidden between the loopback soundcard and the real one.

---

### Post by Cavsfan on 2009-12-01
VertexPusher,
Does this work with 64 bit?
Thanks!

---

### Post by VertexPusher on 2009-12-01
> **Cavsfan said:**
> Does this work with 64 bit?
Yes it does.

---

### Post by Cavsfan on 2009-12-02
VertexPusher,
The output from the 1st command "aplay -l" is identical to mine
with the minor exception that ALC889 was ALC888!
The exact same! However, when I execute the 2nd command it
could not find **snd-aloop** and gave an error saying that.
I looked for in on SPM and it was not there and also tried 
"sudo apt-get install snd-loop" but it displayed "E: Couldn't find package snd-aloop"
Any ideas? 
Thanks!

---

### Post by VertexPusher on 2009-12-02
linux-backports-modules-alsa-karmic-generic needs to be installed for this.

---

### Post by mocha on 2009-12-02
> **Cavsfan said:**
> I forgot to mention that I have 64 bit, so I believe that link to download the jack 
program won't work. I think that is what it said when I clicked on it.
Could you please give me the 64 bit link (I hope it doesn't make a 
difference!).

Actually it does make a difference.  In this case perhaps it's best for you to grab the pulseaudio source and compile it to obtain the jack sink module.  You can do this safely without installing anything.  Try in a temp directory, apt-get source pulseaudio, ./configure --enable-jack, make.  If you are successful the output of the configure script should tell you that jack will be enabled.  When it's done compiling, I believe in the src/.libs directory you'll find the module-jack-sink.so file.  Copy it into /usr/lib/pulse-0.9.19/modules (hopefully this is the same directory for 64 bit) then run "sudo ldconfig".

---

### Post by mocha on 2009-12-02
> **VertexPusher said:**
> Jack is great, but PulseAudio is crap. If you do the same things with ALSA, it will be more stable, latency will be lower, CPU load will be lower, and it will work with all applications that PulseAudio fails to support

This is a nice tutorial, thanks, however it will lead to no end of confusion for someone running a stock Karmic with pulseaudio, especially changing the .asoundrc file.  Besides if you have pulseaudio setup properly, which is pretty much the case now with Karmic, you don't need the alsa loopback since the same audio routings can be done without jack, and much easier though the pulse GUI tools.  As far as latency, I don't see these problems, perhaps it's dependant on hardware/CPU.  I've always captured videos with perfectly sync'd audio using the recordmydesktop-pulse-jack method.  All that said, pulseaudio is certainly not perfect in the way ubuntu sets it up.  Tinkering is part of the fun of using linux anyway.

---

### Post by Cavsfan on 2009-12-02
> **mocha said:**
> This is a nice tutorial, thanks, however it will lead to no end of confusion for someone running a stock Karmic with pulseaudio, especially changing the .asoundrc file.  Besides if you have pulseaudio setup properly, which is pretty much the case now with Karmic, you don't need the alsa loopback since the same audio routings can be done without jack, and much easier though the pulse GUI tools.  As far as latency, I don't see these problems, perhaps it's dependant on hardware/CPU.  I've always captured videos with perfectly sync'd audio using the recordmydesktop-pulse-jack method.  All that said, pulseaudio is certainly not perfect in the way ubuntu sets it up.  Tinkering is part of the fun of using linux anyway.

mocha, did you notice on one of my previous posts where I posted the output of 
"recordmydesktop --print-config"

Jack Disabled
Default Audio Backend    :[COLOR=Red]ALSA[/COLOR])

Will ALSA as default make any difference.
Thanks a lot!

---

### Post by Cavsfan on 2009-12-02
mocha,
I entered "apt-get source pulseaudio" and it gave this error:

```
Cavsfan@Cavsfan-desktop:~$ apt-get source pulseaudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
NOTICE: 'pulseaudio' packaging is maintained in the 'Bzr' version control system at:
http://launchpad.net/~ubuntu-core-dev/pulseaudio/ubuntu
Please use:
bzr get http://launchpad.net/~ubuntu-core-dev/pulseaudio/ubuntu
to retrieve the latest (possibly unreleased) updates to the package.
Skipping already downloaded file 'pulseaudio_0.9.19-0ubuntu4.dsc'
Skipping already downloaded file 'pulseaudio_0.9.19.orig.tar.gz'
Skipping already downloaded file 'pulseaudio_0.9.19-0ubuntu4.diff.gz'
Need to get 0B of source archives.
Skipping unpack of already unpacked source in pulseaudio-0.9.19
Cavsfan@Cavsfan-desktop:~$
```I was able to get it by a couple of initial errors, but don't have a clue about this. 
This may not be that bad, but I don't know. I don't know where these files are going.
Oh, and I did a fresh install a couple hours ago.

---

### Post by Cavsfan on 2009-12-02
VertexPusher,
I got by step 2 and the output looked identical to yours!
I just don't know about the .asoundrc file in my home directory.
Or how to do any of that.

I did find the file asoundrc in the folder usr/share/doc/libasound2/examples/asoundrc.txt.gz
But, didn't find the stuff in the 3rd step (box) of your post inside of it.
I am pretty noobile, so be aware of that. However I am learning fast!
I know windows, but that don't count I know!

Noobile, did I just invent that? LOL

---

### Post by VertexPusher on 2009-12-03
> **Cavsfan said:**
> I just don't know about the .asoundrc file in my home directory.
That's because it doesn't exist by default.

ALSA's main configuration file is /usr/share/alsa/alsa.conf. But you should not modify that. Every time an ALSA client application starts up, ALSA will read the .asoundrc file in your home folder if it exists. This way you can temporarily change ALSA's configuration without requiring root privileges.

There are tools to create .asoundrc files for specific purposes, but they are not bundled with Ubuntu. asoundconf was removed, probably to fool users into believing that PulseAudio is easier to configure. Now you need a text editor to edit .asoundrc manually.

The cool thing about ALSA is that you can create any number of PCM devices (i.e. named inputs and outputs for audio) and map them to the underlying hardware drivers in various ways. You can insert filters such as sample rate/format converters, stream mixers, channel routers, LADSPA effects etc. All this can be configured in .asoundrc.

---

### Post by Cavsfan on 2009-12-03
OK,
One more question: how would I reset the sounds back to normal after doing this?
Yesterday I did this command: 
[COLOR=Blue]sudo modprobe snd-aloop[/COLOR]
Then later I could not figure out how to get the sound to come out of my speakers.
Thinking it was something I borked, I re-installed.
It wasn't that bad as I have everything backed up and hadn't installed very much.
And how do you make a file that starts out with a period? (.asoundrc)
Does .asoundrc in my home folder only have to contain what you have in your example? 

```
pcm.!default {
        type plug
        slave.pcm dmix:Loopback
}
```Thanks!

---

### Post by Cavsfan on 2009-12-03
Update:
I entered "sudo modprobe snd-aloop" and then could not figure out a way to undo it.
I tried the -r option and it said snd-aloop was running.
So, I muddled around a bit and was going to install JACKD,
but typed in just "jack" in SPM and it pulled up alsaplayer-jack.
The notes on it said it works with jack, so I installed it.
My sound started working and I even played a song with RhythmBox!
Looked back at the alsa config (aplay -l) and it is still in loopback mode.

I think I'll try a video after lunch.

---

### Post by Cavsfan on 2009-12-03
](*,) Still can't get it done.

VertexPusher, 
when you mention Home directory, do you mean the dir that appears when you click on
Places > Home Folder? Or do you mean (once your there) you click on the little < to the left 
of your userid/name and go to the actual "Home" directory?

I hope you are referring to the 1st one because I managed to create a dir. called 
.asoundrc in the actual home directory (where the only other dir. is my userid/name) 
and I cannot figure out how to move the file I created named alsa.conf into it.

Is that all I lack - a dir named .asoundrc in my home folder with file called alsa.conf with the stuff below in it? 
Or do I need a file named asoundrc in my home folder with the below in it?
Thanks for your patience!

```
pcm.!default {
        type plug
        slave.pcm dmix:Loopback
}
```

---

### Post by Dodominyk on 2009-12-04
> **mocha said:**
> 
Second, unfortunately it appears that Ubuntu built the Karmic version of recordmydesktop without JACK support.  You can confirm this suspicion by running "recordmydesktop --print-config" and you'll see it says Jack Disabled.  So you're going to have to grab the source (apt-get source recordmydesktop), extract and move the directory into /usr/src, make sure you have all the jack dev packages installed in synaptic, then as root execute:

```
./configure --prefix=/usr --enable-jack=yes LIBS=-ljack CFLAGS=-DHAVE_LIBJACK
make
make install
```

Run "recordmydesktop --print-config" again and it should say enabled.  

After you perform these workarounds the existing functional procedures with gtk-recordmydesktop, JACK, etc, is the same as before.

I dedicated a proof-of-concept video to you!  [http://www.youtube.com/watch?v=_2ij3Gm7bgA]("http://www.youtube.com/watch?v=_2ij3Gm7bgA")

Hi Mocha,

I installed jack from the ubuntu repositories, I extracted and installed the sink and source modules as you described, and then recompiled gtk-recordmydesktop to support jack. But then I do not know what to do. I tried to follow what I could find in many different source: loading the modules by hand, changing the file /etc/pulse/default.pa, etc, but nothing works.

Could you or anyone give a step by step guide to have it to work?

Thanks in advance,

---

### Post by VertexPusher on 2009-12-04
> **Cavsfan said:**
> when you mention Home directory, do you mean the dir that appears when you click on
Places > Home Folder?
Yes.

> I hope you are referring to the 1st one because I managed to create a dir. called 
.asoundrc in the actual home directory (where the only other dir. is my userid/name) 
and I cannot figure out how to move the file I created named alsa.conf into it.
.asoundrc is a file in your home directory. If your username is USER, the file location is:

/home/USER/.asoundrc

It's a file, not a directory. The file does not exist by default, but once you create it, ALSA will read it every time a client starts up.

In order to get things back to factory defaults, reverse the steps I outlined above: terminate Jack, delete (or rename) .asoundrc, restart any running ALSA client application. Then you can remove the snd-aloop module, but it won't hurt if you leave it loaded. It will be gone after the next reboot anyway.

---

### Post by Cavsfan on 2009-12-04
Wonder why Rhythmbox will stop playing when Jack is started?
Then when I click on Quit Jack, Rhythmbox resumes right where it left off?

---

### Post by VertexPusher on 2009-12-04
> **Cavsfan said:**
> Wonder why Rhythmbox will stop playing when Jack is started?
Then when I click on Quit Jack, Rhythmbox resumes right where it left off?
That's because you are using PulseAudio. When Jack is started, PulseAudio is suspended automatically.

There are ways to turn automatic suspension off, but since I don't use PulseAudio at all, I can't help you with that. Remember, my solution was meant to be a simple _alternative_ to the PulseAudio->Jack->ALSA chain.

---

### Post by Cavsfan on 2009-12-04
Even Youtube sound is stopped when Jack starts and resumes when it stops,
I don't understand because I was wanting to use the output of an MP3 or a Youtube 
audio/video during the recordmydesktop session. 

Is that not possible with your solution VertexPusher?
Thank you!

---

### Post by Cavsfan on 2009-12-04
> **mocha said:**
> Actually it does make a difference.  In this case perhaps it's best for you to grab the pulseaudio source and compile it to obtain the jack sink module.  You can do this safely without installing anything.  Try in a temp directory, apt-get source pulseaudio, ./configure --enable-jack, make.  If you are successful the output of the configure script should tell you that jack will be enabled.  When it's done compiling, I believe in the src/.libs directory you'll find the module-jack-sink.so file.  Copy it into /usr/lib/pulse-0.9.19/modules (hopefully this is the same directory for 64 bit) then run "sudo ldconfig".

Mocha, did you see my last post about what happened when I ran the "sudo apt-get source pulseaudio" commands? I put the error it gave in that post. It gave this error:

```
$ apt-get source pulseaudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
NOTICE: 'pulseaudio' packaging is maintained in the 'Bzr' version control system at:
[http://launchpad.net/~ubuntu-core-dev/pulseaudio/ubuntu]("http://launchpad.net/%7Eubuntu-core-dev/pulseaudio/ubuntu")
Please use:
bzr get [http://launchpad.net/~ubuntu-core-dev/pulseaudio/ubuntu]("http://launchpad.net/%7Eubuntu-core-dev/pulseaudio/ubuntu")
to retrieve the latest (possibly unreleased) updates to the package.
Skipping already downloaded file 'pulseaudio_0.9.19-0ubuntu4.dsc'
Skipping already downloaded file 'pulseaudio_0.9.19.orig.tar.gz'
Skipping already downloaded file 'pulseaudio_0.9.19-0ubuntu4.diff.gz'
Need to get 0B of source archives.
Skipping unpack of already unpacked source in pulseaudio-0.9.19
$
```I saw the video you made with my post on it!!! I want to do that! I just don't want to
have to use a microphone.  I want to use an MP3 or a YouTube video on the 
recordmydesktop session. I can do that right?
Thanks!

PS I installed BZR (the error message above) after I figured out what it was. Should I have? 
Thanks!

---

### Post by Cavsfan on 2009-12-04
> **mocha said:**
> So you're going to have to grab the source (apt-get source recordmydesktop), extract and move the directory into /usr/src, make sure you have all the jack dev packages installed in synaptic, then as root execute:

```
./configure --prefix=/usr --enable-jack=yes LIBS=-ljack CFLAGS=-DHAVE_LIBJACK
make
make install
```Run "recordmydesktop --print-config" again and it should say enabled.  


I tried to extract the recordmydesktop source and move the directory into /usr/src
but, it required root privileges. Too much Noob I speculate!

I used to be a good mainframe programmer, with some basic Linux knowledge.
But, I learn fairly quickly. :confused:

---

### Post by mocha on 2009-12-06
"sudo -i" is the usual way to get a root terminal in ubuntu.

I don't understand why you would have problems downloading the pulseaudio source.  That apt-get command simply downloads the source and diff files.  Did you look in the directory you executed the command for the zipped source file?

To the other person that asked about loading the pulse-jack sink module, you should setup Jack to do this on start up.  In the Jack options there is a section where you can specify a script to load at startup.  Make a script somewhere that looks like this:

```
#!/bin/bash

pactl load-module module-jack-sink channels=2
```

That will load the pulse-jack sink module when you start Jack.  There's no reason to load it though the default.pa file unless you're using Jack all the time.

---

### Post by mocha on 2009-12-06
> **Cavsfan said:**
> OK,
One more question: how would I reset the sounds back to normal after doing this?
Yesterday I did this command: 
[COLOR=Blue]sudo modprobe snd-aloop[/COLOR]
Then later I could not figure out how to get the sound to come out of my speakers.
Thinking it was something I borked, I re-installed.

This is exactly why I recommended against this method.  But to each his own.

---

### Post by Cavsfan on 2009-12-06
> **mocha said:**
> This is exactly why I recommended against this method.  But to each his own.

Yes, I backed out of that method. I thought I was doing right. I am trying to follow your 
procedures like I should have in the first place. I guess everyone has his/her own way 
but, I like your idea of keeping things simple. It is just that I have never compiled anything 
in Ubuntu yet. I will see what i can do though...
Thanks!

---

### Post by Cavsfan on 2009-12-06
> **mocha said:**
> "sudo -i" is the usual way to get a root terminal in ubuntu.

I don't understand why you would have problems downloading the pulseaudio source.  That apt-get command simply downloads the source and diff files.  Did you look in the directory you executed the command for the zipped source file?

I was able to download the source for pulseaudio ok. 

There is a dir. called pulseaudio_0.9.19.orig.tar.gz and another one named
pulseaudio_0.9.19-0ubuntu4.diff.gz and another file named pulseaudio_0.9.19-0ubuntu4.dsc in my home directory.

There is also a folder named pulseaudio-0.9.19 . I cannot remember if this was 
created when I extracted one of the other folders. 
I mind is going I think! :redface:

The folder /usr/src has the root privileges attributes.
The command "sudo i" should allow me to move the files to the usr/src folder I 
would think.
But, you said I could do this from a temp dir. anyway, so my home should do right?
I will try that,
Thanks!

---

### Post by Cavsfan on 2009-12-06
I hope I am right in ignoring this:

```
Please use:
bzr get http://launchpad.net/~ubuntu-core-dev/pulseaudio/ubuntu
to retrieve the latest (possibly unreleased) updates to the package.
```The files downloaded.

---

### Post by Cavsfan on 2009-12-06
mocha,
OK I deleted all of the files I mentioned earlier and entered this to download the src 
again: [COLOR=Blue]sudo apt-get source pulseaudio[/COLOR]
That gave me 3 files in my home directory:
[COLOR=Blue]pulseaudio_0.9.19-0ubuntu4.diff.gz [COLOR=Black](dir)[/COLOR]
pulseaudio_0.9.19-0ubuntu4.dsc[/COLOR][COLOR=Blue] [COLOR=Black](file)[/COLOR][/COLOR]
[COLOR=Blue]pulseaudio_0.9.19.orig.tar.gz[/COLOR][COLOR=Blue] [COLOR=Black](dir)[/COLOR][/COLOR]
So, what do I do with these 3 again? I hope I am not being (too big of) a pain!
I am sticking to your help only (sorry vertexpusher) and will get this done no matter 
how long it takes!
Thanks for your help!

---

### Post by VertexPusher on 2009-12-06
> **mocha said:**
> This is exactly why I recommended against this method.  But to each his own.
My method takes no more than 3 minutes to set up and another 3 to revert the changes. You'll find out as soon as you try it.

Your method is an endless orgy of compiling, installing, customizing and reconfiguring the system with no easy way back. The whole idea of routing sound through two audio daemons is incredibly daft. Latency will go through the roof, stability will go out the window.

Will you be around when Cavsfan has finally borked his system beyond repair? I'll get my popcorn and see what happens.

---

### Post by mocha on 2009-12-07
> **VertexPusher said:**
> My method takes no more than 3 minutes to set up and another 3 to revert the changes. You'll find out as soon as you try it.

Your method is an endless orgy of compiling, installing, customizing and reconfiguring the system with no easy way back. The whole idea of routing sound through two audio daemons is incredibly daft. Latency will go through the roof, stability will go out the window.

Will you be around when Cavsfan has finally borked his system beyond repair? I'll get my popcorn and see what happens.

You sound like the people I work with.  "My method" is not really my method at all.  It's the linux way of hacking and trying things out.  Cavsfan already borked his system because of your 1999 method.  Pass the popcorn!  ;)

p.s.  Why do you use Ubuntu at all?  If you're not going to use what the devs gave you, sounds like you'd be better off with Arch or Gentoo.

---

### Post by mocha on 2009-12-07
> **Cavsfan said:**
> [COLOR=Blue]pulseaudio_0.9.19-0ubuntu4.diff.gz [COLOR=Black](dir)[/COLOR]
pulseaudio_0.9.19-0ubuntu4.dsc[/COLOR][COLOR=Blue] [COLOR=Black](file)[/COLOR][/COLOR]
[COLOR=Blue]pulseaudio_0.9.19.orig.tar.gz[/COLOR][COLOR=Blue] [COLOR=Black](dir)[/COLOR][/COLOR]

If you extract the one with the orig.tar.gz extension, it will give you a directory of the source code.

---

### Post by VertexPusher on 2009-12-07
> **mocha said:**
> Cavsfan already borked his system because of your 1999 method.
No, he didn't.

It's not exactly a 1999 method, but to some extent you are right: It worked five years before PulseAudio, and it will continue to work after PulseAudio is gone.

Why will PulseAudio be gone? Because very few people have Cavsfan's patience. Most people prefer stuff that works out of the box and doesn't take a week to set up.

---

### Post by Cavsfan on 2009-12-07
> **mocha said:**
> If you extract the one with the orig.tar.gz extension, it will give you a directory of the source code.
It looks like it already extracted itself as (after deleting all of this stuff and re-downloading the 2 directories and 1 file I mentioned), 
it created a directory called pulseaudio-0.9.19 that has a bunch of stuff including a dir named SRC.
It has a file in it called "compile" - a shell/script.
(You maybe can tell I am new to compiling my own stuff).

There are folders [COLOR=Teal]pulseaudio-0.9.19 [/COLOR]> [COLOR=Teal]src [/COLOR]> [COLOR=Teal]jack[/COLOR] and inside the Jack folder is 4 files named: 
[COLOR=Blue]module-jack-sink.c
module-jack-sink-symdef.h
module-jack-source.c
module-jack-source-symdef.h[/COLOR]

(folders are [COLOR=Teal]green[/COLOR] and files are [COLOR=Blue]blue[/COLOR].

Or, I could be wrong and need to extract the folder with the orig.tar.gz extension like you mentioned.

What do you think?
Thanks! :D

---

### Post by Dodominyk on 2009-12-08
If anyone is interested, I finally got jack to work by following the method on the page [http://sync-signal.com/2009/12/configuring-jack-and-pulseaudio-on-ubuntu-9-10/]("http://sync-signal.com/2009/12/configuring-jack-and-pulseaudio-on-ubuntu-9-10/") .

---

### Post by Cavsfan on 2009-12-08
> **Dodominyk said:**
> If anyone is interested, I finally got jack to work by following the method on the page [http://sync-signal.com/2009/12/configuring-jack-and-pulseaudio-on-ubuntu-9-10/](http://sync-signal.com/2009/12/configuring-jack-and-pulseaudio-on-ubuntu-9-10/) .

"sniffle" I tried it and it looked like it would work, but gtk-recordmydesktop still
got this error immediately when I clicked record:
[COLOR=DarkRed]Recording is finished.
recordMyDesktop has exited with status: 256
Description: error while parsing the arguments.
[/COLOR] 
I entered this: pkill pulseaudio
Started jack and made the connections to PulseAudio JACK Sink (2 left and right) and
PulseAudio JACK Source (2 left and right) (4 total were highlighted). 
Clicked Start Jack. Started recordmydesktop and highlighted the same 4 connections as 
in Jack and clicked record. It quit and gave the above error.

Meanwhile, Jack is still running and I entered this in terminal to see if recordmydesktop showed jack running "recordmydesktop --print-config" and it 
listed this output:

```
recordMyDesktop was compiled with the following options:

Jack            :Disabled
Default Audio Backend    :ALSA

```Could it be that recordMyDesktop needs to be compiled with jack enabled?

I don't have a clue where to go from here. :confused:

---

### Post by Dodominyk on 2009-12-08
Cavsfan,

I'm not sure I understand what you did. In gtk-recordmydesktop I only selected 'PulseAudio JACK Sink:front-left' and 'PulseAudio JACK Sink:front-right'. Did you by any chance also select the JACK Sources? That wouldn't work, these are meant to receive input as I understand.

---

### Post by VertexPusher on 2009-12-09
> **Cavsfan said:**
> Could it be that recordMyDesktop needs to be compiled with jack enabled?
Are you kidding???

mocha told you so **one week ago!** You actually quoted his post where he told you exactly how to do it. You didn't read it, did you?




@mocha: I want my popcorn back.

---

### Post by Cavsfan on 2009-12-09
> **Dodominyk said:**
> Cavsfan,

I'm not sure I understand what you did. In gtk-recordmydesktop I only selected 'PulseAudio JACK Sink:front-left' and 'PulseAudio JACK Sink:front-right'. Did you by any chance also select the JACK Sources? That wouldn't work, these are meant to receive input as I understand.

Yes I highlighted all 4 like the noob that i am. 

Thanks Dodominyk for clarifying that (DOH!). I will try that!

---

### Post by Cavsfan on 2009-12-09
> **VertexPusher said:**
> Are you kidding???

mocha told you so **one week ago!** You actually quoted his post where he told you exactly how to do it. You didn't read it, did you?




@mocha: I want my popcorn back.

I know mocha said that and I was just mentioning it.
And no where did I try to give the impression that I was an expert at this...
So, your point is?

---

### Post by Cavsfan on 2009-12-09
Dodominyk, I tried it again with just the 2 selected 
('PulseAudio JACK Sink:front-left' and 'PulseAudio JACK Sink:front-right')
and still got the 256 error.
I am starting Jack up before starting recordmydesktop, is that correct?
In Jack Patchbay on the left it has Output socket 1 Midi Through Port-0
                                                 Output socket 2
                                                                         capture_1
                                                                          capture_2
On the right it has the same except the capture_1 and 2 are called Playback_1 and 2
There is a single blue line indicating connection.
I'll try to post a picture

---

### Post by Cavsfan on 2009-12-10
I got the source (recordmydesktop-0.3.8.1) moved to /usr/src/ and entered the command

./configure --prefix=/usr --enable-jack=yes LIBS=-ljack CFLAGS=-DHAVE_LIBJACK
(per mocha above)

Here is the output of that command:
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: in `/usr/src/recordmydesktop-0.3.8.1':
configure: error: C compiler cannot create executables
See `config.log' for more details.

Here the output from config.log

```
This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by recordmydesktop configure 0.3.8.1, which was
generated by GNU Autoconf 2.63.  Invocation command line was

  $ ./configure --prefix=/usr --enable-jack=yes LIBS=-ljack CFLAGS=-DHAVE_LIBJACK

## --------- ##
## Platform. ##
## --------- ##

hostname = Cavsfan-desktop
uname -m = x86_64
uname -r = 2.6.31-16-generic
uname -s = Linux
uname -v = #52-Ubuntu SMP Thu Dec 3 22:07:16 UTC 2009

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = unknown
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
/usr/bin/hostinfo      = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:1899: checking for a BSD-compatible install
configure:1967: result: /usr/bin/install -c
configure:1978: checking whether build environment is sane
configure:2021: result: yes
configure:2046: checking for a thread-safe mkdir -p
configure:2085: result: /bin/mkdir -p
configure:2098: checking for gawk
configure:2128: result: no
configure:2098: checking for mawk
configure:2114: found /usr/bin/mawk
configure:2125: result: mawk
configure:2136: checking whether make sets $(MAKE)
configure:2158: result: yes
configure:2399: checking for gcc
configure:2415: found /usr/bin/gcc
configure:2426: result: gcc
configure:2658: checking for C compiler version
configure:2666: gcc --version >&5
gcc (Ubuntu 4.4.1-4ubuntu8) 4.4.1
Copyright (C) 2009 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:2670: $? = 0
configure:2677: gcc -v >&5
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.4.1-4ubuntu8' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --program-suffix=-4.4 --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --disable-werror --with-arch-32=i486 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) 
configure:2681: $? = 0
configure:2688: gcc -V >&5
gcc: '-V' option must have argument
configure:2692: $? = 1
configure:2715: checking for C compiler default output file name
configure:2737: gcc -DHAVE_LIBJACK   conftest.c -ljack >&5
/usr/bin/ld: cannot find -ljack
collect2: ld returned 1 exit status
configure:2741: $? = 1
configure:2779: result: 
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "recordmydesktop"
| #define PACKAGE_TARNAME "recordmydesktop"
| #define PACKAGE_VERSION "0.3.8.1"
| #define PACKAGE_STRING "recordmydesktop 0.3.8.1"
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "recordmydesktop"
| #define VERSION "0.3.8.1"
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:2785: error: in `/usr/src/recordmydesktop-0.3.8.1':
configure:2788: error: C compiler cannot create executables
See `config.log' for more details.

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=set
ac_cv_env_CFLAGS_value=-DHAVE_LIBJACK
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_LIBS_set=set
ac_cv_env_LIBS_value=-ljack
ac_cv_env_XMKMF_set=
ac_cv_env_XMKMF_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_path_install='/usr/bin/install -c'
ac_cv_path_mkdir=/bin/mkdir
ac_cv_prog_AWK=mawk
ac_cv_prog_ac_ct_CC=gcc
ac_cv_prog_make_make_set=yes

## ----------------- ##
## Output variables. ##
## ----------------- ##

ACLOCAL='${SHELL} /usr/src/recordmydesktop-0.3.8.1/missing --run aclocal-1.10'
AMDEPBACKSLASH=''
AMDEP_FALSE=''
AMDEP_TRUE=''
AMTAR='${SHELL} /usr/src/recordmydesktop-0.3.8.1/missing --run tar'
AUTOCONF='${SHELL} /usr/src/recordmydesktop-0.3.8.1/missing --run autoconf'
AUTOHEADER='${SHELL} /usr/src/recordmydesktop-0.3.8.1/missing --run autoheader'
AUTOMAKE='${SHELL} /usr/src/recordmydesktop-0.3.8.1/missing --run automake-1.10'
AWK='mawk'
CC='gcc'
CCDEPMODE=''
CFLAGS='-DHAVE_LIBJACK'
CPP=''
CPPFLAGS=''
CYGPATH_W='echo'
DEFS=''
DEPDIR=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP=''
EXEEXT=''
GREP=''
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
INSTALL_STRIP_PROGRAM='$(install_sh) -c -s'
LDFLAGS=''
LIBOBJS=''
LIBS='-ljack'
LTLIBOBJS=''
MAKEINFO='${SHELL} /usr/src/recordmydesktop-0.3.8.1/missing --run makeinfo'
MKDIR_P='/bin/mkdir -p'
OBJEXT=''
PACKAGE='recordmydesktop'
PACKAGE_BUGREPORT=''
PACKAGE_NAME='recordmydesktop'
PACKAGE_STRING='recordmydesktop 0.3.8.1'
PACKAGE_TARNAME='recordmydesktop'
PACKAGE_VERSION='0.3.8.1'
PATH_SEPARATOR=':'
SET_MAKE=''
SHELL='/bin/bash'
STRIP=''
VERSION='0.3.8.1'
XMKMF=''
X_CFLAGS=''
X_EXTRA_LIBS=''
X_LIBS=''
X_PRE_LIBS=''
ac_ct_CC='gcc'
am__fastdepCC_FALSE=''
am__fastdepCC_TRUE=''
am__include=''
am__isrc=''
am__leading_dot='.'
am__quote=''
am__tar='${AMTAR} chof - "$$tardir"'
am__untar='${AMTAR} xf -'
bindir='${exec_prefix}/bin'
build=''
build_alias=''
build_cpu=''
build_os=''
build_vendor=''
datadir='${datarootdir}'
datarootdir='${prefix}/share'
docdir='${datarootdir}/doc/${PACKAGE_TARNAME}'
dvidir='${docdir}'
exec_prefix='NONE'
host=''
host_alias=''
host_cpu=''
host_os=''
host_vendor=''
htmldir='${docdir}'
includedir='${prefix}/include'
infodir='${datarootdir}/info'
install_sh='$(SHELL) /usr/src/recordmydesktop-0.3.8.1/install-sh'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localedir='${datarootdir}/locale'
localstatedir='${prefix}/var'
mandir='${datarootdir}/man'
mkdir_p='/bin/mkdir -p'
oldincludedir='/usr/include'
pdfdir='${docdir}'
prefix='/usr'
program_transform_name='s,x,x,'
psdir='${docdir}'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target_alias=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define PACKAGE_NAME "recordmydesktop"
#define PACKAGE_TARNAME "recordmydesktop"
#define PACKAGE_VERSION "0.3.8.1"
#define PACKAGE_STRING "recordmydesktop 0.3.8.1"
#define PACKAGE_BUGREPORT ""
#define PACKAGE "recordmydesktop"
#define VERSION "0.3.8.1"

configure: exit 77

```This is really my first compile and Thanks to anyone who can help!!!

---

### Post by thorgal on 2009-12-10
for those who want the flash plugin to output directly to jackd, you can always try what is described here :

[http://linuxmusicians.com/viewtopic.php?f=4&t=2323](http://linuxmusicians.com/viewtopic.php?f=4&t=2323)

if jackd crashes, you will have to remove the browser tab containing the flash video and reopen it. Minor inconvenience but jackd on cool systems never fails, or does it ... ahem ... ;)

ah yeah, for the compilation, don't do it in /usr/src if you are not root :)

do it in ... say /home/<yourself>/src

---

### Post by Capoeira on 2009-12-10
an its also possible to use alsa-jack geting it from debian-repro (last post)

[http://linuxmusicians.com/viewtopic.php?f=4&t=1022&p=6882&hilit=alsa+jack#p6882](http://linuxmusicians.com/viewtopic.php?f=4&t=1022&p=6882&hilit=alsa+jack#p6882)

---

### Post by Cavsfan on 2009-12-10
Finally got recordmydesktop compiled with JACK enabled! Whoot! \\:D/

```
$ recordmydesktop --print-config

recordMyDesktop was compiled with the following options:

Jack                     :Enabled
Default Audio Backend    :ALSA
```Just had to keep adding the files until it could do it's thing.

:guitar:

---

### Post by Cavsfan on 2009-12-10
OK. so I finally got this to work. I can now check this off of my list of things I could not
do. But, even though I have a fairly powerful processor, the quality was pretty bad.
Thanks to those who helped me get there! 
So, I am off to find other things I can't do... :popcorn:

---

