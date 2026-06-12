---
title: "Jack server causes a high pitched ring."
date: 2011-08-17
forum: Ubuntu Studio
---

### Post by Casper! on 2011-08-17
Hi
When I start my Jack server, everything works fine except I get this continuous high pitched ring on my speakers. It also did this in the past when I open the "Sound preferences...". I am using the Behringer UCA222 USB interface. If anyone could help it would be greatly appreciated.

---

### Post by JuanPabloCuervo on 2011-08-19
details about your OS, Machine, Setup, Kernel, etc...

---

### Post by bluesscream on 2011-08-19
Sounds like Hardware. Computers make a lot of electromagnetic pollution and so it's not trivial to check groundloops and the positions of interfaces and their connection cables, which work as antennas and lead all these disturbance fequencies to the input, to be digitalisized and then on their way to the amplifier to be overlayed  again. And such a simple usb interface itself can be only poorly shielded and decoupled. I came not out of those issues until I made up a setup with symmetric connections and ground lifting.
But to underline JuanPabloCuervo's question, the above is poking around in the mud as long as we don't have more information about your special setup.

---

### Post by Casper! on 2011-08-20
Release: Ubuntu 11.04 (natty)
GNOME: 2.32.1 (Ubuntu 2011-04-14)
Kernel: 2.6.38-10-generic (#46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011)
OS Type: Linux
GCC version: 4.5.2 (x86_64-linux-gnu)
Xorg version: 1.10.1 (21 May 2011  11:48:41AM)

CPUs: 2
Model name: Intel(R) Core(TM)2 CPU          4400  @ 2.00GHz
Frequency: 2003 MHz
L@ cache: 2048KB

Memory total: 4973 MiB
Swap total: 5117 Mib

Then as I mentioned before i have the Behringer UCA222 USB interface with KRK Rokit 8s connected to the output.
Thank you for you time!

---

### Post by sgx on 2011-08-21
Ideas to try:
Set qjackctl Periods/buffers to 3 (on the setup page)
No other usb devices at the same time, and no usb hub.
No flourescent lights
Isolate the circuit the computer is on, turn off
all electric appliances by unplugging, or circuit breaker.
Get a new 'shortest' usb cable,tried in each usb plug position.
In some areas, the kitchen circuit is best, by local electric code.
If no improvement, try a few other distros, by live cd/dvd that use
different kernels, AVlinux, among others.

Have you tried headphones on the outputs the speakers are on?
Check google, and the docs for the speakers for details
Cheers

---

### Post by fedexnman on 2011-08-22
I would also try your device on a friends  windows,mac, or linux computer . i had a problem with a presonus firebox letting out a faint whining noise, come to find out it was the actual device and not the computer.

---

### Post by bluesscream on 2011-08-23
nice monitors ;)
but the low voltage cinch connections to those active  monitors are very glitchy, work like receiving aerials.
In my chaotic electromagnetic environment I only get suitable conditions using the XLR.
Please let us take part with your further experiences, we all learn by doing and sharing.

---

