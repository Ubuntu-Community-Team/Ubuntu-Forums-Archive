---
title: "Old pcs recycling project"
date: 2010-11-05
forum: Testimonials &amp; Experiences
---

### Post by pms666 on 2010-11-05
Hi there, I got interested in Ubuntu as I wanted to bring new life to an old Fujitsu Siemens laptop (Amilo D8830) and old pos desktop, Fujitsu Scenic P300 salvage.
 
I will use these machines myself to learn linux music software and linux in general, and probably later end up giving them away if some poor punks need a computer for some reason.
 
The biggest problem has been is that I have a Huawei E1552 usb modem as the only network option and that made this new linux hobby a real struggle. Having no internet was not an option... I was aware about modeswtich etc but with no access to LAN or even wireless and having to play with memory stick it was not going to happen and I gave up :(
 
I downloaded many distros but nothing worked with the Huawei E1552... until yesterday! :D
 
Finally, I got the new Ubuntu 10.10 running on the Amilo and E1552 modem worked immediately. Looks neat, everything "works" and I like it, etc.... BUT:
 
Problem is that 10.10 as it is (apparently) too heavy for 2,66 Ghz, 512mb machine. This is the reason why I have not bothered to install it to the Scenic yet. (2,4ghz, also 512mb).
 
So.. the options for the next step are:
 
-Somehow slim down 10.10 to run better with 512mb. Looking for good ideas at the moment! (?)
 
-Make a LAN connection somehow between the machines as I got the damn Huawei running on the Amilo. I just realised I have a crossover cable somewhere. If that worked, I could make some progress with the other machine too. Cant be bothered to have 2 old computers with the SAME problem. Also, with LAN connection, installing modeswitch stuff for the huawei could be an option I would consider again. 
 
-Find another lighter distro that works with the Huawei. 
 
**Ideally I want these computers to run RT kernel, run something very light like puppy in RAM, work with Huawei E1552 and Ubuntu Studio music software. **
 
The network is the biggest bottleneck but at least I am getting somewhere now. New Lucy Puppy 5.2 looked very cool. Ideally I want something like Puppy Studio 3.0 which offers everything I want... and again: Damn Huawei, I mean really, ffs...
 
Any feedback or ideas would be extremely welcome!

---

### Post by ibizatunes on 2010-11-05
lubuntu is ubuntu ,with a but lighter

---

### Post by pms666 on 2010-11-05
Got few of those lubuntus already. And apparently the latest lubuntu skipped this huawei on kernel so I will skip it as well, i read somewhere the 10.10 lubuntu still expects the drama with modeswitch... Annoying.

---

### Post by armandh on 2010-11-05
more than likely there may be a video and or shared mem issue

I've got 9.10 running on a P-III 933 / 133 FSB 
512 meg mem and a 64 meg AGP video card
Twirly cube and all

But a 600 P-III 100 FSB 256 meg mem
and a 16 meg AGP video card 
I used Puppy

try 8.04 [the pre compiz  Ubuntu]

some time it is easier to just get a different modem.

---

### Post by pms666 on 2010-11-06
> **armandh said:**
> more than likely there may be a video and or shared mem issue

try 8.04 [the pre compiz  Ubuntu]

some time it is easier to just get a different modem.

Video mem issue?? Now 10.10 uses 244ish mb memory, and for an old machine its not good if there is more than firefox running.

I tried 8.04.4 I reckon. No success with huawei though. I read somewhere that should have worked with the modem and be lighter but NO. Damn huawei. Cheers anyhow!

---

### Post by Objekt on 2010-11-06
Not sure if this will help you, but I run Crunchbang Linux on a machine that is older and crappier than either of yours.  It is a Compaq Presario 710.  Specs include a 1.0 GHz Duron CPU with only 256 MB RAM.

Initially, I tried Xubuntu on my Presario, but the XFCE desktop was just too slow.  I also tried Puppy Linux, which ran well.  I didn't stick with Puppy because it's just too different.  I'm used to the Ubuntu way of doing things, and didn't want to learn a different distro just for one machine that I hardly use anyway.  

The current release of Crunchbang is based on an obsolete version of Ubuntu (9.04), so I can't recommend it.  Ubuntu 9.04 has reached "end of life" already, which means no more updates.  Presumably this means Crunchbang doesn't get updates either.  There is a new Crunchbang release in the works, but it's not out yet, so that doesn't help either.

I don't understand what "modeswitch" is or why it's a problem.  Could you explain please?

For the Scenic: You could install standard Ubuntu 10.10 on the Scenic, since you know the Huawei device will work with 10.10, then use the Openbox desktop instead of GNOME.  Any reason that wouldn't work?  I'm pretty sure 10.10 will install on a machine with only 512 MB RAM.

As for sharing the Internet connection between the machines: This should be fairly easy, if you get Ubuntu 10.10 on both machines.  You probably don't need a crossover Ethernet cable.  NICs have been able to automatically switch the signaling for years (called Auto MDIX).  There's a good chance even your old laptops can do it.  But, you can certainly use the crossover cable if that's all you have.

---

### Post by pms666 on 2010-11-06
> **Objekt said:**
> 
I don't understand what "modeswitch" is or why it's a problem.  Could you explain please?


Computer sees the modem as a memory stick. Modeswitch thingy is supposed to solve this and make ubuntu see it as a modem but its not funny when you have to mess around with a memory stick to install those modeswitch thingies on a new OS... silly situation, I know. USB modem users are not apparently a priority.

---

### Post by lancest on 2010-11-06
I heard the Huawei stuff is kind of faulty- maybe inconsistent in configuration. Hard to support. 

My Huawei E620 for 3G works perfectly on 10.10 though. 

It no longer mounts to the desktop as storage as in earlier versions. 

Still shows up as a storage device in Nautilus Computer view though. 

 Auto connects and usually stable.  
 

Meerkat's .35 kernel is really great for me.

---

### Post by Objekt on 2010-11-06
> **pms666 said:**
> Computer sees the modem as a memory stick. Modeswitch thingy is supposed to solve this and make ubuntu see it as a modem but its not funny when you have to mess around with a memory stick to install those modeswitch thingies on a new OS... silly situation, I know. USB modem users are not apparently a priority.

Nor are floppy drive users - one has to enable support manually, and then lock a package (udisks) to an earlier version, lest "upgrades" should break it.

I haven't used a modem, USB or dialup, on any of my computers in years.  But I rather suspect that if I did have a dialup modem, it wouldn't work under Ubuntu 10.04.  The Ubuntu devs seem to have a thing for breaking functionality of old hardware, whether by design or accident.  Meanwhile, Windows 7 did not require any tweaking to allow use of my 3.5" diskette drive, and I suspect it would be happy to run a dialup modem as well.  I don't get it.  

That's sidestepping the whole issue of softmodems and other driver-dependent devices.  I assume the Huawei E1552 is not tied to a Windows-only driver package, else you wouldn't have it working at all.

I found an article addressing use of the Huawei E1552 under Ubuntu 9.04.  Perhaps it could apply to Ubuntu 8.04.4 LTS as well?  It seems worth a try.  You wouldn't even have to install, you could just boot up a live CD session of 8.04.4 on the Scenic & try the commands in the article.  Link:

[http://www.wabama.com/2010/02/12/setup-huawei-e1552-on-ubuntu/]("http://www.wabama.com/2010/02/12/setup-huawei-e1552-on-ubuntu/")

Except, I guess you wouldn't be able to install the required package (udev-extras), given that you can't get online in the first place.  Unless you can first get Internet connection sharing working.

---

### Post by mastablasta on 2010-11-08
> **pms666 said:**
>  
-Somehow slim down 10.10 to run better with 512mb. Looking for good ideas at the moment! (?)
 
Have you tried turning off desktop effects? You didn't say what graphics card you have (maybe it needs better drivers). i don't know about 10.10, but 10.04 runs quite nicelly on a 1.2 GHz, 224 MB RAM....
 
>  
-Make a LAN connection somehow between the machines as I got the damn Huawei running on the Amilo. I just realised I have a crossover cable somewhere. If that worked, I could make some progress with the other machine too. Cant be bothered to have 2 old computers with the SAME problem. Also, with LAN connection, installing modeswitch stuff for the huawei could be an option I would consider again. 

 
If you use cables switch is easier to handle. switch is cheap.
 
> 
-Find another lighter distro that works with the Huawei. 

 
As another option you could just install LXDE or XFCE on your current Ubuntu. but again with your computer configuration it should fly...

---

### Post by pms666 on 2010-11-08
64MB ATi Radeon 9000 Mobility graphics card
 
[http://www.itreviews.co.uk/hardware/h571.htm](http://www.itreviews.co.uk/hardware/h571.htm)
 
it was the 2,66 mhz one.

---

### Post by ivanovnegro on 2010-11-08
I dont know if my suggestion could help you as I dont no about your issue with Huawei, but this distribution is in my opinion really lightweight and very fast even on a system with less than 256 MB Ram, its called [Antix]("http://antix.mepis.org/index.php?title=Main_Page"), based on Debian/MEPIS. For me its running better as the LXDE Desktop Environment on really old machines. ****

---

### Post by mastablasta on 2010-11-08
mobility Radeon really seems to have issues :-)
 
perhaps turn desktop effects off, remove background pic. maybe it will help.
 
also maybe switch to simpler theme such as clearlooks.

---

### Post by pms666 on 2010-11-08
New problem! Screen turns slowly WHITE on boot from the purple screen with ubuntu logo. :confused:

I have another install of the same 10.10 on this amilo that works so I am going to mess up this one as well. :D Not sure how i even messed up the other one.

---

### Post by rhorstkoetter on 2010-11-08
> Problem is that 10.10 as it is (apparently) too heavy for 2,66 Ghz, 512mb machine. This is the reason why I have not bothered to install it to the Scenic yet. (2,4ghz, also 512mb)
I had great success utilizing compcache [1] with low memory configurations running Ubuntu 10.10. It's possible to configure compcache as priority #1 swap with just an upstart job. Let me know if you're interested in details.

Best,
R

[1] [http://code.google.com/p/compcache/](http://code.google.com/p/compcache/)

---

### Post by pms666 on 2010-11-10
I messed up a few things and wanted to test many things and now I installed 10.10 fresh again. I am trying this now:

[http://www.howtogeek.com/howto/ubuntu/install-xfce-xubuntu-on-ubuntu-linux/]("http://psychocats.net/ubuntu/xubuntu")[]("http://www.psychocats.net/ubuntu/purexfce")

---

### Post by pms666 on 2010-11-11
I made some notes of the memory use while tweaking a fresh install of Ubuntu 10.10 on Amilo D8830 (2,66Mhz, 512Mb). The MB amount is what System Monitor says after booting and settling down:
 
[INDENT]1. Live CD:
[/INDENT] 
~189MB
 
-Quite slow
 
[INDENT]2. Installed Ubuntu 10.10:
[/INDENT] 
~155MB
 
-Quite slow on an old computer
 
[INDENT]3. Installed all the updates that Ubuntu wants, and rebooted the system again:
[/INDENT] 
~158MB
 
-Meh. But I still expect this to do something positive. I say this as a former Vista user so an "update" usually means something catastrophic. And the point was to lose weight here so I expect some drawbacks. More diet coke with bacon and cheese!
 
[INDENT]4. Adding Xubuntu to an existing Ubuntu
[/INDENT] 
[http://psychocats.net/ubuntu/xubuntu](http://psychocats.net/ubuntu/xubuntu)
Took a while to download the stuff. Rebooted (did not log out to "session" as the link suggested), and the result was:
 
~118MB
 
-Just lost more than 1/4 of the weight. This is what I call progress!
 
-I did not have that much time yesterday to play around with, but everything seemed to work quickly and looked overall very similar, although windows were BLUE and so was the background. But this is trivial and last a very short time.
 
-The Startup Application preferences are somewhere else as opposed to where they are in Ubuntu. I didnt have time this morning to find it but this is the next tweak...
 
-I did burn Xubuntu 10.10 as well but I reckon the disk or burn was bad and the installer crashed so I decided to try XFCE the way I did. Not sure if fresh install of Xubuntu is diffent or better somehow? I guess I will try that again just to see if theres any difference. But I ran out of cdrs for now :D I got a flat full of Linux cds now that do not work with Huawei E1552. That solves my holiday shopping at least.
 
-More ideas?

---

### Post by pms666 on 2010-11-11
I made some notes of the memory use while tweaking a fresh install of Ubuntu 10.10 on Amilo D8830 (2,66Mhz, 512Mb). The MB amount is what System Monitor says after booting and settling down:

[INDENT]**1. Live CD:**
 
[/INDENT]~189MB 
[INDENT]**2. Installed Ubuntu 10.10:**
 
[/INDENT]~155MB
 
-Quite slow on an old computer
[INDENT]**3. Installed all the updates that Ubuntu wants, and rebooted the system again:**
 
[/INDENT]~158MB
 
-Meh. But I still expect this to do something positive. I say this as a former Vista user so an "update" usually means something catastrophic. And the point was to lose weight here so I expect some drawbacks. More diet coke with bacon and cheese!
[INDENT]**4. Adding Xubuntu to an existing Ubuntu**
 
[/INDENT][[COLOR=#444444]http://psychocats.net/ubuntu/xubuntu[/COLOR]]("http://psychocats.net/ubuntu/xubuntu")
Took a while to download the stuff. Rebooted (did not log out to "session" as the link suggested), and the result was:
 
~118MB
 
-Just lost more than 1/4 of the weight. This is what I call progress!
 
-I did not have that much time yesterday to play around with, but everything seemed to work quickly and looked overall very similar, although windows were BLUE and so was the background. But this is trivial and last a very short time.
 
-The Startup Application preferences are somewhere else as opposed to where they are in Ubuntu. I didnt have time this morning to find it but this is the next tweak...
 
-I did burn Xubuntu 10.10 as well but I reckon the disk or burn was bad and the installer crashed so I decided to try XFCE the way I did. Not sure if fresh install of Xubuntu is diffent or better somehow? I guess I will try that again just to see if theres any difference. But I ran out of cdrs for now :grin: I got a flat full of Linux cds now that do not work with Huawei E1552. That solves my holiday shopping at least.
 
-More ideas?

---

### Post by rhorstkoetter on 2010-11-11
> -More ideas?
Again (not sure why you just ignored my previous post), low memory machines feel slow as they're "swapping" quite fast. This is due to the fact that swap space is significantly slower than "real" memory. 

That said, as mentioned previously, I'd have a look at virtually increase the amount of "real" memory and this can easily be done with compcache (see link above). That way you're able to even run a KDE or GNOME desktop at acceptable pace. I actually did so with a Pentium 4 machine, 2.4 GHz + 512 MB Ram which is pretty similar to your configuration and I can tell you that the difference in system performance is significantly.

---

### Post by cascade9 on 2010-11-11
> **Objekt said:**
> Not sure if this will help you, but I run Crunchbang Linux on a machine that is older and crappier than either of yours.  It is a Compaq Presario 710.  Specs include a 1.0 GHz Duron CPU with only 256 MB RAM.

Initially, I tried Xubuntu on my Presario, but the XFCE desktop was just too slow. 

Dont blame Xfce, blame xubuntu. 

I've got a machien slower than that- P3 866, 256MB, Intel i810 chipset + video (bluegh!). Its hardly a speed emon, but its quite useable..far more usable with a Xfce version thats not loaded down with all sorts of uneeded junk. I've run xubuntu 8.10, 9.04, 9.10, debian xfce (testing + lenny) and sidux xfce on that machine, and debian and sidux eat xubuntu alive for speed. 

@pms666- minimal install then get the xfce4 package. You could be shocked at the difference. 

You could try removing xubuntu-desktop and installing just xfce4, I havent tried that. It would be easier than getting the alternate install CD, burning it, installing, etc..

---

### Post by pms666 on 2010-11-11
> **rhorstkoetter said:**
> Again (not sure why you just ignored my previous post), low memory machines feel slow as they're "swapping" quite fast. This is due to the fact that swap space is significantly slower than "real" memory.

Oops, thanks again for that! Was not ment to seem as I ignored it, I did look at the link quickly when you posted but now I am starting from scratch again and I want to do really simple tests first. I will definitely look into that if you reckon its easy to do?  

I am not in a horry and learn this linux stuff when I have time so bear with me :) And thanks again!

---

### Post by pms666 on 2010-11-11
> **cascade9 said:**
> 

@pms666- minimal install then get the xfce4 package. You could be shocked at the difference. 

You could try removing xubuntu-desktop and installing just xfce4, I havent tried that. It would be easier than getting the alternate install CD, burning it, installing, etc..

The problem is the huawei modem I use. I did download Ubuntu Minimal, and the installer wants to get online immediately. I should have known as the .iso file was very small. And AFAIK ubuntu minimal 10.10 only comes with an option to install with a readily working internet connection? This huawei e1552 modem does not have that feature :P

Very stupid situation and practically I am trying to achieve exactly what you said the wrong way around.

---

### Post by rhorstkoetter on 2010-11-11
> **pms666 said:**
> Oops, thanks again for that! Was not ment to seem as I ignored it, I did look at the link quickly when you posted but now I am starting from scratch again and I want to do really simple tests first. I will definitely look into that if you reckon its easy to do?  

I am not in a horry and learn this linux stuff when I have time so bear with me :) And thanks again!
I recently experimented quite a lot with compcache and just SSH'd into one of the machines it's running on. All you need to do is creating /etc/init/compcache.conf
```
# http://code.google.com/p/compcache/

start on runlevel [2345]
stop on runlevel [!2345]

pre-start script
modprobe ramzswap && /usr/lib/initramfs-tools/bin/rzscontrol /dev/ramzswap0 --disksize_kb=$(awk '/^MemTotal:/ {print $2}' /proc/meminfo) --init && swapon -p 0 /dev/ramzswap0
end script

post-stop script
swapoff /dev/ramzswap0 && /usr/lib/initramfs-tools/bin/rzscontrol /dev/ramzswap0 --reset && modprobe -r ramzswap
end script
```
Then reboot and check proper functionality with
```
ruf@kellerknecht:~$ sudo swapon -s
Filename				Type		Size	Used	Priority
/dev/dm-1                               partition	2002940	0	-1
/dev/ramzswap0                          partition	1025708	0	0
```
This is what it should look like. /dev/ramzswap0 is the compcache I'm talking about with swap priority 0 (over -1 of regular swap). The upstart job I posted above will create a compcache partition worth of equal as much of uncompressed data as your actual RAM (in my case 1GB, in your case 512MB).

Feel free to ask if you need further advice and have a lot of fun!

---

### Post by pms666 on 2010-11-24
...

---

### Post by pms666 on 2010-11-24
Update:
 
**Amilo:**
 
Thanks everyone, this old Amilo laptop runs fine with Ubuntu 10.10, Xubuntu desktop and Huawei E1552. I like it the way it is. I also tried Kubuntu 10.10 but the modem did not work in that (also read somewhere it doesn't work on Lubuntu 10.10 either). 
 
So for now this Xubuntu setup is the one I am going to stick with. Looks and works as nice as Ubuntu, modem works, seems faster and lighter. Only difference is different menus (not worse), and no start up application thingy that Ubuntu had (I wanted to remove programs that I will not use). But - it runs just fine, I gained a new machine from a laptop that I almost binned. It works better than my newer computer for web use, torrent download, and cd burning at least, so this was a success :KS
 
So now I am going to focus on the next machine:
 
**Scenic:**
 
I want it to run with Puppy Studio:
 
[http://www.murga-linux.com/puppy/viewtopic.php?t=60483](http://www.murga-linux.com/puppy/viewtopic.php?t=60483)
 
I downloaded the 'lite' version, only because I had problems with the download and that one finished succesfully first. (not sure why, all versions somehow stopped downloading all the time, same happened on my Vista machine) But for starters, it has more than enough to play with!
 
I know I should emigrate to that puppy forum - but I rather have everything here as well so continue if you are interested. I only messed around for bit and I only have the first expressions at the moment:
 
- Seems exactly what I wanted Linux to do, I will probably buy my next computer to work on this!
 
- On first try I was not able to install it on harddrive. I probably messed up the grub or something - will try again tonite. Puppy Studio runs brilliantly on Live CD tho :D Puppy installer was probably more complicated than me.
 
- Jack crashed when opened. This Scenic P300 has probably the worst audio card so this is not a surprise! 
 
I will try next:
 
- making a connection to the Amilo machine via crossover cable and share internet connection.
 
- and/or install modeswitch stuff for the Huawei E1552. I am not too bothered about making the modem work if its too complicated - i am happy if I can share files etc so this is not as big deal as it was on Amilo.
 
- Connect Evolution MK-225C, a 2-octave USB keyboard
 
- Connect Line 6 UX1 TonePort (its newer version is called UX1 Pod Studio) and try that as the audio device
 
ANYHOW - One machine running just fine, another one on the way.

---

### Post by lancest on 2010-11-24
> **pms666 said:**
>  I gained a new machine from a laptop that I almost binned. 

[COLOR="Green"]Green![/COLOR]

---

### Post by pms666 on 2010-11-24
> **lancest said:**
> [COLOR=Green]Green![/COLOR]

I must get a 4x4 car the size of a house to compensate the size of my... carbon footprint.

---

### Post by mastablasta on 2010-11-25
is it really greeen to use old parts that in some cases use more energy than new ones? ;-)

---

### Post by pms666 on 2010-11-25
After another day:
 
Puppy does not work like ubuntu. Its something completely different. 
 
Probably I dont need to install it at all, if there is a saved session anywhere on the harddrive, this puppy studio boots extremely fast. Also, as I only have to sacrifice the CD drive to boot it, it does not matter as its not a CD _writer_ and its useless anyhow :P 
 
So - probably I will install Xubuntu 10.10 on Scenic as well, and use puppy for the music stuff and boot from the live CD for now. And try the "frugal" install with xubuntu.
 
Next problem is the crossover cable stuff, how do I connect a Xubuntu 10.10 machine with a Puppy511 based machine... off to google!

---

### Post by pms666 on 2010-11-25
> **mastablasta said:**
> is it really greeen to use old parts that in some cases use more energy than new ones? ;-)
 
Who cares? When environmentalism turned apocalyptic, I started to label it under religion.

---

### Post by cascade9 on 2010-11-25
> **mastablasta said:**
> is it really greeen to use old parts that in some cases use more energy than new ones? :wink:

Is it really green to update hardware just becuse there is more power efficent models? 

With all resources used in manufacturing and transport (arcoss half the world  in most cases)  I'm not sure. With the disposal of the 'obsolete' hardware, which normally involves shipping it back to china so that people can use blowtorches to soften motherboards, etc so that the chips can be removed, wires stipped, etc, I really dont think that a new laptop is any more green than using the old one.......and probably quite a bit less green. 

BTW, anyone who has any intrest in seeing what recycling computers can do, find a documentary called 'Manufactured Landscapes'.

> **pms666 said:**
> Who cares? When environmentalism turned apocalyptic, I started to label it under religion.

I label the peoples perception of sceince under 'reilgion' these days. :lolflag:

---

### Post by mastablasta on 2010-11-25
> **pms666 said:**
> Who cares? When environmentalism turned apocalyptic, I started to label it under religion.
 :lolflag:
 
 
ok. now this really made my day....

---

### Post by pms666 on 2010-11-25
Weirdest thing I have heard was the german decision to give 2500 euros to everyone who scraps their 10 (or 15 was it..) year old car and buys a new one. 

I mean REALLY? All the manufacturing, metal processing, recycling :), logistics, hassle etc and get a new one? Environmental? Thats hardly even zero sum game. 

And the worst case scenario is that a person buys a Toyota Prius. They use children to mine lithium in Africa, ship to Canada for processing, make batteries out of it in China, ship em to Japan to be assembled into a car, and the car is shipped over here to Finland to be driven by some moron who likes to drive 'environmental'. 

Even if the greenmobile was emission-free, all this Western scene of being a smug hippie is rendered pointless if 1 percent of Chinese people want a refrigerator.

I do not want to spread nihility, want some reality check. Some people do not propose these ideas of "better to run new stuff as it is more efficient"-bollocks just for fun, its part of the public spending, politics and economy. For example, I walk to work and like to use stuff until they are ready to be binned. Thats good enough. And just because morons being smug annoy me, I might get an SUV. I reckon common sense is lot better for environment than all these weird ideas I hear in media and everywhere.

But also, I might connect this recycled Amilo now to that recycled Puppy Studio desktop over there ->

---

### Post by pms666 on 2010-11-28
I have an idea!

I have 3 computers now - Scenic and Amilo I have been talking about. And also a newer HP Pavilion dv6500 with VISTA HOME :D that has wireless - So what I want to do is:

Keep that damn Huawei modem either on Scenic or the Amilo, it seems to run better on Amilo with Xubuntu 10.10 than on this Vista Pavilion laptop and get a wireless router or something so that I could have no cables as I want at least one of the laptops that way. I have no idea what kind of router would work as I never have messed around with them and I am skint at the moment so this needs to be cheap.

Not sure which way to do this. Most sensical would be on the scenic as its most stationery and maybe on Amilo as its a laptop and might use less electricity as I would live the one with modem running all the time?  

Also, I might keep vista on this HP as I want one computer to run Line6 guitar software and I like the Windows media center as the computer came with remote control. Also, im getting my head around slowly how the Puppy Studio works now - So one idea would be to run Line6 gearbox with Reaper on windows, that should work for recording. And when I need more power, I would run the same files on Puppy Studio as it has Reaper too, and probably have tons of more power. At the moment I think it could work that way and it would be a brilliant setup at least in theory. Also, if the guitar modelling stuff on Linux and media software is as good as media center, I could bin the Windows the last time in my life. That would be nice as I really hate using Vista, and somewhat ashamed to walk outside if anyone knew.

Also I might get another salvage computer, a laptop with broken screen which might be fun to connect to my 40" rear projection tv - that would be a fun media computer too as I have a spare wireless keyboard and mouse :)

---

### Post by pms666 on 2010-11-28
The topic was Ubuntu testimonials and experiences. 

So this far I would list my expriences with different OS even only some of them are Ubuntu, sorry:

-Vista Home Basic: Media Center is good, everything else is annoying, horrible debate about everything I want the computer to do. This is not the way I want to be treated in any interaction, least with a computer.

-Ubuntu 10.10: The first Linux OS I found that works with my Huawei 10.10 modem. The modem support is the main issue why everything is so hard and this pc recycling project has such slow progress. 10.10 seemed like a very neat OS and I liked it, but it was a bit slow on an old Amilo.

-Xubuntu 10.10: Just like Ubuntu 10.10 but uses lots less memory and some details in different places. The best one this far easily.

-Puppy Studio 3.1: On an idea level, this is what I have been looking for, its exactly what a music computer needs. If it works in real life as good as I hope I am one happy bunny. I have only tried it briefly, and its a bit confusing but I do not mind, this is fun and I am not in a horry. One reason it is so brilliant is the puppy aspect, but the puppy makes it confusing as I am new with Linux, and Ubuntu is so easy that everything seems hard next to it. I have to figure out how to networking goes... bizarre for a first timer. And also, why does it have to work with a single click and not double click? Annoying as hell - what is the point and using 50% less clicks hardly makes OS lighter :P . Probably I can set it up somewhere. Lets learn. This is so damn fast, even on the crappiest of my crappy old computers, everything works lightning fast and it boots stupidly fast. I have not installed it on harddrive yet but at the moment I feel there is no need for it either. 

So for me an ideal OS would be puppy studio with xubuntu desktop or something. And I think I read somewhere you can do it, lets try that one day. It might be heavier but I am sure its worth a try at least. Luckily i am only 32 years old so I reckon I have enough time to make everything work one day. If I only had a different modem... Why didn't I hear of Linux music software before I got this modem deal? That would have been soooo much easier.

---

### Post by mastablasta on 2010-11-29
then again for older notebooks you might consider USB dongle or PCMCIA card. there is plenty out there that work great with Linux. i got my self a TP Link PCAMCIA card for a notebook that was written off by my uncle and he gave it to my wife. i changed the battery, went with preinstalled windowsXP for some time until the darn thing came to a half almost. i mean 10-15 minutes just to boot (issue is not enough ram - 256MB). i couldn't upgrade the ram, so finnaly windows went off Ubutnu 10.04 is not on. works lovely. maybe a bit slow but still much faster than windows boot is not 1 minute. and everythign works just fine (appart from few keys i don't use anyway).
 
i actually wanted to use XFCE or Lubutnu on it. however XFCE ket crashing while llubutnu recognised even less keys and battery lasted much shorter. 
 
Ubuntu, surprisingly, increased batery  time from 1.5 hour under windows to about 2.5-3 hours.

---

### Post by pms666 on 2010-11-30
Sharing internet from Xubuntu to Puppy was damn easy!

On Xubuntu 10.10 (EDIT: When already online with Huawei E1552)

 Click on networking icon on top right - VPN Connections - Configure VPN, that opens next window: Wired - Auto eth0 - Add - Ipv4 Settings - Method - Shared to other computers - Apply

On Puppy machine:

Right click on bottom right - Setup Networking - eth0

Voila!

---

