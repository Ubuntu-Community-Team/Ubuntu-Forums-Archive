---
title: "Ubuntu 22.10 Settings-sound-output-test does not work"
date: 2022-08-16
forum: Ubuntu Development Version
---

### Post by corradoventu on 2022-08-16
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1983638](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1983638)

---

### Post by Claus7 on 2022-08-17
Hello,

I installed libcanberra-pulse package both on 22.04 and 22.10. For the latter initially synaptic complained that it is not a trusted package, yet in both cases installation went fine and the test of speakers under Settings->Sound worked.

Regards!

---

### Post by avihaa62 on 2022-08-20
[COLOR=#202124][FONT=arial]The application may have a mute or volume button in its main window, so check that. Also, you can check the volume slider in the Sound panel: Open the Activities overview and start typing Sound. Click on Sound to open the panel.






[SIZE=1][URL="https://anonigstalk.com/"]
[/URL][/SIZE][/FONT][/COLOR][SIZE=1][COLOR=#000000][FONT=Arial][anonigviewer]("https://anonigstalk.com/")
[bingenerator]("https://bingenerator.one/")[/FONT][/COLOR][/SIZE]

---

### Post by jbicha on 2022-08-20
The bug was fixed by installing libcanberra-pulse by default again.

---

