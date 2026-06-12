---
title: "Ubuntu server &quot;built in&quot; temperature monitor differs from lm-sensors"
date: 2021-12-16
forum: Server Platforms
---

### Post by Eazy© on 2021-12-16
Hi!

When I log in to my Ubuntu server with ssh it shows the temperature. I installed lm-sensors. lm-sensors say my cpu is 33c and Ubuntus "built in" says 47c. Which one is correct?
(When I installed lm-sensor I did modprobe nct6775 and then sensors-detect.)

Also wonder, how does Ubuntus "built in" fetch the temperature? What package is used?

---

### Post by QIII on 2021-12-16
Which "built in" temp sensor are you talking about?

Those sensors are generally on the motherboard or other hardware.  All the OS does is gather what is reported.

What is the model of the processor?

---

### Post by ameinild on 2021-12-17
Please include the output of commands or screenshots where you see these temperatures. This will make it easier for anyone here to help decipher the numbers.

---

### Post by MAFoElffen on 2021-12-17
> **Eazy© said:**
> Hi!

When I log in to my Ubuntu server with ssh it shows the temperature. I installed lm-sensors. lm-sensors say my cpu is 33c and Ubuntus "built in" says 47c. Which one is correct?
(When I installed lm-sensor I did modprobe nct6775 and then sensors-detect.)

Also wonder, how does Ubuntus "built in" fetch the temperature? What package is used?
Would you like the short summarized version or longer, detailed technical answer?

Both temperatures you are referring to (MOTD and lm-sensors) are correct. You just need to understand which temp is reported by what, and what they mean.

The Temp reported by the MOTD when you log in via SSH, is the highest temperature logged in the stats. The Temp in lm-sensors is what it is currently. That is why the temp reported by the MOTD was noted as being higher.

MOTD is a series of scripts, which calls other scripts to put together the information. To short-cut to the chase, Python script 'sysstats.py' uses this function
```

def get_thermal_zones(thermal_zone_path=None):
    if thermal_zone_path is None:
        if os.path.isdir("/sys/class/thermal"):
            thermal_zone_path = "[COLOR=#ff0000]/sys/class/thermal[/COLOR]"
        else:
            thermal_zone_path = "[COLOR=#ff0000]/proc/acpi/thermal_zone[/COLOR]"
    if os.path.isdir(thermal_zone_path):
        for zone_name in sorted(os.listdir(thermal_zone_path)):
            yield ThermalZone(thermal_zone_path, zone_name)

```
The files contained in the paths shown in that code in red, contain snapshot temperature statistics stored for the CPU...

Is that enough of an explanation?

So, yes... Both temperatures are correct. It's just a difference of what is current at this moment (the last recorded temp), or what was the highest temperature recorded since uptime...

---

### Post by Eazy© on 2021-12-17
> **MAFoElffen said:**
> Would you like the short summarized version or longer, detailed technical answer?

Both temperatures you are referring to (MOTD and lm-sensors) are correct. You just need to understand which temp is reported by what, and what they mean.

The Temp reported by the MOTD when you log in via SSH, is the highest temperature logged in the stats. The Temp in lm-sensors is what it is currently. That is why the temp reported by the MOTD was noted as being higher.

MOTD is a series of scripts, which calls other scripts to put together the information. To short-cut to the chase, Python script 'sysstats.py' uses this function
```

def get_thermal_zones(thermal_zone_path=None):
    if thermal_zone_path is None:
        if os.path.isdir("/sys/class/thermal"):
            thermal_zone_path = "[COLOR=#ff0000]/sys/class/thermal[/COLOR]"
        else:
            thermal_zone_path = "[COLOR=#ff0000]/proc/acpi/thermal_zone[/COLOR]"
    if os.path.isdir(thermal_zone_path):
        for zone_name in sorted(os.listdir(thermal_zone_path)):
            yield ThermalZone(thermal_zone_path, zone_name)

```
The files contained in the paths shown in that code in red, contain snapshot temperature statistics stored for the CPU...

Is that enough of an explanation?

So, yes... Both temperatures are correct. It's just a difference of what is current at this moment (the last recorded temp), or what was the highest temperature recorded since uptime...

