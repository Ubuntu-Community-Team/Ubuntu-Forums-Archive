---
title: "Is Jack breaking up with me?"
date: 2012-08-14
forum: Ubuntu Studio
---

### Post by swedstal on 2012-08-14
Chagrined, I slink back to this forum. It has been about two years since I sought help getting my Ubuntu Studio system set up. It was really a snap and I've enjoyed using the many wonderful programs like Ardour, Rosegarden, Hydrogen, etc. for my musical projects. Not only that, the support I received from this forum and others was exemplary.

After being away from my computer for about a month, Jack will no longer start. I can think of no major changes I made to my system, except for blindly clicking "Install Updates" from Update Manager whenever prompted. I have searched the help docs but had no luck.

The first error in the start up message is: "firewire ERR: Error creating FFADO streaming device"


My interface is a Phonic Helix Board 18 Firewire MkII. I will post my Jack set up along with my start up error message.

Many thanks in advance for any help!

[IMG]http://i.imgur.com/ciKRQ.gif[/IMG]

[IMG]http://i.imgur.com/BhV5W.gif[/IMG]

---

### Post by BcRich on 2012-08-14
Hi swedstal
The title of this thread really cracked me up :D Thanks for that!
I remember having a similar problem with JACK (I'm also guilty of blindly subjecting my Ubuntu installation to unsolicited copious updates). Although I'm using an external USB device maybe there are similarities with your problem. 
Basically QjackCtl could not initialize because something else was trying to access my sound device before it. It turned out that each time the client failed to start it would leave an instance of jackd running in the background, I subsequently had to manually kill jackd before starting QjackCtl and my problem was solved.
I realize this is somewhat of a trivial suggestion, and you've probably already thought of checking what processes where running post crash. But Nonetheless maybe it helps?

---

### Post by CrocoDuck on 2012-08-14
Hi. Was asked to overwrite a configuration file during update? How about the firewire configuration, have you edited one of $HOME/.asoundrc, /etc/asound.conf (if any) or /usr/share/alsa/alsa.conf ? If you have followed a tutorial when you have set firewire up, repost it.

---

### Post by swedstal on 2012-08-14
> QjackCtl could not initialize because something else was trying to access my sound device before it.The only thing that looks like it could be an issue is the "pulseaudio" process. I don't really know what this is, but I recall seeing it in another post. When I kill this process I am still getting the same error message as before. Interestingly enough each time I try to start Jack with Qjackctrl the pulseaudio process starts again. Any chance this could be the culprit?

> 
If you have followed a tutorial when you have set firewire up, repost it.     I have not recently made any changes to any config file. I generally keep my grubby paws out of these sensitive areas unless I have very clear instructions. It has been about two years since I set this machine up and I'm having a hard time remembering exactly what I did. As I recall, this interface was pretty much plug and play. I spent a decent amount of time tuning the settings in Jack, but I think it pretty much worked for me right away.

Necessity truly is the mother of invention (or education in my case). Once I got my system running well I basically stopped learning about Ubuntu related things. As a scientific person it pains me to admit to thinking of my current system as a black box, but the stability was so great I was never forced to learn anything more. Therefore I am still very much a beginner to these issues despite having used Ubuntu for years.

Thanks, all, for your help and patience!

---

### Post by jejeman on 2012-08-15
To eleminate puleasudio turn it off like this
```
echo "autospawn = no" > ~/.pulse/client.conf && pulseaudio -k
```
This will set pulseaudio not to automaticly start again.

*warning
If you have had set custom client.conf this will erase it. Then just add your self the autospawn line.

Pulseaudio tends to bug jack, specialy pulseaudio-jack-sink. I also use firewire device, and once after quiting qjcakctl forcefully I couldn't get jack to run with ffado again. Didn't want to mess around so I reinstalled U.Studio (I had backup and it was fresh install anyway). Then first thing what I did was to uninstall pulseaudio-jack-sink. After that jack and qjacktl was closing fine. Later while workong with pci card, pulseaudio got even more buggy, start to loose hardver device, so I just turn it off for good. I don't see anymore it's use. With just alsa everything works perfect.

---

### Post by BcRich on 2012-08-15
> **swedstal said:**
> The only thing that looks like it could be an issue is the "pulseaudio" process. I don't really know what this is, but I recall seeing it in another post. When I kill this process I am still getting the same error message as before. Interestingly enough each time I try to start Jack with Qjackctrl the pulseaudio process starts again. Any chance this could be the culprit?

Hi swedstal
Many people recommend un-installing or completely disabling pulseaudio, if your machine is used primarily as an audio production workstation, for numerous reasons. Personally, I have not had to uninstall or disable pulseaudio on my system which runs with a 8.7ms response time (and is certainly usable for audio production). I still occasionally get errors where JACK fails to start, checking that my sound devices have loaded in the correct order and that QJackctl is referencing the correct device is usually the first place I start troubleshooting. Followed by closing QJackctl, I kill the process "jackdbus" (which can be done simply by using System Monitor), when I restart QJackctl, it restarts jackdbus at an appropriate time, and JACK and I are friends again :)
NB.I'm not saying that you shouldn't disable/un-install pulseaudio, it's just that as a high level of abstraction for interfacing with your audio hardware, removing pulseaudio in Ubuntu could inadvertently end up disabling certain non-audio specific applications from interfacing with your sound device. On the other hand having less processes running in the background, could improve your systems performance as I noticed (a little off topic here) that the latency in your JACK settings are already quite high.

