---
title: "Error in qjack (wineasio) Ubuntu 12.04"
date: 2012-12-13
forum: Ubuntu Studio
---

### Post by axy_david on 2012-12-13
Hello, I tried to configure wineasio and jack to work together but i can't manage to get it working I get the following error when I try to start Jack server:

[COLOR=#66cc99]Thu Dec 13 21:09:06 2012: Starting jack server...[/COLOR]
 [COLOR=#66cc99]Thu Dec 13 21:09:06 2012: JACK server starting in non-realtime mode[/COLOR]
 [COLOR=#66cc99]Thu Dec 13 21:09:06 2012: [1m[31mERROR: can't load "/usr/lib/x86_64-linux-gnu/jack/jack_alsa.so": /usr/lib/x86_64-linux-gnu/jack/jack_alsa.so: undefined symbol: jack_driver_nt_init[0m[/COLOR]
 [COLOR=#66cc99]Thu Dec 13 21:09:06 2012: [1m[31mERROR: Cannot initialize driver[0m[/COLOR]
 [COLOR=#66cc99]Thu Dec 13 21:09:06 2012: [1m[31mERROR: JackServer::Open() failed with -1[0m[/COLOR]
 [COLOR=#66cc99]Thu Dec 13 21:09:06 2012: [1m[31mERROR: Failed to open server[0m[/COLOR]
 [COLOR=#66cc99]Thu Dec 13 21:09:07 2012: Saving settings to "/home/axy_david/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#ff0000]21:09:08.238 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

---