Yes, that is enough of an explanation. Just what i wanted to know. Thank you!

For you who wanted to know what I'm talking about:
[http://www.bronsaldersvagen.se/Eazy/temp_ub.png]("http://www.bronsaldersvagen.se/Eazy/temp_ub.png")

---

### Post by Doug S on 2021-12-17
> **MAFoElffen said:**
> So, yes... Both temperatures are correct. It's just a difference of what is current at this moment (the last recorded temp), or what was the highest temperature recorded since uptime...

Disagree. They are both current at the moment they are sampled. The difference is the higher amount of code executed before the sample is taken during the the logon process causing a momentary increase in processor package temperature.

One way to demonstrate this difference is to read the temperature directly via two methods: As root; And with via a sudo prefix, where the sudo code is rather extensive:

```
root@s19:/home/doug/c# rdmsr -a --bitfield 22:16 -u 0x1B1
65
65
65
65
65
65
65
65
65
65
65
65
root@s19:/home/doug/c# exit
exit
doug@s19:~/c$ sudo rdmsr -a --bitfield 22:16 -u 0x1B1
57
57
57
57
57
57
60
60
60
60
60
60
```Now, the actual temperature is 100 (for my processor) - those numbers, or 35 degrees and 43 degrees. In the second case one can already observe the temperature reducing from the "sudo" overhead for the last 6 of 12 CPU measurements.

Another way to demonstrate the issue is to monitor processor package temperature on one terminal, while logging on on another:

```
doug@s19:~/c$ [COLOR="#FF0000"]sudo turbostat --Summary --quiet --show PkgTmp --interval 0.1[/COLOR]
PkgTmp
34  [COLOR="#FF0000"]<<< Why no sudo blib? Because it is 0.1 seconds later, and it has dissipated.[/COLOR]
34
35
34
34
34
34
34
34
34
34
35
35
35
34
35
35
34
42   [COLOR="#FF0000"]<<<<[/COLOR]
51   [COLOR="#FF0000"]<<<< Logged onto another ssh session.[/COLOR] 
37
36
35
35
34
35
35
35
```

---

### Post by MAFoElffen on 2021-12-18
@Doug S... I was wrong and you were right... But with a caveat... (I read the doc's further...) MOTD is at time of login, but is not specific to just CPU or one core...

Quote:
> 
In short, the temperature reported in MOTD is the highest temperature [COLOR=#ff0000]of all thermal zones[/COLOR] reported by Sysfs API, *at login*. For more comprehensive temperature reporting you still want to use sensors...

ANd yes, it is a lot more code in getting that answer. Just for assembling the MOTD, at least 4 scripts.

---

### Post by Doug S on 2021-12-18
@MAFoElffen : Agreed. And turbostat does the same, where "package temperature" is always the highest of all core temperatures. My manual measurements, via direct MSR read were not, so I just read all CPU's (at 2 CPUs per core).

---

### Post by Eazy© on 2021-12-19
Thank you for looking in to this! 

I could not test with turbostat. Seems it is a part of collectd-core but I could not manage it to work.

If i run watch -n 2 sensors (lm-sensors) and then login with another ssh session, the temperature does not raise.

I don't know what is intended by showing the temperature when you log in. If it is a benchmark to show the temps at full speed I could understand why its included as a info (I hope this is the reason).

If the reason to show average temperature, then it is just wrong to show it. If the way to collect the temperature is so hard on the system then it is useless. Again, I hope it is the first reason.

---

### Post by MAFoElffen on 2021-12-19
I'm thinking it is just generic info on current stats, with uptime, temp and upgrades. What is there, as default, is just an example MOTD.

On mine (my servers), I changed my MOTD to show other things... such as (of all things), the current weather, root mail notifications on that server, and some RSS feeds. I already had reports auditing on all the stats of all servers, and warnings on those servers triggered to go to emails on an admin email account receiving those alerts. That, and on my management console, I wrote a Conky widget to show real-time stats and warnings of critical systems... Then 'alerts' that sent to XMessage pop-ups to that Management Console. That includes both physical and virtual machines... and networks.

So, for MOTD's... I found then uninformative, boring, containing info I already had. Consequently, I made my own MOTD's more of an entertainment and FYI.

I know some, who made all their own MOTD's such an ominous warning to others that they were in the wrong place. Example: That they were just infected by a 'digital black death' that they will not recover from... Or a MAC Address/IP Geo back-trace to show their current 'location', to show that it might not be a good idea to be there doing something they are not authorized for.

Yes, be creative. Might as well make it fun right? Life is too short not to have some kind of sense of humor.

---

### Post by Eazy© on 2021-12-19
Did some changes to motd myself and added lm-sensors.

[IMG]http://www.bronsaldersvagen.se/Eazy/motd_stat.png[/IMG]

Wold have looked better if the fan info was on the right of cpu temperature, but don't know how to do that.
The reason temperature info is important to me is that my "server" is on a shelf in a wardrobe (with a fan on the side on it).

---

### Post by Doug S on 2021-12-19
> **Eazy© said:**
> I could not test with turbostat. Seems it is a part of collectd-core but I could not manage it to work.

If i run watch -n 2 sensors (lm-sensors) and then login with another ssh session, the temperature does not raise.
What is your processor make and model? turbostat works on most recent Intel processors and some recent AMD processors. I always thought is was part of the "linux-tools-common" package, but don't really know. I use the most recent upstream kernel version of turbostat, including some yet to be released patches.

Yes, I would expect at two seconds per sample interval with lm-sensors to probably not detect any rise in processor package temperature due to a log on event. Based on the below data, where a logon temperature event spans 0.2 seconds, I would estimate the probability at ~10%. I.e. that you would detect a peritbation in Temperature due to a login event at 1 in 10 attempts to do so.

```
doug@s19:~/tmp/system-info$ sudo /home/doug/temp-k-git/linux/tools/power/x86/turbostat/turbostat --Summary --quiet --show PkgTmp --interval 0.01
PkgTmp
35
35
35
35
35
39  [COLOR="#FF0000"]Event begin. Log in on another SSH session.[/COLOR]
36
36
45
48
48
49
47
49
49
50   [COLOR="#FF0000"]<<< Event begin + 0.1 seconds[/COLOR]
51
50
50
49
46
46
41
48
43
39   [COLOR="#FF0000"]<<< Event begin + 0.2 seconds. Event End[/COLOR]
38
37
37
36
36
36
40
50
50
37
37
36
36
36
36
36
36
```I check to see if turbostat can actually run at 0.01 seconds per sample:

```
$ time sudo /home/doug/temp-k-git/linux/tools/power/x86/turbostat/turbostat --Summary --quiet --show PkgTmp [COLOR="#FF0000"]--interval 0.01 --num_iterations 2000[/COLOR]
PkgTmp
35
35
35
35
...
36
[COLOR="#FF0000"]real    0m21.352s[/COLOR]
user    0m0.078s
sys     0m0.316s
```Or an actual sample rate of 0.0107 Seconds per sample (Close enough).

As for the usefullness or accuracy or whatever of the MOTD reported temperature: I don't normally even notice it, but took these samples while working on this thread:

```

  System load:     0.0                 Temperature:          50.0 C
  System load:    3.49                Temperature:          69.0 C
  System load:    6.39                Temperature:          71.0 C
  System load:    8.84                Temperature:          72.0 C
  System load:  10.24                Temperature:          75.0 C  [COLOR="#FF0000"]<<< My system throttles at 75 degrees, and the average temp would not differ from the MOTD reported temperature.[/COLOR]
  System load:  11.5                  Temperature:          74.0 C
  System load:    8.34                Temperature:          57.0 C
  System load:    2.46                Temperature:          57.0 C   [COLOR="#FF0000"]<<< Retained heat in coolant (water cooled). Actual average ~40 degrees.[/COLOR]
  System load:    0.42                Temperature:          56.0 C

```

---

### Post by Doug S on 2021-12-19
> **Eazy© said:**
> Did some changes to motd myself and added lm-sensors. How did you do that? I would like to try adding a temperature reading also, as I would have expected less discrepancy between the two measurements with your special MOTD.

---

### Post by MAFoElffen on 2021-12-19
> **Eazy© said:**
> Wold have looked better if the fan info was on the right of cpu temperature, but don't know how to do that.

In your script, instead of displaying directly to stdout, assign it temporarily to a variable. Since Temp is 5 lines and Fans is 4 lines, add a line after the Fan output (appended to the end of the variable) so it is an equal line count for both. Pipe the variable through 'column -e'. The '-e' flag will respect blank lines. Since using 'column' as default, it will divide the output in half, displaying down then to the next column...

If you post a snippet of your code, I'll give you an example...

EDIT--
Thought about your concern of it being in a closet and heat... More useful for you, since it is remote, unseen, and you might want to  see the stats more often then just when you ssh into it, might be to use  'glances' in client/server mode. it uses lm-sensors... But you could  see your stats on your local/remotely, in real-time (constantly).

---

### Post by Doug S on 2021-12-19
> **Doug S said:**
> How did you do that? I would like to try adding a temperature reading also, as I would have expected less discrepancy between the two measurements with your special MOTD.O.K. I figured out how, and added this:

```
doug@s19:~$ cat  /etc/update-motd.d/93-doug-test
#!/bin/sh

#
# What is the Processor package temperature.

/home/doug/temp-k-git/linux/tools/power/x86/turbostat/turbostat --Summary --quiet --show PkgTmp --interval 0.001 --num_iterations 1
```in multiple spots:
```
doug@s19:~$ ls -l /etc/update-motd.d
total 68
-rwxr-xr-x 1 root root 1220 Dec  5  2019 00-header
-rwxr-xr-x 1 root root 1157 Dec  5  2019 10-help-text
-rwxr-xr-x 1 root root  191 Dec 19 15:12 [COLOR="#FF0000"]15-doug-test[/COLOR]
lrwxrwxrwx 1 root root   46 Apr 16  2021 50-landscape-sysinfo -> /usr/share/landscape/landscape-sysinfo.wrapper
-rwxr-xr-x 1 root root 5023 Aug 17  2020 50-motd-news
-rwxr-xr-x 1 root root  191 Dec 19 15:12 [COLOR="#FF0000"]65-doug-test[/COLOR]
-rwxr-xr-x 1 root root   96 Feb  2  2020 85-fwupd
-rwxr-xr-x 1 root root  106 May 11  2021 88-esm-announce
-rwxr-xr-x 1 root root  218 Dec  5  2019 90-updates-available
-rwxr-xr-x 1 root root  112 May 11  2021 91-contract-ua-esm-status
-rwxr-xr-x 1 root root  374 Jul 17  2020 91-release-upgrade
-rwxr-xr-x 1 root root  165 Dec 16  2019 92-unattended-upgrades
-rwxr-xr-x 1 root root  191 Dec 19 15:12 [COLOR="#FF0000"]93-doug-test[/COLOR]
-rwxr-xr-x 1 root root  129 Dec  5  2019 95-hwe-eol
-rwxr-xr-x 1 root root  111 Nov 13  2018 97-overlayroot
-rwxr-xr-x 1 root root  142 Dec  5  2019 98-fsck-at-reboot
-rwxr-xr-x 1 root root  144 Dec  5  2019 98-reboot-required
```And got this:
```
C:\Users\dsmyt>ssh doug@s19
doug@s19's password:
Welcome to Ubuntu 20.04.3 LTS (GNU/Linux 5.4.0-91-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage
[COLOR="#FF0000"]PkgTmp
39[/COLOR]

  System information as of Sun 19 Dec 2021 03:22:34 PM PST

  System load:  0.0                 Temperature:          [COLOR="#FF0000"]49.0 C[/COLOR]
  Usage of /:   24.4% of 915.40GB   Processes:            227
  Memory usage: 3%                  Users logged in:      1
  Swap usage:   0%                  IPv4 address for br0: 192.168.111.136

[COLOR="#FF0000"]PkgTmp
40[/COLOR]

26 updates can be applied immediately.
18 of these updates are standard security updates.
To see these additional updates run: apt list --upgradable

[COLOR="#FF0000"]PkgTmp
38[/COLOR]
Your Hardware Enablement Stack (HWE) is supported until April 2025.

Last login: Sun Dec 19 15:13:15 2021 from 192.168.111.122
```Which is not all that insightful.

---

### Post by Eazy© on 2021-12-20
I did it like this /etc/update-motd.d/89-custom:
```

#!/bin/sh
echo 
echo 
echo "CPU Temperature:"
/usr/bin/sensors | grep 'CPU Core' | cut -b 1-22
echo
echo "System Fans:"
/usr/bin/sensors | grep 'Fan' | cut -b 1-22
echo

```

Made it simple like this because I don't have the knowledge about scripting. Think this have to do.

Tried glances, and it was nice, but I wanted to rename the sensors, but didn't find any info if it was possible to do. Also tried netstat, but that was in my opinion too resource-demanding (it is really not, just me being picky).

---

### Post by TheFu on 2021-12-20
Different hardware has different support for all the different temperature locations. This is motherboard, chipset and CPU specific.  

In general, Intel has much better support than AMD.  Each core on an Intel CPU will report a temperature, while only 1 temperature might be reported by an AMD CPU.  

On my B450 Ryzen motherboards, I think I only get 1 other temperature report, though the motherboards have 3 more ... plus some drive cages reported temperature and fan speeds. Alas, I've been unable to get those without extra effort.  Saw a few months ago that better reporting was coming in future kernels for AMD CPUs and motherboards. Someday I'll actually run those.  For now, I think getting the reports requires pulling some code of github, configuring it and compiling, then installing the module for sensors to access.

Wrote a script to gather temperatures ... here's the function in the bash script:
```
# #############################
function Temperatures(){
   Logging "Temperature Overview"

   Logging "System Temperatures - $SENSORS"
   $SENSORS |$EGREP -v '^in|^Vbat|^3VSB|^intrusion' |$TEE -a $LOG

   Logging " smartctl Disk Temperatures"
   for disk in $(sudo fdisk -l | $EGREP "Disk /dev" \
      | $EGREP -v '/dev/loop|/dev/mapper' | $AWK '{ print $2 }' \
      | cut -d: -f1 ); do
      echo "Disk: $disk"
      sudo smartctl -x $disk | $EGREP "^(Temperature:|Current Temperature:)" | \
                                        $TEE -a $LOG
   done
}
```

And some output. This is a B450 with a Ryzen 5600G:
```
INFO: System Temperatures - /usr/bin/sensors 
nvme-pci-0900
Adapter: PCI adapter
Composite:    +35.9°C  (low  = -273.1°C, high = +84.8°C)
                       (crit = +84.8°C)
Sensor 1:     +35.9°C  (low  = -273.1°C, high = +65261.8°C)
Sensor 2:     +41.9°C  (low  = -273.1°C, high = +65261.8°C)


INFO:  smartctl Disk Temperatures 
Disk: /dev/nvme0n1
Temperature:                        36 Celsius
Disk: /dev/sda
Current Temperature:                    33 Celsius
Disk: /dev/sdb
Disk: /dev/sdc
Current Temperature:                    34 Celsius
Disk: /dev/sdf
Current Temperature:                    36 Celsius
Disk: /dev/sdd
Disk: /dev/sde
Current Temperature:                    33 Celsius
Disk: /dev/sdg
```

I seriously doubt this system has ever been -273.1°C or +65261.8°C as reported.  Also, we can see that not all disks provide temperature information. This is probably more about using USB connections and smartctl not getting correct access to the drive hardware.  The disks reporting Temperatures are eSATA or SATA connected.

---

### Post by MAFoElffen on 2021-12-20
@Doug S @TheFu

I'm here happily remembering fondly the last time all three of us got distracted for 'days' playing and experimenting with Temperature readings...

Since then, when I was working as a Warranty Service Tech for Lenovo, HP and Dell... Dell Alienware machines... Intel and Ryzen, have so 11 'different" temp sensors on their boards. CPU, GPU, Disk, and a multitude of other chips... But the big difference which them, is that they have monitoring software that keeps track of them all.

One of the biggest problems I say in that, is that they were 'too' intelligent. It would tell you when there was a problem, and what needed to be replaced to correct it... But it wasn't child proof. Literally meaning, it did not factor in that children may be using it and not know better than to not sit there using it with a blanket or such over the intake or output venting... I had 2 service calls that I was called out to replace system Boards... but they were fine. They had cooled back down, after not having enough airflow... And the 'parents' told me what had happened.

---

