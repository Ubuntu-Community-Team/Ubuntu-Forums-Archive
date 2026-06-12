---
title: "how do I force ttyUSB0 to be ttyUSB0 forever"
date: 2021-05-18
forum: Server Platforms
---

### Post by schmitta on 2021-05-18
I have a microprocessor sending data to a raspberry pi through a FTDI RS232 to USB interface. Sometimes it works and sometimes it does not. I need it to be ttyUSB0 always at each boot up. Sometimes I have to unplug the USB connection and replug it to get it to work. My C program has to do an open to /dev/ttyUSB0 to access the port therefore ttyUSB0 must remain the same each time the system is brought up. Any ideas as to what is going on? Thank you.

---

