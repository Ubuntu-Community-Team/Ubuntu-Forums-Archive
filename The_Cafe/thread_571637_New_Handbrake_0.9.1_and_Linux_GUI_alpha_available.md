---
title: "New Handbrake 0.9.1 and Linux GUI alpha available"
date: 2007-10-09
forum: The Cafe
---

### Post by stmiller on 2007-10-09
[http://www.digg.com/software/HandBrake_0_9_1_Released](http://www.digg.com/software/HandBrake_0_9_1_Released)

New version of [HandBrake]("http://handbrake.m0k.org/?article=7") is out, and a [GTK Linux GUI is available from the forums]("http://handbrake.m0k.org/forum/viewtopic.php?t=885&postdays=0&postorder=asc&start=30"). Check it out!

---

### Post by Incense on 2007-10-09
It looks great. I use this app all the time on my Mac. Nice to have a GUI for Linux.

---

### Post by Polygon on 2007-10-09
nice, ill see if this can rip a DVD that dvd::rip cannot :D

---

### Post by Dixon Bainbridge on 2007-10-09
Handbrake is quality. Nice to see it buffed up for linux.

---

### Post by Incense on 2007-10-09
> **Polygon said:**
> nice, ill see if this can rip a DVD that dvd::rip cannot :D

That's what K9copy is for....

---

### Post by stmiller on 2007-10-09
Handbrake is about twice as fast as those other apps when encoding with x264, I have noticed (using the 'turbo' x264 option). Also k9copy and dvdrip are not multithreaded at this point, unfortunately. So they only use 1 CPU. :(
HandBrake can take advantage of 2, 4, or 8 cores!

---

### Post by Polygon on 2007-10-10
> **Incense said:**
> That's what K9copy is for....

ill keep that program in mind 

and has anyone gotten the GTK+ gui to work? ([http://handbrake.m0k.org/forum/viewtopic.php?t=885&start=30](http://handbrake.m0k.org/forum/viewtopic.php?t=885&start=30))

i installed gtk-sharp and mono and it crashes if i try to run it

---

### Post by Timsy321 on 2007-10-12
Could anyone please give me some instruction on how to go out about installing handbrake on ubuntu gusty. Thanks!

---

### Post by maxx22 on 2007-10-20
Here's what I did to get the GUI going on Gutsy...
-Download linux binary from Handbrake site
-Extract then copy HandBrakeCLI to /usr/bin
-Download HandBrakeGTK from here [http://sourceforge.net/projects/handbrakegtk](http://sourceforge.net/projects/handbrakegtk)
-extract, goto extracted directory, goto bin directory, copy HandBrake directory to /home/username/.config
-chmod 0755 HandBrakeGTK.exe
-copy the HandBrakeGTK.exe to where ever you want to run it from
-sudo apt-get install mono
-sudo apt-get install mono-devel
-sudo apt-get install gtk-sharp
-run 'mono ./HandBrakeGTK.exe' to start the gui
Worked for me.

---

### Post by Polygon on 2007-10-20
thanks...that worked. the guy on the forums forgot to add that you need to install mono-devel :D

---

### Post by kamaboko on 2007-10-20
I use this on my Vista box.  Very nice quality.  I will say though it runs much much slower when trying to compress down to fit on a CD.

---

### Post by Timsy321 on 2007-10-22
Could anyone give me some detailed instructions on how to install the handbrakeCLI. I can't seem to figure it out. Im using Gusty and am a noob with linux. Thanks in advance!

---

### Post by stinkypudding on 2007-10-23
I was able to get it working, but it says "HandBrake is reading the DVD, please be patient as this can take up to a minute."   That was 20 minutes ago, so I certainly don't trust this yet.

---

### Post by Polygon on 2007-10-23
> **Timsy321 said:**
> Could anyone give me some detailed instructions on how to install the handbrakeCLI. I can't seem to figure it out. Im using Gusty and am a noob with linux. Thanks in advance!

easiest way is to move the binary to /usr/bin/

this command should do it

change directory to where the binary is...like your desktop or something (cd ~/Desktop)

sudo mv HandBrakeCLI /usr/bin/

and then you can just use it by running HandBrakeCLI in a terminal...or you can install the GUI using the instructions in this thread.

and stinky.,...something is wrong..it takes only a second for it to read the DVD for me...do you have the dvd lib files installed? (like libdecss and all that)

---

### Post by MystaMax on 2007-11-01
I do most of my ripping on Windows now. Only because I have a set process that works for me. But, I had a couple of questions...

Whats the quality like?
When creating divx files on Windows, I've had problems getting the audio and video to sync up. Has anyone had this problem w/ handbrake?

---

### Post by Polygon on 2007-11-01
ive ripped a total of like 9 dvds with handbrake so far, havent had any video/audio synching problems

the only realy problem is when you try to rip a non like...commercial dvd. I have this dvd that i bought from this guy who im pretty sure made the dvd in his garage, and dvd:rip wouldent even rip it, and in handbrake it takes like 10 times longer then usual...but it still works

---

### Post by notwen on 2007-11-01
Thanks for pointing out this app.  I'll be sure to try it out once I get home.

---

### Post by nelio2k on 2007-11-05
I've tried this before, but it's giving me this error:

** (./HandBrakeGTK.exe:1799): WARNING **: The following assembly referenced from /home/neilhuang/Desktop/HBGTK_alpha1/bin/HandBrakeGTK.exe could not be loaded:
     Assembly:   gtk-sharp    (assemblyref_index=1)
     Version:    2.10.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/neilhuang/Desktop/HBGTK_alpha1/bin/).


** (./HandBrakeGTK.exe:1799): WARNING **: Could not load file or assembly 'gtk-sharp, Version=2.10.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'gtk-sharp, Version=2.10.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.
File name: "gtk-sharp, Version=2.10.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f"

Btw, I've had this same problem with Tomboy Notes... any help on this would be really really great. Mono is giving me headaches

Thanks!

> **maxx22 said:**
> Here's what I did to get the GUI going on Gutsy...
-Download linux binary from Handbrake site
-Extract then copy HandBrakeCLI to /usr/bin
-Download HandBrakeGTK from here [http://sourceforge.net/projects/handbrakegtk](http://sourceforge.net/projects/handbrakegtk)
-extract, goto extracted directory, goto bin directory, copy HandBrake directory to /home/username/.config
-chmod 0755 HandBrakeGTK.exe
-copy the HandBrakeGTK.exe to where ever you want to run it from
-sudo apt-get install mono
-sudo apt-get install mono-devel
-sudo apt-get install gtk-sharp
-run 'mono ./HandBrakeGTK.exe' to start the gui
Worked for me.

---

### Post by Polygon on 2007-11-05
neilo, it seems from the error that its having trouble finding gtk-sharp...are you sure that is installed?

---

### Post by nelio2k on 2007-11-07
Actually I had to reinstall gtk-sharp from scratch, building it from source. After linking it with the environmental variable $MONO_PATH, I got the error to go away. It was a **lot** of work... gah...

So now I have another problem... running the GUI (HandBrakeGTK.exe) with mono, (already have HandBrakeCLI in usr/bin), I get the main window. All is fine and dandy until I click the "Source" button.

So a window pops up, that's supposed to be like the file open dialogue, but then everything quits with the error message:
mono: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64

I've googled everywhere and no one seems to have a fix for this. Does anyone have any idea?

---

### Post by handdog on 2007-11-08
I've been waiting for a gui like this for a while, and am happy to say it works decently for me :)

There are some issues that could be cleaned up (customizing from a preset, saving a preset, deleting entries from the queue, etc.) but overall it's pretty sweet. Can't wait to see it in the apt-get repos..

---

### Post by Terc on 2007-11-15
Fantastic!  I love handbrake on my Mini, but finally having a usable gui for it on my main box means I get much faster rips.  Thanks a million!

---

### Post by denis_std on 2007-11-17
Could someone upload the GUI because the link isn't available anymore... :(

---

### Post by Polygon on 2007-11-17
> **denis_std said:**
> Could someone upload the GUI because the link isn't available anymore... :(

sure

---

### Post by mufflon on 2007-11-22
Seems like the project has a new name on sourceforge, or am I wrong?
[http://rippedwire.sourceforge.net/](http://rippedwire.sourceforge.net/)

Download here:
[http://sourceforge.net/project/showfiles.php?group_id=207412](http://sourceforge.net/project/showfiles.php?group_id=207412)

---

### Post by Polygon on 2007-11-22
thanks for the link muffalon, that looks very promising. he even has a deb now

but to download the deb, replace handbrakegtk in the url with rippedwire or else it wont work

example: [http://downloads.sourceforge.net/rippedwire/handbrakegtk_1.0.1_i386.deb?use_mirror=osdn](http://downloads.sourceforge.net/rippedwire/handbrakegtk_1.0.1_i386.deb?use_mirror=osdn)

---

### Post by Emerzen on 2007-11-28
Just to some up as some confusion surrounds the wonderful software:

Download [Handbrake CLI here]("http://handbrake.m0k.org/?article=download")

Extract the file then copy the file to the /usr/bin directory

Download [HandbrakeGTK/RippedWire here]("http://sourceforge.net/project/showfiles.php?group_id=207412")

Install the .deb package, which takes care of the dependencies.  This was all that was needed for me on a Gutsy i386 install.  It seems that the confusion surrounds the different names of the software Rippedwire=HandbrakeGTK.

---

### Post by Polygon on 2007-11-28
the guy kinda renamed his project without warning,a nd its even still called handbrakegtk even in that new release, which is much better then his first one

and just a note, advanced x264 options dont get passed to the cli in this version, so if you want to use the advanced options, you have to use the cli.

---

### Post by quidpro on 2007-12-08
Does Handbrake take advantage of multi cores when ripping, transcoding, or both?

---

### Post by stmiller on 2007-12-08
> **quidpro said:**
> Does Handbrake take advantage of multi cores when ripping, transcoding, or both?

Yes. It will take every core you've got when ripping/encoding. This is the only DVD encoder that will do this at the moment. Check out the HB forums for comments on people using 8 core machines and so forth. It's pretty crazy.

BTW: HB for OS X and Windows does not rip directly from the CD (only HB in Linux does this!). This is due to the lack of libdvdcss on win32 with cygwin, and lack of libdvdcss in OS X.

---

### Post by rockstar on 2007-12-12
I've got everything installed.  What I would love is if someone would walk me through this step by step so that I can make everything work, I know it's simple, but I'm sure someone's got all the steps ironed out,

Thanks!

---

### Post by Polygon on 2007-12-12
if your using the GUI, you can just select the source (the video_ts folder), and select your settings and off you go. You can select chapters to rip, where to rip it to, what format, what container, etc etc

HOWEVER

if you are wanting to use any advanced h.264 (x264) options, the gui is bugged and wont pass it along to the CLI, so your gonna have to use the CLI version if you want the advanced options to actually take effect.


There are also presets, but again, most of them use advanced h.264 options and those dont work in the gui at the moment. But the command line equivilants can be found here, along with a description of each

[http://handbrake.m0k.org/trac/wiki/BuiltInPresets](http://handbrake.m0k.org/trac/wiki/BuiltInPresets)

replace -i DVD with the path to your cd rom

replace -o ~/Movies/movie.mkv with the path that you want your file to be in.

make sure you remove the ./ infront of HandBrakeCLI if you have already copied HandBrakeCLI to /usr/bin/

---

### Post by rockstar on 2007-12-12
These Scripts look great! I think CLI might be better, everything in ubuntu seems better cli.  Like ABCDE.  Does anyone know how to add subtitles and multiple audio streams to a Script?

Thanks again

---

### Post by Ingenium on 2008-02-14
I tried installing the .deb but I get this error:

```
Unpacking handbrakegtk (from .../handbrakegtk_1.0.1_i386.deb) ...
dpkg: error processing /home/josh/Desktop/handbrakegtk_1.0.1_i386.deb (--install):
 trying to overwrite `/usr/share/applications/brasero.desktop', which is also in package brasero
dpkg-deb: subprocess paste killed by signal (Broken pipe)
```

---

### Post by Polygon on 2008-02-14
it shouldent even be touching brasero....unless the packager screwed up and accidently included that desktop file with it....

the gui is pretty broken anyway. It doesnt pass advanced x264 options to the cli..... and some other problems with it.

---

### Post by Hipenbecker on 2008-02-19
I'm so new to this O/S that I feel lost.

This is what I am doing.

I am opening up a terminal window. (Good I think)

I type  
sudo apt-get install mono
Building dependency tree       
Reading state information... Done
E: Couldn't find package mono

What am I doing wrong here?

---

### Post by Ingenium on 2008-02-19
> **Hipenbecker said:**
> I'm so new to this O/S that I feel lost.

This is what I am doing.

I am opening up a terminal window. (Good I think)

I type  
sudo apt-get install mono
Building dependency tree       
Reading state information... Done
E: Couldn't find package mono

What am I doing wrong here?

You may not be using the universe and multiverse repositories. type:
sudo gedit /etc/apt/sources.list

and uncomment all the lines that begin with deb. Save. Then run:

sudo apt-get update
sudo apt-get install mono

---

### Post by Hipenbecker on 2008-02-20
That did it.

Thanks a lot.

---

### Post by Polygon on 2008-02-20
if you cant ever find a package, either search for it in synaptic or do a 

sudo apt-cache search SEARCH

---

### Post by arbulus on 2008-03-05
> **stinkypudding said:**
> I was able to get it working, but it says "HandBrake is reading the DVD, please be patient as this can take up to a minute."   That was 20 minutes ago, so I certainly don't trust this yet.


I'm having the same problem

---

### Post by stmiller on 2008-03-06
> **arbulus said:**
> I'm having the same problem

You have to have libdvdcss installed via medibuntu.

---

### Post by SZF2001 on 2008-03-06
I'm not sure about HandBrake, but it seems like the latest DeVeDe (the one in the repositories is crap so I used GetDeb.net along with backporting mencoder and mplayer and all that jazz) works fine for me... What's the advantages/disadvantages to this?

---

### Post by Polygon on 2008-03-06
its pretty easy to use and has lots of presets for stuff, such as an ipod or a psp. Can do cool stuff with it so it can like set the size to fit on a CD, has advanced x264 options, 

disadvantages is that this doesnt have a gui that works 100% (at least for linux), so its a bit harder to use, but it does have a CLI guide and the CLI equivalents of all the presets.

---

### Post by zagor on 2008-03-06
But the HandBrakeCLI binary itself works for you?
I don't want to use the GUi because I want to add HandBrake as a user job in my mythtv box.

I've tried downloading the tar.gz file from HandBrake site and untarred to a dedicated directory in my home.
When running the binary I get this:

```
zagor@yumi:~$ mkdir HB2

zagor@yumi:~$ cd HB2

zagor@yumi:~/HB2$ tar xvzf HandBrake-0.9.2_i386.tar.gz
HandBrakeCLI

zagor@yumi:~/HB2$ ./HandBrakeCLI
bash: ./HandBrakeCLI: No such file or directory

zagor@yumi:~/HB2$ ls -al
total 8636
drwxr-xr-x  2 zagor zagor    4096 2008-03-04 01:57 .
drwxr-xr-x 42 zagor zagor    4096 2008-03-04 01:56 ..
-rw-r--r--  1 zagor zagor 2147416 2008-03-04 01:55 HandBrake-0.9.2_i386.tar.gz
-rwxr-xr-x  1 zagor zagor 6667911 2008-02-19 19:51 HandBrakeCLI
```

I've tested the same procedure (using exactly the same file) on a virtual Knoppmyth installation and everything works fine.
What am I getting wrong?
Permissions are fine, I think.

I'm on a Mythbuntu 7.10 x64 box, almost freshly installed.

Thanks

---

### Post by Polygon on 2008-03-06
chmod +x the binary...or just put it in /usr/bin and just run it without the prefixing ./

---

### Post by arbulus on 2008-03-06
> **stmiller said:**
> You have to have libdvdcss installed via medibuntu.


That did it.  I thought I had already installed libdvdcss, but apparently i had not.

---

### Post by zagor on 2008-03-07
> **zagor said:**
> 
[...]
```

zagor@yumi:~/HB2$ ls -al
total 8636
drwxr-xr-x  2 zagor zagor    4096 2008-03-04 01:57 .
drwxr-xr-x 42 zagor zagor    4096 2008-03-04 01:56 ..
-rw-r--r--  1 zagor zagor 2147416 2008-03-04 01:55 HandBrake-0.9.2_i386.tar.gz
-rwxr-xr-x  1 zagor zagor 6667911 2008-02-19 19:51 HandBrakeCLI
```
[...]



> **Polygon said:**
> chmod +x the binary...or just put it in /usr/bin and just run it without the prefixing ./

Well, as you can see from my previous post, the binary is already +x...

Copying it to /usr/bin or /usr/local/bin does not work as well, same error.

Peering through the forums, though, I've found mentioned somewhere that HandBrakeCLI **must be compiled on Ubuntu or it won't work**.
I've installed loads of dependencies, found in their site and in [this ]("http://ubuntuforums.org/showthread.php?t=96765")post.
Than I compiled with jam and the binary hence obtained **_*simply WORKS*_**!

It's a pity I had to overload my essential Mythbuntu with so many development dependencies, but on the other hand I now have a HandBrakeCLI binary compiled on Mythbuntu 7.10 for an AMD64 x2.

In case someone cares, I can find a place where to share it.

---

### Post by Polygon on 2008-03-07
again, that isnt right. I downloaded handbrake 0.9.2 from their website, dropped it in /usr/bin/ and it 'simply worked', so i dunno what your problem was.

and you dont need libdvdcss either, its compiled in.

---

### Post by zagor on 2008-03-07
> **Polygon said:**
> again, that isnt right. I downloaded handbrake 0.9.2 from their website, dropped it in /usr/bin/ and it 'simply worked', so i dunno what your problem was.


Amazing, for in my case HB 0.9.2 does not work if moved to /usr/bin (no ./ prefix, obviously).
It works only if compiled.

Are you on Ubuntu or Mythbuntu?

I'll try it on another Mythbuntu installation, just for curiosity.

---

### Post by cchi on 2008-04-20
> **zagor said:**
> Amazing, for in my case HB 0.9.2 does not work if moved to /usr/bin (no ./ prefix, obviously).
It works only if compiled.

Are you on Ubuntu or Mythbuntu?

I'll try it on another Mythbuntu installation, just for curiosity.

I have exactly the same problem here.  I even have 2 boxes, one running Ubuntu Server 6.06 (32 bit), and one running Ubuntu Server 7.10 (64 bit).

**Ubuntu Server 6.06 (32 bit):** Handbrake 0.92 Binary **_working_** no problem
**Ubuntu Server 7.10 (64 bit):** Handbrake 0.92 Binary (same one as above!) **_will not_** run at all.

This is the output when I run it:

[B]# ./HandBrakeCLI --help
-bash: ./HandBrakeCLI: No such file or directory[/B]

(And yes, the binary *is* actually there, and is has permissions of 755)

Is it a 64 bit issue?  Is it an Ubuntu 7.10 issue?

---

### Post by Polygon on 2008-04-20
Thats really weird....

the binary doesnt have to be in /usr/bin...did you try running it from like your home directory?

and im running ubuntu hardy...(and it works for me)

---

### Post by chris4585 on 2008-04-20
this is pretty sweet thanks!

---

### Post by kinematic on 2008-04-20
Can you fine tune the b-frame ratio/offset and such with Handbrake and does it accept custom quantization for XviD ?

---

### Post by Polygon on 2008-04-20
I dont think it accepts advanced xvid options because no one has added it (i read in a forum that if anyone is ABLE to add it to the program it would be greatly apprechiated)

about the b frames, i have no idea, although its most likely possible.

[http://trac.handbrake.fr/wiki](http://trac.handbrake.fr/wiki)

---

### Post by cchi on 2008-04-20
> **Polygon said:**
> Thats really weird....

the binary doesnt have to be in /usr/bin...did you try running it from like your home directory?

and im running ubuntu hardy...(and it works for me)

Hmm..  I have tried running it from /usr/bin and from my home dir, and from root's homedir (as root!).  Nothing will make it work..

Maybe it does have to be compiled from source to run on this system...

---

### Post by cchi on 2008-04-21
OK, I just confirmed with an Ubuntu guru friend of mine.

The binary was not running because as I mentioned above, the standard binary from HandBrake is 32bit.  My Ubuntu 7.10 is 64bit.

**There are two ways to fix this:**

1. Compile from source on the 64bit system/machine.
2. Install package (from apt-get) called **ia32-libs** - This will allow you to run 32bit binaries on the 64bit system.

I did 2, and its working fine!

I hope this helps someone!

---

### Post by mondoUNC on 2008-04-25
I'm trying to install HandbrakeGTK 1.0.1 using the deb i found [here]("http://sourceforge.net/project/showfiles.php?group_id=207412&package_id=248322&release_id=553070") I still need mono and for the life of me, i can't get it to install.

```
Reading state information... Done
Package mono is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mono has no installation candidate
```

Is the error i keep getting. I'm running Hardy, How can i install mono because handbrake is not the only program that uses it as a dependency. I've tried other solutions posted in this thread and none have worked.

---

### Post by tigerplug on 2008-04-25
This is brilliant!

I was actually just thinking about how handy this would be the other night! 


Thanks for the post ;)

---

### Post by Polygon on 2008-04-26
again, handbrakeGTK is old, buggy and unsupported. If you use any advanced x264 options with handbrakeGTK they will not work. To use handbrake to its full potential its reccomended that you use the command line version


and for some reason im getting the same thing when trying to install mono. You can try manually installing mono-runtime mono-utils  and mono-common and see if that fixes it...

---

### Post by mtgmutton on 2008-04-26
> and for some reason im getting the same thing when trying to install mono. You can try manually installing mono-runtime mono-utils  and mono-common and see if that fixes it...

I tried this.... I got the gui to work before trying it, but the .deb package wouldn't install... and it still won't  :(  I got the gui to work by putting the extracted folder in my /usr/local/bin folder and making a shortcut. BUT the gui freezes when I try to rip a DVD. It also leaves the process running, and I am forced to end it with the system monitor. I am running Hardy.

---

### Post by joeyt2k on 2008-04-26
I'm having the exact same problem.

Ran Handbrake GUI fine in Gutsy, but after the update to Hardy my desktop shortcut was broken and, upon further inspection, the program was gone from my bin (the only program I lost in this way).

Downloaded the tars for the CLI and GUI again, put them in /usr/bin/, my desktop shortcut fires up the GUI, but I'm getting the exact same freeze when trying to rip. 

Also can't get mono, but that's a known Hardy bug apparently.

---

### Post by Polygon on 2008-04-26
it might be because it needs some mono package which isnt installed cuase there is some bug with installing mono apparantly

---

### Post by mtgmutton on 2008-04-26
I just finished ripping a DVD. the CLI keeps running even when the GUI freezes... A bit annoying, but bearable...

---

### Post by SlappyPappy on 2008-05-06
Tried the GUI in Gutsy and it loses all its graphics after I start a rip. Not cool.  :confused:

---

### Post by mtgmutton on 2008-05-06
> **SlappyPappy said:**
> Tried the GUI in Gutsy and it loses all its graphics after I start a rip. Not cool.  :confused:

Yeah, it's bothersome... I suggest setting a "system monitor" on one of your panels. When it's ripping, it will use all of your CPU. When it is done, there will be a dramatic decrease in CPU use. That is when it is done. Force the application to quit and go into the system monitor's task menu thingy. End the CLI part of the application. The file will still be there. It is still annoying, but, as I said, bearable because the program rips properly.

---

### Post by Polygon on 2008-05-06
again, the gui is horribly outdated and depending on what settings you are using, the gui does not pass these to the command like so you get incorrect rips!
'
its much easier to just use the command line and the CLI eqivilants of the presets

[http://trac.handbrake.fr/wiki/BuiltInPresets](http://trac.handbrake.fr/wiki/BuiltInPresets)

---

### Post by elixr on 2008-11-19
I'm trying to install HandbrakeGTK 1.0.1, and it's still trying to overwrite Brasero.Desktop.  Is there any reason it would be trying to touch this file?

EDIT: There is no reason apparent except that whoever packaged it called the file brasero.desktop.  Genius.

Anyway, I found a workaround to open HandbrakeGTK in Ark, then go into data.tar.gz/./usr/share/applications and rename the two files in there, but the problem is, when I do that, the .deb file is open as read only and my changes are not saved.

Any ideas?

---

### Post by Polygon on 2008-11-19
hmm. no idea. you can try the instructions on my blog:

[http://polygon89.wordpress.com/](http://polygon89.wordpress.com/)

thats how i installed it. a few things might be wrong, but check the comments, as i have not gotten around to updating it yet

---

### Post by yavez on 2008-11-19
Has anybody tried the Snapshot build?  It works great this end, full gui, installs flawlessly on Intrepid.  

[http://handbrake.fr/?article=snapshot](http://handbrake.fr/?article=snapshot)

Might save a lot of people from compiling.

---

### Post by Polygon on 2008-11-19
i like the snapshot ones cause they are always fixing bugs left and right, and i dont want to install a static build until the milestone 0.9.0 comes out =P

---

### Post by elixr on 2008-11-19
I ended up removing Brasero, as I don't have a burner installed anyway, but I'd rather correct the issue with the package itself, in case I do eventually get a burner in here.

---

