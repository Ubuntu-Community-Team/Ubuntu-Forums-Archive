---
title: "No Sound"
date: 2010-03-03
forum: System76 Support
---

### Post by johnmata on 2010-03-03
I have a Ratel Value system from System 76

Suddenly I have no sound. When I select system -> preferences -> sound a small window pops up that says "Waiting for sound system to respond", the little window will stay there until i select the only option, "cancel".  i also notice that there is no longer a speaker icon on the desktop taskbar.  when i try to play an MP3 file there are no errors, just no sound, and the volume selections are grayed out. 

the system does seem to recognize the sound card:

john@king:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: VT82xx [HDA VIA VT82xx], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: VT82xx [HDA VIA VT82xx], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Any help is greatly appreciated!

Kind regards,
John Mata

---

### Post by thomasaaron on 2010-03-04
First, go to System > Administration > System76 Driver and click the Install tab and the Install button.

When the driver finishes running, reboot.

I'm not sure if that will fix it, but it's the proper first step.

Your speaker icon is missing... Do you see your networking icon? I'm wondering if the "Notification Area" applet got removed.

---

### Post by johnmata on 2010-03-04
i tried reinstalling the system76 drivers last night, i also performed a system76 restore.  the problem remains.  i still have my other icons, such as the network icon.  any other ideas?

thanks,
john

---

### Post by thomasaaron on 2010-03-05
Could you try booting from a 9.04 or 9.10 live CD? When you do, make sure PCM is turned way up.

Do you have sound there?

If not, we're probably dealing with a hardware issue.

---

### Post by johnmata on 2010-03-07
i booted up to 9.10 and had sound.  i played a CD, no problem.

when i try to play the same cd when i booted back into my normal setting i got an error that said:

"Error playing CD.

Reason: GStreamer error: state change failed and some element failed to post proper error message with the reason for the failure."

any help is immensely appreciated!  

cheers,
john

---

### Post by thomasaaron on 2010-03-08
OK, go to a terminal and run...

gstreamer-properties

...and make sure its set up like the attached screenshot.

---

### Post by johnmata on 2010-03-09
upon opening the gstreamer-properties the proper plugins were already chosen.  however, under default input next to "device" the drop down is grayed out and the reads "none"

---

### Post by thomasaaron on 2010-03-09
It looks like you've run into some sort of bug. But I'm not seeing it across the board. There's not a lot of info on that error message online.

Did you install anything sound-related (software, plugins, codecs, etc...) prior to the problem?

Also, please run...

gnome-volume-control

...from a terminal. This is the same thing as going to System > Prefs > Sound. Since that will not start, let's see if it throws any useful error messages in the terminal.

---

### Post by johnmata on 2010-03-09
i tried running said command in the terminal with the following result:

** (gnome-volume-control:3152): WARNING **: Connection failed, reconnecting...

over and over again this message.

shall i reinstall ubuntu?

---

### Post by thomasaaron on 2010-03-10
OK, that was somewhat helpful. At lease we know others are experiencing it as well...

