---
title: "Installing/Using CUPS.... totally lost"
date: 2008-04-23
forum: Server Platforms
---

### Post by garfonzo on 2008-04-23
I have a home server that I've just set up (used to be a WinXP box) for file sharing (I successfully set up samba and mapped a network drive on each windows machine to the share on the server - beauty) and, hopefully, to share a printer. There are two windows machines (Vista and WinXP) and Ubuntu on the LAN all of which will need to print off the same printer. I'm trying to get the headless 7.10 server to share the printer via CUPs and am determined to get this done via command line.

I'm totally lost.

I'll I've got so far is:
apt-get install cupsys cups-client

(can't remember the exact packages, but basically the server and the client for CUPS).

Now what!? I believe that I've figured out that my printer is on /dev/usb/lp0 but I am unsure what the next step is. It'd be so much easier through a GUI but I really want to remain 'raw' and do it all through the command line. I don't want to resort to Webmin or something. 

Does anyone have any great guides for going through the steps of installing the printer for the server, printing a test page, and then sharing the printer (all the normal stages I would do with a desktop). I've tried looking around but have come up dry.

Thanks a bunch!

Garfonzo

---

### Post by lord_farfig on 2008-04-24
I've run into this snag before myself.  CUPS has it's own Web GUI for printer configuration, runs on port 631.  I've personally edited the CUPS config file to allow me to access it from another PC on my HOME network, but this isn't super safe, by default you can only access the GUI from 'localhost.'

If you have lynx or links on your server you should be able to open [http://localhost:631](http://localhost:631) and you'll have your 'text' GUI... lol.  I've also had to install the drivers for my specific printer since CUPS didn't have a generic driver for it... so YMMV.  You should even be able to check [www.cups.org](www.cups.org) too.

---

### Post by garfonzo on 2008-04-26
The website for CUPS sucks! There is no real "this is how to get your printer up and running" section... Sigh.

[This thread]("http://ubuntuforums.org/showthread.php?t=195077") proved somewhat useful. Thought I'd post this link in case anyone else was having trouble.

---

