---
title: "USB interface stops working after adjusting JACK"
date: 2013-10-03
forum: Ubuntu Studio
---

### Post by kale-3 on 2013-10-03
Hello,
This has happened twice now; once on a vanilla Ubuntu 12.04 upgraded to studio and once on Ubuntu Studio 12.04 (which was installed over said vanilla Ubuntu install). 

I get audio routed from a USB interface (Berhinger Guitar Link) through JACK (using qjackctl) and back out of the computer. Then I go back and adjust jack settings to improve latency and at a certain point, this same connection (hw:1 input, default output: system in to system out) stops outputting, while another program (hydrogen) still outputs. I'm not getting any xruns, either. This problem does not resolve after restoring default qjackctl latency settings. It also does not resolve after a reboot (It does, however, resolve after a reinstall :p).

I'm running a Dell Optiplex 755. Core 2 Duo 2.54 ghz. 

Thanks,
Kale

---

### Post by theDaveTheRave on 2013-10-04
Kale,

show the output of dmesg
```

tail var/log/dmesg

```

during the stages of setup of your equipment

so when the output works, then again when you have made modification to your setting (and it still works) then again after it has failed.

you may want to do the same for the syslog
```

tail var/log/syslog

```

quick note, you may not get all the info that you need in the tail (it defaults to the last ten lines), so you may need to up the number of lines, eg...
```

tail -20 /var/log/dmesg

```

adjust the 20 value to suit.

David

---

