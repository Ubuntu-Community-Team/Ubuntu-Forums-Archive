---
title: "Auto execute this command on server start."
date: 2012-12-18
forum: Server Platforms
---

### Post by ibrahim.k on 2012-12-18
Hi there,

I want from my server to execute these command automatically on server start.
/usr/bin/VBoxManage startvm "VM1" --type headless
/usr/bin/VBoxManage startvm "VM2" --type headless
/usr/bin/VBoxManage startvm "VM3" --type headless

How can I do this please?

Regads,

---

### Post by fdrake on 2012-12-18
```

cd /etc/rc2.d/
sudo su
echo "#/bin/sh" >> S23VBM
echo "/usr/bin/VBoxManage startvm \"VM1\" --type headless" >> S23VBM
echo "/usr/bin/VBoxManage startvm \"VM2\" --type headless" >> S23VBM
echo "/usr/bin/VBoxManage startvm \"VM3\" --type headless" >> S23VBM
chmod +x S23VBM
exit

```

---

### Post by ibrahim.k on 2012-12-18
> **fdrake said:**
> ```

cd /etc/rc2.d/
sudo su
echo "#/bin/sh" >> S23VBM
echo "/usr/bin/VBoxManage startvm \"VM1\" --type headless" >> S23VBM
echo "/usr/bin/VBoxManage startvm \"VM2\" --type headless" >> S23VBM
echo "/usr/bin/VBoxManage startvm \"VM3\" --type headless" >> S23VBM
chmod +x S23VBM
exit

```

After doing the steps mentioned above and restarting my server, 
The virtual machines did not start automatically, 
The output of /usr/bin/VBoxManage list runningvms
 was nothing.
i had to start them manually.
This is the output of "uname -a"
Linux ubuntu 2.6.32-28-server #55-Ubuntu SMP Mon Jan 10 23:57:16 UTC 2011 x86_64 GNU/Linux

regards.

---

### Post by fdrake on 2012-12-18
i am using kernel 3.5.0-17-generic
but i do not see the reason why it should not work.
what runlevel do you use:
```

runlevel

```
also can you try to run the script if it works manually. you have to "sudo su{ to root.

edit
oh wait if i am not wrong the server uses runlevel 3 not 2 .... can you doublke check with me..


