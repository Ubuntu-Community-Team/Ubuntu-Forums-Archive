---
title: "How to Create a Wireless Network/Virtual Router (ath5k or ath9k limitations)"
date: 2015-10-23
forum: Tutorials
---

### Post by branau on 2015-10-23
[CENTER]DISCLAIMER
*****************************************************************************************************************************************************************************************************************************
I am not the original author of this post nor the scripts contained. I merely found some useful information that helped me, and am sharing it with the community. Use at your own risk.                
*****************************************************************************************************************************************************************************************************************************[/CENTER]
                                                
TESTED ON: Ubuntu 15.04, 15.10

I got this information from [another post in the XDA Developer forums]("http://forum.xda-developers.com/showthread.php?t=2009381") from another guy who says that he wasn't the original poster, and just translated the original post into English. So, while I'm nowhere near the original poster, I can say that I tried several solutions that didn't work for me, until I came across this one, and this one did work. The original script has been modified a bit to improve it overall with help from TheFu. You can see the original script from the link at the beginning of this paragraph or at the bottom of this post.

 My apartment doesn't have wireless internet, which made my tablet all but useless and caused me to run through my cellular data in about a week. I do, however, have an ethernet connection available and a laptop running Ubuntu 15.10 (although I tried this on 15.04 and it worked as well. To my knowledge, this should work on Ubuntu 12.04+). While Ubuntu has a built-in hot spot feature, this didn't work for me because the network created by that feature is an ad hoc network, and Android devices cannot connect to ad hoc networks without performing some workarounds. I was unable to find any for my particular devices so I needed a way to create a standard network that would allow Android devices to connect, and multiple devices at the same time as well. This tutorial covered all of my needs. I initially tried this on Ubuntu 15.04 and then I upgraded to Ubuntu 15.10 and both versions handled it with no problems for me.

1. First of all you should make sure, that your wifi adapter supports infrastructure hotspots.

```
sudo lshw -C network

```

Find the network section and make sure that your driver is either ath5k or ath9k, this solution will only work for those drivers.




2. If that checks out, then you need to grab two different pieces of software to make this work:


```
sudo apt-get install hostapd dnsmasq

```

3. stop those services if started already, and prevent them from starting on system start up.


```
sudo service hostapd stop
sudo service dnsmasq stop
sudo update-rc.d hostapd disable
sudo update-rc.d dnsmasq disable

```

4. Now you need to set up the config files. We'll do dnsmasq first:


```
sudoedit /etc/dnsmasq.conf

```

Add these lines to the config file :
```
# Bind to only one interface
bind-interfaces

# Choose interface for binding
interface=wlan0

# Specify range of IP addresses for DHCP leasses
dhcp-range=192.168.150.2,192.168.150.10

```

5. Next up: hostapd config


```
sudoedit /etc/hostapd.conf

```

and add these lines


```
# Define interface
interface=wlan0

# Select driver
driver=nl80211

# Set access point name
ssid=myhotspot

# Set access point harware mode to 802.11g
hw_mode=g

# Set WIFI channel (can be easily changed)
channel=6

# Enable WPA2 only (1 for WPA, 2 for WPA2, 3 for WPA + WPA2)
wpa=2

#Set your password
wpa_passphrase=mypassword

```

You can change the ssid and password to anything you want here. The current config will create a network named myhotspot with a password of mypassword.


6. Now create a shell file, name it what you want, and place it somewhere safe. I placed mine in the /usr/local/bin/ directory and called it start-wifi.sh. Then fill it with the following code: 


```

#!/bin/bash

# First, set the variables for the path names to all of the programs used.
# You can verify that your paths are the same with the which command
KILL=/bin/kill
PID=`/usr/bin/pgrep hostapd`
RFKILL=/usr/sbin/rfkill
IFCONFIG=/sbin/ifconfig
SERVICE=/usr/sbin/service
SYSCTL=/sbin/sysctl
IPTABLES=/sbin/iptables
HOSTAPD=/usr/sbin/hostapd
DNSMASQ=/usr/sbin/dnsmasq

# Start
# End any existing processes before starting a new one
if [ -n "${PID}" ]; then
    $KILL $PID
fi

# Prevent RFKill from causing problems
$RFKILL unblock all

# Configure IP address for WLAN
$IFCONFIG wlan0 192.168.150.1

# Start DHCP/DNS server
$SERVICE dnsmasq restart

# Enable routing
$SYSCTL net.ipv4.ip_forward=1 # Enable NAT
$IPTABLES -t nat -A POSTROUTING -o eth0 -j MASQUERADE

# Run access point daemon
$HOSTAPD /etc/hostapd.conf

```

You might need to change eth0 to match your wired connection.


7. Last step. Now you can start your hotspot by starting your script. First, allow it to be executed: 

