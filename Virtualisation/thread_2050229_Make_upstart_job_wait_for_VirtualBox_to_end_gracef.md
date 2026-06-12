---
title: "Make upstart job wait for VirtualBox to end gracefully"
date: 2012-08-30
forum: Virtualisation
---

### Post by seanlano on 2012-08-30
Hello everyone,

I've been trying for hours and hours to figure out a way of running a VirtualBox machine when my system boots using upstart. I've been able to get it to boot successfully, but I can't seem to make upstart wait for it to close properly. Instead the Virtual Machine just gets killed, and loses all its active state. The guest is configured to immediately shutdown when it receives the acpishutdown signal from VBoxManage. 

This is my upstart script:
```
#Start Transmission's Virtual Machine on boot

description	"Transmission Virtual Machine"

start on (local-filesystems and net-device-up IFACE=eth0)
stop on runlevel [016]

console log

respawn
respawn limit 5 10
kill timeout 20

pre-stop script
	exec sudo -u sean VBoxManage controlvm "Transmission Server" acpipowerbutton
	inactive=0
	while [ "$inactive" == "0" ]; do
		inactive=`vboxmanage showvminfo "Transmission Server" | grep -E "No active facilities." | wc -l`
		sleep 0.5s
	done
end script

script
	exec sudo -u sean VBoxHeadless -startvm "Transmission Server"
end script
```

I had tried it without my attempt at the loop, and obviously that didn't work. I also tried putting all of the pre-stop script in an external script - and that partly worked, although then upstart would hang indefinitely and I also could not re-start the Virtual Machine without first rebooting the host. So that approach went from no delay, to an infinite delay.

This must be possible to do! How can I just tell upstart to wait for 20 seconds for the guest to turn off?

---

### Post by CharlesA on 2012-08-30
I gave up on using upstart for my vbox script.

You can find my script here:
[http://charlesa.net/scripts/linux/virtualbox-script-ubuntu.php](http://charlesa.net/scripts/linux/virtualbox-script-ubuntu.php)

There is also a script another member was working on which can be found here:
[http://ubuntuforums.org/showthread.php?t=1844885](http://ubuntuforums.org/showthread.php?t=1844885)

---

### Post by seanlano on 2012-08-30
Hmm, I really would have preferred to use upstart - it's much more user-friendly. Would this be a bug possibly? Even if I make the pre-stop command the VBoxManage savestate command, it will save the state but then get killed and not restore from it. Virtual Box lists it as "Aborted". Upstart just will not wait any time at all for it to end.

---

### Post by seanlano on 2012-08-30
Having said that, the init.d script does work perfectly. Thanks!

---

### Post by CharlesA on 2012-08-30
Glad you got it (sorta) sorted. :)

Don't forget to mark the thread as solved from thread tools.

---

### Post by seanlano on 2012-08-30
Well, I'm not 100% happy with it though... :P 
The upstart job (if it worked) would boot my VM without needing it to be in the "Saved State", and it would also respawn it if it happened to shut itself down. 

Since upstart appears not to like Virtual Box, how would I add the respawn to the init.d script? Modifying it to boot my VM instead of all saved VMs shouldn't be too hard, but the respawn I'm not sure about.

---

### Post by CharlesA on 2012-08-30
Check out the thread I linked to earlier by doas777

---

### Post by seanlano on 2012-08-30
Ah yes, I see now. This is the post: [http://ubuntuforums.org/showpost.php?p=11283453&postcount=28]("http://ubuntuforums.org/showpost.php?p=11283453&postcount=28"). Very handy. 

Thanks!

---

### Post by seanlano on 2012-08-30
So I suppose it's reasons like this example that explain why upstart hasn't completely replaced all of the init.d scripts...

---

### Post by CharlesA on 2012-08-30
> **seanlano said:**
> Ah yes, I see now. This is the post: [http://ubuntuforums.org/showpost.php?p=11283453&postcount=28]("http://ubuntuforums.org/showpost.php?p=11283453&postcount=28"). Very handy. 

Thanks!
That would be it.

---

### Post by valery1707 on 2013-02-26
This conf works with Ubuntu 12.04 and VirtualBox 4.2:

```

description "Virtual Machine"

start on (local-filesystems and net-device-up IFACE=eth0)
stop on runlevel [016]

env vm_uid_or_name=d82c5d45-e113-4332-8de3-51c6251057c8
env vm_comment=some-comment
env uid=username-under-which-vm-was-created

console log

#respawn
#respawn limit 5 10
kill timeout 120

script
    exec sudo -u $uid VBoxHeadless --startvm "$vm_uid_or_name" --comment "$vm_comment"
end script

pre-stop script
    echo "Send ACPI poweroff event to $vm_uid_or_name"
    sudo -u $uid VBoxManage controlvm "$vm_uid_or_name" acpipowerbutton
    echo "Wait while state is 'running'"
    while sudo -u $uid VBoxManage showvminfo "$vm_uid_or_name" | grep -E "State:\s+running" -q
    do
        sleep 0.5s
    done
    echo "Complite ACPI waiting"
end script

```

---

### Post by tombert on 2013-04-07
I know it is already solved, but my upstart configuration and two scripts here do gracefully shutdown even on reboot, shutdown or power-button events:

[http://askubuntu.com/questions/101294/safely-close-virtualbox-machine-on-host-reboot/278705#278705](http://askubuntu.com/questions/101294/safely-close-virtualbox-machine-on-host-reboot/278705#278705)

See the post from *tombert*.

---

### Post by tombert on 2013-04-07
> **valery1707 said:**
> This conf works with Ubuntu 12.04 and VirtualBox 4.2:

```

description "Virtual Machine"

start on (local-filesystems and net-device-up IFACE=eth0)
stop on runlevel [016]

env vm_uid_or_name=d82c5d45-e113-4332-8de3-51c6251057c8
env vm_comment=some-comment
env uid=username-under-which-vm-was-created

console log

#respawn
#respawn limit 5 10
kill timeout 120

script
    exec sudo -u $uid VBoxHeadless --startvm "$vm_uid_or_name" --comment "$vm_comment"
end script

pre-stop script
    echo "Send ACPI poweroff event to $vm_uid_or_name"
    sudo -u $uid VBoxManage controlvm "$vm_uid_or_name" acpipowerbutton
    echo "Wait while state is 'running'"
    while sudo -u $uid VBoxManage showvminfo "$vm_uid_or_name" | grep -E "State:\s+running" -q
    do
        sleep 0.5s
    done
    echo "Complite ACPI waiting"
end script

```

This script power-offs the machine immediately since upstart is sending the SIGTERM to the process. After the timeout it send the SIGKILL. 
You can improve it by adding:
```
kill signal SIGCONT
```

Also the acpipowerbutton does not work reliably always since Windows might show the shutdown confirmation dialog preventing from shutdown. You could improve this by sending the shutdown directly to the guest using guestcontrol.

Next I would recommend running the stop script before entering the runlevel 0, which could be solved by using:
```
stop on starting rc RUNLEVEL=[!2]
```

---

