---
title: "Powernap"
date: 2012-01-26
forum: Server Platforms
---

### Post by Zanzacar on 2012-01-26
Hi, I have come across this problem and I cant seem to get it resolved. Basically I have a fresh install of powernap with the following config file. For whatever reason as you can see from the powernap.log file that it resets the counter and actually never hibernates as directed in the config file.

Steps I have taken so far.
1. restart the system: which actually works for a short period of time then reverts back to same problem.
2. reviewed information in powernap.err: There isnt anything in that file.
3. apt-get purge powernap & then apt-get install powernap: no results.
4. adjust config file: no results.

If anyone has any suggestions on what I should do next that would be awesome. Also attached for config file & the reset section of the powernap.log file.

---

### Post by ruffEdgz on 2012-01-26
I think its working but it only sleeps for 1 second. The reason for that is this variable in the config file:

INTERVAL_SECONDS = 1

When reading that second, it tells you the benefits/problems of keeping a low time or high time:
> 
# The powernap daemon will wake every INTERVAL_SECONDS and check for activity
# to all of the monitors.  [B]Lower values of INTERVAL_SECONDS will provide
# more detailed process monitoring but will consume more system resources.
# Higher values of INTERVAL_SECONDS will consume less system resources, but
# might miss activity that execute for less than INTERVAL_SECONDS.[/B]
# The minimum runtime of any monitor should not be less than INTERVAL_SECONDS.


I hope this helps.

---

### Post by Zanzacar on 2012-01-26
Thanks for the reply. I believe that is actually not the case with that configuration option. As you can see when I change it to lets say 10 seconds this is the output from the debug.

2012-01-26_10:29:48 DEBUG        Activity not found, increment absent time [10/1800]
2012-01-26_10:29:48 DEBUG      Looking for [threshold] LoadMonitor
2012-01-26_10:29:48 DEBUG        Activity not found, increment absent time [10/1800]
2012-01-26_10:29:48 DEBUG      Looking for [ssh] TCPMonitor
2012-01-26_10:29:48 DEBUG        Activity found, reset absent time [0/1800]
2012-01-26_10:29:48 DEBUG      Looking for [http] TCPMonitor
2012-01-26_10:29:48 DEBUG        Activity not found, increment absent time [10/1800]
2012-01-26_10:29:48 DEBUG      Looking for [vent] TCPMonitor
2012-01-26_10:29:48 DEBUG        Activity not found, increment absent time [10/1800]
2012-01-26_10:29:48 DEBUG    Sleeping [10] seconds
2012-01-26_10:29:58 DEBUG    Examining Monitors
2012-01-26_10:29:58 DEBUG      Looking for [ptmx] ConsoleMonitor
2012-01-26_10:29:58 DEBUG        Activity found, reset absent time [0/1800]
2012-01-26_10:29:58 DEBUG      Looking for [torrent] ProcessMonitor
2012-01-26_10:29:58 DEBUG        Activity not found, increment absent time [20/1800]
2012-01-26_10:29:58 DEBUG      Looking for [threshold] LoadMonitor
2012-01-26_10:29:58 DEBUG        Activity not found, increment absent time [20/1800]
2012-01-26_10:29:58 DEBUG      Looking for [ssh] TCPMonitor
2012-01-26_10:29:58 DEBUG        Activity found, reset absent time [0/1800]
2012-01-26_10:29:58 DEBUG      Looking for [http] TCPMonitor
2012-01-26_10:29:58 DEBUG        Activity not found, increment absent time [20/1800]
2012-01-26_10:29:58 DEBUG      Looking for [vent] TCPMonitor
2012-01-26_10:29:58 DEBUG        Activity not found, increment absent time [20/1800]
2012-01-26_10:29:58 DEBUG    Sleeping [10] seconds


the sleep interval is basically saying how often to monitor everything not how long to sleep for.

---

### Post by ruffEdgz on 2012-01-26
When looking at the additional logs you placed, you are correct to say that 'INTERVAL_SECONDS' is only being used to make sure when powernap will check the services again.

When I installed the powernap package on my computer and used a similar configuration, I noticed immediately that it hibernated my computer but couldn't complete it successfully because my swap space was too small.

When you do the command:
```

sudo free -m

```

What values do you get for your memory and swap? 

