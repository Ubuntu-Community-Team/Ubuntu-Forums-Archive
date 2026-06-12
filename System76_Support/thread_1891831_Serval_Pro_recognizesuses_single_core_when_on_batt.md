---
title: "Serval Pro recognizes/uses single core when on battery power"
date: 2011-12-06
forum: System76 Support
---

### Post by akwala on 2011-12-06
*(Also emailed [EMAIL="support@system76.com"]support@system76.com[/EMAIL] re this.)*

Ubuntu 11.10 amd64
Linux 3.0.0-13-generic

This started happening recently and it happens consistently when I  switch to battery power or boot up when on battery power. It reverts to  the normal multicore once the power supply is connected.
       
      What I see when on battery power:
 
[LIST]
[*]         The machine gets extremely sluggish, almost unresponsive.
[*]         CPU usage hovers around 90+%.
[*]         Sensor indicator shows only Core 0 (Physical id 0) -- see the ouptut of 'sensors' command below.
[/LIST]
      With power connected:
               [FONT=courier new]$ sensors[/FONT]
              [FONT=courier new]acpitz-virtual-0[/FONT]
              [FONT=courier new]Adapter: Virtual device[/FONT]
              [FONT=courier new]temp1:        +52.0°C  (crit = +154.0°C)[/FONT]
               
              [FONT=courier new]coretemp-isa-0000[/FONT]
              [FONT=courier new]Adapter: ISA adapter[/FONT]
              [FONT=courier new]Physical id 0:  +53.0°C  (high = +86.0°C, crit = +100.0°C)[/FONT]
              [FONT=courier new]Core 0:         +53.0°C  (high = +86.0°C, crit = +100.0°C)[/FONT]
              [FONT=courier new]Core 1:         +52.0°C  (high = +86.0°C, crit = +100.0°C)[/FONT]
              [FONT=courier new]Core 2:         +49.0°C  (high = +86.0°C, crit = +100.0°C)[/FONT]
              [FONT=courier new]Core 3:         +53.0°C  (high = +86.0°C, crit = +100.0°C)[/FONT]
               
              On battery power:
                           [FONT=courier new]$ sensors[/FONT]
                      [FONT=courier new]acpitz-virtual-0[/FONT]
                      [FONT=courier new]Adapter: Virtual device[/FONT]
                      [FONT=courier new]temp1:        +52.0°C  (crit = +154.0°C)[/FONT]
                       
                      [FONT=courier new]coretemp-isa-0000[/FONT]
                      [FONT=courier new]Adapter: ISA adapter[/FONT]
                      [FONT=courier new]Physical id 0:  +52.0°C  (high = +86.0°C, crit = +100.0°C)[/FONT]
                      [FONT=courier new]Core 0:         +52.0°C  (high = +86.0°C, crit = +100.0°C)

[/FONT]

[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

### Post by isantop on 2011-12-07
Which Serval is this happening on? 

Also, what does System Monitor say? You can look at the Resources tab to get a live look at what, if any, activity is going on in any of the 8 logical cores, and you can use the processes list to single out what process is causing the sluggishness.

---

### Post by akwala on 2011-12-07
>Which Serval is this happening on?
serp7 
...from the order details -- don't know where to find it on Oneiric.

> **isantop said:**
> Also, what does System Monitor say? You can look at the Resources tab to get a live look at what, if any, activity is going on in any of the 8 logical cores, and you can use the processes list to single out what process is causing the sluggishness.
The attached screenshots of the system monitor were taken in the following order: w/ power supply connected; power supply disconnected (switch to battery power); power supply re-connected. This was done with the same processes running.

While I did the above, gnome-system-monitor spent by far the most time at the top of CPU usage, followed by Xorg and compiz.

Then, w/ the power disconnected, I shut down the System Monitor and watched 'atop' for awhile, while I used multiple programs. No single process hogged the CPU, but the the total usage hovered at 95%+.

---

### Post by sfmadmax on 2011-12-07
I try to reply on these forums when I can.

Sounds like pm-utils might be doing more damage ,  do this..


Plug in power to your laptop

1.)  Open a terminal and type, #tail -f /var/log/syslog

2.)  Unplug power

wait a few seconds


3.) plug power back in

