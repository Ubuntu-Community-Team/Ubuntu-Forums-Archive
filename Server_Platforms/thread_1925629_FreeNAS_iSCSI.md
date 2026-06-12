---
title: "FreeNAS iSCSI"
date: 2012-02-14
forum: Server Platforms
---

### Post by sandyd on 2012-02-14
I currently have several VMs of Ubuntu installed on ESXi.

Just for ZFS, I added a raid volume to the server, and am currently in the process of adding it to freenas.

How can I mount the FreeNAS volumes on Ubuntu through iSCSi?

---

### Post by bakegoodz on 2012-02-17
I'm Not sure you know what iSCSI does, I find many people have heard of it, but don't have the right idea of what it does. I'm taking a Linux server administration class and my instructor knows Samba and LDAP inside and out, but didn't have a clue about iSCSI when someone asked about it. The only thing iSCSI does it makes a storage device on one computer act like its a local drive or device on another computer. So if you connect via iSCSI to a FreeNAS device Linux has to understand the filesystem. Guess what unlike EXT3,4, XFS, JFS, etc, ZFS is not built into Linux. You have add it in one way or another. Look at this page. [https://wiki.ubuntu.com/ZFS](https://wiki.ubuntu.com/ZFS)

Also remember iSCSI will allow multiple computers to connect to the same device, but it is up to you know whether you should do that. Unless it is a Cluster filesystem (not ZFS) having read and write access to the same device from more than one computer will cause filesystem corruption.

I read your question again and realise that you might be doing the opposite having FreeNAS connect to a Ubuntu server. I haven't use FreeNAS much but I think it is all Web based. Here is a iSCSI script I wrote that I use, maybe that can help you

#!/bin/bash

DisplayPartions () { # Format infomation from Parted -l  
IFS=":";
while read A B C D E F G; do 
  if [ "$A" != "BYT;" ]; then 
    if [ "$A" \> "0" ]; then 
      echo -e "$P$A\t$D\t$E\t$F";
    elif [ "$A" == "" ]; then
      echo "";
    else
      P=$A;
      echo -e "Drive/Partition\tSize\tDescription";
      echo -e "$A\t$B\t$G";
    fi;
  fi
done
}

CheckIP () { # Sanity check on entered IP address.
 local  ip=$1
    local  stat=1

    if [[ $ip =~ ^[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}$ ]]; then
        OIFS=$IFS
        IFS='.'
        ip=($ip)
        IFS=$OIFS
        [[ ${ip[0]} -le 255 && ${ip[1]} -le 255 \
            && ${ip[2]} -le 255 && ${ip[3]} -le 255 ]]
        stat=$?
    fi
    return $stat
}


f_iSCSIt () {		# Create iSCSI Target
false
while [ $? != 0 ]
do
  parted -lm | sed -e '/sr0/d' -e '/Warning/d' -e '/read-only/d' | DisplayPartions | sed 's/Error/No Partition Table detected/'
  echo -n "Type in drive to you want dedicated for use by another computer (iSCSI Target): /dev/";
  read target
  file -s /dev/$source     # Checks if device exists
  if [ $? != 0 ]; then # If file program can't find device
    clear
    echo -n $disk; echo " Not a valid Drive, try again"; echo; echo;
    false
  fi
done
 clear
 /etc/init.d/iscsitarget stop
 echo "Target iqn.2011-07.Triage:`date +"%b%d-%H%M"`" > /etc/iet/ietd.conf
 echo "Lun 0 Path=/dev/$target,Type=blockio" >> /etc/iet/ietd.conf
 /etc/init.d/iscsitarget start
 echo "Take note of IP Address"
 for i in `ifconfig | grep "Link encap:" | awk '{print $1}'`; do echo "$i: `ifconfig $i | sed 's/inet addr:/inet addr: /' | grep "inet addr:" | awk '{print $3}'`" | sed '/lo/d'; done
 read -p "Press Enter to continue"
 }

f_iSCSIi () {           # Create iSCSI Initiator
false
while [ $? != 0 ]
do
  echo -n "Type in the IP Address of the iSCSI target: ";
  read RemotePC
  CheckIP $RemotePC     # Pass IP to checker function
  if [ $? != 0 ]; then # Displays the folloing if not a vailid IPV4 address
    clear
    echo -n $disk; echo " Not a valid IP Address, try again"; echo; echo;
    false
  fi
done
 clear
 iscsi_discovery $RemotePC -l -d
 parted -lm | sed -e '/sr0/d' -e '/Warning/d' -e '/read-only/d' | DisplayPartions | sed 's/Error/No Partition Table detected/'    
 read -p "Press Enter to continue"
 }

f_iLogout () {
 clear
 iscsiadm -m node -u
 read -p "Press Enter to continue"
}

f_iShutdown () {
 clear
 /etc/init.d/iscsitarget stop
 echo "" > /etc/iet/ietd.conf
 read -p "Press Enter to continue"
}


while : # Loop till exit
do
clear
cat << !

iSCSI Menu 


  1. iSCSI Target - Allow another computer have dedicated access to a drive

  2. iSCSI Initiator - Connect to remote iSCSI Target drive

  3. Logout - Disconnect connection to remote iSCSI Target

  4. Shutdown local iSCSI Target - Disconnect at remote Initiator first

  5. Exit

!

read choice

case $choice in
1) f_iSCSIt ;;
2) f_iSCSIi ;;
3) f_iLogout ;;
4) f_iShutdown ;;
5) exit ;;
*) echo "\"$choice\" is not valid "; sleep 2 ;;
esac
done

---

### Post by kgatan on 2012-02-18
Ive had the same idee for iscsi and have been trying to evaluate all zfs OS. I thought i could use the zfs file system and share it to alla other OS as iscsi. 

So far ive come to the following conclusion. Please correct me if im missinformed. 

You can use the zfs pool as volume manager for the iscsi devices. 
This will give you some of the functionality of zfs as snapshots and raid management (bare in mind snapshot functionality depends on the filesystem on the shared device and information currently stored in memory). 
As Bakegoodz writes, the filesystem on the device is limited to the initiator OS. 

I would guess that the correct way to use iscsi is not for sharing data but for bootable devices residing on a storage array. For file sharing nfs or cifs is the way to go (with the exception of databases).

---

### Post by kgatan on 2012-02-19
Google is your friend.

Ubuntu 10.04 iscsi target/initiator,
[http://www.howtoforge.com/using-iscsi-on-ubuntu-10.04-initiator-and-target](http://www.howtoforge.com/using-iscsi-on-ubuntu-10.04-initiator-and-target)


FreeNas 8 iscsi guide ESXi,
[http://www.vladan.fr/how-to-configure-freenas-8-for-iscsi-and-connect-to-esxi/](http://www.vladan.fr/how-to-configure-freenas-8-for-iscsi-and-connect-to-esxi/)

---