edit:
this seems to confirm my hypothesis
from [http://ubuntuforums.org/showthread.php?t=843646](http://ubuntuforums.org/showthread.php?t=843646)
> Runlevels

A runlevel is used to tell the OS how far up you want it to boot. Generally, we use runlevel 1 for debugging/recovery mode, runlevel 3 for normal text (no graphics mode) and runlevel 5 for normal with graphics. Runlevels 0 and 6 are when the computer is shutting down/restarting. Runlevels 2 and 4 are user-defined and used for doing crazy stuff without modifying the standard 1,3 and 5 runlevels.

so you have to go to the folder "/etc/rc3.d/" not "/etc/rc2.d/"

---

### Post by ibrahim.k on 2012-12-18
This was the output 
N 2
I Will do the whole thing again using "/etc/rc3.d/

Thnx

---

### Post by oldgraf on 2012-12-18
I start my vm from shortcut with this command 
/usr/lib/virtualbox/VirtualBox -startvm "VM1"
May be try to change Vbonmanage with Virtualbox and add - sign before startvm

---

### Post by Lars Noodén on 2012-12-18
The above is the start  of making a System V init script, but needs a few more steps before it becomes functional.  What you might do instead is put what you need run into /etc/rc.local  That gets run at the end of the boot sequence after the other services are started.

---

### Post by ibrahim.k on 2012-12-18
> **fdrake said:**
> i am using kernel 3.5.0-17-generic
but i do not see the reason why it should not work.
what runlevel do you use:
```

runlevel

```also can you try to run the script if it works manually. you have to "sudo su{ to root.

edit
oh wait if i am not wrong the server uses runlevel 3 not 2 .... can you doublke check with me..


edit:
this seems to confirm my hypothesis
from [http://ubuntuforums.org/showthread.php?t=843646](http://ubuntuforums.org/showthread.php?t=843646)


so you have to go to the folder "/etc/rc3.d/" not "/etc/rc2.d/"


I have done the same steps using "/etc/rc3.d/" but it didn't work as well!

---

### Post by ibrahim.k on 2012-12-19
> **Lars Noodén said:**
> The above is the start  of making a System V init script, but needs a few more steps before it becomes functional.  What you might do instead is put what you need run into /etc/rc.local  That gets run at the end of the boot sequence after the other services are started.

Could you please let me know what should I do with the rc.local file in order to start my virtual machines automatically?

---

### Post by Lars Noodén on 2012-12-19
Edit /etc/rc.local  Enter there what you would have manually typed.  Make sure that it all goes there before 'exit 0'

---

### Post by ibrahim.k on 2012-12-20
> **Lars Noodén said:**
> Edit /etc/rc.local  Enter there what you would have manually typed.  Make sure that it all goes there before 'exit 0'

Did I do it the right way? Because it didn't work.
Regards,

!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
/usr/bin/VBoxManage startvm "ugarit2003" --type headless
exit 0

---

### Post by fdrake on 2012-12-20
something is not right about your command on my advice and on lars' you have typed: > /usr/lib/virtualbox/VirtualBox startvm "VM1"  
instead on post #6 you type:
> 
/usr/lib/virtualbox/VirtualBox **[COLOR="Red"]-[/COLOR]**startvm "VM1"


check that the command is typed correctly...

i've checked online and the reason why it doesn't work is a misstype in your command.
check here the manual:[http://dev.man-online.org/man1/VirtualBox/](http://dev.man-online.org/man1/VirtualBox/)

----------------------------------------------------------------------------------------


[U][B]your command shoyuld have been on both our suggestions this:
> 
/usr/lib/virtualbox/VirtualBox **[COLOR="Red"]--[/COLOR]**startvm "VM1"
 double minus sign !![/B][/U]

---

### Post by oldgraf on 2012-12-20
I am with Virtualbox version 4.1 and just realise that with 4.2 there is new wayhttps://forums.virtualbox.org/viewtopic.php?f=11&t=51529

---

### Post by ibrahim.k on 2012-12-20
> **oldgraf said:**
> I am with Virtualbox version 4.1 and just realise that with 4.2 there is new wayhttps://forums.virtualbox.org/viewtopic.php?f=11&t=51529

[B]
I am also using the version 4.1.2.[/B]

---

### Post by ibrahim.k on 2012-12-20
> **fdrake said:**
> 
----------------------------------------------------------------------------------------


[U][B]your command shoyuld have been on both our suggestions this:
 double minus sign !![/B][/U]

[SIZE=2]
This is the current content of the /etc/rc.local
Did i do it the right way? because the machine did not start automatically on system boot. [/SIZE]

  GNU nano 2.2.2                                           File: /etc/rc.local                                                                                              

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
/usr/lib/virtualbox/VirtualBox --startvm "VM1" 
exit 0

---

### Post by CharlesA on 2012-12-20
> **Lars Noodén said:**
> The above is the start  of making a System V init script, but needs a few more steps before it becomes functional.  What you might do instead is put what you need run into /etc/rc.local  That gets run at the end of the boot sequence after the other services are started.

Indeed. There are a few different scripts that do what the OP is asking.

One is here:
[http://ubuntuforums.org/showthread.php?t=1844885](http://ubuntuforums.org/showthread.php?t=1844885)

;)

---

### Post by LHammonds on 2012-12-20
If it needs to run as root, type "sudo su" and then add the commands to the crontab schedule.

The specific time to use is "@reboot" which will run the command whoever the system restarts.

However, you need to ensure the VMs are shutdown cleanly before you shutdown or reboot the server.

LHammonds

---

### Post by CharlesA on 2012-12-20
> **LHammonds said:**
> However, you need to ensure the VMs are shutdown cleanly before you shutdown or reboot the server.

Agreed. That was one of the main reasons I spent time writing up my original startup/shutdown script.

So far it has worked wonders.

---

### Post by ibrahim.k on 2012-12-23
Sorry guys but still don't know what do I have to do! :(

---

### Post by spynappels on 2012-12-23
Is the script actually running, you can check using ```
ps -ef | grep -i virtualbox 
```If it is not,send the output from the script, including error messages, to a log file and try again.

You  could also try adding it to your crontab as an ```
@reboot
``` line...

---

### Post by CharlesA on 2012-12-23
Make sure you are running the script as the user who is running the VMs, otherwise nothing will happen because VirtualBox VMs are user specific.

---

### Post by spynappels on 2012-12-23
> **CharlesA said:**
> Make sure you are running the script as the user who is running the VMs, otherwise nothing will happen because VirtualBox VMs are user specific.

True, which is why I used cron and added the command to the specific user's crontab.

---

### Post by CharlesA on 2012-12-23
> **spynappels said:**
> True, which is why I used cron and added the command to the specific user's crontab.

+1. The way I did it was using sudo to run the commands as a different user, but running the commands in that user's crontab would have works too if I had not chosen to write up a init.d script. ;)

---

### Post by ibrahim.k on 2012-12-24
> **spynappels said:**
> Is the script actually running, you can check using ```
ps -ef | grep -i virtualbox 
```If it is not,send the output from the script, including error messages, to a log file and try again.

You  could also try adding it to your crontab as an ```
@reboot
``` line...

This is the output>
```
ugarit@ubuntu:~$ ps -ef | grep -i virtualbox
ugarit    1363     1  0 Dec22 ?        00:00:09 /usr/lib/virtualbox/VBoxXPCOMIPCD
ugarit    1369     1  0 Dec22 ?        00:00:35 /usr/lib/virtualbox/VBoxSVC --auto-shutdown
ugarit    1382  1369  9 Dec22 ?        04:41:29 /usr/lib/virtualbox/VBoxHeadless --comment vm1 --startvm 36954419-b0ee-473a-8223-6c15c72d696e --vrde config
ugarit    2540  1369  1 Dec22 ?        00:48:47 /usr/lib/virtualbox/VBoxHeadless --comment vm2 --startvm dc8616d9-1539-48e8-a622-688d0ba7110b --vrde config
ugarit   18889 18871  0 01:50 pts/0    00:00:00 grep --color=auto -i virtualbox

```

---

### Post by ibrahim.k on 2012-12-24
....

---

### Post by spynappels on 2012-12-24
> **ibrahim.k said:**
> This is the output>
```
ugarit@ubuntu:~$ ps -ef | grep -i virtualbox
ugarit    1363     1  0 Dec22 ?        00:00:09 /usr/lib/virtualbox/VBoxXPCOMIPCD
ugarit    1369     1  0 Dec22 ?        00:00:35 /usr/lib/virtualbox/VBoxSVC --auto-shutdown
ugarit    1382  1369  9 Dec22 ?        04:41:29 /usr/lib/virtualbox/VBoxHeadless --comment vm1 --startvm 36954419-b0ee-473a-8223-6c15c72d696e --vrde config
ugarit    2540  1369  1 Dec22 ?        00:48:47 /usr/lib/virtualbox/VBoxHeadless --comment vm2 --startvm dc8616d9-1539-48e8-a622-688d0ba7110b --vrde config
ugarit   18889 18871  0 01:50 pts/0    00:00:00 grep --color=auto -i virtualbox

```

Ok, that shows vm1 and vm2 are at least running.

The next question is what leads you to suspect they are not? Can you not access them through RDP? or through SSH? Is the networking sound, as in have you got the VMs networked correctly through NAT or Bridged connections?

For RDP, have you installed the correct modules to enable RDP access to the console?

---

### Post by ibrahim.k on 2012-12-24
> **spynappels said:**
> Ok, that shows vm1 and vm2 are at least running.

The next question is what leads you to suspect they are not? Can you not access them through RDP? or through SSH? Is the networking sound, as in have you got the VMs networked correctly through NAT or Bridged connections?

For RDP, have you installed the correct modules to enable RDP access to the console?

I know that machines are running because I have started them manually,
I want them to start automatically on server startup.

---

### Post by Lars Noodén on 2012-12-24
> **ibrahim.k said:**
> I know that machines are running because I have started them manually,
I want them to start automatically on server startup.

Then you could try launching them via /etc/rc.local or make either an upstart script or as System V script.  In any of those you could put something like the following:

```

su -c "/usr/lib/virtualbox/VBoxHeadless --comment vm2 --startvm dc8616d9-1539-48e8-a622-688d0ba7110b --vrde config" -l ibrahim.k
```

Obviously subsitute "ibrahim.k" for the user you want the VM to run as.

---

### Post by spynappels on 2012-12-24
> **ibrahim.k said:**
> I know that machines are running because I have started them manually,
I want them to start automatically on server startup.

Ok, let me be clearer. Create the script as mentioned earlier, reboot and then do the ps -ef command. This will confirm whether or not the script ran correctly. Also log the error messages from the strtup script to a file, so you can check them after a boot.

---

### Post by ibrahim.k on 2012-12-26
> **spynappels said:**
> Ok, let me be clearer. Create the script as mentioned earlier, reboot and then do the ps -ef command. This will confirm whether or not the script ran correctly. Also log the error messages from the strtup script to a file, so you can check them after a boot.

This is the output of the "ps -ef"
[http://paste.ubuntu.com/1467063/](http://paste.ubuntu.com/1467063/)

---

### Post by spynappels on 2012-12-26
Ok, that means that the vms are not running. So either the script did not run, or it encountered an error and exited.

My next step would be to alter your script slightly to send all output and error messages to a logfile, and then reboot. Then check the log file to see if there is output which indicates what errors, if any, were encountered. For examples of how to alter the script, do a search for redirecting stdout and stderr to file.

Did you also consider trying the crontab route?

---

### Post by fdrake on 2012-12-26
just pointing out how onethere person was able to fix the problem it seems to be related to the spach at boot time!

[http://ubuntuforums.org/showthread.php?p=12423106#post12423106](http://ubuntuforums.org/showthread.php?p=12423106#post12423106)

---

