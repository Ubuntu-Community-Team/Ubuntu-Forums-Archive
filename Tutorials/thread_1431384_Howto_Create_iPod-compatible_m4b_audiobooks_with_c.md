---
title: "Howto: Create iPod-compatible m4b audiobooks with chapters and cover"
date: 2010-03-16
forum: Tutorials
---

### Post by crabman on 2010-03-16
This guide is intended to show how to create m4b audiobook files, complete with chapter markers, cover, tags and iPod-compatible. It is based on my python-based tool M4Baker:

[http://code.google.com/p/m4baker/]("http://code.google.com/p/m4baker/")

[SIZE="3"]Description:[/SIZE]
A simple tool for creating ipod-compatible, full-featured m4b-audiobooks. Based on SoX, faac and mp4v2.

[SIZE="3"]Features:[/SIZE]

    * make chapter markers
    * add cover picture from various filetypes
    * change and add metadata
    * on the fly conversion
    * batch mode
    * support for many different input file types
    * sort input files by filename or id3-tag (tracknumber)
    * split audiobooks into parts automatically
    * move chapters between audiobooks 

As this program is primary for educational purposes, any suggestions and critics regarding my code are very welcome.

[SIZE="3"]Dependencies:[/SIZE]
python, sox, faac, mp4v2 (inclusive utils, i.e mp4chaps and mp4tags) pyqt and Qt
For the CLI mode please use version 0.1.2 since it was removed in 0.1.90

M4Baker is NOT a KDE but a Qt-app like e.g. vlc, so you wont need kde and it integrates nicely into every Desktop.


[SIZE="5"]1 Install[/SIZE]

Install the dependencies, on ubuntu 10.04 lucid run:

```
sudo aptitude install build-essential checkinstall mpeg4ip-utils sox faac python-qt4 libsox-fmt-all
```

Download, build and install mp4v2:

```
wget [http://mp4v2.googlecode.com/files/mp4v2-1.9.1.tar.bz2](http://mp4v2.googlecode.com/files/mp4v2-1.9.1.tar.bz2)
tar -xf mp4v2-1.9.1.tar.bz2
cd mp4v2-1.9.1
./configure
make
sudo checkinstall
cd
```

Install m4baker:

```
wget [http://m4baker.googlecode.com/files/m4baker-0.1.91.tar.gz](http://m4baker.googlecode.com/files/m4baker-0.1.91.tar.gz)
tar -xf m4baker-0.1.91.tar.gz
cd m4baker-0.1.91/
sudo checkinstall python setup.py install
```

It is now save to remove the downloaded tarballs and the created directories. checkinstall and build-essential can be uninstalled as they are not needed anymore.

[SIZE="5"]2 Rip[/SIZE]

Skip this step if the audiobook CD is already ripped.

Once m4baker is installed, rip your audibook cd using your favorite software. If enough harddisk space (700MB per CD) is availible, i suggest ripping to .wav files. If not, .mp3 will do the job, too.

[SIZE="5"]3 Convert to m4b[/SIZE]

   1. start "m4baker" from the "Applications-> Sound & Video" Menu. For the command line interface, run "m4baker -h" in a terminal. 

   2. click "Add", mark all soundfiles that should be includes in the book, additional files can be added later. Every file will become a single chapter. The files id3tags are read automatically. If no tags are found, file information is guessed from the filename.

   3. sort, rename, remove or add chapters as you wish. Adjust the audiobooks metadata and add a cover file. Set the ouput filename if the automatically generated one does not please you. Experienced users can adjust faacs quality settings in the faac command line. If no changes are made here faacs standard settings are used. These should be fine for most purposes. If needed, the book can be automatically split into parts. The upper limit is 10 hours which should work with all iPod models. Hit Ok now. 

If you have more audiobooks that should be processed, add them as described in steps 1 to 3. It is possible to edit or remove an audiobook from the process queue.

Hit "Process" and get a coffee. Depending on the number of files and audiobooks to process this might take a long time, so one coffee might not be enough. In this case, get a sixpack beer instead.

[SIZE="5"]4 Transfer to iPod or play[/SIZE]

The finished m4b files can be played by most software players. As far as i know, vlc is the only linux software that can show and hanlde chapter makers.

For adding the chapters to your ipod use gtkpod > 0.99.14 with aac support. To install gtkpod run

```
sudo aptitude install gtkpod-aac
```

enjoy your audiobooks on your iPod! 

crabman

EDIT: adjust to new version 0.1.2
EDIT: adjust to new version 0.1.90
EDIT: adjust to new version 0.1.91

---

### Post by tareksobh on 2010-04-08
Crabman, thank you so much for this application. I've been forever looking for a Mp3 M4b converter that supports chapters marking for the iPod. Thanks to you, this application is perfect and with the help of your tutorial, everything seems to run smoothly. I was able to install M4Baker and I'm currently converting an audiobook for testing. I'll write back when it's done. I have a great feeling about it.

---

### Post by crabman on 2010-04-13
great to hear, let me know if you encountered any bugs or have ideas for new features

crabman

---

### Post by Superju55i on 2010-04-13
You Sir, should receive the Nobel Prize in awesome. 
I too have been looking a long time for something like this. The instructions worked great as well.

Vielen dank, and enjoy your sixpack.

---

### Post by nowayoutofhere on 2010-04-14
I've been using M4Baker for a couple of weeks now with good results - thanks for writing a great program :)

I want to report an issue that is causing me problems, maybe you can do something about it in future releases... Files that are longer than 13 hours, 15 mins and 17 seconds won't play properly on ipod. I've been manually spltting my longer books into roughly 10 hour m4b files, but in order to not mess up the chapter times this involves loading all tracks into the gui and removing a lot of them individually.  I've just done Stephen King's It and it took nearly half an hour to arrange for 4 m4b output files with chapters properly timed.

So for long books, an option for M4Baker to automatically split into several output files would be fantastic; failing this, even being able to select and remove multiple files at once in the gui would make life much easier than pressing the remove button hundreds of times.

Keep up the good work!

---

### Post by pearlzilla on 2010-04-16
Hi.

I am getting the following error when I try to run m4baker.  What am I doing wrong?

```
black@black-laptop:~/m4baker-0.1.1$ m4baker
starting in GUI mode
Traceback (most recent call last):
  File "/usr/local/bin/m4baker", line 2, in <module>
    from m4baker.m4baker import main; main()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/m4baker.py", line 145, in main
    gui()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/m4baker.py", line 53, in gui
    ui = MainWindow()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/ui/mainwindow.py", line 68, in __init__
    self.setupUi(self)
  File "/usr/local/lib/python2.6/dist-packages/m4baker/ui/Ui_mainwindow.py", line 53, in setupUi
    self.progressBar.setProperty("value", 0)
TypeError: argument 2 of QObject.setProperty() has an invalid type

```

---

### Post by crabman on 2010-04-17
@ nowayoutofhere
thanks for the hint, ill have a look at this issue, it will be fixed in the next release. How big is a 13 hour m4b file? Im asking because i was wondering if it might be able to reach the 4gb limit of the fat32 ipod filesystem.

@pearlzilla
The error occurs while setting up the gui. Which version of pyqt are you using?

crabman

---

### Post by Asitaka on 2010-05-10
I tried using your software to make a file with bookmarks, and while it did combine all of my mp3s into a single audiobook, which shows up in the iphone's audio book section, it didn't make any chapters. I have a m4b and a txt file with chapter information I assume.

---

### Post by crabman on 2010-05-11
> **Asitaka said:**
> I tried using your software to make a file with bookmarks, and while it did combine all of my mp3s into a single audiobook, which shows up in the iphone's audio book section, it didn't make any chapters. I have a m4b and a txt file with chapter information I assume.

There are two possible reasons for this:

1. There was no chapter info written to the m4b:
To check this, open the file with a recent version of vlc and check if vlc recognizes the chapters.
If vlc does not find any chapters, something went wrong while writing the chapter info to the m4b file. Please start M4Baker from a terminal, process the same audiobook again and post the output and the resulting .txt file here so i can fix this.

2. Your iphone doesnt recognize the chapters:
If you can see the chapters in vlc, there must have gone something wrong during the transfer of the m4b file to your iphone. Make sure you used the VERY latest versions of gtkpod/libgpod or itunes. ANY other software will lead to the iphone not displaying the chapters. If it still fails, this might be a case for the libgpod/gtkpod developers.

Thanks for your feedback,

crabman

---

### Post by Asitaka on 2010-05-12
I made a new file using the gui and command prompt, no problems, though I don't understand why a text file is left behind. I deleted the text file and loaded it into VLC and it worked, all 100 chapters. Then when I copied it to the iPhone, I got no chapters. Do I need to change any file settings when I copy? or something special? I'm using gtkpod 0.99.14 and using libgpod 0.7.2, from the help. I installed gtkpod before I installed gtkpod-aac, could that be the problem?

---

### Post by crabman on 2010-05-12
The text file is needed by mp4chaps which writes the chapter markers to the m4b file. Earlier versions deleted the file afterwards but before releasing i forgot to uncomment the regarding line in the code - so its a bug and its safe to delete the txt file.

Your ploblem seems to be related to gtkpod/libgpod. Maybe because you use an iphone as for iphones the libgpod development is lagging behind sometimes (the devs dont get enough free iphones to work on :)). You should go to [http://www.gtkpod.org/](http://www.gtkpod.org/) and look for bugs or ask the developers via their mailing list. Im afraid i can cant help you with that problem, sorry.

crabman

---

### Post by Asitaka on 2010-05-13
I loaded the iPhone in rhythmbox and copied the m4b file from it to try transferring from a coworkers iTunes. iTunes threatened to wipe my iPhone since it wasn't synced with that PC so I quit, but when I checked the phone, the files had moved to a folder called audible inside the audiobooks section and all the chapters were listed. I'm not sure if it was the brief exposure to iTunes or rhythm box but your program works great for me, thanks for developing it and supporting we who mangle things

---

### Post by crabman on 2010-05-13
youre welcome!
The problem is that you use rytmbox for transferring the file you HAVE to youse gtkpod to make it work. 
The ipod cannot read any metadata itself, so gtkpod/rythmbox/itunes has to extract the metadata (title, artist, chapters) and give it to the ipod seperately. As of today (afaik) gtkpod is the only program which can read and handle chapter data. All other programs (rythmbox, banshee, amarok, songbird...) will make the ipod not recognize the chapters.
Probably connecting the ipod to itunes fixed the problem.

crabman

---

### Post by Asitaka on 2010-05-13
I used gtkpod to transfer, but nothing happened until I loaded it in rythmbox and itunes.

I haven't found a solution yet, but I reckon it's because of this 'Extended info disabled' error

---

### Post by tomhare on 2010-05-14
When I unzipped m4baker I just got m4baker.py so I tried to set that up but then it said:

only the filetypes supported by soxi are supported input files. According to your sox install these are:
.8svx .aif .aifc .aiff .aiffc .al .amb .au .avi .avr .caf .cdda .cdr .cvs .cvsd .cvu .dat .dvms .f32 .f4 .f64 .f8 .fap .ffmpeg .flac .fssd .gsm .hcom .htk .ima .ircam .la .lpc .lpc10 .lu .m4a .mat .mat4 .mat5 .maud .mp2 .mp3 .mp4 .mpg .nist .ogg .paf .prc .pvf .raw .s1 .s16 .s2 .s24 .s3 .s32 .s4 .s8 .sb .sd2 .sds .sf .sl .smp .snd .sndfile .sndr .sndt .sou .sox .sph .sw .txw .u1 .u16 .u2 .u24 .u3 .u32 .u4 .u8 .ub .ul .uw .vms .voc .vorbis .vox .w64 .wav .wavpcm .wmv .wv .wve .xa .xi

any ideas?

---

### Post by pearlzilla on 2010-05-19
I'm not sure, how do I check?

---

### Post by crabman on 2010-05-24
@ tomshare: You run m4baker in CLI mode, right? seems there is something wrong with the parsing of the arguments. What was your complete command, incl args and options?

@ pearlzilla: try "apt-cahe show python-qt4" (not 100% sure because i dont have an ubuntu system around to check)

---

### Post by pbasil on 2010-06-08
Hi guys,

I think I have the same issue as tomhare

That's what happens

:~/m4baker$ ls
baseclasses.py  baseclasses.pyc  __init__.py  m4baker.py  ui

:~/m4baker$ sudo python m4baker.py install --optimize=1
Usage: m4baker.py [options] input_file1 [input_file2 ...] OR m4baker.py [options] for GUI mode

m4baker.py: error: no such option: --optimize

I am running on 
:~/m4baker$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"

Hope you can help. I can not wait to test it. It seems what I've been looking for a long while :p

---

### Post by crabman on 2010-06-08
try
```
sudo python setup.py install --optimize=1
```
instead of
```
sudo python m4baker.py install --optimize=1
```
and it will install correctly

the m4baker.py is the actual program while the setup.py is the installer.

crabman

---

### Post by Xero Xenith on 2010-06-13
Thank you, been looking for something like this for quite some time! A very useful tool indeed. Thank you very much :)

