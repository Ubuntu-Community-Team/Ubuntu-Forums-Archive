---
title: "jpg ?"
date: 2005-02-19
forum: The Cafe
---

### Post by ThePainter on 2005-02-19
Hi,
I have several jpgs that were created with Gimp and I can handle them OK in all the image viewer no probs but  I have (for the first time in linux) plugged my digi camera in and imported a load of jpgs but nothing will open them without crashing ?
They show up in nautilus OK as thumbnails but if I try to view them in one of the image viewers they error with "had to unexpectedly close" and if I try to right click them then Nautilus does the same.
I tried to open one in Gimp and it said there was no plugin to handle that file.
Ive tried them in the original Kernel that came with UBUNTU and the new one that synaptic has just loaded in the upgrade.
The funny thing is I have CrossOver Office with Office XP loaded and I can insert these files as pictures no problem.
And they work OK in XP.
Any ideas why XP can handle a .jpg photo and Linux cant ?

---

### Post by kassetra on 2005-02-19
First: make sure that you have libgphoto2 installed
 Second: you may want to install gtkam in order to work with your camera files correctly.
 
 If your camera is not supported by libgphoto2, then you could have some issues with the files that it produces... so you might want to check the list of cameras libgphoto2 supports: [current stable support list]("http://gphoto.org/proj/libgphoto2/support.php")
 
 Also remember that jpgs from a digital camera are actually a somewhat non-standard jpg+exif configuration, and can have issues if not downloaded properly from the camera.

---

### Post by ThePainter on 2005-02-19
Hi,
Ok they are all installed and they still wont open.
I guess thats another trip Ill have to make back into XP.
The pile of jobs I am having to return to XP to do is getting bigger and bigger !
Soon Ill be spending more time there than here and Ill be wondering why Ive got Linux installed at all ?
Im starting to think that a virus scan, and update and a defrag once a week might be less bother than trying to find ways to do simple jobs in linux.

Im losing faith quickly ?  :mad:

---

### Post by kassetra on 2005-02-19
[QUOTE=ThePainter]
 Im starting to think that a virus scan, and update and a defrag once a week might be less bother than trying to find ways to do simple jobs in linux.[/QUOTE]
 
 First of all, remember that the only reason that things seem so trivial in windows is because they have the power to essentially force products into compliance -- with linux, mostly volunteer people shed blood, sweat, and tears to make things work because many times the information needed to work with a piece of hardware or software is not available to developers outside of the microsoft circle.
 
 Also, I have no idea what kind of camera you have, and what exactly happens when you try to view or edit photos...  Have you tried running the gphoto2 command line app to view/edit your photos?  Have you tried gthumb to view them instead of nautilus?  And have you checked to see if your camera is in the list supported by gphoto?  
 
 Lastly, have you searched on the net for your camera and linux?  If it didn't work in windows, what would you do?

---

### Post by ezeze5000 on 2005-02-19
I use A Kodak camera, and a lot of windows photo programs can't read the files in the native Kodak format, So I use the Kodak editor and resave them as a JPG.

Then I don't have a problem with them anymore.

I have one of my kids that I like to use as a wallpaper on my desktop that I fixed 
this way.

I have it on my Ubuntu Machine right now!

I have them all in a windows shared folder on my home network for easy access, with Ubuntu.

---

### Post by ThePainter on 2005-02-22
Hi,
I would like to appoligise for not appreciating the hard work done by the Authors of Linux.
Ok Ive found a work around.
Ive installed Paintshop Pro 7 which works (minimally) in Crossover Office, I can use batch convert to convert the pics back into their own format, because for some reason when the program opens and resaves the pics it must strip the EXIF stuff and I can open them Ok after that.
I know its a bit unconventional but it works.
Its a shame my scanner driver or VDub & TMPgenc dont work through a wine system or I would never need XP again  :-?

---

### Post by paretooptimum on 2005-03-31
I was having a slightly different problem, but I thought my solution might give you some ideas.

I was taking photos off my camera on Ubuntu but unable to open them on my networked windows box.

phptp.jpg > right click > properties > permissions > group & other > read write

Then it worked fine. Just thought this might help. Still need to figure out how to set this by default for all created photos?(rather than right clicking) Anyone?

---

### Post by ThePainter on 2005-03-31
Hi,
No that wasnt my problem, it was something about Ubuntu couldnt handle the exif from my camera.
I was adivised to install a few lib's but they didnt work.
Im in Mepis now and that has no problem with them.

You could use the command line to set the permissions of the files.

chmod 777 -R Pictures

This would set all the files and folders within the directory called "Pictures" so everyone can do anything with them.
The number controls the permissions.
first figure is - User
second is - group
third is - Others

You calculate them by adding up:
Read - 4
Write - 2
Execute - 1
No permission - 0

So 700 would allow you to do anything and no one else can touch them.
444 - would allow everyone to read but not edit.
And so on.

Experiment with it and check the permissions from the right click to see what is happening.

There are more things you can do with this command but this is all I use it for.

You can change owner with:
chown yourname _R Pictures

Obvioulsly you put a name where yourname is.
If your stealing from root make sure you sudo first.

Good luck and have fun  :-)

---

### Post by poofyhairguy on 2005-03-31
Have yall ever tried Digikam for Kodak cameras? I use it, and it works great!

---

