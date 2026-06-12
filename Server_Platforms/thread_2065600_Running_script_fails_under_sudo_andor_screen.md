---
title: "Running script fails under sudo and/or screen"
date: 2012-10-02
forum: Server Platforms
---

### Post by MG2R on 2012-10-02
I recently reinstalled ubuntu server on my home server. Before I did this I used to have a GUI, but now I opted for a pure CLI.

The problem is that I have a script that needs to run 24-7. The script pings for my laptop's IP and, if my laptop is on, turn on the hard drives. Before, I did this by opening a GUI terminal emulator and executing the script in there. This script runs perfectly fine if I execute it as myself in a regular shell, but from the moment I execute it as root using sudo, it fails.

The script is:
```
enabled=2
while true
do
    if ping -c 1 192.168.1.150 > /dev/null 2>&1
    then
        if ((enabled!=0))
        then
        sudo hdparm -S 0 /dev/sda /dev/sdb
            echo "RAID stand-by disabled"
        fi
        enabled=0
    else
        if ((enabled!=1))
        then
        sudo hdparm -S 2 /dev/sda /dev/sdb
            echo "RAID stand-by enabled"
        fi
        enabled=1
    fi
    sleep 1m
done
```

The error message it gives is:
```
./ping.sh: 14: ./ping.sh: enabled!=1: not found
```

Now, I want this script to run on boot, in the background, with the possibility for me to ssh into the server and take control of the process running the script. So naturally I tried to run the script in SCREEN with the command
```
screen -S ping ~simon/ping.sh
```

This, however, returns the same error as running the script as root. So I thought that maybe screen can not run the script. But when I open a screen with
```
screen -S ping
```
and then type in the command manually, the script runs perfect.

My question: how can I make
```
screen -S ping ~simon/ping.sh
```
work so that I can add it to my crontab? Is the script wrong or is there more at play (linux-internals)?

---

### Post by steeldriver on 2012-10-02
you don't seem to be specifying a shell / interpreter (hashbang) - possibly the root environment is running it in /bin/sh where ((enabled!=0)) is not a valid construct? 

(btw I don't think it's a standard way of doing an integer test in bash either - maybe consider either [ $enabled -ne 0 ] or [[ $enabled != 0 ]] instead?)

---

### Post by LHammonds on 2012-10-02
Yes, the primary problem here is the missing interpreter line.

If you add this via crontab, I would recommend adding a shell path to crontab to make sure it can find all the binary programs you are using too.  Have a look at [this link]("http://www.hammondslegacy.com/forum/viewtopic.php?p=261&sid=2b354c5bc8c57cc2af630d07457dff9a#p261") to see what I'm talking about.

I can help you out if you need me...just send me a PM.

**EDIT:** Here is the modified script:

/var/scripts/drivetoggle.sh
```

#!/bin/bash
#############################################
## Name          : drivetoggle.sh
## Version       : 1.1
## Date          : 2012-10-02
## Author        : MG2R
## Compatibility : Ubuntu Server 12.04.1 LTS
## Purpose       : Toggle drives on/offline based on status of IP.
## Run Frequency : Continuous
## Exit Codes    : None
## Forum         : http://ubuntuforums.org/showthread.php?t=2065600
################ CHANGE LOG #################
## DATE       WHO  WHAT WAS CHANGED
## ---------- ---- ----------------------------
## 2012-10-02 MG2R Created script.
## 2012-10-02 LTH  Minor updates to work via sudo or crontab.
#############################################
Logfile="/var/log/drivetoggle.log"
Machine="192.168.1.150"
Enabled=2
echo "`date +%Y-%m-%d_%H:%M:%S` [INFO] Script started." | tee -a ${Logfile}
while true
do
  ping -c 1 ${Machine} > /dev/null 2>&1
  if [ $? -eq 0 ]; then
    ## Machine is online.
    if [ ${Enabled} -ne 0 ]; then
      ## Turn on the drives.
      hdparm -S 0 /dev/sda /dev/sdb
      echo "`date +%Y-%m-%d_%H:%M:%S` RAID stand-by disabled" | tee -a ${Logfile}
    fi
    Enabled=0
  else
    ## Machine is offline.
    if [ ${Enabled} -ne 1 ]; then
      ## Turn off the drives.
      hdparm -S 2 /dev/sda /dev/sdb
      echo "`date +%Y-%m-%d_%H:%M:%S` RAID stand-by enabled" | tee -a ${Logfile}
    fi
    Enabled=1
  fi
  sleep 1m
done

```Login with your admin account and type "sudo su" to temporarily login as root user.

Type the following:

```

mkdir /var/data
touch /var/data/crontab.root
chown root:root /var/data/crontab.root
chmod 0600 /var/data/crontab.root

```Edit /var/data/crontab.root and add this to the file:

NOTE: If you have anything in the crontab schedule now, add it to this file.

