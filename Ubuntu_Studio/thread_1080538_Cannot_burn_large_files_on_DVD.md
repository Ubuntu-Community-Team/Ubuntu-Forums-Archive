---
title: "Cannot burn large files on DVD"
date: 2009-02-25
forum: Ubuntu Studio
---

### Post by Stason on 2009-02-25
Tried Brasero, Gnomebaker, Gravesomething - they all leave a lot of unused space or refuse to burn large files (i.e. 4.4Gb). All of this is successfully done by Nero under Windows. This is why it is still on my dual boot.:mad:

Help, what am I doing wrong?

---

### Post by taurus on 2009-02-25
What are those files that you try to burn to a DVD?  I assume the total amount is less than/equal 4.4GB.

---

### Post by Stason on 2009-02-25
> **taurus said:**
> What are those files that you try to burn to a DVD?  I assume the total amount is less than/equal 4.4GB.

It is slightly less than 4.4. Does it matter which files are these? Nero under Windows does not seem to care. It's hidef MKV movies.

---

### Post by taurus on 2009-02-25
Are you trying to burn those movies to your DVD so you could play them on your standalone DVD player?

You shouldn't have any problem burning them to a DVD as data files, the way they are, but afraid some players can't read/play them.

---

### Post by binbash on 2009-02-25
I burned around 30 dvds today with both nero linux and brasero today.(4.5gb).If you have nero on windows, this means you have licensed nero, this means you can also use nero linux with that key on linux.

Anyways, at nero or brasero do not select iso , select udf if you have mkv files.

---

### Post by Stason on 2009-02-26
> **taurus said:**
> Are you trying to burn those movies to your DVD so you could play them on your standalone DVD player?

You shouldn't have any problem burning them to a DVD as data files, the way they are, but afraid some players can't read/play them.

I am basically making a backup. I do not even have a standalone DVD player. And yes, I do have problems burning large files and may small files. I think I cannot burn more than 3,5Gb of small files on a 4,7Gb DVD under Linux for some reason. I am trying to find out why, since in Windows I can burn up to 4.4Gb of data quite easily.

---

### Post by taurus on 2009-02-26
Maybe give k3b a try.

What is the error message when you try to burn something large to your DVD?

---

### Post by kayosiii on 2009-02-26
If I remember correctly you can't burn disks over 2gb without enabling UDF. You should hunt in your burning application for this setting. K3B definitely has it.

---

### Post by Stason on 2009-02-26
I use Gnome. I understand that K3B is for KDE.

I have NEC ND1300A and I am trying to burn a 4.37Gb file to a DVD+R disk. 

Here is what I get in Gnomebaker

