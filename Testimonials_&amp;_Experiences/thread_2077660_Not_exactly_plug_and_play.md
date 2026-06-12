---
title: "Not exactly plug and play"
date: 2012-10-29
forum: Testimonials &amp; Experiences
---

### Post by P-I H on 2012-10-29
I decided to install Ubuntu 12.10 on my main computer, which now is running Ubuntu 12.04.
To be a little careful I bought a new SSD disk, to be able to keep the 12.04 installation untouched.
It was not exactly Plug and Play and I start to understand people that favour Apple.
I really like Ubuntu and I want Ubuntu to be used by many more. However, if new users experience the same problems as I did that will not happen.
I had problems with:
- USB boot
- Graphic driver
- Fan controls
- Sound
Hopefully it will not take too long to correct these problems.

My configuration is perhaps not the most common, but I suppose not that unusual and it works perfect in Ubuntu 12.04. The main components are AMD 8120 CPU on a Gigabyte GA-990FXA motherboard, Nvidia GTX 660 graphic card and an Asus Xonar D2X sound card.

My USB boot problem is not necessary an Ubuntu problem, but anyhow embarrassing. I did as usual. Downloaded the iso, and copied it with the dd command to a 2 GB USB stick. The USB stick has worked OK many times before. When booting, I got the error "No configuration file found". Tried all advices found on Internet. This took some time, but nothing worked. At last I tried with another USB stick, 4 GB this time, and this worked fine.

I need the proprietary Nvidia driver to play some games. And the first thing I did after updating the installation, was to use Software Sources to install the driver. The driver wasn't installed correctly and after boot, Ubuntu started with only a pink screen. I prefer to use a graphical ui and booted in recovery mode. This also gave a screen without Launcher and upper Panel. I tried to solve this in terminal mode with apt-get purged nvidia-current, but nvidia-current wasn't found. However Ctrl-Alt-T worked and I was able to start programs by use of the terminal. After some googling I found the name of Software Sources and was able to start the graphical ui, that enabled me to start the VESA driver. After some more googling I found a solution on ASK Ubuntu. The Linux source is not installed and thus the installation of the Nvidia driver fails. After following the advice the Nvidia driver installed OK.

It is very nice to have a noiseless computer and with fancontrol installed in Ubuntu 12.04, I cannot hear the computer during normal use.
There was two problems to get fan control going. Some "microcode_amd_fam15h.bin" was missing. After some searching I found a way to install the micro code, but I do not know if this really is needed. The other problem was that fancontrol needs to be started with sudo. In other case "hwmon0" isn't found. I have not found how to change this.

Sound worked from start, but only in stereo. System Settings/Sound did not give the alternative to activate surround sounds. I installed PulseAudio Manager and in the configuration tab I could activate analog 5.1 sound. However Digital S/PDIF was shown as activated in both System Settings/Sound and PulseAudio Volume Control. After reboot and a new try the settings was OK.

---

### Post by mastablasta on 2012-10-29
wow. too bad. i hope you tried troubleshooting the issues on forums.
 
also using ubuntu certified hardware will make it all work out of the box.
 
the problem i have with certified hardware site is (at least) notebooks are mostly old models not sold aymore. still there are some sites out there that will have information on new hardware and it's compatibility.
 
apple also sells only hardware compatible with their operating system. they never and actually do not want the users to use different hardware (hence the plenty customized plugs on their mashines).
 
the USB stick issue could be BIOS thing. i also can not get most USB sticks i have to boot on my main mashcine. however if i use floppy to boot i can boot from the USB sticks. also some other old sticks work well on the mashine. in short not every stick works on every maschine. at least for boot it seems.

---

### Post by stalkingwolf on 2012-10-30
i have a couple machines that i have to use the bios boot menu to boot from a usb stick. my d800 is one.

Using a usb stick has become my favorite way to install. ive converted all my tools to usb,grub repair,gparted, hirens and ubcd ,and avira av come to mind.
Ive got the 3 Os's i use most on sticks and a back up copy of my day to day system.

---

