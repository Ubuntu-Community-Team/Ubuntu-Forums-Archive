---
title: "Jack, Qsynth,, and Ardour setup... I need help!"
date: 2008-05-20
forum: Ubuntu Studio
---

### Post by thekylehome@gmail.com on 2008-05-20
I am running Jack, Qsynth, and Ardour... and I want to record a piano (using my M-Audio ProKeys 88 keyboard) track in ardour. Well I need someone to tell me how to go about setting up Jack, Qsynth, and Ardour so that I can record and then playback... I am clueless... my keyboard plugs into the computer via USB. 
Someone please tell me how to get this setup... Thanks!

---

### Post by warbread on 2008-05-20
Oh boy, this is no small task.  Don't expect to understand what to do just by reading this.  You'll understand when you are in the program.  Do you have Jack running in real time mode already?  Since you're not recording any analog signals, set the 'Audio' setting on the right of the Jack set up screen to be "Playback Only".  Most every other setting is pretty much useless in this context.  

First step is to get Jack running.  Turn on your plugged in keybaord. Then open up Qsynth, Ardour and **Patchage**.  This program lets you visually connect all of your Jack enabled programs.  Operation is easy.   Blue == sound and green == midi.  Outputs are sort of justified to the right and inputs to the left.  You'll see what I mean, it's straightforward.  To connect things, either click on one and then the other, or click and drag from one to the other.  Repeat the process to disconnect.  You can also right click on an item to disconnect all connections. Connect the first (top) connection from your keyboard to the Qsynth midi input.  

For Qsynth, you'll need soundfonts.  [Here are some free ones]("http://johannes.fr/soundfonts.htm"), though Google can lead to many more.  Qsynth will take some figuring out, but you can do it quicker than I can type this.  

Go into Ardour and create a track.  Just right click on the left side and create a mono or stereo track, your choice.  Name it something you'll understand, like "Piano".  Go back into patchage and connect the Qsynth audio output to the Ardour input of the name you just chose.  You should be good to go!  Arm the track you want to record by pressing the little red button by its name, then hit the bit red record button at the top of the screen and press space bar to start.

---

