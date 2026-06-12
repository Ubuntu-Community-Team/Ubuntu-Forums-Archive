---
title: "Ubuntu CE vs Ichthux"
date: 2006-09-16
forum: Ubuntu Christian Edition
---

### Post by Demonsmasher on 2006-09-16
Hi guys. Ubuntu CE looks real great. I am also looking at Ichthux. What are the main difference in the two. Is it mainly gome vs kde??? I seem to kinda of like both maybe leaning towrd the Ichthux side just alittle. Because I guess of the way the GUI looks alittle bighter than gome GUI. Can any of you lean me back the other way some? :) I've work with computers for 10 years now but just  lately started looking at Linux the past few years. Everytime I try a different distro I never really find installing software really easy like in windows. But thats beside the point right now. My main question is wich of the 2 versions would be right for me.

---

### Post by mhancoc7 on 2006-09-16
> **Demonsmasher said:**
> Hi guys. Ubuntu CE looks real great. I am also looking at Ichthux. What are the main difference in the two. Is it mainly gome vs kde??? I seem to kinda of like both maybe leaning towrd the Ichthux side just alittle. Because I guess of the way the GUI looks alittle bighter than gome GUI. Can any of you lean me back the other way some? :) I've work with computers for 10 years now but just  lately started looking at Linux the past few years. Everytime I try a different distro I never really find installing software really easy like in windows. But thats beside the point right now. My main question is wich of the 2 versions would be right for me.

Hi,
Thanks for your interest in either project. 

One of the main differences is the fact that Ubuntu CE uses Gnome and Ichthux uses KDE. Keep in mind that you can switch Ubuntu CE to KDE by simply installing it. You can also switch Ichthux to Gnome in the same manner. 

Ubuntu CE and Ichthux are also taking a different route with some of the development. Ichthux is works with meta-packages where as Ubuntu CE is working with bash scripts. There are pros and cons to both. Meta-packages are awesome since you can basically install Ichthux to any Ubuntu install. The bash scripts that Ubuntu CE accomplish the same thing in a different way. With the Ubuntu CE Upgrade_ME and Convert_Me scripts a user can easily upgrade their Ubuntu CE install or convert there default Ubuntu install. I decided to take this approach for many reasons, one of which is many of the users coming to Ubuntu CE are coming from Windows and are more accustom to double-clicking and exe file to install things. This is how the scripts work. 

Ubuntu CE also integrates web content filtering powered by Dansguardian. Ichthux comes with filtering as well. You will have to turn it on in Ichthux. In Ubuntu CE the filtering is preinstalled and configured and is funtioning from the LiveCD as well as when installed. We have also added a GUI to make it easy to configure the filter settings. 

Ubuntu CE also includes the Ubuntu CE Installer which allows users to easily install more Education and Christian programs. 

Automatix is also installed by default in Ubuntu CE so users can quickly get their system running. 

I am obviously biased towards Ubuntu CE since it is my project, but I want to be sure to say that Ichthux is an excellent project. I highly respect the developers of it and you would be choosing an excellent distro if you choose Ichthux.

God Bless, Jereme

---

### Post by Demonsmasher on 2006-09-16
OK thanks. Is there away to have  Ubuntu CE and Ichthux installed on one computer? Also I noticed while I am running the live cd that my wireless dosn't work, can this be fixed or just something to get used too?

---

### Post by Lord Illidan on 2006-09-16
dualboot. install on different partitions.

---

### Post by mhancoc7 on 2006-09-16
> **Demonsmasher said:**
> OK thanks. Is there away to have  Ubuntu CE and Ichthux installed on one computer? Also I noticed while I am running the live cd that my wireless dosn't work, can this be fixed or just something to get used too?

Yes, you can dual boot Ubuntu CE and Ichthux. As for the wireless, Ubuntu CE supports wireless in the same way that Ubuntu does. Once you have installed Ubuntu CE you can search the Ubuntu forums for answers to getting your wireless working. I wished I could be more help with the wireless.
Jereme

---

### Post by Demonsmasher on 2006-09-16
Ok as far as the difference. Is there a difference in installing software? This is what I like to do so to give you a better idea. I build and maintain webpages, I like working with music, dvd and other video. Everythime I use a different distro I can never find a any free webpage creation software. Any idea?

---

### Post by mhancoc7 on 2006-09-16
> **Demonsmasher said:**
> Ok as far as the difference. Is there a difference in installing software? This is what I like to do so to give you a better idea. I build and maintain webpages, I like working with music, dvd and other video. Everythime I use a different distro I can never find a any free webpage creation software. Any idea?

Installing software works in much the same way on both. The Ubuntu CE Installer is really the only difference with installation.

[Automatix]("http://www.getautomatix.com/") is also included in Ubuntu CE. [Automatix]("http://www.getautomatix.com/") is a great tool for getting Ubuntu CE setup to play DVDs and mp3s quickly and easily. It also installs and tweaks your system so you can get going quickly. The next release of Ubuntu CE will also include [NVU]("http://www.nvu.com/index.php") web authoring software. [NVU]("http://www.nvu.com/index.php") is as an excellent WYSIWYG web page creator.

If you have any questions just let me know.

Jereme

---

### Post by Raphink on 2006-09-23
Hi,

Dual booting is not necessary in that case since it is the same OS. Ichthux is a derivative as Kubuntu/Xubuntu or Edubuntu.

You can very well get an Ubuntu installation, install Ichthux by following the instructions at [http://ichthux.com/install](http://ichthux.com/install) and then run the Ubuntu CE scripts that will modify the GNOME look & feel.

When logging in, you will have the choice between GNOME (Ubuntu CE) and KDE (Ichthux) on the same OS.

Note that the Ichthux installation will be much easier with Ubuntu 6.10 (Edgy) since the Ichthux packages will be included in the Ubuntu repository. The core Ichthux packages are already there, so if you are running Edgy with universe activated, "sudo apt-get install ichthux-desktop" will install Ichthux, simply :)


God bless


Raphaël

---

