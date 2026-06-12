---
title: "Moblin won't remember wireless key :("
date: 2009-09-26
forum: Ubuntu Moblin Remix
---

### Post by jpl888 on 2009-09-26
Loaded Ubuntu Moblin Remix on my partners Dell Mini 10v this morning and have to say by and large it's excellent. However the major niggle I have is having to re-enter the WPA key for the wireless network after every boot. Anybody know how I might save it?

It also seems some of the included video content won't play because of missing codecs. If somebody knows how to get round that one I'd also appreciate it but the major pain is the wireless key.

---

### Post by NormanFLinux on 2009-09-27
Just click the connect automatically tab. That should do it. In KDE, you have to save the login info in the KDE wallet but under GNOME its automatic.

---

### Post by swallisa on 2009-09-28
Actually i'm using 2.1 and even with the auto setting when you lose the wifi connection every once in awhile it will drop the saved key so it has to be re-entered.  Trying to come up with a work around or find one someone else has used.

---

### Post by jpl888 on 2009-09-28
Sorry maybe I am being a bit daft but where is that tab? I clicked the networks icon, I can see a connect button, a place to enter the passphrase, a cross to delete the phrase and a tick box to show the password and that's it.

---

### Post by NormanFLinux on 2009-09-28
It should save the password in Moblin once you click OK. It should then connect if you ticked the connect automatically box on boot-up.

---

### Post by bfiller on 2009-09-30
As for the video content not playing, you need to install gstreamer0.10-plugins-ugly and gstreamer0.10-ffmpeg packages (via Applications->Settings->Package Manager or terminal "sudo apt-get install xxx") and then all the sample content will correctly play.

Having to re-enter the WPA password is a bug, sometimes it autoconnects on reboot and sometimes it does not. When it does not it appears the password is not kept.

---

