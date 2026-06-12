---
title: "Autostart VM in headless Ubuntu server"
date: 2011-08-04
forum: Virtualisation
---

### Post by Jake.Debord on 2011-08-04
I am looking for a way to have my VMs start when the server boots. Would also be nice to have something that lets them power down correctly before the server shuts down for reboots or whatever else. 

I have googled, and find old scripts that apparently are too outdated to still work? If there is a tut on here would sometime be so kind as to post a link to it. Thanks!

---

### Post by CharlesA on 2011-08-05
Which VM software are you using?

---

### Post by HermanAB on 2011-08-06
VMware has vmrun utility.

---

### Post by Jake.Debord on 2011-08-07
Sorry I meant to mention I'm using vbox. I ending up writing my own bash scripts

---

### Post by CharlesA on 2011-08-07
> **Jake.Debord said:**
> Sorry I meant to mention I'm using vbox. I ending up writing my own bash scripts
Ah nice. I did the same, in the end.

How did they turn out?

---

### Post by Jake.Debord on 2011-08-08
> **CharlesA said:**
> Ah nice. I did the same, in the end.

How did they turn out?

Pretty nicely, except the webservice is giving me some trouble after reboot but I haven't had a chance to look at it yet. It's set to boot on start but for whatever reason it didn't.

---

### Post by CharlesA on 2011-08-08
> **Jake.Debord said:**
> Pretty nicely, except the webservice is giving me some trouble after reboot but I haven't had a chance to look at it yet. It's set to boot on start but for whatever reason it didn't.

Is it vboxweb-service that you are having problems with?

Also, I'm curious what the scripts you wrote up look look. PM me them if you like.

---

### Post by Jake.Debord on 2011-08-08
> **CharlesA said:**
> Is it vboxweb-service that you are having problems with?

Also, I'm curious what the scripts you wrote up look look. PM me them if you like.


Yea its vboxweb-service that didn't start on boot. 
I'll post what I have in case someone runs across this thread needing help.
Here is my bash script:

```


VMUSER=vboxuser
VMNAME="Winxp" 
case "$1" in
start)
echo "Starting VirtualBox VM [Winxp]..."
sudo -H -b -u $VMUSER /usr/bin/VBoxVRDP -s "$VMNAME"
;;
stop)
echo "Saving state of Virtualbox VM [Winxp]..."
sudo -H -u $VMUSER /usr/bin/VBoxManage controlvm "$VMNAME" savestate
;;
*)
echo "Usage: /etc/init.d/Winxp {start|stop}" exit 1
;;
esac
exit 0

```

For those reading, just replace VMUSER to the defined vmuser for your setup.
Aslo, replace VMNAME with the name specified for your VM.
May also change the instances of Winxp in the echo lines to the name of your VM, or whatever description you prefer.

---

### Post by CharlesA on 2011-08-08
Nice script.

Mine's not as elegant, but it works:

Start script

```
#!/bin/bash

SAVEIFS=$IFS
IFS=$(echo -en "\n\b")
BIN=/bin/
USR=/usr/bin/

for vms in $(${USR}VBoxManage -nologo list vms | ${USR}awk -F \" '{ print $2 }';)
do
  if [[ -n $(${USR}VBoxManage showvminfo $vms | ${BIN}grep saved) ]]
    then
    echo "Starting VM $vms" && ${USR}VBoxHeadless -s $vms > /dev/null &
  fi
done
IFS=$SAVEIFS
# eof
```

Stop script
```

#!/bin/bash

SAVEIFS=$IFS
IFS=$(echo -en "\n\b")
USR=/usr/bin/

if [[ -n $(${USR}VBoxManage -nologo list runningvms) ]]
  then
    for runningvms in $(${USR}VBoxManage -nologo list runningvms | ${USR}awk -F \" '{ print $2 }')
    do
    echo Saving state of $runningvms && ${USR}VBoxManage -nologo controlvm $runningvms savestate
    done
  else
    echo "No VMs running"
fi
IFS=$SAVEIFS
# eof

```

Could probably consolidate them, but I'm not all that good at bash scripting.

EDIT: As for the web service, did you define a user in /etc/default/virtualbox ?

---

### Post by Jake.Debord on 2011-08-08
your code looks good too, maybe just thought too hard about it! And yes, I'll post the contents of /etc/default/virtualbox

```

VBOXWEB_USER=vboxuser

```

All that is in there :)

---

### Post by CharlesA on 2011-08-08
Lol. I was trying to write a startup/shutdown script to save/start vms but hit a roadblock since I didn't know how to get it to run as a specific user, so I kinda "haxxed" around it with a couple scripts.

You'd made me see if I can get a startup script working. :)

The /etc/default/virtualbox file looks fine.. Does it not autostart after each boot or every so often? If you start it manually, does it run as the right user?

---

