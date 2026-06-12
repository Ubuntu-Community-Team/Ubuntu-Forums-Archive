---
title: "Conduit: extremely cool syncing concept"
date: 2007-02-19
forum: The Cafe
---

### Post by mostwanted on 2007-02-19
I caught this on Planet Gnome. It's supposed to become a general purpose syncing application for websites, iPods, phones and your computer. The interface is really inventive: you select a device and drag and drop objects like "My Tomboy Notes" and "My F-Spot photos" and it creates a nice graphic for the sync operation (which I presume can be saved in some location so you don't have to drag and drop stuff every time). It looks *really* intuitive, definitely a new way to syncing! Hoping this gets some attention from other Gnome developers.

[[IMG]http://www.johnstowers.co.nz/blog/wp-content/uploads/2007/02/Conduit-Near-v0-3-0.png[/IMG]]("http://mirror.linux.org.au/pub/linux.conf.au/2007/video/monday/monday_1450_GNOME.ogg")

(click photo for Ogg Theora video, it's about 48 MB)

---

### Post by MetalMusicAddict on 2007-02-19
WoW. Thats crazy. :)

---

### Post by mostwanted on 2007-02-19
I think this deserves some more attention, am I really the only one getting excited about this? Check out the video (just click the screen shoot), it explains everything pretty well.

---

### Post by Nikron on 2007-02-19
I don't like apps that like to drag and drop...   mainly because I like maximizing my windows so it can get quite annoying.

---

### Post by Wolki on 2007-02-19
I've been watching Conduit's development for some months, it looks like it could become a wicked cool app, very exciting. I'm especially interested in syncing between computers, since i want to be able to switch between my laptop and my desktop at will and still have all my stuff. I've managed to set it up with Unison, but it has quite a few problems, Conduit will jopefully solve them.

---

### Post by sloggerkhan on 2007-02-19
is there somewhere to learn about this without watching a video?

---

### Post by Super King on 2007-02-19
> **sloggerkhan said:**
> is there somewhere to learn about this without watching a video?

[http://www.conduit-project.org/](http://www.conduit-project.org/)

---

### Post by nzjrs on 2007-02-19
Hey guys,

I am the author of conduit, thanks for all the praise!

Development is moving along nicely, I expect to release 0.3.0 around the time Feisty comes out (my herd4 installation is broken so its a bit hard to develop on).

Im really looking for help with Conduit, there are so may things that people want to sync with and I dont have time to code them all!

So if you are interested in helping then drop me an email.

John

p.s. If you have experience with Django then email me, I have some cool ideas and code in this area for a conduit.net or ubuntu.net (like apples .Mac)

---

### Post by leech on 2007-02-23
I literally was just asking for this very thing and someone pointed me to the website.  This is excellent.  Really all I was looking for was a document sync, where you could for example work on a OpenOffice document on my desktop and then hook up my laptop to the network, sync the file over, and then work on it there.  

Also the ability to choose just any file or folder is exactly what I was looking for, with wanting to copy save game files for when I'm not at home, but have my laptop to play some games on.

I wasn't even thinking about the data types and conversions, that's an excellent idea.  

I wish I could program, I'd help ya out with it.  

Leech

---

### Post by shaunbarlow on 2007-10-04
Hi all,

John - Fantastic program!! 

I've been battling for ages to be able to get podcasts onto my phone via bluetooth without too much dragging and dropping. Also, since my phone (SE Z610i) doesn't have any facility for managing a podcast collection, conduit has become the missing link between amarok and my phone. 

So now amarok downloads the podcasts to my hard drive and keeps them organised, then conduit syncs the my computer's podcast folder with my phone's. 
I grabbed the gnome-vfs-obexftp0.4 from the gutsy repos so I can just put in the obex path to my phone as the location of a folder in conduit. (i.e. obex://[00:11:22:33:44:55]/Memory Stick/Music/)

Whilst I'd really like to cut out the middle man and have amarok recognise obex://...... addresses, that's probably a little way off under gnome. So, conduit helps me out no end!!!

Can anyone suggest how I can incorporate some kind of bluetooth proximity monitor (so that by the very act of my phone being near my computer with bluetooth turned begins the process, instead of me clicking, clicking, clicking), amarok (cued by the proximity thing, to download the podcasts) and conduit (to do the transfer to my phone after amarok has done it's thing)?

I have very limited programming knowledge, but am willing to learn if someone can help by pointing me in the right direction. Plus I have a hunch that once this sort of thing is put together it could be really useful for a heap of people and applications.

Once again congrats on the great job with conduit! I'm looking forward to playing around with a heap this afternoon after only downloading it this morning.

Cheers all,
Shaun

---

### Post by Polygon on 2007-10-04
seems to work well

im wondering how easy it is to create a plugin for certain things, like my mp3 player that just acts as a HDD, but the music and videos gotta go in a specific folder......

---

### Post by shaunbarlow on 2007-10-04
> **Polygon said:**
> seems to work well

im wondering how easy it is to create a plugin for certain things, like my mp3 player that just acts as a HDD, but the music and videos gotta go in a specific folder......
Polygon: I don't think it'd be that hard. I guess you'd just create a different sync group for each type of file you want to sync. The folder dataprovider would probably work for both the local and the mp3 player if, as you say, the mp3 player acts as a hard drive.

---

### Post by nzjrs on 2007-10-29
Just a note to say that the ability to transcode music/videos to different formats, and to put music and video in special device folders, has recently been added to conduit SVN. This should meet most of the needs bought up in this thread. Watch out for the next release and email me if you need more info

John, (Conduit Developer)

---

### Post by sloggerkhan on 2007-10-30
I just compiled from svn... For some reason it doesn't seem to have an evolution sync, and even though I can run it localy, make install doesn't work.

```

Making install in conduit
make[1]: Entering directory `/home/redice/conduit/conduit/conduit'
Making install in datatypes
make[2]: Entering directory `/home/redice/conduit/conduit/conduit/datatypes'
make[3]: Entering directory `/home/redice/conduit/conduit/conduit/datatypes'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/python2.5/site-packages/conduit/datatypes" || /bin/mkdir -p "/usr/local/lib/python2.5/site-packages/conduit/datatypes"
 /usr/bin/install -c -m 644 'Contact.py' '/usr/local/lib/python2.5/site-packages/conduit/datatypes/Contact.py'
 /usr/bin/install -c -m 644 'DataType.py' '/usr/local/lib/python2.5/site-packages/conduit/datatypes/DataType.py'
 /usr/bin/install -c -m 644 'Email.py' '/usr/local/lib/python2.5/site-packages/conduit/datatypes/Email.py'
 /usr/bin/install -c -m 644 'Event.py' '/usr/local/lib/python2.5/site-packages/conduit/datatypes/Event.py'
 /usr/bin/install -c -m 644 'File.py' '/usr/local/lib/python2.5/site-packages/conduit/datatypes/File.py'
 /usr/bin/install -c -m 644 '__init__.py' '/usr/local/lib/python2.5/site-packages/conduit/datatypes/__init__.py'
 /usr/bin/install -c -m 644 'Note.py' '/usr/local/lib/python2.5/site-packages/conduit/datatypes/Note.py'
 /usr/bin/install -c -m 644 'Photo.py' '/usr/local/lib/python2.5/site-packages/conduit/datatypes/Photo.py'
 /usr/bin/install -c -m 644 'Text.py' '/usr/local/lib/python2.5/site-packages/conduit/datatypes/Text.py'
Byte-compiling python modules...
Contact.py DataType.py Email.py Event.py File.py __init__.py Note.py Photo.py Text.py
Byte-compiling python modules (optimized versions) ...
Contact.py DataType.py Email.py Event.py File.py __init__.py Note.py Photo.py Text.py
make[3]: Leaving directory `/home/redice/conduit/conduit/conduit/datatypes'
make[2]: Leaving directory `/home/redice/conduit/conduit/conduit/datatypes'
Making install in dataproviders
make[2]: Entering directory `/home/redice/conduit/conduit/conduit/dataproviders'
make[3]: Entering directory `/home/redice/conduit/conduit/conduit/dataproviders'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: *** No rule to make target `SimpleConfigurator.py', needed by `install-conduitPYTHON'.  Stop.
make[3]: Leaving directory `/home/redice/conduit/conduit/conduit/dataproviders'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/redice/conduit/conduit/conduit/dataproviders'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/redice/conduit/conduit/conduit'
make: *** [install-recursive] Error 1

```

What's the difference between make and make install that might throw errors?

---

### Post by 3rdalbum on 2007-10-30
Oooo... I'll have to grab this from SVN and check it out (pun unintended). I'm writing a program to manage a particular brand of MP3 player, which would include a plugin architecture for input sources of audio and video, and transcoding those into the format that the Mp3 player supports. Maybe a Conduit plugin would be an easier way to do this?

---

### Post by sloggerkhan on 2007-10-30
Don't know if it would be easier or not, but you could probably make a plugin that dumped a directory of music into the player and maybe even transcoded it.

---

### Post by nzjrs on 2007-10-31
> **sloggerkhan said:**
> 

What's the difference between make and make install that might throw errors?

I have not yet updated the makefiles. Just run it uninstalled for now. I will fix the makefiles soon

---

### Post by nzjrs on 2007-10-31
> **3rdalbum said:**
> Oooo... I'll have to grab this from SVN and check it out (pun unintended). I'm writing a program to manage a particular brand of MP3 player, which would include a plugin architecture for input sources of audio and video, and transcoding those into the format that the Mp3 player supports. Maybe a Conduit plugin would be an easier way to do this?

Definately. You could do this in conduit with less than 50 lines of python. Just derive from the appropriate dataprovider.File.FolderTwoWay and dataprovider.File.FileSource for the mp3 player end and source end respectively.

Then add a config dialog and implemet get_input_conversion_args in the sink to support transcoding

Email me or the conduit mailing list for help. Also visit #conduit on gimp IRC

---

### Post by curuxz on 2007-10-31
Anyone know if this will work with KDE 4's data sync frame work or previous versions of KDE?

---

### Post by EdThaSlayer on 2007-10-31
It looks very interesting. Love the creativity going on here. It will make converting things less of a hassle for the GNOME users.

---

### Post by betes on 2007-12-03
Not sure if this is the right place for a howto question, but I'll throw it out there. How do you make another computer on your LAN a dataprovider.  Thats what I would love to use conduit for (synching between my two computers) and from all of the screencasts and screenshots I see of conduit a netowrk machine is listed as a datapoint in the pane on the left.  Are there some steps necessary to set this up?

---

### Post by Roasted on 2008-03-16
I'm almost not sure how to use something like this. I spent a decent amount of time pounding out a solid rsync script to automatically synchronize my home folder to back up on two additional hard drives I have in my rig... something like this that seems simple actually looks a lot harder to me due to the fact I'm used to syncing stuff via text!! 

I'm not even sure I want to try it, simply because the way I sync works fine. But I'm curious to give it a shot... I'd love to try it and see what happens.

Has anybody else used it? What kind of luck did you folks have?

I'm just not sure how I'd set it up... because my setup is kind of weird.

I have 3 drives. SATA A, SATA B, IDE.

SATA A = XP Pro/Ubuntu install, plus my home directory. My home directory is synced onto SATA B. Also on SATA B is 3 additional network share folders that are accessed via samba from 3 other desktops in the household. So essentially, SATA B is a backup of 3 desktops in the house + my home directory on SATA A. Then, IDE, is a complete copy of SATA B. 

That'd be twisted to set up in this program, I would think...

---

### Post by borobudur on 2008-12-25
I'm not sure if this thread is still active but I'll give it a try:
Before I install Conduit on my machines, could someone answer me two questions?

1. What's the architecture of Conduit? Peer to peer? Just install on each machine the application and that's good enough? Or is there a server which manages everything?

2. I'm especially interested in the file synchronization part. Is it also connected to Nautilus (you can see the status of the file synchronization in Nautilus)? There is a application called Dropbox which does that but I don't like the third party storage.

Thanks!

---

