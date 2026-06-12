---
title: "What is this file?"
date: 2012-01-11
forum: Security
---

### Post by themanfromdelmonte on 2012-01-11
I found it in the root home folder while using nautilus. Is it anything to worry about it was called accessibility.conf

```
<!DOCTYPE busconfig PUBLIC "-//freedesktop//DTD D-Bus Bus Configuration 1.0//EN" "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>

  <type>accessibility</type>

  <standard_session_servicedirs/>

  <auth>EXTERNAL</auth>

  <listen>unix:tmpdir=/tmp</listen>

  <policy context="default">
    <!-- Allow root to connect -->
    <allow user="root"/>
    <!-- Allow everything to be sent -->
    <allow send_destination="*" eavesdrop="true"/>
    <!-- Allow everything to be received -->
    <allow eavesdrop="true"/>
    <!-- Allow anyone to own anything -->
    <allow own="*"/>
  </policy>

  <limit name="max_incoming_bytes">1000000000</limit>
  <limit name="max_outgoing_bytes">1000000000</limit>
  <limit name="max_message_size">1000000000</limit>
  <limit name="service_start_timeout">120000</limit>  
  <limit name="auth_timeout">240000</limit>
  <limit name="max_completed_connections">100000</limit>  
  <limit name="max_incomplete_connections">10000</limit>
  <limit name="max_connections_per_user">100000</limit>
  <limit name="max_pending_service_starts">10000</limit>
  <limit name="max_names_per_connection">50000</limit>
  <limit name="max_match_rules_per_connection">50000</limit>
  <limit name="max_replies_per_connection">50000</limit>
  <limit name="reply_timeout">300000</limit>
</busconfig>
```

---

### Post by MadsRC on 2012-01-11
From manpages:
[http://manpages.ubuntu.com/manpages/oneiric/man5/access.conf.5.html](http://manpages.ubuntu.com/manpages/oneiric/man5/access.conf.5.html)

Did you find it in /etc/security/access.conf ?

---

### Post by satanselbow on 2012-01-11
May also be found at /etc/at-spi2

When you say "root home folder" - do you mean "in a folder under my user directories" (ie in your **home** folder "**/home/<username>**") or in the root filesystem (ie under **root** or "**/**")

They are 2 separate locations the former being your "home folder" the later being your "root folder" ;)

---

### Post by satanselbow on 2012-01-11
> **MadsRC said:**
> From manpages:
[http://manpages.ubuntu.com/manpages/oneiric/man5/access.conf.5.html](http://manpages.ubuntu.com/manpages/oneiric/man5/access.conf.5.html)

Did you find it in /etc/security/access.conf ?

The OP found "accessibility.conf" it is part of the dbus system and is expected to be found at the location stated above ;)

It is nothing to be concerned about and is part of the accessibility provision by the dbus daemon.

---

### Post by themanfromdelmonte on 2012-01-11
No I found it in a file called at-spi2 in etc. The only file in the folder.

Could you also tell me why this line is always in my sys.log

```
an 11 05:35:45 Stasi NetworkManager[951]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
```

I have not set up any VPN??

---

### Post by satanselbow on 2012-01-11
It is part of the expect startup behaviour of network manager

---

