---
title: "automatic unmount on reboot"
date: 2010-04-01
forum: Server Platforms
---

### Post by ithaca on 2010-04-01
Hi, I have a problem while rebooting my 9.10 server when I have SAN partition mounted. The message is something about the swap that can not be cleaned during the process. All works if I unmount the partitions before shutting down or rebooting.
So I though to create a bash script that unmounts the parts during runlevel 0 and 6.
I've created a simple script like this in /etc/init.d:
#!/bin/bash
umount /mnt/xxx

and the I've done:

update-rc.d script start 1 0 6 .

In this way the srcipt should run as the first during the runlevels 0 and 6. But the problem is not solved.
Do you think that this is correct? Or do you have any suggestions?

Thanks a lot

---

### Post by ithaca on 2010-04-02
Please, do you have suggestions?
Is quite important....

---

### Post by jrssystemsnet on 2010-04-02
Need more info - like log messages when you shutdown or reboot that might indicate whether your script is even being run (and if you can't find any, adding a line to your script to deliberately log a message when it's run, then trying again).

Keep in mind that if, say, you have a Samba share on that mounted filesystem, and Samba is still running, your script will fail to unmount it.  You have to get all active processes that might be using that mount to stop **before** you try to unmount it.

---

### Post by ithaca on 2010-04-02
I'm not sure to have done the right things but I added this row:
#!/bin/bash
log_daemon_msg "unmounting san" >> /home/san.log
umount /mnt/san0

Nothing happens and the message isn't shown in /var/logmessages neither in /var/log/dsmeg or daemon.log

The mounted file system is empty ext3 formatted.

Thanks

---

### Post by jrssystemsnet on 2010-04-02
You're not using log_daemon_msg correctly, and may not have sourced the function either.  Try using logger instead.

**/usr/bin/logger "unmounting san"**

---

### Post by koenn on 2010-04-02
you've set your script as a 'start' script on runlevels 0 and 6, which means it will run when the system *enters* those rl. This may not be what you want, it's probably better to have a K-script for rl 2,3,4,5, i.e. run when leaving those runlevels.


Also, check that this script actually runs during reboot/shutdown, eg by adding a simple statement that you can check afterwards (eg touch /etc/scripttest  - this will create a file /etc/scripttest if the script actually runs



Did you set the script +x ?

---

### Post by ujodarko on 2010-04-05
Maybe you'll know how to set up automatic unmount and shutting down HDD before computer that is turned off?

You see....

I have Ubuntu installed on 2.5" external HDD. That HDD is powered by USB port, and works fine just as it is an internal drive.

So, system is running from that external drive, and drive has to work nearly second before phisically shutting down computer. Now, HDD is turned off in the same time as the computer stays without power, and HDD allways makes that noise as it is going to die.

Can it be solved somehow?

---

### Post by ithaca on 2010-04-06
Ok solved setting the correct execution rights. I thought that creating that file as root it should have had the +x... 
Thanks a lot.

For ujodarko I'm sorry but I'm not so expert as you see :)

---