---

### Post by crunchyx on 2010-06-27
Just used m4baker, this frontend program is great. Thanks Crabman.

---

### Post by Clopy on 2010-07-07
For all the people that are having trouble finding the setup.py file, it's inside the directory where you untarred it. Don't go inside the m4baker directory.

---

### Post by besnef on 2010-07-08
This worked great to create a chaptered m4b.  However I am not seeing the cover art on my ipod.  

I tried by using the gui mode first specifying a jpg file for the cover (170x170 pixels); this did create a .png but when I loaded the file onto the ipod (using gtkpod) the cover art was not showing.  I tried the same thing with a different set of files and got the same result.  

I then tried using CLI mode, specifying the .png file created by the first process as the cover but when I loaded it onto the ipod the cover art was still missing.

I'd like to determine whether the problem is with the file or with the transfer to the ipod (or some combination).  Is there any way to check the cover art short of loading it onto the device?  This would be the equivalent to opening the file in vlc to check the chapter data.

Any ideas? Is there anything obvious that I am doing wrong?

---

### Post by crabman on 2010-07-09
@ besnef: you can use mp4art --list <your_audiobook>.m4b to check if the file contains a cover art file.

Please tell me if m4baker causes the error so i can fix it.

Crabman

---

### Post by besnef on 2010-07-09
Thank you for the information.

