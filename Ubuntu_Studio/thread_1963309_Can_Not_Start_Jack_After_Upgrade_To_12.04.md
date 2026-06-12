---
title: "Can Not Start Jack After Upgrade To 12.04"
date: 2012-04-22
forum: Ubuntu Studio
---

### Post by Precipitous on 2012-04-22
After upgrading from Ubuntu 11.10 to Ubuntu 12.04 I am no longer able to start Jack. If I try to start it using QjackCtl I get the following:
```
06:05:51.780 Patchbay deactivated.
 06:05:51.847 Statistics reset.
 06:05:51.926 ALSA connection change.
 06:05:51.950 JACK is starting...
 06:05:51.952 /usr/bin/jackd -S -p128 -t1000 -dalsa -dhw:0 -r48000 -p256 -n3
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 06:05:52.465 Could not start JACK. Sorry.
```[COLOR=#FF0000][COLOR=Black]If I try to start it via a command window by running:[/COLOR][/COLOR] 
```
jackd -dalsa -r48000 -p128 -n3 -D -Chw:0,0 -Phw:0,0  
```I get the following:
```
The program 'jackd' can be found in the following packages:
 * jackd1
 * jackd2
Try: sudo apt-get install <selected package>
```When I run:
```
aplay -l
```I get:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```When I run:
```
lspci
```I get:
```
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA Controller [RAID mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G72 [GeForce 7300 LE] (rev a1)
```Has there been a radical change with regard to the way Jack functions  (starting with Ubuntu 12.04)? Are there known compatibility issues with it?  

I am lost...

---

### Post by Precipitous on 2012-04-24
I figured out that the problem is with QJackCtl, not the Jack Server itself...  If I run Patchage I am able to connect to Jack without any problems. As long as I leave it (Patchage) open I can run QjackCtl fine.

I did some research and found a bug report has been posted on Launchpad about this QJackCtl issue already. Hopefully it will be resolved soon!

---

### Post by Precipitous on 2012-06-19
I resolved this issue by running Jackd and qjackctl from the KXStudio repositories.

---

### Post by mjhouska on 2012-06-19
> **Precipitous said:**
> I resolved this issue by running Jackd and qjackctl from the KXStudio repositories.

i have the same problem. how do i do this?

---

### Post by Precipitous on 2012-06-20
> **mjhouska said:**
> i have the same problem. how do i do this?
*I normally install Ubuntu 12.04, then install all of the UbuntuStudio packages. The following assumes that you are doing the same...*

There are two ways to go about this. The first one is the quickest, but carries some risks since it involves potentially uninstalling and re-installing large numbers of applications. Therefore I HIGHLY recommend using the second one.

Method 1. 
You first need to uninstall jackd and qjackctl (if you have jackd1 or jackd2 installed uninstall them too). This is probably best done using Synaptic. You may have a LOT of applications installed that have jack as a dependency. Uninstalling jack will cause them to all be uninstalled as well, so you will need to re-install them later.

Once jack and qjackctl are uninstalled run the following commands to install the KXStudio repositories:
```
sudo add-apt-repository ppa:kxstudio-team/kxstudio
sudo apt-get update
sudo apt-get install kxstudio-repos
sudo apt-get update
```You should then see the KXStudio builds of jackd and qjackctl listed in Synaptic. Install jackd, jackd2 and qjackctl, then re-install any applications that were uninstalled earlier.

Method 2:
Re-install Ubuntu 12.04 from scratch. Once it is installed run the following commands to install the KXStudio repositories:
```
sudo add-apt-repository ppa:kxstudio-team/kxstudio
sudo apt-get update
sudo apt-get install kxstudio-repos
sudo apt-get update
```Next use the Ubuntu Software Center to install Synaptic. 
After that use Synaptic to install jackd, jackd2 and qjackctl. 
Finally, install all of the UbuntuStudio packages and any other audio applications you use.

I hope this helps!

---

### Post by tontis on 2012-11-28
Hi, I have a similar problem, but I'm completely new to using jackd and qjackctl. To be honest I don't really know how it works, or what it does. All that I have read so far on the websites and such just seem to confuse me more. Do I need to mention i am not the most skillful ubuntu user yet? Anyway, I installed it in order to make the audio work for rosegarden, but I can't get it to work.

I'm running ubuntu 12.04 and tried you're method one; adding the KXStudio repositories and reinstalling it from synaptics. Yet jackd still doesn't start. Instead this error text is produced:
```
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
12:16:33.408 ALSA connection graph change.
12:16:40.718 D-BUS: JACK server could not be started. Sorry
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Wed Nov 28 12:16:40 2012: Starting jack server...
Wed Nov 28 12:16:40 2012: JACK server starting in realtime mode with priority 10
Wed Nov 28 12:16:40 2012: [1m[31mERROR: Cannot lock down 82241434 byte memory area (Cannot allocate memory)[0m
Wed Nov 28 12:16:40 2012: [1m[31mERROR: can't load "/usr/lib/i386-linux-gnu/jack/jack_alsa.so": /usr/lib/i386-linux-gnu/jack/jack_alsa.so: undefined symbol: _ZN4Jack14JackPosixMutex4LockEv[0m
Wed Nov 28 12:16:40 2012: [1m[31mERROR: Cannot initialize driver[0m
Wed Nov 28 12:16:40 2012: [1m[31mERROR: JackServer::Open() failed with -1[0m
Wed Nov 28 12:16:40 2012: [1m[31mERROR: Failed to open server[0m
Wed Nov 28 12:16:42 2012: Saving settings to "/home/bixop/.config/jack/conf.xml" ...
12:16:44.846 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
```

Any help is appreciated if you can make any sense out of this!
Cheers!

---

### Post by serfcx on 2012-11-28
Tontis
I suggest you start a new thread as this one is marked "solved" and I presume your problem isn't !

---

### Post by Precipitous on 2012-11-28
> **tontis said:**
> Hi, I have a similar problem, but I'm completely new to using jackd and qjackctl. To be honest I don't really know how it works, or what it does. All that I have read so far on the websites and such just seem to confuse me more. Do I need to mention i am not the most skillful ubuntu user yet? Anyway, I installed it in order to make the audio work for rosegarden, but I can't get it to work.

I'm running ubuntu 12.04 and tried you're method one; adding the KXStudio repositories and reinstalling it from synaptics. Yet jackd still doesn't start. Instead this error text is produced:
```
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
12:16:33.408 ALSA connection graph change.
12:16:40.718 D-BUS: JACK server could not be started. Sorry
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Wed Nov 28 12:16:40 2012: Starting jack server...
Wed Nov 28 12:16:40 2012: JACK server starting in realtime mode with priority 10
Wed Nov 28 12:16:40 2012: [1m[31mERROR: Cannot lock down 82241434 byte memory area (Cannot allocate memory)[0m
Wed Nov 28 12:16:40 2012: [1m[31mERROR: can't load "/usr/lib/i386-linux-gnu/jack/jack_alsa.so": /usr/lib/i386-linux-gnu/jack/jack_alsa.so: undefined symbol: _ZN4Jack14JackPosixMutex4LockEv[0m
Wed Nov 28 12:16:40 2012: [1m[31mERROR: Cannot initialize driver[0m
Wed Nov 28 12:16:40 2012: [1m[31mERROR: JackServer::Open() failed with -1[0m
Wed Nov 28 12:16:40 2012: [1m[31mERROR: Failed to open server[0m
Wed Nov 28 12:16:42 2012: Saving settings to "/home/bixop/.config/jack/conf.xml" ...
12:16:44.846 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
```Any help is appreciated if you can make any sense out of this!
Cheers!
@tontis:  More than likely the problem is that your user account is not a member of the audio group in Ubuntu, which is necessary to use the realtime mode in jack. To add your user account to the audio group in Ubuntu run the following command (change username to your Ubuntu login name):
```
sudo usermod -a -G audio username
```I hope this helps. If not you should probably start a new thread in the forum so your issue gets proper attention.

Cheers!

---

### Post by ektwr on 2013-01-26
> **Precipitous said:**
> 

Method 1. 
You first need to uninstall jackd and qjackctl (if you have jackd1 or jackd2 installed uninstall them too). This is probably best done using Synaptic. You may have a LOT of applications installed that have jack as a dependency. Uninstalling jack will cause them to all be uninstalled as well, so you will need to re-install them later.

Once jack and qjackctl are uninstalled run the following commands to install the KXStudio repositories:
```
sudo add-apt-repository ppa:kxstudio-team/kxstudio
sudo apt-get update
sudo apt-get install kxstudio-repos
sudo apt-get update
```You should then see the KXStudio builds of jackd and qjackctl listed in Synaptic. Install jackd, jackd2 and qjackctl, then re-install any applications that were uninstalled earlier.

Thank you. This method works for me. :p Is it possible to use my firewire focusrite pro 24dsp to listen from other recources like utube etc. ? Thank you again!

---

### Post by Sylos on 2013-01-26
> **ektwr said:**
> Thank you. This method works for me. :p Is it possible to use my firewire focusrite pro 24dsp to listen from other recources like utube etc. ? Thank you again!

It should be possible by using the Pulseaudio Jack-sink. This will allow you to run the output from pulse (which youtube will play through) and run it into jack to then be put through your soundcard. That being said, it may be possible to just change your pulseaudio settings to use the focusrite. It depends on how you have things set up as to which way is best.

Cheers

---

