---
title: "dv9000 with Ubuntu 8.04 Experience"
date: 2008-04-15
forum: Testimonials &amp; Experiences
---

### Post by 0xdeadc0de on 2008-04-15
Any updates  will be posted on [http://roguestar.yi.org:5555/dv9000ubuntu8.04.html](http://roguestar.yi.org:5555/dv9000ubuntu8.04.html)


Ubuntu 8.04 Beta

After running Fedora 8 with stock kernels for nearly a year, the shift to Ubuntu was very nice.

It took a full day to set everything up well enough for me,

OpenOffice just crashed twice while writing this far, bad sign, I turned off the OpenOffice menu fix's in compiz-fusion, hopefully that helps. Not completely, it crashed twice again before the end of writing this.

Back to the main topic, Upgrading from a clean 7.10 install to 8.04. It took a while to say the least. To get 7.10 to even run I had to start with noapic to disable dynticks and bypass the c1e bug. 8.04 luckily comes with a kernel newer than 2.6.4-14 which includes the dynticks patch which finally makes them work for the dv9000 laptops and probably many 6000's and other models.

Battery life actually has improved, in Fedora 8 it was 1-1, if I had 54% charge I had 54 minutes left, now it's about 20% better. (Although after a year this battery is already only holding 28% capacity, which lasts about an hour and a half, not t bad for nearly shot).

Performance has dramatically improved over Fedora 8 with a comparable setup (compiz-fusion, pulseaudio, nvidia binary drivers, ndiswrapper, firefox/adobe flash). I had to download and manually install the adobe flash plugin, no big deal, the libflashsupport plugin is in the ubuntu repo's already. I can tell it's improved, because even with vsync set everywhere it can be just like it was in fedora, I get no video tearing in flash videos (youtube etc), even when I use flash+enhanced desktop zoom. Fedora 8 gave really choppy video using compiz edz+flash.



Wine programs seem to be working better. I setup wine, then set it up using the “standard” dx8, 9, and 7 setup (override lots dll's, find instructions elsewhere), I've been playing 007 goldeneye in Project64k.exe, sonic the hedgehog in Fusion.exe, starfox 64 in 1964.exe, and everybody's favorite, Peggle with “3d acceleration” enabled(Spiffy effects dude!)

For kicks I downloaded js2mouse, installed it, and set it up so xorg can use my gamepad as a mouse (With two buttons in a drawer on the main panel to enable/disable joystick mouse via xsetpointer +-c joystick_name_in_xorg.conf.

To stream my music from my tiny little laptop speakers to my stereo speakers (When I don't care about audio syncing and I want it to come out both speakers) I use a little script which exploits pacat to record the local audio output stream, then play it over the remote sound card (Thank you pulseaudio): pacat -ntest1 -v -r -d alsa_output.pci_10de_26c_sound_card_0_alsa_playback_0.monitor | pacat -v -p -d combined -shome -ntest. A couple nice buttons to enable/disable this in a drawer on the main panel is a nice little feature.

Cpufrequency scaling didn't work by default. There were a couple things I had to do, set permissions on a file to allow the gnome-cpufreq-monitor applet to change things as a non-root. Then I had to install the powernowd and cpufreq governers (userspace, performance, ondemand being the “most important”, but I installed them all just for the hell of it). I tried cpufreqd, it wouldn't let me manually change anything. I'd select 800mhz, it'd pick 1600mhz stay there for a while, then jump when it felt like it.

Gnome-VFS, what a waste of space. In fedora 8 I enjoyed keeping all my music on my ssh server, simply opening rhythmbox and playing my music over ssh:///user@host/home/user/Music saving space on my laptop while letting me enjoy all my music, while streaming the played audio back over the network back to the server to go out it's soundcard after it's played through mine. In Ubuntu 8.04 this just refused to work, I couldn't get rhythmbox to work with my ssh server. Totem streamed them fine. In the end I dumped the whole gnome-vfs, and went with sshfs and afuse. Afuse did give me problems Without afuse, sshfs unmounts the remote mount fairly quickly, and I have to keep manually remounting it (via launcher or terminal).

For afuse to work I had to disable multi-threading support, with multithreading there was an insane amount of lag being created.



Afuse still isn't perfect, in the ~/server folder not only do I have 0xDeadC0de@home like I want, but I also have: ls ~/server/

0xDeadC0de%40home BDAV EXT MPEG-2 PICTURES VIDEO_TS

0xDeadC0de@home BDMV HVDVD_TS MPEGAV SVCD

AUDIO_TS DCIM iPod_Control Music VCD



right?

I use a simple script /bin/connecttohome which is run every time I log in (system/preferences/sessions)

afuse -s -o mount_template="sshfs -o port=15200 0xDeadC0de@home:/home/0xDeadC0de/ %m" -o unmount_template="fusermount -u -z %m" ~/server/ &

I added an entry for “home” in /etc/hosts to point to my internal server ip.

Also, the rhythmbox-metadata program decided to eat a lot of cpu, and rhythmbox started crashing (maybe due to afuse? I don't know, I've had amarok streaming my music via sshfs/afuse for about an hour now with no problems, rhythm had them very quickly)

When I used the %r option instead f user@host:/basefolder/ I seemed t have a lot of problems with “lag”, but this was before I disabled multi-threading with -s. After -s there were no problems, before the lag was mad. I could try again, but it's working well enough for me now.

Oh, and when I used the %r option with -f I saw it trying to mount a bunch of .Trash-1000 folders, which I can't seem to locate anywhere on either system.



I had to install ccsm, fusion-icon, pulseaudio tools, ndiswrapper, and the nvidia driver.

Ndiswrapper gave me the most hassle. Although it installed, recognized the driver, it just wouldn't work. I had blacklisted b43 and ssb so they weren't the problem, but then, turns out somehow they are.

I found ssb and b43 load some other modules, including rfkill, cfg80211, mac80211, and one or two others (modprobe b43 without sudo as non-root), so I tried to load those seperatly, still wouldn't work. The only way I could get it to work was to load b43 & ssb then unload them and the cfg/mac80211 modules. It works every time now. (Note: I used fwcutter to get the required firmware for b43/ssb, it works, but only at 5mbps. Ndiswrapper gets 56mbps)

Here's my /etc/rc.local

modprobe ssb

modprobe b43

rmmod ndiswrapper # hmm?

rmmod b43

rmmod ssb

rmmod mac80211

rmmod cfg80211

modprobe ndiswrapper





And last but not least, the final problem, excess heat. My gpu was running in excess of 90C, idle. A quick, careful yanking of every single screw (except the ones in the lcd casing), then 4 more to remove the fan from it's heatsink, and a split second of pulling gobs of dust caked against the grill out, blowing it out, pull the fan off slowly and careful and get globs of dust out of there before it builds up and causes problems, and bam, instant 40C drop in my gpu while idle, 30C when active. The cpu's are running about 10-30C cooler as well. CLEAN THE DIRT IN THE FANS!!!!

---

### Post by jdrodrig on 2008-04-15
"Performance has dramatically improved over Fedora 8"...

just wondering, would you think it is because of the new scheduler? CFS?

anyone there has a reference to a real-world test that isolates the role of the new scheduler?

---

### Post by 0xdeadc0de on 2008-04-16
The performance increase, i would guess, comes from dynticks working (c1e patch in 2.6.4-14) as well as the new scheduler? In fedora 8 100% memory was in use at all times, if 33% was in use by programs 67% was in use by cache. Ubuntu shows 33% programs, 38% cache. 


After using afuse a little while, and having many problems with it, I switched back to sshfs without afuse and used the  method described in the link, with the following line added to fstab
```

 sshfs#0xDeadC0de@home:/home/0xDeadC0de/	/media/server	fuse	defaults,allow_other,port=15200,user	0	0

```
Testing this now, i hope it stays mounted this time. (With just sshfs it unmounts after about a minute)
[http://thomas.tanreisoftware.com/?p=49](http://thomas.tanreisoftware.com/?p=49)
-It stays connected for a while but does disconnect eventually and needs to be remounted before it can be used again, what's the proper way to automount on access?

Does anyone know of a "better" way to keep it mounted?

---

### Post by kelvingeorge on 2008-04-16
I am new to linux and I love it. Slowly getting rid of windows. Moved from live desrto to full install. No problems except for my wireless and sound card which was fixed by reading this forum. Thank you. Been running two days straight with no problems. Installed about five days ago. I tried it before but it was too complicated then.:guitar:

---

### Post by 0xdeadc0de on 2008-04-17
To connect sshfs to home, and reconnect after errors, I made a little script that 1) checks if it's already mounted, 2) checks to see if the network interface exists, 3) mounts it creates .ismounted, unmounts if already mounted but .ismounted doesn't exist

```

#!/bin/bash


LOCATION="/media/server"
INTERFACE="eth1"
LOOP=9
ARGS=""
RESPONSE=""
while [ $LOOP = 9 ]; do
	if [ -f $LOCATION/.ismounted ]; then
		LSREP=$(ls -l $LOCATION)
		if [ "$LSREP" = "total 0" ]; then
                        echo "Connection Error"
			rm $LOCATION/.ismounted
			continue;
		fi
		echo "Already mounted!";
		sleep 20
	else
	echo "Nope, check net interface"
		ETH1=$(ifconfig | grep "$INTERFACE")
		if [ "$ETH1" = "" ]; then
			echo "Net interface doesn't exist, waiting"
			sleep 20;
			continue;
		else
			echo "Net interface working, trying to mount"
		fi
		RESPONSE=$(mount $LOCATION);
		if [ "$RESPONSE" = "fuse: bad mount point \`$LOCATION\': Transport endpoint is not connected" ]; then
			fusermount -u $LOCATION
			RESPONSE=$(mount $LOCATION);
		fi
		if [ "$RESPONSE" = "" ]; then
			LSREP=$(ls -l $LOCATION)
			if [ "$LSREP" = "total 0" ]; then
				echo "Connection Error"
				fusermount -u umount $LOCATION
				continue
			fi
			TOUCHREP=$(touch $LOCATION/.ismounted)
			if [ "$TOUCHREP" != "" ]; then
				echo "Connection Error"
				unmount $LOCATION
				continue
			fi
			echo "Success, touch ismounted"
		else
		if [ $RESPONSE="fuse: mountpoint is not empty" ]; then
			umount $LOCATION
			echo "Mounted, unmount"
		else
			echo "Unknown response $RESPONSE"
		fi
		fi
	fi
done


```
updates: 
*Fixed another connection bug, hopefully the last?
*Don't consider 0 files on mounted mount to be mounted (fix's a bug)
*Fixed connection errors if connection is lost and it's not unmounted - it stays mounted, the mount command doesn't return anything but touch errors
*Added location variable and interface variable for easy changing
*Fixed REPNOSE typo, 
*Removed awk dependency
*Removed unnecessary exec

---

