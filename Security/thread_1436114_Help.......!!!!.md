---
title: "Help.......!!!!"
date: 2010-03-22
forum: Security
---

### Post by riggs99 on 2010-03-22
I am using Ubuntu 9.10 - the Karmic Koala - released in October 2009 and supported until April 2011.

I am new to Linux and have just installed this release on my laptop
after having various security problems with hackers under windows XP.

Now someone keeps on remotely shutting down my machine...!!  it shuts down then powers off!!!!!

It is as though now i am on linux and not windows the only thing these hackers can do is remote shutdown.

How can i prevent this......urgent.

Kind Regards

---

### Post by bodhi.zazen on 2010-03-22
This is much more likely to be some type of hardware problem (over heating) then some cracking attempt.

---

### Post by Soul-Sing on 2010-03-22
> after having various security problems with hackers under windows XP

- could you explain the security problems under XP?
- how did you know you were under "attack"?
- and how did they "attack" your system?

---

### Post by _h_ on 2010-03-22
> **bodhi.zazen said:**
> This is much more likely to be some type of hardware problem (over heating) then some cracking attempt.

I'd have to agree with this. If you were getting hacked I doubt they would only just shut your system down, they would attempt to completely wipe out your hard drive or cause massive damage to your filesystem causing file corruptions.

---

### Post by Grenage on 2010-03-22
While echoing the above sentiments, I doubt it's actually a hacking attempt.  You'll need to be more forthcoming with the symptoms you had in XP.

---

### Post by 2hot6ft2 on 2010-03-22
I agree with the others here it sounds more like either a hardware issue or overheating. More info needed.

You may want to have a look and add the sensor applet to your top panel to keep an eye on your temperatures.

Here's a short version of installing them:
Just open a Terminal (Applications -> Accessories -> Terminal) and type (or copy and paste):

```
sudo apt-get install lm-sensors sensors-applet hddtemp
```

Next, run sensors-detect. Answer y to each one until finished.
```
sudo sensors-detect
```

Now you can also run
```
sudo hddtemp /dev/sda
```
Where sda is your hard drive.
and it will show the temperature of your hard drive if it can.

All temps. are in Celsius by default.

adding hdd temp to sensors-applet
> **dcstar said:**
> ```
gksudo gedit /etc/default/hddtemp
```

Make RUN_DAEMON="true", save and reboot.
Finally, restart to load all the sensors (you can choose Logout instead of Restart and it will be much faster). Once back at the desktop, right-click on the top panel and choose "Add to Panel." Select "Hardware Sensors Monitor" and click the "Add" button, then "Close." Right-click on all the sensors applet that appear and choose "Preferences." Click the "Sensors" tab. There you can select/de-select all the relevant sensors and adjust their low and high values as well as set alarms if desired.

---

### Post by riggs99 on 2010-03-23
Hi have taken on board the over heating issue and have added sensors thanx, CPU @66c disks @44c...is this ok?

now for arguments sake lets assume someone is remotely shutting down my machine......they have my mac/ip/hostname etc how can i prevent this ?

---

### Post by Tom.Gee on 2010-03-23
Disable your internet connection and see if, with no wireless, no cable, no connection of any kind, if the machine is still being "remotely shutdown."

---

### Post by riggs99 on 2010-03-23
already done this yep all ok when disconnected....

---

### Post by CharlesA on 2010-03-23
66c is a bit hot, is that when it is idle?

---

### Post by partloer on 2010-03-23
Another possibility is a virus or malware.  There are viruses that shut down the computer.  Another case would be some malware running in the background taking up CPU which could be a reason why you are running a little hot.

If your hardware is working well under Ubuntu but not Windows check for the latest drivers.

Somethings to check:
1. Windows Update
2. Update Virus Software
3. Run Virus Scan
4. Check for malware, adware, spyware, trojans, etc.
5. Change password in case this has been compromised

---

### Post by Gregorybekkers on 2010-03-23
Is there any change on ur files or environment?
or just shutting down?

are you a private or buisness user?

else why would a private user be hacked just to shutdown a system..

---

### Post by Tom.Gee on 2010-03-23
> **riggs99 said:**
> already done this yep all ok when disconnected....
Could be a virus that is active when it "sees" an Internet connection.  You can verify for this situation:  Check your router - view the logs.  Look for a sudden fury of outgoing and incoming access, then Google any addresses that are unfamiliar.  

