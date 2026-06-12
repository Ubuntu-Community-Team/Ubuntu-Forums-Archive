---
title: "Sound problems on startup"
date: 2006-08-29
forum: System76 Support
---

### Post by kevinlyfellow on 2006-08-29
I recently purchased a gazelle performance, and I'm very happy with it.  One annoyance I have though is that when I boot it up, occasionally the computer the sound does not work.  The speaker by the date has an x over it and when I click it, it says something along the lines of not having a sound card.  This may be the result of me installing libsdl1.2debian-all, which I did to fix sound delays in my favorite games, but I'm not sure.  Any helpful advice?

One other thing is that it hangs when loading the hardware drivers during bootup occasionally.  This didn't start happening until I ran the "System76 driver installer", in which the next bootup, it hanged and then on occasional boots afterward.

---

### Post by KingBahamut on 2006-08-29
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

Try that.

---

### Post by crichell on 2006-08-29
We installed the package you mentioned and re-ran the System76 Driver Installer and haven't noticed a sound issue.  Is there any pattern to the occasional sound problem.  Possibly a different user account that doesn't have permission to the sound device?

When the speaker has a red X through it, in my experience, it's due to permissions or the driver not being installed.

---

### Post by kevinlyfellow on 2006-08-30
Well, I haven't noticed a pattern yet.  When I brought my computer home from work I rebooted to see if would have any problems.  It hanged on loading hardware drivers, so I shut it off and tried again.  When it rebooted I had the sound problem, though I don't think that this is typical to have the problem after the hang.  I always log in with the same user account, so thats not the issue.  I then tried a few things when the sound was not working:

```

kevinly@ubuntu:~$ aplay -l
aplay: device_list:221: no soundcards found...

kevinly@ubuntu:~$ lspci -v
...
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 1297
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at feb3c000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>
...

```

When the sound is working:

```

kevinly@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


kevinly@ubuntu:~$ lspci -v
...
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 1297
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at feb3c000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>
...

```

the only difference in the lspci -v is the IRQ

---

### Post by crichell on 2006-08-30
When you say hang on Loading Hardware Drivers is it hanging and then it continues to boot or do you have to do a hard shutdown?

---

### Post by kevinlyfellow on 2006-08-30
hard shutdown

---

### Post by crichell on 2006-08-30
A new System76 Driver is coming out in a couple of days (going through final testing).  It includes updates to the Gazelle Performance sound driver.  Lets hang on for it and see if you have trouble after the update.

---

### Post by kevinlyfellow on 2006-08-30
Excellent, I'll let you know how it goes.  And thanks for you help so far

---

### Post by kevinlyfellow on 2006-09-07
Unfortunatly I'm still having the same problem after updating on Tuesday

---

### Post by crichell on 2006-09-07
Lets re-run the System76 Driver installation (System > Administration > System76 Driver Installer) and reboot - make sure you're connected to the internet when running the driver installer.

If you've done this already we'll have to start hacking elsewhere.  We installed the package you mentioned but it didn't seem to cause any adverse effects.

I don't think many games are up to speed on Alsa and require OSS - maybe something was inadvertantly modified there.

run:```
gstreamer-properties
```

Set the output to ALSA.  You can often times set a game to use OSS on an individual bases via it's command.

---

### Post by kevinlyfellow on 2006-09-08
It didn't seem to work.  The games I use (frozen-bubble, blobwars, and planet-penguin) all are working with alsa.

Unfortunatly I'd like to say that there is a pattern, but alas, I can seem to find one.  

I have mucked around the gstreamer packages to get mpegs to work, could that be causing some problems?

---

### Post by crichell on 2006-09-11
Lets try a couple of things.

Memory Test - When you see the GRUB menu at start-up press escape.  Choose Memory Test.  They usually take a little while but this will tell us whether we're having a memory issue.

Give our How To a shot to install the appropriate packages for multimedia.  It's located here:

[http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats)

Use the direction under Ubuntu 6.06 (Dapper) - it's just a matter of cutting and pasting six lines into the terminal.

