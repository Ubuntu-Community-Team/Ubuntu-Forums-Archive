---
title: "Maybe Useful Info for all sound problems posted"
date: 2011-06-13
forum: Ubuntu Studio
---

### Post by Flaggmann on 2011-06-13
Method I use to run audio in ubuntu 11.04, uses ALSA and JACK Audio connection kit.

Step 1. Disable pulse elegantly  (credits for procedure and also link to pdf instructions from [http://www.jeffsplace.net/node/12](http://www.jeffsplace.net/node/12) )

Disable the PulseAudio server and gstreamer's awareness of it;
   1. Tell the packaging system to always rename any file in a package named /usr/bin/pulseaudio 
      to /usr/bin/pulseaudio.ubuntu and /usr/lib/gstreamer-0.10/libgstpulse.so to /usr/lib/gstreamer-0.10/libgstpulse.so.ubuntu.
      This prevents the pulseaudio daemon from running and gstreamer applications from being aware of it.
   2. Put in our own dummy /usr/bin/pulseaudio file

To do that, run the following four commands:

sudo dpkg-divert --add --divert /usr/lib/gstreamer-0.10/libgstpulse.so.ubuntu --rename /usr/lib/gstreamer-0.10/libgstpulse.so
sudo dpkg-divert --add --divert /usr/bin/pulseaudio.ubuntu --rename /usr/bin/pulseaudio
sudo sh -c 'echo '\''#!/bin/sh'\'' > /usr/bin/pulseaudio'
sudo chmod a+x /usr/bin/pulseaudio

Ensure that gstreamer uses ALSA instead of PulseAudio. Run:

gstreamer-properties

and set everything from PulseAudio to ALSA.

As of Ubuntu 10.04, the ubuntu-desktop metapackage also depends on libsdl1.2debian-pulseaudio,
but we want libsdl applications (games, typically) to use alsa instead. Trick the package management 
system into thinking we have libsdl1.2debian-pulseaudio installed by installing the following 
dummy package: libsdl1.2debian-pulseaudio-dummy_1.0_all.deb. 
You can save it somewhere and double-click it to install it or, in a terminal, type

sudo dpkg -i libsdl1.2debian-pulseaudio-dummy_1.0_all.deb
...in the directory where you saved it.

After you have installed the dummy package, now type the following:

sudo apt-get install libsdl1.2debian-all

This should automatically remove the real libsdl1.2debian-pulseaudio package, keeping the dummy, and installing a libsdl library that includes alsa support.

If you want to restore the ALSA volume controls in gnome-panel, use a third party repository by adding the following lines to 
your /etc/apt/sources.list file, replacing lucid with maverick or natty, as necessary:

deb [http://ppa.launchpad.net/dtl131/ppa/ubuntu](http://ppa.launchpad.net/dtl131/ppa/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/dtl131/ppa/ubuntu](http://ppa.launchpad.net/dtl131/ppa/ubuntu) lucid main

Add the key for the repository by running this command:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com F76FFEBE

Then update to the newer packages:

sudo apt-get update && sudo apt-get upgrade

The volume applet in the indicator applet will no longer work. Remove it:

sudo apt-get remove indicator-sound

To add the regular volume applet back, right click on your panel, click "Add to panel...", and select "Volume Control."
Undo
#######################################################################################
* to undo what was done:
*
*1.To undo the file renamings, you can type:
*
*      sudo rm /usr/bin/pulseaudio
*      sudo dpkg-divert --rename --remove /usr/bin/pulseaudio
*      sudo dpkg-divert --rename --remove /usr/lib/gstreamer-0.10/libgstpulse.so
*
*2. Run --> gstreamer-properties
*                -and switch everything from ALSA back to PulseAudio.
*
*3. To restore the original packages, you can type:
*
*      sudo apt-get install libsdl1.2debian-pulseaudio indicator-sound ppa-purge
*      sudo ppa-purge dtl131
########################################################################################
Configure JACK to autostart the server when launched.

Step 2. After having installed all the jack tools and utilities (meters, mixers, racks and metrenomes etc.) start jackd
by selecting qjackctl from the start menus or typing the command 'qjackctl' in a terminal window. This will open the jackd status window. - click on SETUP and put check mark in REALTIME and set driver to ALSA (I also use verbose messages); then
click on the Misc Tab, put a check in "Start JACK audio server on application startup", "Enable system tray icon", & "Start minimized to system tray" then click OK. ( note the save to location .jackdrc is a hidden file in each user's home DIR) {{{I have yet to confirm it, but I suspect removing the checkmark from "single application instance" is where one can 
enable multiple instances of jack}}}


Configure AUTO-Launch of JACK on login (needs to be running first or no other programs will recognize it's existence)

Step 3. From the Start menu, select  "SYSTEM" -->  "Preferences" --> "Startup Applications"
        - click Add    in the Name box enter  "QjackCtl"
                       in the Command box enter "pasuspender /usr/bin/qjackctl"
                       in the Comment box enter "start jackd" (or whatever propmy you want to see in the startup apps list)
        -click Save

** note here I found there was a lot of stuff autostarted that I don't use that I deleted from the startup list which seemed to help speed 11.04 up a bit {ie bluetooth or assisted user enhancements like larger fonts etc} 

        -click "Close"

I then logged out and restarted the box. I see the qjackctl icon in the systray. Right and left click options allow you to view the windows, connections patchbays and messages etc. a tiny little green on white PLAY icon shows up to indicate JACKD is running and the RT in the window display indicates Real Time for low latency. When I view the connections and launch audacious etc. I am able to see them appear in the connections windows available for patching.

Something else to note is that when jack launches it appears to connect outputs to all playout ports; just click the disconnect all and manually drag and drop the connections to the single or stereo desired connections.

If you experience excessive buffer overrun errors in the jackd messages window, add "-S" option to the start command
in the jack SETUP window and resave and restart it. 


Additional info ( credit Paravel Systems)  for jack audio use that might be relevant:

Configure realtime scheduling:
Enable realtime support in the OS via PAM (especially useful if using ALSA or JACK) by editing the /etc/security/limits.conf file.

   press <alt><f2> # to bring up the start Run Application popup
   enter the command: gksudo gedit /etc/security/limits.conf
   copy and paste the following lines some place in the file (near the bottom)
   this will give users in the audio group the ability to run programs at a 
   higher priority:
   # limit realtime and memory locking access to users in the group audio
   # there is no way to say "allow locking all memory", 4G should be enough
   *       -   rtprio      0
   *       -   nice        0
   @audio      -   rtprio      100
   @audio      -   nice        -10
   @audio      -   memlock     4000000

   Save the changes and exit gedit.
   Reboot the machine and log back in to the Ubuntu workstation for these changes to take effect.

You should also have an asound.conf file created to match your sound hardware configuration. (Info available from
ALSA project web site).

I would suspect that removing the check mark from "single instance" in the JACK SETTINGS and creating a separate jackd config for each instance ( one for each of the extra sound cards), naming them each differently and adding all to the startup applications folder would possibly work to see all cards getting used.
The settings each being different hardware and driver specific, as well as a different name; although again here I have yet to confirm this multi card operation.

For what it may be worth to you.... cheers  from a Canucks fan !!   ***grin***

---

### Post by sgx on 2011-06-13
Easier for a hockey player to become futball  player,
than the other way around! :wink:

A thorough sticky for setting up jackd and alsa is really needed here.
Thanks for posting all this. :)
Cheers

---

### Post by Flaggmann on 2011-06-14
[http://alsa.opensrc.org/MultipleCards](http://alsa.opensrc.org/MultipleCards)

---

### Post by jejeman on 2011-06-14
Do one really need to do all this? Does stopping pulseaudio is not enough? When you stop pulseaudio you always use plain alsa. I agree on change for gstreamer-properties to alsa, but I think it is not necessary.

---

### Post by Flaggmann on 2011-06-14
Yes pulseaudio will respawn and of course grab hardware away from whatever you predefine in the midst of what you are doing so just turning it off is not enough, UNinstalling it as an alternative doesn't work well either because the desktop will disappear and you will be in run level 3 from then on.

If you do a google search on "Rivendell Audio Automation wiki" and read through their installation instructions, you will find the explanations for having to kill pulseaudio softly. 

When you use the alsa config files, once you become thoroughly familiar with them, you can see that you can customize the labeling that appears in jack audio connection and patch bay panels by using thes config files. 

I know a lot of folks use alsa and jack for music composition and production, but there is a whole world out there that also uses it for other purposes, and understanding their use can often make it easier to find new ways to enhance music production as well.

---

### Post by jejeman on 2011-06-14
When I said to stop pulseaudio, I aslo ment to disable respawn so it can be "really" stoped.
To achive this one can make user conf file
~/.pulse/client.conf
and put inside option:
autospawn=no
And then stop the daemon with
```
pulseaudio -k
```
To start it again command is
```
pulseaudio -D
```
I'm no expert on pulseaudio, but this worked for me. For me it's lot easyer. And I also like this because it's a user not system configuration.
Volume icon will disappear, so that part about installing volume icon for alsa is needed, and changeing the gstreamer properties too. But all that it's not necessary if pulseaudio disablement is temporary.

---

