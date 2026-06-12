---
title: "Using the output from 'sensors' in a script"
date: 2011-09-18
forum: Server Platforms
---

### Post by MG2R on 2011-09-18
Hi,

I'm trying to write a bash script which checks my CPU-temp and shuts down my server when the temp reaches 80°C. Now, this is not so hard except for the fact that I don't know how I'm supposed to get a variable out of my 'sensors' command. 

When I run sensors, this is my output:
> asb100-i2c-0-2d
Adapter: SMBus I801 adapter at e800
in0:         +1.58 V  (min =  +1.20 V, max =  +1.81 V)   
in1:         +1.58 V  (min =  +1.20 V, max =  +1.81 V)   
in2:         +3.31 V  (min =  +2.96 V, max =  +3.63 V)   
in3:         +2.99 V  (min =  +2.67 V, max =  +3.28 V)   
in4:         +3.07 V  (min =  +2.51 V, max =  +3.79 V)   
in5:         +3.07 V  (min =  +0.00 V, max =  +0.00 V)
in6:         +3.07 V  (min =  +0.00 V, max =  +0.00 V)
fan1:          0 RPM  (min =   -1 RPM, div = 8)
fan2:          0 RPM  (min =   -1 RPM, div = 8)
fan3:          0 RPM  (min =   -1 RPM, div = 8)
temp1:       +26.0°C  (high = +80.0°C, hyst = +75.0°C)  
temp2:       +46.5°C  (high = +100.0°C, hyst = +90.0°C)  
temp3:        -0.5°C  (high = +80.0°C, hyst = +75.0°C)  
temp4:       +25.0°C  (high = +80.0°C, hyst = +75.0°C)  
cpu0_vid:   +1.525 V
The temperature I'm interested in, is temp2. That's the CPU temperature. How can I use that value in a script?

---

### Post by Porcini M. on 2011-09-18
VAL="`sensors | grep temp2 | tr '+' ' ' | tr '°' ' ' | awk '{print $2;}'`"

---

