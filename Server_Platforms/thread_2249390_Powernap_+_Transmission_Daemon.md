---
title: "Powernap + Transmission Daemon"
date: 2014-10-21
forum: Server Platforms
---

### Post by splintr on 2014-10-21
im a long time forum reader, and most of the time i will find my answers. But this time i need my own thread :)

I'm running Ubuntu 14.04 LTS on my homeserver.
The server serves:
SMB Share
Netatalk
Virtual Machines
Transmission-Daemon
Apache (MySQL etc.)
SSH for management.

Recently i was thinking about cutting down costs, after a lot of research i made the following solution.
Enabled Wake-On-Lan, and flashed my router with OpenWRT, made a script (listens for requests to the server, if there is a request send a magic packet) - This part is working perfect.

Then i thought it would be cool if my server isn't doing anything go to suspend s3, researched and found 'Powernap'... Installed it configured it, so far so good.
But i can't find a good solution for my Transmission (Bittorent). If it's idle and not downloading anything (queue empty) powernap must go to standby.

1) I tried to set the transmission port 60000-65000 and added it to powernap config, but that doesn't work. And since most of the trackers all have another ports i can't use that one to. 
2) Checking for the transmission-daemon process isn't the way to go, because it it always running. (when i go to the url of the transmission server, i can manage, add, remove etc torrents - this is my only way to manage torrents and suits my needs)

I don't think i'm the only one that is using powernap in combination with transmission-daemon, but can't find a answer/tip or solution.
Hope somebody can help me.

---

### Post by papibe on 2014-10-21
Hi splintr. Welcome to the forums ):P ...now for real ;)

I use transmission-daemon extensively. There are several cool things you could do by using 'transmission-remote' and scripts.

For instance, you can create a crontab task to check every certain period of time, say 15mins, and check if all torrents are completed. If they all are, you can go to sleep.

Another idea would be to use transmission-daemon completion scripts. You can set a script so that every time a torrent is completed, transmission will launch the script.

Hope it helps. Let us know if you need help creating the scripts.
Regards.

---

### Post by splintr on 2014-10-22
Hi Papibe,