---

### Post by kevinlyfellow on 2006-09-11
I've let memtest run through 4 passes and I've run it through 1 pass before, and there's been no errors.  As far as gstreamer, I looked through and got rid of the programs that I really didn't need, and everything I have belongs to that howto, so I'm assuming that everything I have for gstreamer is typical.

---

### Post by kevinlyfellow on 2006-09-11
Sorry about the double post, I can't seem to find the edit button.  Seeming how this problem only happens every so often, I think I'll let that run over night

---

### Post by crichell on 2006-09-11
Thanks for letting it run - sporadic problems are always the toughest and I'm no gstreamer expert.  I always have to look for patterns to try to determine a problem/solution.  Data always helps to:

Run: ```
sudo aptitude search gstreamer > /tmp/gstreamer.txt
```

Open up /tmp/gstreamer.txt and post the contents here

---

### Post by kevinlyfellow on 2006-09-12
The Memtest didn't find any errors.  Here's the info you asked for.

```

p   gstreamer-editor                - GStreamer Pipeline Editor and other GUI to
p   gstreamer-tools                 - Tools for use with GStreamer              
i   gstreamer0.10-alsa              - GStreamer plugin for ALSA                 
v   gstreamer0.10-audiosink         -                                           
v   gstreamer0.10-colorspace        -                                           
p   gstreamer0.10-doc               - GStreamer core documentation and manuals  
i   gstreamer0.10-esd               - GStreamer plugin for ESD                  
i   gstreamer0.10-ffmpeg            - FFmpeg plugin for GStreamer               
p   gstreamer0.10-fluendo-mp3       - Fluendo mp3 decoder GStreamer plugin      
p   gstreamer0.10-fluendo-mpegdemux - Fluendo GStreamer plugin for MPEG2 demuxin
p   gstreamer0.10-gl                - GStreamer plugin for OpenGL output        
i   gstreamer0.10-gnomevfs          - GStreamer plugin for GnomeVFS             
p   gstreamer0.10-gnonlin           - non-linear editing module for GStreamer   
v   gstreamer0.10-lame              -                                           
p   gstreamer0.10-pitfdll           - GStreamer plugin for using MS Windows bina
i   gstreamer0.10-plugins-bad       - GStreamer plugins from the "bad" set      
p   gstreamer0.10-plugins-bad-doc   - GStreamer documentation for plugins from t
p   gstreamer0.10-plugins-bad-multi - GStreamer plugins from the "bad" set (Mult
i   gstreamer0.10-plugins-base      - GStreamer plugins from the "base" set     
i   gstreamer0.10-plugins-base-apps - GStreamer helper programs from the "base" 
i   gstreamer0.10-plugins-base-dbg  - GStreamer plugins from the "base" set     
p   gstreamer0.10-plugins-base-doc  - GStreamer documentation for plugins from t
i   gstreamer0.10-plugins-good      - GStreamer plugins from the "good" set     
p   gstreamer0.10-plugins-good-dbg  - GStreamer plugins from the "good" set     
p   gstreamer0.10-plugins-good-doc  - GStreamer documentation for plugins from t
i   gstreamer0.10-plugins-ugly      - GStreamer plugins from the "ugly" set     
p   gstreamer0.10-plugins-ugly-dbg  - GStreamer plugins from the "ugly" set     
p   gstreamer0.10-plugins-ugly-doc  - GStreamer documentation for plugins from t
p   gstreamer0.10-plugins-ugly-mult - GStreamer plugins from the "ugly" set (Mul
p   gstreamer0.10-sdl               - GStreamer plugin for SDL output           
i   gstreamer0.10-tools             - Tools for use with GStreamer              
v   gstreamer0.10-videosink         -                                           
i   gstreamer0.10-x                 - GStreamer plugins for X11 and Pango       
p   gstreamer0.8-a52dec             - ATSC A/52 audio decoder plugin for GStream
p   gstreamer0.8-aa                 - AA-lib plugin for GStreamer               
p   gstreamer0.8-alsa               - ALSA plugin for GStreamer                 
p   gstreamer0.8-artsd              - aRtsd plugin for GStreamer                
p   gstreamer0.8-audiofile          - AudioFile plugin for GStreamer            
v   gstreamer0.8-audiosink          -                                           
p   gstreamer0.8-caca               - Colour AsCii Art library plugin for GStrea
p   gstreamer0.8-cdio               - low-level CD-ROM reading and control plugi
p   gstreamer0.8-cdparanoia         - cdparanoia plugin for GStreamer           
v   gstreamer0.8-colorspace         -                                           
p   gstreamer0.8-dirac              - Dirac decoder plugin for GStreamer        
p   gstreamer0.8-doc                - GStreamer documentation                   
p   gstreamer0.8-dv                 - DV plugin for GStreamer                   
p   gstreamer0.8-dvd                - DVD plugin for GStreamer                  
p   gstreamer0.8-esd                - Enlightened Sound Daemon plugin for GStrea
p   gstreamer0.8-faac               - AAC encodingplugin for GStreamer          
p   gstreamer0.8-faad               - AAC decoding plugin for GStreamer         
p   gstreamer0.8-festival           - Festival speech synthesis plugin for GStre
p   gstreamer0.8-ffmpeg             - FFmpeg plugin for GStreamer               
p   gstreamer0.8-flac               - FLAC plugin for GStreamer                 
p   gstreamer0.8-gnomevfs           - Gnome VFS plugin for GStreamer            
p   gstreamer0.8-gsm                - GSM plugin for GStreamer                  
p   gstreamer0.8-gtk                - Gtk/Gdk plugin for GStreamer              
p   gstreamer0.8-hermes             - colorspace conversion plugin for GStreamer
p   gstreamer0.8-jpeg               - JPEG plugin for GStreamer                 
p   gstreamer0.8-lame               - LAME encoder plugin for GStreamer         
p   gstreamer0.8-mad                - MAD MPEG audio decoder plugin for GStreame
p   gstreamer0.8-mikmod             - MikMod decoder plugin for GStreamer       
p   gstreamer0.8-misc               - Collection of various GStreamer plugins   
p   gstreamer0.8-mms                - mms plugin for GStreamer                  
p   gstreamer0.8-mpeg2dec           - MPEG1 and MPEG2 video decoder plugin for G
p   gstreamer0.8-musepack           - Musepack (MPC) audio decoder plugin for GS
p   gstreamer0.8-oss                - OSS plugin for GStreamer                  
p   gstreamer0.8-pitfdll            - DLL/QTX loader plugin for GStreamer       
p   gstreamer0.8-plugin-apps        - Simple GStreamer applications             
p   gstreamer0.8-plugins            - All GStreamer plugins                     
p   gstreamer0.8-plugins-multiverse - All Multiverse GStreamer plugins          
p   gstreamer0.8-sdl                - SDL videosink plugin for GStreamer        
p   gstreamer0.8-sid                - C64 SID decoder plugin for GStreamer      
p   gstreamer0.8-speex              - Speex plugin for GStreamer                
p   gstreamer0.8-swfdec             - SWF (Macromedia Flash) decoder plugin for 
p   gstreamer0.8-theora             - Theora plugin for GStreamer               
p   gstreamer0.8-tools              - Tools for use with GStreamer              
v   gstreamer0.8-videosink          -                                           
p   gstreamer0.8-vorbis             - Vorbis plugin for GStreamer               
v   gstreamer0.8-wavpack            -                                           
p   gstreamer0.8-x                  - X videosink plugin for GStreamer          
p   gstreamer0.8-xvid               - XVID encoder plugin for GStreamer         
p   libgstreamer-gconf0.8-0         - GConf support for GStreamer               
p   libgstreamer-gconf0.8-dev       - Development files for GConf support for GS
i   libgstreamer-plugins-base0.10-0 - GStreamer libraries from the "base" set   
p   libgstreamer-plugins-base0.10-d - GStreamer development files for libraries 
p   libgstreamer-plugins0.8-0       - Various GStreamer libraries and library pl
p   libgstreamer-plugins0.8-dev     - Development files for various GStreamer li
i   libgstreamer0.10-0              - Core GStreamer libraries and elements     
p   libgstreamer0.10-0-dbg          - Core GStreamer libraries and elements     
p   libgstreamer0.10-dev            - GStreamer core development files          
p   libgstreamer0.8-0               - Core GStreamer libraries, plugins, and uti
p   libgstreamer0.8-dev             - GStreamer development libraries and header
p   libgstreamer0.8-ruby            - GStreamer 0.8 bindings for the Ruby langua
i   totem-gstreamer                 - A simple media player for the Gnome deskto
p   totem-gstreamer-firefox-plugin  - Totem Firefox Plugin - gstreamer version 

```