> Executing 'genisoimage -gui -V GnomeBaker data disk -A GnomeBaker -p Stason -iso-level 3 -l -r -hide-rr-moved -J -joliet-long -graft-points --path-list /tmp/GnomeBaker-stasulos/gnomebaker-L0G1PU | builtin_dd of=/dev/hda obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
File /media/deus/Movies/Movie.1992.720p.BluRay.x264.mkv is larger than 4GiB-1.
-allow-limited-size was not specified. There is no way do represent this file size. Aborting.
:-( write failed: Input/output error

Graveman just does not add the file to burning list at all.

---

### Post by Stason on 2009-02-26
Here is what Brasero says:

> imager (BraseroLocalImage) set_output
job (BraseroLocalImage) set_task
imager (BraseroLocalImage) get_track
job (BraseroLocalImage) set_task
Session starting:
	flags			= 8563 
	media type	= 0
	speed		= 3
	track type		= 6
	track format	= 3
	output		= none
job (BraseroGrowisofs) set_source
imager (BraseroGrowisofs) set_output_type
recorder (BraseroGrowisofs) set_drive
imager (BraseroGrowisofs) set_output
imager (BraseroGrowisofs) unsupported operation (in brasero_imager_set_output at burn-imager.c:142)
job (BraseroGrowisofs) set_task
imager (BraseroGrowisofs) get_size
process (BraseroGrowisofs) getting varg
growisofs (BraseroGrowisofs) set_action
process (BraseroGrowisofs) got varg:
	growisofs
	-use-the-force-luke=notray
	-dvd-compat
	-use-the-force-luke=tty
	-Z
	/dev/hda
	-dry-run
	-r
	-J
	-input-charset
	utf8
	-graft-points
	-D
	-path-list
	/tmp/brasero_tmp_q2SgxL/brasero_tmp_85Z9PU
	-exclude-list
	/tmp/brasero_tmp_q2SgxL/brasero_tmp_Y6Z9PU
	-print-size
process (BraseroGrowisofs) launching command
process (BraseroGrowisofs) stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -D -path-list /tmp/brasero_tmp_q2SgxL/brasero_tmp_85Z9PU -exclude-list /tmp/brasero_tmp_q2SgxL/brasero_tmp_Y6Z9PU -print-size | builtin_dd of=/dev/hda obs=32k seek=0'
process (BraseroGrowisofs) stderr: File /media/deus/Movies/Movie.1992.720p.BluRay.x264.mkv is larger than 4GiB-1.
process (BraseroGrowisofs) stderr: -allow-limited-size was not specified. There is no way do represent this file size. Aborting.
process (BraseroGrowisofs) stdout: HUP
process (BraseroGrowisofs) stderr: HUP
job (BraseroGrowisofs) asked to stop
	status	= 0
iter (BraseroGrowisofs) stopping
process (BraseroGrowisofs) got killed
iter (BraseroGrowisofs) stopped
job (BraseroGrowisofs) got out of loop
...
Session error : Unhandled error, aborting

Where do I need to specify the damn -allow-limited-size switch?
And by the way I see no selection between iso and udf in Brasero, nor Gnomebaker.

---

### Post by taurus on 2009-02-26
K3b is KDE but you can still install and use it.  When you install k3b, it will install a bunch of KDE libraries.  I use k3b to do all my burning even though I run Gnome (at home) and XFce4 (Xubuntu in the office).

As they say, the choice is yours.

---

### Post by Stason on 2009-02-27
Are you saying that Linux is so deficient of good dvd burning software? So the only choice for Nero-like operation is K3B at the price of downloading extra 100mb of libraries?

---

### Post by taurus on 2009-02-27
> **Stason said:**
> **Are you saying that Linux is so deficient of good dvd burning software?** So the only choice for Nero-like operation is K3B at the price of downloading extra 100mb of libraries?

I am just telling you what I use and it works for me so you can say or do whatever you want with your machine.

---

### Post by SuperSonic4 on 2009-02-27
> **Stason said:**
> Are you saying that Linux is so deficient of good dvd burning software? So the only choice for Nero-like operation is K3B at the price of downloading extra 100mb of libraries?

> **taurus said:**
> I am just telling you what I use and it works for me so you can say or do whatever you want with your machine.

Nope, just gnome :lolflag:

Seriously, whatever works for you. I've had no problems with K3B either but then it did come preinstalled

---

### Post by Francewhoa on 2009-09-05
Ubuntu includes CD burning capabilities by default, and allows you to easily [create data CDs]("http://library.gnome.org/users/user-guide/stable/nautilus-cdwriter-data.html"), [copy CDs and DVDs]("http://library.gnome.org/users/user-guide/stable/nautilus-cdwriter-copy.html") and [create CDs from a disc image file]("http://library.gnome.org/users/user-guide/stable/nautilus-cdwriter-writeimage.html").

How to burn file bigger than 2GB with Ubuntu 8.04 LTS [http://library.gnome.org/users/user-guide/stable/nautilus-cdwriter-data.html](http://library.gnome.org/users/user-guide/stable/nautilus-cdwriter-data.html)

---