```

sudo chmod +x /usr/local/bin/start-wifi.sh

```

So then you could just run it like this:
```

sudo /usr/local/bin/start-wifi.sh

```

NOTE: If you have done as I did and saved the file in the /usr/local/bin/ directory (recommended), it would be a good idea to add it to your backups.

[CENTER]*****************************************************************************************************************************************************************************************************************************[/CENTER]

And that's where the original tutorial ended. Here is where my extras come in.

I never turn off my computer completely (I know, not the greatest idea), but I usually suspend it when I'm not using it. The problem I came across with this script was that it wouldn't reactivate the network after waking up the computer. I'd have to manually kill the script, and then run it again. Not a big deal, but I'm kind of lazy, and I like having things work automatically. Enter crontabs.

First, I didn't want to worry about forgetting to put my computer to sleep at night and I wanted it to automatically power up in the morning (I work from home so it's nice to just wake up and go). To get this working, I added a cron task like so:

```

sudo crontab -e

```

You'll then be asked to select your preferred editor, if it's your first time using the crontabs. Again, I go with Vim, but you can go with the one you prefer.

```

# m h dom mon dow command

0 0 * * * /usr/sbin/rtcwake -m mem -s 27000

```

This command puts your computer to sleep (suspended to memory) at midnight everyday, for 7 and a half hours. The first 0 in the code is the minute (0-59), the second 0 is the hour (0-23), and the following asterisks represent the day of the month (1-31), month of the year (1-12), and day of the week (0-6), respectively. The 27000 after the -s is the number of seconds (7.5 x 60 x 60) in 7 and a half hours. This sets your computer to go to sleep everyday at midnight and wake up at 7:30 am. You can change these to whatever values you like.

Now to start the script in the morning:

```


45 7 * * * /usr/local/bin/start-wifi.sh

```

This runs my start-wifi script at 7:45 am, every morning, which means my devices are all connected and ready to go by the time I wake up and get moving. My final crontab script looks like this: 

```

# m h dom mon dow command

0 0 * * * /usr/sbin/rtcwake -m mem -s 27000

45 7 * * * /usr/local/bin/start-wifi.sh

```

Make sure you save your file before you quit, and then you should see a message about the crontab being installed. You should now be able to share your ethernet connection wirelessly to all of your devices and have the service run automatically.

[CENTER]***************************************************************************************************
Original Script
The script below is the original script, and is not recommended for use. It is just as a reference to be able to see the improvements made with help from TheFu.
***************************************************************************************************[/CENTER]

dnsmasq.conf file:
```

# Bind to only one interface
bind-interfaces
# Choose interface for binding
interface=wlan0
# Specify range of IP addresses for DHCP leasses
dhcp-range=192.168.150.2,192.168.150.10

```

hostapd.conf file:
```

# Define interface
interface=wlan0
# Select driver
driver=nl80211
# Set access point name
ssid=myhotspot
# Set access point harware mode to 802.11g
hw_mode=g
# Set WIFI channel (can be easily changed)
channel=6
# Enable WPA2 only (1 for WPA, 2 for WPA2, 3 for WPA + WPA2)
wpa=2
wpa_passphrase=mypassword

```

.sh script:
```

#!/bin/bash
# Start
# Configure IP address for WLAN
sudo ifconfig wlan0 192.168.150.1
# Start DHCP/DNS server
sudo service dnsmasq restart
# Enable routing
sudo sysctl net.ipv4.ip_forward=1
# Enable NAT
sudo iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
# Run access point daemon
sudo hostapd /etc/hostapd.conf
# Stop
# Disable NAT
sudo iptables -D POSTROUTING -t nat -o ppp0 -j MASQUERADE
# Disable routing
sudo sysctl net.ipv4.ip_forward=0
# Disable DHCP/DNS server
sudo service dnsmasq stop
sudo service hostapd stop

```

crontab:

```




0 0 * * * sudo rtcwake -m mem -s 27000

45 7 * * * sudo sh start-wifi.sh

```

---

### Post by TheFu on 2015-10-23
Started reading thinking a few minor comments would be my input. I understand you just want to make it easier for the next person to find a solution that works.

Lots of online guides aren't created by experts and don't take the shortest way to a solution. That is certainly the situation here.  Plus there are commands which could be dangerous on many systems and the improper use of both sudo and scheduled cron jobs to be concerned about.
ath5k or ath9k limitations are worth adding to the title. Please do so.

I don't know where to begin. There are lots of issues in those steps, the script, and the crontabs. If you are willing, I am willing to help streamline and fix as much as possible a with what I know from 23+ yrs experience.

To start:
**sudo lshw  -C  network**

*sudo gedit* is dangerous.   Use **sudoedit** instead.  This is a mistake made by inexperienced users.