I checked the .m4b files and they did not contain cover art.  I was able to use mp4art -add to add the cover art and then it did appear on the ipod.

The issue does seem to be when the m4b file is created.  

I'll take a look at that this evening and see if I can tell anything else about what is happening.

---

### Post by crabman on 2010-07-09
Thats good to know. Currently m4baker uses "mp4tags -P cover.png" to add the cover.

Could you check if manually adding the cover using mp4tags fails on your audiobook file?

---

### Post by besnef on 2010-07-09
I tried
```
mp4tags -P cover.png audiobook.m4b

```
without success but
```
 mp4art --add cover.png audiobook.m4b

```
works fine.

I had originally wondered whether spaces in the filenames might have affected it but renaming the files produced the same result.

---

### Post by k3lt01 on 2010-07-10
I've installed m4baker on my 2 main machines, and may I say it is a brilliant program. It worked except for 2 things, this is on my 2 machines:
1. I get a job queue set up and start it working when it is finished it never completes more than 1/2 of the jobs in the queue.
2. I set it up to do another series of jobs and it fails immediately yet it creates the relevant chapter text files and thumbnails.

I have re-installed it completely on my laptop but to no avail, it still wont complete anymore jobs. I have gone looking for the "missing" m4b files thinking it may have created them but not put them where I asked it to and I noticed it has locked the mp3 files it was supposed to use to create the m4b audiobooks.

---

### Post by k3lt01 on 2010-07-11
Any thoughts or suggestions on what is happening with m4baker on my machines?

Like I said it is a brilliant program as the m4b files it did make are excellent, but I would like to do more with it if I can.

