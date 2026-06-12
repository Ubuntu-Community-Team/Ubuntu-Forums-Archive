---
title: "Serial Port tcflush not working"
date: 2016-11-08
forum: Ubuntu Application Development
---

### Post by rmisk on 2016-11-08
I am using Ubuntu 16.04 termios and fcntl to read and write to a modem on a serial port.  My program works okay but one thing I noticed is that 'tcflush(fd, TCIOFLUSH)' does not work, it appears to do absolutely nothing.  Some related Google references indicating adding a delay helps but I haven't seen any such evidence.

This problem seems to have been around for many years so is not likely to get fixed anytime soon.

Does any have any suggestions to get it to work or effect work arounds other than doing dummy reads that are in sync with the writes?

---

