---
title: "linuxband"
date: 2015-04-02
forum: Ubuntu Studio
---

### Post by msaether on 2015-04-02
[COLOR=#111111][FONT=Ubuntu]I'm trying to install linuxband. I installed the requirements and dependencies listed on[http://linuxband.org/documentation.html](http://linuxband.org/documentation.html). The page then says to type three commands: ./configure, make, sudo make install.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]./configure seem to work, there are no errors in the output. Afterwards I type make. The first part of the output is:[/FONT][/COLOR]

s@mathias-N61Jv:/usr/local/src/linuxband-12.02$ make
cc -o target/linuxband-player  -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include    -I/usr/local/include -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include   -I.   -lglib-2.0   -pthread -lgthread-2.0 -lglib-2.0   -ljack -lpthread   -L/usr/local/lib -lsmf -lm -lglib-2.0   src/main/c/linuxband-player.c src/main/c/midi.c src/main/c/remote_control.c
src/main/c/linuxband-player.c: In function &#8216;main&#8217;:
src/main/c/linuxband-player.c:768:2: warning: &#8216;g_thread_init&#8217; is deprecated (declared at /usr/include/glib-2.0/glib/deprecated/gthread.h:261) [-Wdeprecated-declarations]
  g_thread_init(NULL);
  ^
/tmp/ccy7PkTO.o: In function `warning_async':
linuxband-player.c:(.text+0x144): undefined reference to `g_log'
/tmp/ccy7PkTO.o: In function `warn_from_jack_thread_context':
linuxband-player.c:(.text+0x168): undefined reference to `g_idle_add'
/tmp/ccy7PkTO.o: In function `nframes_to_ms':
linuxband-player.c:(.text+0x184): undefined reference to `jack_get_sample_rate'
/tmp/ccy7PkTO.o: In function `ms_to_nframes':
linuxband-player.c:(.text+0x267): undefined reference to `jack_get_sample_rate'
/tmp/ccy7PkTO.o: In function `send_all_sound_off':
[COLOR=#111111][FONT=Ubuntu]
The output continues to list a variant of the to last lines above "undefined reference to XXXX" and "in function XXXXX".  [/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]I'm fairly certain something is wrong here[/FONT][/COLOR]

---

