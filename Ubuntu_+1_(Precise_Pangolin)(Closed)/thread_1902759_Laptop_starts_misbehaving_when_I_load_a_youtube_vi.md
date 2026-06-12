---
title: "Laptop starts misbehaving when I load a youtube video"
date: 2011-12-31
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Jordanwb on 2011-12-31
I'm not sure if this is flash or what but the problem started when Firefox was updated to version 10. 

What happens is that when I load a youtube video (I suppose any Flash video on any site) and I press Fn+Up (Volume up) the volume is turned up as normal, but the Volume HUD doesn't go away and it all goes downhill from there. 

Trying to raise or lower the volume again doesn't have any effect for a few minutes, KDE's task bar doesn't acknowledge window changes (although I can Alt+Tab just fine); the CPU's fan spins up and won't spin down; sometimes Kubuntu just refuses to shutdown and I have to do "sudo halt", even that doesn't work sometimes. None of the icons in the system tray work (IE I can't click the volume icon and manually adjust the volume)

I'm not sure if I have this problem on my Desktop, I thought I did but it might have been the volume control just lagging a bit.

Also how would I find out why my laptop's fan spins up and down every few minutes?

[Edit #504] Yeah I'm having this issue on my desktop but only the volume control part.

---

### Post by ronacc on 2011-12-31
any chance it is because something is getting hot ? There are several monitor widgets that will show your temps if your lappy has the sensors . you can find them with the "get new widgets" button .

---

### Post by Jordanwb on 2011-12-31
I added the Hardware Temperature widget to the desktop but the widget was empty.

---

### Post by ronacc on 2011-12-31
it works on my desktop shows both cpu cores, check and see if you have libsensors4 installed , it was by default on my sys , or your lappy may not have the sensors although I can't see a lappy not having them .

---

### Post by Jordanwb on 2011-12-31
I have libsensors4 installed.

---

### Post by ronacc on 2011-12-31
ok install lmsensors and then run ```
 sudo sensors-detect 
```
that will tell you what sensors if any you have , here is the output from it on my desktop ```
ron@ron-desktop2:~$ sudo sensors-detect
[sudo] password for ron: 
# sensors-detect revision 5946 (2011-03-23 11:54:44 +0100)
# Board: Gigabyte Technology Co., Ltd. GA-M55PLUS-S3G

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): 
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   Success!
    (driver `k8temp')
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
Intel digital thermal sensor...                             No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

```

---

### Post by Jordanwb on 2011-12-31
```
root@jordan-Laptop:/home/jordan# sensors-detect                                                                                                                                     
# sensors-detect revision 5946 (2011-03-23 11:54:44 +0100)                                                                                                                                      
# System: Acer Aspire 5741 (laptop)                                                                                                                                                             
                                                                                                                                                                                                
This program will help you determine which kernel modules you need                                                                                                                              
to load to use lm_sensors most effectively. It is generally safe                                                                                                                                
and recommended to accept the default answers to all questions,                                                                                                                                 
unless you know what you're doing.                                                                                                                                                              
                                                                                                                                                                                                
Some south bridges, CPUs or memory controllers contain embedded sensors.                                                                                                                        
Do you want to scan for them? This is totally safe. (YES/no): yes                                                                                                                               
Module cpuid loaded successfully.                                                                                                                                                               
Silicon Integrated Systems SIS5595...                       No                                                                                                                                  
VIA VT82C686 Integrated Sensors...                          No                                                                                                                                  
VIA VT8231 Integrated Sensors...                            No                                                                                                                                  
AMD K8 thermal sensors...                                   No                                                                                                                                  
AMD Family 10h thermal sensors...                           No                                                                                                                                  
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
Intel digital thermal sensor...                             Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No
```

I said yes to every question and added coretemp to /etc/modules. I modprobe'd coretemp and readded the Hardware Temperature widget but it's still empty.

---

### Post by ronacc on 2011-12-31
what shows up when you click the "wrench" on the hardware monitor widget ?

---

### Post by Jordanwb on 2011-12-31
Glorious nothing

---

### Post by ronacc on 2011-12-31
its not seeing the sensors . I don't have one of those laptops to try things on . I couldn't find any docs on the hardware monitor widget perhaps it don't work with those sensors , try some others , if none of them work maybe you need a driver or firmware for the sensors , try to configure them with lm-sensors that is one of its functions  see the man page for how .

---

### Post by Jordanwb on 2011-12-31
I came across the censors command:

```
jordan@jordan-Laptop:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +47.0°C  (high = +80.0°C, crit = +90.0°C)
Core 2:       +56.0°C  (high = +80.0°C, crit = +90.0°C)
```

So the coretemp module is working. My CPU is hyperthreaded so the physical cores are #0 and #2.

---

### Post by ronacc on 2011-12-31
great ! sometimes you just have to keep fooling around until something works :P

---

### Post by Jordanwb on 2011-12-31
> **ronacc said:**
> great ! sometimes you just have to keep fooling around until something works :P

But that's not solving the issue in the OP. :neutral:

---

### Post by ronacc on 2011-12-31
are you using gnash or libflashplayer.so ? I jut tried with gnash and it works normally for me , I don't have keyboard volume control but on mouse over the volume slider pops up and down normally and volume responds instantly up and down .

edit : I'm 64 bit here I don't know if arch makes any difference with gnash .

---

### Post by Jordanwb on 2011-12-31
Hmm the volume control issue isn't Flash specific, I have the same issue when using smplayer.

---

### Post by ronacc on 2012-01-01
sorry it took awhile to get back , I shutdown shortly after my last post .
have you checked your sound settings ? what mixer are you using , I'm using kmix here with default settings .

---

### Post by Jordanwb on 2012-01-01
I'm using the laptop's onboard audio chip

```
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
```

---

### Post by ronacc on 2012-01-01
what mixer ?

---

### Post by Jordanwb on 2012-01-01
> **ronacc said:**
> what mixer ?

Uhhh pulseaudio? :confused:

---

### Post by ronacc on 2012-01-01
try switching to kmix if that fixes it file a bug on pulse .

---

### Post by Jordanwb on 2012-01-01
> **ronacc said:**
> try switching to kmix if that fixes it file a bug on pulse .

Uhh how do I do that.

---

### Post by ronacc on 2012-01-01
I don't know , I don't use kde much and I just assumed there would be a setting for it but I can't find it , maybe someone with more kde experience will chime in . one thing you can do is check to see if its even installed , it was default on my system .

---

### Post by mc4man on 2012-01-01
Haven't used kde in a long time but - 
have you tried creating a new user & seeing if your issue(s) occur with that user?
I'd assume that top or htop can be used in kubuntu - is any process pegging a cpu when this occurs?

---

### Post by Jordanwb on 2012-01-01
Pulseaudio is installed on my laptop.

> **mc4man said:**
> Haven't used kde in a long time but - 
have you tried creating a new user & seeing if your issue(s) occur with that user?
I'd assume that top or htop can be used in kubuntu - is any process pegging a cpu when this occurs?

I'll try that when I get home later this afternoon.

---

### Post by ronacc on 2012-01-01
top is a built in kernel cmd so you have it , run it in konsole . htop has no dependencies that would block it in kubuntu . also you could try installing kmix , worst case it would destroy your system and you would have to reinstall , this IS a development release

---

### Post by Jordanwb on 2012-01-01
I loaded a YouTube video and ran top in the background and spent about half the video raising and lowering the volume without problem. I decided to check /var/log/dpkg.log.1 and say that in today's upgrades kmix was on of the updates. So for the time being the problem seems to be fixed. Also I checked smplayer's audio device settings and saw that it used alsa, I changed it to pulse(audio) and I can raise and lower the volume without problem.

Problem solved (for now?)

---

### Post by ronacc on 2012-01-01
incase you are new to dev releases breakage ( or fixes ) are only an update away .:lolflag:

mark your thread solved .

---

