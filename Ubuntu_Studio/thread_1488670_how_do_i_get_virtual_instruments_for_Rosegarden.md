---
title: "how do i get virtual instruments for Rosegarden?"
date: 2010-05-20
forum: Ubuntu Studio
---

### Post by Beowulf.1000 on 2010-05-20
Help! I am a noob with music on linux. I am used to Windows and Cubase, Sibelius, Garritan Personal Orchestra, Komplete 6 -- all using VSTs as  virtual instruments for my Windows music composition software. 

I am totally lost in linux. I installed Ubuntu 10.4 amd64 yesterday and it actually installed a version of Rosegarden installed with a 'real time processing' kernel (never was able to achieve that before), but now i have absolutely no idea how to get some virtual instruments to use with Rosegarden; as is, Rosegarden comes with just a piano. I know I need some type of DSSI virtual instruments or plugins, but that is all I know. Where do I download free virtual instruments for Rosegarden/linux, and where do I put them in the filesystem?

---

### Post by pdxken on 2010-05-20
I use qsynth with fluid-soundfont-gm. Both can be installed with synaptic.
Synaptic installed fluid-soundfont-gm as FluidR3_GM.sf2 in /usr/share/sounds/sf2/ on my system. Qsynth will want to know where to find the soundfont when you set it up.

This is for Lucid. Karmic and previous were a little different as I recall.

Qsynth can be setup with multiple synth engines. You can set these up with any .sf soundfont I believe.

Rosegarden will also talk to other synths such as zynaddsubfx, Aeolus, Timidity, etc. These are easy to connect through Qjackctl.

See ustudio community info at [https://help.ubuntu.com/community/UbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio)

Have fun.:)
Ken.

---

### Post by sgx on 2010-05-20
Hi, the best vst option is to install wine and wineasio from synaptic, to
use Reaper, the daw that by far, works best with vsts in linux.
then run these commands from a terminal, after installing wine and wineasio. 

Open a terminal. $ is the user prompt, # is the root user prompt) 

wineprefixcreate    (this makes your windows file structure similar to this: /home/beowulf/.wine/drive_c/Program Files  )

regsvr32 wineasio.dll   (this gets you an asio driver) 

The 'change directory' command is cd, so

cd /home/beowulf/.wine/drive_c/Program*Files  (Note the * must fill all spaces in windows paths/titles that you use in commands. 

Now that you are at $Program Files, use mkdir to create these folders

mkdir Steinberg  then

cd Steinberg    then

mkdir VstPlugins

Now download and install Reaper to your
/home/beowulf folder. 

This is done by the simple command    wine name-of-installer

Now, install your vst collection, use installer defaults, .dll and .fxb files you can just copy to VstPlugins. I have installed a few NI demos, the service center works as it should, only Pace or ilok or dongleware plugins usually fail.

to start reaper, from a new terminal, first start jackd

jackd -d alsa -r 44100     then
 
wine reaper/reaper.exe

Now go to reaper prefs and configure as desired

wineasio will appear in its vst prefs Device page, and then you show reaper what folders to scan for plugins.

Then the typical daw learning-re-learning curve begins. In Reaper, right and left and middle click all widgets and empty spaces to reveal their popup dialogues, and of course the menu nests

This should get you going, so take a deep breath, the power and freedom
will be worth the effort! :)
Cheers

---

### Post by Beowulf.1000 on 2010-05-21
Thanks. I am going to try that, because I want some native linux music composition programs and vsts to play with. I also installed virtualbox with Windows XP and was able to install and run Cubase LE, going to install Cubase SE today and see if that works; I also have the full version of Cubase 5, but will first try SE. Sibelius 6 demo installed in virtualized WinXP but I can't get my legal full version of Sibelius 6 to install, just see a blue box on the screen during attempt to install, frustrating because it installed just fine in previous version of Virtualbox. But virtualbox is blowing my mind, I also installed and ran Sony ACID Pro 6 and Sony VEGAS Pro 8 and they run great.  I also own KOMPLETE 6 which if I can get that running in virtualbox will be sweeeeet. But I do want to get some native linux apps working. Will try your suggestions, thank you!.

---

### Post by thorgal on 2010-05-21
[OT]
I would advocate against using the wildcard * to replace spaces in unix filenames for obvious reasons.
Instead you can use the proper unix way for the terminal to understand spaces as valid characters in filenames, namely the backslash \

so instead of 
```

cd a directory of yours

```

you would write

```

cd a\ directory\ of\ yours

```

[/OT]

---

### Post by sgx on 2010-05-21
[user@localhost ~]$ cd .wine/drive_c/Program\ Files
[user@localhost Program Files]$

That works nicely. Thanks! 

In the context of linux audio, I never use the *
except when using cd for changing wine paths, or using the wine command to start a windows installer, or standalone windows app with spaces in the title. So my unix things are pretty safe.
Cheers

---

