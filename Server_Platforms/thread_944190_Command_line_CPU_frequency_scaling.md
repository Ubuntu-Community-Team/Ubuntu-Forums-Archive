---
title: "Command line CPU frequency scaling"
date: 2008-10-11
forum: Server Platforms
---

### Post by lucaspr on 2008-10-11
I've installed Ubuntu 8.04.1 for 'home' use. Filesharing, printsharing, got zimbra on it and a game server.

Now I've got a AMD BE-2350 cpu. Which I would like to scale down if the computer isn't used. 

What programs can I use from the command line? I did a search for this matter, but all I found was in Gnome, which isn't installed.

I read a post in which someone said that a server should not be scaled, but my server isn't to busy the whole day! Just in the evening. Is it possible to activate frequency scaling from the command line?

Thanx in advance for any replies!

---

### Post by Krupski on 2008-10-11
> **lucaspr said:**
> I've installed Ubuntu 8.04.1 for 'home' use. Filesharing, printsharing, got zimbra on it and a game server.

Now I've got a AMD BE-2350 cpu. Which I would like to scale down if the computer isn't used. 

What programs can I use from the command line? I did a search for this matter, but all I found was in Gnome, which isn't installed.

I read a post in which someone said that a server should not be scaled, but my server isn't to busy the whole day! Just in the evening. Is it possible to activate frequency scaling from the command line?

Thanx in advance for any replies!

Are you running desktop or server?

If you're running desktop, CPU scaling is already installed and running at the lowest speed (unless an app needs more - then it jumps up).

If you want to add control to SERVER, do this:

First, add the line "acpi-cpufreq" (without the quotes) to your "/etc/modules" file.

You have to reboot for it to be loaded, or you can use the command "modprobe acpi-cpufreq" to load it right away.

Next, add these lines to your "/etc/rc.local" file:

```

###############################
# set cpu governor to conservative
###############################
/usr/bin/test -e /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor && /bin/echo [COLOR="Red"]**conservative**[/COLOR] > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
/usr/bin/test -e /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor && /bin/echo [COLOR="Red"]**conservative**[/COLOR] > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
/usr/bin/test -e /sys/devices/system/cpu/cpu2/cpufreq/scaling_governor && /bin/echo [COLOR="Red"]**conservative**[/COLOR] > /sys/devices/system/cpu/cpu2/cpufreq/scaling_governor
/usr/bin/test -e /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor && /bin/echo [COLOR="Red"]**conservative**[/COLOR] > /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor
exit 0

```

Note: no need to edit the file if you have less than 4 cores. The script will only set as many as you have.

This will set your CPU governor to "conservative" which means it will run at minimal speed, unless more is needed. Then, it will jump up in steps as required, up to the maximum. Once the high load process is finished, the CPU will throttle back down all by itself.

This is totally automatic... there's no need to manually change the CPU speed.

Good luck!

-- Roger

---

### Post by Viabobed on 2008-10-11
Wow thats great... 
What if I want to do it the other way around? Instead of "conservative".

I think laptops are already set conservative.

---

### Post by Krupski on 2008-10-11
> **Viabobed said:**
> Wow thats great... 
What if I want to do it the other way around? Instead of "conservative".

I think laptops are already set conservative.

I edited my previous post to colorize the parameters.

If you want something different that "conservative", edit the red highlighted items (previous post) as follows:

[COLOR="Red"]**powersave**[/COLOR] (runs CPU at min clock always).
[COLOR="Red"]**performance**[/COLOR] (runs CPU at full clock always)
[COLOR="Red"]**ondemand**[/COLOR] (CPU clock jumps from low to high as needed)
[COLOR="Red"]**conservative**[/COLOR] (CPU clock jumps up in small steps as needed)


There's a fifth one called "userspace", but I haven't a clue what it does or how it works. I've tried it and it never seems to kick the CPU up when needed (like when running GZIP).

Hope this helps.

-- Roger

---

### Post by Viabobed on 2008-10-12
> **Krupski said:**
> I edited my previous post to colorize the parameters.

If you want something different that "conservative", edit the red highlighted items (previous post) as follows:

