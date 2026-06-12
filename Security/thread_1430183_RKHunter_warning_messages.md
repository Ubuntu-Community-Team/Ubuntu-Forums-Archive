---
title: "RKHunter warning messages"
date: 2010-03-15
forum: Security
---

### Post by ctrlmd on 2010-03-15
hi,
i scanned ubuntu with rkhunter 
and it give me warning on these locations 
> 
/usr/sbin/unhide
/usr/sbin/unhide-linux26   
also it says a warning with 
> 
Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]

 any ideas ?

---

### Post by RedMartin on 2010-03-15
Me too please.

---

### Post by HermanAB on 2010-03-15
Rkhunter is quite useless...

---

### Post by styxcoverbnd on 2010-03-15
> **ctrlmd said:**
> hi,
i scanned ubuntu with rkhunter 
and it give me warning on these locations 

/usr/sbin/unhide
/usr/sbin/unhide-linux26 


Most likely a false positive. You can look at the rkhunter logs to see the different hash numbers, but this is not something to worry about. run ```
rkhunter --check --propudate
``` from the command line to update rkhunter with the latest hash for unhide. Then rerun rkhunter and the warning should be gone

> **ctrlmd said:**
> also it says a warning with 
 
Performing filesystem checks
Checking /dev for suspicious file types [ Warning ]
Checking for hidden files and directories [ Warning ]

any ideas ?

Most likely false positives and nothing to worry about. look at the rkhunter logs and post what they say, but I'm assuming one warning is for pulse audio. Someone posted above that rkhunter is useless, I'm leaning more and more towards that feeling

---

### Post by ctrlmd on 2010-03-15
> **HermanAB said:**
> Rkhunter is quite useless...
well could you provide something better plz ?

---

### Post by ctrlmd on 2010-03-15
> **styxcoverbnd said:**
> Most likely a false positive. You can look at the rkhunter logs to see the different hash numbers, but this is not something to worry about. run ```
rkhunter --check --propudate
``` from the command line to update rkhunter with the latest hash for unhide. Then rerun rkhunter and the warning should be gone

[COLOR=Blue]_**thank you it remove the warning messages from unhide **_[/COLOR]



Most likely false positives and nothing to worry about. look at the rkhunter logs and post what they say, but I'm assuming one warning is for pulse audio. Someone posted above that rkhunter is useless, I'm leaning more and more towards that feeling
[PHP]Checking /dev for suspicious file types         [ Warning ]
[18:14:00] Warning: Suspicious file types found in /dev:
[18:14:00]          /dev/shm/pulse-shm-910181029: data
[18:14:00]          /dev/shm/pulse-shm-2726508941: data
[18:14:00]          /dev/shm/pulse-shm-1703200834: data
[18:14:00]          /dev/shm/pulse-shm-3238220387: data
[18:14:00]          /dev/shm/pulse-shm-2191996288: data
[18:14:00]   Checking for hidden files and directories       [ Warning ]
[18:14:00] Warning: Hidden directory found: /dev/.udev
[18:14:00] Warning: Hidden directory found: /dev/.initramfs[/PHP]

---

### Post by styxcoverbnd on 2010-03-15
> Checking /dev for suspicious file types         [ Warning ]
[18:14:00] Warning: Suspicious file types found in /dev:
[18:14:00]          /dev/shm/pulse-shm-910181029: data
[18:14:00]          /dev/shm/pulse-shm-2726508941: data
[18:14:00]          /dev/shm/pulse-shm-1703200834: data
[18:14:00]          /dev/shm/pulse-shm-3238220387: data
[18:14:00]          /dev/shm/pulse-shm-2191996288: data
[18:14:00]   Checking for hidden files and directories       [ Warning ]
[18:14:00] Warning: Hidden directory found: /dev/.udev
[18:14:00] Warning: Hidden directory found: /dev/.initramfs

Everything from your logs looks ok. [Here](http://ubuntuforums.org/showthread.php?p=4908163) is some more info on /dev/shm if you are interested

---

### Post by km0r3 on 2010-03-15
> hi,
i scanned ubuntu with rkhunter 
and it give me warning on these locations 
 	Quote:
 	 	 		 			 				/usr/sbin/unhide
/usr/sbin/unhide-linux26    			 		 	 	 
also it says a warning with 
 	Quote:
 	 	 		 			 				Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]
			 		 	 	 
 any ideas ? 	

Please use Google or the Forum search to find results next time. You don't know how valuable a Google search can be, as Google told me that your issue was asked many times before [like here]("http://www.pubbs.net/debian/200907/56352/"):
> >> [11:19:43] Warning: The file '/usr/sbin/unhide-linux26' exists on the
>> system, but it is not present in the rkhunter.dat file.

$ apt-file search /usr/sbin/unhide-linux26
unhide: /usr/sbin/unhide-linux26

probably you have installed unhide as suggested by rkhunter and you have =

installed it after the last rkhunter check.

Or even [here]("http://georgia.ubuntuforums.org/showthread.php?p=7799647") in the Forums.

Inform yourself about the meanings of the warnings. I suspect you never read the documentation.
**Hint: **```
man rkhunter
```

---

### Post by finite9 on 2010-03-17
been using rkhunter for 2 years, and get false positives in the daily report every day.

for me this tool becomes useless over time, because you end up ignoring the daily mails.  If it was only a mail when there was a problem I would pay more attention, but I just dont have the energy to check the mail every day for a home server.

I found previously that an apt-get upgrade would start triggering alarms in rkhunter logs.  I don't know if this still happens, but at the time, I thought 'why dont they check for rkhunter and run an update after and apt-get upgrade'.

my 2p.

---

### Post by OpSecShellshock on 2010-03-17
With any kind of rootkit detection software, you're going to get a lot of false positives. In fact, that's the majority of what you'll see, especially at the time of an update to any of the files it checks (which will alter the hashes that it's looking for). There's no absolutely reliable way to check for the presence of a rootkit. The detection utilities just point to values that are different than what they expect. They can't determine the reasons. That's the best anything is going to be able to do, since the goal of rootkits is avoidance of detection by the owner of the system. They'll load as early as possible on system start and change as few files as they can, while making sure their actions don't create logs (or at least don't leave them intact long enough to use).

I can't stress enough how low the risk of getting one on a desktop system is, though. The risk increases for servers that are listening for connections from the web, but that's true with anything. In most cases, if you're concerned enough about security/privacy to run regular checks for rootkits, you're probably already doing the things that will keep them from getting anywhere near your system.

---

### Post by bodhi.zazen on 2010-03-17
> **ctrlmd said:**
> well could you provide something better plz ?

rkhunter is "useless' because of the sheer number of false positives.

In order to be of any value you need to :

1. Run rkhunter from a live cd and a fresh install.

2. Repeat after every update

3. Use google to confirm if what is reported is a problem or a false positive.

This way you will know what is normal and can detect unusual activity.

With so many false positives many people find it is "useless". 

You may decide for yourself.

Personally I advise OSSEC.

---

