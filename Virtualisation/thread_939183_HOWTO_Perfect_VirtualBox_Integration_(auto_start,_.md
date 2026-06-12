---
title: "HOWTO: Perfect VirtualBox Integration (auto start, rdesktop on workspace 2, etc)."
date: 2008-10-05
forum: Virtualisation
---

### Post by edmondt on 2008-10-05
First of all, this thread is going to be long...But in the end it will look something like this:

[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=87396&stc=1&d=1223235372[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=87391&d=1223235138")

This thread is aim to achieve the following:
[LIST]
[*]Auto start VirtualBox on user login.
[*]Auto start rdesktop when Virtual Machine is booted
[*]Auto place rdesktop into workspace 2
[*]Resize rdesktop to fit workspace 2
[*]Replace Virtual Machine (XP Pro) shell into something lighter
[*]Make things pretty :)
[*]Resolve clipboard bug with fullscreen rdesktop
[*]Auto shutdown Virtual Machine on shutdown.
[/LIST]

I have tried many methods before and I found this configuration to be the best and most productive, better than seamlessrdp and virtualbox built in seamless. Here are the problems I have had in the past with other methods:

**[2X Application Server]("http://www.2x.com/")**:
[LIST]
[*]Not very stable when moving windows.
[*]Caused virtual machine to hang on a few occasions.
[*]Higher CPU usage.
[/LIST]
**[seamlessrdp]("http://ubuntuforums.org/showthread.php?t=433359&highlight=seamlessrdp")**:
[LIST]
[*]Not stable when you have too many windows open.
[*]Slower, need to script auto login, logoff then launch the seamlessrdp script.
[*]Causes higher CPU usage, my laptop heats up more.
[/LIST]
**[VirtualBox seamless]("http://gaming.gwos.org/doku.php/udsf:virtualbox")**:
[LIST]
[*]Too many windows gives problems
[*]Apps opened are not on the gnome taskbar like seamlessrdp
[*]Again, causes higher CPU usage, my laptop heats up more.
[/LIST]

Regular rdesktop works the best because CPU usage is lower and it is more stable.

Okie! So let's get started:

What you need:

[LIST=1]
[*]VirtualBox Installed and running.
[*]Virtual Machines Installed Running mine is named **XP** (I Googled [TinyXP Rev09 - eXPerience] because it runs faster)
[*]Remote Assistance Enable (Remote Desktop Enabled).
[*]Compiz Installed and Running
[*]Advanced Desktop Settings Installed (sudo apt-get install compizconfig-settings-manager).
[/LIST]

**Step 1**

Here is the script to start your virtual machine and rdesktop. Copy and paste into a new text file and name it launchXP.sh

```

#!/bin/bash
# launchXP.sh by waspbloke September 2008
#
# requires nmap (sudo apt-get install nmap)
#
# create your own custom app launchers by calling this script with different app arguments
# ORIGINAL SCRIPT FROM: http://ubuntuforums.org/showthread.php?t=904379&highlight=bash+ping

# change these vars to reflect your own setup
PathHere="/home/**yourhomedir**"
GuestIP="10.0.1.2" #The external ip of the Virtual Machine


# check if VM is already running

# if VM not running start the VM and wait while it boots
if [ $(VBoxManage -nologo list runningvms | wc -l) = 0 ]; then
	VBoxHeadless -startvm **XP** &
	echo "Please wait, starting VM **XP**..."
	sleep 55
fi


# check if VM's RDP port is ready to connect
echo "VM started, scanning RDP port 3389..."

until [  "$RDPstate" = "open" ]
do
	# scan port 3389 and send output to file
	nmap -p 3389 $GuestIP > $PathHere/NMAPout
	# set RDPstate var if NMAP scan is successful
	RDPstate=$(awk '/(3389)/ && /(open)/ {print "open"}' $PathHere/NMAPout)
	if [ ! $RDPstate ]; then RDPstate="closed"; fi
	echo "...RDP port is currently $RDPstate..."
	sleep 5
done

# now we can fire up rdesktop
echo "Launching rdesktop session..."
#You can launch in seamlessrdp mode if you want to...
rdesktop localhost:3389 -z -x l &


# clean up before exit
rm $PathHere/NMAPout

exit 0

```

The script requires nmap, install it with the following and make the launchXP.sh executable.
```

sudo apt-get install nmap
sudo chmod +x /home/**yourhomedir**/launchXP.sh

```

**Step 2**

For auto shutdown Virtual Machine on reboot/shutdown, download **[vboxcontrol]("http://farfewertoes.com/code/vboxcontrol/")**, [follow the instructions here]("http://farfewertoes.com/code/vboxcontrol/")

**Note:** 

I did not let vboxcontrol autostart my Virtual Machines, because it screws up my PluseAudio for some reason. So I modified the script with "sudo gedit /etc/init.d/vboxcontrol" see the **bold text**:

```

#! /bin/sh
### BEGIN INIT INFO
# Provides: virtualbox_vms
# Required-Start:    $local_fs $syslog $remote_fs
# Required-Stop:     $local_fs $syslog $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Control VirtualBox Virtual Machine instances
### END INIT INFO
#
# Version 2008051100 by Jochem Kossen <jochem.kossen@gmail.com>
# http://farfewertoes.com
#
# Released in the public domain
#
# This file came with a README file containing the instructions on how
# to use this script.
#

. /lib/lsb/init-functions

# Are we running from init?
run_by_init() {
    ([ "$previous" ] && [ "$runlevel" ]) || [ "$runlevel" = S ]
}

################################################################################
# INITIAL CONFIGURATION
VBOXDIR="/etc/virtualbox"
VM_USER="root"
USE_NAT="yes"

export PATH="${PATH:+$PATH:}/bin:/usr/bin:/usr/sbin:/sbin"

if [ -f $VBOXDIR/config ]; then
    . $VBOXDIR/config
else
    echo "ERROR: $VBOXDIR/config does not exist. Exiting."
    exit 1
fi

SU="su $VM_USER -c"
VBOXMANAGE="VBoxManage -nologo"
#VBOXMANAGE="VBoxVRDP -s"

################################################################################
# FUNCTIONS

# Determine if USE_NAT is set to "yes"
use_nat() {
    if [ "$USE_NAT" = "yes" ]; then
        return `true`
    else
        return `false`
    fi
}

# Bring up the bridge interface
enable_bridge() {
    # If NAT is enabled, don't do anything
    use_nat && return

    # Load the tun module
    if [ ! -e /dev/net/tun ]; then
        modprobe tun
    fi

    brctl addbr br0 || /bin/true

    # Disable $HOST_IF; host will use br0 instead
    ifdown $HOST_IF
    ifconfig $HOST_IF 0.0.0.0 promisc
    brctl addif br0 $HOST_IF

    # Bring up br0
    ifup br0

    # Answer ARP requests for $HOST_IP (which now come on br0) with the MAC
    # address of $HOST_IF
    arp -Ds $HOST_IP $HOST_IF pub
}

# Bring down the bridge interface
disable_bridge() {
    # If NAT is enabled, don't do anything
    use_nat && return

    ifdown br0
    brctl delbr br0
    ifup $HOST_IF
}

# Activate tap interfaces
enable_taps() {
    # If NAT is enabled, don't do anything
    use_nat && return

    for TAP in $TAPS; do
        # Check if $TAP is configured already
        ifconfig $TAP > /dev/null 2>&1
        if [ $? != 0 ]; then
            tunctl -t $TAP -u $VM_USER
            brctl addif br0 $TAP

            # Disable tap interfaces for host; guest will activate them for themselves
            ifconfig $TAP 0.0.0.0 promisc

            # Enable proxy_arp so that ARP requests can be answered correctly
            # by the host
            echo 1 > /proc/sys/net/ipv4/conf/$TAP/proxy_arp

            # Add a route for the tap device
            route add -host $HOST_IP dev $TAP
        else
            log_failure_msg "Interface $TAP already configured"
        fi
    done
}

# Disable/deconfigure tap interfaces
disable_taps() {
    # If NAT is enabled, don't do anything
    use_nat && return

    for TAP in $TAPS; do
        route del -host $HOST_IP dev $TAP
        brctl delif br0 $TAP
        tunctl -d $TAP
    done
}

# Check for running machines every few seconds; return when all machines are
# down
wait_for_closing_machines() {
    RUNNING_MACHINES=`$SU "$VBOXMANAGE list runningvms" | wc -l`
    if [ $RUNNING_MACHINES != 0 ]; then
        sleep 5
        wait_for_closing_machines
    fi
}

################################################################################
# RUN
case "$1" in
    start)
        if [ -f /etc/virtualbox/machines_enabled ]; then
            if [ ! `use_nat` ]; then
                enable_bridge
                enable_taps

                chown root.vboxusers /dev/net/tun
                chmod 0660 /dev/net/tun
#            else

            fi
# Configure Networking...
#                 chown root.vboxusers /dev/net/tun
                 **tunctl -t tap1 -u edmondt**
                 **ifconfig tap1 10.0.1.1**
            cat /etc/virtualbox/machines_enabled | while read VM; do
                log_action_msg "Starting VM: $VM ..."
**#                $SU "$VBOXMANAGE startvm \"$VM\" -type vrdp"**
            done
        fi
        ;;
    stop)
        # NOTE: this stops all running VM's. Not just the ones listed in the
        # config
        $SU "$VBOXMANAGE list runningvms" | while read VM; do
            log_action_msg "Shutting down VM: $VM ..."
            $SU "$VBOXMANAGE controlvm \"$VM\" acpipowerbutton"
**#            $SU "$VBOXMANAGE controlvm \"$VM\" savestate"**
        done
        wait_for_closing_machines

        if [ ! `use_nat` ]; then
            disable_taps
            disable_bridge
        fi
        ;;
    bridge-up)
        enable_bridge
        ;;
    bridge-down)
        disable_bridge
        ;;
    taps-up)
        enable_taps
        ;;
    taps-down)
        disable_taps
        ;;
    start-vm)
        log_action_msg "Starting VM: $2 ..."
        $SU "$VBOXMANAGE startvm \"$2\" -type vrdp"
        ;;
    stop-vm)
        log_action_msg "Stopping VM: $2 ..."
        $SU "$VBOXMANAGE controlvm \"$2\" acpipowerbutton"
        ;;
    poweroff-vm)
        log_action_msg "Powering off VM: $2 ..."
        $SU "$VBOXMANAGE controlvm \"$2\" poweroff"
        ;;
    status)
        log_action_msg "The following virtual machines are currently running:"
        $SU "$VBOXMANAGE list runningvms" | while read VM; do
            echo -n "$VM ("
            echo -n `$SU "VBoxManage showvminfo $VM|grep Name:|sed -e 's/^Name:\s*//g'"`
            echo ')'
        done
        ;;
    *)
        log_failure_msg "Usage: $0 {start|stop|status|start-vm <VM name>|stop-vm <VM name>|poweroff-vm <VM name>|bridge-up|bridge-down|taps-up|taps-down}"
        exit 3
esac

exit 0

```


**Step 3**

On System > Preference > Session, under Start Up Programs **Add...**

Name: Start VirtualBox
Command: sh /home/**yourhomedir**/launchXP.sh
Comment: Start virtualbox and rdesktop

**Step 4**

Now your VM should autostart and rdesktop should auto load, it look a little ugly, but we will change that...

Open Terminal and launch

```
ccsm &
```

Disable window borders for rdesktop and shadows:

Goto: **Window Decoration**
**Decoration windows:** any & !(class=rdesktop)
**Shadow windows:** & !(type=Dock) & !(class=rdesktop)

Goto: **Window Rules**
[LIST]
[*]Enable Window Rules.
[/LIST]
**Skip taskbar:** title=rdesktop - localhost
**Skip pager:** title=rdesktop - localhost
**Fullscreen:** title=rdesktop - localhost
**No ARGB visuals:** title=rdesktop - localhost
**Non movable windows:** title=rdesktop - localhost
**Non minimizable windows:** title=rdesktop - localhost
**Non maximizable windows:** title=rdesktop - localhost
**Non closable windows:** title=rdesktop - localhost

Goto: **Place Windows**
[LIST]
[*]Enable Place Windows.
[/LIST]

Under **Fixed Window Placement**, Add **Viewport positioned windows:**

**Viewport positioned windows:** (class=rdesktop) & title=rdesktop - localhost
**X Viewport Positions:** 1
**Y Viewport Positions:** 0

This is optional, it is more productive for me when I enable **Edge Flip Pointer**, when my mouse is over the edge of the screen, it switches to Viewport 1 (Where rdesktop is running).


Under **Rotate Cube**, check **Edge Flip Pointer**

Try to run the script, *fingers crossed* once windows is running, we would still need to resize the Virtual Machine Resolution:

My hp tx1000 runs at 1280x800, I would just need to make my VM a little bit shorter to fit the top and bottom gnome bars:

```
VBoxManage controlvm "**XP**" setvideomodehint 1280 760 32
```

Resize your VM to your situation, since some people only have the bottom bars

That should be about it, I will keep updating this thread for instructions as to how to change the default shell on windows... I hope this is helpful :)

*Update*

2008.11.07 - I Upgraded to 8.10 :) and made some changes (see [post 11]("http://ubuntuforums.org/showpost.php?p=6128394&postcount=11"))
2010.03.01 - Changed the port number from 4000 to 3389 (Thanks "Ng Oon-Ee"). Looking at updating this HOWTO...

