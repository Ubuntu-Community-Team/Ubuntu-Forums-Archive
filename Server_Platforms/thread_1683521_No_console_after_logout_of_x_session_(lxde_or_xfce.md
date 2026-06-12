---
title: "No console after logout of x session (lxde or xfce) on ubuntu 10.10"
date: 2011-02-07
forum: Server Platforms
---

### Post by gino.eelen on 2011-02-07
Hi,

I am  planning setting up an Ubuntu 10.10 server. 

Since for some tasks I prefer using a GUI, I want to install xfce4 or lxde so I can call it up from the console when needed, but I always run into the same problem: I can start the GUI with startx, but after logging out from the GUI I am not taken back to a console. The screen displays the GUI background, and no user input is possible. Not even ALT-CTL-Fx or ALT-CTL-BACKSPACE. I have to hard-reset the machine.

It works OK in 9.04, so I am wondering why it goes wrong in 10.10.

I am still playing and testing possible setups so I am installing and running in a VMWare virtual machine for now.

I intalled the gui's with
sudo apt-get install lxde
sudo apt-get install xfce4

I also installed xinit
sudo apt-get install xinit

Anybody have any suggestions how I can get this to work? 
Thanks a lot!

---

