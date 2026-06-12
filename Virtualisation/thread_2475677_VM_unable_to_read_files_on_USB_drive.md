---
title: "VM unable to read files on USB drive"
date: 2022-06-04
forum: Virtualisation
---

### Post by satimis on 2022-06-04
Hi all,

Host - Ubuntu 20.04
VM - Ubuntu 22.04
Oracle VirtualBox

USB drive - Samsung Galaxy mobile phone

Host can read/download files on mobile phone.  

VM
USB drive has been forward to VM.  It is mounted but unable to read its content.  Its folder is empty.

Right-click the empty folder -> Properties -> Permissions

Warning```

The permissions of "SAMSUNG_SAMSUNG_Android_.......(mtp)" could not be determined

```

What is "mtp"

Please help.  Thanks

Regards

---

### Post by TheFu on 2022-06-04
MTP is an Android file access protocol. It isn't a normal mount.

Use a network protocol instead or setup a USB passthru from the Android device directly into the VM.  I use sftp. There are sftp clients for Android. There are also sshd servers for android, though they aren't usually fully patched for security issues.
Of course, you could use a file sharing server as an intermediary like nextcloud. I use that sometimes too. The Android NC client is pretty good. The Linux NC client access methods sorta suck. They are dependent on WebDAV which has a terrible implementation.  I use it, but it is probably 20x slower than any other protocols like sftp, scp, rsync, ... sshfs ... everything.  WebDAV is just terrible.

---

### Post by ajgreeny on 2022-06-04
Alternatively you may simply need to go to ***Settings -> Connected Devices*** in the phone and choose to allow file transfer, or however it's described.

For the very few times I need to do this I use an Android app called **WiFi File Transfer** though I use it only to move files (photos) from phone to computer; I don't think you can do the moves in the other direction, ie, to the phone; never tried so it may be possible.

---

### Post by satimis on 2022-06-04
Hi all,

Thanks for your advice.

It is very strange to me.  I can remote-control the desktop of my mobile phone but unable to download its files

On mobile phone, under Developer Options
USB Debugging On

On VM
scrcpy has been installed

Host - Mobile phone connected and its files can be read and download

VM - Mobile phone also connected but its folder is empty
Right-click its empty folder -> Permissions
Warning;```
 
The permission fo "Satimis's Galaxy S9+" could not be determined

```

Again

On VM VirtualBox meun bar
Devices -> USB -> (check) Samsung Android [0C00]

On VM desktop -> right click Samsung Android icon -> mount 

On VM terminal run;
$ scrcpy

Then I can remote-control the mobile phone desktop.  But clicking mobile phone icon on VM desktop starts the warning (pls refer to screenshot)

Neither I can drag-n-drop files from mobile phone desktop to VM desktop

Suggestion would be appreciated.  Thanks

Regards

---

### Post by satimis on 2022-06-05
> **ajgreeny said:**
> Alternatively you may simply need to go to ***Settings -> Connected Devices*** in the phone and choose to allow file transfer, or however it's described.

For the very few times I need to do this I use an Android app called **WiFi File Transfer** though I use it only to move files (photos) from phone to computer; I don't think you can do the moves in the other direction, ie, to the phone; never tried so it may be possible.
That is exactly what I'm planning to do.

I use the mobile phone to scan film negatives.  Shooting is remotely controlled on 22.04 desktop VM.  I expect to save the scanned negatives images direct to Ubuntu 22.04 desktop VM, instead of saved on the phone. Then moved the saved negatives images from Gallery to Ubuntu 22.04 VM.  I need to save the scanned negative images direct to the VM, for post-editing, because some filter plugins of GIMP unable to run on Ubuntu 20.04 desktop, the Host.

Besides is there any way marking the serial numbers assigned to each shooting according to my way of marking, not allotted by the phone automatically.  I can do it on the images after shooting but it'll take tedious time treading hundreds of images.

Regards

---

### Post by TheFu on 2022-06-05
> **satimis said:**
>  
Besides is there any way marking the serial numbers assigned to each shooting according to my way of marking, not allotted by the phone automatically.  I can do it on the images after shooting but it'll take tedious time treading hundreds of images.


