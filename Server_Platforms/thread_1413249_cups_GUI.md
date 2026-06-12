---
title: "cups GUI"
date: 2010-02-22
forum: Server Platforms
---

### Post by Dotan on 2010-02-22
Hi,

it might be basic stuff, but I can't get to the cups web interface.

all I have to do is //localhost:631 on the web browser. and it doesn't work.

I use MediaTomb - //localhost:49152. and it works!
I use webmin - //localhost:10000. and it also works!

what could be the problem with cups web interface on my machine?
I followed those instructions:

[http://lifeonubuntu.com/setting-up-cups-and-installing-local-printer-in-ubuntu-server/](http://lifeonubuntu.com/setting-up-cups-and-installing-local-printer-in-ubuntu-server/)

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

I installed the driver on my server, using a .deb file.

but I can't get the web interface...

what now?

---

### Post by Detonate on 2010-02-22
I had the same problem, and it was caused by pending print jobs that refused to be canceled.  The quickest solution I came up with was:

```
sudo apt-get purge cups
```
```
 sudo apt-get install cups
```

You will have to reinstall your printers.

---

### Post by Dotan on 2010-02-22
no. didn't work.

anyone else?

---

### Post by Detonate on 2010-02-22
OK, try it again, and this time after purging cups, delete (as sudo) all of the files in /etc/cups.  Then reinstall cups.

---

### Post by Dotan on 2010-02-22
nope... didn't work either.

maybe I'm doing it wrong?

the physical system is this:
 an old laptop that has an ubuntu 9.10 server on it.
 a printer that is plugged in via USB

I installed cups on the server, the server ip is 20.0.0.4.
I open the terminal on my laptop (not the server laptop, the ubuntu desktop one), I connect to it by ssh, lpinfo -v shows me that:

network lpd
network http
network socket
direct usb://Brother/HL-2030%20series
network ipp
direct scsi
direct parallel:/dev/lp0
network smb
network beh
serial serial:/dev/ttyS0?baud=115200

then, I open my browser, I type: 20.0.0.4:631
and it gives me the "page not found" message.

what did I do wrong?

---

### Post by Dotan on 2010-02-22
Holy Abraham!

It works!

actually, I followed this tutorial:

[http://lifeonubuntu.com/setting-up-cups-and-installing-local-printer-in-ubuntu-server/](http://lifeonubuntu.com/setting-up-cups-and-installing-local-printer-in-ubuntu-server/)

and used Detonate advise.

thanks Detonate!!

---

### Post by slakkie on 2010-02-22
No need to purge cups for this.

You need to edit /etc/cups/cupsd.conf and add the following line:

Port 631

Restart cups: /etc/init.d/cups restart and you should be good to go.

---

### Post by Dotan on 2010-02-22
You right - you need to add "port 631" instead of "listen localhost:631" (in the etc/cups/cupsd.conf file)

this is what I did and it worked.

---

### Post by Detonate on 2010-02-22
I suspect that port 631 is not open on the server.  That's the port that cups uses.  I could give you a bunch of CLI commands, but one of the easiest ways to fix this is to install firestarter and use it to control and open the port.

---

