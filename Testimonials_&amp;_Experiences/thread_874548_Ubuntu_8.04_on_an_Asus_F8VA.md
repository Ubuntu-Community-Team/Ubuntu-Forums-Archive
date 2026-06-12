---
title: "Ubuntu 8.04 on an Asus F8VA"
date: 2008-07-30
forum: Testimonials &amp; Experiences
---

### Post by dickohead on 2008-07-30
Alright...

So now that I have a notebook with Express Gate/SplashTop installed (woof) I was starting to doubt whether or not I would ever leave the rapid booting environment. But the temptation was too much so I installed Hardy on my notebook - and this is what I've found so far.

**System Specs:**
CPU: Intel C2D T9400 2.53GHZ
RAM: 4GB DDR2 800MHz
HDD: 320GB SATA 5400RPM
ROM: Bluray drive
Video: ATI Mobility Radeon HD 3650 1GB (native 1440x900)
Audio: Built-in Azalia compliant audio chip, with 3D effect & full duplex
LAN: Not sure yet... Reported as Unknown
Wireless: Intel® WiMAX/WiFi Link 5100
[Asus Specs Link]("http://www.asus.com/products.aspx?modelmenu=2&model=2370&l1=5&l2=26&l3=501&l4=0")

I was able to boot from the CD just fine and started to install Ubuntu (x86_64). The keyboard and mouse were picked up fine and I proceeded to repartition my hard drive with great ease.