4.) paste the output displayed from /var/log/syslog here..  

also run

#apt-cache policy pm-utils

let me know if you have a config files in /etc/pm/power.d

thats a start.  

I have the Older Pangolin and pm-utils drove my laptop nuts, knocking out cores whenever I unplugged power .. It did however give me about 20-30 minutes extra when on battery. 

you can modify the config file (if one exists) for power.d to be less harsh on the processors. Also if you have a SSD/Hybrid i don't think it's necessary to remount the Hard Drive. 

Let me know,
-Sean

---

### Post by akwala on 2011-12-07
Thanks, Sean!

> **sfmadmax said:**
> Plug in power to your laptop

1.)  Open a terminal and type, #tail -f /var/log/syslog

2.)  Unplug power

wait a few seconds


3.) plug power back in

4.) paste the output displayed from /var/log/syslog here..  
```
Dec  7 20:37:15 UbuntuServalPro postfix/master[4288]: warning: /usr/lib/postfix/local: bad command startup -- throttling
Dec  7 20:37:26 UbuntuServalPro kernel: [12972.089022] coretemp coretemp.0: TjMax is 100 C.
Dec  7 20:37:26 UbuntuServalPro kernel: [12972.093203] CPU 1 is now offline
Dec  7 20:37:26 UbuntuServalPro kernel: [12972.096270] CPU 5 MCA banks CMCI:0 CMCI:1 CMCI:3
Dec  7 20:37:26 UbuntuServalPro kernel: [12972.097040] coretemp coretemp.0: TjMax is 100 C.
Dec  7 20:37:26 UbuntuServalPro kernel: [12972.100501] CPU 2 is now offline
Dec  7 20:37:26 UbuntuServalPro kernel: [12972.106149] CPU 6 MCA banks CMCI:0 CMCI:1 CMCI:3
Dec  7 20:37:26 UbuntuServalPro kernel: [12972.107944] coretemp coretemp.0: TjMax is 100 C.
Dec  7 20:37:26 UbuntuServalPro kernel: [12972.111529] CPU 3 is now offline
Dec  7 20:37:26 UbuntuServalPro kernel: [12972.115604] CPU 7 MCA banks CMCI:0 CMCI:1 CMCI:3
Dec  7 20:37:26 UbuntuServalPro kernel: [12972.218672] CPU 4 is now offline
Dec  7 20:37:26 UbuntuServalPro kernel: [12972.224955] Broke affinity for irq 54
Dec  7 20:37:26 UbuntuServalPro kernel: [12972.226223] CPU 5 is now offline
Dec  7 20:37:26 UbuntuServalPro kernel: [12972.234016] Broke affinity for irq 23
Dec  7 20:37:26 UbuntuServalPro kernel: [12972.235999] CPU 6 is now offline
Dec  7 20:37:26 UbuntuServalPro kernel: [12972.251053] Broke affinity for irq 17
Dec  7 20:37:26 UbuntuServalPro kernel: [12972.252851] CPU 7 is now offline
Dec  7 20:37:26 UbuntuServalPro kernel: [12972.252858] SMP alternatives: switching to UP code
Dec  7 20:37:30 UbuntuServalPro kernel: [12975.735996] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
Dec  7 20:37:44 UbuntuServalPro kernel: [12989.713602] SMP alternatives: switching to SMP code
Dec  7 20:37:44 UbuntuServalPro kernel: [12989.725947] Booting Node 0 Processor 1 APIC 0x2
Dec  7 20:37:44 UbuntuServalPro kernel: [12989.725951] smpboot cpu 1: start_ip = 98000
Dec  7 20:37:44 UbuntuServalPro kernel: [12989.836881] Switched to NOHz mode on CPU #1
Dec  7 20:37:44 UbuntuServalPro kernel: [12989.880802] coretemp coretemp.0: TjMax is 100 C.
Dec  7 20:37:44 UbuntuServalPro kernel: [12989.901031] Booting Node 0 Processor 2 APIC 0x4
Dec  7 20:37:44 UbuntuServalPro kernel: [12989.901036] smpboot cpu 2: start_ip = 98000
Dec  7 20:37:44 UbuntuServalPro kernel: [12990.012822] Switched to NOHz mode on CPU #2
Dec  7 20:37:44 UbuntuServalPro kernel: [12990.013545] coretemp coretemp.0: TjMax is 100 C.
Dec  7 20:37:44 UbuntuServalPro kernel: [12990.019399] Booting Node 0 Processor 3 APIC 0x6
Dec  7 20:37:44 UbuntuServalPro kernel: [12990.019404] smpboot cpu 3: start_ip = 98000
Dec  7 20:37:44 UbuntuServalPro kernel: [12990.130890] coretemp coretemp.0: TjMax is 100 C.
Dec  7 20:37:44 UbuntuServalPro kernel: [12990.132197] Booting Node 0 Processor 4 APIC 0x1
Dec  7 20:37:44 UbuntuServalPro kernel: [12990.132201] smpboot cpu 4: start_ip = 98000
Dec  7 20:37:44 UbuntuServalPro kernel: [12990.132780] Switched to NOHz mode on CPU #3
Dec  7 20:37:44 UbuntuServalPro kernel: [12990.244746] Switched to NOHz mode on CPU #4
Dec  7 20:37:44 UbuntuServalPro kernel: [12990.244841] Booting Node 0 Processor 5 APIC 0x3
Dec  7 20:37:44 UbuntuServalPro kernel: [12990.244846] smpboot cpu 5: start_ip = 98000
Dec  7 20:37:44 UbuntuServalPro kernel: [12990.356708] Switched to NOHz mode on CPU #5
Dec  7 20:37:44 UbuntuServalPro kernel: [12990.356997] Booting Node 0 Processor 6 APIC 0x5
Dec  7 20:37:44 UbuntuServalPro kernel: [12990.357002] smpboot cpu 6: start_ip = 98000
Dec  7 20:37:44 UbuntuServalPro kernel: [12990.468675] Switched to NOHz mode on CPU #6
Dec  7 20:37:44 UbuntuServalPro kernel: [12990.470075] Booting Node 0 Processor 7 APIC 0x7
Dec  7 20:37:44 UbuntuServalPro kernel: [12990.470080] smpboot cpu 7: start_ip = 98000
Dec  7 20:37:45 UbuntuServalPro kernel: [12990.584632] Switched to NOHz mode on CPU #7
Dec  7 20:37:45 UbuntuServalPro anacron[6666]: Anacron 2.3 started on 2011-12-07
Dec  7 20:37:45 UbuntuServalPro anacron[6666]: Normal exit (0 jobs run)
Dec  7 20:37:48 UbuntuServalPro kernel: [12994.150512] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
```> **sfmadmax said:**
> also run

