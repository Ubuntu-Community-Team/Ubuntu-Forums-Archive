---
title: "Ubuntu Studio and Tascam US-122 Install / Setup (Complete) with Jack Guide"
date: 2016-03-17
forum: Ubuntu Studio
---

### Post by Dave_Lamb on 2016-03-17
# After reading through many forums and instructions, I have pieced this set together and proved it works for a UBUNTU STUDIO
# installation using a Tascam US-122 external soundcard.
# Make sure the Tascam US-122 usb cable is connected at all times, unplugging/plugging gets unpredictable problems
# with other usb devices.
# for all commands use a terminal screen, for editing files use gedit (under root user for blocks of commands, and use sudo before commands for
# single root user access to files.
# Type the following commands exactly as documented in this post.
 
 
# From a fresh install of Ubuntu open a Terminal
# Load the Firmware for Tascam US-122
sudo -i -u root (then enter your root password)
apt-get update
apt-get install fxload alsa-firmware-loaders
wget [ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.16.tar.bz2)
tar xf alsa-firmware-1.0.16.tar.bz2
mkdir /usr/share/alsa/firmware
cd alsa-firmware-1.0.16 && mv * /usr/share/alsa/firmware

# Create a special rule for UDEV to autoload the firmware 
in /etc/udev/rules.d/55-tascam.rules (requires a kernel > 2.6.15) 
by using any editor or gedit. You may need to alter some paths to match exactly where your system has stored the required files.
BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8006", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/sbin/fxload -D %N -s /usr/share/alsa/firmware/usx2yloader/tascam_loader.ihx -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx'"
BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8007", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/usr/bin/usx2yloader'"
# Exit the editor.

# Add these lines to the file /etc/asound.conf (on entering the file there are no lines in my file)
pcm.Live        { type hw; card Live; }
ctl.Live        { type hw; card Live; }
pcm.USX2Y       { type hw; card USX2Y; }
ctl.USX2Y       { type hw; card USX2Y; }
pcm.!default    pcm.USX2Y
ctl.!default    ctl.USX2Y
 

# Symlink your usx2yloader (lights up the Tascam US-122) to the /lib/firmware folder (pick the command which suits where
# your current usx2yloader is:-
ln -s /usr/share/alsa/firmware/usx2yloader /lib/firmware/usx2yloader
OR
ln -s /usr/local/share/alsa/firmware/usx2yloader /lib/firmware/usx2yloader

# Set up Real Time for your user name
sudo adduser (your_username) audio   Note-Do not type the brackets and this will probably say user already a member of audio
# Add these lines to the /etc/security/limits.conf 
@audio - rtprio 99
@audio - memlock unlimited
@audio - nice -10

# Now check Soundcards on your system 
cat /proc/asound/cards 
# if the USX2Y is not present restart your computer and check again

# You will now see your your main card as 0 and the USX2Y for the Tascam as 1.

# Now force the order which Jack Connection Kit will see the soundcards by editing the /etc/modprobe.d/alsa-base.conf file.
# You need the names of the soundcards to do this - found on the previous command cat /proc/asound/cards after the device numbers.
# Add these lines to the end of the alsa-base.conf file.
options snd-usb-audio index=-2
options snd-hda-intel id=USX2Y index=0
options snd-hda-intel id=INTEL index=1
# Where USX2Y and INTEL are your card names.
# Now restart your computer again to pick up these changes.

# Now lets light up the Tascam US-122 - open a terminal and enter the following command - make sure the USB cable is plugged in at all times, I found that plugging/unplugging
# disables all other USB sockets so you lose your wireless keyboard/mouse with a crash reboot your only way out!
sudo usx2yloader
# The USB green light on the Tascam US-122 will now be on, so we can now test this card and get some sound out of it.
# Plug you guitar into the Tascam US-122 - Line/Guitar In on left side and adjust the input and output volume controls.
# Start Jack Audio Connectio Kit QjackCtl from your drop down menu Start-Audio Production-QjackCtl and go to the Setup screen
# Realtime box should be ticked
# Frames/Period should be set to 1024
# Sample Rate should be 48000
# Periods/Buffer should be set to 2
# Driver should be alsa
# Interface - overtype this with hw:USX2Y - it will not be in the drop down selection
# Leave all other parameters as set by the program
# OR put the following commands in a bash script and run from the desktop after running sudo usx2yloader

jack_control eps realtime true
jack_control ds alsa
jack_control dps device hw:USX2Y
jack_control dps rate 48000
jack_control dps nperiods 2
jack_control dps period 1024
# Click OK - you will need to stop/start Jack control for this to take effect
# Now check all volumes are not muted with Alsa Mixer and Pulseaudio - GUI programs in Audio dropdowns.
# For Alsa - Audio Production/Mixers and Card Control/Audio Mixer from start menu
# For PulseAudio - Media Playback/PulseAudio Volume Control from start menu.
# Close all programs and restart the computer.
# Open terminal and do sudo usx2yloader again to power up Tascam.
# I am using a guitar as input so do the following:-
# Start Jack Control
#
# Start Guitarix from within Audio programs
# Guitarix will be started. Open the Tuner (this will give the first indication every thing is working once you have completed the next step).
# Open the Messages window within Jack - this will show you whats is going on and any error messages
# Now you need to set up the Jack Connections
# Click Connect on the Jack panel
# under the Audio tab do the following
# Click Expand All
# Click Disconnect All
# Drag system/capture_1 on left pane to gx_head_amp on right pane (Guitarix tuner will now light up - Tascam working!!)
# Drag gx_head_amp on left pane to gx+head_fx on right pane
# Drag gx_head_fx on left pane (both out_0 and out_1) to system on right pane (will trace to both playback 1 and 2)
# under the ALSA tab do the following
# Drag the Tascam US-X2Y in the left pane to the Tascam US-X2Y in the right pane (you should now hear the guitar through your Monitors/Speakers)
# Close the Connections pane
# PLAY WITH GUITARIX - great piece of software.
# Note - setting within Jack Setup are for me due to an old pc being used, latency is not great but ok - change the rate and period to suit the speed
# of your computer and reduce latency times. The message box in Jack will tell you if you are trying to go too low - XRUN CALLBACKS will start to appear.
# Hope this helps someone out there.

---

