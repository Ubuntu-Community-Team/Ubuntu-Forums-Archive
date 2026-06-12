---
title: "What could be bottlenecking this system?"
date: 2009-02-15
forum: The Cafe
---

### Post by TravisNewman on 2009-02-15
I've been running Ubuntu and Windows on it for a while, but it's been getting slower and slower. It ran full Ubuntu fine until a couple of releases ago. I didn't use it that much though because the wireless was worthless. Once they got the wireless working better on this model I wanted to use it on the laptop, but it was much slower than XP. So this laptop was XP only for a while. We got a new laptop to replace it, but I'm trying to fix this one up. 

Long story short, I have Ubuntu on this laptop now, running LXDE, using nothing but a terminal and Kazehakase, and it still goes slow as molasses. Before installing Ubuntu, XP was practically unusable. XFCE ran slower than XP which is saying something.

It's a Dell Latitude D410, 1.6Ghz P4, with 256 megs of ram. I know that's not a lot of ram, but that can't be all thats causing this. The air coming from the system fan is getting a lot hotter as well, though not dangerously hot.

Any ideas what could be happening? The memory does test fine.

EDIT: just wanted to add, I didn't put this in the support categories because I don't think it's an Ubuntu problem, it seems like a hardware issue.

---

### Post by prshah on 2009-02-15
> **panickedthumb said:**
> I've been running Ubuntu and Windows on it for a while, but it's been getting slower and slower. 

 still goes slow as molasses.

It's a Dell Latitude D410, 1.6Ghz P4, with 256 megs of ram.

If you find the HDD light is constantly lit and the laptop seems to temporarily freeze up, then you should probably consider the HDD has bad sectors.

A quick badblocks test from a live CD boot```
sudo badblocks -v /dev/sda1
``` will confirm it. 

A quicker, but less through test will be to check for DRDY or Emask exception messages in your dmesg```
dmesg | grep -i drdy\|emask
``` If you find any such messages, it can indicate either logical or physical HDD damage.

If you can manage to keep top running from the terminal, you can also look for programs that are eating up CPU cycles; in my case, running accessibility programs such as dolphin in another login, eats 100% CPU when the launching user logs out, and has to be manually killed.

---

### Post by TravisNewman on 2009-02-15
dmesg came up with nothing. Running the badblocks test now. Dunno why I didn't think to do this earlier either. I haven't had to diagnose any of my linux systems for a while ;)

Even if the badblocks test comes up clean, would that rule out the hard drive? I have seen a lot of drives that just get really slow over time. Unfortunately, as this is a laptop, I can't just swap in some spare hardware I have lying around to test it and I don't want to buy something that won't help.

EDIT: yup, badblocks came up clean.

---

### Post by Colro on 2009-02-15
Dust and overheating issues perhaps? I still wouldn't rule out the hard drive, even if the tests come up clean. Old drives get slower, it's just a fact of life. Do yourself a favor and slap at least a 1GB stick of ram in that thing though, you can grab one off newegg for $10-20 these days.

---

### Post by |{urse on 2009-02-15
Do a cold boot and run this command

touch log && dmesg | more > log

attach that log to a post and we'll have a looksee =)

Edit: Maybe that log needs an extension? idk noone ever does it for me lol

---

### Post by blueturtl on 2009-02-15
The Pentium IV will slow down noticeably if the CPU overheats, so you might want to ensure that cooling is working properly. Just a thought.

---

