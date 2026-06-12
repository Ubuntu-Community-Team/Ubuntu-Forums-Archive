---
title: "HP DL360 G6 Issues"
date: 2009-07-06
forum: Server Platforms
---

### Post by diss3ntive on 2009-07-06
Hello,

I have been running multiple servers over the past month in the exact same configuration.

- HPDL360 G6
- Nahalem 2.66 QC 
- RAID:  HP Smart Array - 410i (no BBWC)
         Configuration: RAID1 (2x72G)
- DDR3-1333
         12G Memory (3x4G)

- Ubuntu Server 9.04

------------------------

OK!  So, I have been running into issues with random lockups.  All processes that require dynamic allocation lock up.  Any process that has a static allocation in memory still seems to work fine.  I can run things like 'df -h', 'ps -ef', etc but if I issue commands like rm, ssh, etc it hangs.

So - It hangs, whats next?  shutdown -r now and get the server back up.  Well. . . 'shutdown -r now' hangs.  Nothing happens?  Ok. . . . 'ps -ef'  I see KxxProcess scripts.....there hanging too?  What went wrong?

Ok.....lets remote power these suckers and get them back online.  OK they are back up!

vi /var/log/messages
vi /var/log/syslog
vi /var/log/etcetcetc

*4 Hours Later*

I don't see ANYTHING to why it locked up!  This is happening on a daily basis, but nothing indicates what is wrong.  It always starts the same - Processes start hanging, system runs dirt slow, and I have to reboot to bring back up.

During the 'bad state':

Network:
   The device is pingable - 0% packet loss
Memory/Hard-Drive:
    'free -m' - Usually 8G free
    'df -h' - 90% Free

(from admin box)

admin1:  ssh badbox1 uptime
                 *hang*

(from remote interface)
login:  user1
            *hang*

(Wait!  I remember I keep an open terminal for this issue...ALT+F2)

$user1: ls 
               *hang*

$user1: ps -ef 
               <STDOUT>

$user1: top
               1: init

$user1: kill `pidof processesIneedRunning`
               *hang*

$user1: shutdown -r now
               "System is rebooting!"
               *hang*

$user1:  ps -ef 
                Kill Scripts......
         
$user1:  kill `pidof of killscripts`
                *Do this 10 times*

                 Server Reboots!  Sometimes. . . .. .. ....And never reboots after any specific kill script, or any particular device shutdown.

So?  Maybe its a software issue.  Ubuntu seems to be bulky in some areas.....Ok - Let's disable every known service that does NOT need to run.  OK!  It locked up again!  This has to be hardware!  Really?  

So what now?  It seems to be hardware related at this point, and specifically related to some sort of RAID or hard-drive issue, but I can't be certain without some sort of *real* diagnostics, not a guess.  Any real application I can run determine if this is memory/hard-drive/raid/network/motherboard....whatever so I quit guessing?

HP is no help.  There support is as good as a monkey with a screwdriver - Canonical certified this hardware, but maybe they certified it after a successful installation.  The hardware with this server platform is too new, and I really feel like the guinea pig right now running into these issues.....But I would love to help if I just knew what would be a genuine test :)

---

### Post by diss3ntive on 2009-07-06
> **diss3ntive said:**
> Hello,

I have been running multiple servers over the past month in the exact same configuration.

- HPDL360 G6
- Nahalem 2.66 QC 
- RAID:  HP Smart Array - 410i (no BBWC)
         Configuration: RAID1 (2x72G)
- DDR3-1333
         12G Memory (3x4G)

- Ubuntu Server 9.04

------------------------

OK!  So, I have been running into issues with random lockups.  All processes that require dynamic allocation lock up.  Any process that has a static allocation in memory still seems to work fine.  I can run things like 'df -h', 'ps -ef', etc but if I issue commands like rm, ssh, etc it hangs.

So - It hangs, whats next?  shutdown -r now and get the server back up.  Well. . . 'shutdown -r now' hangs.  Nothing happens?  Ok. . . . 'ps -ef'  I see KxxProcess scripts.....there hanging too?  What went wrong?

Ok.....lets remote power these suckers and get them back online.  OK they are back up!

vi /var/log/messages
vi /var/log/syslog
vi /var/log/etcetcetc

*4 Hours Later*

I don't see ANYTHING to why it locked up!  This is happening on a daily basis, but nothing indicates what is wrong.  It always starts the same - Processes start hanging, system runs dirt slow, and I have to reboot to bring back up.

During the 'bad state':

Network:
   The device is pingable - 0% packet loss
Memory/Hard-Drive:
    'free -m' - Usually 8G free
    'df -h' - 90% Free

(from admin box)

admin1:  ssh badbox1 uptime
                 *hang*

(from remote interface)
login:  user1
            *hang*

(Wait!  I remember I keep an open terminal for this issue...ALT+F2)

$user1: ls 
               *hang*

$user1: ps -ef 
               <STDOUT>

$user1: top
               1: init

$user1: kill `pidof processesIneedRunning`
               *hang*

$user1: shutdown -r now
               "System is rebooting!"
               *hang*

$user1:  ps -ef 
                Kill Scripts......
         
$user1:  kill `pidof of killscripts`
                *Do this 10 times*

                 Server Reboots!  Sometimes. . . .. .. ....And never reboots after any specific kill script, or any particular device shutdown.

So?  Maybe its a software issue.  Ubuntu seems to be bulky in some areas.....Ok - Let's disable every known service that does NOT need to run.  OK!  It locked up again!  This has to be hardware!  Really?  

So what now?  It seems to be hardware related at this point, and specifically related to some sort of RAID or hard-drive issue, but I can't be certain without some sort of *real* diagnostics, not a guess.  Any real application I can run determine if this is memory/hard-drive/raid/network/motherboard....whatever so I quit guessing?

HP is no help.  There support is as good as a monkey with a screwdriver - Canonical certified this hardware, but maybe they certified it after a successful installation.  The hardware with this server platform is too new, and I really feel like the guinea pig right now running into these issues.....But I would love to help if I just knew what would be a genuine test :)

Updated Title

---

### Post by vladoportos on 2010-11-22
Hello, 

I find your post here, I just bought DL 360 G6 and going to install
ubuntu on it so hopefully we can see whats going on.. 

HP support isn't that bad ( I'm working for them ) you just need to know where to call :D
and usually what is not running HPUX doesn't have much support on HP servers... 

I'm going to install it tomorrow and try to post if any issue occur.. Did the hanging for you happen after installation or after some time of use ?

VladoP.

---

