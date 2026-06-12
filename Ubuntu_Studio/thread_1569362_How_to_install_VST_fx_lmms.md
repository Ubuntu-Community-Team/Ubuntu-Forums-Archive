---
title: "How to install VST fx: lmms ?"
date: 2010-09-06
forum: Ubuntu Studio
---

### Post by vedix on 2010-09-06
Im trying to install some vst effects to the lmms, but the vstfx-gui window is grey (or it shows up normal for half a second then goes grey).

I think maybe i did not install it right, I put the fx .dll in my lmms/vst folder where my instruments are.

Then i saw this comment in a blog:

> Installing an instrument/effect:

Download a VST and export the archive, the DLL file is the VST.
Open LMMS.  In the top menu, click Edit, then click Settings.
Click  in the window that pops up.
Copy the path under VST-PLUGIN DIRECTORY. 

Open your file browser and visit the copied path.  Put only the DLL file in this folder. ** *NOTE* effects must be placed in the root directory**
[http://brycecoulson.com/tutorials/vstinstruments/](http://brycecoulson.com/tutorials/vstinstruments/)

So effects must be in "root"directory,where is that? does anyone know how i will find the right place for my vsteffect?

---

### Post by Pablo_F on 2010-09-06
I think it refers to the root directory of /home/user/lmms/vst, meaning that you must not create subdirectories. So I think you have it right.

I don't use lmms, but I have experience with other hosts for Windows VST's and I can say:

- If needed, rename the file so that it does not contain any space.

- Not all windows VST's work in Linux through wine, at least not out of the box. Sometimes "winetricks allfonts" helps, but not always.


$ wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks) 
$ sh winetricks allfonts 


Which is the effect?, so someone else can test it, maybe with a demo?

And, what is the ouptput of 

$ echo $VST_PATH

Cheers! Pablo

---

### Post by vedix on 2010-09-06
> **Pablo_F said:**
> I think it refers to the root directory of /home/user/lmms/vst, meaning that you must not create subdirectories. So I think you have it right.
ok, i&#314;l keep them there.
> 
I don't use lmms, but I have experience with other hosts for Windows VST's and I can say:

- If needed, rename the file so that it does not contain any space.

- Not all windows VST's work in Linux through wine, at least not out of the box. Sometimes "winetricks allfonts" helps, but not always.


$ wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks) 
$ sh winetricks allfonts 