Here's a list of "familiar" port numbers:  [http://graphcomp.com/info/specs/ports.html](http://graphcomp.com/info/specs/ports.html)

```
EX:

	Outgoing Log Table	
	LAN IP  	Destination URL/IP	Service/Port Number
	900.0.0.12	61.144.146.364    	6381
	900.0.0.12	61.78.205.290    	53197
	900.0.0.11	xpantivirus.com    	74600
	900.0.0.12	67.22.50.281    	53197
	900.0.0.12	67.22.10.306    	53197
	900.0.0.12	google.com        	HTTP
	900.0.0.11	78.135.226.178    	4611
	900.0.0.12	88.175.114.286    	807
	
	Incoming Log Table	
	Source IP	Destination Port Number
	32.135.351.149	10847
	93.321.135.91	10847
	320.213.108.144	50132
	81.172.59.257	50132
	70.307.168.23	808

```
	
If an IP is given instead of a URL, you can PING the IP with the -a switch to do a lookup.  

```
Ex: 
	ping -a 67.195.160.76
	Pinging ir1.fp.vip.ac4.yahoo.com [67.195.160.76] with 32 bytes of data:

	Reply from 67.195.160.76: bytes=32 time=27ms TTL=49
	Reply from 67.195.160.76: bytes=32 time=25ms TTL=49

	Ping statistics for 67.195.160.76:
	    Packets: Sent = 2, Received = 2, Lost = 0 (0% loss),
	Approximate round trip times in milli-seconds:
	    Minimum = 25ms, Maximum =  27ms, Average =  26ms
	

```
This way you know for example, that an HTTP request to 67.195.160.76 is going to Yahoo.com.

---

### Post by riggs99 on 2010-03-23
Hi all just catching up.....

The temp is averaging 66c when idle.

On the windows side i have done all the that stuff.

This is my home PC, and why would someone hack me...we all have enemies!!

I  do not have access to my router as this is a service provided by the appartment via CAT5, no wireless.

Q. does this linux have a system log like windows so i can see what shut the machine down?

Rgds...

---

### Post by 2hot6ft2 on 2010-03-23
> **riggs99 said:**
> 
The temp is averaging 66c when idle.

Just wondering if that's the CPU or the GPU the C and G could be misread.
CPU (Central Processing Unit)
GPU (Graphics Processing Unit)
That temp would be more in line with a GPU. Mine runs ~57-58C at idle.
I have dual a dual core and they each run at ~38C at idle.

There are logs but I'll leave that to someone more familiar with them.

---

### Post by rookcifer on 2010-03-23
You haven't been cracked.  You either have a hardware problem or some software is going haywire somewhere on your machine.  No one cracks a machine just to shut it down.  Sorry, ain't happening no matter how much you insist it does.

---

### Post by slowth5 on 2010-03-23
> **riggs99 said:**
> I  do not have access to my router as this is a service provided by the appartment via CAT5, no wireless

You need a router. This should isolate you from the shared network. If everyone in your apartment is sharing a wired network, who knows what's going on.

Also, 66c is hot for an idling cpu.

---

### Post by riggs99 on 2010-03-24
Guys i will give you heads up on this....

myself i have worked in information technology coming up for 30 years!! over the years have done all the courses currently hold MCSE which i done twice Master Novell certified engineer, Cisco CCNA i have not done unix since i done a SCO course in 89'(really wish i'd done more....but hey the money was with Novell then Windows) i started out as a mainframe engineer.  I am not the greatest but not the worst either!!. Recently was involved in an internet startup with some other serious tekkies more developement orientated, and there was a mega falling out..!! and this hacking business is a result of this.  So consequently they had access to a lot of my personal info ie email, laptop in some cases etc.

So from a computer point of view in the windows environment i'm pretty ok, i know my stuff but so do they!! Anyone can ride in thru port 80 on a cookie!!

When i loaded ubuntu this seriously cut down their effectiveness
so they resorted to shutdowns as hey everyone knows windows.

I booted into windows the other day opened up firefox it did not default to google as per norm but went to a website in their town with a big banner caption at the top of page saying "Welcome back we have missed you"

I hate to admit it i was impressed.

