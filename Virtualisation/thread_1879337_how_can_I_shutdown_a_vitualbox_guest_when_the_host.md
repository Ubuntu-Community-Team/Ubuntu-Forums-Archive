---
title: "how can I shutdown a vitualbox guest when the host is shutting down"
date: 2011-11-11
forum: Virtualisation
---

### Post by Krist Blomme on 2011-11-11
Hi

I'm having a Virtualbox guest starting up when the host boots-up.

From time I forget that this guest is still running when I shutdown the host , 
so the host doesn't continue shutting down until I confirm the guest's shutdown .

The idea was to run some script having the following statement 

```
VBoxManage controlvm XP acpipowerbutton
```

and put it somewhere in the init.d sequence .

However these script's are executed as root , and at that point I'm facing a problem .
That is ,when I use VBoxManage as root ( or via sudo) I'm not seeing the registrated VM's 

exp:
when I run as the user that created the VM's

```
krist@XII-Apostoli:/etc/init.d$ **VBoxManage list vms**
"XP" {58ef1d80-d1db-4d2e-9494-b94c789317a8}
"XP+MSOffice2K7" {8d8f91a4-b4a6-45a0-86a1-8f6956d73cae}
"Ubuntu 11.04 " {96b4ce99-74fd-45f8-881d-d84dae24602e}
```

I can see all my VM's

when I run this via sudo 

```
krist@XII-Apostoli:/etc/init.d$ **sudo VBoxManage list vms**
```

I get no result 

exp:
when I try to shutdown a guest 

```
krist@XII-Apostoli:/etc/init.d$ **VBoxManage controlvm XP acpipowerbutton**
```

the guest goes down as expected 

when I do this with sudo 

```
krist@XII-Apostoli:/etc/init.d$ **sudo VBoxManage controlvm XP acpipowerbutton**
VBoxManage: error: Could not find a registered machine named 'XP'
VBoxManage: error: Details: code VBOX_E_OBJECT_NOT_FOUND (0x80bb0001), component VirtualBox, interface IVirtualBox, callee nsISupports
Context: "FindMachine(Bstr(a->argv[0]).raw(), machine.asOutParam())" at line 97 of file VBoxManageControlVM.cpp
```

the guest keeps running .


Has anybody a clue how to solve this ?

---

### Post by JKyleOKC on 2011-11-12
Try ```
sudo su - krist -c VBoxManage controlvm XP acpipowerbutton
```which should invoke VBoxManage as user "krist" rather than as "root" (and if it works, omit the "sudo" when putting it into the shutdown script).

I use a package called vboxtool, written in 2008 by Mark Baaijens <mark.baaijens@gmail.com>, that handles the problem completely and also provides other features. At system shutdown, it saves the state of all running VMs instead of doing the acpi shutdown, which saves time at the next startup since they only restore their RAM images instead of doing full reboots.

I think it's on SourceForge, but a Google search for "vboxtool" ought to find it. It's a bash script so ought not have any dependencies, and comes with a ReadMe file that tells how to install and configure it.

---

### Post by CharlesA on 2011-11-12
^ That.

I have a startup/shutdown script on my site, if you want to take a look.

It's also posted on the forum somewheres.

---

### Post by JKyleOKC on 2011-11-12
I thought I remembered you creating a script that was far less complex than "vboxtool" but didn't do a search for it...

---

### Post by CharlesA on 2011-11-12
> **JKyleOKC said:**
> I thought I remembered you creating a script that was far less complex than "vboxtool" but didn't do a search for it...

Not sure if it's less complicated since I haven't used vboxtool. I did look at it but it wasn't under development as far as I know.

---

### Post by Krist Blomme on 2011-11-15
Tnx for the reply's Jim and Charles ,

but I'm not yet there .

When I try the script I have the same problem , when run as root it doesn't find running vms 
When I run it as the user ( krist ) that created the vms , it works ok

```
krist@XII-Apostoli:~/shellScripts$ sudo ./stopvm.sh
No VMs running
krist@XII-Apostoli:~/shellScripts$ ./stopvm.sh
Saving state of XP
0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
```

of coarse the idea to save the state is a benefit .

