---
title: "[SOLVED] Slow bootup time"
date: 2008-05-10
forum: System76 Support
---

### Post by glacialfury on 2008-05-10
Maybe this is my unfamiliarity with Ubuntu, but the Serval Performance (serp4) is taking 3-5 minutes to boot the system.  It reaches the screen with the Ubuntu logo and the loading bar, seems to hang toward the beginning of the loading bar, and then again at the end.  If I let it sit for 3-5 minutes, it will eventually reach the login screen; however, surely Ubuntu doesn't take this long to boot on a system of this power? 

Is there a way I can see what's going on during the loading to see if it's having a problem with something?  I've had bystanders ask me why a new computer is freezing on startup, it takes so long.

---

### Post by riseringseeker on 2008-05-10
> **glacialfury said:**
> Maybe this is my unfamiliarity with Ubuntu, but the Serval Performance (serp4) is taking 3-5 minutes to boot the system.  It reaches the screen with the Ubuntu logo and the loading bar, seems to hang toward the beginning of the loading bar, and then again at the end.  If I let it sit for 3-5 minutes, it will eventually reach the login screen; however, surely Ubuntu doesn't take this long to boot on a system of this power? 

Is there a way I can see what's going on during the loading to see if it's having a problem with something?  I've had bystanders ask me why a new computer is freezing on startup, it takes so long.

Hit ALT F5 as soon as the progress bar appears, or the grub menu thing goes away.

---

### Post by jdb on 2008-05-10
I have a Daru2 & i just timed it.
From the time I hit the power button until I get the login prompt is 40 seconds.

If you edit /boot/grub/menu.lst & remove the splash boot option you can see what is going on while it boots.

It's on a line that looks like this:

kernel	/boot/vmlinuz-2.6.24-16-generic root=UUID=394bb8f6-fdc0-415b-928d-ac0238ae0dc6 ro quiet splash

Just remove the word splash on the end.

jdb

---

### Post by unutbu on 2008-05-10
It would not hurt to remove the 'quiet' option either.

---

### Post by glacialfury on 2008-05-11
Thank you for the replies, I will try them tomorrow.  The slow boot-up happens intermittently, about half the time.  The other half it does boot in about 40 seconds.  

Does Ubuntu store some updates for the next boot cycle?

---

### Post by jdb on 2008-05-11
There is info on each partition about the last time it was checked and how many times it's been mounted since it was last checked.
Depending on how it's optioned, a partition will be checked every so many mounts or every so many days.
If a partition is 100 gigs or more the check can take a while.
If the splash boot option is removed you can see when a partition is being checked and there will be a progress bar.

The options can be dumped or set.

to see the options for sda1:

sudo -h dumpe2fs /dev/sda1

To set it to be checked every 10 days:

sudo tunesfs -c 0 -i 10 /dev/sda1

To learn more about these commands:

man dumpe2fs
man tune2fs

jdb

---

### Post by unutbu on 2008-05-11
jdb's idea is very good, but there were typos in the commands he gave. They should be

```
sudo dumpe2fs **-h** /dev/sda1
```

(assuming your linux partition is /dev/sda1), and
```

sudo **tune2fs** -c 0 -i 10 /dev/sda1
```

---

### Post by jdb on 2008-05-12
unutbu,

Thanks for the corrections. :)

jdb

---

### Post by glacialfury on 2008-05-12
I started by hitting Alt-F5 after the GRUB menu to observe.  It began going through loading processes, then ran FSCK on /dev/sda1, finished very quickly, then began running FSCK on /dev/sda3 with the following results:

Around 0.2%, it seemed to hang for about a minute; around 0.4% it hanged for another minute or two.  Often it would seem like it wasn't doing anything as it progressed very slowly.  If I tapped the left alt key, it would progress; if I held the button down, it increased the overall pace of the progress meter by more than double.

Around 44-45%, it stopped again, this time for more than five minutes.  Eventually it gave the following output:

[586.899674] iwl4965: Microcode SW error detected. Restarting 0x82000000.
[589.901810] iwl4965: Can't stop Rx DMA.

