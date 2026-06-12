---
title: "GUI program to change the CPU frequency scaling governor"
date: 2012-05-03
forum: The Cafe
---

### Post by JRV on 2012-05-03
Tested on Ubuntu 12.04 (Precise Pangolin) 64 bit.
Should work on all versions with Unity.

System Requirements: A processor that supports frequency scaling.

Dependencies: cpufrequtils - Can be installed from software center.
               zenity - preinstalled on Ubuntu, not on Lubuntu.

Copy this code to a file in your home directory:
```

#!/bin/bash

# Tested on Ubuntu 12.04 (Precise Pangolin) 64 bit.
# Should work on all versions with Unity.

# System Requirements: A processor that supports frequency scaling.

# Dependencies: cpufrequtils - Can be installed from software center.
#               zenity - preinstalled on Ubuntu, not on Lubuntu.

# Copy this to a file in your home directory.
# Name the file "Freq.sh"
# Make it executable with the command: chmod +x Freq.sh

# Available options on my machine:
#   conservative 
#   ondemand 
#   userspace 
#   powersave 
#   performance 
#
# Yours may be different. Run this command to check, make changes if necessary.
#
# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors

# I have a quad core processor with hyperthreading, so I have eight threads running.
# Change the scaling governor for all of them (--cpu 0 - 7)
# You will need to add/delete lines to equal the number of threads you have running.
# Run System Monitor and look at the Resources tab to see how many threads are running.
# System Monitor starts counting at one, you will need to start from zero.

# Run the program from the terminal with the command: gksudo ./Freq.sh
 
# Check to make sure it is working with this command:
#
#   cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

# To create a launcher:
#
# install alacarte with the command: sudo apt-get install alacarte
#
# Run alacarte, click New Item
#
# Type: Application
# Name: Freq
# Command: gksudo /home/YOUR_USER_NAME/Freq.sh
# Commant: Whatever you want to say. 
#
# I left the springboard icon, you can click on the icon to change it.  
#
# Click Okay 
#
# This will create a file named Freq.desktop in /home/YOUR_USER_NAME/.local/share/applications.
# It can be found in the dash.
# It will have an entirly different name if you open a terminal 
# and look for it from the command line. This is normal.



GOV=`zenity --title="Freq" --text="Set Frequency Scaling Governor" --height=300 --width=300 \
--list --column="Available Settings:" "Conservative" "Ondemand" "Userspace" "Powersave" "Performance"`

if [ "$GOV" = "Conservative" ]; then
   cpufreq-set --cpu 0 --governor conservative
   cpufreq-set --cpu 1 --governor conservative
   cpufreq-set --cpu 2 --governor conservative
   cpufreq-set --cpu 3 --governor conservative
   cpufreq-set --cpu 4 --governor conservative
   cpufreq-set --cpu 5 --governor conservative
   cpufreq-set --cpu 6 --governor conservative
   cpufreq-set --cpu 7 --governor conservative
fi

if [ "$GOV" = "Ondemand" ]; then
   cpufreq-set --cpu 0 --governor ondemand
   cpufreq-set --cpu 1 --governor ondemand
   cpufreq-set --cpu 2 --governor ondemand
   cpufreq-set --cpu 3 --governor ondemand
   cpufreq-set --cpu 4 --governor ondemand
   cpufreq-set --cpu 5 --governor ondemand
   cpufreq-set --cpu 6 --governor ondemand
   cpufreq-set --cpu 7 --governor ondemand
fi

if [ "$GOV" = "Userspace" ]; then
   cpufreq-set --cpu 0 --governor userspace
   cpufreq-set --cpu 1 --governor userspace
   cpufreq-set --cpu 2 --governor userspace
   cpufreq-set --cpu 3 --governor userspace
   cpufreq-set --cpu 4 --governor userspace
   cpufreq-set --cpu 5 --governor userspace
   cpufreq-set --cpu 6 --governor userspace
   cpufreq-set --cpu 7 --governor userspace
fi

if [ "$GOV" = "Powersave" ]; then
   cpufreq-set --cpu 0 --governor powersave
   cpufreq-set --cpu 1 --governor powersave
   cpufreq-set --cpu 2 --governor powersave
   cpufreq-set --cpu 3 --governor powersave
   cpufreq-set --cpu 4 --governor powersave
   cpufreq-set --cpu 5 --governor powersave
   cpufreq-set --cpu 6 --governor powersave
   cpufreq-set --cpu 7 --governor powersave
fi

if [ "$GOV" = "Performance" ]; then
   cpufreq-set --cpu 0 --governor performance
   cpufreq-set --cpu 1 --governor performance
   cpufreq-set --cpu 2 --governor performance
   cpufreq-set --cpu 3 --governor performance
   cpufreq-set --cpu 4 --governor performance
   cpufreq-set --cpu 5 --governor performance
   cpufreq-set --cpu 6 --governor performance
   cpufreq-set --cpu 7 --governor performance
fi

```

