---
title: "Webpage to change Network Configuration"
date: 2020-04-14
forum: Server Platforms
---

### Post by maurocn on 2020-04-14
I have to build a simple webpage for my Ubuntu Server to display and manage the Network configuration.

Any suggestion where I can find a a sample of html with script or php source to do this?

Furthermore... I'm not sure but have I to grant sudo privileges to www-data user? Isn't dangerous?

Thnx
M.

---

### Post by TheFu on 2020-04-15
This is a terrible idea, since when you make a mistake with networking, you'll lose access to the webpage, so it cannot be fixed.  It is also an attack vector, so securing this page/tool/webapp will be very important. For examples, you can get the source code for webmin and look over it. I think webmin is perl, not php. I would never suggest that someone install webmin outside of a lab environment.

> Isn't dangerous?
YES! Very.

---

### Post by LHammonds on 2020-04-16
This is a bad idea if you are talking about making text edit changes to the net config.

If you need to switch between different pre-configured config files, that would be easy but I still would not grant the web service any extra privileges to the OS.  In this case, I would present a dropdown selection for configuration selections and depending on which one you select, I would have it create an entry in a database (or flat file) for which file should be active.  Then have a shell script scheduled to run every minute or so that can access that database (or flat file) and read the desired configuration and compare to what is currently active.  If different, then shuffle around the configuration files to match what was desired.

LHammonds

---