[COLOR="Red"]**powersave**[/COLOR] (runs CPU at min clock always).
[COLOR="Red"]**performance**[/COLOR] (runs CPU at full clock always)
[COLOR="Red"]**ondemand**[/COLOR] (CPU clock jumps from low to high as needed)
[COLOR="Red"]**conservative**[/COLOR] (CPU clock jumps up in small steps as needed)


There's a fifth one called "userspace", but I haven't a clue what it does or how it works. I've tried it and it never seems to kick the CPU up when needed (like when running GZIP).

Hope this helps.

-- Roger

That is exactly what I was looking for. I really appreciate the information Roger.

I was just trying to keep the clock speed up for an old laptop having trouble run webpages. 

Thanks again.

-Sherwin

---

### Post by windependence on 2008-10-12
You're crazy spending so much effort on a chip that is designed to use less energy to start with. Did you know, this processor uses only 45 watts at FULL power? That Cool 'n Quiet and SpeedStep are already built in to the chip and can be enabled in the BIOS without regard to your Operating system. and that you probably won't even notice the power diff at all since it uses about the same power of a 40 watt light bulb?

It's already extremely efficient, and you would only gain maybe 10% by doing what you are planning to do. Is $4 REALLY worth it for all the time and effort

-Tim

---

### Post by lucaspr on 2008-10-12
> **windependence said:**
> You're crazy spending so much effort on a chip that is designed to use less energy to start with. Did you know, this processor uses only 45 watts at FULL power? That Cool 'n Quiet and SpeedStep are already built in to the chip and can be enabled in the BIOS without regard to your Operating system. and that you probably won't even notice the power diff at all since it uses about the same power of a 40 watt light bulb?

It's already extremely efficient, and you would only gain maybe 10% by doing what you are planning to do. Is $4 REALLY worth it for all the time and effort

-Tim

I get your point, but what if I had another server which isn't as energy efficient? What about knowledge? I thank Krupski for the info! As I could not get it clear on my own, so I think in my case I'm not in for the money, just the knowledge to do it and doing so and seeing it work... Makes me feel good! And I want it to run as energy efficient as possible! But then again.. Indeed.. It will not save me much. 

Always the kick of getting things done! :)

I first typed this reply then tried Krupski's commands..

getting this error: **FIXED**

Now for the next step... How can I check the frequency from command line?

I'm checking my cpu with: cat /proc/cpuinfo

AHA!Just checked it, it always was 2100Mhz no it is 1000Mhz! Thanx Krupski for your information!!

---

### Post by Krupski on 2008-10-12
> **windependence said:**
> You're crazy spending so much effort on a chip that is designed to use less energy to start with.

Not really...

My file server has a dual core 2.66 GHz. Intel CPU in it. I use the conservative governor and it runs at the minimum of 1.536 GHz. most of the time. It only jumps up when I do cpu intensive stuff like random number generation or GZIP / ZIP / UNZIP'ping a file.

I really don't care about the energy savings, but I do notice that the server box runs noticeable cooler (as determined by the temperature of the air coming out of the power supply).

I haven't measured it, I just notice that it "feels less warm".

Why run at full speed if it's not necessary?

---

### Post by Krupski on 2008-10-12
> **lucaspr said:**
> I get your point, but what if I had another server which isn't as energy efficient? What about knowledge? I thank Krupski for the info! As I could not get it clear on my own, so I think in my case I'm not in for the money, just the knowledge to do it and doing so and seeing it work... Makes me feel good! And I want it to run as energy efficient as possible! But then again.. Indeed.. It will not save me much. 

Always the kick of getting things done! :)

I first typed this reply then tried Krupski's commands..

getting this error: **FIXED**

Now for the next step... How can I check the frequency from command line?

I'm checking my cpu with: cat /proc/cpuinfo

AHA!Just checked it, it always was 2100Mhz no it is 1000Mhz! Thanx Krupski for your information!!

Here's a little script that I use to watch the CPU speed. I call it "[COLOR="Red"]**cpus**[/COLOR]", but you can name it anything you wish:

```

#!/bin/sh
###############################
# display speed of cpu cores
###############################
/usr/bin/test -e /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq && /bin/echo -n 'cpu_core_0:   ' && /bin/cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq
/usr/bin/test -e /sys/devices/system/cpu/cpu1/cpufreq/cpuinfo_cur_freq && /bin/echo -n 'cpu_core_1:   ' && /bin/cat /sys/devices/system/cpu/cpu1/cpufreq/cpuinfo_cur_freq
/usr/bin/test -e /sys/devices/system/cpu/cpu2/cpufreq/cpuinfo_cur_freq && /bin/echo -n 'cpu_core_2:   ' && /bin/cat /sys/devices/system/cpu/cpu2/cpufreq/cpuinfo_cur_freq
/usr/bin/test -e /sys/devices/system/cpu/cpu3/cpufreq/cpuinfo_cur_freq && /bin/echo -n 'cpu_core_3:   ' && /bin/cat /sys/devices/system/cpu/cpu3/cpufreq/cpuinfo_cur_freq

```

This script should be placed in a directory that's in your path... like "/usr/local/sbin" so that it can be run from a command line. Also, it's execute permissions must be set (i.e. chmod 0755).

No need to edit it... it will only display as many cores as you have.

You can also use it to watch your CPU clocks continuously... with the "watch" command:

```

watch --i=1 [COLOR="Red"]**cpus**[/COLOR]

```

This runs the script "cpus" every second (the "--i=1" parameter) and allows real time watching of the clock speeds.


(by the way, my broswer (firefox) shows the "u" in cpus as a "mu" (micro) symbol. Obviously, it's the letter U, not "mu".)

---

### Post by cariboo on 2008-10-13
Some times we get to involved in getting  things done the geeky way when there is a much easier solution. I know there is a setting in my BIOS that I believe it is called cool and quiet, it cuts down the cpu frequency by 50% until full power is needed then it ramps up to full speed. I don't use it on my desktop, but if my server had that feature I would use it. It takes a reboot and a couple of seconds and its done.

Jim

---

### Post by Krupski on 2008-10-13
> **cariboo907 said:**
> Some times we get to involved in getting  things done the geeky way when there is a much easier solution. I know there is a setting in my BIOS that I believe it is called cool and quiet, it cuts down the cpu frequency by 50% until full power is needed then it ramps up to full speed. I don't use it on my desktop, but if my server had that feature I would use it. It takes a reboot and a couple of seconds and its done.

Jim

The OP asked for help with "**_Command line_** CPU frequency scaling". Hence the "geeky" response.

---

### Post by lucaspr on 2008-10-14
Krupski.. My hero ;)

But it works like a charm! I'm also using the conservatie governer! Super script and thank you so much! 

My problem is solved!

---

### Post by Krupski on 2008-10-14
> **lucaspr said:**
> Krupski.. My hero ;)

But it works like a charm! I'm also using the conservatie governer! Super script and thank you so much! 

My problem is solved!

Glad I could help!

-- Roger

---

### Post by Twizzle on 2008-10-14
This is just what I have been looking for!

I do however have a question or two. I currently have my Athlon XP2400 underclocked through the bios in my home server and run athcool to keep both temperature and power consumption down. If I use this method:

1) Will I see an advantage over athcool?
2) Can I use both athcool and this method together?
3) Should I set my cpu back to the default frequencies if I use this method? The server just serves video and music occasionally and is also running ZoneMinder as a single camera CCTV system. I currently have it underclocked to 1300Mhz but I guess with this method I might see an even better drop when idle.

As it stands, my server runs at around 40C and consumes around 80 watts using athcool and underclocking.

I will start playing around with settings tomorrow but I did not want to risk running athcool and this together without advice as I have heard that athcool can, in some circumstances, cause serious problems!

---

### Post by Krupski on 2008-10-14
> **Twizzle said:**
> This is just what I have been looking for!

I do however have a question or two. I currently have my Athlon XP2400 underclocked through the bios in my home server and run athcool to keep both temperature and power consumption down. If I use this method:

1) Will I see an advantage over athcool?
2) Can I use both athcool and this method together?
3) Should I set my cpu back to the default frequencies if I use this method? The server just serves video and music occasionally and is also running ZoneMinder as a single camera CCTV system. I currently have it underclocked to 1300Mhz but I guess with this method I might see an even better drop when idle.

As it stands, my server runs at around 40C and consumes around 80 watts using athcool and underclocking.

I will start playing around with settings tomorrow but I did not want to risk running athcool and this together without advice as I have heard that athcool can, in some circumstances, cause serious problems!