---

### Post by edmondt on 2008-10-06
So now you should be able to rotate your cube back and forth with your mouse from ubuntu and windows like this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=87699&stc=1&d=1223491506[/IMG]

It is time to replace the windows shell into something lighter, like GeoShell ([download here]("http://www.geoshell.org/index.php?option=com_content&task=view&id=3&Itemid=9")). Install it then goto C:\GeoShell\Utilities and run GeoSkin.exe and choose the skin you like, the one I use was "**silver_luna**" ([see attached]("http://ubuntuforums.org/attachment.php?attachmentid=87701&stc=1&d=1223491989")), I have modified the colors a little bit to make it nicer looking.

Now you have the best of both worlds :) Feel free to ask questions :)


*Attached the [Elementary Wallpaper by lehighost]("http://ubuntuforums.org/attachment.php?attachmentid=87702&stc=1&d=1223492216")

---

### Post by Adam Ryczkowski on 2008-10-13
This howto surely promises a miracle to happen. Unfortunately I'm stuck on various positions.

1. Step 2. The script (both original and modified version) doesn't seem to work when you get configuration from DHCP server (there is no mention of this problem on the meagre documentation from farfewertoes.com). Am I correct?

I know other solution to the bridging problem - one which doesn't require so much scripting. You edit the /etc/network/intefaces:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto tap0
iface tap0 inet manual
tunectl_user <user name, who runs VBox>

