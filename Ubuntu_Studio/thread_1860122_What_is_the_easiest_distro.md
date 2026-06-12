---
title: "What is the easiest distro???????"
date: 2011-10-14
forum: Ubuntu Studio
---

### Post by Stanley2011 on 2011-10-14
What is the easiest distro to use? One that is easy to set up? One where qjackctl works in?
I have tried archbang it is hard to install. I have tried ubuntu 11.04, ubuntu studio 11.04 and 11.10 no luck. I can not set up qjackctl. I have to have it to do any recording midi keyboard etc. I have followed all the instructions.

---

### Post by collisionystm on 2011-10-14
> **Stanley2011 said:**
> What is the easiest distro to use? One that is easy to set up? One where qjackctl works in?
I have tried archbang it is hard to install. I have tried ubuntu 11.04, ubuntu studio 11.04 and 11.10 no luck. I can not set up qjackctl. I have to have it to do any recording midi keyboard etc. I have followed all the instructions.

try Linux Mint.

Mint and Ubuntu are about as easy as it gets.

---

### Post by Blasphemist on 2011-10-14
It looks like it should work on all the Ubuntu's. You may want to try the forum at this address [http://sourceforge.net/projects/qjackctl/forums](http://sourceforge.net/projects/qjackctl/forums) but if you provide the specifics of your issues when installing someone here may be able to help.

---