Well... I've never used "athcool", but I don't like what I've read about it:

```

Warnings
athcool only sets/unsets the "Disconnect enable when STPGNT detected" bit in the northbridge of the chipset. To save power, someone has to send the STPGNT signal when the CPU is idle. This is done by the ACPI subsystem when the C2 state is entered. Hence, you need ACPI support in your kernel to achieve power savings.

Depending on your motherboard and/or hardware components, enabling power-saving mode may cause:

    * noisy or distorted sound playback,

    * a slowdown in disk performance,

    * system freezes or instability,

    * massive corruption of the filesystem (rare, but observed at least once).

Before use athcool, you must recognize these potential DANGERS. Please use athcool AT YOUR OWN RISK. 

```


If your motherboard is fairly new, it will support ACPI. If so, then you can disable and get rid of ATHCOOL and just load "acpi-cpufreq" in your "/etc/modules" file, then use the scripts (in previous posts up above) to set your CPU throttling activity.

The acpi-cpufreq governors set not only the cpu clock speed, but also the core voltage as required.

A CPU running at a lower frequency can run stable with a lower supply voltage, so acpi-cpufreq controls both appropriately.

I like how it works. It keeps the box nice and cool, and it throttles up if necessary.

I would suggest giving it a try.

-- Roger

---

### Post by Twizzle on 2008-10-15
Hmmm. I think I have a problem.

I was running an Athlon XP2200+ CPU (not 2400 as mentioned above!) underclocked through the bios to 1300Mhz and athcool. My results were an idle power consumption of 91.5W and temperature of around 40C.

I reset the bios to automatically set the clock speed and ran it again with athcool and have an idle power consumption of 101.5W and temperature around the same (admittedly I have not given it time to run in)

I then turned athcool off and rebooted. Power remained at around 101W and temperature remained similar.

I added "acpi-cpufreq" (without the quotes) to the "/etc/modules" file as directed previously and tried to use the command "modprobe acpi-cpufreq" but got the following error:

```
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.24-16-server/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufrew.ko): Operation not permitted
```

If I run "sudo modprobe acpi-cpufreq" I get:

```
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.24-16-server/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufrew.ko): No such device
```

I tried to reboot instead and did not see any errors so I added the code as directed to my /etc/rc.local . (I only used two lines instead of the four though - I only have one core...)

I then rebooted and again saw no errors.

If I run cat /proc/cpuinfo my Mhz remains at 1800 (1727.975 to be precise) and my power consumption remains at 101W.

I am guessing that the FATAL error has someting to do with this!

---

### Post by Krupski on 2008-10-15
> **Twizzle said:**
> Hmmm. I think I have a problem.

I was running an Athlon XP2200+ CPU (not 2400 as mentioned above!) underclocked through the bios to 1300Mhz and athcool. My results were an idle power consumption of 91.5W and temperature of around 40C.

I reset the bios to automatically set the clock speed and ran it again with athcool and have an idle power consumption of 101.5W and temperature around the same (admittedly I have not given it time to run in)

I then turned athcool off and rebooted. Power remained at around 101W and temperature remained similar.

I added "acpi-cpufreq" (without the quotes) to the "/etc/modules" file as directed previously and tried to use the command "modprobe acpi-cpufreq" but got the following error:

```
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.24-16-server/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufrew.ko): Operation not permitted
```

If I run "sudo modprobe acpi-cpufreq" I get:

```
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.24-16-server/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufrew.ko): No such device
```

I tried to reboot instead and did not see any errors so I added the code as directed to my /etc/rc.local . (I only used two lines instead of the four though - I only have one core...)

I then rebooted and again saw no errors.

If I run cat /proc/cpuinfo my Mhz remains at 1800 (1727.975 to be precise) and my power consumption remains at 101W.

I am guessing that the FATAL error has someting to do with this!

OK... for an AMD XP processor I think the CPU governor you need is "powernow", not "acpi-cpufreq".

Try this... see if it loads without an error:

```

sudo modprobe powernow-k8

```

If it loads with no error, then put the line "powernow-k8" (without the quotes of course) into your "/etc/modules" file. Also, *remove* the line "acpi-cpufreq" if you put that in - as it is not working for you.