---

### Post by k3lt01 on 2010-07-12
Just thought I'd let you know I went to try it again on my desktop but the menu entry  in Applications > Sound & Video has disappeared. It did that on my laptop the other day but it returned after a reboot, no such luck on my desktop unfortunately. I can get it to start using a terminal though. It still wont complete a job now though.

I also tried it again on my laptop but it still wont complete a job.

Looking for any help you can provide, if you want any more details please don't hesitate to ask.

---

### Post by crabman on 2010-07-12
@ besnef: thanks for your help. The next release of m4baker will use mp4art instead of mp4tags which should fix this bug.

@ k3lt01:
I wasnt able to reproduce this bug.
Please run m4baker from the terminal and post the output here after it has failed.
What exactly happens when you try to run a job that fails? Does the entire ui hang, at which percentage does the progressbar stop, or is simply no valid m4b file created?
Have you tried other input files? it seems like there is a problem during the reencoding.
Do you use any uncommon filenames such as special characters or very long names?

The disappearing of the icons must be a problem with your machine, try to reinstall m4baker.

crabman

---

### Post by k3lt01 on 2010-07-12
> **crabman said:**
> What exactly happens when you try to run a job that fails?I click on Process, a second later the job list disappears.
> **crabman said:**
> Does the entire ui hang, at which percentage does the progressbar stop, or is simply no valid m4b file created?No percentage happens at all. The job list now simply disappears about 1 second after I click Process. It does create valid chapter txt files and even album covr art files but no m4b file at all.
> **crabman said:**
> Have you tried other input files? it seems like there is a problem during the reencoding.I have tried various files on 2 separate machines. A file that is processed on first use on one machine will not process on 2nd use on another.
> **crabman said:**
> Do you use any uncommon filenames such as special characters or very long names?The files have come from Librivox and yes some are long file names but no out of the ordinary characters. Like I said a file that was produced on 1 machine on the programs first use would not be produced on another machine on its 2nd use.
> **crabman said:**
> The disappearing of the icons must be a problem with your machine, try to reinstall m4baker.If it was on 1 machine only I would definitely agree, but, on 2 machines that are setup differently?

I will do the rest in the morning and get back to you.

---

### Post by theshadowx on 2010-07-14
hi, thanks for this titurial,
I have some issues here what i get from the terminal:

theshadowx7@theshadowx:~$ m4baker
starting in GUI mode
Traceback (most recent call last):
  File "/usr/local/bin/m4baker", line 2, in <module>
    from m4baker.m4baker import main; main()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/m4baker.py", line 172, in main
    gui()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/m4baker.py", line 51, in gui
    from PyQt4 import QtCore, QtGui
ImportError: /usr/lib/pymodules/python2.6/PyQt4/QtCore.so: undefined symbol: _ZN13QStateMachine22beginSelectTransitionsEP6QEvent

i m in ubuntu 10.04 32bits, so what should i do?

thanks in advance

---

### Post by theshadowx on 2010-07-14
just after i posted i tried

```
sudo m4baker
```

and it worked, :popcorn:

---

### Post by crabman on 2010-07-14
@ theshadowx: There seems to be something wrong with your PyQt install. 

Please dont run any software as root that doesnt explicitly require that. It can be dangerous and harm your system.

I suggest you update your system, if that doesnt help try to reinstall PyQt. Using "sudo m4baker" is definitely a bad idea.

crabman

EDIT: typo

---

### Post by k3lt01 on 2010-07-15
I did a complete re-install following the first post to the letter, apart from the version numbers which are different.

I created a new job list which has never been tried before, the files are from a good known source, i.e. ripped of my own personal CDs.

I started m4baker via terminal, it isn't appearing in my Applications > Sound and video list so the only way I can now operate it is via terminal.

I created the job queue, clicked process, immediately 2 files appeared. The 1st being a chapters txt file and the 2nd being an m4b file. Both files are for different m4bs.

See screenshots for terminal, m4baker, music directory where files should have been created. If you need any other info feel free to ask.

---

### Post by crabman on 2010-07-16
@ k3lt01: Thanks for the detailed description. 
The problem is your mp4v2 install. In the console output in your screenshot are two error messages from mp4chaps and mp4tags which are part of mp4v2. M4baker doesnt contain any routines to handle crashes of these programs, thats why it behaves so strangely.

---

### Post by k3lt01 on 2010-07-16
> **crabman said:**
> @ k3lt01: Thanks for the detailed description. 
The problem is your mp4v2 install. In the console output in your screenshot are two error messages from mp4chaps and mp4tags which are part of mp4v2. M4baker doesnt contain any routines to handle crashes of these programs, thats why it behaves so strangely.I could figure the crash out myself, the difficulty I am having is trying to get m4baker to get past that. Am I correct in assuming then that you have no tips or tricks I could try? When it works it is a brilliant piece of software.

---

### Post by crabman on 2010-07-16
m4baker relies on these programs. mp4chaps is used to add the chapter markers to the m4b file and mp4tags is needed for tags and cover picture. Without these programs m4baker is rather useless. For simply converting the mp3 files to a single .m4b file you can use sox and faac directly:

```
sox chapter_1.mp3 chapter_2.mp3 -t .wav -o - | faac -o output.m4b -

``` (note the two minuses at the end of each command)

instead of specifying every mp3 seperately you can use "*.mp3" if the mp3s are named correctly, such as 001.mp3, 002.mp3 ... 123.mp3