---

### Post by kevinlyfellow on 2006-09-12
I agree with you that sporadic problems are terrible, and that without a pattern, it is difficult to diagnose.  My biggest concern now is if it is a hardware problem or a software problem.  Would it be wise at this point in time to accept that the problem is unknown, and reinstall the os, so that I can say for sure if it was a bad setting, or something wrong with the laptop/initial configuration?  I have no reservation in doing this, except for the fact that if it is fixed I'll never know what the problem was.

If I do reinstall the os from your cd, do I have any options to configure the installation?

---

### Post by crichell on 2006-09-12
If you sent the laptop in to us we would probably end up restoring it too.  The restore DVD takes the system back to the exact state when you first received it.  After the restore you run through the first time setup (language, location, name/username etc.)

There are no options during the restore.

BTW - The only difference I see between your installed gstreamer packages and mine is: gstreamer0.10-gl  - GStreamer plugin for OpenGL output

I don't know if it's related (i doubt it) but if your thinking of restoring maybe try installing it first.

---

### Post by kevinlyfellow on 2006-09-22
I tried to restore last night, but you guys made an embarrasing mistake on your restore dvd... you burned the iso file onto a data dvd, instead of actually writing the image.  How can I get a new restore dvd?

---

### Post by crichell on 2006-09-22
oops.  Shoot us an email to support (at) system76.com - I'll overnight a new restore DVD.

