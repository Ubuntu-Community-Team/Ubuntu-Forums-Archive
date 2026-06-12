---
title: "Traverso:  Can you share and work on project files between Windows and Linux?"
date: 2010-03-17
forum: Ubuntu Studio
---

### Post by DuggyFreddy on 2010-03-17
Hello, 
My friend and I are setting up a studio together, with the aim that we each have an individual studio, but get together to record and play live (we live in different towns) and combine equipment to get the best setup.  He is running windows with a firewire interface, and I am running Ubuntu Studio karmic.  I am dedicated to staying on Linux, he is a maybe about switching over.  So I was wondering, if we used Traverso, would we be able to use files that were created on each other's system?  Also, will Traverso work with Jack?  I switched over to Linux about 6 months ago and I am finally starting to figure it out.  I use Jack to connect Hydrogen, Ardour,Calf,jkmeter, and Jamin.  I have it all runnning and working pretty well and like that set up, but I gather the trading files thing won't work with Ardour, except as wav files that we could import into the track and try to adjust/sync.  It would be much easier to just open a project file and have it work nice and easy!  

Thanks to everyone for the great help.  This forum has helped me make it this far.

---

### Post by sgx on 2010-03-17
> **DuggyFreddy said:**
> Hello, 
My friend and I are setting up a studio together, with the aim that we each have an individual studio, but get together to record and play live (we live in different towns) and combine equipment to get the best setup.  He is running windows with a firewire interface, and I am running Ubuntu Studio karmic.  I am dedicated to staying on Linux, he is a maybe about switching over.  So I was wondering, if we used Traverso, would we be able to use files that were created on each other's system?  Also, will Traverso work with Jack?  I switched over to Linux about 6 months ago and I am finally starting to figure it out.  I use Jack to connect Hydrogen, Ardour,Calf,jkmeter, and Jamin.  I have it all runnning and working pretty well and like that set up, but I gather the trading files thing won't work with Ardour, except as wav files that we could import into the track and try to adjust/sync.  It would be much easier to just open a project file and have it work nice and easy!  

Thanks to everyone for the great help.  This forum has helped me make it this far.
Hi, this a guess, but if you can install your linux traverso to be in a .wine folder,  (created when you install wine)

/home/username/.wine/drive_c/Program Files

if your paths are the duplicate of his real windows paths, 
including the default save/load folders in .wine, your chances might be good.

If the project files are text files (as in Reaper, Cantabile etc) you can edit the important ones, how tedious this is depends on the particular app, but using a word processors search function can speed up finding the parts needed to edit, as often there is a long list of gibberish, separated by 20 lines of readable data with paths and plugins you can alter as needed. Load a file in a WP, and snoop around! gedit is perfect for that!
You might also consider buying a pair of identical usb/firewire hard-drives, to be used for recording, and saving projects. Yours would likely need to be formatted on his machine, meaning NTFS, so install the ntfs-3g app, or whatever its called in your synaptic repository, to maintain
read/write functions.
Cheers

---

### Post by Capoeira on 2010-03-18
> **DuggyFreddy said:**
> I was wondering, if we used Traverso, would we be able to use files that were created on each other's system? 

well, it's cross-plattform - so it should work

---

### Post by DuggyFreddy on 2010-03-18
Thanks for the info.  I'm going to download the program and fiddle around with it.  I'll try it with and without wine, and find a friend close by with windows to test it out.  I'll post the results when I figure it out.


Edit:  I installed and tested it out on my system.  I was able to get it to record with using Jack with alsa player to play a raw mix, thru calf compressor, to jamin, jkmeter, and into traverso.  It worked great.  It even exported w/out crashing (haven't solved that problem w/ ardour yet).  Next I will burn onto cd and send it to my friend to see if it will work on his windows version.

---

### Post by rsijrier on 2010-03-27
Hi,

You can share Traverso projects fine, as long as you point traverso to the directory the project map is in.

so if you copy the Traverso project map to an external hard disk, or CD, and load it again in the Windows/Mac OS X/Linux version, it should work fine.

Hope this helps, else visit the traverso forum ;)

[http://traverso-daw.org/forum/index.php]("http://traverso-daw.org/forum/index.php")

Have a nice day

---

### Post by DuggyFreddy on 2010-03-27
@rsijrier:  thanks for the link.  there looks to be great info there.  I am starting to get the hang of the program.  I have been able to test sending files to myself over google docs (free! and up to 1G) and reassembling them into a folder on my system, and then loading that into Traverso.  That has worked well, so now just the test w/ my friend's windows system.  I am still figuring out some stuff, and am looking for a way to just send the whole folder over the internet instead of file by file, which would take a long time on a real song.  But sending the individual tracks and just importing them into Traverso works and they seem to sync up from my tests so far.

---

### Post by sgx on 2010-03-28
> **DuggyFreddy said:**
> @rsijrier:  thanks for the link.  there looks to be great info there.  I am starting to get the hang of the program.  I have been able to test sending files to myself over google docs (free! and up to 1G) and reassembling them into a folder on my system, and then loading that into Traverso.  That has worked well, so now just the test w/ my friend's windows system.  I am still figuring out some stuff, and am looking for a way to just send the whole folder over the internet instead of file by file, which would take a long time on a real song.  But sending the individual tracks and just importing them into Traverso works and they seem to sync up from my tests so far.
Hi, if you both get the same archive program, winrar, p7zip, etc you can
archive what you need and off they go, back and forth. Test on an out-take ;)

---

