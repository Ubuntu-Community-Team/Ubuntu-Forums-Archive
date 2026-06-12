---
title: "Moving from FreeBSD to Ubuntu Feisty 7.04 Beta"
date: 2007-04-13
forum: Testimonials &amp; Experiences
---

### Post by puuque on 2007-04-13
Hi!

I recently installed Feisty 7.04 Beta on my laptop after I had several negative experiences with FreeBSD 6.2. 

First, I have to explain, that my laptop is really old. Though it has a Pentium III with 800 MHz there are only 128 MB RAM (and the graphics card uses 8 MB of that). Theoretically, you should be able to boot from CD / DVD but it doesn't work. That leaves only a floppy or hard disk install. I had already Windows 98 installed but since I can't type Chinese and Japanese with that it's not that useful for me. On Christmas I (with the help of my brother) installed FreeBSD 6.2 RC. FreeBSD had every program I needed and good hardware support but maintaining it was really a pain: you have to configure everything manually and sometimes an update breaks something important. I don't use my laptop often and I spent more time trying to make certain things work (again) than actually using it. I had heard for a long time, that Ubuntu is so easy to use that I decided to give it a try (instead of just installing Fedora which I have on my desktop computer).

As mentioned before, I can't boot from CD so I tried the (experimental) Windows-Installer for Feisty Beta. As expected, it didn't work (it downloaded the Ubuntu-alternate iso and installed grub but that was it). I then burned the Ubuntu iso on CD, copied the files into a folder on the windows partition and used the existing grub to start the installation from hard disk.

I had heard that there could be problems with the graphics driver while installing but since the FreeBSD text installation went flawlessly I didn't expect any problems. I couldn't have been more wrong. Not only was the screen flickering wildly, a third of the installation menu was not visible (the left part). In spite of that, I proceeded, confident in my knowledge of installing operating systems. I don't know the graphical installer for Ubuntu but the text based installer is not for newbies. (Is the installer on the alternate-cd different from the desktop one?) When I came to the part where to set up your partition there were three choices: 1. use the whole hard disk (not good because it overwrites the Windows partition) 2. use the free space on the disk and 3. set up everything manually. There was no option to overwrite existing Linux partitions or set up a default Linux install with a chosen partition size. So I created a custom Linux partition and a (too small) swap partition (the part where to type in the size wasn't visible). After that I choose to install ubuntu-desktop (there was no other choice). Then Feisty installed itself. Hey, shouldn't have there been an option to set up grub? Nope, there wasn't. So much for not having to manually edit configuration files. (FreeBSD set up the dual-boot correctly.)

Anyway, the installation was successful. My laptop booted into Ubuntu (there was no Win98 in the boot menu). The whole booting process took much longer than FreeBSD but that was to be expected. When Gnome finished loading, I was alerted that there were lots of updates available (so the network was set up correctly). I started downloading updates until there came a message which said I should insert the Feisty 7.04 Beta Desktop CD (which I didn't have). I canceled and looked at the settings where you choose from where to install (internet or CD). The boxes for the installation from CD weren't checked. After changing the server I tried again. Same error message. I installed part of the updates which didn't trigger the message but that was no real solution. Then I looked into the config file for synaptic (in /etc/apt/sources.list; had to look up on the internet where it is) and the lines for installation from CD weren't set as comment. So I manually did that, which fixed the problem. But using Synaptic in a window manager like Gnome with not even 128 MB RAM is not a good idea because it overtaxes system resources and can lead to a faulty installation. So it is better to update or install using the console.

Installing stuff from the Ubuntu repositories went on smoothly afterwards. I really like the customization options in Synaptic, e.g. if you want a certain KDE game you can install it without having to install the whole package. The option to install restricted packages is also very useful. 

All the hardware was setup properly from the beginning: I could burn CDs, hear music, my mp3-player was detected when I plugged it in and the windows partition (FAT32) was mounted.

Then it was time to install some 3rd party software. Opera didn't even start, which was a big disappointment. There seems to be a fix now ([http://my.opera.com/desktopteam/blog/2007/04/06/hotfix?cid=2738532]("http://my.opera.com/desktopteam/blog/2007/04/06/hotfix?cid=2738532")), but I haven't tried it yet. After that I added Automatix and installed some more stuff. The biggest surprise was Acrobat Reader 7. It works! That shouldn't be possible with my hardware specifications (on the Adobe site it says a minimum of 512 MB RAM is needed), but it works nevertheless. 

Finally, I edited the grub menu and now I can use Win98 again, if I want. 

To sum everything up: The installation of FreeBSD was easier and better than the Ubuntu one. After installation, setting up and customizing Ubuntu was much easier and faster than setting up FreeBSD. So for now, I'm sticking with Ubuntu (using the fvwm-crystal window manager).

Thanks for the nice distro, bye

---

