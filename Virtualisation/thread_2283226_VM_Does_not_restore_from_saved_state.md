---
title: "VM Does not restore from saved state"
date: 2015-06-20
forum: Virtualisation
---

### Post by Jonners59 on 2015-06-20
I created a script to save the state of my open VMs and allow me to shut down or reboot my machine nicely.  As the state was saved, it then automatically opened quickly where I left off upon re starting the machine via another script.

I recently had a problem with an upgrade from 14:10 to 15:04 which has resulted in an almost complete rebuild, though nothing should have changed for the scripts as they are saved on a separate Home directory.  However, I was testing the VM as I noticed it was not working, by using the basic test commands.
```
VBoxManage -nologo list runningvms
``` to show me running VMs, just to check the name.
```
VBoxManage -nologo controlvm 3cxServer savestate
```  To test to saved state
```
VirtualBox --startvm 3cxServer &
```  To restore from saved state.

Note the VM is "3cxServer"

It seems to save the state, but when it restores it fails to open the saved machine properly.  It says "Aborted".  I have to open via the VirtualBox app and then it starts in the Windows "machine didn't shut down properly..." screen.

My shutdown script which is adapted from others, is below, though not ready to use it due to the above errors:
```
                                                     #!/bin/bash            
            # /shut.vm            
            

                        ################################################## ######################            
                        VBoxManage -nologo controlvm 3cxServer savestate            
                        ################################################## ######################            
                        

                        zenity --text="Click YES if you want to Shutdown or Reboot. Click No to resume." --title="Shutdown or Reboot?" --width="320" --height="150" --question            
            closeorcancel=$?            
            if [ "${closeorcancel}" == "0" ]            
            then            
            echo "You chose to Shutdown or Reboot"            
            else            
            echo "You chose No to resume your work"            
            exit            
            fi            
            zenity --text="Click YES if you want to Reboot. Click No to Shutdown." --title="Shutdown or Reboot?" --width="320" --height="150" --question            
            shutorboot=$?            
            if [ "${shutorboot}" == "0" ]            
            then            
            echo "You chose to Reboot"            
            if [ ! ${RUNVMLIST
[*]}]            
            then            
            echo "No VMs open, straight to reboot"            
            sudo -H -u server /etc/init.d/vboxdrv stop            
            sudo /etc/init.d/preload stop            
            sudo /sbin/shutdown -r now            
            else            
            echo "All open VMs will be closed to a saved state"            
            for vm in ${RUNVMLIST
[*]}            
            do            
            (VBoxManage controlvm $vm savestate) | zenity --progress --pulsate --width="320" --height="150" --title="Please Wait while VMs are Saved" --auto-close            
            echo "$vm was closed to a saved state"            
            done            
            echo "Rebooting now"            
            sudo -H -u server /etc/init.d/vboxdrv stop            
            sudo /etc/init.d/preload stop            
            sudo /sbin/shutdown -r now            
            fi            
            else            
            echo "You chose to Shutdown"            
            if [ ! ${RUNVMLIST
[*]}]            
            then            
            echo "No VMs open, straight to shutdown"            
            sudo -H -u server /etc/init.d/vboxdrv stop            
            sudo /etc/init.d/preload stop            
            sudo /sbin/shutdown -r now            
            else            
            echo "All open VMs will be closed to a saved state"            
            for vm in ${RUNVMLIST
[*]}            
            do            
            (VBoxManage controlvm $vm savestate) | zenity --progress --pulsate --width="320" --height="150" --title="Please Wait while VMs are Saved" --auto-close            
            echo "$vm was closed to a saved state"            
            done            
            echo "Shutting down Now"            
            sudo -H -u server /etc/init.d/vboxdrv stop            
            sudo /etc/init.d/preload stop            
            sudo /sbin/shutdown -h now            
            fi            
            fi            
                        exit
```

---

### Post by Jonners59 on 2015-06-20
Nudge....  Any help, please??????

---

### Post by Jonners59 on 2015-06-21
Seems to have resolved itself...  Now working

---

### Post by TheFu on 2015-06-21
> **Jonners59 said:**
> Nudge....  Any help, please??????

The code was too hard to read, so I didn't.  Would have been better to use normal "code" tags, not HTML. The lesson is to make it easy for volunteers to understand the issue, make it easy to read and understand.

---

### Post by Jonners59 on 2015-06-22
That was a typo, though when I read it after I still found it easy to read so didn't notice....

The script and everything else had worked for a few years and was really quite good.  Could not understand why it did not work after the rebuild, but as it seems to have fixed itself and I now have a fully working shutdown/reboot the script shall only serve to aid others, though I have taken a lot out re notes as other things like soduers need changes (takes out the need for a password).

---