### Post by Jake.Debord on 2011-08-08
I don't reboot enough to be able to tell you for sure. I do remember having many issues with it while setting up vboxphp. It starts just fine when I tell it to start through webmin though! That's probably rather vague... Webmin says it's set to start on boot. I would reboot now just to see but it's mid day on a Monday and people would freak and they have killed for less around here!

---

### Post by CharlesA on 2011-08-08
Hmm, quite strange. What host OS are you running? I just install VBox 4.1 on 10.04 and set everything up with phpvirtualbox and it's running fine.

---

### Post by Jake.Debord on 2011-08-08
> **CharlesA said:**
> Hmm, quite strange. What host OS are you running? I just install VBox 4.1 on 10.04 and set everything up with phpvirtualbox and it's running fine.


Ubuntu 10.10 and I use vbox 4.0.8

---

### Post by CharlesA on 2011-08-08
> **Jake.Debord said:**
> Ubuntu 10.10 and I use vbox 4.0.8

Ah. I was running 4.0.8 earlier today on 10.04 fine. Wonder what could be causing it. I know I've run into the problem of the web server not starting up, but I can't recall the fix.

Have you cleared out the virtualbox file and readded the web user?

Also: How do you have the startup script set to run? Did you use update-rc.d ?

---

### Post by Jake.Debord on 2011-08-09
> **CharlesA said:**
> Ah. I was running 4.0.8 earlier today on 10.04 fine. Wonder what could be causing it. I know I've run into the problem of the web server not starting up, but I can't recall the fix.

Have you cleared out the virtualbox file and readded the web user?

Also: How do you have the startup script set to run? Did you use update-rc.d ?



No, havent tried that yet, you think I possibly have an error in my vbox file? 

And yea, I just used update-rc.d to update and install the script

---

### Post by CharlesA on 2011-08-09
It's worth taking a look at.

Hrm.. I used the defaults when I added the script to shutdown but it's not liking it, apparently.

---

### Post by Jake.Debord on 2011-08-09
what commands are you using with update-rc.d

edit: also, what are the permissions on the file did you use chmod on it at all?

---

### Post by CharlesA on 2011-08-09
> **Jake.Debord said:**
> what commands are you using with update-rc.d

edit: also, what are the permissions on the file did you use chmod on it at all?

I was using the defaults. I figured out that the problem was that I wasn't using sudo to run the VBox binaries as the user that has the VMs running.

Here's what the finished script looks like:

```
#!/bin/bash

### BEGIN INIT INFO
# Provides:       vmboot
# Required-Start: vboxdrv
# Required-Stop:
# Default-Start:  2 3 4 5
# Default-Stop:   0 1 6
# Short-Description: Stop/Start VMs on System shutdown
### END INIT INFO

# Add this script to /etc/init.d/
# Run update-rc.d (for debian) or chkconfig (centos/redhat)

VBOXUSER=vboxuser
SU="sudo -H -u $VBOXUSER"
VBOXMANAGE=/usr/bin/VBoxManage
VBOXHEADLESS=/usr/bin/VBoxHeadless
RUNNINGVMS=$($SU $VBOXMANAGE --nologo list runningvms | sed -e 's/^".*".*{\(.*\)}/\1/')
ALLVMS=$($SU $VBOXMANAGE --nologo list vms | sed -e 's/^".*".*{\(.*\)}/\1/')

case $1 in
stop)
if [[ -n $RUNNINGVMS ]]; then
	echo "Saving the state of all running VMs..."
	for v in $RUNNINGVMS; do
		$SU $VBOXMANAGE --nologo controlvm $v savestate
	done
fi
;;
start)
for v in $ALLVMS; do
	if [[ -n $($SU $VBOXMANAGE --nologo showvminfo $v | grep saved) ]]; then
		echo "Restoring VMs..." && $SU $VBOXHEADLESS -s $v & > /dev/null
	fi
done
;;
*)
echo "Usage: /etc/init.d/vmboot start | stop"; exit 1
;;
esac
exit 0
```

The only quirk I've seen so far is that you need to have the VRDP port set in the VM itself, as the script doesn't pass that to VBoxHeadless.

Also, it doesn't really give you any feedback, but if the VMs are running, they'll show as running soo.. ;)

What do you think?

---

### Post by Jake.Debord on 2011-08-09
looks like there is more than one way to skin a cat! haha, I think your just fine with that and I'm like you I wouldn't be too worried about how verbose the feedback is. Since all the script does is tell it to pause and start if it works now then if something breaks down the line its probably in vbox and not in the script so redundant logs just waste disk space :P I'm going to keep your script in case I ever decide to edit mine I'd like to compare to what others have done

---

### Post by CharlesA on 2011-08-09
Yep, that's probably true. The worst thing that can happen is that it'll get stuck when the machine is shutting down whining about that the kernel module vboxdrv isn't loaded... just ran into that after moving VMs from one user's home directory to another (which fails.. checking it out more now)

Doing some more testing.

---

