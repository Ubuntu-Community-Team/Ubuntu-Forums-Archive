---
title: "Gazelle Pro 6 shutting down and freezing."
date: 2013-09-16
forum: System76 Support
---

### Post by sderrick on 2013-09-16
I have a Gazp6 that just(yesterday and today) started crashing and freezing. Its never done this before for the 2.5 years I've had it.
I'm running Mint, which I've run on it since the second day I received it. Nothing new installed in the last week or so.

It seemed like it was running hotter than usual, so I checked the fans. I blew them out, but they were already pretty clean. No change in temp.

I looked in the syslog and see this happening

Code:

Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.978291] CPU2: Core temperature above threshold, cpu clock throttled (total events = 1)
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.978292] CPU6: Core temperature above threshold, cpu clock throttled (total events = 1)
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.978294] CPU1: Package temperature above threshold, cpu clock throttled (total events = 1)
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.978297] CPU3: Package temperature above threshold, cpu clock throttled (total events = 1)
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.978298] CPU4: Package temperature above threshold, cpu clock throttled (total events = 1)
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.978300] CPU5: Package temperature above threshold, cpu clock throttled (total events = 1)
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.978301] CPU7: Package temperature above threshold, cpu clock throttled (total events = 1)
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.978302] CPU0: Package temperature above threshold, cpu clock throttled (total events = 1)
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.978303] CPU6: Package temperature above threshold, cpu clock throttled (total events = 1)
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.978312] CPU2: Package temperature above threshold, cpu clock throttled (total events = 1)
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.979303] CPU2: Core temperature/speed normal
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.979303] CPU6: Core temperature/speed normal
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.979304] CPU7: Package temperature/speed normal
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.979305] CPU1: Package temperature/speed normal
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.979306] CPU3: Package temperature/speed normal
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.979307] CPU0: Package temperature/speed normal
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.979308] CPU5: Package temperature/speed normal
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.979309] CPU4: Package temperature/speed normal
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.979309] CPU6: Package temperature/speed normal
Sep 16 12:58:45 scott-Gazelle-Professional kernel: [ 3779.979315] CPU2: Package temperature/speed normal
Sep 16 13:00:45 scott-Gazelle-Professional kernel: [ 3899.540130] [Hardware Error]: Machine check events logged

The same second the kernel is reporting a temp above normal and throttling the cpu, it reports temp normal. It just can't cool down that fast!

And then there is the follow on [Hardware error]? Is that referencing the over temp? Is that logged somewhere else? I've looked in /var/log and don't see anythign usefull.

Here is a picture of the temp spike

[IMG]http://tnstaafl.net/images/Screenshot%20from%202013-09-16%2013:25:37.png[/IMG]

The temp rises and falls on all 4 CPU's really fast! 

This is my work machine and I've had it freeze 3 times and shut down twice today.

ANy help woudl be appreciated!

Scott

---

### Post by sderrick on 2013-09-16
I'm contemplating upgrading the Mint 15 from Mint 14 to see if that woudl make any differnce.  I normally wait at least a couple major versions before going through the pain of upgrading.  While I do have my /home and /opt folders on a seperate partition, it still takes days to get things back the way I want them.

Scott

---

### Post by sderrick on 2013-09-16
I compressed a large file and recorded the CPU temp and activity.  3.2 GB file

here is the temp run, it took about 10 minutes

[IMG]http://tnstaafl.net/images/Screenshot%20from%202013-09-16%2014:40:49.png[/IMG]

here is the activity during the last minute of the compression

[IMG]http://tnstaafl.net/images/Screenshot%20from%202013-09-16%2014:41:26.png[/IMG]

---

### Post by tgalati4 on 2013-09-16
It seems like you have a loose heatsink or the heatsink paste has worn out.  I would open the machine and clean it thoroughly and apply new heat paste.  Check the condition of the heatsink fasteners.  If one of them is cracked (many are nylon) then the heatsink won't work properly.  I wouldn't bother with a distro upgrade.  Work the hardware issue first.

A working heatsink should allow all 8 cores at 100% and not exceed 70C in a 25C environment.  Use *cpuburn* (and run multiple instances) to test.  But only test after you have inspected/repaired the heatsink.

The rapid rise and fall in temperature is consistent with a loose heatsink.

---

### Post by sderrick on 2013-09-16
I suspected the heat sink also.  A car low on coolant will do the same thing.  The sinks were not loose, metal screws. 

I removed the two heat sinks and the paste was still paste, though a bit chunky.  CPU thermal paste is 80 miles away, or I would have been to the store already.  

Its a good suggestion, and I guess I will have to make the trip.

thanks,

Scott

---

### Post by tgalati4 on 2013-09-16
When the paste dries out, it doesn't do its job.  Use a very, very thin layer.  Too much will interfere with heat transfer.  There are some youtube tutorials on the proper technique.  If it heats up after the new paste, then I suspect that you have a motherboard issue, or you have a core that is starting to fail causing excessive heating.  You can run *cpuburn* in the background to load each core and see if the heat load is consistent between cores.  Check your BIOS for shutdown temperatures.  You may want to raise them a few degrees to keep from rapid shutdown while you are troubleshooting.  Then set them back down after you have collected some data.

---