I use a script to **rename** images, then group them together by subject and use **geeqie**'s multiple-rename to add text.  I go out of my way to keep the photos in order per event/date, since having a slideshow in order tells a different story than a slide show based just on content.  Also, I try not to 100% trust the EXIF, so I want the most important aspects of metadata about any photo to be captured in the directory and file name.  I've been burned before by 'photo management software' screwing all sorts of things up. Never again.

---

### Post by satimis on 2022-06-05
> **TheFu said:**
> I use a script to **rename** images, then group them together by subject and use **geeqie**'s multiple-rename to add text.  I go out of my way to keep the photos in order per event/date, since having a slideshow in order tells a different story than a slide show based just on content.  Also, I try not to 100% trust the EXIF, so I want the most important aspects of metadata about any photo to be captured in the directory and file name.  I've been burned before by 'photo management software' screwing all sorts of things up. Never again.
Thanks for your advice.

I have no problem renaming the photos, adding description etc. But all such works are done in post editing.

When we shoot photos, the mobile phone (In my case Samsung Galaxy S9+) will assign each photo a serial number, such as;
20220321_162831.jpg
20220604_170424.jpg
20220604_170655.jpg
20220604_171718.jpg
........
etc.

The front 20220321 is the date of shooting.  But on scanning film negatives I don't need the date.  I expect naming it in my way such as:-
AA_01.jpg
AA_02.jpg
AA_03.jpg
...
etc.

AA is the number labelled by me on the folder pad holding the negatives

Next folder pads
AB_01.jpg
AC_01.jpg
..
..
AZ_01.jpg

Then
BA_01.jpg
BB_01.jpg
BC_01.jpg
..

Then
CA_01.jpg
CB_01.jpg
CC_01.jpg
..
etc.

In this way I know the negative images coming from which folder pad.

How can I set them on mobile phone?

Regards

---

### Post by TheFu on 2022-06-05
> **satimis said:**
>  
How can I set them on mobile phone?

That's a question for Android people.  I'd use sshfs from a Linux system, if I wasn't happy about moving them over immediately, which is what I do. I don't keep photos taken on the phone in the phone.  I pull them off ASAP, do the initial renaming, delete as many as possible, as soon as possible, do processing, then put them into the central gallery before the nightly backups get started.

After all that, if I want the photos on the phone, then I can pull them back to the external microSD "Photos/{yyyy}/{mm}-{Event}/ structure.  I only have about 100 photos there. My tablet has all the "best" photos, while the gallery has all that weren't deleted and that gallery is my "system of record".  If the phones or tablets die, I've lost nothing.

---

### Post by satimis on 2022-06-05
> **TheFu said:**
> That's a question for Android people.  I'd use sshfs from a Linux system, if I wasn't happy about moving them over immediately, which is what I do. I don't keep photos taken on the phone in the phone.  I pull them off ASAP, do the initial renaming, delete as many as possible, as soon as possible, do processing, then put them into the central gallery before the nightly backups get started.

After all that, if I want the photos on the phone, then I can pull them back to the external microSD "Photos/{yyyy}/{mm}-{Event}/ structure.  I only have about 100 photos there. My tablet has all the "best" photos, while the gallery has all that weren't deleted and that gallery is my "system of record".  If the phones or tablets die, I've lost nothing.
Do you know where is Samsung S9/S9+ official forum ?

I won't retain the scanned negative images on phone.  I would download all of them to Ubuntu 22.04 VM after finishing scanning negatives in 1 or 2 folder pads.  Then I'll run batch editing converting all negative images to positives images.  ImageMagick is my target software for graphic editing in command line and in batch.

Now I have 2 desktops running side-by-side, Galaxy S9+ phone and Ubuntu 22.04 desktop VM.  How can I download files from the former to the latter?  Preferably by drag-n-drop ?

Edit
==
There are other 4 command-line graphics tools for Linux, similar to ImageMagick;

1. GraphicsMagick Image Processing System
[http://www.graphicsmagick.org/](http://www.graphicsmagick.org/)
2. Scrot: Linux command-line screen grabs made simple
[https://opensource.com/article/17/11/taking-screen-captures-linux-command-line-scrot](https://opensource.com/article/17/11/taking-screen-captures-linux-command-line-scrot)
3. Feh
[https://feh.finalrewind.org/](https://feh.finalrewind.org/)
4. Exiv2
[https://exiv2.org/](https://exiv2.org/)

Do you have experience running them?  Please shed me some light.

---