### Post by Stanley2011 on 2011-10-14
Will this is this time around just jack. I have tried ever thing I have find. just tried it with patchage and rosegarden no luck.

 p, li { white-space: pre-wrap; }  [COLOR=#999999]14:05:57.777 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]14:05:57.821 Statistics reset.[/COLOR]
 [COLOR=#cccc99]14:05:57.839 ALSA connection change.[/COLOR]
 Cannot connect to server socket err = Connection refused
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]14:05:57.845 ALSA connection graph change.[/COLOR]
 [COLOR=#999999]14:06:13.636 JACK is starting...[/COLOR]
 [COLOR=#990099]14:06:13.637 /usr/bin/jackd -r -m -dalsa -dhw:0 -r44100 -p256 -n2 -D -Phw:0[/COLOR]
 Cannot connect to server socket err = Connection refused
 Cannot connect to server socket
 jack server is not running or cannot be started
 Cannot create thread 1 Operation not permitted
 [COLOR=#999999]14:06:13.659 JACK was started with PID=8117.[/COLOR]
 Cannot create thread 1 Operation not permitted
 jackdmp 1.9.7
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2010 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK server starting in non-realtime mode
 Cannot lock down memory area (Cannot allocate memory)
 control device hw:0
 control device hw:0
 audio_reservation_init
 Acquire audio card Audio0
 creating alsa driver ... hw:0|hw:0|256|2|44100|0|0|nomon|swmeter|-|32bit
 control device hw:0
 Using ALSA driver HDA-Intel running on card 0 - HDA ATI SB at 0xfbcf4000 irq 16
 configuring for 44100Hz, period = 256 frames (5.8 ms), buffer = 2 periods
 ALSA: final selected sample format for capture: 32bit integer little-endian
 ALSA: use 2 periods for capture
 ALSA: final selected sample format for playback: 32bit integer little-endian
 ALSA: use 2 periods for playback
 [COLOR=#ff0000]14:06:21.665 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.[/COLOR]
 JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
 Driver is not running
 Cannot create new client
 JackSocketClientChannel read fail
 Cannot open qjackctl client
 jackd: ../common/JackGraphManager.cpp:45: void Jack::JackGraphManager::AssertPort(jack_port_id_t): Assertion `port_index < fPortMax' failed.
 [COLOR=#999999]14:06:21.767 JACK was stopped successfully.[/COLOR]
 [COLOR=#cc3366]14:06:21.769 JACK has crashed.[/COLOR]

---

### Post by sgx on 2011-10-14
Hi, maximize a terminal window, full screen, and run the command

ps ux

if pulse is mentioned anywhere in the output, issue the command

killall pulseaudio  then start jackd with

jackd -d alsa -r 44100

then start qjackctl, and follow these guides

[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

pclinuxos is much easier than mint. Mint has more 'latest-version'
software in its repositories. I use both, and also puppy studio for portable booting, so I speak from that experience.

The easiest up front is puppystudio 3.3 or its commercial version, Studio4. The software is already installed, RT is set up, and wineasio/reaper are configured by default. You are prompted for and guided through 2 important decisions, the first time you shut down. But package management and default file management are more work
in any puppy linux, than using synaptic an various default file managers in pclinuxos and mint.

Please list your soundcard/chip, video card/chip, motherboard chipset,
and all connected peripherals.
Cheers

---

### Post by Stanley2011 on 2011-10-14
Hi sgx, I'm on linux mint now it dose do have qjack.ctl in its appsbut it has adour but same thing it want work.
run the command

ps ux

---

### Post by sgx on 2011-10-14
open konsole, the bash terminal

bash-4.1$ ps ux
press enter key...

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND

username    3321  4.1  1.1 115976 23248 ?        SNsl 00:29   0:01 /usr/bin/qjackctl
username    3334  0.5  0.1  32996  3464 ?        SNsl 00:29   0:00 
 /usr/bin/jackd -P89 -t200 -dalsa -r44100 -p512 -n2 -D -

----------------------------------------------------------------------
click and drag the mouse from a top corner of konsole, to the bottom,
move the mouse to the opposite corner, all the text will be selected. 

Now, choose the copy command in the konsole file menu,
then left-click in your web browsers reply window, and choose
'paste' from the web browser 'edit' menu.
Seeing the output is helpful to find the villain.

Also post the text from this command

sudo gedit /etc/security.d/limits.conf

and from this:

aplay -l

Cheers

---

### Post by Stanley2011 on 2011-10-14
OK here you go.

username@ubuntustanley:~$ USER PID %CPU %MEM VSZ RSS TTY STAT START TIME COMMAND
USER: command not found
username@ubuntustanley:~$ USER PID %CPU %MEM VSZ RSS TTY STAT START TIME COMMAND username 3321 4.1 1.1 115976 23248 ? SNsl 00:29 0:01 /usr/bin/qjackctl 
USER: command not found
username@ubuntustanley:~$ username 3334 0.5 0.1 32996 3464 ? SNsl 00:29 0:00
username: command not found
username@ubuntustanley:~$ /usr/bin/jackd -P89 -t200 -dalsa -r44100 -p512 -n2 -D-
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Cannot create thread 1 Operation not permitted
Cannot create thread 1 Operation not permitted
JACK server starting in realtime mode with priority 89
Cannot lock down memory area (Cannot allocate memory)
control device hw:0
control device hw:0
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|512|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
Using ALSA driver HDA-Intel running on card 0 - HDA ATI SB at 0xfbcf4000 irq 16
configuring for 44100Hz, period = 512 frames (11.6 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
Cannot use real-time scheduling (RR/89)(1: Operation not permitted)
AcquireSelfRealTime error

---

### Post by sgx on 2011-10-14
A few things to try, reboot, and use this command

jackd -P50 -t200 -dalsa -r44100 -p512 -n2 -D

then start qjackctl

If that fails, use the same command with sudo

sudo jackd -P50 -t200 -dalsa -r44100 -p512 -n2 -D

Type the command    groups

audio, and your username should be in the list. There is a sytem software to manage groups and users.

in a new terminal, type

sudo gedit /etc/security/limits.conf

post the text of the file that opens, the last 4 lines should look like this:


@audio          -       rtprio           99
@audio          -       nice             -15
@audio          -       memlock          unlimited
# End of file

 The spacing between the elements of the top row, should be
10, 7 and 11. (the forum removes the spacing!)The lower row elements should line up with the top row, and then save the file,
and reboot.

---

### Post by dFlyer on 2011-10-14
All linux is easy to use if you can get past the windows mind set.

Ubuntu
Mint
SuSE
RedHat
Debian

Just to name a few.

---

### Post by Stanley2011 on 2011-10-14
ok. I am wondering if I should have #audio etc.?

#<domain>      <type>  <item>         <value>
#

#*                 soft     core            0
#root             hard    core            100000
#*                 hard    rss             10000
#@student      hard    nproc           20
#@faculty       soft     nproc           20
#@faculty       hard    nproc           50
@audio           -         rtprio          99
@audio           -         nice            -15
@audio           -        memlock         unlimited

The terminal says

(gedit:8006): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.MHOK3V': No such file or directory

(gedit:8006): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

---

### Post by sgx on 2011-10-14
OK, the file may NOT be limits.conf anymore, but is in a nearby spot and with a similar name, audio.conf. The settings are almost the same.

sudo gedit /etc/security/limits.d/audio.conf

go here and scroll halfway down the page to the Realtime Support
section.

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

It describes the file, and the installation of the RT-kernel.

Cheers

---

### Post by Stanley2011 on 2011-10-15
Late yesterday I reinstalled Ubuntu studio. I like the look and feel of it. I would like to get studio 4 but have to wait till the 1st of the mouth. I still need to get more hardware for this project. 1) Behringer Xenyx X1222USB 12- channel USB Mixer. Are there software that can be use in it place? 2) Behringer UM250 25Key MIDI keyboard with audio interface. 3) Behringer B1031A 2- way studio monitor speakers. 4) HDMI Video Card. 5) M-audio PCI Card. Where can I find out if any of these thing are support by Linux?
[IMG]http://q.ebaystatic.com/aw/pics/s.gif[/IMG]

---

### Post by sgx on 2011-10-15
Hi, hdmi video is still new, will likely be a problem, second or third generation nvidia graphics cards have been around awhile, so there was time to make solid drivers for them. I use a 9400 gts agp model. 8500/8600 also should be affordable used, avid gamers are a good source. nvidia make a new uncomplicated pci card to, usually $50 or so.

An maudio pci card, with 5pin midi, mic preamps and multiple i/o is a good choice, well supported with the snd_ice1712 kernel module. I use an maudio 24/96 pci, don't need the many i/o, and it works and sounds great.

[http://www.musiciansfriend.com/pro-audio/m-audio-delta-1010-lt-pci-digital-audio-computer-interface/701376000000000](http://www.musiciansfriend.com/pro-audio/m-audio-delta-1010-lt-pci-digital-audio-computer-interface/701376000000000)

For a mixer software, 

[http://www.harrisonconsoles.com/joomla/index.php?option=com_content&task=view&id=108&Itemid=42](http://www.harrisonconsoles.com/joomla/index.php?option=com_content&task=view&id=108&Itemid=42)

This is high quality at a great price, and a demo can be tried.

For a midi keyboard, ebay/craigslist, have older lightly used synthesizers with 5 pin midi ports, they usually have better key action than cheap new ones. E-mu, yamaha, roland, korg, kurzweil, ensoniq, alesis, plus they often come with great sounds built in. If you see one of interest, check its reviews at

[http://www.vintagesynth.com/menufull.php](http://www.vintagesynth.com/menufull.php)

So $600-$800 price range for an studio excellent setup that won't drive you crazy, with sound quality that won't ever be obsolete.
Cheers

---

### Post by Stanley2011 on 2011-10-20
Ok as of right now I have gave up on JACK!!! I have ask this be for what is the easiest studio distro to run jack in or what distro is jack really stable in? why do so many ppl have a hard time getting JACK up and running? To me Jack is not stable and needs to be fix. Or some one needs to write a new program. Now if Puppy Studio 3.3 is the most stable how do you install it and where to get it from? By stable I mean that after the distro is installed Jack works out of the box.

---

### Post by sgx on 2011-10-20
There is a link in the text below to puppystudio .iso. Note
the passwords. When burned to a CD, and booted, the main screen has a toolbar with the qjackctl icon, so it is easy to start and use, right from the live cd. You can choose zynaddsubfx from the audio menu, then connect it in the qjackctl alsa and audio tabs, as per the wiki page and ubuntu how-to pages. Select the desired items on the left and right sides of the panel, and press the connect button, and a line is drawn between them. Alsa tab for midid keyboard, audio tab
for soundcard output, both must connect to zynaddsubfx.

When you end your first puppy session, you will be prompted to store your settings, which will go in a file on your hardisk. The next liveCD session will load it's settings from that file.

from here:  [http://www.murga-linux.com/puppy/viewtopic.php?t=72402](http://www.murga-linux.com/puppy/viewtopic.php?t=72402) 

"Hi all,

Thought you might like to know that this iso (377.92mb) is available for download now, with 10wt3ch's permission:

[www.puppylinuxstuff.meownplanet.net/10wt3ch/PuppyStudio3.3-rt.iso](www.puppylinuxstuff.meownplanet.net/10wt3ch/PuppyStudio3.3-rt.iso)

Enter username: puppy and pawsword: linux when prompted, thank you.

This OS features a large selection of popular multimedia applications, targeted at musicians and audiophiles, and the kernel has been optimised for real-time synchronisation.

Some of the apps included are Jack, Ardour (a digital audio workstation), and Rosegarden (a MIDI + Audio sequencer which includes notation and audio editing).

Enjoy Cool "

Cheers :)

---

### Post by sgx on 2011-10-20
So I'm posting this from puppy studio, installed on a usb stick.
click the  qjackctl button, far left icon on the tasksbar,
and when the gui appears, press the start button. jackd is running.

Now go to the menu  

Multimedia -Media Tools -zynaddsubfx

when it starts, press the connect button on the main
qjackctl gui, and in the alsa tab, select zynaddsubfx on the right,
to your midi connection on the left.

In the audio tab, zynaddsubfx should be already connected to your
soundcard. 

If you have no midi keyboard, press the vK button on the zynaddsubfx screen, to bring up its own keyboard.  Now go to

Multimedia -Media Tools - Jack Timemachine

In the qjackctl audio tab, connect zynaddsubfx to Timemachine.
When you play zynaddsubfx, you'll see it in the Timemachine meter,
so adjust the zynaddsubfx volume, press the Timemachine record button.
Press it again, to complete recording. The recorded file will look like

tm-2003-01-01T02-40-37.w64  Import this into audacity, edit, and export
as mp3, or wav

Cheers :)

---

