---
title: "DVD burning"
date: 2008-08-15
forum: Ubuntu Studio
---

### Post by Rohbart on 2008-08-15
Hi,
I tried to burn a dvd from drive to hard disc by doing the following:

> 

Install dvdbackup from the repository.

Then insert your DVD movie in the drive and type this in the terminal:

dvdbackup -i /dev/dvd -M -o dir/

This will backup the whole DVD movie with extras and menus, etc. You might want to have a Dual layer burner for this too. It will put the backup in the directory that you put in place of dir/. example: dvdbackup -i /dev/dvd -M -o backupmovie/

After it finishes this then insert your blank DVD disc into the drive and type from terminal:

growisofs -speed 1 -dvd-compat -Z /dev/dvdrw -dvd-video dir/

example using the backupmovie/ directory that contained my backup would be:
growisofs -speed 1 -dvd-compat -Z /dev/dvdrw -dvd-video backupmovie/

The dvdbackup command will put into the backupmovie/ subdirectory the disc title of the movie. So be sure to include that at the end of the growisofs command. Such as:
growisofs -speed 1 -dvd-compat -Z /dev/dvdrw -dvd-video backupmovie/GHOST/

This works great, and I can backup my DVD movies with way even dual layer movies.
at the end of the ripping process backupmovie says: libdvdread: check_value failed.
And while ripping there are often errors while reading the dvd.
What can I do to watch the movie from my harddisc?

---

