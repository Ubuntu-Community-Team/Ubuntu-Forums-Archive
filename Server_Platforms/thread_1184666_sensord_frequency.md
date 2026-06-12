---
title: "sensord frequency"
date: 2009-06-11
forum: Server Platforms
---

### Post by TheHilikus on 2009-06-11
I'm trying to configure sensord to do the routine reading of the sensors less frequently. Right now it is doing it every 30mins. the help doc says this

> -l, --log-interval time: Specify the interval between logging all sensor readings; the default is to log all readings every half hour. 

but there doesn't seem to be an option in a config file for that. the only config file for sensord is to configure the sensors chips, this option seems to be only available in the command line so i would have to change the way sensord is called directly but i've never had to do this with any other program, usually you configure something in a config file instead of changing the command line that's used to start the daemon so i think i'm missing something

any ideas?

Thanks

---

### Post by TheHilikus on 2009-06-11
ok i found it
so sensord doesn't have a file for these settings, they can only be configured from the command line when starting the daemon
the arguments are set in **/etc/default/sensord**

---

