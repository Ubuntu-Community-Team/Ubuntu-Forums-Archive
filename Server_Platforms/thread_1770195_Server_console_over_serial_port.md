---
title: "Server console over serial port"
date: 2011-05-28
forum: Server Platforms
---

### Post by ralfarof on 2011-05-28
Hi all,

Is there a way to get console output over a serial (COM) port? I have a box that I use as a NAS, DNS, DHCP and mt-daapd server, I don't have a spare monitor and it is not worth buying one just to use it once or twice a year.

I found this guide [http://linux.koolsolutions.com/2009/03/29/howto-redirecting-linux-console-output-over-serial-port-on-another-machine/]("http://linux.koolsolutions.com/2009/03/29/howto-redirecting-linux-console-output-over-serial-port-on-another-machine/")
but it doesn't work with Natty :(

Any help is appreciated ;)

Cheers!

---

### Post by boutch55555 on 2011-05-28
Can't you just ssh to the host ?

Sounds easier to me...

---

### Post by Lars Noodén on 2011-05-29
> **ralfarof said:**
> 
Is there a way to get console output over a serial (COM) port?

Yes.  I've set it up many times, mostly on Debian, but always from the first beginning of the installation never afterwards.  I'm sure there is a way to retrofit the machine, but am not sure how.

I took a look in one machine and see that /etc/initab has some info about the serial connection.  I don't know if it is adequate to just change that one file but it is a start.

```

T0:23:respawn:/sbin/getty -L ttyS0 19200 vt102

```

---

### Post by ralfarof on 2011-05-29
> **Lars Noodén said:**
> Yes.  I've set it up many times, mostly on Debian, but always from the first beginning of the installation never afterwards.  I'm sure there is a way to retrofit the machine, but am not sure how.

I took a look in one machine and see that /etc/initab has some info about the serial connection.  I don't know if it is adequate to just change that one file but it is a start.

```

T0:23:respawn:/sbin/getty -L ttyS0 19200 vt102

```

there's no /etc/inittab on Natty, that's the problem.

I found this in /etc/init/tty1.conf

```

# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on stopped rc RUNLEVEL=[2345]
stop on runlevel [!2345]

respawn
exec /sbin/getty -8 38400 tty1

```

I'm gonna play with that and see what happens, worst case scenario I'll be busy the next few hours reinstalling my server :D

---