Name the file "Freq.sh"
Make it executable with the command:
```

chmod +x Freq.sh

```

Available options on my machine:
[LIST]
[*] conservative 
[*] ondemand 
[*] userspace 
[*] powersave 
[*] performance 
[/LIST]

Yours may be different. Run this command to check, make changes if necessary.
```

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors

```

I have a quad core processor with hyperthreading, so I have eight threads running.
Change the scaling governor for all of them (--cpu 0 - 7)
You will need to add/delete lines to equal the number of threads you have running.
Run System Monitor and look at the Resources tab to see how many threads are running.
System Monitor starts counting at one, you will need to start from zero.

Run the program from the terminal with the command: 
```

gksudo ./Freq.sh
[/CODE} 
Check to make sure it is working with this command:
[CODE]
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```
It should return the governor setting that you set.

To create the launcher:

Install alacarte with the command:
```

sudo apt-get install alacarte

```

Run alacarte, click New Item.

[LIST]
[*] Type: Application
[*] Name: Freq
[*] Command: gksudo /home/USER_NAME/Freq.sh
[*] Commant: Whatever you want to say. 
[/LIST]

I left the springboard icon, you can click on the icon to change it.  

Click Okay 

This will create a file named Freq.desktop in /home/USER_NAME/.local/share/applications.
It can be found in the dash.
It will have an entirly different name if you open a terminal 
and look for it from the command line. This is normal.

This documentation is included in comments in the script file,
I like well documented programs.

---

### Post by mwinthrop on 2012-05-13
I very much appreciate your tutorial and script code.  I just used it in Ubuntu Studio 12.04 using the XFCE4 desktop and it worked nicely.  Thanks.

---

### Post by ssam on 2012-05-13
have you benchmarked to see the effect of these modes?

> To a first approximation, the Powersave governor will only save you power if you're playing 3D games. The performance governor will basically never give you extra performance. Don't use them. Use ondemand instead. Do not make it easy for your users to choose them. They will get it wrong, because it is difficult to explain why this result is true.
Thermal management is not the job of a power manager. Using power management to implement thermal management will result in your computer taking up more power overall, reducing battery life. Implement things in the right places.

