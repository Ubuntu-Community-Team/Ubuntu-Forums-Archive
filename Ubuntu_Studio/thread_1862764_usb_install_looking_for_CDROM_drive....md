---
title: "usb install looking for CDROM drive..."
date: 2011-10-17
forum: Ubuntu Studio
---

### Post by mtmigs on 2011-10-17
My computer's DVD drive died and I am trying to load Ubuntu Studio 10.04 for my wife. I realize this is not the latest version but it is the version on other computers in my house.

I tried using Imagewriter.exe but that would not boot at all. I tried using Universal-USB-Installer-1.8.6.8.exe. That did not list Ubuntu Studio 10.04 in the options so I tried using other iso and both old and new Syslinux. I cannot remember what happened but the install did not even start.

I then tried unetbootin-windows-563.exe. It started the install but kept failing to mount the CD-ROM. I read the previous thread and tried "shut off all non-essentials, acpi, powermanagement, networking, bluetooth..." listed. My computer has very few bios options and none of those were there. I am not sure how I can turn off any of the things listed in Ubuntu since Ubunti is not loaded and the install does not give any options but the next step.

---

### Post by jejeman on 2011-10-17
If I remembre correctly, once I had the same problem with ubuntustudio 11.04. I just end up trying again and again untill it worked. I mean until it recognised the usb as cd, not starting installation all over again.
But, it was a long time ago, maybe I imagine it.

---

### Post by mtmigs on 2011-10-17
I gave up and tried something different. Searching the web I found an old message stating to just do this at the command prompt:

sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt

It seems it might work even though the message was upgrading from standard ubuntu version 8 to ubuntu studio. Though I needed to play with the repositories. It again wanted a CD for the upgrade.

---

### Post by jejeman on 2011-10-17
Yes, you can install plain ubuntu, or mini.iso, and then install ubuntustudio packages.
thisi is what is instaled on my ubuntustudio 10.04
```
$ dpkg -l|grep ubuntustudio
ii  plymouth-theme-ubuntustudio                       0.38.3                                           Ubuntu Studio Plymouth theme
ii  ubuntustudio-audio                                0.70                                             Ubuntu Studio Audio Package
ii  ubuntustudio-audio-plugins                        0.70                                             Ubuntu Studio audio plugins Package
ii  ubuntustudio-controls                             0.4.7                                            Ubuntu Studio Controls is a small app that changes A/V se
ii  ubuntustudio-default-settings                     0.26ubuntu2                                      Default settings and artwork for the Ubuntu Studio deskto
ii  ubuntustudio-desktop                              0.70                                             Ubuntu Studio Desktop Package
ii  ubuntustudio-font-meta                            0.70                                             Ubuntu Studio fonts Package
ii  ubuntustudio-graphics                             0.70                                             Ubuntu Studio graphics Package
ii  ubuntustudio-icon-theme                           0.11                                             Ubuntu Studio Icon theme
ii  ubuntustudio-look                                 0.38.3                                           Ubuntu Studio look
ii  ubuntustudio-menu                                 0.13                                             Menu for Ubuntu Studio
ii  ubuntustudio-screensaver                          0.4                                              Ubuntu Studio screensaver
ii  ubuntustudio-sounds                               0.10                                             Ubuntu Studio's GNOME audio theme
ii  ubuntustudio-theme                                0.38.3                                           Ubuntu Studio look - GTK and Metacity theme
ii  ubuntustudio-video                                0.70                                             Ubuntu Studio video Package
ii  ubuntustudio-wallpapers                           0.38.3                                           Ubuntu Studio - Wallpapers
```
also you need the preempt kernel to have full studio feel. If you dont do audio you don't need it.
```
ii  linux-headers-preempt                             2.6.32.34.40                                     Linux kernel headers for Low Latency Servers.
ii  linux-image-preempt                               2.6.32.34.40                                     Linux kernel image for Low Latency Servers.
```

---

