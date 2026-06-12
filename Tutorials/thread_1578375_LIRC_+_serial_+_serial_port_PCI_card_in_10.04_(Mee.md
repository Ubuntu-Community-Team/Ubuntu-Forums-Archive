---
title: "LIRC + serial + serial port PCI card in 10.04 (Meerkat)"
date: 2010-09-20
forum: Tutorials
---

### Post by anzevi on 2010-09-20
hi everybody,

this is a short walk-thru guide for anyone that need to get serial remote IR receiver working with internal PCI card with 2 serial ports on it. This is the typical case if you would like to have serial IR receiver installed on newer machines that doesn't have serial ports.

In this scenario I have bought ST Lab PCI controller card, model l-390 (PCI 2S serial card). 

This is how I got it working for my MythTV at home:

1) After you plug in serial port PCI card, check if your hardware is detected and print the configuration out:

```

lspci -v | grep -A4 Serial
04:05.0 Serial controller: NetMos Technology PCI 9865 Multi-I/O Controller (prog-if 02)
	Subsystem: Device a000:1000
	Flags: medium devsel, IRQ 17
	I/O ports at cce0 [size=8]
	Memory at dbefa000 (32-bit, non-prefetchable) [size=4K]
--
04:05.1 Serial controller: NetMos Technology PCI 9865 Multi-I/O Controller (prog-if 02)
	Subsystem: Device a000:1000
	Flags: medium devsel, IRQ 18
	I/O ports at cce8 [size=8]
	Memory at dbefc000 (32-bit, non-prefetchable) [size=4K]
```

As you can see, I have two serial ports (com1 and com2) with irq 17 and 18 and addresses 0xcce0 and 0xcce8. You will need this information later to put it in your lirc config file.

2) Install and buils LIRC modules:

```

apt-get install lirc lirc-modules-source module-assistant
m-a update,prepare
m-a clean lirc
m-a a-i -f lirc
dpkg-reconfigure lirc-modules-source
```

At this point you should have your lirc modules built.

3) Update your settings in /etc/modprobe.d/lirc-serial.conf:

```

#COM1 equivalent, /dev/ttyS0
options lirc_serial irq=17 io=0xcce0
#COM2 equivalent, /dev/ttyS1
options lirc_serial irq=18 io=0xcce8
alias char-major-61 lirc_serial
options lirc_serial share_irq=1
```

Make sure you have the right parameters for IRQs and com port addresses. Also, note that you need to have "share_irq=1" parameter otherwise it will not work and you will be seeing errors like this in your syslog file:

```

Sep 19 16:42:15 sataras lircd-0.8.6[2628]: lircd(default) ready, using /var/run/lirc/lircd
Sep 19 16:42:17 sataras lircd-0.8.6[2628]: accepted new client on /var/run/lirc/lircd
Sep 19 16:42:17 sataras lircd-0.8.6[2628]: could not open /dev/lirc0
Sep 19 16:42:17 sataras lircd-0.8.6[2628]: default_init(): Device or resource busy
Sep 19 16:42:17 sataras lircd-0.8.6[2628]: Failed to initialize hardware
Sep 19 16:42:17 sataras kernel: [ 1333.890444] lirc_serial: IRQ 17 busy
```

4) Update your settings in /etc/lirc/hardware.conf. It should look something like this:

```

LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE="/dev/lirc0"
MODULES="lirc_dev lirc_serial"

# Default configuration files for your hardware if any
#LIRCD_CONF="/etc/lirc/lircd.conf"
LIRCMD_CONF=""
#REMOTE="Home-brew (16x50 UART compatible serial port)"
REMOTE_MODULES="lirc_dev lirc_serial"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""
TRANSMITTER="Custom"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
REMOTE_SOCKET=""
TRANSMITTER_SOCKET=""
```

5) Start lirc service and you should be good to go:

```
/etc/init.d/lirc restart
```

If everything is ok, you should see soething like this in /var/log/syslog:

```
Sep 19 17:08:27 sataras lircd-0.8.6[17298]: lircd(default) ready, using /var/run/lirc/lircd
Sep 19 17:08:28 sataras lircd-0.8.6[17298]: accepted new client on /var/run/lirc/lircd
Sep 19 17:08:28 sataras kernel: [ 2904.888110] IRQ 18/lirc_serial: IRQF_DISABLED is not guaranteed on shared IRQs
Sep 19 17:08:36 sataras lircd-0.8.6[17298]: accepted new client on /var/run/lirc/lircd
```

This is it. Enjoy.

---

### Post by colonelpenguinx on 2011-08-23
I want to start by saying thanks for taking the time to post your  how-to.  I am surprised there don't seem to be many people trying this  yet.  I ordered a two-port pci card recently, but haven't been able to  get it working with my receiver yet.  I built the simple receiver  circuit at lirc.org, and I successfully tested it on an older desktop  computer.

I had to install the MCS9865 linux driver to get  /dev/lirc0 to appear.  It creates the serial ports at /dev/ttyD0 and  /dev/ttyD1.  

lspci -v shows:

03:05.0 Serial controller: NetMos Technology PCI 9865 Multi-I/O Controller (prog-if 02 [16550])
        Subsystem: Device a000:1000
        Flags: bus master, medium devsel, latency 64, IRQ 17
        I/O ports at d000 [size=8]
        Memory at cfff6000 (32-bit, non-prefetchable) [size=4K]
        Memory at cfff5000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [48] Power Management version 2
        Kernel driver in use: mcs9865-serial

03:05.1 Serial controller: NetMos Technology PCI 9865 Multi-I/O Controller (prog-if 02 [16550])
        Subsystem: Device a000:1000
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at d400 [size=8]
        Memory at cfffc000 (32-bit, non-prefetchable) [size=4K]
        Memory at cfff7000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [48] Power Management version 2
        Kernel driver in use: mcs9865-serial

I added the following to /etc/modprobe.d/lirc-serial.conf:

#COM1 equivalent, /dev/ttyS0
options lirc_serial irq=17 io=0xd000
#COM2 equivalent, /dev/ttyS1
options lirc_serial irq=18 io=0xd400
alias char-major-61 lirc_serial
options lirc_serial share_irq=1

I added the following to my rc.local file:

setserial /dev/ttyD0 uart none
/sbin/modprobe lirc_dev
/sbin/modprobe lirc_serial

When  I start my PC the serial driver loads and the RTS line goes from -7v to  9v.  This is sufficient to power the receiver.  I used a scope to  detect the dcd line and it is 5v until I press a remote button.  It then  pulses low.  The problem is I can't figure out how to get LIRC to read  the DCD line on the serial card.

mode2 -d /dev/lirc0 doesn't show any results when I press the button.

I  don't really know how to debug what is going wrong?  I would greatly  appreciate some suggestions.  I have spent way too many hours on this.   Thanks in advance for your help!

---

### Post by colonelpenguinx on 2011-08-25
I was finally able to get this working, but I am not sure why yet.  First... I forgot to mention earlier that I had to disable modem-manager because it was interfering with lirc_serial loading properly.

To fix the issue of no output using mode2 -d /dev/lirc0, I had to modify the serial cards driver source code.  I had to change the devices major number to 4 before compiling.  After that, it worked fine.  Can anyone explain why this worked?

---

