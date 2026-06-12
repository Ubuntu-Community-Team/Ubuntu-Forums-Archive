---
title: "making my web server live"
date: 2014-10-19
forum: Server Platforms
---

### Post by jacebennest on 2014-10-19
Hi all,

To start off i have ubuntu 14 desktop installed on my ****** little laptop, which I leave on at home all the time, and only use for my LAMP class at school right now. I use my MBP for most of my media, schoolwork, developing etc. Anyway, I had a website on my friends server, but he moved and is in the (slow)process of getting it back up. I was wondering, since I have LAMP stack downloaded on the laptop can i easily make it live?

Can anyone point me to good tutorials to set that up. 

I live in Canada, use Shaw internet and I have a time capsule for my router. Thought those might be relevant. 

Thanks for any and all help guys.

---

### Post by TheFu on 2014-10-19
Well, just make your system exactly like his - php, apache, mysql, all the files, data, logins and configurations for those things.  Get it working internally.

Making it available externally with DNS is a little harder and means paying someone.  You need to own a domainname - a "registrar" is will need ot be paid.  Then you need a DNS service to tell example.com --> IP address.  If your ISP gives you a static IP, it is easier, but with DHCP you can pay a DNS provider to support rapid changes so folks can find your changed IP relatively quickly (5 min).  I'm not on Shaw, but they could block all inbound port 80 traffic (default for http traffic). If the do not, you are almost done. If they do ... er ... the end users will need to specify the port exactly. Oh ... and you'll want to open port 80 on the local router and direct that to an internal LAN IP.  That little laptop will need a static IP on your LAN, regardless.

Of course, if you don't use a domainname, then folks will need to know the public IP address and use that always. This is free, since there isn't any need for a registrar or dns provider.  OTOH, it is a hassle if the public IP keeps changing from day to day.  OTOH, when I had a residential cable internet connection, my public IP changed about once every other year. YMMV.

Hope that is clear.  