---

### Post by k3lt01 on 2010-07-16
Ok, I'll fiddle with it and see what I can come up with.

What I don't understand is why it will produce 1 of 3 m4b files, when there was no real difference between them.

I'll let you know what I find, if I find anything.
Thanks for the brilliant program.

---

### Post by Digital Magi on 2010-07-21
Thanks for putting this useful app together. I've been using it the last couple of days with no problems.

---

### Post by bocaccio on 2010-07-21
Haven't even started and i love this tutorial!!! I hate when i can't sync my nano because i dont wanna lose my spot on an audio book. So i have to charge it with a 3rd party crappy charger from hong kong that took 3weeks to get here and less than 3dollars to buy!!
 
Thank you i will see if i can apply all this to my ubuntu netbook remix.

---

### Post by crabman on 2010-10-01
The new version 0.1.90 introduces verbose mode. If any problems occur please start m4baker with ```
m4baker --verbose
``` and post the output here.

crabman

---

### Post by Chaelin on 2010-10-04
The progress bar is getting to 99% and then hangining...
 
when I ran it in verbose mode from terminal, the error message is:
 
**AttributeError: 'QString' object has no attribute 'join'**
 
I am running Ubuntu 10.04 with python-qt4 installed...  what am I missing?

---

### Post by crabman on 2010-10-04
oops, that sounds like a bug.

could you attach the entire console output? just copy and paste it to a file.

Thanks,

crabman

---

### Post by Chaelin on 2010-10-04
Sure thing.   Your program is sweet, just need it to complete my processing!  Is this what you need?

```

FAAC: 21650/21670 ( 99%)|   56.7  |   13.8/13.8   |   36.51x | 0.0
FAAC: 21670/21670 (100%)|   56.7  |   13.8/13.8   |   36.52x | 0.0
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/baseclasses.py", line 709, in __encFinished
    self.audiobookList[self.processBooknum].tagChapters()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/baseclasses.py", line 219, in tagChapters
    trimmedOutfileName = re.sub('\..*$',  '',  self.outfileName)
  File "/usr/lib/python2.6/re.py", line 151, in sub
    return _compile(pattern, 0).sub(repl, string, count)
AttributeError: 'QString' object has no attribute 'join'
Segmentation fault
jharbin@ubuntu-pen1:~$

```

Seg fault is due to me closing out the program since it hangs with the error...

Also, on a side note...  when I run it as root (tsk, tsk, tsk), as opposed to my normal user account, the interface looks different without the icons and graphical flair...  is this normal?

---

### Post by Chaelin on 2010-10-04
Let me give you some more messages....

The previous post used source Mp3 with spaces in the name...  If removed the spaces from the source files, ie:  01of52.mp3 and 02of52.mp3, this is the error I get:

```

FAAC: 21650/21670 ( 99%)|   56.7  |   13.9/13.9   |   36.16x | 0.0
FAAC: 21670/21670 (100%)|   56.7  |   13.9/13.9   |   36.18x | 0.0
MP4CHAPS: Importing 2 QuickTime and Nero chapters from file Cressida Cowell - How to be a Pirate.chapters.txt into file "Cressida Cowell - How to be a Pirate.m4b"
optimizing Cressida Cowell - How to be a Pirate.m4b
WARNING: optimize failed: Cressida Cowell - How to be a Pirate.m4b

```The output file and the chapter file that it creates are pulled from the mp3 tags and still have spaces in them..

If I remove the space from the source file names and change the output file name to not have spaces, ie pirate.m4b, I then go back to my original 'join' error:

```

FAAC: 21650/21670 ( 99%)|   56.7  |   13.9/13.9   |   36.26x | 0.0
FAAC: 21670/21670 (100%)|   56.7  |   13.9/13.9   |   36.27x | 0.0
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/baseclasses.py", line 709, in __encFinished
    self.audiobookList[self.processBooknum].tagChapters()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/baseclasses.py", line 219, in tagChapters
    trimmedOutfileName = re.sub('\..*$',  '',  self.outfileName)
  File "/usr/lib/python2.6/re.py", line 151, in sub
    return _compile(pattern, 0).sub(repl, string, count)
AttributeError: 'QString' object has no attribute 'join'
Segmentation fault
jharbin@ubuntu-pen1:~$ 

```Hopefully this is helpful.  Looking forward to a solution!

---

### Post by crabman on 2010-10-04
> Also, on a side note... when I run it as root (tsk, tsk, tsk), as opposed to my normal user account, the interface looks different without the icons and graphical flair... is this normal?

Yep, thats normal. You havent set a style for the root user.

> Hopefully this is helpful. Looking forward to a solution!
Thanks for the output, it helped a lot! I fixed the bug for the next release (beta2), it was just one line i forgot. It will occur everytime you change the output file name.
For the meantime you can work around by not clicking the button for changing the file. Just rename the file after it was created manually.

> WARNING: optimize failed: Cressida Cowell - How to be a Pirate.m4b
can be ignored safely. It is mp4chaps output and you wont notice a difference between optimized files and non-optimized ones.

crabman

---

### Post by crabman on 2010-10-14
@chaelin: The bug was fixed in the new 0.1.91 released today. Please update.

---

