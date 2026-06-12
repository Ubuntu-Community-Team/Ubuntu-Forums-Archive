---
title: "Problems with Gazelle Value and multimedia"
date: 2006-08-20
forum: System76 Support
---

### Post by frainbart on 2006-08-20
I was having some other restarting and shutdown problems with my Gazelle value so I decided to start from scratch again (other wonkiness including freezing on restarts, freezing on shutdown, not recognizing wifi on restart, etc., I think stemming from my fooling around with sleep and hibernating). I just did a system retore and did all the automatix updates with all the latest multimedia codecs for mplayer. I did all the automatic ubuntu updates, and now I cannot play any movies in totem, mplayer or gxine. I get a blank screen when the file is opened (DVD or multimedia file) which requires a hard reboot. I had all the mutlimedia working at one point before the system restore, including the fun DemocracyTV. It is frustrating that I have lost all my video playing capability (youtube videos still work). I have been reinstalling all the multimedia codecs over again without any sucess. I am pretty sure that I have all the latest updates as well... I was using mplayer for the most part before (totem always gave me problems), but I can't even play the videos in the Ubuntu examples folder.

---

### Post by crichell on 2006-08-20
I'm sure what automatix does anymore - I've stayed away from it in Dapper.  We have a multimedia codecs How To [here.]("http://knowledge76.com/index.php/Installing_Restricted_Formats")

Cut and paste the six lines from the How To and you should be up and running; although, automatix may cause trouble.  If the How To doesn't work you may need to remove what automatix has done or just run a restore start from there.

Let me know how it goes.

---

### Post by frainbart on 2006-08-20
Yeah, already did the how-to a few times. I'll do a restore and try not using automatix. I'll let you know how it goes later tonight.

---

### Post by frainbart on 2006-08-21
I did a system restore and then installed all the codecs from the how-to page. I still can't play the sample movie or DVD via mplayer or totem. Totem freezes and the screen goes blank. mplayer reports an error loading codec with a blue screen, and the the computer freezes. Both require a hard reboot. Sound seems to be working fine. I tried playing movies before and after the automatic ubuntu updates, with the same result. Automatix was not installed.

---

### Post by crichell on 2006-08-21
Well here's the good news - I've finally reproduced this.  Will be trouble shooting and get back to you soon.

---

### Post by crichell on 2006-08-21
I've got a quick fix for this now.

Use EasyUbuntu to install multimedia codecs.
Easy Ubuntu is located here: [http://easyubuntu.freecontrib.org/get.html](http://easyubuntu.freecontrib.org/get.html)

Tick the checkboxes on the multimedia tab (I had some trouble with the other tabs so I skipped them for now)

After the package installation is completed you still won't be able to play video via Totem.  Run the following:

```
sudo apt-get install gxine
```

Use Gxine for playing video.

I'll check out what easyubuntu is doing differently and also work on getting Totem to work properly (I've always had some trouble with totem-gstreamer though)

---

### Post by frainbart on 2006-08-21
Did you do a system restore again and ignore the System76 how-to and then use only Easyunbuntu? Just installing the multimedia codecs from Easyubuntu didn't work for me. Just running gxine freezes my computer when it starts up. I will try to do another system restore again.

---

### Post by crichell on 2006-08-21
I'm on a fresh install (restore).  Ran EasyUbuntu w/ all of the checkboxes on the Multimedia tab ticked.  Install gxine and I could play DVD's with gxine.  Totem didn't play the DVD but it did not freeze the system either.

---

### Post by crichell on 2006-08-21
The difference between EasyUbuntu and our How To is the gstreamer version.  Looks like they're using gstreamer0.8 where as we're using gstreamer0.10.

What makes this interesting is that this only occurs on the Gazelle Value w/ Celeron Processor - to my knowledge so far.  Our How To using gstreamer0.10 works on all other machines and the Gazelle Value w/ Pentium M.

I'm not sure what's up with that.  If anyone knows please fill us in.

---

### Post by frainbart on 2006-08-21
That's weird. I have the Pentium M 740, 1.73 MHz, in my Gazelle Value, not the Celeron...

---

### Post by crichell on 2006-08-21
> That's weird. I have the Pentium M 

