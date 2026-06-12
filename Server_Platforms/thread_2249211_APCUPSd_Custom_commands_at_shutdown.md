---
title: "APCUPSd: Custom commands at shutdown"
date: 2014-10-20
forum: Server Platforms
---

### Post by mattlach on 2014-10-20
Hey all,

So I have been doing a bunch of reading on this and come up a little short.

Many guides suggest editing the /etc/apcupsd/apcontrol script to insert custom commands at shutdown time, but the comments in the file itself warns against doing this, as this file is replaced during updates.

There are many references to a "proper" way of doing this, but I have googled a lot and not come up with what this proper way is.

In my setup, I would like to use plink to send an ssh command to shutdown another host when battery power gets low.

I tried this by entering commands into apccontrol (like is recommended against) and my commands that work fine in shutting down the remote system when entered directly in console, are not having any effect once called from apccontrol.   I am currently assuming this is because the server with apcupsd installed is running on an ssd, and thus shuts down VERY fast, possibly before the completion of my command.

Does anyone have any suggestions?

I was thinking of maybe creating a cronjob that runs on shutdown, but I have found cron - while great in time based commands - to be very unreliable when it comes to running things at startup and shutdown.

I'd appreciate any suggestions!

--Matt

---

### Post by mattlach on 2014-10-20
Actually, never mind, finally found this:

[http://linux.die.net/man/8/apccontrol](http://linux.die.net/man/8/apccontrol)

If anyone has a good example of of a doshutdown script, showing how to correctly exit with status 0 or status 99, I'd really appreciate it!

--Matt

---

### Post by tgalati4 on 2014-10-20
[apcupsd]("https://help.ubuntu.com/community/apcupsd") is an old framework and there may be better ways to do this.  Newer versions of Ubuntu have some apc shutdown capability already built in, so you want to research that first.  

Using the existing apcupsd framework, you can set up a master and slave arrangement such that the UPS is connected to the master and any other computer on the LAN can be a slave (running apcupsd in slave mode) and will get a shutdown signal through ethernet.  This assumes that your router has some UPS protection and any running PC's on your network are either laptops (with working batteries) or other desktops with dumb (not-connected) UPS's.

Many smartups have firmware that can be configured (through dip switches) to perform graceful shutdowns when the battery limit is reached, so you don't really do the doshutdown script.  I would just set the shutdown delay to 60 seconds, send a network message out (this happens automatically), and have the machine shutdown after this 60 seconds.  If your power is out for a minute, there is a good chance it will stay down for a while anyway.

If the power just flickers (because of maintanence on the lines, or trees brushing on the power lines) your system will stay up.

You will have to describe your Use Case in more detail.  I would make a flowchart to show how and when you want your system (and other devices) to shut down and under what conditions.

Some other ups links:  

[http://blog.shadypixel.com/monitoring-a-ups-with-nut-on-debian-or-ubuntu-linux/](http://blog.shadypixel.com/monitoring-a-ups-with-nut-on-debian-or-ubuntu-linux/)

[http://ubuntuforums.org/showthread.php?t=2178713&highlight=apcupsd](http://ubuntuforums.org/showthread.php?t=2178713&highlight=apcupsd)

---

### Post by mattlach on 2014-10-20
First off, thank you for taking the time to help, I really appreciate it!

> **tgalati4 said:**
> 
You will have to describe your Use Case in more detail.  I would make a flowchart to show how and when you want your system (and other devices) to shut down and under what conditions.

I will start with this, as it may help in the following questions.  Unfortunately I can't draw a flowchart right now, so my text description of my setup will have to do.

The Ubuntu server in this case, is a dedicated headless mini-install used ONLY for UPS monitoring.

It resides as a guest OS on my VMWare ESXi server, along with numerous other guests.

I have two separate UPS:s, one APC Smart-UPS 1500.  (Only the ESXi host is plugged in to this one) and one APC Smart-UPS 750 (Switch, Wireless AP, FIOS ONT, and a handful of other small devices plugged into this one)

My router is actually pfSense running as a guest on the same ESXi host above.

Nothing on the smaller 750 unit requires a tidy shutdown, so I figured I'll just let it run dumb until battery is drained and it shuts itself down.

The ESXi host, however needs a tidy shutdown, and the Ubuntu server guest with apcupsd is intended to accomplish this.

It all looks like this (UPS:es not pictured) to put it into context.
[img]https://farm6.staticflickr.com/5560/15104817929_f85d18d3a6_b.jpg[/img]

> **tgalati4 said:**
> [apcupsd]("https://help.ubuntu.com/community/apcupsd") is an old framework and there may be better ways to do this.  Newer versions of Ubuntu have some apc shutdown capability already built in, so you want to research that first.

I have done some reading here.     APC does have a version of their PowerChute software available as a virtual appliance that can be installed in ESXi, but unfortunately this requires a fully licensed version of ESXi with vMA.   Since this is a basement server, I can't afford a license like that, and am relying on the free standalone license.

I tried NUT at first, as NUT actually has a package that can be installed in ESXi as a slave for tidy shutdown purposes, but unfortunately I have found that NUT has rather poor compatibility with APC's Smart UPS models.   Over the serial connection the NUT server just identifies it as an "unknown device" and refuses to do anything with it.   Using the USBHID driver it detects it, but then immediately the NUT server segfaults.   Same thing happens when I try to do it over SNMP over ethernet.   Detects the unit, followed by an immediate segfault.

Based on this I decided to go with APCUPSd.

> **tgalati4 said:**
> 
Using the existing apcupsd framework, you can set up a master and slave arrangement such that the UPS is connected to the master and any other computer on the LAN can be a slave (running apcupsd in slave mode) and will get a shutdown signal through ethernet.  This assumes that your router has some UPS protection and any running PC's on your network are either laptops (with working batteries) or other desktops with dumb (not-connected) UPS's.

Unfortunately I am not aware of any version of the apcupsd client that is able to run natively in ESXi.


So, based on these limitations the setup I have in mind is as follows.

The mini dedicated Ubuntu server monitors the UPS via APCUPSd.  This works beautifully.  It detects it over the serial interface, and I can get all the information from it using the apcaccess command.

If power is lost, and the battery is drained down to my preset timeleft setting (currently I have it set to 10 minutes) I want it to use plink to ssh in to the ESXi server, and issue the command for orderly shutdown of all guests, followed by system shutdown.

(this happens to be ""/sbin/shutdown.sh && /sbin/poweroff")

Some people ([like this guy](http://www.designervisuals.com/Shutdown_ESXi_and_VMs_During_a_Power_Failure.html)) have had luck with this in editing the /etc/apcupsd/apccontrol script, but this doesn't work for me.

While using plink manually directly from the command line has the desired effect (shuts down all guests in an orderly fashion, followed by ESXi host shutdown) once embedded in the apccontrol script it does not work at all.   I'm guessing this is because my server is very small and lightweight, and runs on a very fast SSD, so it shuts down very quickly once the poweroff command is issued, and thus the plink command to the ESXi host is never issued completely.

Based on this, I think what I want is to ignore the normal shutdown behavior of apcupsd, (since the guest will shutdown orderly once ESXi gets the command to do so anyway) and just have it issue the shutdown command to the ESXi host.


Based on my reading thus far, I think a doshutdown script that looks like this should accomplish that (or at least so I hope)

```

#!/bin/bash
plink -ssh -2 -pw password root@xxx.xxx.xxx.xxx "/sbin/shutdown.sh && /sbin/poweroff"
exit 99

```

Is that correct? (this is really simple and barely worth calling a script, but bash scripting is not my expertise by any stretch of the imagination)    Then if I give it the "exit 99" it should ignore the normal shutdown behavior in apcontrol, and ONLY issue this shutdown line to ESXi.

After this, ESXi should then shut down each guest in orderly fashion, including the dedicated UPS Ubuntu server (as defined in ESXi configs) and shut itself down.

Not quite sure what will happen to the UPS shutdown itself after this.   I read somewhere that with SmartUPS models you can define a delay after which the UPS shuts down, but I am not sure where this is (maybe in the web cofigurator for the UPS itself, or somewhere in the apcupsd config file?)

I have done numerous timed shutdowns of my host, and shutting down all the guests, followed by a host shutdown takes repeatedly 2min 35s (+/- a couple of seconds) so I figure I should be safe if I set the UPS delay to 5 minutes.  Maybe even 10 (I currently have everything set to trigger a shutdown when TIMELEFT reaches 10 minutes, just to be on the safe side.

I'd appreciate any thoughts or insights you might have into this setup.

Thank you again,
Matt

---

### Post by tgalati4 on 2014-10-20
Well, running an EXSi hypervisor does add some complexity.  If you were running Xen, then you would have a linux hypervisor with apcupsd running in host process table and then could shut down your vm's in a controlled fashion.

So search the web, I found a few of these links:

[https://communities.vmware.com/docs/DOC-11482](https://communities.vmware.com/docs/DOC-11482)

[http://serverfault.com/questions/462993/vmware-esxi-shutdown-triggered-by-apc-ups-connected-via-usb](http://serverfault.com/questions/462993/vmware-esxi-shutdown-triggered-by-apc-ups-connected-via-usb)

The second link discusses how you can use a NUT slave in an EXSi vm to trigger a shutdown.  Understand that NUT is a generic UPS framework and apcupsd is a specific UPS framework for APC Smartups and similar devices that use the smartups commands.

Because of the length of time to shut down EXSi vm's, timing is important so that you have enough battery power to keep the server running while you dump vm clients as quickly as possible.

Otherwise, use the approved, corporate solution--buy the license and use powerchute.

---

### Post by mattlach on 2014-10-20
> **tgalati4 said:**
> Well, running an EXSi hypervisor does add some complexity.  If you were running Xen, then you would have a linux hypervisor with apcupsd running in host process table and then could shut down your vm's in a controlled fashion.

So search the web, I found a few of these links:

[https://communities.vmware.com/docs/DOC-11482](https://communities.vmware.com/docs/DOC-11482)

[http://serverfault.com/questions/462993/vmware-esxi-shutdown-triggered-by-apc-ups-connected-via-usb](http://serverfault.com/questions/462993/vmware-esxi-shutdown-triggered-by-apc-ups-connected-via-usb)

The second link discusses how you can use a NUT slave in an EXSi vm to trigger a shutdown.  Understand that NUT is a generic UPS framework and apcupsd is a specific UPS framework for APC Smartups and similar devices that use the smartups commands.

Because of the length of time to shut down EXSi vm's, timing is important so that you have enough battery power to keep the server running while you dump vm clients as quickly as possible.

Otherwise, use the approved, corporate solution--buy the license and use powerchute.

Thank you for that.  Yes, it does add a little bit of complexity.

I vaguely recall playing with Xen back when I originally set this up in 2010, but I wasn't as happy with it as I was with ESXi Free.  Took 4 years for me to finally cross "get a UPS for the server" off my to do list :p

As mentioned I did try NUT, but the NUT server seems incompatible with my APC SmartUPS 1500  (SUA1500) model, which is unfortunate.

The corporate approved method would be great, and probably worth it for a corporation, but for a home tinkerer like myself, the ESXi licenses are just a little bit too pricey, so I am stuck with the free license.

It's too bad there isn't a cheaper home use license for ESXi, but then again, there probably aren't that many of us playing with ESXi servers at home :p

I had a thought.   What if the NUT client were compatible with the apcupsd server, so I could run apcupsd on the server, and set up the NUT client to get information from it and handle the shutdown, but that probably isn't the case.

I am going to try creating the doshutdown script with my plink command in it and see if that does it.   (fingers crossed)

---

### Post by volkswagner on 2014-10-21
Is your pfsense machine capable of connecting to the smart UPS?

Perhaps pfsense can be the "leader of the pack"?

---

### Post by mattlach on 2014-10-21
> **volkswagner said:**
> Is your pfsense machine capable of connecting to the smart UPS?

Perhaps pfsense can be the "leader of the pack"?

Possibly.   What would be the benefit of this?   Does pfSense have good built in UPS support?

I generally try to avoid doing any custom stuff in pfSense and FreeNAS, partially because they are based on limited BSD images to save space, and partially because I find the default BSD console clunky and annoying compared to Ubuntu and other Linux distributions.

Appreciate your suggestion!

---

### Post by tgalati4 on 2014-10-21
You can get the same functionality under freenas, you just have to add the correct packages and set up the configuration just as you would in Linux.  Xen has improved a lot in 4 years.  For the power consumption of a 96GB, Xeon server, you can buy new UPS each year for each device.

Installing apcupsd on freenas:  [https://forums.freenas.org/index.php?threads/ups-nut-communications-with-ups-lost.23348/](https://forums.freenas.org/index.php?threads/ups-nut-communications-with-ups-lost.23348/)

Is your UPS similar to this? [http://forums.apc.com/message/49943](http://forums.apc.com/message/49943)

An interesting discussion on why APC does not support newer UPS's in linux:  [http://forums.apc.com/thread/5374](http://forums.apc.com/thread/5374)

---

### Post by mattlach on 2014-10-21
> **tgalati4 said:**
> You can get the same functionality under freenas, you just have to add the correct packages and set up the configuration just as you would in Linux.

Oh, I know I can, I guess I was wondering if he was suggesting there was any benefit in doing so, over the approach I have gone down with Ubuntu, which I much prefer due to the ease of the package manager, better documentation and my familiarity with all the command line syntax of commn commands, which is very subtly different in BSD, but enough to be an annoyance.  (that, and I never understood why my delete key never works in BSD, instead inserting an annoying character :p )

I find it much nicer to manage my Ubuntu server, so to me, it will well worth the extra shared 128MB of RAM and one shared core that mostly idles, it cost me to install a basic dedicated Ubuntu server for the task.

> **tgalati4 said:**
> 
Xen has improved a lot in 4 years.

I'm sure it has.  I would love to try it again, as I much prefer open source initiatives, but I have everything set up the way I like it, and would need to find lots of time to start over with Xen.   It's not a production server, but down time does matter, as I run home stuff off of it (including all the house TV through a MythBuntu backend running as a guest)

> **tgalati4 said:**
> 
For the power consumption of a 96GB, Xeon server, you can buy new UPS each year for each device.

Well, I built it with low power L5640's, a free flow 4U case, so fan speeds can be lower, and used an 80+ platinum power supply, so power use is actually very reasonable.

Besides, what would be the use of having a bunch of UPS's and nothing to plug into them?  :p

[QUOTE=tgalati4;13148538]
Installing apcupsd on freenas:  [https://forums.freenas.org/index.php?threads/ups-nut-communications-with-ups-lost.23348/](https://forums.freenas.org/index.php?threads/ups-nut-communications-with-ups-lost.23348/)

Yeah, I've seen that, thank you.

Unless there is a really good reason to do so, I prefer to keep my appliance installs (pfSense and FreeNAS) as appliance as possible, and not mess with installing packages and jails if I can avoid it.

> **tgalati4 said:**
> 
Is your UPS similar to this? [http://forums.apc.com/message/49943](http://forums.apc.com/message/49943)

No, the X series are newer post-Schneider acquisition models.   My SUA1500 (and SUA750) are older models.  They still use some stupid proprietary stuff (like non-standard serial cables) but nowhere near as bad as the newer models released after Schneider acquired the company.

> **tgalati4 said:**
> 
An interesting discussion on why APC does not support newer UPS's in linux:  [http://forums.apc.com/thread/5374](http://forums.apc.com/thread/5374)

This is interesting, considering their official PowerChute VM appliance is linux based (RHEL I believe)

Ever since the Schneider acquisition they have been acting very stupidly in regards to making everything opaque and closed and not interracting with the open source community.   it is too bad.

There are few UPS:es out there as effective and bulletproof as their old Smart-UPS models, with their true sine wave designs, and dependable builds, which is why so many of them are still in use by hobbyists and companies 10 years after they were originally built.

---

### Post by tgalati4 on 2014-10-21
I have refurbished a few of the older SmartUPS.  I like the metal cases--they don't melt like the plastic ones that I have seen in extreme amp pulls.  They seem to handle lightning strikes (which destroy them, of course) but fail in a way that doesn't cause further damage.

Schneider is only interested in emergency building lighting and buying APC gave them a lot of technology.  It's big money because it is mandatory in any new building, but server UPS is probably a small market in comparison, and linux support is obviously not on their radar.

So grab those older pre-Scheider APC-SmartUPS's before they get zapped by lightning and replace the batteries and you should be good for 10 years or so.  The batteries will need changing, but at least those are easy to find.

---

### Post by mattlach on 2014-10-21
> **tgalati4 said:**
> I have refurbished a few of the older SmartUPS.  I like the metal cases--they don't melt like the plastic ones that I have seen in extreme amp pulls.  They seem to handle lightning strikes (which destroy them, of course) but fail in a way that doesn't cause further damage.

Schneider is only interested in emergency building lighting and buying APC gave them a lot of technology.  It's big money because it is mandatory in any new building, but server UPS is probably a small market in comparison, and linux support is obviously not on their radar.

So grab those older pre-Scheider APC-SmartUPS's before they get zapped by lightning and replace the batteries and you should be good for 10 years or so.  The batteries will need changing, but at least those are easy to find.

Yep, that's exactly what I did.

They were a bargain too...  The SUA1500 on eBay was only $125 shipped, without a battery (bought one locally at Batteries Plus for ~$150)

I hadn't even planned on buying the second one, but I already had two compatible batteries I had recently bought (for another project that wasn't going anywhere) and one popped up in my feed for only $50 shipped, so I couldn't resist.

Moved all the accessories (switch, ONT, etc.) over to the new smaller one, and increased my uptime on the big one attached to the server to 55 minutes.

The older SmartUPS units are built like tanks.   Most places don't make products like this anymore.

Now I just have to figure out this auto-shutdown thing.  I set it up using the doshutdown script exiting in 99 last night, but wasn't able to test it, as my future mother-in-law was watching TV (the server also hosts my MythTV Backend as a guest).  Hoping to get a chance to test it tonight!

After that, I have to move on to the next in my list of "things I thought would be easy, but turned out to be surprisingly difficult", namely properly setting up per client traffic shaping using pfSense.  :p

---

### Post by mattlach on 2014-10-21
> **mattlach said:**
> 
Now I just have to figure out this auto-shutdown thing.  I set it up using the doshutdown script exiting in 99 last night, but wasn't able to test it, as my future mother-in-law was watching TV (the server also hosts my MythTV Backend as a guest).  Hoping to get a chance to test it tonight!

Hmm, so I just did a test, with negative results.

I placed the doshutdown script in the /etc/apcupsd folder as mentioned in [the manual](http://linux.die.net/man/8/apccontrol).

It looks like this:

```

#!/bin/sh
plink -ssh -2 -pw password root@xxx.xxx.xxx.xxx "/sbin/shutdown.sh && /sbin/poweroff"
exit 99
```

The contents of my /etc/apcupsd looks like this:
```

# ls -lh
total 60K
-rwxr-xr-x 1 root root 3.9K Oct 20 19:28 apccontrol
-rw-r--r-- 1 root root  13K Oct  5 21:31 apcupsd.conf
-rwxr-xr-x 1 root root  455 May 19  2013 changeme
-rwxr-xr-x 1 root root  444 May 19  2013 commfailure
-rwxr-xr-x 1 root root  483 May 19  2013 commok
-rwxr-xr-x 1 root root  103 Oct 21  2014 doshutdown
-rw-r--r-- 1 root root  662 May 19  2013 hosts.conf
-rwxr-xr-x 1 root root  617 May 19  2013 killpower
-rw-r--r-- 1 root root 2.3K May 19  2013 multimon.conf
-rwxr-xr-x 1 root root  450 May 19  2013 offbattery
-rwxr-xr-x 1 root root  415 May 19  2013 onbattery
-rw-r--r-- 1 root root    0 Oct 21 13:24 powerfail
-rwxr-xr-x 1 root root  944 May 19  2013 ups-monitor
```


When I just do a ./doshutdown as root, it sends the command to ESXi as expected, and orderly shutdown of all guests, followed by orderly shutdown of host commences.

If I power it back on again, boot everything up, and unplug the UPS and wait, I get the following:

```

Broadcast Message from root@apcupsd                                            
        (somewhere) at 12:39 ...                                               
                                                                               
Power failure on UPS SUA1500. Running on batteries.  
```

followed by:

```

Broadcast Message from root@apcupsd                                            
        (somewhere) at 13:24 ...                                               
                                                                               
Remaining battery runtime below limit on UPS SUA1500. Doing shutdown.          
                                                                               
                                                                               
Broadcast Message from root@apcupsd                                            
        (somewhere) at 13:25 ...                                               
                                                                               
Continuing with shutdown.                                                                               

```

but the host never initializes shutdown...

The odd thing is, apcupsd must be recognizing my script, ending with "exit 99", as it no longer tries to shut down the guest   (according to the manual, exiting with 99 means the script overrides default shutdown behavior, and exiting with 0 means to continue with default shutdown behavior after completing script), but for whatever reason the ssh command is never sent to the ESXi host via plink, even though this behavior works perfectly when I just execute the script directly....


I am at a loss...

It seems to be an issue in apcupsd or with plink.

I wonder if there is any reason apcupsd would skip over that line in the script, or if there is any reason plink would refuse to execute properly when triggered by apcupsd, but work just fine when the doshutdown script is executed manually?

I'd appreciate any ideas!

--Matt

---

### Post by mattlach on 2014-10-21
Grrr...

And apparently it still tells the UPS to kill power, because a few minutes later (after the configured delay) the UPS cut power to the fully powered up server....

Luckily nothing seems to have broken.

---

### Post by mattlach on 2014-10-21
Did some googling, found multiple users complaining of these issues (mostly in 2012) on various user groups and forums, but have not yet seen any solutions...

---

### Post by tgalati4 on 2014-10-21
Testing shutdown procedures is tedious.  I use a 100-watt light bulb, so I can see the load (I know it is exactly 100 watts with a Power Factor of 1.0), but keep the server plugged into another (non-ups) outlet.  I can then watch the messages, calculate the runtime (compared to the actual measured) and keep the server protected from a sudden poweroff.  Then I perform this test 10 times (charging the battery in between and allowing the MOSFETs to cool--important) to check that the timing is correct and consistent.  If the timing is messed up, you get premature shutdowns--which are bad.

What user is *apcupsd* running as?  When you run the script manually, you are in a root terminal.  So a difference in user would account for the script to fail while under the *apcupsd* user.  This is done to improve security, but at a cost of Agony Units.

---

### Post by mattlach on 2014-10-21
> **tgalati4 said:**
> Testing shutdown procedures is tedious.  I use a 100-watt light bulb, so I can see the load (I know it is exactly 100 watts with a Power Factor of 1.0), but keep the server plugged into another (non-ups) outlet.  I can then watch the messages, calculate the runtime (compared to the actual measured) and keep the server protected from a sudden poweroff.  Then I perform this test 10 times (charging the battery in between and allowing the MOSFETs to cool--important) to check that the timing is correct and consistent.  If the timing is messed up, you get premature shutdowns--which are bad.

What user is *apcupsd* running as?  When you run the script manually, you are in a root terminal.  So a difference in user would account for the script to fail while under the *apcupsd* user.  This is done to improve security, but at a cost of Agony Units.

Yeah,  thank you, I checked that.

According to top, it is running as root:
```
                                                                                
  905 root      20   0  103372    700    460 S  0.0  0.6   0:00.19 apcupsd                                                                                   

```

And this is further confirmed by that the echo messages the script sends are showing as coming from root:

```

Broadcast Message from root@apcupsd                                            
        (somewhere) at 12:39 ...                                               
                                                                               
Power failure on UPS SUA1500. Running on batteries.
```

So it should be the same from a users and permissions perspective.

Good call on having the server connected to a different outlet.   I didn't think this would be needed, as I was standing right there and could plug the UPS in if needed, but I obviously wasn't accounting for the killpower command, after the 9 minute delay.   

Would there be any reason why it might ignore environment variables?  Maybe I should use the full path "/usr/bin/plink"?

---

### Post by tgalati4 on 2014-10-21
It's a mystery.  It's always a good idea to include the full path.  You could include an *env* to print out the environment variables in the script.  I have not used *plink* or *pfsense*, nor have I tried to use *freenas* to snooker an EXSi server into a safe shutdown.  I would have built a proper Xen server and then all the linux frameworks would work as you expect.

A diagram of your topology would be helpful to come up with a more elegant solution.

It could also be a security/authentication issue.  When you are in a root terminal, you have gone through an authentication process that then allows you to execute scripts, binaries, etc.  Inside a running process, even root, there are some inter-process limitations that prevent root actions--presumably to improve security of a system against a rogue root script.

---

### Post by koenn on 2014-10-24
mattlach,
AFIACS, you're on the right track. Actually, I've been setting up something similar, but with the complication that I have 1 apcupsd monitoring multiple UPSes, and I haven't implemented any shutdown yet - I have apcupsd send me mail.

Which is a very convenient way to test a setup. If you just put a mail command in your doshutdown script, you van easily see whether the commands in 'doshutdown' are executed : you'll get that mail. If you don't have a suitable mail infrastructure, just put some echo commands and redirect them to a file.

appcontrol passes 2 to 4 parameters to eventhandling scripts (such as doshutdown) so you might use those to see stuff happening. 
So your testversion of the doshutdown script could be something like this

```

#!/bin/bash
#
# This shell script is to be called by /etc/apcupsd/apccontrol 
# and inherits commandline params from it

date > /path/to/file
echo "$0 called by appcontrol with params $1 $2 $3 $4 " >>  /path/to/file
 
exit 99 

```

actually, you could also insert that in a number of other eventhandlers to see if they get triggered instead.

Now if a powerfailure triggers apccontrol to call doshutdown, you'll see it happen. If that worls, you can start deugging your plink statement.

---

### Post by koenn on 2014-10-24
(had a quick look through my notes and found this - so  just in case you missed it :  )

the thresholds for doshutdown are set in the apcupsd conf file 
```

MINUTES 2
BATTERYLEVEL 1
TIMEOUT 0

```
This says : 'doshutdown' when BATTERYLEVEL reaches 1% or Runtime Remaining is (less than) 2 minutes, which ever happens first. IIRC, TIMEOUT is "time since powerfailure (+ DELAY)", 0 disables it. (check the comments in the config file to make sure.)

---

### Post by mattlach on 2014-10-24
> **koenn said:**
> mattlach,
AFIACS, you're on the right track. Actually, I've been setting up something similar, but with the complication that I have 1 apcupsd monitoring multiple UPSes, and I haven't implemented any shutdown yet - I have apcupsd send me mail.

Which is a very convenient way to test a setup. If you just put a mail command in your doshutdown script, you van easily see whether the commands in 'doshutdown' are executed : you'll get that mail. If you don't have a suitable mail infrastructure, just put some echo commands and redirect them to a file.

appcontrol passes 2 to 4 parameters to eventhandling scripts (such as doshutdown) so you might use those to see stuff happening. 
So your testversion of the doshutdown script could be something like this

```

#!/bin/bash
#
# This shell script is to be called by /etc/apcupsd/apccontrol 
# and inherits commandline params from it

date > /path/to/file
echo "$0 called by appcontrol with params $1 $2 $3 $4 " >>  /path/to/file
 
exit 99 

```

actually, you could also insert that in a number of other eventhandlers to see if they get triggered instead.

Now if a powerfailure triggers apccontrol to call doshutdown, you'll see it happen. If that worls, you can start deugging your plink statement.

Thank you for that.   My next test is going to be to send the stderr and stdout from my plink line to a file, trigger it, and then see what is going on.

I have confirmed that the environment is not my issue. Printing the environment variables to a file showed that everything that was supposed to be in the path was there.  I even changed it to a full path of the plink bin, and that still didn't help.

> **koenn said:**
> (had a quick look through my notes and found this - so  just in case you missed it :  )

the thresholds for doshutdown are set in the apcupsd conf file 
```

MINUTES 2
BATTERYLEVEL 1
TIMEOUT 0

```
This says : 'doshutdown' when BATTERYLEVEL reaches 1% or Runtime Remaining is (less than) 2 minutes, which ever happens first. IIRC, TIMEOUT is "time since powerfailure (+ DELAY)", 0 disables it. (check the comments in the config file to make sure.)

Thank you, yeah, I already have my apcupsd.conf file set up the way I like it.   Only thing I ahve left to figure out is why plink isn't executing properly when apcupsd launches doshutdown, (but when I launch it manually it works fine)

---

### Post by mattlach on 2014-10-24
Finally solved it!

The issue was that the environment that the doshutdown script executes in for some reason lacks NAME, USERNAME and HOME environment variables, so plink can't find the file containing the host key.

I solved this by adding a "export HOME=/home/matt" line to point to my home dir right before the plink command in the script, and now everything works! :)

For reference, if anyone else tries to do this, my doshutdown script looks like this:

```

#!/bin/sh
export HOME=/home/matt
plink -ssh -2 -pw password root@xxx.xxx.xxx.xxx "/sbin/shutdown.sh && /sbin/poweroff"
exit 99
```

(oh, and of course, replace my home user name for the user your key file is stored under)

This feels a little bit like a hack, but at least it works!  Been struggling with this problem for a month.  Happy to have it working!

---

### Post by tgalati4 on 2014-10-24
I'm glad you have it sorted.  I couldn't sleep.  I had a feeling it was an *env* issue.

---

