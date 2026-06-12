---
title: "ubuntu 8.10 server and com ports problem"
date: 2009-04-19
forum: Server Platforms
---

### Post by AbuHeissam on 2009-04-19
hi,

i hope u can help me, i searched the net but until now i cant figure it ouzu meinem problem. i hav set up a computer withubuntu 8.10 server edition as OS. the mainboard, an asrock n73v-s, has only one built in serial-port, but i need at least 3. so i fetched a pci-addin card with 2 more serial ports. at bootup these 2 ports are declared as undefined

lspci -v prints me:

01:07.0 Serial controller: Device 4348:3253 (rev 10) (prog-if 02)
Subsystem: Device 4348:3253
Flags: medium devsel, IRQ 19
I/O ports at ef80 [size=8]
I/O ports at ef00 [size=8]
Kernel driver in use: serial

and
dmesg | grep ttyS1
[ 1.584254] 0000:01:07.0: ttyS1 at I/O 0xef80 (irq = 19) is a XScale

dmesg | grep ttyS2
[ 1.584415] 0000:01:07.0: ttyS2 at I/O 0xef00 (irq = 19) is a XScale

the onboard com-port is working just fine:
dmesg | grep ttyS0
[ 1.583199] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 1.583706] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A



any ideas????????


here the specs to the system:
Intel core2duo 2.8
asrock n73v-s (nforce610i chipset)
4gb Ram
160.gb hdd

pci-karte with 2 com ports and CH352L chip

greetings 
Abu

---

### Post by Perpetuum_Mobile on 2009-08-04
i had just the same trouble.
it seemed, that scaner was not working on com-port of this device.
try to 'cat /dev/ttySx', where 'x' is between 1 & 2 and, i'm sure, you'll find what you want to ;)

---