Oh - and please, please, please secure your apps. [https://www.owasp.org/index.php/PHP_Security_Cheat_Sheet](https://www.owasp.org/index.php/PHP_Security_Cheat_Sheet)

---

### Post by Doug S on 2014-10-20
> **TheFu said:**
>   I'm not on Shaw, but they could block all inbound port 80 traffic (default for http traffic). If the do not, you are almost done. If they do ... er ... the end users will need to specify the port exactly.It is my understanding that Shaw does not block any ports.> **TheFu said:**
> Of course, if you don't use a domainname, then folks will need to know the public IP address and use that always. This is free, since there isn't any need for a registrar or dns provider.  OTOH, it is a hassle if the public IP keeps changing from day to day.  OTOH, when I had a residential cable internet connection, my public IP changed about once every other year.Shaw dynamic IP addresses change very very rarely.

---

### Post by jacebennest on 2014-10-20
Thanks for the replies guys. It was actually a lot easier than I thought it would be!

I had a domain already from godaddy. So I just changed it to go to my IP. And port forwarding was pretty easy as I had already had experience opening up a port to ssh into the same laptop.

---

### Post by jacebennest on 2014-10-21
Next question!!!

because I am using a laptop to host the site, is there a way to have it run in the minimum amount of power. She is quite the beast and has been warmer than usual lately lol. I know the easy answe is to get a proper server, but finances (and effort) are low and I'm busy with other things. I just wanted to make sure ole betsy (my laptop) lasts as long as possible

thanks again

---

### Post by Doug S on 2014-10-21
Which CPU frequency governor is it using? The answer to your question depends. Example:```
doug@s15:/etc/apache2/sites-available$ [COLOR=#ff0000]cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver[/COLOR]
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
```If you are using the acpi-cpufreq governor, then just set powersave mode. If you get "No such file or directory" then there isn't anything you can do. If you are using the intel_pstate driver, then  you will want to set the maximum frequency (in percent) to the same as the minimum frequency (in percent). Example 1:```
doug@s15:/etc/apache2/sites-available$ [COLOR=#ff0000]grep . /sys/devices/system/cpu/intel_pstate/*[/COLOR]
/sys/devices/system/cpu/intel_pstate/max_perf_pct:100
[COLOR=#ff0000]/sys/devices/system/cpu/intel_pstate/min_perf_pct:42[/COLOR]
/sys/devices/system/cpu/intel_pstate/no_turbo:0
[COLOR=#ff0000]echo "42" > /sys/devices/system/cpu/intel_pstate/max_perf_pct[/COLOR]
```Example 2:```
doug@s15:/etc/apache2/sites-available$ [COLOR=#ff0000]cat /home/doug/temp/set_cpu_powersave[/COLOR]
#! /bin/bash
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
for file in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor; do echo "powersave" > $file; done
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
```

---

### Post by jacebennest on 2014-10-21
> **Doug S said:**
> Which CPU frequency governor is it using? The answer to your question depends. Example:```
doug@s15:/etc/apache2/sites-available$ [COLOR=#ff0000]cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver[/COLOR]
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
```If you are using the acpi-cpufreq governor, then just set powersave mode. If you get "No such file or directory" then there isn't anything you can do. If you are using the intel_pstate driver, then  you will want to set the maximum frequency (in percent) to the same as the minimum frequency (in percent). Example 1:```
doug@s15:/etc/apache2/sites-available$ [COLOR=#ff0000]grep . /sys/devices/system/cpu/intel_pstate/*[/COLOR]
/sys/devices/system/cpu/intel_pstate/max_perf_pct:100
[COLOR=#ff0000]/sys/devices/system/cpu/intel_pstate/min_perf_pct:42[/COLOR]
/sys/devices/system/cpu/intel_pstate/no_turbo:0
[COLOR=#ff0000]echo "42" > /sys/devices/system/cpu/intel_pstate/max_perf_pct[/COLOR]
```Example 2:```
doug@s15:/etc/apache2/sites-available$ [COLOR=#ff0000]cat /home/doug/temp/set_cpu_powersave[/COLOR]
#! /bin/bash
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
for file in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor; do echo "powersave" > $file; done
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
```

I have acpi-cpufreq, but no power save mode in power options page

---

### Post by Doug S on 2014-10-21
> **jacebennest said:**
> I have acpi-cpufreq, but no power save mode in power options pageExample 2 in my previous post  shows you how to set the acpi_cpufreq driver to powersave mode.

---

### Post by wlraider70 on 2014-10-21
You would be amazed at how old of a system you can run Ubuntu server on.  Find ANY desktop machine and install 14.04 server and see. I'll bet whatever box you find will work for your site.

---

### Post by jacebennest on 2014-10-22
> **Doug S said:**
> Example 2 in my previous post  shows you how to set the acpi_cpufreq driver to powersave mode.
 ah i see, thanks

just for curiosity's sake, what exactly does it change? appending the file with "powersave" is all that needs to happen?

---

### Post by Doug S on 2014-10-22
> **jacebennest said:**
> just for curiosity's sake, what exactly does it change? appending the file with "powersave" is all that needs to happen?for the acpi-cpufreq driver using the "powersave" frequency governor will cause the CPU to always be held at its minimum clock frequency, which corresponds to minimum power consumption.

---

### Post by mastablasta on 2014-10-22
> **wlraider70 said:**
> You would be amazed at how old of a system you can run Ubuntu server on.  Find ANY desktop machine and install 14.04 server and see. I'll bet whatever box you find will work for your site.

depending on the complexity and server demands of webstite raspbery Pi can run it. not much funding needed for that and also very low power usage.

---

### Post by jacebennest on 2014-12-29
hey guys, back again

everything is going great with betsy, but i want to make her life as easy as possible... this might be the same question as before, but

is there a way to shut off most of the system but leave just whats necessary to ssh in and to access the the websites i am hosting?

when i suspend, it clearly shuts too many things down to be a successful webhost. and when i log out, it still sounds like she is having a tough time every now and then.

i think, in essence, what i am asking is if there is a way to make my ubuntu OS act like ubuntu-server when i am not using the computer for personal use(which is limited, as i do most of my work on a different computer)

---

### Post by TheFu on 2014-12-30
Yes, but probably not worth your effort.
Logout and kill the GUI programs - perhaps through ssh?
You could setup the login program to be console-based, that would make this happen automatically when you logout.

Basically X/Windows is the largest hog on most desktop systems that cannot be turned off.

BTW - is it always best to ask a new question in a new thread. Nobody will see this post who isn't subscribed.

---

