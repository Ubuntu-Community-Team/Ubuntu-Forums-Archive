---
title: "Edgy to Dapper"
date: 2007-03-25
forum: The Cafe
---

### Post by Irony on 2007-03-25
I'm not sure this belongs in the Cafe but it is a discussion of sorts.

I've just reverted back to Dapper from Edgy; Edgy had a number of problems... messed up bootsplash, open as root didn't work, connect to server didn't work, occasional freezing on booting, they were small but irritating and I was easily able to get around them. One thing that did work noticeably better in Edgy was the Gnome Partition Editor - in Dapper it is at best indecisive. Also the Edgy CD doesn't work as a live CD.

Dapper has no problems so I reverted back to that and discovered a few new things because I wanted to install the latest programs, so here they are plus a few things I've picked up in the past;

Inkscape 0.45.1 - Autopackage [http://autopackage.org/downloads.html](http://autopackage.org/downloads.html) - I've been using Ubuntu since Hoary but haven't noticed this install system before; it went very smoothly when installing inkscape 0.45.1. I'm not sure why its not mentioned in the Ubuntu forums more often.

Firefox 2.0.0.3- [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox) aysiu's and nanotube's script works like magic to install the latest version of firefox. Apparently firefox will now work like the windows version in that it will offer to update automatically when new firefoxes come out.

Blender 2.43 - [http://www.blender.org/download/get-blender/](http://www.blender.org/download/get-blender/) I've always found that simply uncompressing the blender.org linux file and running blender from it means blender opens much faster than the repository installed blender. Install Yafray from the repositories and it will run from the uncompressed Blender.

Tiling - [http://freshmeat.net/projects/wmtile/](http://freshmeat.net/projects/wmtile/) I installed this version of the tiling software which allows me to vertically and horizontally tile windows. A newer version is here [http://ftp.unixdev.net/pub/debian-udev/pool/main/t/tile/](http://ftp.unixdev.net/pub/debian-udev/pool/main/t/tile/) though I haven't tried it. I've always wondered why Gnome and KDE don't have this tiling - its something Windows has but not Linux.

Wine - on reverting back to Dapper I found that my fonts were messed up in Wine. So instead of reinstalling the repository Dapper Wine I went to [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) and added the Dapper repository for the latest wine, it works better in that Autosketch 7.0 now has a functional zooming mousewheel and the fonts of wine installed stuff are sorted.

OpenOffice 2.1 - In Dapper and Edgy OO 2.02 and 2.04 don't work properly (zoom and microsoft fonts for example) whereas 2.1 does - note uninstalling the repository OO uninstalls ubuntu-desktop; this is not a problem but when updating to newer Ubuntus it will have to re-installed. Install the DEBs from here [http://www.nic.funet.fi/pub/misc/openoffice/localized/finnish/stable/2.1.0/latest/](http://www.nic.funet.fi/pub/misc/openoffice/localized/finnish/stable/2.1.0/latest/) (sudo dpkg -i) or convert the RPMs from here [http://download.openoffice.org/2.1.0/index.html?focus=download](http://download.openoffice.org/2.1.0/index.html?focus=download) via alien to DEBs [http://ubuntuforums.org/showthread.php?t=318865&page=3](http://ubuntuforums.org/showthread.php?t=318865&page=3)

So in my case Dapper LTS is more workable and more updated than Edgy. Funnily enough I retained the rounded edged windows from Edgy in Dapper, so my Dapper looks rather like Edgy...

---

### Post by Quillz on 2007-03-25
Sorry to hear Edgy didn't work out for you. You should give Feisty a try, though. It is a huge upgrade from 6.10, and especially 6.06.

---

### Post by karellen on 2007-03-25
I like edgy more than dapper ;)

---

### Post by Ireclan on 2007-03-25
> **Irony said:**
> I'm not sure this belongs in the Cafe but it is a discussion of sorts.

I've just reverted back to Dapper from Edgy; Edgy had a number of problems... messed up bootsplash, open as root didn't work, connect to server didn't work, occasional freezing on booting, they were small but irritating and I was easily able to get around them. One thing that did work noticeably better in Edgy was the Gnome Partition Editor - in Dapper it is at best indecisive. Also the Edgy CD doesn't work as a live CD.

Dapper has no problems so I reverted back to that and discovered a few new things because I wanted to install the latest programs, so here they are plus a few things I've picked up in the past;

Inkscape 0.45.1 - Autopackage [http://autopackage.org/downloads.html](http://autopackage.org/downloads.html) - I've been using Ubuntu since Hoary but haven't noticed this install system before; it went very smoothly when installing inkscape 0.45.1. I'm not sure why its not mentioned in the Ubuntu forums more often.

Firefox 2.0.0.3- [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox) aysiu's and nanotube's script works like magic to install the latest version of firefox. Apparently firefox will now work like the windows version in that it will offer to update automatically when new firefoxes come out.

Blender 2.43 - [http://www.blender.org/download/get-blender/](http://www.blender.org/download/get-blender/) I've always found that simply uncompressing the blender.org linux file and running blender from it means blender opens much faster than the repository installed blender. Install Yafray from the repositories and it will run from the uncompressed Blender.

Tiling - [http://freshmeat.net/projects/wmtile/](http://freshmeat.net/projects/wmtile/) I installed this version of the tiling software which allows me to vertically and horizontally tile windows. A newer version is here [http://ftp.unixdev.net/pub/debian-udev/pool/main/t/tile/](http://ftp.unixdev.net/pub/debian-udev/pool/main/t/tile/) though I haven't tried it. I've always wondered why Gnome and KDE don't have this tiling - its something Windows has but not Linux.

Wine - on reverting back to Dapper I found that my fonts were messed up in Wine. So instead of reinstalling the repository Dapper Wine I went to [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) and added the Dapper repository for the latest wine, it works better in that Autosketch 7.0 now has a functional zooming mousewheel and the fonts of wine installed stuff are sorted.

OpenOffice 2.1 - In Dapper and Edgy OO 2.02 and 2.04 don't work properly (zoom and microsoft fonts for example) whereas 2.1 does - note uninstalling the repository OO uninstalls ubuntu-desktop; this is not a problem but when updating to newer Ubuntus it will have to re-installed. Install the DEBs from here [http://www.nic.funet.fi/pub/misc/openoffice/localized/finnish/stable/2.1.0/latest/](http://www.nic.funet.fi/pub/misc/openoffice/localized/finnish/stable/2.1.0/latest/) (sudo dpkg -i) or convert the RPMs from here [http://download.openoffice.org/2.1.0/index.html?focus=download](http://download.openoffice.org/2.1.0/index.html?focus=download) via alien to DEBs [http://ubuntuforums.org/showthread.php?t=318865&page=3](http://ubuntuforums.org/showthread.php?t=318865&page=3)

So in my case Dapper LTS is more workable and more updated than Edgy. Funnily enough I retained the rounded edged windows from Edgy in Dapper, so my Dapper looks rather like Edgy...

Funnily enough, it was DAPPER that I had problems with. It kept locking up during the install sequence. Edgy worked like a charm.

---

### Post by Quillz on 2007-03-25
> **Nomad O' North said:**
> Funnily enough, it was DAPPER that I had problems with. It kept locking up during the install sequence. Edgy worked like a charm.
Yeah, same here. I never got my native resolution (or 915resolution) working with Dapper, but it worked great in Edgy. Automatix worked better, too. And the ATI drivers only wanted to work in 6.10. For me, the LTS release wasn't that great.

---

### Post by getaboat on 2007-03-25
Dapper is the shared house computer. Edgy is now my own personal computer (bye bye Windows except at work). Edgy is better IMHO - though did do all my experimentation on Dapper. I can't see the point of Beryl, though my teenage son thinks it's cool so perhaps that's the point. 

Networking (with W98, W2k and XP) and wireless (WPA) are still I prob so I am looking to upgrade to Fiesty on both post Beta. I'd go to Edgy on the Dapper box if Fiesty wasn't around the corner.

---

### Post by Quillz on 2007-03-25
> **getaboat said:**
> Dapper is the shared house computer. Edgy is now my own personal computer (bye bye Windows except at work). Edgy is better IMHO - though did do all my experimentation on Dapper. I can't see the point of Beryl, though my teenage son thinks it's cool so perhaps that's the point. 

Networking (with W98, W2k and XP) and wireless (WPA) are still I prob so I am looking to upgrade to Fiesty on both post Beta. I'd go to Edgy on the Dapper box if Fiesty wasn't around the corner.
Beryl has some uses. It uses live thumbnails for Alt+Tab switching, and it also has an Expose clone. Both of those make viewing your open applications much easier than the standard icon-based switching.

---

