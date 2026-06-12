---
title: "Ubuntu and dial-up fun"
date: 2010-08-05
forum: The Cafe
---

### Post by theraje on 2010-08-05
I managed to get my Ubuntu box connected to the Internet via dial-up using a USB modem today. It was a little difficult, being a Linux initiate, and having nothing but man pages to go on. But, I did it! :)

I plugged in my USB dial-up modem, and found out (though I forgot how exactly :?) that it was attached through /dev/ttyACM0. I edited wvdial.conf to have the line:

Modem = /dev/ttyACM0

At the start, put in my other info, saved the file, and went back to the terminal. It took a few tries (maybe the auth server was down), but I finally managed to get connected!

It only took a couple hours to update the repository listings in Synaptic. :P

I'm happy though. This means I can try to download some stuff I've been needing without waiting for DVD sets of the repository packages to be released. :)

---

### Post by juancarlospaco on 2010-08-05
You can control a remote Ubuntu with that, 
the other pc needs to be configure to get tty on serial port and attached to a serial external modem,
you dial to these modem and get a bash terminal, pretty h@x0r. :)

---