Now, reboot.

If all goes well, your CPU speed should now be under control (and controllable).

Good luck!

-- Roger

---

### Post by windependence on 2008-10-16
> **cariboo907 said:**
> Some times we get to involved in getting  things done the geeky way when there is a much easier solution. I know there is a setting in my BIOS that I believe it is called cool and quiet, it cuts down the cpu frequency by 50% until full power is needed then it ramps up to full speed. I don't use it on my desktop, but if my server had that feature I would use it. It takes a reboot and a couple of seconds and its done.

Jim

Indeed, this is what I was talking about. All of the major chips now have automatic CPU throttling built in. PowerNow is just an older version, and Intel also has it's version. All this stuff is not necessary and probably won't even be possible in a few years.

-Tim

AMD Channel Partner

---

### Post by Twizzle on 2008-10-16
windependence:

> Indeed, this is what I was talking about. All of the major chips now have automatic CPU throttling built in. PowerNow is just an older version, and Intel also has it's version. All this stuff is not necessary and probably won't even be possible in a few years.

But what if you don't have an up to date major chip (Athlon XP2200...) and your Bios does not have a setting to turn on cool and quiet or anything similar for Athlon chips? I certainly don't and this is a very helpful and to me useful post. I could go out and spend lots of money on the latest chip and motherboard to make sure it does do it all without me telling it to but 1) It would be a waste of money and I am trying to save some (all be it a small ammount granted) and 2) where is the fun in that? I jumped into the Linux world to experiment and learn what I could do. If I wanted boring let the OS / Computer control everything and think for me I would have stayed with Mr Gates...

Krupski:

I appreciate you help, so thank you but...

> Try this... see if it loads without an error:

Code:

sudo modprobe powernow-k8



I get the same error - No such device.

Just to play around I tried powernow-k6 to k8 with the same error. powernow-k5 was just 'Module powernow_k9 not found' as was k5.

Slight update.

If I run dmesg the last line is:

powernow-k8: Processor cpuid 681 not supported.

---

### Post by windependence on 2008-10-16
> **Twizzle said:**
> windependence:



But what if you don't have an up to date major chip (Athlon XP2200...) and your Bios does not have a setting to turn on cool and quiet or anything similar for Athlon chips? I certainly don't and this is a very helpful and to me useful post. I could go out and spend lots of money on the latest chip and motherboard to make sure it does do it all without me telling it to but 1) It would be a waste of money and I am trying to save some (all be it a small ammount granted) and 2) where is the fun in that? I jumped into the Linux world to experiment and learn what I could do. If I wanted boring let the OS / Computer control everything and think for me I would have stayed with Mr Gates...

Krupski:

I appreciate you help, so thank you but...



I get the same error - No such device.

Just to play around I tried powernow-k6 to k8 with the same error. powernow-k5 was just 'Module powernow_k9 not found' as was k5.

Slight update.

If I run dmesg the last line is:

powernow-k8: Processor cpuid 681 not supported.

OK if you are dtermined to do it, here is a great article on precisley what you want to do:

[http://saf.bio.caltech.edu/saving_power.html](http://saf.bio.caltech.edu/saving_power.html)

You should be aware that indeed, your Athlon XP 2200+ has throttling built in and consumes only 62.1 watts of power which isn't bad even by today's standards.

Your argument about buying new processors doesn't really wash if you were using this equipment other than for learning or testing purposes. I can buy a decent MSI board for $57, and outfit it with a AMD Athlon 64x2 4800 Boxed processor for another $70. Please note that this is the *server* forum, so you normally would only use this type of hardware on a home server, but even so, most all hardware since about 2000 has had some type of power management or CPU control.

As to the fun, there are so many fun things you can do with Linux/Unix, that it just seems trivial to me to be mucking around with sometihng that isn't going to give you much in the way of results. Of course, YMMV. ;)

-Tim

---

### Post by Krupski on 2008-10-16
> **Twizzle said:**
> Krupski:

I appreciate you help, so thank you but...
I get the same error - No such device.


Sorry my friend... I'm out of ideas. There ARE quite a few other CPU frequency governors that are CPU specific. One of them may work for you. You'll have to ask here or Google to find out what they are... I don't know all of them offhand.

Sorry I couldn't be of more help.

-- Roger

---

### Post by Krupski on 2008-10-16
> **windependence said:**
> As to the fun, there are so many fun things you can do with Linux/Unix, that it just seems trivial to me to be mucking around with sometihng that isn't going to give you much in the way of results [CPU throttling]. Of course, YMMV. ;)

-Tim

I disagree. I use acpi-cpufreq in my file server boxes and I notice that they run "quite a bit" cooler than if they were at full speed.

I have not measured actual temperature or watts, but I do know that at full speed the box and the air coming out of the power supply feel "warm" and when the governor is installed and activated, the box feels "ambient" and the air coming out of the PS feels "much less warm".

I'm an electrical engineer and I know that heat is the #1 killer of solid state devices.

Over time, individual atoms of the interconnects on the CPU (and memory) chips themselves can migrate from one point to another under electrostatic force. Heat makes this process happen faster.

Given enough time, the migrating metal atoms can actually build a sliver thin "bridge" between two interconnects and short out the section of the chip, obviously causing it to fail.

There is also thermal resistance between the actual chip and it's package. There is more resistance between the case and the heatsink.

If the heatsink is, say, 60 deg.C., the CPU package might be 62 degrees and the chip die itself 70 degrees.

This is the reason I tell everyone NOT to overclock their machines. Putting a huge liquid cooler on the CPU may keep the case cool, but the CPU die is still screaming in pain (and it's life is shortened due to accelerated electromigration).

Therefore, the reverse is obvious... UNDERCLOCKING and/or using a CPU governor not only saves money in the form of electricity, but it also greatly prolongs the life of the chips.

It's certainly not an exercise in futility.

-- Roger

---

### Post by Krupski on 2008-10-16
By the way... if anyone wants it, here's a tiny C program that displays the CPU core frequency (same as the script does).

Only difference is that it formats the clock speed as "1.230 GHz." instead of 1230000 (megahertz).

It's so simple anyone should be able to edit it to their liking.

```

/***********************************************************************/
/* cpus.c - apr 11, 2008 - Roger A. Krupski - krupski@acsu.buffalo.edu */
/*                                                                     */
/* This software is free and hereby released to public domain. You may */
/* use it, edit it, give it away, bundle it with other software. Do    */
/* anything you wish with it, but don't charge money for it. It's FREE */
/* There is no warranty. I hope it works properly for you. If not, you */
/* can edit it or delete it... but don't bug me about it.              */
/*                                                                     */
/*  Compile it as such: 'cc cpus.c -o cpus'                            */
/***********************************************************************/

#include <stdio.h>
#include <stdlib.h>
#define cores 4 /* how many files to look for */

FILE *infile; /* input file control structure */

char fname[BUFSIZ]; /* filename buffer */
char buffer[BUFSIZ]; /* buffer to read file into */
int n; /* how many to check for */
long int f; /* frequency read from file */
float ff; /* fractional cpu frequency display */

int main(int argc, char *argv[])
{
  if(argc != 1)
  {
    fprintf(stderr, "cpus: no command line options accepted\n");
    fflush(stderr); /* flush stderr */
    return(1); /* exit with error status */
  }

  for((n = 0); (n < cores); (n++)) /* check for 'cores' number of cpu cores */
  {
    sprintf(fname, "/sys/devices/system/cpu/cpu%d/cpufreq/cpuinfo_cur_freq", n); /* generate filename */
    infile = fopen(fname, "r"); /* try to open the file, readonly */

    if((infile == NULL) && (n == 0)) /* if FIRST file is not found... */
    {
      fprintf(stderr, "cpus: could not find the \"/sys/devices/system/cpu/cpu%d/cpufreq/cpuinfo_cur_freq\" file\n", n); /* error */
      fprintf(stderr, "      ...do you have a cpu frequency control daemon installed?\n");
      fflush(stderr);
      return(1);
    }

    if(infile != NULL) /* if file exists, get, format and print it's info */
    {
      fgets(buffer, (BUFSIZ-32), infile); /* read the file into buffer */
      fclose(infile); /* close the file RFN */
      f = atoi(buffer); /* convert cpu freq string into int 'f' */
      ff = (f / 1e6); /* convert megahertz to gighertz */
      fprintf(stdout, "CPU Core %d: %.3f GHz.\n", n, ff); /* display result to stdout */
      fflush(stdout); /* make sure it prints right away */
    }
  }
  return(0); /* exit with no error */
}

```


Enjoy!

-- Roger

---

### Post by eliphant0723 on 2009-02-21
Here is a link to pertaining info for those interested:

[http://rffr.de/acpi](http://rffr.de/acpi)

Includes info on controlling cpu scalling dynamically via cli.  :D

---

### Post by mehturt on 2009-08-19
Is there any reason for the file /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq to be root-readable only?

---

### Post by tipiglen on 2009-09-09
Krupski, (I hope this isn't the wrong place to ask)

> This is the reason I tell everyone NOT to overclock their machines. Putting a huge liquid cooler on the CPU may keep the case cool, but the CPU die is still screaming in pain (and it's life is shortened due to accelerated electromigration).

Therefore, the reverse is obvious... UNDERCLOCKING and/or using a CPU governor not only saves money in the form of electricity, but it also greatly prolongs the life of the chips.

My (laptop) machine (always running on a/c, due to shot battery) keeps shutting down due to apparent overheating.  I have both cores as wee panel icons, and I can prevent (mostly) the shutdowns by setting them both to minimum speed following login.  Is there a simple way I can set this option in the boot (etc/)scripts so I don't have to do it manually?

And it seems sometimes to be able to jump into "ondemand" despite my having manually opted out.

Your advice would be welcomed.


Salaam/Shalom/Shanthi/Peace
   Namaste -ed
[http://home2.btconnect.com/tipiglen/loveandpeace3.gif](http://home2.btconnect.com/tipiglen/loveandpeace3.gif)

---

### Post by tipiglen on 2009-09-19
Krupski,

Sorry!  I found my answer in your earliest couple of posts.  Set etc/rc.local to "powersave" and that seems to work, but it tells me it's set for "Userspace", so perhaps they're the same...

Thanks for your helpful suggestion, even if it took me a week to read back to it.

;-(

---

### Post by 9072997 on 2011-03-22
To all wondering what userspace is it allows applications that are not the kernel to adjust the CPU clock speed instead of deciding the appropriate speed with the kernel module

---

### Post by AMSlider on 2011-04-13
I took what folks have provided and made a small script I thought I'd share.  I call it cpufreq.ksh

```

#!/bin/ksh
##################################################
# set cpu governor and displays current frequency
##################################################

function usage
{
   echo "cpufreq.ksh [ powersave | performance | ondemand | conservative | userspace | display ]"
   echo ""
   echo "powersave - runs CPU at min clock always"
   echo "performance - runs CPU at full clock always"
   echo "ondemand - CPU clock jumps from low to high as needed"
   echo "conservative - CPU clock jumps up in small steps as needed"
   echo "userspace - let's users apps control the frequency"
   echo ""
   echo "display - prints out data about current cpu frequency"
   echo "        - use 'sudo watch --i=1 ./cpufreq.ksh display' to monitor it every second"
   exit 1
}

case "$1" in

   powersave | performance | ondemand | conservative | userspace )
      for cpunum in `ls -d /sys/devices/system/cpu/cpu[0-9]`
      do
         cpunum=`basename $cpunum`
         /usr/bin/test -e /sys/devices/system/cpu/${cpunum}/cpufreq/scaling_governor && /bin/echo $1 > /sys/devices/system/cpu/${cpunum}/cpufreq/scaling_governor
      done
      ;;

   display )
      for cpunum in `ls -d /sys/devices/system/cpu/cpu[0-9]`
      do
         cpunum=`basename $cpunum`
         curfreq=`/bin/cat /sys/devices/system/cpu/${cpunum}/cpufreq/cpuinfo_cur_freq`
         maxfreq=`/bin/cat /sys/devices/system/cpu/${cpunum}/cpufreq/cpuinfo_max_freq`
         /usr/bin/test -e /sys/devices/system/cpu/$cpunum/cpufreq/cpuinfo_cur_freq && /bin/echo "Core $cpunum: `expr $curfreq / 1000 ` MHz of `expr $maxfreq / 1000` MHz"
      done
      ;;

   * )
      usage
      ;;

esac
exit 0

```

---