#apt-cache policy pm-utils
```
$ apt-cache policy pm-utils
pm-utils:
  Installed: 1.4.1-8ubuntu1
  Candidate: 1.4.1-8ubuntu1
  Version table:
 *** 1.4.1-8ubuntu1 0
        500 http://www.lug.bu.edu/mirror/ubuntu/ oneiric/main amd64 Packages
        100 /var/lib/dpkg/status
```> **sfmadmax said:**
> let me know if you have a config files in /etc/pm/power.d
There are no config files, but I found these scripts in /etc/pm/power.d...
```
00flag*  00-jupiter-cpu*  01cpu_online*  cpu_frequency*  eth_speed  kms_powermode  usb  usb_autosuspend*  video
```...of which, 01cpu_online "Turns off all the CPU's (cores) available but CPU0." ](*,)  I don't know whether/how this gets invoked.

[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

### Post by sfmadmax on 2011-12-07
Hey!

So yea, looks like your suffering from pm-utils stabbing all of your cores upon switching to battery, Is this a original install or upgraded from a original install? 

one more command i forgot to ask you to run,

#apt-cache policy laptop-mode-tools

I just want to know if your running the standard power tools or the modified version. I don't think Oneiric installs the modified version by default.

Well theres 2 ways to fix this,

1.) Uninstall power tools

This will run for laptop full blast with / without power, I'm not sure if this is acceptable for you but def a workaround. Not sure how long you will get.. mabye 45 - 60 minutes?  you'l have to benchmark it to really know. 