So I have to combine with Jim's solution ,however perhaps there is a typo in the statement .
When I run the su command in this way I get the help dump from VBoxManage 

```
krist@XII-Apostoli:~/shellScripts$ sudo su - krist -c VBoxManage list vms
Oracle VM VirtualBox Command Line Management Interface Version 4.1.2
(C) 2005-2011 Oracle Corporation
All rights reserved.

Usage:

VBoxManage [-v|--version]    print version number and exit
VBoxManage [-q|--nologo] ... suppress the logo

VBoxManage list [--long|-l] vms|runningvms|ostypes|hostdvds|hostfloppies|
                            bridgedifs|hostonlyifs|dhcpservers|hostinfo|
                            hostcpuids|hddbackends|hdds|dvds|floppies|
                            usbhost|usbfilters|systemproperties|extpacks


```

---

### Post by Krist Blomme on 2011-11-15
I posted a bit to quick , following syntax works fine 

```
krist@XII-Apostoli:~/shellScripts$ sudo su - krist -c "VBoxManage controlvm XP acpipowerbutton"
```

---

### Post by CharlesA on 2011-11-15
> **Krist Blomme said:**
> I posted a bit to quick , following syntax works fine 

```
krist@XII-Apostoli:~/shellScripts$ sudo su - krist -c "VBoxManage controlvm XP acpipowerbutton"
```
Aye.

Here's the startup script I cobbled together. The stopvm.sh and startvm.sh were my early attempts and they work if you run them as the user who is running the VMs.

The startup script uses sudo to run the command as the user who is running the VMs.

The script is here:

```
#!/bin/bash

### BEGIN INIT INFO
# Provides:       vmboot
# Required-Start: vboxdrv
# Required-Stop:  vboxdrv
# Default-Start:  2 3 4 5
# Default-Stop:   0 1 6
# Short-Description: Stop/Start VMs before/after System shutdown
### END INIT INFO

# Add this script to /etc/init.d/
# Run update-rc.d vmboot defaults as root

# Written to work with VirtualBox 4.x

# User who is running the VMs
VBOXUSER=vboxuser
SU="sudo -H -u $VBOXUSER"
# Path to VBoxManage
VBOXMANAGE="/usr/bin/VBoxManage --nologo"
# Get UUID of All Running VMs
# UUID looks like this: a02b5b54-a84d-48fa-8dac-2a3fad55717e
RUNNINGVMS=$($SU $VBOXMANAGE list runningvms | sed -e 's/^".*".*{\(.*\)}/\1/')
# Get UUID of All VMs
ALLVMS=$($SU $VBOXMANAGE list vms | sed -e 's/^".*".*{\(.*\)}/\1/')

# Check to insure $ALLVMS is not null and exit if it is.
if [[ $ALLVMS = "" ]]; then
        echo "No VMs are detected on this host! Did you configure the VBOXUSER variable?"; exit
fi

case $1 in
stop)
if [[ -n $RUNNINGVMS ]]; then
        for v in $RUNNINGVMS; do
        echo -e "Saving state of $($SU $VBOXMANAGE list vms | grep $v | awk -F\" '{print $(NF-1)}')..." && $SU $VBOXMANAGE controlvm $v savestate
        done; else
        echo "No running VMs to save!"
fi
;;
start)
for v in $ALLVMS; do
        if [[ -n $($SU $VBOXMANAGE showvminfo $v | grep saved) ]]; then
                echo -e "Waiting for VM \"$($SU $VBOXMANAGE list vms | grep $v | awk -F\" '{print $(NF -1)}')\" to power on..." && $SU $VBOXMANAGE startvm $v --type headless 1> /dev/null && echo -e  "VM \"$($SU $VBOXMANAGE list vms | grep $v | awk -F\" '{print $(NF-1)}')\" has been successfully started."; else
                echo "No Saved VMs to start!"

        fi
# If the previous loop has an error, the loops exits and returns an error.
        if [[ $? -ne 0 ]]; then
                echo "There was an error starting your VMs! Try starting them manually to see what the problem is."; break
        fi
done
;;
status)
if [[ -n $RUNNINGVMS ]]; then
        echo "List of Running VMs:" && $SU $VBOXMANAGE list runningvms; else
                echo "No VMs Currently Running!"
fi
;;
*)
echo "Usage: /etc/init.d/vmboot start | stop | status"; exit 1
;;
esac
exit 0
# eof
```

