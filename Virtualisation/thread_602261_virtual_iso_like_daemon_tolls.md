---
title: "virtual iso like daemon tolls"
date: 2007-11-04
forum: Virtualisation
---

### Post by enchesss on 2007-11-04
I need to mount an nrg (nero iso) image. Is it possible to use Daemon tools with ubuntu? It works well in windows.

---

### Post by jinx099 on 2007-11-04
try this

```

mount -o loop youriso.iso

```

---

### Post by Rhubarb on 2007-11-04
You can only mount iso files in linux (not nrg files).
You'll first need to convert the nrg image into an iso image.
```
sudo aptitude install nrg2iso
```

Then to convert the nrg, put the nrg file in your home folder, and type this in:
```
nrg2iso name_of_image.nrg
```

This will give you an ISO, from there you can mount it as jinx099 says.

---

### Post by enchesss on 2007-11-05
thanks for the help - the conversion worked without a hitch even though i needed to be more specific with the output file name

but

when i try to mount using these instructions i get

en@enGUTSY1:~$ mount -o loop myisofile.iso
mount: only root can do that
en@enGUTSY1:~$ sudo su
root@enGUTSY1:/home/en# mount -o loop myisofile.iso
mount: can't find myisofile.iso in /etc/fstab or /etc/mtab
root@enGUTSY1:/home/en# mount -o loop -t myisofile.iso /en/Desktop
usage message...

question is:

do i type the iso file name into /ect/fstab?

have searched around and found a few scripts but again - i cant find my scripts dir to put one of them and the other does not work.

---

### Post by enchesss on 2007-11-05
Thanks again

I have finally mounted the image on the desktop.

Some much easier instructions can be found here:

[http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html]("http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html")

But because it is a windows exe program i now cant run it.

I have tried to use wine but cant run the file

when i double click on the exe install file in wine it says that there is no application able to run it.

what is doing?

---

### Post by snkmad on 2007-11-05
Im using Ultra ISO to convert cd images to iso, using wine.
Working great.

---

### Post by MRiGnS on 2007-11-05
AcetonISO, native Linux app, for kde, but there is a gnome port, if you don't like to install kdelibs.

[http://www.acetoneteam.org/central.html](http://www.acetoneteam.org/central.html)


- Mount automatically ISO, MDF, NRG, BIN, NRG
- A nice interactive display
- Convert2iso / Extract2folder :
  *.bin *.mdf *.nrg *.img *.daa *.cdi *.b5i *.bwi *.pdi and much more
- Play a DVD Movie Image inside Kaffeine / VLC with cover downloader
- Generate an ISO from a Folder or CD/DVD
- Generate / Check MD5 file of an image
- Encrypt / Decrypt an image
- Split / Merge image in X megabyte
- Compress with High Ratio an image in 7z format
- Rip a PSX cd to *.bin to make it work with epsxe/psx emulators
- Restore a lost CUE file of *.bin *.img
- Convert Mac OS *.dmg to a mountable image
- El-Torito support to create ISO bootable Cd
- Mount an image in a specified folder from the user
- Create a database of images
- Extract the Boot Image of a CD/DVD or ISO

---

### Post by leach on 2007-11-06
Nice :D

AcetonISO is exactly the type of program I've been looking for and more thanks for the link.

---

