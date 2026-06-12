---
title: "Qjackctl will not run after upgrade to 10.04"
date: 2010-05-12
forum: Ubuntu Studio
---

### Post by prylux on 2010-05-12
I was using qjackctl in ubuntu 9.10 but I upgraded to 10.04 and I just tried to start qjackctl. When I do I see the jack control panel appear on the desktop for a moment then it disappears. I tried to run it from the Terminal but got this message...
[INDENT]
~$ qjackctl
Suspending PulseAudio
WARNING: Child process terminated by signal 11[/INDENT]

Then it disappears and shuts down.
I have read some other forums and checked the /etc/security/limits.conf
and added
  @audio          -       rtprio          100
  @audio          -       nice            -10
I have made sure my user account is part of the audio group

I have tried to start jackd in a terminal using:
  [INDENT]~$ jackd -R -d alsa
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    2315442
JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
[/INDENT]

I don't understand why qjackctl will not work now?

---

### Post by prylux on 2010-05-12
I just tried to start qjackctl as "administrator" and I could get it to stay on the desktop and could get into the "preferences" but when I clicked on the start button it crashed again and now when I try to start it as root it will not stay on the desktop but crashes...

---

### Post by prylux on 2010-05-12
I loaded Kernel 2.6.32.21 and tried to start qjackctl and got this output in the "Messages" window:
[INDENT]
17:41:49.043 Patchbay deactivated.
17:41:49.340 Statistics reset.
17:41:49.439 Startup script...
17:41:49.440 artsshell -q terminate
17:41:49.446 ALSA connection graph change.
sh: artsshell: not found
17:41:50.020 Startup script terminated with exit status=32512.
17:41:50.021 JACK is starting...
17:41:50.022 /usr/bin/jackd -r -dalsa -dhw:0 -r48000 -p1024 -n2 -D -Chw:1 -H -M
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    2315442
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0|hw:1|1024|2|48000|0|0|hwmon|hwmeter|-|32bit
control device hw:0
17:41:50.098 JACK was started with PID=2549.
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
17:41:50.248 JACK was stopped successfully.
17:41:50.249 Post-shutdown script...
17:41:50.249 killall jackd
17:41:50.253 ALSA connection change.
jackd(2522): Operation not permitted
jackd: no process found
17:41:50.664 Post-shutdown script terminated with exit status=256.
17:41:52.343 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/INDENT]

I don't have anything using "hw:0" to my knowledge... How do I find out what is using the hardware? And what is artsshell?

---

### Post by sgx on 2010-05-13
a few things to try from a cold start

sudo alsaconf  -should start a soundcard configuration process

jackd -d alsa -r 44100

barebones non realtime jackd

Make sure all wireless, internet, 3d, and audio apps
are off, and none start automatically on the sly in Lucid.

You can also choose to reinstall qjackctl, jackd (its name may be different in synaptic) and their libraries and Qt gui dependencies.

I saw this reply about artshell, in an 2009 episode much like yours:

"the very first error message about artsshell not found means that you do not have audio permissions, and thus nothing will work right if at all. To give yourself permissions, go to System->Administration->Users and Groups. Select and Unlock your user name. In your Properties, in the User Privileges tab, check "Use audio devices". Save your changes and re-boot (I select the RT kernel from Grub). Now Jack runs for me."

Cheers

---

### Post by prylux on 2010-05-13
Thank you very much for the response, I tried the things you suggested with the results below...  

I tried:
> sudo alsaconf -should start a soundcard configuration process
and got:
[INDENT]sudo: alsaconf: command not found[/INDENT]

I did:
> jackd -d alsa -r 44100
But qjackctl still won't stay up...
I can get jackd to run in realtime and without through bash
I can see it running as a process and if I run jackd in bash again it says it is running already...

> You can also choose to reinstall qjackctl, jackd (its name may be different in synaptic) and their libraries and Qt gui dependencies.
I tried this and still the same, I even tried "Completely Remove" in synaptic but still nothing changed

> give yourself permissions, go to System->Administration->Users and Groups. Select and Unlock your user name. In your Properties, in the User Privileges tab, check "Use audio devices"
I looked but I already have permissions selected...

 I inserted a Ubuntu 10.04 LIVE CD and installed Jack and Ardour and they work 
