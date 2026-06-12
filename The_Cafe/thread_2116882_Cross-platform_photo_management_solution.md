---
title: "Cross-platform photo management solution?"
date: 2013-02-17
forum: The Cafe
---

### Post by Potters Son on 2013-02-17
After getting back from my first trip abroad, I decided I was going to consolidate and organize the numerous photos I've taken both over the years and on the trip in one place, on one computer (which I will back up regularly, of course). I had tried doing this once before under Ubuntu 10.04, but then Gnome decided to switch from Fspot to Shotwell, wiping out my carefully-organized tags.

I'm looking for a (somewhat) future-proof solution of tagging and organizing photos that will survive switching platforms and application deprecation. Maybe one doesn't exist and I need to content myself to folder hierarchies. Maybe I'll try to write a web-based system for personal use.

I've considered cloud-based solutions such as Google+, Picasa Web Albums, Facebook, etc. but I'm concerned how easy it would be to pull everything back down or switch platforms, and there's always the possibility a company could fold or change their policies (Instagram, anyone?).

---

### Post by sudodus on 2013-02-17
> **Potters Son said:**
> After getting back from my first trip abroad, I decided I was going to consolidate and organize the numerous photos I've taken both over the years and on the trip in one place, on one computer (which I will back up regularly, of course). I had tried doing this once before under Ubuntu 10.04, but then Gnome decided to switch from Fspot to Shotwell, wiping out my carefully-organized tags.

F-spot is still available (I have it in 12.04 to make the transition easy.)
```
sudo apt-get install f-spot
```
> 
I'm looking for a (somewhat) future-proof solution of tagging and organizing photos that will survive switching platforms and application deprecation. Maybe one doesn't exist and I need to content myself to folder hierarchies. Maybe I'll try to write a web-based system for personal use.

I've considered cloud-based solutions such as Google+, Picasa Web Albums, Facebook, etc. but I'm concerned how easy it would be to pull everything back down or switch platforms, and there's always the possibility a company could fold or change their policies (Instagram, anyone?).
But I think DigiKam (from KDE but fully functional in Unity, XFCE or LXDE) is much more mature and advanced. So I use that now, and I hope it will continue to be supported in the future.
```
sudo apt-get install digikam
```
It will bring a lot of KDE libraries, but they will not interfere with the execution of other programs. They will only occupy disk space.

---

### Post by eric-yorba on 2013-02-18
> **Potters Son said:**
> I'm looking for a (somewhat) future-proof solution of tagging and organizing photos that will survive switching platforms and application deprecation.

Almost every photo manager -- F-Spot and Shotwell included -- has an option to write tags and other metadata to the photo's EXIF fields.  (Keep in mind this will work for JPEGs but not RAW photos.)

This way you'll never have to worry about losing tags when you switch photo managers.  Now that said, keep in mind you are modifying the original files, so strictly speaking it's not a non-destructive process.

---

### Post by tgalati4 on 2013-02-18
You might consider running your own instance of:

[http://galleryproject.org/](http://galleryproject.org/)

That way your phones, tablets, notebooks, laptops, ultrabooks, desktops, and workstations can access your photos.  Cloud services (like real clouds) have a tendency to float away.

---

### Post by PhilGil on 2013-02-18
As others have mentioned, be sure you enable the option to write metadata to the images. If you shoot exclusively in RAW, extract low resolution reference jpegs that you can tag.

DigiKam is by far the best open source photo management software I have ever used. It handles my photo library (containing tens of thousands of images) without a hiccup, search is remarkably fast and the editing tools are surpassed only by GIMP. The other great feature of DigiKam is that your tags and captions are written to both XMP and IPTC metadata fields, so they are readable by almost any other photo organization software that reads jpeg metadata.

---

### Post by aspergerian on 2013-02-18
> **PhilGil said:**
> DigiKam is by far the best open source photo management software I have ever used. It handles my photo library (containing tens of thousands of images) without a hiccup, search is remarkably fast and the editing tools are surpassed only by GIMP.

I have PS CS5 on my w7 computers, have worked w and agaith GIMP now and again, and have used DigiKam a bit less. I really like DigiKam. Might you name some specific editing features GIMP has that DigiKam doesn't?

---

### Post by PhilGil on 2013-02-18
> **aspergerian said:**
> I have PS CS5 on my w7 computers, have worked w and agaith GIMP now and again, and have used DigiKam a bit less. I really like DigiKam. Might you name some specific editing features GIMP has that DigiKam doesn't?

Disclaimer: I no way am I dismissing DigiKam, which is an extremely impressive program and representative of the best that Open Source has to offer. 

For my own editing habits, the most significant feature I miss in DigiKam are layers, which I use for every photo I post-process. Also, the extensibility of GIMP (using plugins) means that I can take advantage of a extensive range of special effects scripts, B&W conversion scripts and sharpening/refocusing algorithms.

I also don't care for the defaults DigiKam uses for RAW conversions. I shoot RAW+JPG and like to start my RAW conversions with an image that is close to an out of camera JPEG as possible. DigiKam's are not. To be fair, I don't really care for the gimp-ufraw plugin, either - my favorite RAW converter is RawTherapee.

In my opinion, DigiKam is fine for "quick and dirty" post processing, but any jobs that require finer-grained control go to GIMP.

---

