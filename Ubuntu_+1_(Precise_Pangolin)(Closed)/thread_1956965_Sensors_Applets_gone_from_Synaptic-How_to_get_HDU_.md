---
title: "Sensors Applets gone from Synaptic-How to get HDU temps in Conky?"
date: 2012-04-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by emarkay on 2012-04-11
I added "lmsensors", "sensord" and "xsensors" but still no temps. This woks fine in 10.04.

Thank you, 
MRK

---

### Post by cariboo on 2012-04-11
Please check [this]("http://askubuntu.com/questions/33976/is-there-a-hardware-temperature-sensor-indicator") thread, it should solve your problems

---

### Post by emarkay on 2012-04-11
Thanks, will check that out tomorrow.  That should work in Conky, too?

---

### Post by stinkeye on 2012-04-12
Did you run 
```
sudo sensors-detect
```
after installing lm_sensors?
[**_[COLOR="DarkRed"]Using Sensors[/COLOR]_**]("http://conky.pitstop.free.fr/wiki/index.php5?title=Using_Sensors_(en)")


...and for **hddtemp** make sure it is installed as SUID root, so it can be used without "sudo".
```
sudo dpkg-reconfigure hddtemp
```


Working fine here in 12.04 in my conky.


[COLOR="Red"]*****NB.**[/COLOR] There is a bug in the current conky package for 12.04 where execi commands don't run
until your computer uptime is greater than your execi interval.
eg. After a fresh boot, if you have an **${execi 1800**... command in 
your conky you will get an output of "(null)" until your computer uptime
reaches half an hour (1800secs).

---

