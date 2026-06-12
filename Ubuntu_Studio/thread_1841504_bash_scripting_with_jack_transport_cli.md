---
title: "bash scripting with jack_transport cli"
date: 2011-09-09
forum: Ubuntu Studio
---

### Post by NoxDeleo on 2011-09-09
Hi all,

I'm not an experienced bash coder, but I'm trying to script some things with jack. jack_connect and jack_disconnect are scripting fine, but jack_transport is a program with it's own command prompt. Does anyone know how I would pass commands from a bash script to this cli...or alternatively, anyone know of any other ways to control the JACK transport without resorting to C++ coding with JACK's API?

Example of what I want to do:
#!/bin/bash
jack_transport
jack_transport> locate 0
jack_transport> play

Thanks in advance.

---