auto br0
iface br0 inet dhcp
bridge_ports eth0 tap0
bridge_maxwait 0

```

Be warned, that with this solution only one user can use bridged networking.

3. When I use the bridge config as above, I still couldn't get the script "lanuchXP.sh" to connect with the rdp port. The script get stuck at displaying endlessly "...RDP port is currently closed...". As a workaround I can suggest waiting a minute until Windows boots, and then typing in the terminal "rdesktop <ip.address.of.vbox.guest>". Or get used to using your Ubuntu as a root on regular basis, because the script "launchXP.sh" uses nmap, which successfully probes the 3389 port only when ran by root... ;-)

4. Multiuser environment. Is it possible to have VBox running if you are not the same user, who installed the ubuntu (and not root, of course)? I didn't have much luck due to the network bridging problems.

           *     *           *     *

So, in short. Is it possible to have this perfect Ubuntu + Windows integration when you are not root, and, if yes, what are the minimal rights the user should have (beyond being a member of "vboxusers" group, having a right to read VBox configuration files and having read & write access to the VBox virtual harddrive)?

---

### Post by edmondt on 2008-10-14
Try adding the following to rc.local should work too:

sudo gedit /etc/rc.local

```
echo "Setting up tap0 interface..."
tunctl -t tap1 -u **yourusername**
ifconfig tap1 10.0.1.1