Rgds

---

### Post by riggs99 on 2010-03-24
Also.....reply to Slowth5

I have not really thought about installing another router, i will have to think this thru as to whether you can have one DSL router connected to another one with ip adress,dhcp and NAT etc. in the early days of this i was moving my ip address (changed to static) every day but they were still finding me implying they had some program on my machine now on linux not as easy.  I would be able to get wireless connection at the end though which may provide another barrier.

Rgds

---

### Post by Grenage on 2010-03-24
As long as you have a firewall, you'll be fine.

---

### Post by CharlesA on 2010-03-24
> **Grenage said:**
> As long as you have a firewall, you'll be fine.

This. It sounds a bit like paranoia to me tbh.

I'm betting the CPU is overheating and causing the shutdowns.

---

### Post by justanothergreysky on 2010-03-24
> **riggs99 said:**
> Guys i will give you heads up on this....

-snip-

So from a computer point of view in the windows environment i'm pretty ok, i know my stuff but so do they!! Anyone can ride in thru port 80 on a cookie!!

I'm sorry... but... ROFL.

A cookie is a text file stored on your own computer.  It doesn't DO anything at all.  It can't.

But it was good for a laugh. 

:-)

---

### Post by Tom.Gee on 2010-03-24
> **riggs99 said:**
> I have not really thought about installing another router, i will have to think this thru as to whether you can have one DSL router connected to another one with ip adress,dhcp and NAT etc. 
You can add a router between the Cat5 the apartment provides and the computer.  To the Internet your computer will still be at the IP address the apartment has assigned or dynamically allocated at the time, to your router, the apartment's Cat5 will look no different than a cable modem or a DSL.  Your advantage will be the firewall it provides and the logging you will be able to do.  If your complex is anal about seeing the same MAC connected to its Cat5, most routers these days are capable of cloning the MAC address of your computer.

---

### Post by OpSecShellshock on 2010-03-24
If the access is provided by your apartment management, chances are that it's configured in the most open way possible to ensure that all tenants can use whatever they want on it. That means that it's going to be wide open for a lot of things. It also probably means that you won't have any trouble putting a hardware router/firewall between your computer and the network drop. And I'd say it's probably essential.

---

### Post by riggs99 on 2010-03-25
Hi guys...!!

The cookie file in firefox is some sort of sql file not text, "cookies.sqlite" Mozilla probably done this because there are malicious/spyware cookies out there which are trojans but look like/disguised as bog standard text file cookies......

Anyway....found the syslog.........

Mar 24 12:21:11 ubuntu kernel: [92189.556987] Critical temperature reached (81 C), shutting down.
Mar 24 12:21:12 ubuntu kernel: Kernel logging (proc) stopped.
Mar 24 13:02:18 ubuntu kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Mar 24 13:02:18 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="913" x-info="http://www.rsyslog.com"] (re)start
Mar 24 13:02:18 ubuntu rsyslogd: rsyslogd's groupid changed to 102
Mar 24 13:02:18 ubuntu rsyslogd: rsyslogd's userid changed to 101
Mar 24 13:02:18 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset


So yes it has overheated and shut down.....not going beserk over this yet will monitor....hats off to all who pointed me in this direction

PS. As a Windows guy i do like this Linux!!!

---

### Post by bodhi.zazen on 2010-03-25
> **riggs99 said:**
> Hi guys...!!

The cookie file in firefox is some sort of sql file not text, "cookies.sqlite" Mozilla probably done this because there are malicious/spyware cookies out there which are trojans but look like/disguised as bog standard text file cookies......

Anyway....found the syslog.........

Mar 24 12:21:11 ubuntu kernel: [92189.556987] Critical temperature reached (81 C), shutting down.
Mar 24 12:21:12 ubuntu kernel: Kernel logging (proc) stopped.
Mar 24 13:02:18 ubuntu kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Mar 24 13:02:18 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="913" x-info="http://www.rsyslog.com"] (re)start
Mar 24 13:02:18 ubuntu rsyslogd: rsyslogd's groupid changed to 102
Mar 24 13:02:18 ubuntu rsyslogd: rsyslogd's userid changed to 101
Mar 24 13:02:18 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset


So yes it has overheated and shut down.....not going beserk over this yet will monitor....hats off to all who pointed me in this direction

