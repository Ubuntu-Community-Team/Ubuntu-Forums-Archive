---
title: "Sun Fire V100 won't boot"
date: 2007-01-11
forum: Sun Sparc Users
---

### Post by ineo on 2007-01-11
Wondering if anyone can help. My Sun Fire V100 won't boot during installation. It hangs directly after the 'Booting Linux...'

I've even got it to go 1 step further and give me an error reading my PCI:
PCI: Address space collision on region 6 [000001ff00080000:000001ff000bffff] of device 0000:00:05.0

After trying to check the md5sum and the CD's integraty, and then burning a 2nd CD just to be sure. But still not luck.

Any idea's out there?

Thanks

---

### Post by jsl123 on 2007-01-24
Are you sure it doesn't boot? I get the same error and after a short pause, the boot process continues. Also during the installation procedure  i had to edit the silo.conf file and add
[FONT="Courier New"]ide=nodma[/FONT] to the append line. Although before i did this it wouldn't get past the SILO prompt

---

### Post by ineo on 2007-01-24
Yup pretty sure, it did continue twice, but still hung eventually after selecting country and keyboard type. At the SILO prompt all I can do is hit Enter or Recover, but I don't even have anything installed yet. Any suggestions?
Thanks

---

### Post by Cal6171 on 2007-01-28
I am having the same problem with a Sun Ultra 10 with Creator 3D.  The CD boots and then after the initial checks I get the "Booting Linux" prompt that stays there for hours.   That is as far as I have gotten.  

I will check the .version command.  I did recently install additional RAM to bring it up to 512MB and installed Solaris 10 which works OK, but slowly.  

Just no luck going through the install sequence on Ubuntu for Sparc.

---

### Post by Cal6171 on 2007-01-28
Where does one find the silo.conf file.  I searched for it, but did not find it.  Running Solaris 10 on the Ultra 10 Creator 3D with OBP 3.29.0 2000/12/20 and POST 3.1.0 2000/06/27.

---

### Post by Moulton on 2007-02-04
Try booting from a cold power-on, or after doing a 'reset-all' at the Open Boot prompt.

I found that booting Linux was erratic unless the machine was in a completely reset state.

An ordinary 'reset' before booting generally resulted in a failure partway into the booting process.

---

### Post by surlyjake on 2007-08-20
make sure you boot using "Linux ide=nodma" at the SILO prompt.

---

### Post by ElusiveMind on 2007-09-05
I am hoping someone can help me with this. I have a SunFire V100 that I inherited when I took my current job. While we are upgrading hardware, I need to find a use for this machine - and part of this means installing linux.

For whatever reason, I can't seem to get this machine to boot the installer CD. Does anyone have any information on what I need to do in order to get it to boot? I've tried several things I've looked up on google with no success. I'll admit I'm completely unfamiliar with the Sun LOM environment and frankly find it a bit frustrating.

Any guidance would be tremendously appreciated.

EM

---

### Post by shale on 2007-09-13
assuming you can connect to A LOM via minicom or something similar, this is what I did to boot to the CD:

#  hold the switch by the power cord in the down position for 7 seconds ( until both green lights turn off in the back of the sunfire v100 )
# when you use minicom it should come up with a "lom > " promt

   1. lom > bootmode forth
   2. lom > poweron
   3. ... wait for it to power on, you should see an "ok " prompt
   4. ok > setenv auto-boot? false
   5. ok > reset
   6. ... wait for it to restart
   7. ok > boot cdrom
   8. ... it should directly boot to the cdrom now 
(there are suggestions to boot with "install ide=nodma" when you get to the cd boot prompt, however my installation is still hanging at 85% complete on the "Installed update-manager-core " when trying to install Feisty ) 


( here is where I got some information [http://www.dbforums.com/showthread.php?t=1007175](http://www.dbforums.com/showthread.php?t=1007175) )

---

### Post by Scootin159 on 2007-09-17
> **shale said:**
> assuming you can connect to A LOM via minicom or something similar, this is what I did to boot to the CD:

#  hold the switch by the power cord in the down position for 7 seconds ( until both green lights turn off in the back of the sunfire v100 )
# when you use minicom it should come up with a "lom > " promt

   1. lom > bootmode forth
   2. lom > poweron
   3. ... wait for it to power on, you should see an "ok " prompt
   4. ok > setenv auto-boot? false
   5. ok > reset
   6. ... wait for it to restart
   7. ok > boot cdrom
   8. ... it should directly boot to the cdrom now 
(there are suggestions to boot with "install ide=nodma" when you get to the cd boot prompt, however my installation is still hanging at 85% complete on the "Installed update-manager-core " when trying to install Feisty ) 


( here is where I got some information [http://www.dbforums.com/showthread.php?t=1007175](http://www.dbforums.com/showthread.php?t=1007175) )
Thank you for this information.  I got to the same 85% with 7.04, but had no problems with the install of 6.06 LTS.

---

### Post by sys64738 on 2007-11-09
I have never been able to get a SunFire V100 with a Kernel version 2.6.17 and newer to work . mostly due to network problem. "modeprobe tulip" dont work either

so, if any of you are having problem loading Linux, THAT would be your problem.

ubuntu 6.06-1 server works  and 7.10server wont.

kernel 2.6.17 and newer DO NOT WORK with SunFire V100.
please use 2.6.16 and older

could someone make a fix please for V100's?????????????

---

### Post by qrwe on 2007-12-19
My heart almost stopped of joy when my server finally even *booted* after following the last two advices (including trying 6.06 LTS).
..just to begin to beat normal again of boredom when it still didn't work; the following message appear before the server freeze:

[    1.707368] PCI: Address space collision on region 6 [000001ff00080000:000001ff000bffff] of device 0000:00:05.0

Has anyone else seen this before?

---

### Post by qrwe on 2008-01-08
..and in the following thread, someone answered why. Sadly, it's simply incompatible with my Sunfire V100. :'(
[http://ubuntuforums.org/showthread.php?t=528094](http://ubuntuforums.org/showthread.php?t=528094)

---