### Post by Chaelin on 2010-10-15
Just downloaded and ran through 5 books with no problem.  Thanks for fixing.
 
 
A side-note request.... I am converting from an external hard drive...  each time I go to pick an output file/location or add files, it defaults to my user directory and I have to navigate to my external volume and through the directory structure... kind of a pain each time... so...  for each session, can it remember where you last were when you opened the file dialog?  And for output file, can I have the same file dialog "memory" and/or a checkbox to say to output the output file in the same directory as the source files...

---

### Post by Inanaeroplane on 2010-10-19
> **nowayoutofhere said:**
> I've been using M4Baker for a couple of weeks now with good results - thanks for writing a great program :)

I want to report an issue that is causing me problems, maybe you can do something about it in future releases... Files that are longer than 13 hours, 15 mins and 17 seconds won't play properly on ipod. I've been manually spltting my longer books into roughly 10 hour m4b files, but in order to not mess up the chapter times this involves loading all tracks into the gui and removing a lot of them individually.  I've just done Stephen King's It and it took nearly half an hour to arrange for 4 m4b output files with chapters properly timed.

So for long books, an option for M4Baker to automatically split into several output files would be fantastic; failing this, even being able to select and remove multiple files at once in the gui would make life much easier than pressing the remove button hundreds of times.

Keep up the good work!
I wish I had found you sooner.  I have IT in three audio files, the first keeps breaking exactly where you said it does and I had to buy the book to get fill in the gap.  Great Book!

---

### Post by ryks on 2010-11-27
Hi, I have to say thanks, too. It's really a great and helpful program.
At most audiobooks it works without problems. But I found some strange behaviour.
I have one audiobook with following details
- 36 mp3 files
- titles are named "abschnitt 01" to "abschnitt 36"
- length 7 hours 2 minutes

When adding all of the files to m4baker everything seems to be ok. But after processing the result file does not contain any chapters, not in vlc and not on ipod/iphone. The file itself contains the whole audiobook and is playable but without chapter information. I have another audiobook that shows the same behaviour but also another one with the same title description (21 tracks, title: abschnitt 01 to abschnitt 21, length 5h 18min) that shows the correct chapters from abschnitt 01 to abschnitt 21. While converting I noticed that the progress bar shows percentage values above 100 % up to 1047% and so. If I split the audiobook in two parts, that means, converting the first 18 files and afterwards the other 18 files it shows the right percentage values up to 100%, but the result file does also not have any chapters. The result file size is about 430mb, so file size should not be a problem.
Do you have any idea? Thanks!

---

### Post by crabman on 2010-11-27
which version are you using?
could you run m4baker on the problematic files again starting it with "m4baker --verbose" from console and post the output here? (Just copy and paste from console)

crabman

---

### Post by ryks on 2010-11-28
I used the latest version mp4v2-1.9.1 and m4baker-0.1.91

I think the reason for the mentioned behaviour is the following:

The artist of the audiobook was "steven r. covey" and because of the "." in the artist name mp4chapters created the filename of the chapters file only until the "." that means: "stephen r.chapters.txt" and not "stephen r. covey - die 7 wege zur effektivität.chapters.txt" how it should be because the m4b file had this name. Thatswhy it whas not able to find the corresponding chapter file to the m4b file, could not merge and so there were no chapters.

Here is what the terminal said:

---------------
ERROR: MP4CHAPS: ERROR: opening chapter file 'stephen r. covey - die 7 wege zur effektivität.chapters.txt' failed: **[COLOR=Red]No such file or directory[/COLOR]**
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/baseclasses.py", line 711, in __encFinished
    self.audiobookList[self.processBooknum].tagMeta()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/baseclasses.py", line 262, in tagMeta
    verboseOutput(str(taggerProc.readAllStandardOutput()), str(taggerProc.readAllStandardError()),  u'MP4ART')
  File "/usr/local/lib/python2.6/dist-packages/m4baker/baseclasses.py", line 57, in verboseOutput
    print name + ': ' + standardOutput
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 51: ordinal not in range(128)
Segmentation fault
-----------------------------------

After that I removed the "." in the artist field and tried again. This time it worked.

--------------------------------------
MP4CHAPS: [COLOR=SeaGreen]**Importing 5 QuickTime and Nero chapters from file stephen r covey - die 7 wege zur effektivität.chapters.txt into file "stephen r covey - die 7 wege zur effektivität.m4b"**[/COLOR]
optimizing stephen r covey - die 7 wege zur effektivität.m4b
WARNING: optimize failed: stephen r covey - die 7 wege zur effektivität.m4b
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/baseclasses.py", line 711, in __encFinished
    self.audiobookList[self.processBooknum].tagMeta()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/baseclasses.py", line 262, in tagMeta
    verboseOutput(str(taggerProc.readAllStandardOutput()), str(taggerProc.readAllStandardError()),  u'MP4ART')
  File "/usr/local/lib/python2.6/dist-packages/m4baker/baseclasses.py", line 57, in verboseOutput
    print name + ': ' + standardOutput
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 50: ordinal not in range(128)
------------------------------

In conclusion: It seems that mp4chaps does not allow "." in artist or title field because while creating the chapter file name it thinks the name ends at the position of the first ".". So without any "." in artist or title tag it works fine. It would be cool if this could be corrected so that it creates the whole chapter filename including several ".". 
Are you, crabman, also the author of mp4chaps or should we tell this to somebody else?

nice sunday, ryks

PS: Could you please explain the other warnings in the terminal output: "WARNING: optimize failed" and "UnicodeDecodeError:". It seems not to be a problem but I would like to understand. Thanks!

