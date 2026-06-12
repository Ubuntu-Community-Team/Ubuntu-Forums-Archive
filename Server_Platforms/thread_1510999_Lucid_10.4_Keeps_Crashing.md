---
title: "Lucid 10.4 Keeps Crashing"
date: 2010-06-16
forum: Server Platforms
---

### Post by Nunners on 2010-06-16
I've recently installed Ubuntu Server Lucid 10.4 onto as a new system, with a view to making it into our email gateway and monitoring server.

The only problem is, prior to launching it all live, I've left it on for a week or so, and it keeps crashing.
I've done a memory test (from the Lucid disc) and it didn't bring up any errors.  Can anyone suggest what might be wrong?

There's nothing in the logs that suggests anything; literally all that happens is the screen freezes, and won't react ot any keyboard input, and the network cards become unpingable/anything else-able....

Any help gratefully received.

Thanks
Nunners

System setup is: 2U Small Rack-mount Server case with Dual AMD Opteron Socket 940 CPUs 2.4Ghz, 2GB ECC DDR RAM, 80GB HDD

---

### Post by Nunners on 2010-06-25
This unfortunately is still causing a problem.

I've done a full memory check (using the Ubuntu ISO CD) and that came up with no errors.
I've also done some monitoring of the temperatures, both in the case and on the CPU, and it doesn't seem to crash in correlation to any temperate rises.

Has anyone got any thoughts (please) on what might be causing this?

Cheers
Nunners

---

### Post by VH-BIL on 2010-06-25
Is there any information in the logs?

---

### Post by Nunners on 2010-06-25
Here's the syslog and message log... not sure what else you'd need...

/var/log/syslog - [http://pastebin.com/VtwCdKZw](http://pastebin.com/VtwCdKZw)
/var/log/messages - [http://pastebin.com/sR7Wwz05](http://pastebin.com/sR7Wwz05)

The server failed at around 10.30 localtime....

---

### Post by VH-BIL on 2010-06-25
There is no 10:30 in the logs, and no error messages.

---

### Post by Nunners on 2010-06-25
Exactly, that's why I can't work out what's happening.  I've currently got it sat next to me, and keep checking the screen/pinging it... and only know it's crashed when I can't ping or enter anything on the command line, directly on the server.

That's why I thought about memory/temperature, but as I can't find an error with them, I've got to look elsewhere!!!!

---

### Post by QfwfQ on 2010-06-25
Same here. Screen freezing and system restarts. Some times I have to force a hard-power-button shut down.

I can't relate this with any running program in particular (although Firefox and OOffice are up most of the time), and I also can't find anything to blame in syslog.

10.04 Desktop

---

### Post by wynand2020 on 2010-06-25
Try a re-install of the OS, check the memory

---

### Post by VH-BIL on 2010-06-25
Do you think it could be a hardware issue?

---

### Post by Nunners on 2010-06-25
There's no "non-specific" hardware installed, so if it is, it's the motherboard or associated.  I've also had about 3/4 of these machines and none has gone on me yet!

I'll try and reinstall I think... just need to save all the config of stuff I've put on so far!

---

### Post by VH-BIL on 2010-06-25
I know but I have had trouble with NIC's going south on me when administrating servers.

---

### Post by Nunners on 2010-06-25
The thing is, in my case it's not just the NIC going... unless the two NICs are causing the whole lot to go...?

---

### Post by Nunners on 2010-06-25
OS Reinstall complete... going through adding all the config in etc... It has crashed once already... nothing in logs again, although I'm not certain it wasn't something I'd done this time... I'll keep monitoring...

---

### Post by Nunners on 2010-06-25
No definitely not any better... back to the drawing board... anyone got any ideas?

---

### Post by VH-BIL on 2010-06-25
No, maybe hardware or the configuration of the hardware. I had a problem with a hardware configuration that caused a system freeze. It just happen to be the graphics card was not happy in the slot it was in and was moved, after no problems.

---

### Post by Nunners on 2010-07-02
Sort out hitting a brick wall with this one... the motherboard is all in one... i.e. the sound and display card are in-built, therefore there isn't mich that can go wrong.  Is this likely to be something either install specific, something with Lucid or more than likely a fault on the motherboard/CPU etc?  If it's the latter, then that's fine... but not sure what else I can do if it's the first two... can anyone suggest anything?

Cheers
Nunners

---

### Post by sh1ny on 2010-07-02
It can be any number of things.
Just so you're sure you can install a different OS for a test, see if it crashes there. Something that has different kernel version preferred.

From the way it sounds, seem like a mobo issue to me. Try with a different PSU after the OS reinstall above. Try installing lm-sensors and monitoring the temps, something might be causing overheating.

I've had a few cases of boxes freezing ( tho not rebooting ) and it was almost always either the mobo or the PSU.

---

### Post by Nunners on 2010-07-02
I have tried a different PSU, so probably mobo... I'm going to try debian, as apparently that can handle odd hardware better (not that I think this is an odd hardware issue) and see where we go from there!

---

### Post by VH-BIL on 2010-07-02
Sh1ny has a good point.

---

### Post by Nunners on 2010-07-07
Now up and running on Debian 5.05 - and it all seems fine... no faults nothing.. and actually, looking at the stats, it's running better as well - better load and memory usage...

I'll stick with that for now then - thanks for your help guys...

---

### Post by HermanAB on 2010-07-07
Howdy,

I would plug it into a UPS and see if the problem continues.  In my experience, many/most crashes are caused by dirty power, not software.

---

### Post by ab1m on 2011-10-12
My Ubuntu 10.04 was crashing too! Then I remembered that my system
was working fine till I installed Google earth. So I un-installed
Google earth and it (my computer) hasen't crashed since:-)

Ck and see if you installed something a day or so be for it
(your system) started crashing. If so un-install the software.

---

### Post by ab1m on 2011-10-13
Just a quick follow up on my last post. My system crashed
a few hours later again!

So I took someones advise and did a new install
with no regrets

---