Progress then continued very slowly, with several instances of hanging for a number of minutes.  Eventually it finished, and brought me to the Ubuntu login screen.

The entire booting process during this took approximately 20 minutes.

---

### Post by jdb on 2008-05-12
I don't know how big your disk is but that is way longer than I've ever seen a partition check take.

I think those messages from the wireless hardware are the problem but I'm no expert on networking.  You might see something from the output of dmesg.

I've had computers bog down for a loooong time when some code was waiting for some network event it wasn't getting.

I think someone here is going to be able to help you out with this one.

jdb

---

### Post by unutbu on 2008-05-12
A quick google search on "iwl4965: Can't stop Rx DMA" brings up

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/149214](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/149214)

Although this may be an issue for you, it -- in and of itself --  does not seem to cause all machines to be slow at boot time.

I think the next thing to do is look at the output of `dmesg` and also the log files /var/log/messages and /var/log/syslog.

These three give copious output. Look for error messages and post them here. Also, the 'messages' and 'syslog' files have time/date stamps, so you can tell on what lines a lot of time has been consumed.

The kernel writes to 'messages' and 'syslog' during the boot process, and also during normal operation. To find the logs for the latest boot, open the file up in a text editor, go to the *end* of the file, and search backwards for the string 

```
: restart
```

---

### Post by thomasaaron on 2008-05-12
The previously mentioned bug has a couple of workarounds.
See the post with this heading...
Anton Khokhlov  wrote on 2007-12-20:  (permalink)  

