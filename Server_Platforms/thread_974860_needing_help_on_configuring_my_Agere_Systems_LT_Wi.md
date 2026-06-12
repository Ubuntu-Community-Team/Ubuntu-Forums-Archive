---
title: "needing help on configuring my Agere Systems LT WinModem  on my server"
date: 2008-11-07
forum: Server Platforms
---

### Post by kustomjs on 2008-11-07
Hi Guys
I need help on configuring my Agere Systems LT WinModem onto my server 8.04 and I am using hylafax and avantfax.

---

### Post by windependence on 2008-11-08
Check out this thread:

[http://sudan.ubuntuforums.com/showthread.php?t=918368](http://sudan.ubuntuforums.com/showthread.php?t=918368)

-Tim

---

### Post by kustomjs on 2008-11-08
i tried to update the drivers here is what i got:

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S2   S3

---

### Post by kustomjs on 2008-11-08
here is the error im getting when trying to install the driver

make -C /lib/modules/2.6.24-16-server/build SUBDIRS=/home/tim/agrsm modules
make: *** /lib/modules/2.6.24-16-server/build: No such file or directory.  Stop.
make: *** [module] Error 2
tim@server2:~/agrsm$ sudo make install
make -C /lib/modules/2.6.24-16-server/build M="/agrsm" modules_install
make: *** /lib/modules/2.6.24-16-server/build: No such file or directory.  Stop.
make: *** [install] Error 2

---

### Post by windependence on 2008-11-08
Have you unzipped and untarred the files?

-Tim

---

### Post by kustomjs on 2008-11-08
yes I have tim and still alots of troubles

here is the errors im getting [http://timscomputerrepair.net/errors.htm](http://timscomputerrepair.net/errors.htm)

---

### Post by kustomjs on 2008-11-08
everytime I do sudo wvdialconf wvtest I get this:
Scanning your serial ports for a modem.

Modem Port Scan<*1>: Scanning ttySM0 first, /dev/modem is a link to it.
ttySM0<Info>: No such device or address
Modem Port Scan<*1>: SM0
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S2   S3


all I want to do is just fax just not using dial up

---

### Post by kustomjs on 2008-11-08
ok I took out my 56k from the computer and here what I found on it 
its model number 90109 and fcc number 2D7USA-35107-M5-E and it says its from smart modular technologies and chipset is Lucent 1648T00 and I tried updating the drivers I was able to get it to update but when I try to create a modem inside of avantfax it just show modem---please wait but I cant dial out or even try to send out a fax. what do I do next? and I do know it works for faxes because modem was in my xp machine it was working great.

---

### Post by kustomjs on 2008-11-08
alright I guess I will be switching to windows server 2003 since lack of drivers for this modem.

---

