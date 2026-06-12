---
title: "Mythbuntu udev rules  - multiple dvb tuners"
date: 2014-04-29
forum: Tutorials
---

### Post by furything on 2014-04-29
Hi 

This post provides my udev rules for mythbuntu when mixing dvb cards between terrestrial and satellite, in my case a dual dvb-t (WinTv NOVA TD500) and a quad dvb-s2 (TBS-6985). When searching the internet I could not find a complete answer so hopefully this will help someone avoid my pain.

So why do all this? Every time you reboot your system, udev can reassign the dvb tuners thus mixing them up. This means tuner one that was configured for satellite is now configured as terrestrial. You can no longer use tuner one as it tries to tune a satellite frequency instead of terrestrial. You can of course check the backend every time you reboot and configure as appropriate or you can use udev with symbolic names and never have to worry again.

This particular website helped a lot although if you compare my bash script and udev rules you will see that I could not get this sites information to work properly
[URL="http://www.digitalinferno.com/wiki/Wiki.jsp?page=UDEV"]http://www.digitalinferno.com/wiki/Wiki.jsp?page=UDEV

[/URL]The main issues I had with this sites examples were 
[LIST=1]
[*]The parameter passing from the udev rules file to the bash script 
[*]The site uses a udev rule of 
[/LIST]
> KERNEL=="dvb[0-9]*",KERNELS=="0000:03:00.0"
For the latter I ended up with multiple symbolic links for the same dvb tuner

This site contains a lot of useful information so I won't repeat all of it but view this site first, particularly how to identify your dvb tuner
```
udevadm info -a -p $(udevadm info -q path -n /dev/dvb/adapterX/frontendY)
```
This helps you work out the most appropriate rules for your tuner. Trial and error is the best way here. Look at the output and create a list of unique values for a particualr dvb tuner to filter against. This way you will get a single symbolic link for the actual tuner you want.

So I have added my udev rule to 
> /etc/udev/rules.d/99-dvb.rules
My understanding is you can name the file pretty much anything provided you do not use the system provided ones but it does help to try and identify what the purpose is if you include dvb in the name.

My rules
```
# New rules file to create symlink for quad and dual DVB tuners
# Reminder to get data: udevinfo -a -p $(udevinfo -q path -n /dev/dvb/adapter0/frontend0)

# Create a symlink /dev/dvb/adapter_tbsx pointing to TBS 
## TBS 6985 DVB-S2 quad tuner card
# add action
KERNELS=="0000:04:00.0",ENV{DVB_DEVICE_TYPE}=="frontend",SUBSYSTEM=="dvb",SUBSYSTEMS=="pci",DRIVERS=="SAA716x TBS",ATTRS{subsystem_device}=="0x0002", ATTRS{subsystem_vendor}=="0x6985", ATTRS{device}=="0x7160", ACTION=="add", ENV{devpath}="%k", ENV{link}="/dev/dvb/adapter_tbs", RUN+="/etc/udev/create-ln.sh '$env{devpath}' '$env{link}'"

# remove action, for the multi tuner card we just remove everything whenever one is removed... since they are all from the same card
KERNELS=="0000:04:00.0",ENV{DVB_DEVICE_TYPE}=="frontend",SUBSYSTEM=="dvb",SUBSYSTEMS=="pci",DRIVERS=="SAA716x TBS",ATTRS{subsystem_device}=="0x0002", ATTRS{subsystem_vendor}=="0x6985", ATTRS{device}=="0x7160", ACTION=="remove", PROGRAM="/bin/sh -c 'rm -f /dev/dvb/adapter_tbs*'"

# Create a symlinks for both tuners of Hauppauge Nova-T device
KERNELS=="2-1" ENV{DVB_DEVICE_TYPE}=="frontend",SUBSYSTEM=="dvb", SUBSYSTEMS=="usb", DRIVERS=="usb", ATTRS{idProduct}=="8400", ATTRS{bcdDevice}=="0100", ATTRS{product}=="WinTV Nova-DT", ATTRS{idVendor}=="2040", ATTRS{idProduct}=="8400", ACTION=="add", ENV{devpath}="%k", ENV{link}="/dev/dvb/adapter_hp", RUN="/etc/udev/create-ln.sh '$env{devpath}' '$env{link}'"

# remove action, for both tuners of Hauppauge Nova-T device
KERNELS=="2-1" ENV{DVB_DEVICE_TYPE}=="frontend",SUBSYSTEM=="dvb", SUBSYSTEMS=="usb", DRIVERS=="usb", ATTRS{idProduct}=="8400", ATTRS{bcdDevice}=="0100", ATTRS{product}=="WinTV Nova-DT", ATTRS{idVendor}=="2040", ATTRS{idProduct}=="8400", ACTION=="remove", PROGRAM="/bin/sh -c 'rm -f /dev/dvb/adapter_hp*'"
```

My script file (if you examine my udev rules file) lives in /etc/udev and must be given execute permissions. For parameter passing apparently you just use $1 for the first parameter and $2 the second and so on. My script uses this parameter reference as opposed to trying to pass $link1 as in the [http://www.digitalinferno.com/wiki/Wiki.jsp?page=UDEV](http://www.digitalinferno.com/wiki/Wiki.jsp?page=UDEV) example. Also note that I have added the ability to distinguish between 2 dvb cards as they both have multiple tuners. Every example I had for the nova T tuner ended giving the second tuner both symbolic links so you actually lose a tuner (you don't access it through the symbolic link).
```
#!/bin/bash
# $1 is the device full path, $2 is the symbolic link we are trying to create
link=$2

number=$(echo "$1" | cut -d \. -f1 | grep -s -o -E '[0-9]+')

# I don't want to change the link variable, so this will be the symlink name
pathTo="$link"

#check if we are dealing with the tbs multi tuner card
if [[ $link == *adapter_tbs ]]; then
        datfile="/run/tbs-dvb-num"
        lockfile="$datfile.lck"

        exec 9>>"$lockfile"
        flock -x -w 5 9 || exit
        {
            tbs_adapter_num="1"
            if [ -e "$datfile" ]; then
                read -r tbs_adapter_num < "$datfile"
            fi
            next=`expr $tbs_adapter_num + 1`
            echo $next > "$datfile"
            pathTo="$link$tbs_adapter_num"
        } 9<&-
        exec 9<&-
fi

if [[ $link == *adapter_hp ]]; then
        datfile="/run/hp-dvb-num"
        lockfile="$datfile.lck"

        exec 9>>"$lockfile"
        flock -x -w 5 9 || exit
        {
            hp_adapter_num="1"
            if [ -e "$datfile" ]; then
                read -r hp_adapter_num < "$datfile"
            fi
            next=`expr $hp_adapter_num + 1`
            echo $next > "$datfile"
            pathTo="$link$hp_adapter_num"
        } 9<&-
        exec 9<&-
fi

dvb="/dev/dvb/adapter$number"

ln -f     -n -s $dvb $pathTo
```

If you have a** single** satallite tuner together with a **single** terrestrial tuner you don't need a bash script. Just find a way and uniquely identify you dvb tuners and enter a single udev rules for each.

Now all you have to do is open myth backend and change each tuner to point to a symbolic link instead of the actual dvb adapter

---

