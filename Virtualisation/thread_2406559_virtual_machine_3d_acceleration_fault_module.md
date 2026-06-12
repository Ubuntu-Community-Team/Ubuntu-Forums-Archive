---
title: "virtual machine 3d acceleration fault module"
date: 2018-11-22
forum: Virtualisation
---

### Post by spiridonios on 2018-11-22
Hi,

 I am trying to run an application in virtual machine (host ubuntu 18.04.1 LTS  - guest windows 8) which needs 3d acceleration. The application is a more than a decade old video game.
When i have unchosen 3d acceleration in the settings of virtualbox, the application starts normally, i am guided through the menu and when i am trying to start playing the game, it instantly crashes. The application screen turns off and i am left at the operating system (windows) desktop. If i enable 3d acceleration the application does not start at all. Instead, i get a window saying that the application has stopped working, and when i click to see the problem details, i see that the problem event name is **APPCRASH**, the fault module name is** VBoxDispD3D-x86.dll** and the fault module version is **5.0.40.15130**
 I tried changing the paravirtualisation interface from default to legacy, then to hyper-V and then to none, each time rebooting and trying to run the application, but i had no better luck. I also tried adding more cpus for the guest system, through: settings-->system-->processor, with no luck either. 
 I guess that something should be done with the fault module mentioned earlier, but i do not have the knowledge to judge correctly.
 Would anyone have an idea how i could proceed on fixing this?

---

### Post by ajgreeny on 2018-11-22
Have you added the Guest-Additions to the VBox application itself on the host and then enabled them fully in the guest OS as that might make a difference?

However, I have to admit to never bothering with 3D acceleration in my guests as in the past that there were many display problems when enabled, and I do not need 3D for any of my guest's applications.

---

### Post by spiridonios on 2018-11-22
Hi ajgreeny,

thank you for your reply. I have downloaded the guest-additions package. i am not sure if i had installed it in the host Os previously, but by following some info of another post, i installed added the iso image to virtual machine's storage device and i executed the files in the host. I guess the package should be installed now. By trying to run the application again though, i have the same problem.

Meanwhile, i created a second host Os with an edition of windows 10, and on this, i was able to run the application. The graphics though respond quite slow, which makes it impossible for actually playing the game.

I also had installed virtual box and windows in order to run a specific software for a plotter that could not be adopted to linux easily. Maybe it would be better to stick to that to not end up making things worst..

---