### Post by themanfromdelmonte on 2012-01-11
Thanks one last question what is registry.i686.bin all about. Ill post a page or two of the fifty. Thanks for all your help. Complete file here [http://ubuntuone.com/7DByYGpHLD22zRxhbMMWRi](http://ubuntuone.com/7DByYGpHLD22zRxhbMMWRi)

```
                                   0.10.30.1###########################################################&#65533;&#65533;##&#65533;&#65533;TN########autodetect#Plugin contains auto-detection plugins for video/audio in- and outputs#/usr/lib/gstreamer-0.10/libgstautodetect.so#0.10.30#LGPL#gst-plugins-good#GStreamer Good Plugins (Ubuntu)#https://launchpad.net/distros/ubuntu/+source/gst-plugins-good0.10#2011-06-15##GstElementFactory#autovideosink####################Auto video sink#Sink/Video#Wrapper video sink for automatically detected video sink#Jan Schmidt <thaytan@noraisin.net>#########sink#ANY#GstChildProxy#GstElementFactory#autovideosrc####################Auto video source#Source/Video#Wrapper video source for automatically detected video source#Jan Schmidt <thaytan@noraisin.net>, Stefan Kost <ensonic@users.sf.net>#########src#ANY#GstChildProxy#GstElementFactory#autoaudiosink####################Auto audio sink#Sink/Audio#Wrapper audio sink for automatically detected audio sink#Jan Schmidt <thaytan@noraisin.net>#########sink#ANY#GstChildProxy#GstElementFactory#autoaudiosrc####################Auto audio source#Source/Audio#Wrapper audio source for automatically detected audio source#Jan Schmidt <thaytan@noraisin.net>, Stefan Kost <ensonic@users.sf.net>#########src#ANY#GstChildProxy###&#65533;&#65533;##&#65533;&#65533;TN########liveadder#Adds multiple live discontinuous streams#/usr/lib/gstreamer-0.10/libgstliveadder.so#0.10.30#LGPL#gst-plugins-good#GStreamer Good Plugins (Ubuntu)#https://launchpad.net/distros/ubuntu/+source/gst-plugins-good0.10#2011-06-15##GstElementFactory#liveadder####################Live Adder element#Generic/Audio#Mixes live/discontinuous audio streams#Olivier Crete <olivier.crete@collabora.co.uk>##########src#audio/x-raw-int, rate=(int)[ 1, 2147483647 ], channels=(int)[ 1, 2147483647 ], endianness=(int){ 1234, 4321 }, width=(int){ 8, 16, 24, 32 }, depth=(int)[ 1, 32 ], signed=(boolean){ true, false }; audio/x-raw-float, rate=(int)[ 1, 2147483647 ], channels=(int)[ 1, 2147483647 ], endianness=(int){ 1234, 4321 }, width=(int){ 32, 64 }##########sink%d#audio/x-raw-int, rate=(int)[ 1, 2147483647 ], channels=(int)[ 1, 2147483647 ], endianness=(int){ 1234, 4321 }, width=(int){ 8, 16, 24, 32 }, depth=(int)[ 1, 32 ], signed=(boolean){ true, false }; audio/x-raw-float, rate=(int)[ 1, 2147483647 ], channels=(int)[ 1, 2147483647 ], endianness=(int){ 1234, 4321 }, width=(int){ 32, 64 }###|&#65533;##&#65533;&#65533;TN#### ###effectv#effect plugins from the effectv project#/usr/lib/gstreamer-0.10/libgsteffectv.so#0.10.30#LGPL#gst-plugins-good#GStreamer Good Plugins (Ubuntu)#https://launchpad.net/distros/ubuntu/+source/gst-plugins-good0.10#2011-06-15##GstElementFactory#edgetv####################EdgeTV effect#Filter/Effect/Video#Apply edge detect on video#Wim Taymans <wim.taymans@chello.be>###########sink#video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)65280, green_mask=(int)16711680, blue_mask=(int)-16777216, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]; video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)-16777216, green_mask=(int)16711680, blue_mask=(int)65280, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]#########src#video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)65280, green_mask=(int)16711680, blue_mask=(int)-16777216, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]; video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)-16777216, green_mask=(int)16711680, blue_mask=(int)65280, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]#GstElementFactory#agingtv#####################AgingTV effect#Filter/Effect/Video#AgingTV adds age to video input using scratches and dust#Sam Lantinga <slouken@devolution.com>##########sink#video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)65280, green_mask=(int)16711680, blue_mask=(int)-16777216, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]; video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)-16777216, green_mask=(int)16711680, blue_mask=(int)65280, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]#########src#video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)65280, green_mask=(int)16711680, blue_mask=(int)-16777216, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]; video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)-16777216, green_mask=(int)16711680, blue_mask=(int)65280, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]#GstElementFactory#dicetv##################DiceTV effect#Filter/Effect/Video#'Dices' the screen up into many small squares#Wim Taymans <wim.taymans@chello.be>############sink#video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)-16777216, green_mask=(int)16711680, blue_mask=(int)65280, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]; video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)16711680, green_mask=(int)65280, blue_mask=(int)255, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]; video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)65280, green_mask=(int)16711680, blue_mask=(int)-16777216, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]; video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)255, green_mask=(int)65280, blue_mask=(int)16711680, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]#########src#video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)-16777216, green_mask=(int)16711680, blue_mask=(int)65280, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]; video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)16711680, green_mask=(int)65280, blue_mask=(int)255, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]; video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)65280, green_mask=(int)16711680, blue_mask=(int)-16777216, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]; video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)255, green_mask=(int)65280, blue_mask=(int)16711680, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]#GstElementFactory#warptv##################WarpTV effect#Filter/Effect/Video#WarpTV does realtime goo'ing of the video input#Sam Lantinga <slouken@devolution.com>############sink#video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)-16777216, green_mask=(int)16711680, blue_mask=(int)65280, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]; video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)16711680, green_mask=(int)65280, blue_mask=(int)255, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]; video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)65280, green_mask=(int)16711680, blue_mask=(int)-16777216, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]; video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)255, green_mask=(int)65280, blue_mask=(int)16711680, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]#########src#video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)-16777216, green_mask=(int)16711680, blue_mask=(int)65280, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]; video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)16711680, green_mask=(int)65280, blue_mask=(int)255, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]; video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)65280, green_mask=(int)16711680, blue_mask=(int)-16777216, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]; video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)255, green_mask=(int)65280, blue_mask=(int)16711680, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]#GstElementFactory#shagadelictv####################ShagadelicTV#Filter/Effect/Video#Oh behave, ShagedelicTV makes images shagadelic!#Wim Taymans <wim.taymans@chello.be>##########sink#video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)65280, green_mask=(int)16711680, blue_mask=(int)-16777216, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]#########src#video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)65280, green_mask=(int)16711680, blue_mask=(int)-16777216, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]#GstElementFactory#vertigotv###################VertigoTV effect#Filter/Effect/Video#A loopback alpha blending effector with rotating and scaling#Wim Taymans <wim.taymans@chello.be>##########sink#video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)-16777216, green_mask=(int)16711680, blue_mask=(int)65280, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]; video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)65280, green_mask=(int)16711680, blue_mask=(int)-16777216, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]#########src#video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)-16777216, green_mask=(int)16711680, blue_mask=(int)65280, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]; video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)65280, green_mask=(int)16711680, blue_mask=(int)-16777216, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]#GstElementFactory#revtv###################RevTV effect#Filter/Effect/Video#A video waveform monitor for each line of video processed#Wim Taymans <wim.taymans@chello.be>#########sink#video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)65280, green_mask=(int)16711680, blue_mask=(int)-16777216, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]; video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)-16777216, green_mask=(int)16711680, blue_mask=(int)65280, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]#########src#video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)65280, green_mask=(int)16711680, blue_mask=(int)-16777216, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]; video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)-16777216, green_mask=(int)16711680, blue_mask=(int)65280, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]#GstElementFactory#quarktv#####################QuarkTV effect#Filter/Effect/Video#Motion dissolver#FUKUCHI,  Kentarou <fukuchi@users.sourceforge.net>##########sink#video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)16711680, green_mask=(int)65280, blue_mask=(int)255, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]; video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)255, green_mask=(int)65280, blue_mask=(int)16711680, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]; video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)65280, green_mask=(int)16711680, blue_mask=(int)-16777216, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1,  
```

---

