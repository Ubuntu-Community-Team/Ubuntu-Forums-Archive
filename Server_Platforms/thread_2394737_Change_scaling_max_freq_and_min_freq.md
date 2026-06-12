---
title: "Change scaling_max_freq and min_freq"
date: 2018-06-20
forum: Server Platforms
---

### Post by fastserver on 2018-06-20
hello guys i have a problem here that i dont know how work


i have a server whit e3 1230


i  want to run always in 3.20GHz,  it is never at that speed, it is always  lower, i disable intel_pstate, I put performance as a governor

driver: acpi-cpufreq
CPUs which run at the same hardware frequency: 7
CPUs which need to have their frequency coordinated by software: 7
maximum transition latency: 10.0 us.
hardware limits: 1.60 GHz - 3.20 GHz
available  frequency steps: 3.20 GHz, 3.20 GHz, 3.10 GHz, 3.00 GHz, 2.90 GHz, 2.70  GHz, 2.60             GHz, 2.50 GHz, 2.40 GHz, 2.30 GHz, 2.20 GHz, 2.10  GHz, 1.90 GHz, 1.80 GHz, 1.70 GHz, 1.60 GHz
available cpufreq governors: conservative, ondemand, userspace, powersave, performance, sche            dutil
current policy: frequency should be within 1.60 GHz and 3.20 GHz.

The governor "performance" may decide which speed to use
within this range.
current CPU frequency is 3.20 GHz (asserted by call to hardware).
cpufreq  stats: 3.20 GHz:99.71%, 3.20 GHz:0.00%, 3.10 GHz:0.00%, 3.00 GHz:0.00%,  2.90 GHz:0.0            0%, 2.70 GHz:0.00%, 2.60 GHz:0.00%, 2.50  GHz:0.00%, 2.40 GHz:0.00%, 2.30 GHz:0.00%, 2.20 GHz:0            .00%,  2.10 GHz:0.00%, 1.90 GHz:0.00%, 1.80 GHz:0.00%, 1.70 GHz:0.00%, 1.60  GHz:0.28%  (16)



i need to change the current policy: frequency should be "within 1.60 GHz and 3.20 GHz"

i wanted to stay always as 3.20GHz, i understood that i need to chaange 

[COLOR=#000000]scaling_max_freq and scaling_min_freq but i dont know how[/COLOR]

---

### Post by slickymaster on 2018-06-20
Thread moved to **Server Platforms** for a better fit

---

### Post by QIII on 2018-06-20
Hello!

In general, you would want your frequency to scale down when the load is light and up when the load climbs.  You may never see 3.2GHz because it is not necessary for what the machine is doing at the time.

If your are in your car and idling at a traffic light, would you want to depress the accelerator and run the engine up to the red line?  Would you want to press the accelerator going up a hill and let off on it when going down?

Do you have a particular purpose in mind for keeping it running at such a high clock speed all the time?  Is your server generally under high load all the time and the latency of the frequency scaling change is affecting performance?  Are you using it for a space heater?  ;)

If your server is not consistently under high load, I'd recommend OnDemand to keep your server cool and efficient -- and keep the energy bill down.  The kernel and hardware will change the frequency as needed within a few cycles, say 3 milliseconds.

---

### Post by fastserver on 2018-06-20
> **QIII said:**
> Hello!

In general, you would want your frequency to scale down when the load is light and up when the load climbs.  You may never see 3.2GHz because it is not necessary for what the machine is doing at the time.

If your are in your car and idling at a traffic light, would you want to depress the accelerator and run the engine up to the red line?  Would you want to press the accelerator going up a hill and let off on it when going down?

Do you have a particular purpose in mind for keeping it running at such a high clock speed all the time?  Are you using it for a space heater?  ;)

I'd recommend OnDemand to keep your server cool and efficient -- and keep the energy bill down.  The OS and hardware will change the frequency as needed within a few cycles, say 3 milliseconds.
hello and thanks for fast response! i just used the server as the seedbox, for that i wanted the best performance.

---

### Post by QIII on 2018-06-20
OK.  Is it always under heavy load, or does the number of leechers vary dramatically?

Are you willing to risk reduced CPU lifetime (from the heat) in exchange for the reduction in latency?  Is this a production box that is critical enough to your bottom line that the expense of repair/replacement is outweighed by the need for high availability?

(This is up to you.  I'm not saying not to do it, but I'm just making a recommendation as we wait for someone with the answer to your original question.)

---

### Post by fastserver on 2018-06-20
> **QIII said:**
> OK.  Is it always under heavy load, or does the number of leechers vary dramatically?

Are you willing to risk reduced CPU lifetime (from the heat) in exchange for the reduction in latency?  Is this a production box that is critical enough to your bottom line that the expense of repair/replacement is outweighed by the need for high availability?
well yeah, its a server in i3d i think they have a very good cooling system,can you helpme QIII? i will see is the perform is better or the same, if is the same i will back change to normal like now

---

### Post by QIII on 2018-06-20
Is cpufrequtils installed on your machine?

---

### Post by fastserver on 2018-06-20
> **QIII said:**
> Is cpufrequtils installed on your machine?
Yes QIII, I disabled intel pstate to

---

### Post by QIII on 2018-06-20
And is your server ***bare metal*** or a virtual server?  You may not be able to do anything if it is a virtual server, as i3D may control the behavior of the CPU on its virtual machines.

I'm going from memory here, since I'm not at a Linux machine at the moment.

Issue the command

```
echo 'GOVERNOR="performance"' | sudo tee /etc/default/cpufrequtils
```

followed by (I hope this works with systemd...)

```
sudo update-rc.d ondemand disable
```

The second will disable the default "ondemand" setting.

Reboot if you can without messing up your server to see if that persists.

---

### Post by fastserver on 2018-06-20
> **QIII said:**
> And is your server ***bare metal*** or a virtual server?  You may not be able to do anything if it is a virtual server, as i3D may control the behavior of the CPU on its virtual machines.

I'm going from memory here, since I'm not at a Linux machine at the moment.

Issue the command

```
echo 'GOVERNOR="performance"' | sudo tee /etc/default/cpufrequtils
```

followed by (I hope this works with systemd...)

```
sudo update-rc.d ondemand disable
```

The second will disable the default "ondemand" setting.

Reboot if you can without messing up your server to see if that persists.
Oh thanks QIII, if I need to change back just put enable in ondemand?

---

### Post by QIII on 2018-06-20
I would first set "ondemand" in the first command and then, yes, enable ondemand.

---

### Post by fastserver on 2018-06-20
And another question, it will run at 3.20GHz or 3.6GHz(turbo)

---

### Post by QIII on 2018-06-20
That I can't say for sure.

---

### Post by QIII on 2018-06-20
You will probably have to restart the service for this to take effect immediately if you don't want to reboot.  But I'm not going to try to recall that from memory with systemd.

---

### Post by fastserver on 2018-06-20
And how I restart the service, sorry for so many questions, i am a very new Linux user  :(

---

### Post by QIII on 2018-06-20
Heh!

I have four physical Linux machines in my lab and 14 Linux VMs.  Alas, I am at a client location right now and they use Windows.  

Let's see if someone else chimes in.

---

### Post by fastserver on 2018-06-20
i think is this

sudo /etc/init.d/cpufrequtils restart

---