Thanks for your reply.
I'm not familiar with 'Transmission-remote' i will check into it.
The system is headless and i use the web interface ([http://(ip):9091)](http://(ip):9091)) to add/mange torrents from client computers

But the problem is that 'Powernap' is the lead process, it runs very high in the top processes. (Example, if powernap is running and you are connected to a samba share on the server, and if the samba process or port isn't in the powernap configuration, the system will still go into 'S3 Suspend mode')

I don't know how to create a solution that hooks on the powernap solution or tells powernap to sleep checking period until script is complete.
Ideally i would like a solution where transmission-daemon is always running, but when i'm downloading something powernap don't go to 's3 suspend' and when the download is complete or nothing is in the queue the system may go to 's3 suspend' mode.

I only have very basic scripting knowledge, but with a lot of reading and trial/error most of the time i can write something.
English isn't my native language so i hope the problem is clear :)

Regards

---

### Post by papibe on 2014-10-22
Is transmission-daemon your only concern, or there are other processes you want to watch with powernap?

---

### Post by splintr on 2014-10-22
Hi,

My powernap is currently configured with
AFP (fileshare mac)
SMB (fileshare windows)
SSH (management)

The above is configured in the powernap config based on ports.
When a client is connected to 1 or more of the services above, powernap pauses and the system doesn't go to standby. When i disconnect my client that is connected to one or more service... Powernap continues or something and the server goes to suspend s3 mode.

When transmission-daemon is fixed with the above services, i can use my server again as a 24/7 machine.

Thanks

---

### Post by papibe on 2014-10-22
Thanks.

So if I understood correctly... If we manage to shutdown the service 'transmission-daemon' when all torrents are completed, then you would be able to added to the powernap mix, and you would accomplish what you want?

Regards.

---

### Post by splintr on 2014-10-22
Hi,

No almost.
I'm looking for something to hook on to the powernap process. So i can hook my own set of rules to the powernap-daemon (in this case transmission-daemon). 
If im correct, it is also possible to hook a running process to powernap-daemon.
But with the scenario above, when the transfers in transmission-daemon are complete, the daemon shutdowns and the server goes to suspend s3. But when i connect again the transmission-daemon is not running anymore.

I copied a part of the default powernap config for you, currently i use TCPMonitor for the services in a post above
```

############################################################################
####                          MONITORS                                  ####
############################################################################


# The [WoLMonitor] section lists all ports on which the WoL Monitor will be
# listening for WoL Packets for any of the network interfaces.
# Once a WoL Packet is received, the WoLMonitor will compare the data received
# with all the network interfaces (eth's) to determine wether it is destined
# for any of the network interfaces.
# The default is to monitor ports 7 and 9 for WoL data packets. It can also be
# set to any other port on which the machine is receiving WoL packets
# Example:
#  wol1052 = 1052
[WoLMonitor]
wol7 = 7
wol9 = 9


# The [ConsoleMonitor] section enables or disables  monitoring of activity
# in the Console (tty), also tracking activity from any locally connected
# mouse and keyboard (PS2 Only).
# The default is enabled, set to 'y'. It can be disabled by setting it to 'n'.
# Examples:
#  console = y
#  console = n
[ConsoleMonitor]
ptmx = y


# The [ProcessMonitor] section lists all the processes to Monitor by using
# regular expressions.
# Each item listed will be compared against the output of "ps -eo args".
# The default is to monitor /sbin/init, which should always be running.
# Examples:
#  mplayer = "mplayer "
#  sshd = "sshd: .*\[priv\]$"
#  kvm = "kvm "
[ProcessMonitor]
#init = "^/sbin/init"


# The [LoadMonitor] section defines the load threshold.  When the system load
# according to /proc/loadavg is above this value, then system will be deemed
# 'active' and will not powernap.  If the system is already powernapping, then
# the system will awake out of the powernap mode if the load raises above the
# threshold.
# If the threshold is set to "n" (which is default), threshold is automatically
# calculated to be the number of online processors, as determined by:
#   getconf _NPROCESSORS_ONLN
# Example:
#   threshold = 1.5
#   threshold = 9999
#   threshold = 0
#   threshold = n
[LoadMonitor]
threshold = n


# The [TCPMonitor] section lists all the TCP ports on which to watch for
# established connections using netstat(8). It supports both, single TCP
# as well as port ranges.
# There is no default TCP Monitor.
# Examples:
#  ssh = 22
#  http = 80
#  https = 443
#  other = 64500-65000
[TCPMonitor]
#ssh = 22


# The [UDPMonitor] section lists all the UDP ports on which to listen
# for data.
# Each item listed will BIND a UDP port and listen to any data. Keep
# in mind that this port will be bined and no other application will
# be able to use this port.
# There is no default UDP Monitor.
# Examples:
#  udp-1 = 1025
#  udp-2 = 2048
[UDPMonitor]
#udp-1025 = 1025


# The [IOMonitor] section lists all the processes to Monitor for IO
# activity. A regular expressions is used to find the processes PIDs, which
# are later used to monitor IO.
# There is no default IO Monitor.
# Examples:
#  kvm-io = "kvm"
#  mysqld-io = "mysql"
[IOMonitor]
#kvm-io = "kvm"
#mysqld-io = "mysql"

```

---

### Post by papibe on 2014-10-23
I've been thinking how to do this, and I believe there's no simple way to add that service to Powernap.

At this moment I have a couple of ideas:

Continuing with the idea of stopping transmission when completes all downloads. I think we could use the pm-utils scripts to take an action when the computer wakes up, and relaunch transmission-daemon.

Alternatively, we can create a simple bash scripts that watches transmission, and goes down when all is completed. Then you could monitor that process instead of transmission itself.

Let me know what you think, and if you'd like test one of those ideas.
Regards.

---

### Post by splintr on 2014-10-24
Yo Papibe,

I did some testing today, i thought if i create a /etc/pm/sleep.d script where i write a case statement with 'service transmission-deamon stop' in the suspend section and 'service transmission-daemon start' in the resume section. But the suspend section isn't executed but the resume section will be executed.
So i think if i put the transmission-daemon process on the powernap list with some kind of external script that checks if there is a download in the queue, if not stop the service.

[downloading torrent]
If i'm correct powernap checks then for the service, sees the service is the running list, so it doesn't go to suspend mode.
The download completes, some kind of script (don't know this part) checks the queue sees nothing in the list, so it closes transmission-daemon
powernap checks again for the service in the running list, doesn't see the transmission-daemon so it goes to suspend mode.

i send a wol magic packet, the resume script from sleep.d starts transmission-daemon and everything starts over.

- Only problem i see in this is, i'm managing my server with ssh (or I'm connect to a afp or SMB share) (system doesn't go to suspend because ssh is on the powernap list). The 'script' checks for download queue, but there is none so it closes the transmission-daemon. but i'm still in the same session and after I'm done with managing i want to download a torrent, but now the service is down, so i can't connect to it.
(ok ssh isn't the best example is this one because i can manually type service transmission-daemon start, but you get the problem :) )

---

### Post by splintr on 2014-10-24
Yo Papibe Bro,

i've found a solution.
I went to the script folder of powernap and checked where the source files where. They were in the python directory under powernap, i checked the directory monitors to see what the monitors are doing. I found a monitor named 'IOMonitor' i opened the script in nano and saw that it was checking the /proc directory and all the directories are scanned for the status file. i went to the running processes list and saw that transmission-daemon is called 'transmission-da' and named 'transmission-da' in the status file. So i added transmission-da to the powernap config (above) under the title IOMonitor. Did some testing and when a torrent is downloading powernap doesn't send a suspend command, when the torrent is done powernap checks all the other ports in the powernap config and if nothing is used, powernap sends a suspend signal.

i don't know exactly how the IO of processes works, but for now it all works :D

Thanks for your time and solutions Papibe. 
Hope you can help me again in the future if I'm stuck again, thanks bro !

Regards

---

