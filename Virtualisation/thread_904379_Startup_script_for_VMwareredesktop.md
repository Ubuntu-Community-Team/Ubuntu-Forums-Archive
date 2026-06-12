---
title: "Startup script for VMware/redesktop"
date: 2008-08-29
forum: Virtualisation
---

### Post by waspbloke on 2008-08-29
Hi,

I've been trying to create a script to launch my VM and then run rdesktop.

I am running a headless existing XP partition VM and then rdesktop in seamless mode thru' a host-only network.

Problem is, how to get the script to wait until the XP VM is ready to accept client connections? If I just ping away at the VM, it responds long before XP has fully booted and port 3389 is ready.

Can anybody help fill in the # wait for XP to boot:
```

#! /bin/bash
vmrun start "/path/to/Windows XP Home Edition.vmx"

# wait for XP to boot

read -s -p &#8220;Enter Password: &#8221; mypassword
rdesktop -A -s 'seamlessrdpshell explorer' 192.168.xxx.xxx -u ubuntu -p $mypassword

```

Also, is it possible to have the script run without a terminal window? As far as I can make out, I have to launch the script from a terminal as the read command requires user input. Is there a dialogue box equivalent to read?

**** EDITBUMP: SOLVED AS PER MY REPLY BELOW ****

---

### Post by waspbloke on 2008-09-02
Okay, no takers for this one so I went off and figured it out for myself and am rather pleased with myself as this is my first bash script.

You'll need nmap to probe the VM and then make the script executable for terminal free execution.

```

#!/bin/bash
# launchXP.sh by waspbloke September 2008
#
# requires nmap (sudo apt-get install nmap)
#
# script defaults to run explorer or accepts optional argument of app/path to execute eg:
# 	launchXP.sh taskmgr
# 	launchXP.sh "c:\program files\skype\skype.exe"
#
# create your own custom app launchers by calling this script with different app arguments

# change these vars to reflect your own setup
PathHere="/path/to/script"
PathToVMX="/path/to/winxp.vmx"
GuestIP="192.168.128.128"


# check for windows app as ARG
AppToRun="explorer"
if [ "$1" ]; then AppToRun="$1"; fi
echo "Windows app to run: $AppToRun"


# collect XP user logon info
MyAccount=`zenity --entry --title="XP User Account" --text="Please enter the XP username to login with:"`
MyPassword=`zenity --entry --title="XP User Password" --hide-text --text="Please enter the password for $MyAccount:"`


# check if VM is already running
vmrun list > $PathHere/VMRUNout

# EDIT THIS LINE HERE: /winxp/      TO: /something relevant/    AS PER YOUR 'vmrun list' RESULT
VMrunning=$(awk '/winxp/ {print "true"}' $PathHere/VMRUNout)

if [ ! $VMrunning ]; then VMrunning="false"; fi
echo "VM running: $VMrunning"

# if VM not running start the VM and wait while it boots
if [ "$VMrunning" = "false" ]; then
	vmrun start $PathToVMX
	echo "Please wait, starting VM $PathToVMX..."
	sleep 45s
fi


# check if VM's RDP port is ready to connect
echo "VM started, scanning RDP port..."

until [  "$RDPstate" = "open" ]
do
	# scan port 3389 and send output to file
	nmap -p 3389 $GuestIP > $PathHere/NMAPout
	# set RDPstate var if NMAP scan is successful
	RDPstate=$(awk '/(3389)/ && /(open)/ {print "open"}' $PathHere/NMAPout)
	if [ ! $RDPstate ]; then RDPstate="closed"; fi
	echo "...RDP port is currently $RDPstate..."
	sleep 5s
done

# now we can fire up rdesktop
echo "Launching rdesktop session..."
rdesktop -A -s 'seamlessrdpshell '$AppToRun $GuestIP -u $MyAccount -p $MyPassword

# clean up before exit
rm $PathHere/VMRUNout
rm $PathHere/NMAPout

exit 0

```

Obviously you need to change the path and IP variables as noted.

I'd be interested to here any thoughts about this script and suggestions for improvements. I think I might try incorporation the modded rdesktop script I've seen somewhere for using a master session and launching slave rdesktop sessions from it next.

---

### Post by lazyart on 2008-09-02
Good work.

Just a note- if you set your VM to run automatically (I do this with my web and mail server VMs) you could eliminate half the script.

---

