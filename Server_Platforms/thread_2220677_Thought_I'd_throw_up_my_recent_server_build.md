---
title: "Thought I'd throw up my recent server build"
date: 2014-04-29
forum: Server Platforms
---

### Post by david144 on 2014-04-29
This post documents the build of my iSCSI SAN target server.
For many people the use of NAS devices off the shelf is second nature. Some people may want to build an iSCSI target for specific purposes such as increased storage for their desktop, or in my case I plan to use it to increase storage for my HTPC and VMWare host. I know a lot of people think it's a lot of trouble to go to but it's satisfying when you can build something like a Drobo, HP Smart Array, Dell Powervault, Apple xStack, or EMC (although not the same performance or functionality of course) at a fraction of the cost.


To start I wanted to build a linux host and I've been used to ubuntu desktop in the past and on occasion have installed server for other projects (folding@home, nagios) so I went with the current LTS which at the begining was 12.04.3 Precise Pangolin (12.04.4 update came out as of writing and I rebuilt the server after I had spent a lot of time playing with configs and messing around with stuff so I went back to a clean install before I continued)


My hardware was my old gaming motherboard/case that I upgraded years ago:

Thermaltake Xaser II A5000 A Case (yep cold heavy steel.. might as well be lead it's so damned heavy)
EVGA nForce 680i LT SLI motherboard
Intel Core2 Duo E6850 @ 3.00GHz 4MB cache
2GB DDR2 PC2-4200
(no video, purely headless after install of ssh server)
Intel 20GB SATA SSD (boot/kernel)
RAID Arrays:
 -mdadm
   md0 - (3) 4TB Seagate Barracuda ST4000DM - RAID5
 -megasasctl (PERC5i)
   (devices unnamed as I am doing blockio access)
   rd0 - (8) 320GB Samsung Spinpoint M8 ST320LM001 - RAID5
   rd1 - (3) 2TB Hitachi GST Deskstar 7K2000 - RAID5
Network:
SSH
 (1) nForce MCP55 Onboard Ethernet (eth6)
7x Bonded LACP ports
 (1) Intel 82546EB PCI-X Dual (eth5, eth7)
 (1) Realtek 8169s PCI (Netgear GA311) (eth0)
 (2) Realtek 8111/8168/8411 Dual Port PCIe x1 (eth1, eth2, eth3, eth4)


Base install of Ubuntu 12.04.4 from a verbatim 4GB USB flash drive 
 *using unetbootin
 *I had to rename the files which their names were truncated, and even then sometimes they weren't copying so I included the ISO on the stick and dropped to command line install to complete
 *If running expert install, you will need to enable the "universe" respository for iscsitarget


tasksel:
 
[*] OpenSSH server

get any updates
```

 sudo apt-get update
 sudo apt-get upgrade

```

Install packages:
```

 sudo apt-get install vim iscsitarget iscsitarget-dkms mdadm ifenslave

```
*my iscsitarget-dkms wouldn't build on 3.11.0-19-generic, was getting a make error about the frame size being too large, I added comments to how I got it working here: [https://bugs.launchpad.net/ubuntu/+source/iscsitarget/+bug/1195607](https://bugs.launchpad.net/ubuntu/+source/iscsitarget/+bug/1195607)

Yep I'm still not a hardcore vi user so tiny is just too much of a strain on my patience, iscsitarget's and mdadm (s/w raid) are probably obvious, ifenslave is the bonding package.

configure mdadm/postfix
 -I have comcast as my ISP so I chose Satelite for postfix during setup

Setup postfix - main.cf
```

 sudo vi /etc/postfix/main.cf

# I had best results with these settings: (*=change, +=add)
# don't use the *_ or +_ preceding the following lines

* smtpd_use_tls=no                        # change from yes, sasl worked for me and only if I disabled tls, yours might need it try it and see what works
+ smtp_sasl_auth_enable = yes                    # The next three sasl auth lines were needed because I couldn't get it working with just tls
+ smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd    #
+ smtp_sasl_security_options = noanonymous            #
+ relayhost = [smtp.comcast.net]:587                # 587 is secure smtp, most isp's are switching to this to allow subscribers to relay once again
+ inet_protocols = ipv4                        # keeps postfix from trying to get out via ipv6, I don't get an ipv6 currently and dont feel like setting up my fw/router to tunnel it down to ipv4

#(ymmv, check with your provider if TLS is necessary)
#esc/:w(rite):q(uit)

```

Create sasl_passwd database
```

 sudo vi /etc/postfix/sasl_passwd

#insert the line below
[smtp.comcast.net]:587 YourUsernameHere:YourPasswordHere    # substitute your ISP username and password of course
#esc/:w(rite):q(uit)

```

Create postfix lookup table
```

 sudo postmap /etc/postfix/sasl_passwd

```

**If you have any trouble with permissions for the sasl_passwd.db
```

 sudo chmod 640 sasl_passwd sasl_passwd.db
 sudo chown root:postfix /etc/postfix /etc/postfix/*

```

Update your aliases
```

 sudo vi /etc/aliases

#insert line below
root:    **YourEmailAddressHere@YourDomain.dom
#esc/:w(rite):q(uit)

```

Update your aliases db
```

 sudo newaliases

```

Setup RAID (This step will vary for everyone depending on your needs and desires)
```

 sudo mdadm --create /dev/md0 --chunk=1024 --level=5 --raid-devices=3 /dev/disk/by-id/scsi-SATA_ST4000DM000-1F2_W300AGRR /dev/disk/by-id/scsi-SATA_ST4000DM000-1F2_Z3005ZQQ /dev/disk/by-id/scsi-SATA_ST4000DM000-1F2_Z30053FT

```
If like me you're annoyed at how the udev proc or modprobe (not sure who to blame because they all point the finger elsewhere for the solution) w/e changes the device names sda-b-c-d-f-z from boot to boot, use the by-id like I did above and then write down your superblock information for each drive that way you know which drive to replace when you get seemingly random device names in your monitor daemon emails. My original frustration came from trying to make a system that booted from a USB stick, I'd have it working and then something along the way would always kill my progress and the USB stick would no longer be at the begining of the boot order either my 2nd PERC, or the 3rd onboard SATA drive for the mdadm sw raid. In the end I broke down and put in a 20GB Intel SSD, even found a unique spot to mount it (see pics)

Enable iscsitarget, you can set your fqn's to whatever you want I choose the uuid's for the raid arrays
```

 sudo vi /etc/default/iscsitarget
    *change: ISCSITARGET_ENABLE=false to true
    #esc/:w(rite):q(uit)
 sudo vi /etc/iet/ietd.conf
    #insert: your iscsitarget info, here was mine:
        Target iqn.2000-01.dom.local.iSCSI-SAN:7e907dd7:4f7e017d:28503ca1:888c3bde
                Lun 0 Path=/dev/md0,Type=blockio
        Target iqn.2000-01.dom.local.iSCSI-SAN:6f7848fa:00184fe6:448722a4:7648cd33
            Lun 0 Path=/dev/md1,Type=blockio
    #esc/:w(rite):q(uit)

```

If you want to limit your iSCSI targets to specific initiators or IP's or adapters
```

 sudo vi /etc/iet/targets.allow
    *change: ALL ALL to whatever your address for your target's interface if doing a dedicated NIC or bond setup
    # in my case it's:
    ALL 172.16.255.1
    # you can set specific IPs or Ranges for specific targets from your ietd.conf file if you wish, in my case I'm using an LACP bond so I'll let the switch and NICs work out the bandwidth
    # esc/:w(rite):q(uit)

```

Restart iscsitarget daemon
```

 sudo /etc/init.d/iscsitarget restart

```

If you are running multiple NICs with ifenslave: Setup your bond
```

 sudo vi /etc/network/interfaces
*NOTE: This config is for LACP which requires a capable Layer 3 switch, for standard L2 Bonding use either bond-mode 2,5,or 6 depending on what works with your switch. If you don't have a layer 2 or 3 switch stick with bond-mode 1 (active-backup)
    +add: (your interfaces may vary in number and device name, use "sudo lshw -class network" if you want to label your NICs but it's not required)

        # Bonded interface LACP
        # ---------------------------------------------------------------------
        #eth5 Intel 82546EB Dual port Server PCI-X Network Interface Card
        auto eth5
        iface eth5 inet manual
        # depending on the mode you are going to run your bond-master and bond-slave settings may vary
        bond-master bond0

        #eth7 Intel 82546EB Dual port Server PCI-X Network Interface Card
        auto eth7
        iface eth7 inet manual
        bond-master bond0

        #eth0 RTL8169 PCI Gigabit Ethernet Controller
        auto eth0
        iface eth0 inet manual
        bond-master bond0

        #eth1 RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
        auto eth1
        iface eth1 inet manual
        bond-master bond0

        #eth2 RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
        auto eth2
        iface eth2 inet manual
        bond-master bond0

        #eth3 RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
        auto eth3
        iface eth3 inet manual
        bond-master bond0

        #eth4 RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
        auto eth4
        iface eth4 inet manual
        bond-master bond0

        # bond0
        auto bond0
        iface bond0 inet static
        address 172.16.255.1
        netmask 255.255.255.0
        # Bonding Mode 4 requires a Layer 3 LACP capable switch
        bond-mode 4
        bond-miimon 100
        # bond-lacp-rate not required if bond-mode!=4
        bond-lacp-rate 1
        bond-slaves eth5 eth7 eth0 eth1 eth2 eth3 eth4

```

For more information on Bonding check out [https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

If you have ufw installed and enabled make sure to create an allow rule for your target portal:
```

sudo ufw allow from 172.16.255.0/24 to 172.16.255.1 port 3260 proto tcp

```
(and whatever other rules you might want like SSH, SAMBA, etc)

In the end I decided to go with iSCSI for my VMFS storage on my 2TB 8 drive raid because some day I want to setup a vSphere testbed, however for my other raid volumes md0 and rd1, I used SAMBA so I could have multiple windows machines have access and not have to limit my bandwidth to the VM guest and VM host networking layers. While I am still limited to a single gigbit pipe per connection/session I can do things from multiple computers and still get 50-65MB/s on each. I was copying 150GB of backup data from my gaming computer, watching a moving in the living room, and exporting a premiere project in HD Blueray format all without breaking a sweat. I'm sure I would enjoy it more if I had a ton of memory, & unRaid, or FreeNAS for the fancy gui interface, but I honestly only needed a simple raid system and am not afraid of the terminal.

I still need to work on getting the LSI software installed so I can get monitoring for my PERC controllers, but the system is up and functional.

Notes: 
-In case iscsitarget-dkms build process breaks with frame errors. I ended up using the debian files off the universe repository directly:
```

wget http://ftp.ubuntu.com/ubuntu/pool/universe/i/iscsitarget/iscsitarget_1.4.20.3+svn490-2ubuntu1_amd64.deb

wget http://ftp.ubuntu.com/ubuntu/pool/universe/i/iscsitarget/iscsitarget-dkms_1.4.20.3+svn490-2ubuntu1_all.deb

sudo dpkg -i iscsitarget_1.4.20.3+svn490-2ubuntu1_amd64.deb

sudo dpkg -i iscsitarget-dkms_1.4.20.3+svn490-2ubuntu1_all.deb

```

---

### Post by david144 on 2014-04-29
In my custom built cabinet

---

### Post by david144 on 2014-05-01
Found a very cool blog on monitoring temperature that came in very handy for me:
Source: [http://poundcomment.wordpress.com/2009/08/28/ubuntu-cpu-temperature-terminal-prompt/](http://poundcomment.wordpress.com/2009/08/28/ubuntu-cpu-temperature-terminal-prompt/)
```
sudo apt-get install lm-sensors
sudo sensors-detect
```
#went with defaults
#Last question I answered yes to:
## Do you want to add these lines automatically to /etc/modules? (yes/NO)yes
```
sudo modprobe coretemp
sensors | grep temp
```
output:> coretemp-isa-0000temp1: -65.0Â°C (high = +0.0Â°C, hyst = +127.0Â°C) sensor = diode
temp2: +31.5Â°C (high = +127.0Â°C, hyst = +0.0Â°C) ALARM sensor = diode
temp3: +40.0Â°C (high = +127.0Â°C, hyst = +0.0Â°C) sensor = thermistor
```
sensors | grep temp3
```
output:> temp3: +40.0Â°C (high = +127.0Â°C, hyst = +0.0Â°C) sensor = thermistor
```
sensors | grep "temp3" | sed 's/.*:\s*+\(.*\) .*(.*/\1/' | sed s/Â°C//
```
output:> 40.0
create script: cpu_temp.sh
```
#! /bin/bash
# Records the CPU temp and writes it to a temporary file.
while [ 1 ]; do
     sensors | grep "temp3" | sed 's/.*:\s*+\(.*\) .*(.*/\1/' | sed s/Â°C// >& \
     /tmp/.cpu_temp;
sleep .5;
done
#you can adjust your cpu sleep time as you deem necessary
```


vi ~/.bashrc:
```

#find:    
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
#replace:
PS1='[`cat /tmp/.cpu_temp`deg C] ${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '


#find:
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
#replace:
PS1='[`cat /tmp/.cpu_temp`deg C] ${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '


#find:
PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
#replace:
PS1="\[\e]0;[`cat /tmp/.cpu_temp`deg C] ${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
```

move cpu_temp.sh to /etc/cpu_temp/ and make executable
```
sudo mkdir /etc/cpu_temp
sudo mv cpu_temp.sh /etc/cpu_temp
sudo chmod 755 /etc/cpu_temp/cpu_temp.sh
```

create /etc/init.d/cpu_temp:
```

sudo touch /etc/init.d/cpu_temp
sudo chmod 755 /etc/init.d/cpu_temp
sudo vi /etc/init.d/cpu_temp

[code]#!/bin/sh
# Simple script to enable/disable CPU temperature monitor.
PIDFILE="/var/run/cpu_temp.pid"
NAME="cpu_temp"
DAEMON="/etc/cpu_temp/$NAME.sh"


# Return 0, process already started.
# Return 1, start cpu_temp
do_start()
{
        if [ -f $PIDFILE ]; then
                return 0
        fi
        $DAEMON &
        echo "$!" > $PIDFILE
        return 1
}


# Return 0, process not started.
# Return 1, kill process
do_stop()
{
        if [ ! -f $PIDFILE ]; then
                return 0
        fi
        kill -9 `cat $PIDFILE`
        rm $PIDFILE
        return 1
}


case "$1" in
  start)
        do_start
        case "$?" in
                0) echo "$NAME already started." ;;
                1) echo "Started $NAME." ;;
        esac
        ;;
  stop)
        do_stop
        case "$?" in
                0) echo "$NAME has not started." ;;
                1) echo "Killed $NAME." ;;
        esac
        ;;


  status)
        if [ ! -r "$PIDFILE" ]; then
                echo "$NAME is not running."
                exit 3
        fi
        if read pid < "$PIDFILE" && ps -p "$pid" > /dev/null 2>&1; then
                echo "$NAME is running."
                exit 0
        else
                echo "$NAME is not running but $PIDFILE exists."
                exit 1
        fi
        ;;
  *)
        N=/etc/init.d/$NAME
        echo "Usage: $N {start|stop|status}" >&2
        exit 1
        ;;
esac


exit 0
```[/code]

update startup sequence
```
sudo update-rc.d cpu_temp defaults
```

start it up
```
sudo /etc/init.d/cpu_temp start
```


I also created a script and setup as a service similar to above to send me email notifications when certain thresholds were met

to make this work below some additional pkgs were needed:
```
sudo apt-get install bc
sudo apt-get mailutils
```

I called this script cpu_temp_notif, and installed with update-rc.d in the same manner as above
```
#!/bin/bash
nl=$(cat "/tmp/.cpu_temp" | wc -l)
declare -a celcius
declare -a NUM
declare -a fahrenheit
#celcius="$(cat /tmp/.cpu_temp)"
celcius=1
while [ $celcius > 0 ]; do
   celcius="$(cat /tmp/.cpu_temp)"
   NUM=$(echo "scale=1;$celcius * 9" | bc)
   fahrenheit=$(echo "scale=1;$NUM / 5" | bc)
   NUM=$fahrenheit
   fahrenheit=$(echo "scale=1;$NUM + 32" | bc)


   if [ $(echo "$celcius > 44.4" | bc) -eq 1 ]; then
   touch /tmp/dangerzone.txt;
   echo "iSCSI-SAN current temperature: ${celcius}C / ${fahrenheit}F" > /tmp/dangerzone.txt;
   cat /etc/chk-cpu-tmp/chart.txt >> /tmp/dangerzone.txt
   mail -t *youremail@domain.dom* -s "iSCSI-SAN Temp Warning" < /tmp/dangerzone.txt
   rm /tmp/dangerzone.txt
   fi


   if [ $(echo "$celcius > 48.3" | bc) -eq 1 ]; then
   touch /tmp/inverted.txt;
   echo "iSCSI-SAN current temperature: ${celcius}C / ${fahrenheit}F" > /tmp/inverted.txt;
   cat /etc/chk-cpu-tmp/chart.txt >> /tmp/inverted.txt
   mail -t *youremail@domain.dom* -s "iSCSI-SAN Temp entering Danger Zone" < /tmp/inverted.txt
   rm /tmp/inverted.txt
   fi


   if [ $(echo "$celcius > 53.3" | bc) -eq 1 ]; then
   touch /tmp/TOOHOT.txt;
   echo "iSCSI-SAN current temperature: ${celcius}C / ${fahrenheit}F" > /tmp/TOOHOT.txt;
   cat /etc/chk-cpu-tmp/chart.txt >> /tmp/TOOHOT.txt
   mail -t *youremail@domain.dom* -s "iSCSI-SAN Temp nearing critical levels" < /tmp/TOOHOT.txt
   rm /tmp/TOOHOT.txt
   fi


   if [ $(echo "$celcius > 56.1" | bc) -eq 1 ]; then
   touch /tmp/critical.txt;
   echo "iSCSI-SAN current temperature: ${celcius}C / ${fahrenheit}F" > /tmp/critical.txt;
   cat /etc/chk-cpu-tmp/chart.txt >> /tmp/critical.txt
   mail -t *youremail@domain.dom* -s "iSCSI-SAN CRITICAL TEMP - SHUTDOWN INITIATED" < /tmp/critical.txt
   rm /tmp/critical.txt
   sleep 20; halt -p -f
   fi


   sleep 900;
done
```
*note chk-cpu-tmp was what I named cpu_temp described at the begining (you can name these scripts and services whatever you like it's not critical, just make sure you match up all your names correctly in your init.d file before runnning update-rc.d)

/etc/chk-cpu-tmp/chart.txt:
> Celcius    ->    Fahrenheit

*** I feel the need... ***
*** the need for speed ***
 32.2   90  |  38.3    101
 32.8   91  |  38.9    102
 33.3   92  |  39.4    103
 33.9   93  |  40.0    104
 34.4   94  |  40.6    105
 35.0   95  |  41.1    106
 35.6   96  |  41.7    107
 36.1   97  |  42.2    108
 36.7   98  |  42.8    109
 37.2   99  |  43.3    110
 37.8  100  |  43.9    111


    **YOU'RE IN THE**
     **DANGER ZONE**
      44.4     112
      45.0     113
      45.6     114
      46.1     115
      46.7     116
      47.2     117
      47.8     118


 ****4G'S..INVERTED****
      48.3     119
      48.9     120
      49.4     121
      50.0     122
      50.6     123
      51.1     124
      51.7     125
      52.2     126
      52.8     127


OK NOW WE'RE GETTING TOO HOT
TIME TO SHUTDOWN CRITICAL SYS


      53.3     128
      53.9     129
      54.4     130
      55.0     131
      55.6     132


System will auto halt at 56.1 / 132

No I'm not a top gun nut but, I decided to be funny ;)

---

### Post by tgalati4 on 2014-05-01
Nice tutorial and an impressive build.  

Why would you build such a system?
[I]
Because you can.[/I]

---