2.) modify the cpu script so it doesn't offline all the cores. Mabye leave 2 / 3 cores online.  If you can paste the 01cpu_online script in a pastebin. ( [http://pastebin.ubuntu.com](http://pastebin.ubuntu.com)  ) and send me the link.  I'll take a look when i get a chance..  

I had this problem originally like you, I ended up uninstalling laptop-mode-tools completely. Besides being swamped @ work with no time to troubleshoot my laptop problems, I do alot of work in virtual machines qemu/vbox, so I always need the laptop at full power when i'm working. I do use battery mode when attending meetings but thats about it. Usually the meetings don't run too long. 

It also caused more problems than doing any good.  My ethernet port would randomly disconnect and reconnect itself, I also had a hard time keeping a Gig uplink. It would always drop to 10/100. I pin pointed the issue to power mgmt. No matter if I was on power or battery, the hard disk would randomly remount and various hardware devices would reset, the ethernet driver was one of them. 

After removing it problem was gone. however I think we should be able to modify the script. If you feel comfortable with editing the script feel free to take a crack at it and i can proof it.  

Let me know,
Sean

---

### Post by akwala on 2011-12-07
> **sfmadmax said:**
> Hey!

So yea, looks like your suffering from pm-utils stabbing all of your cores upon switching to battery, Is this a original install or upgraded from a original install? 
I installed Oneiric from scratch, it's not an upgrade.

> **sfmadmax said:**
> one more command i forgot to ask you to run,

#apt-cache policy laptop-mode-tools

I just want to know if your running the standard power tools or the modified version. I don't think Oneiric installs the modified version by default.
I don't have laptop-mode-tools installed -- I had come across [this bug]("https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/801623") which is still open.