I always forget about this but a computer hibernating can depend on swap space ([https://help.ubuntu.com/community/SwapFaq):](https://help.ubuntu.com/community/SwapFaq):)
> 
Hibernation (suspend-to-disk) The hibernation feature (suspend-to-disk) writes out the contents of RAM to the swap partition before turning off the machine. Therefore, your swap partition should be at least as big as your RAM size. The hibernation implementation currently used in Ubuntu, swsusp, needs a swap or suspend partition. It cannot use a swap file on an active file system.


Hope we can solve this for ya.

---

### Post by Zanzacar on 2012-01-26
Thanks for the response. I didnt know about hibernation using your swap so that was news to me. Also here is the output from free -m

```

             total       used       free     shared    buffers     cached
Mem:          3895       3626        269          0        204       3181
-/+ buffers/cache:        240       3655
Swap:         4027          5       4022


```Based off this information do you think I should increase my swap size? 

Let me know if you have any questions or if there is anything else I should do.

Thanks for all the help.

---

### Post by ruffEdgz on 2012-01-26
Thanks for the additional information.

When looking at the RAM and swap size, you should be good (you would only be using a max of 3895MB of swap space when used).

Another question, when the powernode daemon is active, are you watching the monitor to make sure it does hibernate? When I was doing my tests with powernap on my computer, it worked but took my right back because of my swap problem (I didn't make my swap large enough hence why I wanted to make sure you didn't have the same problem). 

Here are the logs I got from my system which started the hibernation process but stopped right after it noticed I didn't have enough swap space:
```

2012-01-26_14:47:44 WARNING  Entered into GRACE PERIOD. Action [/usr/sbin/powernap] will be taken in [-24] seconds
2012-01-26_14:47:44 WARNING  Taking action [/usr/sbin/powernap]
2012-01-26_14:47:44 DEBUG    Reseting counters prior to taking action
2012-01-26_14:47:48 DEBUG    Sleeping [30] seconds
2012-01-26_14:48:18 DEBUG    Examining Monitors

```
As you can see, I see the same thing you did but it reset itself once I couldn't complete the hibernation process and reset my counter for me.

Also, take a look at these logs to see if they might give you some more information on this problem:
```

/var/log/pm-suspend.log
/var/log/syslog

```
I don't know how long this has been happening but remember to look at all those logs as they are rotated through logrotate ;)

---

### Post by Zanzacar on 2012-01-26
So here is what I did. I stop powernap deleted all the log files for pm-suspend, pm-powersave and powernap. Then I started powernap waited for it to attempt to shut down and then I stopped it. Basically capturing the errors only. Then I rebooted my machine because I know after a reboot it will actually shut down. That being said here are the two results.

pm-suspend.log = failed hibernate
```
Initial commandline parameters: 
Thu Jan 26 16:29:39 PST 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:
kernel update inhibits hibernate (/var/run/do-not-hibernate present)
```pm-suspend.log = sucessful hibernate
```
Initial commandline parameters: 
Thu Jan 26 16:41:03 PST 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux ubuntu-server 3.0.0-15-server #26-Ubuntu SMP Fri Jan 20 19:07:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
arc4                   12529  2 
rt2800usb              22590  0 
rt2800lib              54538  1 rt2800usb
nouveau               728677  1 
crc_ccitt              12667  1 rt2800lib
snd_hda_codec_idt      70553  1 
rt2x00usb              20830  1 rt2800usb
snd_hda_intel          33390  0 
rt2x00lib              50365  3 rt2800usb,rt2800lib,rt2x00usb
snd_hda_codec         104931  2 snd_hda_codec_idt,snd_hda_intel
ttm                    76805  1 nouveau
drm_kms_helper         42558  1 nouveau
drm                   236290  3 nouveau,ttm,drm_kms_helper
snd_hwdep              13613  1 snd_hda_codec
snd_pcm                96714  2 snd_hda_intel,snd_hda_codec
mac80211              462092  3 rt2800lib,rt2x00usb,rt2x00lib
snd_timer              29991  1 snd_pcm
i2c_algo_bit           13423  1 nouveau
snd                    68182  6 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
soundcore              12680  1 snd
cfg80211              199630  2 rt2x00lib,mac80211
mxm_wmi                12979  1 nouveau
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
psmouse                73882  0 
wmi                    19256  1 mxm_wmi
serio_raw              13166  0 
video                  19412  1 nouveau
dcdbas                 14490  0 
ppdev                  17113  0 
parport_pc             36962  1 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
ahci                   26002  3 
libahci                26861  1 ahci
tg3                   147729  0 
             total       used       free     shared    buffers     cached
Mem:       3989428     216900    3772528          0      17820      56996
-/+ buffers/cache:     142084    3847344
Swap:      4124668          0    4124668
```That is just the beginning of the file but it appears I need to do a kernel update. What exactly does that intail? I have done the following things since this.

```
sudo apt-get update
sudo apt-get upgrade
```Is there more that I need to do? I found one article online about updating the kernel but I just wasnt sure about it.

---

### Post by ruffEdgz on 2012-01-27
Well, when looking into the suspend/hibernation process in /usr/lib/pm-utils/sleep.d/000kernel-change and the script itself is an easy one:
```

if [ "$1" = "hibernate" ] && [ -f "/var/run/do-not-hibernate" ]; then
        echo "kernel update inhibits hibernate (/var/run/do-not-hibernate present)"
        exit 1
fi

```
Its saying that it needs to make sure the first variable when running 000kernel-change equals 'hibernate' and if the file exists called '/var/run/do-not-hibernate', then echo out the problem and exit the process.

The document that I found from Ubuntu is old but makes sense ([https://help.ubuntu.com/community/HibernateWhatHappens](https://help.ubuntu.com/community/HibernateWhatHappens)) but it says that the file called '/var/run/do-not-hibernate' is there is the kernel has been upgraded recently and you will need to reboot to complete the kernel update process.

Lets get the basics of your machine by running these commands:
```

cat /etc/*-release
uname -a

```

We can start from there and maybe more to the grub part if needed because it sounds like the rebooting process hasn't work when updating to the newest kernel update.

---

### Post by Zanzacar on 2012-01-27
Here is the data you requested. 

After I did apt-get update * apt-get upgrade everything seemed to be working up to par.


```
media@ubuntu-server:~$ cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
media@ubuntu-server:~$ uname -a
Linux ubuntu-server 3.0.0-15-server #26-Ubuntu SMP Fri Jan 20 19:07:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
media@ubuntu-server:~$

```

---