---

### Post by kevinlyfellow on 2006-09-27
Ok, I reinstalled, and I'm feeling fairly confident that my sound is working just fine.  But now I'm facing two less problems that I was not facing before.

First, my touchpad is having difficulties determining when I'm scrolling and when I'm just trying to use it.  For instance: when scrolling up, it will sometimes just move the mouse up or when trying to move my mouse from side to side it takes it as a horizontal scroll.

Second is the NetworkManager Applet.  It doesn't know when there is a wireless network, although the networking works fine.  I installed the os off of a network, maybe thats the problem... but I tried to reinstall the NetworkManager programs and it didn't do anything.

---

### Post by EriK76 on 2006-09-27
Were glad to hear sound is working.  

We're looking into the touchpad issue but for the Network Manager Applet:

sudo gedit /etc/network/interfaces 

comment out everything but:

auto lo
iface lo inet loopback

Reboot and your Network Mangager Applet should see your wirless networks.

---

### Post by EriK76 on 2006-09-27
kevinlyfellow,

For your synaptics issue can you confirm that the line:

Option         "SHMConfig" "1"

is in your /etc/X11/xorg.conf file in the Section "InputDevice" for Identifier  "Synaptics Touchpad"

---

### Post by kevinlyfellow on 2006-09-28
Success with nm-applet!!!

I can confirm that Option "SHMConfig" "1" is in the appropiate place in xorg.conf

---

### Post by kevinlyfellow on 2006-09-28
I've changed by touchpad configuration to circular but only to use the right side.  This seems to solve the problem, unless you anyone can think of a way to fix it the proper way

---

### Post by kevinlyfellow on 2006-10-02
I got the touchpad problem fixed.  I had to configure qsynaptics by hand for whatever reason.  Thanks for all your help!

---

