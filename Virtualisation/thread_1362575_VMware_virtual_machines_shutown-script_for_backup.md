---
title: "VMware: virtual machines shutown-script for backup"
date: 2009-12-23
forum: Virtualisation
---

### Post by Sisma86 on 2009-12-23
Hi all! This is my bash script that I use to shutdown virtual machine before Bacula starts its backup. This is my system:

Ubuntu Server 8.04 (2.6.24-24-server)
Bash 3.2.39(1)-release
VMware Server 2.0.2 build-203138

```

#Written by Simone Berchielli
#Released under GPL v2.0 license

#!/bin/bash

#Variables

VM_ARRAY=(64 144 128)    #This is the only variable you need to change. This array contains virtual machines you are trying to shutdown for backup.
                                         #Machines shutdown in the order you give in this array. In this case 1st=64, 2nd=144 and so on. To get the number of
                                         #a virtual machine just launch "vmware-vm-cmd vmsvc/getallvms" and it will be prompted a list.

NUMBER_VM=${#VM_ARRAY[@]}
ERROR_CONTROL=0
ON="Powered on"
OFF="Powered off"

#Script start

LOGDATE=`date +%D" "%H":"%M":"%S`
echo "--- VM_SHUTDOWN LOG "$LOGDATE" ------------------------------------------------------">>VM_shutdown_LOG.txt

for ((i=0;i<$NUMBER_VM;i+=1));do

    LOGDATe=`date +%D" "%H":"%M":"%S`
    echo $LOGDATE" - Virtual machine No. "${VM_ARRAY[${i}]}" is shutting down..." >> VM_shutdown_LOG.txt

    VM_STATE=`vmware-vim-cmd vmsvc/power.getstate ${VM_ARRAY[${i}]}| grep Powered`
    
    CYCLE=1
    ATTEMPTS=0
    
    if [ "$VM_STATE" = "$ON" ];then
    
        while [ "$VM_STATE" = "$ON" -o $CYCLE -eq 10 ]; do
        
            if [ $CYCLE -eq 1 -o $CYCLE -eq 6 ];then

                : $((CYCLE=CYCLE+1))
                : $((ATTEMPTS=ATTEMPTS+1))

                LOGDATE=`date +%D" "%H":"%M":"%S`
                echo $LOGDATE" - Sending shutdown command, attempt No. "$ATTEMPTS >> VM_shutdown_LOG.txt

                vmware-vim-cmd vmsvc/power.shutdown ${VM_ARRAY[${i}]}
                sleep 60
                VM_STATE=`vmware-vim-cmd vmsvc/power.getstate ${VM_ARRAY[${i}]}| grep Powered`

            else
            
                VM_STATE=`vmware-vim-cmd vmsvc/power.getstate ${VM_ARRAY[${i}]}| grep Powered`
                : $((CYCLE=CYCLE+1))
            
            fi
            
        done
        
        if [ "$VM_STATE" = "$OFF" ];then

        
            LOGDATE=`date +%D" "%H":"%M":"%S`    
            echo $LOGDATE" - Virtual machine No. "${VM_ARRAY[${i}]}" successfully shutted down at attempt No. "$ATTEMPTS >> VM_shutdown_LOG.txt

        else
            
            LOGDATE=`date +%D" "%H":"%M":"%S`
            echo $LOGDATE" - Virtual machine No. "${VM_ARRAY[${i}]}" shutting down failed!" >> VM_shutdown_LOG.txt
            : $((ERROR_CONTROL=ERROR_CONTROL+1))
            
        fi
        
    else
        LOGDATE=`date +%D" "%H":"%M":"%S`
        echo $LOGDATE" - Virtual machine No. "${VM_ARRAY[${i}]}" is already off" >> VM_shutdown_LOG.txt
        
    fi
done

if [ $ERROR_CONTROL -eq 0 ]; then

    LOGDATE=`date +%D" "%H":"%M":"%S`
    echo $LOGDATE" - Virtual machines successfully shutted down" >> VM_shutdown_LOG.txt
    
    exit 0
    
else

    LOGDATE=`date +%D" "%H":"%M":"%S`
    echo $LOGDATE" - Powering on virtual machine No. "${VM_ARRAY[${i}]}"..." >> VM_shutdown_LOG.txt

    for ((i=0;i<NUMBER_VM;i+=1)); do

        VM_STATE=`vmware-vim-cmd vmsvc/power.getstate ${VM_ARRAY[${i}]}| grep Powered`
    
        if [ "$VM_STATE" = "$OFF" ]; then

            LOGDATE=`date +%D" "%H":"%M":"%S`
            echo $LOGDATE" - Sending power on command" >> VM_shutdown_LOG.txt

            vmware-vim-cmd vmsvc/power.on ${VM_ARRAY[${i}]}
            sleep 30

            LOGDATE=`date +%D" "%H":"%M":"%S`
            echo $LOGDATE" - Virtual machine No. "${VM_ARRAY[${i}]}" has been powered on" >> VM_shutdown_LOG.txt
            
        else
            LOGDATE=`date +%D" "%H":"%M":"%S`
            echo $LOGDATE" - Virtual machine No. "${VM_ARRAY[${i}]}" is already on" >> VM_shutdown_LOG.txt
        
        fi
    done
    
    exit 1
    
fi

```This script produces a log file called VM_shutdown_LOG.txt placed in the same directory of the script!

---

### Post by Sisma86 on 2009-12-23
- How it works -

I need to stop virtual machines before my backup system (in this case Bacula) starts to save virtual machines files and folders. So i decided to write this scrip that do this. Virtual machines are stored in an array. You can put many machine as you want. The shutdown order begins from the machine at index 0. Each machine must be off to have a "0 exit". Otherwise the script powers on again machine shutted down in this way and the exit is 1. The script tries the shutdown twice per machine.

I hope it will be helpful!

---

