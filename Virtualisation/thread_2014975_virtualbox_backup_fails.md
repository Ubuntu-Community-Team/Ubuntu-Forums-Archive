---
title: "virtualbox backup fails"
date: 2012-07-02
forum: Virtualisation
---

### Post by Angusnz on 2012-07-02
Hi All
I am fairly new to ubuntu and Oracle virtual box and have the following problem.
 
Details first - using Ubuntu 10.04 and Oracle Virtual Box 4.1.12.r77245
 
I was asked to set up a backup of the virtual boxes on this machine every week.
 
I've set up a script, which checks which vms are running, powers them down in turn, rsyncs the files to a separate storage area and then restarts the box.
This is cronned and logs output to a log file.
 
When run as a simple command in the shell - no problem.
However when running via cron the boxes restart but are inaccessible, so I then have to power them down and restart them from the host.
 
So I thought instead of using the poweroff option, let's try it with the acpipowerbutton option. 
Tested this and the machines came back up but with a locked session on each.
 
Has anybody any ideas as it's severely bugging me - i've looked at tkms etc, but no joy.
 
Code can be pasted along with error messages (none in the logs).
All help appreciated - as I'm sure people must be backing up their vms all over the place
 
Thanks

---

### Post by drdos2006 on 2012-07-02
Are you running the cron command as "root" or as the owner of the vm ?
Are you backing up .vdi files?

regards

---

### Post by Habitual on 2012-07-02
doh!

---

### Post by Angusnz on 2012-07-02
Hi
 
cron is running as owner of the vms (not root), and yes it is backing up the vdi files

---

### Post by CharlesA on 2012-07-02
What command or script are you using to start/stop the VMs?

---

### Post by Angusnz on 2012-07-02
Hi
 
the core of the script is
 
/usr/bin/vboxmanage controlvm 'vmname' acpipowerbutton
sleep 7
/usr/sbin/rsync -rp 'sourcedir' 'destination
sleep 10
/usr/bin/vboxmanage startvm 'vmname'
 
It's all within a do loop, as I pipe the runningvms into a shell array
 
Originally I was using poweroff  - and then tried using acpipowerbutton - both fail
 
Thanks

---

### Post by CharlesA on 2012-07-02
Take a look at my script here:
[http://charlesa.net/scripts/linux/virtualbox-script-ubuntu.php](http://charlesa.net/scripts/linux/virtualbox-script-ubuntu.php)

Also check out the links in that page.

Work on getting the VM stop/start problem fixed and deal with the rsync later.

---

### Post by Angusnz on 2012-07-02
Hi Charles and thanks for this.
 
A couple of questions, as my script apart from the rsync doesn't su to the vm owner as it is the owners crontab. Do you do this for a reason? As I've neevr used su in shell on purpose?
Also - you go for the UUID wheras my script goes for the vmname?
Is this likely to be a cause? as I'm quite happy to change that.
 
I shall comment out the rsync and see what happens and let you know
 
Many thanks

---

### Post by CharlesA on 2012-07-02
> **Angusnz said:**
> Hi Charles and thanks for this.
 
A couple of questions, as my script apart from the rsync doesn't su to the vm owner as it is the owners crontab. Do you do this for a reason? As I've neevr used su in shell on purpose?
Also - you go for the UUID wheras my script goes for the vmname?
Is this likely to be a cause? as I'm quite happy to change that.
 
I shall comment out the rsync and see what happens and let you know
 
Many thanks
My script is meant to be run as root or as another user with sudo ability, which is why I used:

```
# User who is running the VMs (Change this!)
VBOXUSER=vboxuser

# Environmental Variables (Do Not Modify!)
SU="sudo -H -u $VBOXUSER"
```

That makes the command run as the user who is running the vbox VMs.

If the script is running as the same user the VMs are running sd, you shouldn't need to use sudo.

As for the UUIDs, I use them so I can handle VM names with spaces but, as long as your VM names don't have spaces, you should be ok to use just the name.

---

### Post by Angusnz on 2012-07-04
Hi
Tried the script, in the hope it would restart the vms in the event of a reboot caused by accident or power outage (which has happened a couple of times).
 
So did the following:
 
sudo and halted the system
waited a while
then restarted the system
loggged on to the console and the vms were running.
Forgot to check if they were running without me loggin on
 
Simulated a power outage by pulling the cables
waited again
restarted the system
tried to ping the vms - no response after 5 minutes
logged on to the console to discover the vms were not started
 
Any ideas - and this is before I start trying to back them up
 
Thanks
 
Will report back on the halt scenario in half an hour, to check whether the vms start without a console login

---

### Post by Angusnz on 2012-07-04
nope - had to log on in order for the vms to be started.
this is driving me nuts

---

### Post by CharlesA on 2012-07-04
> **Angusnz said:**
> Hi
Tried the script, in the hope it would restart the vms in the event of a reboot caused by accident or power outage (which has happened a couple of times).
 
So did the following:
 
sudo and halted the system
waited a while
then restarted the system
loggged on to the console and the vms were running.
Forgot to check if they were running without me loggin on
 
Simulated a power outage by pulling the cables
waited again
restarted the system
tried to ping the vms - no response after 5 minutes
logged on to the console to discover the vms were not started
 
Any ideas - and this is before I start trying to back them up
 
Thanks
 
Will report back on the halt scenario in half an hour, to check whether the vms start without a console login

Was the machine hooked up to a UPS, so it had a controlled shutdown? The script I use only starts the VMs up if they are in a "saved" state, so it doesn't start all the VMs up.

If you want all the vms powered on, you can change the start block to read:

```

start)
for v in $ALLVMS; do
        if [[ -n $($SU $VBOXMANAGE showvminfo $v | grep saved) ]]; then
                echo -e "Waiting for VM \"$(getVMName $v)\" to power on..." && $SU $VBOXMANAGE startvm $v --type headless 1> /dev/null && echo "VM \"$(getVMName $v)\" started successfully!"
        fi
# If the previous loop has an error, the loops exits and returns an error.
        if [[ $? -ne 0 ]]; then
                echo "There was an error starting $(getVMName $v)! Try starting it manually to see what the problem is."; break
        fi
done
if [[ -z $($SU $VBOXMANAGE showvminfo $v | grep saved) ]]; then
        echo "No Saved VMs to Start!"
fi
;;

```

To:

```
start)
for v in $ALLVMS; do
	echo -e "Waiting for VM \"$(getVMName $v)\" to power on..." && $SU $VBOXMANAGE startvm $v --type headless 1> /dev/null && echo "VM \"$(getVMName $v)\" started successfully!"

# If the previous loop has an error, the loops exits and returns an error.
        if [[ $? -ne 0 ]]; then
                echo "There was an error starting $(getVMName $v)! Try starting it manually to see what the problem is."; break
        fi
done
;;

```

---

### Post by Angusnz on 2012-07-04
Many thanks - that worked - I should have spotted that line - very loose thinking on my part.
Now I can concentrate on getting the rsync working - and remember to RTFM
:D
 
I originally used cut -d in my first script rather than awk, as it was less typing :)

---

