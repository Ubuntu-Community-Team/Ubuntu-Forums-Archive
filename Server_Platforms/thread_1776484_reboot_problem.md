---
title: "reboot problem"
date: 2011-06-06
forum: Server Platforms
---

### Post by mandza on 2011-06-06
i have problem with my reboot command.

sudo reboot and sudo halt -f now dont work (they dont reboot)
but sudo halt -p is shutting down my pc

how can i solve this problem???

---

### Post by arrrghhh on 2011-06-06
> **mandza said:**
> i have problem with my reboot command.

sudo reboot and sudo halt -f now dont work (they dont reboot)
but sudo halt -p is shutting down my pc

how can i solve this problem???

What do they do...?

Have you tried ```
sudo shutdown -r now
```?

It should be the same as sudo reboot, but maybe that alias got buggered somehow...?

---

### Post by mandza on 2011-06-07
Everything is going fine at the beginning and system says:
*will now restart
[ 563.34456456] Restarting system.

and after that it stop, dont do anything. :(
and i had tryed sudo shutdown -r now, it run same error.

---

### Post by arrrghhh on 2011-06-07
> **mandza said:**
> Everything is going fine at the beginning and system says:
*will now restart
[ 563.34456456] Restarting system.

and after that it stop, dont do anything. :(
and i had tryed sudo shutdown -r now, it run same error.

Do any services actually get killed?  You can verify if processes are going away with ps...

---

### Post by mandza on 2011-06-08
> **arrrghhh said:**
> Do any services actually get killed?  You can verify if processes are going away with ps...

All processes were killed but it doesnt reboot.
it shows all killed processes and after that "*now rebooting" message is showen but not reboot. that is my problem.

---

### Post by brettg on 2011-06-08
I always use sudo init 6 but maybe that's just me. Does that work?

---

### Post by arrrghhh on 2011-06-08
> **brettg said:**
> I always use sudo init 6 but maybe that's just me. Does that work?

lol that makes at least 3 ways to reboot...

To the OP, it's worth a shot... but I would like to know why the shutdown -r command doesn't work, I would think something like a disk umount is hanging (have you tried hooking up directly to the box?  I'm not sure if it spits out all that debug info in ssh shell sessions...)

---

### Post by blind2314 on 2011-06-08
> **arrrghhh said:**
> lol that makes at least 3 ways to reboot...
 
To the OP, it's worth a shot... but I would like to know why the shutdown -r command doesn't work, I would think something like a disk umount is hanging (have you tried hooking up directly to the box? I'm not sure if it spits out all that debug info in ssh shell sessions...)
 
 
This.
 
You'll need some sort of direct connection to the machine (whether it's a dedicated console NIC, a WYSE terminal, etc) to see all the available debug information, since SSH is turned off far before the box is completely down. Also, have you tried looking at /var/log/messages to see what's going on? My money is on a filesystem not relinquishing its lock or a process refusing to terminate.

---

### Post by mandza on 2011-06-08
Thanks all of you for your assistance, but i will install ubuntu server all over again. i hope that i will not have the same problem :(

---

### Post by arrrghhh on 2011-06-08
> **mandza said:**
> Thanks all of you for your assistance, but i will install ubuntu server all over again. i hope that i will not have the same problem :(

That's hardly a solution, especially if you have a hardware issue... I'm not saying you do, but you *could*...

---

### Post by mandza on 2011-06-08
i had install sistem and i still have the same error. it could be hardware issue but on windows it work without problems.
What can i do :) i will use it this way.

---

### Post by arrrghhh on 2011-06-08
> **mandza said:**
> i had install sistem and i still have the same error. it could be hardware issue but on windows it work without problems.
What can i do :) i will use it this way.

Follow the other directions?  Check /var/log/messages, hook a monitor up locally and watch the reboot process..

Edit - Or perhaps you're saying you are just going to use the server as a Windows box...?  Why even post then, pointless.

---

### Post by ruffEdgz on 2011-06-08
> **arrrghhh said:**
> Follow the other directions?  Check /var/log/messages, hook a monitor up locally and watch the reboot process..

Edit - Or perhaps you're saying you are just going to use the server as a Windows box...?  Why even post then, pointless.
I don't think he is going to turn this box into a Windows server but was telling us that the server in question worked well under a Windows OS, nothing more ;)

Did you try to force the reboot?
```
sudo reboot -f
```

I agree with arrrghhh's comment about finding a way to watch the reboot process happen to see why the 'reboot' does not work and that can help understand where the problem is coming from.

Also, once you have that monitor hooked up, run this command to see if we can get a bit more information from the reboot process:
```
sudo reboot --verbose
```

Cheers!

---

### Post by mandza on 2011-06-08
> **arrrghhh said:**
> Follow the other directions?  Check /var/log/messages, hook a monitor up locally and watch the reboot process..

Edit - Or perhaps you're saying you are just going to use the server as a Windows box...?  Why even post then, pointless.

I had checked /var/log/messages and i did not find any usefull information, but i will check it again tomorrow.

i will not use server as a windows box, i just sayed that i can reboot my pc without problem under windows. i was insalled it to check would it work.
--------------------------
NOT: i apologize for my bad english :)

---

### Post by chazz_tsc on 2011-06-08
Because of where it is stopping, it sounds like it may be an issue with how ACPI is responding to the shutdown request. What version of ACPI is set in your BIOS, and what other ACPI-related settings are there?

---

### Post by mandza on 2011-06-09
i had try sudo reboot -f but it fails to.
sudo reboot --verbose is giving this informations:

---------------------------------
The system is going down for reboot now!
* stopping web server apache2
init: tty4 main process (533) killed bu TERM signal
init: tty5 main process (542) killed bu TERM signal
init: tty2 main process (546) killed bu TERM signal
init: tty3 main process (549) killed bu TERM signal
init: tty6 main process (554) killed bu TERM signal
init: cron main process (569) killed bu TERM signal
init: tty1 main process (723) killed bu TERM signal
init: plymount-upsart-bridge main process (949) terminated with status 1
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting ok
Checking for running unattended-upgrades: *Asking all remaining processes to terminate... ok
* all processes ended within 1 seconds.... ok
* deconfiguring network interfaces... ok
* deactivating swap... ok
* unmounting weak filesystems... 
mount: /is busy
* will now restart
[ 166.883050] restarting system.
----------------------------

and system is stoping here, it not reboot.

---

### Post by arrrghhh on 2011-06-09
What is /is?

```
mount: /is busy
```

Seems like an issue.

---

### Post by mandza on 2011-06-09
is there anyone who can solve this problem :D ?

---

### Post by arrrghhh on 2011-06-09
> **mandza said:**
> is there anyone who can solve this problem :D ?

Uhm, I asked a question, would be nice to get an answer.  Seems we posted at almost the same time tho.

At any rate, it's also pretty rude to bump threads so quickly.  Give it at least 24 hrs - I usually give it 72, depending on the issue.

---

### Post by mandza on 2011-06-09
> **arrrghhh said:**
> Uhm, I asked a question, would be nice to get an answer.  Seems we posted at almost the same time tho.

At any rate, it's also pretty rude to bump threads so quickly.  Give it at least 24 hrs - I usually give it 72, depending on the issue.

Yes, ,it seems we posted at the same time :)
i'll wait...
--------------
mount: /is busy seems to be an issue but i dont know what and how to solve it :(

---

### Post by arrrghhh on 2011-06-09
> **mandza said:**
> mount: /is busy seems to be an issue but i dont know what and how to solve it :(

So you don't know what's mounted on /is?  Please figure it out and let us know.  That's not a "normal" mount point by any means.

---

### Post by fafa007 on 2011-06-22
> **arrrghhh said:**
> So you don't know what's mounted on /is?  Please figure it out and let us know.  That's not a "normal" mount point by any means.

I am having exactly the same problem.
The message is "/ is busy" and not '/is busy'
It's talking about / mount point (not /is)
 If somebody can help...

---

### Post by arrrghhh on 2011-06-22
> **fafa007 said:**
> I am having exactly the same problem.
The message is "/ is busy" and not '/is busy'
It's talking about / mount point (not /is)
 If somebody can help...

Oh der.  That makes a lot more sense now that I stop and think about it sheesh...

Well that is the problem.  I'm not sure if lsof would be best to figure out why the root partition is busy, I'm assuming some process didn't properly shut down, holding a lock on the partition...

---

### Post by fafa007 on 2011-06-22
> **arrrghhh said:**
> Well that is the problem.  I'm not sure if lsof would be best to figure out why the root partition is busy, I'm assuming some process didn't properly shut down, holding a lock on the partition...

             Well, finally, I’m not sure this message is linked to our problem.
When i use the command "halt --verbose", the command works perfectly but I can see shortly the message "/ is busy”!
Actually, this must be a warning message with no effect on the shutdown command…

---

### Post by arrrghhh on 2011-06-22
> **fafa007 said:**
> Well, finally, I&#8217;m not sure this message is linked to our problem.
When i use the command "halt --verbose", the command works perfectly but I can see shortly the message "/ is busy&#8221;!
Actually, this must be a warning message with no effect on the shutdown command&#8230;

/ can be busy, so long as eventually the lock is relinquished and the partition is successfully unmounted.  If it can't be unmounted, then shutdown will fail.

You say ```
halt --verbose
``` works but any of the other shutdown commands like ```
shutdown -r now
``` or ```
shutdown -h now
``` do not...?

---

### Post by mandza on 2011-06-25
> **arrrghhh said:**
> / can be busy, so long as eventually the lock is relinquished and the partition is successfully unmounted.  If it can't be unmounted, then shutdown will fail.

You say ```
halt --verbose
``` works but any of the other shutdown commands like ```
shutdown -r now
``` or ```
shutdown -h now
``` do not...?

it is the problem :)

---

### Post by pavlista on 2011-09-27
Bump
Same problem here... And same problem occured after installation
Intel Atom D525 MO
10.04.3. LTS server x64

---

### Post by martin.fletcher on 2011-09-28
Try 
```
 'sudo shutdown -pH now' 
```

This shuts down your linux box. If you want to reboot its simply 

```
 'sudo reboot' OR 'sudo shutdown -r now' 
```

---

### Post by trundlenut on 2011-09-28
I have a Toshiba laptop which will not reboot due to a ACPI issue, works fine with windows but not with Ubuntu, whether I try it via gnome or CLI.

Can you get the machine to go into standby and come back out again.  If not I would suspect this is a ACPI/BIOS issue.

---

### Post by caojinyu on 2011-09-28
maybe you can use the instruction "sudo shutdown -r now",the computer immediately reboot.if you want to reboot after several minutes,for example 5 minutes,so you can input the words "sudo shutdown -r +5".if you want to send out a message before reboot ,you can use parameter "-k message".for example "sudo shutdown -r +5 -k the computer will reboot after 5 minutes".

---

### Post by pavlista on 2011-09-29
Hello,
so shutdown commands are generally working
```
shutdown -PH now
``` L causes sysfans spins, but disk is off. Hard reset don´t work, power switch do.
```
shutdown -h now 
```L works ok
```
shutdown -r now
``` L do not work, freezes ( i presume "/" busy, i cant see over ssh),


after installing pm-utils ```
pm-hibernate
``` L works with no problems
others: pm-suspend-hybrid, pm-hibernate, pm-powersave do not (idk if there are some parameters need to be added)

i tried to reinstall once, i changed disk mode from IDE to AHCI and setup LVM partitions. I don´t check installation CD for defects, but its freshly and slowly burned. Installation freezes at the end at reboot time.

---

### Post by trundlenut on 2011-09-29
Depending on the machine it will have different capabilities, my Dell Poweredge server can only hibernate not suspend.

You can find out from somewhere in /proc what your machine capable in terms of suspend/hibernate etc.  Sorry can't remember off the top of my head where though.

---

### Post by Entilza on 2011-09-29
Just to link another similar issue from another post:

> I added acpi=force and reboot=acpi to my boot options and now it works fine.

Reference:

[http://ubuntuforums.org/showthread.php?t=1848968&page=2](http://ubuntuforums.org/showthread.php?t=1848968&page=2)

---

### Post by pavlista on 2011-09-29
Where exactly are these options located?

- i cant find boot/grub/menu.list (new grub :confused: )
- i dont know whitch script runs reboot command

Thank you :)

---

### Post by Entilza on 2011-09-29
edit /etc/defaults/grub

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

Add to that line as an example.

then:

sudo update-grub

---

### Post by pavlista on 2011-09-29
Thanks, problem solved!

Works perfectly! 
I added ```
acpi=force reboot=acpi
```

into 
```
/etc/default/grub
```

finall code looks like 
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi=force reboot=acpi"
```

btw. manual page BootOptions is empty..

---

### Post by mandza on 2012-04-30
i changed my server pc and problem was solved. :)

---

