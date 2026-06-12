---
title: "Problem starting jackd at boot"
date: 2009-08-18
forum: Ubuntu Studio
---

### Post by Ulrik Kjems on 2009-08-18
Hi
I want to start a multimedia real-time audioprocessing application using jackd at boot time running as a non-root user. I am using Ubuntu studio 8.04 
The core of the problem is as follows:

If I login normally (as str_uk) I can start jackd with real-time priority just fine, e.g. with 
   jackd -R -d alsa
so I'm pretty sure my /etc/security/limits.conf is ok (I append it at the end of this message)

However, I run into problems when trying to run jackd as user str_uk from an init script. What I do boils down to
  su str_uk -c "jackd -R -d alsa"
and I get the following error:
  ...
  JACK compiled with System V SHM support.
  cannot use real-time scheduling (FIFO at priority 10) [for thread -1210001744,   from thread -1210001744] (1: Operation not permitted)
  cannot create engine

The strange thing is that if I open a terminal in a gnome session and run the above "su" command as root, I get no error. But if I login as root from the console window (text mode) and issue the su-command I get the error. If I log in on the console as user "str_uk" I dont get the error. 
I am guessing that the settings in /etc/security/limits.conf are not being applied in the cases where I get the error. 

The output of "id" is given here, and it is the same when I get the error or not.
id:
uid=2206(str_uk) gid=1000(mha) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),109(lpadmin),110(admin),115(netdev),117(powerdev),1000(mha)

uname -a:
Linux kbnux-mha-3 2.6.24-24-rt #1 SMP PREEMPT RT Sat Jul 25 01:01:25 UTC 2009 i686 GNU/Linux

/etc/security/limits.conf:
@audio          -       rtprio          99
@audio - memlock unlimited

---

### Post by Ulrik Kjems on 2009-08-18
I found the solution myself:

In /etc/pam.d/su, uncomment the line
session    required   pam_limits.so

Problem solved!
I think this setting ought to be the default!

---