PS. As a Windows guy i do like this Linux!!!

Thank you for posting that information.

---

### Post by ibuclaw on 2010-03-25
> **riggs99 said:**
> 
Anyway....found the syslog.........

Mar 24 12:21:11 ubuntu kernel: [92189.556987] Critical temperature reached (81 C), shutting down.
Mar 24 12:21:12 ubuntu kernel: Kernel logging (proc) stopped.
Mar 24 13:02:18 ubuntu kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Mar 24 13:02:18 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="913" x-info="http://www.rsyslog.com"] (re)start
Mar 24 13:02:18 ubuntu rsyslogd: rsyslogd's groupid changed to 102
Mar 24 13:02:18 ubuntu rsyslogd: rsyslogd's userid changed to 101
Mar 24 13:02:18 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset


So yes it has overheated and shut down.....not going beserk over this yet will monitor....hats off to all who pointed me in this direction


What type of Laptop are you running? What surface are you running it on? And how long does it take for the Laptop to shutdown via overheating?

Have you tried any powersaving techniques?

Regards
Iain

---

### Post by riggs99 on 2010-03-27
My laptop is quite old now but is 17" zd8000 one of the original desktop replacement's

processor - 3.40 GHz Intel® Pentium® 4 Processor 650
mem -2gb
video - ATI MOBILITY RADEON X600 graphics 256 MB dedicated
hard drive - 100 GB 4200 rpm
display - 17" WXGA+ High Definition BrightView Widescreen

They do have heat problems, just checking out site must clear air vents etc.

It sits on a wooden table with about 10 mm gap.

Rgds

---

### Post by CharlesA on 2010-03-27
Might want to take the bottom off and clean it out with air if you feel comfortable doing that.

Otherwise get a chillmat or something similar that'll blow cool air to the intake fans on the bottom of the laptop.

---

### Post by Tamalin on 2010-03-27
Definitely get some sort of cooling or fan pad for that.  The cold air can actually speed up your computer a little bit as well, electrons travel faster in the cold I beleive.  I once had an old Inspiron that would heat up to 140+ degrees (I measured w/ a meat thermometer) when idling.  It was extremely slow and hard to use (but it still booted faster than Vista!).

---

### Post by riggs99 on 2010-03-28
Q. I am dual booting between XP and Ubuntu....how come i never have 

   this problem under XP after all its the same hardware ?

Rgds

---

### Post by OpSecShellshock on 2010-03-28
> **riggs99 said:**
> Q. I am dual booting between XP and Ubuntu....how come i never have 

   this problem under XP after all its the same hardware ?

Rgds

I'm going to guess video drivers, and that the reason it only happens while connected to the network is that there's a browser open that happens to be rendering several images in short periods of time. You'd be able to tell for sure if you check the temperature once while disconnected from the network, once while connected but without a browser open, and then again with a browser open. You might also be able to try running something other than a browser but that's still got a lot going on graphically, like a game.

With the Radeon X600 being what's politely known as "legacy," I'm not sure you'll find much vendor support if that turns out to be the issue. You may be in a situation where you need to disable things like desktop effects and/or lower the resolution. WinXP existed at the time that the X600 was new, but Ubuntu 9.10 did not.

Sorry, bit of a tangent. Best to find out if the video driver is actually the problem before attempting to solve it, I suppose.

---

### Post by cbecker78 on 2010-04-01
Have you also checked to make sure the fan is coming on?  Mine wasn't for a while after I first installed Ubuntu and had to fool around with some stuff to make it work.... of course, my laptop was pretty new.  I would expect older models have better support by now, but you never know...:-?

---

### Post by riggs99 on 2010-04-13
Hi Guys,

Got this from the AUTH.LOG

Apr 13 08:17:01 ubuntu CRON[5023]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 13 08:17:01 ubuntu CRON[5023]: pam_unix(cron:session): session closed for user root
Apr 13 08:25:54 ubuntu gdm-session-worker[1552]: pam_unix(gdm:session): session opened for user riggs99 by (uid=0)

The first 2 entries happened prior to the pc shutting down.....the 3rd one is me logging in after reboot.

What do the first 2 entries mean?

Rgds

---

### Post by CharlesA on 2010-04-13
That is normal. Those show up when a cron tab is running.

---

