---
title: "sonsor warnings + munin"
date: 2008-11-19
forum: Server Platforms
---

### Post by threetimes on 2008-11-19
I have munin with the sensors_temp and sensors_volt plugins configured.
[https://munin.peter-server.homelinux.net/localdomain/localhost.localdomain-sensors_volt.html](https://munin.peter-server.homelinux.net/localdomain/localhost.localdomain-sensors_volt.html) (Voltage)
[https://munin.peter-server.homelinux.net/localdomain/localhost.localdomain-sensors_temp.html](https://munin.peter-server.homelinux.net/localdomain/localhost.localdomain-sensors_temp.html) (Temperature)
 
But it warns my about my CPU temperature and "Critical" -5 and -12 voltages.
 
> peter@peter-server:~$ sensors 
as99127f-i2c-0-2d 
Adapter: SMBus PIIX4 adapter at e800 
VCore 1: +1.70 V (min = +1.46 V, max = +1.84 V) 
VCore 2: +2.54 V (min = +2.24 V, max = +2.74 V) 
+3.3V: +3.46 V (min = +2.96 V, max = +3.62 V) 
+5V: +5.08 V (min = +4.49 V, max = +5.48 V) 
+12V: +11.43 V (min = +9.12 V, max = +13.62 V) 
-12V: -11.70 V (min = -9.60 V, max = -14.37 V) 
-5V: -5.06 V (min = -4.00 V, max = -6.00 V) 
fan1: 0 RPM (min = 0 RPM, div = 4) 
fan2: 0 RPM (min = 0 RPM, div = 4) 
fan3: 0 RPM (min = 0 RPM, div = 4) 
M/B Temp: +26.0Â°C (high = **+105.0**Â°C, hyst = **+0.0**Â°C) 
CPU Temp: +34.5Â°C (high = **+100.0**Â°C, hyst = **+92.0**Â°C) 
temp3: -31.5Â°C (high = +122.0Â°C, hyst = +121.0Â°C) 
cpu0_vid: +1.650 V 
beep_enable:enabled
 
For the temperatures, I feel that i have to change the bold values, but how?
And what is wrong with my voltages?

---

### Post by threetimes on 2008-11-20
Is there really noone who at least knows where to look?

---