I stand corrected.  When I ran our How To on a Pentium it worked and on a Celeron had trouble.  I'm not sure what's causing the trouble.  I know that gstreamer0.10 was fresh of the press for Dapper so maybe it has some bugs.

---

### Post by frainbart on 2006-08-21
No luck. Just did a clean factory install and the Easyubuntu. No dice. Starting gxine freezes the computer as well as totem. :confused:

---

### Post by crichell on 2006-08-21
lets check what plugins are installed - run:
```
sudo aptitude search gstreamer > /tmp/gstreamer.txt 
```
Open up /tmp/gstreamer.txt and post the contents here

---

### Post by frainbart on 2006-08-21
Here you go:

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
i   gstreamer0.10-pitfdll           - GStreamer plugin for using MS Windows bina
i   gstreamer0.10-plugins-bad       - GStreamer plugins from the "bad" set      
p   gstreamer0.10-plugins-bad-doc   - GStreamer documentation for plugins from t
i   gstreamer0.10-plugins-bad-multi - GStreamer plugins from the "bad" set (Mult
i   gstreamer0.10-plugins-base      - GStreamer plugins from the "base" set     
i   gstreamer0.10-plugins-base-apps - GStreamer helper programs from the "base" 
p   gstreamer0.10-plugins-base-dbg  - GStreamer plugins from the "base" set     
p   gstreamer0.10-plugins-base-doc  - GStreamer documentation for plugins from t
i   gstreamer0.10-plugins-good      - GStreamer plugins from the "good" set     
p   gstreamer0.10-plugins-good-dbg  - GStreamer plugins from the "good" set     
p   gstreamer0.10-plugins-good-doc  - GStreamer documentation for plugins from t
i   gstreamer0.10-plugins-ugly      - GStreamer plugins from the "ugly" set     
p   gstreamer0.10-plugins-ugly-dbg  - GStreamer plugins from the "ugly" set     
p   gstreamer0.10-plugins-ugly-doc  - GStreamer documentation for plugins from t
i   gstreamer0.10-plugins-ugly-mult - GStreamer plugins from the "ugly" set (Mul
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

### Post by crichell on 2006-08-21
here is my copy from a "multimedia working" gazelle value

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
i   gstreamer0.10-pitfdll           - GStreamer plugin for using MS Windows bina
i   gstreamer0.10-plugins-bad       - GStreamer plugins from the "bad" set      
p   gstreamer0.10-plugins-bad-doc   - GStreamer documentation for plugins from t
i   gstreamer0.10-plugins-bad-multi - GStreamer plugins from the "bad" set (Mult
i   gstreamer0.10-plugins-base      - GStreamer plugins from the "base" set     
i   gstreamer0.10-plugins-base-apps - GStreamer helper programs from the "base" 
p   gstreamer0.10-plugins-base-dbg  - GStreamer plugins from the "base" set     
p   gstreamer0.10-plugins-base-doc  - GStreamer documentation for plugins from t
i   gstreamer0.10-plugins-good      - GStreamer plugins from the "good" set     
p   gstreamer0.10-plugins-good-dbg  - GStreamer plugins from the "good" set     
p   gstreamer0.10-plugins-good-doc  - GStreamer documentation for plugins from t
i   gstreamer0.10-plugins-ugly      - GStreamer plugins from the "ugly" set     
p   gstreamer0.10-plugins-ugly-dbg  - GStreamer plugins from the "ugly" set     
p   gstreamer0.10-plugins-ugly-doc  - GStreamer documentation for plugins from t
i   gstreamer0.10-plugins-ugly-mult - GStreamer plugins from the "ugly" set (Mul
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
c   totem-gstreamer                 - A simple media player for the Gnome deskto
p   totem-gstreamer-firefox-plugin  - Totem Firefox Plugin - gstreamer version  
```

---

### Post by crichell on 2006-08-21
The only difference is that I don't have totem-gstreamer installed.  And that's not the issue.  Are you doing a restore then upgrading to Dapper or is the restore taking you directly to Dapper?

---

### Post by frainbart on 2006-08-21
Yup, I see the difference. The System Restore DVD takes me directly to Dapper, what you see is just what I get when I restore and then install the codecs from EasyUbuntu and gxine. I have the automatic updater notifying me about 161 updates that I have not installed yet (I installed them earlier tonight afterwards, and still a no go, the test you see does not include the latest updates).

---

### Post by crichell on 2006-08-21
I'm running with the latest updates as well.

Earlier I said I thought EasyUbuntu was installing gstreamer0.8 but in looking at what's is installed it doesn't appear that way.  All I see is gstreamer0.10 packages.

---

### Post by frainbart on 2006-08-22
No difference between gstreamer before and after the Ubuntu updates for me.

---

### Post by crichell on 2006-08-22
i'm now testing this off of the same restore DVD you have - previously i was using our imaging server which is always newer than restore DVD's.

---

### Post by crichell on 2006-08-23
Just wanted to give a quick update.  I've restored via DVD ran EasyUbuntu and the system crashed on inserting DVD.  Ran Updates - same system crash.

Restored from DVD again, ran all updates, ran EasyUbuntu, inserted DVD and crash.

Restore from our imaging server, ran EasyUbuntu, insert DVD, and DVD plays.  I'm going to get to the bottom of this.  It's a strange one but we now know that a difference between the image that comes on the laptop allows this to work but the image that comes from the DVD does not (wierd).

---

### Post by frainbart on 2006-08-23
Thanks, I have reproduced the system crashes under those same conditions on my laptop.

---

### Post by crichell on 2006-08-25
frainbart - as a quick fix I can create a new DVD image for you from our imaging server and mail it out to you.  It doesn't get to the root of the problem but it will get multimedia playing for you.

Let me know if you would like me to do this.

Cheers, Carl

---

### Post by frainbart on 2006-08-25
Carl, thanks. I might as well try that; go ahead and send it to me. Is there a way to restore the image without having to destroy your pre-existing partitions because I have a dual boot setup with Windows at the moment.

---

### Post by crichell on 2006-08-25
The restore DVD does wipe out and repartition the disk.  I'm going to keep at it over the weekend.  We need to get it solved anyway - full restore should never be the solution.  If I don't get it cleared over the weekend I'll send out a disk to you on Monday.

---

### Post by crichell on 2006-08-28
GOT IT!  Xv is the problem.

```
gstreamer-properties
```

Multimedia Systems Selector Pops Up > Click the Video Tab

Change Default Output Plugin to "XWindows (No Xv)"

Close

---

### Post by crichell on 2006-08-28
Some further config and info on this.

The above fix disables Xv for gstreamer but gstreamer0.10 doesn't yet support DVD playback.  To use totem-xine or gxine for DVD playback we have to disable Xv there as well.

```
sudo gedit /etc/X11/xorg.conf
```

Comment out the extmod module as so.

```
Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "dri"
#   Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

```

---

### Post by frainbart on 2006-08-28
Thanks Carl! That seemed to do the trick. Totem still plays DVDs but as a cdrom...weird. It will play the video (labeled cdrom0) without all the menus available and the video sometimes stutters. Gxine seems to play them alright, including menus and alternate audio tracks, but the colors are screwed up; everything is purple or green. Totem streams video and music now from the internet well (I never realized how well totem works until now, hehe, never had it run without a crash until now). I will look into gxine's settings to see if I can fix the color problem, or try other xine players.

---

### Post by crichell on 2006-08-28
I noticed totem-xine works much better too (colors are purple for me is gxine as well).  I'm happy with Totem using the xine backend.  It will be nice once gstreamer is the standard for all of us.

---

### Post by frainbart on 2006-08-28
Yup, totem-xine works better, not as smooth as gxine. It seemed Totem-gstreamer just about played anything. Totem-xine won't stream m3u files (Magnatune), but VLC works nicely with streaming and DVDs.

---

### Post by frainbart on 2006-08-29
I have the same problem with Democracy TV as I did with gxine. I guess they are based on the same xine video player foundation. I get purple, green, gray video with the frame sometimes shifted off screen which recenters after a window resize. I tried some tweaks at the xine website, [http://xinehq.de/index.php/faq]("http://xinehq.de/index.php/faq"), but it didn't help.

---