(Though it wants me to configure some things for realtime) so I know it's not hardware. 
It was working fine before the move to 10.04 (It was working in realtime even).

 I would like to figure this out because I love a mystery.
I know that I can reinstall Ubuntu and solve this issue, but that is the reason I stopped using Windows, 
I'm tired of solving issues through re-installation of the OS.

 The operating system is open to us with Linux, 
I just need to figure out, how to figure out where to look for the issue and then correct it. 
My only fault is I'm not a programmer just a intuitive user...

If anyone has any other ideas or insight please let me know. 
I use this computer as the DAW in my bands studio and we are in big need of it soon...
 And would like to put a [SOLVED] on this thread

---

### Post by sgx on 2010-05-13
Hi, you could try patchage, its a different gui to connect jackd items.
qtractor may be another option. If time is running out, reinstalling the old working version may be needed. Backups backups backups.
A separate /home partition makes reinstalls easy, preserving lots of configurations by not formatting /home.

I think qjackctl has some issues. On a different distro and kernel, I have similar results. 

It appears alsaconf is a configuration script in some distros that uses alsactl 

Look in /sbin or /usr/sbin or /usr/bin for alsactl or similar. 

alsactl --help gave some options, I ran

sudo alsactl init

and it replied:

Unknown hardware: "ICE1712" "ICE1712 - multitrack" "" "0x1412" "0xd634"
Hardware is initialized using a guess method

(ICE1712 is my soundchip) I started jackd as earlier, no problems, but no changes to qjackctl misbehaving.

Cheers

---

### Post by prylux on 2010-05-15
Okay I will type as I try these options...

> Hi, you could try patchage

Got this in bash:

[INDENT]~$ patchage
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
Connected to JACK server with client name 'LASH_Server'
Opened ALSA sequencer with client ID 128
Listening for connections
Connected to LASH.
Loading configuration file /home/user/.patchagerc
Unable to load file /home/user/.patchagerc!
Created project project-1 in directory /home/user/audio-projects/project-1
Added client 23ad532a-ce66-4576-86b3-5114b470fa34 of class patchage to project project-1
Client 23ad532a-ce66-4576-86b3-5114b470fa34 set its name to 'Patchage'
Connecting to Jack... Done
Connecting to Alsa... Done
Client Patchage removed from project project-1
Project project-1 removed
Segmentation fault
[/INDENT]

> qtractor may be another option

[INDENT]~$ qtractor
Segmentation fault
[/INDENT]

> ~$ sudo alsactl init

[INDENT]Unknown hardware: "HDA-Intel" "Conexant CX20561 (Hermosa)" "HDA:14f15051,103c30d9,00100000" "0x14f1" "0x5051"
Hardware is initialized using a guess method
[/INDENT]

>  If time is running out,reinstalling the old working version may be needed

I know this is an option and right now I am using Windows and KristalAE to record as I try to rectify this issue. Like I said earlier though, there is a stubborn part of me that believes that there is a solution to this problem. I'm not willing to give up so easily. When I used Windows "Nuke the HDD" was normally the way to fix every major issue

 I started using Linux not because it was free but because it was open. I could get under the hood of the OS and fix it. I'm the kind person that will go get a book if my car breaks down even though I'm not a mechanic. And I will tear out the carpet, tear down the paneling, drywall, paint, and trim and install crown molding in the living room without ever doing any of it before in my life, but doing it by asking questions and reading...

I figure most of us feel the same. I am not an expert on Linux and often times I learn more on the forums than I can contribute but I can apply what I know and I think that if we can solve this issue we can help contribute to the community not just fix my issue. I know of one way to fix it now (Nuke HDD), I just don't wanna do it that way...](*,)

---

### Post by 4String_Gal on 2010-05-15
What the hay? No JACK? Or rather, the icon I put on my task bar is there, but when I try to start it, I'm told:

"Could not connect to JACK server as client. Overall operation failed. Unable to connect to server. Please check the messages window for more info."

