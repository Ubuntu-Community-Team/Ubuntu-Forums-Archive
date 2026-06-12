---
title: "bonp5 vgaout adapter"
date: 2012-05-27
forum: System76 Support
---

### Post by oxman on 2012-05-27
I have a bonp5. I am seeking to do an Libreoffice Impress presentation. I have purchased an adapter to do vga out of the laptop and vga in to the projector. The projector is not picking up the laptop screen. I have tried to do Fn F7 thinking that was my option to no avail. Any assistance is appreciated. Thx.

---

### Post by Arioch on 2012-05-27
Hi,

that is a known bug with Nvidia cards and ubuntu 12.04 and previous versions. The displays app or Func+F7 don't work. You have to use Nvidia-XServer-settings.

Open dash (ubuntu key)
type nvidia...
open Nvidia X Server settings.
go to displays configuration and select the options you need (most likely twinview)
click apply and you should be ready to go.

hope this helps

PS if you go to askubuntu.com there are many threads about this issue.

---

### Post by oxman on 2012-05-27
Arioch, Your suggestion was very helpful. It at least gave me a point of reference. I attempted to configure the nvidia settings as recommended but it still did not work. You also suggested that I check out [askubuntu.com]("http://askubuntu.com") . This was very helpful also. There was a suggestion there to login via ubuntu 2D. At that point my projector picked up the signal but responded as a dual monitor. It did not pick up the signal on screen#1. The work around is very complicated and I am hoping for a simpler resolution to the problem.
I am very grateful to you for your assistance. It is helping me pinpoint the problem.

Once I was able to get the projector to pick up the signal I did manage to run through the slide presentation using screen #2. Unfortunately screen #1 locked up and I had to re-initiate the server doing Ctrl+Alt+Backspace 

(The keyboard is not configured to do that automatically. You must first do go to: System Settings > Keyboard > Layout Settings > Options > Key sequence to kill the X server > select)

to get back to normal. I will try fine tuning this work around and posting it here. Thx again.

---

### Post by Arioch on 2012-05-27
No problem, always a pleasure to help. I still think that you should be able to configure it just using Nvidia Xserver settings but as long as it works any way will do.

At the moment this bug is one of the most annoying 'features' still bugging me in Ubuntu as I also have to hook up my laptop to projectors in workshops and conferences.

Miss the good old days of Fn+F7

---

### Post by drewbenn on 2012-05-27
Some coworkers are using a tool called '[disper]("http://willem.engen.nl/projects/disper/")' with the nVidia graphics cards in their laptops.  They say it works well with multiple different display setups (laptop-only, docked+monitor, laptop+monitor), though I haven't tried it yet myself.

I typically use (on Debian stable) nvidia-settings or a custom script to toggle my docking station's external monitor on and off, but I've never gotten things back to normal after using a projector without an X restart (if I used projectors more than about twice a year I'd be in a bigger hurry to try out disper).

---

### Post by oxman on 2012-05-28
Still no joy after the disper install but it does seem to be narrowing down to the nvidia driver. Ubuntu acknowledges the projector. The interface  between the graphics card and nautilus/unity is no good. My work around only works as a dual monitor setup  and dash shows up once in a while when it feels like it ... with the obligatory lock up afterwards of course.

---