```

########################################
# Name: Crontab Schedule for root user
# Author: LHammonds
############# Update Log ###############
# 2012-10-02 - LTH - Created schedule
########################################

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# Crontab SYNTAX:
# minute(0-59) hour(0-23) day-of-month(1-31) month(1-12) day-of-week(0-6) command-to-execute
#
# Adjust the time clock
#
0 1-23 * * * /usr/sbin/ntpdate ntp.ubuntu.com > /dev/null 2>&1
#
# Toggle drives on/offline based on status of IP
#
@reboot /var/scripts/drivetoggle.sh > /dev/null 2>&1

```To enable the root schedule using this file, type the following:

```
crontab -u root /var/data/crontab.root
```To disable the root schedule, type the following:

```

touch /tmp/deleteme
crontab -u root /tmp/deleteme
rm /tmp/deleteme

```LHammonds

---

### Post by MG2R on 2012-10-02
> **LHammonds said:**
> Yes, the primary problem here is the missing interpreter line.

If you add this via crontab, I would recommend adding a shell path to crontab to make sure it can find all the binary programs you are using too.  Have a look at [this link]("http://www.hammondslegacy.com/forum/viewtopic.php?p=261&sid=2b354c5bc8c57cc2af630d07457dff9a#p261") to see what I'm talking about.

Ok, I've followed your procedure and checked out your forums... Going to look more closely at the mail setup guide in the near future (I've been attempting to make a private mail server for over a year).

One more question: if I want to add more IP adresses that need to be checked, what is the most efficient way to do this? At the moment I did it like this:
```
#!/bin/bash
#############################################
## Name          : drivetoggle.sh
## Version       : 1.1
## Date          : 2012-10-02
## Author        : MG2R
## Compatibility : Ubuntu Server 12.04.1 LTS
## Purpose       : Toggle drives on/offline based on status of IP.
## Run Frequency : Continuous
## Exit Codes    : None
## Forum         : http://ubuntuforums.org/showthread.php?t=2065600
################ CHANGE LOG #################
## DATE       WHO  WHAT WAS CHANGED
## ---------- ---- ----------------------------
## 2012-10-02 MG2R Created script.
## 2012-10-02 LTH  Minor updates to work via sudo or crontab.
#############################################
Logfile="/var/log/drivetoggle.log"
Machine1="192.168.1.151"
Machine2="192.168.1.152"
Enabled=2
echo "`date +%Y-%m-%d_%H:%M:%S` [INFO] Script started." | tee -a ${Logfile}
while true
do
  ping -c 1 ${Machine1} > /dev/null 2>&1 || ping -c 1 ${Machine2} > /dev/null 2>&1
  if [ $? -eq 0 ]; then
    ## Machine is online.
    if [ ${Enabled} -ne 0 ]; then
      ## Turn on the drives.
      hdparm -S 0 /dev/sda /dev/sdb
      echo "`date +%Y-%m-%d_%H:%M:%S` RAID stand-by disabled" | tee -a ${Logfile}
    fi
    Enabled=0
  else
    ## Machine is offline.
    if [ ${Enabled} -ne 1 ]; then
      ## Turn off the drives.
      hdparm -S 2 /dev/sda /dev/sdb
      echo "`date +%Y-%m-%d_%H:%M:%S` RAID stand-by enabled" | tee -a ${Logfile}
    fi
    Enabled=1
  fi
  sleep 1m
done
```

which seems to work. Or is there a better way?

Thanks a lot!

---

### Post by LHammonds on 2012-10-02
Are you wanting to check very specific IP addresses or a range?

**EDIT:** For a range, you can use the handy-dandy seq command.

Example block of code:
```

ip-start=150
ip-stop=160

for ipaddr in $(seq ${ip-start} ${ip-stop}); do
  ping -c 1 192.168.1.${ipaddr}
done

```

---

### Post by usalug on 2012-10-03
Try putting your ip's you want to search into a for loop.

```

#!/bin/bash
echo "`date +%Y-%m-%d_%H:%M:%S` [INFO] Script started." | tee -a ${Logfile}

# Start outer loop
while true
  do

    # Start inner loop
    for MACHINE in 192.168.1.151, 192.168.1.153
      do
	ping -c 1 ${MACHINE} > /dev/null 2>&1
	if [ $? -eq 0 ]; then
	  ## Machine is online.
	  if [ ${Enabled} -ne 0 ]; then
	    ## Turn on the drives.
	    hdparm -S 0 /dev/sda /dev/sdb
	    echo "`date +%Y-%m-%d_%H:%M:%S` RAID stand-by disabled" | tee -a ${Logfile}
	  fi
	Enabled=0
	else
    ## Machine is offline.
      if [ ${Enabled} -ne 1 ]; then
	## Turn off the drives.
	hdparm -S 2 /dev/sda /dev/sdb
	echo "`date +%Y-%m-%d_%H:%M:%S` RAID stand-by enabled" | tee -a ${Logfile}
      fi
      Enabled=1
    fi
  done
  # end inner loop

  sleep 1m
done
# end outer loop

```

---

