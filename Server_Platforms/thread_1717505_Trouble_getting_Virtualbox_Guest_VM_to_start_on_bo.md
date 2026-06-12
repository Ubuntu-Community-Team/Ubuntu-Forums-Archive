---
title: "Trouble getting Virtualbox Guest VM to start on boot"
date: 2011-03-29
forum: Server Platforms
---

### Post by hawk2010 on 2011-03-29
Hi All,

I'm running the host server on Ubuntu 10.04 LTS (64bit) . I'm using virtual box. I want to automatically for one of the guest vritualboxes to start on reboot. Following is already done without a success. Please help me in solving this.

1. I have created the following shell script
#!/bin/bash
/usr/bin/nohup /usr/bin/VBoxHeadless --startvm "VMNAME" 2> /dev/null &

2.From the current logged on user I did a crontab -e and did the following

crontab -e

@reboot /bin/sh /home/myaccount/shellscript.sh
Please note that I do not encrypt the home directory and sufficient permissions are there.

Upon reboot the virtual machine doesn't start. Any idea why?

---

### Post by hawk2010 on 2011-04-18
Any idea guys ? I'm still waiting

> **hawk2010 said:**
> Hi All,

I'm running the host server on Ubuntu 10.04 LTS (64bit) . I'm using virtual box. I want to automatically for one of the guest vritualboxes to start on reboot. Following is already done without a success. Please help me in solving this.

1. I have created the following shell script
#!/bin/bash
/usr/bin/nohup /usr/bin/VBoxHeadless --startvm "VMNAME" 2> /dev/null &

2.From the current logged on user I did a crontab -e and did the following

crontab -e

@reboot /bin/sh /home/myaccount/shellscript.sh
Please note that I do not encrypt the home directory and sufficient permissions are there.

Upon reboot the virtual machine doesn't start. Any idea why?

---

### Post by SeijiSensei on 2011-04-18
Run the command from /etc/rc.local.  I've never seen the "@reboot" construct, but /etc/rc.local is the last script to be run at startup.

---

### Post by Sirkyuubi on 2011-04-18
You don't use crontab for booting. I believe, correct me if im wrong, try adding your script to your init.d folder.

---

### Post by Sirkyuubi on 2011-04-18
Sorry for the delay in posting... Im not the best person to try to explain this, but since noone else is helping out I will try help as best I can with my limited knowledge.

If you simply want a script to run on boot then you could add it to your default run level folder. As you may know linux distro's have different run levels. When any of these run levels are activated your system just goes to the corresponding run level folder and runs everything in it. However the folder names and the specifics of how it works is different with every distribution. I don't actually know what the default(boot) run level folder is for ubuntu, but if I had to make a guess I would say it's the init.d folder. Furthermore the run level folders have a certain order in which the files are executed. This is, if I remember correctly, determined by filename. If you are to add your script to the default run level folder I would recommend that you find a way to name it right so it get executed last. You wouldn't want the system to try to execute it before the services required to run it were loaded.

Let us know how things turn out for you.

---

### Post by SeijiSensei on 2011-04-18
> **Sirkyuubi said:**
> Sorry for the delay in posting... Im not the best person to try to explain this, but since noone else is helping out I will try help as best I can with my limited knowledge.

Well, I don't have "limited knowledge" about this.  Placing commands you want to run at boot in /etc/rc.local is the easiest solution.  It's certainly not worth creating an /etc/init.d/ script and its associated symlinks for the various run-levels just to run a single line command.

---

### Post by hawk2010 on 2011-04-19
Thanks a lot ! I will give it a shot and see.

---

### Post by hawk2010 on 2011-04-19
Hi. I added the following to rc.local but no luck : ( Any log file i can refer to?

/usr/bin/nohup /usr/bin/VBoxHeadless --startvm "Proxy" 2> /dev/null &

---

### Post by SeijiSensei on 2011-04-19
Let's start from the beginning:

Did you try running that command from a terminal prompt as root with sudo?

```
sudo /usr/bin/nohup /usr/bin/VBoxHeadless --startvm "Proxy" &
```

I removed the 2>/dev/null since that sends error reports into a "black hole." 

[Headless]("http://www.virtualbox.org/manual/ch07.html#vboxheadless") runs the server without any display output.  It's designed to run the VM on a remote machine that you view over the network with VRDP.  Is that what you want?

Also I don't see nohup being used in any of the examples in the manual.

---

### Post by hawk2010 on 2011-04-21
Actually Seiji, I'm have created and running the vm as a normal user and that command without sudo works fine. I included the blackhole so there won't be anything displayed back. My intention is that I have a server on which this vm runs. Currently when the server is rebooted or coming up from shutdown I have to manually start the vm which is a pain. So I want it to be started after the OS boots up and most probably for it to gracefully shutdown when its going for the power off.I'm using headless since i'm running Ubuntu server with text mode and easier manage. I could have used the VBoxManage too. The reason for me to use nohup is that its prevents shutdown of the VBoxHeadless process when i log out. Otherwise it will just die

---

### Post by Zeosa on 2011-04-21
Here's what I did...

create a script in /etc/init.d

```

#startvm.sh


#!/bin/bash


MACHINES=`cat /etc/vbox/machines.conf`

for i in $MACHINES ; do
        /usr/bin/VBoxManage startvm $i --type vrdp
done

```

then create another script

```

#stopvm.sh
#!/bin/bash

declare -a RUNVMLIST
vmnum=0

for running in $(VBoxManage -nologo list --long runningvms |grep Name: | grep -v UUID)
do
echo $running is running
name=$(VBoxManage -nologo showvminfo $running | grep "Name:" | grep -v UUID | awk 'BEGIN{FS="Name: "}{print $2}')
RUNVMLIST=( "${RUNVMLIST[@]}" "$name")
vmnum=$(($vmnum + 1))
done


if [ ! "$running" ]
then
echo "No VMs running"
else
echo "Running VMs = "${RUNVMLIST[*]}
echo "Number of VMs Running = "${#RUNVMLIST[*]}
fi

echo "All open VMs will be shutdown"
for vm in ${RUNVMLIST[*]}
do
VBoxManage controlvm $vm savestate
sleep 20
echo "$vm was shutdown gracefully"
done

```

then link startvm.sh in /etc/rc2.d
```

ln -s /etc/init.d/startvm.sh /etc/rc2.d/S99startvm

```

create another link in rc6.d

```

ln -s /etc/init.d/stopvm.sh /etc/rc6.d/K09stopvm

```

Then create the /etc/vbox directory

In that directory, create a plain text file listing the names of the machines you wish to start at boot...

```

vmname1
vmname2
vmname3
...

```

While probably not the most graceful solution, this starts my vm's at boot, and gracefully shuts them down at reboot/poweroff...

---