---

### Post by swedstal on 2012-08-15
Thanks, guys. This is giving me something to work with.

Perhaps I'm a pacifist at heart, but I would prefer to fix this problem without killing a normal process. Tell me if it's naivete, but I trust that people much smarter than I have put this in here for a reason. That said if I don't find a solution soon, I may become a bit trigger happy.

I did some more studying about pulseaudio and have read and re-read the responses here. I've succeeded in getting a little lost again. Here's where I'm struggling:

> checking that my sound devices have loaded in the correct order and that  QJackctl is referencing the correct device is usually the first place I  start troubleshootingThat sounds great but I have no idea how to go about this. Any tutorials to which I could be directed? I wish I wasn't so needy....

>  I kill the process "jackdbus" This is not showing up in my Processes list on System Monitor, regardless of whether I have Qjackctrl up or not. I have "dbus-launch" and "dbus-daemon". Are those the ones that need to be killed?

One more question: What is the best way to see if my interface is actually connected? (and don't say look at the cable :)). I did lspci and that output for firewire showed:

```
03:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. Device 3403
```I then unplugged the interface and it gave me the same line. Is there a clue here? Maybe the port went bad somehow...? Is there a proper command to see what's connected?

Thanks again, everyone. I'm learning, albeit slowly.

---

### Post by sgx on 2012-08-15
The existance/purpose of pulse audio, and its inclusion in an audio
production system, are two different topics. It is best to remove it
if possible, or stop its access, if your system is mainly for producing recorded music.

On the other hand, home theater users may find it possible
to use pulse to do special things for various media and devices, and
to interact and interconnect the computer within their
home entertainment system.

Your screenshot shows a hw:0 for one thing, and 'default'
for some others. I would try to insure everything is using
the same device.

aplay -l
cat /proc/asound/cards

those commands should reveal the detected soundcards in brackets.
Run them with a fresh boot, card unplugged, then power off, plug it in, reboot, and run them again. Check in qjackctl dropdown list
for the devices displayed in brackets:
Input Device >     click the > to see the dropdown list.
OutputDevice >

If a power supply is optional,
it should be used, as bus power is probably too weak for fault free operation.
Cheers

---

### Post by smartboyhw on 2012-08-16
Hello.
 
I am not recommending to uninstall or deactivate Pulse Audio in anyway.
 
I do agree that Jack sometimes broke down, and that I think the Ubuntu Studio team will make an effort to do so.
 
However, Pulse Audio is, at least for me, a core package for Ubuntu Studio, and that sometimes you may find inconvenience in doing so.
 
If Jack continues to break down and you think is a software problem, please report a bug to us.
 
Thank you.
 
Regards,
Howard Chan
Ubuntu Studio Team Member in [https://wiki.ubuntu.com/UbuntuStudio/TeamStructure](https://wiki.ubuntu.com/UbuntuStudio/TeamStructure)

---

### Post by jejeman on 2012-08-16
> What is the best way to see if my interface is actually connected?After you plugin firewire device you should get something like this from kernel 
```
firewire_core: created device fw1: GUID 0040ab0000c3757b, S400, 1 config ROM retri
```
to see above message use```
dmesg | tail
```
And new device must be present /dev/fw1

This is for 12.04.

---

### Post by swedstal on 2012-08-16
The plot thickens.....

It does not appear that my interface(or maybe even my firewire port) is being found anywhere.

I ran:

aplay -l
and
cat /proc/asound/cards

with the interface both unplugged and plugged in I got the same result both times:
```

ba@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ba@ubuntu:~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xf7ff4000 irq 16

```I'm pretty sure this output just shows my onboard audio, not my firewire card.

Next I used:

dmesg | tail
and got output:

```
ba@ubuntu:~$ dmesg | tail
[   37.737271] wlan0: authenticated
[   37.737284] wlan0: associate with AP 68:7f:74:87:c3:f1 (try 1)
[   37.752687] wlan0: RX AssocResp from 68:7f:74:87:c3:f1 (capab=0x431 status=0 aid=4)
[   37.752689] wlan0: associated
[   37.753539] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   37.800652] Intel AES-NI instructions are not detected.
[   37.804791] padlock: VIA PadLock not detected.
[   38.163827] __ratelimit: 27 callbacks suppressed
[   38.163830] type=1503 audit(1345155984.902:21):  operation="open" pid=1637 parent=1570 profile="/sbin/dhclient3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/lib/wicd/dhclient.conf"
[   48.006012] wlan0: no IPv6 routers present

```No sign of anything firewire going on here.

Have we eliminated all but hardware issues? I'm not really sure how to test my firewire port since I don't think I own anything else that runs on firewire. I'm getting a bit frustrated but at least I'm learning some things in the process. Thanks for sticking with me, guys. I am so grateful for the help.

---

### Post by swedstal on 2012-08-16
I have one more little clue here. There is a little blue light on this board that used to glow when the interface was connected. Now there's nothing. It is not receiving any firewire signal.


[IMG]http://imgur.com/INnhN[/IMG]

---

### Post by smartboyhw on 2012-08-17
> **swedstal said:**
> I have one more little clue here. There is a little blue light on this board that used to glow when the interface was connected. Now there's nothing. It is not receiving any firewire signal.
 
 
[IMG]http://imgur.com/INnhN[/IMG]
 Maybe your board can't realize the card..... That's bad. Try another card and see if it works
 
Regards,
Howard Chan
Ubuntu Studio Team member in [https://wiki.ubuntu.com/UbuntuStudio/TeamStructure](https://wiki.ubuntu.com/UbuntuStudio/TeamStructure)

---

### Post by jejeman on 2012-08-17
Check the cable.

---

### Post by Sylos on 2012-08-17
Sounds like a HW problem from what you say but it might be worth checking from a Live CD if you have the one you installed from. If you know that worked OOTB then it may be worth seeing if the result is the same when booting into that Live. It would eliminate the possibility of Kernel upgrade issue etc.

Best of luck.

---

### Post by swedstal on 2012-08-17
Booting up with a live CD is a great idea. I should have thought of that. Unfortunately Ubuntu Studio does not appear that it can be used as a live CD. I pulled out the standard Ubuntu 10.04 and ran that live. I did not see anything different. There was still no sign of my interface. I even tried setting up JACK but I think some of the changes require a reboot to work correctly.

I tried one other thing. I remembered I had a firewire card bus for my laptop so I plugged the interface into that system and ran the same live CD of 10.04. Still nothing.

I believe I can rule out the cable as the problem. Whenever the interface is newly plugged in to firewire, the firewire indicator light glows for a couple of seconds. It does this regardless of whether I plug it in to the interface or the motherboard first. This shows that there is at least some sort of signal going through the cable.

As I trace back to the beginning of this problem, I'm still very surprised that it just stopped working after being stable for years. Being a novice linux user, I have made very few changes since I set it up. I installed no new programs around the time it stopped working.

I feel bad that so many people have volunteered their time to help me solve this and still I have been unable to make progress. Without the support of the Ubuntu community I would surely be cursing at Windows for some other problem right now.

---

### Post by smartboyhw on 2012-08-19
> **swedstal said:**
> Booting up with a live CD is a great idea. I should have thought of that. Unfortunately Ubuntu Studio does not appear that it can be used as a live CD. I pulled out the standard Ubuntu 10.04 and ran that live. I did not see anything different. There was still no sign of my interface. I even tried setting up JACK but I think some of the changes require a reboot to work correctly.
 
I tried one other thing. I remembered I had a firewire card bus for my laptop so I plugged the interface into that system and ran the same live CD of 10.04. Still nothing.
 
I believe I can rule out the cable as the problem. Whenever the interface is newly plugged in to firewire, the firewire indicator light glows for a couple of seconds. It does this regardless of whether I plug it in to the interface or the motherboard first. This shows that there is at least some sort of signal going through the cable.
 
As I trace back to the beginning of this problem, I'm still very surprised that it just stopped working after being stable for years. Being a novice linux user, I have made very few changes since I set it up. I installed no new programs around the time it stopped working.
 
I feel bad that so many people have volunteered their time to help me solve this and still I have been unable to make progress. Without the support of the Ubuntu community I would surely be cursing at Windows for some other problem right now.
 
Er, why can't it be live? Choose "Try Ubuntu Studio before Installing" after booting into the CD. It should be in live mode.
 
BTW, wait, tell me about your Windows info and see may Windows affect it.
 
Regards,
Howard Chan
Ubuntu Studio Team Member at [https://wiki.ubuntu.com/UbuntuStudio/TeamStructure](https://wiki.ubuntu.com/UbuntuStudio/TeamStructure)

---

### Post by BcRich on 2012-08-21
Hi swedstal
Have you had any luck with getting your sound device to work yet?
My bad, I just realised from reading your posts again that you're using 10.04. For some reason I assumed you were using 12.04. When pulseaudio was first implemented in Ubuntu it was met with alot of criticism not because it's a particularly bad piece of software (as many popular Linux distros use it ) but because of the way that it was implemented in Ubuntu. Over the years Ubuntu has steadily improved on pulseaudio integration and 12.04 is the first release of Ubuntu that I'm using pulseaudio at near to default settings alongside audio production software (JACK, Ardour, Rosegarden etc). Having said that prior to 12.04 I always had to seriously tweak pulseaudio, completely remove it or try to disable it. No offence meant to the developers but pulseaudio never worked very well for me prior to 12.04. I do recall that when I used 10.04 I would control pulseaudio with an app called Pulse Audio Volume Conrol (or pavucontrol as it's called in the repos), this worked pretty well for me as it's a gui that makes visualizing what pulseaudio is doing in the background easy to understand for a non-programmer, end user such as myself. If that doesn't work and you're sure it's not a hardware problem maybe it's time to consider a more drastic solution?

---

### Post by chkneater on 2012-08-23
Hi, I've found that jack will sporadically alter either the interface or the in/outputs, even if they still say default.  Alsamixer will sometimes pickup the wrong card and you'll have to change it back.  Also starting from a terminal with 'sudo' might help.  when you close it down, make sure to Stop, then Quit; that's one other thing that will break it.

---

### Post by swedstal on 2012-09-03
At the point of my last post, about 2 weeks ago, I was becoming quite frustrated. Experience has taught me that I do not make rational decisions when in this state of mind. Consequently I decided to take a break from this project and am now revisiting it with some fresh information and a fresh perspective.

Hardware:
-New FW cable did not make a difference.
-Bought and installed a PCI to FW card which still did not help.
-Opened up the interface (meaning my sound card, a Phonic Helix 18, checked accessible connections with a multimeter for continuity, inspected and re connected cables. All looked fine.
-Checked all audio inputs and outputs on the interface (16 and 2, I believe). All are working.

Software:
-Ubuntu Studio 12.04 *is* available as a live CD unlike the 10.04 that I've been using for the last few years. I booted right into 12.04 and poked around. There is still no sign of my interface anywhere. Jack does find my on board sound card and my keyboard (an M Audio Sono 88 which has a 2 channel USB interface built in) just fine. I rechecked this with what I found in 10.04 and determined that I am getting the same thing from both releases.
-I'm still downloading the live CD for 32-bit so I can try it on my old laptop through a firewire cardbus.

I will reiterate that the setup I was using worked wonderfully for over two years. I regularly recorded up to 4 channels of audio at a time with no problems.

Can anyone think of anything else I can try? Thanks again for bearing with me!

---

### Post by sgx on 2012-09-04
For many ubuntu users, 10.04 is the best option for audio. 
New system releases often do not have pro quality audio recording
as a priority, so a long season may transpire before usability is
the wide result.  Go back to what worked, and test new releases
in your spare time, from live media, or external drive installs.

Compare output from lsmod, between 10.04 and 12.04 to see
in kernel module is missing from 12.04

compare the versions of libjack, jackd, qjackctl and ffado items,
odd failing combos of these can be fixed by using different versions
(debian stable, testing, and unstable)

compare the existance, and startup of pulseaudio between 12.04 and 10.04  (use htop, top, or the command  ps ux to see what's running
on startup.

jackd2 is different from, but not always better than jackd1,
and firewire handling may be a victim of one or the other.

Try Bodhi, light 400 meg ubuntu based distro, and add just the audio basics using synaptic, in case some conflicts from the general package base, have infiltrated.
Cheers

Verify the mixer is working on another system, just for luck.

---

### Post by jejeman on 2012-09-04
I agree 10.04 is still more stable than 12.04, but 12.04 is LTS so it is worth the switch. I'm still transitioning from 10.04 to 12.04 and been using it for two months now.

I will talk about 12.04.

First, as I already posted, you need to see your firewire controler

/dev/fw0

than the devices will follow

/dev/fw1 (etc.)

I suggest, if you can, to try some camcoder to see if firewire card works, but, if your device gets the device node it should work. Try to capture some video with Kino.
Also, if you can, try the sound card on diffrent PC or in windows. Just to see if it works.

Now, the JACK on 12.04 saga.
I have discovered that JACK2, for some reason "breaks", and it can no longer start FFADO driver. This "breaking" happends when JACK2 crashes or Qjackctl does not closes nicely, but not exclusevly just then. After that you can not use firewire audio card, more precisley JACK2 can not start FFADO driver. For now only solution I found out is to reinstall system, I didn't manage to "clean out" JACK2 differently. Purging JACK2, FFADO or removing all files related to them from home directory makes no difference. In this stage JACK2 is working fine with ALSA, so it's not compleatly "broken" just something related to FFADO.
Some workarounds I've found:
- remove everything wich could crash JACK2 or Qjackctl > pulseaudio-jack-sink, turning off JACK dbus in Qjackctl
With this workaround I've been working for two months with no problems.
- switch to JACK1 - Last thing I did when JACK2 got "broken" i installed JACK1 and FFADO works. (Here I want to make clear that FFADO always works eg. FFADO mixer recognises the audio card, and there is always device node. So, only JACK2 can't use it.) 
I didn't had time to test how stable the JACK1 is, thats next. While JACK2 was working everything was pretty stable. Very Few JACK2 crashes for two months.

Well, the next step is, I guess, to go to JACK2 devs and to find what the problem is or how can I "clean" JACK2. But, who have time for that when music is need to be made. ;):guitar:

---

### Post by nairatinu on 2012-09-05
christ, I've been struggling for days trying to get jack to be "stable", not realizing that I hadn't selected the correct soundcard in the setup. My confusion is forgiveable, I think, because I had disabled the nvidia onboard sc in bios, but it was still being detected (didn't have this problem with studio 10.04).

---

### Post by swedstal on 2012-09-06
Sorry for the delay since my last post. It's been a busy work week.

Wow. Thanks again for the detailed responses. I would be lost(er) without you guys!

I've taken another step back and thought about everything I've done so far. I believe the title of this post is unfortunate since I now believe that my problem is pre-Jack. Were I getting any kind of firewire data that far, I think the problem would be easier to solve.

> First, as I already posted, you need to see your firewire controler

I don't believe that I am even to this point yet. Regardless of my version of Ubuntu Studio, I am not seeing my device as a recognized sound card.

```
aplay -l
```....just shows my onboard audio. I have followed the tutorials (yes, I do have "Enable Raw 1394 access" checked in US Controls) but am still not seeing my interface. 

Declaring any computer problem to be a "hardware issue" is often a bit hasty, but I have made zero progress on the software side. My plan now is to:

1. Get my interface recognized on a different computer (I have tried it on my old laptop with a CardBus adapter running 12.04 live, but I don't know if I can consider this a sufficient test.

2. Find some other Firewire peripheral that I can get working with my system. Does anyone know what my cheapest option would be in this category? I don't really need any more equipment at this time. I need more friends who are techies ;).

How does this plan sound? Thanks again for all of the support. You guys are way better than calling someone in Hyderbad.

---

### Post by jejeman on 2012-09-07
First, you are in the wrong. ALSA will never see firewire device. ALSA is audio driver only for PCI and USB soundcards. FFADO is driver for firewire audio devices. So with "aplay" you can't list firewire sound card.

Practicly you have two drivers
1. driver for firewire contorler - firewire_ohci, firewire_core (12.04)
2. driver for firewire audio card - FFADO
Second one works through first one. If I'm in wrong please someone correct me. First driver is in kernel. You can see if first driver is active with "lsmod" command. If firewire controler is present this modules should be loaded. And with only first driver you should see device nodes /dev/fw0 (contorler), /dev/fwX (devices). To work with devices you need to have installed this libs: libraw1394, libffado, which are by default. Also you need to be in the group which can use this devices (audio) in which you are by default on 12.04.

Your plan is okay. 
1. Live DVD is sufficient for the task, my card works with live DVD.
2. If you can, borrow DV camcoder and see if it is recognised. Use Kino to grab some footage.

---

### Post by swedstal on 2012-10-15
"No" would be the answer to my original enquiry.

I finally have the problem solved. I was able to pick up a PreSonus Firepod for about $120 on ebay. I plugged it in and Jack started right up.

I did my best Tiger Woods fist pump.

Turns out that my interface had just pooped out, but only the firewire send part. Everything else still works fine on it. I've been trying to think about how I could have caught this problem earlier, but the fact that all other functions on the board were working made it a tough one to figure out.

Thanks again for all of the wonderful help! I once again increased my knowledge through working on this problem so it was not a waste. For now, my soap opera with Ubuntu continues.....

---

### Post by BcRich on 2012-10-16
Rad :)

---

