---
title: "How to: Use Sony NWZ- video walkman with Ubuntu"
date: 2008-07-21
forum: Tutorials
---

### Post by RocksThatFloat on 2008-07-21
Drag and drop loading and unloading of Sony NWZ series (video walkman) on Ubuntu is possible.

It can work on Rhythmbox or Amarok.

I like Amarok better, because you don't need to use terminal every time:
Step 1: Install pmount. Trying step 3 without this installed gave me an easy way to install it. If you do not have pmount installed and do not know how, go to step 2.

Step 2: Connect your Walkman and type in a terminal:
```
ls /dev/disk/by-label -lah
```
This will tell you what your walkman is connected as, mine was sdb1.

Step 3: Type in a terminal:
```
pmount /dev/#yourWalkman# /media/Walkman
```
Mine was
```
pmount /dev/sdb1 /media/Walkman
```

Your walkman should now be mounted in media as Walkman and should appear on your desktop.

Step 4: Open Amarok.

Step 5: Go to settings- configure amarok- media devices- add device.

Step 6: Use these settings:
Plugin=Generic Audio Device
Name=Walkman
Mount Point=/media/Walkman

Step 7: Click the Configure Settings button beside the plugin(three gears) and insert pre-connect and post-disconnect commands:
pre:
```
pmount #yourWalkman# e.g:sdb1 Walkman
``` (where #yourWalkman# is as above)
post:
```
pumount #yourWalkman# e.g:sdb1
```

Step 8: Type in a terminal:
```
pumount #yourWalkman#
``` again where #yourWalkman# is something like sdb1

Step 9: Go back to Amarok and click connect in the devices tab.
If all is good, your walkman should mount and your files should show up.
Then all you need to do is add files to a playlist and drag them over to the MUSIC folder and press transfer.

It took me many hours to get my nwz working and it was a pain. I hope this helps others get it done faster. I couldn't get the nwz working on my mac, but I did on linux... Free Stuff: 1, Paid Stuff: 0.

---

### Post by _dede_ on 2008-08-23
Great tutorial, I have been looking to do that for quite some time.
Altought, I have one question:
Did you manage to transfert playlists into the Walkman as well? Because I can't.

---

### Post by valmorel on 2008-09-08
I came across this thread today and wondered if you had seen this:

[http://kubuntuforums.net/forums/index.php?topic=3096598](http://kubuntuforums.net/forums/index.php?topic=3096598)

It seems there is a bug in Hal (Hardy Heron), and if you follow these instructions, you can fix it. Threafter, just plug in your walkman, and it will automount to an icon on the desktop as a mass storage device, allowing drag and drop etc straight from the computer file system.

I now use Exaile to handle my music library and transfer music as it is so fast compared to Amarok

---

### Post by valmorel on 2008-09-09
Another Way Including Playlists
You can use Gnomad, which is a very fast file manager for MTP players. Plug in you Walkman to the USB port, and start Gnomad. Even if your set up does not recognise the Walkman as a mass storage device, Gnomad will recognise and mount it as an MTP device like Amarok, except that it will autodetect. No need to configure anything. Once Gnomad has been loaded, set up the path to your PC based music in the left hand pane, your player will be the right hand pane, and transfer tracks to your player at will.
Now here is the super-cool part: In the Gnomad window, select the Playlist tab. It will display a totally blank window. Right click in the window, and a context menu will pop up from which you can create a playlist. Create your playlist and switch back to the music transfer window. On the player side, select the tracks (click, shift click, or ctrl click in the usual file manager way), then right click on one of the tracks you have selected. A pop up menu will appear allowing you to add the tracks to your playlist. You can add tracks to multiple playlists.
You can create your playlists before you even transfer music to your device, then, when you transfer tracks, you will be prompted to add the tracks to one or more playlists as you go.
Is that not just the coolest thing...

---

### Post by mellowb on 2008-09-22
Thanks RocksThatFloat, it is a great post. 

However, I still have a problem. After mounting the walkman the /media/Walkman folder looks like:

drwx------  9 root root    32768 1969-12-31 21:00 Walkman

The owner is the root and I don't have access privileges from my account.

If I type sudo nautilus, I am able to open the folder and access its contents. However, I should be able to do it from my account. I tried "sudo chmod 777 Walkman" and "sudo chown my_username Walkman" but these commands doesn't had any effect. 

Do anyone knows what is happening and how to fix it?

---

### Post by milesje on 2008-10-18
try sudo cmod -R 777 /media/Walkman and sudo chown -R my_username /media/Walkman

the -R makes the change recursive down to all files and folders.

---

### Post by Capt_Zaphod on 2009-01-06
Okay ... I had used this successfully a couple times.

Now, my Sony Walkman will no longer connect.

It's mounted, but Amarok won't seem to connect to it.

Any suggestions my friends?

Thank you

---

### Post by osnofla on 2009-05-05
I have a NWZ-S615F Walkman, and this guide worked wonders on Ubuntu 8.04... But now I've upgraded to Jaunty, and it automatically mounts my mp3 player! The problem is that altough it appears to have been mounted, none, NONE of the following media players recognizes it! Rythmbox, Amarok (1.4 nor 2.2) nor Gnomad2.

I've tried many things, such as "ls /dev/disk/by-label -lah", but it doesn't show up. Does anyone have the same problem?

---

### Post by 3rdalbum on 2009-05-06
> **osnofla said:**
> I have a NWZ-S615F Walkman, and this guide worked wonders on Ubuntu 8.04... But now I've upgraded to Jaunty, and it automatically mounts my mp3 player! The problem is that altough it appears to have been mounted, none, NONE of the following media players recognizes it! Rythmbox, Amarok (1.4 nor 2.2) nor Gnomad2.

Should they? The NWZ series are made for drag 'n' drop loading; you don't need to use any music playing programs. I don't remember Rhythmbox picking up my player under Gutsy, Hardy, Intrepid or Jaunty.

---

### Post by osnofla on 2009-05-12
I also tried drag&droping, and I get an error every time I try:

"Hubo un error al copiar el archivo en gphoto2://[usb:001,003]/.
Error al escribir el archivo: -2: Parámetros incorrectos"

Basically, what the first line says is that the file couldn't be copied (by drag&drop), in the path above mentioned, and the second line says that there was an error while trying to write the file, because the arguments were wrong. What bugs me is the path: "[usb:001,003]/", because I can't find it, and none the walkman isn't recognized as a sdb* device.

---

### Post by ez815 on 2009-05-16
same problem here. I'm using a sony nwz-a820 on ubuntu 9.04. when I connected my walkman on the computer, the sony walkman icon automatically appeared on the desktop, which means the device should've already been mounted, however, when i tried ls /dev/disk/by-label lah in terminal, it said directory not exit, and i got this gphoto2 error too...can anyone help?  many thanks here

---

### Post by osnofla on 2009-11-13
Hey guys, I also have a NWZ S615f Sony Walkman, and I tried to use it in Ubuntu 9.04 Jaunty, to no avail. 

However, in 9.10 Karmic, the issue of mounting it has been solved, and it detects it automatically in Rythmbox and Amarok2. However, when I try to upload songs, after 80 songs or so, Rythmbox tells me there's been an error, and it stops uploading. Tried that in Amarok2 and it wasn't successful either.

So, what I did was download Amarok 1.4 (which is still the greatest mp3 player, in my opinion) and tried. I followed the instructions given in this thread, and it worked just fine! However, seeing as 9.10 Karmic already mounts it when inserted, it was not necessary to add a pre-mount and post-mount command, just create a new Device, Generic Player, and that's it, no fuss.

Any questions, I'm here =).

---

### Post by Mangus on 2009-11-14
> **osnofla said:**
> Hey guys, I also have a NWZ S615f Sony Walkman, and I tried to use it in Ubuntu 9.04 Jaunty, to no avail. 

However, in 9.10 Karmic, the issue of mounting it has been solved, and it detects it automatically in Rythmbox and Amarok2. However, when I try to upload songs, after 80 songs or so, Rythmbox tells me there's been an error, and it stops uploading. Tried that in Amarok2 and it wasn't successful either.

So, what I did was download Amarok 1.4 (which is still the greatest mp3 player, in my opinion) and tried. I followed the instructions given in this thread, and it worked just fine! However, seeing as 9.10 Karmic already mounts it when inserted, it was not necessary to add a pre-mount and post-mount command, just create a new Device, Generic Player, and that's it, no fuss.

Any questions, I'm here =).

I'm not so lucky as you :(
s639f here...but i cannot mount it neither in amarok nor rhythmbox...only on nautilus but so I can't manage playlists...

---

### Post by Capt_Zaphod on 2009-12-10
> **osnofla said:**
> Hey guys, I also have a NWZ S615f Sony Walkman, and I tried to use it in Ubuntu 9.04 Jaunty, to no avail. 
However, in 9.10 Karmic, ~~~~

Any questions, I'm here =).

Hello osnofla;
  I've a question, please.
  I'm on Ubuntu 9.10 Karmic & have downloaded the amarok-1.4.9.1.tar.bz2 file.
  
  How do I install it?

Thank you,
-Z

---

### Post by osnofla on 2009-12-12
> **Capt_Zaphod said:**
> Hello osnofla;
  I've a question, please.
  I'm on Ubuntu 9.10 Karmic & have downloaded the amarok-1.4.9.1.tar.bz2 file.
  
  How do I install it?

Thank you,
-Z


Extract it (tar -xvzf amarok-1.4.9.1.tar.bz2), then go into the created directory, and run "sudo make", and then "make install". If you've got all the required libraries and stuff, it should go well, however, you may need to install aditional files, if such is the case, I suggest you use "sudo apt-get install name_of_file".

If you still get lots of errors, you can try downloading amarok from a repository. I took the instructions from this page [http://pcollaog.firefox.cl/2009/04/19/instalando-amarok-14-en-ubuntu-jaunty/comment-page-1/#comment-11043]("http://pcollaog.firefox.cl/2009/04/19/instalando-amarok-14-en-ubuntu-jaunty/comment-page-1/#comment-11043"). It's in spanish, so here it goes in english:

First, you must add a new repository. You may do this in Synaptic or directly editing the file sources.list, and the repository lines are:

deb [http://ppa.launchpad.net/bogdanb/ppa/ubuntu](http://ppa.launchpad.net/bogdanb/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/bogdanb/ppa/ubuntu](http://ppa.launchpad.net/bogdanb/ppa/ubuntu) jaunty main

(I know, it says jaunty, but it has worked that way.)Then, we import the keys of the repository:

sudo apt-key adv --recv-keys --keyserver \
keyserver.ubuntu.com 0x1d7e9dd033e89ba781e32a24b9f1c432ae74ae63

And now, we just remove whatever's installed of amarok2, and then install amarok14 (It's been renamed so there's no confusion):

sudo apt-get remove amarok
sudo apt-get update
sudo apt-get install amarok14

And that's it. I sometimes find that downloading .deb files from a repository is far easier than building source code, because there's almost always something missing. Anyways, try it.

---

### Post by Capt_Zaphod on 2009-12-12
> **osnofla said:**
> Extract it (tar -xvzf amarok-1.4.9.1.tar.bz2), then go into the created directory, and run "sudo make", and then "make install". If you've got all the required libraries and stuff, it should go well, however, you may need to install aditional files, if such is the case, I suggest you use "sudo apt-get install name_of_file".
~~~~~~

And that's it. I sometimes find that downloading .deb files from a repository is far easier than building source code, because there's almost always something missing. Anyways, try it.
osnofla;

  Thank you.  It's installed now.
  It doesn't seem to work 100% though.  When I was on Ubuntu 8.4, with a different build of Amarok (using my Sony NWZ-E436F) it worked well ... better.  The only thing that didn't work with the other version was that lots of the track info got lost in the transfer.
  Now it transfers files to walkman's home folder, instead of to where I set it, in a music folder.
  "Guess tags from filename" also no longer works.

  Any ideas?
Thanks;
-Z

---

### Post by M&amp;StL on 2009-12-25
NwZ-E436F Sony Walkman recently obtained does not synch. Rythm Box shows a Sony Walkman is there, but what we have here is a failure to communicate. 
Any ideas on version 9.1? Is it the same as 9.04?  Opening terminal widows and typing is shaky territory for me. Is there a cut paste of what goes in after the $ sign?

---

### Post by djwkd on 2010-10-22
Hi,
I have a Sony NWZ-S639F, and can't even do step 2. The player shows up as it is connecting in Computer, but after that, it dissapears, and doesn't seem to have a /media connection, and nor can I see a /dev 'link'. Can anyone help?

---

### Post by greg_is on 2011-12-14
I found the easiest way to put working playlist in a Sony Walkman Player (NWZ xxx, and others) on Linux (or not!).

I spent so many hours on that problem, I wanna share it with people with the same problem.

I´m on a  Asus Eee PC 900 with Joli Os on it (so, made on ubuntu lucid lynx).

I use Clementine (for Linux) as Music Manager.

I plug my NWZ E344 and it automounts (in Nautilus and in Clementine) so I can only help people who see it mounted.

So the trick is to forget having your playlist in the icon ¨playlist¨, because it´s made for working with Windows Media Player 11, so trying to workaround with that is too much time consuming and, endless.

So, when your Sony Walkman mounts, you can see these folders in your filebrowser :

[IMG]http://img847.imageshack.us/img847/1213/92877689.png[/IMG]

So you just to create a new folder in the [MUSIC] folder, with the name of the wanted playlist.

Then, go in your favorite music player, open the playlist you want to transfer, select all the files and drag and drop them in the previous created folder.

And that´s it!

So now you can still browse your song by artist or album or whatever, and if you want to listen to a playlist, just go in ¨Folder¨ in the Music icon in the player.

I understand that if you have songs that are in more than one playlist you will have double files, but actually, it´s the only way to have working playlists on these Sony players, if you don´t want to use WMP 11.

And with this trick you can do it from whatever computer (if your device  shows up). :D

---

