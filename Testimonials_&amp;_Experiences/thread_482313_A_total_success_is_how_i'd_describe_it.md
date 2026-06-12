---
title: "A total success is how i'd describe it"
date: 2007-06-23
forum: Testimonials &amp; Experiences
---

### Post by jnorthr on 2007-06-23
here's an opinion on ubuntu on my kit. Decided to try the kde flavor of ubuntu called kbuntu on my laptop (nicknamed 'tiny') as K has a smaller footprint then ubuntu. Laptop is 20GB drive 800MZ cpu and maxed out 256MB ram plus floppy,2xUSB's PCMCIA's, normal UK keyboard and touchpad mouse. No direct internet access.

Downloaded kubuntu desktop 7.0.4.iso  onto my wife's windows desktop machine then burned the .iso desktop version to dvd. 

Took it to tiny and mounted it. Then restarted and kbuntu runs live from the dvd, though very slowly. It does not use the hard disk unless you do an install which i did. 

During the installation a utility called super grub allowed me to change the single fat32 windows partition. 
So cancelled out of kubuntu and went back into windows just to reduce disk usage. Did a defrag and then started kbuntu install again and it went quite ok. created a small swap partition, a /home partition of 3GB and the root partition of about 8GB.

I was very impressed. almost no effort involved to install and the kde desktop is quite something. Loads of free packages and software (it says) can be included though i can't see them on this DVD. Runs quite quickly @800mz and EVERYTHING works! Out of the box, it all works, the floppy, cd, my freecom usb drive, and this version of kbuntu has a driver to read AND write to fat32 partitions, so no need to change into windows just to get some files off. .mp3's, pdf's movies, sound, mice are ok too. Recognised every key on the keyboard correctly

Since i do a lot of development I'm starting to look into how to install java 1.6 and will need to solve some permissions issues first, but i like it ALOT. :KS It assumes you are on the internet, but works ok even if not.

Now if i can just figure out how to download java stack from the internet respository onto the windows box then copy to something to load onto tiny....:o

---

### Post by jfinkels on 2007-06-23
> **jnorthr said:**
> here's an opinion on ubuntu on my kit. Decided to try the kde flavor of ubuntu called kbuntu on my laptop (nicknamed 'tiny') as K has a smaller footprint then ubuntu. Laptop is 20GB drive 800MZ cpu and maxed out 256MB ram plus floppy,2xUSB's PCMCIA's, normal UK keyboard and touchpad mouse. No direct internet access.

Downloaded kubuntu desktop 7.0.4.iso  onto my wife's windows desktop machine then burned the .iso desktop version to dvd. 

Took it to tiny and mounted it. Then restarted and kbuntu runs live from the dvd, though very slowly. It does not use the hard disk unless you do an install which i did. 

During the installation a utility called super grub allowed me to change the single fat32 windows partition. 
So cancelled out of kubuntu and went back into windows just to reduce disk usage. Did a defrag and then started kbuntu install again and it went quite ok. created a small swap partition, a /home partition of 3GB and the root partition of about 8GB.

I was very impressed. almost no effort involved to install and the kde desktop is quite something. Loads of free packages and software (it says) can be included though i can't see them on this DVD. Runs quite quickly @800mz and EVERYTHING works! Out of the box, it all works, the floppy, cd, my freecom usb drive, and this version of kbuntu has a driver to read AND write to fat32 partitions, so no need to change into windows just to get some files off. .mp3's, pdf's movies, sound, mice are ok too. Recognised every key on the keyboard correctly

Since i do a lot of development I'm starting to look into how to install java 1.6 and will need to solve some permissions issues first, but i like it ALOT. :KS It assumes you are on the internet, but works ok even if not.

Now if i can just figure out how to download java stack from the internet respository onto the windows box then copy to something to load onto tiny....:o

I'm glad it's working for you so far!

If you can get an internet connection on your Windows partition, then you should most likely be able to get an internet connection on your Ubuntu partition! Remember to search the forums and make a thread in the forum for any problem you're having; we can fix it!

Once you get an internet connection working, iinstalling software is a breeze, see the link in my signature about Installing Software.

---

### Post by YoG%*@ on 2007-06-23
first of all, congratulations on your successfull installation!

if you want to install java without having direct access to the net, you might want to consider downloading the binary from [http://java.sun.com]("http://java.sun.com/") and install java through that.

then there's always [http://packages.ubuntu.com]("http://packages.ubuntu.com/"), which has all the packages available for ubuntu. but you'll have to take care of resolving the dependencies yourself.

another option would be [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) - APTonCD which i've heard can be quite usefull for installing packages offline.

hth
mux

---