[http://www.google.com/#hl=en&source=hp&q=gnome-volume-control%3A3152%29%3A+WARNING+**%3A+Connection+failed%2C+reconnecting&aq=f&aqi=&aql=&oq=&fp=439483403d199a5c](http://www.google.com/#hl=en&source=hp&q=gnome-volume-control%3A3152%29%3A+WARNING+**%3A+Connection+failed%2C+reconnecting&aq=f&aqi=&aql=&oq=&fp=439483403d199a5c)

Try running...

sudo apt-get remove pavucontrol

...and then rebooting.

Re-installing would definitely fix it. But if you want to keep tinkering with it, I think we can at least find some more leads.

---

### Post by johnmata on 2010-03-13
here's the result of running the command:

Package pavucontrol is not installed, so not removed
The following packages were automatically installed and are no longer required:
  gcj-4.3-base libglib1.2ldbl imlib11 libwildmidi0 libboost-regex1.34.1
  guile-1.8 librpmbuild0 libavutil-unstripped-49 lilypond-doc aisleriot
  libboost-regex1.38.0 gtali lilypond-data libgcj9-0 ttf-wqy-zenhei
  swh-plugins glchess libgcj-bc libk3b3 sndfile-programs libgtk1.2
  libsoundtouch1c2 postfix libdiscid0 twolame mplayer-skins gnobots2
  gnome-mahjongg liblog4j1.2-java-gcj ttf-kannada-fonts lsb-graphics
  lsb-desktop same-gnome libdca0 libopenspc0 m4 liblog4j1.2-java librpmio0
  audacity-data librpm0 ncurses-term libass1 libass3 libboost-thread1.37.0
  gnibbles libcommons-cli-java libdvbpsi5 libswt-gtk-3.4-java gcj-4.4-jre-lib
  libggi-target-x libgcj10 libmysqlclient15off libx264-65
  libtorrent-rasterbar2 libvlc2 gnome-games-common libk3b3-extracodecs
  libenca0 gcj-4.4-base libqt4-gui libggi2 gnotski libgcj-common gnometris
  libgii1 ttf-telugu-fonts libclutter-1.0-0 libswt-gnome-gtk-3.4-jni freepats
  vamps lsb libgcj9-jar libnspr4-dev pax iagno glines libffado0 flac
  libdbus-qt-1-1c2 libpano13-0 libgii1-target-x libclutter-gtk-0.10-0
  gnome-sudoku rpm lilypond libphonon4 libkate1 libcdaudio1 libmimic0
  libgtk1.2-common imlib-base gnotravex gnect gdk-imlib11 liblua5.1-0
  ttf-oriya-fonts mjpegtools bsd-mailx rosegarden-data libgmyth0 vlc-data
  liblrdf0 libtar libboost-filesystem1.37.0 mailx libcommons-lang-java
  mkvtoolnix lsb-core ttf-bengali-fonts libvlccore2 alien
  libswt-cairo-gtk-3.4-jni libebml0 libboost-system1.37.0 libglademm-2.4-1c2a
  libmatroska0 libofa0 libmms0 libiptcdata0 texinfo libboost-python1.37.0
  qt4-qtconfig libsdl-image1.2 libswt-gtk-3.4-jni java-wrappers lsb-cxx
  libmusicbrainz3-6 libswt-mozilla-gtk-3.4-jni gnomine
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.

---

### Post by thomasaaron on 2010-03-15
Whew. Tough one.

Try running...

lsmod | grep -i snd

...and let's see if all of your audio modules are being loaded. Your list should look something like this...

thomasaaron@ubuntu:~$ lsmod | grep -i snd
snd_hda_codec_si3054     5856  1 
snd_hda_codec_realtek   277860  1 
snd_hda_intel          31880  2 
snd_hda_codec          87584  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  4 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27296  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  17 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm

---

### Post by jpv on 2010-03-16
Give this a try [http://ubuntuforums.org/showpost.php?p=8686757&postcount=6](http://ubuntuforums.org/showpost.php?p=8686757&postcount=6)

---

### Post by edc80 on 2010-03-28
(I just posted this on another thread too.)

I'm no Ubuntu expert, but I've had this problem twice, once when upgrading to Karmic 9.10, and again today when downgrading to Jaunty 9.04 (for other reasons).  Just now, I got my sound back by doing the following:

1: Left click on the speaker icon that's in the upper right corner of my screen.

2: In the little window that opens up, left click "Volume Control".

3: In the volume control box, left click "Preferences" and add a check-mark to every single thing on the list that shows up, then close that little pop-up box.

4: Go across the tabs in the open Volume Control box and click on "Switches."

5: Remove the check-mark from "External Amplifier."

6: Close all open boxes.

I'm not sure why this works, but it has worked twice now, so I thought I should share it.

With thanks,
-Ed.

---
To Jesus through Mary

---

### Post by thomasaaron on 2010-03-29
Yeah, I think that's a different issue than the one in this thread. I believe what you have is a known bug that only manifests itself on the older Gazelles.

---