```

Instead of modifying /etc/network/intefaces and see if you can rdp to the VM.

I did not know that nmap in launchXP.sh only works if you are root, I am actually running as a user and it works for me.

```
edmondt@edmondt-laptop:~$ nmap -p 3389 localhost

Starting Nmap 4.53 ( http://insecure.org ) at 2008-10-14 16:06 EDT
Interesting ports on localhost (127.0.0.1):
PORT     STATE SERVICE
3389/tcp open  ms-term-serv

Nmap done: 1 IP address (1 host up) scanned in 0.053 seconds

```

> **Adam Ryczkowski said:**
> This howto surely promises a miracle to happen. Unfortunately I'm stuck on various positions.

1. Step 2. The script (both original and modified version) doesn't seem to work when you get configuration from DHCP server (there is no mention of this problem on the meagre documentation from farfewertoes.com). Am I correct?

I know other solution to the bridging problem - one which doesn't require so much scripting. You edit the /etc/network/intefaces:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto tap0
iface tap0 inet manual
tunectl_user <user name, who runs VBox>

auto br0
iface br0 inet dhcp
bridge_ports eth0 tap0
bridge_maxwait 0

```

Be warned, that with this solution only one user can use bridged networking.

3. When I use the bridge config as above, I still couldn't get the script "lanuchXP.sh" to connect with the rdp port. The script get stuck at displaying endlessly "...RDP port is currently closed...". As a workaround I can suggest waiting a minute until Windows boots, and then typing in the terminal "rdesktop <ip.address.of.vbox.guest>". Or get used to using your Ubuntu as a root on regular basis, because the script "launchXP.sh" uses nmap, which successfully probes the 3389 port only when ran by root... ;-)

4. Multiuser environment. Is it possible to have VBox running if you are not the same user, who installed the ubuntu (and not root, of course)? I didn't have much luck due to the network bridging problems.

           *     *           *     *

So, in short. Is it possible to have this perfect Ubuntu + Windows integration when you are not root, and, if yes, what are the minimal rights the user should have (beyond being a member of "vboxusers" group, having a right to read VBox configuration files and having read & write access to the VBox virtual harddrive)?

---

### Post by markba on 2008-10-18
Your comments about other 'integration 'solutions are spot on, I also strugled with this. I wanted the same (VirtualBox, autostart and connect via rdesktop), but I've taken a slightly different and IMHO much simplier route, to accomplish almost the same as your goal. 

First of all, host interfacing is not needed in this setup. I can see in the script launchXP.sh that rdesktop connects to localhost. The problem is that by using vboxcontrol, this automatically sets these host interfaces for you. Host interfacing almost always leeds to problems, see example(s) in this thread, so if you don't need it, don't set it up.

For autoshutdown I use VBoxControl (a toolset I created myself, see my sig; I apologize for this shameless plug!). VBoxControl does not setup host interfacing, so this can not cause problems.

Next, I don't have a problem with audio on my setup: Hardy, VBox 2.0.2, Windows 2000 with guest additions. Maybe your problem has to do with a different sound setting in VBox (mine is on ALSA) or something else, user/machine specific. 

Autostart at boot time was no problem for me, again using VBoxTool.

You always start rdesktop within launchXP.sh. Although that's nice, I opted for making a starter, pointing to rdesktop.

**In short these are the steps:**

1. [Download]("http://sourceforge.net/project/showfiles.php?group_id=239993") and [install]("http://vboxtool.svn.sourceforge.net/viewvc/vboxtool/trunk/readme.txt?view=markup") VBoxTool

2. Create /etc/vboxtool/machines.conf:

```
Windows 2000,3391
```

3391 is offcourse the VRDP-port on which rdesktop can connect. VBoxTool configures this on startup.

3. Create /etc/vboxtool/vboxtool.conf:

```
vbox_user='<user name>'
```

4. Reboot your system OR issue the following command:

```
vboxtool autostart
```

By now, session(s) should be running and configured.

5. Check if sessions or running, with the assumed vrdp-port:

```
vboxtool showrun
```

6. Create a starter, with commandline: 

```
rdesktop localhost:3391 -T "Windows 2000"
```

That's it. It doesn't do everything just as fancy your solution does, but it is very easy to setup.

[[IMG]http://img232.imageshack.us/img232/7124/win2000autostartrdesktoag9.th.png[/IMG]](http://img232.imageshack.us/my.php?image=win2000autostartrdesktoag9.png)[[IMG]http://img232.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by detroit/zero on 2008-11-05
I'm sorry to say I was unable to get either one of these methods to work. I'm sure i did something wrong, as I've never really messed with rdesktop before, and am all but totally ignorant to the ways of networks and such.

Edmont's method and install seemed to go OK, but after following all his instructions and the instructions for vboxcontrol, when I got to the final stage and tried to launch the script to start my rdesktop session for XP, I got an "invalid machine name" error in terminal. I'm not sure why, as the machine is simply-named "WinXP" and I made sure to change that where needed.

I thought I'd try markba's method, as it seemed a little simpler and more likely to work for someone such as myself. After following all his instructions and issuing the *rdesktop localhost:3391 -T "WinXP"* command, I was promptly shot down with a "Connection Refused" message.  Other commands from the vboxtools help file were also ineffective. *Vboxtools start*, for example, seemed to work (and a *vboxtools showrun* even listed my WinXP machine) but no window was open anywhere on any of my desktops.

Can anybody tell me where I may have gone wrong or what to look for?

---

### Post by markba on 2008-11-05
It seems like the vrdp-port is not configured.

Did you configure /etc/vboxtool/machines.conf? In here, the VRDP-port has to be configured, something like this: Windows XP,3391,

Does 'vboxtool showrun' reveal a configured vrdp-port?

This is some sample output on my machine:

```
$ vboxtool showrun
Windows 2000 Fixed (1): state=running vrdp=3391 cpu=2.0% mem=234m

```

Also, configuration only takes place when issuing 'vboxtool autostart', only on sessions *not* running. Note that this command is automatically executed on boot.

Looking back, I think, my implementation plan lacks some steps. :(

---

### Post by detroit/zero on 2008-11-05
> **markba said:**
> It seems like the vrdp-port is not configured.

Did you configure /etc/vboxtool/machines.conf? In here, the VRDP-port has to be configured, something like this: Windows XP,3391,

Does 'vboxtool showrun' reveal a configured vrdp-port?

This is some sample output on my machine:

```
$ vboxtool showrun
Windows 2000 Fixed (1): state=running vrdp=3391 cpu=2.0% mem=234m

```Also, configuration only takes place when issuing 'vboxtool autostart', only on sessions *not* running. Note that this command is automatically executed on boot.

Looking back, I think, my implementation plan lacks some steps. :(
Should I use the name of the machine itself ("WinXP") or, as you list it ("Windows XP")

I can make it work if I issue the command *rdesktop localhost:3391 -T "WinXP"* from a terminal, but if I try to use the *vboxtool* *start* command, it fails.

Here's the output of vboxtool showrun:```
zero@zero-laptop:~$ vboxtool showrun
WinXP
 New Filter 1
 SanDisk Corporation U3 Cruzer Micro [0010]
 USB DISK 2.0 [0100] (vrdp=3391): running (cpu=8%, mem=405m)
```EDIT: After killing my rdesktop sessions (by doing *killall rdesktop* at a terminal - I didn't have any titlebar or any other way to kill it) now I can't connect with the rdesktop command like before. Here's the error I get now:```
zero@zero-laptop:~$ rdesktop zero-laptop:3391 -T "WinXP"
Autoselected keyboard map en-us
ERROR: connect: Connection refused

```Which is different than it was before - it never said anything about keyboard selection.

Thing is: Now I can connect using *vboxtool autostart*, and I do get output for *vboxtool showrun*, but there's still no window open and no XP desktop being shown.```
zero@zero-laptop:~$ vboxtool autostart
Starting "WinXP
 New Filter 1
 SanDisk Corporation U3 Cruzer Micro [0010]
 USB DISK 2.0 [0100]" (vrdp=3391)
Waiting for the remote session to open...
Remote session has been successfully opened.
zero@zero-laptop:~$ vboxtool showrun
WinXP
 New Filter 1
 SanDisk Corporation U3 Cruzer Micro [0010]
 USB DISK 2.0 [0100] (vrdp=3391): running (cpu=10%, mem=401m)

```[[IMG]http://img368.imageshack.us/img368/8718/screenshotqn9.png[/IMG]]("http://img368.imageshack.us/my.php?image=screenshotqn9.png")

---

### Post by detroit/zero on 2008-11-05
OK, OK... wait. Stop.

I must have slept through something I was doing last night when I followed these instructions.

I didn't realize that the *vboxtool autostart* command was being issued at machine startup.

This explains why I'm getting the "connection refused" output in the terminal - there's no vm running after I did a *vboxtool stop. *

Now, at a freshly started session, if I bring up a terminal and do the rdesktop command as outlined above, I get a window showing my XP-VM desktop. Except there's no window decorations - no titlebar, no min/max buttons, no borders, nothing. And, it opens on whatever desktop I happen to be working off of.

How do I set window rules in CCSM for it? Is the rdesktop window titled "WinXP" if my command is *rdesktop localhost:3391 -T "WinXP"*? That's what the -T switch is, right - the window title?

EDIT: Ok, I figured that out on my own. I guess I'll just quit making posts until I'm done monkeying around. You'll have to excuse me - I drank a lot of coffee today.

---

### Post by markba on 2008-11-05
> **detroit/zero said:**
> I must have slept through something I was doing last night when I followed these instructions.

I am to blame. I adapted the implementation steps (added task 4 + 5), so it should be comprehensive right now.

---

### Post by edmondt on 2008-11-07
*Update:

I changed my VirtualBox setting to null audio and added the -rclipboard:PRIMARYCLIPBOARD -rsound to make sure the clipboard work and sound plays perfectly (only very minor delay when watching youtube videos on the Virtual Machine).

The following code start and stops the rdesktop to the VirtualBox Machine. Save it as rdesktop.sh somewhere and drag and drop to your gnome-panel for your convenience:

```

#!/bin/bash

#Check if rdesktop is running...
if pidof rdesktop | grep [0-9] > /dev/null
  then
    #rdesktop is running, kill it...
    exec killall rdesktop
else
  #Start rdesktop...
  exec rdesktop localhost:3389 -rclipboard:PRIMARYCLIPBOARD -rsound -DP -z -5 -xl

fi
exit

```

You may modify the launchXP.sh to launch this script instead...

```

# now we can fire up rdesktop
echo "Launching rdesktop session..."
#You can launch in seamlessrdp mode if you want to...
#rdesktop localhost:3389 -z -x l &
sh /home/**edmondt**/rdesktop.sh &

```

---

### Post by Arabiest on 2008-11-08
Thank you all

---

### Post by cacadu on 2008-12-14
@ markba
Excuse my English. These online translators are funny! 
My system: Host Ubuntu (Hardy), Guest WinXP (prof).
Your way is the only one who works with me. Starting and Stopping go smoothly. What does not work, are the Number Buttons in the number pad? [+ - * /. enter] goes! This happens only via rdesktop. Do you have a idea, what's wrong?

Greetings from Switzerland
Roland

---

### Post by bigpetefox on 2009-01-31
Highly informative thread, thank you!

---

### Post by Ng Oon-Ee on 2009-02-05
Hi edmondt, thanks for your very informative thread. Just noticed, your script as-is won't work because your awk looks for port 4000 instead of 3389 as stated in the comments. Which is, I believe, the reason for the first respondent's problems.

Thanks again.

---

### Post by tkpunk on 2009-02-08
Hey, this may be a stupid question, but why would I want to run rdesktop along with virtualbox?

---

### Post by Master_Legacy on 2009-03-25
well I've been working on setting up my virtualbox to run TinyXP via this guide and I've run into a couple problems. like detroit/zero I ran into the "invalid machine name" while using edmondt's method, and I don't see where I might have missed changing the machine name.

I then switched to markba's instructions and now I seem to be randomly getting the "Connection Refused" message.  Sometimes the TinyXP desktop appears perfectly, other times it gets the Connection Refused.  although this could just be my lack of understanding of how markba's vboxtool works...

anyway, I'm confused on all the "tap0" stuff people have, I can't get that option to appear under host interfaces, even after trying the various modifications people have posted to /etc/network/interfaces and /etc/rc.local.  

I set the network adapter for this VM to "NAT" since it worked on another windows xp vm I have on this computer, but I'd still like to understand the tap0 things better.  what's the difference between the two options?

i tried googling tap0 and host interfaces but most of the sites i found left me more confused than when I started -_-

oh and since this is my first post on Ubuntu Forums, greetings everyone ;)

---

### Post by corsakh on 2009-10-16
Hey guys, is this possible to extend this or any other seamless windows setup to several workspaces?

---

### Post by mishkind on 2009-11-11
@cacadu
try adding -N to the rdesktop command

  ```
exec rdesktop localhost:3389 -rclipboard:PRIMARYCLIPBOARD -rsound -DP -z -5 -xl -N

```
other rdesktop commands can be found by typing ```
man rdesktop
```

@corsakh
did you ever find a solution for multiple workspaces?

---

### Post by spydeyrch on 2009-12-03
Hey guys, I believe that there was an unanswered question that intrigues me too. Why would you want to use RDP to get asccess to the VM when you can just interact with the VM directly? What is the point of using a remote session? Advantages?
 
Thanks for the info!!
 
:popcorn:
 
-Spydey

---

### Post by edmondt on 2010-03-05
I have found myself using less of VirtualBox these days, since I can now sync my iPhone 3Gs and Windows Mobile from Ubuntu, Outlook 2007 works amazingly well with Crossover Office. But I have VirtualBox just in case I want to run iTunes or Paint Shop Pro etc.

Latest screenshot on Ubuntu 9.10 (attached wallpaper):

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=149087&stc=1&d=1267806260[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=149088&stc=1&d=1267806260[/IMG]

I changed the XP taskbar to the same color as the panel color to a more integrated look :)

Edit: The Ubuntu menu is actually the mintmenu (I simply change the menu icon and change the wording to say "UBUNTU")

---

### Post by Wiredfixer on 2010-11-02
Well, now im working with SeamlessRDP and Runs Fine.. but i have a question...

I want to enable this:

Disable window borders for rdesktop and shadows:

Goto: Window Decoration
Decoration windows: any & !(class=rdesktop)
Shadow windows: & !(type=Dock) & !(class=rdesktop)

But in every single user logged on my pc or another Ubuntu Desktop.

I need to deploy this configuration on several PC, but i cant make it automatic (i've copied .compiz folder on /etc/skel),my goal is make a LiveCD with SeamlessRDP, the appz are on a W2k3 Server, when i execute the shortcut on the LiveCD, the window appears but with the gnome border, i only want to see is the Windows Border.

 I do the configuration in a single machine, works well, but i want to do more automatic because i need to use in LiveCD or with another logged user.

Any thoughts?

---

### Post by edmondt on 2013-03-10
Kinda glad this thread is still here :)

---

### Post by overdrank on 2013-03-11
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

