---
title: "OS freezes frequently"
date: 2023-09-22
forum: Virtualisation
---

### Post by satimis on 2023-09-22
Hi all,

Oracle VirtualBox
Host - Ubuntu 22.04
VM/Guest - Ubuntu 22.04

Starting
Oracle VM VirtualBox Manager - Ubuntu VM
Settings ->
select System/Display/etc.

It freezes the OS.  I have to press Hard-reboot.

Please advise where I have to check?  Thanks

Regards

---

### Post by ian-weisser on 2023-09-22
Guest: Ubuntu Desktop 22.04? Or Ubuntu Server 22.04?

Does the VM have the minimum recommended resources?

---

### Post by satimis on 2023-09-22
> **ian-weisser said:**
> Guest: Ubuntu Desktop 22.04? Or Ubuntu Server 22.04? 
Ubuntu Desktop 22.04 desktop
installed on ubuntu-22.04.3-desktop-amd64.iso

> 
Does the VM have the minimum recommended resources?
more than recommended minimum resources

Regards

---

### Post by MAFoElffen on 2023-09-25
I'm going to stay out of this for supporting, because you already have a few qualified people involved here to help you with this.

My only comment to help is that they need specific detailed information to help. This could be so many things that you really need to be specifc with your ansers in how how configured the VM and the system within it.

Why? You say it freezes when do something as simple as going to the Settings options in the VM right? They asked you about the resources given to the Guest and how you set the guest up... and your answer was only:
[quote=satimis]
more than recommended minimum resources
[/quote]
That very short answer does not say much, nor give any details in order to help you. How would you feel about getting that answer if you asked for more details? They should not have to take 40 posts to 'extract' information from you. *Please explain yourself in detail.* Help them to be able to help you. 

That makes sense right? I wish you luck.

---

### Post by satimis on 2023-09-25
> **MAFoElffen said:**
> I'm going to stay out of this for supporting, because you already have a few qualified people involved here to help you with this.

My only comment to help is that they need specific detailed information to help. This could be so many things that you really need to be specifc with your ansers in how how configured the VM and the system within it.

Why? You say it freezes when do something as simple as going to the Settings options in the VM right? They asked you about the resources given to the Guest and how you set the guest up... and your answer was only:

That very short answer does not say much, nor give any details in order to help you. How would you feel about getting that answer if you asked for more details? They should not have to take 40 posts to 'extract' information from you. *Please explain yourself in detail.* Help them to be able to help you. 

That makes sense right? I wish you luck.
Sorry, it would be diffulty for me to explain the incidents.  In some cases when I started a VM and another case when I was browsing Internet on Firefox and another case when I started Firefox browser etc.

In recent few days the freezing incidence reduces.  I don't know WHY?  I haven't altered any change on the OS, Ubuntu 22.04

Regards

---

### Post by ian-weisser on 2023-09-25
> **satimis said:**
> Sorry, it would be diffulty for me to explain the incidents.

Without some details or some troubleshooting data, not much we can help you with. We would be guessing in the dark. You don't need our help for that.

Perhaps you can narrow the potential causes causes by reviewing your logs, checking your CPU and memory usage when your system begins to sputter, test your hardware when possible, and looking for patterns.

---

### Post by satimis on 2023-09-26
> **ian-weisser said:**
> Without some details or some troubleshooting data, not much we can help you with. We would be guessing in the dark. You don't need our help for that.

Perhaps you can narrow the potential causes causes by reviewing your logs, checking your CPU and memory usage when your system begins to sputter, test your hardware when possible, and looking for patterns.
Please advise where shall I check the log in next freezing?

If it is caused by;
1) Browsing Iternet on Firefox or starting Firefox to browse Internet ?

2) Operating Ubuntu 22.04 VM of VirtualBox ?

Thanks

Regards

---

### Post by ian-weisser on 2023-09-26
> **satimis said:**
> Please advise where shall I check the log in next freezing?

Review all you can find. As logs are timestamped, it should not be onerous.

---

### Post by MAFoElffen on 2023-09-26
I just came up with this for you to use. Here you go...

I am sure that ian-weisser can explain to you how to set this up and how to use it.

@ian-weisser -- add to or modify as you choose. Just an idea to make this simple and short.
```

#!/bin/sh
## MAFoElffen,<MAFoElffen@ubuntu.com>,2023.09.26
# Filename: sysres.sh
# Purpose: Log System Stats to log at /var/log/sysreq.log
#
# Add this to crond:
#     */1 * * * * /full/path/to/sysres.sh
# Note: That will run this every 1 minute...

## Notes: If you comment out this next line... It will send the log messages directly to /var/log/syslog...
#  so you can see in your syslog where other things are happening
logger -f /var/log/sysres.log

logger "$(free -m | \
    awk 'NR==2{printf "Memory Usage: %s/%sMB (%.2f%%)\n", $3,$2,$3*100/$2 }')"

logger "(df -h | \
    awk '$NF=="/"{printf "Disk Usage: %d/%dGB (%s)\n", $3,$2,$5}')"

logger "$(top -bn1 | \
    grep load | \
    awk '{printf "CPU Load: %.2f\n", $(NF-2)}')"


```
If ran as is, reviewing this log, and seeing system resources 'high', then search your syslog on the same timestamp....

Caution: this is gong to only be needed during your tests, once done, remove the cron job so it doesn't fill storage over time.

---

### Post by satimis on 2023-09-26
> **ian-weisser said:**
> Review all you can find. As logs are timestamped, it should not be onerous.
Hi ian-weisser

Just had an incident.

Start PC -> Login -> Start Google Chrome

The OS (Ubuntu 22.04 desktop) freezed.  Waiting for 5 min it was still the same.

Pressed hard-reboot with no effect.  I have to switch off the PC and re-switched the PC on.  Now I can log-in and continue to work.

Where I have to check?  Where I can find the relevant log-file?

Regards

---

### Post by ian-weisser on 2023-09-26
> **satimis said:**
> Pressed hard-reboot with no effect.

If "pressed hard-reboot" means the same thing to both of us (?), that suggests a hardware fault.

Please be specific about exactly what key-presses and switches you did.

---

### Post by satimis on 2023-09-26
> **ian-weisser said:**
> If "pressed hard-reboot" means the same thing to both of us (?), that suggests a hardware fault.

Please be specific about exactly what key-presses and switches you did.
Hard-reboot without effect, the screen still freezing. It won't reboot the PC

Finally
Switch off the power of the PC
Switch on the power of the PC again
Start the PC
It boots straight to Login screen of Ubuntu 22.04
Login
Start Ubuntu 22.04 screen
Click Google Chrom icon on left vertical menu to start Chrome browser.

It is now working without problem

Regards

---

