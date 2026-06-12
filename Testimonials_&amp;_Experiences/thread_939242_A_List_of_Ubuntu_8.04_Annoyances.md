---
title: "A List of Ubuntu 8.04 Annoyances"
date: 2008-10-05
forum: Testimonials &amp; Experiences
---

### Post by yman on 2008-10-05
I know I should write bug reports, but I just hate going through that process, so instead I post my little list here. Maybe I'll get around to it later. Anyway, I figure that keeping this list to myself isn't doing good to anyone, so I'm posting it. If anyone can help, that's great. If not, I'll just continue working around these problems and changing my habits to accommodate them. That's not ideal, but even with these annoyances, Ubuntu is so convenient and comfortable that it's worth it.

This is a fresh install on an HP Pavilion dv2910us. Ubuntu is the sole OS on this computer. Anything else that was here previously has been wiped out.

Anyway, here is the list:
[LIST=1]
[*] "key presses repeat when key is held down" is checked but doesn't work:
	[LIST=1]
	[*] On a fresh install.
	[*] After playing Funguloids.* - (Bug #278904)
	[/LIST]
[*] The mouse cursor feels sluggish:
	[LIST=1]
	[*] When using the Touch Pad.
	[*] When playing Glest.
	[/LIST]
[*] Totem doesn't play audio while Adobe Flash is using audio. In the case of totem-xine, it always freezes after a few seconds or if interacting with the GUI. - Installing libflashsupport fixes this.
[*] Some of the icons, especially that of Pidgin, occasionally become invisible in the System Tray.
[*] The Main Menu lags behind in updating it's contents after it is edited.
[*] Transmission doesn't always react properly when using it to open a torrent file through Firefox 3.0. - Either completely or partially fixed upstream. The fix will be included in Ubuntu 8.10. (Bugs #204184, #257499).
[*] Netbeans debugging API doesn't exist or something. At least that's what the error message says. (Bug #254587).
[*] XShogi should depend on gnushogi, but it doesn't. Without gnushogi, XShogi crashes and burns immediately upon start-up. (Bug #8896)
[*] Package funguloids exists in the repository even though it is missing dependencies and is thus uninstallable.
[*] Glest, Warzone2100, Globulation2, Wesnoth and Funguloids all install with the wrong resolution. In the case of Glest and Funguloids, there is no GUI for setting the screen resolution either, so I had to modify their configuration files by hand.
[*] If the downloads window is open when I close Firefox 3.0, FF forgets all of its tabs.
[*] The interface (main menu) of Funguloids is sluggish.
[*] The Java documentation package should automatically install the documentation instead of asking the user to do so manually.
[*] I can't see other computers in Places -> Network. - This is fixed, but I still can't see Windows shares on Windows computers.
[*] When I switch to static IP address I need to use ifdown and ifup in the CLI.
[*] Where is there a tool allowing me to record video with my webcam? Right now I can record the visual, and I can record the audio, but I can't do both. - There is Cheese, at the very least.
[*] Every so often, when my computer awakes from sleep mode, I get an error saying it failed to suspend, even though it just woke up from a successful suspension.
[*] 2 keys on my keyboard, and 3 buttons on the remote don't seem to work at all. 2 of those 3 buttons are the same as the 2 on the keyboard.
[*] VLC installs with the PulseAudio backend by default, but it doesn't seem to work. I had to install the ALSA backend in order to bring it to working order. - Actually, it may be that I only had to switch to the ALSA backend in the preferences, without having to install vlc-plugin-alsa.
[*] totem-xine doesn't correctly recognize flash video files as flash video files, and thus fails to open them.
[*] totem-gstreamer can't figure out how to play DVDs properly. It only plays the legal notice and that's it.
[*] Inconsistency between the behavior of different (default!) applications:
	[LIST=1]
	[*] totem toggles between fullscreen and windowed mode when double-clicking on the display area. Evince doesn't.
	[/LIST]
[*] "Leave Message" in the locked screen doesn't work - the message doesn't appear on my screen when I log back in.
[*] Ekiga has an ugly, unintuitive, comlplicated interface. Ubuntu needs something simpler and prettier.
[*] openJDK doesn't fully support everything, so at least some Java applications don't work. This includes iVocalize Web Conference 4.whatever (I think that's what it's called), which is just about the only Java app I use.
[*] When starting the computer, the QuickPlay Mute button and the Ubuntu Volume Control are not in sych.
[*] Seeking in Flash videos doesn't work properly (at all?) with totem-gstreamer.
[*] The cursor mark occasionally disappears, like right now while I'm typing this.
[*] totem-gstreamer randomly failed to play some Flash Videos.
[*] VLC and totem-gstreamer were both rendering videos in black and white. This happened out of the blue for no apparent reason and did not repeat after a restart (same for #29). - Seems to be a result of running Cheese - This is weird: I can't reproduce the bug.
[*] When recording in Cheese, the camera occasionally deactivates.
[*] When recording in Cheese, the audio turns on and off, and the video seems to be way too fast.
[*] When seeking in totem-gstreamer with rmvb files, the audio and image get out of sync and the image freezes. (the w32codecs package from medibuntu is  installed). - This only happens when seeking backwards. Everything gets back in order when seeking forwards.
[*] The button in the taskbar doesn't seem to glow anymore when I get new messages in Pidgin.
[*] No audio notifications in Pidgin - Switching it to ALSA fixes this.
[*] I sometimes need to restart Ubuntu after Suspending because wireless stops working.
[*] Mute doesn't seem to work for the earphones, only for the built-in loud-speakers. - Fixed.
[*] Firefox doesn't use the "Open With" dialog to choose an application to use for opening a file type, instead forcing you to brows for an executable in the file manager.
[*]  In Synaptic, when I set it to "Consider recommended packages as dependencies" Synaptic forgets the setting upon logout. (Bug #154349).
[*] In Nautilus, in Icon View, selection works like in selecting a range of cells in a spreadsheet, instead of as expected. The one exception is that when I choose one item and then Shift-click another it selects all items in between.
[/LIST]
*I used the Debian unstable ("Sid") packages for funguloids and all of it's dependencies which are missing from the Ubuntu repositories.

And this is basically all I did in terms of package management. I may have installed more stuff, but then it was all purged:
```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

sudo apt-get install ubuntu-restricted-extras wine cheese inkscape eclipse netbeans jokosher pitivi thoggen virtualbox-ose virtualbox-ose-modules-2.6.24-19-generic totem-xine libdvdcss2 w32codecs graphthing lybniz pioneers gnucash grisbi planner qt4-designer vlc gmountiso

```

The exception is funguloids and its missing dependencies, which were installed from Debian Sid:
```

funguloids_1.06-7_i386.deb
libfreeimage3_3.10.0-1_i386.deb
libmad0_0.15.1b-3_i386.deb
libogremain-1.4.9_1.4.9.dfsg1-1_i386.deb
libopenal1_1.4.272-2_i386.deb
libopenexr6_1.6.1-3_i386.deb
ogre-plugins-cgprogrammanager_1.4.9-1_i386.deb

```

---

### Post by Idefix82 on 2008-10-05
Wow, this is a long list!
Most of the things you have listed seem to be genuine bugs but I would like to comment on some of these things:
24. is a matter of taste and personally I find the interface adequate. I know that this doesn't help you at all but instead of demanding for ekiga to be replaced by something which you find prettier and others uglier, it would be better to make it customizable by skins. But I am sure that you will agree that this can't possibly be high on the priority list, not even of the ekiga developers.
25. OpenJDK is open source, Sun's JRE is not. That I guess is the main reason for OpenJDK being the default JRE. This may change in the future if Sun completely open their code. I think that it is a good guideline to only have open source software as default choices for anything. This will trigger user interest in the software and thus hopefully also fuel development, which can and should result in the removal of the shortcomings you are talking about.
35. I wouldn't list it as a bug strictly speaking since it is well known that different audio architectures work best on different machines. That's the main reason they are all pre-installed. If you can fix a sound issue by switching to ALSA then you are using ALSA exactly the way it was meant to be used.
36. Have you tried switching eth1 (or whatever it is on your system) off and on rather than rebooting? I am sure that whatever it is in the reboot process that gets wireless back to normal can be done by hand without rebooting. If that's the case then you could modify the relevant script which handles the suspend/wakeup routine. It might be worth having a look at it anyway as suggested by 17.

Sorry, I couldn't be of more help.

---

### Post by yman on 2008-10-05
> **Idefix82 said:**
> Wow, this is a long list!
Most of the things you have listed seem to be genuine bugs but I would like to comment on some of these things:
24. is a matter of taste and personally I find the interface adequate. I know that this doesn't help you at all but instead of demanding for ekiga to be replaced by something which you find prettier and others uglier, it would be better to make it customizable by skins. But I am sure that you will agree that this can't possibly be high on the priority list, not even of the ekiga developers.

This was originally meant to be a private list, so you should read it as notes-to-self rather than a list of demands or anything like that.

Aside from that I really think it doesn't fit the look and feel of most other default apps.

And I agree it's not the most urgent thing in the world.

> 
25. OpenJDK is open source, Sun's JRE is not. That I guess is the main reason for OpenJDK being the default JRE. This may change in the future if Sun completely open their code. I think that it is a good guideline to only have open source software as default choices for anything. This will trigger user interest in the software and thus hopefully also fuel development, which can and should result in the removal of the shortcomings you are talking about.

What bothers me is that FF doesn't use the same "Open With" dialog as the file manager. Actually, this calls for an edit of the annoyance list.

> 
36. Have you tried switching eth1 (or whatever it is on your system) off and on rather than rebooting? I am sure that whatever it is in the reboot process that gets wireless back to normal can be done by hand without rebooting. If that's the case then you could modify the relevant script which handles the suspend/wakeup routine. It might be worth having a look at it anyway as suggested by 17.

I tried:

```

sudo ifdown -a
sudo ifup -a

```
as well as restarting the X server, disabling networking via GUI, and turning off the WiFi with the switch. Nothing seemed to work.

> 
Sorry, I couldn't be of more help.
It's the intent that counts, and you gave me food for thought. I say you were a big help, especially in helping me better understand exactly what annoys me and what doesn't.

---

### Post by Idefix82 on 2008-10-05
> **yman said:**
> 
I tried:

```

sudo ifdown -a
sudo ifup -a

```
as well as restarting the X server, disabling networking via GUI, and turning off the WiFi with the switch. Nothing seemed to work.


How about the really hard way:
```
sudo modprobe -r wireless_driver
sudo modprobe wireless_driver
```
and then repeating the scan and all that? I mean something in the reboot process must get the WiFi to work so your task is just to isolate this something.

---

### Post by yman on 2008-10-05
> **Idefix82 said:**
> How about the really hard way:
```
sudo modprobe -r wireless_driver
sudo modprobe wireless_driver
```
and then repeating the scan and all that? I mean something in the reboot process must get the WiFi to work so your task is just to isolate this something.

How do I find out what wireless driver I have? And can't constant adding and removing cause breakage? I really wouldn't like to risk ruining my good-enough wireless support for a solution that entails about just as much hassle.

BTW, how can I see a live report of my data upload/download? sometimes I need to know it especially so I'd know if others in the house have a slow internet connection because of my humongous network traffic.

---

### Post by Idefix82 on 2008-10-05
I don't know what the command for monitoring upload/download is but you can see it in the System Monitro under System->Administration.

To see what wireless driver you have you can type in
```
lshw -C network
```
and find the block relating to your wireless card. In the last line there will be something saying "driver=...". If you post the output from that command here I can help you locate the relevant bit of information.

You don't need to be afraid of restarting the driver since all these changes will be lost on next reboot. But if that turns out to fix the problem then you can modify the suspend/wakeup script accordingly to have this restarting done routinely. I know this is a crude hack and the behaviour you are describing is still a bug but you would save some time on not having to reboot.

As a side note: in my opinion, someone who can't be bothered to submit bug reports doesn't deserve a bug free open source OS since it can only be bug free if all bugs are reported and the developers receive the maximum amount of information on how and when these bugs occur :) I guess this is my flame-like way of saying: Please spend half an hour or an hour on submitting helpful bug reports. :popcorn:

---

### Post by yman on 2008-10-05
> **Idefix82 said:**
> I don't know what the command for monitoring upload/download is but you can see it in the System Monitro under System->Administration.

I probably already knew that but forgot. How stupid of me.

> 
To see what wireless driver you have you can type in
```
lshw -C network
```
and find the block relating to your wireless card. In the last line there will be something saying "driver=...". If you post the output from that command here I can help you locate the relevant bit of information.


```

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 14
       serial: 00:1d:72:6c:f5:72
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 61
       serial: 00:21:5c:19:43:4d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes **driver=iwl4965** ip=192.168.0.100 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g

```

> 
You don't need to be afraid of restarting the driver since all these changes will be lost on next reboot. But if that turns out to fix the problem then you can modify the suspend/wakeup script accordingly to have this restarting done routinely. I know this is a crude hack and the behaviour you are describing is still a bug but you would save some time on not having to reboot.

Where is that script?

> 
As a side note: in my opinion, someone who can't be bothered to submit bug reports doesn't deserve a bug free open source OS since it can only be bug free if all bugs are reported and the developers receive the maximum amount of information on how and when these bugs occur :) I guess this is my flame-like way of saying: Please spend half an hour or an hour on submitting helpful bug reports. :popcorn:
Who said I expect Ubuntu to be bug-free? And I did submit at least one bug report for something that isn't on this list (apparently it was fixed a while ago). The problem is I have weird fears: fear of programming (which ironically is something I love doing), fear of tinkering, and fear of reporting bugs.

BTW, I also contributed some translations, but I think non were accepted. If any were, I don't know about it.

So please don't say that I contribute nothing. It may be little, but it's something. And publishing this list here is a step forward from keeping my peace, right?

---

### Post by mssever on 2008-10-05
> **yman said:**
> 3. Totem doesn't play audio while Adobe Flash is using audio. In the case of totem-xine, it always freezes after a few seconds or if interacting with the GUI.
I recently discovered the solution to that: I installed libflashsupport, and voilà.

---

### Post by yman on 2008-10-05
> **mssever said:**
> I recently discovered the solution to that: I installed libflashsupport, and voilà.

Wow! Thanks, that sure fixed it up, alright!

---

### Post by mssever on 2008-10-05
> **yman said:**
> Wow! Thanks, that sure fixed it up, alright!
I went to file a bug report asking for libflashsupport to be a dependency of flashplugin-nonfree and discovered that the reason it isn't a dependency already is that libflashsupport exercises a bug in Flash that crashes Firefox sometimes. I haven't experienced any crashes yet, but be warned. Hopefully this will be fixed in Intrepid.

---

### Post by iponeverything on 2008-10-06
> **yman said:**
> 
Who said I expect Ubuntu to be bug-free? And I did submit at least one bug report for something that isn't on this list (apparently it was fixed a while ago). The problem is I have weird fears: fear of programming (which ironically is something I love doing), fear of tinkering, and fear of reporting bugs.

BTW, I also contributed some translations, but I think non were accepted. If any were, I don't know about it.

So please don't say that I contribute nothing. It may be little, but it's something. And publishing this list here is a step forward from keeping my peace, right?

The way that you are going about this is great - measured and rational. Too many folks don't document at all, something pushes them over the edge and then they post some crazy sounding rant that is full of inaccuracies and pent-up frustration. Don't let folks lay that not contributing guilt trip on you.. it is just that, a guilt trip.

---

### Post by Idefix82 on 2008-10-06
> **yman said:**
> 
Where is that script?


I am happy to look into this if you are willing to give it a try. But before I spend any time on it we would have to check whether removing the driver and putting it back into the kernel actually solves the problem. If you would rather not mess with a system which basically works then that's fair enough. Otherwise let me know and we will try to fix this issue.

> **yman said:**
> 
Who said I expect Ubuntu to be bug-free? And I did submit at least one bug report for something that isn't on this list (apparently it was fixed a while ago). The problem is I have weird fears: fear of programming (which ironically is something I love doing), fear of tinkering, and fear of reporting bugs.

BTW, I also contributed some translations, but I think non were accepted. If any were, I don't know about it.

So please don't say that I contribute nothing. It may be little, but it's something. And publishing this list here is a step forward from keeping my peace, right?

In that case I appologise! You made it sound different in your first post.

---

### Post by yman on 2008-10-06
> **Idefix82 said:**
> I am happy to look into this if you are willing to give it a try. But before I spend any time on it we would have to check whether removing the driver and putting it back into the kernel actually solves the problem. If you would rather not mess with a system which basically works then that's fair enough. Otherwise let me know and we will try to fix this issue.

I thought you already knew where it is, but I'm not going to ask you to bother for nothing. Also, reproducing this bug is a little difficult, as I need to suspend, go to a place where the current WLAN isn't available, and then resume. And I'm not sure this bug appears equally with all WLANs.

> 
In that case I appologise! You made it sound different in your first post.
I don't see how, but no matter.

If you look at the list again you'll see I've started attaching bugs to items, and Bug #278904 was reported by me.

---

### Post by ft23002 on 2008-10-06
Don't know if these are annoyances, mistakes or me...
(probably me)

Newbies coming over to ubuntu are unlikely to know the differences between gnome and KDE. A big reason for me wanting to give ubuntu another try was seeing compiz-fusion effects (the cube). Not knowing all the different ways to install at the time... cli, add-remove, SPM, I went to the add-remove gui.
In the add-remove gui, the only compiz-fusion setup tool is for KDE. Looking at the SPM, there appears to be different versions/programs of compiz depending on what one is using, KDE or Gnome. So, when one installs the only shown compiz program in add-remove, are they installing the wrong version? During one install of compiz, had problems with it saving settings, the PC using high cpu resources all the time and now wondering if this is why, as I'm pretty sure this was the way I installed compiz. Since reinstalling ubuntu and installing compiz thru SPM, the default backend is saving settings, cpu resources are much lower and all seems to be running much better.

If one installs compiz set-up tool for KDE from the add-remove gui on a newly installed ubuntu system, are they installing the wrong version of compiz? Would also point out, this is under Show- supported applications pull down and is the only compiz program shown in add-remove.

IMHO, when a user uses the show (only) supported applications pull down in add-remove, it should only show apps that are for the current configured system... running gnome or kde and any other variables that would matter. Why are programs not supported for the current configured system still shown? Another example of this is hardware drivers, while there is 2 shown, 1 for gnome and 1 for kde, only gnome is correct for the default installed ubuntu system. It doesn't help users depending on the show supported applications when it still shows applications that are Not supported by the current system configuration. If I'm missing something here or wrong about this, please let this newb know.

Yesterday after attempting to change the login screen, it didn't change and booting to a working desktop failed. Nautilus had 2 errors and couldn't get it solved without an ubuntu reinstall. Noticed many threads/posts about desktop grey screens caused by various reasons and sometimes no apparent reason at all. This was a big annoyance. Is this a problem with ubuntu, nautilus, or in my case, the downloaded log-in package?
There is 3 updates to nautilus today, did these updates fix these problems?
Would like to change the log-in screen, but don't think its worth the risk.

---

### Post by mssever on 2008-10-06
> **ft23002 said:**
> SPMWhat's SPM? I assume it's an abbreviation you've invented, because no well-known package tool is called SPM.
> In the add-remove gui, the only compiz-fusion setup tool is for KDE.Um, I just opened up Add/Remove and searched for compiz. The first hit was Advanced Desktop Effects Settings, which is for Gnome. Maybe it'd work in KDE, too, but I don't know since I'm not a KDE user. Remember, Compiz is set up by default if your video card and drivers can handle it, so there's no need to install Compiz. You just need to configure it, which is that the first package mentioned is for. If you read the description, you'll see that.
> IMHO, when a user uses the show (only) supported applications pull down in add-remove, it should only show apps that are for the current configured system... running gnome or kde and any other variables that would matter.It appears that the dropdown was poorly-worded. "Supported applications" means apps that Canonical supports if you purchase a support contract from them. These apps are in the main repository, rather than the community-maintained universe or multiverse. It has absolutely nothing to do with your system configuration. Your best bet is to show all available applications and ignore the other options. (You also need to configure your software sources to include the universe and multiverse.) As far as Gnome and KDE apps go, in most cases, it's possible to run KDE apps on Gnome and vice versa.

> Yesterday after attempting to change the login screen, it didn't change and booting to a working desktop failed. Nautilus had 2 errors and couldn't get it solved without an ubuntu reinstall. Noticed many threads/posts about desktop grey screens caused by various reasons and sometimes no apparent reason at all. This was a big annoyance. Is this a problem with ubuntu, nautilus, or in my case, the downloaded log-in package?Dunno, since you didn't provide the error messages or other important details. It's highly unlikely that a reinstall was required. In ten years of running Linux, I've only re-installed once.
> There is 3 updates to nautilus today, did these updates fix these problems?
Would like to change the log-in screen, but don't think its worth the risk.
Dunno if they'd fix your problems, since you didn't say what they were. But you should always install updates unless you have a very good reason not to. Also, you can change the login screen. I don't know what you did, because I've changed mine many times without any problems.

---

### Post by yman on 2008-10-06
> **ft23002 said:**
> Don't know if these are annoyances, mistakes or me...
(probably me)

Newbies coming over to ubuntu are unlikely to know the differences between gnome and KDE. A big reason for me wanting to give ubuntu another try was seeing compiz-fusion effects (the cube). Not knowing all the different ways to install at the time... cli, add-remove, SPM, I went to the add-remove gui.
In the add-remove gui, the only compiz-fusion setup tool is for KDE. Looking at the SPM, there appears to be different versions/programs of compiz depending on what one is using, KDE or Gnome. So, when one installs the only shown compiz program in add-remove, are they installing the wrong version? During one install of compiz, had problems with it saving settings, the PC using high cpu resources all the time and now wondering if this is why, as I'm pretty sure this was the way I installed compiz. Since reinstalling ubuntu and installing compiz thru SPM, the default backend is saving settings, cpu resources are much lower and all seems to be running much better.

What's SPM? Do you mean Synaptic?
Whether an app is a GNOME app or a KDE app shouldn't matter. They should both work. I think that "Supported" thing has to do with whether or not Canonical (the commercial sponsor of Ubuntu) provides technical Support for that app.
As to it being a KDE app, that's only relevant in how the look and feel match the rest of the system and integrating with other applications. It will still work, it would just work better in it's native environment. What I'm trying to say is that your Compiz problems sound like they mostly come from the hardware.

> 
If one installs compiz set-up tool for KDE from the add-remove gui on a newly installed ubuntu system, are they installing the wrong version of compiz? Would also point out, this is under Show- supported applications pull down and is the only compiz program shown in add-remove.

It's all the same Compiz. Ubuntu 8.04 "Hardy Heron" comes with it by default. In order to enable it go to System -> Preferences -> Appearance -> Visual Effects and choose either Normal or Extra. be warned that if it's on None then your hardware isn't on the list of hardware that works well with Compiz.

To customize Compiz you should probably use ccsm. In Add/Remove switch to "Show All available applications" and search for it (or Compiz). It should be the first option.

> 
IMHO, when a user uses the show (only) supported applications pull down in add-remove, it should only show apps that are for the current configured system... running gnome or kde and any other variables that would matter. Why are programs not supported for the current configured system still shown?

They are supported (they work, and Canonical offers technical support for them). The problem is they don't integrate well.

> 
Another example of this is hardware drivers, while there is 2 shown, 1 for gnome and 1 for kde, only gnome is correct for the default installed ubuntu system. It doesn't help users depending on the show supported applications when it still shows applications that are Not supported by the current system configuration. If I'm missing something here or wrong about this, please let this newb know.

You are right that it will confuse people. However, both are supported by Canonical and both work. A user might prefer to use the KDE option on Ubuntu or vice versa, and it will work. I don't know whether hiding non-integrated applications is a good idea (probably is though), or how it should be implemented.

> 
Yesterday after attempting to change the login screen, it didn't change and booting to a working desktop failed. Nautilus had 2 errors and couldn't get it solved without an ubuntu reinstall. Noticed many threads/posts about desktop grey screens caused by various reasons and sometimes no apparent reason at all. This was a big annoyance. Is this a problem with ubuntu, nautilus, or in my case, the downloaded log-in package?

Don't know. Never happened to me.

> 
There is 3 updates to nautilus today, did these updates fix these problems?
Would like to change the log-in screen, but don't think its worth the risk.
Again I don't know.

I think you should open a separate thread with these problems, as what you are saying is that you're in trouble and need help while this threads is more in the nature of complaining about problems that originate in Ubuntu. I'm sure you'll get more help then too, since not very many people will visit this thread for the purpose of trying to help people solve problems.

---

### Post by ft23002 on 2008-10-06
> **mssever said:**
> What's SPM? I assume it's an abbreviation you've invented, because no well-known package tool is called SPM.

SPM- thought it was a known abbreviation for "Synaptic Package Manager", guess not, thank you for pointing that out.

> **mssever said:**
> 
Um, I just opened up Add/Remove and searched for compiz. The first hit was Advanced Desktop Effects Settings, which is for Gnome. Maybe it'd work in KDE, too, but I don't know since I'm not a KDE user. Remember, Compiz is set up by default if your video card and drivers can handle it, so there's no need to install Compiz. You just need to configure it, which is that the first package mentioned is for. If you read the description, you'll see that.

Guess it has to do with what drop down is used in add-remove. when searching compiz with Show: Supported applications, all that shows is:

Desktop Effects
compiz setup tool for KDE 
A simple Compiz configuration tool for KDE. Installs and sets Compiz as the window manager.

...which is how I was viewing it.

When all available applications drop down is used, I now see the rest for compiz and yes Advanced Desktop Effects Settings is shown first.
Reading your reply, would agree the drop down is poorly worded. Thought it meant apps supported by current system. Will leave it as you suggested... show all applications, thanks.


> **mssever said:**
> 
Dunno, since you didn't provide the error messages or other important details. It's highly unlikely that a reinstall was required. In ten years of running Linux, I've only re-installed once.

Dunno if they'd fix your problems, since you didn't say what they were. But you should always install updates unless you have a very good reason not to. Also, you can change the login screen. I don't know what you did, because I've changed mine many times without any problems.

Wish I had the error messages, but I don't. Sure it could have been resolved without reinstall, but as a newbie with little knowledge of linux and it being a newly installed system, it seemed to be the quickest fix. Tried a few things prior with no help. Didn't get much help yesterday, but it may be because I didn't note the error messages.

Would appreciate any further comments you might have and will look to the below thread for them about the dead desktop & log-in screen change.
Thanks

[http://ubuntuforums.org/showthread.php?t=938794]("http://ubuntuforums.org/showthread.php?t=938794")

---

### Post by mssever on 2008-10-06
> **ft23002 said:**
> SPM- thought it was a known abbreviation for "Synaptic Package Manager", guess not, thank you for pointing that out.The usual short term is Synaptic or synaptic. The lowercase variant is the command line name of the program, which is almost always an acceptable variant name. Sometimes, it's even better. For example, the menu entry for one of the default programs reads "Text editor." But there are many text editors, so it'd be better to refer to that one as gedit, which is the name of the command that starts it.

> Wish I had the error messages, but I don't. Sure it could have been resolved without reinstall, but as a newbie with little knowledge of linux and it being a newly installed system, it seemed to be the quickest fix. Tried a few things prior with no help. Didn't get much help yesterday, but it may be because I didn't note the error messages.[]("http://ubuntuforums.org/showthread.php?t=938794")
That's likely why you didn't get much help.

---

### Post by bodhi.zazen on 2008-10-06
> **yman said:**
> I know I should write bug reports, but I just hate going through that process, so instead I post my little list here. 

Yes, bug reports are the way to go. If you would like assistance with any specific problem, start a thread. IMO I advise 1 issue / thread.

---

### Post by yman on 2008-10-06
> **bodhi.zazen said:**
> Yes, bug reports are the way to go. If you would like assistance with any specific problem, start a thread. IMO I advise 1 issue / thread.

Who said I'm trying to get things fixed on my system? Getting help is just a bonus, my real goal being that I want these issues fixed on Ubuntu's side. If you haven't noticed I am trying to make sure these issues get the appropriate bug reports. I'm not sure what I'm trying to accomplish with this thread, but it sure isn't to get help (messed up by putting it in the "General Help", I guess. Good call on moving this thread). I am grateful to those who gave me their time of day, though. Thanks, folks.

EDIT: This isn't exactly a testimonial of my experience with Ubuntu. This is a list of problems that are seeking solutions, not a description of my overall experience or anything.

> **iponeverything said:**
> The way that you are going about this is great - measured and rational. Too many folks don't document at all, something pushes them over the edge and then they post some crazy sounding rant that is full of inaccuracies and pent-up frustration. Don't let folks lay that not contributing guilt trip on you.. it is just that, a guilt trip.

There's no way I'd give up using a great system like Ubuntu just because of a few minor annoyances. There's no need to worry about me ranting and railing against it.

> **Idefix82 said:**
> I am happy to look into this if you are willing to give it a try. But before I spend any time on it we would have to check whether removing the driver and putting it back into the kernel actually solves the problem. If you would rather not mess with a system which basically works then that's fair enough. Otherwise let me know and we will try to fix this issue.

I got to check it and it works, but the downside is it will make connecting to the network slower where it's not needed. I guess I'll just make a script and run it whenever the problem arises.

---

### Post by Idefix82 on 2008-10-07
> **yman said:**
> 
I got to check it and it works, but the downside is it will make connecting to the network slower where it's not needed. I guess I'll just make a script and run it whenever the problem arises.

That sounds like a decent solution. Glad I could help with this one!

---