### Post by TravisNewman on 2009-02-15
> **|{urse said:**
> Do a cold boot and run this command

touch log && dmesg | more > log

attach that log to a post and we'll have a looksee =)

Edit: Maybe that log needs an extension? idk noone ever does it for me lol

Here's the log, the command didn't require an extension for the log, but the forums do. However, the text file went over the forums limits, so I gzipped it.

---

### Post by Icehuck on 2009-02-15
It's a Dell, so pop off the keyboard and look at the fan. Given that its a 410 its quite old(in terms of computers) and probably needs a spray from a can of air. Too much dust will slow those suckers down. 

I would also say it could still be the hard drive. Even if it doesn't have bad sectors the moving parts inside can still break down. 

Edit - Did you wipe the Dell systems diagnositic partition? If not run the tests and it will tell you what hardware isn't functioning properly. You can download the test off their website if you didn't.

---

### Post by gnomeuser on 2009-02-15
I suspect that might have a fair bit of swapping going on, so it might be affected by this:
[http://bugzilla.kernel.org/show_bug.cgi?id=12309](http://bugzilla.kernel.org/show_bug.cgi?id=12309)

---

### Post by prshah on 2009-02-15
> **panickedthumb said:**
> 
Even if the badblocks test comes up clean, would that rule out the hard drive? I have seen a lot of drives that just get really slow over time. 


Since badblocks shows up clean, I'd rule out the HDD. If you still feel that it could be the cause of the bottleneck, you could maybe test it with the hdparm command; however, I don't know what you'd compare it against:```
 sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1642 MB in  2.00 seconds = 820.77 MB/sec
 Timing buffered disk reads:  152 MB in  3.03 seconds =  50.20 MB/sec

```

This is a SATA Seagate 7200rpm / Intel Core 2 Duo 1.7Ghz / 1 Gb Single channel RAM.

---

### Post by jomiolto on 2009-02-15
> **panickedthumb said:**
> It's a Dell Latitude D410, 1.6Ghz P4, with **256 megs of ram**.

That is probably your issue. 256MB really is too little for modern operating systems, including XP if you run firewall, antivirus and such.

What does 'free' in command line tell you?

---

### Post by ssam on 2009-02-15
bad blocks wont tell you about blocks that the disk has realocated. the SMART tools might be better for showing the health of the disk. install smartmontools, and run
```
sudo smartctl -a /dev/sda

```

then run the tests. lots of info online, eg [http://www.captain.at/howto-linux-smartmontools-smartctl.php](http://www.captain.at/howto-linux-smartmontools-smartctl.php)

I'd also second that its a small amount of RAM. spare RAM can speed everything up because linux uses it for caching (install preload to get maximum benefit). Have you checked with top to see what's using you memory. if you run top and type shift+m you get it sorted by memory use.

---

### Post by |{urse on 2009-02-15
okay, looked at the log.. Im sorry is this a 2xcore? Because it's only bringing up 1 cpu 

> [    0.491493] CPU0: Intel(R) Pentium(R) M processor 1.60GHz stepping 08
[    0.492030] Brought up 1 CPUs
[    0.492030] Total of 1 processors activated (3191.98 BogoMIPS).?

OH duh... Pentium M nvm.. I'll keep lookin @ this

also have you done an hdparm -t (or -T) on your disks?

---

### Post by |{urse on 2009-02-15
You do have this bug.

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/296710](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/296710)

Heres the fix

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/296710/comments/13](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/296710/comments/13)

Improper module ordering on a > 2.4 kernel? Idk how bad that could be. Do you have any rogue usb devices popping up that arent really there?

Edit, reading further into the log

> [    3.488058] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.488183] usb usb5: configuration #1 chosen from 1 choice
[    3.488220] hub 5-0:1.0: USB hub found
[    3.488228] hub 5-0:1.0: 8 ports detectedDo you have 8 usb ports?

Yeah... looking at this more. Looks like it causes slow boot due to double polling and makes usb2x devices perform at 1x speeds. Not cool, but it doesn't sound like it could be causing the sort of serious slowdown you're talking about.

---

### Post by TravisNewman on 2009-02-15
I think I may have solved a portion of it. I threw in another gig of ram :) Now it's not hitting the hard drive for swap as often. I also have a drive that I might test. I'll update after a day of running it and see how that works.

EDIT: I now notice that I'm not using any swap at all, and everything is peachy. I did get temporary possession of the exact same drive, and did some testing. badblocks tests MUCH faster on  it than the one that came with the laptop. I think the moving parts are wearing out. Since it's not hitting swap right now, it's not dragging.

Thanks for your help everyone!

---

