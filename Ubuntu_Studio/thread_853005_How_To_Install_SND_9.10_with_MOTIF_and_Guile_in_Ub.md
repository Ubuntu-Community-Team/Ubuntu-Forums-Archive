---
title: "How To Install SND 9.10 with MOTIF and Guile in Ubuntu 8.04"
date: 2008-07-08
forum: Ubuntu Studio
---

### Post by namae on 2008-07-08
Step by step, How to install a fully functional SND 9.10 sound editor with motif graphical toolkit and scheme extension language on Ubuntu 8.04. (not Ubuntu Studio):

This is from a fresh install of the OS, and works on my ASUS/P4 desktop with Maudio Delta-1010 sound card as well as on my Dell P3 laptop with internal motherboard-based sound.

If you feel uncomfortable with the safety of executing any of these commands then you can always read up on them to see what they do. Nothing too scary looking here though, I don't think.

OK

Open up a terminal and...

1) First, get the SND source tarball from its home page:
wget [ftp://ccrma-ftp.stanford.edu/pub/Lisp/snd-9.10.tar.gz](ftp://ccrma-ftp.stanford.edu/pub/Lisp/snd-9.10.tar.gz)

2) Get what you need to compile packages from ubuntu source repo:
sudo apt-get install build-essential

3) Install Guile extension language and Guile and Alsa libs/dev packages:
sudo apt-get install guile-1.6 guile-1.6-dev guile-1.6-libs libasound2-dev

4) Install the build dependencies for the Motif libs/clients:
sudo apt-get build-dep libmotif3 libmotif-dev motif-clients

5) Get and automatically build the Motif toolkit source packages:
sudo apt-get source --compile libmotif3 libmotif-dev motif-clients

6) Install the motif packages that you just auto-built:
sudo dpkg -i libmotif3_2.2.3-2_i386.deb libmotif-dev_2.2.3-2_i386.deb motif-clients_2.2.3-2_i386.deb 

7) Install the menu package to finish setting up motif-clients
sudo apt-get install menu

Now its time to actually install SND...

8) Assuming you haven't changed directories:
tar -xvzf snd-9.10.tar.gz

9) Go into the resultant snd-9.10 directory: 
cd snd-9.10/

NOTE: lots of helpful documentation in snd1.html and README files

10) Run the configure script with some special switches:
./configure --with-alsa --with-static-xm --with-doubles --with-motif-prefix=/usr/lib 

If the "Options selected" field at the end of the messages following the ./configure command indicates that your extension language is Guile, audio system is ALSA, and graphics toolkit is Motif, then you are ready to build SND...

11) Run make to build SND:
make

12) Install SND:
sudo make install

Now that SND is installed there are a few important things left to do...

13) Create the initialization file to load .scm extensions. I used vim but use whichever text editor you like best: 
sudo vim /etc/snd_guile.conf 

15) Add this line, including parentheses, to that file: 
(load "/usr/local/share/snd/misc.scm")

At this point SND is installed and will load some usefull .scm extensions when it is started, however audio playback may not be working. If that is the case (as it was for me) you have to set some environment variables that SND looks for at startup.

16) Add the following line to the already existing "/home/username/.bashrc" file. Use whichever text editor you like best:
export MUS_ALSA_DEVICE="hw:0,2"

NOTE: The .bashrc file is hidden but it is certainly there in your "/home/username/" directory.  If you are in that directory do "ls -lah" with no quotes on the command line to see the hidden files. Shift + pageup if it scrolled by too fast.

17) Save your changes to the file, log out and then log back in so your .bashrc file is re-read.

You should now have a fully functional installation of SND-9.10!


18) Normally you start SND in a terminal by typing:
snd

But you should read this first!

Important note!:

The "File-->Open" dialog in SND doesn't let me navigate my directory structure on my desktop computer, though it works fine on my laptop. I probably need to set some environment variable for Motif, but not sure which. If this is the case for you too, then type in the full path to a directory full of sounds in the text field of the graphical file browser in SND. Make sure to type "/" with no quotes at the end of the path to the soundfiles directory and then hit the enter key. You should then see all your sounds and should be able to play and open them. 

Alternatively you can just use the preload switch "-p" followed by the path to a directory of sounds when you start SND.

ex:
snd -p /path/to/soundfiles/

In that case, once SND is running, select View-->Files with the mouse and you should be able to see your "preloaded" sounds.

The last method is to just give an absolute path to a single or multiple sounds (not so many that your computer will freeze as SND loads them all) when you start SND on the commandline:

snd /path/to/soundfiles/sound1.wav



Here is a file to play with if you don't have anything yet. (This link works sometimes, and sometimes it doesn't??)

wget [http://www.geocities.com/SoHo/Museum/4312/AMENST.wav](http://www.geocities.com/SoHo/Museum/4312/AMENST.wav)



Lastly, if you feel so inclined, drop Bill Schottstaedt (bil@ccrma.stanford.edu) a line, not me, and tell him thanks for SND.

(I actually haven't done this step yet)

---

