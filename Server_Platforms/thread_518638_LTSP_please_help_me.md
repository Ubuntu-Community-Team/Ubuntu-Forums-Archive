---
title: "LTSP please help me"
date: 2007-08-06
forum: Server Platforms
---

### Post by krotaz on 2007-08-06
I've a big big problem 

I'm trying to install LTSP on my Ubuntu 7.04 I've followed the [ubuntu quick install guide]("https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall") but it's doesn't work.

The thin client it's not an old machine, its a vmware server machine.

The problem is that when the virtual machine loads the dhcp is recognized and then goes to the tftp step, here is where everything crashes and a [COLOR="Red"]TFTP open timeou[/COLOR] error appears.

I've tryed modifyint all the conf files in dhcp, tftp, but still the same problem. Ive a mother board with 3 network cards (2 wired and a wireless) in case you need information.

Please help me

Bye

---

### Post by krotaz on 2007-08-06
> **krotaz said:**
> I've a big big problem 

I'm trying to install LTSP on my Ubuntu 7.04 I've followed the [ubuntu quick install guide]("https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall") but it's doesn't work.

The thin client it's not an old machine, its a vmware server machine.

The problem is that when the virtual machine loads the dhcp is recognized and then goes to the tftp step, here is where everything crashes and a [COLOR="Red"]TFTP open timeou[/COLOR] error appears.

I've tryed modifyint all the conf files in dhcp, tftp, but still the same problem. Ive a mother board with 3 network cards (2 wired and a wireless) in case you need information.

Please help me

Bye

well I belive that the problem is that the tftp server is not running because this link

**[http://wiki.ltsp.org/twiki/bin/view/Ltsp/TFTP](http://wiki.ltsp.org/twiki/bin/view/Ltsp/TFTP)**

sais that if I execute this command
[B]
netstat -apn | grep ":69 "[/B]

the output must be something like this

**udp      0    0 0.0.0.0:69           0.0.0.0:*                    6122/in.tftpd**

but the output I get is

**udp        0      0 0.0.0.0:69              0.0.0.0:*                          -**

as you can see almost everithing is the same but the last colum because in the first example I'm supposed to get the 6122/in.tftpd with I guess it's the pid and the name of the process but in my output I get a simple   -   with I belive means that there's no pid and so the process it's not running.

am I ok???

thanks

---

### Post by sdowney717 on 2007-08-15
edit 
etc/default/tftpd-hpa and set DAEMON="yes"
probably have to reboot.

Do you know where the tftp server files are located in the filesystem?

#Defaults for tftpd-hpa
RUN_DAEMON="no"
OPTIONS="-l -s /var/lib/tftpboot"

---

