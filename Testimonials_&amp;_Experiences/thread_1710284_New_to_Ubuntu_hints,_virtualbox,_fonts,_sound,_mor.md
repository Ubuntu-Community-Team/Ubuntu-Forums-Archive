---
title: "New to Ubuntu hints, virtualbox, fonts, sound, more"
date: 2011-03-19
forum: Testimonials &amp; Experiences
---

### Post by flemur13013 on 2011-03-19
I thought I'd share a "Windows to Ubuntu experience": first some BS, and then what I did to install Ubuntu and getting it running as I liked: fonts, sound and windows apps/wine/virtualbox info that might help other new-to-ubuntu guys; things that were pretty simple but weren't documented properly or were just hassles that turned out to be pretty common.

My background: old-time C/UNIX programmer, turned Windows semi-expert.
My machine: a low-end eMachines ET1831-07 (a great buy!), supposedly 10.04 compatible, plus a semi-fancy nVidia graphics card.

1: I'd installed 10.04 a few years ago, dual-boot, and Ubuntu would completely die if I tried "Normal" or "Extra" visual effects (after automagically installing new drivers and "Cancel" didn't work!), also had some sound hassles (different machine).  

10.10 won't demo or install on this machine, but 10.04 did; it also does "Normal" visual effects now, tho I've been too chicken to try "Extra" (I leave it at "None" anyway).  

2: When I tried to use Ubuntu 10.04 in demo mode as a repair disk, it mildly corrupted my NTFS file system and displayed errors while trying to copy some firefox profile-files (of all things...?), and that didn't give me the warm fuzzies about Ubuntu's compatibilty with NTFS.

3: I was always sick of MS's duct-tape-and-baling-wire-works-as-poorly-designed software, and  Win7's ludicrous "junction" implementation and "xsx" files finally broke the camel's back. 

I replace almost all Winos apps, including the "explorer" file browser, the "explorer" internet browser, and even the "explorer" desktop mangler (BBlean rocks & runs fine w/Win7 underneath), and I also replace text editors, defragmenter, disk tools, firewall/security, SW installer, etc,etc, with far better stuff, so I figured it was time to just dump the whole thing.

4: My concerns about Ubuntu/linux were: 
- Availability of applications (they mostly kinda suck compared to the best non-MS windows apps - mostly referring to graphics, sound, video, DVDs), and maybe #2 happening again (it didn't), and the ugly fonts, especially in Firefox.

Installing Ubuntu.
1: In windows I backed-up *everything* to USB disk and deleted/moved NTFS partitions to leave about 100G unused space for Ubuntu+data; I had an NTFS partition w/data that I wanted to save despite backup.  

In a previous install I'd created ext3 and swap partitions in Windows but the Ubuntu installer seemed to ignore them, and made it's own partitions from space in a big NTFS partition, which I didn't want. Note: the installer instructions(GUI) and choices could be clearer! Also, if you make swap too big it silently complains, but install was really pretty simple. 

2: I let Ubuntu create ext and swap partitions and install itself; everything went smoothly.

3: Fonts: Yes, FF looked ugly, often with very tiny text. 

 ++
Font fix 1: Play around with 
- gnome DPI (112), 
- min font size in FF (16 or 18), 
- userChrome.css to change FF GUI fonts (12px,bold,various types), 
- Various fonts in System>Prefs>Appearance>Fonts.

Font fix 2: Install some TTF fonts.  
I've seen complicated instructions for doing this, but it turns out to be real simple:
 a: Copy the .ttf files to /usr/share/fonts/truetype/somename/fontnames.ttf
 b: Run "fc-cache -f -v" and look for errors and reasonableness, and that your new "somename" is  mentioned. The files might have to be owned by root...

Font fix 3: In FF the smaller fonts were still not anti-aliased ("smoothed") despite setting it thru the gnome GUI, so I added this to /home/name/.fonts.conf at the end, after the other anti-aliasing stuff:
 <match target="font">
 <edit mode="assign" name="autohint">
 <bool>true</bool>
 </edit>
 </match>
and then FF looked a lot better.  Not quite as good as in Winos, but pretty close.

Font fix 4: gnome-terminal > rt-click > Profile > Prefs - pick a not default-system font and it'll anti-alias in the terminal and vi, etc.

 ++

SOUND: Playing worked, no recording worked. 

After much screwing around, my fix was to install "pulse" and, **while the app is trying to record**, start Applications>Sound>PulseAudio Volume Control -> Recording, and select the one with "Monitor" in the name.

Windows apps: Wine is pretty half-assed most of the time, so I decided to try VIRUTALBOX.  It was pain to install, mostly because of crummy instructions, but it runs great! VERY easy and fast enough, once you get it there.

