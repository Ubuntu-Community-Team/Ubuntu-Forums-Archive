---
title: "JACK-related programs crash on opening"
date: 2010-09-06
forum: Ubuntu Studio
---

### Post by kellanium on 2010-09-06
I finally (Finally) got JACK working on my computer. Now whenever i try to open up a JACK-reliant application (i.e. Meterbridge) it opens and then immediately shuts down. If I'm doing something wrong, please be gentle, I'm a complete noob at this whole thing and I'm still learning. 

qjackctl seems to be the exception to this.

Thanks for the help in advance!

---

### Post by Pablo_F on 2010-09-07
Hi, 

launch the pograms from a terminal so you can see (and paste here if you wish) the errors. 
How to do this: Add a launcher to the desktop or panel and look at the launcher's properties, you will see the complete command that you can copy to a terminal.

Also, can you give the output of 

cat .jackdrc

? This is to know your jackd configuration.

Cheers! Pablo

---

### Post by kellanium on 2010-09-07
> **"JAMin"]jamin 0.95.0
(C) 2003-2005 J. Depner, S. Harris, J. O'Quin, R. Parker and P. Shirkey
This is free software, and you are welcome to redistribute it
under certain conditions said:**
> 

[quote="MeterBridge"]Meterbridge version 0.9.2 - [http://plugin.org.uk/meterbridge/](http://plugin.org.uk/meterbridge/)

Usage meterbridge: [-r ref-level] [-c columns] [-n jack-name] [-t type] <port>+

where ref-level is the reference signal level for 0dB on the meter
  and type is the meter type, one of:
     'vu'  - classic moving needle VU meter
     'ppm' - PPM meter
     'dpm' - Digital peak meter
     'jf'  - 'Jellyfish' phase meter
     'sco' - Oscilloscope meter


[quote="JACK Rack"](jack-rack:6912): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(jack-rack:6912): atk-bridge-WARNING **: IOR not set.

(jack-rack:6912): atk-bridge-WARNING **: Could not locate registry
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_init: could not connect to server 'localhost' - disabling LASH
Status update: jack_rack_6912
/usr/local/bin/jackd: symbol lookup error: /usr/local/bin/jackd: undefined symbol: jackctl_server_create
[/quote]

My JACK config. 
[quote="That one command"]/usr/bin/jackd -dalsa -dhw:0 -r48000 -p512 -n2 -S -Xseq
[/quote]

---

### Post by AutoStatic on 2010-09-07
```
/usr/local/bin/jackd: symbol lookup error: /usr/local/bin/jackd: undefined symbol: jackctl_server_create
```Best is to delete all the JACK related stuff you compiled yourself and reinstall JACK with Synaptic/apt-get install/Software Center.

---

### Post by kellanium on 2010-09-07
Did that, at least i think i did, and then i tried bitmeter. And the strangest thing happened.

[quote="BitMeter"]/usr/local/bin/jackd: symbol lookup error: /usr/local/bin/jackd: undefined symbol: jackctl_server_create
jack server not running ?
[/quote]

It *is* running, apparently the program can't detect it. What am I doing wrong?

---

### Post by AutoStatic on 2010-09-08
Did you reinstall JACK from the official repositories afterwards again? And what does the terminal command **ls /usr/local/bin/** output?

---

### Post by kellanium on 2010-09-08
> **AutoStatic said:**
> Did you reinstall JACK from the official repositories afterwards again? And what does the terminal command **ls /usr/local/bin/** output?
```
jack_alias     jackd            jack_lsp             jack_netsource       jack_thru
jack_bufsize   jack_delay       jack_metro           jack_samplerate      jack_unload
jack_connect   jack_disconnect  jack_midiseq         jack_server_control  jack_wait
jack_control   jack_evmon       jack_midisine        jack_showtime        jack_zombie
jack_cpu       jack_freewheel   jack_monitor_client  jack_simple_client
jack_cpu_load  jack_load        jack_multiple_metro  jack_test
```


Okay, you're gonna have to walk me through how to delete all of this stuff. It won't let me move any of it to trash.

---

### Post by Pablo_F on 2010-09-09
> Okay, you're gonna have to walk me through how to delete all of this stuff. It won't let me move any of it to trash. 

sudo rm /usr/local/bin/jack*

---

### Post by kellanium on 2010-09-09
okay, that's done, now JACK won't work at all. It keeps saying "Overall Operation Failed"

```
 p, li { white-space: pre-wrap; } [COLOR=#999999]21:48:05.033 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]21:48:05.098 Statistics reset.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66CC99]21:48:05.163 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]21:48:05.446 ALSA connection change.[/COLOR]
 [COLOR=#999999]21:48:14.087 Startup script...[/COLOR]
 [COLOR=#990099]21:48:14.087 artsshell -q terminate[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 sh: artsshell: not found
 [COLOR=#999999]21:48:14.493 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]21:48:14.493 JACK is starting...[/COLOR]
 [COLOR=#990099]21:48:14.494 /usr/bin/jackd -P10 -dalsa -dhw:1 -r48000 -p1024 -n2 -S -Xseq[/COLOR]
 /usr/bin/jackd: symbol lookup error: /usr/bin/jackd: undefined symbol: clock_source
 [COLOR=#999999]21:48:14.504 JACK was started with PID=5227.[/COLOR]
 [COLOR=#999999]21:48:14.513 JACK was stopped with exit status=127.[/COLOR]
 [COLOR=#999999]21:48:14.515 Post-shutdown script...[/COLOR]
 [COLOR=#990099]21:48:14.515 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]21:48:14.929 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]21:48:16.549 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
```

---

### Post by AutoStatic on 2010-09-10
Also check */usr/local/lib*, probably there are still some JACK libs in there. And afterwards reinstall JACK and libjack from the standard repositories.

---

### Post by AutoStatic on 2010-09-10
...

Mobile internet isn't always working that well ;)

---

### Post by AutoStatic on 2010-09-10
...

Shalalishalala ;)

---

### Post by kellanium on 2010-09-10
Thank you! works now! 

Your patience is very much appreciated.

---

