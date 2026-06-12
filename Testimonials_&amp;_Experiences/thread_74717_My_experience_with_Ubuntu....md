---
title: "My experience with Ubuntu..."
date: 2005-10-12
forum: Testimonials &amp; Experiences
---

### Post by daveisadork on 2005-10-12
I've been using Ubuntu at home for several months now, and Debian for quite some time prior to that. Today, I decided to do a fresh install of RC1 on my work computer, which consists of an Intel motherboard with an Intel Pentium 4 3.0GHz (it's an EM64T chip, but I'm doing an i386 install), 2 SATA hard drives, a Plextor USB DVD burner and a GeForce PCX5750. I had reserved half of the system drive for "other operating systems" to run alongside Windows XP x64. 

So I popped in the CD and booted from it. Answered a few questions regarding my keyboard layout and time zone, told the installer to use the free space on the system drive and a little while later Ubuntu was installed. It booted up nicely (the new graphical boot is very slick) and came to the GDM login in a surprisingly small amount of time. At this point, I noticed that only one of my dual monitors was working, so I logged in and opened up Synaptic (by clicking on System > Administration > Synaptic Package Manger) and installed nvidia-glx. I then opened a terminal (Applications > Accessories > Terminal) and issued:
```
$ sudo nvidia-glx-config enable
$ sudo gedt /etc/X11/xorg.conf
```
and added the following under the "Device" section of my xorg.conf to enable TwinView:
```
Option     "TwinView"
Option     "MetaModes"  "1280x1024,1280x1024; 1280x1024; 1024x768,1024x768; 1024x768; 800x600,800x600; 800x600"
Option     "TwinViewOrientation"      "RightOf"
Option     "SecondMonitorHorizSync"   "UseEdidFreqs"
Option     "SecondMonitorVertRefresh" "UseEdidFreqs"
Option     "RenderAccel"
Option     "HWcursor"
```
Then I restarted Xorg by issuing Ctrl+Alt+Backspace and was greeted with the nVidia splash spanning both monitors. 

My sound card was detected, but muted. I had to go to Applications > Sound & Video > Volume Control, and change the device to the OSS mixer (Realtek ALC880 in case anyone is wondering, it opened to the default ALSA mixer labeled HDA Intel), and turn up the Volume fader. Then all the blips and bleeps from using the GNOME interface were coming through loud and clear.

Next, I opened up Synaptic again and installed gstreamer0.8-plugins so that Rhythmbox (Applications > Sound & Video > Rhythmbox Music Player) could play my audio files. I also installed totem-xine (which in turn removed totem-gstreamer), and issued to following commands in a Terminal window to download the various codecs and enable totem to play movies using them:
```
$ cd ~
$ wget http://ftp5.mplayerhq.hu/mplayer/releases/codecs/all-20050412.tar.bz2
$ tar xvjf all-20050412.tar.bz2
$ cd all-20050412
$ sudo mkdir /usr/lib/codecs
$ sudo ln -s /usr/lib/codecs /usr/lib/win32
$ sudo mv * /usr/lib/codecs
```
My Pioneer PX-708UF was detected. I have a few NTFS partitions I needed to access, so I opened a terminal and issued these commands:
```
$ sudo mkdir /media/sda1
$ sudo mkdir /media/sdb1
$ sudo gedit /etc/fstab
```
Then I added the following lines to my fstab:
```
/dev/sda1	/media/sda1	ntfs		ro,user,umask=0			0	0
/dev/sdb1	/media/sdb1	ntfs		ro,user,umask=0			0	0
```
I saved the file and closed gedit and then issued the following command in a Terminal to mount the partitions:
```
$ sudo mount -a
```
I had 2 icons labeled sda1 and sdb1 pop up on my desktop allowing me access to my NTFS partitions.

After this, I commenced customization with my favorite background, theme and icons and I also installed some other software I use (gaim-guifications, gmail-notify). I'm amazed at how well everything worked. Performing the same setup on a Windows XP box would've taken me at least twice as long. Big thumbs up to the Ubuntu team on Breezy. 

I know at times it must seem like you guys hear nothing but complaints, especially in these days so close to the release. But rest assured, some of us are very grateful for your making our lives as easy as you have. I for one could not be happier with this release. Never before have I had so little trouble installing and setting up an operating system. Keep up the good work guys.

---

### Post by matthew on 2005-10-12
Thanks for the positive tone and the informative post. I appreciate both and imagine that someone will benefit from reading about your experience when they perform their installation.

---

### Post by wylfing on 2005-10-12
Great description of your install process. It's actually quite helpful for people to post success stories as well as trouble spots, especially clean walkthroughs like this, because they come up when people search for issues with their kit.

---