> **sfmadmax said:**
> 2.) modify the cpu script so it doesn't offline all the cores. Mabye leave 2 / 3 cores online.  If you can paste the 01cpu_online script in a pastebin. ( [http://pastebin.ubuntu.com](http://pastebin.ubuntu.com)  ) and send me the link.  I'll take a look when i get a chance..  
Here it be: [http://pastebin.ubuntu.com/763391/](http://pastebin.ubuntu.com/763391/)
Looks straightforward. I'll try modifying set_cpu_online() to maybe turn off 2 of the 4 CPUs. Will report back what I find.

Thanks for all the info, good to know all the things that might go wrong because of pm tweaks.
[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

### Post by sfmadmax on 2011-12-07
> **akwala said:**
> 

Here it be: [http://pastebin.ubuntu.com/763391/](http://pastebin.ubuntu.com/763391/)
Looks straightforward. I'll try modifying set_cpu_online() to maybe turn off 2 of the 4 CPUs. Will report back what I find.

Thanks for all the info, good to know all the things that might go wrong because of pm tweaks.
[LEFT][COLOR=#000000][/COLOR][/LEFT]


Awesome!  yea very simple to modify actually now that I look at it..  All you need to do is change the for statement...  

So if you have 8 cores and you want to leave 3 on all the time, change the for statement to look like this. 

set_cpu_online() {
	for cpu in /sys/devices/system/cpu/cpu[2-7]/online; do
		[ -w "$cpu" ] || continue
		echo $1 > $cpu
	done
}

Depending on how many cores you want active just change the 1st number.. 
[1-7] == 2 cores active
[2-7] == 3 cores active
[3-7] == 4 cores active

so on , so on,

I live in boston too btw ;P 
hopefully we don't get too much snow.

---

### Post by fuduntu on 2011-12-08
Holy crap, what the hell is that?

If you have a package installed called "powernap" remove it.

---

### Post by akwala on 2011-12-08
> **fuduntu said:**
> Holy crap, what the hell is that?

If you have a package installed called "powernap" remove it.
I do have 'powernap' installed but I've never run it -- I've been meaning to investigate it. Why do you advise against it?
[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

### Post by fuduntu on 2011-12-08
> **akwala said:**
> I do have 'powernap' installed but I've never run it -- I've been meaning to investigate it. Why do you advise against it?
[LEFT][COLOR=#000000][/COLOR][/LEFT]

Powernap is what provides that awful trigger that disables your CPUs.

If you look in the kernel documentation, turning the CPUs "off" just means the kernel directs processes away from it and fences it.  It doesn't actually power the core down, so you don't save any power.  Maybe a marginal savings from the core being in extended sleep.

I verified with a kill-a-watt, it's practically worthless.

Do they include this by default?  What a horrid piece of software.

---

### Post by akwala on 2011-12-08
> **sfmadmax said:**
> So if you have 8 cores and you want to leave 3 on all the time, change the for statement to look like this. 

set_cpu_online() {
    for cpu in /sys/devices/system/cpu/cpu[2-7]/online; do
        [ -w "$cpu" ] || continue
        echo $1 > $cpu
    done
}

Depending on how many cores you want active just change the 1st number.. 
[1-7] == 2 cores active
[2-7] == 3 cores active
[3-7] == 4 cores active

so on , so on,
So... My chip is i7-2630QM, which has 4 CPUs, each or which has 2 threads. The 8 "cores" are thus actually 8 threads, numbered 0-7 and referred to as CPUs or cores. /sys/devices/system/cpu/cpu0 cannot be disabled, so [2-7] in the above would give 2 active cores (0 and 1); [3-7] would give 3 active cores (0, 1 and 2); etc.

It would follow that, with 1-7 disabled, I had a single active thread, cpu0. When I disabled 2-7, System Monitor showed 2 CPUs and I saw marked improvement wrt the sluggishness.

> I live in boston too btw ;P 
hopefully we don't get too much snow.
Yeah, I'm hoping for a mild winter too.

[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

### Post by akwala on 2011-12-08
> **fuduntu said:**
> Powernap is what provides that awful trigger that disables your CPUs.

If you look in the kernel documentation, turning the CPUs "off" just means the kernel directs processes away from it and fences it.  It doesn't actually power the core down, so you don't save any power.  Maybe a marginal savings from the core being in extended sleep.

I verified with a kill-a-watt, it's practically worthless.

Do they include this by default?  What a horrid piece of software.
Ah. Good to know. Powernap is not included in the standard install, I installed it myself. I did not expect it to have any effect unless I ran it. 01cpu_online and the other scripts in /etc/pm/power.d/ belong to the powernap-common package, it certainly is bad form that these get invoked even if powernap is not running.

Re saving power by turning off the CPUs, there also seems to be some question as to whether this is effective in Intel's "Sandy Bridge" chips like the one I have.

[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

### Post by sfmadmax on 2011-12-09
> **akwala said:**
> So... My chip is i7-2630QM, which has 4 CPUs, each or which has 2 threads. The 8 "cores" are thus actually 8 threads, numbered 0-7 and referred to as CPUs or cores. /sys/devices/system/cpu/cpu0 cannot be disabled, so [2-7] in the above would give 2 active cores (0 and 1); [3-7] would give 3 active cores (0, 1 and 2); etc.

Correct you got it! I should of realized you had a newer generation processor. My apologies



> **akwala said:**
> It would follow that, with 1-7 disabled, I had a single active thread, cpu0. When I disabled 2-7, System Monitor showed 2 CPUs and I saw marked improvement wrt the sluggishness.

Great, glad to see that you saw a improvement!
[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

### Post by sfmadmax on 2011-12-09
> **akwala said:**
> Ah. Good to know. Powernap is not included in the standard install, I installed it myself. I did not expect it to have any effect unless I ran it. 01cpu_online and the other scripts in /etc/pm/power.d/ belong to the powernap-common package, it certainly is bad form that these get invoked even if powernap is not running.

Yea this has been broking for a while, i believe prior to natty, hence why i removed all of the power mgmt tools off of my laptop. 

> **akwala said:**
> 
Re saving power by turning off the CPUs, there also seems to be some question as to whether this is effective in Intel's "Sandy Bridge" chips like the one I have.

IMHO , these power tools might be a waste. At the last [_Ubuntu Developer Summit_]("http://uds.ubuntu.com") we talked about improving power mgmt in Ubuntu for the future releases

[https://blueprints.launchpad.net/ubuntu/+spec/desktop-p-power-consumption](https://blueprints.launchpad.net/ubuntu/+spec/desktop-p-power-consumption)


&&

[https://blueprints.launchpad.net/linaro/+spec/linaro-hackfest-kernel-pm-4](https://blueprints.launchpad.net/linaro/+spec/linaro-hackfest-kernel-pm-4)


-Sean

[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

