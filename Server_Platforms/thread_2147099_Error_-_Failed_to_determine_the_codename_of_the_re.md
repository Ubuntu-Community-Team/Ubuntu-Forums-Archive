---
title: "Error - Failed to determine the codename of the release."
date: 2013-05-20
forum: Server Platforms
---

### Post by leolol on 2013-05-20
Error while starting base system install..
Pls help, no idea why that is.

oh: i'm using a USB CD-ROM drive.

---

### Post by ibjsb4 on 2013-05-20
I have never dealt with this error, but did get some hits that may help you out.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Error+-+Failed+to+determine+the+codename+of+the+release&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Error+-+Failed+to+determine+the+codename+of+the+release&sa=Search&cof=FORID:9)

---

### Post by leolol on 2013-05-20
I googled to but most of which i got where related to booting with a USB stock, hdd etc.. that's why i included that i'm using a usb cd-rom, as my internal one can't read the cd.

It could also be as my server is (as far as i know) running a hardware raid?

---

### Post by oldfred on 2013-05-20
What version are you installing? The newest do not have RAID. 

I believe 12.04.2 still has the alternative installer which is just text based, but then has RAID drivers.

[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop)
> 
[LIST]
[*]There are several options for installing using software RAID.  You can: 
[LIST]
[*][install using the mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD"), distributed from the 'debian-installer' directory on the mirrors; 

[*]install using the desktop CD and migrate the disks to RAID post-install; 
[*]install with the [Ubuntu 12.04 LTS alternate CD]("http://releases.ubuntu.com/12.04/") and upgrade. 
[/LIST]
[/LIST]


---

### Post by leolol on 2013-05-21
I'm running the latest (version 12) server ubuntu.
It's not software raid, it is hardware.
For some reason i came a bit closer then yesterday today: i got one of the drives out. But now it says loads of files are corrup (base installer) and then, when i wanna restart the base installer i get the same error.

---

### Post by leolol on 2013-05-21
Ok i was able to make the install.
Now it says: change your monitor output timings etc. on my monitor... but how should i change those when i can't see anyhting?

---

### Post by oldfred on 2013-05-21
Are you installing Desktop not server?
If you only have one operating system you have to hold shift key down to get grub menu. The use e on ubuntu entry to add nomodeset in place of quiet splash on linux line. Or use recovery mode, in sub menu.

How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by leolol on 2013-05-21
i am installing the server edition.
Sorry, i am a linux noob so any explanaition on how to do it step by step would be great.
It is installed, it also boots but i just can't see anything on my screen and i get the message from it.

---

### Post by oldfred on 2013-05-21
i do not know server. But it does not have a gui. Just command line.
If a new user you may want to install a desktop (gui). Many with servers just install a lightweight one for minimal gui use but primarily use command line.

[https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

Lightweight Desktop enviroment
Ubuntu Server + lxde
works smooth in under 256mb ram on a p2
sudo apt-get install lxde
Or Xfce GUI without any of the associated Xubuntu applications
sudo apt-get install xfce
Comparison of desktop environments 
[https://wiki.archlinux.org/index.php/Desktop_Environment](https://wiki.archlinux.org/index.php/Desktop_Environment)
[http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments](http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments)
Minimal gnome
sudo apt-get install lightdm gnome-terminal synaptic && sudo apt-get install --no-install-recommends gnome-session-fallback

---

### Post by leolol on 2013-05-22
But shouldn't the command line be displayed on my monitor anyways? I don't think installing a gui is gonna solve this use, but i'm gonna do it anyways.

---

### Post by leolol on 2013-05-22
Should i just install the regular desktop ubuntu, what is the difference between the server and desktop variants?

---

### Post by oldfred on 2013-05-22
Server has the option to install all the various server applications. Desktop defaults to desktop type applications and the different versions of Ubuntu may install different apps.

You can  install all server apps to a desktop and vice-versa.
       Used by Server install to choose what you want
sudo apt-get install tasksel
sudo tasksel


 The key meta packages of Ubuntu are :
ubuntu-base (the whole base system which everybody should install)
ubuntu-desktop (the whole gnome environment)
kubuntu-desktop (the whole kde environment)
xubuntu-desktop (the whole xfce4 environment)
lubuntu-desktop (the whole LXDE desktop environment)
edubuntu-desktop (the whole kids/schools oriented gnome environment)
sudo apt-get install ubuntu-desktop

If you are just getting black screen you may need nomodeset of other video boot parameters.

 How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by leolol on 2013-05-22
I don't boot into a black screen. I boot into nothing. All i get is an error message from my monitor that the output timings are wrong and that i need to change them.. i just have no clue how.

---

### Post by leolol on 2013-05-22
that's how far i am atm.. what did i do: i booted normal linux from a usb drive (i think) and then got this, after pressing (i think) f5. 
[IMG]https://lh6.googleusercontent.com/-RrkIEj1LJFw/UZ0dk8N6UdI/AAAAAAAAFMQ/Lz_GhIIehng/w640-h480-no/2013-05-22+21-31-29.356.jpg[/IMG]

---

### Post by leolol on 2013-05-23
Nobody?

---

