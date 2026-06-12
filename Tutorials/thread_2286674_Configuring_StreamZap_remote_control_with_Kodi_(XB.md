---
title: "Configuring StreamZap remote control with Kodi (XBMC) in Ubuntu 14.04"
date: 2015-07-13
forum: Tutorials
---

### Post by dudous on 2015-07-13
I was successfully using my Streamzap remote control with XBMC 11, but since it was a little old, his add-ons stopped working one by one, and i was forced to update to XBMC version 14.2 (now known as Kodi). 

I don´t know exactly what has changed, but my usual procedure to make streamzap work wasn´t functioning anymore. 
The problem was that if i has installed Kodi and tried to use streamzap out of the box (without lirc), only the arrow buttons were working inside Kodi and after lirc's  installation and configuration through my old method ,no buttons were responding anymore!

After many hours trying, i finally got make it working again as expected! :guitar:
Below follows the steps that worked for me. I hope it can be useful to someone.

 

==================================
Kodi installation - Mint 17.2/Ubuntu 14.04
=================================

sudo add-apt-repository ppa:team-xbmc/ppa
sudo apt-get update
sudo apt-get install kodi kodi-audioencoder-*

Obs: Change the first command words to "ppa:team-xbmc/unstable" or "ppa:team-xbmc/xbmc-nightly" if you wish to try the latest versions.





==========================================
StreamZap Remote control installation
==========================================


1)  Plug Streamzap receptor in the USB port


2)  Install LIRC from Ubuntu repositories:


sudo apt-get install lirc


3)  Configure Streamzap if necessary with :

sudo dpkg-reconfigure lirc


4)  Choose "Streamzap PC Remote"  as your receiving device and "None" as your transmitting device.


5)  Check if the files  /etc/lirc/hardware.conf and /etc/lirc/lircd.conf were created.



6)  Restart LIRC service:

sudo /etc/init.d/lirc restart


7) Test if the remote control buttons are being readed with :


irw




=============================================
Setting Kodi to use StreamZap correctly   
=============================================

1)  Copy the attached file Lircmap.xml to the path:


~/.kodi/userdata


2)  Copy the attached file remote.xml to the path:


~/.kodi/userdata/keymaps


obs: remote.xml is just the original file inside your "/usr/share/kodi/system/keymaps/" path, so you can also get it from there. 
You can change the remote control mappings inside Kodi with it with some knowledge. 
Here are some links about this:

[http://nucblog.net/2014/01/mapping-the-buttons-on-the-remote-control/](http://nucblog.net/2014/01/mapping-the-buttons-on-the-remote-control/)
[https://github.com/graysky2/streamzap](https://github.com/graysky2/streamzap)


=========================================================
Changing StreamZap power button behavior to ShutDown computer instead of just Quit the application
=========================================================

Browse through this path in the GUI and change the Shutdown function from Quit to Shutdown:

Settings > System > Power saving > Shutdown function > Shutdown 



============================================
If remote control buttons are being readed more than one time 
===========================================

Create a file named as bellow 

sudo gedit /usr/share/X11/xorg.conf.d/90-streamzap.conf



Paste the following lines and save it:

Section "InputClass"
  Identifier "Ignore Streamzap IR"
  MatchProduct "Streamzap"
  MatchIsKeyboard "true"
  Option "Ignore" "true"
EndSection

---