The messages window says:

 p, li { white-space: pre-wrap; }  [COLOR=#999999]18:15:21.109 Startup script...[/COLOR]
 [COLOR=#990099]18:15:21.110 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]18:15:21.515 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]18:15:21.515 JACK is starting...[/COLOR]
 [COLOR=#990099]18:15:21.516 /usr/bin/jackd -v -P89 -dfirewire -dhw:0 -r44100 -p64 -n3[/COLOR]
 [COLOR=#999999]18:15:21.521 JACK was started with PID=5222.[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 Memory locking is unlimited - this is dangerous. You should probably alter the line:
      @audio   -  memlock    unlimited
 in your /etc/limits.conf to read:
      @audio   -  memlock    6145665
 getting driver descriptor from /usr/lib/jack/jack_dummy.so
 getting driver descriptor from /usr/lib/jack/jack_alsa.so
 getting driver descriptor from /usr/lib/jack/jack_oss.so
 getting driver descriptor from /usr/lib/jack/jack_net.so
 getting driver descriptor from /usr/lib/jack/jack_firewire.so
 no message buffer overruns
 JACK compiled with System V SHM support.
 server `default' registered
 registered builtin port type 32 bit float mono audio
 registered builtin port type 8 bit raw midi
 clock source = system clock via clock_gettime
 loading driver ..
 start poll on 3 fd's
 Enhanced3DNow! detected
 SSE2 detected
 new client: firewire_pcm, id = 1 type 1 @ 0x1ea21c0 fd = -1
 new buffer size 64
 libffado 2.0.0 built Mar 31 2010 16:21:44
 firewire ERR: Error creating FFADO streaming device
 cannot load driver module firewire
 starting server engine shutdown
 freeing shared port segments
 server thread back from poll
 stopping server thread
 last xrun delay: 0.000 usecs
 max delay reported by backend: 0.000 usecs
 freeing engine shared memory
 max usecs: 0.000, engine deleted
 cleaning up shared memory
 cleaning up files
 unregistering server `default'
 no message buffer overruns
 [COLOR=#999999]18:15:21.750 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]18:15:21.752 Post-shutdown script...[/COLOR]
 [COLOR=#990099]18:15:21.752 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]18:15:22.169 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]18:15:23.729 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

Here's more info:

cat ~/.jackdrc
/usr/bin/jackd -R -P89 -dfirewire -dhw:0 -r44100 -p64 -n2

uname -a
Linux computername 2.6.31-10-rt #153-Ubuntu SMP PREEMPT RT Tue Jan 12 11:01:03 UTC 2010 x86_64 GNU/Linux

Mind you, doing anything with Alsa is not going to work for me as I have a firewire sound card (a PreSonus Firepod, which worked just fine with the previous version of Ubuntu Studio.) So, that would be firewire, freebob or ffado. Not alsa. Not pulseaudio. Not anything else. Mind you, only firewire and freebob are choices for me in the setup window.

It seems to me that JACK is the ONE application OVER ALL OTHERS that should work in a "studio" distro. But it's broken, and now I have a broken music machine. And I have no idea how to fix it with this version. This is something that should have been resolved during the release cycle.

I'm very frustrated. All I wanted to do was fire up some tunes while I'm packing for a move out west, and now I can't. The only way I can do that is to reinstall the old version, if I can find the DVD, and I just don't have time.

-Susan

---

### Post by bluesscream on 2010-05-15
> **4String_Gal said:**
> What the hay? No JACK? 

hi susan, these (dist)updates frequently overwrite configuration files and customized settings without asking. This is my way if ffado/jack don't do their job - distilled out of many howto's:
0. run ffadomixer. If it shows the gliders goto 4.
1. Run ubuntustudio-controls with all options defaults marked
2. control files manually: /lib/udev/rules.d/50(or an other number)-udev-default-rules: is there a line 'KERNEL=="raw1394", GROUP="video"' (mostly near the end of the file)?
ls -l /dev/raw1394 should be like 'crw-rw---- 1 root video 171, 0 2009-11-26 09:56 /dev/raw1394. reboot
3. has user rights for audio and video? (system/administration/users and groups/myuser/properties/user rights). If ffadomixer still shows no device goto 10.a.
4. make sure /etc/security/limits.conf contains a line '@audio - rtprio 99'
5. does jackd run with alsa? with rt unmarked? with low performance settings? Explicitely the internal soundchip selected? if not at all goto 10 b
6. reset fw device, make sure the same samplerate is selected as in qjackctl.
7. try lower priorities in jack i.E. default(=10)
8. Is cpu frequency set to full speed - 'userspace max' or 'perfomance' for each core?
9. Have a look into system-monitor-applet - are there zombie-processes of jackd or other stopped programmes?
10. If it's still not running, completely remove a. ffado b. jackd, with all configurations, install them new after consulting the howtos.
good luck
bluesscream

P.S. For me most frequent ffado failure was result of forgetting to set the sample rate in jack  to the same value as selected with the device's knob

---

### Post by sgx on 2010-05-15
the firewire howto is here

[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

jackd -d alsa -r 44100

should let you listen to tunes on a motherboard chip,
if you can't find your old install disc. Seems like I read
that the limits.conf type of file formerly used, is now in a different but nearby folder, have a quick snoop.

On a side note, California, Oregon and Washington
are actually all bankrupt, with massive unfunded public employee
pensions, unsupportable union contracts, and corruption at all
levels of government and management. They did their
last gasp of tax increases, and veiled unprovoked fee hikes,
and are still circling the drain, only faster. Real unemployment is 18%, in the good locations, and getting worse due to the new financial burdens. It is going to get ugly. If one of them will be your new home, be prepared!

Cheers

---

### Post by 4String_Gal on 2010-05-15
> **bluesscream said:**
> hi susan, these (dist)updates frequently overwrite configuration files and customized settings without asking. This is my way if ffado/jack don't do their job - distilled out of many howto's:
0. run ffadomixer. If it shows the gliders goto 4.
1. Run ubuntustudio-controls with all options defaults marked
2. control files manually: /lib/udev/rules.d/50(or an other number)-udev-default-rules: is there a line 'KERNEL=="raw1394", GROUP="video"' (mostly near the end of the file)?
ls -l /dev/raw1394 should be like 'crw-rw---- 1 root video 171, 0 2009-11-26 09:56 /dev/raw1394. reboot
3. has user rights for audio and video? (system/administration/users and groups/myuser/properties/user rights). If ffadomixer still shows no device goto 10.a.
4. make sure /etc/security/limits.conf contains a line '@audio - rtprio 99'
5. does jackd run with alsa? with rt unmarked? with low performance settings? Explicitely the internal soundchip selected? if not at all goto 10 b
6. reset fw device, make sure the same samplerate is selected as in qjackctl.
7. try lower priorities in jack i.E. default(=10)
8. Is cpu frequency set to full speed - 'userspace max' or 'perfomance' for each core?
9. Have a look into system-monitor-applet - are there zombie-processes of jackd or other stopped programmes?
10. If it's still not running, completely remove a. ffado b. jackd, with all configurations, install them new after consulting the howtos.
good luck
bluesscream

P.S. For me most frequent ffado failure was result of forgetting to set the sample rate in jack  to the same value as selected with the device's knob

Hi bluesscream,

Thank you so much!!!

Item 2 above was the culprit.

Meanwhile, ffadomixer tells me that "Somehow the connection to the DBUS-service of FFADO couldn't be established. Shall we take another try?" I don't know if this will matter when I want to record something. But I probably won't be able to test that out for a few weeks. I'm going to keep your tips handy.

I went back into QJackCtrl setup and checked "Realtime" and "No Memory Lock" again, which seemed to make the playback of the CD I wanted to listen to happy:)

I really appreciate your help. Everything worked with the previous version of Ubuntu Studio, and I was really looking forward to the upgrade version of some packages that are now supposed to work with JACK. So, this threw me for a loop!

Note to the developers - you should open up a big README file when there's an upgrade and users have to take these steps manually.

Cheers!

-Susan
:guitar:

---

### Post by 4String_Gal on 2010-05-15
> **sgx said:**
> the firewire howto is here

[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

jackd -d alsa -r 44100

should let you listen to tunes on a motherboard chip,
if you can't find your old install disc. Seems like I read
that the limits.conf type of file formerly used, is now in a different but nearby folder, have a quick snoop.

On a side note, California, Oregon and Washington
are actually all bankrupt, with massive unfunded public employee
pensions, unsupportable union contracts, and corruption at all
levels of government and management. They did their
last gasp of tax increases, and veiled unprovoked fee hikes,
and are still circling the drain, only faster. Real unemployment is 18%, in the good locations, and getting worse due to the new financial burdens. It is going to get ugly. If one of them will be your new home, be prepared!

Cheers

Hi SGX,

Thanks, I read the firewire how to for the last install, and I was just upset that something that worked beautifully was now broken on the upgrade. That shouldn't have happened, imo. I'm very thankful for this great online community:)

I also have my onboard sound disabled, don't have anything connected there. So, Alsa, portaudio, etc are pretty much useless for me.

I currently live in Washington, DC, which is the center of corruption. Not by the public servants I know, they're really good people. But anyway, life is good for now, I'm getting to telecommute from my current job and my boyfriend is in CA. My biggest worry is getting to know new people to play with. I have a lot of friends who play, including an amazing guitarist who is the most easy going person I've ever met in my life:)

Cheers!

-Susan

---

### Post by bluesscream on 2010-05-15
> **sgx said:**
> the limits.conf type of file formerly used, is now in a different but nearby folder, have a quick snoop.
tx for the hint. It's now /etc/security/limits.d/audio.conf created automatically by jackd's postinst and should no longer be be edited by hand but by using dpkg-reconfigure -p high jackd
I should have read news and changelogs ;)
could it be that the problems with not recognized soundchips have to do with linux-alsa-driver-modules, linux-backports-... or alsa headers? I remember such issues from a machine I gave away, had to install these packets and edit  /etc/modprobe.d/alsabase.conf. Don't know if this is helpful...:-k
cheers

---

### Post by sgx on 2010-05-16
> **4String_Gal said:**
> Hi SGX,

Thanks, I read the firewire how to for the last install, and I was just upset that something that worked beautifully was now broken on the upgrade. That shouldn't have happened, imo. I'm very thankful for this great online community:)

I also have my onboard sound disabled, don't have anything connected there. So, Alsa, portaudio, etc are pretty much useless for me.

I currently live in Washington, DC, which is the center of corruption. Not by the public servants I know, they're really good people. But anyway, life is good for now, I'm getting to telecommute from my current job and my boyfriend is in CA. My biggest worry is getting to know new people to play with. I have a lot of friends who play, including an amazing guitarist who is the most easy going person I've ever met in my life:)

Cheers!

-Susan
Hi, for good luck, I keep copies of /etc, and all the relevant .folders,
and have synaptic save the .debs in its cache 
(Settings-->Preferences-->Files menu option in synaptic, and put it all on media and usbsticks just in case. Once in a while ,overwriting a file, or finding a key portion, has saved a reinstall, but having a separate
/home paritition makes reinstall quite painless.

My mains audio setup may be Frankenstinian, but its tame, obediant, and works :) All qualities I'm striving for. ;)

As for session players, ninjam internet jamming in Reaper might be possible, since reaper works so well in wine/wineasio, here is a reaper forum howto link, I have never tried it myself.

[http://forum.cockos.com/showthread.php?t=12578](http://forum.cockos.com/showthread.php?t=12578)

cheers

---

### Post by sgx on 2010-05-16
> **bluesscream said:**
> tx for the hint. It's now /etc/security/limits.d/audio.conf created automatically by jackd's postinst and should no longer be be edited by hand but by using dpkg-reconfigure -p high jackd
I should have read news and changelogs ;)
could it be that the problems with not recognized soundchips have to do with linux-alsa-driver-modules, linux-backports-... or alsa headers? I remember such issues from a machine I gave away, had to install these packets and edit  /etc/modprobe.d/alsabase.conf. Don't know if this is helpful...:-k
cheers
Thanks for finding it. It looks like once again the coders have made
things more even cryptic and confusing for users to configure. :(
(and its not just ubuntu, other linuxi are just as bad). Upgrade to 8.04, and make some music.  :guitar:

---

### Post by mango42 on 2010-05-17
> **sgx said:**
> Upgrade to 8.04, and make some music.  :guitar:

LOL - 9.10's pretty good though, and I'm sure 10.04 will settle down before too long (fingers crossed!)

Do you have any personal recommendations on where to upload copyright-free, 'all-Linux-produced' music without getting entangled in spook run 'social networking (aka Big Brother database)' sites like Farcebook?

---

### Post by sgx on 2010-05-17
A lot of people like Bandcamp. There is no charge, and although it is designed for sales of downloads, it also allows many options, free downloads among them. A review:

[http://blog.artistshousemusic.org/post/92532479/bandcamp-1-0-the-best-home-on-the-web-for-your-music](http://blog.artistshousemusic.org/post/92532479/bandcamp-1-0-the-best-home-on-the-web-for-your-music)

Cheers

---

### Post by mango42 on 2010-05-18
> **sgx said:**
> A lot of people like Bandcamp. There is no charge, and although it is designed for sales of downloads, it also allows many options, free downloads among them. A review:

[http://blog.artistshousemusic.org/post/92532479/bandcamp-1-0-the-best-home-on-the-web-for-your-music](http://blog.artistshousemusic.org/post/92532479/bandcamp-1-0-the-best-home-on-the-web-for-your-music)

Cheers

Thanks - I just checked out the review and did a quick scan of the site - streams well for sure - so long as I don't have to register with CitiGroup's PayScam... Now to dig into who they are and where they're coming from, policy-wise.

"And we won't even ask to play tambourine." - nice ;-)

---

### Post by sgx on 2010-05-18
Are you familiar with the paypal micropayments option? This greatly reduces the fees charged on sales of individual song downloads.
its just a nickel per sale, plus 5% , and 3.5% more if
currency exchange is needed overseas. This seems reasonable, allowing for international sales. A second account can be used if one also sells a lot of more expensive items that would get a higher-than-normal fee under a micropayment account. The micro rate is for items less than $12

[https://micropayments.paypal-labs.com/](https://micropayments.paypal-labs.com/)

Perhaps someday a competitor will come along with better rates,
but I'm not holding my breath :-&

Cheers

---

### Post by prylux on 2010-05-24
I never did find out why Qjackctl didn't work. I nuked the HDD and reinstalled Ubuntu 10.04 but this time I went with the 64bit version.

Jack is now running but I get XRUNs if I run in "Realtime"

 I have tried:

[LIST]
Running the rt-kernel (I did make sure to choose it in grub at boot)[/LIST]
[LIST]Added myself to the "Audio group"[/LIST]
[LIST]Added[/LIST]
[INDENT]  @audio          -       rtprio          99
  @audio          -       nice            -10
  @audio          -       memlock         231086154
to /etc/security/limits.conf[/INDENT] 

It runs fine without checking "Realtime" and checking "Soft Mode"

The only issue I have now, and I don't know if it is because I'm not using "Realtime" or because of my CPU, is that I will have to increase the latency while using Ardour or I will get stuttering in the audio. So I will start with a buffer size of 64 and then I will end up with a buffer size of 1024 or higher.

:-k
My system is a laptop with: 

Pentium Dual-Core T2330 @ 1.6GHz
3GB ram
Ubuntu 10.04 64bit
Beringer UAC202 USB external sound card
Using Ardour as the DAW

and this is my Jack settings:

[IMG]http://i93.photobucket.com/albums/l78/prylux/Screenshot.png[/IMG]

Is there anything I could do to help the latency or maybe get the Realtime working? :-k


If I am using the package for jackd from the repositories is it a 64bit version of jackd or am I using the 32bit version
Also why isn't there a jackdmp version for Ubuntu?

Thanks...

---

### Post by sgx on 2010-05-24
Hi, the release notes for 10.04 mention a change to where and
how jackd checks limits.conf, you might verify that the
edited file you have, agrees with the new binary version the system creates.

jackd has several zombies wandering around creating chaos,
it would be handy to kill off all but one, but here they come again! :)

---

### Post by bluesscream on 2010-05-25
hi prylux,
I guess, your jack's settings are too low.
Just give it a try with frames/period = 128,
periods/buffers = 3 
This will lead to 8ms latency, the time a sound event needs for running from it's source to your ear if you stand away 240 cm, 
good enough for all live played software synthies or home studio playback recording activities.
Another really important for getting reasonable performance is fixing cpu frequencies at highest available level: right click top panel, select and configure cpu frequency scaling applet separately for each core. There are postings around in this forum how to change default cpu frequency governor from ondemand to userspace or performance - but this might be no good option when your notebook is running on battery. But if it's plugged in, for making music this absolutely is a must.
best regards bluesscream

---

### Post by prylux on 2010-06-20
I know it's been awhile...

but

Thanks bluesscream
That helped
:guitar:

---

