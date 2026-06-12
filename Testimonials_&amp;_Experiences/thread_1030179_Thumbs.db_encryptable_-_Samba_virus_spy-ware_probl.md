---
title: "Thumbs.db: encryptable - Samba virus spy-ware problem? No, Ubuntu."
date: 2009-01-04
forum: Testimonials &amp; Experiences
---

### Post by Pierpaolo Cellini on 2009-01-04
Some feature of the system itself or some particular application, I only suppose so, that I was not able to identify, insert in folders with images on ntfs volumes, these files empty, in the name similar to those that contain thumbnails of images, but that, using the illegal ":" colon, make impossible to Windows normal operations on files and folders that contain them. Copy transfer erase.

Not speaking about Thumbs.db, that are the usual hidden files in Windows, containing the database of previews "thumbs", but about other files generated perhaps by one of the graphics programs based on Ubuntu or perhaps by browser Nautilus itself when it generates its previews, which opening the folders that contain images, and where there is contemporaneously also a legal file Thumbs.db produce a new file. 
With the new twin exact name of the ADS meta data "alternate data streams" present in all Thumbs.db.
Exactly “thumbs.db: encryptable” that does not contain the correct data, it is always just a vacuum, but they had a colon ":"  that is notoriously illegal character for a  file name in ntfs.

This problem occurs
           tune2fs with-o journal_data_writeback    -almost constantly
    and tune2fs-o journal_data
       or tune2fs-o journal_data_ordered    -unpredictable randomly

I have made many tests being careful not to introduce other elements of disturbance.
For the little that I understand of course.
 
Anyone who has installed the two systems together, honestly can redo the test of what I say.

Moreover, are not undeletable. It's not, that they are not easily erasable by widows, they are indelible. Like any other files that have illegal characters in the name.
If one writes a text, and called him: "Why have you left me?" Is his fault, but these files thrusts alone in a lot of places that a lack remembers.
Certainly it's easy to find and delete them from Ubuntu, but then must close and restart the session without doing anything, if not the next time someone will always check out.

This little thing makes impossible the coexistence of Ubuntu with Windows. I had to choose to delete the partition containing Ubuntu on my laptop and, forced by a “Immediately remove this garbage from my computer!”, on those of the entire family, I believe first full of enthusiasm, with some regret, but we use photoshop, adina, MathLAB, autocad, excel, and other things, to we bought a license, we have learned to use and do not have substitutes minimally adequate.

Even in the past had different times and for various Linux distributions to install on the handset to work with Ubuntu and only the percentage of things that do not work was for the first time acceptable.

On my HP dv7 1139el do not work the digital TV, the microphone with Skype for audio and I had to add to / etc / modprobe.d / alsa-base line: options snd-hda-intel model = laptop single_cmd = 1 enable_msi = 1, which is a poor piece.

I must say that there would be even more tested on linux, if I had not found these three free programs:

1 EasyBCD 1.7.2 to [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)
that allows you to use standard windows bootloader and add a module called neogrub that communicates with the mbr of Ubuntu installed and confined according to the caution in its own partition root.

2 driver which is [http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)
that allows you to permanently mount ext3 partitions in reading and writing, copy and edit what you want in perfect safety.

3 SelfImage a [http://selfimage.excelcia.org/](http://selfimage.excelcia.org/)
3 minutes in which the copy 5GB of data in the Ubuntu partition of 20 GB on a file. img of 2.5 GB and in three minutes it back on the partition of origin completely overwritten sector by sector.

Without taking by two copies of all the partition of Ubuntu in its stages of progress, I would not be ever able to get on top of false hardware errors like this:
usb xx: device not accepting address xx, error -71
then disappear overnight with the restore operation.

Regards
Pierpaolo Cellini
  [email]pierpaolo_cellini@libero.it[/email]

---

### Post by albinootje on 2009-01-04
> **Pierpaolo Cellini said:**
> 

On my HP dv7 1139el do not work the digital TV, the microphone with Skype for audio and I had to add to / etc / modprobe.d / alsa-base line: options snd-hda-intel model = laptop single_cmd = 1 enable_msi = 1, which is a poor piece.

I assume that you've of course phoned this HP company asking them why there was only a MS-Windows cdrom that came with your laptop, containing no instructions or support whatsoever for Linux ?

---

### Post by Pierpaolo Cellini on 2009-01-04
> **albinootje said:**
> I assume that you've of course phoned this HP company asking them why there was only a MS-Windows cdrom that came with your laptop, containing no instructions or support whatsoever for Linux ?
I am Italian, and, like italian generally assume that a company behaves in a manner oppressive and unreasonable. The HP company does not support even Windows xp on my laptop, I wonder Canonical, that is so weaker,  not worry about living with Microsoft, respecting the system of metadata on ntfs. You seems to me an idealist and unreasonable supporter of linux

---

### Post by albinootje on 2009-01-04
> **Pierpaolo Cellini said:**
> I am Italian, and, like italian generally assume that a company behaves in a manner oppressive and unreasonable. The HP company does not support even Windows xp on my laptop, I wonder Canonical, that is so weaker,  not worry about living with Microsoft, respecting the system of metadata on ntfs. You seems to me an idealist and unreasonable supporter of linux

If you look at my comment, and the text in my comment from your posting that I've quoted, you can see that I responded about the hardware and software support from Ubuntu concerning your laptop.

My comment was not referring at all about your NTFS-problems.

For the rest was my comment trying to be informative.
Some hardware companies are trying to support Linux the best they can, however the situation for Linux is still far from perfect, especially when it comes to power-management on laptops.
My proposal was simply to indicate that Linux is not the only thing you can blame for the hardware support problems you had.

If you want the easiest and most well-known used computer worldwide, buy a Mac.

Have a nice day.

---

