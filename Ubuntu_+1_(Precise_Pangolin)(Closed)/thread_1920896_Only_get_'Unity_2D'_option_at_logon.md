---
title: "Only get 'Unity 2D' option at logon"
date: 2012-02-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Hedgehog1 on 2012-02-05
It has me a little stumped, frankly.

nVidia driver is loaded and active.  I can even play 'Oil Rush' on this laptop just fine, so I know the nVidia drive is OK.  I have not loaded a special version of the driver, it is the one that occurred with a clean 12.04 install about 14 days ago.

Has this happened to anyone else?

***The Hedge***

:KS

---

### Post by keithpeter on 2012-02-05
Hello Hedgehog1

I'm using a GeForce GT520 nvidia card in this recycled PC.

When I did a fresh install of 12.04 on the 28th Jan I only had Unity 2d. To get Unity 3d I had to install the 'restricted drivers' for nvidia. I used 'jockey' the restricted driver discovery program.

---

### Post by Hedgehog1 on 2012-02-05
Thanks for the idea, keithpeter.

I just tried both of the restricted drivers offered via Jocky.  Neither blow up, but neither gives me a choice of anything but 'Unity 2D'.

I will futz with it some more.  This laptop is just for testing Ubuntu+1, so it not a huge deal.

I am please to see that Unity 2D does seem to work pretty well.  I might not have tried it otherwise.

***The Hedge***

:KS

---

### Post by cariboo on 2012-02-05
Try running nvidia-xconfig as root, then reboot.

---

### Post by jbicha on 2012-02-05
When you say you only get the Unity 2D option, do you mean Unity isn't in the session chooser gear button on the login screen? If so, you must have accidentally uninstalled Unity. Reinstall it.

---

### Post by effenberg0x0 on 2012-02-05
I'd recommend giving a try to NVidia proprietary drivers using their binary installer. It does some checking for conflicting files and settings during install.

- Get it here: [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
(Select the right one for your architecture 32/64-Bit)
- Save it to /home/you/Downloads
- Save your work (we will restart the session)
- Switch to a VT (Ctrl+Atl+F6) and login
- Run:
```
sudo service lightdm stop
cd
cd Downloads
sudo chmod +x NVIDIA-Linux*run
sudo ./NVIDIA-Linux*run
```- Answer "Yes" to all questions
- Test Unity support:
```
sudo apt-get install nux-tools
/usr/lib/nux/unity_support_test -p
```- If OK, then restart lightdm
```
sudo service lightdm start
```- See if Ubuntu (not 2d) is available.
- Test something OpenGL
```
sudo apt-get install mesa-utils
glxgears
```

---

