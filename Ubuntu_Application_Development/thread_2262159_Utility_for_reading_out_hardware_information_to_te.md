---
title: "Utility for reading out hardware information to terminal"
date: 2015-01-23
forum: Ubuntu Application Development
---

### Post by veddox on 2015-01-23
Hello everyone,

recently I've been a bit frustrated when I was working in a tty on my laptop, and all of a sudden it dies on me for lack of battery - terminal doesn't warn you when you're running low, after all. I then discovered that there was a lot of hardware information stored in the /proc directory, including the current state of the battery. However, I'm too lazy to have to navigate to /proc/acpi/battery/.../state every time I want to check my battery condition from terminal, and I have been wanting a simple program to read out hardware information from commandline anyway.

To cut the story short, I decided to scratch my own itch and wrote 'comp', a small C++ utility for doing just that. If you are interested, you will find the code on [Launchpad]("https://launchpad.net/comp"). It is a *very* small program, but somebody else might find it useful too...

If you decide to have a look at it, I would value some feedback :-)

---

### Post by tgalati4 on 2015-01-23
There are a lot of utilities for reading /proc:

> tgalati4@Mint17 ~ $ acpitool -B
  Battery #1     : present
    Remaining capacity : unknown, 96.57%
    Design capacity    : 4000 mA
    Last full capacity : 2537 mA, 63.42% of design capacity
    Capacity loss      : 36.58%
    Present rate       : 0 mA
    Charging state     : Unknown
    Battery type       : Li-ion 
    Model number       : GARDA71
    Serial number      : 1315


and

```
lshw
```

For "list hardware".

and

```
lspci
lsusb
```

But, you are correct, if you are not in a graphical environment, all of the usual notifications are not available, so your tool is indeed useful.

---

### Post by ajgreeny on 2015-01-23
I am using a desktop at the moment so can't check this, but it should be possible to make an alias for the command **cat /proc/acpi/battery/.../state** as you show above to give you the information you want with a simple command such as **bat**.

Add the line ```
alias bat='cat /proc/acpi/battery/.../state'
``` to the ~/.bashrc file in your home. Adding that will mean that typing **bat** either at a tty or a GUI terminal will report the info in that file, which incidentally is a virtual file and appears empty if using gedit or any other GUI text editor.

Perhaps the ```
acpitool -B
``` command shown above reports the exact same file content in which case you can make the alias for that command instead of my **cat /proc/acpi/battery/.../state**

EDIT:
Sorry, but having looked at the archive of your **comp** utility it appears I am teaching you to suck eggs, and that you probably already know everything I have said here.  I leapt in too quickly with my answer without looking more closely at your full post and the links in it.

---

### Post by tgalati4 on 2015-01-23
It's a nice utility, but my battery status is not kept in the usual place.  In fact I don't know where it is!

> tgalati4@Mint17 ~/Projects/Comp_Utility $ comp battery
ERROR: Could not find or access /proc/acpi/battery/BAT1/state!
ERROR: Could not find or access proc/acpi/battery/BAT0/state!


I'm running Linux Mint MATE 17 (based on 14.04).

---

### Post by veddox on 2015-01-24
@ajgreeny: Yes, I had thought of the alias idea ;-) I'm currently working on a script that is supposed to work in the background and alert the user automatically from terminal if the battery levels are getting low.

@tgalati4: Thanks for adding the error output - I just noticed a rather stupid bug: if you look at the second error, it refers to a 'proc' directory instead of to '/proc'... I fixed that, you can get the latest code from the Launchpad repository.

If 'comp battery' still doesn't work for you with that fix, then I'm a bit baffled. I checked on a laptop with Mint 13, that had its battery information stored in /proc/acpi/battery/BAT0/state - my laptop with Ubuntu 14.04 has it in /proc/acpi/battery/BAT1/state. If you do find out where your battery files are, could you let me know? (Either here or via a Launchpad bug report.) Thanks!

---

### Post by tgalati4 on 2015-01-24
This laptop is an Acer Extensa and I don't have much in my /proc/acpi directory:

> tgalati4@Mint17 /proc/acpi $ ls
button  wakeup


And I still have not found the battery file.

---

### Post by veddox on 2015-01-26
Discovered in a post by [nixCraft]("http://www.cyberciti.biz/faq/linux-laptop-battery-status-temperature/") that your battery file may not be in /proc at all. Check the /sys directory, more specifically: /sys/class/power_supply; if you find anything there.

---

### Post by tgalati4 on 2015-01-26
Yes, that is where it is:

> tgalati4@Mint17 /sys/class/power_supply $ ls -la
total 0
drwxr-xr-x  2 root root 0 Jan 16 08:55 .
drwxr-xr-x 57 root root 0 Jan 16 08:55 ..
lrwxrwxrwx  1 root root 0 Jan 16 08:55 ADP1 -> ../../devices/platform/ACPI0003:00/power_supply/ADP1
lrwxrwxrwx  1 root root 0 Jan 26 16:36 BAT0 -> ../../devices/LNXSYSTM:00/device:00/PNP0A08:00/device:28/PNP0C09:00/PNP0C0A:00/power_supply/BAT0
tgalati4@Mint17 /sys/class/power_supply $ cat BAT0
cat: BAT0: Is a directory
tgalati4@Mint17 /sys/class/power_supply $ cd BAT0
tgalati4@Mint17 /sys/class/power_supply/BAT0 $ ls
alarm     charge_full         charge_now   cycle_count  manufacturer  power    serial_number  subsystem   type    voltage_min_design
capacity  charge_full_design  current_now  device       model_name    present  status         technology  uevent  voltage_now
tgalati4@Mint17 /sys/class/power_supply/BAT0 $ cat status
Unknown
tgalati4@Mint17 /sys/class/power_supply/BAT0 $ cat voltage_now
12318000

(Which I presume is 12.3 Volts.)


---

