---
title: "Ubuntu Server 10.04 Faster Processing"
date: 2011-05-02
forum: Server Platforms
---

### Post by daviddon on 2011-05-02
I'm a relative new user to Ubuntu - especially the server (non-gui) interface.

I have an Asus P6T running an iCore 7 920 Processor, 12 GB of DDR3 ram, 1Tb Sata3 Drive.

I have installed Ubuntu Server 10.04, apache2, MySql, php5, php5-cli, PhpMyAdmin, Webmin, and OpenSSH.

I am running filtering looping scripts on data files 10,000 to 100,000 lines long - From the command line interface - comparing one to one, each line of data against every other line in the data, once, writing the results to a separate data table.
The smallest of these runs 499,500 lines of data against each other and take 3.25 hours, and runs very stable, but I'd like to go faster.

The benchmarks for the system 
100% Ubuntu Server 10.04 with Gnome Gui installed running script from Firefox browser.
107% Ubuntu Server 10.04 with Gnome Gui installed running script from CLI
185% Ubuntu Server 10.04 (no GUI) running script from CLI

* so, there ends the argument about weather or not the Gnome GUI effects server perfomance. It's killing mine! *

HERE IS THE PROBLEM: According to my system monitor, I'm still nowhere near using all 8 cores, and only 15% of the available ram.

Anyone got any ideas how to utilize MORE of my resources to may this run - and complete - faster?

I have changed the php.ini file 
"memory_limit=128m" to "memory_limit=1024m"
- and there is no noticeable change in performance.

Any ideas are appreciated.

---

### Post by dtfinch on 2011-05-02
We'd probably have to see the script. 42 lines per second doesn't sound very fast for most things. And to use multiple cores you'd have to divide it into smaller jobs and run them in parallel.

---

