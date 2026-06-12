---
title: "Windows XP (guest)Modem issue (no response from modem)"
date: 2009-12-12
forum: Virtualisation
---

### Post by nuccx2001 on 2009-12-12
I have Ubuntu 9.10 64bit Host with a Windows XP 32bit Guest
Virtual Box 3.1.0 R55467
Simple RS232 Modem (USRobotics 56k external)

Settings>Serial Ports>Port Mode: is 'Host Device' and Port/File Path: is '/dev/ttyS0'

```
dmesg | grep ttyS0
```Reveals 
[    0.562093] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.562365] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

```
ls -l /dev/ttyS0
```Reveals
crw-rw---- 1 root dialout 4, 64 2009-12-11 14:49 /dev/ttyS0

I am a member of dialout

In my guest OS I see the Com port is there...  but I cant query the modem on it. 

EDIT: I can query it, but no response..

Manually installed Driver on Guest os...

Am I missing something on Host box?

also posted on Virtualbox Forums

---

### Post by nuccx2001 on 2009-12-13
Is there a better choice for a modem?  Do I need an internal one to make this happen...  I truly would rather not have to Duel boot If I dont have to,  But the modem is necessary for a legacy app.

---

### Post by Zweitaktmotor on 2009-12-19
Hi, I have exactly the same problem and it seems to be hardware related.

Here is my configuration:

Acer Aspire M1640
56K external Rockwell modem

Linux Mit 8 (aka Ubuntu 9.10)

All the diagnostic commands you mention give me exactly the same results.

Upon some further testing (even booting the machine to DOS and using an old terminal that I know to work perfectly), I found that I can send commands to the modem and it will receive them, but no modem messages will get back to the PC. It looks like the serial port only works in one direction, but I cannot find anything in the BIOS to adjust it.

Please also see my lenghty thread here:

[http://www.linuxquestions.org/questions/linux-hardware-18/modem-troubles-774967/](http://www.linuxquestions.org/questions/linux-hardware-18/modem-troubles-774967/)

I must stress that this has nothing to do with Linux or the modem. It is a problem with the pc hardware, specifically the serial port.

---