tried this, nothing happened.
> 
Which is the effect?, so someone else can test it, maybe with a demo?
Glitch v 1.3.05
free VST effect tested with lmms
[http://illformed.org/plugins/glitch/](http://illformed.org/plugins/glitch/)
[http://lmms.sourceforge.net/wiki/index.php?title=Tested_VSTs](http://lmms.sourceforge.net/wiki/index.php?title=Tested_VSTs)

> 
And, what is the ouptput of 

$ echo $VST_PATH

Cheers! Pablo
I dont know what this is but when i run this i get blank line..?


I am running some VSTinstruments in lmms that are working good(sort of, 1 out of 3).
I also tried with OhmBoyz vsteffect, that showed up for a half a second looking just as it should then all of a sudden a grey window showed up..

Setup:
Lucid 10.04
lmms 0.4.7
jack2
wine 1.3.1, win7

---

### Post by Pablo_F on 2010-09-07
Hi, 

I have tested Glitch v 1.3.05. For me:

fst, compiled with the Steinberg headers, it works. Festige too.

vsthost from dssi-vst 0.8, it doesn't.

lmms 0.4.6 in ubuntu karmic, it works.

I have wine-1.1.31

I doubt if setting the VST path will help in your case but it won't hurt. 

Edit ~/.bashrc 

and add this line:

export VST_PATH=/home/your-login-name/lmms/vst : other/paths/to/VST_files (without the spaces)

Logout and login and your vst path will be set. Check with
$ echo $VST_PATH


Another hint: Launch lmms from the terminal and see if there are error messages. 

You can also try updating to LMMS 0.4.8
It seems that there are two VST related problems fixed. See:
[http://sourceforge.net/news/?group_id=105168](http://sourceforge.net/news/?group_id=105168)

Cheers! Pablo

---

### Post by vedix on 2010-09-08
> **Pablo_F said:**
> Hi, 

I have tested Glitch v 1.3.05. For me:

fst, compiled with the Steinberg headers, it works. Festige too.

vsthost from dssi-vst 0.8, it doesn't.

lmms 0.4.6 in ubuntu karmic, it works.

I have wine-1.1.31

I doubt if setting the VST path will help in your case but it won't hurt. 

Edit ~/.bashrc 

and add this line:

export VST_PATH=/home/your-login-name/lmms/vst : other/paths/to/VST_files (without the spaces)

Logout and login and your vst path will be set. Check with
$ echo $VST_PATH


Another hint: Launch lmms from the terminal and see if there are error messages. 

You can also try updating to LMMS 0.4.8
It seems that there are two VST related problems fixed. See:
[http://sourceforge.net/news/?group_id=105168](http://sourceforge.net/news/?group_id=105168)

Cheers! Pablo

Thank you for your replies..

I did try set the path, run lmms from terminal, Glitch did not open, got this message
> unique ID: dG[_
RemotePlugin:: DebugMessage: inputs: 2  output: 2
RemotePlugin:: DebugMessage: creating editor
RemotePlugin:: DebugMessage: editor successfully created
remote plugin died! invalidating now.


The "remote plugin died" shows when I add the path in .bashrc .

I will try the update when the PPA gets updated.

Thanks again.

---

### Post by vedix on 2010-09-10
I now have 0.4.8 and it works!

I also kept the VSTPath,,

Between the crashes and workarounds I might finish of a track at last with lmms.

---

### Post by Tone303 on 2012-01-09
> **vedix said:**
> I now have 0.4.8 and it works!

I also kept the VSTPath,,

Between the crashes and workarounds I might finish of a track at last with lmms.

I have the same exact problem - Loading VST effects results in a blank gray wrapper

This problem exists even with 0.4.12

Yes, VeSTige can load VSTi's

but VST effects no NOT work with LMMS

for 3 years of using linux, i run into constant problems all the time that take hours and hours to research & solve. constant problems, im sick of it. Windows, MAC & Linux are all terrible. There is no half-decent computer experience. Im not going to take two bad things and pretend one is good, Windows and Linux BOTH suck.

---

### Post by sgx on 2012-01-09
Hi, Reaper using wineasio, in an all 32bit system, with a quality
soundcard, is the best way to utilize vst in linux, at present, and actually uses less system resource than native linux software trying to do the same thing.

wine reaper/reaper.exe

You can expect 90% of non-pace, non-ilok, non-dongled vst and vsti,
to work in linux Reaper. Synthmaker plugins, very old plugins,
or poorly coded plugins, make up most of the 10%

What is your focus? Keys, guitar, vocals, drums, whole band?
I'll post some relevant ones that I know to work,
that are both free and excellent. If the latest Reaper 4.xxx
gives you any issues, get V3.76 The installer is less than 6 meg,
and you can install it in /home/username, it all goes in one
folder, and launch it with

wine reaper/reaper.exe

note: after installing wineasio, run the command

regsvr32 wineasio.dll

Then choose that as your asio driver in reaper preferences,
and also in reaper vst preferences, browse to your vst folder,
which reaper will scan, as directed, or automatically,
when new plugins have been added.

Reaper will autoconnect in qjackctl, so you can route it's output
to any other linux software, for recording, or further processing.

For a guitarist wanting a quick jam, Festige will load most of the
many free windows amp-sim and fx plugins. Again, these can be routed
to Guitarix, rakarrack, calf/invada/mda plugins, etc, so specific
favorite combinations are always available. :guitar:

PS, you are right, computer operating systems are evil monsters with
control-freak personalities imposing their will at every turn.
But linux gives us the tools to carve out a personalized system,
and tolerable, if imperfect workflows, the time learning being better spent,
than merely bowing in submission to apple and microsoft, and big-box DAW makers.

Cheers

---