---

### Post by crabman on 2010-11-28
Thanks for the extensive bug report, ill work on it this week, it should be fixed in the next release.

I think i already explained this optimie warning somewhere here, its not important, you can ignore it.

The unicode decode error is a bug in m4baker. Its already fixed in git.

crabman

---

### Post by ryks on 2010-11-28
thanks for your quick reply.

There is another feature I would appreciate if I could express a wish :-)

The result chapter name of every chapter starts with a number, for example "1 - introduction", "2 - chapter 02" and so on. On iphone the chapterlist has a number for each chapter itself, so it looks like this:

1. 1 - introduction
2. 2 - chapter 02

As you can see the number of the chapter is shown twice. One time as the real chapter number and also in chapter name. Would it be possible to add an option to choose, if I want the chapter number within chapter name or not? In my case while using the iphone it would look better without the chapter number within the chapter name.

Thanks, ryks

---

### Post by crabman on 2010-11-28
This is a problem best to be solved by using a tag edior like easytag or exfalso. M4baker only takes the tracks id3 title tags and uses them as chapter names. It is not meant to edit these tags as other programs can do this much better.

Just fire up easytag, load the mp3 files and tag them as you want the chapter names to appear. In your case remove the "1 - " from the titles. Then save the changes and load the chapter into mp4tag.

crabman

---

### Post by ryks on 2010-11-29
The title tags of my mp3 files do not contain "1 - " or "2 - ". They are  just "introduction" and "chapter 02" for example. First after creating  the m4b-file with m4baker the chapter names get an additional "1 - " or  "2 - ".  So it seems to be added by mp4chaps.

ryks

---

### Post by crabman on 2010-12-02
OK, now i get what you mean.It sounds lie a good idea. Its on my TODO list for 0.2.1

crabman

---

### Post by SadoTron on 2011-01-25
Yet another audiobook creator for ubuntu:[ http://www.ausge.de]("http://www.ausge.de/modules.php?name=Downloads&d_op=getit&lid=6")
Comes with GUI; script written in php. 
May be you like to try this one ;)

