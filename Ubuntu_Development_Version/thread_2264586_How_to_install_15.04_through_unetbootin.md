---
title: "How to install 15.04 through unetbootin?"
date: 2015-02-08
forum: Ubuntu Development Version
---

### Post by NunoLava1998 on 2015-02-08
So im trying to install ubuntu 15.04 through unetbootin. What is the option? Is it Daily?

EDIT: Solved, i used mkusb and i got to the setup, the only bug is when i clicked restart it gave me a black screen, power off would not work, force shutdown worked, stopped force shutdown and booted into a black screen again, but after 2 minutes it finally loaded the login screen, My usb instead of saying "SEM NOME" now says "Ubuntu 15.04 amd64", Requesting solved tag.

---

### Post by sudodus on 2015-02-08
You are welcome to try 15.04 and help us iso-test it. Be prepared that  it may break a few times before the release date in April! And please report your results via the [testing tracker]("http://iso.qa.ubuntu.com/") and bugs to [Launchpad]("http://launchpad.net/").

Yes, start by downloading the daily build, and check the md5sum. You may want to use ***zsync***, particularly if you want to download several daily images.

If Unetbootin works, fine, otherwise you should try [mkusb]("https://help.ubuntu.com/community/mkusb") (from linux) or [Win32 Disk Imager]("https://wiki.ubuntu.com/Win32DiskImager/iso2usb") (from Windows). Sometimes there are problems with a tool like Unetbootin with new versions (particularly before they are released).

---

### Post by NunoLava1998 on 2015-02-08
After doing, unetbootin gets messed up. Everything is fine, but if i try i get a error reading a file, i tried a second iso, same thing, tried to install ubuntu 14.04.1 exactly as i did in linux mint and i get the same error. i can get out of there by doing ctrl+alt+delete which reboots the system.

---

### Post by NunoLava1998 on 2015-02-08
> **sudodus said:**
> You are welcome to try 15.04 and help us iso-test it. Be prepared that  it may break a few times before the release date in April! And please report your results via the [testing tracker]("http://iso.qa.ubuntu.com/") and bugs to [Launchpad]("http://launchpad.net/").

Yes, start by downloading the daily build, and check the md5sum. You may want to use ***zsync***, particularly if you want to download several daily images.

If Unetbootin works, fine, otherwise you should try [mkusb]("https://help.ubuntu.com/community/mkusb") (from linux) or [Win32 Disk Imager]("https://wiki.ubuntu.com/Win32DiskImager/iso2usb") (from Windows). Sometimes there are problems with a tool like Unetbootin with new versions (particularly before they are released).

(sorry for the post above, didnt read the end.)
Where i download mkusb? Software center says that there is no mkusb, Also, does mkusb support pen drives/pen usb's? I dont use win32 disk images beacuse it is for windows and im running ubuntu.

---

### Post by sudodus on 2015-02-08
I think it is easiest to install it via the PPA described in this link

[URL="https://help.ubuntu.com/community/mkusb"]https://help.ubuntu.com/community/mkusb

[/URL]```
sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb
```

[URL="https://help.ubuntu.com/community/mkusb"]
[/URL]

---

### Post by sudodus on 2015-02-08
Using standard Ubuntu you may want to enable the repository **universe** too:

Run this command line in a terminal window or text screen (if you run mkusb in the Ubuntu version 14.04 LTS or newer)

```
sudo add-apt-repository universe
```will 'enable the **universe** distribution component for all sources', in other words 'install' or make available the repository **universe** and make the tool ***pv*** available for installation.

---

### Post by Elfy on 2015-02-08
> **NunoLava1998 said:**
> After doing, unetbootin gets messed up. Everything is fine, but if i try i get a error reading a file, i tried a second iso, same thing, tried to install ubuntu 14.04.1 exactly as i did in linux mint and i get the same error. i can get out of there by doing ctrl+alt+delete which reboots the system.

What error? 

If it's com32 then it's known about. 

Press tab - then unetbootindefault will get you to the desktop - unless of course you get this [http://ubuntuforums.org/showthread.php?t=2262798](http://ubuntuforums.org/showthread.php?t=2262798)

---

### Post by NunoLava1998 on 2015-02-08
Elfy:
Its a error loading COM32.

---

### Post by NunoLava1998 on 2015-02-08
> **sudodus said:**
> I think it is easiest to install it via the PPA described in this link

[URL="https://help.ubuntu.com/community/mkusb"]https://help.ubuntu.com/community/mkusb

[/URL]```
sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb
```

[URL="https://help.ubuntu.com/community/mkusb"]
[/URL]

Already installed some time ago. Im gonna download iso tommorow beacuse my cores are heating up to 70-80c, and that is not healthy.

---

### Post by sudodus on 2015-02-08
> **NunoLava1998 said:**
> Elfy:
Its a error loading COM32.

> **NunoLava1998 said:**
> Already installed [mkusb] some time ago. Im gonna download iso tommorow beacuse my cores are heating up to 70-80c, and that is not healthy.

So now you have two tools that are likely to work in order to make a USB boot drive :-)

---

### Post by sudodus on 2015-02-08
> **NunoLava1998 said:**
> Already installed some time ago. Im gonna download iso tommorow beacuse my cores are heating up to 70-80c, and that is not healthy.

Have you checked other possible causes for the heat: a fan that stopped working, dust inside the computer, a process the loads the CPU constantly?

---

### Post by NunoLava1998 on 2015-02-08
> **sudodus said:**
> Have you checked other possible causes for the heat: a fan that stopped working, dust inside the computer, a process the loads the CPU constantly?

Im pretty sure its dust. And other problem is fan that stopped working.
SERIOUSLY, I have 4 fans in lm-sensors, 3 of the fans are at 0 RPM (not working)
the other 1 fan never reaches 2000 RPM and never goes below 1250 RPM.

---

### Post by sudodus on 2015-02-09
Maybe it is a good idea to blow the dust away and replace the bad fans now :-)

---

### Post by NunoLava1998 on 2015-02-10
Another error was that unetbootin was messing up the ubuntu font.

---

### Post by sudodus on 2015-02-10
> **NunoLava1998 said:**
> Another error was that unetbootin was messing up the ubuntu font.

I don't understand how that could happen. Or are you talking about the boot menu? Unetbootin's boot menu is different from that of Ubuntu, when booted from DVD or via mkusb and the Startup Disk Creator, but when Ubuntu is booted live or installed, its fonts should be independent of Unetbootin.

-o-

How far have you reached now in your attempts to install and try Ubuntu 15.04?

- Have you tried it live? - results?
- Have you installed it? - results?

---

### Post by jerrylamos on 2015-02-10
Well, having test Ubuntu partitions, I just
zsync latest vivid .iso (or any other ubuntu .iso for the last couple years)
Select Files from the unity launcher
navigate to where ever the .iso file is
double left click on it
do a "restore" plugging in a USB drive 
Make sure USB drive is selected and not a hard drive.  You get a couple chances to make sure.
Note, wipes out whatever is on the USB drive
Note: I don't see a way to do a live persistent image.

Has been the most reliable USB bootable image writer I've run over the years.

---

