---
title: "checking logs for intrusion"
date: 2010-06-02
forum: Security
---

### Post by ubuntu27 on 2010-06-02
Hello everyone. 
Yesterday my laptop computer operated a force shutdown without my input.

So, I am looking for the cause of this. It might be a hardware failure or someone operated a remote shutdown. (I was connected to a non-encrypted wifi)

How do I check the later?


I am using Fedora 12 KDE. 


Thank you.

---

### Post by cariboo on 2010-06-02
The first thing I'd do is check hardware temps, as being the most likely culprit.

What services are you running, where were you when this happened?

Check /var/log/auth.log, for any unusual login attempts.

---

### Post by ubuntu27 on 2010-06-02
> **cariboo907 said:**
> The first thing I'd do is check hardware temps, as being the most likely culprit.

What services are you running, where were you when this happened?

Check /var/log/auth.log, for any unusual login attempts.

Thank you Cariboo.

My Fedora doesn't have auth.log for whatever reasons.

Syslog, auth.log, and damon.log doesn't exist either. 

How do I check the temperature?

---

### Post by cariboo on 2010-06-02
There are several ways to check tempuratures, unfortunately this is specific to Ubuntu, but they may work with fedora,

Open a terminal and type sensors, you may get something that looks like this:

```
 sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +38.0°C                                    
Core1 Temp:  +38.0°C
```

You may be better of checking [here]("http:///fedoraforum.org/") for answers to your questions.

---

### Post by ubuntu27 on 2010-06-02
```
sensors
``` doesn't work with Fedora.

I just searched for some package for Sensors and came across "Ksensors" a graphical utility which is a front-end for lm-sensors

In the CPU STATE it shows: 

IDLE  96.6
SYS   0.9
NICE  0.0
USER  2.6

I also installed ```
lm-sensors
```, but the command "sensors did not work" (I also tried to run it as root)


**EDIT:** Looks like a equivalent to Sensors is "sensors-detect" in Fedora. I am running the command now. It shows:

> [ubuntu27@fedora ~]$ sensors-detect
You need to be root to run this script.
[knight@hp-air ~]$ su
Password: 
[ubuntu27@fedora]# sensors-detect
# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: Hewlett-Packard HP Pavilion dv6700 Notebook PC (laptop)
# Board: Quanta 30CC

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): YES


**EDIT:**

> Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): YES
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): 


I wonder if I should prove the I2C/SMBus adapters. It mentions that it is risky. What do you think? I will Google it.


**EDIT:** Now I get it. I had to run Sensor-detect before Sensors.

Now the sensors output is:

```
sensors                                                                                                                                
coretemp-isa-0000                                                                                                                                            
Adapter: ISA adapter                                                                                                                                         
Core 0:      +53.0°C  (high = +85.0°C, crit = +85.0°C)                                                                                                                                                                                         
coretemp-isa-0001                                                                                                                                            
Adapter: ISA adapter                                                                                                                                         
Core 1:      +53.0°C  (high = +85.0°C, crit = +85.0°C) 
```

---

### Post by ubuntu27 on 2010-06-02
What's the acceptable temperature? (What degree should I be concerned with?)

---

### Post by bodhi.zazen on 2010-06-02
> **ubuntu27 said:**
> What's the acceptable temperature? (What degree should I be concerned with?)

From the output of lmsensors:

> (high = +85.0°C, crit = +85.0°C)

53 is fine, monitor the temp for a few days, see if it goes up with use.

---

### Post by ubuntu27 on 2010-06-03
THank you [cariboo907]("http://ubuntuforums.org/member.php?u=77104") and [bodhi.zazen]("http://ubuntuforums.org/member.php?u=89054")

Previously in [one of my post]("http://ubuntuforums.org/showpost.php?p=9400464&postcount=3"), I mentioned that I do not have auth.log, syslog, daemon.log in /var/log/

I have been searching in the web for this. But I can't find many sources on why it is not in Fedora and how to fix it.

THe closes  was [this thread]("http://www.linuxquestions.org/questions/linux-newbie-8/missing-auth-log-625419/") at linuxquestion.org

One of the members mentions:

> You would have to look into your system logging configuration(s) or some such thing to find out which services are being logged. The applications are probably running but no logs are maintained.

How do I access a "system logging configuration" ?

---

### Post by cllow2020 on 2010-06-03
i need help, my box is under attack from outside wan, notice from modem is blinking all the time, about 5 second each, Check /var/log/auth.log, found unusual login attempts as below , few thousand line. 
> 
[SIZE=2]Jun 3 13:17:01 myhostname CRON[1363]: pam_unix(cron:session): session opened for user root by (uid=0)
[SIZE=2]Jun 3 13:17:01 myhostname CRON[1363]: pam_unix(cron:session): session closed for user root
[/SIZE][/SIZE]
 
is there someting we ca do , like logon fail 5 times in 10 mins block it IP ? 
 
i truely really need help..please

---

### Post by spynappels on 2010-06-03
Those entries are generated by services running on your computer and are normal if you created the CRON job that runs them.

---

### Post by bodhi.zazen on 2010-06-03
> **ubuntu27 said:**
> THank you [cariboo907]("http://ubuntuforums.org/member.php?u=77104") and [bodhi.zazen]("http://ubuntuforums.org/member.php?u=89054")

Previously in [one of my post]("http://ubuntuforums.org/showpost.php?p=9400464&postcount=3"), I mentioned that I do not have auth.log, syslog, daemon.log in /var/log/

I have been searching in the web for this. But I can't find many sources on why it is not in Fedora and how to fix it.

THe closes  was [this thread]("http://www.linuxquestions.org/questions/linux-newbie-8/missing-auth-log-625419/") at linuxquestion.org

One of the members mentions:



How do I access a "system logging configuration" ?

Just a polite reminder, Fedora has a fine forums as well.

Your question is somewhat Fedora specific and I suggest using the Fedora Forums.

See also : [http://docs.fedoraproject.org/en-US/Fedora/12/html/Deployment_Guide/ch-logfiles.html](http://docs.fedoraproject.org/en-US/Fedora/12/html/Deployment_Guide/ch-logfiles.html)

---

