---
title: "What worked for me for Ventrilo"
date: 2009-03-10
forum: Wine
---

### Post by xXNI4NI on 2009-03-10
I realize there are thousands of thousands of threads of getting wine/ventrilo installed and the like but what I also am finding that alot people get through those steps but are stuck in trying to hear themselves/talking to work so i decided to help out those who don't have the option to support linux and make the switch to alternate voice/chat programs, here's what worked for me regarding getting others to hear you:
Under the Wine Configuration Menu (Applications-Wine-Configure Wine) choose the Audio tab and ensure ALSA is selected.
Next is to get the repositories for ALSA via Synaptic (System-Administration- Synaptic Package Manager). 
Search ALSA.
Check the following for Install.
-alsa-base
-alsa-firmware-loaders
-alsaplayer-alsa
-alsa-source
-alsa-tools
-alsa-utils
-libasound2
-linux-sound-base
(i realize some come bundled but it's a good checklist)
Install-Reboot
Open Ventrilo (Applications-Wine-Programs-Ventrilo-Ventrilo)
Open Set-Up
Check Mark  "Use Direct Sound" for Output device AND set the output device as "dmix:0"
Make sure for the Input Device it is NOT check marked for Direct sound and "Default Wave Mapper" is selected.
I have "none" selected for "Hardware Input Mixer"
My ventrilo server runs on the Speex coded but I have tested and GSM 6.10 works fine as well.
TEST YOUR SET UP!
if it works than congratulations and I hope I have helped
IF NOT
than some troublshooting options are..
check to see if your microphone is working through Sound Recorder (Applications-Sound and Video) if it is NOT then ensure that your microphone is ON, and plugged in correctly (i know this goes w/out saying but you never know)
if it is plugged in and on check to see if it is enabled.
Open Volume Control (double click your volume icon on your taskbar)
ensure the microphone is enabled there should be a speaker icon underneath the volume adjustment if there is a red X than it is not and click it to enable and aswell check to make sure the volume is turned up.
If you do not see a microphone option check to see if it is hidden under the volume control (edit-prefrences) and make sure it is ticked.
Next Under volume control pannel navigate to the "Recording" tab and make sure the volume is enabled and up (see the enable step for microphone above)
Thirdly go to the switches tab next to the recording tab and make sure the microphone is selected 
if all this is done and no success please post and i'll try to help :popcorn:

edit: for gsm6.10 codec users it might behoove you to check out this website helping out w/ some codecs...if you are good friends w/ the vent admin. see if he/she can change to speex i've found/read alot more success w/ the speex codec. anywho; [http://appdb.winehq.org/appview.php?iVersionId=3936]("http://appdb.winehq.org/appview.php?iVersionId=3936")

---

### Post by loudog23 on 2009-03-15
yeesterday, I was able to make it work.

For some reason, this morning, it's not orking anymore.
My speaker stay red in VentriloClient
If i use Monitor, nothing is captured
I followed your how-to and installed the missing package, we will see the come up.

I would like to Add to the Vent/Ubuntu knowledge by adding this:
I use Ventrilo in AnarchyOnline using PlayOnLinux

I installed PlayonLinux
I followed this How-to to install Vent : [http://ubuntuforums.org/showthread.php?t=923017&highlight=Ventrilo](http://ubuntuforums.org/showthread.php?t=923017&highlight=Ventrilo)
The difference bieng that i changed the directories to .PlayOnLinux/wineprefix
/Ventrilo/*
Set up POL to run Vent with Wine 1.1.14 (as GSM codec don't work with 1.1.15+)

Yesterday, it was working great until i installed AO and done some tweaking. My guess is that i screw up something somewhere because now it dosen't work.

Ill come back wth the outcome

---