[http://mjg59.livejournal.com/101706.html](http://mjg59.livejournal.com/101706.html)
[http://mjg59.livejournal.com/92880.html](http://mjg59.livejournal.com/92880.html)

---

### Post by Thibaud74 on 2012-08-19
Thanks you. However, the cpu-freq-set doesn't work with me. It modifies the governor, but the governor changes immediatly and come back to "ondemand" flag. Any ideas ?

Thanks you,
Thibaud.

---

### Post by eexcellent on 2012-10-28
This worked for me thanks JRV :)

Xubuntu 12.04 athlon II x2 250

---

### Post by thirnick on 2012-11-22
good post  i wish it had been my first search hit

---

### Post by pqwoerituytrueiwoq on 2012-11-22
You could mode my cpu-freq-applet script for my genmon plugin in xfce, it auto detects governors, speeds, and cores relevant code in bold
```
#!/bin/bash
ICONS="/usr/local/share/pixmaps/cpufreq-applet"
if [ -z "$1" ];then
    echo "<img>$ICONS/cpufreq-na.png</img><txt>Which Core?</txt>"
    echo -e "<tool>$(basename $0) [Core Number]\n$(basename $0) 0</tool>"
    exit
fi
[B]LOC="/sys/devices/system/cpu/cpu$1/cpufreq"
GOV=$(cat $LOC/scaling_governor)
if [ "$2" == "--set" ];then
    GOVS=$(cat $LOC/scaling_available_governors)
    LIST=$(echo ${GOVS:0:-1} | sed 's/.*/\L&/;s/[a-z]*/\u&/g;s/ / FALSE /g')
    NewGOV=$(zenity --list --title 'Choose a Governor' --text 'Select one' --radiolist --column 'Pick' --column 'Opinion' TRUE $LIST)
    if [ -n "$NewGOV" ];then
        if [ "$NewGOV" == "Userspace" ];then
            SPD=$(cat $LOC/scaling_available_frequencies)
            LIST=$(echo ${SPD:0:-1} | sed 's/ / FALSE /g')
            NewSPD=$(zenity --list --title 'Choose a Frequency' --text 'Select one' --radiolist --column 'Pick' --column 'Opinion' TRUE $LIST)
            if [ -z "$NewSPD" ];then
                exit
            fi
        fi
        CoreCt=$(ls /sys/devices/system/cpu/ | grep 'cpu[0-9]' | wc -l)
        if [ $CoreCt -gt 1 ];then
            if [ $(zenity --question --text="Apply this to all cores?";echo $?) -eq 0 ];then
                Core=0
                while [ $Core -lt $CoreCt ];do
                    #echo ${NewGOV,} > /sys/devices/system/cpu/cpu$Core/cpufreq/scaling_governor
                    cpufreq-set -c $Core -g ${NewGOV,}
                    if [ -n "$NewSPD" ];then
                        #echo $NewSPD > /sys/devices/system/cpu/cpu$Core/cpufreq/scaling_setspeed
                        cpufreq-set -c $Core -f $NewSPD
                    fi
                    Core=$(($Core+1))
                done
                exit
            fi
        fi
        #echo ${NewGOV,} > $LOC/scaling_governor
        cpufreq-set -c $1 -g ${NewGOV,}
        if [ -n "$NewSPD" ];then
            #echo $NewSPD > $LOC/scaling_setspeed
            cpufreq-set -c $1 -f $NewSPD
        fi
    fi
    exit
fi[/B]
CUR=$(cat $LOC/scaling_cur_freq)
MAX=$(cat $LOC/scaling_max_freq)
USE=$(perl -e "print int($CUR/$MAX*1000)")
GHz=$(perl -e "print $CUR/1000000")
if [ "$2" == "--bar" ];then
    echo "<img>$ICONS/cpufreq-na.png</img>"
    echo "<bar>$(($USE/10))</bar>"
elif [ $USE -lt 125 ];then
    echo "<img>$ICONS/cpufreq-0.png</img>"
elif [ $USE -lt 375 ];then
    echo "<img>$ICONS/cpufreq-25.png</img>"
elif [ $USE -lt 625 ];then
    echo "<img>$ICONS/cpufreq-50.png</img>"
elif [ $USE -lt 875 ];then
    echo "<img>$ICONS/cpufreq-75.png</img>"
else
    echo "<img>$ICONS/cpufreq-100.png</img>"
fi
if [ ${GHz:0:1} -gt 0 ];then
    Spd="$GHz GHz"
else
    MHz=$(perl -e "print $GHz*1000")
    Spd="$MHz MHz"
fi
USE="$(($USE/10))"
if [ $USE -lt 100 ];then
    echo "<txt>$USE%<span fgcolor=\"#18191A\">0</span></txt>" # 18191A is my panel color
else
    echo "<txt>$USE%</txt>"
fi
echo -e "<tool>Core $1 is at $Spd\nGovernor is ${GOV^}</tool>"
echo "<click>$(basename $0) $1 --set</click>"
exit

```to anyone who wants my scrip as is i attached the image files
This will allow yuo to change the gov/freq, until you reboot (change the 3 to the number of cores/threads you have -1)
```
sudo bash -c "chmod 777 /sys/devices/system/cpu/cpu{0..**3**}/cpufreq/{scaling_setspeed,scaling_governor}"
```

---

### Post by alterpinguin on 2013-08-30
hi, maybe usefull for someone too, it toggles between ondemand and powersave.
I use this script (i named it "switch_cpu_governer.sh") with a starter in the desktop top-bar:
```

#!/bin/bash
# made for Ubuntu-12.04, cause i missed the old button to pull down cpu-s
# to powersave or back to ondemand
# has to be run as "bash" for the numerical calculation with "let"
#
# first get the current state of the cpu-setting
gov=`cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor`;
#echo "old $gov";
# now toggle the setting - may go wrong if future kernel may change names
# --- but why should they?
# if current cpu setting is ondemand, set new to powersave or set ondemand
if [ "$gov" = "ondemand" ]; then
        gov="powersave";
else
        gov="ondemand";
fi
#echo "new $gov"
# no count thru all available cpu-cores and set the new state
let cpu=0
#for i in 0 1; do
for i in /sys/devices/system/cpu/cpu?; do
#echo "$cpu -   cpufreq-selector -c $i -g $gov"
        cpufreq-selector -c $cpu -g $gov
        let cpu=cpu+1
done
# give some visual response what was done
zenity --notification --text "cpugoverner: $gov" &

```

---

