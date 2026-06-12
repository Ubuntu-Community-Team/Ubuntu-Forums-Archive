---
title: "My new MIDI game--what do you think?"
date: 2008-05-22
forum: Ubuntu Studio
---

### Post by srhlefty on 2008-05-22
I'm the author of a game called Piano Odyssey (EDIT: changed the name 23 May 2008 to avoid any potential legal issues of using the 'Hero' moniker).  Starting at release 0.8.1, I have native linux binaries compiled using Gusty (full source code is of course available if you need to compile it for your own platform).

The game is about 95% complete, but I have no idea if it works on other linux machines other than my own.  Will you help me play test the game? (Windows binaries are also downloadable at the site below)

You can get the code at sourceforge:
[http://sourceforge.net/projects/pianoherogl]("http://sourceforge.net/projects/pianoherogl")
The basic requirements to run the game are:
[LIST]
[*]the fltk dev package (libfltk1.1-dev)
[*]the portmidi dev package (libportmidi-dev)
[*]the glut dev package (libglut3-dev)
[*]a MIDI keyboard
[*]a MIDI-to-USB cable[/LIST]

Here is a youtube link that shows one of my relatives playing the game on windows:
[http://www.youtube.com/watch?v=yseqUhyOWNI]("http://www.youtube.com/watch?v=yseqUhyOWNI")

As of right now, the package comes with four songs which you can play on Easy, Medium, Hard, or Expert.  Just like Guitar Hero, at the easiest levels you don't have to play as many notes.  However since this is a piano, higher levels introduce extra difficulty through hand motion; on Expert, you play every note on the sheet music (unlike Guitar Hero).

The four songs I have so far:
[LIST]
[*]La Candeur, by Burgmuller
[*]Fur Elise, by Beethoven
[*]Super Mario Bros 1 (Underwater Theme)
[*]Zelda 1 (Dungeon Theme)[/LIST]

---

### Post by robeast on 2008-05-23
I downloaded the source (I'm on 64studio) but how do I compile it?

---

### Post by srhlefty on 2008-05-23
Hmm, in retrospect I should have made it a bit easier to compile by hand.  I've included in the source package project files for the Eclipse IDE.  Each of the subdir's has the hidden files .cdtbuild, .cdtproject, and .project.  If you've got Eclipse and the Eclipse plugin CDT (for developing C/C++ programs), you can open the PianoOdysseyGL source folder as a workspace (EDIT: described below)

Does this make sense?  I used an IDE because I'm not a big fan of command-line stuff, yet ironically the make/make install method is much easier to tell people about! ;)

---

### Post by warbread on 2008-05-23
This is a fantastic idea.  I can think of no better way to teach someone the piano.

You should fully expect further from me once I've played with this for a few hours.  I'll toy with it this weekend.

---

### Post by srhlefty on 2008-05-23
> **robeast said:**
> I downloaded the source (I'm on 64studio) but how do I compile it?

Here's a list of steps it takes to compile the program from source: (I realize this isn't the easiest way, but if you intend to hack around in a program I feel IDE's are much better suited).

EDIT: I split this up into two posts due to the 8-image restriction.

[LIST=1]
[*]Load Eclipse, selecting the PianoOdysseyGL 'src' folder as the workspace
[IMG]http://webfiles.uci.edu/hunts/public/step1.png[/IMG]

[*]Go to the workbench, if you're not there already
[IMG]http://webfiles.uci.edu/hunts/public/step2.png[/IMG]

[*]Change to the C/C++ perspective
[IMG]http://webfiles.uci.edu/hunts/public/step3.png[/IMG]

[*]File->Import, choose General->Existing projects into workspace
[IMG]http://webfiles.uci.edu/hunts/public/step4.png[/IMG]
[IMG]http://webfiles.uci.edu/hunts/public/step5.png[/IMG]

continued below...
[/LIST]

---

### Post by srhlefty on 2008-05-23
second half of the instructions:



[LIST=1]
[*]Navigate to the folder where the source is (make sure "Copy projects into workspace" is checked)
[IMG]http://webfiles.uci.edu/hunts/public/step6.png[/IMG]
[*]All the projects will begin compiling in the "Debug" configuration
[IMG]http://webfiles.uci.edu/hunts/public/step7.png[/IMG]
[*]Select the PianoOdyssey project
[IMG]http://webfiles.uci.edu/hunts/public/step7.5.png[/IMG]
[*]Change the build configuration to "Release"
[IMG]http://webfiles.uci.edu/hunts/public/step8.png[/IMG]
[*]Allow the build process to complete.  It may take a minute or so, and should compile with no errors if you have the appropriate libraries installed.
[*]Your PianoOdysseyGL directory should now have a shiny new game executable!
[IMG]http://webfiles.uci.edu/hunts/public/step9.png[/IMG]
[/LIST]

---

### Post by Stochastic on 2008-05-23
Reminds me of Frets on Fire: [http://fretsonfire.sourceforge.net/screenshots/](http://fretsonfire.sourceforge.net/screenshots/)

You might want to take a look at their source code to see what might work to port to yours.

---

### Post by srhlefty on 2008-05-23
> **Stochastic said:**
> Reminds me of Frets on Fire: [http://fretsonfire.sourceforge.net/screenshots/](http://fretsonfire.sourceforge.net/screenshots/)

You might want to take a look at their source code to see what might work to port to yours.

You're right, that game is in a similar vein, as is Synthesia.

However from what I gather Frets on Fire is for your PC keyboard and targets guitar players, while mine uses MIDI interaction and targets piano players.  

I'm hoping that the two projects have dissimilar enough goals that mine won't have to compete against such an impressive program :)

---

### Post by srhlefty on 2008-05-24
> **warbread said:**
> This is a fantastic idea.  I can think of no better way to teach someone the piano.

You should fully expect further from me once I've played with this for a few hours.  I'll toy with it this weekend.

Great!  Can't wait to hear how it goes :)

---

### Post by robeast on 2008-05-24
Thanks for the compile instructions. I may end up simply downloading the Ubuntu package because if I install Eclipse, it would be in Hardy anyway (I'm still keeping it around for non-audio stuff). I don't want to weigh down 64studio; it's running lean and mean right now.

---

### Post by srhlefty on 2008-05-24
> **robeast said:**
> Thanks for the compile instructions. I may end up simply downloading the Ubuntu package because if I install Eclipse, it would be in Hardy anyway (I'm still keeping it around for non-audio stuff). I don't want to weigh down 64studio; it's running lean and mean right now.

Luckily, I found out that Eclipse generates makefiles for me.  I'll include them in the next release, but for now, here is a _very dirty_ shell script that will perform all the commands that the makefile does, but without any checking for errors. :)

After the script finishes, if there were no build errors all the executables will appear in the root PianoOdysseyGL folder.

PS: I'm pretty sure Eclipse runs in a self-contained folder.  Is it java that would end up weighing your system down?

```
#!/bin/bash


#**** Build of configuration Release for project libglpng ****
cd libglpng
mkdir Release
cd Release
echo "Building file: ../glpng.c"
gcc -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"glpng.d" -MT"glpng.d" -o"glpng.o" "../glpng.c"
echo "Building file: ../zlib/adler32.c"
gcc -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"zlib/adler32.d" -MT"zlib/adler32.d" -o"zlib/adler32.o" "../zlib/adler32.c"
echo "Building file: ../zlib/crc32.c"
gcc -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"zlib/crc32.d" -MT"zlib/crc32.d" -o"zlib/crc32.o" "../zlib/crc32.c"
echo "Building file: ../zlib/infblock.c"
gcc -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"zlib/infblock.d" -MT"zlib/infblock.d" -o"zlib/infblock.o" "../zlib/infblock.c"
echo "Building file: ../zlib/infcodes.c"
gcc -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"zlib/infcodes.d" -MT"zlib/infcodes.d" -o"zlib/infcodes.o" "../zlib/infcodes.c"
echo "Building file: ../zlib/inffast.c"
gcc -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"zlib/inffast.d" -MT"zlib/inffast.d" -o"zlib/inffast.o" "../zlib/inffast.c"
echo "Building file: ../zlib/inflate.c"
gcc -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"zlib/inflate.d" -MT"zlib/inflate.d" -o"zlib/inflate.o" "../zlib/inflate.c"
echo "Building file: ../zlib/inftrees.c"
gcc -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"zlib/inftrees.d" -MT"zlib/inftrees.d" -o"zlib/inftrees.o" "../zlib/inftrees.c"
echo "Building file: ../zlib/infutil.c"
gcc -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"zlib/infutil.d" -MT"zlib/infutil.d" -o"zlib/infutil.o" "../zlib/infutil.c"
echo "Building file: ../zlib/zutil.c"
gcc -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"zlib/zutil.d" -MT"zlib/zutil.d" -o"zlib/zutil.o" "../zlib/zutil.c"
echo "Building file: ../png/png.c"
gcc -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"png/png.d" -MT"png/png.d" -o"png/png.o" "../png/png.c"
echo "Building file: ../png/pngerror.c"
gcc -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"png/pngerror.d" -MT"png/pngerror.d" -o"png/pngerror.o" "../png/pngerror.c"
echo "Building file: ../png/pngget.c"
gcc -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"png/pngget.d" -MT"png/pngget.d" -o"png/pngget.o" "../png/pngget.c"
echo "Building file: ../png/pngmem.c"
gcc -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"png/pngmem.d" -MT"png/pngmem.d" -o"png/pngmem.o" "../png/pngmem.c"
echo "Building file: ../png/pngpread.c"
gcc -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"png/pngpread.d" -MT"png/pngpread.d" -o"png/pngpread.o" "../png/pngpread.c"
echo "Building file: ../png/pngread.c"
gcc -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"png/pngread.d" -MT"png/pngread.d" -o"png/pngread.o" "../png/pngread.c"
echo "Building file: ../png/pngrio.c"
gcc -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"png/pngrio.d" -MT"png/pngrio.d" -o"png/pngrio.o" "../png/pngrio.c"
echo "Building file: ../png/pngrtran.c"
gcc -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"png/pngrtran.d" -MT"png/pngrtran.d" -o"png/pngrtran.o" "../png/pngrtran.c"
echo "Building file: ../png/pngrutil.c"
gcc -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"png/pngrutil.d" -MT"png/pngrutil.d" -o"png/pngrutil.o" "../png/pngrutil.c"
echo "Building file: ../png/pngset.c"
gcc -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"png/pngset.d" -MT"png/pngset.d" -o"png/pngset.o" "../png/pngset.c"
echo "Building file: ../png/pngtrans.c"
gcc -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"png/pngtrans.d" -MT"png/pngtrans.d" -o"png/pngtrans.o" "../png/pngtrans.c"
echo "Building target: libglpngPH.a"
ar -r "libglpngPH.a"  ./glpng.o  ./zlib/adler32.o ./zlib/crc32.o ./zlib/infblock.o ./zlib/infcodes.o ./zlib/inffast.o ./zlib/inflate.o ./zlib/inftrees.o ./zlib/infutil.o ./zlib/zutil.o  ./png/png.o ./png/pngerror.o ./png/pngget.o ./png/pngmem.o ./png/pngpread.o ./png/pngread.o ./png/pngrio.o ./png/pngrtran.o ./png/pngrutil.o ./png/pngset.o ./png/pngtrans.o   
mv libglpngPH.a ../../lib/libglpngPH.a
cd ../../

#**** Build of configuration Release for project libTimer ****
cd libTimer
mkdir Release
cd Release
echo "Building file: ../timers.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"timers.d" -MT"timers.d" -o"timers.o" "../timers.cpp"
echo "Building target: libTimer.a"
ar -r "libTimer.a"  ./timers.o   
mv libTimer.a ../../lib/libTimer.a
cd ../../

#**** Build of configuration Release for project libFontContainer ****
cd libFontContainer
mkdir Release
cd Release
echo "Building file: ../FontChar.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"FontChar.d" -MT"FontChar.d" -o"FontChar.o" "../FontChar.cpp"
echo "Building file: ../FontContainer.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"FontContainer.d" -MT"FontContainer.d" -o"FontContainer.o" "../FontContainer.cpp"
echo "Building target: libFontContainer.a"
ar -r "libFontContainer.a"  ./FontChar.o ./FontContainer.o   
mv libFontContainer.a ../../lib/libFontContainer.a
cd ../../

#**** Build of configuration Release for project libPHContentManager ****
cd libPHContentManager
mkdir Release
cd Release
echo "Building file: ../PHContentManager.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"PHContentManager.d" -MT"PHContentManager.d" -o"PHContentManager.o" "../PHContentManager.cpp"
echo "Building target: libPHContentManager.a"
ar -r "libPHContentManager.a"  ./PHContentManager.o   
mv libPHContentManager.a ../../lib/libPHContentManager.a
cd ../../

#**** Build of configuration Release for project FontCreate ****
cd FontCreate
mkdir Release
cd Release
echo "Building file: ../FontCreate.cxx"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"FontCreate.d" -MT"FontCreate.d" -o"FontCreate.o" "../FontCreate.cxx"
echo "Building file: ../gldisplay.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"gldisplay.d" -MT"gldisplay.d" -o"gldisplay.o" "../gldisplay.cpp"
echo "Building target: FontCreate"
g++ -L../../lib -o"FontCreate"  ./FontCreate.o ./gldisplay.o   -lfltk -lfltk_gl -lFontContainer -lPHContentManager -lglpngPH
mv -f FontCreate ../../../
cd ../../

#**** Build of configuration Release for project FontTest ****
cd FontTest
mkdir Release
cd Release
echo "Building file: ../FontTest.cxx"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"FontTest.d" -MT"FontTest.d" -o"FontTest.o" "../FontTest.cxx"
echo "Building file: ../gldisplay.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"gldisplay.d" -MT"gldisplay.d" -o"gldisplay.o" "../gldisplay.cpp"
echo "Building target: FontTest"
g++ -L../../lib -o"FontTest"  ./FontTest.o ./gldisplay.o   -lfltk -lfltk_gl -lFontContainer -lPHContentManager -lglpngPH
mv -f FontTest ../../../
cd ../../

#**** Build of configuration Release for project KeyImages ****
cd KeyImages
mkdir Release
cd Release
echo "Building file: ../interface.cxx"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"interface.d" -MT"interface.d" -o"interface.o" "../interface.cxx"
echo "Building target: KeyImages"
g++ -L../../lib -o"KeyImages"  ./interface.o   -lfltk -lfltk_gl -lPHContentManager -lglpngPH
mv KeyImages ../../../
cd ../../

#**** Build of configuration Release for project MidiTest ****
cd MidiTest
mkdir Release
cd Release
echo "Building file: ../MidiTest.cxx"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"MidiTest.d" -MT"MidiTest.d" -o"MidiTest.o" "../MidiTest.cxx"
echo "Building file: ../pm_stuff.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"pm_stuff.d" -MT"pm_stuff.d" -o"pm_stuff.o" "../pm_stuff.cpp"
echo "Building target: MidiTest"
g++  -o"MidiTest"  ./MidiTest.o ./pm_stuff.o   -lfltk -lportmidi -lporttime
mv -f MidiTest ../../../
cd ../../

#**** Build of configuration Release for project PianoOdyssey ****
cd PianoOdyssey
mkdir Release
cd Release
echo "Building file: ../Animate.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"Animate.d" -MT"Animate.d" -o"Animate.o" "../Animate.cpp"
echo "Building file: ../FileList.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"FileList.d" -MT"FileList.d" -o"FileList.o" "../FileList.cpp"
echo "Building file: ../FontCtrl.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"FontCtrl.d" -MT"FontCtrl.d" -o"FontCtrl.o" "../FontCtrl.cpp"
echo "Building file: ../GLcommon.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"GLcommon.d" -MT"GLcommon.d" -o"GLcommon.o" "../GLcommon.cpp"
echo "Building file: ../GameStateMachine.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"GameStateMachine.d" -MT"GameStateMachine.d" -o"GameStateMachine.o" "../GameStateMachine.cpp"
echo "Building file: ../HeroSongRender.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"HeroSongRender.d" -MT"HeroSongRender.d" -o"HeroSongRender.o" "../HeroSongRender.cpp"
echo "Building file: ../HiScore.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"HiScore.d" -MT"HiScore.d" -o"HiScore.o" "../HiScore.cpp"
echo "Building file: ../MidiSetup.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"MidiSetup.d" -MT"MidiSetup.d" -o"MidiSetup.o" "../MidiSetup.cpp"
echo "Building file: ../ReadSongFile.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"ReadSongFile.d" -MT"ReadSongFile.d" -o"ReadSongFile.o" "../ReadSongFile.cpp"
echo "Building file: ../SongFolder.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"SongFolder.d" -MT"SongFolder.d" -o"SongFolder.o" "../SongFolder.cpp"
echo "Building file: ../StateDetailedStats.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"StateDetailedStats.d" -MT"StateDetailedStats.d" -o"StateDetailedStats.o" "../StateDetailedStats.cpp"
echo "Building file: ../StateGameplay.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"StateGameplay.d" -MT"StateGameplay.d" -o"StateGameplay.o" "../StateGameplay.cpp"
echo "Building file: ../StateGameplayMenu.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"StateGameplayMenu.d" -MT"StateGameplayMenu.d" -o"StateGameplayMenu.o" "../StateGameplayMenu.cpp"
echo "Building file: ../StateMainMenu.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"StateMainMenu.d" -MT"StateMainMenu.d" -o"StateMainMenu.o" "../StateMainMenu.cpp"
echo "Building file: ../StatePostSong.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"StatePostSong.d" -MT"StatePostSong.d" -o"StatePostSong.o" "../StatePostSong.cpp"
echo "Building file: ../StatePracticeOptions.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"StatePracticeOptions.d" -MT"StatePracticeOptions.d" -o"StatePracticeOptions.o" "../StatePracticeOptions.cpp"
echo "Building file: ../StatePreSong.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"StatePreSong.d" -MT"StatePreSong.d" -o"StatePreSong.o" "../StatePreSong.cpp"
echo "Building file: ../StateSelectDifficulty.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"StateSelectDifficulty.d" -MT"StateSelectDifficulty.d" -o"StateSelectDifficulty.o" "../StateSelectDifficulty.cpp"
echo "Building file: ../StateSongSelect.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"StateSongSelect.d" -MT"StateSongSelect.d" -o"StateSongSelect.o" "../StateSongSelect.cpp"
echo "Building file: ../StateStats.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"StateStats.d" -MT"StateStats.d" -o"StateStats.o" "../StateStats.cpp"
echo "Building file: ../StateTitleScreen.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"StateTitleScreen.d" -MT"StateTitleScreen.d" -o"StateTitleScreen.o" "../StateTitleScreen.cpp"
echo "Building file: ../art.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"art.d" -MT"art.d" -o"art.o" "../art.cpp"
echo "Building file: ../fiai.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"fiai.d" -MT"fiai.d" -o"fiai.o" "../fiai.cpp"
echo "Building file: ../globals.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"globals.d" -MT"globals.d" -o"globals.o" "../globals.cpp"
echo "Building file: ../main.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"main.d" -MT"main.d" -o"main.o" "../main.cpp"
echo "Building file: ../pianoheroUI.cxx"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"pianoheroUI.d" -MT"pianoheroUI.d" -o"pianoheroUI.o" "../pianoheroUI.cxx"
echo "Building file: ../queues.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"queues.d" -MT"queues.d" -o"queues.o" "../queues.cpp"
echo "Building file: ../queues_class.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"queues_class.d" -MT"queues_class.d" -o"queues_class.o" "../queues_class.cpp"
echo "Building target: PianoOdyssey"
g++ -L../../lib -o"PianoOdyssey"  ./Animate.o ./FileList.o ./FontCtrl.o ./GLcommon.o ./GameStateMachine.o ./HeroSongRender.o ./HiScore.o ./MidiSetup.o ./ReadSongFile.o ./SongFolder.o ./StateDetailedStats.o ./StateGameplay.o ./StateGameplayMenu.o ./StateMainMenu.o ./StatePostSong.o ./StatePracticeOptions.o ./StatePreSong.o ./StateSelectDifficulty.o ./StateSongSelect.o ./StateStats.o ./StateTitleScreen.o ./art.o ./fiai.o ./globals.o ./main.o ./pianoheroUI.o ./queues.o ./queues_class.o   -lfltk -lfltk_gl -lFontContainer -lPHContentManager -lglpngPH -lTimer -lportmidi -lporttime
mv -f PianoOdyssey ../../../
cd ../../

#**** Build of configuration Release for project SongEdit ****
cd SongEdit
mkdir Release
cd Release
echo "Building file: ../GLcommon.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"GLcommon.d" -MT"GLcommon.d" -o"GLcommon.o" "../GLcommon.cpp"
echo "Building file: ../HandElement.cxx"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"HandElement.d" -MT"HandElement.d" -o"HandElement.o" "../HandElement.cxx"
echo "Building file: ../HeroHandLine.cxx"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"HeroHandLine.d" -MT"HeroHandLine.d" -o"HeroHandLine.o" "../HeroHandLine.cxx"
echo "Building file: ../HeroNoteLine.cxx"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"HeroNoteLine.d" -MT"HeroNoteLine.d" -o"HeroNoteLine.o" "../HeroNoteLine.cxx"
echo "Building file: ../HeroSongRender.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"HeroSongRender.d" -MT"HeroSongRender.d" -o"HeroSongRender.o" "../HeroSongRender.cpp"
echo "Building file: ../KeyDetect.cxx"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"KeyDetect.d" -MT"KeyDetect.d" -o"KeyDetect.o" "../KeyDetect.cxx"
echo "Building file: ../KeyboardPick.cxx"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"KeyboardPick.d" -MT"KeyboardPick.d" -o"KeyboardPick.o" "../KeyboardPick.cxx"
echo "Building file: ../KeyboardPick2.cxx"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"KeyboardPick2.d" -MT"KeyboardPick2.d" -o"KeyboardPick2.o" "../KeyboardPick2.cxx"
echo "Building file: ../NoteElement.cxx"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"NoteElement.d" -MT"NoteElement.d" -o"NoteElement.o" "../NoteElement.cxx"
echo "Building file: ../ReadImagesCfg.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"ReadImagesCfg.d" -MT"ReadImagesCfg.d" -o"ReadImagesCfg.o" "../ReadImagesCfg.cpp"
echo "Building file: ../ReadSongFile.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"ReadSongFile.d" -MT"ReadSongFile.d" -o"ReadSongFile.o" "../ReadSongFile.cpp"
echo "Building file: ../art.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"art.d" -MT"art.d" -o"art.o" "../art.cpp"
echo "Building file: ../globals.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"globals.d" -MT"globals.d" -o"globals.o" "../globals.cpp"
echo "Building file: ../midi.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"midi.d" -MT"midi.d" -o"midi.o" "../midi.cpp"
echo "Building file: ../queues.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"queues.d" -MT"queues.d" -o"queues.o" "../queues.cpp"
echo "Building file: ../queues_class.cpp"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"queues_class.d" -MT"queues_class.d" -o"queues_class.o" "../queues_class.cpp"
echo "Building file: ../ui.cxx"
g++ -O3 -Wall -c -fmessage-length=0 -MMD -MP -MF"ui.d" -MT"ui.d" -o"ui.o" "../ui.cxx"
echo "Building target: SongEdit"
g++ -L../../lib -o"SongEdit"  ./GLcommon.o ./HandElement.o ./HeroHandLine.o ./HeroNoteLine.o ./HeroSongRender.o ./KeyDetect.o ./KeyboardPick.o ./KeyboardPick2.o ./NoteElement.o ./ReadImagesCfg.o ./ReadSongFile.o ./art.o ./globals.o ./midi.o ./queues.o ./queues_class.o ./ui.o   -lfltk -lfltk_gl -lFontContainer -lPHContentManager -lglpngPH -lportmidi -lporttime -lTimer
mv -f SongEdit ../../../
cd ../../
 
echo "Build process complete"

```

---

### Post by srhlefty on 2008-05-30
Hi guys I hope this makes it easier for you to get my game compiled.  Piano Odyssey 0.8.3 has just been released.  Eclipse is no longer required to build the game.  The project now uses automake & friends, and so there's no excuse not to give it a try ;)

This release also includes two new songs, the Bubble Bobble theme (from the old Nintendo game) and a finger exercise from the classic Hanon book.

I'm interested in hearing if it compiles and installs for you (or if it doesn't).

---

### Post by AppleSeed2010 on 2008-08-05
Hi,

I'm on ubuntu 64bits, and no compilation is possible. Tested with src for 8.3 and 8.5 : same error. 'configure' is ok, but 'make'...


> KeyboardPick2.cxx: In member function «Fl_Double_Window* KeyboardPick2::make_dlg(KeyboardPick2*)»:
KeyboardPick2.cxx:905: erreur: cast from «KeyboardPick2*» to «int» loses precision
make[1]: *** [KeyboardPick2.o] Erreur 1
make[1]: quittant le répertoire « /media/500-1/Downloads/PianoOdysseyGL/src/SongEdit »
make: *** [all-recursive] Erreur 1

Bye.

---

### Post by srhlefty on 2008-08-05
> **AppleSeed2010 said:**
> Hi,

I'm on ubuntu 64bits, and no compilation is possible. Tested with src for 8.3 and 8.4 : same error. 'configure' is ok, but 'make'...

Bye.

Thanks for posting this.  I see what the problem is--on a 64-bit machine, pointers are no longer the same size as an 'int'.  I'm not very familiar with 64-bit data types, so I'll look up a proper solution and fix the code.  

Unless of course, someone can tell me off the top of their head what the built-in data type is called for 64-bit integers on linux systems?

---

### Post by srhlefty on 2008-08-05
> **AppleSeed2010 said:**
> Hi,

I'm on ubuntu 64bits, and no compilation is possible. Tested with src for 8.3 and 8.5 : same error. 'configure' is ok, but 'make'...

Bye.


Hi,
I have fixed the issue that was causing the compile error.  The changes will appear in the next released version (which is coming as soon as I get around to packaging it).  For the adventurous, I have attached the patch files that will correct the source code.

Please let me know if these correct or don't correct the problem on a 64-bit system!

-Steve

---

### Post by AppleSeed2010 on 2008-08-06
Hello, 
Thanks for the reply ^^

It seem that i need to wait for the next release :lolflag:


> 
$ patch SongEdit/KeyboardPick2.cxx KeyboardPick2.cxx.patch.txt 
(Stripping trailing CRs from patch.)
patching file SongEdit/KeyboardPick2.cxx
Hunk #1 FAILED at 745.
Hunk #2 FAILED at 928.
Hunk #3 FAILED at 957.
Hunk #4 FAILED at 1053.
4 out of 4 hunks FAILED -- saving rejects to file SongEdit/KeyboardPick2.cxx.rej


Good night.

---

### Post by srhlefty on 2008-08-06
> **AppleSeed2010 said:**
> Hello, 
Thanks for the reply ^^

It seem that i need to wait for the next release :lolflag:

Good night.

I think the problem with those files might be the way I generated the patches.  I used WinMerge, which gives a ton of different ways to generated patchs: "Normal", "Context", and "Unified"; the latter two have 6 sub-styles.  I just picked one and hoped that linux's patch command would figure it out.  Maybe not all those methods are compatible.

---

### Post by srhlefty on 2008-08-06
> **AppleSeed2010 said:**
> Hello, 
Thanks for the reply ^^

It seem that i need to wait for the next release :lolflag:

Good night.

No more waiting necessary.  The next release was all ready to go anyway, so I went ahead and packaged it.  Version 0.9.0 is now [live at sourceforge]("http://sourceforge.net/project/showfiles.php?group_id=226595&package_id=274228&release_id=618261") [[http://sourceforge.net/project/showfiles.php?group_id=226595&package_id=274228&release_id=618261](http://sourceforge.net/project/showfiles.php?group_id=226595&package_id=274228&release_id=618261)]

Hiscores save properly now, and there's no longer any post-install tweaking to be done.

---

### Post by sun2z_emily on 2008-08-07
hello!

i had just downloaded the source and tried compiling it.
make runs without problem, but make install (actually i used checkinstall) ends up with error

```

make  install-exec-hook
make[3]: Entering directory `/home/shani/Sources/PianoOdysseyGL'
touch /usr/local/share/pianoodyssey/.PH.sco && chmod a=rw /usr/local/share/pianoodyssey/.PH.sco
chmod: changing permissions of `/usr/local/share/pianoodyssey/.PH.sco': No such file or directory
make[3]: *** [install-exec-hook] Error 1
make[3]: Leaving directory `/home/shani/Sources/PianoOdysseyGL'
make[2]: *** [install-exec-am] Error 2
make[2]: Leaving directory `/home/shani/Sources/PianoOdysseyGL'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/shani/Sources/PianoOdysseyGL'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK
```

I don't know what to do.

---

### Post by srhlefty on 2008-08-07
> **sun2z_emily said:**
> hello!

i had just downloaded the source and tried compiling it.
make runs without problem, but make install (actually i used checkinstall) ends up with error

```

make  install-exec-hook
make[3]: Entering directory `/home/shani/Sources/PianoOdysseyGL'
touch /usr/local/share/pianoodyssey/.PH.sco && chmod a=rw /usr/local/share/pianoodyssey/.PH.sco
chmod: changing permissions of `/usr/local/share/pianoodyssey/.PH.sco': No such file or directory
make[3]: *** [install-exec-hook] Error 1
make[3]: Leaving directory `/home/shani/Sources/PianoOdysseyGL'
make[2]: *** [install-exec-am] Error 2
make[2]: Leaving directory `/home/shani/Sources/PianoOdysseyGL'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/shani/Sources/PianoOdysseyGL'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK
```

I don't know what to do.


Hi,
So what's supposed to happen at that point in the install process is that a file called .PH.sco is created at /usr/local/share/pianoodyssey/, hence the command
```
touch /usr/local/share/pianoodyssey/.PH.sco
```
Then, it changes the permissions to be writable by everybody, since it's the hiscore file:
```
chmod a=rw /usr/local/share/pianoodyssey/.PH.sco
```

I'm not sure why the touch command did not actually create the file, did you execute make checkinstall without root permissions?  In the script I'm assuming that people run it with the regular 'sudo make install', so maybe that is the cause.  I can't say for sure, since I'm not a makefile expert.

---

### Post by sun2z_emily on 2008-08-08
nevermind that. i installed using make install and it works fine.
perhaps it's a problem with checkinstall

But apparently the notes will stuck, i could press a key, and the star will show up, but then the star will stay greyed out and i cannot press any more of the same key.
I use the midi test program, note on and note off are detected correctly, so i dont know what is the problem.

---

### Post by srhlefty on 2008-08-08
> **sun2z_emily said:**
> nevermind that. i installed using make install and it works fine.
perhaps it's a problem with checkinstall

But apparently the notes will stuck, i could press a key, and the star will show up, but then the star will stay greyed out and i cannot press any more of the same key.
I use the midi test program, note on and note off are detected correctly, so i dont know what is the problem.


Ok, this is great feedback.  Based on that, I am pretty confident I know what is happening:

In the midi test program, when testing the note on/off messages I'm looking at the entire allowed range.  The midi spec says note on can have any code between 0x90 and 0x9F, while note off can have any code between 0x80 and 0x8F.

There's a flaw in the game's midi code since I wrote that section of code earlier, so after looking at it just now the values appear to still be hard-coded to what my keyboard returns :lolflag:

I could have not found this bug myself, since I have only one keyboard :)

The fix is trivial, but it is late for me, so I will do it tomorrow and post a patch (this time using the linux diff command so that I get a proper patch file! :D)

---

### Post by srhlefty on 2008-08-08
> **sun2z_emily said:**
> nevermind that. i installed using make install and it works fine.
perhaps it's a problem with checkinstall

But apparently the notes will stuck, i could press a key, and the star will show up, but then the star will stay greyed out and i cannot press any more of the same key.
I use the midi test program, note on and note off are detected correctly, so i dont know what is the problem.

Hi,
Attached is a patch for the file MidiSetup.cpp in the PianoOdyssey game source (i.e. PianoOdysseyGL/PianoOdyssey/MidiSetup.cpp)

I think that this should fix your problem.  I tested the patch command with this file, and it doesn't throw errors this time ;)  Let me know how it goes.

```
patch MidiSetup.cpp patch.txt
```

---

### Post by musiloco on 2008-08-17
Very nice game.
I was looking for something like this!
I have Ubuntu in all my machines except for one for MIDI, my usb EMU does not work in Linux :(
So, I installed it in Windows and it is working great.
Now, I also have a MIDI drums (Yamaha DD 55). It is possible to have some drum songs?

Thanks and keep this great job!

---

### Post by srhlefty on 2008-08-17
> **musiloco said:**
> Very nice game.
I was looking for something like this!
I have Ubuntu in all my machines except for one for MIDI, my usb EMU does not work in Linux :(
So, I installed it in Windows and it is working great.
Now, I also have a MIDI drums (Yamaha DD 55). It is possible to have some drum songs?

Thanks and keep this great job!

Glad to hear it's working for you!

In order to make a drum song, or a song for any other instrument for that matter, I would need some way of allowing the user to set the MIDI program number (i.e. instrument).  The most natural place for that value would be the song file itself.  That would be an easy thing for me to add.

The next question I have is, what note does a MIDI drum set send?  Maybe different drum kits use different notes, and so making a drum song with particular notes would not work for all sets (of course, you could use the Song Editor to make your own songs! :))

Also, the game is set up to draw the notes over the keyboard.  It might be visually confusing--the player has to remember things like "C3 corresponds to my left drum", for example.

Any suggestions about those topics?

---

### Post by AppleSeed2010 on 2008-08-21
Hello,

Patch + compiling + checkinstall (with a little mkdir mkdir /usr/local/share/pianoodyssey/) OK.

I have a little error after a play :

```

practice mode: leave to PracticeOptions or MainMenu
	warning: unable to open hiscore file for reading.
	Attempted location was "/home/apple80464/Downloads/PianoOdysseyGL/.PH.sco"
loaded hiscore file

```

/home/apple80464/Downloads/PianoOdysseyGL is my src folder (for compiling)

After each startup, i need to choose the keyimages.cfg and midi config. Is here a way to save it ???

A little feature request, it would be great if we can use the mouse in the menu to configure it :guitar:

Great job, and sorry for the testing delay.
Good night.

---

### Post by srhlefty on 2008-08-21
Hi,
> **AppleSeed2010 said:**
> Patch + compiling + checkinstall (with a little mkdir mkdir /usr/local/share/pianoodyssey/) OK.
Thanks for the report.  I'm very happy to hear that the game compiles and runs on a 64-bit installation! :):)

> **AppleSeed2010 said:**
> I have a little error after a play :

```

practice mode: leave to PracticeOptions or MainMenu
	warning: unable to open hiscore file for reading.
	Attempted location was "/home/apple80464/Downloads/PianoOdysseyGL/.PH.sco"
loaded hiscore file

```

/home/apple80464/Downloads/PianoOdysseyGL is my src folder (for compiling)

This is fixable by simply creating the file it's looking for, in the right place:
```
touch /home/apple80464/Downloads/PianoOdysseyGL/.PH.sco
```
It's an artifact of using the checkinstall target over the regular install target--my automake files need to be fixed :)

> **AppleSeed2010 said:**
> After each startup, i need to choose the keyimages.cfg and midi config. Is here a way to save it ???
This is an annoying problem, I agree.  I haven't yet figured out a cross-platform way of saving preferences.  On windows I could use the registry, on linux I suppose there's gconf.  I'm open to suggestions.

> **AppleSeed2010 said:**
> A little feature request, it would be great if we can use the mouse in the menu to configure it :guitar:
I see where you're coming from on this point.  It's a good idea, but it goes against my original design goal: to make it as "arcade-y" as possible; so that once you start the game, you never have to touch your computer again.  I will consider it though, but I won't make any promises :)

---

### Post by srhlefty on 2008-08-21
> **srhlefty said:**
> 
This is an annoying problem, I agree.  I haven't yet figured out a cross-platform way of saving preferences.  On windows I could use the registry, on linux I suppose there's gconf.  I'm open to suggestions.


Silly me!  I forgot that FLTK has a built-in preferences class designed for just such an occasion.  I'll get right on it...

---

### Post by srhlefty on 2008-09-01
I've just released version 0.9.1 onto the sourceforge page.

0.9.1 incorporates the 64-bit compatibility patch above, as well as introducing automatic saving of which artwork file the user chose last time the game was launched.

Note that the artwork file changed locations, from the root pianoodyssey folder to the pianoodyssey/art folder.

Thank you to everyone who has tried it out so far!  Keep the feedback coming, I really appreciate it.

---

### Post by AppleSeed2010 on 2008-09-14
Compilation Ok
art/default.cfg Ok

Need ability to import midi file now ^^.

Good job.

---

### Post by srhlefty on 2008-09-17
Yeah being able to import a MIDI file into the song editor would be nice.  For me the step that takes the longest to do when creating songs is entering the Expert level notes.  It'll take a fair amount of work though.

---

### Post by nine tails on 2008-10-21
This is what I try to find :D thank you very much :p

---

