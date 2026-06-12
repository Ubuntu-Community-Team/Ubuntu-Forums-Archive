---
title: "AppArmor is not working"
date: 2014-03-05
forum: Ubuntu Development Version
---

### Post by The Keeper on 2014-03-05
Last weekend I set up a demo server with 13.10 and upgraded it to 14.04 as I don't have the option to install 14.04 right away. Regardless, sometime after upgrade I noticed that AppArmor wasn't running as sudo apparmor_status outputs "apparmor module is not loaded".

So I re-installed apparmor packages by running:
sudo apt-get clean && sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install --reinstall apparmor apparmor-profiles apparmor-utils libapparmor-perl

And rebooted the server. Module still not loaded. So I tried sudo service apparmor restart, the command completes without any output whatsoever. Likewise running sudo dmesg | grep -i apparmor produces no output.

Using my last trick, I edited /etc/default/grub.
Line GRUB_CMDLINE_LINUX_DEFAULT="nomdmonddf nomdmonisw" to "nomdmonddf nomdmonisw apparmor=1 security=apparmor". Then ran update-grub and rebooted.

dmesg now outputs the changes to grub, but nothing else.
Command line: BOOT_IMAGE=/bzImage-3.10.23-xxxx-std-ipv6-64 root=/dev/sda5 ro nomdmonddf nomdmonisw apparmor=1 security=apparmor nomdmonddf nomdmonisw
Kernel command line: BOOT_IMAGE=/bzImage-3.10.23-xxxx-std-ipv6-64 root=/dev/sda5 ro nomdmonddf nomdmonisw apparmor=1 security=apparmor nomdmonddf nomdmonisw

What gives?

---

### Post by Cavsfan on 2014-03-05
This is what is installed on my system:

[ATTACH=CONFIG]250884[/ATTACH]

HTH

---

### Post by Cavsfan on 2014-03-05
Oops. I don't have a server just Ubuntu 64 bit if that matters concerning apparmor.

---

### Post by ventrical on 2014-03-06
> **The Keeper said:**
> Last weekend I set up a demo server with 13.10 and upgraded it to 14.04 as I don't have the option to install 14.04 right away. Regardless, sometime after upgrade I noticed that AppArmor wasn't running as sudo apparmor_status outputs "apparmor module is not loaded".



  I am just curious as to which method you used to upgrade.

Regards..

---

### Post by The Keeper on 2014-03-06
sudo do-release-upgrade -d

I even reinstalled latest kernel just now, but that didn't help either. Dmesg, apparmor_status and service apparmor restart still all outputting blank.

---

### Post by ventrical on 2014-03-06
> **The Keeper said:**
> sudo do-release-upgrade -d

I even reinstalled latest kernel just now, but that didn't help either. Dmesg, apparmor_status and service apparmor restart still all outputting blank.


To be perfectly honest I have never used that method so I cannot comment sepcifically.  However, I have found that during devlopment cycle that the 'upgrade mangler' is to be avoided.

 I most always use these methods here:


[http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873](http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873)

 Also .. to upgrade any exisiting Ubuntu, one can use the daily Trusty .iso (I do). It will save all of your important files, bookmarks etc.. looks like your system became broke because of the upgrade method (but I'll wait for someone else to jump in here).

 Using Synaptic may help but then you are running server. Can  you install fvwm-crystal and run synaptic from there and see if that resolves the apparmor issue? (as it has done here on many occasions)..

Regards..

---

### Post by ventrical on 2014-03-06
I am just wondering if it is too late to try this :

```

aptitude update && aptitude  safe-upgrade


```

but you would have to install aptitude first.

---

### Post by The Keeper on 2014-03-06
As far as dpkg and apt are concerned dependencies have been met, so there is nothing for aptitude to do. I do not have physical access to the server so installing fvwm-crystal wouldn't do me much good, unless I go for the trouble of setting up remote desktop of some sort from shell.

If nobody else has any good ideas I'll be reinstalling the server tomorrow and will try plain old apt instead of do-release-upgrade.

---

### Post by ventrical on 2014-03-06
Found this ..

Not sure it will help.


[LIST]
[*]                          AppArmor can be disabled, and the kernel module unloaded by entering the following:             
 sudo /etc/init.d/apparmor stop
sudo update-rc.d -f apparmor remove
[*]                         To re-enable AppArmor enter:         
 sudo /etc/init.d/apparmor start
sudo update-rc.d apparmor defaults
[/LIST]
Edit:

 Just a theory .. but  during upgrade/update there is a program that asks if you want to have certain programs restarted when they are terminated..etc...  I am just assuming that apparmor was disabled during your upgrade and may  only need to be enabled again.

---

### Post by ventrical on 2014-03-06
> **The Keeper said:**
> 

And rebooted the server. Module still not loaded. So I tried sudo service apparmor restart, the command completes without any output whatsoever. Likewise running sudo dmesg | grep -i apparmor produces no output.



 Yes .. it looks like you excluded some code.

 Good luck.

---

### Post by The Keeper on 2014-03-06
> **ventrical said:**
> 
sudo update-rc.d apparmor defaults

This produces following output:
update-rc.d: warning: default start runlevel arguments (2 3 4 5) do not match apparmor Default-Start values (S)
update-rc.d: warning: default stop runlevel arguments (0 1 6) do not match apparmor Default-Stop values (none)
 Adding system startup for /etc/init.d/apparmor ...
   /etc/rc0.d/K20apparmor -> ../init.d/apparmor
   /etc/rc1.d/K20apparmor -> ../init.d/apparmor
   /etc/rc6.d/K20apparmor -> ../init.d/apparmor
   /etc/rc2.d/S20apparmor -> ../init.d/apparmor
   /etc/rc3.d/S20apparmor -> ../init.d/apparmor
   /etc/rc4.d/S20apparmor -> ../init.d/apparmor
   /etc/rc5.d/S20apparmor -> ../init.d/apparmor

But module still doesn't load.

---

### Post by grahammechanical on 2014-03-06
Just to clarify a small point. According to this you did in fact use the official command to upgrade a server to the development branch.

[https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html](https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html)

Regards.

---

### Post by ventrical on 2014-03-06
But there is that disclaimer...

---

### Post by ventrical on 2014-03-06
> **The Keeper said:**
> This produces following output:
update-rc.d: warning: default start runlevel arguments (2 3 4 5) do not match apparmor Default-Start values (S)
update-rc.d: warning: default stop runlevel arguments (0 1 6) do not match apparmor Default-Stop values (none)
 Adding system startup for /etc/init.d/apparmor ...
   /etc/rc0.d/K20apparmor -> ../init.d/apparmor
   /etc/rc1.d/K20apparmor -> ../init.d/apparmor
   /etc/rc6.d/K20apparmor -> ../init.d/apparmor
   /etc/rc2.d/S20apparmor -> ../init.d/apparmor
   /etc/rc3.d/S20apparmor -> ../init.d/apparmor
   /etc/rc4.d/S20apparmor -> ../init.d/apparmor
   /etc/rc5.d/S20apparmor -> ../init.d/apparmor

But module still doesn't load.

 I guess my next question would be if you plan to use the upgraded server as a production machine or a testing machine? The reason that I ask is because close to the end of the testing cycle as we are there are normally some real doozies (borks) that seem to come down the pipe now and again. I am not saying that this is what happened to your machine. @graham is correct - but something happened during the upgrade I would think. Unless there is another method for a fix ? I would not know .. only what I have learned so far from others here.

Regards...

---

### Post by ventrical on 2014-03-06
And this ... at least thats the official askubuntu take on it..  So the two official ubuntu pages contradict each other.
Nice:)


[http://askubuntu.com/questions/328072/do-release-upgrade-to-13-04-crashed](http://askubuntu.com/questions/328072/do-release-upgrade-to-13-04-crashed)

---

### Post by The Keeper on 2014-03-07
Well, the problem has been solved. There never was a problem with the Ubuntu upgrade. The problem was that hosting provider had installed custom kernel and made it default. All I had to do was to edit /etc/default/grub and change GRUB_DEFAULT=0 to 1.

Now that the server is running standard kernel, apparmor is working. Unfortunately I figured this out AFTER I reinstalled the server.

---

