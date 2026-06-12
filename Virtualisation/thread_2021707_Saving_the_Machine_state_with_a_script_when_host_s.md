---
title: "Saving the Machine state with a script when host shuts down"
date: 2012-07-09
forum: Virtualisation
---

### Post by mjzebis on 2012-07-09
I am working on a script to work with a program called "APCUPSD" for the battery backup monitor. We have tons of power outages and keep our computers running 24/7. It is mission critital for these VM's to keep up and running.
In APCUPSD there is a script called RUNLIMIT; this is the script that is supposed to execute when the program detects that there is a certain number of minute of battery life remaining and these are the things its going to do before it safely shuts down the operating system. In this case its Ubuntu. We are using this on versions 10, 11, and 12 of ubuntu. 

Here is the script I put in RUNLIMIT:

```

#! /bin/sh
#This event is generated when the MINUTES value
#defined in the apcupsd.conf file expires while
#in a power fail condition. The MINUTES is the
#remaining runtime as internally calculated by
#the UPS and monitored by apcupsd. After completing
#this event, apcupsd will immediately initiate
#a doshutdown event.

logfile=/home/user/apcupsd.log
echo $(date +%C%y-%m-%d) $(date +%l:%M:%S.%N): EVENT LOG START >> $logfile
echo $(date +%C%y-%m-%d) $(date +%l:%M:%S.%N): Event: runlimit >> $logfile
echo "Power is critacally low, less than 25 minutes until shutdown" | festival --tts
echo $(date +%C%y-%m-%d) $(date +%l:%M:%S.%N): "Power is critacally low, less than 25 minutes untill shutdown." >> $logfile
echo $(date +%C%y-%m-%d) $(date +%l:%M:%S.%N): "Uptime:" $(uptime) >> $logfile
echo $(date +%C%y-%m-%d) $(date +%l:%M:%S.%N): "Current running VM's:" >> $logfile
echo $(date +%C%y-%m-%d) $(date +%l:%M:%S.%N): $(sudo -u zebisrep -i vboxmanage list runningvms) >> $logfile
echo saving the virtual machine state | /usr/bin/festival --tts
echo $(date +%C%y-%m-%d) $(date +%l:%M:%S.%N): "Saving the virtual machine state." >> $logfile
sudo -u user -i vboxmanage controlvm WinXP savestate >> $logfile 2>%1
COUNT=1
sleep 5
echo $(sudo -u user -i vboxmanage list runningvms | grep WinXP) >> $logfile

while su - user vboxmanage list runningvms | grep WinXP
do
sleep 25
echo $(sudo -u user -i vboxmanage list runningvms) >> $logfile
COUNT=$((COUNT+1))
echo "loop number $COUNT" >> $logfile
if [ $COUNT -gt 10 ] 
then
echo "Server still running." >> $logfile #exit 10
exit 10 
fi
#after 5 minutes the VM is still running
done
echo virtual machine state saved | /usr/bin/festival --tts
echo $(date +%C%y-%m-%d) $(date +%l:%M:%S.%N): "Virtual machine state saved." >> $logfile
echo $(date +%C%y-%m-%d) $(date +%l:%M:%S.%N): END EVENT LOG >> $logfile
echo "---------------------------------------------" >> $logfile
exit 0

```The problem we are having is that sometimes it starts to run this script as we can tell from the log it creates but it addruptly stops. It never saves the state, aborts our running VM, interupts mission critical operations, and causes alot of file corruption. Fortunatly we regulalry backup our VM's VDI's, but we don't need to be spending 30-40 minutes copying old VDI's back every time the power goes out. 

If anyone hase ever done this before, or if you have any suggestions as to what to do. Please let us know. This summer has been brutal on our computers. We are in the south parts of florida "the lighting capital". So you can just imaging how often we loose power. Is almost a daily occurence and it ussually happens between 1 and 5 am, when we can't be here to save our VM states.

---

### Post by Dedoimedo on 2012-07-10
Do you know the stage where it quits?
Always at the same point? A specific command?
Dedoimedo

---

### Post by CharlesA on 2012-07-10
*pokes thread*

See the script I wrote up here:
[http://charlesa.net/scripts/linux/virtualbox-script-ubuntu.php](http://charlesa.net/scripts/linux/virtualbox-script-ubuntu.php)

I ended up writing it in order to get around the haxxish way I was saving the VM state on power failure - having a script run every minute to check if a power failure flag existed and shutdown the VMs if it did.

Running a startup/shutdown script is way easier.

---