This bug report...
[https://bugs.launchpad.net/linux/+bug/200509](https://bugs.launchpad.net/linux/+bug/200509)
... also offers some suggestions.

I'm guessing the computer will NOT do this if your wireless switch is turned off or if you are booting with an ethernet cable connected, right?

If this is the case, see if running...
sudo apt-get --reinstall install linux-backports-module-hardy
...fixes the problem.

---

### Post by glacialfury on 2008-05-15
**@thomasaaron:**

```
sudo apt-get --reinstall install linux-backports-module-hardy
``` gives me the following:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-module-hardy
```

======================================================================

**@unutbu:**

Here are the files - I apologize, not being very familiar with linux, I'm not quite sure what to look for in an error.

[dmesg]("http://glacialsystems.com/storage/output/dmesg.txt")
[messages]("http://glacialsystems.com/storage/output/messages.txt")
[syslog]("http://glacialsystems.com/storage/output/syslog.txt")

Meanwhile, I will try the fix listed in the bug report - I also have had some problems with the wireless shutting off on the laptop after using it for awhile, while it continues to work on my other PCs.

---

### Post by unutbu on 2008-05-15
Your dmesg and /var/log/messages -- at least to my inexperienced eyes -- look very clean. Your syslog.txt looks like it has been freshly rotated (too short). If you wish, post /var/log/syslog.0 and I (and hopefully others) will take a look at it. 

Because of the cleanliness of your dmesg and messages, however, I'm beginning the think the problem may not be apparent from the log files. 

I'm also wondering if maybe the fact that you could make the progress bar go faster by pressing your ALT key is a clue. Is it just the ALT key, or will any key work? Could this be a sign that there is an IRQ problem?

Please post 

```
cat /proc/interrupts
```

Finally, regarding thomasarron's suggestion, try

```
sudo apt-get --reinstall install linux-backports-modules-hardy
```

---

### Post by glacialfury on 2008-05-18
Just an update - I've been working for several days and have not had a chance to experiment with other solutions.  It may also suffer from the wifi-dropping, which it did after several hours of continual bittorrent use, and maybe if that gets resolved - as described in the bug reports you showed me - the other problem may resolve as well.

I will work on it some more Monday and post the results.  Thank you for your patience, and for your help.

---

### Post by eyecreate on 2008-05-18
I don't know how similar my problem is to this, but I also will have the loading hang at times unless I push a key. It does it for normal boot up and can be seen happening when the HD light stops blinking. Pushing the key(usually ALT of CTRL) makes it continue for a bit. This also happens when it does disk checks. It pauses disk checks until I hit a key, which makes it continue. I have a serp4 also. I have not too my knowledge had a wireless problem, though, as the key press thing seems to happen even if my wireless is off.

---

### Post by glacialfury on 2008-05-20
I haven't had the boot speed problem lately, although that appears like it will only occur during a disk check.  The wireless bit of it though, as mentioned in the bug reports, I've got a little more info on.

I recall now that the first time I lost the wifi connection on the laptop was after using Transmission for several hours.  I know some of the users have mentioned they lost their hifi after heavy traffic on the network, and this could have been the case with Transmission.

---

### Post by thomasaaron on 2008-07-16
ATTEN: EYECREATE AND GLACIALFURY

What CPU are you using?
```
cat /proc/cpuinfo  #will give you the answer.
```

---

### Post by eyecreate on 2008-07-16
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     T8100  @ 2.10GHz
stepping	: 6
cpu MHz		: 800.000
cache size	: 3072 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm ida
bogomips	: 4193.45
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     T8100  @ 2.10GHz
stepping	: 6
cpu MHz		: 800.000
cache size	: 3072 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm ida
bogomips	: 4189.46
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

---

### Post by Naenyn on 2008-07-17
Greets!

I am also having this same problem with my Serval Performance I received last week. still trying to diagnose the issue, but it is definitely related to the iwl4965 microcode thing. I've tried the solutions in the threat here, but haven't had any success as of yet.

Its awfully frustrating, to say the least. Hopefully we can figure things out quickly. :confused:

-naenyn

---

### Post by unutbu on 2008-07-17
I hear System 76 customer support is excellent.
Have you contacted them about the problem?

---

### Post by Naenyn on 2008-07-17
That's why I'm here posting in the System76 Support forum .. on an issue that others have encountered. ;)

I have also sent in an email directly to support tho.

---

### Post by thomasaaron on 2008-07-17
NOTICE: Please do not make any further tweaks to your system to fix the slow booting issue. We've duplicated the problem in our shop and are working now to fix it.

---

### Post by thomasaaron on 2008-07-17
Could you guys run some specific tests for me, please?

1. sudo gedit /boot/grub/menu.lst
Remove the "quiet" kernel option, save, and reboot.
What message is displaying when it hangs?

2. Does it only hang when the computer is started after being turned off for a while, or does it happen even when the machine is warm?

---

### Post by eyecreate on 2008-07-17
it stopped at "reading files needed to boot"..which is right after "running /scripts/init-bottom"
it does not always stop there, just sometimes, but still 90% of time will time out on the splash screen and just finish the boot with a text terminal(not the same as quiet) will the fix you are looking at possible fix that too?

It seems to be more after it has been off and not just a reboot. It did not stop for me on a reboot but did after shutdown and power back on.

---

### Post by Naenyn on 2008-07-17
> **thomasaaron said:**
> Could you guys run some specific tests for me, please?

1. sudo gedit /boot/grub/menu.lst
Remove the "quiet" kernel option, save, and reboot.
What message is displaying when it hangs?

2. Does it only hang when the computer is started after being turned off for a while, or does it happen even when the machine is warm?

1. This seems to vary. Some examples that it has hung after:

Running /scripts/init - bottom
Preparing restricted drivers...
Starting the Winbind daemon winbind

2. This doesn't seem to matter. I've had it hang on first bootup when I get to work as well as immediate reboots.

Some testing results now... After it'd been on but idle for a couple hours. First restart was fine. Second restart hanged (at Running /scripts/init). Third restart hang (at restricted drivers). Shutdown, waited 20 seconds, powered on, made it pretty far then hanged at winbind. 

Turned off splash just to get a better view and see if I could repeat the iwl4956 microcode error.. rebooted, had a disk check forced. Made it 21.2% then hung. Hit shift once, made it to 58.1%, hang. Shift again, 60%.0, hang. Held down shift until disk check completed and boot finished.

Now that splash is off, I can give you a bit of a better message. 

Restarted and it hanged at:

/build/buildd/linux-2.6.25/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver

Restarted, hanged at:
ata3: SATA max UDMA/133 abar m20480@0xf8404000 port 0xf8404200 irq 504

Hit a key, it did a few more things, then hanged at:
Uniform CD-ROM driver Revision: 3.20

Hit a key, went a bit farther, then hanged at fsck immediately after "Checking file systems...". No actual disk access here until I hit a key.

Hit a key, then hanged after activating swapfile swap...

Hit a key, then it finally booted without any more hangs.

As you can see, it hangs all over the place at various times. Every time it hangs, hitting any key (I usually use left shift) makes it continue. During the hang, there is no disk access. During some restarts, it hangs many times. During others, only once.. and occasionally not at all. 

I've caught on a couple occasions a microcode error regarding the iwl4956. It hasn't popped up today yet though.. Don't know if that's related, but googling for slow boots with that driver returned many recent posts, so I'm figuring it is related.

All of these tests were performed with the system plugged in to AC power, plugged in to an active wired network, and with the wireless switch on (and within range of a few wireless networks).

-naenyn

---

### Post by eyecreate on 2008-07-18
I booted up again today and it stopped at "Preparing Restricted drivers" which is after the last one it stopped at for me. It also did a disk check today too. It was a pretty slow disk check because it paused at 20.6% for a while. I did not have to push any button for it, but it took a few minutes on just that number

---

### Post by thomasaaron on 2008-07-18
OK, guys please try this:

1. Go into your BIOS setup menus, to the Advanced tab, and disable AHCI.

2. add clocksource=jiffies to your kernel option as follows

```
sudo gedit /boot/grub/menu.lst
```

Make your first kernel line look something like this...
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3887ab68-7cd4-462e-9d56-8b2096f10353 **clocksource=jiffies** ro quiet splash

Save and Reboot.

Does that fix it?

---

### Post by eyecreate on 2008-07-18
wow..beautiful...i think it's fixed. My start up was much faster than before with no delays. I will continue to monitor it today and will tell you if anything changes, but thomasaaron, you've really helped with this problem. Will this fix be put into the system76 restore/driver utility? I'd be nice to have those who buy a serp4 in the future to not have to edit the grub menu to fix thier problem.

---

### Post by thomasaaron on 2008-07-18
It absolutely will be in the next driver.

---

### Post by Naenyn on 2008-07-18
> **thomasaaron said:**
> OK, guys please try this:

1. Go into your BIOS setup menus, to the Advanced tab, and disable AHCI.

2. add clocksource=jiffies to your kernel option as follows

```
sudo gedit /boot/grub/menu.lst
```

Make your first kernel line look something like this...
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3887ab68-7cd4-462e-9d56-8b2096f10353 **clocksource=jiffies** ro quiet splash

Save and Reboot.

Does that fix it?

So far, this looks to have fixed it. Excellent work!

Could you explain what the problem was and what the fix does? I just want to make sure that the fix doesn't break / affect anything else.. =]

Thanks a bunch for figuring this out.

-naenyn

---

### Post by eyecreate on 2008-07-18
I'm no expert on this stuff (which is why I was asking for help :D), but after Googling about clocksource, it seems to be where the linux kernel decides to determine the length of a "tick".
> The clock is its heartbeat. It basically defines when a
processor will do an instruction. Normal instructions for the chip take between
one to three clock cycles to complete; a clock cycle is the low-hi-low transition
of the clock. So the faster the clock runs, the faster the chip work([http://www.google.com/url?sa=t&ct=res&cd=2&url=http%3A%2F%2Fwww.avrfreaks.net%2Findex.php%3Ffunc%3DviewItem%26item_id%3D380%26module%3DFreaks%2520Tools&ei=7OCASNvyI5SY8wTJlvnmBQ&usg=AFQjCNEIepbo3NHthFgSBNJcjftG6TtGsA&sig2=aO4Iwdlesii1obBeP7_-Fw](http://www.google.com/url?sa=t&ct=res&cd=2&url=http%3A%2F%2Fwww.avrfreaks.net%2Findex.php%3Ffunc%3DviewItem%26item_id%3D380%26module%3DFreaks%2520Tools&ei=7OCASNvyI5SY8wTJlvnmBQ&usg=AFQjCNEIepbo3NHthFgSBNJcjftG6TtGsA&sig2=aO4Iwdlesii1obBeP7_-Fw))

The other option disabled advanced enhancements to SATA drives and how their memory is managed. ACHI is used mostly in RAID controllers. ([http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface](http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface))

I don't know how they connect, but I'm going to guess access to the drive was not syncing to the clock. But you should get a real answer from someone who knows more.

---

### Post by BoomSie on 2008-07-19
> **thomasaaron said:**
> OK, guys please try this:

1. Go into your BIOS setup menus, to the Advanced tab, and disable AHCI.

2. add clocksource=jiffies to your kernel option as follows

```
sudo gedit /boot/grub/menu.lst
```

Make your first kernel line look something like this...
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3887ab68-7cd4-462e-9d56-8b2096f10353 **clocksource=jiffies** ro quiet splash

Save and Reboot.

Does that fix it?You hit the problem on the spot **thomasaaron** :D

Thanks. I really dedicated this weekend for this problem, cause I cant afford to loose / jeopardize / risk to break my system during the week. First hints already let me to wireless && AHCI/ACPI issues. Cause I tried acpi=off one time and the system flew! to the login screen. But then speedstepping doesn't work anymore etc, and since it's a laptop ... the solution was a no-go :( 

For me the disabling of AHCI was already enough, the clock cycle/tick added to the boot parameters weren't really needed in the end.

Now to let you all understand why I'm so amazingly happy with this:
Before: [  319.315662] <<< last message of the kernel in time ... 5 minutes and 19 seconds !!!!

Now: [   37.089523] :confused:
In plain human language ... ALMOST 10 TIMES FASTER! ( 40 seconds total if I type my username+password fast ;) )

---

### Post by webmaster_ph on 2008-07-30
help! i'm having the same problem too with my hp pavillion dv4050ea laptop. it takes soooo long (like 5 minutes or more) to get to log in screenthere's no option for turning ahci off; all i could do is add clocksource=jiffies to the kernel option. also tried installing the module backports with no luck.

---

### Post by thomasaaron on 2008-07-30
webmaster,

You may want to try adding acpi=off as a kernel option. We don't have a pavilion to test with, though. This forum is for System76 computers.

---

### Post by webmaster_ph on 2008-08-12
any news about this issue?

---

### Post by webmaster_ph on 2008-08-12
> **thomasaaron said:**
> webmaster,

You may want to try adding acpi=off as a kernel option. We don't have a pavilion to test with, though. This forum is for System76 computers.

sorry about that. i was hoping to get some solutions here.

anyway, thanks it seems to work.

---

### Post by glacialfury on 2008-08-14
My apologies for not responding sooner, nor for providing the output you requested; I've been computer-less at Air Force training.

1) I've applied the fix suggested (the bios option and grub change); so far, so good. I'll keep an eye on it.

2) Do you still want the output requested in the 2nd and 3rd pages of the topic?

I'll note that the problem of slow booting - that can be "fixed" by pressing shift/control/alt etc to kickstart it again - only occurs for me during a disk check of /sd3.  Left unattended, it took upwards of 30-40 minutes to boot on occasion.  This disk check occurs every 20 boot cycles, so on the next one I will watch and see if it recurs.

Secondly, for those who noted that the slow boot only occurs when the laptop is plugged into AC power, that is because the disk checking is skipped when you boot on battery power.

---

### Post by thomasaaron on 2008-08-15
If you applied the fix, you don't need to post the previously requested output. You're probably good to go now.

What kind of training are you doing? I spent 4 years in the Army and did a lot of my technical training with the Air Force at the old Lowry Air Force Base. They had the best electronics program at the time, and all of the branches went there.

That was a looooong time ago, though.

---

### Post by glacialfury on 2008-08-15
I'm a medical student at USUHS, a joint service military medical school in Washington, DC.

---