It's easier to use "sudo -H -u someuser" instead of sudo su imo.

---

### Post by JKyleOKC on 2011-11-15
> **Krist Blomme said:**
> When I try the script I have the same problem , when run as root it doesn't find running vms 
When I run it as the user ( krist ) that created the vms , it works okJust to make the reason for this a bit more clear, what's happening is that VBox puts the VMs themselves into a subdirectory within the home directory of the user who creates them. Prior to VBox V4.0, the subdirectory was a hidden one named .VirtualBox; with version 4.0, the program changed to creating a non-hidden one when the first VM was built, but if the hidden one existed, it would continue to use it. It only searches within the home directory of the running user when reporting, so when "sudo" switches the running user to "root" the program loses sight of all the VMs except those that were created by root.

Using the "su -u krist -c" construct tells VBoxManager that the current user is "krist" even though it's running as "root" so things work. Incidentally, many folk interpret the "su" as an acronym for "super user" but it really means "switch user" and originally was used mostly for this type of situation. Then administrators discovered that "-u root" wasn't necessary if the command defaulted to that, and the current version came into being.

---

### Post by Krist Blomme on 2011-11-20
Tnx again Charles and Jim .

We'r are almost their now .
What I did following your reply

- I placed Charles his script in /etc/init.d/ as vmboot
- ```
sudo chmod 755 vmboot
```
- ```
sudo update-rc.d vmboot default
```
- I have set the VBOXUSER parameter in the script vmboot

The script runs fine :
```

krist@XII-Apostoli:~$ sudo /etc/init.d/vmboot stop
Saving state of XP...
0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
Saving state of XP+MSOffice2K7...
0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
krist@XII-Apostoli:~$ 

```

but when I do a shutdown ,there is a popup interrupting somehow the execution of the vmboot script 

"
Some programs are still running:
/usr/lib/virtualbox/VirtualBox
This program is blocking log out
waiting for programs to finish,  Interrupting
these programs way cause you to lose work
<Lock Screen><Cancel><shutdownAnyway>
" 

(sorry don't know how I can paste the screenshot , I attached it to the thread)

Where the VMs are running I got the Virtualbox dialog to shutdown again .

---

### Post by CharlesA on 2011-11-20
You might have to set the script to run prior to the GUI shutting down, but I'm not quite sure how to do that.

Check here:
[http://ubuntuforums.org/showthread.php?t=1844885](http://ubuntuforums.org/showthread.php?t=1844885)

Maybe it has the answer.

---

### Post by JKyleOKC on 2011-11-20
When you use the **defaults** option to update-rc.d, both the start and stop sequence numbers are set to "20" according to the man page. I suspect that the stop sequence number should be a lower number, so that vbox gets saved before the drives are unmounted -- but I've never directly changed these values in a Debian-based system so cannot give you step by step instructions. Try "man update-rc.d" for the full description of what happens.

There's also a GUI utility for making such changes but I don't remember its name.

The key thing is to make sure that the "stop" part of the script is executed before the file systems are unmounted during the shutdown sequence. Look in the /etc/rc0.d and also rd1.d and rc6.d directories for these sequences. Those that start with K are executed, in the sequence indicated by their numbers, when that runlevel is entered, followed by those that start with S. On this box (which is not running the script for automatic start or stop but is running another script to control the vbox module itself) the vboxdrv script is K20 when shutting down and S20 when starting up. On shutdown, filesystems unmount at S40 so there should be plenty of time there.

However the auto start/stop script should be called **before** the module script when shutting down, and **after** when starting up, so this might be part of the problem. Sorry I can't be more helpful at this point!

Incidentally, "man 7 upstart" will tell you more than you probably want to know about the boot sequences...

EDIT: Post #8 in the thread Charles referenced tells one way to change the numbers, and the third page of that thread includes a link to a modified version of the script.

---

### Post by CharlesA on 2011-11-20
I ran into that a couple times, but I run my VMs headless on a headless server, so I don't have a GUI to worry about.

---