(never meant to blast this thread 8-[)

---

### Post by chak8870 on 2011-03-10
Hi Crabman,
This program is fabulous. I have been using it for last one week. It was converting the mp3 files to audiobook file perfectly with the chapter marks. Yesterday, I did a recommended software update on my computer (running lucid lynx) and all of a sudden the audiobooks can't be split. The process is actually halting after sometime. I check the details of recent package upgrade on the synaptic and I found that I have upgraded python-avahi. I am not sure whether that is causing the problem

I ran m4baker --verbose and got the following output. I believe the output is indicating that the python script is not behaving the way it is supposed to behave.

Any help is appreciated. Once again thanks for this wonderful program.

Error Output

 in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 257250/80028 (321%)|   81.2  |  285.1/88.7   |   20.95x | -196.4
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 257300/80028 (321%)|   81.2  |  285.2/88.7   |   20.95x | -196.5
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 257350/80028 (321%)|   81.2  |  285.2/88.7   |   20.95x | -196.5
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 257400/80028 (321%)|   81.2  |  285.3/88.7   |   20.95x | -196.6
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 257450/80028 (321%)|   81.2  |  285.3/88.7   |   20.95x | -196.6
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 257500/80028 (321%)|   81.2  |  285.3/88.7   |   20.95x | -196.7
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 257550/80028 (321%)|   81.2  |  285.4/88.7   |   20.95x | -196.7
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 257600/80028 (321%)|   81.2  |  285.5/88.7   |   20.95x | -196.8
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 257650/80028 (321%)|   81.2  |  285.6/88.7   |   20.95x | -196.9
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 257700/80028 (322%)|   81.2  |  285.6/88.7   |   20.95x | -196.9
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 257750/80028 (322%)|   81.2  |  285.7/88.7   |   20.95x | -197.0
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 257800/80028 (322%)|   81.2  |  285.7/88.7   |   20.95x | -197.0
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 257850/80028 (322%)|   81.2  |  285.8/88.7   |   20.95x | -197.1
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 257900/80028 (322%)|   81.2  |  285.8/88.7   |   20.95x | -197.1
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 257950/80028 (322%)|   81.2  |  285.9/88.7   |   20.95x | -197.2
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 258000/80028 (322%)|   81.2  |  285.9/88.7   |   20.95x | -197.2
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 258050/80028 (322%)|   81.2  |  286.0/88.7   |   20.95x | -197.3
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 258100/80028 (322%)|   81.2  |  286.0/88.7   |   20.95x | -197.3
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 258150/80028 (322%)|   81.2  |  286.1/88.7   |   20.95x | -197.4
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 258200/80028 (322%)|   81.2  |  286.2/88.7   |   20.95x | -197.5
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 258250/80028 (322%)|   81.2  |  286.2/88.7   |   20.95x | -197.5
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 258300/80028 (322%)|   81.2  |  286.3/88.7   |   20.95x | -197.6
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 258350/80028 (322%)|   81.2  |  286.3/88.7   |   20.95x | -197.6
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 258400/80028 (322%)|   81.2  |  286.4/88.7   |   20.95x | -197.7
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 258450/80028 (322%)|   81.2  |  286.4/88.7   |   20.95x | -197.7
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 258500/80028 (323%)|   81.2  |  286.5/88.7   |   20.95x | -197.8
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 258550/80028 (323%)|   81.2  |  286.5/88.7   |   20.95x | -197.8
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 258600/80028 (323%)|   81.2  |  286.6/88.7   |   20.95x | -197.9
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 258650/80028 (323%)|   81.2  |  286.7/88.7   |   20.95x | -198.0
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 258700/80028 (323%)|   81.2  |  286.8/88.7   |   20.95x | -198.1
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 258750/80028 (323%)|   81.2  |  286.8/88.7   |   20.95x | -198.1
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 258800/80028 (323%)|   81.2  |  286.9/88.7   |   20.95x | -198.2
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 258850/80028 (323%)|   81.2  |  286.9/88.7   |   20.95x | -198.2
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 258900/80028 (323%)|   81.2  |  287.0/88.7   |   20.95x | -198.3
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 258950/80028 (323%)|   81.2  |  287.0/88.7   |   20.95x | -198.3
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 259000/80028 (323%)|   81.2  |  287.1/88.7   |   20.95x | -198.4
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 259050/80028 (323%)|   81.2  |  287.1/88.7   |   20.95x | -198.4
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 259100/80028 (323%)|   81.2  |  287.2/88.7   |   20.95x | -198.5
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 259150/80028 (323%)|   81.2  |  287.2/88.7   |   20.95x | -198.5
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 259200/80028 (323%)|   81.2  |  287.3/88.7   |   20.95x | -198.6
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 259250/80028 (323%)|   81.2  |  287.4/88.7   |   20.95x | -198.7
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 259300/80028 (324%)|   81.2  |  287.5/88.7   |   20.95x | -198.7
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 259350/80028 (324%)|   81.2  |  287.5/88.7   |   20.95x | -198.8
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 259400/80028 (324%)|   81.2  |  287.6/88.7   |   20.95x | -198.8
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 259450/80028 (324%)|   81.2  |  287.6/88.7   |   20.95x | -198.9
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 259500/80028 (324%)|   81.2  |  287.6/88.7   |   20.95x | -198.9
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 259550/80028 (324%)|   81.2  |  287.7/88.7   |   20.95x | -199.0
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 259600/80028 (324%)|   81.2  |  287.8/88.7   |   20.95x | -199.1
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 259650/80028 (324%)|   81.2  |  287.9/88.7   |   20.94x | -199.1
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 259700/80028 (324%)|   81.2  |  288.0/88.7   |   20.94x | -199.2
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 259750/80028 (324%)|   81.2  |  288.0/88.7   |   20.94x | -199.3
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 259800/80028 (324%)|   81.2  |  288.1/88.7   |   20.94x | -199.3
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 259850/80028 (324%)|   81.2  |  288.1/88.7   |   20.94x | -199.4
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 259900/80028 (324%)|   81.2  |  288.1/88.7   |   20.94x | -199.4
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 259950/80028 (324%)|   81.2  |  288.2/88.7   |   20.94x | -199.5
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
FAAC: 260000/80028 (324%)|   81.2  |  288.2/88.7   |   20.95x | -199.5
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 503, in dataChanged
    self.populateAudiobookProperties()
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 360, in populateAudiobookProperties
    pixmap = pixmap.scaledToWidth(width)
RuntimeError: underlying C/C++ object has been deleted
Segmentation fault

---

### Post by MikSam on 2011-08-02
Hi!
First, thanks for the great app!
Been testing this out for a few days and ran into some minor problems: I don't seem to get flac - format working, any help on this?
MP3 works fine but since I have _lots_ of audiobooks ripped into flac I'd like to use them directly without the mp3-conversion bonus step in the workflow.

Running a 64 bit system, if that matters.

Here's my console output when trying to add flac - file into audiobook:
```
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/m4baker/mainWindow.py", line 158, in on_actionAddAudiobook_triggered
    newbook = audiobook([chapter(element) for element in fnames])
  File "/usr/local/lib/python2.6/dist-packages/m4baker/baseclasses.py", line 69, in __init__
    self.setFile(filename)
  File "/usr/local/lib/python2.6/dist-packages/m4baker/baseclasses.py", line 98, in setFile
    self.title = re.match(r'(\/.*\/)?(.*?).mp3$', filename).groups()[1]
AttributeError: 'NoneType' object has no attribute 'groups'

```

---

### Post by linfidel on 2012-02-13
Does this work with 11.10?  I tried to get it going, but I can't get past an error message on running it (menu or commandline) that says 
"Missing dependency: mp4chaps is not properly installed. 
 Please read INSTALL.txt 
 Exiting."


I read the file, and I seem to have all the dependencies in the right versions; I didn't see any errors during the builds, and I do see a mp4chaps script in the mp4v2-1.9.1 directory.


I'd love to get this working, as I listen to a lot of audiobooks.  I can convert individual mp3s, but it would be nice to have the additional features of this program.

---

### Post by IanW on 2012-02-22
Works perfectly this way.

```

1: For Precise, ensure the "Universe" repo is enabled, or for Oneiric, add "ppa:jonasped/ppa"
2: Install mp4-utils
3: Follow download and build instructions on the m4baker wiki
4: Launch m4baker from the dash
5: (optional) Right-click m4baker's icon in the Unity bar & tick "Keep in Launcher"

```

---

### Post by suntchan on 2012-09-03
Hello,

I am trying to use your software but have the following error : 

ERROR: SOX: sox FAIL sox: Input files must have the same # channels

Is there anything I can do ?

Thank you!

---

