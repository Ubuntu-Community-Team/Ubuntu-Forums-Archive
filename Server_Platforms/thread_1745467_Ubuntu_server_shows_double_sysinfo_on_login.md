---
title: "Ubuntu server shows double sysinfo on login"
date: 2011-05-01
forum: Server Platforms
---

### Post by paal_a on 2011-05-01
When I SSH into any of my Ubuntu 10.04.2 LTS (x86) server installations I get TWO sysinfos. One for current time and another from April 20.

```

Linux ubuntusrv1 2.6.32-31-generic-pae #61-Ubuntu SMP Fri Apr 8 20:00:13 UTC 2011 i686 GNU/Linux
Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

  System information as of Sun May  1 08:55:58 CEST 2011

  System load:  0.0               Processes:           90
  Usage of /:   7.8% of 29.93GB   Users logged in:     0
  Memory usage: 54%               IP address for eth0: 192.168.10.11
  Swap usage:   0%

  Graph this data and manage this system at https://landscape.canonical.com/

Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

  System information as of Wed Apr 20 22:09:50 CEST 2011

  System load:  0.09              Processes:           93
  Usage of /:   7.9% of 29.93GB   Users logged in:     0
  Memory usage: 57%               IP address for eth0: 192.168.10.11
  Swap usage:   1%

  Graph this data and manage this system at https://landscape.canonical.com/

5 packages can be updated.
0 updates are security updates.

Last login: Sun May  1 08:45:53 2011 from 192.168.10.198

```

At first I only notices the 5 packages can be updated. But after runing apt-get update and upgrade as well as trying aptitude full-upgrade without any packages being updated I noticed the sysinfo actually showing two different days. Any idea on how to get rid of the second one?

---

### Post by CharlesA on 2011-05-01
Check to see what is in /etc/motd.tail.

---

### Post by elico on 2011-05-01
[SIZE=3]**edit:** simple soulution[/SIZE]
run the command:
> /usr/lib/update-notifier/update-motd-updates-available --forceyou will get the current status.

and to make sure it will work properly change the file:
/etc/update-motd.d/90-updates-available

from:
> exec /usr/lib/update-notifier/update-motd-updates-availableto
> exec /usr/lib/update-notifier/update-motd-updates-available --force
and make sure to remove the /etc/motd or /etc/motd.tail fle
[SIZE=4][B]

here is my old post:[/B][/SIZE]
> it's a bug from lately caused by landscape or motd.
if you use the commands:
[QUOTE]apt-get clean
apt-get update
apt-get upgradeand you get the output
> Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
then the os is updated and there is a bug in the landscape/motd.
to make sure it's motd
use
> cat /etc/motd
cat /etc/motd.tail
 and you should get the same stuff wrong.(double)
then erase the files using:
> rm /etc/motd
rm /etc/motd.tailand re install landscape-common
> apt-get -f install --reinstall landscape-commonlogout and then login and see what happens.

[B]just remember that if apt-get upgrade output is that your os is updated it is updated.
[/B][/QUOTE]

---

### Post by elico on 2011-05-01
got a nice script that make sure that everything is ok with a nice login screen:
based on:[http://www.ubuntugeek.com/how-to-change-message-of-the-day-motd-in-ubuntu-server.html](http://www.ubuntugeek.com/how-to-change-message-of-the-day-motd-in-ubuntu-server.html)

> 
#!/bin/bash
function mydate(){
strDayofMonth=$(date +%d)
intLength=${#strDayofMonth}
intOff=$(($intLength-1))
strDayPart=${strDayofMonth:intLength:intOff}

case $strDayPart in

1)
strOrdinal="st"
;;

2)
strOrdinal="nd"
;;

3)
strOrdinal="rd"
;;

*)
strOrdinal="th"
;;

esac
day=$(date +%d | sed 's/^0//')
myDate=$(date +%A" "%B" $day$strOrdinal, "%Y" at "%l":"%M%P" "%Z)
}

echo

### START MESSAGE OF THE DAY ###
cal
echo -n "\"$(hostname)\" $(cat /etc/issue)-$(uname -r)";echo
mydate
echo $myDate
echo

### PHYSICAL DRIVE USAGE ###
drives=$(df | grep "/dev/sd" | awk '{print $1}')
echo "Disk Usage"
echo "----------"
echo "$(df -h --total $drives)"
echo

### IPV4 INTERFACE INFORMATION ###
echo "Interfaces"
echo "----------"
list=$(ifconfig | grep "eth" | awk '{print $1}')
for item in $list; do
address=$(ifconfig $item | grep "inet addr" | awk '{print $2}' | cut -d ":" -f2)
echo "IPV4 Address of $item is $address"
done
echo

### SYSTEM INFORMATION ###
echo "System Info"
echo "-----------"
pcount=$(ps aux | wc -l)
phymem=$(free -m | grep "Mem:" | awk '{printf "%d%%\n", $3*100/$2}')
swapmem=$(free -m | grep "Swap:" | awk '{printf "%d%%\n", $3*100/$2}')
updatea=$(/usr/lib/update-notifier/update-motd-updates-available --force)
echo "Total Processes: $pcount"
echo "Physical memory usage: $phymem"
echo "Swap memory usage: $swapmem"
echo "updates avilable: $updatea"
echo

### USER LOGIN INFORMATION ###
echo "Login Info"
echo "----------"
logins=$(who | wc -l)
echo "Number of users logged in: $logins"
who
echo

exit 0

---

