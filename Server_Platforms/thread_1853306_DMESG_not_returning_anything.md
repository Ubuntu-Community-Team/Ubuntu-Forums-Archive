---
title: "DMESG not returning anything"
date: 2011-10-02
forum: Server Platforms
---

### Post by Sock! on 2011-10-02
Hi Guys,
I'm trying to get my Ubuntu box to connect to my cisco switch but when I type a dmesg command nothing outputs. [HTML]root@DHCP:~# dmesg | grep tty
root@DHCP:~#
[/HTML]I have also tried other dmesg commands but the same thing happens. Any help would be greatly appreciated.

---

### Post by Sock! on 2011-10-02
> **zackwasa said:**
> In this particular case the dmesg output just does not contain anything tty. Did you try running simply:
```

dmesg

```

running dmesg does output stuff, any idea why it does not output what I want?

---

### Post by TravisZ on 2011-10-02
I'm guessing you are looking for serial ports.  Does the server actually have any serial ports?

Have you tried using something like "setserial"?

This is on my Gentoo box with no serial connection currently:

```
travisz ~ # setserial -g /dev/ttyS*
/dev/ttyS0, UART: unknown, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3
/dev/ttyS2, UART: unknown, Port: 0x03e8, IRQ: 4
/dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3
```And this is from a machine using a serial connection:

```
setserial -g /dev/ttyS*
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: 16550A, Port: 0xac00, IRQ: 82
/dev/ttyS2, UART: 16550A, Port: 0xa880, IRQ: 82
/dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3
```In the second example ttyS0,S1 and S2 are detected and working.

On the machine where it does detect the serial connection using setserial I do not see anything in dmesg either so I'm not 100% sure there, but it does detect the connection in the end.

---

### Post by Sock! on 2011-10-03
> **TravisZ said:**
> I'm guessing you are looking for serial ports.  Does the server actually have any serial ports?

Have you tried using something like "setserial"?

This is on my Gentoo box with no serial connection currently:

```
travisz ~ # setserial -g /dev/ttyS*
/dev/ttyS0, UART: unknown, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3
/dev/ttyS2, UART: unknown, Port: 0x03e8, IRQ: 4
/dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3
```And this is from a machine using a serial connection:

```
setserial -g /dev/ttyS*
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: 16550A, Port: 0xac00, IRQ: 82
/dev/ttyS2, UART: 16550A, Port: 0xa880, IRQ: 82
/dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3
```In the second example ttyS0,S1 and S2 are detected and working.

On the machine where it does detect the serial connection using setserial I do not see anything in dmesg either so I'm not 100% sure there, but it does detect the connection in the end.


Yes my server does have 2 serial ports. When I run the command you showed it is detected but i still cant connect to it with Kermit.
```
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: 16550A, Port: 0x02f8, IRQ: 3
```

---

### Post by Wayne_V on 2011-10-03
dmesg is a ring buffer, so if there are a lot of messages being logged you will lose the initial boot messages.  Try this instead:

cd /var/log ; grep ttyS dmesg messages *log | more

---

