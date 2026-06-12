---
title: "Power off/on virtual machines with vmware server 2.0"
date: 2009-12-03
forum: Virtualisation
---

### Post by any.linux12 on 2009-12-03
Hi!

I would like to power off a machine then use tar to back it up and then power it on again using the command line only but I haven't found any vmware command for that.

Any idea?

thanks

---

### Post by dcstar on 2009-12-04
> **any.linux12 said:**
> Hi!

I would like to power off a machine then use tar to back it up and then power it on again using the command line only but I haven't found any vmware command for that.

Any idea?

thanks

Use the **vmrun** command:

[http://download3.vmware.com/vmworld/2006/dvt4696.pdf](http://download3.vmware.com/vmworld/2006/dvt4696.pdf)
[http://www.vmware.com/pdf/vix160_vmrun_command.pdf](http://www.vmware.com/pdf/vix160_vmrun_command.pdf)

---

### Post by shairozan on 2009-12-15
Hey, 

I actually have a script I'll have to get for you when I get home. I wrote it to backup all of my production VMs until I moved to ESXI. 

What it does is check for all running machines and one by one does the following:

(1) Pause machine
(2) Snapshot
(3) CP machine to separate location
(4) Resume Machine
(5) Move to next machine

Just need to add a section to it for it to tar the directory and you'll be good to go. Then just run it on cron.

---

### Post by shairozan on 2009-12-16
Hey, 

Here is the script I wrote for backing up off of VMware Server 2.0. Let me know if you have any issues with it.

```
#! /bin/bash
#
#  Developed by Darrell Breeden
#  For Open Source Solutions
#
#  Distributed under the GPL license. You are free to make
#  modifications, as long as the original header remains untouched
#  minus new version information. 
#
#
#  V1.0     5-11-2009    Darrell breeden
#
############################################

### First, we will get a list of all running machines and dump that file to a temp location

vmrun -T server -h https://localhost:8333/sdk -u username -p password list | awk '{print $2}'| nl > /tmp/schedule

#  Schedule will appear in the following format
#   
#    1	running
#    2	moodle/moodle.vmx
#    3	mail.ossfb.com/mail.ossfb.com.vmx
#    4	support.ossfb.com/support.ossfb.com.vmx
#    5	new_web_server/new_web_server.vmx

#  Now we will declare some variables

counter=2
schedule=/tmp/schedule
vm=`grep $counter $schedule | awk '{print $2}'`
user= user
password= password
address=https://my.server.ip.address:8333/sdk
max=`tail -1 /tmp/schedule | awk '{print $1}'`&& max=$(($max + 1))
source='/var/lib/vmware/Virtual\ Machines'
dest='/media/disk/vmbackup'


### Sanity Check : Checks to Make Sure user is Root

if [ "$(id -u)" != "0" ]; then
   echo "This script must be run as root" 1>&2
   exit 1
   else echo "User Validation Completed"
        echo "You are Root. Executing Script"
        sleep 5
fi

### Now we will build the for / while loop to suspend the machines.

while [ $counter -lt $max ] ;
do 

echo "Suspending $vm"
vmrun -T server -h $address -u $user -p $password suspend "[standard] $vm"
counter=$(($counter + 1))
vm=`grep $counter $schedule | awk '{print $2}'`
sleep 60

done

### Now we will copy the virtual machines to the End Destination

echo "Machines are Backing Up"

cp -vrf $source $dest

echo "Machines Have Been Succesfully Backed Up"

sleep 180

### Now We will Resume all of the Virtual Machines

counter=2
vm=`grep $counter $schedule | awk '{print $2}'`

while [ $counter -lt $max ] ;
do 

echo "Starting $vm"
vmrun -T server -h $address -u $user -p $password start "[standard] $vm"
counter=$(($counter + 1))
vm=`grep $counter $schedule | awk '{print $2}'`
sleep 60

done

echo "All Files are Backed Up Completely." | mailx -a "Subject: Backup complete on $(date +%m/%d/%Y)" admin@ossfb.com

rm $schedule
```

---

