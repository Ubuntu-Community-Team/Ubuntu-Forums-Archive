---
title: "Galago UltraPro webcam problems (green output)"
date: 2013-08-17
forum: System76 Support
---

### Post by Jean-Francis_Roy on 2013-08-17
Hi!

Using the Galago UltraPro's BisonCam, NB Pro, some applications show a green output instead of the webcam output.

Working applications :
- cheese

Non-working applications :
- Skype
- vlc v4l2:///dev/video0
- guvcview


Appending any of the following lines does not work :
LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so PROGRAM_NAME
LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libv4l/v4l2convert.so PROGRAM_NAME
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so PROGRAM_NAME
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so PROGRAM_NAME

Also tried the following (found in Ubuntu documentation), and it didn't help :
export XLIB_SKIP_ARGB_VISUALS=1


Please help me with this issue. I had Skype working with different (old) webcams using the LD_PRELOAD trick, but it does not seem to help here. Also, Google doesn't help, seems that the LD_PRELOAD trick works for everybody else... :-(

Thanks!

---

### Post by Jean-Francis_Roy on 2013-08-17
Well, I figured it out.

The problem was not the webcam, but the Intel video driver.

Installing the latest driver from [https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.2](https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.2) solved the issue.

However, this is a shame that one would need to manually install the latest driver, I hope Ubuntu's intel driver gets updated soon!

---

### Post by Pobega on 2013-08-18
Hey dude, would you mind doing a quick review of your laptop? A lot of people over on notebookreview.com are waiting on solid information about this model and no one seems to have much of anything yet.

[http://forum.notebookreview.com/sager-clevo/721987-clevo-w740su-14-1-a-23.html#post9336740](http://forum.notebookreview.com/sager-clevo/721987-clevo-w740su-14-1-a-23.html#post9336740)

---

### Post by raphael-estrada on 2013-08-19
I'm having trouble running that Intel video installer 1.0.2. Complaining about not being able to remove libdrm2.. see [http://imagebin.org/268117](http://imagebin.org/268117)

Any ideas?

Edit: moved this into an own thread: [http://ubuntuforums.org/showthread.php?t=2169102](http://ubuntuforums.org/showthread.php?t=2169102)

---

### Post by treyhunner on 2013-08-29
I also had this problem and the new driver fixed it for me also.

The following worked for me:

wget [https://download.01.org/gfx/ubuntu/13.04/main/pool/13.04/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.0.2-0intel3_amd64.deb](https://download.01.org/gfx/ubuntu/13.04/main/pool/13.04/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.0.2-0intel3_amd64.deb)
wget -q "http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x8D8847D52F4AAA66" -O- | sudo apt-key add -
sudo dpkg -i intel-linux-graphics-installer_1.0.2-0intel3_amd64.deb
intel-linux-graphics-installer  # follow GUI install from here and reboot

---

