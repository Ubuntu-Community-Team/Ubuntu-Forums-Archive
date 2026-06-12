---
title: "gazp9 small issues"
date: 2013-08-07
forum: System76 Support
---

### Post by golfdiesel on 2013-08-07
I have just unpacked my gazp9 and all works well but there are a couple of things that I want to report.
The CPU fan is allways on. The CPU stays at around 37 to 42 degrees C. The laptop is on a hard surface so there should be enough airflow.
The second thing that the CPU fan makes an annoying noise, there is a ever so slight rattle to be heard so you do not only hear the airflow but you hear it when you are in a quiet environment.

Another thing is that the webcam does not work when using Skype. The webcam itself is working but not in skype.

And one final question, are the necessary optimisations applied by System76 to get the maximum performance out of a SSD (trim, swappiness)

---

### Post by Federico_Paredes on 2013-08-10
I don't have the CPU fan  problem, but the laptop get extremely hot, even with good airflow. 

I'm also having the same Skype problem with the camera thatyou mention, and in addition, the Skype sounds are awkward, like saturated. Maybe there are existing incompatibilities with Ubuntu 13.04

Finally, I got some problems with bluetooth and WiFi working at the same time. With some WiFi connections, whenever I link to a bluetooth device, the WiFi starts failing and I need to restart to regain connection.

---

### Post by phxpx on 2013-08-12
Hi I had similar issues.

I had fan and temperature problems. 
I have installed TLP ( link for tlp [http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html](http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html) ) Which solved my occosionally noisy fan.
I still have my CPU temperature around 55 degree Celcius but tech support said that's normal.

I have also installed intel graphics drivers. This install chipset drivers. It solved my Skype video issue :) But still I don't have a practical solution for sound with Skype. 
Link for intel graphics drivers [https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.2](https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.2)

---

### Post by phxpx on 2013-08-13
I have solved my Skype sound problem thanks to Mark Hoffart ( System76 Support )

Actually it was easy.
We all install Skype from its website but it has problems with 13.04.
Instead I have installed Skype from canonical partners, it worked fine :)
Follow this link: [http://askubuntu.com/questions/293693/how-to-install-skype-with-13-04](http://askubuntu.com/questions/293693/how-to-install-skype-with-13-04) and use canonical partners ppa

---

