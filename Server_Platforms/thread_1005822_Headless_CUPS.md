---
title: "Headless CUPS?"
date: 2008-12-08
forum: Server Platforms
---

### Post by rhcm123 on 2008-12-08
I have a server that does, in effect, everything but the kitchen sink Web server, DHCP, file and media, STMP (although not really working :) ), DNS,  you name it, it does it. It runs (recently upgraded) ubuntu server 8.10 on a 95 mhz processor with 80-ish mb ram.

To cut my energy consumption (I'm GOIN GREEN!!!! ):KS) I have decided to integrate my samba/cups print server (a spluttering, literally, toshiba laptop) with this machine (take advantage of those 2 usb ports :) ). 

However, i can't find anything about how to configure a printer from the command line. I have an hp psc 1200 and it shares with the rest of the house, and I would like to do it through my main server, but I can't figure out any way to do it from the command line. Anybody have any ideas?

---

### Post by Dr Small on 2008-12-08
Intstall CUPS, then configure it from the web interface at:
[http://localhost:631](http://localhost:631)

;)

---

### Post by rhcm123 on 2008-12-08
> **Dr Small said:**
> Intstall CUPS, then configure it from the web interface at:
[http://localhost:631](http://localhost:631)

;)

I get a 403 forbidden error when i try to access it (my to-be CUPS server has no gui, so i'm doing this from my laptop.)...

---

### Post by cariboo on 2008-12-08
You will either have to access the cups interface locally from your server using links, just ssh in and at the prompt type:

```
links http://localhost:631
```

Once you are using the cups interfacee you can set it to allowe you to administer it remotely.

Jim

---

### Post by janascii on 2008-12-18
I manages to set one up last week following this thread.

[http://ubuntuforums.org/showthread.php?t=240282](http://ubuntuforums.org/showthread.php?t=240282)

---

### Post by CarolinaGuy on 2008-12-19
Follow the config file [here]("http://www.linuxforums.org/forum/servers/120309-cups-403-forbidden-error.html")

CarolinaGuy

---

### Post by rhcm123 on 2008-12-19
> **CarolinaGuy said:**
> Follow the config file [here]("http://www.linuxforums.org/forum/servers/120309-cups-403-forbidden-error.html")

CarolinaGuy

Nevermind, i got it working, thanks to caribu!!!
One thing though. It works fine through samba, but, unlike when it was connected to my other computer, i cant use ipp/cups straight up. Anybody know why?

---

