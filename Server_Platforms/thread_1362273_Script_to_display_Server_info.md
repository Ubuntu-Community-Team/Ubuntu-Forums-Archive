---
title: "Script to display Server info"
date: 2009-12-22
forum: Server Platforms
---

### Post by humphreybc on 2009-12-22
I've got a home server setup with lm-sensors and hddtemp, and I'd like to have a script that I can easily run that displays all the server information in one command..

I think there is one floating around that someone else wrote, but I'm not sure. I don't know how to write scripts.

Also, I installed a Chassis fan today and it's connected via ATA... lm-sensors picks it up:

```

Chassis Fan:     6308 RPM  (min =   -1 RPM, div = 2)

```

It's going at maximum RPM all the time, which is unnecessary - how can I change the RPM, perhaps have it set at 3000 RPM all the time?

EDIT: I played around with Q-Fan in the BIOS... unfortunately it only controls the CPU fan, not the Chassis Fan (which is on 100% all the time). So, I just switched around the two plugs for Chassis and CPU - now the CPU fan runs a bit faster than it was before, and the chassi fan changes depending on CPU heat - most of the time it runs at 90% normal speed, because the CPU heat is very low, it's only a file server.

Now would be a good time to tell me that it's bad to run the CPU fan faster than it's meant to, or that I should have switched the two around. I want to know if my CPU is about to melt...

Thankyou

---

### Post by CharlesA on 2009-12-23
Stupid question, but is that new fan a PVM fan?

---

### Post by humphreybc on 2009-12-23
Doesn't appear to be, running the pvm command (forgotten what it is) says that there are no pvm fans detected or something.

Switching the CPU and Chassis plugs around seems to be working okay, it's not as whiny loud now!

---

### Post by CharlesA on 2009-12-23
Ah ok. Not that it'll help you any, but I just checked my BIOS setting for my fans.

CPU: 1600 RMP
Chassis: 1100 RMP
Power: 700 RMP

CPU and Chassis were set to "Turbo" in Q-FAN and my system is running at around 35C.

Also: How old is the system? In my system, newer CPU, 4 pin power connector won't accept the 3-pin power connector of a case fan.

As for the script, I suppose you could write something that'll query the fan speed/temps and grep the data that you want.

```
lmsensors | grep "FAN1"
```

---

### Post by humphreybc on 2009-12-23
Hmm cheers. Yeah my CPU is running at about 3000 RPM, the case is about 2000 - but that's only because I switched the plugs around. The figures below for fan speeds have to be divided by two.

```

benjamin@benjamin-server:~$ sensors
asb100-i2c-1-2d
Adapter: SMBus nForce2 adapter at 5500
VCore 1:          +1.71 V  (min =  +1.31 V, max =  +1.97 V)   
+3.3V:            +3.34 V  (min =  +2.96 V, max =  +3.63 V)   
+5V:              +5.03 V  (min =  +4.49 V, max =  +5.51 V)   
+12V:            +11.80 V  (min =  +9.55 V, max = +14.41 V)   
-12V (reserved): -12.32 V  (min =  -0.00 V, max =  -0.00 V)
-5V (reserved):   -5.17 V  (min =  -0.00 V, max =  -0.00 V)
CPU Fan:         4687 RPM  (min =   -1 RPM, div = 2)
Chassis Fan:     6683 RPM  (min =   -1 RPM, div = 2)
Power Fan:          0 RPM  (min =   -1 RPM, div = 2)
M/B Temp:         +28.0°C  (high = +80.0°C, hyst = +75.0°C)  
CPU Temp (Intel): +25.0°C  (high = +80.0°C, hyst = +75.0°C)  
Power Temp:        -0.5°C  (high = +80.0°C, hyst = +75.0°C)  
CPU Temp (AMD):   +25.0°C  (high = +80.0°C, hyst = +75.0°C)  
cpu0_vid:        +1.650 V

w83l785ts-i2c-1-2e
Adapter: SMBus nForce2 adapter at 5500
CPU Diode:   +37.0°C  (high = +110.0°C) 

```

The system isn't particularly old, I got it for $50 without a hard drive. It was a bargain, 512MB RAM, 1.2GHz AMD Athlon XP I believe. It's perfect for a server. The case is in beautiful condition.

I might have another hunt for that script that someone has already written, it seemed very useful - gave you everything from the system name and network information to the hard drive temps and uptime.

---

### Post by humphreybc on 2009-12-23
Found it! Got it working with sensors, but hddtemp needs to be run as root... anyway to change that?

```

<?php
// ==================================================================
// Basic server infomation and links to internal webpages.
// ==================================================================
?>

<html>
<head>
<title> Server</title>
<center>
<br/>
<h1>Server Pages</h1><br/>
<a href="http://google.com"> Add Links Here </a>


</center>
<br/>
<STYLE type=text/css>
BODY { FONT-SIZE: 8pt; COLOR: black; FONT-FAMILY: Verdana,arial, helvetica, serif; margin : 0 0 0 0;  }
#turnkey-credit #override { display: none; }
</STYLE>
</head>
<body>
<center><table><tr><td>
<pre>
<b>Uptime:</b> 
<?php system("uptime"); ?>

<b>Kernel Information:</b>
<?php system("uname -a"); ?>

<b>External I.P.</b>
<?php system("wget www.whatismyip.com/automation/n09230945.asp -O - -o /dev/null"); ?>

<!--
<b>System Information:</b>
<?php system("lsb_release -a"); ?>
-->
<b>Memory Usage (MB):</b> 
<?php system("free -t -m"); ?>

<b>Disk Usage:</b> 
<?php system("df -h | grep /dev/sd"); ?>

<b>Hard Drive Temperature:</b>
<?php system("sudo hddtemp /dev/sda"); ?>

<b>Sensor Information</b>
<?php system("sensors"); ?>

<b>CPU Information:</b> 
<?php system("cat /proc/cpuinfo | grep \"vendor_id\\|\model name\\|cpu MHz\\|bogomips\""); ?>
</pre>
</td></tr></table></center>

</body>
</html>

```

---

### Post by CharlesA on 2009-12-23
Hmm where did you find that?

You could probably add it like this:

```
<?php system("lmsensors| grep "CPU Fan""); ?>

```

Don't quote me on that tho, since I've not used that script (which looks like it serves an internal webpage with system info)

---

### Post by humphreybc on 2009-12-23
Yep I worked it out and added in the sensors command, works great now.

Except hddtemp needs to be run as root, like this:

sudo hddtemp /dev/sda

But it won't work through this php page obviously - How can I change hddtemp to not require sudo?

---

### Post by BkkBonanza on 2009-12-23
Add just before the </pre> near the end.

<b>Sensor Information:</b> 
<?php system("sensors");?>

Of course, you could use grep to pull certain lines only.
eg. system("sensors | grep Fan");

Edit: Oh, I'm a few minutes late! Oh well.

---

