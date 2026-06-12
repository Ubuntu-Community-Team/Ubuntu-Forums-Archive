---
title: "Serial Port hanging issues in Ubuntu 10.04 with kernel linux-2.6.32.44"
date: 2013-01-27
forum: Server Platforms
---

### Post by allplexwebmaster on 2013-01-27
Hi 
 
I am new to this forum.  We were using Ubuntu 10.04 with the  linux-2.6.32.44 and we have customized the kernel for our requirement.  We are using serial port rs 232 for communicating the peripherals. It’s  basically 4 wires with the only RTS flow control. Couple of days later  serial communication failed and Transmitting byte is successful and we  are checking whether all the transmitted bytes are send from serial port  buffer using below logic and found TIOCSERGETLSR bit never set and  every  ioct call get  success. Even if we try to flush the serial port  using tcflush but no success. This issues happening in few systems so  for. Once this issue happens we have to reboot the system and same  problem happens again with in few day. After these issues happened  serial port was not responding. This code was working with Redhat 9 more  than 7 years without issues and we have recently updated the system  from the Redhat 9 to Ubuntu 10.04.

    do        {                 ioctl(hanio->fd, TIOCSERGETLSR, &status);         }while(!(status & TIOCSER_TEMT));

---