There is entirely too much use of sudo in the rest of the post. 

That crontab is just dangerous and full of security issues. NEVER trust the PATH. If you need something to run in cron with elevated privileges, use one of the root crontabs  instead. I didn't look too closely-there may be a better way to do that.

Anyway ...  let me know how/if you'd like to move forward.

---

### Post by branau on 2015-10-23
TheFu, you have my respect, feel free to correct me anytime, anywhere if you see I've made a mistake. As my signature says, I've only been around on Linux since April, so I'm still relatively new myself. 

I put in a request to have the title changed, as I myself cannot do so. 

As for the streamlining/corrections for this post, please share your knowledge.

---

### Post by TheFu on 2015-10-23
Start by editing the current suggestions into the first post - #1 -  above.
Additionally, remove all "sudo" from the start-wifi.sh script.

Also, implement scripting "best practices"  
[http://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting](http://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting)

Ask if you get stuck.

---

### Post by branau on 2015-10-25
Hey TheFu, I've edited my original post to include the changes you've mentioned so far. All mentions of sudo within the script are now gone, and the cron jobs are now placed in the root profile's cron jobs. I've also included the paths to each of the programs being used in the crontab and reworked the script a little. What else could be improved?

---

### Post by TheFu on 2015-10-26
Nice progress.

We'll come back to  the  script later. Parts of it can be made less dangerous and for some parts like the killall commands, there should be better options like reading the PID-file and killing the  specific PID  instead.  Killall  is a shotgun approach which could have undesirable side effects.

Most of the remaining issues are due to not specifying the exact, full-path, to the script and programs to be run. This is highly dangerous, especially when running things as root. Someone could replace the script earlier in the PATH and completely pwn your box. There are 500 different ways to solve this. I would:
* put the script into /usr/local/bin/start-wifi.sh
* ```
chmod +x /usr/local/bin/start-wifi.sh
```
* make the **sudo crontab -e** - no need to add other option/root.
```
45 7 * * * /usr/local/bin/start-wifi.sh
```

I don't know anything about hostapd, so cannot say anything about the configuration or how it works, if it supports a PID file, etc.  syslog is going away - may already be gone in 15.10, so how will that impact this?  If you didn't clearly say which Ubuntu release this was used on, please add that with a caveat that later releases with more systemd integration will need different steps for logging and update-rc.d stuff.

To start the script cleanup, begin by using explicit, full, paths to all the  programs. It is often easier to use variables for this.  An example: [http://blog.jdpfu.com/files/kernel-cleanup.sh](http://blog.jdpfu.com/files/kernel-cleanup.sh)  note all the commands at the top?

---

### Post by branau on 2015-11-02
Hey TheFu, again, thanks a million for your help. I've been a bit busy this past week but I finally got around to fixing up the script. Here are the latest changes:

The script now has full paths to all of the commands invoked, referenced by variables, and I figured out a way to get the PID of the hostapd process and only kill it if it exists. That should be quite a bit safer than the killall method correct? Also, the script has been moved to the /usr/local/bin/ directory as you suggested. I modified the tutorial to reflect that.

I wasn't aware that syslog was disappearing, so I'll have to find a new way to get the log files for this.

---

### Post by TheFu on 2015-11-02
Very nice. I could leave it as-is  now,  but  ....  something can always be improved.

* Please mention the specific Ubuntu release AT-THE-TOP that you've tested this on. People need to know that more than anything. Did you test this  on Ubuntu server? Mate? Gnome3? Kubuntu? Lubuntu?
* For the script -  add some whitespace between different code sections for readability.
* For the crontab, I always  add a  comment to the top:
```
# m h  dom mon dow   command
```
See how things line up nice? A blank crontab is a scary thing, but with that 1 line, the fields are much clearer.
* using any GUI (gnome-schedule) with sudo can have undesired effects. Most gnome tools will write settings to $HOME.... which is NOT modified with a plain sudo command. Having root-owned settings you joeuser's HOME is generally a bad thing - especially if directories were created by root in the process.
* Now that something  has been  added under /usr/local/, that area needs to be added to  any backups.

Anyway-nice job. Looks good. Hope this is helpful to someone.  Would be nice to add the original script to the bottom so the transformation can also be learned from.

---

### Post by branau on 2015-11-02
Updates:

* I added the versions of Ubuntu that I've personally tested this with at the top
* I added the whitespace between the different commands
* I added the crontab comment
* I removed the reference to gnome-schedule
* I added a note about including that section in the backups (I would've added a section on how I do it but I don't have any external drives and I don't trust any cloud storage services with a complete backup of all of my data, so until I get myself an external drive, I'll leave that part out).

Thanks a ton for your help TheFu! I was just hoping to possibly help someone else learn something new and I ended up learning quite a bit!

---

