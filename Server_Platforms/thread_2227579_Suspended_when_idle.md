---
title: "Suspended when idle?"
date: 2014-06-02
forum: Server Platforms
---

### Post by Graysonh on 2014-06-02
I've got 14.04 installed on a nice simple setup with Samba and Transmission running.

I notice that if I come back to the server after ten minutes or so (when it is actively downloading) and try to access from Transmission remote GUI (or web interface) or using SSH I cannot find the box. Only when I strike a key on the keyboard of the server does everything become usable again. Is there some sort of sleep function that is enabled by default or what could be going on here to cause this?

Additionally, when transferring files or folders that are large they will hang at some point (usually over 600mb) - SSH will then disconnect. Samba and SSH will display the same symptoms as above, becoming usable again after waking the server screen.

Little more info: Everything is fine when nothing is requested - however, upon adding two torrent files I lost connection with the server approximately a minute after the addition. I launched WinSCP almost immediately and attempted to connect - which it did, although it took almost twice as long as usual. The second I am authenticated - poof - everything is back. As I'm writing this, it has disconnected again and the open connection in WinSCP is rejected, only to allow me to log in immediately after again and see everything come back.

---