The system then rebooted and presented me with a logon screen running at 1280x800, I logged in and received no login Audio (this always happens, so I wasn't worried).

My first task was to change my resolution to 1440x900; because I'm a fussy turd, so I proceeded to the System Menu and checked out the Restricted Drivers to find that the ATI Drivers were installed, but not active... So I opened up a terminal and cat'd /etc/X11/xorg.conf and to my surprise - bugger all was configured. So I tried to enable the driver to no avail and then loaded up Synaptic to install a different driver - only to find that my network card had not been identified!!! THE HORROR!

I then rebooted into Express Gate and downloaded some files from the Asus website ([from here]("http://support.asus.com/download/download.aspx?SLanguage=en-us")) complete with drivers for VGA/Audio/LAN and Raid. Inside this file were LAN drivers for Suse, Mandriva, RHE and Fedora... no Ubuntu.

After cursing Asus I opened up the Mandriva folder to find that the included sis190.ko file was for X86_64 architectures, but none of the others were. So I copied this file to /lib/modules/`uname -r`/kernel/drivers/net/sis190.ko and rebooted - it freakin worked!!!

Who'd've thunk it?

I then loaded up synaptic, searched for "radeon" and installed the FGLRX drivers. I rebooted again and was greeted automatically with 1440x900 resolution and a much prettier desktop. I then turned on "normal effects" and dribbled a little.

So now I am left with fixing the WLan (no surprises there), testing Bluetooth (the applet is there) and finding out why ALSA has correctly identified my sound card; but is unable to playback any sound. I suspected it might have been "switches" or "options" under the Sound Applet as it was on my last notebook, but this did not work.

I also need to look into finger-print-reader support for Linux since I really do like this feature and Vista does it so nicely (*ducks*).

All in all - a pleasant surprise over my last Hardy-notebook experience. I'll update this post as I fix more things and discover more stuff that I like!

If anyone is looking for a new notebook - the F8VA is awesome!
And if Asus is looking to send me free stuff, send me an e-mail.
:D

---

### Post by dickohead on 2008-08-01
Alright. I tried to get my sound working and have epically failed.

I followed the tutorial located [here]("https://help.ubuntu.com/community/HdaIntelSoundHowto") and even did the extra bits in the event the first stuff didn't work... and it still doesn't work.

So now I'm back to thinking that maybe; sound, Ubuntu and I had some problems in the past and now I'm paying for them... so be it. I'll use Vista... See what I did there, I instilled a little bit of fear, so now when I try and get the sound working it'll want to work!

My LAN card also switches between giving itself a 169.x.x.x address and getting one from my DHCP server (never happened before). I have to continually replace the sis190.ko file then reboot before it works again - ughhhhh!

Any suggestions or additional info you'd like?

---

### Post by Chris Cudahy on 2008-08-09
I bought a F8VA last week and I've had close to the same experience running ubuntu 8.04. The restricted video driver just worked for me, as did LAN but both Wireless LAN and audio are not functioning.

 There's an ath9k driver in development which I believe should help with wireless. If I'm reading it correctly it was recently merged into wireless-testing (see the comment on [http://wireless.kernel.org/en/users/Drivers/ath9k#Getthecode](http://wireless.kernel.org/en/users/Drivers/ath9k#Getthecode) ). I haven't been able to get this running yet.

 ASUS has a newer BIOS available, version 206 which claimed to "Fix bug that when disable the USB, the Audio and modem are disabled, too". This seemed promising, but didn't help.

 A USB audio headset I plugged in as a sanity check works perfectly.

---

### Post by wolfen69 on 2008-08-09
it's probably good to get a spare wireless card (PCMCIA) that works in linux OOTB. i have not needed to use mine yet, but at least i know that no matter which laptop i use or get, i'll be able to get online. i think if you're going to get serious about linux, also need to get serious about using compatible hardware. people buy computers with windows, dont they? and then complain that it's not ready for prime time. do yourself a favor and buy a pc with linux pre-installed, or use compatible hardware. the experience will blow your mind. why fight it?

---

### Post by dickohead on 2008-08-10
@wolfen69 - was not complaining mate, just putting my experiences down so that others may benefit and provide feedback as Chris did.

I also understand that there will always be hardware that won't immediately work, but if everyone avoids that hardware in favour of compatible alternatives; we'd never get anywhere. :D

---

### Post by wolfen69 on 2008-08-10
> **dickohead said:**
> @wolfen69 - was not complaining mate, just putting my experiences down so that others may benefit and provide feedback as Chris did.

I also understand that there will always be hardware that won't immediately work, but if everyone avoids that hardware in favour of compatible alternatives; we'd never get anywhere. :D

it wasnt really directed at you, i was just making a statement.

---

### Post by FlyingPenguin on 2008-10-09
I was thinking about buying this at newegg. Any updates on these issues? Any info on the built in webcam?

---

### Post by dickohead on 2008-10-09
After I ran some updated the LAN card issue went away, and I could get the Video working quite well. But still no sound, no wireless (this should work with the 2.6.27+ kernel) and no idea if the webcam works!

I installed 8.10 on last night and the video has gone bad on me, but it did pick up the WiFi card (dmesg | grep 5100 or dmesg | grep WiFi).

So I suggest you wait for 8.10 and see how much success we have there!

The laptop is reeeel pretty though. :D

---

### Post by winzxb1985 on 2008-10-10
[color=#282827]I agree with you !I support you .[/color] As formidable as the [Ball Mill](http://www.ballmills.cn)

---

### Post by stalkingwolf on 2008-10-10
maybe the EEE version would be of help?  It was written for an ASUS.

Just a thought.

---

### Post by dickohead on 2008-10-10
Yeah I thought that too, but the EEEPC uses a different wireless card. :(

---

### Post by stalkingwolf on 2008-10-12
Before I started using 8.04 I never paid any attention to the internal
WIFI on my laptops. I just stuck in a netgear wg111 adapter or a dlink
wg650 aircard and off I went.

When I installed 8.04 on my HP NC8000 I found I had 2!! wireless connections.
Well Damn I never even thought about the internal.

---

### Post by dickohead on 2008-11-08
For those of you also using an Asus F8V notebook, I can confirm that 8.10 works!

From an 8.04 installation I ran **sudo apt-get dist-upgrade**, as I couldn't install from the CD - same white screen error.

Once you've upgraded and rebooted, you'll need to login to the command line (Ctrl+Alt + F2 to show the command line) and run:
**sudo aticonfig --initial** then kill all running x servers:
**sudo ps -A | grep X** will show you the PID of any X servers running
**sudo kill -9 1234** will let you kill the running X servers, replace 1234 with the PID from above.
Running **startx** from the command line should now you get you into your desktop.

:D

---

### Post by FlyingPenguin on 2008-11-22
You can also apt-get from terminal the latest proprietary ati driver. After aticonfig --initial, a reboot, and you're money.

Still no sound on 8.10 for me though, any suggestions?

---

### Post by dickohead on 2008-11-22
No i've got no sound either. I tried playing with the switches in the audio config as this fixed it on another notebook, but not this time.

Also, I couldn't change mine from within Gnome/X because it wouldn't start... How'd you get yours to boot into X initially?

---

### Post by mgerdzhev on 2008-11-22
I didn't have sound either before. What fixed this for me was editing the file /etc/modprobe.d/alsa-base
```
sudo gedit /etc/modprobe.d/alsa-base
```
and append this to the end of the file:
```
options snd-hda-intel model=m51va
```
Reboot and the sound should work. Hope that helps

---

### Post by dickohead on 2008-11-22
... you know I love you right?

That worked perfectly!!!

---

### Post by mgerdzhev on 2008-11-23
@dickohead: I'm glad I could help.

I have actually opened a bug report at launchpad for the sound problem. I found that this solution brings some other problems for me - eg. can't have simultaneous sound from different applications and youtube videos hanging on 2-3 seconds if rhythmbox was playing something. Anyway if anyone has similar problems it would be nice if you can post here [https://bugs.launchpad.net/bugs/301185]("https://bugs.launchpad.net/bugs/301185")
so that they can fix the problems.

---

### Post by jrphorbin on 2009-01-20
WOW! SOUND! I've stumbled on this thread after at least a month steady of trying everything to get sound on my F8Va laptop. I have it triple booted XP - ViZta Ultimate 64 bit and UUE 2.0(8.04 upgraded to 8.10). Tried at least 10 dif distros on here and ALAST ....SOUND!  Thank you for Mgerdzhev's post: 

Re: Ubuntu 8.04 on an Asus F8VA
I didn't have sound either before. What fixed this for me was editing the file /etc/modprobe.d/alsa-base
Code:

sudo gedit /etc/modprobe.d/alsa-base

and append this to the end of the file:
Code:

options snd-hda-intel model=m51va

Reboot and the sound should work. Hope that helps

---

### Post by PMDirac on 2009-01-25
> **mgerdzhev said:**
> 
```
options snd-hda-intel model=m51va
```
Reboot and the sound should work. Hope that helps

Thank you so much. Works finally.

---

### Post by ARam1024 on 2009-01-26
@mgerdzhev
Thanks for the advice on the sound.  It works for the ASUS M50VM-B1 as well.

---

### Post by marienvuik on 2009-03-18
Thanks that worked perfectly.I could only get suse to work but i'm very happy to have ubuntu working after a few instalations.

---

