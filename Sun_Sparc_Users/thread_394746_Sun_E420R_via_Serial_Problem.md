---
title: "Sun E420R via Serial Problem"
date: 2007-03-27
forum: Sun Sparc Users
---

### Post by unixfudotnet on 2007-03-27
Hello, 

I am having problems where I do not get anything via serial from my Sun E420R server. I am trying to avoid paying for a sun/sgi monitor (shipping) and install via serial.

Minicom is listening on ttyS0, 9800, 8N1... tail -f /dev/ttyS0 shows no data (that is the only active serial device).

I have a null modem cable, 25 pin on the sun side and 9 pin on my pc side.

I changed the Serial Jumpers as recommended ([http://ubuntuforums.org/showthread.php?t=266189](http://ubuntuforums.org/showthread.php?t=266189)), yet still nothing.

Not sure what else to do. I don't want to have to spend 100USD to get a monitor to just install this thing. Please help if you know.

Thanks in advance!

---

### Post by thingy on 2007-03-27
Just did a quick search on google...umm have you looked for a sun made serial cable? This url indicates that sun's cables are slighly different:

[http://www.experts-exchange.com/OS/Unix/Solaris/Q_22441490.html](http://www.experts-exchange.com/OS/Unix/Solaris/Q_22441490.html)

Other interesting urls:

[http://www.obsolyte.com/sunFAQ/serial/](http://www.obsolyte.com/sunFAQ/serial/)

Have you got a keyboard plugged into the sun box by the way? The above url says not too!

[http://www.sunhelp.org/unix-serial-port-resources/](http://www.sunhelp.org/unix-serial-port-resources/)

and from the above url, you can get this link [http://www.sunhelp.org/unix-serial-port-resources/serial-pinouts/#420r.link](http://www.sunhelp.org/unix-serial-port-resources/serial-pinouts/#420r.link)

which shows what the pin out for the serial port on the your server is like.

Does your null modem cable conform to this scheme? If not, the above urls have links to places you can buy sun serial cables from.

Its pretty silly for Sun to have these non-standard pin assignments. bah! :-/

---

### Post by unixfudotnet on 2007-03-27
> **thingy said:**
> Just did a quick search on google...umm have you looked for a sun made serial cable? This url indicates that sun's cables are slighly different:

[http://www.experts-exchange.com/OS/Unix/Solaris/Q_22441490.html](http://www.experts-exchange.com/OS/Unix/Solaris/Q_22441490.html)

Other interesting urls:

[http://www.obsolyte.com/sunFAQ/serial/](http://www.obsolyte.com/sunFAQ/serial/)

Have you got a keyboard plugged into the sun box by the way? The above url says not too!

[http://www.sunhelp.org/unix-serial-port-resources/](http://www.sunhelp.org/unix-serial-port-resources/)

and from the above url, you can get this link [http://www.sunhelp.org/unix-serial-port-resources/serial-pinouts/#420r.link](http://www.sunhelp.org/unix-serial-port-resources/serial-pinouts/#420r.link)

which shows what the pin out for the serial port on the your server is like.

Does your null modem cable conform to this scheme? If not, the above urls have links to places you can buy sun serial cables from.

Its pretty silly for Sun to have these non-standard pin assignments. bah! :-/
Googling was my first avenue of help, it is what brought me to this ubuntu sparc forum, even :)

Hrm, seems to be standard layouts, unless I am missing something. I know others have used regular null modem 25 and 9 pin layouts fine.

I've read that information before, including the sun manuals, I am baffled. I changed the serial jumpers to be RS232 as per manual instructions too. Minicom shows nothing :\

Can anyone that successfully did this offer advice to what I may be missing.

---