I used the version (3.whatever) already listed in Synaptic, and installed it from there and DIDN'T SEE THE ERROR MESSAGES.  It seemed like it installed OK, and started up, but nothing really worked as advertised (or instructed), so I installed it from command line and saw the problem.

So here's my virtualbox install hints:

- If you have errors installing Virtualbox and/or don't get the "First run" GUI, or have other weird problems, look for help with "uname -r" in it: you need to update some linux stuff (pretty easy ... if you know you have to do it).

- YOU HAVE TO INSTALL THE "GUEST ADDITIONS" if you want to "share folders". If you don't share folders, the whole thing is pretty pointless...

Running hints: 

- I start virtualbox, start Windows (XP, couldn't see any reason for 7) from there, pop it to full-screen with the window Maximize button (gnome GUI for virtualbox); then the gnome workspace switcher, menus, etc are still available - much nicer than the "full-screen mode" which gives you a little more space but is a pain to switch from back to gnome.  I never have to "Rt-Ctrl".

- To stop, don't shut-down windows, just exit virtual box and it'll ask what to do: select "Save machine state" and it'll start/stop a lot faster than shutting-down and booting.

- I share one NTFS folder, set up only for that purpose.

- Playing sounds from XP worked without hassle; 
I got recording to work in Virtualbox/Windows by trying to record with Audition in windows, and doing the SOUND/pulse thing up above; FWIW, it saw  "virtualbox" trying to record, not Audition.
I can start Audition, start recording, pause it (don't exit the program), stop/save XP in virtual box as above, and then later start Audition as a recorder just by starting windows, and it'll all start nearly as fast as starting firefox.

Screenshots:
[One]("https://lh4.googleusercontent.com/_FmU-MMrp8qE/TYT4V_rgZ9I/AAAAAAAABIg/KI-ZgoHXge8/Screenshot-virtualbox-1.png")
[Two]("https://lh5.googleusercontent.com/_FmU-MMrp8qE/TYT4Vw9pbUI/AAAAAAAABIk/q50hIrraZvw/Screenshot-virtualbox-2.png")
- or - 
[https://lh4.googleusercontent.com/_FmU-MMrp8qE/TYT4V_rgZ9I/AAAAAAAABIg/KI-ZgoHXge8/Screenshot-virtualbox-1.png](https://lh4.googleusercontent.com/_FmU-MMrp8qE/TYT4V_rgZ9I/AAAAAAAABIg/KI-ZgoHXge8/Screenshot-virtualbox-1.png)
[https://lh5.googleusercontent.com/_FmU-MMrp8qE/TYT4Vw9pbUI/AAAAAAAABIk/q50hIrraZvw/Screenshot-virtualbox-2.png](https://lh5.googleusercontent.com/_FmU-MMrp8qE/TYT4Vw9pbUI/AAAAAAAABIk/q50hIrraZvw/Screenshot-virtualbox-2.png)

Other notes:

The computer is hooked up to a regular TV via the videocard S-video output: to make it work, I installed the "recommended" nVidia driver thru Synaptic (not 173).  I was leery because this has badly screwed-up things before, but not this time.

nVidia had newer drivers but I couldn't get their install method to work (start a term with ctrl-alt-F1, then kill the dektop manager, "sh NVIDIA-whatever.run", etc: ctrl-alt-F-anything locks up this machine!). 

Anyway, the TV out is a nicer than in winos, don't have to lower the main screen's resolution to that of the TV in order to use the TV: it's a viewport into the main window.

I installed kubuntu (KDE 4) out of curiosity but didn't like it.  It was a bit ugly, tho that's fixable, but it didn't like my main "panel" at the top of the screen - KDE left empty room for the panel at the  bottom that full-screen apps didn't cover.  In gnome I put a panel at the top for text (menus, app list) and a panel on the left for more icons, similar to my BBlean setup.

A couple of obnoxious windows-like gnome things: 

- Part of the Workspace Swticher Prefs GUI (workspace names) can be missing in certain standard themes. Does this happen in other places?

- Rt-click "Edit Menus" (Main Menu) won't let you put in empty sub-menus, and silently un-checks them when you try to do something else. Pretty minor, but I wasted a fair amount of time trying to find out why I couldn't add "Debian" and make it stay there!

- If I setup my login via "Login Screen", it doesn't do what I said. This might have started with kubuntu, not sure, fiddling around a lot (add/remove a new user and other crap) after uninstalling kubuntu finally fixed it.

EOF, dudes!

---

### Post by cariboo on 2011-03-19
THis really isn't a support question, moved to T&E

---

