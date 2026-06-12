---
title: "HP openview DP 5.5, win cell manager can't find linux scsi tape device (hardy)"
date: 2011-02-04
forum: Server Platforms
---

### Post by m.ardito on 2011-02-04
Hi all,
i have a hp openview data protector win cell manager, and two device licenses, one of which was  bound to an hp autoloader (which is now dead) attached to the same win  machine by external uwscsi cable. i am now using the other device  license to make backups to a file device, on a big lan storage, until i  get back with a working tape device.

now, as the autoloader is dead, i wish to replace it with a new hp  ultrium3 960 drive i just bought, and i am trying to make a new setup:  attach the drive on a linux box, and make the win cell manager pilot  future backups to the tape on the linux box.

first, to make things clear, i have to admit i tried this on a ubuntu  8.04 box (ibm x205 server), i know rhel and sles are officially  supported, could try centos maybe, but i feel it could work also on  debian based distributions, and would like to try everything to make it  work here...

anyway, apparently ubuntu system sees the tape with no problems:

* i tried lsscsi and it reports:
[1:1:3:0]    tape    HP       Ultrium 3-SCSI   D22D  /dev/st1

* i installed the hp LTT utility (also not supported on debians, anyway it works) and it can query the drive:
Libraries/Autoloaders:
Processors/Enclosures:
   1 IBM SERVERAID (Address: 10.15.0[1-/dev/sg2])
   2 IBM YGLv3 S2 (Address: 11.8.0[1-/dev/sg4])
Drives:
   3 SEAGATE DAT    9SP40-000 (Address: 0.6.0[0-/dev/sg0])
   4 HP Ultrium 3-SCSI (Address: 11.3.0[1-/dev/sg3])
Other Devices:
   5 IBM SERVERAID (Address: 10.0.0[1-/dev/sg1])

On the linux box i installed both DA and MA agents, and made the win  cell manager import client, and i can see the DA and MA installed from  there (as for now, i did not check the "client is device server"  checkbox).

But, as i try to add the new device, i have an error as i always get a "no device found" both with 
* Add device...
* Autoconfigure devices

I searched hp forums
[http://forums11.itrc.hp.com/service/forums/categoryhome.do?categoryId=251](http://forums11.itrc.hp.com/service/forums/categoryhome.do?categoryId=251)

and tried a suggested command:
sudo ./devbra -dev

i just note that the install script installed the "omni" folder in "/usr", instead of "/opt"

but devbra hangs a few minutes and then exits with no output, 
and no trace is in /var/log/syslog 
or /usr/omni/log/debug.log 
or /usr/omni/log/inet.log 

can someone help to find out what is not working?

Thanks, Marco

---

### Post by m.ardito on 2011-02-09
I've attached here a debug log i had running:

$/usr/omni/bin/devbra -dev -debug 1-500

any hint, anyone? ...please...

Marco

---

### Post by m.ardito on 2011-02-09
...hate to say this but maybe could help someone...
devbra worked instantly as soon as i put a tape inside the drive... GRRR

and, voilà, the win cell manager autodiscovered the new drive!

Marco

---

